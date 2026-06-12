---
title: "security with ubuntu live dvd"
date: 2013-03-19
forum: Security
---

### Post by rchubcitywihwy1480 on 2013-03-19
according to info on the directions on the ubuntu live dvd session, it says that the computer may be compromised by doing this?  why would one want to take this chance?

Security and Updating

While linux systems are more secure than Windows, LiveCD sessions are not meant for long-term use nor for sessions lasting several days. Because LiveCDs can't easily be updated, they may well be vulnerable to security issues discovered in the months since their release. They also can't protect you against scams such as phishing. If a criminal broke in to your live session, any changes he made to your session would be reset along with everything else when you reboot, although he could make permanent changes to the computer's hard drive.

A persistent image can be updated as new security issues emerge, but also lets any damage done to your computer persist across sessions.

---

### Post by deadflowr on 2013-03-19
A reason live session are less secure than an install is because live sessions don't need a password to gain root.

---

### Post by Old_Grey_Wolf on 2013-03-19
Moved to Security Discussions sub-forum. Should get better answers about security there.

---

### Post by rchubcitywihwy1480 on 2013-03-19
so i'd assume it is not the best thing to do?

---

### Post by Old_Grey_Wolf on 2013-03-19
The advice you quoted is not entirely true. Wait for relies from the security forum before making an assumption like that.

> **rchubcitywihwy1480 said:**
> so i'd assume it is not the best thing to do?

> **rchubcitywihwy1480 said:**
> While linux systems are more secure than Windows, LiveCD sessions are not meant for long-term use nor for sessions lasting several days. Because LiveCDs can't easily be updated, they may well be vulnerable to security issues discovered in the months since their release. They also can't protect you against scams such as phishing. If a criminal broke in to your live session, any changes he made to your session would be reset along with everything else when you reboot, although he could make permanent changes to the computer's hard drive.

---

### Post by rchubcitywihwy1480 on 2013-03-19
> **Old_Grey_Wolf said:**
> The advice you quoted is not entirely true. Wait for relies from the security forum before making an assumption like that.

comes from here

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Figure 5: 10.04 login screen

Security and Updating

While linux systems are more secure than Windows, LiveCD sessions are not meant for long-term use nor for sessions lasting several days. Because LiveCDs can't easily be updated, they may well be vulnerable to security issues discovered in the months since their release. They also can't protect you against scams such as phishing. If a criminal broke in to your live session, any changes he made to your session would be reset along with everything else when you reboot, although he could make permanent changes to the computer's hard drive.

---

### Post by haqking on 2013-03-19
> **rchubcitywihwy1480 said:**
> comes from here

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Figure 5: 10.04 login screen

Security and Updating

While linux systems are more secure than Windows, LiveCD sessions are not meant for long-term use nor for sessions lasting several days. Because LiveCDs can't easily be updated, they may well be vulnerable to security issues discovered in the months since their release. They also can't protect you against scams such as phishing. If a criminal broke in to your live session, any changes he made to your session would be reset along with everything else when you reboot, although he could make permanent changes to the computer's hard drive.

Are you asking the question from your OP ?

Why use it ?

Because it is to see if you like it and it works mostly with your hardware and needs.

As it states in the quote you posted:
> 
LiveCD sessions are not meant for long-term use nor for sessions lasting several days

---

### Post by rchubcitywihwy1480 on 2013-03-19
but it states this also

"although he could make permanent changes to the computer's hard drive."

---

### Post by CharlesA on 2013-03-19
> **rchubcitywihwy1480 said:**
> but it states this also

"although he could make permanent changes to the computer's hard drive."

Boot a liveCD and you can access any drives in the machine.

Unless you have a specific reason for using a livecd (testing/troubleshooting), don't bother.

---

### Post by rchubcitywihwy1480 on 2013-03-19
so your advice is not to run a live dvd to run ubuntu, to be on the internet etc?  only use it to trouble shoot?

---

### Post by CharlesA on 2013-03-20
> **rchubcitywihwy1480 said:**
> so your advice is not to run a live dvd to run ubuntu, to be on the internet etc?  only use it to trouble shoot?

Unless you are running an up-to-date "livecd" you risk more by using out of date software than you do by using an up-to-date OS.

---

### Post by zemega on 2013-03-20
Instead of live dvd, you will be better off permanent install ubuntu on a thumbdrive if you just want to surf the internet and do some basic stuff. 16GB one should be enough,32GB if you wish to use lots of programs. It will be faster and you can just plug it in any other computer or platform (that includes tablets as well.).

---

### Post by tubbygweilo on 2013-03-20
> **zemega said:**
> Instead of live dvd, you will be better off permanent install ubuntu on a thumbdrive if you just want to surf the internet and do some basic stuff. 16GB one should be enough,32GB if you wish to use lots of programs. It will be faster and you can just plug it in any other computer or platform (that includes tablets as well.).

As I expect Ubuntu on a thumbdrive can be keep up to date with the latest Ubuntu supplied security updates which seems to be a good idea.

---

### Post by CharlesA on 2013-03-20
> **tubbygweilo said:**
> As I expect Ubuntu on a thumbdrive can be keep up to date with the latest Ubuntu supplied security updates which seems to be a good idea.

Only if you create it with persistence. Otherwise it acts just like a livecd.

---

