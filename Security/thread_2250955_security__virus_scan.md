---
title: "security / virus scan"
date: 2014-11-01
forum: Security
---

### Post by afrohippie82 on 2014-11-01
Hi I was wondering if anyone had any information on how to go about getting some security/virus protection for Lubuntu 14.04 I'm totally a newbie can anyone help.

---

### Post by Bucky Ball on 2014-11-01
*Thread moved to **Security**.*

I've moved your thread here so you might have a better chance of support. Depending on what you're doing there's not a lot to worry about already. What kind of security protection are you after?

---

### Post by afrohippie82 on 2014-11-01
I'm after virus scaning and removal.

---

### Post by afrohippie82 on 2014-11-01
Has anyone had any experience Using ClamAV?

---

### Post by Bucky Ball on 2014-11-01
No, but you might find this useful:

[http://www.good-linux-tips.com/2014/04/installing-using-clamav-antivirus-linux.html](http://www.good-linux-tips.com/2014/04/installing-using-clamav-antivirus-linux.html)

And there are a heap of leads here:

[https://duckduckgo.com/?q=Using+ClamAV](https://duckduckgo.com/?q=Using+ClamAV)

(PS: Regular font size and style is fine, thanks. ;))

---

### Post by afrohippie82 on 2014-11-01
> **Bucky Ball said:**
> No, but you might find this useful:

[http://www.good-linux-tips.com/2014/04/installing-using-clamav-antivirus-linux.html](http://www.good-linux-tips.com/2014/04/installing-using-clamav-antivirus-linux.html)

And there are a heap of leads here:

[https://duckduckgo.com/?q=Using+ClamAV](https://duckduckgo.com/?q=Using+ClamAV)

(PS: Regular font size and style is fine, thanks. ;))


Thanks Bucky Ball i will look into these links to gain more knowledge....

---

### Post by Rob Sayer on 2014-11-02
You just don't get viruses on linux like you do in windows.  The linux permission levels work properly ... you may have thought you were the administrator in windows but you weren't really ... so it's too hard for viruses to spread.

I know people who have a lot more experience in unix/linux than I do.  Some have been making a living with it for 20 years.  None of them have a windows type AV program running in the background on their own systems.

You should still install clamAV if you're going to download a file that may end up on your or someone else's windows setup.  That's what I do, and I just use it as an on demand scanner.

That does NOT mean you can't be hacked.  Newbies should avoid installing from untrusted ppa's ... stick to the repos.  There's not only stuff in there that can make your system less stable (which isn't a security thing per se)  but can contain malware.

Use all the same precautions you'd use in any other OS.  Browser plugins etc.

Linux/unix is designed to be more secure because it was written form the start to be a multiuser OS.  That's largely why when you do a system update it also updates all your app software too.  That's an important security feature.

Some things are less obvious security features.  LIke if you mistype your login password it doesn't ask again immediately ... there's a 2 second delay.  This makes brute force remote attempts to guess your password much harder.

You don't actually even need a firewall running the way you need to in windows because linux doesn't leave unused ports open.  But you should probably still run one anyway, especially if you run torrent client programs a lot.  Ufw is already installed but it's a terminal program.  Install GUFW ... the GUI version ... and turn the firewall on.  The default settings should work fine.

Of course, you still need a strong password.

I didn't install linux because there are no known viruses.  IMHO the worst security thing you can do is install an OS or program because you think it'll make you hack proof.  The old saying that the biggest security problem is between the chair and the keyboard is true.  But I must admit I don't miss running AV scanners all the time.

---

### Post by HermanAB on 2014-11-02
Howdy,

The Microsoft support and update process is exceptionally bad.  They have enormous numbers of security bugs that never gets fixed.  They rely on third party band-aids and chewing gum to keep Windows together.  

In Linux, when a security problem is identified, there is a rush to fix the problem and an update is released within hours.  Therefore there are no working viruses and no need for scanners to detect malware and deploy band-aids.

---

### Post by deadflowr on 2014-11-03
> **afrohippie82 said:**
> Has anyone had any experience Using ClamAV?

Clamav is a command line version.You would probably be better served with the graphical version(frontend version) clamtk.

I've used it, and it works fine.
Two things to note

1) The version in the Ubuntu repositories is usually out of date, not that the virus definitions are out of date but that the interface tends to be. Since the database for the definitons is typically always up to date, the out of date graphical feature is probably not a big deal.
If you want everything to be up-to-date, then download the package from here
[https://code.google.com/p/clamtk/](https://code.google.com/p/clamtk/)
(If on Ubuntu 14.04;or variants like lubuntu, use the one for Debian/Ubuntu 13/14 DEB, I would point to another which would support Lubuntu's file manager but none seem to do that. So the basic version will probably suffice, though no file manager integration. (In normal Ubuntu that means you can scan a file or folder directly in the file manager, without the need to open clam)

2) Clam has a history of reporting false positives, so be wary of that possibility.

Hope this helps.
My 2 cents anyway

---

