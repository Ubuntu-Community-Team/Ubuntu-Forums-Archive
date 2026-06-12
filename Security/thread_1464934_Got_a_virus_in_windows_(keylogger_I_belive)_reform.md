---
title: "Got a virus in windows (keylogger I belive) reformatted HD, still facebook hacked."
date: 2010-04-28
forum: Security
---

### Post by SyphonX67 on 2010-04-28
Hello Everyone, I recently had to install ubuntu 10.04 RC on my laptop (HP Pavillion dv2945se due to the fact that I got a virus on my computer. I believe it is a keylogger because my Facebook account has been hacked, I believe my email has as well. I heard that even if you reformat a harddrive, the virus could still sit there and apparently that is what happened to me. I belive the virus is still sitting on my computer somewhere and I have no idea how to be rid of it and keep my security. I installed RKhunter and Chkrootkit. Rkhunter reports warning files while checking my filesystem. I can post a log if need be. Please help me, I'm a freshman in highschool and want my life back. Thank you for your help and your time.

---

### Post by SyphonX67 on 2010-04-28
Here is my log file: 
[21:12:57]   Checking for SSH configuration file             [ Not found ]
[21:12:57]   Checking for running syslog daemon              [ Found ]
[21:12:57]   Checking for syslog configuration file          [ Found ]
[21:12:57] Info: Found syslog configuration file: /etc/rsyslog.conf
[21:12:57]   Checking if syslog remote logging is allowed    [ Not allowed ]
[21:12:57]
[21:12:57] Performing filesystem checks
[21:12:57] Info: Starting test name 'filesystem'
[21:12:57] Info: SCAN_MODE_DEV set to 'THOROUGH'
[21:12:58]   Checking /dev for suspicious file types         [ Warning ]
[21:12:59] Warning: Suspicious file types found in /dev:
[21:12:59]          /dev/shm/pulse-shm-4036988491: data
[21:12:59]          /dev/shm/pulse-shm-3614157495: data
[21:12:59]          /dev/shm/pulse-shm-2454063017: data
[21:12:59]          /dev/shm/pulse-shm-3178695942: data
[21:12:59]          /dev/shm/pulse-shm-3544865885: data
[21:12:59]          /dev/shm/pulse-shm-1299973828: data
[21:12:59]          /dev/shm/pulse-shm-1709560336: AmigaOS bitmap font
[21:12:59]          /dev/shm/pulse-shm-1001135989: data
[21:12:59]          /dev/shm/pulse-shm-3197394543: data
[21:12:59]   Checking for hidden files and directories       [ Warning ]
[21:13:00] Warning: Hidden directory found: /etc/.java
[21:13:00] Warning: Hidden directory found: /dev/.udev
[21:13:00] Warning: Hidden directory found: /dev/.initramfs
[21:13:36]
[21:13:36] Info: Test 'apps' disabled at users request.

---

### Post by CharlesA on 2010-04-28
Formatting would get rid of a keylogger or virus in Windows.

Change your passwords and you should be fine. Use a strong password and be careful about your browsing habits.

---

### Post by SyphonX67 on 2010-04-28
> **CharlesA said:**
> Formatting would get rid of a keylogger or virus in Windows.

Change your passwords and you should be fine. Use a strong password and be careful about your browsing habits.

I did reformat before installing ubuntu, yet my facebook account continues to be hacked regardless. How else are they accessing my new facebook password when I change it?

---

### Post by CharlesA on 2010-04-28
If your email account is compromised as well, then they can just reset the password.

Have you changed both passwords?

If they have/had access to your email, they could have changed the email address that recovery info is sent to or changed the recovery questions.

---

### Post by OpSecShellshock on 2010-04-29
How many different computers/devices have you used to access Facebook? Have you removed all third-party Facebook applications attached to your profile? Have you set all of the privacy info on your account so it can't be indexed by search engines and can only be seen by your friends? How did you find out that your account had been compromised? Were you alerted about it in an email and then told to follow a link or download and install something in an attachment?

---

### Post by SyphonX67 on 2010-04-29
I use my ipod, cell phone* and Imac, to access facebook. That is it. I found out about the foreign access cause when I log into facebook. It goes through the recent activity thing in order that I can "restore my facebook acccount". It tells me that my facebook was attempted to be logged in from the Netherlands using Windows XP. That is all taht I know at this point.

---

### Post by CharlesA on 2010-04-29
Check [here]("http://www.facebook.com/help.php/?topic=security") and [here]("http://www.facebook.com/security?v=app_7146470109").

---

### Post by SyphonX67 on 2010-04-29
Ok, but what do I do about hte warning files from rkhunter? I'm looking into KillDisk, and then installing ubuntu again. Apparently, even when you reformat a harddrive, the virus could still be located on the CMOS battery or somewhere else on the Hard Drive.

---

### Post by CharlesA on 2010-04-29
If you are that worried about having a virus *somewhere* on the disk, even after formatting, just DBAN the thing.

As for the warnings, pulse-shm is part of pulseaudio. ./java, .udev and .initramfs are normal.

---

### Post by spynappels on 2010-04-29
That was discussed on these forums very recently, and the concensus(sp?) appeared to be that this type of attack which would inject code into your BIOS would have to be very targetted and not likely to be within the scope of someone who is interested in hacking your FB account.

A reformat as you described it will normally suffice to get rid of anything nasty infecting your machine.

---

### Post by uRock on 2010-04-29
> **SyphonX67 said:**
> I did reformat before installing ubuntu, yet my facebook account continues to be hacked regardless. How else are they accessing my new facebook password when I change it?

Have you reported this to Facebook?

---

### Post by SyphonX67 on 2010-04-29
How do I use DBAN?

---

### Post by uRock on 2010-04-29
[http://www.facebook.com/help/?page=797#!/help/?search=hacked%20account](http://www.facebook.com/help/?page=797#!/help/?search=hacked%20account)

---

### Post by SyphonX67 on 2010-04-29
I understand what DBAN does, but is it GUI or DOS/command line action?

---

### Post by cdenley on 2010-04-29
> **SyphonX67 said:**
> I understand what DBAN does, but is it GUI or DOS/command line action?

It is a text-based user interface on a minimal boot CD for erasing hard drives using very thorough methods which take a very long time and prevent any theoretical forensic data recovery attempt.
[http://sourceforge.net/project/screenshots.php?group_id=61951&ssid=39777](http://sourceforge.net/project/screenshots.php?group_id=61951&ssid=39777)

A little overkill for eliminating malware from a previous filesystem.

---

### Post by CharlesA on 2010-04-29
> **SyphonX67 said:**
> I understand what DBAN does, but is it GUI or DOS/command line action?
You boot off of the livecd and follow the on screen instructions.

---

### Post by SyphonX67 on 2010-04-29
Yeah I guess its a bit of overkill, but I dont mind, I was planning on completely erasing anyways. Also, I dont know if I should have a new thread for this but, I want to change my HD connection type from ATA to AHCI. I have a phoenix bios and when I boot into it I don't have advanced options and no options to change it. Any ideas? or I can also post a new thread.

---

### Post by CharlesA on 2010-04-29
Check mobo manual.

---

### Post by SyphonX67 on 2010-04-29
Unfortunately, I have no idea where that manual is, are the other ways to change such a setting from within ubuntu?

---

### Post by CharlesA on 2010-04-29
It is BIOS only unfortunately.

---

### Post by rookcifer on 2010-04-29
> **SyphonX67 said:**
> Hello Everyone, I recently had to install ubuntu 10.04 RC on my laptop (HP Pavillion dv2945se due to the fact that I got a virus on my computer. I believe it is a keylogger because my Facebook account has been hacked, I believe my email has as well. I heard that even if you reformat a harddrive, the virus could still sit there and apparently that is what happened to me. I belive the virus is still sitting on my computer somewhere and I have no idea how to be rid of it and keep my security. I installed RKhunter and Chkrootkit. Rkhunter reports warning files while checking my filesystem. I can post a log if need be. Please help me, I'm a freshman in highschool and want my life back. Thank you for your help and your time.

Not to be rude, but it isn't the job of these forums to clean up Windows boxes.

> I understand what DBAN does, but is it GUI or DOS/command line action

You don't need DBAN.  You already have the tools you need on the Ubuntu LiveCD.  Just pop it into your drive, open a terminal once it boots and type the following:

```
sudo shred -vfz /dev/sda

Where /dev/sda is the hard drive in question (it might be named something else).
```

You now have a clean HD.

---

### Post by Jive Turkey on 2010-04-29
> **SyphonX67 said:**
> Please help me, I'm a freshman in highschool and **want my life back.**

Stop using facebook for starters.  Go outside.

---

### Post by SyphonX67 on 2010-04-29
Yeah, I play soccer. I know, thanks for the help everyone.

---

### Post by uRock on 2010-04-29
Report to FB that your account has been hacked, then create a real password using nonsequencial letters, numbers and symbols. A simple uRock$910# would rate as a strong password on most meters. Until you can get your hard drive cleared up, download and burn Puppy Linux to disk and boot from it. It is one of the best LiveCDs I have used. Or, if you already have a LiveCD of ubuntu, use it.

---

### Post by CharlesA on 2010-04-29
Second Puppy. Even Knoppix is decent for a livecd.

---

### Post by OpSecShellshock on 2010-04-30
> **uRock said:**
> Report to FB that your account has been hacked, then create a real password using nonsequencial letters, numbers and symbols. A simple uRock$910# would rate as a strong password on most meters. Until you can get your hard drive cleared up, download and burn Puppy Linux to disk and boot from it. It is one of the best LiveCDs I have used. Or, if you already have a LiveCD of ubuntu, use it.
You could do something like this:

Install a password generator:

```
sudo apt-get apg
```

When that's done,

```
apg -a 1 -m 16 -M SNCL
```

That will give you 8 options for decent passwords. They won't be the sort you'll ever remember mentally, but you can practice typing it several times until you don't have to think about it, or you can allow Firefox to save it. I'd take care of the email password first, then do Facebook (with a different password). Plus in your home where you have private working space there's little risk in writing it down, so you could just do that.

---

