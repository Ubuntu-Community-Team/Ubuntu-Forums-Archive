---
title: "Strange things happening since upgrade"
date: 2011-09-14
forum: Server Platforms
---

### Post by Shinhan on 2011-09-14
I upgraded my router box thats running Ubuntu Server to Natty (from Lucid Lynx if I remember correctly). 

The strange things I mention in the title is GMail attachments stopped working. Nobody on my network is able to upload any attachments in their GMail accounts. Tried using simple mode, other browsers, other computers, nothing. Files tested were <100kb word documents and some <1MB images. Singly or in groups, never works.

Today I tried uploading an image to imgur.com and I noticed something weird. When I try uploading a 141kb image the progress bar stalls at 23%. The 80kb image stalls at 40%. Diving I get to 32kb uploaded in both cases. 

So, it seems I am unable to upload anything larger than 32kb.

ADSL is provided by Netgear DG834 but it has Allow All rule, I disabled "Port Scan and DOS Protection option" and any other option that smacks of firewalls.

This might be relevant:
```

root@hogosha:~# tc qdisc show dev eth0
qdisc tbf 8001: root refcnt 2 rate 210000bit burst 28159b lat 50.0ms

```

As for using internet, everything else works. Websites, online games, torrents...

---

### Post by Shinhan on 2011-09-16
Still nothing? Nobody has any ideas?

---

