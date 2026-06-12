---
title: "Webserver access shuts down after a few hours"
date: 2012-04-24
forum: Server Platforms
---

### Post by megahost on 2012-04-24
I posted this in general help, but figured I posted in the wrong section. I left a note saying not to comment in that one, but here's my problem.

I've recently encountered a problem that I haven't seen before. Usually, I'm able to turn on my test server and have it run continuously without a problem. Recently, I've encountered a problem where the web server crashes a few hours after boot, and I cannot connect to my test sites, or even connect via SSH for that matter(I had been able to before without a problem).

I appreciate all suggestions and hope to get this resolved.
Sean

EDIT - It works every time after boot for a few hours (just a side note)

---

### Post by Ryan Dwyer on 2012-04-25
You could start by looking at logs...

---

### Post by Jonathan L on 2012-04-25
Hi megahost

> It works every time after boot for a few hours

You wouldn't know if the uptime is the same each time you boot?  Always stays running for 3 hours or whatever?  That would be a great clue.

Also: do you know if it's still running and just the networking has stopped, or whether it's completely stopped.

Of course, the logs are the right place to start.  See if you can find out how long it was up for.

I'd also take a look at the networking.  If it's on a static IP address, is it possible something else switches on and starts using it?  Or if it's DHCP, is it possible there's something awry with your DHCP server?

Hope those tips help.

Kind regards,
Jonathan.

---

### Post by louis vitton on 2012-04-25
Is it a VPS or is it your own server?
If all else fails and it is a VPS - take it up wit hthe hoster - if that fails software rebuild (reinstall everything from backups) if at all possible.

---

### Post by megahost on 2012-04-25
> **Jonathan L said:**
> Hi megahost



You wouldn't know if the uptime is the same each time you boot?  Always stays running for 3 hours or whatever?  That would be a great clue.

Also: do you know if it's still running and just the networking has stopped, or whether it's completely stopped.

Of course, the logs are the right place to start.  See if you can find out how long it was up for.

I'd also take a look at the networking.  If it's on a static IP address, is it possible something else switches on and starts using it?  Or if it's DHCP, is it possible there's something awry with your DHCP server?

Hope those tips help.

Kind regards,
Jonathan.

Thanks for the reply. Unfortunately, (I don't know why) when I boot it I cannot connect at all via ssh. The modem doesn't even recognize the server is on, thus it's not even making the wired connection.

I've checked for Ethernet cord problems yet I still have the same problem

---

### Post by megahost on 2012-04-27
New information

After booting it up and hooking it to a monitor, I found a boot error that looks much like this one:

```
[ 1565.842367] Call Trace:
[ 1565.842473]  [<f8ab660f>] ieee80211_vap_detach+0x7f/0x130 [wlan]
[ 1565.842585]  [<f8c7a845>] ath_vap_delete+0x125/0x460 [ath_pci]
[ 1565.842685]  [<c021a2a6>] __delay+0x6/0x10
[ 1565.842777]  [<f8b91de5>] zz016e1251+0x5f/0x15a [ath_hal]
[ 1565.842887]  [<f8ab66d6>] ieee80211_ifdetach+0x16/0x60 [wlan]
[ 1565.842994]  [<f8c79f29>] ath_detach+0x79/0x160 [ath_pci]
[ 1565.843097]  [<f8c81833>] ath_pci_remove+0x23/0x90 [ath_pci]
[ 1565.843198]  [<c02274a6>] pci_device_remove+0x16/0x40
[ 1565.843290]  [<c02826d4>] __device_release_driver+0x64/0xa0
[ 1565.843387]  [<c0282c2b>] driver_detach+0xcb/0xd0
[ 1565.843482]  [<c0282223>] bus_remove_driver+0x73/0xa0
[ 1565.843576]  [<c022757e>] pci_unregister_driver+0xe/0x70
[ 1565.843672]  [<f8c81c82>] exit_ath_pci+0x12/0x2b [ath_pci]
[ 1565.843769]  [<c01521a2>] sys_delete_module+0x112/0x190
[ 1565.843865]  [<c031e14f>] do_page_fault+0x13f/0x730
[ 1565.843958]  [<c01804a0>] do_munmap+0x180/0x1f0
[ 1565.844054]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 1565.844153]  =======================
[ 1565.844208] Code: de 8b 86 a0 00 00 00 8b 15 fc 8a ae f8 8b 40 08 e8 b8 90 6f c7 83 3d f8 8a ae f8 01 74 44 83 2d f8 8a ae f8 01 8b 86 9c 00 00 00 <8b> 50 5c 85 d2 74 1a 89 d0 e8 c4 ab 6b c7 8b 86 9c 00 00 00 c7
[ 1565.846514] EIP: [<f8ad2e7e>] ieee80211_virtfs_vdetach+0x8e/0xf0 [wlan] SS:ESP 0068:cbc19e64
[ 1565.846688] ---[ end trace e7ac0b008e3f587c ]---
```

This one's not my exact one but I don't know how to get the information from the shell on the server over here. I'm stuck here and it won't complete the boot. Thanks again for anyone who can help out!

---

### Post by Jonathan L on 2012-04-27
> This one's not my exact one but I don't know how to get the information from the shell on the server over here. I'm stuck here 

Hi ... if you can scroll up just a touch you'll see the error message itself, rather than the context ... perhaps you could get a photo on your phone?
Kind regards,
Jonathan.

---

### Post by webservervideos on 2012-04-27
not sure about your system so I cannot really help...  but, I would try a script on the webserver that runs every 10 minutes and sends a signal out (a mail, a ping, whatever) and see if it stays awake and does not disappear.  if a virtual environ or a bonded bridge is around, that could cause an issue with loss of connection, but the above ping would keep it up.  I think you got to tell us more...is this in a datacenter? what switch, router, etc is being used to get to it. are you using ip addresses to access it as well as domain names and they are both down?  is this a home unit? router at home? dhcp, static....  hard to know where to go without knowing where you are.

---