### Post by kurt18947 on 2013-03-20
Perhaps I did something wrong but I've tried running updates on a liveUSB with persistence.  The install failed sooner or later.  I found that things like bookmarks, network settings, preferences worked fine with persistence.  Trying to update the O.S. system files did not.  At least that was my experience.  On the other hand, I've formatted USB flash drives to ext2, unplugged the hard drive to save any "oopses" and did a 'real' install on the flash drive.  I was able to update that and it behaved like a (slow) 'real' install.  I've also noticed when browsing flash drives that some are labeled bootable, some are not.  I used ext2 to reduce the number of write cycles, I probably could have used ext4 with jounaling disabled but didn't know how to do that.

---

### Post by rchubcitywihwy1480 on 2013-03-20
> **zemega said:**
> Instead of live dvd, you will be better off permanent install ubuntu on a thumbdrive if you just want to surf the internet and do some basic stuff. 16GB one should be enough,32GB if you wish to use lots of programs. It will be faster and you can just plug it in any other computer or platform (that includes tablets as well.).

 Quote Originally Posted by rchubcitywihwy1480 View Post
so your advice is not to run a live dvd to run ubuntu, to be on the internet etc? only use it to trouble shoot?
Unless you are running an up-to-date "livecd" you risk more by using out of date software than you do by using an up-to-date OS. 
----------------------------------------------------

The reason for burning the iso was to try ubuntu without install,  but if it is going to put one at risk,,i can't do that.

---

### Post by CharlesA on 2013-03-20
Like it was said earlier.. It is fine for *testing* just not if you are going to run it all the time.

---

### Post by rchubcitywihwy1480 on 2013-03-20
I guess the way i read it, it makes your system compromise-able regardless.

---

### Post by haqking on 2013-03-20
> **rchubcitywihwy1480 said:**
> I guess the way i read it, it makes your system compromise-able regardless.

Everything is compromisable, including installed systems.

A live DVD is so you can see if you like it before installing.

---

### Post by rchubcitywihwy1480 on 2013-03-20
i will wait till i get another one to avoid an unknown

---

### Post by Ms. Daisy on 2013-03-20
> **rchubcitywihwy1480 said:**
> i will wait till i get another one to avoid an unknown
I don't understand what you're hoping to accomplish with the live CD. 

If you want to have a secure setup then read the stickies in this forum and the basic security wiki. 

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by rchubcitywihwy1480 on 2013-03-20
i gather that the purpose is to run it from the dvd without install, if that is  true, and leaves a vulnerability as stated, i have to much on 2 of my systems to risk a  a stated issue.

---

### Post by pfeiffep on 2013-03-20
I'm not certain that > [COLOR=#000000]leaves a vulnerability as stated[/COLOR] is intended to be interpreted as once you  boot from the live dvd and after testing boot to original OS that the vulnerability REMAINS. 
If the nature of your system(s) is so delicate or valuable it probably isn't a good idea to test anything on them, but rather have a 'test' system that mirrors on of the other 2 for complete testing and validation.

---

### Post by maglinu on 2013-03-21
Some distros I believe provide a livecd that by default boots into a user account (PCLOS for one I seem to recall) with a root password (root) to permit install.

You can make a fresh livecd from an up to date installation (eg with mylivecd on PCLOS, or remastersys). You'll finish up with a lot of useless cd's though.

---

### Post by pfeiffep on 2013-03-21
I use remastersys and I only have 2 dvds - one rw for each pc

---

### Post by coldcritter64 on 2013-03-22
> **CharlesA said:**
> Only if you create it with persistence. Otherwise it acts just like a livecd.
No persistence needed on a full installation to the usb stick itself (16 and 32 GB sticks mentioned above your post). Only problem is usb sticks can fail pretty quickly with all the read/writes of a full OS install. No issues with out of date software/security issues that the OP had though with a full install as earlier suggested (zemega's post).

---

### Post by CharlesA on 2013-03-22
> **coldcritter64 said:**
> No persistence needed on a full installation to the usb stick itself (16 and 32 GB sticks mentioned above your post). Only problem is usb sticks can fail pretty quickly with all the read/writes of a full OS install. No issues with out of date software/security issues that the OP had though with a full install as earlier suggested (zemega's post).

Ah, gotcha. Thanks.

I've always thought of USB sticks are the equivalent to livecds, not a full install.

---

### Post by coldcritter64 on 2013-03-22
> **CharlesA said:**
> Ah, gotcha. Thanks.

I've always thought of USB sticks are the equivalent to livecds, not a full install.
You can go either way actually 1. a live dvd on usb, with or without persistence or 2. do a full install to a usb. With the 2nd option the lack of security and updated OS aren't a problem for the OP; only problem is usb sticks have failed on me after a few months with the load of a full installation.

To avoid data/system losses because of hardware failures on a full usb installation, I regularly "dd" the usb stick to an image file (*.img). This is like a rolling backup, as a usb stick goes very "funky" very quickly if it fails :). Cheers.

---

### Post by nomenkultur on 2013-03-22
When I had my windows7 system compromised (read: totally utterly pwned by eastern european hackers) I used the ubuntu cd to be able to change passwords/send emails.


 I didn't want to alter anything in the hard drive so the police could run their forensic tools.

 Here's the best method IMO:

  dump the live cd into ram  (boot parameter  to_ram I believe)

  activate firefox's aa profile

   download a firewall and harden it 

  
   now how can they compromise your system? what services are they going to exploit? how can they exploit anything?

  even without a root password a live session is secure enough

---

