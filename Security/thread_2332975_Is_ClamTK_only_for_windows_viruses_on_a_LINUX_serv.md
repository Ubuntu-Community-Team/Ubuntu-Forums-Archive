---
title: "Is ClamTK only for windows viruses on a LINUX server?"
date: 2016-08-05
forum: Security
---

### Post by xenon3 on 2016-08-05
LINUX servers that serve windows clients and could spread windows viruses to these clients? The ClamTK documentation Software Center does not say such a thing.

---

### Post by &amp;KyT$0P# on 2016-08-05
[https://ubuntuforums.org/showthread.php?t=2332576](https://ubuntuforums.org/showthread.php?t=2332576)

---

### Post by xenon3 on 2016-08-06
> **halogen2 said:**
> [https://ubuntuforums.org/showthread.php?t=2332576](https://ubuntuforums.org/showthread.php?t=2332576)

Thanks, yes, it practically says indeed only "windows" viruses, but I do not agree that these are always harmless for LINUX, could be platform independent viruses among them, my experience is that with these viruses on my LINUX system system freezes (non responsive) and must be reboot and virus scanned

---

### Post by Habitual on 2016-08-06
Consider the source: [http://clamtk.sourceforge.net/faq.html](http://clamtk.sourceforge.net/faq.html)
and If a Windows user can't be bothered to guard his own system against  threats that are the result of shortcomings in his own operating system,  then the efforts of the comparatively small base of Linux users aren't  going to make a shred of difference. Such a Windows user will  unavoidably get infected from somewhere else.[[1]("https://sites.google.com/site/easylinuxtipsproject/security")]

---

### Post by xenon3 on 2016-08-06
> **Habitual said:**
> Consider the source: [http://clamtk.sourceforge.net/faq.html](http://clamtk.sourceforge.net/faq.html)
and If a Windows user can't be bothered to guard his own system against  threats that are the result of shortcomings in his own operating system,  then the efforts of the comparatively small base of Linux users aren't  going to make a shred of difference. Such a Windows user will  unavoidably get infected from somewhere else.[[1]("https://sites.google.com/site/easylinuxtipsproject/security")]

[h=3]thought Linux doesn't NEED antivirus protection![/h]  			It is true that you may not need it - at least, not in the sense  of a Windows computer and running all the time.  This program is more  geared for users interested in scanning files prior to sending them to  other users.
 			Note that programs like rkhunter, chkrootkit, and unhide are more Linux-specific programs.

It does say "...not in a sense..." and "...more geared..." it does not rule out it protects LINUX also for the few LINUX viruses that are out there ;-)

However many thanks, for the link, I could spread viruses by mail to windows friends? If I don't ClamTK scan my LINUX? Or when I Facebook chat? Or FTP?

---

### Post by xenon3 on 2016-08-06
> **Habitual said:**
> Consider the source: [http://clamtk.sourceforge.net/faq.html](http://clamtk.sourceforge.net/faq.html)
and If a Windows user can't be bothered to guard his own system against  threats that are the result of shortcomings in his own operating system,  then the efforts of the comparatively small base of Linux users aren't  going to make a shred of difference. Such a Windows user will  unavoidably get infected from somewhere else.[[1]("https://sites.google.com/site/easylinuxtipsproject/security")]

Finds PUA.Doc.Tool.LibreOffice.Macro-1 in libreoffice subdirectory, never mind that it could be a false positive, however I scanned maybe a couple of hundred times the whole HOME before, unlikely ClamTK did not see it before, or it must come from a recent signatures update, well congratulations you never will know if the infection is recent :( unless you get reinfected with the same virus

---

### Post by HermanAB on 2016-08-21
ClamAV is a general purpose file scanner.  As such it can detect virus signatures in any files that you care to scan with it.

However, since there are not any active Linux viruses, there is no need to scan Linux files.

The reason why there are not any active Linux viruses is manyfold.  Mainly, because the Linux patch and repair strategy is extremely fast, as opposed to Microsoft whose patch and repair cycle is extremely slow.  

In essence, on MS systems you need to fix the symptom, while on Linux you fix the problem, which is rather more efficient.

---

### Post by xenon3 on 2016-08-24
> **HermanAB said:**
> 

The reason why there are not any active Linux viruses is manyfold.  Mainly, because the Linux patch and repair strategy is extremely fast, as opposed to Microsoft whose patch and repair cycle is extremely slow.  

  

This is great news! One of my customers is plagued with that windows "trackid=sp-006" virus does 20 alterations in registry and a diaspora of 10 exe and dll files, evolutes very fast, nothing one can do, one could rebuild, but it comes back. Maybe you heard of it? Virus evolution began that it (trackid...) was added to every keyword string in Google Chrome and it was consequently in all search results and the URL of the result page also had it. Now IE also affected. Can be that one installs dubious software and so one gets the virus, I hope

---

