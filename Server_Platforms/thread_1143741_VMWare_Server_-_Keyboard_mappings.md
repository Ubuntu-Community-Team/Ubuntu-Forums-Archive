---
title: "VMWare Server - Keyboard mappings"
date: 2009-04-30
forum: Server Platforms
---

### Post by Yoeri on 2009-04-30
Hi,

I installed VMWare server 2 on an Ubuntu 9.04 server. The VMWare server has a few Windows XP Machines configured.
I only use the firefox console addin to use the machines (I use ubuntu 9.04 as desktop os).


However, the keyboard mappings in Windows XP are not right. I tried adding xkeymap.usekeycodeMap = true to
every imaginable config file on the server without satisfying results.
The alt-gr key keeps acting like an enter, up, down, left and right are
not mapped correctly, ...


Can anybody help out?

Kind regards

Yoeri

---

### Post by fmsismo on 2009-04-30
I have the same issue with vmware server 2.0.1 and ubuntu jaunty.

I will keep searching for a solution.

---

### Post by Yoeri on 2009-05-01
It is very annoying and almost makes vmware server unusable to me.
I foud keymap files in the .mozilla firefox extensions folders, so I thought he would be using the keymap that corresponds to your browser language, without success.

Hope someone picks up this thread with a good solution...

I'll keep you posted if i find something...

grtz
Yoeri

---

### Post by Easdaq on 2009-05-01
i have the same problem..i search all internet but not found solution
 
 
 
> **Yoeri said:**
> Hi,
 
I installed VMWare server 2 on an Ubuntu 9.04 server. The VMWare server has a few Windows XP Machines configured.
I only use the firefox console addin to use the machines (I use ubuntu 9.04 as desktop os).
 
 
However, the keyboard mappings in Windows XP are not right. I tried adding xkeymap.usekeycodeMap = true to
every imaginable config file on the server without satisfying results.
The alt-gr key keeps acting like an enter, up, down, left and right are
not mapped correctly, ...
 
 
Can anybody help out?
 
Kind regards
 
Yoeri

---

### Post by Yoeri on 2009-05-01
SOLVED.

I always tried adding config lines to server configurations. When noticing that the console worked correclty in Windows, I started to think about the client.

Steps To Solve:
1. touch ~/.vmware/config      Config doesn't exist when using the addin
2. add xkeymap.nokeycodeMap = true to the config file
3. reconnect to your virtual machine and it works

An answer in this post motivated me in creating the config file myseld  [https://bugs.launchpad.net/ubuntu/intrepid/+source/vmware-package/+bug/289098](https://bugs.launchpad.net/ubuntu/intrepid/+source/vmware-package/+bug/289098)

Grtz
Yoeri

---

### Post by Easdaq on 2009-05-01
Please help me
my strucuture is one folder called 
vmware-server-distribo
   inside this folder i have the folders
bin
doc
etc
installer
lib
man
sbin
vmware-vix
 
where i could create the config file? please help me

---

### Post by Yoeri on 2009-05-02
Hi, I did this:

- Install Ubuntu Jaunty Server on my server machine
- Followed the instructions at  [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) for installing VMWare server
- Used a client desktop machine (ubuntu 9.04) with firefox to connect to the server
- Installed the Firefox VMWare addin
- Edited ~/.vmware/config on the **client** to get the key mappings right.

Hope this helps

Grtz
Y.

---

### Post by windependence on 2009-05-02
You guys can do what you want but trust me, ESXi is way faster and more stable than VMware Server. No need for a host OS, and none of the problems you are experiencing. There is a myth out there that it is not free and you need some kind of special console viewer. You don't. You can use the VIC (VMware Infrastructure Client) to manage your VMs. It comes with ESXi. When you install it, if you open the web console in a browser, there is a link to download the VIC. Many people are not aware of this. The only issue you may have is getting your storage recognized, but there are work arounds for that too.

-Tim

---

### Post by Yoeri on 2009-05-02
Thanks, I was not aware of that ...

I'll keep my vmware server for the moment as he is now installed and configured like it should ...

---

### Post by fmsismo on 2009-05-02
Thanks a lot.  Work for me!

---

### Post by Easdaq on 2009-05-02
ok, finally solved. I found the hide file in the hide folder i don't know this. 
All keys solved with
xkeymap.usekeycodeMap = true 
less alt gr solved with
xkeymap.keycode.108 = 312 # Alt_R
Thanks a lot Yoeri

---

