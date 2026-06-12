---
title: "New Koobface Variant Infects Linux Systems"
date: 2010-10-28
forum: Security
---

### Post by Kinstonian on 2010-10-28
[New Koobface Variant Infects Linux Systems](http://news.softpedia.com/news/New-Koobface-Variant-Infects-Linux-too-163450.shtml)  Interesting... sounds easily avoidable like any other malware, but is probably a nice reminder Linux users aren't invincible.

---

### Post by CharlesA on 2010-10-28
AppArmor and NoScript would stop that dead in it's tracks.

---

### Post by OpSecShellshock on 2010-10-28
That's an awful lot of things that have to go wrong before it causes an infection, though. And it's not even a real system compromise since it's not persistent across sessions and doesn't elevate privileges (not that it could).

To sum up: you'd have to have the Java plug-in enabled in the first place (not wrong in and of itself, but not exactly necessary), you'd have to not be blocking scripts running by default in the browser (which is bad), you'd have to follow a shortened link in a painfully obvious social engineering message from an almost certain stranger (very bad), then you'd have to manually allow the applet to run and perform its installation routine (which--let's face it, if you would do that then you should wear a crash helmet just to use the internet). After that you'd have to never restart.

So while it's true that malware can work on Linux machines, the end user has to really want it. Even then, it's not going to stick around or do any of the really nasty stuff that the versions of Koobface for Windows can do.

---

### Post by Kinstonian on 2010-10-28
> **OpSecShellshock said:**
> That's an awful lot of things that have to go wrong before it causes an infection, though. And it's not even a real system compromise since it's not persistent across sessions and doesn't elevate privileges (not that it could).

To sum up: you'd have to have the Java plug-in enabled in the first place (not wrong in and of itself, but not exactly necessary), you'd have to not be blocking scripts running by default in the browser (which is bad), you'd have to follow a shortened link in a painfully obvious social engineering message from an almost certain stranger (very bad), then you'd have to manually allow the applet to run and perform its installation routine (which--let's face it, if you would do that then you should wear a crash helmet just to use the internet). After that you'd have to never restart.

So while it's true that malware can work on Linux machines, the end user has to really want it. Even then, it's not going to stick around or do any of the really nasty stuff that the versions of Koobface for Windows can do.

Pretty much.  However, I'd disagree a little on the system compromised part.  It is a real compromise and has an obvious negative impact on security, it's just hopefully going to be an easy fix in most cases.

---

### Post by movieman on 2010-10-28
> **Kinstonian said:**
> It is a real compromise and has an obvious negative impact on security, it's just hopefully going to be an easy fix in most cases.

Particularly given that every distro should have patched the Java holes by now.

---

### Post by dogdo on 2010-10-28
Can someone explain why rebooting a ubuntu machine removes the virus-Does it have something to do with RAM being volatile memory? 

Would rebooting remove new viruses on a ubuntu machine-could we be entering a age where antivirus on linux might be needed?

---

### Post by CharlesA on 2010-10-28
> **dogdo said:**
> Can someone explain why rebooting a ubuntu machine removes the virus-Does it have something to do with RAM being volatile memory? 

Would rebooting remove new viruses on a ubuntu machine-could we be entering a age where antivirus on linux might be needed?

Viruses written for Windows won't run on a Linux machine unless they have Wine installed and if that was the case it would be confined to the .wine folder.

I don't know where you got the rebooting removes viruses, unless you mean they are being stored in the browser cache which is deleted after each reboot (since it's stored in /tmp/ as far as I know)

---

### Post by tgm4883 on 2010-10-28
> **dogdo said:**
> Can someone explain why rebooting a ubuntu machine removes the virus-Does it have something to do with RAM being volatile memory? 

Would rebooting remove new viruses on a ubuntu machine-could we be entering a age where antivirus on linux might be needed?

> **CharlesA said:**
> Viruses written for Windows won't run on a Linux machine unless they have Wine installed and if that was the case it would be confined to the .wine folder.

I don't know where you got the rebooting removes viruses, unless you mean they are being stored in the browser cache which is deleted after each reboot (since it's stored in /tmp/ as far as I know)

You guys should really read the linked article.

> The applet is dropped inside the user's home directory and stops running at computer reboot. This means that on Linux, unlike on Windows, the Koobface infections are temporary.

---

### Post by CharlesA on 2010-10-28
> **tgm4883 said:**
> You guys should really read the linked article.

I skimmed it earlier.

That just means that it's stopped after a reboot due to the process that spawned it being killed off.

---

### Post by OpSecShellshock on 2010-10-28
Does kind of make me wonder, though--given that even up to the level of something that stops when the user session is terminated it still requires user interaction to run the malware, why not go for broke and try to get them to install a package? Not that I'm complaining, of course.

Also, since researchers somewhere have apparently seen the dropped files, it sure would be nice if they'd give out the names or other identifying characteristics so affected users could delete them.

---

### Post by tgm4883 on 2010-10-28
> **OpSecShellshock said:**
> Does kind of make me wonder, though--given that even up to the level of something that stops when the user session is terminated it still requires user interaction to run the malware, why not go for broke and try to get them to install a package? Not that I'm complaining, of course.

Also, since researchers somewhere have apparently seen the dropped files, it sure would be nice if they'd give out the names or other identifying characteristics so affected users could delete them.

That already happened not too long ago. IIRC, there was a theme package on gnome-look that installed a trojan.

---

### Post by CharlesA on 2010-10-28
> **tgm4883 said:**
> That already happened not too long ago. IIRC, there was a theme package on gnome-look that installed a trojan.

True. That was a bit of social engineering tho, masquerading as a theme pack.

---

