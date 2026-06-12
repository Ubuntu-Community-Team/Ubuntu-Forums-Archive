---
title: "Server 11.10"
date: 2011-12-18
forum: Server Platforms
---

### Post by Giles102 on 2011-12-18
Im trying to get up a server for my finial year project.
At the moment i have configured a virtual server using VirtualBOX : LAMP server
I have brought the domain name [www.torrentchain.com](www.torrentchain.com) with godaddy.

How do i configure it so when people type in the doamin [www.torrentchain.com](www.torrentchain.com) they will be redirected to my server. 
I can display the server pages on my network (internal) but when i try extrenal such as at a friends house. They do not dispaly.
My sever IP is 192.168.0.15 and my public address is 

Need you help ASAP.
Can you try and explain it simple aswell. 

Thanks Giles102

---

### Post by volkswagner on 2011-12-18
You need to use GoDaddy console and set you domain A record to your public ip.
GoDaddy > DomainManager > DNS Manager > Zone file Edit
Change the ip address for Host @ to your public ip.

Then you need to open port 80 on your router and forward it to your server's internal ip address.

Get this setup and working first, before you worry about if you have a Dynamic IP address from your isp.

---

### Post by Giles102 on 2011-12-18
Hi this is want I've done so far.

Go onto godaddy dns manger 
Changed the a host to @ to ip address  
Gone to sky router manger interface 
Opened ports so that inbound service are sent o LAN server 192.168.0.15

But now when I type in my URL domain it takes me to my sky router interface and not the web server . Any ideas .? 

Cheers alan

---

### Post by Giles102 on 2011-12-18
> **Giles102 said:**
> Hi this is want I've done so far.

Go onto godaddy dns manger 
Changed the a host to @ to ip address  
Gone to sky router manger interface 
Opened ports so that inbound service are sent o LAN server 192.168.0.15

But now when I type in my URL domain it takes me to my sky router interface and not the web server . Any ideas .? 

Cheers alan

I've also checked that the ports am opend which they are

---

### Post by Giles102 on 2011-12-18
Update ok

[Http://torrentchain.com](Http://torrentchain.com)  is working 
But [www.torrentchain](www.torrentchain) is not 

Why? 

Cheers Alan

---

### Post by volkswagner on 2011-12-18
what does your virtual host file look like?  You may need to set an alias directive.

```
server alias www.domain.com
```

---

### Post by Giles102 on 2011-12-18
> **volkswagner said:**
> what does your virtual host file look like?  You may need to set an alias directive.

```
server alias www.domain.com
```

I know this may be a bit of a pain but could u tell me how to set a server up. That why I know I've done it right. There two many different ways online to do it. All I want is a server that allows internal and Internet connection. Along with MySQL . Php and apache basically a lamp server.  Using the domain name of [www.torrentchain.com](www.torrentchain.com) and ip address of 192.168.0.15 on a virtual server. 

Cheers alan

---

### Post by volkswagner on 2011-12-18
The [sticky at the top of the Server forum ]("http://ubuntuforums.org/showthread.php?t=1046738")should be your first stop for information.


There are good instructions on [Apache]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") Virtual hosts in there.  One thing to note is the how to shows a wild card for the Server Alias so you will need to have minimal understanding to apply your specific needs.  This will be true with most how-to's since no two admin requirements are the same.

You are on the road to success.  It is best to jump in, and ask specific questions once you run into a snag.

---

### Post by Giles102 on 2011-12-19
cheers mate i think it working now.

---

### Post by Dry Lips on 2011-12-19
Btw... Is the IP address you posted your personal IP address? In other words,
is your server connected through your home connection? If it is, I recommend
you to remove the IP address from your posts above...

Good luck!

---

### Post by Giles102 on 2011-12-19
> **Giles102 said:**
> cheers mate i think it working now.

Hi Guys,

I've created a torrent tracker server for my final year porject at university.

The website is in the beta stage

Could you try it out for me, add some of ur own torents and download some ect.. Comment on any ideas you have or any trouble you may be having.

[www.torrentchain.com](www.torrentchain.com)

Cheers Alan

---

### Post by Giles102 on 2011-12-19
> **Dry Lips said:**
> Btw... Is the IP address you posted your personal IP address? In other words,
is your server connected through your home connection? If it is, I recommend
you to remove the IP address from your posts above...

Good luck!

Good idea lol

---

