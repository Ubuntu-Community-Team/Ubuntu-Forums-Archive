---
title: "[Ubuntu server] How to disable ACPI system suspend?"
date: 2019-08-27
forum: Server Platforms
---

### Post by asimmetrico on 2019-08-27
Hello,
I'm pretty new to Linux.
I installed a docker application in docker in Ubuntu Server 19.04 on an old netbook Samsung N150 running an Atom 550. It works :)
My problem now is that if I close the lid (it must run as a server so I want the display off and the lid closed. I manage it mostly via SSH) it suspends.
I tried to disable CPU throttling and "open lid resume" from BIOS but with no result.
How can I disable the system suspension keeping the display off when not needed?

Thanks for your hellp

Alberto

---

### Post by asimmetrico on 2019-08-27
This worked for me

[COLOR=#242729][FONT=Arial]To disable entering the sleep mode I had to edit the /etc/systemd/logind.conf file and modify the line:[/FONT][/COLOR]
#HandleLidSwitch=suspend
[COLOR=#242729][FONT=Arial]to[/FONT][/COLOR]
HandleLidSwitch=ignore
[COLOR=#242729][FONT=Arial]Then do[/FONT][/COLOR]
sudo service systemd-logind restart

---

