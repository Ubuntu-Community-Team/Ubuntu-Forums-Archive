---
title: "Things I have found about CNR that all users should know"
date: 2008-04-17
forum: The Cafe
---

### Post by Seisen on 2008-04-17
#1 Reason
The fact that it uses SETUID. For anybody who doesn't have any idea what that is here is the definition 

> "setuid and setgid (short for set user ID upon execution and set group ID upon execution, respectively) are Unix access rights flags that allow users to run an executable with the permissions of the executable's owner or group" or essentially root. > While the setuid feature is very useful in many cases, it can pose a security risk if the setuid attribute is assigned to executable programs that are not carefully designed. Users can exploit vulnerabilities in flawed programs to gain permanent elevated privileges, or unintentionally execute a trojan horse program.  
**[http://en.wikipedia.org/wiki/Setuid]("http://en.wikipedia.org/wiki/Setuid")**

So every time you run CNR and add packages to your install or upgrade it guess what CNR runs as root and doesn't ask you for a password, which is very insecure. That means any user on that computer can go into CNR and add or remove packages. At least using apt, synaptic or add/remove programs your prompted for a password.  You know there is a reason why the Ubuntu developers included sudo instead of having a default root user.

Reason #2 
No 64-bit. Many users have complained about the CNR installer not working on there systems for 64-bit. If you go to CNR.com and click on the Ubuntu icon to install the cnr client for Ubuntu version no where it it listed that this is only a 32-bit installer.

Reason #3
Some software listed on cnr.com is outdated including the flash package which is version 9.0.64 which can be exploited.

**[http://www.macnn.com/articles/08/04/10/adobe.fixes.flash.exploit/]("http://www.macnn.com/articles/08/04/10/adobe.fixes.flash.exploit/") **

Now if you check the Ubuntu repositories you see that their package has fixed the very critical exploit. 

Reason #4
Where do you find the codecs? I typed in codecs in the search bar and a whole bunch of things that said codecs popped up. If your a beginner you are not going to have no idea what to install. Also if you use the cnr client it doesn't tell what dependences its pulling when you install a package, so you really don't know what is going on all you get is this box that says it completed. 

Reason #5
When you upgrade from Gutsy to Hardy CNR-client gets removed , so you have go through the whole process over again of installing it. But here is the kicker part after you install the hardy client here is the repository that it was set on (see attachment). So unless you go and check you are never going to know.

---

### Post by madjr on 2008-04-17
interesting findings

i'll stay away from CNR for now.

i don't even think Ubuntu needs it anyway. It's better for other distros with less pre-compiled software

---

### Post by forrestcupp on 2008-04-17
If they actually had some worthwhile things to install that we can't already get, it might be worth it.  But I'm pretty disappointed with their offerings.  I had hopes that they would have more that isn't so easy to obtain.

---

### Post by madsmeg on 2008-04-17
Wow... so many holes so little time, will never use, would not before anyway because i actually dont mind taking the time to install my free software for free...:guitar:

---

### Post by billgoldberg on 2008-04-17
At the risk of sounding stupid, what is CNR?

Some kind of new package manager/application in hardy?

---

### Post by swoll1980 on 2008-04-17
> **billgoldberg said:**
> At the risk of sounding stupid, what is CNR?

Some kind of new package manager/application in hardy?

It's Lin(free)spires package management gizmo. Since they based that crappy distro off Ubuntu it's compatible  with 7.10

---

### Post by The Tronyx on 2008-04-17
Nice post seisen.

> 
So every time you run CNR and add packages to your install or upgrade it guess what CNR runs as root and doesn't ask you for a password, which is very insecure. That means any user on that computer can go into CNR and add or remove packages


Being a security concerned individual, that alone would keep me from using CNR.  Thanks again for the heads up.

---

### Post by madsmeg on 2008-04-17
> what is CNR?

It is:
> CNR.com is a free one-click software delivery service designed to standardize the process and eliminate the complexity of finding, installing and managing Linux software for the most popular desktop Linux distributions, both Debian and RPM based.

Very basically a package manager... which we already have....

---

### Post by compiledkernel on 2008-04-17
CNR.com is a free one-click software delivery service designed to standardize the process and eliminate the complexity of finding, installing and managing Linux software for the most popular desktop Linux distributions. There is a standardized client and web interface to go with the application. 

It pretty much duplicates the efforts that Synaptic and Gnome-App-Install (Add/Remove in your application listing) provide you on a default installation.

---

### Post by billgoldberg on 2008-04-17
> **swoll1980 said:**
> It's Lin(free)spires package management gizmo. Since they based that crappy distro off Ubuntu it's compatible  with 7.10

Thanks for clarifying.

Well since you don't need to put a password to delete or install stuff, it's incredibly unsafe (xp standard admin unsafe).

---

### Post by swoll1980 on 2008-04-17
> **compiledkernel said:**
> CNR.com is a free one-click software delivery service designed to standardize the process and eliminate the complexity of finding, installing and managing Linux software for the most popular desktop Linux distributions. There is a standardized client and web interface to go with the application. 

It pretty much duplicates the efforts that Synaptic and Gnome-App-Install (Add/Remove in your application listing) provide you on a default installation.

Yes the only differences are the pretty pictures and the huge security holes

---

### Post by Saint Angeles on 2008-04-17
so theres virtually no difference between synaptic and CNR (except synaptic is preinstalled and more secure) ?

man i remember last week there was a flood of spammers talking about how cool CNR is.

losers.

---

### Post by The Tronyx on 2008-04-17
> **Saint Angeles said:**
> 

man i remember last week there was a flood of spammers talking about how cool CNR is.

losers.

Kind of off topic but I couldn't help it.  I LOL'ed in class.

---

### Post by compiledkernel on 2008-04-17
> **Saint Angeles said:**
> so theres virtually no difference between synaptic and CNR (except synaptic is preinstalled and more secure) ?

Honestly, SA, No, there isnt.

---

### Post by speeddemon8803 on 2008-04-17
CNR is completely rediculess.....waste of time....synaptic is MUCH better..and in fact...actually..GETDEBI is a hundred percent better than freakin CNR...ive got HUNDREDS of people that can back me up on this one. If you dont agree with the fact that CNR sucks...um.....do me a favor..read my thread on cnr never ever ever going to be supported. Thanks :)

---

### Post by capink on 2008-04-17
I think the only point of enabling cnr for ubuntu is that it provides codecs in a legal way.

---

### Post by swoll1980 on 2008-04-17
> **speeddemon8803 said:**
> CNR is completely rediculess.....waste of time....synaptic is MUCH better..and in fact...actually..GETDEBI is a hundred percent better than freakin CNR...ive got HUNDREDS of people that can back me up on this one. If you dont agree with the fact that CNR sucks...um.....do me a favor..read my thread on cnr never ever ever going to be supported. Thanks :)

