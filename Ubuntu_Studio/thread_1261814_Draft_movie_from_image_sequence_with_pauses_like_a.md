---
title: "Draft movie from image sequence with pauses like avisynth? AVIdemux? SMIL? Blender?"
date: 2009-09-09
forum: Ubuntu Studio
---

### Post by fizzybrain on 2009-09-09
'ello.
This is what I had under windows with avisynth:
I have written perl code which generates an animation in the form of lots (~5000) of SVG files. Those individual frames are rendered into png, etc. and the code automaticaly generates an avisynth file (.avs) which is then passed to virtualdub to collect those frames into a movie. Crucially, though, the animation is made up of various segments with pauses between those segments, and those pauses are also controlled by the .avs file. This means that I can easily change the length of the pauses manually after everything has been rendered.
e.g. (.avs file - real thing is much longer ~50 segments, ~50 pauses)
```

clip_0 = ImageSource("scale3d_16c_%03d.png", start=0, end=0, fps=8,pixel_type = "rgb24")
pause_0=ImageSource("scale3d_16c_000.png", fps=8,pixel_type = "rgb24").trim(1,16)
clip_1 = ImageSource("scale3d_16c_%03d.png", start=1, end=17, fps=8,pixel_type = "rgb24")
pause_1=ImageSource("scale3d_16c_017.png", fps=8,pixel_type = "rgb24").trim(1,1)
clip_2 = ImageSource("scale3d_16c_%03d.png", start=18, end=58, fps=8,pixel_type = "rgb24")

+clip_0+pause_0+clip_1+pause_1+clip_2

```

So I can quickly view the finished sequence as a movie without further rendering, encoding, or even waiting for completion (I "update" the .avs file during the run, and refresh it in virtualdub). It also allows me to stitch together different sequences regardless of their file-numbering scheme. If I choose to I can then export as a movie.

I would like to do something similar on Linux (as I think SVG>PNG conversion is *much* faster on Linux, and that is at least half my rendering time), but what is the best way to do it?

I have considered several ideas, perhaps you could give me some idea which I should invest my time in...:
- (quickest?) use avisynth on Linux - I have seen mixed reports about the success of this. I doubt it will be fast enought to give a real-time preview of the movie (which I can manage on windows+avisynth+virtualdub). Where would I start?
- generate still images for those segments (by copying the last image of each pause Nx25 time for N-second pauses, in accordance with file-numbering system) and then open as a conventional (numbered) sequence - yuk, big, clunky, difficult to modify after the event, difficult to stitch different sequences
- use SMIL - this looks like it might do it, but how do I specify filenames with wildcards and pauses, and then what do I play the resultant SMIL file in? Basically, is this appropriate for SMIL?
- use Blender - no idea whether this is sensible, but I imagine there must be a sequence editor in there somewhere and I want to learn Blender next :-) . Can I automatically generate a script though?
- use some clever command-line script
- use something else
, etc....

I know I could render those files into a movie and I could probably even work out how to generate a script to do it, but at this drafting stage I'd like to keep the flexibilty and speed of viewing sequences as they are being created.

Any thoughts?

Oh yes, and I'd like bells on it too please.

Share and Enjoy,
Fizz

---

### Post by fizzybrain on 2009-09-09
Well, in case anyone's interested, I managed to get it to run using avidemux and avsproxy.exe and WINE. It's simple and quick, but it it took me *ages* to find out where to get avsproxy.exe! In the end I found it in amongst the source files of an old version of avisynth (it might be in a new version as well, but maybe not).
Now I can use avidemux and its lovely shuttle control, hurrah!
And, by the way, to render the SVG into PNG I'm now using rsvg, part of librsvg, and it's *way* faster than inkscape under winXP (can't say what it's like under linux). It uses a different default font though, which is a bit ugly, so I'll have to:
a) find how to set a default font-family for a whole SVG document;
b) change the code to specify the font-family of each bit of text;
or c) do the final render using Inkscape.
Share and enjoy,
EDIT:
In fact, rsvg text output is broken (when using transform and span, anyway)
Rendering 57 text-heavy files:
Linux + rsvg = 142 seconds (ugly; broken ouput; ok for drafting; no crashes so far)
Linux + inkscape = 192 seconds ( good-quality output, but sometimes crashes - "emergency save activated" - , destroying preferences.xml and preventing batch processing)
WinXP + inkscape = 242 seconds (good-quality, reliable)

Gwenview does a great job of rendering SVG using Qt... maybe it's worth using that for converting all files at once after the run is finished....

---

