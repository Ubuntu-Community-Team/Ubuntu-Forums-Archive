---
title: "Dell 2748 switch password recovery"
date: 2012-12-20
forum: Security
---

### Post by termvrl on 2012-12-20
Hi all,
 i have a problem with a Dell 2748 switch.
 how can i managed the switch if i dont know the management IP, username and password.
 i cant reset it to default because it running on production.
 i'm a new network admin, previous guy dont document what he has done.
 as i googled, i found this article.
 i wonder if i do this, is the running config will erase to default?
 [www.ehow.com/how_6069377_reset-password-dell-powerconnect-2716.html]("http://www.ehow.com/how_6069377_reset-password-dell-powerconnect-2716.html")


need your help.
 Thanks in advance.


p/s: sorry if this is not the right place to ask.

---

### Post by chadk5utc on 2012-12-22
If the device can not be reset then youll likely need to find another admin with sufficient access to this device, and get the information from them. I would before attempting the instructions on the link attempt to locate a backup of the current config. Yes it is possible that it will reset the running config.

Step one states you can restore to factory defaults.....

---

### Post by spynappels on 2012-12-22
I guess the safest option would be to configure a second switch (from a lab environment perhaps) and swap them out during an Emergency or Planned Maintenance Window, that's the only way you can minimise downtime in case the config is erased.

If you don't have another switch, planned downtime is the only way to fix this safely without affecting live traffic.

---

