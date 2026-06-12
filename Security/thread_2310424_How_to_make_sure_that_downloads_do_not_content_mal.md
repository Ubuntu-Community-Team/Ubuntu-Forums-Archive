---
title: "How to make sure that downloads do not content malware."
date: 2016-01-19
forum: Security
---

### Post by juan53 on 2016-01-19
Hi mates
I write this post because I realize that many kinds of downloads in Linux systems are downloaded and installed by ussing terminal. So, I have no idea of how to verify the content and the lack of malware.
And, in a some way related pair of questions: I pretend to install (concretely) Numix theme. Is it "trusty" (in the way, clean)? How safe is download themes from the web linked to "add more themes" option in the customization panel of Ubuntu?
Thanks for your time.

---

### Post by Bucky Ball on 2016-01-19
Anything you install from the official Ubuntu/Canonical repos is 'trusted'. Anything you install manually from a third-party site is at your own risk. You take responsibility. The apps might contain bad code, but very unlikely viruses.

If you are installing third-party PPAs and apps from third-party source on a regular basis expect crashes when there's a conflict (which Ubuntu can't do anything to resolve). 

As for downloading malware which is directed at Linux, unlikely. Downloading bad code in apps from third-party sources that will crash your machine, more likely.

About your only issue would be downloading files infected with a Windows virus, not apps, then transferring them to a Windows machine. A Windows virus in a file will be completely ignored by Ubuntu and will be of no consequence ... until you transfer it to a Windows machine. It will then infect the Windows machine.

Absently clicking on random links and advertisements in webpages or opening emails and attachments from people you don't know has much more chance of getting you into trouble. But that is not Linux specific.

'Common sense' are the key words here. Sure others will join in to tell you what firewalls and what-not you should run on Ubuntu. I haven't used one in eight years. :)

---

### Post by juan53 on 2016-01-19
Thanks for the answer. I noticed that Linux systems let you breathe, in comparation of Windows Systems (which almost all "free" program brings a "gift"). But, is't there some way to check the integrity and lack of malware of pacages? I've know the existence of "md5sum" command to check integrity from website, once you've downloaded that into your system, and before installing. But could I do the same on pacages installed by terminal? Could I make an anti-virus or online scanners to check that pacages?Thanks a lot!

---

### Post by maglin2 on 2016-01-19
If you want to run an AV for 'peace of mind' then you can.

Here are some reviews:

[https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/](https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/)

[http://www.av-comparatives.org/linux-reviews/](http://www.av-comparatives.org/linux-reviews/)

The only one in the repositories is Clamav.

As has been pointed out above, this is not likely to really add much to linux security.

---

### Post by Bucky Ball on 2016-01-19
Yea, ClamAV is fine. Install that from Software Centre, as mentioned. Update the virus definitions regularly with:

> sudo freshclam

... in a terminal.

---

### Post by maglin2 on 2016-01-19
If you decide to install ClamAV please don't use it to scan for PUA (Potentially Unwanted Applications). You will get false positives, a known one of which is a system file that will break your OS if deleted or quarantined.

To my mind the greatest contribution to desktop security comes from having a good back-up system for your personal data (documents, emails, calendars, photos etc). Reinstalling Ubuntu OS is fairly quick and easy. Recovering lost data is sometimes impossible.

---

### Post by juan53 on 2016-01-21
Thanks a lot. :)

---

### Post by kurt18947 on 2016-01-21
> To my mind the greatest contribution to desktop security comes from  having a good back-up system for your personal data (documents, emails,  calendars, photos etc). Reinstalling Ubuntu OS is fairly quick and easy.  Recovering lost data is sometimes impossible. 				

Take that to heart. Ubuntu comes with a backup prog installed and there are others available. After installing and updating (and updating and updating) Windows, Ubuntu is a dream but losing documents, photos and such can be a nightmare.

---

### Post by HermanAB on 2016-01-23
Howdy,

My tuppence worth:
Code downloaded from the official repositories of recognized Linux distributions can be trusted to be good.

Code downloaded from other sources can generally be trusted if it is a one-man-show computer geek that you heard about from another trusted source.  You go to the guy's web site, read up about him, do some googling, then 'cast your bread on the water', download and compile his code on a virtual machine (that is what Virtualbox is for!) and see if it works.  If it doesn't work, then it is usually an honest to goodness bug and not malicious.  If you think you know what you are doing, then you can report it to the guy and hear what he says, maybe he'll help you to make it work, if he has the time to spare.  People do this for mental stimulation in between whatever else they are doing, so don't expect a quick response - it may take a few days - unless maybe if the guy is already retired and just doing this for fun.

---

