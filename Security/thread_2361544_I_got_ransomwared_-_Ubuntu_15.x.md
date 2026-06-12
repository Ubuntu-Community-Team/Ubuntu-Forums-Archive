---
title: "I got ransomwared - Ubuntu 15.x"
date: 2017-05-17
forum: Security
---

### Post by mstenkil on 2017-05-17
Hey all,

I had a machine running a small family server in a commercial server farm, the hardware was failing and I could not reboot it (but hey, it ran great!) as a consequence, it stayed on Ubuntu 15.  I did run security upgrades on it "every now and then" -this morning I noticed mail wasn't working right - when I ssh'ed into the machine this is what I was greeted with.

Last login: Wed May 17 15:15:58 on ttys001
Martins-MBP:~ martin$ ssh kanon.net
<snip>'s password: 
****************************************!WARNING!*********************************************
******************************YOUR SERVER ARE INFECTED****************************************
*******ALL YOUR DATABASES, SITES AND USERS HOME DIRECTORIES HAVE BEEN ENCRYPTED***************

==============================================================================================
YOUR UUID IS : 726349278347239749328749237041988979623988102984432098203143998724235434532029
==============================================================================================


If you want to restore your files, send your UUID to e-mail: <snip>
You have to pay for decryption in Bitcoins. The price depends on how fast you write to 
us. After payment we will send you the decryption tool that will decrypt all your files.

FREE DECRYPTION AS GUARANTEE
Before paying you can send to us up to 1 files for free decryption.
Please note that files must NOT contain valuable information
and their total size must be less than 1Mb

**********************************************************************************************
**********************************************************************************************
****************************************!WARNING!*********************************************
-bash: cannot create temp file for here-document: No space left on device
martin@zero:~$ 

