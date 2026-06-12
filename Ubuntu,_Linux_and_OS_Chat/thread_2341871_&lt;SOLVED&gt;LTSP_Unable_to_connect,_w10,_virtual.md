---
title: "&lt;SOLVED&gt;LTSP Unable to connect, w10, virtual box virtual server."
date: 2016-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by JayKay3OOO on 2016-11-01
Hi all.

I have, in the past installed the linux terminal server project (ltsp) and connected thin clients to it using a single network card. Even a ltsp vm connecting a virtual computer and a real laptop to it.

I followed this guide this time:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

on version ubuntu gnome 16.10 64 bit (I used standard ubuntu server last time)

I thought there was more steps than that to make it work on a single network card. It knows about the ltsp server IP, but times out. I've set up the ltsp config file to match my network.

I'll keep looking around for that old guide I used, but if anyone can help that would be fantastic as I would like to present my ideas to my boss at some point.

But, I will try ubuntu server again. Perhaps I am missing some things it has.

Regards.

---

### Post by JayKay3OOO on 2016-11-01
Ah, well. I still have no idea what I was doing wrong.

It looks like I was installing the full ltsp which has a dns server rather than using dnsmasq and using the existing dns.

[http://blog.bobbyallen.me/2015/07/19/setup-a-ubuntu-14-04-lts-mate-terminal-server-with-ltsp/](http://blog.bobbyallen.me/2015/07/19/setup-a-ubuntu-14-04-lts-mate-terminal-server-with-ltsp/)

This is the guide I used. No need to even set up ips. Good for a test environment at least. 

Phew. That took a long time for something really simple!

Ran it on a base ubuntu server with kde on top. TO THE NEXT CHALLENGE!

---

