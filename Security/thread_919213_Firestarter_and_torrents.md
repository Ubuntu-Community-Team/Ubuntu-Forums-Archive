---
title: "Firestarter and torrents"
date: 2008-09-13
forum: Security
---

### Post by notsomeone on 2008-09-13
Is it possible to open every port for a torrent application but not for anything else?
All I can see is rules for unblocking IPs or ports.
I unblocked 6881-6891, but there are still so many blocked connection attempts from users on random ports outside of this range. It slows down the download a lot.
I am probably too paranoid, but I block all outbound traffic, and only whitelist when I see the need.
I use deluge on Kubuntu.

---

### Post by lovinglinux on 2008-09-14
> **notsomeone said:**
> Is it possible to open every port for a torrent application but not for anything else?

There is [TuxGuardian]("http://tuxguardian.sourceforge.net/"), that you can use to control network connections on an application basis, but is a dead project. I do not recommend using it. Nevertheless, the way Linux iptables work you will have to open the port for all applications and block access to specific applications on TuxGuardian. You can't open a port for a single application.

> **notsomeone said:**
> All I can see is rules for unblocking IPs or ports.
I unblocked 6881-6891, but there are still so many blocked connection attempts from users on random ports outside of this range. It slows down the download a lot.
I am probably too paranoid, but I block all outbound traffic, and only whitelist when I see the need.
I use deluge on Kubuntu.

The problem is that you are blocking outbound traffic, so most of blocked connections you are having are from your machine trying to connect to peers. When you open the ports 6881-6891 you are allowing inbound connections on these ports, so you will only accept connections on them. But, outgoing connections do not necessarily use those ports. You torrent client will choose any port available to send request to other peers. So if you block outbound connection, you will have to allow each and every outbound connection attempt, which is simply unpractical with torrent activity.

So what you have to do is use "Permissive" policy for outbound connections, at least while using torrent and create a rule in Firestarter to allow incoming connections on the ports you specified on your torrent client.

To increase your security  you could use Deluge IP Blocklist plugin. You can download IP blocklists from [[COLOR="Red"]**iBlocklist**[/COLOR]]("http://iblocklist.com/lists.php") or from [[COLOR="Red"]**Bluetack**[/COLOR]]("http://www.bluetack.co.uk"). So while your outgoing connections are "Permissive" and your torrent port is open for inbound connections, the blocklist will prevent your torrent client from attempting to connect to unwanted IP's and will prevent unwanted IP's from connecting your client even with the open port.

I do recommend that you don't use ports 6881-6891, because these are standard ports for torrent and several ISP's caps the bandwidth on those ports to slow down your torrent activity. You can use any port between 49152 to 65535 and don't forget to use Full Stream encryption. Using different ports from the torrent standards does not mean your speed will be compromised, because when you start a torrent your client will inform the tracker which port you are using, then the tracker will inform the other peers, so they can connect to you in the right port.

Also recommend that you use [[COLOR="Red"]**Moblock/Mobloquer**[/COLOR]]("http://moblock-deb.sourceforge.net/") to block IP's system wide, not only for torrent activity.

---

