---
title: "Put ppp0 appearing in virtualbox"
date: 2010-06-08
forum: Virtualisation
---

### Post by bizkyt on 2010-06-08
Hello,

I'm using virtualbox with windows xp guest. My problem is my 3G pen connection doesn't appear in virtual box options -> network -> Bridged Adapter. Here goes a print screen:

[IMG]http://img696.imageshack.us/img696/8550/capturaecrawindowsconfi.png[/IMG]

ifconfig of ppp0:
> 
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.140.74.213  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:230 (230.0 B)  TX bytes:257 (257.0 B)


I know I can use the option Nat, and that works. But I want to use wireless connection in my host, and the 3G connection in the virtualbox. 
So anyone can help how to use or putting the ppp0 connection appearing in virtualbox?




Regards

---

### Post by pytheas22 on 2010-06-08
[This page]("http://webcache.googleusercontent.com/search?q=cache:b89HD8QNL4YJ:forums.virtualbox.org/viewtopic.php%3Ff%3D2%26t%3D12724+ppp0+bridge+virtualbox&cd=1&hl=en&ct=clnk&gl=us&client=ubuntu") (link to Google's cache because the real page isn't loading right now) basically explains how to do that.  But it says it might be difficult if you can only get one IP address assigned to your device.

---

### Post by bizkyt on 2010-06-08
I have read, but I don't know how to do what they say:

"f you can't select the connection from the VM settings, you can always do it the old fashioned way. You have to create a TAP interface manually, as VB no longer supplies this utility, and bridge it to your GSM connection. However, it might not work properly. Check it on the host first if you still have connectivity with the bridge running, then boot the VM and see how that works. You might get a problem due to only one IP address available."

I'me relatively new to linux and don't know how to do that :S

---

### Post by bizkyt on 2010-06-08
I have resolved the problem installing vmware player with xubuntu and now all work fine (virtualbox doesn't work with 3G, at least with me).

---

### Post by pytheas22 on 2010-06-09
I used to use [this thread]("http://ubuntuforums.org/showthread.php?t=346185") for manually bridging interfaces for use with VirtualBox.  In principle those commands should all work if you replace "eth0" with "ppp0".  If you need help let me know.

EDIT: didn't see your post above until posting my last response.  Glad to hear you've figured it out with VMware (as much as I dislike VMware...).

---

### Post by lio_013 on 2010-10-19
> **bizkyt said:**
> I have resolved the problem installing vmware player with xubuntu and now all work fine (virtualbox doesn't work with 3G, at least with me).

could you   tell me how did  u do it or the tutorial that u follow ?

---

### Post by pytheas22 on 2010-10-19
lio_013: a good place to start would be [here]("https://help.ubuntu.com/community/VMware").

---

