---
title: "inter net dosnot work after over night downloading. Deluge+PIA+Openvpn"
date: 2017-03-04
forum: Server Platforms
---

### Post by orbitmipi on 2017-03-04
helo

I have ubuntu mate 16.04 on a Odroid xu4 singel bord. I'm runing deluge + Privat Internet Accsess(VPN) + openvpn(its how I get PIA to work).
I have tryed to reconect wifi card. I have tryed chainging openvpn 'xxCassSinsitevexx.ovpn' (log into server P.I.A.) to a diferant ip. The only thaing that works is rebooting.

any sujestions like switshing to transmission ?

---

### Post by oldrocker99 on 2017-03-04
It's unclear whether Deluge is causing your trouble. You can always try Transmission, or qbitorrent, or any of the other torrent programs out there.

---

### Post by orbitmipi on 2017-03-04
the pia tech responded to my pc might have went in to sleep/hybernation. I run codi all night for tv wiel deluge is runing on ubuntu mate. So is it posabul for the desktop to go to sleep/hybernat ? and if so how to stop that ?

---

### Post by wildmanne39 on 2017-03-04
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-03-05
Have you checked the Power Options (or something called similarly) in the OS? It's similar in any OS, there are options controlling when you want the computer to spin down HDD, go to sleep, etc...

---

### Post by orbitmipi on 2017-03-05
ya I chek'd power setings for sleep. I woke up this morning ad the problime is the same. Seing I cant find any other options than chainging the torrent cliant ill try that and see if the problem is fix'd.

---

### Post by darkod on 2017-03-06
Depending on the torrent client it might be too much for the limited resources of such small boards. Give transmission a shot and check how it goes.

---

### Post by mastablasta on 2017-03-08
the issue is most likely because you allowed too many connections. and perhap syou are even downloading using too many connections. limit those to osme safe setting and work from there to increase these.

e.g. i you have 1 Mbit connection start by limiting speed to say 200 kbit, 2 file simultaneous download and allow max 30 connection in/100 connection out. it might be slow, but you Will see if the issue repeats or not. then if all is good you can increase it a bit more and a bit more until you hit the sweet spot.

i have 50mbit download speed, but for torrent i allow it to use max 5 mbit download and 1mbit upload. with limited connections etc.

---

