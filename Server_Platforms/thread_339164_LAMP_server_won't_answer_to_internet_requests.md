---
title: "LAMP server won't answer to internet requests"
date: 2007-01-15
forum: Server Platforms
---

### Post by joaomario@edgy on 2007-01-15
Hi Folks,

I've got my server up and running, I just need a little help on the IP configuration.

The Linksys router's IP are 201.52.109.9 192.168.1.1, the server is connected at it, and I've redirected the port 80 in the router to the server's IP, which is 192.168.1.100.


So, at /etc/network/interfaces I tryed this:

....
iface eth0 inet static
          address 192.168.1.100
          netmask 255.255.255.0
          gateway 192.168.1.1

iface eth0:0 inet static
          address 201.52.102.9
          netmask 255.255.240.0
          broadcast 201.52.102.191 (POSSIBLE FONT OF ERRORS, AS I DONT KNOW IF THIS VALUE IS CORRECT)


/etc/apache2/sites-available/default

NameVirtualHost 201.52.102.9
NameVirtualHost 192.168.1.100
<VirtualHost 201.52.102.9 192.168.1.100>
....
</VirtualHost>


I just need the server to be accessed by it's IP, without the need of an web-domain. And, it works on the intranet, I can access it from the other computers connected to the same router/gateway (192.168.1.1).


Thank you very much,


Joao.

---

### Post by joaomario@edgy on 2007-01-15
Interesting observations:

If I ping the address 201.52.102.9 from a computer not in the intranet it work's only whith the server turned ON. I shutted it down and the ping get's 100% lost. So, in my newby opinion, maybe I got the wrong guess typing the broadcast number. Would anybody be able to help me on this matter?


Thanks again.


Joao.

---

### Post by TSMJ on 2007-01-16
> **joaomario@edgy said:**
> 
iface eth0:0 inet static
          address 201.52.102.9
          netmask 255.255.240.0
          broadcast 201.52.102.191 (POSSIBLE FONT OF ERRORS, AS I DONT KNOW IF THIS VALUE IS CORRECT)



You'll probably want to remove that. Your Internet router will use NAT and translate between your public IP and the server's private one (hence the port forward required).

---

### Post by petok on 2007-01-16
Are you sure the right port is *really* open? Please test it at this website [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2").
Can someone explain what the broadcast option is doing?

---

### Post by Brazen on 2007-01-16
> **petok said:**
> 
Can someone explain what the broadcast option is doing?

The broadcast address is an address that you can send to and EVERY machine on the subnet will accept it.  in joaomario's case, it should have been 201.52.111.255.  Unless you know what this is, it should be left out and let the system set it automatically.  It shouldn't have any impact on joaomario's problem, though.

---

### Post by Brazen on 2007-01-16
> **TSMJ said:**
> You'll probably want to remove that. Your Internet router will use NAT and translate between your public IP and the server's private one (hence the port forward required).

I'll just second that you _absolutely_ must remove the eth0:0 section from your config.  As TSM says, your router handles translating this address.

---

### Post by Brazen on 2007-01-16
> **joaomario@edgy said:**
> Interesting observations:

If I ping the address 201.52.102.9 from a computer not in the intranet it work's only whith the server turned ON. I shutted it down and the ping get's 100% lost. So, in my newby opinion, maybe I got the wrong guess typing the broadcast number. Would anybody be able to help me on this matter?


Thanks again.


Joao.

that's pretty odd that pings from the internet would be reaching your server.  The linksys box should be blocking any ping requests, whether your server is turned on or not.

---

### Post by joaomario@edgy on 2007-01-16
First I'd like to thanks for the attention folks.


I took out the whole eth0:0 section. In fact I did this through SSH, which works fine, because I am in a friend's house. So, this makes me believe that Apache isn't configured right. 

Att.


Joao.

---

### Post by joaomario@edgy on 2007-01-16
I tryed nmap 201.52.102.9 and it didn show any ports.

When I did this command at the intranet, it had shown ports 80 and 22 for the SSH.

Is it possible that the port 80 is only opened for the intranet???

---

### Post by Brazen on 2007-01-16
> **joaomario@edgy said:**
> I tryed nmap 201.52.102.9 and it didn show any ports.

When I did this command at the intranet, it had shown ports 80 and 22 for the SSH.

Is it possible that the port 80 is only opened for the intranet???

It's _very_ likely that your ISP blocks incoming port 80.  My home ISP does (Cox).  They do this so you can't run your own server.  They want you to pay for a business connection in order to run your own webserver (it's one of those fine print things).

---

### Post by joaomario@edgy on 2007-01-16
Ok,


Thank's everybody. I called my ISP and they have a special (more expencieve of course) plan for an IP with access to the port 80.

---

### Post by Brazen on 2007-01-16
You could run your website on a different port, for instance port 81.  Then when you want to access your website from the internet, you would use [http://ipaddress:81](http://ipaddress:81).  I did this for a while to my home, and just created a dyndns account with a redirect to my home address at port 81.

The problem with this though, is for companies that do not allow port 81 outgoing from their network, such as the network I administer.  I only allow certain ports that people need to use for valid reasons, such as port 80 for web and port 25 for email, but port 81 would not be allowed from a computer at this company.

---

### Post by joaomario@edgy on 2007-01-19
Success on port 81!!!!


[www.joaomario.adm.br](www.joaomario.adm.br)



Thanks,


Joao.

---

