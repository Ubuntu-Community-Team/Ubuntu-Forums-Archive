---
title: "Windows virus scanner for Ubuntu"
date: 2012-08-23
forum: Security
---

### Post by Leukozyt on 2012-08-23
Hi there,

I'm relatively new to Linux use, but I like it. Heh. Especially cause there are no virus problems.
BUT:
I use the same file system with Linux (which I use for all Internet activities) and Windows XP (for using the proprietary software I need for my work). My windows system has NO internet connection and NO virus scanner installed (and therefore it runs as smoothly as XP can run).

In case I download email attachments or online files in linux (most of them pdfs or .doc files, some images, jpg etc.), save it on disk and then access the disc from Win XP, there could be a threat in that, I imagine. For Windows, not for Linux, of course.

Is there any Windows virus scan software that works well on Ubuntu 12.04?
Perfect especially if easy to install ;)
Perfect also if it updates automatically, and runs permanently in the background. I know thant's not Linix-philosphy, but as I use Ubuntu only for browsing, ressources are not the big problem.

Thanks a lot!
Leuk.

---

### Post by Stonecold1995 on 2012-08-23
I'd suggest [ClamAV]("http://www.clamav.net/lang/en/").  It's very fast, free, open source, and very lightweight.  The Linux version scans for both the tiny amount of Linux malware out there, as well as Windows viruses.  You can install it from the official site or by using:
```
sudo apt-get install clamav
```
It does update automatically, but it does *not* run in the background (if by run in the background you mean it constantly scans files as they are opened).  You can set it to do a full scan at certain intervals, or just scan a specific folder (you can get it to scan Windows' Program Files folder every day, for example).

If you absolutely need something with real-time protection (I assume that's what you mean by "runs in the background"), then I'd say to go with [Avast!]("http://www.avast.com/linux-home-edition") antivirus.  Avast! is very feature rich, and has one of the most customizable GUIs.  Unfortunately it isn't free,  and it isn't open source.

Here are the pros and cons of each:
ClamAV pros: very fast, free, open source, light weight
ClamAV cons: no real-time scanning, isn't good at detecting rootkits (according to the [Wikipedia page]("https://en.wikipedia.org/wiki/Clam_AntiVirus"))

Avast! pros: very feature rich, real-time scanning
Avast! cons: expensive, closed source, can be a system hog, very poor self-defense (based on personal experience)

Overall, I'd highly recommend ClamAV, but if real-time scanning is an absolute must, then you might just have to go with Avast! instead.

---

### Post by Laiquendi on 2012-08-23
And there is a graphical interface for clamav called clamTK, if you prefer.

---

### Post by Leukozyt on 2012-08-24
Thank you!
Going to collect experience with ClamAV first ;-))

---

