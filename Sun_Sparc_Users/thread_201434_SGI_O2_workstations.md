---
title: "SGI O2 workstations"
date: 2006-06-21
forum: Sun Sparc Users
---

### Post by dark_knight on 2006-06-21
Hey Sun guys..... I need some help.. I have first searched the fourms and all "SGI" brings up is ATI video cards... so here it go's  I have some O2 SGI workstations that I am trying to get working for some non profit org that can not afford computers... can you install Ubuntu on SGI workstations? is there any online How to's you can point me to... please excuse the shortness I am in dire need of help with this issue.   


Thanks

---

### Post by netztier on 2006-06-22
SGI O2s are based on the MIPS processors - not SPARC.

To my knowledge, ther currently is no MIPS version of Ubuntu - bad luck, then. Some later SGI workstations were Intel- (IA64)-based, AFAICR, and were even shipped with Linux. If you have an IA64-SGI, Ubuntu's [IA64-Port ]("http://cdimage.ubuntu.com/ports/releases/6.06/release/")might work.

To find out about SGI and Linux, a starting point might be [here]("http://www.sgi.com/developers/technology/linux/")


kind regards

Marc

---

### Post by netztier on 2006-06-22
[QUOTE=dark_knight]is there any online How to's you can point me to... 
[/QUOTE]

Even better:

[http://www.linux-mips.org/]("http://www.linux-mips.org/")

kind regards

Marc

---

### Post by GTvulse on 2006-06-22
[QUOTE=dark_knight]Hey Sun guys..... I need some help.. I have first searched the fourms and all "SGI" brings up is ATI video cards... so here it go's  I have some O2 SGI workstations that I am trying to get working for some non profit org that can not afford computers... can you install Ubuntu on SGI workstations? is there any online How to's you can point me to... please excuse the shortness I am in dire need of help with this issue.   
[/QUOTE]

If the advice by netztier doesn't work out, you can always use [NetBSD]("http://www.netbsd.org/").  Heck, you can run NetBSD in a [toaster]("http://www.netbsd.org/Changes/#toaster"). Once you set up the machines with a graphical desktop, an end user will find it difficult to tell the difference.

---

### Post by allnameswereout on 2006-06-29
Linux (e.g. Debian), OpenBSD, NetBSD support the O2 but hardware support is limited and installation may be different than normal. You'll have to carefully figure this out.

Your O2 will not run any faster or better running an open source system. It will be slower than IRIX and slower than a P2/400 MHz hence IMO you're better off keeping IRIX on it. This supports all your O2s hardware.

Or use a faster, more powerful machine. Probably not a MIPS. Sell your O2 now that it is still worth a bit (e.g. on eBay) and buy a better 2nd hand, powerful machine or 2 for your NGO.

There are better ways to waste time. (Been there, done it.)

---

### Post by Max Luebbe on 2006-07-02
If youve got a working O2 with IRIX running on it, it can be a fun machine to keep around and mess with.

I've got an Indy, an O2 and an Octane2 - none of them compare to my Centrino laptop for speed - but owning a computer that used to cost more than a car is pretty cool. (And so is a video card the size of an ATX motherboard!)

I say hold onto it, because its a piece of history thats becoming increasingly rare.

---

### Post by allnameswereout on 2006-07-04
Max,

TS said "non profit org that can not afford computers".

I don't think "fun" and "being cool" combines well with that.

We're talking productivity here. Its not clear what TS wants w/the machine, but one can safely assume it'll be a desktop or workstation. Although vague, assume it will run the browser Mozilla Firefox only. For such a simple purpose even IRIX on this machine is pretty slow compared to a mid-class x86 machine. An old Athlon or faster with similar RAM running Ubuntu will run circles around it. Plus, SGI's Freeware repository is out of date and the Mozilla Firefox port contains security vulnerabilities.

For productivity these machines are simply not "cool" or "fun" at all unless you run some specific software on it or already have it in production environment. Even in such environments those machines are phased out nowadays which is why mortals can buy them now 2nd hand.

Therefore i suggest selling the MIPS machine to someone who likes such "cool" machine and buying a better (2nd hand) mid-class x86 machine instead.

---

### Post by Compucore on 2006-09-10
I had gone through the same thing over here. With mine looking around. I had remember a user here on Ubuntu Mentioning that as well for the SGI O2 didn't have any here at ubuntu. I had downloaded Debian version for MIPS. And I am in a process of burning in a 13 cd set plus the two patch cd as well over ehre for mine. *(Plus a 19-21 inch Sunmicrosystem monitor with d15 pin for hooking it up to.)* It's a nice machine to go along with my nextstation computers as well. And to learn of of as well Maybe do some video editing with it too once I can get some extra hard drives for it. Not many of the main streamers of windows or Mac for that mater knows about these kind of machines since. Due to lack of interest of computers. I have heard of them them over the yuears due to their animation capabilities long ago. 

Compucore

---

### Post by mips on 2006-09-11
No ubuntu support for MIPS, might wanna look at debian.

---

### Post by Compucore on 2006-09-11
Yeah That is what I did over here. Downloaded it already over here 13 cd's and 2 patch cd's for it I am slowly burning them onto CD's like you had mentioned MIPS. There is no real different between the ubuntu version and the  Debian one here with the exception of one going under ubuntu name and my O2 going under the debian name. So it should not be that much of a thing to learn on both of them. And hopefully I'll be able to do some things with the O2 on the debian that I could work with on the RISC CPU in there. At least keep me occupied with it for a little while. It would have been nice though to have it under the ubuntu hat as well. But hey we can all dream about it. But its fun learning this stuff.

Compucore


> **mips said:**
> No ubuntu support for MIPS, might wanna look at debian.

---

### Post by mips on 2006-09-12
Ubuntu and debian are pretty similair. You could always make it look like ubuntu ;)

