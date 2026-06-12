---
title: "ClamTk Virus Scanner?"
date: 2015-01-21
forum: Security
---

### Post by Daveski17 on 2015-01-21
I have noticed that the ClamTk Virus Scanner is in the Ubuntu Download Centre. Does anyone use this? Are there benefits, advantages or disadvantages to running an anti virus program on Ubuntu, any thoughts anyone?

Thanks, Dave.

[ClamTk SourceForge Page]("http://clamtk.sourceforge.net/")

---

### Post by deadflowr on 2015-01-22
Benefits = peace of mind, imo.
You cannot completely abandon behaviors you may have used running other systems, like Windows.
And the ability to scan your files for malware and viruses is a common thing on Windows, so it's nice to be able to do the same, on some level, in Ubuntu, if you want.

[Though viruses on Ubuntu, and linux in general, are few and far between, hence a general peace of mind. It can also help stop you from sending out bad stuff to others, who may not be running Ubuntu; who would otherwise be prone to the affects of said viruses]

(Clam has a nautilus extension so you can do quick scans on files.)
(I think it's called nautilus-clamscan...)

Outside of that two things about it would be:

1) the version in the repos is old and will show that it's out-of-date.
If you download the .deb from sourceforge and install that, it'll install as an upgrade(if you install from the repo first) and then the system will have a fully up-to-date version.

[If you forego the upgrade using the .deb package, the virus database, known as freshclam, does get updated frequently, but the engine and the interface do not, afaict, fwiw]

2)Now I haven't had these, but I have heard/read that clam is renown for producing false positives.
So if you did use it and keep seeing it flag known virus-free files, then you know it's the virus scanner and not those files.
Which might make you end up doing more about non-issue stuff than you would want to do.

Hope this helps, or at least makes sense.

---

### Post by mikodo on 2015-01-22
> **deadflowr said:**
>  snip

1) the version in the repos is old and will show that it's out-of-date.
If you download the .deb from sourceforge and install that, it'll install as an upgrade(if you install from the repo first) and then the system will have a fully up-to-date version.
+1 for the whole response.

It has been a long time since I used ClamAV but, I think it doesn't matter if the version is out of date, as long as one keeps the "freshclam" data base, current. 

(I have it on disk, and running on start up, as my bank demands that it's depositors who use on line services, have an anti-virus before they will insure security of transactions. I like my "Credit Union". I believe in it's philosophy and as such, having ClamAV, is really not a concern for me to be sure I live up to what they think is necessary, for me to know that my banking on line is guaranteed. If anything does happen, I can honestly tell them, that I use an antivirus program). That said, the security of it all remains, between they doing the encrypting for me, and my attending to my end of things, to not open my connection unsafely, and to properly keep my passwords secure off-line.

There, I missed the proceeding bracket ( [ ), in the end of the quote.

---

### Post by SeijiSensei on 2015-01-22
> I think it doesn't matter if the version is out of date, as long as one keeps the "freshclam" data base, current. 

No, sometimes ClamAV will complain that it's binary needs to updated as well as the malware definitions.

I can only see using ClamTK if you're allergic to the command line.  Otherwise you can just type:
```
sudo clamscan /path/to/windows/files
```
and let it go.  

Scanning Linux systems for viruses usually isn't very fruitful.  I use ClamAV to scan incoming messages on my mail server, but I don't bother to scan any of my Linux systems.  If you have a dual-boot system, you might try scanning the Windows partition as I suggested above.

---

### Post by sammiev on 2015-01-22
Bitdefender has picked up malware in FF on my linux system. It seems to work very well with Ubuntu.

---

### Post by mikodo on 2015-01-22
> **SeijiSensei said:**
> No, sometimes ClamAV will complain that it's binary needs to updated as well as the malware definitions.
I am sure that must be the case if, while paying more  attention to updates than I, you see that.

Thank you, for the correction.

Edit:

Of course I keep the updates current, but I tried this after many years of not even thinking about it:

> sudo clamscan ~/Downloads

No complaints there about updating, so I must be good.

---

### Post by Daveski17 on 2015-01-22
> **deadflowr said:**
> Benefits = peace of mind, imo.
You cannot completely abandon behaviors you may have used running other systems, like Windows.
And the ability to scan your files for malware and viruses is a common thing on Windows, so it's nice to be able to do the same, on some level, in Ubuntu, if you want.

[Though viruses on Ubuntu, and linux in general, are few and far between, hence a general peace of mind. It can also help stop you from sending out bad stuff to others, who may not be running Ubuntu; who would otherwise be prone to the affects of said viruses]

(Clam has a nautilus extension so you can do quick scans on files.)
(I think it's called nautilus-clamscan...)

Outside of that two things about it would be:

1) the version in the repos is old and will show that it's out-of-date.
If you download the .deb from sourceforge and install that, it'll install as an upgrade(if you install from the repo first) and then the system will have a fully up-to-date version.

[If you forego the upgrade using the .deb package, the virus database, known as freshclam, does get updated frequently, but the engine and the interface do not, afaict, fwiw]

2)Now I haven't had these, but I have heard/read that clam is renown for producing false positives.
So if you did use it and keep seeing it flag known virus-free files, then you know it's the virus scanner and not those files.
Which might make you end up doing more about non-issue stuff than you would want to do.

Hope this helps, or at least makes sense.

Thanks for the information and your opinion. I often scan files I download onto Linux with VirusTotal and Jotti's Virus Scan online. One of the reasons for my switch to Ubuntu was because of false-positives from over enthusiastic AV and anti-malware programs on Windows. These can often be more damaging than actual malware!

