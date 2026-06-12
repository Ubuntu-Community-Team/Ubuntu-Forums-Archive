---
title: "/etc/host help"
date: 2006-08-17
forum: Server Platforms
---

### Post by jrcproduct on 2006-08-17
I need to learn more about the host file and what is for.

I know that this is where you name your computer. I dont know how it is used.

Here is a exspamle of a problem I have now. I have a domain from godady called jrcproduct.com I have the dns point to my IP. I would also like to host a virtual hosting server with apache2. I have not work on the host file, its all defualt and I get a > apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 and from what I can see its do to the host file.

I'v seen tutorials where they say to add 
> 192.168.0.100   server1.example.com     server1

now would that be the same way for me?
> 192.168.0.100   server1.jrcproduct.com     server1

and what about any other doamin name I use to point to my virtual hosting server, would I add them that way too?

the real problem is I dont now what it's used for and how its used, and real info about he proper why to set that up would be a great help.

---

### Post by chonger on 2006-08-17
Google for the "Apache ServerName Directive". That's a good place to start.

---

### Post by jrcproduct on 2006-08-17
thanks for the input about the way it fits in to the use for virtual hosting but you kinda side steped the q: about the hosts file. I still now know as much about that file as I did befor, but now becuase of  your help I know a little more about how it will work with apache. still could use a bit of help.

---

### Post by chonger on 2006-08-18
My bad. I misunderstood what you're driving at; I thought you mainly wanted to make sure Apache shows the servername.

The /etc/hosts file is used to map names to IP addresses. For example, typically  computers talk (over a network) to a DNS server to find out what IP [www.google.com](www.google.com) is mapped to. 

However, if you want to manually specify the mapping of name to ip using a text file, you can do it by specifying the mapping in the /etc/hosts file. However, since only your computer sees the /etc/hosts file, only your computer knows that mapping of name to IP address. 

It's almost as if you did name your computer, but only *you* know about that name.

To make sure other computers on a network (or on the Internet) knows the name of your computer (and the IP it is mapped to), it gets more complicated. That's a whole different story.

Note that Windows also has a 'hosts' file. It is typically localted in %WINDIR%/system32/drivers/etc/hosts. Not sure why it is under a directory called "drivers".

---

### Post by ape on 2006-08-18
A simple 'man hosts' will give you more information on the /etc/hosts file.

---

### Post by Ozz on 2006-08-18
If you still want to know about /etc/hosts and apache's virtual hosts, I do use'em and it's exactly as you mention:
192.168.1.100 whatever.com
192.168.1.100 somethingelse.com

And apache will serve the request with the proper site.

Ozz.

---

### Post by jrcproduct on 2006-08-22
> **Ozz said:**
> If you still want to know about /etc/hosts and apache's virtual hosts, I do use'em and it's exactly as you mention:
192.168.1.100 whatever.com
192.168.1.100 somethingelse.com

And apache will serve the request with the proper site.

Ozz.
first thanks to every one for all the info.

this is more what I was wondering since I wanting to have a virtual hosting server. it's been a problem for me because I'v seen it in a bunch of howto guides that show you chaging this to just one domain usaly server1.exsample.com. I wanted to know if I should add one for every domain I have in my virtual host? or if I should and one at all and just leave it at local host?

Just looking for best practice.

---