---

### Post by allnameswereout on 2006-09-13
The O2 is incredibly slow. Both the mainboard and the RISC processor no matter which revision. The only interesting hardware on it IMO, is the video board. But IIRC you need IRIX to use that. All the video editting apps for SGI/MIPS are prorietary and since ages available on Linux/x86, Windows NT/x86 (and MacOSX/PPC) which hardware costs a fraction of a SGI or the applications are open source hence also available on many cheaper platforms. I'm just saying it so you won't be too disappointed (been there, done it). If you want a faster SGI/MIPS, try one of the mid or high end Octanes + V10/V12, or Fuel. Naturally, come with a higher pricetag.

MIPS, besides ARM, is still interesting though. Heavily used in the embedded industry, but such is not Ubuntu's aim.

---

### Post by Compucore on 2006-09-13
For me personally. I do not mind it being slow at what ever speed the main processor is set to. For myself personally. Is just another learning tool to work with. ANd being something different than your normal off the shelf X86 that you can get. Its fun. And besides I got it for free to boot from a techie friend of ine that I know. We're both living on the same street.  So for me its just a earning tool. And to have something different How many people here can say that they are also running 2 color nextstation here. :D And those are even slower than the O2 that I have here and my Dell GX150.


> **allnameswereout said:**
> The O2 is incredibly slow. Both the mainboard and the RISC processor no matter which revision. The only interesting hardware on it IMO, is the video board. But IIRC you need IRIX to use that. All the video editting apps for SGI/MIPS are prorietary and since ages available on Linux/x86, Windows NT/x86 (and MacOSX/PPC) which hardware costs a fraction of a SGI or the applications are open source hence also available on many cheaper platforms. I'm just saying it so you won't be too disappointed (been there, done it). If you want a faster SGI/MIPS, try one of the mid or high end Octanes + V10/V12, or Fuel. Naturally, come with a higher pricetag.

MIPS, besides ARM, is still interesting though. Heavily used in the embedded industry, but such is not Ubuntu's aim.

---

