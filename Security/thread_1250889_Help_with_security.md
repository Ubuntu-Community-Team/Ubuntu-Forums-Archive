---
title: "Help with security?"
date: 2009-08-27
forum: Security
---

### Post by sadwinch on 2009-08-27
Hi,

So I am a complete newbie when it comes to running linux, and am completely baffled by security and networking.

Ok, so I am running ubuntu jaunty, and the gnome gui. I installed this firewall application called Firestarter, and now when I check the "Active Connections" list there are connections there constantly, even when i am not using the internet or any program that uses the internet.

The most worrying aspect is most of the IPs on this list seem to belong to regular people, i.e. are regular machines.

Info on the list is shown as followed.
Source    Destination           Port         Service    Program 

Heres a couple of lines.

                86.136.73.131                     Unknown       this is blank for all of them

                189.115.4.60                       Traceroute      


The second one worries me to no end.
So my questions are:

1. Is my computer being used by others?
2. Is there some app on my comp that initiates those connections?
3. Couuld this be caused by windows malware because im using wine?
4. Did I just make a complete *** of myself on the forums, and there is nothing to worry about?

Thanks in advance.

EDIT:
So I just saw there is a security section in the general support area. Sorry for posting here.

---

### Post by rookcifer on 2009-08-27
run in the terminal:

```
sudo netstat -atpvnl
```

This will show all your current connections and what program is initiating the connection.

I am not familiar with firestarter because I don't use a firewall (other than my router).  It would be better if you were to use GUFW (the graphical front-end for Ubuntu's firewall).  

P.S. all Linux firewalls utilize the Netfilter kernel hooks and the IPtables firewall.  In other words, all of these firewalls are just GUI's for the same firewall in the kernel.

---

### Post by sasho_zl on 2009-08-27
First of all remove Firestarter - it is not supported anymore. Install the gufw firewall configuration tool. 
Second - read the sticky threads in the forum section. Everything you need to know about Linux security for now is there. You can also check the book "Ubuntu pocket guide" which you can download for free from the link in the beginners section.
Good luck.

---

### Post by mouchero08 on 2009-08-27
okay so i went and got this new gefw apt
where can i run in from
i cant see it in my applications

---

### Post by HermanAB on 2009-08-27
If you have done a default Ubuntu install, then relax and enjoy your nice new system - Ubuntu is secure by default.  

You don't really need any firewall software, unless you are doing something advanced and is running FTP, Email or Web servers on your machine.

---

### Post by sadwinch on 2009-08-27
Thanks for your help everyone.

---

### Post by fela on 2009-08-27
Yeah, 98% of the time you won't need to configure a firewall.

Strange thing is, I'm on an annoying firewall at the ISP level that I can't control. It means I can't use my server as a web server, or anything serving to outside my local network :S

---

