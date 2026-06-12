---
title: "Server worked but now times out"
date: 2009-11-28
forum: Server Platforms
---

### Post by ZJ88 on 2009-11-28
I recently put a website up with a Ubuntu server I have, it has been working great but just in the last day or two, I can no longer connect to the website. [www.hirekriskringle.com](www.hirekriskringle.com) I'm not sure why this is. I cannot even connect on my servers web browser. Can anybody help?

---

### Post by cariboo on 2009-11-28
a bump for the move.

---

### Post by Denbert on 2009-11-29
> **ZJ88 said:**
> I recently put a website up with a Ubuntu server I have, it has been working great but just in the last day or two, I can no longer connect to the website. [www.hirekriskringle.com](www.hirekriskringle.com) I'm not sure why this is. I cannot even connect on my servers web browser. Can anybody help?

Which web server are you using?

Is it running?

---

### Post by BkkBonanza on 2009-11-29
That domain reverse ips to c-67-166-65-117.hsd1.ut.comcast.net
This leads me to believe you set up your server on a dynamic ip link (like your home adsl or similar).
If so, then be aware that your ISP will change your ip address from time to time and every time the ip changes your name no longer resolves.
So to handle this you need to setup a method to update your DNS for your domain name so that the ip is always current.
There are a few simple ways to do this. If your router supports it then setting up dynamic dns updating could be as simple as enabling it on your router with a suitable dynamic dns provider like dyndns or zoneedit.
Another easy way is to install and configure ddclient on your web server so that your DNS gets updated.
Search this forum for dynamic dns as this issue comes up over and over (ad nauseum).

---

### Post by ZJ88 on 2009-11-29
Ok thanks I'll check that out. but I am running Ubuntu 9.04 I believe and it is on

---

### Post by ZJ88 on 2009-11-29
Ok I figured it out. What had happened is that I moved my server from downstairs to upstairs and the intaddress changed. so that means my port forwarding changed and didn't work. The weird thing is I moved it more than a two or so weeks ago and it just barely happened. Thanks for the help!

---

### Post by BkkBonanza on 2009-11-29
Are you sure you're on a "static ip"? The port forwarding would cause your problem but also if your ip changes you'll have the same problem. Check your current ip by going to [www.whatsmyip.org](www.whatsmyip.org) (or similar). If this address isn't the one you set in your DNS for your domain then that's a problem.

It's likely the site was down as soon as you moved the server but your browser cached the page and so you didn't notice. Also possible you were using DHCP on your LAN and the ip upstairs was the same until just recently when for some reason (a new computer on the LAN?) the upstairs ip got assigned differently.

BTW your site is now loading here.

---

### Post by ZJ88 on 2009-12-01
Yeah what I'm thinking is that I need to check my internal ip. I know that my external ip is static but my internal might be dynamic.

---

### Post by BkkBonanza on 2009-12-01
Yup. Your typical router uses DHCP to assign IPs and it could/would/will vary. Usually there is a way to config an IP to a MAC address, then it will always give that machine the right IP even if things on the LAN change. In DD-WRT that I use on my Linksys it's in the DHCP config as a "static lease".

---

