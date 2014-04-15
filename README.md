Lazy Vertical Rhythm
==========

Sass vertical rhythm functions and mixins


Stand Alone Edition
==========

All variables, functions, and mixins have been separated into their own folder.


Whats It Do?
==========

Sets the vertical rhythm of the page based on initial line height. New font sizes will have line height, padding, borders, and margin adjusted accordingly.
Works with pixel values, em values, or rem values (with a pixel fallback provided.)


Calling Order
==========

You should import these in the following order
@import 'rhythm/rhythm_vars';
@import 'rhythm/rhythm_helpers';
@import 'rhythm/rhythm';


Table of Contents
==========

The rhythm_vars file has all the default variables for you to configure. Here you'd set default font size, line height, margin and padding. I've also included a variety of font scaling variables to use (there's an example of how to use them in rhythm_starters)
The rhythm_helpers file has the secondary functions that help with some of the lifting of our other mixins
The rhythm file has the 3 mixins you'll be using to set up your sizes, line heights, padding, borders, and margins.


Gotchas
==========

Margins and padding are defined as multipliers. So if you say you want a margin of 1, it'll be default line height * 1 (if line-height were 24px your margin would be 24px)
If you said give me a margin of 0.5 you would have a margin of 12px, a margin of 2 would return 48px, and so on. 

Example Calls
==========

@include rhythm takes up to 4 variables, 1: your desired font size in pixels, 2: the unit you would like to use (em, rem, px), 3: your top margin multiplier (optional), 4: bottom margin multiplier (optional).

For setting font size you'd do something like this:
p {
		@include rhythm($font_px, rem);
}

which would output

p {
  font-size: 16px;
  font-size: 1rem;
  line-height: 1.5;
  margin-top: 6px;
  margin-top: 0.375rem;
  margin-bottom: 18px;
  margin-bottom: 1.125rem; }

We have margins because of variables file includes a default for margins and padding. If you'd like to overwrite do something like

p {
		@include rhythm($font_px, rem, 0, 0);
}

or change the variables to whatever you'd like. 

All variables are optional in @include padding_rhythm. If you are using em, please provide a variable for desired size as em's scale per their parent font, not the root.

p {
	@include padding_rhythm(24, em, 0, 0)
}

which will return your desired padding.


@include border_rhythm is the most complicated

@include border_rhythm($desired-size: $font_px, $unit: px, $lazy-padding-top: $rhythm-padding-top, $lazy-padding-bottom: $rhythm-padding-bottom, $border: false, $border_horizontal: false, $border_bottom: false, $border_left: false)

Unfortunately at this time if you would like border top and border bottom but not border left or right you need to provide 3 borders.

Example
@include border_rhythm(24, px, 0, 1, 2px solid #000, 0px, 1px solid #FF0000);
