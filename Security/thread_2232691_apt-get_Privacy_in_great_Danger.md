---
title: "apt-get Privacy in great Danger ?"
date: 2014-07-03
forum: Security
---

### Post by Opencast on 2014-07-03
Hi,

As far as i can see all repository servers in Ubuntu/Debian use "http" to download binaries and sourcecode. I think this is a big problem because it is not encrypted it would be possible for others to see wich software i am installing or wich software allready is installed in the system (by watching wich updates system downloads).

Newest snowden files show that the NSA is marking and surveillancing everybody who is downloading privacy software such as TOR, I2P, GNUnet and so on (see: [http://daserste.ndr.de/panorama/aktuell/nsa230_page-1.html](http://daserste.ndr.de/panorama/aktuell/nsa230_page-1.html)). 

So if im going to make a "apt-get install tor" or "tails" it might be quite likely that this will cause my internetconnection to be under surveillance cause NSA (and others who are doing Deep Packet Inspection) can see that im Downloading TOR or other software. If they know what Software i have installed they could use this information for targetet attacks and so on.

An other Problem might be that authoritarian regimes like china or russia might block downloading some software from repository by using their DPI Systems to disconnect Download. Have allready seen that in shool networks where all Ubuntu Software with "torrent" in filename is blocked by filter and therefore not downloadable.


So why is Ubuntu not using SSL for its Repositories to strenghten Privacy and make Censorship impossible ???

---

### Post by mooreted on 2014-07-03
Everyone, everywhere is on their stupid lists. But you might have a point. The repos might use other methods of protecting themselves, I don't know.

---

### Post by tgalati4 on 2014-07-03
That would then make all Ubuntu users targets of packet collectors.  

I think their current filters include emacs users and exclude those who have Unity installed.

---

### Post by ian-weisser on 2014-07-04
Apt will happily use SSL if you wish it to.
See [http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get](http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get)

---

### Post by monkeybrain20122 on 2014-07-10
> **Opencast said:**
> Hi,
Newest snowden files show that the NSA is marking and surveillancing everybody who is downloading privacy software such as TOR, I2P, GNUnet and so on (see: [http://daserste.ndr.de/panorama/aktuell/nsa230_page-1.html](http://daserste.ndr.de/panorama/aktuell/nsa230_page-1.html)). 


Well you are probably being marked already for being on this forum ;)
[http://ubuntuforums.org/showthread.php?t=2232902](http://ubuntuforums.org/showthread.php?t=2232902)

---

### Post by thnewguy on 2014-07-11
> **ian-weisser said:**
> Apt will happily use SSL if you wish it to.
See [http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get](http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get)

The problem is, many repositories do not support HTTPS connections, making APT's ability to use an encrypted connection useless. You almosst have to have your own repository mirror set up to make use of APT's SSL support.

---

### Post by ian-weisser on 2014-07-11
Any mirror can indeed use HTTPS if the mirror admin wishes.

Mirrors are volunteers. I don't think there is any way to compel a mirror admin to require HTTPS or to forbid HTTPS.

You might get a better answer if you ask the mirrors mailing list. See [https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors) for more information on the mirror standards and how to contact the volunteer mirror admins.

---

