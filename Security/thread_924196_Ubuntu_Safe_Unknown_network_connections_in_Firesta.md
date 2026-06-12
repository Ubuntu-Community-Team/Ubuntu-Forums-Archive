---
title: "Ubuntu Safe? Unknown network connections in Firestarter"
date: 2008-09-19
forum: Security
---

### Post by patsymcox on 2008-09-19
Firestarter currently shows 4 active connections to UNKNOWN, There is no listing that says in which program these connections are running, Deluge connections are coming under 'Python' as the program. 

I have seen another thread also with same question. Somebody know something about this? 

Other thread.

[http://ubuntuforums.org/showthread.php?t=783816](http://ubuntuforums.org/showthread.php?t=783816)

Sometimes Firestarter blocks some connections too.

(I have recently installed and uninstalled the program called SubdiverSVN. which was not running, so I uninstalled it, ([http://subdiversvn.sourceforge.net/](http://subdiversvn.sourceforge.net/)) Is this program safe?)

Thanks

---

### Post by lovinglinux on 2008-09-19
Check if the connection is outbound or inbound. If the connection is outbound then most likely that Firestarter will know the program originating it. Deluge gives you Pyhton, because it is written in Python and uses it as "backend".

Incoming connections usually have a blank program name because Firestarter cannot determine the software originating the connection. This is normal.

If you have configured Deluge to accept connections in the standard torrent ports, then incoming connections will probably listed as BitTorrent service, but if you choose a different port it can be listed as "Unknown" or even something else. This is normal because Firestarter uses the port number to determine the service name.

Even if the connection is outbound, Firestarter can give you a different service depending on destination port. For example, if the peer you are connecting to has configured his torrent client to accept connections on port 21, your Firestarter will list the connection as FTP service. If the port is not used by a common service it will be listed as "Unknown". This is also normal.

I'm not an expert and these are observations I have made myself. So if you are really concerned you shouldn't rely on Firestarter to monitor connections. There are other softwares out there that can give you more reliable info about your ports and connections.

---

### Post by lovinglinux on 2008-09-19
About the other thread you have posted the link:

I read somewhere that Firestarter can show you connections as active, even if they are already closed, specially after running a torrent client like Deluge.

I have observed this myself. One or two connections remain listed as active, even if I turn of my modem. These connections are also listed as active using iptstate to monitor connections, but not using iptraf.

If you are really concerned about them you can stop your modem and reboot. Once you are logged in again the connection will be gone, then you can connect to ISP again to retrieve a new IP if you have a dynamic one (most likely). With this new IP there is no way to the persistent connection to get to you again, unless is your machine that is originating it.

---

