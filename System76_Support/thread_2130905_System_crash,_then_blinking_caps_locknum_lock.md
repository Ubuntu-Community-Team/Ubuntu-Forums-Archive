---
title: "System crash, then blinking caps lock/num lock"
date: 2013-03-30
forum: System76 Support
---

### Post by cephalopoda on 2013-03-30
Hi,

I have a Lemur Ultra (lemu3), running Ubuntu 12.04. Recently my computer crashed twice without warning, and upon reboot the num lock and caps lock lights were blinking. There were no error messages. 

Could someone please help me diagnose the problem?

Thanks very much.

---

### Post by tgalati4 on 2013-03-30
Those lights indicate kernel panic.  If you can't boot, take the drive out and put it in a USB enclosure and read the log files (/var/log/syslog) on another machine.  Does the laptop have any cracks in the case?  Perhaps too much flexing of the motherboard?  While you have the drive out, now would be a good time to perform a backup.  Also flex the screen, in case there is a short in the screen cable that routes through the hinge.  In that case, hook up an external monitor to see if you get any farther into boot.

Can you boot with a Live CD/DVD?  If not, then I would suspect a serious hardware problem.

---

### Post by jbelmonte on 2013-04-01
It could also be a heat issue. If the laptop is overheated, a reboot without letting it cool off could result in a kernel panic. Get some compressed air and blow out the vents to make sure they are not clogged with dust.

---

### Post by cephalopoda on 2013-04-05
Thanks for the replies. Both times it happened I was able to reboot. However, now I am getting an error message every time I boot up (I'm not sure if it is related): "Sorry, Ubuntu 12.04 has experienced an internal error."

Any help is very much appreciated.

---

### Post by jbelmonte on 2013-04-05
Can you boot from a Live CD?

---

### Post by cephalopoda on 2013-04-07
> **jbelmonte said:**
> Can you boot from a Live CD?

Well now this is really getting bad. I tried to update to 12.10 but the computer froze, and when I restarted I lost the sidebar in unity, so I'm not able to make a live USB using the GUI. Is there a command line method for making a Live USB?

---

### Post by cephalopoda on 2013-04-07
Ok, I managed to get 12.04 on a liveUSB, however when I try to boot into it I get "Machine Check Error" and an automatic reboot. Any suggestions?

---

### Post by Edward_G_Prentice on 2013-08-28
I just got my Bonobo/bonx7 today, and twice tonight I got the same symptom (system freeze, caps & num lock blinking). That's twice in about four hours.

---

### Post by Edward_G_Prentice on 2013-08-29
It has now happened four times in 5.5 hours. Each time the system rebooted OK. I ran fsck to check for errors. I am disappointed with the reliability so far. Let's how System76 support responds.

---

### Post by isantop on 2013-08-29
This sounds like either software corruption (requiring reinstall) or a hardware glitch. If you run from a live disk, does the system still shut down?

---

### Post by Edward_G_Prentice on 2013-08-30
This symptom has disappeared for me, since then I've worked through a few more symptoms. Reinstalling ubuntu 13.04 seems to have eliminated the kernel panics. Knock on wood.

---

### Post by Telefreak on 2013-08-31
I have been having the same problem that Edward outlines... usually, I work out my own issues with the systems I build/buy, but as I received this yesterday and have had this happen 4 times, I wanted System76 support to know that more than one person is having the issue.  From my own support experience, I know that if you are hearing it from 2 or more, especially in just a matter of days, it is probably something you should look into.  I mean, if it was just myself and Edward, sure, it could be a situation where something moved out of place in shipping, but I don't think that is the case.

At any rate, I am about to reinstall the OS rather than use the "out of the box" installation.  Will update if it continues.

BTW, this is the most expensive computer I have ever bought for myself, and for me, the first one that I didn't build.

To the System76 Support team: If it helps for logging purposes I bought a Bonobo Extreme, maxed out the RAM to 32GB and had a 750GB/8GB hybrid HD installed.  No other options were upgraded as part of the purchase.

Steve Campbell

---

### Post by Telefreak on 2013-08-31
OS Reinstall complete... I'll install a few apps that I use regularly, but will refrain from restoring my backed up files until I am confident that the issue is resolved... update to follow later.

Steve

---

### Post by Telefreak on 2013-09-01
Update: 6 Hours and no blinking caps- or scroll-lock... I didn't add the System76 drivers, nor have I moved my personal files to the HD.  About to move files, and add 35K pics to Shotwell.  I believe the issue was driver related, and I have not been able to test all the devices yet.  However, it appears that sound and wifi currently work with no problem.  I don't use the microphone or camera, so I can't say that those drivers may have been included.

Also, in my initial installation/configuration of the Bonobo Extreme, I recovered my home directory from backup using "name@system:~$ cp /media/name/BackupDevice -Ruv .", so it is entirely possible that some configuration setting I had backed up from my old system didn't play well with the new system.

Steve

---

### Post by Telefreak on 2013-09-02
Update: 2 and a half days, still no kernel panic since reinstalling... seems to be resolved.

Steve

---

