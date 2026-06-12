---
title: "Ubuntu Server 13.10. How to change the network interface name?"
date: 2013-10-31
forum: Server Platforms
---

### Post by Roswebnet on 2013-10-31
Hi everyone,

In previous versions of Ubuntu you could easily change the name of a network card in following file:
*vim /etc/udev/rules.d/70-persistent-net.rules*

then search for eth0 and replace it with e.g.: LAN. Further, it is possible to use this name in following file:

[I]vim /etc/network/interfaces

[/I]In Ubuntu server 13.10 there is no *70-persistent-net.rules* file. Therefore, I have a logical question 

How I can change the network card name on Ubuntu 13.10?

Thank you.

---

### Post by Roswebnet on 2013-11-08
No one?

---

### Post by Doug S on 2013-11-08
> **Roswebnet said:**
> 
In previous versions of Ubuntu you could easily change the name of a network card in following file:
*vim /etc/udev/rules.d/70-persistent-net.rules*
... In Ubuntu server 13.10 there is no *70-persistent-net.rules* file.Strange, I have the file:```
doug@test-smy:~$ [COLOR=#ff0000]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
doug@test-smy:~$ [COLOR=#ff0000]ls -l /etc/udev/rules.d[/COLOR]
total 8
-rw-r--r-- 1 root root  443 Oct  4 14:09 [COLOR=#ff0000]70-persistent-net.rules[/COLOR]
-rw-r--r-- 1 root root 1157 Sep 18 11:14 README
doug@test-smy:~$
```

---

### Post by Roswebnet on 2013-11-10
Hi Doug S
  
  I tried your commands here is the result:
  
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Ubuntu%20Network/Screenshot%202013-11-11%2000.32.01.png[/IMG]

Results looks strange, isn't it?
  
  
  The Ubuntu was downloaded from here:
  
  [http://releases.ubuntu.com/13.10/](http://releases.ubuntu.com/13.10/)
  
  ubuntu-13.10-server-amd64.iso               16-Oct-2013 21:46
 
 P.S. By the way I had the same problem by 13.04. However, it was not so important. I thought it was just a bug, but when it comes on 13.10 I began to wonder why? By12.04 it worked without problems. In addition, this is a virtual machine in VirtualBox 4.3 on Windows 8.1 Pro.

---

### Post by Doug S on 2013-11-12
Well, I am at a loss. I do not have the file ( /etc/udev/rules.d/70-persistent-net.rules ) on my 13.10 desktop VM machine. It also doesn't seem to be there on a 14.04 server VM that I created yesterday, however there is currently other grief with that VM. I searched and searched and any reference I could find about changing network interface name used the /etc/udev/rules.d/70-persistent-net.rules file method.

---

### Post by Roswebnet on 2013-11-12
I searched too, but cannot find anything. That is weird. It looks like 70-persistent-net.rules file was removed or there is not happened any generation of this file. In addition, maybe udev does not work? I tried couple of codes to regenerate but without success.

I am out of any solutions... Bug?

---

### Post by Doug S on 2013-11-12
Have a look at /lib/udev/rules.d/75-persistent-net-generator.rules. There is a [link]("http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/") in the file that, I think, contains the answers you have been looking for.

---

### Post by Roswebnet on 2013-11-12
Oh man... It's a bit complicated... Why not to add a generated or exampled "70-my-net.rules" file under  /lib/udev/rules.d/ ? It was so easy before this update...
  
  Like this one(based on standard 70-persistent-net.rules):
 
 ```

 #Uncomment this line
 #SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:xx", NAME="ethx"
 #Check ifconfig -a for network cards and related MAC address.
 #Place right MAC address in "xx:xx:xx:xx:xx:xx".
 #Give a right name for your network adapter, by replacing the "ethx".
 #Repeat for other network adapters.
 #Do not forget to fill the /etc/network/interfaces with chosen names.
 
```
 
 However, the reasons which are displayed [here]("http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/") of course are very useful, especially this 5:
[LIST]
[*]Stable interface names across reboots 
[*]Stable interface names even when hardware is added or removed, i.e. no re-enumeration takes place 
[*]Stable interface names when kernels or drivers are updated/changed 
[*]Stable interface names even if you have to replace broken ethernet cards by new ones 
[*]The names are automatically determined without user configuration, they just work 
[/LIST]
But the 70-xxx.rules should stay under  /lib/udev/rules.d/. IMHO.
 
 After Doug S link I found a bit more advanced tutorial on Gentoo forum:
 [http://forums.gentoo.org/viewtopic-p-7285268.html](http://forums.gentoo.org/viewtopic-p-7285268.html)
 Looks also useful, but I prefer option 2 from [http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) under chapter:
    I don't like this, how do I disable this?
 Those one I choose for solution (see the code tag from this post)
 
 Thank you.

---

