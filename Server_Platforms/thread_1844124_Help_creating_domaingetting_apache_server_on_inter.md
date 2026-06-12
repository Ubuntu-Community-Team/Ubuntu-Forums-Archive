---
title: "Help creating domain/getting apache server on internet"
date: 2011-09-14
forum: Server Platforms
---

### Post by ScottG89 on 2011-09-14
I currently have an apache web server setup, but I was wondering if anyone can tell me how to set it up so it is accessible on the internet. Or can tell me a good tutorial for this. I'm not exactly sure what BIND is but I'm assuming I need that?

Thanks in advance,
Scott

---

### Post by agillator on 2011-09-14
Start with telling us how you installed Apache? Was it by apt-get or by downloading and installing the .tar.gz file? This makes a big difference on where various files are and how the configuration file(s) is/are used. How are you connected to the internet, through a firewall, a router? Do you have control of the connection, specifically can you setup port forwarding if it is necessary? Do you have a static or dynamic ip?

---

### Post by ScottG89 on 2011-09-14
Yes I installed through apt-get
I am connected directly to cable modem.
Dynamic IP
Not sure about access to port forwarding, do I need that if I am directly connected. I know how to do it, but only when its through a router.

---

### Post by agillator on 2011-09-14
The apache reference manual is located at [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/). Note that the directories named in the manual will be different. [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html) is a good source of configuration instructions as well as a list of what is where. Beware security problems. Basic configuration leaves your site open to the public - anyone who wants to go there. There are ways to hack your computer in that case. You might consider basic or digest authentication - explained on the configuration reference. 

Since you have a dynamic ip. You will either need to get a static ip from your provider which costs money or sign up for an account with a dynamic dns server such as dyndns. There are free ones available, dyndns.com being one of them.. They will give you instructions on how to keep them updated. 

