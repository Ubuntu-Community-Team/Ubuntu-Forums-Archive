---
title: "Wanting to set up a server..."
date: 2010-07-29
forum: Server Platforms
---

### Post by cptrohn on 2010-07-29
Mainly just to be able to stream media to multiple PC's in the house... I have a netbook running Kubuntu netbook 10.04, a full size laptop running Kubuntu 10.04 and a Foxconn Mini system I built.. The Foxconn is the system I want to use as a server now... It has 2gb of RAM and a 2 TB Hard Drive, Atom dual core 64 bit processor SO I think it could be a decent server for my music, videos, pics, documents etc... My question is would be better off using my current install and setting it up for this like in this How-to I came across [http://www.instructables.com/id/Creating-a-Home-Media-Streaming-Center-with-Ubuntu/](http://www.instructables.com/id/Creating-a-Home-Media-Streaming-Center-with-Ubuntu/)  Or would it be better to use Ubentu server edition?  I also would like to be able to share these with my girlfriends windows vista machine (yes I still love her anyway lol)  I have never tried this or attemted it before.. Any tips or pointers that will save me some headaches down the road?  Any advice is greatly appreciated... Thanks!

---

### Post by Iowan on 2010-07-29
Moved to Server Platforms.
The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") is a good place to start. The server version comes OOTB (out of the box) without a GUI, but you can add one if you wish.

---

### Post by garfonzo on 2010-07-29
I have a Ubuntu Server running on similar specs. It holds all of our music, movies, TV recordings, and various documents. All computers in the house access the shared drives. I have three WinXP machines and one Vista machine all of which play nicely with Ubuntu and Samba shares. The tricky part I found (and when I say tricky, I mean that the whole process was easy, but this was a little less easy, but easy none the less) was setting up the Samba share structure. You have to edit a file on the server to allow the computers on your lan to access stuff. After that works, though, just setup network drives on the windows machines (map network drive). Then, the windows machines can access the server's data as if it were on their machine. 

Easy peasy :)

---

### Post by kgatan on 2010-07-31
For what you want id recommend you to set up a FreeNAS instead.
It has everything you need and is very easy to configure, everything is done through web interface.


A full blown server does all these things as well but needs much more configuration.

---

