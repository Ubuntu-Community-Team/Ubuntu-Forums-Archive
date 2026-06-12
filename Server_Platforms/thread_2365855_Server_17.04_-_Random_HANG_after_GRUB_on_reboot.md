---
title: "Server 17.04 - Random HANG after GRUB on reboot"
date: 2017-07-11
forum: Server Platforms
---

### Post by jpelletier on 2017-07-11
Hi,

[COLOR=#111111][FONT=Ubuntu]I have an [/FONT][/COLOR]Intel NUC NUC6CAYS + 128GB SSD[COLOR=#111111][FONT=Ubuntu] and another unit, [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]Intel NUC NUC6CAYH + 4GB Ram + 128GB SSD[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] both [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]updated to latest bios. _Randomly on reboot, the system will hang right after Grub menu_. I installed and updated Ubuntu Server 17.04 and installed Intel Graphics Update Tool 2.0.5

I tried to get more logs with [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]debug loglevel=7 earlyprintk=efi[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] but it's hanging right after:

[/FONT][/COLOR][    0.00000] Console: colour dummy device 80x25
[    0.00000] console [tty0] enabled 
[    0.00000] bootconsole [earlyefi0] disabled[FONT=Ubuntu] [/FONT][COLOR=#111111][FONT=Ubuntu]So it's not really helping me.

I have a [systemd script rebooting]("https://communities.intel.com/servlet/JiveServlet/download/485079-171358/RebootScript.md.zip") every 15 seconds, when I'm using the 2GB memory, it will freeze in 15 minutes MAX. When I'm using a 4GB memory instead, it take about 1h15 minutes before it freeze. I really don't understand what is happening and what is the root cause. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I [/FONT][/COLOR][asked on AskUbuntu]("http://askubuntu.com/questions/929714/ubuntu-server-17-04-nuc6cays-random-freeze-after-grub")[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111], unfortunately no answer.[/COLOR][/FONT][COLOR=#111111][FONT=Ubuntu]

I also tried to get more support from Intel Community, you can see my [post here with a lot of details]("https://communities.intel.com/thread/115864") but Intel said that, since it's after GRUB, it can't be a bios issue.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I really need help to investigate the issue further since I'm not a Linux expert. Is this an issue with the NUC? Is it a configuration issue? Is it a Kernel issue? [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Thanks a lot for help[/FONT][/COLOR]

---

### Post by jpelletier on 2017-07-12
Really need help on this one, any idea on what could be the cause or more debug hints to find it would be really appreciated!

---

