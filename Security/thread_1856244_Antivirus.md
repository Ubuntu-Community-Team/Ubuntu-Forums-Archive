---
title: "Antivirus"
date: 2011-10-07
forum: Security
---

### Post by Orcris on 2011-10-07
I know that I don't need an antivirus, but I'm working with Windows users all the time and sending attachments, and I'm also kind of paranoid. What's the best Linux AV? I don't like ClamAV, and it's the only one in the Ubuntu repositories, so what's the best Linux antivirus?

---

### Post by lisati on 2011-10-07
Aunty Virus? Have a look here: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by bodhi.zazen on 2011-10-07
IMO running antivirus is completely unnecessary on a Linux Desktop.

---

### Post by ubun2geek on 2011-10-07
That's a plus about ubuntu. You've got a steel wall around your PC with no Windows to let any viruses in. :)

---

### Post by Dangertux on 2011-10-07
You know I'd been curious about the debate of "Linux anti-malware" solutions. So I did a little research on it, and tested several of the "popular" AV solutions against multiple files that should be found as malicious based on heuristics alone. 

They didn't find it, the one's that worked properly. IMO Linux AV is a complete waste of time, and if someone does decide to start writing malware for linux we're all going to be playing catch up. However, with the current state of Linux AV solutions I wouldn't bother, it's a waste of cpu time.

---

### Post by sammiev on 2011-10-07
> **Orcris said:**
> I know that I don't need an antivirus, but I'm working with Windows users all the time and sending attachments, and I'm also kind of paranoid. What's the best Linux AV? I don't like ClamAV, and it's the only one in the Ubuntu repositories, so what's the best Linux antivirus?

I think you are on the right track as I work with many windows computers (friends) and I would hate to think I may have infected their Windows computer from a Linux computers from mine. So I scan mine once a week to confirm I'm clean. :) I never had a virus yet either in windows or Linux. :)

---

### Post by collisionystm on 2011-10-07
> **Orcris said:**
> I know that I don't need an antivirus, but I'm working with Windows users all the time and sending attachments, and I'm also kind of paranoid. What's the best Linux AV? I don't like ClamAV, and it's the only one in the Ubuntu repositories, so what's the best Linux antivirus?

Eset nod32

---

### Post by mikaelcrocker on 2011-10-07
You could go try Avast anti virus.  There is a freeware version and it's pretty decent.  I know on Tomshardware they did a review of anti-virus thats free, you may have to do some looking to find it, but it's pretty good.

---

### Post by sammiev on 2011-10-07
> **mikaelcrocker said:**
> You could go try Avast anti virus.  There is a freeware version and it's pretty decent.  I know on Tomshardware they did a review of anti-virus thats free, you may have to do some looking to find it, but it's pretty good.

Avast is #1 in my books, :) for both windows and Linux. :)

---

### Post by OpSecShellshock on 2011-10-08
What situation are you trying to avoid specifically? The various AV scanning engines are really going to be equally effective (which is to say, not particularly). The most that scanning a file is going to do for you is allow you to say that you've scanned it (which, sure, satisfies some compliance requirements sometimes).

Most of the malicious attachments that I've encountered for the last several years have been crafted specifically to be malicious, and since I assume you aren't doing that before sending them, there's no risk there. The Windows users that you are sending files to probably have something in place to check all attachments and downloads, but if they don't, or if they're not up to date, then there's really nothing you can do for them.

---

### Post by SeijiSensei on 2011-10-08
> **Orcris said:**
> I know that I don't need an antivirus, but I'm working with Windows users all the time and sending attachments, and I'm also kind of paranoid.

Most every mail service provider scans for viruses and malware distributed via email.  If your talking about exchanging files with other users on a private network, like at work, then your mail server should have anti-virus scanning in place as well.  If you don't, I recommend installing [MailScanner]("http://www.mailscanner.info/") and ClamAV in your place of business.

---

### Post by haqking on 2011-10-08
Waste of time and resources to be honest, if it is for the benefit of the windows machines then let their own AV deal with it.

---

### Post by jerenept on 2011-10-09
> **ubun2geek said:**
> That's a plus about ubuntu. You've got a steel wall around your PC with no Windows to let any viruses in. :)

Do you um, actually *know* how viruses work?

---

### Post by Elysius on 2011-10-12
> **Orcris said:**
> I don't like ClamAV

What's it you don't like about ClamAV?

---

### Post by fishfisting on 2011-10-14
> **haqking said:**
> Waste of time and resources to be honest, if it is for the benefit of the windows machines then let their own AV deal with it.

Don't you think it benefits him as well?

Who wants to work with someone who is sending them viruses? 

At least to me personally I would lose trust in someone who is sending me new viruses all the time. Or at least think "what is up with that?".

It leaves a very bad business impression and I think the idea to not pass viruses around is a good one, all benefits from it.

---

### Post by haqking on 2011-10-14
> **fishfisting said:**
> Don't you think it benefits him as well?

Who wants to work with someone who is sending them viruses? 

At least to me personally I would lose trust in someone who is sending me new viruses all the time. Or at least think "what is up with that?".

It leaves a very bad business impression and I think the idea to not pass viruses around is a good one, all benefits from it.

yes and no.

Most of the reports from Linux AV are false positives anyways, ClamAV is pretty poor.

If you share files with windows users then by all means run some, but dont rely on it being any good.

---

### Post by fishfisting on 2011-10-14
> **haqking said:**
> yes and no.

Most of the reports from Linux AV are false positives anyways, ClamAV is pretty poor.

If you share files with windows users then by all means run some, but dont rely on it being any good.


I don't have the best experiences from antiviruses myself (and I currently do not use one). 

One nice service one could use is virustotal.com it lets you scan files that you want to send without having a service constantly running in the background.

I sometimes scan files using that service. The file will get scanned by multiple scanners, witch should be better than to use just one antivirus.

The bad thing is that personal/business documents may not be the smartest thing to upload to a site. :P

---

