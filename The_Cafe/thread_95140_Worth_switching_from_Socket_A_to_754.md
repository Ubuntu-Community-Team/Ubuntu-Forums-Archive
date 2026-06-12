---
title: "Worth switching from Socket A to 754?"
date: 2005-11-25
forum: The Cafe
---

### Post by hcker2000 on 2005-11-25
I'm pondering buying some newer hardware. Right now my current specs are an albatron mobo (love it), 2400+ at 2.2ghz, 1 gig of pc 3200 by kingston. Every thing else is prity average 80 gig segate 7200rpm 8mb cach, fx5600 video card.

I do alot of 3d rendering, video editing, gaming of corse. So basicly I'm looking at some thing to cut my rendering and compression time down. I am planing to pick up a 256 meg 6600 (eather agp or pci depending but right now it looks like agp).

So dose any one know if I will be gaining any thing by going from what i have now to some thing like an A64 at 2.0ghz on a socket 754?

---

### Post by ember on 2005-11-25
It does gain you a noticable perfomance increase. I've seen the difference between an Athlon 3000+ and an Athlon 64 2800+ - speaking in Doom 3 terms you could play it in 1024x768 on the latter one, while the first one had problems with 800x600.
I would advise you to speed up via a new (S-ATA) harddisk, yet basically that means more or less a complete upgrade.
And think about heat problems in advance. The Athlon 64 can be used as a surrogate heating under heavy load.

---

### Post by hcker2000 on 2005-11-25
Ok and your talking about a 754 64 bit right?

Games I guess are on my list but render time and compression is the big thing I'm looking for in a new upgrade. If I can get a substantal gain in all 3 areas by going to a socket 754 A64 cpu and mobo then it will be well worth the $170. If we are only talking shaving 4 or 5 min off a 7 hour render then no its not worth it.

---

### Post by ember on 2005-11-25
Yes - that's right. 

