---
title: "How to install ubuntu server 12.04 in IBM x330m4 server"
date: 2014-05-06
forum: Server Platforms
---

### Post by mailkrushna on 2014-05-06
Hi Team.

   Recently procured a new IBM server x3300M4  . After installing ubuntu 12.04 server , it is not booting from harddisk . Is there any way to resolve this issue .

This is critical issue for us . Any help is highly appreciable .

---

### Post by Gyokuro on 2014-05-06
Hi

Checking IBM's site Ubuntu Server is not listed as an supported operating system: RHEL, SLES are but you can try in UEFI-settings:  **enable legacy only** and check following site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) (12.04 get mentioned in it) another try would to test 14.04. Sorry nothing better as we use HP equipment.

---

### Post by slickymaster on 2014-05-06
Not answering your question, but sort of correlated with it. You can find a list of certify Ubuntu on a range of IBM server models [here]("http://www.ubuntu.com/certification/make/IBM/?query=&category=Server&release=&level=Any").

---

### Post by mailkrushna on 2014-05-07
Hi Gyokuro,

   Thanks for reply . I don't want to configure raid at all . We have single HDD(1tb ) attached  . I am able to install ubuntu  . Not able to boot after installation completes . Just need info , need to take any extra steps for booting IBM server from ubuntu . IBM team not giving any support for installing any OS but recommending install RHEL .

I am not first people facing the issue .
[http://askubuntu.com/questions/303869/ubuntu-server-13-04-on-ibm-x3300-m4-boot-failure](http://askubuntu.com/questions/303869/ubuntu-server-13-04-on-ibm-x3300-m4-boot-failure)

---

