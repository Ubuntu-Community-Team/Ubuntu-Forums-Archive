---
title: "Forked-daapd alternatives?"
date: 2012-05-23
forum: Server Platforms
---

### Post by Fury24 on 2012-05-23
So im running three computers two laptops and a desktop the desktop is a dedicated ubuntu server which i just upgraded to 12.04 and forked-daapd broke which made me sad. So now im hunting around trying to find some alternatives to forked-daapd preferably still in the command line. One temporary work around im considering is tangerine on the non main laptop but id really prefer the server handle all the streaming any solutions (other than patience?)

---

### Post by Rezista on 2012-05-24
Are you getting any errors in /var/log/forked-daapd.log? I am actually half way through building it here locally with some more features. I could look into it for you.

---

### Post by Valentini on 2012-05-24
I don't have any alternatives, but you might be experiencing [https://bugs.launchpad.net/ubuntu/+source/forked-daapd/+bug/921119]("https://bugs.launchpad.net/ubuntu/+source/forked-daapd/+bug/921119")

---

### Post by Fury24 on 2012-05-24
> **Rezista said:**
> Are you getting any errors in /var/log/forked-daapd.log? I am actually half way through building it here locally with some more features. I could look into it for you.
Oddly enough I'm not getting any errors.

---

### Post by Fury24 on 2012-05-24
What im noticing is that when i restart the server the program dies without any aanoucement and when i run /etc/init.d/*forked*-[I]daapd start i get 
[/I]```

Starting RSP and DAAP media server:     main: Forked Media Server Version 0.19gcd taking off
 ERROR.

```

this is a copy of my daapd-forked log 
```

[2012-05-21 23:08:13]     mdns: Avahi state change: Client failure
[2012-05-21 23:08:13]     mdns: Avahi Server disconnected, reconnecting
[2012-05-21 23:08:13]     mdns: Avahi state change: Client connecting
[2012-05-21 23:08:24]     main: Got SIGTERM or SIGINT
[2012-05-21 23:08:24]     main: Stopping gracefully
[2012-05-21 23:08:24]     main: mDNS deinit
[2012-05-21 23:08:24]     main: Remote pairing deinit
[2012-05-21 23:08:24]     main: HTTPd deinit
[2012-05-21 23:08:25]     main: Player deinit
[2012-05-21 23:08:25]     main: File scanner deinit
[2012-05-21 23:08:25]     main: Database deinit
[2012-05-21 23:08:27]     main: Exiting.
[2012-05-21 23:17:33]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-21 23:24:42]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-22 00:05:24]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-22 07:53:13]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-23 21:00:38]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-23 22:22:29]     main: Forked Media Server Version 0.19gcd taking off
[2012-05-23 22:22:53]     main: Forked Media Server Version 0.19gcd taking off

```
if youd like anymore information please ask id love to get this problem solved since my work around is proving not working

---

### Post by Rezista on 2012-05-24
When I'm building/deploying forked-daapd here i get that a lot when trying to start it. I wait a few seconds then try again and it starts up ok 90% of the time.

---

### Post by Fury24 on 2012-05-24
> **Rezista said:**
> When I'm building/deploying forked-daapd here i get that a lot when trying to start it. I wait a few seconds then try again and it starts up ok 90% of the time.
Im using server 12.04 im reasonably sure that something has been broken between 11.10 and 12.04

---

