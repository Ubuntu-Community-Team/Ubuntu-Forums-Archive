---
title: "WHY Brasero? low rating out of 600"
date: 2015-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by thatguymark on 2015-01-26
I was burning an audio CD from a few MP3s and it produced a rapid bleeping, installed and used XFBurn with no problems. In the process I notice there are almost 600 reviews in the Ubuntu Software Center with an average of 2 out of 5 stars for Brasero. I just don't understand why it's included in a release as new as Trusty when there are obviously issues with it, this should be simple and straight forward functionality not to mention other people will have other issues - what gives??

---

### Post by speartip on 2015-01-26
I think Brasero is only as good as it is set up.
The 1st thing I do on a fresh install, is open Brasero, go to edit/plugins, & make sure all the plugins are installed & the boxes are ticked. I then untick "image checksum" & "normalisation".
Once I have done this I find it as good as any burner there is.
 With most people I think the problem is that the correct dependencies aren't installed, not the quality of the program. IMO of course.

---

### Post by Rob Sayer on 2015-01-26
I haven't used software center for so long I forget how it works exactly, for 2 reasons.

It's way too slow.

The user reviews are useless.

---

### Post by Bucky Ball on 2015-01-26
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. Never had issues with Brasero myself. If you would like to know why it is included as the default burner (I'm not sure it is as don't use the regular desktop Ubuntu) then we can't tell you that. Ubuntu devs rarely visit here and the forum community has no control over what is or isn't included as a default app in any release of Ubuntu or its flavours. You might like to approach Canonical directly.

---

### Post by craig10x on 2015-01-26
They key to having an efficient and fast Brasero is really very simple...you click on "edit" on the top and bring up the plug ins window...You uncheck two boxes....the one that says "File Checksum" and the one that says "Image Checksum"...once that is done it will burn a cd or dvd very quickly and do an excellent job of it....Leave those two boxes checked and it will take forever to burn the disc and you would conclude it's a crappy program ;)

Why it has those two enabled by default, i'll never know and it could easily give a bad initial impression...That is probably why there are so many negative reviews on it...

---

### Post by monkeybrain20122 on 2015-01-26
I use k3b

---

### Post by Bucky Ball on 2015-01-26
> **monkeybrain20122 said:**
> I use k3b

Lot of people like that. Only trouble with that is it drags in a ton of stuff and Kubuntu (KDE) things. Have been using XFburn on my current install and that seems to work fine, too.

---

### Post by mastablasta on 2015-01-27
> **craig10x said:**
> They key to having an efficient and fast Brasero is really very simple...you click on "edit" on the top and bring up the plug ins window...You uncheck two boxes....the one that says "File Checksum" and the one that says "Image Checksum"...once that is done it will burn a cd or dvd very quickly and do an excellent job of it....Leave those two boxes checked and it will take forever to burn the disc and you would conclude it's a crappy program ;)

Why it has those two enabled by default, i'll never know and it could easily give a bad initial impression...That is probably why there are so many negative reviews on it...

there is a reason why those two are there. i believe this is default in nero as well. however in nero you can turn it off while it's burning the disk (if i am not mistaking).

---

### Post by kc1di on 2015-01-27
You may also want to try simpleburn or xfburn they both work well as to why brasero is the default , most likely because it GTK based and the default of the Gnome desktop. 
Cheers!

---

### Post by leclerc65 on 2015-01-28
> Lot of people like that. Only trouble with that is it drags in a ton of stuff and Kubuntu (KDE) things.
I don't mind that. 
K3b and kTorrent are my favorites, Brasero and Transmission are not.

---

### Post by craig10x on 2015-01-28
I use to run k3b which is great (no question) but always wanted to be able to use a gnome burner...used XFBurn for a while and it worked quite good, but once i discovered the "secret" to make brasero fast and efficient (uncheck those darn checksum plug ins) it worked so well, i haven't gone back again to k3b...

---

### Post by rrnbtter on 2015-01-29
Greetings,

> **leclerc65 said:**
> I don't mind that. 
K3b and kTorrent are my favorites, Brasero and Transmission are not.

+1

With 4gig of ram and 500 gig of hd whats a few dependencies. 
I used Nero for a few years because both brasero and K3b were fragging too many disks. But a couple of years ago K3b got its act together and Nero started having problems with the big changes in Ubuntu so I made the final leap and went back to K3b. I never thought of ktorrent but after the post above I think I will give it a try. I can't stand the KDE desktop but I love the software.

---

### Post by justingx2 on 2015-01-30
I've always liked Brasero, it's given me no problems compared to K3B... ugh.

---

### Post by leclerc65 on 2015-02-02
> **justingx2 said:**
> I've always liked Brasero, it's given me no problems compared to K3B... ugh.
I have quite a few of spoiled discs because of Brasero, none with k3b or Imgburn (Windows)

---

### Post by speartip on 2015-02-02
> **leclerc65 said:**
> I have quite a few of spoiled discs because of Brasero, none with k3b or Imgburn (Windows)
And yet if you check out what programs they rely on, they're the same.
cdrdao, wodim, genisoimage, transcode, sox, etc... etc...
So it must come down to configuring Brasero or k3b correctly.

---

### Post by Mopar1973Man on 2015-02-05
Speartip has poin there. The dependencies are basically the same. Its just the optional stuff that is different from one to another.

---

