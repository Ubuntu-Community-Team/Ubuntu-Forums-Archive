---
title: "Ubuntu One does not add a computer"
date: 2010-05-14
forum: Ubuntu One (CLOSED)
---

### Post by milenixloerdi on 2010-05-14
Hello,

After the upgrade to 10 Lucid Ubuntu one 1) did not connect 2) cannot add any computers anymore.

The help provided here [https://wiki.ubuntu.com/UbuntuOne/FAQ#Account](https://wiki.ubuntu.com/UbuntuOne/FAQ#Account) did not work, i.e. no browser window opened after the execution of the command

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```so that I can add my computer.

Can anybody help please?

Thanks.

---

### Post by joshuahoover on 2010-05-14
> **milenixloerdi said:**
> Hello,

After the upgrade to 10 Lucid Ubuntu one 1) did not connect 2) cannot add any computers anymore.

The help provided here [https://wiki.ubuntu.com/UbuntuOne/FAQ#Account](https://wiki.ubuntu.com/UbuntuOne/FAQ#Account) did not work, i.e. no browser window opened after the execution of the command

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```so that I can add my computer.

Can anybody help please?

Thanks.

I think I can help. :) Do you use Network Manager for managing your network connections or do you use something like a USB modem or something else that is managed by a different piece of software? If you're not using Network Manager for your network connection, but have it installed, then it will cause Ubuntu One to not function properly. Please see the steps detailed in the comments (starting at comment #11) of the following bug: [https://launchpad.net/bugs/576636](https://launchpad.net/bugs/576636) 

Thank you,

Joshua

---

### Post by milenixloerdi on 2010-05-14
Hi Joshua,

I followed it since #11 and I "Got state: 3". Does this mean I use Network Manager? I dont want to loose my connection if I try to uninstal it with sudo apt-get remove network-manager

It still doesnt allow me to add computer though...

---

### Post by joshuahoover on 2010-05-14
> **milenixloerdi said:**
> Hi Joshua,

I followed it since #11 and I "Got state: 3". Does this mean I use Network Manager? I dont want to loose my connection if I try to uninstal it with sudo apt-get remove network-manager

It still doesnt allow me to add computer though...

OK, 3 there means you are connected via Network Manager so definitely do not remove it. 

Can you file a bug following these steps, so that I can take a look at the logs?

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by milenixloerdi on 2010-05-27
Thanks.

The commands
```
sudo apt-get install ubuntuone-client-tools
u1sync --authorize

```worked for me to open browser window and add computer.


Its still doesn't appear to be synchronizing, but I will examine what this reason might be.

Cheers!

---

