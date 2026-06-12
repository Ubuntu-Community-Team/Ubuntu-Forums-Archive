---
title: "Ubuntu Server Messages Log Issue"
date: 2006-12-17
forum: Server Platforms
---

### Post by sindows on 2006-12-17
Hey Guys,

Been using ubuntu for about 4 months now... Running desktops and a server.

I was having some login issues with one of my users on the server, so i have a look in /var/log/messages and noticed that there is heeps of instances (and i mean heeps) of the follwing

```
Dec 17 06:47:05 phantom syslogd 1.4.1#17ubuntu7: restart.
Dec 17 07:07:05 phantom -- MARK --
Dec 17 07:27:05 phantom -- MARK --
Dec 17 07:47:06 phantom -- MARK --
Dec 17 08:07:06 phantom -- MARK --
Dec 17 08:27:07 phantom -- MARK --
Dec 17 08:47:07 phantom -- MARK --
Dec 17 09:07:08 phantom -- MARK --
Dec 17 09:27:08 phantom -- MARK --
Dec 17 09:47:08 phantom -- MARK --
Dec 17 10:07:09 phantom -- MARK --
Dec 17 10:27:09 phantom -- MARK --
Dec 17 10:47:10 phantom -- MARK --
Dec 17 11:07:10 phantom -- MARK --
Dec 17 11:27:11 phantom -- MARK --
Dec 17 11:47:11 phantom -- MARK --
Dec 17 12:07:11 phantom -- MARK --
Dec 17 12:27:12 phantom -- MARK --
Dec 17 12:47:12 phantom -- MARK --
Dec 17 13:07:13 phantom -- MARK --
Dec 17 13:27:13 phantom -- MARK --
Dec 17 13:47:14 phantom -- MARK --
Dec 17 14:07:14 phantom -- MARK --
Dec 17 14:27:14 phantom -- MARK --
Dec 17 14:47:15 phantom -- MARK --
Dec 17 15:07:15 phantom -- MARK --
Dec 17 15:27:16 phantom -- MARK --
Dec 17 15:47:16 phantom -- MARK --
Dec 17 16:07:17 phantom -- MARK --
Dec 17 16:27:17 phantom -- MARK --
Dec 17 16:47:18 phantom -- MARK --
Dec 17 17:07:18 phantom -- MARK --
Dec 17 17:27:19 phantom -- MARK --
Dec 17 17:47:19 phantom -- MARK --
Dec 17 18:07:19 phantom -- MARK --
Dec 17 18:27:20 phantom -- MARK --
Dec 17 18:47:20 phantom -- MARK --
Dec 17 19:07:21 phantom -- MARK --
Dec 17 19:27:21 phantom -- MARK --
Dec 17 19:47:22 phantom -- MARK --
Dec 17 20:07:22 phantom -- MARK --
Dec 17 20:27:22 phantom -- MARK --
Dec 17 20:47:23 phantom -- MARK --
Dec 17 21:07:23 phantom -- MARK --
Dec 17 21:27:24 phantom -- MARK --
Dec 17 21:47:24 phantom -- MARK --
Dec 17 22:07:24 phantom -- MARK --
Dec 17 22:27:25 phantom -- MARK --
Dec 17 22:47:25 phantom -- MARK --
Dec 17 23:07:26 phantom -- MARK --
Dec 17 23:27:26 phantom -- MARK --
Dec 17 23:47:27 phantom -- MARK --

```

Now im running ubuntu server drapper drake.

This is probably a really simple issue but i couldnt find anything on google for the error/non-error.

Any help would be much appricated!

Cheers,
M.

---

### Post by adaptr on 2006-12-17
The MARK log line is output every 20 minutes by the kernel to assure you it's still alive.
That's it, really.

---

