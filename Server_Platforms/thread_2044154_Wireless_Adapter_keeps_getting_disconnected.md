---
title: "Wireless Adapter keeps getting disconnected"
date: 2012-08-18
forum: Server Platforms
---

### Post by computerfox on 2012-08-18
Hello all,

     I know I posted this topic before and I need help with it again.  Here are my specs:

     OS:Ubuntu
     Copy: Server
     Version: 11.10


    Here's my problem:

     I have a Netgear PCI wireless card installed.  If I do iwlist, it finds all of my networks.  If I try to connect, it connects.  After about 10 minutes, it gets disconnected from my router.  I would really like to set this up wirelessly.  Does any member have any suggestions?  Would backports do it?  If so, which backport should I use and please specify what I should install.  I know that the card is good because I tested it with multiple computers and I even had the client edition installed, which worked great.

    Some more specs:

      I edited my /etc/network/interfaces file because I remember that the client version didn't have any other interfaces except for the loopback.  I also restarted it via /etc/init.d/networking restart


I would be eternally grateful if someone can help me with this. Thanks.

---

### Post by computerfox on 2012-08-18
As an added note, I can put it back up simply with the script I wrote to reconnect and find the IP.  In order to fix it, I was thinking about creating a deamon out of my script, but I don't think that should need to be done since I think it's a basic function.

---

### Post by computerfox on 2012-08-18
WIth the potential of it being a bad PCI card or a card that needed a special driver, I'm trying out a Netgear USB.  Let's cross our fingers,toes,eyes, and ears.

---

### Post by computerfox on 2012-08-19
So, so far it's been staying connected, but now there's another problem-it's amazingly slow.  Would there be any way to speed it up?  What would cause it to slow down so much?

---

