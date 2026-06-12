---
title: "Adiós  Ubuntu (No Flames Please)"
date: 2009-03-14
forum: Testimonials &amp; Experiences
---

### Post by RustyWyatt on 2009-03-14
Yup,

Unfortunately is is true...  As you can see by my login I've been around for awhile and am currently using Ubuntu on a number of systems AND am very happy and VERY disappointed by my latest finding!

So why am I going back to Window$?

It is VERY simple; but first a little background info.  I have spent the last month looking for a simple way to install and maintain Ubuntu on a computer I plan on using as a DVR/HDTV (MythBuntu) server in my home where I do not have a telephone or Internet connection.

I use my cell phone as my only voice and data connection in rural Northern NV and Sprint only provides Window$ drivers for my tethering Black Berry; which works VERY well for me!

I am willing to workout tethering via Ubuntu but one MUST be able to download applications and updates to another computer and then transfer them to Ubuntu system in order to install and maintain a complete system.

So here is the fatal flaw in Ubuntu: It appears that one cannot download updates or new applications to another computer as packages and then transfer the "files" (via CD or local network) to the Ubuntu box to apply them!

In my personal opinion this is a MAJOR LIMITATION
to using Ubuntu!

Please don't waste my time flaming me...

You may not understand that not everyone cannot have a high speed Internet connection and/or everyone does not necessarily want to have a high speed Internet connection everywhere in their life.

However, it is unarguable that Ubuntu needs to provide a way to have a healthy and complete system without requiring a direct Internet connection.

Regretfully,
Tom

---

