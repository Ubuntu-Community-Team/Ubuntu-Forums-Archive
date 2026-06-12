---
title: "Server Access"
date: 2012-07-16
forum: Server Platforms
---

### Post by pstonge on 2012-07-16
Hey guys/girls I have a few questions i need answers too, i have been looking around, and I am new to ubuntu server, and i just cant seem to understand the answers that i am reading. 
 
Question
How to i set up my ubuntu server so that i can keep the same IP address? 
Is it something i configure through my router, or through ubuntu?
 
And is there a way i can access my server when I am not at home?
Like I want it so that my friends/family can access it, or dose it have to be registered domain. I keep hearing that ubuntu servers are free to hosts, is this the same thing? 
And if so, how to i set that up. 

I have came along way, I just 1 day of learning ubuntu server i have set up a LAMP server with SSH, and I am able to access it through my home network, but my ip address changes so i always have to do ifconfig on my server to see what address i have then i can insert it into my web browser and access it. But how to people NOT on my network access it. I just want to set up a simple file server for now. 

Any advice on these topics would be great.
I am learning the shell commands good, and I understand networking as i have taken CCNA, but i never used it in a real world experiance yet. Only textbook. lol so there is a big difference. 
 
Thanks again guys for being so kind to me.
Have a good day !!!!

---

### Post by papibe on 2012-07-16
Hi pstonge.

> **pstonge said:**
> How to i set up my ubuntu server so that i can keep the same IP address? 
Is it something i configure through my router, or through ubuntu?

The easiest solution would be let the server 'as is', and set in the router either and fixed LAN IP or a DHCP reservation (different names on different routers).

If that's not possible. You would have to do it on the server. First step is again on the router. Check the DHCP range, so you setup an address out of that range. Check the section called Static IP Address Assignment in these [guide]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html") to learn how to do it.

> **pstonge said:**
>  
And is there a way i can access my server when I am not at home?
Like I want it so that my friends/family can access it, or dose it have to be registered domain.

In most cases I know, this is very possible. There are several steps you need to take. Here's a checklist:
[LIST]
[*]Subscribe to a dynamic DNS service. There are several that are free (check [here]("http://dnslookup.me/dynamic-dns/")).
[*]Install and setup the dynamic DNS client. ddclient in the repos and works with most of providers.
[*]Forward the necessary port on your router to your Server. Usually the ssh port.
[/LIST]
For a bare bones explanation on this concepts check this very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.


> **pstonge said:**
>  I keep hearing that ubuntu servers are free to hosts, is this the same thing? 
And if so, how to i set that up.
Could you explain this? I don't quite follow.
--

I hope that helps. Let us know how it goes.
Regards.

---

