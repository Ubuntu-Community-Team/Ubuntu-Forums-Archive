---
title: "Webcam and video support - what's needed for Linux?"
date: 2008-02-07
forum: The Cafe
---

### Post by Yfrwlf on 2008-02-07
Video4Linux seems like an often used "video stack" for web cams, video capture cards, and other things.  Yet, web cam support in Linux is still pretty rocky at best.  My question is does Linux need a new "video stack" that makes it easier to implement things for video software like web cam viewers/recorders, video editors, etc, or is what is really needed here more software, or is it both?  Couldn't find any other threads discussing this really so I thought I'd make one, maybe I'm blind. :)

---

### Post by bufsabre666 on 2008-02-07
i like cheese thats under the add/remove, it can take pics and videos and it has nice effects, but linux webcam support needs to improve, ive never had a problem however, so maybe logitech ((The only brand ive ever bought)) isnt that bad, ive had 3 differnt cams work

---

### Post by Yfrwlf on 2008-02-08
> **bufsabre666 said:**
> i like cheese thats under the add/remove, it can take pics and videos and it has nice effects, but linux webcam support needs to improve, ive never had a problem however, so maybe logitech ((The only brand ive ever bought)) isnt that bad, ive had 3 differnt cams work

Wow that's great, perhaps this problem isn't as bad as I thought.  I have heard developers mention that things like web cam support was difficult to implement, and also that the drivers were also difficult to create for Linux, but perhaps neither are true!  Sure hope so.

Perhaps it's even less of an issue now that we have [Skype 2]("http://www.skype.com/intl/en/download/skype/linux/beta/") for Linux, even though it's not open sourced right now.  I wonder how difficult it was for Skype to implement this.

Oh, and of course lets not forget Ekiga. :)

OK so maybe I'm totally wrong and it's a great system, I was really hoping someone could be enlightening but maybe this is all the proof I need. >.<

---

### Post by LaRoza on 2008-02-08
I have great support for my webcam, out of the box and perfect. 

(Logitech Quickcam Chat)

---

### Post by OffHand on 2008-02-08
My Philips ToUcam Fun II PCVC730K works out of the box (about 7 years old though)

---

### Post by Yfrwlf on 2008-02-08
> **LaRoza said:**
> I have great support for my webcam, out of the box and perfect. 

(Logitech Quickcam Chat)

> **OffHand said:**
> My Philips ToUcam Fun II PCVC730K works out of the box (about 7 years old though)

Wow, I really believed things were much more abysmal, I had a heck of a time getting my web cams working and I even heard that the Asus EEE laptop had a built-in web cam but didn't even support it with drivers or something.  I guess I was led astray!  It's certainly an important area for a lot of users, so perhaps what we need is simply more applications to take advantage of it, though there are several that do so far it seems.

Awesome. :)

---

### Post by Kingsley on 2008-02-08
It took a bit of CLI configuration to make my laptop's built-in webcam work.

---

### Post by Yfrwlf on 2008-02-09
> **Kingsley said:**
> It took a bit of CLI configuration to make my laptop's built-in webcam work.

Hmm, well at least you got it working.

A problem I see is that each program has it's own problems with webcams sometimes, they seem to all directly read and interpret video inputs the way they want to from V4L and this might be fine, if they just got it right, but it seems like they often have difficulty.  For example, Ekiga can't display my web cam at all no matter what I set it to, while Skype can.  Why the difference?  Seems like it might be nice to have the desktop have a video configuration tool so that you can adjust things like brightness or whatnot there, and then each program can also modify the setting or have program-specific settings, etc.

If you made a "video capture stack" that was "as powerful" as say Pulse Audio, you could have powerful tools to change your settings without forcing a program to have all the options itself.  For example Ekiga allows some graphics settings for the video device, while Skype does not currently.

Why not make it easier for the software developers by making a more powerful system that has an easy-to-implement API that still gives them all the power they want without making them re-invent the wheel every time they want to make a video program for Linux?

Maybe I'm wrong, maybe V4L1/2 can do everything users and developers could really want, but so far from what I've seen implemented in various video capture programs, I'd guess not, I'd guess that things might be a lot nicer if there was a better subsystem and/or API, perhaps a higher-level one for ease of implementation.

I've never tried to develop one myself, so I don't know and maybe these programs just all suck, but maybe it's the API/subsystem instead that could use some improvements to make things easier on everyone else.

If there is a problem here and everyone wants to see more programs for Linux, it's addressing issues like these that are really important.  You have to have a functional/powerful/robust/scalable "framework" (or system of APIs, etc, whatever) to make Linux a "platform" so it can be developed for more successfully, not to mention users finally actually being able to share programs regardless of their distro of choice.

---

### Post by blueturtl on 2008-02-09
Well one thing you need to consider is that USB web cams are tough cookies for Linux because every manufacturer has implemented their own approach. Why there is no standard for video through USB is that USB was not designed for high bandwidth transfers. It was designed for peripherals such as mice, keyboards and printers. If there was a standard we'd have no trouble with web cams. FireWire web cams have a standard for video transfer and because of that have superior functionality on all platforms.