+1 for [www.getdeb.net](www.getdeb.net)

---

### Post by saulgoode on 2008-04-17
> **Seisen said:**
> So every time you run CNR and add packages to your install or upgrade it guess what CNR runs as root and doesn't ask you for a password, which is very insecure. That means any user on that computer can go into CNR and add or remove packages. At least using apt, synaptic or add/remove programs your prompted for a password.  You know there is a reason why the Ubuntu developers included sudo instead of having a default root user.

A Linspire forum member named BigDawg did indeed state [(in this thread)]("http://community.cnr.com/message/1029#1029") that "any user can install/unisntall/update software", however, after examining the CNR installation scripts, it would seem that permission to execute CNR is restricted to members belonging to the "admin" group. 

If I understand things correctly, this suggests that not just any user on an Ubuntu machine can use CNR, only those with sudo privileges. This is admittedly more reasonable than letting **all** users modify the system; but does presume that an admin account is used to surf the web (which is not particularly advisable from a security standpoint), and it does mean that there will be no prompting for an admin password.

---

### Post by st33med on 2008-04-17
True, CNR is quite ridiculous. It hasn't been ported to a lot of the distros promised, such as Ubuntu. The fact that microsoft is behind this charade is also very intriguing. They might be only porting to those who succumbed to their patent racket. 

Heck, if I were to compare it to Automatix2, Automatix takes my vote. Though, I would not install either on my machine :D

---

### Post by mrgnash on 2008-04-17
S3indiana should show up anytime now....

---

### Post by compiledkernel on 2008-04-17
> **saulgoode said:**
> A Linspire forum member named BigDawg did indeed state [(in this thread)]("http://community.cnr.com/message/1029#1029") that "any user can install/unisntall/update software", however, after examining the CNR installation scripts, it would seem that permission to execute CNR is restricted to members belonging to the "admin" group. 

If I understand things correctly, this suggests that not just any user on an Ubuntu machine can use CNR, only those with sudo privileges. This is admittedly more reasonable than letting **all** users modify the system; but does presume that an admin account is used to surf the web (which is not particularly advisable from a security standpoint), and it does mean that there will be no prompting for an admin password.

