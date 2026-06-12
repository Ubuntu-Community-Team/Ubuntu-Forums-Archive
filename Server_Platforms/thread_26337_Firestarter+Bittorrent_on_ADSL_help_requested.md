---
title: "Firestarter+Bittorrent on ADSL: help requested"
date: 2005-04-12
forum: Server Platforms
---

### Post by tv123 on 2005-04-12
Hi,

I am running a prerelease version of Hoary, and have setup my
firewall using firestarter (I will write a mini HOWTO later on). My FS
setup is rather restrictive, with no inbound connections allowed,
and opening only those ports and services necessary (HTTP/DNS etc),
both in FS setup as well as /etc/services.

Now, I opened up outbound ports 6881-6889 (in FS) to allow bittorrent (BT)
to work on my ADSL (earthlink) connection. But, BT doesn't work unless
I stop the firewall. After reading: [http://btfaq.com/serve/cache/25.html](http://btfaq.com/serve/cache/25.html),
I tried a few things there as I could interpret them, but the instructions
are slightly vague in the FS setting.

If there is a knowledgeable person out there on this issue, I'd appreciate
any comments and suggestions.

Thanks
Tom

---

### Post by falcon15500 on 2005-05-03
Hello,

  You have it a bit around the wrong way.  Ports 6881 - 6889 are ports that you open for **incoming** connections, not outgoing.  Not sure how you have set up FS, but your BT client generally needs to be able to connect outbound to port 6969, which is the common port for a BT tracker.
  While you don't _have_ to enable those inbound ports, BT will get better speeds if you do.  This is because of the way BT works.  If you don't allow inbound connections, you will only be connected to as many other BT clients as your client explicitly connects to - instead of other BT clients being able to connect to you directly.

Hope this helps.

falcon

---

### Post by kosmic on 2005-05-07
see in your Bittorent program what port is in used for outgoing conections, in general it should be 6969, and if it is that, just open that port in FireStarter.


For extra security just open that port for the machine that have the bittorrent runing, and drop all other traffic to the same machine

---

