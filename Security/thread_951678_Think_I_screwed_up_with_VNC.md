---
title: "Think I screwed up with VNC"
date: 2008-10-18
forum: Security
---

### Post by AmusedToDeath on 2008-10-18
Here's the scenario: I have a file server/torrent box that runs headless on my network at home behind a router. I have VNC/ssh running with resumable sessions, and usually just access the box on my local network behind the router, with 5900 closed on the router. Unfortunately, I recently opened port 5900 temporarily to access it via the internet, but forgot to close it when I was done (I know, I'm an idiot - should've used tunneling). 

When I got home I discovered a copy of TheWorld.exe (a windows browser I discovered - which seems strange) sitting on my desktop, indicating someone had been using it besides me. There were multiple copies of it there that had been unzipped from it's tar file - which makes me think (hope?) it was just a harmless script kiddie that stumbled in. There's nothing particularly sensitive on the Linux box, but I realized that it has samba running on it and is shared with a windows box that *does* have some very sensitive financial data on it. So my fear is that whoever accessed the machine may have accessed other files on the network.

Is there some way I can tell what activity went on while this person used the machine?

---

### Post by cariboo on 2008-10-18
The first thing to do is pull the network cable. Then check your log files to see if you can find what whoever it was changed. If you can't find anything in the logs, a full reinstall is in order.

If you are really interested in what happened follow the Forensic section if this howto:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

Jim

---

### Post by AmusedToDeath on 2008-10-18
Thanks for the help Jim. The first thing I did was "pull the plug", and I will definitely follow your advice to do a full format/reinstall. For the reasons outlined in my original post, I am concerned about what happened after the machine was compromised. I'm a little bit of linux noob - which log files should I be checking?

---

### Post by Dr Small on 2008-10-18
Did the VNC server have a password setup on it, and if so, was it secure?

---

### Post by cariboo on 2008-10-18
Did any users on your Ubuntu computer have write access to your windows shares, it might be an idea to scan your windows computer for root kits. You can find a free tool here:

[http://www.sophos.com/products/free-tools/sophos-anti-rootkit.html](http://www.sophos.com/products/free-tools/sophos-anti-rootkit.html)

as well as doing a complete virus and spyware scan.

Jim

---

### Post by AmusedToDeath on 2008-10-19
Dr Small: I used [this]("http://ubuntuforums.org/showthread.php?t=122402") guide to set up my VNC server. But I think I set the password using vncpasswd instead on putting it in the conf file. SO it may have been accessible without a password. Again, it was only intended to be used on a trusted network. 

Jim: Sophos detected no rootkits. Thanks!

---

