---
title: "Exposing Apache2 - Safely"
date: 2012-05-10
forum: Security
---

### Post by danix803 on 2012-05-10
I want to expose my Apache2 webserber to the internet... Problem is, that I'm behind a DSL modem and a router... I'm not certain how to do it... 
I know that I could put the entire computer into the modem and router's DMZ... but, I don't want to expose the entire computer... just the ports needed for d/ling data, like port 80... 
 
Of course, I don't want to give too many details... the modem is a seimens speedstream and the router is, the real router that exists, cisco... I'm not going to mention model numbers or anything and certainly not any IP or MAC addresses...
 
I know that there are lots of 'how tos' for hardening my kubuntu apache2 webserver... and I'll do that as soon as I can figure out how to get a limited number of ports visible through the modem and router with exposing the entire computer and all of it's ports to the world... 
 
But, if anyone has a similar setup as far you can tell with the limited info that I've provided, please feel free to offer constructive advice...
 
Thanks in advance for any and all constructive advice on this matter... :KS

---

### Post by lisati on 2012-05-10
It's good that you want to play it safe by sharing the bare minimum of information here. 

For my setup at home, I have a fairly standard installation of apache2. For basic exposure of web pages, I have port 80 forwarded in my router from my public IP address to my server's IP address on my home network.

One of the first things I did before this was to change my router's web-based control panel to use something other than the default user name and password that it shipped with, and turn on its firewall. This will help reduce the chance of someone messing with your router's settings without your knowledge and/or permission. Some people also recommend turning uPNP off.

There are other things you can do to help tighten up security, which no doubt people will be able to help you with.

---

### Post by computeratin on 2012-05-11
I can't help you with the network setup.
 
But, In so far as router security goes, if you're router suppports / has the following:
 
1) If you have WPA (Wifi Protected Acess) then turn it off. NOW! NOW! NOW! This is supposed to make for eaiser wireless network set up. You enter a PIN # from the back of the router in to a GUI to speed up set up. Unfortunately there is a MAJOR flaw in the hash sums used to protect the process. A descent script kiddie with a sniffer can now crack it in nothing flat. This allows them to add theirselves to your router / network and do all kinds of nasty stuff (MTM, etc).
 
2) If your router can be admin'd wirelesly turn it off. Just string an extra piece of CAT5 out the back so you can jack in and admin when you need to.
 
3) Better routers support an exclusion enforcement policy. If you have one then turn it on. The details differ by router. But most have both white and black list capabilty. I run a white list; i.e. ONLY machines with MAC addresses A,B&C can connect to my router. This allows you define what MAC addresses can connect to your router. (I'm GUESSING you'd have to expose some of your server ports by forwarding them through the DMZ to let stuff outside your network connect to your server.)
 
4) If you have a wireless network use WPA2-PSK encryption. The throughput is limited to 54MBps on a lot of routers. But it's the most secure. 
 
5) Brute force crackers are getting stronger, faster and smarter. Read up on the latest password strength / safety protocols. If your router will support 24 characters a good trick is to come up with a strong password and then "pad" it out with a random number of spaces before and after to bring it up to 24 characters.

---

### Post by CharlesA on 2012-05-11
Just a note: MAC filtering is pathetically easy to get past.

---

### Post by computeratin on 2012-05-11
I didn't have time to get to some stuff, trying to get out of work on a Friday afternoon. (WOOOHOOO!)
 

 6) DO NOT DISABLE BROADCASTING YOUR SSID ON A WIRELESS NETWORK. I now this sounds counter intuitive and that lots of places recommend you do it. THEY&#8221;RE WRONG!!!
 

 All you will achieve by turning off SSID broadcasting is to hide from your neighbor who doesn't know how to hack anyway. A script kiddie with a sniffer will still find you.  
 

 And the really fun part is that you are actually less secure because you are forcing your computer to broadcast all the info that the script kiddie needs to impersonate your router as it tries to contact the (NOT) &#8220;invisible&#8221; router.
 

 7) Absolutely make sure you turn off UPnP. It is one of the most easily exploited processes that has ever been written. It is a major hunk of junk.
 

8 )If you don't want Google to map you then add &#8220;_nomap&#8221; to the end of your SSID: cheesy1_nomap
 

 9) Last but not least: VPN!!!!

---

### Post by lisati on 2012-05-11
> **CharlesA said:**
> Just a note: MAC filtering is pathetically easy to get past.

Agreed: on its own, it will only serve to slow down the bad guys by a small amount of time without actually stopping them.

---

### Post by CharlesA on 2012-05-11
Make sure mod_security is enabled for apache as well.

> **lisati said:**
> Agreed: on its own, it will only serve to slow down the bad guys by a small amount of time without actually stopping them.

Yep. It is better to have a longer passphrase - all 256-bits, if possible on WPA2.

---

### Post by computeratin on 2012-05-11
> **CharlesA said:**
> Just a note: MAC filtering is pathetically easy to get past.

Good point.

10) Install the ArpON daemon from the repositories. And configure it. 

Not hard, even I figured it out. Just Google it. There's lots of doc on it. I didn't get in to the reporting and all that jazz. I just did the basics to help prevent ARP cache poisoning.

(I have zero idea how that would effect your network.)

---

### Post by bodhi.zazen on 2012-05-11
> **danix803 said:**
> I want to expose my Apache2 webserber to the internet... Problem is, that I'm behind a DSL modem and a router... I'm not certain how to do it... 
I know that I could put the entire computer into the modem and router's DMZ... but, I don't want to expose the entire computer... just the ports needed for d/ling data, like port 80... 
 
Of course, I don't want to give too many details... the modem is a seimens speedstream and the router is, the real router that exists, cisco... I'm not going to mention model numbers or anything and certainly not any IP or MAC addresses...
 
I know that there are lots of 'how tos' for hardening my kubuntu apache2 webserver... and I'll do that as soon as I can figure out how to get a limited number of ports visible through the modem and router with exposing the entire computer and all of it's ports to the world... 
 
But, if anyone has a similar setup as far you can tell with the limited info that I've provided, please feel free to offer constructive advice...
 
Thanks in advance for any and all constructive advice on this matter... :KS

1. Use Ubuntu server, without the (KDE) desktop. If that is not possible, run your server in a virtual machine.

2. Forward port 80.

3. The problem is not really Apache, the problem is any additional services you use, php, mysql.

4. mod_security is nice, but comes with a learning curve.

---

