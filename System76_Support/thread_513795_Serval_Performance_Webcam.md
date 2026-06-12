---
title: "Serval Performance Webcam?"
date: 2007-07-30
forum: System76 Support
---

### Post by steveneddy on 2007-07-30
I was just curious how the webcam development for the Serval Performance lappie is coming?

The Serval that I purchased this year has a lot of road miles on it already and I would now like to have the built in web cam operational for after hours communication with friends and family while on the road.

BTW, the Serval has given me perfect performance since the first day it arrived and it is the envy of all around me. 

Thanks for a great product.

-SE

---

### Post by thomasaaron on 2007-07-31
We've still not been able to get the web cam working.

We've made some progress in our know-how in this area with the new Darter. But it doesn't translate exactly to the old Serval.

---

### Post by steveneddy on 2007-10-18
I am curious, with the new Gutsy and new /sys76 driver, if there will ever be webcam support on my Serval Performance version 1?

Maybe you guys know of a web cam that works out of the box and actually has a good picture?

I have Gutsy 64 bit installed and the System76 driver 2.1

:popcorn:

---

### Post by thomasaaron on 2007-10-18
We've stil not been able to get the old Serval's web cam to work.
We've tested a number of drivers, but no joy. Still some more to go though.

---

### Post by crichell on 2007-10-18
> **steveneddy said:**
> I am curious, with the new Gutsy and new /sys76 driver, if there will ever be webcam support on my Serval Performance version 1?

Maybe you guys know of a web cam that works out of the box and actually has a good picture?

I have Gutsy 64 bit installed and the System76 driver 2.1

:popcorn:

I've had this on my back burner for too long :-).  We'll work on it today and post back.

---

### Post by steveneddy on 2007-10-18
> **crichell said:**
> I've had this on my back burner for too long :-).  We'll work on it today and post back.

Thank you, Carl and Thomas. I really appreciate the swift response.

Does the new Serval Performance have working web cam?

Maybe I just need to buy a new one?

:D

---

### Post by crichell on 2007-10-18
How about something cool but useless.  The fingerprint reader is now supported; however, it is not yet integrated into PAM or login.

To view your fingerprint (Gutsy Only):

```
sudo apt-get install aes2501-wy
```

Open up your home folder and a terminal.  From your terminal:

```
aes2501
```

Scan your finger and watch the image pop up in your home folder.  Anyone interested in creating a GTK wrapper?

---

### Post by palintheus on 2007-10-18
> **crichell said:**
> How about something cool but useless.  The fingerprint reader is now supported; however, it is not yet integrated into PAM or login.

To view your fingerprint (Gutsy Only):

```
sudo apt-get install aes2501-wy
```

Open up your home folder and a terminal.  From your terminal:

```
aes2501
```

Scan your finger and watch the image pop up in your home folder.  Anyone interested in creating a GTK wrapper?

Will this work on the daru2?

---

### Post by crichell on 2007-10-18
> **palintheus said:**
> Will this work on the daru2?

This one won't work on the Darter; however, I have a driver for it too.  I have had trouble compiling the driver - and have to find it again.  I'll post once I find it and you guys can try your hand.

---

### Post by crichell on 2007-10-18
> **palintheus said:**
> Will this work on the daru2?

To try to keep this thread to the "classic" Serval I created a new post for the Darter fingerprint reader: [http://ubuntuforums.org/showthread.php?t=580027](http://ubuntuforums.org/showthread.php?t=580027)

---

### Post by steveneddy on 2007-10-18
> **crichell said:**
> 
Scan your finger and watch the image pop up in your home folder. 

Cool - now what do I do with this?

When you get this running, let me know.

It does seem to work, though.

:popcorn:

---

### Post by crichell on 2007-10-18
> Cool - now what do I do with this?

exactly - not very useful yet - but a step forward now with driver support.  still working on webcam.

---

### Post by steveneddy on 2007-10-18
I was looking at the new Serval Performance. That thing is **SWEET!**

4 GIG Ram - Faster FSB - better video card - sweet monitor

You just ruined my life, Carl. Do you realize how many PB & J sandwiches I am gonna have to eat so I can ethically afford one by Christmas?

That thing is a powerhouse! The last time I looked at Dell, they didn't have anything close. If you want hardware power, System76 is the place to go.

I even think I can get one a little cheaper that the Serval Performance that I bought this year.

We're gonna have to work out a deal on this one, Carl. 

I've gotta have one now. 

What's a GTK wrapper and how do I make one? I'll try anything to get a new Serval Performance. 

BTW - Gutsy is doing well on this **old** lappie. SD card reader works very well, all hardware was detected, except the camera, the system has been the most reliable PC I have ever owned besides my server. I thought I was going to wait a few years to get another, but not now. The new Serval kicks butt!

Thanks for all the hard work, fellas. Speaking for the customers and myself, you guys do a bang up job and we couldn't ask for more, besides a free Serval to help promote Linux/Ubuntu/System76.

Hello? Where'd they go?

:D

---

### Post by crichell on 2007-10-18
> Do you realize how many PB & J sandwiches I am gonna have to eat so I can ethically afford one by Christmas?

don't forget to throw in some Cup O' Noodles for variety :-).  ahh the college years.

