---
title: "Ubuntu is perfect, but there are some missing parts to make it perfect for everybody"
date: 2007-04-19
forum: Testimonials &amp; Experiences
---

### Post by Mr. Eddy on 2007-04-19
Hi,

I'm using Ubuntu since hoary hedgehog (5.04) and I'm using feisty for 3 months now. I must say that I like Ubuntu! Every release is a huge step forward! If you track the development and community a bit, you feel the Ubuntu project growing and become more mature. I like the feeling that, the software I use  today is already a little bit better than the day before. Now feisty is also a big step forward to maturity. things as...

[LIST]
[*]Easy codec installation
[*]Installation of proprietary software for difficult hardware like graphics drivers.
[*]The new way of managing networks with the new network manager and zero-conf
[*]Disk usage analyser included by default
[*]So many other things...
[/LIST]

...are a great improvement. It makes Ubuntu almost perfect. Now I just want to give some hints to make Ubuntu perfect perfect for me and many simple home users / business users.

Here's my feature request list:

**1) Pda / pocket pc**

There should be a nice and reliable tool to sync windows mobile based pda's/pocket pc's. It's a very important thing if you want to have Ubuntu adopted by businessman. A businessman wants it's addresses, mails, calendar, contacts synchronized with there application of choice (evolution, thunderbird, sunbird, kontact,...). That's also the most important reason I can't switch my dad's laptop to Ubuntu.
[B]
2) Xorg configuration[/B]

There should be a graphical tool for making changes in the xorg.conf file. A problem with Ubuntu (and windows) is monitor detection. So sometimes the right frequencies and resolutions can't be chosen. I know you can't detect the specifications of a monitor but it should be possible to “install” the monitor with the windows ini/inf -file. Sax2 from suse linux can do that. It's a very easy way to make your monitor work the way it's designed to work. 
Now newbies don't know what to do if they can't change the wished resolution and frequency in the “screen resolution”. MAYBE they go searching for a solution on the internet, but how do you find the right info for that problem if they're not 'into' computers? IF they find the right info, they find out they have to change the xorg.conf file. Editing a config-file is a huge pain for a newbie, they are afraid of everything with editable text (config-files, console). Let's assume they find the right section in the file, but what horizontal and vertical sync do they have to fill in for their monitor? ... I think you get my point. I consider it as the weakest point in Ubuntu for the newbie. Because it's a bad first impression, and a first impression is so important.

[CENTER]“Why can't Ubuntu adopt Sax2 or make a similar tool?”[/CENTER]

[B]3) Scan software
[/B]
Something what's lacking in Linux is mature scan-software. I know, we have XSane. But in my eye's, it's a monster of an application.  

[CENTER]“How the hell will I explain my mum how to scan that delicious receipt...?” [/CENTER]

One of the first things that come up in my mind if I open that application. Words that don't fit with XSane are: clean, polished, user friendly. Ubuntu stands for: clean, polished, user friendly...
I don't think this piece of software is usable for the simple home user. Ubuntu should have a clean and user friendly scan application for home and office use. XSane should have an easy to use wizard or something to set some basic settings to get something scanned quickly. That wizard can also be used as integration in applications as F-spot or Gimp maybe OpenOffice. The user interface of XSane should have a facelift. Not all scan options must be available on the main window. Hide professional settings in menu's or something similar. XSane uses only Icon's, but put some text next tot the icon that explains what the icon does.
[CENTER]
“Why should someone want to switch to Ubuntu if that person can't use it's new bought scanner in an easy way?”[/CENTER]

In some offices, all mail comes in at the secretary. Then she scans the mail to pdf and e-mails it to the right employee. This is an important functionality for office users.
[B]
4) Print settings[/B]

There should be an easy way to switch preconfigured printer property's in “File -> Printer settings -> printer property's“ in an application. Now you get a list with a lot of parameters, you can edit manually. But this is to advanced for 'the simple user'. A simple screen to choose preconfigured settings...

[LIST]
[*]Best – normal – fast – econofast
[*]black - colour
[*]single side - double side
[/LIST]

... should be available. I'm not sure Ubuntu can do something about this or if it's the responsibility of the printer manufacturer.

**5) Clean desktop**

This is a minor thing. In Ubuntu if a external device is mounted like a usb hard drive or usb stick. The Icons on the desktop sometimes overlap each other. So if I mount my usb stick, I have to right-click on my Desktop and choose “Clean Up by Name”. Ubuntu should do this automatically.

I just wanted to share my view on Ubuntu with everyone. I know, one day, these thing will be good in Ubuntu. I will use and support Ubuntu until that day (and also after that day)! I want to thank the developers and the community for the great work they deliver!

Keep in mind I'm not a native English speaking person, sorry for that.

A happy Ubuntu user

---

### Post by Rinzwind on 2007-04-19
If you make this post conform the Gutsy Gibbon sub-forum rules you should post this here: [http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)
NOW is the time to offer things you think need improving.

---

### Post by rillip on 2007-04-19
As for the icon thing, I think this is specific to you; I have not had this issue.  It may be fixable.

As for configuring xserver, I agree, however, it's not as bad as you think.  It's not as good as you'd like either, however.  If you run sudo dpkg-reconfigure xserver-xorg, you get a textual configuration utility, similar to what happens when you install Windows 2k or XP.

Still not as easy as a gui tool, but not quite as arcane.  Worse case scenario, you can hit enter a lot.

I'm not sure that synching a Windows PDA with Linux is technologically possible. Have you investigated running Linux on your PDA?  Not sure how this would work, or if it's possible.  It'll depend on the firmware I think, and which filesystem it's using.  If it's ntfs I suppose it's possible, or fat 32, but if it's some filesystem it can't read... well, it can't read it.

---

### Post by Mr. Eddy on 2007-05-07
IDEA requests are made, thanks for the hint

---

### Post by Mr. Eddy on 2007-05-07
> As for configuring xserver, I agree, however, it's not as bad as you think. It's not as good as you'd like either, however. If you run sudo dpkg-reconfigure xserver-xorg, you get a textual configuration utility, similar to what happens when you install Windows 2k or XP.

I have a highscreen monitor that isn't detected correctly even when I run the "sudo dpkg-reconfigure xserver-xorg" command.

> I'm not sure that synching a Windows PDA with Linux is technologically possible. Have you investigated running Linux on your PDA?

Switching to linux on the pda is not an option because the company where my dad works depends on windows mobile.

---

### Post by balloons on 2007-05-21
try gnomescan or gscan2pdf - both made for novices. gnomescan i think is going to be in gnome at some point as well

---

