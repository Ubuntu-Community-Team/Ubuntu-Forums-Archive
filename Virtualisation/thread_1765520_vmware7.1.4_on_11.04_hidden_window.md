---
title: "vmware7.1.4 on 11.04 hidden window"
date: 2011-05-23
forum: Virtualisation
---

### Post by aznot on 2011-05-23
Hi everybody,
This post is about small workaround I found. I did not find it on [_10^100_]("http://en.wikipedia.org/wiki/Googol"), so it is not probably existing yet.

Issue: Lost vmware application window, after starting guest os. It happens for some guest os.

Background:
  I upgraded from Ubuntu 10.10 to 11.04.
  After upgrade from 10.10 to 10.04, my vmware workstation stopped working(issue with module compilation modules can not be compiled, another issue with unity).
  This issues are discussed [_here_]("http://communities.vmware.com/message/1745502") and [_here(Google)_]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=vmware+ubuntu+11.04+unity#sclient=psy&hl=sk&source=hp&q=vmware+ubuntu+11.04+unity+issues&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=597bbf215fc3d7ce").

  First issue I solved with latest vmware version(7.1.4), second with uninstalling/disabling unity(my graphics card is very very old). I did not try unity 2d.

After that I run into another problem, when I start some of my guest os, vmware window disappeared. For some guest os it works fine, others just cause vmware window to disappear. When I check task manager, i can see vmware process consuming memory, cpu, ... you can even connect to guest os via remote desktop. On my desktop I can only see vmware notification icon, where you can start, stop, suspend ... your machines. This works perfectly.

I found out, that machines which works correctly has only one cpu with one core assigned. After I changed setting for all my machines to one cpu and one core all works fine. I can see vmware window on my desktop.

In previous version of vmware workstation I have used different combinations of number of cpu and cores. In latest version it fails.

---