### Post by Shazaam on 2009-03-15
Have you looked at these few examples?
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)
[http://www.getdeb.net/](http://www.getdeb.net/)
[http://linuxappfinder.com/](http://linuxappfinder.com/)
Many more available.

---

### Post by JPtux on 2009-03-15
Pretty sure you can just transfer the debs using a CD or a flash drive

---

### Post by ALIENDUDE5300 on 2009-03-15
If you can find .deb files for the packages you require (most likely by browsing the repositories), you can put them on a flash drive or something to transfer them to your other computer. Much more environmentally friendly than CDs. ;)

---

### Post by cptrohn on 2009-03-15
If you use Sprint then why don't you use one of their mobile broadband devices instead of tethering with your cell phone?

It's a better connection, and I am about 95% certain that they do have linux drivers available for the USB modems...

evdoforums is the place to go and find out for sure though, but you do get better download and upload speeds with those devices than you get with the tethering from the cell phone... (and I used both options when I used to use windows, the USB modems are far and away MUCH better than the cell phone connection) and the price for their unlimited use is right at $60 a month.... sure it's what $20 cheaper to tether with the phone but the service doesn't work nearly as well with the phone either.

---

### Post by Arup on 2009-03-15
Apt on CD does it all and nicely, far better than installing Windows upgrades. Windows destroyed Autopatcher which was the only sane way to get updates from Windows and patch it. Now you have to go through the Windows catalog and apply each and every update one by one. Its far more painful.

---

### Post by cptrohn on 2009-03-15
I just searched there to make sure and they do have linux drivers for most of the USB modems available there...

I would take a look and maybe contact them there about it... those guys are one of the absolute best outfits when it comes to EVDO... if it can be done, they can do it.

---

### Post by cptrohn on 2009-03-15
Here is one of those USB modems that does come with Linux drivers here.

[http://www.linuxdevices.com/news/NS3484307139.html](http://www.linuxdevices.com/news/NS3484307139.html)

Hope this helps some.

---

### Post by markusf21 on 2009-03-15
You could always try [COLOR="Blue"]_[this]("http://keryxproject.org/")_[/COLOR].

---

### Post by kansasnoob on 2009-03-15
> **Arup said:**
> Apt on CD does it all and nicely, far better than installing Windows upgrades. Windows destroyed Autopatcher which was the only sane way to get updates from Windows and patch it. Now you have to go through the Windows catalog and apply each and every update one by one. Its far more painful.

+1!

I've set up nearly 30 computers with either Ubuntu, Xubuntu, Kubuntu, or Linux Mint. Most were older machines still running Win 98 or ME, and with a power supply upgrade and the cheapest available all-in-one motherboard I've managed to get most of them on AT&T's $10.00 @ month DSL, but a few still had to stay on dial up due to their locale!

Since they all have relatively slow DL speeds I use aptoncd a lot! Compared to downloading anti-virus/spyware updates, and Windows own security updates it's a snap!

But then, each to their own!

---

### Post by robert shearer on 2009-03-15
+1 for aptoncd. Works just fine everytime.

---

### Post by Cheesemill on 2009-03-15
+1 for Keryx, has always worked brilliantly for me.

---

### Post by alanwalterthomas on 2009-03-15
I think he has a bit of a point. It is possible to get packages from another computer; however, downloading software on one computer & then installing it on another isn't as convenient/easy/obvious as it should be, especially for windows users who are used to downloading a single .exe that's put right in front of them & then works the same on whatever computer with a double click.
For example, just tried to install gl-117 (the air combat sim) on another computer.
I wasn't able to get it from Add/Remove. I went to synaptic, looked it up, & checked the box "Download package files only"
Here's the real problem: Once the files were downloaded I had to find them. They weren't downloaded to ~/Desktop so I had to find them. So, I went to a terminal (which typical user doesn't even want to know about) & typed something that one CAN NOT expect typical user to know:

sudo updatedb (then wait 2 minutes)

locate gl-117

Then I copied the four (two .debs - one for data, one  & I think a .png & something else) files to another computer. Then I installed from the debs. Done - it showed up in synaptic as locally installed software & the icon was in Applications - Games.

So, make it obvious where the downloaded files are going, or let us choose where they're downloaded. Would it be possible to have synaptic automatically put copies of the files on the desktop when we choose to only download the package files?
This also isn't great because I'm left with copies of the program on the computer I originally used to download it & I'm afraid to go sudo remove the files "locate" found for me because I might screw up APT's database ~ what it thinks should be available in /var/cache/apt/archives won't be.

And besides, it doesn't always work. I tried to copy gcc (whatever's used to compile stuff) to a netbook where I had to compile madwifi before it could connect to the internet wirelessly & it turned into a bloody mess. There seemed to be a dozen files involved, I had no idea where to start so I just tried to install (by double clicking on each, didn't (& shouldn't need to) know any better) the .debs one by one, which gave me my first taste of dependency hell. One package installed badly because another wasn't there first or something; I couldn't install the .deb that looked like it would satisfy those dependency problems, & synaptic basically crapped out on me saying it wouldn't work right until I fixed the bloody dependency problems.
I ended up reinstalling & finding an Ethernet connection so I could install the compiler from synaptic, but it was a major pain in the *ss. If ethernet didn't work either (& it broke when I updated the kernel - a regression) I'd be S.O.L.

The problems go beyond just getting the software on the other computer - I have to worry about how it'll affect the rest of the computer. For example, I can't use the newest fglrx driver because when I try, it says it can't parse OpenOffice.org dependencies, & quits. I removed openoffice 2.4 from my Hardy installation to put 3.0 on. Now why on earth should my openoffice version have anything to do with my graphics card driver??? I got around it when I had just installed Ubuntu fresh by removing OOo, installing latest fglrx, then installing OOo.
However, I'd really rather not have to reinstall OOo every month because fglrx thinks it's not installed correctly. (Again, WHY SHOULD IT CARE?)
Just to update my non-synaptically installed OOo to OOo 3.0.1 I had a hassle. OOo told me to update, downloaded the new files, but when it was time to actually install it wouldn't. After researching it a little bit on these forums, because I'm very patient & too cheap to use Windows, I found out I'd have to run the update as root. So since I'm trying to learn here besides just use the computer, I found out how to extract from the command line, & then went typed "sudo sh Desktop/OOO[tab]/update" & finally it worked.
The point is: Not doing things the "Ubuntu Way" (get everything from repos & if it's not there live with it) can make Linux a real pain. Little things that take a few seconds on Windows can take a lot longer on Linux if you include research time.

So I managed. But most anyone else would follow the OOo GUI update installer, click install, & see that nothing happens, leading to a very big W.T.F.?!?! moment. Then conclude "Linux sux & I'm going back to Windows" Seriously, couldn't it at least tell me that I need root priviliges (& HOW TO GET THEM? sudo sh, or, gksu) if it can't just pop up a put-in-your-password window like synaptic?

What's a little odd is that when I installed the Penumbra series from Frictional Games (btw it's one of the best games I've played, linux or otherwise) all I had to do was double click the install script file, & off it went. As simple as Windows. No worries about anything (it might have asked for my password once). Why can't OOo do that?
(on the other hand, I've no idea how to uninstall except updatdb, locate the name of the program, then remove it all manually - so long as I guess the name of the folders & files I'm looking for)

So this has been a bit of a long post. About updating a program. People looking into Linux get scared off if they see long discussions about something as simple as updating a program. Please Ubuntu, make the double click - Enter Password (if necessary) dream come true.

In Linux I've found that there are many quick & easy ways to do things - but to a noob even more important than quick & easy is OBVIOUS

---

### Post by stalkingwolf on 2009-03-15
SPRINT also has a mobile router, just plug your USB stick into it and you have a wireless access point.

---

### Post by betrunkenaffe on 2009-03-15
Umm, I'm not sure I've ever had a need to do what the OP is wanting to do. I can't see how this would be a feature requested by a large majority of users... 

I've installed programs via double clicking on a deb without any issues and the other solutions provided seem to accomplish exactly what the OP wanted to do. Maybe I'm not understanding the problem.

---

### Post by wolfen69 on 2009-03-15
sprint mobile broadband would work. why tether?

problem solved.

wasn't that easy?

---

### Post by EXCiD3 on 2009-03-15
With [Keryx]("http://keryxproject.org"), I am working on adding package installation support soon, which will basically be a fully functional, portable package manager. It works just like synaptic so it is easy to find packages and download them with the only tough part being that you have to install them yourself, which you can use Gdebi or dpkg, whichever you prefer. I wrote it with the intention to try to fill this gap here. It is a real problem when you work offline and want to install new software or update something that you are experiencing bugs with.

---

### Post by Muskegman on 2009-03-15
I myself live in a remote area of Canada and cannot connect to the internet via landline ADSL .........but i use a Sierra Wireless aircard and it works just great with ubuntu, no messing around or any software to install, ubuntu recognized it automatically and had me online within 20 minutes of a fresh install.

---

### Post by Nero147 on 2009-03-15
Tom,

Sorry to lose you, I feel your pain. At various points over the years I have taken a break from Ubuntu (and sometimes from GNU/linux in general) I'm not going to tell you that you're wrong, or tell you that you should replace all your hardware to get ANY operating system to work, because I too have had people tell me when I had hardware problems, "Well you should have bought this _link_. How could you have not known that." I generally do my homework now, but sometimes odd things happen.

I don't think that people that stop using Ubuntu are traitors, but you sound like a nice person, so I hope that if your situation changes you consider GNU/linux as an always present alternative.

---

### Post by RustyWyatt on 2009-03-15
Howdy,

Well folks Thank You VERY much for all of the advice and help!  I hope I did not sound too whiny...
I have been trying to solve this problem for a month and did not receive any mention of “aptoncd “ or “Keryx”!  

I am encouraged by all of the community help in Ubuntu and am going to follow the leads from all of you before I jump ship.  I think I will also go back and try to get my laptop Ubuntu partition to work on my Spring tether setup (no luck with this project either so far) and then try some of the ideas here.

Ideally, what I need right now is the ability to down load updates and packages via Windows and then CD or network them over to my laptop and HDTV/DVR Ubuntu setups.

As for the usb modems solutions, I currently get unlimited voice, txt, data(!) etc. etc. etc for a flat $100 bucks a month.  I use this setup for all of my voice and data at both my home and business.  Unfortunately it doubles my monthly expense to add a usb wireless modem and is subject to usage limitations ;-(  And of course, I'm only in one place at a time;-)

So until then, I'm stuck with Window$

Thanks again!

Tom

---

### Post by EXCiD3 on 2009-03-15
Looks like all you've gotta do is tell the forums you are about to leave and reason why and we will lure you back in with our never ending enthusiasm for linux. :D

---

### Post by Tamlynmac on 2009-03-16
> EXCiD3 	 		**Re: Adiós  Ubuntu (No Flames Please)**
 Looks like all you've gotta do is tell the forums you are about to leave and reason why and we will lure you back in with our never ending enthusiasm for linux. :grin:

Perhaps the OP realized that and posted in this section deliberately. Unfortunately, finances appear to limit the OP's ability to implement a number of the solutions purposed. I've learned some issues (primarily hardware) may only be overcome by financially investing in the solution. IMHO no one product (not even Ubuntu) will meet the expectations/requirements of all people.

If Windows successfully meets the OP's computing requirement, then I suggest the adage of "Using What Works" applies. Unlike others I don't view that as loosing a user, but rather I'm pleased that RustyWyatt has a solution to the problem. It's not always about competition, many times the problem may simply be situational and/or financial.

To the OP:
Farewell & Good Luck

---

### Post by cptrohn on 2009-03-16
> **RustyWyatt said:**
> Howdy,

Well folks Thank You VERY much for all of the advice and help!  I hope I did not sound too whiny...
I have been trying to solve this problem for a month and did not receive any mention of “aptoncd “ or “Keryx”!  

I am encouraged by all of the community help in Ubuntu and am going to follow the leads from all of you before I jump ship.  I think I will also go back and try to get my laptop Ubuntu partition to work on my Spring tether setup (no luck with this project either so far) and then try some of the ideas here.

Ideally, what I need right now is the ability to down load updates and packages via Windows and then CD or network them over to my laptop and HDTV/DVR Ubuntu setups.

As for the usb modems solutions, I currently get unlimited voice, txt, data(!) etc. etc. etc for a flat $100 bucks a month.  I use this setup for all of my voice and data at both my home and business.  Unfortunately it doubles my monthly expense to add a usb wireless modem and is subject to usage limitations ;-(  And of course, I'm only in one place at a time;-)

So until then, I'm stuck with Window$

Thanks again!

Tom

So Sprint doesn't charge for the PAM service anymore?  I know when I used it they charged $40 a month extra for PAM (phone as modem)... but the USB data package via the USB modem is unlimited use through Sprint, there is no limit on the data package with their mobile broadband..  I know Verizon had something like a 5g limit per month but as of right now Sprint has no cap on data.

---

### Post by EXCiD3 on 2009-03-16
> **Tamlynmac said:**
> Perhaps the OP realized that and posted in this section deliberately. Unfortunately, finances appear to limit the OP's ability to implement a number of the solutions purposed. I've learned some issues (primarily hardware) may only be overcome by financially investing in the solution. IMHO no one product (not even Ubuntu) will meet the expectations/requirements of all people.

If Windows successfully meets the OP's computing requirement, then I suggest the adage of "Using What Works" applies. Unlike others I don't view that as loosing a user, but rather I'm pleased that RustyWyatt has a solution to the problem. It's not always about competition, many times the problem may simply be situational and/or financial.

To the OP:
Farewell & Good Luck

Indeed, if it does not fit your situation properly, you have to use what works. He gave it his best shot, in the future situations will change hopefully and all will be swell.

---

