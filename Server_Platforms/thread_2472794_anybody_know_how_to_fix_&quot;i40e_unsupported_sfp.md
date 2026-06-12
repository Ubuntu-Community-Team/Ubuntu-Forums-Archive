---
title: "anybody know how to fix &quot;i40e unsupported sfp+&quot;"
date: 2022-03-12
forum: Server Platforms
---

### Post by kustomjs on 2022-03-12
Hello Guys
I am just wondering if anybody came up with good fix for issue i40e unsupported sfp+ on intel network adapters for ubuntu 21.10? because I tried this: [https://www.serveradminz.com/blog/unsupported-sfp-linux/](https://www.serveradminz.com/blog/unsupported-sfp-linux/) and it didnt come up with the interface at all.
but when I run: tim@libreqos:~$ rmmod ixgbe
rmmod: ERROR: Module ixgbe is not currently loaded <--- I get that error
tim@libreqos:~$ modprobe ixgbe
modprobe: ERROR: could not insert 'ixgbe': Operation not permitted  <--- error



Tim

---

### Post by #&amp;thj^% on 2022-03-12
> **kustomjs said:**
> Hello Guys
I am just wondering if anybody came up with good fix for issue i40e unsupported sfp+ on intel network adapters for ubuntu 21.10? because I tried this: [https://www.serveradminz.com/blog/unsupported-sfp-linux/](https://www.serveradminz.com/blog/unsupported-sfp-linux/) and it didnt come up with the interface at all.
but when I run: tim@libreqos:~$ rmmod ixgbe
rmmod: ERROR: Module ixgbe is not currently loaded <--- I get that error
tim@libreqos:~$ modprobe ixgbe
modprobe: ERROR: could not insert 'ixgbe': Operation not permitted  <--- error



Tim
Permissions I'm betting, run again as root or sudo.

---

### Post by kustomjs on 2022-03-12
I tried that and I get this:
root@libreqos:/home/tim# cd
root@libreqos:~#  rmmod ixgbe
rmmod: ERROR: Module ixgbe is not currently loaded
root@libreqos:~# modprobe ixgbe <---- noting loads

---

### Post by #&amp;thj^% on 2022-03-12
I think you missed a few steps, to confirm show this:
```
cat /etc/modprobe.d/ixgbe.conf
```

---

### Post by kustomjs on 2022-03-12
root@libreqos:~# cat /etc/modprobe.d/ixgbe.conf
cat: /etc/modprobe.d/ixgbe.conf: No such file or directory
root@libreqos:~#

---

### Post by #&amp;thj^% on 2022-03-12
Missed this or something else happened.
We will now add a parameter &#8220;options ixgbe allow_unsupported_sfp=1&#8221; to the ixgbe modue whoes path is :
All this should be run as root
**&#8220;/etc/modprobe.d/ixgbe.conf&#8221;. **
The commands is as follows:

    ```
# nano /etc/modprobe.d/ixgbe.conf [ which now opens a blank text editor ]

```
 ```
options ixgbe allow_unsupported_sfp=1
```
 ####[add this parameter ]
```
# rmmod ixgbe; modprobe ixgbe
```
 we then remove the module and reload it again with these commands. 

```
# ip a 
```
to check whether the missing interface with the uplink is showing.

If the above steps are successful and the missing interface is showing, then we can confirm that the issue is unsupported SFP+. However, the above test is not permanent and will be flushed out once rebooted.
Lets see how this works first.

---

### Post by kustomjs on 2022-03-12
tim@libreqos:~$ rmmod ixgbe; modprobe ixgbe
rmmod: ERROR: ../libkmod/libkmod-module.c:799 kmod_module_remove_module() could not remove 'ixgbe': Operation not permitted
rmmod: ERROR: could not remove module ixgbe: Operation not permitted

---

### Post by #&amp;thj^% on 2022-03-12
I plainly said as Root This is not root "$ " this is root "#"

---

### Post by kustomjs on 2022-03-12
its not going make a difference if its in regular user or root still same issue and error: 
root@libreqos:~# rmmod ixgbe; modprobe ixgbe
libkmod: ERROR ../libkmod/libkmod-config.c:657 kmod_config_parse: /etc/modprobe.d/ixgbe.conf line 2: ignoring bad line starting with 'rmmod'
root@libreqos:~#

---

### Post by #&amp;thj^% on 2022-03-12
Yes it dose mater,
one more time 
```
cat /etc/modprobe.d/ixgbe.conf
```

---

### Post by kustomjs on 2022-03-12
here you go root@libreqos:~# cat /etc/modprobe.d/ixgbe.conf
options ixgbe allow_unsupported_sfp=1
rmmod ixgbe; modprobe ixgbe
when I do ip a the sfp module doesnt even show up

---

### Post by #&amp;thj^% on 2022-03-12
> **kustomjs said:**
> here you go root@libreqos:~# cat /etc/modprobe.d/ixgbe.conf
options ixgbe allow_unsupported_sfp=1
rmmod ixgbe; modprobe ixgbe
root@libreqos:~#
Begs the question Why is this added? "**rmmod ixgbe; modprobe ixgbe**"
It should only show this:
```
options ixgbe allow_unsupported_sfp=1
```
Fix it first and try again as Root.

---

### Post by kustomjs on 2022-03-12
root@libreqos:~# cat /etc/modprobe.d/ixgbe.conf
options ixgbe allow_unsupported_sfp=1

root@libreqos:~#  rmmod ixgbe; modprobe ixgbe
rmmod: ERROR: Module ixgbe is not currently loaded
root@libreqos:~#

---

### Post by #&amp;thj^% on 2022-03-12
Try first:
```
#modprobe ixgbe
```
Show any out put please.
Or right after that command show this:
```
lsmod | grep  ixgbe
```

---

### Post by kustomjs on 2022-03-12
root@libreqos:~# modprobe ixgbe ---> shows noting
root@libreqos:~# lsmod | grep  ixgbe
ixgbe                 348160  0
xfrm_algo              16384  1 ixgbe
mdio                   16384  1 ixgbe
dca                    16384  3 igb,ioatdma,ixgbe

---

### Post by #&amp;thj^% on 2022-03-12
Whats shows in:
```
ip a
```
Any sign of the missing link?

---

### Post by kustomjs on 2022-03-12
SFP port doesnt even show up

---

### Post by #&amp;thj^% on 2022-03-12
Lets see if it's simmered down now,
```
# rmmod ixgbe
```
any output shown
If all is well try
```
# modprobe ixgbe
```
to reload, and take a peek at "ip a" again.

---

### Post by kustomjs on 2022-03-12
shows noting: 
root@libreqos:~# rmmod ixgbe
root@libreqos:~# modprobe ixgbe

noting in ip a link setup

---

### Post by #&amp;thj^% on 2022-03-12
If you want to force this mod add:
```
ixgbe.allow_unsupported_sfp=1
```
to the line GRUB_CMDLINE_LINUX=&#8221;ixgbe.allow_unsupported_sfp=1&#8221; 
```
sudoedit /etc/default/grub
```
update grub:
```
sudo update-grub
```
reboot>>> The Reboot flush's what we done thus far.
And starts with mod loaded, so if nothing still. IJDK 
and now check with "ip a" 
Now you know how to also remove it if this is futile.

---

### Post by kustomjs on 2022-03-12
I gave up on it I dont know if its going to work

---

### Post by #&amp;thj^% on 2022-03-12
Worth a try, we had a couple of misfires that would be a sure way to check if it will work. (or not :))

---