---

### Post by thomasaaron on 2007-10-19
You can also get cheap bologna. It fries up real nice. Just like a steak!

---

### Post by steveneddy on 2007-10-19
**fried **bologna?

:shock:

---

### Post by palintheus on 2007-10-19
> **steveneddy said:**
> **fried **bologna?

:shock:

strange yes, but to my wife's family its like a delicacy.

---

### Post by 982000971 on 2008-01-19
I'm glad you guys have a sense of humor about this. I however have lost my patience. I have waited well over a year since I purchased my Serval Performance, and back then I was being told webcam support was just around the corner. I can't help but feel mislead.

Will you or will you not get webcams working on the Serval Performance?

I have good experiences with System76, but this whole webcam thing leaves a sour taste in my mouth.

---

### Post by steveneddy on 2008-01-20
> **982000971 said:**
> I'm glad you guys have a sense of humor about this. I however have lost my patience. I have waited well over a year since I purchased my Serval Performance, and back then I was being told webcam support was just around the corner. I can't help but feel mislead.

Will you or will you not get webcams working on the Serval Performance?

I have good experiences with System76, but this whole webcam thing leaves a sour taste in my mouth.

It wasn't advertised at the time, so if I ever get it going it would be a blessing.

The fact that they will eventually get the webcam working in this laptop is a testament to the open sourced movement.

I would think that if it was an advertised feature and it didn't work, I would be disappointed also. I just don't ever remember the webcam being advertised on this version of the Serval Performance.

:popcorn:

---

### Post by 982000971 on 2008-01-20
Carl / Fri Jul 28, 2006 8:14 pm
"We have a driver for the camera in development..."

thomasarron / Tue Jun 26, 2007 2:18 pm
"Our goal is to get the camera and fingerprint readers on both computers functional by the release date..." [JUL 26th]

thomasarron / Mon Sep 10, 2007 8:16 pm
"...We're shooting for late October / early November..."

