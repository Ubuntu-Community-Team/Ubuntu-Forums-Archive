---
title: "How To Make A Website Server?"
date: 2008-11-25
forum: Server Platforms
---

### Post by hollisterdude94 on 2008-11-25
I would like to turn my 5 year old desktop server into a website server. I have already installed Ubuntu Desktop version to the computer. I have no experience making a server since I have always just purchased a Linux server from other companys. I am familiar with basic commands in Ubuntu though.

The computer I have has a 100GB hard drive and 512mb memory.

I want to be able to have mysql and php 5 on the server. I also want to have some kind of control panel for each site that I host on the server (the controls panel needs to be free though) and I am not sure what control panel to choose.

I would need step by step slow instructions from start to finish since I am a newbie :lolflag: If anyone could help that would be great and I would really appreciate it.

---

### Post by rev0lv3r on 2008-11-25
Sounds like you want to set up a LAMP stack

Maybe include Webmin for your control panel? Not sure what you are asking?
phpmyadmin?

Take a look at some of these google results
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=FOB&q=8.10+ubuntu+apache+mysql+php&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=FOB&q=8.10+ubuntu+apache+mysql+php&btnG=Search)

You will be delighted to know that setting up a FULL linux+apache2+php5+mysql5+phpmyadmin+webmin+cacti+ssh+trac+svn is a complete walk-in-the-park

linux - os
apache2 - web server
mysql - db server
php5 - front end scripting
phpmyadmin - remotely work on the db
webmin - remotely work on the server
cacti - monitoring + graphing
ssh - remotely work in the computer
trac - project management, see revisions in a neat format
svn - project mangement, repository software

---

### Post by hollisterdude94 on 2008-11-25
Thanks so much! I installed PHP5, Apache2, and PHPMyAdmin. How do I get the server able to be seen by the public? Like if I have a website that I want everyone to see how do I get that set up? I have a domain that I can set up. I dont know how to get all the IP addresses and nameservers, ect. Also, how do I install Webmin?

---

### Post by hollisterdude94 on 2008-11-25
If I want the public to be able to look at my websites do I set my linux firewall in Webmin to "Allow all trafic" or what do I set it to

---

### Post by laceiba on 2008-11-25
> **hollisterdude94 said:**
> If I want the public to be able to look at my websites do I set my linux firewall in Webmin to "Allow all trafic" or what do I set it to

You may want to be careful about doing this. Many ISPs do not allow you to run web servers on their systems, at least not without paying extra for it. Also, running a webserver and keeping it secure is a tricky business. I don't recommend that you expose your server to the world at large without having a very solid idea about securing Apache and the other services that you are running.

---

### Post by hollisterdude94 on 2008-11-25
I checked and it looks like my ISP allows me to. How do I secure Apache and other services I am running?

---

### Post by Dr Small on 2008-11-25
> **laceiba said:**
> You may want to be careful about doing this. Many ISPs do not allow you to run web servers on their systems, at least not without paying extra for it. Also, running a webserver and keeping it secure is a tricky business. I don't recommend that you expose your server to the world at large without having a very solid idea about securing Apache and the other services that you are running.
Apache is relatively secure by default; That's why it's the most popular and most used websever on the net. What you should be cautious on is the scripts and applications you serve with Apache.

---

### Post by trentscott4 on 2008-11-25
You'll need to set Ubuntu to connect via static ip to your router. I've written a guide to do that [here]("http://trentforge.com/?p=33").  Then, you need to go into your router and set it to forward port 80 to that static IP address.  That way, your router knows anytime someone tries to connect on port 80 (a website), forward their request to your server (the static ip).

Let me know if you have any questions.

---

### Post by hollisterdude94 on 2008-11-26
Ok well I deleted my network manager before I got my IP and gateway and stuff. How do I get network manager reisntalled if I do not have internet anymore since I deleted the manager??

---

### Post by trentscott4 on 2008-12-02
1. Open the network config:

sudo vi /etc/network/interfaces

2. Then, change it to read:

# The primary network interface
auto eth0
iface eth0 inet dhcp

3. Press ‘Esc’ and type ‘:wq’ to save the file and quit the editor.

4. Restart your networking:
sudo /etc/init.d/networking restart

That above will set your networking to connect via DHCP to the router.  Once you have Internet again, run 'sudo ifconfig' and note your gateway/subnet addresses.  Then, modify your /etc/network/interfaces, it will look something like:

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.y.y

Trent

---

