---
title: "Filter is there, but CUPS doesn't see it"
date: 2009-11-17
forum: Server Platforms
---

### Post by koepked on 2009-11-17
I've tried setting up an HP DeskJet printer on 8.04 LTS in CUPS both from the command-line, and through the web interface. I can install, and see the printer, but nothing prints, and the printer page in CUPS says "Unable to start filter "foomatic-rip-hplip" - No such file or directory. 

Looking at the error log, I see that CUPS is trying to access a filter at: /usr/lib/cups/filter/foomatic-rip-hplip. In my filesystem, this is a link to /usr/lib/cups/filter/foomatic-rip, which is a link to /usr/bin/foomatic-rip, which does exist, with read and execute permissions for all.

Can anyone tell me what is going on?

---

### Post by koepked on 2009-11-18
Sorry about this, I gave bad info. I've been getting used to remotely administering over ssh, and the links that I said existed in the parent post DID exist, it's just that they existed on the local machine, not the server the printer is attached to. Might have to change the color scheme for the terminal I use for ssh so I can easliy differentiate it from my local terminal. Anyway, I put the links in on the server and all is good. If it's useful/interesting to anyone, I think rather than make the links by hand, they probably would have been created by installing the hplip package. Not sure though.

---