### Post by Compucore on 2006-09-13
I probably could make it look like Ubuntu too. But I will wait and see once I get the burn ins done. And get the OS back in their. The original my friend doesn't have the password for root. And THere is no way I can figure out on how to break the password for it. So might as well just format and reinstall fresh. What I migh want to do once I get it running and hooked up to my network here. Is to hook my Aptiva, my second Dell GX150, and this together as a beowulf kind of thing. Just to see how it works together you know. Like try and do some kind of rendering animation with it. Where it can use all three of them together and just do something simple with it. 

> **mips said:**
> Ubuntu and debian are pretty similair. You could always make it look like ubuntu ;)

---

### Post by allnameswereout on 2006-09-14
If you accept the relatively slow speed, use it for fun, and got the time -- sure, I wish you all the fun. The case is at least sexy :D. Just don't expect too much from it. Don't expect to do video processing on it esp if you don't run IRIX. If it runs IRIX and you lost the password there are many ways to crack it. I had this problem too with an Octane of mine. What I did IIRC was booting up IRIX via CD, grabbing the passwd file, and cracking it using Crack or Jack the Ripper or sth. Took a few hours on a slow AMD K7 running Linux. Ofcourse, YMMV depending on the password. Or I am confused with a Sun, and I just reinstalled IRIX. Don't know anymore. My Indy's and Indigo2s were all passwordless when I got 'em.

You say you can make it look like Ubuntu. Just forget it. Drop that attitude. If you want X, you are going to run one of the WMs or at best XFce. Making it look like Ubuntu requires GNOME. If you run IRIX, you'll either have an archaic GNOME version from Freeware.SGI.com, a 3rd party one (does exist for at least GNOME 2.6), or your self-compiled one (good luck w/the latter). If you run Linux/MIPS on it, sure, you can get GNOME. I guarantee you it will be absolutely unusable on your machine. I ran GNOME 2.x on an Octane running IRIX. For about 5 minutes or so. Then it was finally started, I looked around, figured it was far and far too slow, and switched back to good ol' 4DWM (which isn't _that_ bad). The machine, with 4DWM ran Firefox fine though as the standard Netscape 4 has.. hmm.. issues. Keep in mind that machine was faster than yours (dual R10000 195 MHz, 384 MB RAM, almost an Octane2, faster than any O2 in existance). From what I read at Nekochan.net (a SGI community) people with O2s are absolutely frustrated w/the slowness of Firefox on O2 @ IRIX. The thing is simply too slow. Some bought new non-SGI CPUs for it (RMD7200 or sth like that) which are a bit faster running at sth like 400 MHz. Also, that is all with IRIX, not with Linux (IRIX will run better on it). Imagine it'd run GNOME then which compared to 4DWM is bloated beast not even worth mentioning. I say, forget GNOME, and give IRIX a shot. IRIX is a learning experience as well, and you can get the full experience from your SGI as it was meant to be. I also gave my Octane away for 100 EUR.. which I've not received till this day heh.

For compiling, you could use CCache (from Samba.org) on it.

Sure, a NeXT is nice. Guess what though... what OS do people run on it? ;)

What I don't like about SGIs is their power consumption. This thing had something like 700W power supply. If that'd be less it could surely function as e.g. a sexy terminal.

