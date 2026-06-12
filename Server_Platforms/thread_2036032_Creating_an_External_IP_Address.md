---
title: "Creating an External IP Address"
date: 2012-08-01
forum: Server Platforms
---

### Post by jason328 on 2012-08-01
I am completely new to ubuntu server. I've set up my server and  installed webmin and openSSH. I can access my server through my own  network. However I want to be able to access it with an external ip  address outside of my network via the internet. This will be for my own  testing purposes. All of that being said, I have had a hard time finding  any tutorials on how to set up an external ip address. When I do find  any tutorials discussing external ip addresses, I feel like a 3rd grader  in a Calculus class. Can anyone point me to a tutorial guide on how to  set one up, for the beginner in understanding servers.

---

### Post by cesar98026 on 2012-08-01
? at a quick glance. You should be able to go on google and search ip. That will give you your ip address and you can ssh to that :KS Unless you have 2 ssh severs, you will have to change the port on one of them! :P

---

### Post by Hashimi on 2012-08-01
Did you look at this tutorial: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

I think that will help you set your IP

---

### Post by papibe on 2012-08-01
Hi jason328.

Take a look at post #2 of this [thread]("http://ubuntuforums.org/showthread.php?t=2028831&highlight=revision3").

Let us know how it goes.
Regards.

---

### Post by jason328 on 2012-08-01
I did that and Putty SSH refused the connection. I also tried it for jokes on a browser and of course the webpage never appeared, showing only connecting... as the title of the tab page.


Will take a look at the tutorials in the morning and return with the results. Thanks for the suggestions.

---

### Post by cesar98026 on 2012-08-01
> **jason328 said:**
> I did that and Putty SSH refused the connection. I also tried it for jokes on a browser and of course the webpage never appeared, showing only connecting... as the title of the tab page.


Will take a look at the tutorials in the morning and return with the results. Thanks for the suggestions.

Do you have port forwarding configured on your router? (if you have one)
:guitar:

---

### Post by The Cog on 2012-08-01
You say you want to create an external address. I take it that this means the addresses you use internally are different. I am guessing that the internal addresses start with "192.168.", "172." or "10.", and that you go through a router that performs address translation in the outgoing connections, making the calls appear to come from the router's public address. 

If so, then the problem is that the router doesn't know which internal address to forward new incoming calls to. You have to configure the router to accept incoming calls and tell it which internal address to translate to. E.g. something like "incoming calls to your port 22 should be forwarded to 102.168.42.42 port 22". This is known as port forwarding, and you can guide different port numbers to different servers. In every case, the callers out there on the internet connect to the public address of your router - you don't do anything to your server to allow this, you don't give the server a new addrsss. You just configure the router to do the forwarding of incoming calls to itself.

---

### Post by jason328 on 2012-08-01
Ok so I'm currently at the port forwarding of my router section. I'm not sure what to put in for open ports in both the public port and the private port. Where do I find this information out? Also when I type in the internal IP Address (I have a list of different networks I can connect too on my router page), my server is not shown. I am able to access the server remotely so I know that the server is connected to the network.

---

### Post by papibe on 2012-08-01
If your router allow forwarding external ports into different local ports, I would advice to do so.

Choose a port number on the dynamic range (49152-65535) and forward it to the local machine hosting openssh-server on port 22.

For instance:
```
44444 -> your_local_machine's port 22
```

Then from outside you would connect using a different port:
```
ssh -p 44444  user@your_dynamic_dns_name
```
Tell us how it goes.
Regards.

---

### Post by jason328 on 2012-08-02
I'm confused by what you mean. I understand I pick a port number. Do I then insert the created number into the public and private port in my router configuration?

---

### Post by papibe on 2012-08-02
Is it possible for you to post a screenshot of your router's forwarding page?

Regards.

---

### Post by spynappels on 2012-08-02
> **papibe said:**
> Is it possible for you to post a screenshot of your router's forwarding page?

Regards.

Or even post the make and model of the router, so we can look at what the configuration pages look like and direct you to the right page on portforward.com

As a general rule, the public port is the one facing the internet, and as Papibe said, it can be pretty much anything. The private port is the port the service listens on in the LAN, so for this instance it would be port 22 for SSH, this should not be changed.

Just for your own security, I would not advise you to open a port to SSH on your server from the Internet unless you have taken some steps to secure it. The simplest and best way to do that is to use key based authentication. An explanation is found here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Shout if you need any more help!

---

### Post by The Cog on 2012-08-02
the port numbers that you forward will depend on the protocols you want to use. Each protocol has a different port number that it normally uses, e.g. ssh=22, http=80. You can see these listed in the file /etc/services on a Linux box. Just forward the ports for those services that you want to make public. 

Don't trust the public. If you forward ssh for instance, then you **will** get hackers using password guessing programs hammering away at your machine all day long, so make sure you use good passwords, or look at using certificates for authentication. You can use a firewall on the server to limit which IP addresses can connect, or install something like fail2ban to block repeated connections.

---

### Post by jason328 on 2012-08-02
Here is the screenshot of the router configuration window. I also want it to be known that the server will be only known to two people. I have no intentions of releasing this out to the public, and neither does the other person that knows. Should I still then have to worry about a security compromise?

Edit: I guess what I'm confused about is when looking at the port forward website, which type of server I should choose. I want to run a website for testing purposes so I imagine I should choose Apache under the type of server I want to modify? Here is the page I'm referring to. 

[http://portforward.com/english/routers/port_forwarding/Dlink/DIR-655/default.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DIR-655/default.htm)

---

### Post by The Cog on 2012-08-02
I think you do need to worry. If the computer is reachable then it will be found and people will try to break in. Not telling anyone the address is no defence. There are robots out there that just try addresses at random.

I do not know exactly what what the fields on that configuration page are for - you'll have to find someone familiar with d-links (not hard), but you are definitely looking at the right page there. EDIT: It seems that darkod knows better. Ignore this paragraph.

---

### Post by darkod on 2012-08-02
You posted a screenshot of the Virtual Servers option page, but according to that link info you better use the Port Forwarding menu for more than one port.

As included in the info about Apache, you only need to forward ports 80 and 443 for both TCP and UDP protocol. That should do it.

As for not telling anyone about the server, that means nothing. Scanners scan at random and will find you. So make sure any firewall on the router is enabled.

Also, if you plan to allow SSH access though the router too on top of the web access, definitely think about protecting it better.

---

### Post by jason328 on 2012-08-02
Since I installed the LAMP server on ubuntu server and that contains apache, I typed in the two ports 80 and 443 in the port forwarding section of my router configuration. I then clicked saved setting and my router decided to go haywire, deleting the password required for it's wireless connection and preventing access to the Internet. This is more frustration than I can handle. I'm going to walk away from this and return when my frustration dies down. When I decide to put the web server on the internet I'll return to this thread for the advice given. Thanks everyone for the help.

---

