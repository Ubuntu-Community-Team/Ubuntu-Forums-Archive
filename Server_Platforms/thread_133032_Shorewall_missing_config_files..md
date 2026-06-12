---
title: "Shorewall missing config files."
date: 2006-02-19
forum: Server Platforms
---

### Post by fipeso on 2006-02-19
Hi,

I have just installed Ubuntu 5.10 as server.

I attempted to install shorewall.
sudo apt-get install shorewall
sudo apt-get install shorewall-doc

Now when I read how to configure shorewall at shorewall.net, I cant find the configurations files on my system.

Is there somthing else I need to apt-get, or do I need to use the tarball ?

---

### Post by XDevHald on 2006-02-19
[I]Quote from Shorewall.net

[/I]> If you install using the .deb, you will find that your /etc/shorewall directory is empty. This is       intentional. The released configuration file skeletons may be found on       your system in the directory /usr/share/doc/shorewall/default-config.       Simply copy the files you need from that directory to /etc/shorewall and modify the       copies.

**EDIT!**
> Note that you must copy /usr/share/doc/shorewall/default-config/shorewall.conf       and /usr/share/doc/shorewall/default-config/modules       to /etc/shorewall even if you do       not modify those files.
 
Hope this helps.

---

### Post by fipeso on 2006-02-19
Yes I read that also, but the files are not there.

But with "find -name two*" I found "/usr/share/shorewall-doc/examples/two-interfaces.tgz"

Seems ubuntu installs shorewall files in different places.

So, how do I untar that file ? As you can see I am completly newbie.

Thanks

EDIT

In case some other newbie is trying to get shorewall to work, apt-get also shorewall-doc. Then find the examplefiles in /usr/share/doc/shorewall-doc/examples/

tar -zxvf /usr/share/doc/shorewall-doc/examples/two-interfaces.tgz

---

