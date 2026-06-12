---
title: "Updating the LAMP stack?"
date: 2012-01-26
forum: Server Platforms
---

### Post by taze on 2012-01-26
A newb question:
Is the best way to update the LAMP stack by just running
sudo apt-get update
&
sudo tasksel install lamp-server

again?

Any risk to settings/data?

This is on Ubuntu Server 10.04 LTS 64bit.

---

### Post by kwinto on 2012-01-26
The best way to update is to use "sudo apt-get upgrade". Also there is no need to use tasksel in future for LAMP installing, as you can use "sudo apt-get install lamp-server^", caret (^) is important here.

---

