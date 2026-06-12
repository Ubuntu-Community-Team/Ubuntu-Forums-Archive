---
title: "clamav warning"
date: 2009-03-26
forum: Security
---

### Post by Sbarton on 2009-03-26
Hi all! After installing clamav and starting the program I get a warning message re- editing.
I have attached the message and would appreciate  how to deal with the editing so that I can update signatures.
Thanks and regards

---

### Post by cariboo on 2009-03-27
I'm not sure what config files you have to edit, but if you open an Applications-->Accessories-->Terminal and type:

```
sudo freshclam
```

It will update your Windows virus signatures and set up a cron job that checks for updates daily. Clamav does check for Linux viruses, but they are so rare in the wild, that there is a bounty on them.

Jim

---

### Post by the_phenom on 2009-03-28
Also, go download a newer version: [http://clamtk.sf.net]("http://clamtk.sf.net")

There are .deb files available.

---

### Post by hyper_ch on 2009-03-28
are you sure you even need antivirus?

---

### Post by Sbarton on 2009-03-28
Thanks for the replies!
*
caraboo907: I had tried that but no difference, shame but thanks!
*
the_phenom: I may well do that!
*
hyper_ch: playing safe with my XP dual boot!

If anyone else reads this I would like to have known what I needed to edit (see attachment above).
regards to all

---

### Post by Sbarton on 2009-03-28
As a update the link given by the_phenom gives a March22nd Latest News which includes a known bug which stops manual updates, but gives a workaround. The bug will be fixed.
Thanks again
regards

Add problem solved by downloading latest clamtk 4.1.1

---

### Post by WkenCouser on 2009-03-29
Hello,

I typed the command sudo freshclam.
I was informed that my version is out of date.
 sudo freshclam
ClamAV update process started at Sun Mar 29 10:50:21 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cld is up to date (version: 9179, sigs: 37725, f-level: 41, builder: sven)
Question 1:   How do I get the latest version?
Also when I look at the GUI for Virus Scanner is says that I have 0 signatures whereas according t the code above I have 500667 and 37725 signatures.
Question 2:    Do I have the signatures for Virus Scanner?

Thank you,
Ken

I am running Ubuntu 8.10 and I am gettting ready to replace my last Windows machine.

---

### Post by hyper_ch on 2009-03-29
don't you run AV on Windows?

---

### Post by thewolfman on 2009-03-29
Try Avast for Linux, it is an "on demand" only scanner but works for me, very simple to use and maintain. I cannot tell you how (if at-all!) effective it is but its free!.

---

### Post by the_phenom on 2009-03-29
> **WkenCouser said:**
> Hello,

I typed the command sudo freshclam.
I was informed that my version is out of date.
 sudo freshclam
ClamAV update process started at Sun Mar 29 10:50:21 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cld is up to date (version: 9179, sigs: 37725, f-level: 41, builder: sven)
Question 1:   How do I get the latest version?
Also when I look at the GUI for Virus Scanner is says that I have 0 signatures whereas according t the code above I have 500667 and 37725 signatures.
Question 2:    Do I have the signatures for Virus Scanner?

Thank you,
Ken

I am running Ubuntu 8.10 and I am gettting ready to replace my last Windows machine.

Don't worry about the ClamAV warning - when a new version is pushed, you'll be able to get it.
For the two questions, see the above post for upgrading to a new version of ClamTk. The version in the repositories is very old.

---

### Post by Chemical Imbalance on 2009-03-29
> **cariboo907 said:**
> Clamav does check for Linux viruses, but they are so rare in the wild, that there is a bounty on them.

Jim

Really?  That's very interesting.  I didn't know it included linux signatures.  I'll have to look this up.

---

### Post by swiftwood on 2009-03-29
> **the_phenom said:**
> Don't worry about the ClamAV warning - when a new version is pushed, you'll be able to get it.
For the two questions, see the above post for upgrading to a new versyeion of ClamTk. The version in the repositories is very old.

So it's not out yet?

I'm getting the same error.

I get the following when I try 
*sudo apt-get update*
I get the following
> Fetched 190B in 2s (74B/s)
Reading package lists... Done
W: GPG error: [http://volatile.debian.org](http://volatile.debian.org) etch/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC61E0B0BBE55AB3
W: You may want to run apt-get update to correct these problems


The update worked last time, I don't see why I would need a new key.

---

### Post by Sbarton on 2009-04-05
Apologies for not reposting. I have been away for a week on the south coast of England chilling out.No PC's no technology just a few beers/wine.
Oh! and with the wife!!

As for clamtk update the new version can be obtained here:
[http://sourceforge.net/projects/clamtk/](http://sourceforge.net/projects/clamtk/)

Oh!Yeah!, hyper_ch. AVG on one and Avast on another on windows.
It's called the Windows Syndrome! ;)

regards

---