(If you need IRIX 6.5 base or 6.5.22, check DC++/eMule or send me PM. Newer than .22 won't run on it.)

---

### Post by Compucore on 2006-09-14
Well when I got it from my techie friend that I do some projects with from time to time over here. Neither of us has the original cd's of Irix 6.X or even a burn in copy of it. So trying to grab the file in question like you mentioned is out of the question for it. So the olny way to go right now for me is to just do the burn in of the cd's that I have already for it of Linux from Debian and install it. I am not planning to do that much video edit if any at all. Its just a learning tool that I want to work with it. I do not expect it to be a high flying machine like your saying there. For most of us we're doing this for fun and learning. And I never came up with an atitude with it. Maybe for you its too slow maybe for some one else it may not it all depends on what you want to do with the machines. Not everyone will be the same with their own machines. What one person does with their own machine is what they do with it. If it runs slow it runs slow I am not expecting it to run in the indy 500 on it. And at least I do have a burn in of the OS for the two nextations of openstep. And they are working fine with it. . 

> **allnameswereout said:**
> If you accept the relatively slow speed, use it for fun, and got the time -- sure, I wish you all the fun. The case is at least sexy :D. Just don't expect too much from it. Don't expect to do video processing on it esp if you don't run IRIX. If it runs IRIX and you lost the password there are many ways to crack it. I had this problem too with an Octane of mine. What I did IIRC was booting up IRIX via CD, grabbing the passwd file, and cracking it using Crack or Jack the Ripper or sth. Took a few hours on a slow AMD K7 running Linux. Ofcourse, YMMV depending on the password. Or I am confused with a Sun, and I just reinstalled IRIX. Don't know anymore. My Indy's and Indigo2s were all passwordless when I got 'em.

You say you can make it look like Ubuntu. Just forget it. Drop that attitude. If you want X, you are going to run one of the WMs or at best XFce. Making it look like Ubuntu requires GNOME. If you run IRIX, you'll either have an archaic GNOME version from Freeware.SGI.com, a 3rd party one (does exist for at least GNOME 2.6), or your self-compiled one (good luck w/the latter). If you run Linux/MIPS on it, sure, you can get GNOME. I guarantee you it will be absolutely unusable on your machine. I ran GNOME 2.x on an Octane running IRIX. For about 5 minutes or so. Then it was finally started, I looked around, figured it was far and far too slow, and switched back to good ol' 4DWM (which isn't _that_ bad). The machine, with 4DWM ran Firefox fine though as the standard Netscape 4 has.. hmm.. issues. Keep in mind that machine was faster than yours (dual R10000 195 MHz, 384 MB RAM, almost an Octane2, faster than any O2 in existance). From what I read at Nekochan.net (a SGI community) people with O2s are absolutely frustrated w/the slowness of Firefox on O2 @ IRIX. The thing is simply too slow. Some bought new non-SGI CPUs for it (RMD7200 or sth like that) which are a bit faster running at sth like 400 MHz. Also, that is all with IRIX, not with Linux (IRIX will run better on it). Imagine it'd run GNOME then which compared to 4DWM is bloated beast not even worth mentioning. I say, forget GNOME, and give IRIX a shot. IRIX is a learning experience as well, and you can get the full experience from your SGI as it was meant to be. I also gave my Octane away for 100 EUR.. which I've not received till this day heh.

For compiling, you could use CCache (from Samba.org) on it.

Sure, a NeXT is nice. Guess what though... what OS do people run on it? ;)

What I don't like about SGIs is their power consumption. This thing had something like 700W power supply. If that'd be less it could surely function as e.g. a sexy terminal.

(If you need IRIX 6.5 base or 6.5.22, check DC++/eMule or send me PM. Newer than .22 won't run on it.)

---

### Post by pvz on 2006-09-16
[http://www.cyrius.com/debian/o2/](http://www.cyrius.com/debian/o2/)

Works great, I used one as a webserver for over a year.
You have to do a netboot to install btw, so no need to burn all those CD's..

---

### Post by chatuser on 2006-10-05
I currently own a sgi Indy and I use dual boot IRIX 6.5.22 / Debian MIPS.

IRIX is MUCH MORE faster than Debian, is totally optimized for sgi hardware.

Debian works but is very slow, even on "powerful" machines such as O2 or Octane.

I'm a little bit disappointed with Debian performance on my sgi Indy, it looks like a P-133 MHz system; IRIX works much more faster.

If your want to use a non-Intel platform with Ubuntu, better buy a SPARC system or a Mac on eBay.

---

### Post by mips on 2006-10-05
Maybe have a look at NetBSD/OpenBSD and see how those run on SGI boxes.

---

### Post by chatuser on 2006-10-06
I have tried OpenBSD or NetBSD on my Indy but the system console crashed at startup.

I have read it works fine on O2/Octane.

---

