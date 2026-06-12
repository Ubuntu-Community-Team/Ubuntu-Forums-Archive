---
title: "Secure Firewall - UFW"
date: 2009-08-01
forum: Security
---

### Post by knetcozd on 2009-08-01
I need help to configure my system to a secure state, i know the basics of allowing ports and denying ports(21,53,110 etc...)using ufw, but i not a security expert, coming from windows XP - Norton 360 automatically setup the firewall rules and i had no problems.

I want to bring my firewall to the same or even more secure level than my XP Norton 360 system(i know some people debate how secure Norton firewall is -but i never had any problems with it), is there a easy to follow tutorial for noobs out their you can recommend or possibly a commercial firewall system like Norton for Ubuntu/Linux.

Thanks in advanced!!

---

### Post by wojox on 2009-08-01
I think this is what your looking for:

[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by sasho_zl on 2009-08-01
I'm using Shorewall ( [http://www.shorewall.net/](http://www.shorewall.net/) ) for configuring my netfilter and it works great.
Also it's a very good thing to familiarize yourself with iptables which is very powerful tool. You can find a good tutorial for iptables here - [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by ajgreeny on 2009-08-01
Are you running a server of some sort or just a standard desktop system?  If it's just a stand alone desktop system you probably don't need to configure your firewall in any way from the default that ubuntu gives you when installed.

Iptables, which is the actual firewall, not ufw or gufw, both of which are tools which just allow you to configure iptables, is set with all ports in a non listening state, so no outsiders can get in to your machine unless you allow them to.  I have not had any firewall configuration application, such as gufw or firestarter, on my machine for about 4 years, since I learned that one was not really needed.

See what other people say, and of course if you have a server setup, then you may well need to sort this out in more detail.

---

### Post by knetcozd on 2009-08-02
No i am just using a standard desktop, just concerned about on-line shopping,Although i do use xampp - just for php development.

---

### Post by ajgreeny on 2009-08-02
Sorry, no idea what xampp is but if it is not a server, you probably will be perfectly OK with the ubuntu iptables exactly as it is at install.  If you are behind a router, probably even less need for ufw or gufw.

OK, a quick search shows me that xampp is a server application related to apache, so a firewall application may well be needed, but as you can possibly guess, I am the wrong person to help you with this as I don't use one.

---

### Post by sasho_zl on 2009-08-02
> **knetcozd said:**
> No i am just using a standard desktop, just concerned about on-line shopping,Although i do use xampp - just for php development.
If you are interested in running a firewall like Shorewall just let me know and I will give you a detailed instructions how to set it up on a Ubuntu box for less then a minute :)

---

### Post by Rob_H on 2009-08-02
> **ajgreeny said:**
> Are you running a server of some sort or just a standard desktop system?  If it's just a stand alone desktop system you probably don't need to configure your firewall in any way from the default that ubuntu gives you when installed.

The default when you install Ubuntu is NO firewall. That's one of my few gripes about out-of-the-box security on Ubuntu. Fortunately, it is easy to enable it with:
```
sudo ufw enable
```
By default, UFW blocks all unsolicited incoming traffic, which works well unless you're running a server.

OTOH, if you have a desktop system behind a wired or wireless router, there's not much need for a software firewall anyway, as your router serves that function. Roaming laptops are a different story.

---

### Post by ajgreeny on 2009-08-02
> By default, UFW blocks all unsolicited incoming traffic, which works well unless you're running a server.
Sorry, but I believe you are misunderstanding what is meant by the ubuntu firewall.  As I understand things, running ```
sudo ufw enable
``` as you suggest changes nothing, as the default in ubuntu is exactly the same, ie, block all unsolicited incoming traffic.  The danger could be that the unwary will open ports such as those needed for the web or email and they will be open all the time, not just when running a browser or email client.

If I am wrong, apologies, but this is an ongoing discussion on these forums, and I think I am right.

---

### Post by Sef on 2009-08-02
> ajgreeny 	 		 		 	Quote:
 	 	 		 			 				By default, UFW blocks all unsolicited incoming traffic, which works well unless you're running a server. 			 		 	 	 
Sorry, but I believe you are misunderstanding what is meant by the ubuntu firewall.  As I understand things, running 

You are correct ajgreeny.    Ubuntu comes with a [firewall installed]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") ([netfilter aka iptables]("http://www.netfilter.org/")), but it is only accessible via the command line, unless you install a gui like ufw.

---

### Post by ajgreeny on 2009-08-03
Thank you Sef.

I sometimes doubt myself and begin to wonder if I really ought to have a firewall configuration application installed and use it, as many new users, more used to windows tend to do.  Your agreement with my thoughts is a confirmation that I can leave things as they are, not bother with running ufw or gufw, and just enjoy the freedom and security of Ubuntu as it comes for my non-server desktop machine.

---