I created a dummy web mail address and sent them a mail, they wanted 1.5 Bitcoin (roughly USD 2700) to unlock it (wasn't going to pay out of principle - and def NOT that kind of amount)

Anyway - this post is just a FYI. I fully realize that since I was running an older version of Ubuntu - and I haven't been running updates for a few weeks, this is my own fault.
if anyone want a login to the server to try and fool around (in the name of science) just pm me. I couldn't even get in ...but I am sure there are a lot smarter people than me around here.

although mail and ssh stopped working, the machine is not fully frozen. I am able to open webmail and view all mail received up until last night - so I am not even sure the box is as fully compromised as they claim.

Anyhoo - it did kinda make me want to cry

---

### Post by juan53 on 2017-05-17
I suppose that you want to retrive your data.

Well, if your data really is encripted, there is little to do for it except paying. In such case, you should take all out of the platform and reinstall the machine. But if it is only a nasty banner, there is something to do.
In such case you can create a live-USB of the distribution of your choice and you should be able to retrieve the documents. After doing so, reinstall the machine.
If you have difficulties with the usual tools, there are a couple of forensic distros which have tools for those purposes.

All of these are highly recomended:
[http://www.deftlinux.net/](http://www.deftlinux.net/)
[http://www.caine-live.net/](http://www.caine-live.net/)

It's esential you can reboot the machine. If you can't do anything for it.

Best wishes.

---

### Post by HermanAB on 2017-05-18
Howdy,

In my experience, 99% of the time a Linux machine gets infected simply because someone used a kewl four character password.  

You can actually enforce long passwords (at least 12 chars) with PAM.

Usually, it is easier to re-install a machine than to attempt to clean it up.

---

### Post by ajgreeny on 2017-05-18
You do, of course, have backups, don't you?

If so, simply wipe the disk, reinstall and restore the backups.  If not this will, unfortunately, be a lesson learned the worst way possible.

---

### Post by mstenkil on 2017-05-19
Hey all,

I really just posted this as FYI - there is no backup and while it sucks it was a low priority machine - mostly doing mail for family members who had their local copies in their outlook/mail/etc

That being said - thank you for the kind words and suggestions :)

I did manage to get into the machine and see that the majority of files has an added .enc to them and is full of encrypted data.

As far as I am concerned, its dead :) I moved the family members over to a gmail $5/month thingy

Martin

ps: still not sure how they got in - I am the only sudo user and do not  use a 4 letter password, but like I said originally - I do not believe the machine was up to date with security patches.

---

### Post by Habitual on 2017-05-19
> **mstenkil said:**
> when I ssh'ed into the machine this is what I was greeted with.
```
bash: cannot create temp file for here-document: No space left on device
``` a here-document on login is curious.

You didn't even see all of the 
```

****************************************!WARNING!* ********************************************
```as you ran out of disk space.

Look at all the open ports!

---

### Post by #&amp;thj^% on 2017-05-19
Wow the first I have seen this here,
Now I have not tried this...but looks promising>>[http://www.zdnet.com/article/how-to-fix-linux-encoder-ransomware/](http://www.zdnet.com/article/how-to-fix-linux-encoder-ransomware/)
It would be nice to see a success story with this.
Still very sad to see this happening at all.
Kind Regards

---

### Post by oldos2er on 2017-05-19
As I'm sure you know now both 15.04 and 15.10 are EOL. This is why we always recommend upgrading before a version loses support; just like making backups, it saves a lot of grief.

---

### Post by LastDino on 2017-05-19
Thank you for posting this. 

I've no suggestions or kind words, but this is going to serve as a useful reminder for my friends from uni who get careless with Linux thinking it is immune to virus and malware. A real case actually helps things understand better.

---

### Post by linuxyogi on 2017-05-25
> **Habitual said:**
> a here-document on login is curious.

You didn't even see all of the 
```

****************************************!WARNING!* ********************************************
```as you ran out of disk space.

Look at all the open ports!

+1

Which ports were open ?

---

### Post by bashiergui on 2017-05-29
> **mstenkil said:**
> ps: still not sure how they got in - I am the only sudo user and do not  use a 4 letter password, but like I said originally - I do not believe the machine was up to date with security patches.
Looks like it could be **Crypt0locker/torrentlocker** (which disappeared last year but then came back).
[https://www.bleepingcomputer.com/news/security/new-torrentlocker-crypt0l0cker-variant-released-that-encrypts-files-with-the-enc-extension/](https://www.bleepingcomputer.com/news/security/new-torrentlocker-crypt0l0cker-variant-released-that-encrypts-files-with-the-enc-extension/)

or maybe **cryptoboss** (which I'd never heard of until I googled this bit in your ransom note "Before paying you can send to us up to 1 files for free decryption") That line is identifying as it's not used in most ransomware.
[https://www.enigmasoftware.com/cryptobossransomware-removal/](https://www.enigmasoftware.com/cryptobossransomware-removal/)

Both of those target Windows users afaik. It wouldn't surprise me to learn someone adapted existing ransomware for linux servers though.

How it got infected: were you running samba on this machine (meaning did you have port 445 open)?

---

### Post by TheFu on 2017-05-31
> **oldos2er said:**
> As I'm sure you know now both 15.04 and 15.10 are EOL. This is why we always recommend upgrading before a version loses support; just like making backups, it saves a lot of grief.

This ^^^^^^^^^^^^^^^^   +1000!

Don't run unsupported releases. Ever.
Always have versioned backups.

Your email server was hacked.  Never use those email addresses again.

If your family is like most normal people, they need to quickly change all their financial account contact emails ASAP!!!  This is how bank accounts are taken over and identities are stolen.

Ubuntu has very clear support periods for different releases. This page has timelines for each Release  [https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) . 

If you are installing a server today, it should be on 16.04.1 (or 16.04.2).  The .2 version will need to be dist-upgraded around August of this year and every year to maintain support.  The .1 version just needs weekly safe-upgrade patching until support ends in May-ish 2021.   Pick the correct release to make your life easier.  NEVER pick an odd year release to run a server without expecting to upgrade the complete release every 6 months.

If you don't patch weekly, expect your server to be hacked. It really is that simple.  Every week it isn't hacked is pure luck.  There have been some really nasty remote takeover issues since support for 15.xx releases lost support in early 2016. The fact that it took this long to be hacked is just luck.

IMHO.  BTW, I've had servers hacked twice since becoming an admin - last time was 2002. Be diligent.

---

