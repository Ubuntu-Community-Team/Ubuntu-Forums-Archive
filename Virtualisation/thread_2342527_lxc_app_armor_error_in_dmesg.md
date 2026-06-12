---
title: "lxc app armor error in dmesg"
date: 2016-11-07
forum: Virtualisation
---

### Post by alex351 on 2016-11-07
hi everyone,

I recently started getting these error in dmesg which clearly result from lxc containers but I don't know which container from and what is the trigger - up until recently there were no issues. Does anybody have an idea on how to fix this?

```
[COLOR=#000000][FONT=Menlo][263310.878677] audit: type=1400 audit(1478526828.374:45): apparmor="DENIED" operation="mount" info="[/FONT][/COLOR][COLOR=#C33720][FONT=Menlo]**failed**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=13342 comm="(install)" flags="rw, rslave"[/FONT][/COLOR][COLOR=#000000][FONT=Menlo][263310.909289] audit: type=1400 audit(1478526828.406:46): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=13395 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][263310.940092] audit: type=1400 audit(1478526828.434:47): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=13530 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][263311.071644] audit: type=1400 audit(1478526828.566:48): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=13912 comm="(mysqld)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][263312.102069] audit: type=1400 audit(1478526829.598:49): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=16030 comm="(an-start)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][263312.107614] audit: type=1400 audit(1478526829.602:50): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=16040 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269996.633766] audit: type=1400 audit(1478533514.106:51): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=26263 comm="(install)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269996.688503] audit: type=1400 audit(1478533514.162:52): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=26488 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269996.748186] audit: type=1400 audit(1478533514.222:53): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=26539 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269996.867881] audit: type=1400 audit(1478533514.342:54): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=26970 comm="(mysqld)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269997.839277] audit: type=1400 audit(1478533515.314:55): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=28674 comm="(an-start)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][269997.885035] audit: type=1400 audit(1478533515.358:56): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=28785 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273598.074650] audit: type=1400 audit(1478537115.534:57): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=5901 comm="(install)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273598.107292] audit: type=1400 audit(1478537115.566:58): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=5991 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273598.323477] audit: type=1400 audit(1478537115.782:59): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=6502 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273598.433489] audit: type=1400 audit(1478537115.894:60): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=6763 comm="(mysqld)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273599.740559] audit: type=1400 audit(1478537117.202:61): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=9093 comm="(an-start)" flags="rw, rslave"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][273599.749716] audit: type=1400 audit(1478537117.210:62): apparmor="DENIED" operation="mount" info="[COLOR=#c33720]**failed**[/COLOR] flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=9134 comm="(sh)" flags="rw, rslave"[/FONT][/COLOR]

```

thanks in advance
alex

---

