---
title: "Ubuntu Ready for Prime Time ... Part Trois"
date: 2007-05-29
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2007-05-29
Back again ...

You might remember my first experience which was that I said that Ubuntu wasn't ready for prime time:

[http://ubuntuforums.org/showthread.php?t=410395&highlight=geekkit](http://ubuntuforums.org/showthread.php?t=410395&highlight=geekkit)

I had used 6.10 and had many problems including the kernel crashing when I hooked up my Nokia mobile phone via USB. Then, after 7.04 came out I installed 7.04 on my work machine which actually took about 15 minutes to install. It was a quick install and did not require a lot of setting up to do. Link of that was posted here:

[http://ubuntuforums.org/showthread.php?t=448074&highlight=geekkit](http://ubuntuforums.org/showthread.php?t=448074&highlight=geekkit)

Well, I went back to my home computer which has a little bit of legacy hardware and I decided that I would see how 7.04 stood up to my machine and whether or not the problems I had with 6.10 would resurface with 7.04.

This time around I did not have the SATA issue. I'm not sure if that's because I had reset my BIOS to defaults or if 7.04 worked around it. Installation went without a hitch and so I was able to have a working Ubuntu in about 30 minutes. The difference in time when comparing to my office computer can only be chalked up to my older legacy hardware. But either way, installation went smoothly.

Then I set up my printer, printed a test page, found my wife's computer, linked to a shared directory, linked to her shared printer. After that I decided to try my phone. Remember, last time I did this it crashed and so I was prepared for the worst. Guess what? It worked! Joy! *insert Ren voice*  Wammu and Gnome Phone Manager worked without a hitch. Then I realized I would need (well, okay, want), to have Shoutcast streaming support and the ability to play DVDs and other video media. So, found a link:

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

And followed the instructions. Got the CODECS and was able to listen to Groove Salad, watch a DVD, play quicktime, AVI, WMV, and MPEG videos. Excellent! *insert Mr. Burns' voice*. All between two applications too: RhythmBox and Totem Movie Player.

Next was the NVidia support. The following link helped greatly:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

This installed a control panel specifically for NVidia cards which is very very nice since it even updates your[FONT="Courier New"] xorg.conf[/FONT] file. The NVidia control panel now sits in my Applications->System Tools menu. 

The only hitch I had was setting up SAMBA which is still, unfortunately, a royal pain in the **** to set up. I had to go to command line, do the whole mapping SAMBA accounts to system accounts, and configure the[FONT="Courier New"] smb.conf[/FONT] file. I never was able to make it so that it worked correctly with accounts. In the end I simply opened it up to a directory with wide open privileges and the printer with the following:

[FONT="Courier New"]available = yes
restrict anonymous = no
browsable = yes
public = yes
writable = yes
case sensitive = no
guest ok = yes[/FONT]

Which is fine since I'm behind a hardware firewall (and yes I changed the password and account name on it and don't have remote changing allowed). Having said that, most (if not all) Windows novice users will not know how to share printers and folders on a network either. And I must say that the install wizard for Ubuntu is actually easier to use than XP's install routine.

Other things that I noticed that were fixed were Synaptic and Add/Remove Programs don't seem to crash anymore (I did a lot of installing, reinstalling, and uninstalling of software), GnomeSword actually installs instead of refusing to with a cryptic error message. Beryl is not there but Compiz is there and takes up much less space in memory. In fact, I couldn't believe my eyes when I realized that without any applications running, I was sitting at 158 MB of used memory! I don't remember the last time I saw XP down to that (2000 might have been but that was a while back!).

One thing that still blows my simple mind is just how lovely the text renders on screen. Even really small fonts are incredibly well rendered and thus crisp, clear, and not requiring me to squint.

So, all in all it appears (from MHO) that the Ubuntu team has definitely addressed a lot of the problems from 6.10 and have raised the bar. I would even go so far to say that it's a desktop replacement. I can now do everything I could do in XP.

My wish list would include the installation of 3rd party CODECs to be an option at the tail end of the installation process of Ubuntu as well as an option to set up a directory for sharing, and a printer for sharing and have SAMBA configured then within a GUI.

Anyways, thanks for reading. It's now my pleasure to be running something on my computer that I can trust.

;)

---

### Post by mybunche on 2007-06-01
Thanks for an informative and interesting read. Good to hear.

---

