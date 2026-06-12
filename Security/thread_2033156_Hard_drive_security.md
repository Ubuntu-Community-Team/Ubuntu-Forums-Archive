---
title: "Hard drive security"
date: 2012-07-25
forum: Security
---

### Post by emagar on 2012-07-25
I am relatively new to Linux. I recently broke something in the boot records of my SSD. I created a live USB and booted to attempt a fix. I then came to realize that I have no admin privileges in the live-USB system, so it would not let me do much about my problem (I tried running sudo e2fsck).

Hence my first question: (1) How can I log in as root from a live-usb?

And this begs another question: (2) Assuming that there is a way to achieve that described in (1), could anyone with a live-usb get access to my personal files if my laptop came to be stolen?

Thanks for your input.

---

### Post by ranger1021994 on 2012-07-25
>U can use command from terminal (attach sudo to your command)
>Unless you encrypted it...Yes anyone can view your files (try truecrypt for encryption)

---

### Post by emagar on 2012-07-25
> **ranger1021994 said:**
> >U can use command from terminal (attach sudo to your command)


Thanks Ranger. That is what I attempted. Attaching 'sudo' in the terminal before the command prompted for the password that I do not have. I must be doing something wrong when I boot from live-usb... How can I gain superuser privileges?

Thanks again.

---

### Post by emagar on 2012-07-25
> **ranger1021994 said:**
> >Unless you encrypted it...Yes anyone can view your files (try truecrypt for encryption)

So a system password is really of secondary protection. All it takes to copy/modify files is to boot a machine with a live cd/usb? (Which, BTW, I still haven't managed to do successfully...)

---

### Post by cariboo on 2012-07-25
As has been said many, many times before, physical access is root access. The only way to protect your data from prying eyes, is to encrypt it.

---

### Post by emagar on 2012-07-25
> **cariboo907 said:**
> As has been said many, many times before, physical access is root access. The only way to protect your data from prying eyes, is to encrypt it.

Thanks Cariboo. 

So encryption it will be. I'll search that theme in the threads. 
In my case, however, I have been unable to get root access to my damaged drive with a live-USB. Searching the forum has led me to several threads covering how to make a USB bootable --- which I have done ok. I have found none indicating how to get root privilege after I select "Try Ubuntu" (ie., sudo requesta a password I do not have.) What am I doing wrong?

Any advice will be much appreciated.

---

### Post by Ms. Daisy on 2012-07-25
> **emagar said:**
> In my case, however, I have been unable to get root access to my damaged drive with a live-USB. Searching the forum has led me to several threads covering how to make a USB bootable --- which I have done ok. I have found none indicating how to get root privilege after I select "Try Ubuntu" (ie., sudo requesta a password I do not have.) What am I doing wrong?
Check this out

[http://www.psychocats.net/ubuntu/resetpassword/](http://www.psychocats.net/ubuntu/resetpassword/)

---

### Post by cariboo on 2012-07-26
> **emagar said:**
> Thanks Cariboo. 

So encryption it will be. I'll search that theme in the threads. 
In my case, however, I have been unable to get root access to my damaged drive with a live-USB. Searching the forum has led me to several threads covering how to make a USB bootable --- which I have done ok. I have found none indicating how to get root privilege after I select "Try Ubuntu" (ie., sudo requesta a password I do not have.) What am I doing wrong?

Any advice will be much appreciated.

Running development releases, I use a Live USB to make repairs when things go wrong all the time, and have never had to enter a password when using sudo. I have seen it happen to others, and it usually happens when your iso is corrupted or incomplete. I'd suggest you re-download the iso. I use the Startup Disk Creator utility to create my usb device.

---

