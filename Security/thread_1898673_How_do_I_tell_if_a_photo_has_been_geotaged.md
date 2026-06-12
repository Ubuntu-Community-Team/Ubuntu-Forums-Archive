---
title: "How do I tell if a photo has been geotaged?"
date: 2011-12-21
forum: Security
---

### Post by waterbob on 2011-12-21
How do I tell if a photo has been geotaged?

---

### Post by lisati on 2011-12-21
I don't have quick access to any geotagged photos, but would suggest that a good place to look is to right-click on the photo in nautilus, select "properties", then open the "image" tag.

---

### Post by waterbob on 2011-12-21
> **lisati said:**
> I don't have quick access to any geotagged photos, but would suggest that a good place to look is to right-click on the photo in nautilus, select "properties", then open the "image" tag.
I don't see any gps numbers does that mean it is not?

And do new cell phones automatically geotag photos?

---

### Post by lisati on 2011-12-21
> **waterbob said:**
> 
And do new cell phones automatically geotag photos?
It might depend on the phone. In our house we have 3 mobile phones that we've had from new for under 12 months. AFAIK none of them put the geotag info in the file.

---

### Post by waterbob on 2011-12-21
> **lisati said:**
> It might depend on the phone. In our house we have 3 mobile phones that we've had from new for under 12 months. AFAIK none of them put the geotag info in the file.
I use a Samsung does that automatically geotag?

---

### Post by Tom Collier on 2011-12-21
> **waterbob said:**
> I use a Samsung does that automatically geotag?

Geo-tagging usually has to be turned on in your smart phone's camera settings. On mine, I press the app menu (not the phone menu), and it allows me to change photo size, quality, storage location, brightness, contrast, etc .... and to turn geotagging on or off. When geotagging is on, with my phone at least, there is a specialized icon in one corner of the viewfinder.  

Check your camera app's settings and look to see if it has a geotagging toggle switch that let's you turn it on or off.

---

### Post by lensman3 on 2011-12-24
Try this:

listgeo - utility program (distributed with libgeotiff) for dumping the metadata of a GeoTIFF file

This works for some geotiff maps I have.  It might be smart enough to see the Lat-Long coords of a GPS aware camera.

Hope this helps

---

### Post by Myrddin Emrys on 2011-12-25
[FONT=Verdana]You could use exiftool (install the libimage-exiftool-perl package). Then:
[/FONT][FONT=Verdana][FONT=monospace]
[/FONT][FONT=Courier New]exiftool -a -gps:all image.jpg[/FONT]
[/FONT][FONT=Verdana]
Here's a sample geotagged image:

[http://www.panoramio.com/photo/18517440](http://www.panoramio.com/photo/18517440)
[http://static.panoramio.com/photos/original/18517440.jpg](http://static.panoramio.com/photos/original/18517440.jpg)

Alternatively, you could upload the image to this site (based on exiftool):

[http://regex.info/exif.cgi](http://regex.info/exif.cgi)

and search the results page for 'GPS'. 

More on exiftool:

[http://www.sno.phy.queensu.ca/~phil/exiftool/]("http://www.sno.phy.queensu.ca/%7Ephil/exiftool/")





[/FONT][FONT=Verdana]
[/FONT]

---