I'm a tad ambivalent about the approach to security on Linux. I employ browser hardening (NoScript, WOT *inter alia*) in combination with Adblock Edge, but old habits die hard. As you say; peace of mind. Part of me was considering some form of on-demand scanner. Having said that, the fact that this ClamTk in the repo is a bit out of date speaks volumes. I suppose I have to decide whether to risk potentially damaging false-positives against a percieved real malware threat. I'll have to think more about it. ;)

---

### Post by Daveski17 on 2015-01-22
> **sammiev said:**
> Bitdefender has picked up malware in FF on my linux system. It seems to work very well with Ubuntu.

OK, thanks for the info.

---

### Post by SeijiSensei on 2015-01-23
> **mikodo said:**
> No complaints there about updating, so I must be good.

Usually I see these warnings in the log files, especially the log for freshclam.  They look like this:
```

ClamAV update process started at Thu Dec 18 04:19:01 2014
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.98.4 Recommended version: 0.98.5
DON'T PANIC! Read http://www.clamav.net/support/faq

```

---

### Post by greg69 on 2015-01-25
Personally I've never seen the need for an anti-virus program. Ubuntu and other flavours of linux are naturally built to resist viruses. 
Also, I tried ClamTK. It was a nightmare to use and I couldn't even get it to scan my home directory :(

---

### Post by bashiergui on 2015-01-25
> **SeijiSensei said:**
> Scanning Linux systems for viruses usually isn't very fruitful.  I use ClamAV to scan incoming messages on my mail server...How effective is it preventing malicious attachments?

---

### Post by lisati on 2015-01-25
> **bashiergui said:**
> How effective is it preventing malicious attachments?

Things might have changed in the couple of years since I've run a mail server, but I did receive the occasional message that was flagged as containing malware. Most of the unwanted mail I received could be stopped or trapped by other means, so it's possible that I missed a few....

---

### Post by SeijiSensei on 2015-01-26
The ClamAV database also has signatures for other types of malware besides viruses.  At one site, we also scan all inbound traffic over the web using [SquidClamAV]("http://squidclamav.darold.net/").  The most common things it catches are various JavaScript exploits.

I use [MailScanner]("http://www.mailscanner.info/") which has an array of anti-virus and anti-spam features beyond simply scanning with ClamAV and SpamAssassin.  We routinely block attached executable files without even scanning them.  It's been running at the same site I mentioned above scanning hundreds of messages daily.  The client has had a couple of viruses pop up in their network, but they have never come in via email or the web.  Most of the time it's people inserting infected USB sticks into their PCs.

---

### Post by Daveski17 on 2015-01-27
> **greg69 said:**
> Personally I've never seen the need for an anti-virus program. Ubuntu and other flavours of linux are naturally built to resist viruses. 
Also, I tried ClamTK. It was a nightmare to use and I couldn't even get it to scan my home directory :(

Thanks for your reply. I've resisted the temptation to test ClamTk and I believe it is superfluous anyway.

---

### Post by AllenGG on 2015-01-27
Previous comments are interesting. to wit :
**¨Personally I've never seen the need for an anti-virus program.(in) Ubuntu.......**
***................................oops !***
Lately I have been scanning with **ClamTK** _ every day._
On average  8 problems found.   normally I see:
[I]1. Java script stored
2. infected web page.
3. phishing bank
...others...malware etc.
T[/I]o be sure that they are NOT false positives I re.run ClamTK after removing the offense files.
Always zero left.  
........................................
So, the question is,  are others facing the same problems ?
Does anyone believe that I am only seeing false positives.?
and, **is there a better virus scanning program (app) ****available**** _?** The reason that Ubuntu uses 4.66 has been explained.

Personally I believe that the Internet has taken another wild turn.
gracias, Allen[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by maglin2 on 2015-01-28
> **AllenGG said:**
>  T[/I]o be sure that they are NOT false positives I re.run ClamTK after removing the offense files. Always zero left.   ]  That doesn't indicate whether they are FP.   They could also be PUP/PUA (which is enabled by default in ClamTk i believe)  Run clamscan from terminal with PUA disabled to test if they are PUA/PUP.  Submit to virustotal to see if they are FP.

---

### Post by AllenGG on 2015-01-28
As suggested by   [COLOR=#000000][[COLOR=#000000]maglin2[/COLOR]]("http://ubuntuforums.org/member.php?u=1905722") [/COLOR]
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG], reran, nothing showed up on Clamscan using sudo. 
And re/ran ClamTK, received 3 notifications.  
2 > ch.PUA.JS.Xored
and one PUA.Phishing.bank.
Removed these, re/ran ClamTK  and nothing left.

Since all , or  most, previous findings were PUA, and removed, possibly over 200, the question is what is the inherent problem with PUA files ?,** Potentially Unwanted** , or potentially **Dangerous. ????**
Look at Manpages for Clamscan and this comes up> [COLOR=#333333][FONT=inherit]See  [/FONT][/COLOR][http://www.clamav.net/support/pua](http://www.clamav.net/support/pua)[COLOR=#333333][FONT=inherit]  for  the[/FONT][/COLOR]              complete list of PUA, again, Ooops !  [IMG]http://www.clamav.net/img/ClamAVLogo_med.png[/IMG]Allen

---

### Post by maglin2 on 2015-02-02
[http://www.clamav.net/doc/pua.html](http://www.clamav.net/doc/pua.html)

---

### Post by AllenGG on 2015-02-02
Thanks, it wasn´t working earlier.
And, this is what bothers me: [FONT=arial black][COLOR=#B3B3B3]**runtime packers are widely used with malicious files since they can prevent a already known malware from detection by an Antivirus **product.[/COLOR][/FONT]

---