[http://system76.com/product_info.php?cPath=28&products_id=51](http://system76.com/product_info.php?cPath=28&products_id=51)
Why say "Camera: Built-In Webcam" if it doesn't even work? Shouldn't you warn your customers? I know I wasn't warned when I bought mine over a year ago.

I hate to be that angry message board guy, but this is ridiculous. I've been teased into thinking the webcam would be up and running since before I made my purchase. At least come out and say "We have no freaking clue how to make it work or if it ever will". But it just seems like everyone keeps saying "It's just around the corner" ... Well it's obviously not, it's been forever. Just a little more honesty about whats taking place would be appreciated. I feel completely justified in being as upset as I am.

So I ask the guys from System76 once again, Will you or will you not get webcams working on the Serval Performance?

---

### Post by compholio on 2008-01-20
> **982000971 said:**
> ...
[http://system76.com/product_info.php?cPath=28&products_id=51](http://system76.com/product_info.php?cPath=28&products_id=51)
Why say "Camera: Built-In Webcam" if it doesn't even work? Shouldn't you warn your customers? I know I wasn't warned when I bought mine over a year ago.
...

That is the SERP3 advertised there, which I purchased and the webcam performs beautifully.  An example of something not advertised on mine is the fingerprint reader.  While I would be excited to have it work, I completely recognize that it is not advertised as a feature of the laptop and therefore will not get upset if it does not become supported.

---

### Post by 982000971 on 2008-01-20
Touche! That is not my laptop, my Serval is older. But the built-in webcam thing was on mine when I clicked purchase. It was implied. They should have had big bold letters saying, "WEB CAM NOT SUPPORTED". I mean if you buy a new car that says moon roof included don't you expect it to work?

---

### Post by asmiller-ke6seh on 2008-01-22
Getting this webcam to work, as far as I can tell, is waiting on a hardware driver for the Chinese built chip that is, somewheat uniquely, contained in the webcam of the Serval Performance. So, either System76 is going to write the driver for the Open Source community, or we have to wait for someone else (maybe someone who writes video drivers for Linux who also happen to own a Serval Performance and is impatient to wait for System 76 or some other group or person to write the driver) to write the driver.

Does anyone know if there may be source code for a Webcam device driver that is being actively researched and written for this internal webcam? I certainly don't know if, or when, or even where?

---

### Post by steveneddy on 2008-02-05
Just kicking a dead horse around.

Any new news?

---

### Post by Vadi on 2008-02-09
?

Using my serval that came in yesterday, I just installed the "cheese" program, and it takes video & pics just fine.

---

### Post by asmiller-ke6seh on 2008-02-11
> **Vadi said:**
> ?

Using my serval that came in yesterday, I just installed the "cheese" program, and it takes video & pics just fine.

You probably have the latest SERP3 - which, as I remember reading, has a (different) supported webcam, unlike the earlier SERval Perfomances.

I sure thomasaaron will weigh in if I am incorrent.

---

### Post by Vadi on 2008-02-11
Yeah, it does say serp3 in the drivers thing.

That's unfortunate then. But I'm *really* hoping the fingerprint reader will work - I'm getting tired of typing my password for sudo knowing that I could be able to just swipe my finger :(

---

### Post by asmiller-ke6seh on 2008-02-11
> **Vadi said:**
> ----%<---CLIP------
But I'm *really* hoping the fingerprint reader will work - I'm getting tired of typing my password for sudo knowing that I could be able to just swipe my finger :(

It is being actively worked on. I know that the actual fingerprint scanning device currently works on the SERP family -- what is needed is the APP that supports and controls the ID/Security functions, but that project is moving along well. There is not ETA for delivery, but it will happen.

Until then ... don't worry - be happy :)

---

### Post by Vadi on 2008-02-11
Have a link? I'd gladly donate some to encourage things.

---

### Post by asmiller-ke6seh on 2008-02-12
> **Vadi said:**
> Have a link? I'd gladly donate some to encourage things.

I found this link by doing a Websearch for "gnome fingerprint":

[http://www.novell.com/coolsolutions/feature/20020.html](http://www.novell.com/coolsolutions/feature/20020.html)

At the bottom of that page, I found this link:

[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

I hope this convinces you that work is under way ... and this is just one of the projects that I found.

---

### Post by Vadi on 2008-02-12
I see.. unfortunately there are only 32bit .debs provided atm, so I'll wait a bit,

---

### Post by asmiller-ke6seh on 2008-02-12
> **Vadi said:**
> I see.. unfortunately there are only 32bit .debs provided atm, so I'll wait a bit,

And your point? 32-bit or 64-bit - makes no difference. If it works, it works. It's not like this is a high-bandwidth application; it's only a tiny applet. You say you run 32-bit games in your 64-bit environment. Why is this so different?

---

### Post by Vadi on 2008-02-12
Erm because gdebi refuses to install the 32bit debs :P

---

### Post by asmiller-ke6seh on 2008-02-14
> **Vadi said:**
> Erm because gdebi refuses to install the 32bit debs :P

Why not download and install from the source code?

---

### Post by Vadi on 2008-02-14
If there are clear instructions, then sure. I tried following the Novell ones and the compile failed :/

---

### Post by farruinn on 2008-02-14
This is getting off-topic, but if there is a deb-src repository, installing from source isn't too hard. [www.debian.org](www.debian.org) has some excellent documentation on compiling debian packages from source.

---

### Post by asmiller-ke6seh on 2008-04-08
Eager owners want to know, now that we are on the eve of the release of Hardy...last I heard, that was going to be the release that was going to help enable the internal Webcam on the pre-Serp3 laptops.

Can you provide an update to us?

> **982000971 said:**
> Carl / Fri Jul 28, 2006 8:14 pm
"We have a driver for the camera in development..."

thomasarron / Tue Jun 26, 2007 2:18 pm
"Our goal is to get the camera and fingerprint readers on both computers functional by the release date..." [JUL 26th]

thomasarron / Mon Sep 10, 2007 8:16 pm
"...We're shooting for late October / early November..."

[http://system76.com/product_info.php?cPath=28&products_id=51](http://system76.com/product_info.php?cPath=28&products_id=51)
Why say "Camera: Built-In Webcam" if it doesn't even work? Shouldn't you warn your customers? I know I wasn't warned when I bought mine over a year ago.

I hate to be that angry message board guy, but this is ridiculous. I've been teased into thinking the webcam would be up and running since before I made my purchase. At least come out and say "We have no freaking clue how to make it work or if it ever will". But it just seems like everyone keeps saying "It's just around the corner" ... Well it's obviously not, it's been forever. Just a little more honesty about whats taking place would be appreciated. I feel completely justified in being as upset as I am.

So I ask the guys from System76 once again, Will you or will you not get webcams working on the Serval Performance?

---

### Post by thomasaaron on 2008-04-08
It doesn't work by default in Hardy. However, this is what we are looking into at the moment...

[https://bugs.launchpad.net/ubuntu/+bug/153176](https://bugs.launchpad.net/ubuntu/+bug/153176)
[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

