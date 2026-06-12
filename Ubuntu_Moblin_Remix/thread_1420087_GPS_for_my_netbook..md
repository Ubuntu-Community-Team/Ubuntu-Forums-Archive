---
title: "GPS for my netbook."
date: 2010-03-02
forum: Ubuntu Moblin Remix
---

### Post by n00bl0r14n on 2010-03-02
Greetings!

My first post here so let's see how it goes.

I have a USB GPS dongle ([link]("http://www.chinavasion.com/product_info.php/pName/gps-receiver-usb-adapter-for-computers-netbook-laptop-umpc/")) that I want to use to ubuntu but I'm unsure how and where I should get software and maps. I tried it before in windows xp before I installed ubuntu and the test program worked good. Now I would want to test it in ubuntu, what should I do?

-Thanks

---

### Post by tgalati4 on 2010-03-02
sudo apt-get install gpsd gpsdrive
gpsdrive

---

### Post by n00bl0r14n on 2010-03-02
Thanks! How do I resize it? To big for my netbook.

---

### Post by tgalati4 on 2010-03-02
man gpsdrive

See if there are any switches to set the default window.

Perhaps:

       -s height
              Set  the  height of the screen, if autodetection doesnâ&#8364;&#8482;t satisfy
              you, height is i.e. 768,600,480,200

       -r width
              Set the width of the screen, if autodetection donâ&#8364;&#8482;t satisfy you.
              Works only in combination with -s

---

### Post by sgosnell on 2010-03-02
What netbook?  There is a version of Maemo Mapper, originally for the Nokia N8**, ported for the Asus EEE-PC.  It might run on other netbooks, but I'm not sure.  You can check the Maemo Garage for the project, and read the user forum for it for details.  It takes maps from several places, including Virtual Earth, Google, and OpenStreet, and displays your GPS location on them.  It's a very nice program.  I use it on my N800 regularly, and I'm thinking about installing it on my EEE.  You can also try RoadNav, which uses vector data from US Census maps, allowing on-the-fly routing, which is only possible with vector maps.  Anything using raster maps, like Maemo Mapper or Google Maps, has to have a route downloaded in advance, and can't change the route without an internet connection.

---

### Post by tgalati4 on 2010-03-03
I have an n800 and I use maemo mapper.  I was not aware that it had been ported.

---

### Post by sgosnell on 2010-03-04
Just done, and apparently not perfectly.  It requires some additional libraries, which I don't have sorted out yet.  I haven't really had time to work on it very much.  Details on the Maemo Mapper discussion page on Maemo.

---

### Post by him610 on 2010-03-15
Here is the link to an informative article; I did this; it all works.
[http://http://www.linux.com/archive/feature/152468]("http://http://www.linux.com/archive/feature/152468")

Cheers,

---

### Post by debianmike on 2010-03-23
get gpsd for sure, then (good) gps clients can talk to it.

gpsd talks to your gps device, then the app's talk to gpsd.

I *think* I use Viking since that gpsdrive isn't sized right at all.

xgps is also a quick test to see if your netbook is talking to the device.

Also note that the maps come from the internet so unless you are online your maps will be blank.  You can pre-download any area you want however, though I haven't found a good way to do so other than just browsing to that area while online.

---

### Post by debianmike on 2010-03-23
sorry, it's TangoGPS

[http://www.tangogps.org/gps/cat/About](http://www.tangogps.org/gps/cat/About)

---

### Post by jameshock on 2010-04-10
This GPS Receiver USB Adapter for Computers is a compact, faithful GPS earpiece with low power activity that plugs into your computer's USB port. This earpiece is fit for all the applications of a tralatitious GPS earpiece including planning your activate before you head discover or finding your location while you are camping. All you need is: (1) the CVGI-B07 GPS dongle; (2) a computer; (3) GPS navigation software**; and (4) a destination. After installing the earpiece and the needed software, you can find your location correct on your laptop. The GPS earpiece takes its power from the PC it is attached to, so there are no extra wires or cables to bond you down.

---

### Post by latticeguy on 2010-04-14
gpsdrive and tangogps are pretty good, but if you have patience "google navit" and then go to the wiki
compiling it is tedious because of many dependencies, but quite instructive
for maps, planet.bin gives you the whole world in one huge file, but you only need to download it once
Once it is set up, it works wonderfully!

---

### Post by n00bl0r14n on 2010-06-01
Ok, I have a eee 901.

I have tried GPSDrive but I can't get it to work properly.
GPS Tango have worked fine.

How do I get maps for Tango?

After I enabled Tracking and came home in range for my Wifi I got a map (it even showed that I drove by someone xD) but how can I make routes from addres A to B?

---

### Post by Herman on 2010-06-29
> After I enabled Tracking and came home in range for my Wifi I got a map  (it even showed that I drove by someone xD) but how can I make routes  from addres A to B?     :) Hello n00bl0r14n, I also have Tango GPS in my EeePC 701 and it works great with my [USB GPS receiver]("http://asia.chinavasion.com/images/Chinavasion-CVGI-B07-1.jpg"). 

Before I started using Tango GPS for away from home I spent a lot of time with my EeePC plugged into the internet and I panned around my surrounding area at various zoom levels to download as many map files from each of the kinds of map that Tango GPS can display, so that I have a large store of maps stored in my computer.
The Google Maps and Google Sat images are both very useful for route planning where I live.

In case the maps that can be automtically downloaded from the internet aren't enough, another program I use in conjunction with Tango GPS is Quantum GIS. It's possible to use Quantum GIS to make our own customized maps.
Tango GPS can create a log file when that function is enabled.
It only takes two commands to change the .log files from Tango GPS into .csv files that can be used by Quantum GIS, for convenience I made them into a script,
```
#!/bin/bash
# a script for changing tango gps log files into csv files
# just copy this script and paste in inside a directory full of gps log files and run it

# add the required header line to the top of all .log files in the current directory
for fil in *.log; do sed -i '1iY_Coords_WGS84,X_Coords_WGS84,Z_Coords,satinfo1,satinfo2,satinfo3,Date_Time' $fil; done

# replace the .log file name extensions with the .csv filename extension
for f in *.log; do mv "$f" "${f%.log}.csv"; done
```Quantum GIS has mapping tools that are outside the scope of Tango GPS so those two programs make a good combination.
We can open the new .csv files we make with the Delimited text Plugin in Quantum GIS to show lines of dots marking where we have been. 
If you already have features recorded in the map you are working on in Quantum GIS it's obvious that you can use that information for planning routes as well. 
Regards, Herman :)

---

### Post by n00bl0r14n on 2011-06-13
I got the exact same dongle as you Herman xD

I goto try Quantum GIS and test it out. It would be cool if I could enter street addresses into TangoGPS so it would work like a car gps.

TangoGPS has worked fine and wonder if it have any other nifty features. Still haven't got it from 0.99.3 to 0.99.4.

GPSDrive could find any signals (while Tango did) and I got confused with it.

Navit I could not get anywhere with, just saw a green circle.

What other programs can I try?

---

### Post by Herman on 2011-06-14
Live GPS tracking is available in Quantum GIS now, from the 'View' menu, [GPS Tracker tool in QGIS trunk]("http://linfiniti.com/2010/01/gps-tracker-tool-in-qgis-trunk/").

---

