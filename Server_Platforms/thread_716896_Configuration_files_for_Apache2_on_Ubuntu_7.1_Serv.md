---
title: "Configuration files for Apache2 on Ubuntu 7.1 Server for web pages"
date: 2008-03-06
forum: Server Platforms
---

### Post by MjrNuT on 2008-03-06
After a few days of searching, I have not been able to resolve my understanding of this concept.

Currently my DocumentRoot = /home/usr/public_html/

To elaborate on my setup:

Host OS is XP Pro (*.1.11)
Virtual PC 2007 for Ubuntu 7.1 Server (*.1.16), using default localhost = 127.0.0.1 

I am successful at seeing the public_html directory on LAN as well as WAN (using my public IP address, which forwards HTTP to *.1.16).

Therefore, I can see my index of web pages and they view correctly.

Current issue is that I have a Home web page that has links to subpages.  I don’t understand how to link those sub pages to the Home page such that it works on LAN and WAN.

Could someone please enlighten what Config files to modify (if any).  I would gladly appreciate an example setup to follow.

Thanks in advance!

---

### Post by slafochmed on 2008-03-06
I am only a noob to ubuntu and apache2, but isn't that an issue about using relative links in the subpages instead of absolute links? Like "../../../../somefolder/index.html" instead of "www.mypage.net/somefolder/index.html".

---

### Post by MjrNuT on 2008-03-06
> **slafochmed said:**
> I am only a noob to ubuntu and apache2, but isn't that an issue about using relative links in the subpages instead of absolute links? Like "../../../../somefolder/index.html" instead of "www.mypage.net/somefolder/index.html".

You're right.  I actually tried that early on to no avail.  and then found out...case sensitivity!!!!  omg!!

A follow up question to you or others:

1.  On my home page i have some buttons.  The buttons have 2 images, when the cursor is on or off of it.  The image for when the cursor is ON the button does not resolve.  As if the image were not found.  I have a .js file that contains the code for this.  Am I possibly missing some installation on the server?

2.  Could someone shed light on how to make automatic index.html occur?  As in, when a url is set like [http://mysite.com/](http://mysite.com/)  is entered it automatically does [http://mysite.com/index.html](http://mysite.com/index.html)

Thanks again for any responses.

---

### Post by MjrNuT on 2008-03-07
I have resolved my previous 2 issues.

I would like to know how to make [http://mysite.com](http://mysite.com) resolve to the localhost.  Such that on the LAN I can enter ^ URL rather than the IP address.  I hope I understand that right and explained what my desire.  

Here is my current /etc/hosts file

```

127.0.0.1 localhost
127.0.0.1 ubuntu-server.hsd1.co.comcast.net. ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
fe00::0 ip6-mcastprefix
fe00::1 ip6-allnodes
fe00::2 ip6-allrouters
fe00::3 ip6-allhosts

```

This file was generated automatically.  

Thanks in advance!

---

