---
title: "Upgrade / update GLPI on UBUNTU"
date: 2009-03-02
forum: Server Platforms
---

### Post by joenieburg on 2009-03-02
Hello there,

Ik have on the UBUNTU 8.10 server a version 0.70.2  GLPI working,
In this version the LDAP doesn't go as I wanted it to go.

So I want to upgrade my installed version to 0.71.5

But I installed GLPI using this link
[http://www.ubuntugeek.com/glpi...are.html]("http://www.ubuntugeek.com/glpi-it-and-asset-managemet-software.html")

I already updated my UBUNTU server with apt-get update
and apt-get upgrade

But GLPI stays on the version 0.70.2

Anyone ho can help me with update-ing in ubuntu?
(the config fles are set in
/etc/glpi/config because of the ubuntu installation)

Thanks in advantage.

---

### Post by chele on 2009-09-15
First, I would recommend the newest version of glpi 0.72. It includes significant changes to the way software inventory and licenses are handled.

Second, you might try the .deb from debian. That installed on Ubuntu 9.04 without any conflicts for me.

---

