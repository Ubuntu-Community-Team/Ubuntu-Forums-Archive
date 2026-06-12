---
title: "ClamAV installation is outdated"
date: 2013-10-12
forum: Server Platforms
---

### Post by sarmad-hassan on 2013-10-12
My logwatch is continuously sending me the following logs related to my Clamav installation. 

The usual apt-update doesn't find anything to update. Other postings in the same forum have been tried but it doesn't work, may be because its a new Clamav update. 

```
[FONT=Trebuchet MS]WARNING: Your ClamAV installation is OUTDATED![/FONT]
[FONT=Trebuchet MS]   WARNING: Local version: 0.97.8 Recommended version: 0.98[/FONT]
[FONT=Trebuchet MS]   DON'T PANIC! Read [/FONT][http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
[FONT=Trebuchet MS]   main.cld is up to date (version: 55, sigs: 2424225, f-level: 60, builder: neo)[/FONT]
[FONT=Trebuchet MS]   daily.cld is up to date (version: 17953, sigs: 406966, f-level: 63, builder: dgoddard)[/FONT]
[FONT=Trebuchet MS]   bytecode.cld is up to date (version: 228, sigs: 43, f-level: 63, builder: neo)[/FONT]
```

---

### Post by SeijiSensei on 2013-10-14
Looks like 0.97.7 is still the [shipping version]("https://launchpad.net/ubuntu/+source/clamav") of ClamAV for current releases.  [0.98 still has not been released](http://ubuntuforums.org/showthread.php?t=2177181).  

Usually clamav builds cleanly from [source]("http://www.clamav.net/lang/en/download/sources/") if you want to go that route.

---

### Post by sarmad-hassan on 2013-10-14
Thanks SeijiSensei :) 

I think I'll just wait a bit more and let apt-get do its magic.

---

