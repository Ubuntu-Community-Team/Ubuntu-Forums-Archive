---
title: "The Linux Mom"
date: 2008-02-27
forum: Testimonials &amp; Experiences
---

### Post by elfprince13 on 2008-02-27
So, with both my mom's 10 year old iMac G3, and my slightly newer Pentium 3 
Dell running XP experiencing harddrive failure in the last few months I had 
to come up with a solution to consolidate computers. Fortunately I now have 
my laptop, so I didn't need the desktop, but it made it hard for the 
non-laptop owners in the family (e.g. brothers + mom) to do anything on the 
computer. Fortunately I had a copy of Gutsy Gibbon laying around and a spare 
20 gig hard drive that I mooched from our high school IT department.
The installation went pretty smoothly, I set up a separate partition for 
/home/, everything else on the primary partition. Then came the process of 
recovering data from the other 2 drives. The G3 was fairly easy since it 
still booted up (usually), so I turned on FTP file sharing. Note: the ftp 
server on OS X 10.3 SUCKS. So I turned to Samba and dumped everything onto 
the Ubuntu machine that way (I realise that sharing information between 2
non-Windows machines with a M$ protocol is made of fail, but it worked). The 
Dell's old harddrive was a little harder since my external drive enclosure 
is for 2.5" drives. I ended up turning it off, unplugging the CD drive, 
plugging in the old harddrive and turning it back on. I mounted it, and 
copied everything over into everyone's new home folders. This was PAINFULLY 
slow from GNOME so I ended up switching to tty1 and doing it from the 
terminal.
This brought me to the step of importing all mom's mail settings from 
Mail.app into Thunderbird. This was fairly easy at first, copied over the 
settings by hand and found an apple script to export Address Book entries to 
.csv format. I started thunderbird again just to double check, sent out a 
test email, everything was working fine. The next day Mom sent me an email saying that for some reason NEITHER computer could get incoming mail, but that she could still send mail out fine, and asked if I thought the new computer had broken it. I couldn't think of how it would have, but at least the problem made some sense since she uses our ISP for outgoing mail and her account with the college for incoming mail, but the college webmail was working fine, so obviously their servers were still up and running. I emailed both a friend at the college who uses linux, and the college IT desk, and evidently they recently designed to enforce the use of SSL to connect to their IMAP server. Problem solved. Also, since Linux has better support for Windows media formats then OS X does, mom was really psyched to be able to listen to her VPR Classical internet radio with Rhythmbox. Score another one for Linux :D I also copied over her background image from the Mac, and she really likes the scroll wheel over the iMac's puck mouse. Not too fond of the right click button yet, but I think she'll adapt.


Outstanding tasks:

editing device permissions to make digital cameras, TI graphing 
calculators, and iPods usable without administrative privileges.

netatalk recognizes our Apple Laserwriter 320, which is currently hooked 
up to the house LAN via an AsanteTalk gadget localtalk to ethernet adapter), but won't actually print 
things to it. The CUPS web interface gives me an error about pap/the backend when i try to print a test page. the URI is pap://%2a/Arwen%20Dickerson/LaserWriter

Samba seems a little flaky. I can access the new Ubuntu set up from other computers, but not vice-versa. The other computers are all configured to allow Windows Networking.



help on any of these would be useful if someone reading this is familiar.

posted by elfprince13 at 7:35 PM 0 comments

---

### Post by wPwLUi3N on 2008-03-28
MY Grandmother only need to check mail and browse i am also planning to take out my old p3 and put Ubuntu on it. 
Hope so its smooth transaction for her.

---

### Post by armandh on 2008-03-28
I've had very good luck running Ubuntu on P-IIIs over 256 meg mem.
any thing over 800 mhz with a good video card will run dvds as well

---

### Post by elfprince13 on 2008-03-28
even the integrated graphics seems to be able to handle DVDs pretty well

---

### Post by djamu on 2008-03-28
hehehe, 

I put Ubuntu on my moms laptop a while back ( she's really a computer noob, & quite paranoid ). Never seen somebody so happy with a laptop... She even started customizing her desktop > large icons , background, hooking up every junk she found having USB.  She also started connecting her digital cam, just plugged it in & never wondered that it just worked.. ( before she just brougt it to a shop to get prints ), 
On top of that she even starts torrenting stuff....

For her this is a whole new experience, before the laptop had XP & in the couple of years she had it absolutely nothing changed or got customized.... 

So whenever somebody tells me Linux is not ready for the desktop I'll tell them this story... If my mom gets her way around everybody will...


:guitar:

---

### Post by stream303 on 2008-03-29
Now to finish up - put Ubuntu (or Kubuntu or Xubuntu) on the G3 iMac, provided it has about 256mb of memory or thereabouts.

You can use the last officially supported version, 6.06 or run newer "unofficially supported" versions, along with unofficial support here in the Apple PPC forums.

For example, Feisty 7.04 for PPC can be found here:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

It is highly recommended that you download the "ALTERNATE" version, and use a low speed for the iso burn, and hold the "C" key to boot the disk.  If the hard disk has been upgraded, for that machine you need to boot with an ubuntu partition of no larger than about 7.5 GB.  (the rest you can use as storage, and the faqs and users can help.)

If you decide to follow this route, we look forward to seeing you in the ppc forum.

---

