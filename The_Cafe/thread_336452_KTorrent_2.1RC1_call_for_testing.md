---
title: "KTorrent 2.1RC1: call for testing"
date: 2007-01-11
forum: The Cafe
---

### Post by jdong on 2007-01-11
For those who don't know, KTorrent is light(ish)weight, feature-rich BitTorrent client written with KDE libraries (but it runs fine in GNOME, much lighter than Azureus to say the least!)

2.1RC1 represents a major upgrade to the 2.0.3 series. It now is one of the only Linux clients that supports (in parentheses are other clients that support the functionality mentioned under Linux):
 * Mainline DHT with full support for creating and using decentralized torrents (uTorrent+WINE and BitTorrent Mainline have full support, Deluge and rtorrent can use decentralized torrents but not properly create them. Azureus uses an incompatible DHT implementation)
 * uTorrent Peer Exchange for acquisition of more peers when trackers aren't available or are peers are dispersed amongst several trackers (uTorrent+WINE is the only other client to support this, Deluge will at 0.6-ish. Azureus will support this standard in the future too, but currently uses its own incompatible PEX)
* Reasonable RAM usage, 30MB RSS or less when downloading 2 DVD Linux ISO's (uTorrent+WINE [somewhat disputed because WINE library occupation cannot be measured without kernel memory profiling patchsets], rTorrent, Deluge)
* LAN peer finder for locating and prioritizing peers on the LAN (Azureus)
* Web interface and console interface for remote control (Azureus)


I'd like to introduce KTorrent 2.1 as soon as it releases (in about two weeks) in the dapper-backports and edgy-backports repositories, but I want to make sure that it's reasonably stable before doing so.

In all my testing, 2.1RC1 has been very stable with no bugs I've noticed, and few bugs reported.


Dapper and Edgy debs are available at [http://ktorrent.org/index.php?page=downloads](http://ktorrent.org/index.php?page=downloads) , if you have/use prevu, these debs can also be built from Feisty sources as a "backport".

If you are more bleeding edge, you can find SVN snapshot debs at [http://ktorrent.org/forum/viewtopic.php?t=1031](http://ktorrent.org/forum/viewtopic.php?t=1031)




Thanks in advance for all your help!

---

### Post by williamts99 on 2007-01-22
Do you know how to get the web interface to work on Gnome?  I haven't been able to get it to work, I get the following error when entering the web interface

HTTP/1.1 Internal Server Error
PHP executable error


Edit: Solved
sudo apt-get install php5-cli

---

### Post by bionnaki on 2007-01-23
the ktorrent beta is great. I highly recommend it to everyone. my only complaint is the icons look washed out and blurry. how about crystal icons?

---

