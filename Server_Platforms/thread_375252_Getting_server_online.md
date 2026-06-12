---
title: "Getting server online"
date: 2007-03-03
forum: Server Platforms
---

### Post by voytek on 2007-03-03
Hello, i am having a problem, after 3 days of fighting with ubuntu and joomla i got it all working fine now on my local host 127.1.0.0 but now i would like to post the things actualy online that anybody could see it. I know i need to get a domain name dont have that yet but i thought i could still host it and get to my site with just IP address. I got Comcast service at home so it is possible for me to put all that content online and how ? Thanks in advance

---

### Post by invalid on 2007-03-03
You need to set this up through either your modem or router (or both) to allow access on certain ports to certain local IPs. Try looking in these settings for some options.

---

### Post by Mr. C. on 2007-03-03
Open your firewall port 80 and direct it to your server machine's IP address.

Then, from an external IP address, try [http://your-ISP-IP](http://your-ISP-IP) and if configured correctly, you should see your pages.

There is a possibility that to work properly a hostname might be required (as some internal pages redirect using the host's name, instead of IP address; at this point things will start to fail).

You can use your ISPs hostname instead of the IP address - that may help.

MrC

---

### Post by devious1 on 2007-03-03
you're doing way better than me. I'm stuck on the point you just figured out. for ip try no-ip.com or dyndns.com also no a few others try googling for free ip address.

are you connected through a router? I'm trying to figure out how to put in the correct info for my server tried step by step but i'm not understanding something

---

