---
title: "Samba share opening in windows media player"
date: 2014-12-22
forum: Server Platforms
---

### Post by Giovanni_Stephan on 2014-12-22
Hi everyone and thank you for trying to help me. I have installed samba on my Ubuntu server and I want to access my share from a windows 7 computer. If I open "network" on my windows 7 computer, I can see my share but it is located in the "media device" section instead of the "computers" section. I think it's because of that that when I try to open the share, it opens windows media player instead of the shared folder. How can I bring my share to the computer section instead of being recognized as a media device?  Here's a picture (its in french if you are wondering):

[IMG]http://i.imgur.com/FueTruo.png[/IMG]

---

### Post by TheFu on 2014-12-22
Installing samba is NOT enough. It must be configured.  There are lots of how-to guides. The howtogeek blog has the easier versions that use a desktop gui for this.  

Further, just installing samba doesn't make it into a DLNA server ... that happens from some other service - could be a few different options - definitely NOT samba doing that.

---

### Post by Giovanni_Stephan on 2014-12-22
Well Ive configured samba right cause if I kill samba process, the share dissapear in windows so I think its configured right

---

### Post by volkswagner on 2014-12-22
TheFu is correct.  I'm guessing you installed The Plex media server on your ubuntu server. Plex is the DLNA server
showing as a media server in Windows Explorer. Why it disappears when you kill SAMBA is unknown to me (perhaps your media server
is attached to the share).

Open Windows explorer and enter your server ip and see what share populate.

\\192.168.0.25 or whatever the ip of the server is.

From the server post the output of:

```
testparm -v
```

Also, is "ubuntumediaserver" the hostname or netbios name for the server.  Windows limits NETBIOS names to 15 characters, so
that would be a bit long and cause problems.

---