Make sure your firewall (you are using one, aren't you) does not block port 80, or whatever port you decide to use.

Setup and configuration is not all that difficult once you have been through it one time. However, there is really more to it than can be listed here, nor should we reinvent the wheel when there are so many good references and tutorials available. So check out the references I have given you. If you have specific questions, and your first time to set it up I'm sure you will have, ask here but do as much as you can yourself.

---

### Post by ScottG89 on 2011-09-14
Ok, thank you very much. I really am trying to get this to work, but I am having no success at all. After reading that site, I wound up just changing my <VirtualHost *:80> to my external ip:81. And it still won't come up available on the internet. Maybe I did this completely wrong. I'm sorry, I'm just getting frustrated because I have been trying to do this for months and I can't get it at all. Do I even need bind. That site you told me about doesn't say anthing about it.

---

### Post by agillator on 2011-09-14
No, you don't need bind. Unless you have changed ports somewhere, your virtual host should be port 80, not 81. Also, let's try the obvious - are you SURE apache is running? Try 'sudo /etc/init.d/apache2 restart' and see what messages you get. If it starts/restarts then I assume you have a firewall on your computer. Is port 80 open? Most firewalls close all ports for incoming packets until there is an outgoing packet to an ip, and then it will open the necessary port to that ip. So, check your firewall and make sure port 80 is open to the world. I assume you are using something based on iptables, so cd to your home directory and enter in a terminal: sudo iptables -L -n -v --line-numbers > rules. Then examine the rules file with less and see if there are any references to a sport (source port) 80 or anything like that, probably in the INPUT chain. If there are, there should be a -j ACCEPT in that rule. That opens the port. Once we determine that port 80 is open, we will go to the next step.

---

### Post by elico on 2011-09-15
the basic installation of apache will make the server up and runing with the "It works" page.
what you need is not bind server but to buy or use a dyndns\noip or some other dynamic ip dns service.
you can start with the free one of one of them and see onn.
if the machine is connected directly to the INTERNET using the cable modem and getting dynamic ip from the ISP you should be ok as it is just learn a bit about networking to understand what you are doing.(recommendation)

---

### Post by ScottG89 on 2011-09-15
> **agillator said:**
> No, you don't need bind. Unless you have changed ports somewhere, your virtual host should be port 80, not 81. Also, let's try the obvious - are you SURE apache is running? Try 'sudo /etc/init.d/apache2 restart' and see what messages you get. If it starts/restarts then I assume you have a firewall on your computer. Is port 80 open? Most firewalls close all ports for incoming packets until there is an outgoing packet to an ip, and then it will open the necessary port to that ip. So, check your firewall and make sure port 80 is open to the world. I assume you are using something based on iptables, so cd to your home directory and enter in a terminal: sudo iptables -L -n -v --line-numbers > rules. Then examine the rules file with less and see if there are any references to a sport (source port) 80 or anything like that, probably in the INPUT chain. If there are, there should be a -j ACCEPT in that rule. That opens the port. Once we determine that port 80 is open, we will go to the next step.

Ok, thank you very much. I just wanted to let you know that I am going to be doing a complete reinstall of Ubuntu and apache so it is back to default settings. I will be doing that later today. Thank you again for being patient and helping me

---

### Post by ScottG89 on 2011-09-15
Ok, so I just reinstalled 11.04. And then went to terminal and installed apache2, php5, and mysql.
Apache is definitely working so we can cross that off.

_**IP Tables:**_
I went to this site [http://www.farinspace.com/secure-firewall-linux-server/](http://www.farinspace.com/secure-firewall-linux-server/) to find out how to setup the iptables, but am having trouble using this command:[COLOR=#c20cb9]****[/COLOR][FONT=Verdana]
sudo iptables-restore < /etc/iptables.test.rules
[/FONT] so I tried using your instructions:
iptables -L -n -v --line-numbers > rules
and then,
iptables -L -n -v --line-numbers < rules
and I got these results:
Chain INPUT (policy ACCEPT 9844 packets, 10M bytes)
num   pkts bytes target     prot opt in     out     source               destination         
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy ACCEPT 9308 packets, 1658K bytes)
num   pkts bytes target     prot opt in     out     source               destination   

________________________________________________________________________
I also just used the command
ufw allow www

I tested to see if it works using my external ip on my smartphone (not connected to the network) and it worked!
I'm assuming it was because I used the ufw allow www as opposed to the iptables
because I couldn't get that command to work or maybe because I didn't have a port 80
in any of the rules (I don't really know how iptables work :/) Thank you very much for your help, you helped
solve a project that I have been working on for months. I was wondering if you have any tips or recommendations
(if I should create any rules in the iptables or anything like that) also, where can I change
my domain name so I don't have to type my external ip.

Thank you an exponential amount!!

---

### Post by agillator on 2011-09-15
Glad it is working. 

Domain name: go to one of the free dynamic dns sites - I use dyndns.com - and sign up for an account. Pay close attention to their instructions. What happens is that you will select/create a domain name from a list they control. Then you will run a program that will keep track of your ip address. Anytime the address changes the program notifies the site so it is kept current. For example, I use IPCop as a firewall and it will handle dynamic dns automatically. Some DSL and cable modems will handle this also. Check the configuration of your modem/router and see. If it won't, the site you sign up with should be able to recommend daemons you can use that will.

IPTables: For the moment ufw will handle what you need so you don't really need to learn a whole lot about iptables. However, it is a subject well worth reading up on since it can give you full control over your firewall. Do a search for an iptables tutorial. Of course man iptables gives you a fairly comprehensive explanation, but it is best if you already understand a little before you start relying in that.

---

### Post by ScottG89 on 2011-09-15
Ok cool thank you. So there is no way to get a free [www.yourdomain.com](www.yourdomain.com) without paying I assume.

Yes, I'll definitely look into reading about the iptables

---

### Post by agillator on 2011-09-15
dyndns.com and some other sites give you a free domain name - or let you choose from an extensive list they control. I have used dyndns for several years now without paying them a cent. Eventually I will want their pay services, I suppose, but for now their free services are all I need.

---

