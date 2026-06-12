---
title: "any recommended antiviruses for Xubuntu?"
date: 2015-11-01
forum: Security
---

### Post by ardouronerous on 2015-11-01
I need an antivirus for Xubuntu to project my father's Windows XP laptop, I help him with legal documents and research and we do this via email, I don't want to accidentally send him a infected file, so I want to scan it before I send.

I've tried clamAV and it's full of false positives, even a fresh wine installation is being flagged of having viruses. I've tried to install Comodo, after viewing a video of it on Youtube, I don't mind the "filesystem filter driver is not loaded" thing, I just want an good on-demand antivirus scanner, but when I tried to install it, Ubuntu Software Center, it gave me a "package is of bad quality" error.

---

### Post by bashiergui on 2015-11-01
> **ardouronerous said:**
> I just want an good on-demand antivirus scanner,
They are all equally mediocre. It doesn't matter which one you use, so use the one that installs easily and will easily download signature updates often.

---

### Post by Shane_Carmichael on 2015-11-01
Agreed, all open source antivirus scanners will do the job but will be mediocre and susceptible to hack. You may also want to look at Avast, AVG and BitDefender. I have heard great things from each of these and they are easy to install. Not sure if any are better than the other, but you should be okay using any of them. If you are looking for more reliability perhaps look into more expensive options. Otherwise you can use this link for installs: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by ardouronerous on 2015-11-02
Avast and AVG don't seem to exist anymore, all I'm getting off their websites is the Windows version of their antivirus.

I've tried BitDefender, and the gui seems to crash on scan.

---

