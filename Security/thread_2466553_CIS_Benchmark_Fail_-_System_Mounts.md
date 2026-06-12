---
title: "CIS Benchmark Fail - System Mounts"
date: 2021-08-30
forum: Security
---

### Post by seeptiim on 2021-08-30
[COLOR=#141618][FONT=&quot]Greetings. I have found that Ubuntu does not pass the following CIS Benchmarks:[/FONT][/COLOR]

[COLOR=#141618][FONT=&quot]2500 - Ensure mounting of freevxfs filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2501 - Ensure mounting of jffs2 filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2502 - Ensure mounting of hfs filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2503 - Ensure mounting of hfsplus filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2504 - Ensure mounting of squashfs filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2505 - Ensure mounting of udf filesystems is disabled[/FONT][/COLOR]
[COLOR=#141618][FONT=&quot]2506 - Ensure mounting of FAT filesystems is disabled[/FONT][/COLOR]

[COLOR=#141618][FONT=&quot]Are these filesystems necessary for the correct functioning of Ubuntu? What would be the effect of disabling them?[/FONT][/COLOR]

[COLOR=#141618][FONT=&quot]Thank you in advance![/FONT][/COLOR]

---

### Post by TheFu on 2021-08-30
> **seeptiim said:**
>  Are these filesystems necessary for the correct functioning of Ubuntu? What would be the effect of disabling them? 

Try it. Report back. Please.

My guess is that 2 of those are mandatory, but none of the other are. I doubt the packages are even installed, unless a specific system requires is.  I've never seen jffs2 except on routers, for example.  It isn't like connecting a disk will automatically mount it on any properly configured Linux system (IMHO).  Never allow mounting of storage unless the admin actually configures that mount.

---

