---
title: "System is hacked"
date: 2013-12-10
forum: Security
---

### Post by Sheyl_Karakas on 2013-12-10
Hi all!

I have an issue. There has been a hacker on my network at home. I have a Windows machine and an Ubuntu machine. I've cleaned my Windows machine, but I cannot access my Ubuntu machine anymore because my password has been changed.
I've read that I can change it again by booting it in recovery mode, login as root and change the password using the root user. But when I try to boot it in recovery mode, the system stops. I cannot logon as root. 

Can anyone help me?

---

### Post by kulen19 on 2013-12-10
Well, you can do it quick and dirty, and do a fresh install, which will remove the  Ubuntu installation. Probably the safest alternative. Use another computer and load an ubuntu .iso to a USB-stick, using i.e. [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) . Good luck

---

### Post by bashiergui on 2013-12-10
How do you know you have a hacker on your network?

---

### Post by hakermania on 2013-12-10
> **bashiergui said:**
> How do you know you have a hacker on your network?

Well, the Ubuntu password was changed?

---

### Post by Sheyl_Karakas on 2013-12-10
I had a virus on my Windows machine and a lot of mal and spyware suddenly. After cleaning up that one, I had to log on my ubuntu (xbmcbuntu) machine to copy files from there. I couldn't... So that's why...

---

### Post by bashiergui on 2013-12-10
Hmm. Do you have a backup of the data on the ubuntu machine?
Is the ubuntu machine still plugged into the network? If it is then unplug the ethernet cord.

---

### Post by bashiergui on 2013-12-10
A few other questions: when you say you "cleaned up the Windows machine" what exactly does that mean?


Are there other computers on this network?


What services were running on both machines?

---

### Post by Sheyl_Karakas on 2013-12-17
Nope, I don'te have a backup of the Ubuntu machine, nor the Windows machine.
The Ubuntu machine is my HTPC, running on XBMCbuntu. It only has movies and TV shows on it. And yes it's still plugged into my network...

The only other devices on that network are my Windows laptop and PS3/PS4.

Running services on XBMCbuntu are OSCAM, TVHEADEND, XBMC, Couchpotatoe, Sickbeard, SABnzbz and Spotweb

With cleaning up my Windows laptop I mean I've ran Hijackthis and some other tools to clean up malware/spyware. I've been assisted by [www.hijackthis.nl](www.hijackthis.nl)

---

### Post by bashiergui on 2013-12-17
There's no time like the present ;) Back up the files and data on Windows onto an external drive or DVD or something. Then I would HIGHLY recommend you reimage the windows machine. I would never trust that I got it all.

*UNPLUG THE ETHERNET CORD TO UBUNTU*. If you can't get into it, at least make it impossible for the bad guy to get in.

If you can't use recovery mode to get the password reset for Ubuntu, and you still can't log in with any password, then I don't have any solutions for you other than to reinstall Ubuntu. It would then be wise to then create a method for backing up Ubuntu data continuously in the future.

---

### Post by Sef on 2013-12-19
Psychocats has a tutorial on how to [reset your password]("http://psychocats.net/ubuntu/resetpassword").

---

### Post by staticx2 on 2013-12-29
I'm surprised no one suggested Ubuntu's live CD approach and rooting yourself that way. Would that be not an option and that I jumped the gun with a funny yet stupid suggestion?

---

### Post by SCBrisbane on 2014-01-08
How do you think they got in?

Is your 'buntu system full of messages like this in /var/log/auth.log?

Failed password for root from 124.35.54.185 port 53530 ssh2

---

### Post by Don_Stahl on 2014-01-08
[COLOR=#000000]Sheyl_Karakas, perhaps you can boot from a Ubuntu or Puppy or other live CD. Make the CD using Windows. Then perhaps you can copy your data from the Ubuntu machine. Of course, with a lot of media files you may need a big storage device... :(

If you can get the data off, then I would agree with the previous poster that a clean install is your best shot.

If you can't access the data from a live CD, then things get more complicated, I guess. You might try downloading specialized software such as the Trinity rescue disk:

[http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en](http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en) \

and try to boot from that. [/COLOR]

---

### Post by houstonbofh on 2014-01-11
1) If your linux box was actually hacked and not just broken, you simply can not trust it.  There are some VERY good rootkits out there that will never be found.

2) If you can not boot into recovery mode, you can boot a live CD and mount your drive.  At that pount you can use "chroot" to mount your old file system as a running system, but still running the live cd image.  then you can fix any passwords.

3) Look at /etc/shadow (You will need to do it as root, so use sudo) and the root account should look like this...
```
root:!:15899:0:99999:7:::
```
If it looks like this,
```
root:$6$YvsDcBp$vCjxd.EvFcRu3F/mIR.tqtrDyXQOne41eCkbq//tR8r1psChdHRD2V0i0ILhABrZfuzwXIp1TZ658p9mnvZJm.:15899:0:99999:7:::
```

Then you have been given a root password.  Change it back to lock them out. (Assuming no other rootkits, which ain't likely)

---