### Post by SeijiSensei on 2015-11-02
How about Kaspersky? [http://www.kaspersky.com/product-updates/linux-endpoint-security](http://www.kaspersky.com/product-updates/linux-endpoint-security)

I don't use an antivirus except for ClamAV on mail servers (which works very well, by the way, despite the badmouthing here), but Kaspersky has a good reputation and has been in the business for well over a decade.

---

### Post by maglin2 on 2015-11-02
Have a look here
[https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/](https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/)
and here
[http://www.av-comparatives.org/linux-reviews/](http://www.av-comparatives.org/linux-reviews/)

Also, if you or your Dad uses gmail, then all attachments are  automatically scanned (using two different scanners if I recall  correctly). If your Dad then uses TBird, and allows integration with  his resident AV in its settings that gives another check. This may be a route for you to investigate, rather than putting an AV on you linux desktop.

---

### Post by ardouronerous on 2015-11-02
> **maglin2 said:**
> Have a look here
[https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/](https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/)
and here
[http://www.av-comparatives.org/linux-reviews/](http://www.av-comparatives.org/linux-reviews/)

Also, if you or your Dad uses gmail, then all attachments are  automatically scanned (using two different scanners if I recall  correctly). If your Dad then uses TBird, and allows integration with  his resident AV in its settings that gives another check. This may be a route for you to investigate, rather than putting an AV on you linux desktop.

True at gmail has it's own virus protection, but I would like to avoid sending him viruses in the first place.
Linux Security Review 2015 is very informative, thanks, why isn't that included in [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

After reading, it seems a lot of Linux antiviruses are paid-for programs and only free one-month trials. COMODO Antivirus is very impressive to me, I don't mind not having real-time protection, but how do I get around this "package is of bad quality" error when I try to install it?

---

### Post by SeijiSensei on 2015-11-02
Let's take a step back and ask how you would send him a "virus" in the first place.  Do you attach executable files (.exe, .com, etc.) to the files you send?  You'd never get those past my mail server which blocks all incoming executables at the doorstep.  In other words, don't send executables.  Are you worried about macro viruses in things like spreadsheets?  Make sure his version of any such program is set to require permission to run macros.  I think a little common sense and ordinary computer hygiene is a lot more effective than relying on some type of antivirus program.

---

### Post by ardouronerous on 2015-11-03
I mostly send him pdf, doc and excel files, and on occasions, jpegs and pngs.

After doing some research, I read it is possible to place malicious codes on photo files, and since I frequent social media websites, I wouldn't want to accidently share an infected photo, here's the link: [www.pcworld.com/article/2105408/3/watch-out-for-photos-containing-malware.html](www.pcworld.com/article/2105408/3/watch-out-for-photos-containing-malware.html).

Isn't it a myth to say that Linux doesn't get viruses? I mean, there's cross-platform viruses, like Bliss, and other viruses that exploit security holes in Adobe products like Flash and Adobe Reader, so wouldn't a antivirus be handy in these cases?

---

### Post by maglin2 on 2015-11-03
Package is of bad quality implies that it doesn't satisfy the Debian package policy requirements. This can be for a number of reasons, and usually the specific reason is given under 'Details' along with the warning.

If you google I think you will come across suggestions for how to install such a package if you're really determined - but doesn't software centre offer you an option to override and install anyway? 

(I also think I recall reading that the number one way for Linux systems to become infected is through installation of infected packages from outside the official repositories.)

---

### Post by ardouronerous on 2015-11-03
> **maglin2 said:**
> Package is of bad quality implies that it doesn't satisfy the Debian package policy requirements. This can be for a number of reasons, and usually the specific reason is given under 'Details' along with the warning.

If you google I think you will come across suggestions for how to install such a package if you're really determined - but doesn't software centre offer you an option to override and install anyway? 

(I also think I recall reading that the number one way for Linux systems to become infected is through installation of infected packages from outside the official repositories.)

When I try to install, Ubuntu Software Center gives me these warnings, 'package is of bad quality' 'could damage my system' and 'E: cav-linux: maintainer-address-malformed comfortable'

Yes, there is an option to override, but I usually adhere to warnings and never override, for fear of borking my system.

---

### Post by SeijiSensei on 2015-11-03
> **ardouronerous said:**
> After doing some research, I read it is possible to place malicious codes on photo files, and since I frequent social media websites, I wouldn't want to accidently share an infected photo, here's the link: [www.pcworld.com/article/2105408/3/watch-out-for-photos-containing-malware.html](www.pcworld.com/article/2105408/3/watch-out-for-photos-containing-malware.html).

After reading that article, I'd say the chances of infection are exceedingly low.  Obviously you won't send him something like badphoto.jpg.exe, and the warning about malware supposedly encoded in the photo also notes
> Luckily, such an altered image can't do much by itself. No image viewer will see or know what to do with that code, even if it isn't encrypted. But malware developers often break up their code into multiple pieces and distribute them separately to avoid detection. The information hidden in a picture could contain instructions useful to another piece of malware on your computer.

So you'd need to have sent him multiple infected files all with hooks to other infected files.  How likely is that?


> Isn't it a myth to say that Linux doesn't get viruses? I mean, there's cross-platform viruses, like Bliss, and other viruses that exploit security holes in Adobe products like Flash and Adobe Reader, so wouldn't a antivirus be handy in these cases?

I never use Adobe Reader nor should you or your dad.  Use a third-party PDF viewer.  Firefox now comes with its own built-in PDF viewer.  Flash is still unavoidable, so the solution is to keep it up-to-date.  Exploits of things like Reader and FlashPlayer are nearly always designed with the expectation that this software is running on Windows.  Malware for Linux exists but is very rare, and exploits intended for Windows won't work on a Linux machine.  I've been using Linux for two decades and have never had any form of "infection" on my desktop machines.  I once had a server exploited (rather benignly) many years ago, but only because I was negligent in updating the Apache web server software.

Remember that sites like PCWorld have an incentive to write scary articles like that one in an effort to garner readers and ad views.  Not to mention that antivirus companies are advertising mainstays on sites like that.

---

### Post by bashiergui on 2015-11-05
Nearly all malware sent via email targets Windows. Linux can be exploited, but malicious emails are not the most effective method to exploit it.

Yes any file can be altered to contain malicious code. The most effective way to prevent malicious code from executing on a Windows machine is with EMET (which is a free tool offered by Microsoft [https://www.microsoft.com/en-us/download/details.aspx?id=46366](https://www.microsoft.com/en-us/download/details.aspx?id=46366)). Have your dad install that instead of worrying about scanning email with anti-virus.

I wasn't bad mouthing anti-virus. I was offering facts such as the ones Brian Krebs outlined here [http://krebsonsecurity.com/2012/06/a-closer-look-recent-email-based-malware-attacks/](http://krebsonsecurity.com/2012/06/a-closer-look-recent-email-based-malware-attacks/)

His research indicates that, at top performance, any given anti-virus software (open source or not) will catch 20% of all the malware in your email inbox. That's why I say it doesn't matter which one you use. Whichever one you do choose, though, it's critical to keep the signatures updated. If the software doesn't make it simple to update signatures and you fall behind, then you will catch much less than the abysmal percentage expected.

---

### Post by bashiergui on 2015-11-05
Here's how Microsoft describes EMET
[https://www.microsoft.com/en-us/download/details.aspx?id=46366](https://www.microsoft.com/en-us/download/details.aspx?id=46366)
> The Enhanced Mitigation Experience Toolkit (EMET) helps raise the bar against attackers gaining access to computer systems. EMET anticipates the most common actions and techniques adversaries might use in compromising a computer, and helps protect by diverting, terminating, blocking, and invalidating those actions and techniques. EMET helps protect your computer systems even before new and undiscovered threats are formally addressed by security updates and antimalware software. EMET benefits enterprises and all computer users by helping to protect against security threats and breaches that can disrupt businesses and daily lives. 

---

### Post by ardouronerous on 2015-11-05
> **bashiergui said:**
> Here's how Microsoft describes EMET
[https://www.microsoft.com/en-us/download/details.aspx?id=46366](https://www.microsoft.com/en-us/download/details.aspx?id=46366)

Unfortunately, EMET is designed for Windows 7 and up, my dad's laptop is only designed to handle Windows XP, so incompatible.

Thanks for the help.

---

### Post by bashiergui on 2015-11-06
> **ardouronerous said:**
> Unfortunately, EMET is designed for Windows 7 and up, my dad's laptop is only designed to handle Windows XP, so incompatible.

Thanks for the help.
Microsoft offers free upgrades to Windows 10. There is no anti-virus solution that can defend an unsupported operating system (XP) running unsupported software (IE, flash, adobe, etc). Using AV will only provide a false sense of security.

Or tell your dad to keep XP and assume his computer is compromised and never use it for banking or other sensitive matters.

---

### Post by ardouronerous on 2015-11-09
> **maglin2 said:**
> Package is of bad quality implies that it doesn't satisfy the Debian package policy requirements. This can be for a number of reasons, and usually the specific reason is given under 'Details' along with the warning.

If you google I think you will come across suggestions for how to install such a package if you're really determined - but doesn't software centre offer you an option to override and install anyway?

(I also think I recall reading that the number one way for Linux systems to become infected is through installation of infected packages from outside the official repositories.)

Yesterday, I've finally decided to choose to override the warning and install COMODO Antivirus for Linux, and it works quite well, the virus definitions auto update via the Internet, no real-time protection, but that's expected since it only works on Xubuntu 12.04, on demand scanning works well, I've tested the scanner with the EICAR test file, it caught it, so it's all good.

NOTE: I didn't need to activate the 'post_setup.sh' via the Terminal, it seems that COMODO works out of the box, even without activating the 'post_setup.sh'. I think the 'post_setup.sh' is needed to activate COMODO's real-time protection, which doesn't work on Xubuntu 14.04 anyway.

> **bashiergui said:**
> Microsoft offers free upgrades to Windows 10. There is no anti-virus solution that can defend an unsupported operating system (XP) running unsupported software (IE, flash, adobe, etc). Using AV will only provide a false sense of security.

Or tell your dad to keep XP and assume his computer is compromised and never use it for banking or other sensitive matters.

As I said, laptop was only designed to handle XP, and thanks for the advice!

---

