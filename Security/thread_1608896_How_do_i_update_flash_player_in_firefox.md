---
title: "How do i update flash player in firefox?"
date: 2010-10-29
forum: Security
---

### Post by dogdo on 2010-10-29
Will the newest version be in the repositories or do i have to go to the flash website?

---

### Post by OpSecShellshock on 2010-10-29
As I understand it, Flash itself doesn't really get put in the repositories--just the installer. But when it is available (11/9) then the installer will be in the repos within a couple of days.

---

### Post by dogdo on 2010-10-29
> **OpSecShellshock said:**
> As I understand it, Flash itself doesn't really get put in the repositories--just the installer. But when it is available (11/9) then the installer will be in the repos within a couple of days.

Its just that according to that mozilla plugin checker site im using a insecure version of flash. 

So your telling me to wait a few days before using the repos? 

I dont suppose the automatic system updates will install the new flash player version for me will it?

---

### Post by slakkie on 2010-10-29
See: [http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

Just add that repository and you'll be fine.

---

### Post by OpSecShellshock on 2010-10-29
The Flash vulnerability that was announced yesterday has not yet been patched, and won't be until November 9 according to Adobe. The current version of the Flash plugin until then would be 10.1 r85 I think. However, the most current available version is vulnerable and will remain so for the next week and a half.

---

### Post by dogdo on 2010-10-29
> **OpSecShellshock said:**
> The Flash vulnerability that was announced yesterday has not yet been patched, and won't be until November 9 according to Adobe. The current version of the Flash plugin until then would be 10.1 r85 I think. However, the most current available version is vulnerable and will remain so for the next week and a half.

Would apparmor prevent firefox from being compromised in this situation?

Worst case scenario-my firefox is attacked by this exploit-whats the worst that could happen on ubuntu? Would my system be rooted/data stolen/my pc becomes part of botnet etc?

---

### Post by movieman on 2010-10-29
> **dogdo said:**
> Would apparmor prevent firefox from being compromised in this situation?

If you run 64-bit you can use an apparmor profile for nspluginwrapper which is where Flash runs; then you can ensure it can't do anything bad. I don't think there's any way to do the same on 32-bit Ubuntu?

I've basically prevented nspluginwrapper from accessing anything other than its own config files and /tmp, so there's not much harm it can do.

---

### Post by movieman on 2010-10-29
Actually, according to this page Flash should be run in plugin-container on 32-bit Linux so we should be able to create a profile for that similar to nspluginwrapper:

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

---

### Post by SeijiSensei on 2010-10-29
> **dogdo said:**
> Would apparmor prevent firefox from being compromised in this situation?

Good question.  Anyone know?

> Worst case scenario-my firefox is attacked by this exploit-whats the worst that could happen on ubuntu? Would my system be rooted/data stolen/my pc becomes part of botnet etc?

I think the chances are quite slim.  First only malicious Flash videos and PDF files can trigger this exploit.  You might want to avoid the hottest YouTube videos of the moment, but videos that have been there for years aren't really a threat.

I also don't use the Adobe Reader plugin. Do you?  My Kubuntu system uses Okular to display PDF files.  I doubt it will be affected by this exploit, nor will the GNOME equivalent.  If you're really paranoid, use Ghostscript.

---

### Post by movieman on 2010-10-29
> **SeijiSensei said:**
> You might want to avoid the hottest YouTube videos of the moment, but videos that have been there for years aren't really a threat.

Youtube reencodes videos on upload, doesn't it? In which case you couldn't get infected from a Youtube video unless Youtube itself is hacked.

---

### Post by dogdo on 2010-10-29
> **movieman said:**
> If you run 64-bit you can use an apparmor profile for nspluginwrapper which is where Flash runs; then you can ensure it can't do anything bad. I don't think there's any way to do the same on 32-bit Ubuntu?

I've basically prevented nspluginwrapper from accessing anything other than its own config files and /tmp, so there's not much harm it can do.

im running 64 bit linux ubuntu but to be honest i have no idea of how to configure apparmor- i read the sticky but i still can grasp it-i always end up making too restrictive a profile-firefox not booting up etc. I think a UI for apparmor is on the ubuntu wishlist...

---

### Post by dogdo on 2010-10-29
> **SeijiSensei said:**
> Good question.  Anyone know?



I think the chances are quite slim.  First only malicious Flash videos and PDF files can trigger this exploit.  You might want to avoid the hottest YouTube videos of the moment, but videos that have been there for years aren't really a threat.

I also don't use the Adobe Reader plugin. Do you?  My Kubuntu system uses Okular to display PDF files.  I doubt it will be affected by this exploit, nor will the GNOME equivalent.  If you're really paranoid, use Ghostscript.

But cant any flash videos be hacked? im watching a video on hulu at the moment-how would i know if i was being hacked? 

As for as i know im using evince reader for gnome ubuntu and apparmor by default locks down evince. Hopefully im ok for pdf files at least.

---

### Post by WeAreLinux on 2010-10-30
> **dogdo said:**
> But cant any flash videos be hacked? im watching a video on hulu at the moment-how would i know if i was being hacked? 

As for as i know im using evince reader for gnome ubuntu and apparmor by default locks down evince. Hopefully im ok for pdf files at least.

They would have to hack Hulu's website itself. User posted flash videos, esp. ones not on trusted servers/websites would be the real threat.

The security alert only effects Adobe Reader, not Evince.

---

