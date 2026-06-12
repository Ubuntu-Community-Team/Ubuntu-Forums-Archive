---
title: "Why can't I unlock an image recovery of encrypted disk, despite using the correct pw?"
date: 2016-12-16
forum: Security
---

### Post by koampapapa on 2016-12-16
[COLOR=#111111][FONT=Ubuntu]My understanding of the Linux encryption protocol is that the keys are "distributed" over the entire disk, so even a tiny amount of damage can cause a significant amount of casualty. In particular, damage to the "master key" (not the password) basically renders the device non-functional unless you have a backup. I am talking here about **hard disk encryption** (at boot), not home directory encryption.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After mounting my device, the error I receive is familiar:[/FONT][/COLOR]
Command failed with code 1: No key available with this passphrase.
[COLOR=#111111][FONT=Ubuntu]Assuming that *I am* using the same password, what else could cause this error? My disk image appears to contain a valid version of the header.[/FONT][/COLOR]
> cryptsetup -v luksDump /dev/sdb5
LUKS header information for /dev/sdb5

Version:        1
Cipher name:    aes
Cipher mode:    xts-plain64
Hash spec:      sha1
Payload offset: 4096
MK bits:        512
MK digest:      23 97 8b 80 e5 92 5a 2f dd c8 cf d9 c0 d1 e7 42 7c bc 3e 4f 
MK salt:        05 a5 10 62 46 45 36 8a 89 13 f1 94 0f 4b 9a 39 
                16 ca e0 f9 47 45 fd 0c 1b e0 bd e9 40 c4 91 d3 
MK iterations:  40500
UUID:           ef71756f-2724-4f44-90ed-29ddb760e73c

Key Slot 0: ENABLED
    Iterations:             161615
    Salt:                   f9 ad 13 c6 26 7f 59 c2 72 81 99 4f 67 b9 19 9e 
                            17 bc 17 75 96 d4 7d dd 74 4a d0 87 c7 b8 8d 95 
    Key material offset:    8
    AF stripes:             4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED
Command successful.
[COLOR=#111111][FONT=Ubuntu]I have actually been at this for a while and have a number of theories about what could've happened. **Please help me knock these down to the most likely solution.**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1) The damage to the hard disk caused the encryption keys to change.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2) I encrypted the disk on Ubuntu 14.04, and am trying to load it on Ubuntu 16.04. Because my password uses special characters, some input protocol is fudging this. In a number of projects I've done, strings containing "!" tend to confuse the command line. So I'm wondering if that could be happening here.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]3) I encrypted the hard disk on one device, but am trying to load it on another device. See special characters comment in #2[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]4) I'm inputting the incorrect password[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]5) An attacker invaded my machine and re-encrypted it with an alternative password.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]6) ... Other? Maybe it's starting at the wrong bit when reading the key?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

I have cross posted this on another reputation-based Ubuntu forum, but it didn't get any bites.[/FONT][/COLOR]

---

### Post by TheFu on 2016-12-16
I think #2 is most likely.  Can you validate that the locale and console language is set to the same value?  
Another thing to try is using a file manager that understands LUKS and LVM to open the LV with the data. **caja** does.

BTW, I've pulled a 14.04 LUKS disk with LVM from 1 machine, placed it into an external enclosure and caja hasn't had any issues recognizing and opening the different LVs on it when the correct decryption key (I use 2FA) is entered.

---

### Post by koampapapa on 2016-12-17
Thanks for the quick reply. I have since tried with many different keyboard layouts so i don't think that's it. I will try with Caja and update back.

---

### Post by TheFu on 2016-12-18
> **koampapapa said:**
> Thanks for the quick reply. I have since tried with many different keyboard layouts so i don't think that's it. I will try with Caja and update back.

Don't confuse keyboard layout with locale.

---

### Post by koampapapa on 2017-01-03
My next post is about locales/caja. Sorry for double posting.

 I was wondering here if anyone could tell anything by the partition layout below. Specifically, sdc2 and sdc5 are the relevant partitions. One is an Extended disk, the other is Linux. However, the Linux one seems to start 2 bits later on the disk, but they weirdly run over the same area otherwise. Is that how it's supposed to be? Are they both supposed to take up the same space like that? I believe sdc5 is the true encrypted one:

```
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ef7d8

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdc1  *         2048     499711     497664   243M 83 Linux
/dev/sdc2          501758  976771071  976269314 465.5G  5 Extended
/dev/sdc3       976771072 3907028991 2930257920   1.4T 83 Linux
/dev/sdc5          501760  976771071  976269312 465.5G 83 Linux
```

---

### Post by koampapapa on 2017-01-03
This is a great post that might be of some help to others: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047384](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047384)
I do think I may have installed this one using Ubuntu 14. It may be worth trying to decrypt that way, somehow... 

As far as changing the locale... Right now I'm using the update-locale command. What's extremely annoying is that these locale changes only seem to take effect after a new login session? That is the case according to the man page. How do I get the locale to change just for a terminal, using the terminal? Also, is locale the same thing as language?

Right now my plan is to write a script to try and  programatically change the locales and maybe even the languages each  time I try to decrypt it using a grandmaster password file that I  haven't made yet. To do this I would be using luksOpen from the command  line. Is there a reason my time would be better spent trying to get it  to mount in caja? For example, does Caja do something like this  automatically for me?

This is what happens when I try to change my locale within a single terminal, then list my locale to see if it's changed. It doesn't update. Any clue how LANG, LANGUAGE, NUMERIC, and CTYPE are different? I can figure the others pretty well.
```
root@p:/media/p# update-locale LANG="en_AU.utf8"
root@p:/media/p# locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
root@p:/media/p# update-locale LANGUAGE="en_AU.utf8"
root@p:/media/p# locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

---

### Post by TheFu on 2017-01-03
```

Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ef7d8

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdc1  *         2048     499711     497664   243M 83 Linux
/dev/sdc2          501758  976771071  976269314 465.5G  5 Extended
/dev/sdc3       976771072 3907028991 2930257920   1.4T 83 Linux
/dev/sdc5          501760  976771071  976269312 465.5G 83 Linux
```

Please use code tags so things line up and are easy to read.

2 is the Extended partition - it is a form of "primary" partition.
5 is a "Logical Partition" INSIDE 2.  
1 and 3 are primary partitions.  Only 4 are allowed with MSDOS partitioning.  The "logical" partitioning is a hack to work around these limitations.  GPT (vs MSDOS) partition tables remove these limitations. I suppose there are limits, but well over 100 primary partitions are allowed. There aren't **any** logical partitions. GPT is required to access more than 2TB disks. Windows has some limitations around when GPT is required and when it can be used. Linux doesn't have those limitations.

Wouldn't know about 2 block differences. Only talking about 1KB. Could just be an alignment thing. Misaligned partitions can slow a disk down 30%.

Only mentioned caja because it is the only file manager I know that recognizes LVM and encrypted storage.  That doesn't mean other file managers don't too. I don't really use file managers, so I'm hardly an expert.

Really shouldn't be doing anything as root.

---

### Post by koampapapa on 2017-01-04
Thanks. I didn't know that about partitions. It does seem like things are set-up in order then. I think it's unlikely LUKS is starting from the wrong bit when reading the key. My initial research suggests if it were starting at the wrong place, I would not have a valid LUKS header to begin with. 

Currently going to move back to Ubuntu 14 and try things from there. Instead of changing the locales, I guess I can just focus on using the characters that change based on the locale (see link in last post; '#' can come up as a quotation mark, etc). I have already scanned over ~30% of the key space for this header based on my suggested passwords. Unfortunately my laptop shut down during the process. I will do another run focusing on only the commonly swapped characters.

I also need to check if the key slot is damaged somehow. I wasn't able to do that on ubuntu 16. Perhaps the script I was using will work on Ubuntu 14.

Sorry dumb question; why is it bad to do work as Root? I never really learned Ubuntu through a class; I just had a Windows laptop crash a while back and switched to Ubuntu because it was free and I enjoy it so so so much more.

---

### Post by ian-weisser on 2017-01-04
> **koampapapa said:**
>  why is it bad to do work as Root? 
Because humans make mistakes and typos. Root can be very unforgiving of those.

Every oldster has a horror story of a project or system they destroyed with a human mistake or typo while running as root.

---

### Post by TheFu on 2017-01-04
> **koampapapa said:**
> Sorry dumb question; why is it bad to do work as Root? I never really learned Ubuntu through a class; I just had a Windows laptop crash a while back and switched to Ubuntu because it was free and I enjoy it so so so much more.

Google can answer many questions: [https://askubuntu.com/questions/16178/why-is-it-bad-to-login-as-root](https://askubuntu.com/questions/16178/why-is-it-bad-to-login-as-root)
Just be certain you have the background to understand the answer.  

When I was new to Linux, I didn't have the appropriate background and got into all sorts of problems by copy/pasting stuff from other people who were
a) noobs themselves
b) experts and left out tiny details they assumed I knew

It is hard to tell the difference.  To get over the noob stage, it is best to work through some directed training.  LPI has some free training materials which are a good start. Linux Foundation and EdX do too.  I've put links and other suggestions on my blog - "Learning Linux" article.  Sadly, they explain "WHAT", but lack the "WHY."  The why comes from a mentor and/or experience.  Experience is another term for "oops" or "I screwed up."  ;)

There are many things which are possible, but often doing something because is *should work* is a bad idea.  It takes experience to recognize those things and experience with non-Unix OSes (or OSX) will warp your idea of what should work.  

Stupid things (that should work) get people into trouble all the time. This is because of the way that Linux gets put together by 1,000s of unpaid people from different parts of the world, not a single, controlling, company.  

Simple things to know:
* hostnames are all lowercase. In theory it shouldn't matter, but sometimes a bad script doesn't handle it. No underscores allowed. Dashes ok.
* userids are all lowercase. see above.
* Get hostname <--> IP lookups working for your network/home LAN. Lots of issues happen because client-a and server-b don't know each other as client-a and server-b. This is not a Linux thing. It is an IP thing.
* Don't use special characters or spaces in directories or files or Samba Shares or disk labels or .... anything. Where I want a space, I put an _.  Mixed case is completely, totally, supported here, however. Avoid special characters in those things too. Think Latin alphabet and numbers.
* passwords should accept **any** character. Just be aware that the locale often will change the encoding of the character, so being strange/mixed with locale/language settings can cause issues. I've had this issue accessing my password manager, BTW.
* Don't use plain FTP. Use sftp/scp instead.
* ssh is the swiss-army knife of connectivity. It can facilitate secure, convenient connections for file xfer, remote shell, remote desktop, remote windows, tunnels, proxies, remote editing, etc .... Just don't use passwords after the initial setup is finished (about 10 minutes, top).
* Don't use NTFS/FAT partitions. Use native Linux file systems unless there is an extremely good reason otherwise. There is 1 reason that is good - portable disks that have to be read by Windows.  Samba doesn't work as well with non-Linux file systems. Software development has issues with non-Linux partitions too. There are reasons this is true.

Do or don't do those things as you see fit.

---