AFAIK FireWire web cams do not even require device spesific drivers on Linux!

---

### Post by Yfrwlf on 2008-02-09
> **blueturtl said:**
> Well one thing you need to consider is that USB web cams are tough cookies for Linux because every manufacturer has implemented their own approach. Why there is no standard for video through USB is that USB was not designed for high bandwidth transfers. It was designed for peripherals such as mice, keyboards and printers. If there was a standard we'd have no trouble with web cams. FireWire web cams have a standard for video transfer and because of that have superior functionality on all platforms.

AFAIK FireWire web cams do not even require device spesific drivers on Linux!

Wow, very interesting, I didn't know Firewire had such a "high-level" standard implemented, that is indeed quite convenient.  However, it is kind of strange...make that really strange, IMO, to make a connector standard also be a file transfer standard, etc.  Lumping standards all into the same unit seems like locking things in a bit, however if they can be used with other connectors like USB that would be nice.  I just don't think there is a reason to lump a file transfer protocol for example in with a connector/wire standard among other things, and just because USB is slower doesn't mean that the protocol has to be different.  I'm just speculating but I wouldn't be surprised if Apple lumped all these standards together to try to sell the entire "package" and collect royalties, or is firewire an open standard?

Regardless, I agree that devices could definitely benefit from using an open standard for full device communication so that you wouldn't need drivers.  I see no reason why such a standard couldn't exist and provide similar data transfer standards as firewire, but to be able to do it over any "port" that they desire, including network, etc.  Now *that* would be a truly robust standard, and perhaps one exists.

Going back to the problem though, V4L should be able to access the device based on the driver and what protocol it detects it needs to use to correctly pull the data from it and communicate with it (and manufacturers should use more standards), that way any programs wishing to interface with V4L would do so correctly.  To me this doesn't seem to be the case, as like I've stated different programs get different results from video devices.  That seems way too "low-level" to me.  While you should of course retain all the power for interfacing with a video device that you can and in that sense stay "low-level", you should provide a basic, solid, but scalable API for interfacing with V4L so that the program doesn't have to do the work of detecting the video device, but can still manipulate it as much as it needs to.

Quite simply, perhaps V4L is outdated, and needs replacing or updating?

Cheers. :)

---

### Post by blueturtl on 2008-02-09
> Wow, very interesting, I didn't know Firewire had such a "high-level" standard implemented, that is indeed quite convenient.

> I'm just speculating but I wouldn't be surprised if Apple lumped all these standards together to try to sell the entire "package" and collect royalties, or is firewire an open standard?

