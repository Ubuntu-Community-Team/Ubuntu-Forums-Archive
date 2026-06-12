---
title: "Going Backwards"
date: 2009-04-29
forum: Testimonials &amp; Experiences
---

### Post by gettinoriginal on 2009-04-29
I have been with Ubuntu since 6.04, actually thought I had a handle on it to the point I was able to help some others solve their glitches, and always upgraded without serious problems.  I just did a fresh install of 9.04,(actually 3 times), IPv6 cannot be disabled, so is messing up my email (404 errors) and access to some sites(Address Not Found).  Sound and video won't work properly, and of course the solution is at [www.ubuntugeek.com](www.ubuntugeek.com) which is one of the sites I cannot access.  So I'm going back to 8.10 which gave me a flawless install with only minimal personal options to change.  Will try again with 9.04 after they fix IPv6 and the sound/vid problems/or at least allows access to sites for fixing them from my end which I can do in 8.04.

---

### Post by wbee on 2009-04-29
Hello,

I came to Linux/Debian a month ago,wanting an alternative to Vista on a machine without enough capacity to run Vista properly.

I have a dual boot with XP for those times I have to do something without taking the time to learn the new trick here,but those times are becoming fewer.

It is just in the last week or two that I feel comfortable with it,the steepest learning curve for me having been alsa plus pulse audio plus jacks.

Everybody has been helpful and the two times I went to launchpad,I received e mails quickly,telling me it was fixed.
(Which it was and I sent thank you replies.)

True,people with problems are posting and many perfect installs/updates go without forum comment.

All that said,I'm waiting either a month or when the volume of "help me" install posts diminish a lot(which ever comes later) before I leave 8.10,which I like more every day I use it.

-------------

W

---

### Post by calrogman on 2009-04-29
Use `sudo rmmod ipv6` to remove the ipv6 module from the kernel until the next reboot.  You can then find someone who knows some more about Linux to help you to remove it from your system (you could try recompiling the kernel and removing ipv6 completely).

---

### Post by wirelessmonkey on 2009-04-29
blacklist the ipv6 module... tada

Though, if IPv6 support is causing a problem, you have a more significant problem somewhere in your network.

---

### Post by cariboo on 2009-04-29
ipv6 is compiled right into the kernel, it is not a module, so trying to remove the module won't help.

---

### Post by gettinoriginal on 2009-04-29
With 9.04 I could not access certain sites not matter which browser I used, and got 404 errors in email links.  Reverted back to 8.04 (wish I hadn't given my 8.10 disk away)LOL. and immediately have no email troubles or connection problems, it works flawlessly.  This tells me it is a 9.04 issue and not an issue with my system.  But I am just happy to be solid with Ubuntu again.

---

### Post by gettinoriginal on 2009-04-30
New update, started over with clean install of 8.04 (only disk I had), then upgraded to 8.10.  All was still stable with no "Address not Found" or 404 errors.  Decided since I was starting over anyway, to try Upgrading to 9.04 instead of a clean install (tried 3 different disks from 3 different mirrors), and viola, I have 9.04 working flawlessly, including sound/video, no 404 errors, or "Address not found".  So I guess the secret to success on here is to upgrade if you have a working system, not a fresh install.:P

---

### Post by longtom on 2009-04-30
Coming back to the ipv6 issue and it's permanent removal.

I quote from Keir Thomas' Book "Ubuntu Kung Fu", which I recommend to everybody, experienced or not, as part of your standard library as far as Ubuntu and Linux is concerned.  It is worth every cent.

Here it goes:

> 
1. Open a terminal window and type gksu gedit /etc/modprobe.d/aliases.
   In the Gedit window, look for the line that reads alias net-pf-10 ipv6
   and change ipv6 to off, so it reads alias net-pf-10 off. Then save the
   file.
2. Open the /etc/hosts file in Gedit (gksu gedit /etc/hosts) and, after the
   line that reads # The following lines are desirable for IPv6 capable hosts,
   put a hash at the beginning of each line following that contains
   ip6 within it (so the first line will read #::1 ip6-localhost ip6-loopback;
   the second #fe00::0 ip6-localnet, and so on). See Figure 3.18 for how
   the file looked after editing on my test PC. Once done, save the file
   and quit Gedit.
3. Start Firefox and, in the address bar, type about:config. You can
   ignore the warning that appears about changing settings. In the
   Filter text field, type ipv6. Then double-click network.dns.disableIPv6
   so that it now appears in bold (and you might notice that, at the
   end of the line, false changes to true). Then close Firefox and reboot
   your computer.


---

### Post by Elfy on 2009-04-30
> **longtom said:**
> Coming back to the ipv6 issue and it's permanent removal.

I quote from Keir Thomas' Book "Ubuntu Kung Fu", which I recommend to everybody, experienced or not, as part of your standard library as far as Ubuntu and Linux is concerned.  It is worth every cent.

Here it goes:

That doesn't work in jaunty it seems - it's built into the kernel now. (see an earlier post too :) )

[http://ubuntuforums.org/showpost.php?p=6710941&postcount=7](http://ubuntuforums.org/showpost.php?p=6710941&postcount=7)

---

### Post by Elfy on 2009-04-30
Thread closed at OP request.

---

