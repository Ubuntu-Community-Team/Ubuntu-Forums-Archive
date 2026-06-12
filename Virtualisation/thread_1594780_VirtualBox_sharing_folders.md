---
title: "VirtualBox sharing folders"
date: 2010-10-12
forum: Virtualisation
---

### Post by dpanda88 on 2010-10-12
Hi guys,

I'm just wondering if its possible for this to work. 

Right now I have 10.10 running as my main OS while using virtual box to run Windows XP Professional for work purposes. When I'm travelling I won't have the ability to use the internet therefore causing me to not be able to share my folders from 10.10 to windows xp.

Is there a work around where I can share my folders in 10.10 and be able to pick them up in virtual box (win XP) without having internet?

---

### Post by pricetech on 2010-10-12
Yes.  All you need to do is share what you want shared on your Ubuntu host and your windows guest will be able to access it.  You don't need Internet access to do that.

---

### Post by dpanda88 on 2010-10-12
> **pricetech said:**
> Yes.  All you need to do is share what you want shared on your Ubuntu host and your windows guest will be able to access it.  You don't need Internet access to do that.

can you guide me on how to do that? I'm still a newb in linux even though I took courses back in university haha. I never know much about virtualbox. Please and thank you!

---

### Post by pricetech on 2010-10-13
Try not to think about virtualbox per se.  Your Ubuntu host should be sharing just as if you were planning to access it over the network, which you are in effect doing.

In Synaptic search for system-config-samba which will install both Samba and an easy to use configuration tool which will appear as System - Administration - Samba.

Set your shares up that way and you'll be able to access them from your Windows guest as if the two machines were separate nodes on the same subnet.

The only other thing you'll need to do, which I forgot to mention earlier, is determine what Windows see as its gateway.  ipconfig /all will give you that address.  Use that as the host address for the shares you are trying to access.

---

### Post by dpanda88 on 2010-10-14
i tried the method you told me too but doesn't work. After turning off the internet and attempting to connect to the IP on the windows guest. It doesn't pick up.

---

### Post by ysNoi on 2010-10-15
Hi dpanda88...:)

Please try the following procedure...

1. Go to Settings of your Guest OS [XP]
2. Click on Shared Folders [You can see there an icon to add Shared Folders]
3. Select the Folder you want to share [Make sure to have Folder Name]
4. Click OK.

Now, turn on your Guest OS [XP]:

5. On the Devices Menu, click Install Guest Additions [Follow Instructions there].
6. On your Guest OS [XP], right click on My Network Places.
7. Select Map Network Drive [Choose Drive Letter]
8. On Folder option, encode \\vboxsvr\xxx where xxx is the Folder Name you shared on step no. 3.
9. Click Finish.

Hope that helps...

Enjoy...:)

---

### Post by pricetech on 2010-10-15
So you already have Samba and shares set up on the Ubuntu box ??

Can you ping it by the IP that shows up as the gateway for your windows guest ??

And yes, install guest additions if it's not already installed.  May or may not help with this, but you'll want it.

---

### Post by HermanAB on 2010-10-17
Hmm, this is not as simple as it should be...

If the host doesn't have an internet connection and is configured with DHCP, then the ethernet port and the whole network stack may be disabled and then the VMs cannot connect to the host.

To remedy that, you may have to assign an address to the host and the VM.

$ sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.2

Now the host should work.

On the guest, do the same kind of trick and set the default GW to point to the host:

$ sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.1

Now the two machines, host and guest, should be able to talk to each other.

---

### Post by andddlay on 2010-11-21
> **ysNoi said:**
> Hi dpanda88...:)

Please try the following procedure...

1. Go to Settings of your Guest OS [XP]
2. Click on Shared Folders [You can see there an icon to add Shared Folders]
3. Select the Folder you want to share [Make sure to have Folder Name]
4. Click OK.

Now, turn on your Guest OS [XP]:

5. On the Devices Menu, click Install Guest Additions [Follow Instructions there].
6. On your Guest OS [XP], right click on My Network Places.
7. Select Map Network Drive [Choose Drive Letter]
8. On Folder option, encode \\vboxsvr\xxx where xxx is the Folder Name you shared on step no. 3.
9. Click Finish.

Hope that helps...

Enjoy...:)

Thank you so much!!!  This helped a lot!  I can not access my music folder on Ubuntu on virtualbox :)

---

