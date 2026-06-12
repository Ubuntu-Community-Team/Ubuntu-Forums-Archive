---
title: "Ramblings of a beginner installing to USB stick"
date: 2011-09-17
forum: Testimonials &amp; Experiences
---

### Post by Denver Dave on 2011-09-17
I've played around with the DVD a fair amount and decided that I'm not ready to install on my HD, but maybe time for a USB stick.

Purchased an 8 GB Scandisk USB and wondered how to install 11.04 from DVD to USB.  Found various directions which varied, some indicated had to download USB burner. 

Since there is an install choice during bootup and also an install under administration from the ubuntu interface, which seem to be the same, I decided to start from the interface.

Before that I plugged in the USB under XP in case something needed to be installed and to verify that I could see the USB stick.

Then tried to see if I could select boot from USB from the F1 PC boot setup, so far could not figure out anything there in the Boot order.

Back to install.  Scares me to select what I want to do (delete all files) and install, before I choose the drive.  But found some Youtube videos without sound which gave a clue that could pick the drives later. 

Did select the USB stick to install to and hope that works, since I really don't wish to lose my hard drive.   Installing for quite a while.

Installing language packs took a long time - just English would be fine.   Configuring hardware - DVD would have been fixed, wonder why USB needs this.  I was hoping to use the stick on multiple computers like I do with DVD.

Oh - finished - time to restart.... wonder when I get the DVD out? ... there's the DVD drive ... removed DVD ... leave USB in and press enter - here goes .... Booted into Windows XP ... crap.  But guess I should be glad windows XP is still on my main drive .... count my blessings.

OK, reboot and do the F1 Setup and examine the drives for boot order again.... but first, curious if can see USB drive under XP and if there is anything on it.

Removeable Disk L is there, but says not formatted, I'll leave it alone.

Rebooting and doing F1 boot setup - 4 choices for Boot Device Priority are:

1st Boot Device [Floppy Group]
2nd Boot Device [CD-ROM Group]
3rd Boot Device [HDD Group]
4th Boot Device [Network Boot Group]

- Floppy Group Boot Priority [Not Installed]
- CD-ROM GHroup Boot Priority [TSSTcorpCD/DV]
- HDD Group Boot Priority [WDC WD2000JS-]

Don't see removable devices .... oh there it is under HDD Group Boot Priority <whew>  ... move scandisk up ...  don't know how to get out of this screen - let's save and exit and see what happens.

Well isn't that interesting booted into ubuntu and now have the unity menu where I had the classic menu when booted from the DVD.  At least it is now consistent between my desktop and laptop - never bought the video controller card explanation.

First impression, like the classic menu better, but give unity a chance.  

Interesting that the system seems slower from the USB than from the DVD, could that be possible?  
**** later note - DVD boot on desktop 2 min 45 sec, USB boot on desktop 1 minute 45 secs.  For comparison, XP boot from hard drive until I start loading applications automatically - 5 minutes 30 seconds.  Where ubuntu shines, when ask to shut down, it shuts down right off.  XP varies, but takes a while, sometimes quite a while.

So sound - interesting, even with unity sound is muted - unmute - have sound and Abobe Flash within side of FireFox

- wmv files work inside of FireFox

See there is another video editor installed by default Pitivi, will check out later for now install openshot and see if can duplicate what I ran from DVD (added there).

Openshot runs fine from USB

Wish I'd used Ubuntu as the logon name not my name, but OK for now.  Still think the classic interface is easier to use (note to self, give unity a chance.)

See how to change unity to classic and back under login in settings.

On reboot - Good comes up not muted.

Hope this helps someone, wish I'll had a step by step while I fretted about USB install.

Oh one more, let's try switching USB to laptop.  Have to save this so I can reboot.

---

### Post by wildmanne39 on 2011-09-17
Hi, if you want to save settings to the usb drive so they last after a reboot you need to make the usb persistent here is a link for it.
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Thank you

---

### Post by Denver Dave on 2011-09-17
I wonder if the USB stick is hardware dependent.

From DVD desktop always used classic and laptop always used unity.

From USB created on desktop, can boot into either unity or classic (go figure) and remembers from session to session.  Now with the laptop which formally used unity from DVD only will classic come up even if select unity from the logon screen.

Wonder if I'd run DVD with unity on the laptop and created the USB there what would have happened.  Enough for now.  If I want unity on the laptop, I'll use the DVD.   I'll probably do most of my work on the desktop.  So fine for now.  Somehow seems like unity must be better, don't see it, classic seems much easier, but I'll try out unity for a while, maybe takes getting used to.

= = = = = 

Let's not loose sight that a rank beginner with umbuntu has ubuntu running from both DVD and USB and most everything works on two separate computers(except dial-up modems), but not that important and might take a special modem.

Seems faster than XP on my desktop and with XP I usually have a sense that lots of crap is running and wonder why.

Thanks a lot - looking forward to trying applications - openshot looked great!

Amazing .

---

### Post by jockyburns on 2011-09-17
Hi Denver Dave, my experience of Ubuntu 11.04.. HDD in my machine stopped working about a month ago, so bought a new HDD. Nephew promised to download Win7 and bring it up and install it for me. 4 hrs later, he's still not been up and won't answer his phone (what a let down that lad is). Anyway. I'd heard about Linux OS's on the internet so using my G/F's computer, I downloaded 11.04 to  a USB stick (followed all of the instructions) placed it in my computer and turned on.  As per your experience, it took some time to install things, but , what the heck, suddenly I'm back online etc (all from a little memory stick:D), So I surfed the net for about half an hour. When I went to shutdown my computer, I was given the option to install Ubuntu to my new HDD. I thought,"Well everything seems to work ok (albeit slightly differently from Windoze), so I installed it to my hard drive. 
Well I can tell you that apart from one problem last might, it has ran faultlessly. From initial switch on, it takes lees than 20 seconds  to desktop screen. I got my G/F to turn her machine on at the same time as mine and asked her to tell me when she could get on the internet. I beat her by almost 5 minutes.:D:D:D
I'm really pleased so far with Ubuntu. Only downside is the lack of support from some leading manufacturers for machines running Linux OS's for their products. (I'm struggling to install a Lexmark printer, but getting a new HP which is fully supported)

---

### Post by armandh on 2011-09-17
setting the bios to boot from USB is real handy and some times NOT
storage USB sticks will hang the boot process 
if they are in a USB port checked B4 the live OS USB stick 
[at least on the hardware I've tried]

much faster than live CD but not as fast as loaded to ram.

Caution; Unrecognized file systems often show up as unformatted
more often in win as there are fewer recognized

as the above post noted Lexmark just wont work and they seem unwilling to help
I have gotten some unlikely printers to work with Ubuntu
It took a while for this hardware that was widely used under a number of labels
a Data Graphics DDS-32 where last factory driver is a win 2K beta [xp ok]
works just fine [even duplex] with an Ubuntu generic postscript driver
or Hitachi DDP-70 or a Tally ML450 driver.
getting it to work in win 7 was not easy 
[IBM infoprint 32 PS driver]
[another close cousin of a printer]

HP has always been the best choice
.

---

### Post by Ms_Angel_D on 2011-09-17
Thank you for your feedback...if your looking for support please post in the relevant sections of the forum.

---

