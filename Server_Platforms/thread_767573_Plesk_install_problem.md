---
title: "Plesk install problem"
date: 2008-04-25
forum: Server Platforms
---

### Post by pearjam on 2008-04-25
Hi,

Here's the issue... At my job, I'm moving from Shared Server Support to Dedicated Server Support which runs all Unix / Linux (right on). The tool the customers use is the Plesk Control Panel. I would like to install Plesk on my home box to study it before I change depts. I use Ubuntu Studio 8.04 w/ an xampp server.

I've downloaded Plesk, but when I run the auto-installer, it tells me there is no suitable version for your OS (because its 8.04, not 7.10).

Does anyone know how to force install, or otherwise make it work? Maybe make the install think the OS is 7.10?

---

### Post by windependence on 2008-04-29
> **pearjam said:**
> Hi,

Here's the issue... At my job, I'm moving from Shared Server Support to Dedicated Server Support which runs all Unix / Linux (right on). The tool the customers use is the Plesk Control Panel. I would like to install Plesk on my home box to study it before I change depts. I use Ubuntu Studio 8.04 w/ an xampp server.

I've downloaded Plesk, but when I run the auto-installer, it tells me there is no suitable version for your OS (because its 8.04, not 7.10).

Does anyone know how to force install, or otherwise make it work? Maybe make the install think the OS is 7.10?

I have done lots of these installs, and I don't know of a way to force the install. You probably don't want to do that anyway as Plesk uses their own modified packages when the install is run and they have to match the version you are installing on or very bad things can happen. Why don't you run VMware Server or Xen and put a virtual machine on your box that is version 7.10? 

-Tim

---

### Post by pearjam on 2008-04-29
Well, I've re-partitioned my disk and installed 7.10. The Plesk control panel auto installer works, but I can't bring up the log in in a browser....  any ideas there?

---

### Post by Edward0181 on 2009-04-08
Would there be anyone that knows howto get Plesk 9.0 installed on 8.10 Ubuntu?

It keeps nagging about my 8.10 version server.

Thanks in advance

---

