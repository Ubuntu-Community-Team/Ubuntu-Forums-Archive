---
title: "backing up entire system to tape"
date: 2008-09-04
forum: Server Platforms
---

### Post by Mrwasab1 on 2008-09-04
after a few weeks of installing configuring and troubleshooting, Ive got my server to a stage where i am happy with it, now i am having problems with my raid controller and i want to make a backup of my system before i start messing around with my raid.
A friend a mine gave me a DDS4 tape drive and some brand spanking 20gb native 40gb compressed tapes.

I want to take a "snapshot" of my server as it is now and back it up to tape, should the worst happen i can simply reinstall, switch to single user mode and copy everything back.

I haven't had a lot to do with tapes before, so please tell me if ive got the wrong idea about how backing up to tape works.

Can anyone tell me or point me in the right direction as to how i would copy the entire system to a tape? or couple of tapes? im sure i shouldn't need more than 1 tho.

---

### Post by HermanAB on 2008-09-04
Install the tape drive and the mt-st tools.

Then use tar to backup everything except /dev, /sys, /proc and /tmp.

mt -f /dev/st0 rewind
tar -zcvf /dev/st0 /boot /root /usr /var /home

Hope that helps.

Herman

---

### Post by Mrwasab1 on 2008-09-18
thanks for the reply herman.
Quick question, what about /bin /etc /lib?

also how would i restore from tape? would i need to do a fresh install and then tar it back out of the tape?

---

### Post by jacobc2 on 2008-09-18
> **Mrwasab1 said:**
> thanks for the reply herman.
Quick question, what about /bin /etc /lib?

also how would i restore from tape? would i need to do a fresh install and then tar it back out of the tape?
/bin and /lib are normally just standared programs, I would add /etc to the backup as I'm guessing you have done a lot of custom configuring so your command would then be 

tar -zcvf /dev/st0 /boot /root /usr /var /home /etc 

to be honest you could also leave /boot off unless you have custom kernel or grub conf you want to save.

But if you are wanting to do a full system image as if you are going to recover everything from the tape you could just use

tar -zcvf /dev/st0 /

to resotre you want to use

tar -zxvf /dev/st0

heres a nice little tutorial that I used
[http://nic.phys.ethz.ch/readme/80](http://nic.phys.ethz.ch/readme/80)

Hope that helps

---

