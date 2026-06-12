---
title: "Server not responding issue"
date: 2011-01-18
forum: Server Platforms
---

### Post by gypsumwolf on 2011-01-18
History: Server running Ubuntu 10.10 Server Edition, CUPS and SSH. Cant print to laser printer (via cups) from windows laptop just about every morning until server is restarted. Already known: This is not a hardware problem.

Wrote a cron script to see if it solves issue.

Cron Job:
```
*/10 * * * * sh /scripts/keepalive
```

Script:
```
ping -c 1 192.168.1.1 > /stuff/ping_gateway.txt
sleep 15 && ping -c 1 [www.google.com](www.google.com) > /stuff/ping_google.txt
```


Any thoughts or suggestions?

---

### Post by Iowan on 2011-01-18
I doubt a server would have power management enabled (in BIOS)... but thought I'd mention it...

---

### Post by gypsumwolf on 2011-01-18
> **Iowan said:**
> I doubt a server would have power management enabled (in BIOS)... but thought I'd mention it...

I disabled it in BIOS. This is not a regular server, its a desktop used as a server.

---

### Post by gypsumwolf on 2011-01-19
I removed the cron job and script.

Now I double checked the bios. I did disable apic.

In the grub default I added a few options here it is:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=off apm=off noapic nolapic"
```

any other suggestions?

I had this issue on 4 separate computers and 2 different routers with Ubuntu Server Edition on semi-older machines.

---

