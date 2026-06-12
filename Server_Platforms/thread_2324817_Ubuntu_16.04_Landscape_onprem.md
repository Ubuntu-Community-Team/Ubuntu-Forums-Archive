---
title: "Ubuntu 16.04 Landscape onprem"
date: 2016-05-16
forum: Server Platforms
---

### Post by cerberus2 on 2016-05-16
I am trying to centrally manage my  ubuntu servers at home, I have 8 which is well within the free portion of landscape for on prem. I tried these instructions here:
[http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use](http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use) and [https://help.landscape.canonical.com/FrontPage?action=show&redirect=LDS%2FRecommendedDeployment](https://help.landscape.canonical.com/FrontPage?action=show&redirect=LDS%2FRecommendedDeployment)

Neither set of instructions works they fail at the same step. [COLOR=#111111][FONT=Consolas]sudo apt-get install landscape-server-quickstart
[/FONT][/COLOR]This package doesn't come down from the ppa in fact it doesn't exist in the ppa at all....
[https://launchpad.net/~landscape/+archive/ubuntu/16.03/+index](https://launchpad.net/~landscape/+archive/ubuntu/16.03/+index)

there is a landscape-server but that's vastly different from the quickstart. I didn't attempt to install that since I was under the impression that the onprem was specifically landscape-server-quickstart.

I have tried other ppa's 15.04 I believe was the last and I managed to grab a copy of landscape-server-quickstart which then fails for apache-mpm-prefork workers. I couldn't find that package and ended up tossing my hands in the air, I even went so far as to look at cramming spacewalk into my environment at home and managing ubuntu from that...I'd rather not have to do that. So...does anyone have any experience with landscape on-prem? Is the landscape-server the same as landscape-server-quickstart?

---

### Post by swanseaboy on 2016-07-20
You can now install quickstart with:

add-apt-repository ppa:landscape/16.06
apt update
apt install landscape-server-quickstart

---

### Post by toby-humphrey on 2016-09-06
I am trying to install, have the 16.06 ppa added but get the message:

*E: Unable to locate package landscape-server-quickstart*

---

