---
title: "Ubuntu home server for a family"
date: 2012-12-16
forum: Server Platforms
---

### Post by igodspeed on 2012-12-16
Hi,

I would like this to be a work in progress. What I would like to do is create a discussion on setting up ubuntu server for home where a list of possible software that could be installed on the server which would allow for more uses of a typical home server. So like i would like to create a file storage system but also use that computer to save tv shows using tv tuner card. In this discussion people can list useful software or links which would possibly make life easier after setting up dedicated Ubuntu server for family. 


[LIST]
[*]I would like the internet to go through the server and so i can allow for internet access to  kids on only set times.  I would also like logs to be made of website visited and restrict websites. So this would be my first request.
[*]A server configuration which would use the least amount of power possible.
[/LIST]
Thanks and hope to hear from you

---

### Post by igodspeed on 2013-04-13
Bumb

---

### Post by Cheesehead on 2013-04-14
> **igodspeed said:**
> Hi,
I would like the internet to go through the server and so i can allow for internet access to  kids on only set times.

You're really talking about two different services: A configurable gateway/router, and a service to do that configuration.

It's a good idea to keep your gateway/router as simple as possible - it should *only* handle network connectivity and security. That simplicity keeps the machine from crashing, and makes recovery much simpler. I built a gateway/router that is very low power, fanless, and boots from a custom LiveUSB (no disk). It has 700 days of uptime and counting. When you add hardware and services, you add power consumption, you add points of failure, and you add complexity that makes diagnosing and fixing the problem much harder (and you don't have an internet connection to look up answers until it's fixed).

Put other services (like DVR, media jukebox, backup servers, game servers, chat servers, log servers, torrent servers, ntp servers, etc) on a real server. A totally separate machine with disks and disk monitoring software and power management software and wake-on-LAN and other complexities that require a bigger, louder power supply and fans...but spends most of it's time sleeping.

Changing user access is a service, too. Use the server to host the logic and settings and cron jobs, and have the service log into the router using ssh. This keeps your router simple, and allows you to test changes before implementing.

As my needs grew, I wound up splitting my server. I wanted some services to run 24/7, but other services only occasionally. So I built a second low-power system for the always-on services (gameserver, chat logger, logserver, torrent server) so my power-hungry server (backups, media server, different games) would wake up less often.

---

### Post by igodspeed on 2013-08-01
Still i am wondering if there is an actual program. Perhaps a distribution of linux which already does this. You mentioned power management, do you know of any program which does power management like spin down the disk and so forth?

---

### Post by Hexxus on 2013-08-01
> **igodspeed said:**
> Still i am wondering if there is an actual program. Perhaps a distribution of linux which already does this. You mentioned power management, do you know of any program which does power management like spin down the disk and so forth?

Most routers can accomplish the first part you're trying to accomplish - with even filters on keywords that you don't want your kids exposed to. 

For example most modern routers I've seen can:

* Authorized computers for non-restricted browsing (parents machines)
* Times other computers can access the internet
* Keywords to block content (from your kids machines)

Most of my friends servers at home are learning boxes that they do things with, then have others for file-sharing, printer sharing etc... like you spoke of.

---

