---
title: "[SOLVED] Samba?"
date: 2008-02-07
forum: Server Platforms
---

### Post by tjwoosta on 2008-02-07
i downloaded firestarter today although i have been told previously that it was not necessary.
 right off the bat i keep getting hits from  193.158.1.45 on port 138 that say the service is samba, what is samba? 
also from the same ip on port 6646 that say service unknown. what could this be? do i need to worry about this or is this something i should ignore?

---

### Post by renzokuken on 2008-02-07
samba is a service that allows windows computers and linux computers to communicate and exchange files over a network

---

### Post by tjwoosta on 2008-02-07
is this something to do with my home  network being a windows network?
 it doesn't seem to do anything when i block it, therefore i dont need it right?
The only thing that i share with windows computers is the printer.

---

### Post by freebeer on 2008-02-07
You'll note that the IP address is traditionally one used for local traffic.  If you check your windows machine, it's IP address is probably the same, so that tells you that it's coming from that machine.

You'll want to do a little research on that port 6646 thingy.  I did a quick google, and apparently there is a known exploit using that port as a form of DoS attack on McAffee products.  I didn't dig into it any deeper.  This wouldn't be a problem for your server, but it *might* (don't panic now :) ) indicate that your Windows machine has a nasty infection that is trying to exercise the exploit.  Then it could be nothing at all, but it's worth trying to figure out what on your Windows machine is using that port number... and why.

---

### Post by tjwoosta on 2008-02-07
hmm that sounds bad because i use mccaffe on our windows computer.  I just went out and bought it last month. This is why i want to switch over to ubuntu.

---

### Post by freebeer on 2008-02-07
Heh... I'm on the helpline staff for a game and we have to tell folks to uninstall mcaffee and Norton because they interfere with the game's ability to communicate with the game servers.  They're both resource hogs, too.  We get them to use free and superior AV programs that don't exhibit this behavior.

It's possible that it's not a virus at all.. perhaps there's some bit of code in mcaffee that using that port to phone home or whatever.  It could be perfectly innocent.  *shrug* but it's worth checking out to know what it's really doing.  Peace of mind and all that... ;)

---

### Post by buntunub on 2008-02-07
> **tjwoosta said:**
> is this something to do with my home  network being a windows network?
 it doesn't seem to do anything when i block it, therefore i dont need it right?
The only thing that i share with windows computers is the printer.

Yes. SAMBA is the Windows Network Protocalls. Its used to communicate with Windows machines on a Network. Its very bothersome to get it setup right and there is quite the detailed wiki on it on Ubuntu docs, amongst many other places. For Printing use one of the other Printing Protocalls if you dont want to mess with Windows Networking. Linux has many, many different ways to Network which are much simpler to setup and configure and far more secure such as NFS, sshfs, and ssh. Of course, you can always go with FTP too. Research these and have fun with Linux!

---

### Post by karlwilbur on 2008-04-08
I came across this port (6646) being open when I nmaped a friend's system across the internet. After a bit of digging and a lot of Googlein, it would seem that McAfee uses this port as a cross-talk port for its applications. Systems running McAfee software will send/receive broadcast traffic on port 6646. (Just try running etheral/wireshark for a few days with and without McAfee running day and you'll see what I am talking about)

I did see that there was a security vulnerability with McAfee software that allowed a remote attacker to send an oversized packet (not sure how big it needs to be) to a victim machine on port 6646 which would result I a DoS. I don't know if the DoS is localized to the McAfee service or if it actually locks up Windows.

I would appreciate and insight that others might nave on this.

--
Karl Wilbur

---

