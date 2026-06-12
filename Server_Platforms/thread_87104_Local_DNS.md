---
title: "Local DNS"
date: 2005-11-07
forum: Server Platforms
---

### Post by i-x on 2005-11-07
Hello,

I hope somebody have time to help. I'm writing here since I don't have succeded with finding answers thru google or else where on the WWW.

I have a smal LAN, ie one client and a server computer both running Ubuntu Breezy.

On the server I have BIND9 installed.


What I wish to be able to do is to configure a local DNS server so I can surf [http://intranet/](http://intranet/) etc from the workstation computer.

But I can't figure out how to do that. Please, give me a hint. I can post my config files if you need them.

Thanks in advance!

---

### Post by Glut on 2005-11-07
If you only have one client computer, then bind is a little overkill. Modifying the hosts file of the client will be the easiest way to go.
Bind is a fairly complex package and it pays to look into it in depth.  A simple way to go is to install webmin and use that to setup your DNS server. A better way to go would be to study the documentation for bind (look at the man pages, I'm fairly sure they give you a website to go to)

---

### Post by senectus on 2005-11-17
I have the same situation except I have 4 PC's and a couple of laptops popping in and out.. so HOSTS isn't any good for me...
Can anyone recommend a good guide?

---

### Post by nagilum on 2005-11-18
With just 2 computers I agree with Glut that Bind would be overkill. If you want to do this nonetheless here's the DNS HOWTO on Bind 9: [http://langfeldt.net/DNS-HOWTO/BIND-9/](http://langfeldt.net/DNS-HOWTO/BIND-9/)

For small networks there are a number of easier alternatives. One is 'dnsmasq' which acts as a normal DNS server but reads the hostnames from the /etc/hosts file on the server, you just have to maintain this single file. It can in addition also be used as a DNS forwarder for general DNS resolution.

If you want an authorative nameserver (one, which is just responsible for your local domain and nothing else) on your network there are a few alternatives to Bind, PowerDNS for example (package 'pdns'). Don't know if they are easier to setup, though.

---

### Post by spade_shark on 2005-11-18
> I hope somebody have time to help. I'm writing here since I don't have succeded with finding answers thru google or else where on the WWW.
  I do not believe you my dear friend.  Cut and paste this into google (1 of about 12,700,000) :  "edit local host file" without the quotes of course.
However my $.02.  With only a handfull of clients, edit the hosts file of the client machine.  I agree with the others.  If bind is needed, you may consider installing webmin and the plugins for BIND on the server.  This may make life easier.  You would then be able to use a web browser to administor your BIND services, and not have to worry about the format and setup of the proper text files.  Plus next best thing to no gui is a web based display.

---

### Post by Digital Ninja on 2007-12-26
Sorry for bumping this old thread but ..

This local DNS stuff doesnt work for urls without "www.". If i write the url in the address bar in my Firefox with no "www." then it just goes to that site. If i write it with the "www." then it redirects to the site i specified in the hosts file. I tried putting both versions of the url in the hosts file or just on of them, but none of those solutions seem to work.. Any idea why that is?

---

### Post by Digital Ninja on 2007-12-31
Oh well, it kinda works now, so never mind i guess ..

---

