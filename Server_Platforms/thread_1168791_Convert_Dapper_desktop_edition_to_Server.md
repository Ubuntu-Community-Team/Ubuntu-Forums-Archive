---
title: "Convert Dapper desktop edition to Server"
date: 2009-05-24
forum: Server Platforms
---

### Post by /etc/init.d/ on 2009-05-24
Hello

I am running Ubuntu 6.06.2 LTS (Dapper) on my server at the moment.

When I installed the server, I used the regular desktop ISO but opted to install a server (i.e. no GUI).  

I noticed that Dapper is due to reach end of life in June for the desktop edition, but the server edition will be supported until 2011.

However, I'm not sure which edition I am running.  I did not specifically use the server ISO so I assume I'm running the desktop edition.

If this is the case, is there any way I can convert the desktop install to a server install, or is there a way I can use the server repositories?  I want to still be eligible for security updates but I don't want to reinstall my server as it's stable and running exactly how I need it.

Thanks.

---

### Post by Iowan on 2009-05-24
[Here]("http://ubuntuforums.org/showthread.php?t=1089168") is a similar thread.
I thought support for Dapper had ended (since support for Gutsy just ended), but I discovered that Dapper server (LTS) support (as you mentioned) goes through 2011.

---

### Post by netztier on 2009-05-24
> **/etc/init.d/ said:**
> 
However, I'm not sure which edition I am running.


The contents of the file **/etc/issue** will tell you

> **/etc/init.d/ said:**
> 
If this is the case, is there any way I can convert the desktop install to a server install, or is there a way I can use the server repositories?

There are no "server specific" repositories, it's all shared. 

The main thing that makes a server install is the special preselected **set of packages** (or rather: the lack thereof, since the default server install has no GUI, no Multimedia thingamagics etc), and the **server kernel**. 


So to "convert" an existing Desktop installation to a Server installation, the main change you do is to install the server kernel. There are two meta-packages by the names of **linux-image-server** and **linux-restricted-modules-server**, they will always point to the most current version for your distribution/version. The server kernel has different tuning parameters for server workload.

So... 

```
aptitude install linux-image-server linux-restricted-modules-server
```

might just do the trick. 

The problem with such a "crossgrade" might be that you won't get updates for *all* installed software packages. The typical "server software" packages like dns, dhcp, samba, apache, mySQL etc. and of course the kernel will be maintained and patched up to 2011, but the installed GNOME, Multimedia etc packages probably won't, once Desktop support for Dapper runs out. 

You just might do away with the unneeded packages by performing a rigorous *aptitude remove --purge <package name>* session, until all desktop-related packages are removed. Like this you can return to the stripped-down feature/software set of a server install - while keeping your services up-and-running.

regards

Marc

---