Apparently there is a standard called the "IIDC specification" which most FireWire video devices adhere to. This voluntary spesification eliminates the need for device spesific drivers. As long as the spesification is public the devices can be supported under any OS (I'm under the impression it is). They could have done the same for USB, but since USB at the time of it's release was (and still is in some ways) a poor solution to desktop video Intel never came up with a protocol for that purpose.

I'm pretty sure Apple came up FireWire  because they market Macs as a viable video editing platform. Intel could have designed a competing standard for PCs but apparently they didn't see the need to and thus other manufactures started using USB for video (seeing as it was the only viable alternative due to it's market spread).

On a more cynical note, I'm sure Microsoft prefers it this way because they get all the third party support and the lack of a common standard will long be a chink in interoperability and device compatibility between different x86 operating systems.

Not meaning to derail your thread, I'm just pointing out that problems with Video4Linux are probably much related to trying to tie in all sorts of different devices and protocols, many of them unsolvable until we either get a standard or the schematics for all the different web cams out there.

---

### Post by herbster on 2008-02-09
I just got a Logitech Quickcam 9000 Pro, great cam but I have noticed that no matter the webcam, they all have brutal framerates in linux compared to what one can do with the Logi software in Windows, for example.

I figure my best option for getting quality video clips onto my comp is just using my handheld video camera and pluggin' 'er in via firewire.

---

### Post by Yfrwlf on 2008-02-11
> **blueturtl said:**
> Apparently there is a standard called the "IIDC specification" which most FireWire video devices adhere to. This voluntary spesification eliminates the need for device spesific drivers. As long as the spesification is public the devices can be supported under any OS (I'm under the impression it is). They could have done the same for USB, but since USB at the time of it's release was (and still is in some ways) a poor solution to desktop video Intel never came up with a protocol for that purpose.

I'm pretty sure Apple came up FireWire  because they market Macs as a viable video editing platform. Intel could have designed a competing standard for PCs but apparently they didn't see the need to and thus other manufactures started using USB for video (seeing as it was the only viable alternative due to it's market spread).

On a more cynical note, I'm sure Microsoft prefers it this way because they get all the third party support and the lack of a common standard will long be a chink in interoperability and device compatibility between different x86 operating systems.

Not meaning to derail your thread, I'm just pointing out that problems with Video4Linux are probably much related to trying to tie in all sorts of different devices and protocols, many of them unsolvable until we either get a standard or the schematics for all the different web cams out there.

So as long as Firewire isn't a standard that is tied down or proprietary in any way, perhaps it should be promoted as the ideal solution for video devices of any kind as it is the most "free" and non-restrictive.  You're very correct though about Microsoft, don't downplay yourself, they love things like that and try to do it in any area they can as they see it as "fair" business practice.  It's not just Microsoft though of course, but with software they are certainly a big offender.

About V4L, you may be completely right and I appreciate your input.  In no way did I mean to portray that I know what I'm talking about, I just wanted to hear the opinions of where the problem may stem from because I really don't know, other than typical problems with there not being as many drivers in Linux.  Perhaps V4L, and maybe specifically V4L2 is a good system as it is.

One thing I was curious though is if, similar to the Firewire standard, V4L had a similar standardized language that was easy to interface with so that programs could interface with video devices easily.  Perhaps there could also be an easier way for programs to render video in Linux, too.  I guess I was mainly just trying to figure out why Gaim hadn't adopted it, but maybe the programmers are just totally uninterested instead of it being "too difficult", but there is a general lack of video editing/capturing programs for Linux, so it wasn't just that fact that made me suspicious.  Guess I will have to explore V4L to find out what it can do and to find it out if there is some kind of standard Linux API for it.  I really really wish there were standard APIs for most everything in Linux so that everything could be completely modular.  Aah, the ideal world. :)

> **herbster said:**
> I just got a Logitech Quickcam 9000 Pro, great cam but I have noticed that no matter the webcam, they all have brutal framerates in linux compared to what one can do with the Logi software in Windows, for example.

I figure my best option for getting quality video clips onto my comp is just using my handheld video camera and pluggin' 'er in via firewire.

But you can't stream live feed that way, just copy the files from the camera, right?  I've been looking for a good quality web cam that Linux supports, and if the Logitech ones don't cut it then I'm off searching for another brand I guess.

Was disappointing, the two web cams on New Egg that explicitly state they are supported by Linux (a rare thing indeed for anything to say that) unfortunately have bad reviews for their Linux compatibility.  [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=web+cam+Linux&x=0&y=0](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=web+cam+Linux&x=0&y=0)

---

### Post by herbster on 2008-02-11
Nope, can't stream of course, just a normal camera.

And "works" in linux is different than "works" in Windows with the webcams. Logitech works just fine, google uvc driver and you'll find a list of cams that work out the box with the standard driver, like mine did. However, with every camera pretty much getting the same crappy FPS/quality, you'd be fine buying a $20 Quickcam and using another video camera to actually make clips, if that's of interest (is to me).

---

### Post by blueturtl on 2008-02-11
> I've been looking for a good quality web cam that Linux supports

For FireWire I've read that this is a good choice:
[http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm](http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm)

For USB I guess I can only refer you to the list of supported devices:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by Yfrwlf on 2008-02-14
> **herbster said:**
> However, with every camera pretty much getting the same crappy FPS/quality, you'd be fine buying a $20 Quickcam and using another video camera to actually make clips, if that's of interest (is to me).

Perhaps you should look into other brands of cameras then, there has to be some out there for Linux that don't suck, maybe peruse some of these that blueturtl mentioned [http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm](http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm)

> **blueturtl said:**
> For FireWire I've read that this is a good choice:
[http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm](http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm)

For USB I guess I can only refer you to the list of supported devices:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

That cam is pretty pricey but they do actually say they support Linux which is nice.  The resolution isn't the greatest now days, and the software to control the camera in "special ways" is Windows-only.  I may get it though, but I'm sure there are some other good quality cams out there for Linux too. :)

Thanks a bunch for all the links and info.

---

### Post by EmilyRose on 2008-02-14
We need software so that we can chat with AIM/iChat users on video chat. If I could do that, I would be thrilled. My mom, my aunt, my grandparents all have macs and I really, really wish I could video chat with them, but I can't cause' theres no AIM  video support in linux!! There is in Windows. But none in Linux. WHY not???

---

### Post by LaRoza on 2008-02-14
> **EmilyRose said:**
> We need software so that we can chat with AIM/iChat users on video chat. If I could do that, I would be thrilled. My mom, my aunt, my grandparents all have macs and I really, really wish I could video chat with them, but I can't cause' theres no AIM  video support in linux!! There is in Windows. But none in Linux. WHY not???

Simple, Linux didn't write AIM and doesn't control it.

I use my webcam with Yahoo fine, perhaps you can all use that instead.

(The AOL web mail doesn't work outside of IE and AOL's browser, so don't expect them to make their chat software work on a different operating system)

---

### Post by no2498 on 2010-01-23
try pidgin for the last guy

fastest way to see if you can use your cam is
open a terminal type ( gstreamer-properties )click enter
click video try v4l1 or v4l2

now get a program to use it with
cheese wxcam xawtv ,is a lot more than that

---

