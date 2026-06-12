---
title: "Anyone in the mood to help me with Geometry and Math?"
date: 2010-01-09
forum: The Cafe
---

### Post by legolas_w on 2010-01-09
Hello everyone.

I have a problem and I am not able to solve it, I thought maybe some one in the cafe could help me with that.

I have a map with coordinates of its four corners. I need to calculate the coordinate of a given point inside the map. So far I am able to calculate the distance of the given point from all four corners but I do not know how to calculate the coordinates of the point.  

For example the corners coordinates are as follow:
Top Left: 40.799947, 30.60000
Top Right: 40.79930, 30.62686

Bottom Left:40.788588, 30.60006
Bottom Right:40.788613, 30.626819

And the distance of a point from the corners is as follow:
From TL: 2018 meters
From TR: 307 Meters
From BL:2292 Meters
From BR: 1130 Meters

If you can help me with some formula or algorithm to calculate the point coordinate, I will be thankful.

thanks

---

### Post by starcannon on 2010-01-09
[http://en.wikipedia.org/wiki/List_of_canonical_coordinate_transformations#To_polar_coordinates_from_Cartesian_coordinates](http://en.wikipedia.org/wiki/List_of_canonical_coordinate_transformations#To_polar_coordinates_from_Cartesian_coordinates)

That'll teach you how.

---

### Post by koleoptero on 2010-01-09
Draw a horizontal line from the point you have on the map. That line connects with the edge of the map at some point. calculate the distances from the top corner there. Then the latitude at that point can be calculated as:

[latitude of top] + **(**latitude of top - latitude of bottom**)*****(**[distance of point from top]/[distance of bottom from top]**)**

same goes for longitude (that's what its called right?)

---

### Post by starcannon on 2010-01-09
Here is something more straight forward, in case your still messing with this:
[http://www.maa.org/projectwelcome/ca_preview/txt_book/sec21b.htm](http://www.maa.org/projectwelcome/ca_preview/txt_book/sec21b.htm)

I'd be more forthcoming if I was sure you weren't doing homework or something of that nature.

---

### Post by legolas_w on 2010-01-10
> **koleoptero said:**
> Draw a horizontal line from the point you have on the map. That line connects with the edge of the map at some point. calculate the distances from the top corner there. Then the latitude at that point can be calculated as:

[latitude of top] + **(**latitude of top - latitude of bottom**)*****(**[distance of point from top]/[distance of bottom from top]**)**

same goes for longitude (that's what its called right?)

Hi,

thank you for helping me on this. I tried your formula for the following inputs:


```
LAT of Top : 40.810993

LAT of Bottom: 40.804031

Top to Bottom Distance: 766.33 Meters

Point distance from top: 296.72 Meters

```

putting them into the formula is as follow:

```

40.810993 + ((40.810993-40.804031)*(296.72/766.33)) 

```

The calculation result is  40.813688659 while the actual LAT of the point is 40.808309

Can you please review the formula and let me know whether I am placing the numbers in the correct orders or not?

---

### Post by legolas_w on 2010-01-10
> **starcannon said:**
> Here is something more straight forward, in case your still messing with this:
[http://www.maa.org/projectwelcome/ca_preview/txt_book/sec21b.htm](http://www.maa.org/projectwelcome/ca_preview/txt_book/sec21b.htm)

I'd be more forthcoming if I was sure you weren't doing homework or something of that nature.

Hi,

Can you please be more specific on this? I am working to develop a software and it is few days that I am trying to calculate the coordinates of a point when I have its distance from some known coordinates.

Being more specific, I have few screenshots of google earth with coordinates of their corners. Now I want to extract the coordinate of a given pixel in the pictures based on the fact that I have other four coordinates.


It is not homework, I am trying to help with my friend to add some visualization to his thesis which is about distribution of water resources and population in rural areas. I am not good in math and geography so I am not able to come with a formula for this calculation.

Thanks.

---

### Post by koleoptero on 2010-01-10
> **legolas_w said:**
> Hi,

thank you for helping me on this. I tried your formula for the following inputs:


```
LAT of Top : 40.810993

LAT of Bottom: 40.804031

Top to Bottom Distance: 766.33 Meters

Point distance from top: 296.72 Meters

```

putting them into the formula is as follow:

```

40.810993 + ((40.810993-40.804031)*(296.72/766.33)) 

```

The calculation result is  40.813688659 while the actual LAT of the point is 40.808309

Can you please review the formula and let me know whether I am placing the numbers in the correct orders or not?

If latitude counts from bottom to top (increases as you go higher) then you need the distance of the point from the bottom, and not the top. I am sorry, I'm a mathematician but I haven't ever used actual maps. :)

---

### Post by legolas_w on 2010-01-11
Hi, Thank you for looking back at the thread.

I replace the values it looks like the following equation:

40.810993 + ((40.810993-40.804031)*(469.61/766.33)) which resulted in 40.815259341 but it is not the correct lat of the point (the correct lat is 40.808309).

Can you please take a look and let me know what I am doing wrong?


Thanks

---

### Post by koleoptero on 2010-01-11
> **legolas_w said:**
> Hi, Thank you for looking back at the thread.

I replace the values it looks like the following equation:

40.810993 + ((40.810993-40.804031)*(469.61/766.33)) which resulted in 40.815259341 but it is not the correct lat of the point (the correct lat is 40.808309).

Can you please take a look and let me know what I am doing wrong?


Thanks

It might be I'm doing it wrong :-k I'll check it again.

I saw what's wrong, it's the map, I should have thought about it. We need to triangulate the distances. I'll see to it and let you know the results.

P.S.: I am not saying it's the map's fault.

---

### Post by legolas_w on 2010-01-11
Hi,


Thank you for looking into th issue. I really appreciate it.

---

### Post by gn2 on 2010-01-11
[http://jan.ucc.nau.edu/~cvm/latlongdist.html](http://jan.ucc.nau.edu/~cvm/latlongdist.html)

---

### Post by kayvortex on 2010-01-11
The formula you used, and were given was based on Euclidean geometry (geometry on flat spaces, basically). But, the Earth is a sphere and so you must use trigonometric calculations if you want accurate answers, especially since your differences of latitude and longitude are so large.

But, it's going to be more complicated that even that because I don't know how Google projects the Earth into a 2D image; although it's probably planar projection, which means that the picture gets squashed at the sides (zoom out of Google Earth and look at countries at the edge of the globe: they look distorted and are not scaled at the same amount than countries directly facing you).

You might be better off getting somebody else to do these calculations for you in person rather than over the Internet where it's difficult to draw pictures and present formulae, but if I can get it conveyed in a way that's simple to understand, I'll try to do it.

---

### Post by kayvortex on 2010-01-11
*Edit: the equation may look easy, but involves a bit of work to derive, so I'm just going to give it without explanation. If it is homework (which seems a bit implausible to me -- i.e., I'm inclined to believe you're not 15 and cheating!) then you'll get no marks without showing work anyway. If anyone objects, make a post and I'll remove the equation. (In fact, I might remove it after a while anyway so that someone else doesn't stumble upon it, which still seems a bit unlikely to me).*

Ok, the basic formula is this (this will give you the latitude or longitude, so it's the same formula for both):

L = latitude (longitude) difference from the very top and bottom (very left and right) of your map picture in degrees.
X = distance between the very top and bottom (very left and right) in metres.
R = radius of Earth.
x = distance you measure from top or bottom (left or right) latitude (longitude) in metres.

angle = L/2 - arctan( (X-2x)/(2R) ).

So, you want a latitude answer, so we'll use the latitude figures:
L = (40.810993 - 40.804031) degress = 0.006962 degrees
X = 766.33 metres
R = 6371000 metres
x = 296.72 metres from top latitude (so, the answer will be degrees from the top latitude too).

angle = 0.006962/2 - arctan( ( 766.33 - 2*296.72 ) / 2*6371000) )
angle = 0.00270358... degrees

Since our x was metres from the TOP LATITUDE, our answer is degrees from the TOP LATITUDE. So, the latitude of our point is about ( 40.810993 - 0.00270358 ) degrees = 40.808289 degrees.

This looks like a pretty good answer. The radius of the Earth varies from place to place (and gets shorter the closer to the north or south poles you go) and so was only given to 4 significant figures (got the answer from wikipedia) and so the final answer also to 4 significant figures matches up OK.

**But, I haven't checked the equation and I might have made a mistake (there was a Hindi film bellowing in the background while I was deriving it!). I suggest you try it out with extreme values of latitude and longitude to see if the answers are still good (i.e. take maps with lats/longs that differ by up to tens of degrees).**

[I]Edit: the equation is based on the assumption that the Google Earth image is formed from a planar projection of the Earth's surface onto a 2D rectangular image that is centred on the centre of the Earth.
1) If the 2D projected image is not rectangular, then the measurements have to be taken from a constant horizontal or vertical line from whatever corner the numbers are derived from (i.e., things will be more difficult if the Google Earth image on your screen is not a rectangle of some sort -- shouldn't really be a problem since the frame where the Google Earth picture is shown **is** rectangular).
2) If the 2D projected image is not such that the point in the middle of the projected image overlaps the centre of the Earth, then the figures will need to be adjusted. The easiest way to avoid this problem is to not move the Earth in space -- just spin it around.
3) Finally, if Google Earth doesn't use planar projecting, then the whole thing is definitely wrong (but, I'm pretty sure it does use it, so that shouldn't be a problem).[/I]

---

### Post by legolas_w on 2010-01-12
kayvortex,

Thank you very much for your help. 

I tried your formula and it works fine for the Latitude calculation but when it come for the longitude, my calculation results in a highly inaccurate value.

for example for a point with longitude = 30.644028 I have the following information:

```

distance from right: 1016.14
distance from left: 292.81
right to left distance: 1308.95

longitude of Right: 30.656095  
longitude of LEFT: 30.640553



L: 30.656095 -30.640553 = 0.015542
X: 1308.95
R: 6371000
x: 1016.14  (distance from right)

Based on L/2 - arctan( (X-2x)/(2R) ) we have: 

0.015542/2-arctan((1308.95-2*1016.14)/(2*6371000))  = 0.00782777


```

Can you please take a look and let me know whether I am missing something in this calculations? 
If The full coordinates of the map is required: 
```

Lat of top: 40.812455
lat of bottom: 40806599

longitude of Right: 30.656095  
longitude of LEFT: 30.640553

Sample point coordinates: 40.809527°,  30.644028°

```

Thank you.

---

### Post by kayvortex on 2010-01-12
I'm so sorry *legolas_w*, I must have been especially stupid yesterday: the formula I worked out for you was for (a slightly non-standard) stereographic projection. So, it was totally wrong! This is the correct formula you want:

L = lower latitude (longitude) value in degrees.
H = higher latitude (longitude) value in degrees.
X = total height (width) of window in metres (same definition as before).

Now, if you're going to use a distance from L (the lower value), then use:

**angle = arccos( cos L - (l/X)(cos L - cos H) )**   <--- N.B. that's an "l" not a "1" in "(l/X)"
l = distance from L in metres

and if you're going to use a distance from H (the higher value), then use:

**angle = arccos( cos H + (h/X)(cos L - cos H)**
h = distance from H in metres.

So, depending on whether you measure from the top or bottom latitude (left or right longitude) then you have to slightly change the formula by using cos of that line you're measuring from and switching the sign in the middle.

OK, this formula(e) should just give you your final angle; so, let me do the latitude calculation again:

L = 40.804031
H = 40.810993
X = 766.33
h = 296.72 <-- this is the distance from the top (i.e. distance from H) so we use the formula with "h" in it instead of "l".

angle = arccos( cos(40.810993) + (296.72 / 766.33 ) * (cos(40.804031)-cos(40.810993)) )

angle = 40.808297...

I tried the longitude figures and they also match up OK this time, but I'll let you do the calculation in order to make sure that you know how to use the formula and that I've explained this clearly.

Again, try it out with more extreme values, and I'm sorry about wasting your time with that other formula!

---

### Post by legolas_w on 2010-01-18
Thank you very much for your help. I got it working perfectly.

---

