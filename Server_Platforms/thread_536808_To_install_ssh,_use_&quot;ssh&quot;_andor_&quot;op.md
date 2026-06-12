---
title: "To install ssh, use &quot;ssh&quot; and/or &quot;openssh-server&quot;"
date: 2007-08-28
forum: Server Platforms
---

### Post by kentl on 2007-08-28
Hi!

I'm about to install SSH for remote controlling my home server.

This advice
```
sudo apt-get install ssh openssh-server

```Is given
[LIST]
[*][Ubuntu 7.04 (Feisty Fawn) LAMP Server Setup]("http://onlyubuntu.blogspot.com/2007/05/ubuntu-704-feisty-fawn-lamp-server.html") under the subheader "Install SSH Server"
[*][Installing Webmin On Ubuntu Feisty Fawn (7.04)]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty") under the subheader "Install SSH"
[/LIST]

But if I look at
[LIST]
[*][SSHHowTo]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29")
[/LIST]
It seems like I only can install the openssh-server.

I looked up those two packages at packages.ubuntu.org but I didn't really understood what their difference was. Do I need them both?

Thanks for reading! I'll thank you even more if you help me! :popcorn:

---

### Post by AndyCooll on 2007-08-28
No you don't need them both. You just need "sudo apt-get install ssh"

"ssh" is a metapackage and installs everything ssh related includingl openssh-server.

:cool:

---

### Post by kentl on 2007-08-28
Thanks! You may eat these virtual popcorn. :popcorn:

---