Well - according to [http://www.tabsnet.com/]("http://www.tabsnet.com/"), you shouldn't expect too much when it comes to rendering. 
Maybe you can gain additional speed when you build your rendering software for 64-bit. 

From a subjective point of view, I would say, the overall performance gain is about 15 or 20%. 

If you have a short sequence to render, I could measure the duration for you.

Best,
ember

---

### Post by hcker2000 on 2005-11-25
Unfortunitly its going to be a year or two before new rendering/modeling software is out as they just released max 8.

If you dont mind downloading pov ray ([http://www.povray.org/download/](http://www.povray.org/download/)) there is a scene in there that is for bencharking 3d rendering and of corse pov ray is free. I don't have access to my box right now but I will in a few hours so if you would post your resulting time then I could compare it here in a bit.

Figuring in a 15% increse at 420 min results in cuting off of 63 min. Which for about 170 worth of upgrades isnt to bad. Not even counting the added gaming benifits and normal video compression time.

If you could tell me how many fps you can do when encoding a dvd quality video into divx or xvid that would give me a good idea of video performance gains.

---

### Post by basketcase on 2005-11-25
Why not go to 939?  It doesn't cost much more.

---

### Post by hcker2000 on 2005-11-25
That is an option if any one can site the difference from going from socket A to 939 then that would help.

---

### Post by poptones on 2005-11-25
There's a new "ultimate processor shootout" on Tom's (big ol' grain-o-salt mandatory) and it seems to show a pretty substantial difference in video processing times once you get into the better AMD 64 chips. Basically, it seems Sempron's aint't worth the money but once you get above "Sempron" it looks pretty substantial. 

I'm still using a pre-barton 1800. I never upgrade until a 2x performance increase is about $100... yes, it's time to upgrade :)

---

### Post by hcker2000 on 2005-11-26
Thanks I will check it out. I was thinking of going with [this]("http://www.newegg.com/Product/Product.asp?item=N82E16819103424") and an albatron mobo.

So if that will bring my rendering times down an hour or maby a bit better than that it would be a good buy.


Ok now the stupid stain on my desk is still not dry. So ran the povray test on my 3.4ghz pentium 4 laptop. It took 34m, 04s.

---

### Post by ember on 2005-11-26
O.k. I ran the benchmark:

Time For Parse:    0 hours  0 minutes   4.0 seconds (4 seconds)
Time For Photon:   0 hours  0 minutes  51.0 seconds (51 seconds)
Time For Trace:    0 hours 35 minutes  22.0 seconds (2122 seconds)
    Total Time:    0 hours 36 minutes  17.0 seconds (2177 seconds)

I used povray 3.5 from the repositories. My system specs are:
Shuttle SN85G4v2 (Nforce 3) / Athlon 64 2800+/1 GB Kingston RAM / MSI GF FX5700LE
Ubuntu 5.10 / i386 kernel

Best,
ember

---

### Post by psoleko on 2005-11-26
The Socket 754 CPUs do not contain a dual channel memory controller, whereas the the socket 939 (hence the extra pins) do. This provides more bandwidth for the CPU to access memory which will generally improve performance in applications such as games, media creation, encoding. You are better off spending a little bit more for 939 and do remember you need to buy memory in pairs. Also, make sure you go for an nvidia chipset, my experience with nvidia hardware under Linux has been amazing to say the least. Absolutley zero problems with hardware detection.

---

### Post by Teroedni on 2005-11-26
I run the command

```
sudo povray /tmp/fr-SqO1jt/benchmark.pov
```

Persistence of Vision(tm) Ray Tracer Version 3.5.0c-10 (Debian x86_64-linux-gcc)
  This is an unofficial version compiled by:
  Jeroen van Wolffelaar <jeroen@wolffelaar.nl> for Debian ([www.debian.org](www.debian.org))
  The POV-Ray Team(tm) is not responsible for supporting this version.
Copyright 1991-2002 POV-Ray Team(tm)
and etc..................


*note: I was running xmms and xchat and 3 ephiany while im benchmarked


Time For Parse:    0 hours  0 minutes   5.0 seconds (5 seconds)
Time For Photon:   0 hours  0 minutes  49.0 seconds (49 seconds)
Time For Trace:    0 hours  5 minutes  55.0 seconds (355 seconds)
    Total Time:    0 hours  6 minutes  49.0 seconds (409 seconds)
teroedni@turion:~$
This is on a 754 socket;)
Turion ml 30 proc(1,6ghz 1mb l2cache)
Xfx 6200 256
Asus k8n 250
one memory module 512 elixir ram(cheapy;)
P80 samsung sata 8mb/7200rpm cheap but damn good hardrive:)

---

### Post by hcker2000 on 2005-11-26
I'm checking out the 939's right now for prices.

If that 754 will do it in 6 min insted of the half hour it takes my laptop to do it. I know my desktop that I want to upgrade is a bit faster than this 3.4ghz but I dont think its any ware near that much faster.

I already have matched memory (a gig of it from kingston) so thats already taken care of.

As for going with nvidia thats a given as I love there chipsets.

---

### Post by ember on 2005-11-26
Hmm ... do we all use the same benchmark? Just to get sure. I used the one from the scenes/advanced and ran

povray benchmark.ini

That gave me 36 minutes (and I have an athlon 64, too - yet running 32bit linux)

---

### Post by hcker2000 on 2005-11-26
Yea it should be in the advanced foulder and its the benchmark file.

Was your test at around 2ghz? I also left a few things open like firefox and my instant messenger.

---

### Post by ember on 2005-11-26
Yes, it was - the 2800+ has 1,8 GHz - there was QuodLibet open in the background but not playing.

---

### Post by poptones on 2005-11-26
Just for kicks I tried that benchmark on my xp1800... and it killed it almost five minutes in. Had to reboot the damn pc.

Yes... indeed it is time for an upgrade.

---

### Post by hcker2000 on 2005-11-26
lol sounds like its time for you to upgrade. :D

---

### Post by poptones on 2005-11-26
Ayup, I ran it again and the same thing happened at almost exactly the same point.

It seems a bit strange a hardware fault could cause it to lock up at the same point in the test each time.  If I should feel ambitious I think I might compile it myself and see whazzup.

---

### Post by mstlyevil on 2005-11-26
[QUOTE=hcker2000]That is an option if any one can site the difference from going from socket A to 939 then that would help.[/QUOTE]

  The biggest difference between a 939 and a 754 socket is the memory controler is built into the motherboard on a 754 and the 939 has the memory controller built on to the cpu eliminating the front side bus bottlekneck. The performance difference is drastic because the cpu no longer has to wait for information from the memory because it is now directly linked to it in the 939 socket. The few extra dollars you spend on a 939 system are well worth the upgrade. Also you should consider a 6600 gt 128mb over a regular 6600 with 256 mb. There is a substantial difference in performance between the 2 cards. I can get a 6600 gt here in OKC for $139.00 so you probally could find it for about the same price online.

---

### Post by mstlyevil on 2005-11-26
[QUOTE=psoleko]The Socket 754 CPUs do not contain a dual channel memory controller, whereas the the socket 939 (hence the extra pins) do. This provides more bandwidth for the CPU to access memory which will generally improve performance in applications such as games, media creation, encoding. You are better off spending a little bit more for 939 and do remember you need to buy memory in pairs. Also, make sure you go for an nvidia chipset, my experience with nvidia hardware under Linux has been amazing to say the least. Absolutley zero problems with hardware detection.[/QUOTE]
 
 Sorry didn't see this post before. Basically the same thing I said earlier.

---

### Post by hcker2000 on 2005-11-27
I'm going with the 256 because thats what I have now and I have found this card faster than the 128 equivalents in new games because of the added memory.

I can get 939 for a few bucks more so thats the way I think that im headed.

---

### Post by hcker2000 on 2005-11-30
Ok a bump for some more specs to compare to.

---

### Post by hcker2000 on 2005-12-04
Just got every thing back set up agine. My amd 2400+ at 2.18ghz (190fsb) will do the pov ray bench mark at defult settings in 14 minuets flat.

Big difference from my laptop. My friend just bought a 2800+ and is at its default clock speed of 2.083ghz (166fsb) and dispite the fact that his has more L2 cach mine still dose the render 1 minute 34 seconds faster.

Ok if any of you A64 users out there can beat 14 minutes flat on a 32 bit os let hear it and list your specs.

---

### Post by Shifty Powers on 2005-12-04
Well this is what happened hwne i ran it on my system.

I've got a amd 3500+ venice core
ASRock dual sata-II (brand new uli m1695 chipset)
1 gig ddr 400 ram in dual channel
fx5900 with 2656mb ram

hmm... seems a bit slow compared to your score,, or have i done something wrong?

```
shiftypowers@FosterFamilyZoo:~/Desktop/povray-3.6/scenes/advanced$ sudo povray bencgmark.ini
povray: cannot open the user configuration file /home/shiftypowers/.povray/3.6/povray.conf: No such file or directory
Could not find file 'bencgmark.ini'
Cannot open INI file 'bencgmark.ini'.
Cannot process command-line due to a parse error.
This is not a valid command-line. Check the command-line for syntax errors, correct them, and try again!
Valid command-line switches are explained in detail in the reference part of the documentation.
To get a short list of command-line switches, use either the '-h', '-?', '-help' or '--help' switch.
Failed to render file due to error(s)!
shiftypowers@FosterFamilyZoo:~/Desktop/povray-3.6/scenes/advanced$ sudo povray benchmark.ini
povray: cannot open the user configuration file /home/shiftypowers/.povray/3.6/povray.conf: No such file or directory
Persistence of Vision(tm) Ray Tracer Version 3.6.1 (g++ 3.4.1 @
 i686-pc-linux-gnu)
This is an official version prepared by the POV-Ray Team. See the
 documentation on how to contact the authors or visit us on the
 internet at http://www.povray.org/.
POV-Ray is based on DKBTrace 2.12 by David K. Buck & Aaron A. Collins
Copyright 1991-2003 Persistence of Vision Team
Copyright 2003-2004 Persistence of Vision Raytracer Pty. Ltd.

Primary POV-Ray 3.5/3.6 Developers: (Alphabetically)
  Chris Cason         Thorsten Froehlich  Nathan Kopp         Ron Parker

Contributing Authors: (Alphabetically)
  Steve Anger         Eric Barish         Dieter Bayer        Steve A. Bennett
  David K. Buck       Nicolas Calimet     Aaron A. Collins    Chris Dailey
  Steve Demlow        Andreas Dilger      Alexander Enzmann   Dan Farmer
  Mark Gordon         Christoph Hormann   Mike Hough          Chris Huff
  Kari Kivisalo       Lutz Kretzschmar    Jochen Lippert      Pascal Massimino
  Jim McElhiney       Douglas Muir        Juha Nieminen       Bill Pulver
  Eduard Schwan       Wlodzimierz Skiba   Robert Skinner      Yvo Smellenbergh
  Zsolt Szalavari     Scott Taylor        Massimo Valentini   Timothy Wegner
  Drew Wells          Chris Young

Other contributors are listed in the documentation.

Support libraries used by POV-Ray:
  ZLib 1.2.1, Copyright 1995-1998 Jean-loup Gailly and Mark Adler
  LibPNG 1.2.5, Copyright 1998-2002 Glenn Randers-Pehrson
  LibJPEG 6b, Copyright 1998 Thomas G. Lane
  LibTIFF 3.6.1, Copyright 1988-1997 Sam Leffler, 1991-1997 SGI
Redirecting Options
  All Streams to console..........On
  Debug Stream to console.........On
  Fatal Stream to console.........On
  Render Stream to console........On
  Statistics Stream to console....On
  Warning Stream to console.......On
Parsing Options
  Input file: benchmark.pov (compatible to version 3.50)
  Remove bounds........On
  Split unions.........Off
  Library paths:
    /usr/local/share/povray-3.6
    /usr/local/share/povray-3.6/ini
    /usr/local/share/povray-3.6/include
Output Options
  Image resolution 384 by 384 (rows 1 to 384, columns 1 to 384).
  Graphic display......Off
  Mosaic preview.......Off
  CPU usage histogram..Off
  Continued trace......Off
Tracing Options
  Quality:  9
  Bounding boxes.......On   Bounding threshold: 3
  Light Buffer.........On
  Vista Buffer.........On   Draw Vista Buffer....Off
  Antialiasing.........On  (Method 1, Threshold 0.300, Depth 3, Jitter 1.00)
  Clock value:    0.000  (Animation off)

  0:00:02 Parsing 310K tokens


 Building mesh2:
   - vertex_vectors
   - normal_vectors
  0:00:03 Parsing 1445K tokens
   - uv_vectors
   - face_indices

  0:00:03 Creating bounding slabs
  0:00:03 Creating vista buffer
  0:00:03 Creating light buffers 2299K tokens
Scene Statistics
  Finite objects:          171
  Infinite objects:          3
  Light sources:             2
  Total:                   176

  0:00:42 Building Photon Maps Photons 55440 (sampling 1x1)
  0:00:42 Sorting photons 55439 of 55440
  0:31:57 Rendering line 384 of 384, 53306 supersamples
  0:32:00 Done Tracing
Render Statistics
Image Resolution 384 x 384
----------------------------------------------------------------------------
Pixels:           147840   Samples:          575680   Smpls/Pxl: 3.89
Rays:            1846630   Saved:             18738   Max Level: 12/12
----------------------------------------------------------------------------
Ray->Shape Intersection          Tests       Succeeded  Percentage
----------------------------------------------------------------------------
Box                           79436382         9481595     11.94
Cone/Cylinder                 78064700         6655191      8.53
CSG Intersection             169784243        58832163     34.65
CSG Merge                       822497           35181      4.28
Fractal                        1858962          105642      5.68
Height Field                   3572091          103296      2.89
Height Field Box               3572091          689172     19.29
Height Field Triangle          3262615          106510      3.26
Height Field Block             5692357         1673045     29.39
Height Field Cell             22403989         1790003      7.99
Isosurface                    11962129          729246      6.10
Isosurface Container          12479608        11962660     95.86
Isosurface Cache                137117           43508     31.73
Mesh                          15346240           64463      0.42
Plane                         92236685         1287698      1.40
Sphere                       281534261       175812938     62.45
Superellipsoid                  531632           42873      8.06
Torus                          2958183          420998     14.23
Torus Bound                    2958183          485549     16.41
True Type Font                  791844           80280     10.14
Clipping Object                2575957         1528372     59.33
Bounding Box                 521916858       149343487     28.61
Vista Buffer                  22489691        12940773     57.54
----------------------------------------------------------------------------
Isosurface roots:          11956910
Function VM calls:        172506979
----------------------------------------------------------------------------
Roots tested:                485549   eliminated:               277080
Calls to Noise:          4833747161   Calls to DNoise:      2619431418
----------------------------------------------------------------------------
Media Intervals:           39685635   Media Samples:         358022729 (9.02)
Shadow Ray Tests:         128832003   Succeeded:              52521678
Reflected Rays:              216108
Refracted Rays:              136462
Transmitted Rays:            622280
----------------------------------------------------------------------------
Number of photons shot:           74025
Surface photons stored:           55440
Priority queue insert:          1378843
Priority queue remove:           132615
Gather function called:          673257
----------------------------------------------------------------------------
Smallest Alloc:                   9 bytes
Largest  Alloc:             1440008 bytes
Peak memory used:           5508931 bytes
Total Scene Processing Times
  Parse Time:    0 hours  0 minutes  3 seconds (3 seconds)
  Photon Time:   0 hours  0 minutes 42 seconds (42 seconds)
  Render Time:   0 hours 32 minutes  0 seconds (1920 seconds)
  Total Time:    0 hours 32 minutes 45 seconds (1965 seconds)

```

---

### Post by hcker2000 on 2005-12-05
Can you let us know what resolution the final image came out to? It also looks like you had AA turned on which I didn't so you will want to try it with no AA.

Test renders I did were at 512x384 with no AA.

---

### Post by Shifty Powers on 2005-12-05
Yeah ive got AA turned on in my nvidia settings so that i force Day Of Defeat source to use them when i run it through Cedega. I belive that the final image came out as 384*384.

Will run the benchmark again in a mo and put the results on again as soon as i can.

---

### Post by hcker2000 on 2005-12-05
The AA in your nvidia settings shouldent matter when rendering. You just need to make sure to turn the AA off in pov ray and make sure the image size is the same.

If there is a gui for the linux pov ray use that and there should be a drop down box with the resolution I said and no AA and give it a render.

---

