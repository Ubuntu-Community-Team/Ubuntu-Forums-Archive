---
title: "Firewall and IP blocker (New Linux user)"
date: 2009-05-06
forum: Security
---

### Post by Ace King on 2009-05-06
I installed Ubuntu 9.04 on my PC and Laptop and was wondering if I need to setup a firewall and IP blocker? I download torrents and want to make sure I'm as secure as possible. I am new to Linux, and still figuring a lot of things out. I used to use Zonealarm Security Suite when I was running XP. If there was a program out there that is easy to use it would be nice.

Thanks,
Ace

---

### Post by Ace King on 2009-05-06
Ok, I installed Firestarter which was easy to setup. I am still unsure about IP blockers. I used to use Peer Guardian 2 in XP. I do not know how to set anything manually as I am an EXTREME NEWBIE!
I apologize in advance if these are dumb questions. I am hoping that I pick this new OS up quickly.

---

### Post by lovinglinux on 2009-05-06
Firestarter is not recommended anymore. It's kind of old and problems with it are starting to be a common place. BTW, Firestarter is not a firewall, but a firewall manager, which means it is just a tool for configuring rules for [iptables](http://en.wikipedia.org/wiki/iptables) (the real firewall), without knowing the commands.

The recommended firewall manager now is ufw, which can be controlled by gufw interface. Just open "Applications >> Add/Remove and search for "gufw", then install the application called "Firewall Configuration".

For ip blocking you have basically two choices, [iplist](http://iplist.sourceforge.net/) and [moblock](http://moblock-deb.sourceforge.net/). I personally use and recommend moblock, but since you were a Peerguardian user, you will probably feel more comfortable with iplist, since it looks a lot like Peerguardian.

---

### Post by Ace King on 2009-05-06
Thanks for the response. I uninstalled Firestarter and installed "gufw" Firewall. Not to sound stupid, but what settings do I use while downloading torrents?
And just out of curiosity, why do you like Moblock better? Is it easy to use?
It always sucks being the new guy!

---

### Post by lovinglinux on 2009-05-06
> **Ace King said:**
> Thanks for the response. I uninstalled Firestarter and installed "gufw" Firewall. Not to sound stupid, but what settings do I use while downloading torrents

Basically, you will deny all incoming traffic and allow just what you need. In this case, you need t allow incoming connections on the port configured in your torrent client. 

> **Ace King said:**
> And just out of curiosity, why do you like Moblock better? Is it easy to use?

Both programs are excellent. Iplist GUI uses java, which I don't like. But I think the most important to me is that moblock has built-in scripts that I can use to include my own iptables rules, so I don't need to use a firewall manager. With moblock I have a single application that handles my firewall settings and the ip blocklists. I also think that moblock has more flexibility in regard to allowing ports, protocols or IPs, but I might be wrong since it has been a while since I used iplist for the last time.

---

### Post by brian_p on 2009-05-06
> **Ace King said:**
> Thanks for the response. I uninstalled Firestarter and installed "gufw" Firewall. Not to sound stupid, but what settings do I use while downloading torrents?

You are are new to Ubuntu so may not know the default install has no open ports. No services are running so nobody can connect to your machine.

If you run a torrent client it will allow connections on a port you designate. Now people can connect to your machine but that is what you want (isn't it?) because you are file sharing. Note that all the other ports are denied.

You have now installed ufw and set it to deny all connections, which is what was happening before you configured it. You then open port x for torrenting, which is what you did before installing ufw by just running the torrent client.

From this you may conclude installing ufw hasn't exactly got you anywhere. You would be correct.

---

### Post by Ace King on 2009-05-06
Thank you both for the responses. My questions were answered. I will go onto the IRC channel and see if I can just listen in and learn. There is so much to learn with this new OS.

---

### Post by uljanow on 2009-05-06
There's a good [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download_main.html") for Beginners and few threads regarding IP blockers [1][2].


[1] [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)
[2] [http://ubuntuforums.org/showthread.php?t=803183](http://ubuntuforums.org/showthread.php?t=803183)

---

