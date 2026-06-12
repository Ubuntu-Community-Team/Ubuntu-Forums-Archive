---
title: "OpenLDAP Problem"
date: 2010-05-01
forum: Server Platforms
---

### Post by satyanash on 2010-05-01
Hi,

  Problem Here,

The Ubuntu official server guide tells me that when installing OpenLDAP,the installation should ask me for a LDAP admin user name and pass. But when i give the command it simply doesn't ask me for one. 
I use Ubuntu 10.4 Server Edition.

The guide I've been following: [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html]("https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html")

The command used to install is:
> sudo apt-get install slapd ldap-utils

In the next line in the guide it is said that you can reconfigure the password with the dpkg command i tried doing that but then too it doesn't ask for a password anytime.

I tried becoming super user and then gave both the above commands but in vain.

And the installation and reconfiguration completes without any visible error. 

Please Help.
STTU


Edit:

This thread has been marked solved because this was posted when the guide for 10.4 was not available. Now it is available and the 10.4guide now does not anymore mentions that Open LDAP asking for a username and password..

The new guide : [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

---

### Post by IMadhavan on 2010-11-02
hi
it has been solved or not, Kindly reply me Because i am also having same problem. reply me ASAP

---

### Post by satyanash on 2010-11-02
well i did not actually solve it i just did a workaround.. 

We just wanted to shift servers and that one was taking space.. so i just cloned the whole server using clonezilla.. made a virtual machine using VirtualBox in another more powerful server and then loaded the image of that server into this VM.. 
in short we did not want to upgrade it, we just wanted to remove it so that it would take up less space.. and we could not shift the project because of reasons mentioned above..this seemed the only way to do it..

---

### Post by jabes69 on 2010-11-02
This issue regarding the availabilty of guides for Ubuntu Server 10.04 has been resolved although the guide for 10.04 is wrong and will not produce a working OpenLDAP installation and running the commands will result in errors. The guide for 10.10 has been updated and the commands in this guide will not produce errors but at the same time the guide will not produce a working LDAP server either.

Not sure if the guide is incomplete (though the assumption is that it is incomplete) but I have been working for 3 weeks now trying to setup an OpenLDAP server on 10.10 with no luck using any guide from anywhere. As soon as I get it working yoou can bet I will put up an extensive step by step HOWTO.

Until then good luck and don't let it stress you out too much - cuz it will if it can!

---