Interesting Point Saulgoode. 

I would have to express in this scenario that still the latter part of your examination is of still great concern.

---

### Post by cardinals_fan on 2008-04-17
> **mrgnash said:**
> S3indiana should show up anytime now....
Yeah, I don't know where he is...

---

### Post by jrusso2 on 2008-04-18
I don't know how you expect security from a company Linspire that its Operating system the user account was the root account and they still defend that

Many of the Linspire users thought nothing was wrong with running as root and still prefer it.

Btw S3Indiana is a paid member of the Linspire staff so he would be defending it.

---

### Post by Midwest-Linux on 2008-04-18
Not to get off the subject, but is Lin/Free spire plan on new versions? Is there going to Freespire 3.0 or Linspire 7.0 ? 

Thanks

---

### Post by gn2 on 2008-04-18
CNR is a total waste of space, lots of discussion of it in this thread: [http://ubuntuforums.org/showthread.php?t=636551](http://ubuntuforums.org/showthread.php?t=636551)

---

### Post by PartisanEntity on 2008-04-18
I still do not understand what CNR's strengths are. As far as I understood it, it's just another repository, but with the hopes of making money through it by offering, in addition to free software, also non-free software. Or did I miss something?

---

### Post by compiledkernel on 2008-04-18
Partisan Entity, the money grab is from offering one click installable proprietary software, once you mill through all the standard duplicated existing repositories, then through the thousands of web apps (flickr, myspace, and the like), youll find a handful of proprietary applications (StarOffice, etc).

---

### Post by LaRoza on 2008-04-18
> **mrgnash said:**
> S3indiana should show up anytime now....

> **cardinals_fan said:**
> Yeah, I don't know where he is...

> **jrusso2 said:**
> I don't know how you expect security from a company Linspire that its Operating system the user account was the root account and they still defend that

Many of the Linspire users thought nothing was wrong with running as root and still prefer it.

Btw S3Indiana is a paid member of the Linspire staff so he would be defending it.

I don't think he will. 

This CNR issue is a recurring discussion I believe.

---

### Post by compiledkernel on 2008-04-18
Actually an interesting  to Point 4 of the Original Post 

K3B - burning application. 

Deps --   cryptsetup dmsetup k3b kamera kcontrol kdebase-data kdebase-kio-plugins kdemultimedia-kio-plugins kdesktop kicker libdbus-qt-1-1c2 libflac++6 libk3b2 
 libkcddb1 libkonq4 pmount vcdimager

Seems you would want to know that these dependencies are installed.

---

### Post by Seisen on 2008-04-21
First things quit trying to flamebait S3Indiana into coming into this discussion, if we wants enter this discussion I sure he will do it on his own terms besides that I don't wan't this thread closed.

Secondly I did finally find the Windows codecs, I stumbled across this webpage. [http://press-release-depot.com/pr/linspire-fluendo-partner-to-bring-easy-one-click-multimedia-software-to-desktop-linux-users.html]("http://press-release-depot.com/pr/linspire-fluendo-partner-to-bring-easy-one-click-multimedia-software-to-desktop-linux-users.html")  
which has a link to the fluendo megabundle as they call it. I have two concerns with this, one you don't know what packages you are getting until you pay for the package and install it and secondly if you go the fluendo website for $45 dollars you get two additional codecs while on CNR.com you pay $40 and are missing the H.264/AVC Video Decoder and AAC Audio Decoder. Another thing is on the f luendo website you get this warning 
> "These plugins are made to run on systems with GStreamer 0.10.3 or higher and glibc 2.4 or higher. We recommend that all users try the free mp3 plugin before buying any other plugins to verify that our plugins runs on their system.
Not anywhere on the fluendo mega-bundle page on CNR.com does it state that anywhere. That to me is kind of shady its like your telling people that they will work even though there could be a chance that they won't. Also as of right now CNR.com doesn't offer a refund it the package doesn't work so.....

---

### Post by NE Key on 2008-04-21
> **Saint Angeles said:**
> so theres virtually no difference between synaptic and CNR (except synaptic is preinstalled and more secure) ?

man i remember last week there was a flood of spammers talking about how cool CNR is.

losers.

The main point about about CNR is that it is a retail outlet where software authors can sell their products. Also users can add reviews of the products.

Most of the products on it are free but it is a "shop" and accepts payment etc.

I think the Ubuntu "add software" routine I find in 7.10 has caught up with and overtaken CNR for ease of use but this was not the case a few years ago when CNR was created.

---

### Post by NE Key on 2008-04-21
> **jrusso2 said:**
> I don't know how you expect security from a company Linspire that its Operating system the user account was the root account and they still defend that
.

In Linspire 5 & Freespie 1 the initial account created on installation was root; one was then expected to create user accounts.

Linspire 6 & Freespire 2 are based on Ubuntu 7 and create accounts in the same way as Ubuntu 7 on installation.

---

### Post by compiledkernel on 2008-04-21
So Seisen, if you give Fluendo the money they will provide you with Codec's that you dont get by buying from CNR.com. 2 of Fluendo's apps (Flumotion and Elisa) are products that I actively use currently. Its interesting to note however that the plugins provided by universe in respect to Fluendo (gstreamer based) fluendo-mp3, fluendo-mpegmux, and fluendo-mpegdemux. So really all your getting out of the deal for the 40 dollars to CNR.com is 

    * Windows Media Audio Decoder
    * Windows Media Video Decoder
    * Windows Media ASF Demuxer
    * Windows Media MMS Networking MPEG2
    * Video Decoder MPEG4
    * AC3 Audio Decoder

But toss Fluendo the 45 dollars and you get 

Windows Media Audio Decoder (Windows Media 7, 8, 9, 10, Pro, Lossless and Speech)
Windows Media Video Decoder (Windows Media 7, 8, 9 and VC1)
Windows Media ASF Demuxer
Windows Media MMS Networking
MPEG2 Video Decoder
MPEG4 Part 2 (DivX) Video Decoder
H.264/AVC Video Decoder (32 bits only)
MPEG2 Program Stream and Transport Stream demuxer
MPEG4 ISO Demuxer
MP3 Audio Decoder
AC3 Audio Decoder
AAC Audio Decoder (32 bits only)

I think its all a matter of whats legal to you vs what is not. But its interesting yet again to see that CNR short changes the user out of what is already out there and existing, yet another clearly reason to show for dated software , or incomplete packages. Or support you , even in the event of "Non-Functionality" , to allow you a refund. 

Kinda not good.

---

### Post by xArv3nx on 2008-04-21
> **compiledkernel said:**
> So Seisen, if you give Fluendo the money they will provide you with Codec's that you dont get by buying from CNR.com. 2 of Fluendo's apps (Flumotion and Elisa) are products that I actively use currently. Its interesting to note however that the plugins provided by universe in respect to Fluendo (gstreamer based) fluendo-mp3, fluendo-mpegmux, and fluendo-mpegdemux. So really all your getting out of the deal for the 40 dollars to CNR.com is 

    * Windows Media Audio Decoder
    * Windows Media Video Decoder
    * Windows Media ASF Demuxer
    * Windows Media MMS Networking MPEG2
    * Video Decoder MPEG4
    * AC3 Audio Decoder

But toss Fluendo the 45 dollars and you get 

Windows Media Audio Decoder (Windows Media 7, 8, 9, 10, Pro, Lossless and Speech)
Windows Media Video Decoder (Windows Media 7, 8, 9 and VC1)
Windows Media ASF Demuxer
Windows Media MMS Networking
MPEG2 Video Decoder
MPEG4 Part 2 (DivX) Video Decoder
H.264/AVC Video Decoder (32 bits only)
MPEG2 Program Stream and Transport Stream demuxer
MPEG4 ISO Demuxer
MP3 Audio Decoder
AC3 Audio Decoder
AAC Audio Decoder (32 bits only)

I think its all a matter of whats legal to you vs what is not. But its interesting yet again to see that CNR short changes the user out of what is already out there and existing, yet another clearly reason to show for dated software , or incomplete packages. Or support you , even in the event of "Non-Functionality" , to allow you a refund. 

Kinda not good.
Yeah, yeah, keep talkin'. We all know you're an anti-CNR fanboy.

The most interesting thing I find about CNR.com is the Aisles feature, which basically allows you to add a bunch of packages together into one aisle, so every time you reinstall all you have to do is click the Aisle CNR button once and it reinstalls all those packages you added to it before.

You all may not like it, but can we please stop making "how much CNR sucks" threads?

---

### Post by compiledkernel on 2008-04-22
This is a civil discussion ,  xArv3nx(Jo). Please refrain from name calling and steering the discussion off topic by doing so. 

Name calling and general disrespectful behavior are a clear violation of Forum CoC.

---

### Post by awakatanka on 2008-04-22
Isn't it that a company that makes a deal with cnr to advertise our sell there software in cnr. If so then cnr can't be blamed if Fluendo sells less packages in cnr. So the one to blame is Fluendo then.

---

