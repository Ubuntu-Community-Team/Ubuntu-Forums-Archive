---
title: "Can't ping local FQDN's"
date: 2009-03-26
forum: Server Platforms
---

### Post by worldtraveller2007 on 2009-03-26
Hi all,

I am hoping you can help me out here.

I have a brand new install of Ubuntu Server 8.10 on an old IBM E Server. It has a static address and I have configured the resolv.conf file as described on these forums.  This currently sits in a Windows 2003 AD environment and I want to join the server to my domain.

I am having real problems with my networking though.  DNS is taken care of by my 2K3 AD server and all windows machines can ping the hostname of a machine or the FQDN of a machine but the new Ubuntu box cannot.

The Ubuntu machine can ping a hostname fine but as soon as I try to ping "winserver.domain.local" it comes back with 'unknown host'.  When I ping "winserver" it returns the FQDN and is sucessfull.  When I do "nslookup winserver" it brings back the FQDN and I am now really stumped!

This is the same whatever machine I ping on my network.  Now I know from reading other articles on here that the ability to be able to ping a local FQDN is vital when you are trying to join the Ubuntu box into the windows domain.

My resolv.conf looks like this:
> search domain.local
nameserver 192.168.0.1 

Any he you guys can give would be greatly appreciated!

Many thanks in advance.

---

### Post by worldtraveller2007 on 2009-03-26
Please ignore now.

I decided to rebuild the server and now all works fine.  Think there must have been an issue when I installed gnome on the server, even though I was only accessing through SSH.

Oh well, sorted now!

---

### Post by Zeon100 on 2009-11-08
Hi,
I'm having the exact same problem with a new 9.10 installation. Like you I have installed Gnome and can't reach my local domain controller (which runs DNS and this has been set in the ubuntu configuration).

The fact that I can ping my server "apollo.pbs.local" without "pbs.local" (ie I just type in "ping apollo" and it adds the pbs.local) would suggest to me it is already adding that suffix? I remember I had set that at one of the setup screens when I was initially installing the system.

I will investigate further but it seems really strange behavior.

---

### Post by Zeon100 on 2009-11-08
I have come across the fix, I've just tested and it works!

[http://longerthan5.blogspot.com/2008/05/help-i-cant-ping-fqdns-in-ubuntu.html](http://longerthan5.blogspot.com/2008/05/help-i-cant-ping-fqdns-in-ubuntu.html)

> 
Okay, for this tip I need to specify that I have only ever encountered the problem on Ubuntu 7.10 (Gutsy Gibbon). However, from what I read while researching the problem it also applies to Ubuntu 8.04 (Hardy Heron). Basically, what happened was I could ping my mail server by its name (rex), but not its Fully Qualified Domain Name (rex.cms.local).

Turns out there is some strange interaction between DNS and Avahi (no not the woolly lemur the Linux implementation of Zeroconf) that only rears its ugly head when your local domain ends in a .local. Now, I hear that Avahi is great if you have a network of computers, no DNS server and no desire to set one up, but I don't have that problem. I have a DNS server dang it!! Two of them to be precise. All I want is nice easy DNS resolution!!

Well here is your solution:

[LIST]
[*]Open **/etc/nsswitch.conf** in your favorite text editor (I like nano, vim works, if you are an emacs user.......well I guess you can keep reading).
[*]find the following line:
**hosts: file mdns4_minimal [NOTFOUND=return] dns mdns4**
[*]Change it to:
**hosts: files dns**
[*]Thats it!!
[/LIST]
Once again, it will break Avahi, but most likely you wont need it. 


---

### Post by StarQuake on 2009-11-18
Does anyone have a solution that doesn't break avahi?

Found a post that explains the problem:
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

The problem is the domain.local part

Anyone have a suggestion what to use as a good alternative to domain.local?

---

