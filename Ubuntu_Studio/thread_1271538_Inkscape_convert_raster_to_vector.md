---
title: "Inkscape: convert raster to vector"
date: 2009-09-21
forum: Ubuntu Studio
---

### Post by billdotson on 2009-09-21
I want to convert raster digital camera photographs to vector images and I do not know how to do it. I opened a png or tiff in inkscape and saved it as svg but when I opened the svg and zoomed in the image became pixelated.

My main idea for raster to vector was to see if a vector image could keep a similar amount of detail when compared to a raster photo. Part of my desire to do this is because I want to use vector graphics for the game I am working on.

Thanks.

---

### Post by alphacrucis2 on 2009-09-21
> **billdotson said:**
> I want to convert raster digital camera photographs to vector images and I do not know how to do it. I opened a png or tiff in inkscape and saved it as svg but when I opened the svg and zoomed in the image became pixelated.

My main idea for raster to vector was to see if a vector image could keep a similar amount of detail when compared to a raster photo. Part of my desire to do this is because I want to use vector graphics for the game I am working on.

Thanks.

Wikipedia has a table of converters. Looks like there are some GPL ones but I don't known how good they are:

[URL="http://en.wikipedia.org/wiki/Comparison_of_raster_to_vector_conversion_software"]http://en.wikipedia.org/wiki/Comparison_of_raster_to_vector_conversion_software
[/URL]

---

### Post by Stochastic on 2009-09-21
What you have done is imbed the tiff file into the svg file.  It's still a bitmap, it hasn't been vectorized.

Inkscape can easily vectorize bitmaps by opening them, selecting the bitmap object (by clicking on it once), then going to the menu item Path->Trace Bitmap
A dialog window will open with all sorts of options.  You will probably want to select Multiple Scans -> Colors and increase the number of color layers it traces.

Then the last step is to delete the bitmap that is embedded in the image (move the new vector layer out of the way) then save the image.

Here's a more complete tutorial: [http://www.inkscape.org/doc/tracing/tutorial-tracing.html](http://www.inkscape.org/doc/tracing/tutorial-tracing.html)

Hope that helps.

---

### Post by mcduck on 2009-09-21
Stochastic already explained how to vectorize the image, so  just wanted to point out that vectorizing pohotos will result in considerably larger images than the original bitmap file if you want to keep all the details. Instead of defining just a pixel color it would have to create a new object for each pixel, and then define the objects shape, location and color. That's a lot more data so vectorizing photographs only makes sense if you reduce colors and details, never if you want to maintain the same level of details.

---

### Post by Saadh on 2013-04-01
[COLOR=#000000][FONT=Arial]Accelerated-IO.com has an online app that can convert raster to SVG then animates it. The app can also edit existing animation. Check [http://www.pac-n-zoom.com/](http://www.pac-n-zoom.com/).


[/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-04-05
Thread closed. Please do not post in old threads.

---

