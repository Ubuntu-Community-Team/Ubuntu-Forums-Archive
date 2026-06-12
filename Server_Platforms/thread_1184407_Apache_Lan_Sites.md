---
title: "Apache Lan Sites"
date: 2009-06-11
forum: Server Platforms
---

### Post by CrazyMonkeyFox on 2009-06-11
I have apache setup and running for me (localhost is working and all that jazz). I'm in an office, and I need to be able to host a site for the office to see. So I need to put the site up on a lan, I, being new to both Ubuntu and Apache, have no idea how to go about this. Thanks in advanced for any help.



CrazyMonkeyFox

---

### Post by dannybuntu on 2009-06-11
Simplest way is to go to /var/www/

Then execute

$ sudo gedit index.html

Then type this:

```
<html>Hello Office Mates</html>
```

---

### Post by ad_267 on 2009-06-11
You need to make sure your local IP address is static, then depending on how your network is set up the other computers should be able to just enter you IP address in their web browser. You can edit the /etc/hosts file or the equivalent on Windows (C:\Windows\system32\drivers\etc\hosts) so that people can enter your computer name instead of the IP address.

You can find out your IP address using the ifconfig command, for example mine says: "inet addr:10.1.1.3"

I can edit the hosts file and add:
```
10.1.1.3 adamscomputer
```

so that people can access my webserver using "http://adamscomputer/"

---

### Post by CrazyMonkeyFox on 2009-06-11
I changed it so the localhost reads out of my home/user/public_html directory. And I cannot find the etc/hosts folder at all. And lastly all the address returned when I ran ifconfig return 192.168.x.x, where x are numbers, usually that means only i can see it.

---

### Post by bigbearomaha on 2009-06-11
'hosts' is a file, not a directory in the 'etc' directory.

Does your computer use dhcp to connect? if so, you should change it to static and set an address similar to the one you have now ( meaning the first three sections of the address should be the same ie...192.168.1.new )

the index page should then be in your home web directory, if not, you can create one there.

---

### Post by v3xtra on 2009-06-12
> **ad_267 said:**
> 
I can edit the hosts file and add:
```
10.1.1.3 adamscomputer
```

so that people can access my webserver using "http://adamscomputer/"

Doesn't that only apply to YOUR computer or by changing that on your computer that allows others to be able to use that as well?  For some reason I thought that you couldn't use that if you weren't on the actual computer or didn't have that changed in your hosts file because how would your computer know that adam's computer is named adamscomputer instead of 10.1.1.3?

Also, CrazyMonkeyFox, as long as your office is on the same subnet ( and I'm not sure if it would work correctly if they were on a different subnet unless you had routing between them ), they should be able to type in your IP address, the one you found in ifconfig, and access your web page.  There is nothing more you have to really do.  No one on the outside should be able to access it because your router shouldn't be forwarding the HTTP/80 port to your computer, so no access can be made outside.

Pretty much, think of it like this.  A user such as me tries to make a request to your computer.  95% of the time, the line coming from the router to the internet has one IP address, and inside the router, it splits that IP address into multiple INTRANET ip addresses.  By going to a site such as what-is-my-ip.com, you can see your outside IP address.  If I went to [http://thatipaddress/](http://thatipaddress/), it is trying to access port 80 on the router.  By forwarding that port from the router to your INTRANET ip address, it allows you to "direct" traffic from the outside to your computer's port HTTP/80.  Since you have not likely forwarded that port, the router cannot find any open port HTTP/80, and the request is denied.

What this means is that your web site should be safe from the outside, and only accessible from the inside.  By adding a DNS server on the inside ( on your Ubuntu box ), I believe that you can have name resolution, so that you COULD have a simple domain, such as intra.mycompany.com, and everyone who has that as their DNS server should be able to enter that address and see YOUR website!  :)

An old company of mine did this for information about clients and techniques used in the field, which was only available to them in the shop ( intranet ) but never accessible from the outside.  It worked perfectly.  :)

Hope that kind of explains things a bit better, I think I ranted on a bit more than you probably needed.  My bad!

---

### Post by ad_267 on 2009-06-12
> **v3xtra said:**
> Doesn't that only apply to YOUR computer or by changing that on your computer that allows others to be able to use that as well?  For some reason I thought that you couldn't use that if you weren't on the actual computer or didn't have that changed in your hosts file because how would your computer know that adam's computer is named adamscomputer instead of 10.1.1.3?


Yes, I meant edit the /etc/hosts file of the other computers, not my own computer.

---

