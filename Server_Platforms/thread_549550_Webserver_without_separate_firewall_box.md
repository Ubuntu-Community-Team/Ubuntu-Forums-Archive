---
title: "Webserver without separate firewall box?"
date: 2007-09-12
forum: Server Platforms
---

### Post by shimamoto on 2007-09-12
Is it possible to configure a secure Ubuntu webserver without having a separate box as a firewall?  

The server is only running one website, and nothing else.  I was thinking about just using iptables to close down every port except 80 and a random port for OpenSSH.  

If you properly configure iptables is that enough to eliminate the need for another firewall box in front of the server?  

I'd like to keep it simple and do it all in one box, but maybe it's not a good idea.  What are the major issues?  Has anyone else ever tried this and got it to work successfully?  

I'm running 6.06 LTS with a basic LAMP configuration for the site.

Thanks.

---

### Post by robert_pectol on 2007-09-12
The answer is.....  drumroll......   YES!  :-)

And here's a firewall solution for you called, "Ubuntu-firewall" that will make it easy to do exactly what you suggested:

[http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)

Good luck!

---

### Post by HermanAB on 2007-09-12
It would be an insult to put a firewall box in front of a Linux server.  In any case, what OS is the firewall going to run - most likely Linux...

---

### Post by reckless2k2 on 2007-09-12
way to put over your project robert_pectol...jk

seriously though. your webserver can hang on a DMZ now anyway. ubuntu has no open ports until you open them. 80 is open and whatever other server you might have running on that box like ssh. 

ubuntu has really got the incoming thing down. iptables can help you with the outgoing and tweak the incoming more to drop stuff rather than reject...etc.

so basically run a netstat -tap and see what's going on. like i lock my stuff down on ssh hard and everything else along with using like fail2ban or denyhosts.

---

### Post by shimamoto on 2007-09-12
Thanks for the info.

I've had a lot of people tell me that you should always have a separate firewall, but I don't know if they have a clue and I have never worked with Ubuntu as a webserver before.

I've seen some interesting things done with iptables:
[http://ubuntuforums.org/showthread.php?t=546468](http://ubuntuforums.org/showthread.php?t=546468)
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/)

So, it seems like it makes sense, but I haven't found a definite source of info on the subject.  I just want to make sure the security of my webserver is bulletproof from the beginning.

I'd appreciate any more suggestions on the subject.

---

### Post by HermanAB on 2007-09-13
Most firewall devices run Linux, so putting a Linux firewall in front of a Linux server is redundant and won't buy you any more security.

If you are running a Windoze server, then you absolutely *have* to put a Linux firewall in front of it, or it won't last very long.

Cheers,

Herman

---

### Post by reckless2k2 on 2007-09-13
again....typically when you are running web servers, ftp servers, mail, etc........................they are on your DMZ. when they are on your DMZ there is no protection. servers of this nature typically run linux because of the builtin firewall. 

ubuntu has all ports closed by default except those you open like 80 for web server. 

adding runs or more software would be related to incoming AND outgoing. if you are concerned about an outgoing issue dive in to it.

---