### Post by zombifier25 on 2012-08-25
> **Stonecold1995 said:**
> I'd suggest [ClamAV]("http://www.clamav.net/lang/en/").  It's very fast, free, open source, and very lightweight.  The Linux version scans for both the tiny amount of Linux malware out there, as well as Windows viruses.  You can install it from the official site or by using:
```
sudo apt-get install clamav
```
It does update automatically, but it does *not* run in the background (if by run in the background you mean it constantly scans files as they are opened).  You can set it to do a full scan at certain intervals, or just scan a specific folder (you can get it to scan Windows' Program Files folder every day, for example).

If you absolutely need something with real-time protection (I assume that's what you mean by "runs in the background"), then I'd say to go with [Avast!]("http://www.avast.com/linux-home-edition") antivirus.  Avast! is very feature rich, and has one of the most customizable GUIs.  Unfortunately it isn't free,  and it isn't open source.

Here are the pros and cons of each:
ClamAV pros: very fast, free, open source, light weight
ClamAV cons: no real-time scanning, isn't good at detecting rootkits (according to the [Wikipedia page]("https://en.wikipedia.org/wiki/Clam_AntiVirus"))

Avast! pros: very feature rich, real-time scanning
Avast! cons: expensive, closed source, can be a system hog, very poor self-defense (based on personal experience)

Overall, I'd highly recommend ClamAV, but if real-time scanning is an absolute must, then you might just have to go with Avast! instead.

AFAIK not a single Linux antivirus have real time scanning.

So, go with ClamAV. It's in the repo, and it's free.

---

### Post by jibawakee on 2012-08-25
Go to Avast.com and they should have download section for linux i have never used it on linux but i have on windows and its awesome i think it runs in the terminal so if you dont like the terminal i would suggest getting Clamav 
[code]sudo apt-get install clamav[code]

---

### Post by jibawakee on 2012-08-25
> **Stonecold1995 said:**
> I'd suggest [ClamAV]("http://www.clamav.net/lang/en/").  It's very fast, free, open source, and very lightweight.  The Linux version scans for both the tiny amount of Linux malware out there, as well as Windows viruses.  You can install it from the official site or by using:
```
sudo apt-get install clamav
```
It does update automatically, but it does *not* run in the background (if by run in the background you mean it constantly scans files as they are opened).  You can set it to do a full scan at certain intervals, or just scan a specific folder (you can get it to scan Windows' Program Files folder every day, for example).

If you absolutely need something with real-time protection (I assume that's what you mean by "runs in the background"), then I'd say to go with [Avast!]("http://www.avast.com/linux-home-edition") antivirus.  Avast! is very feature rich, and has one of the most customizable GUIs.  Unfortunately it isn't free,  and it isn't open source.

Here are the pros and cons of each:
ClamAV pros: very fast, free, open source, light weight
ClamAV cons: no real-time scanning, isn't good at detecting rootkits (according to the [Wikipedia page]("https://en.wikipedia.org/wiki/Clam_AntiVirus"))

Avast! pros: very feature rich, real-time scanning
Avast! cons: expensive, closed source, can be a system hog, very poor self-defense (based on personal experience)

Overall, I'd highly recommend ClamAV, but if real-time scanning is an absolute must, then you might just have to go with Avast! instead.


Well that avast part is not entirely true they have a free version for linux ;) just saying

---

### Post by Stonecold1995 on 2012-08-26
> **jibawakee said:**
> Well that avast part is not entirely true they have a free version for linux ;) just saying

But it is missing many features such as heuristics in real-time scanning, scanning running processes (I think), and is overall slower and less efficient.  It's artificially crippled (crippleware) unless you pay for the full version.

---

### Post by Leukozyt on 2012-08-26
> **Stonecold1995 said:**
> Now cracks a noble heart. Good-night, sweet prince;
And flights of angels sing thee to thy rest.
[COLOR=Olive]R.I.P. Demonoid[/COLOR].
Oh, yes...

---

### Post by SeijiSensei on 2012-08-26
> **Leukozyt said:**
> In case I download email attachments or online files in linux (most of them pdfs or .doc files, some images, jpg etc.), save it on disk and then access the disc from Win XP, there could be a threat in that, I imagine. For Windows, not for Linux, of course.

Are you saying you're using a mail provider that does not already scan every single message for viruses and malware and quarantine those that do?  I'd be looking for a new mail provider if that's the case.  Or, better yet, set up your own mail server and run [MailScanner]("http://www.mailscanner.info/") with ClamAV and SpamAssassin to clean your mail.

If you have a spare box lying around, you might look into turning it into a proxy cache with Squid and adding the [SquidClamAV]("http://squidclamav.darold.net/") package.  That will scan every single object for malware before it reaches your browser.  

I manage a gateway server for a client that uses MailScanner to clean all the mail before it gets forwarded to their Exchange server, and uses SquidClamAV to scan all their HTTP traffic.  Now this is a pretty hefty box, but it serves some 200+ users.  Even scanning all the web traffic shows no noticeable degradation in performance.

---

### Post by Soul-Sing on 2012-08-26
> AFAIK not a single Linux antivirus have real time scanning.

So, go with ClamAV. It's in the repo, and it's free.

avira with the dazuko module
and several commerc. antivirus products give on access protection.
(realtime= on access)

---

