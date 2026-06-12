---
title: "Integrating Debian default or Ubuntu in an office network"
date: 2011-03-16
forum: Server Platforms
---

### Post by PunkLV on 2011-03-16
Greetings.
So I've been asked to install a file/printer server and, possibly, inet proxy for a small office (5 PCs). My concern is:
There are:
[LIST]
[*]4 PCs on XP x32
[*]1 PC on Win7 x64
[*]2 Printers, one of them with a scanner
[/LIST]
Some buisness software they use does not cope with win7.
Had hard time installing additional x64 drivers for printer (which are obsolete by now, I guess).

Network runs on a simple router which is connected to internet.
For now they have been using simple sharing of C:\ folders, which had freaked my out a bit. 

So..Despite XP being old and a presence of x64 machine on the network, do I:
[LIST]
[*]install x64 server edition
[*]install x32 one
[/LIST]

What additional software, besides Samba and printer/scanner drivers, I will need to handle both architectures?

I have rather basic understanding of how servers work, i.e. I run samba, apt-cacher, torrents on my home network, therefore:

Any advice from people who have dealt with architectural chaos on a win offic network is really appreciated.

---

### Post by lykwydchykyn on 2011-03-16
IME client OS architecture makes zero difference in choosing a server OS.  64 bit debian/ubuntu isn't going to work any better with 64 bit Windows than the 32 bit version.

The more pertinent question is what server hardware you're installing on?  If it's new and has 4 GB of RAM or more, I'd go with 64 bit.  Otherwise stick to 32.

For network scanning I've had good experiences with saned, but I've never tried it with Windows clients.  There is a Win32 client for saned, but I've never tried it. See [http://www.xsane.org/xsane-win32.html](http://www.xsane.org/xsane-win32.html)

---

### Post by PunkLV on 2011-03-16
Thank you.
So the main problem currently they have is:
Printing is screwed up. Printer was connected to XP machine (A), then moved to Win7. Now XP machine (A) and (B), see the printer, but do not print. 

As I understand they are planning to gradually upgrade their OS'es and this leaves me with one question:
Will implementing a single machine for file and printer sharing solve the current and possible future problems?

As far as I know (and that is not too far), print server would not care which machine had sent him the print request and can be set to override any user preferences for printing.

And the other concern: should Samba security level be *user* with their accounts in passwd and smbpasswd? Which in turn will be in the same unix group with certain group privileges?

---

### Post by lykwydchykyn on 2011-03-17
I have always found printer sharing more straightforward on Linux (barring the unfamiliarity aspects) than on non-domain Windows machines.  I won't say you won't ever have *any* issues moving to a print server, but it uncomplicates a lot of things.

As for the best way to approach SAMBA, I suggest you take a look at a book called "samba by example", which you can find in HTML or PDF format for free on the samba.org site.  The technical details are somewhat redhat-oriented, but if you gloss over that the theory is very helpful.  It describes situations very similar to what you're working on and how best to approach them.

---

### Post by PunkLV on 2011-03-17
Am currentry on chapter 5.
By the way, today have had successfully solved the printing issue. Nonetheless, got their chief convinced to put up a server for all their files plus backup, and, possibly, squid, from their old hardware.
Anyways..
Thanks for the help, lykwydchykyn
Best of luck,

---

