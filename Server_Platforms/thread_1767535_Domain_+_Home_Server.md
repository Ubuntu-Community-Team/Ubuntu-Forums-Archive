---
title: "Domain + Home Server"
date: 2011-05-25
forum: Server Platforms
---

### Post by Skullclamp on 2011-05-25
Recently I installed ubuntu server and to configure all used this general tutorial:[click here]("http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3") . And also acquire a domain.

My question is how do i set up the domain "to hit" on my server.

I have the server configured in a manner similar to general tutorial do i have the server installed and configured correctly?

Thanks Skullclamp

---

### Post by tristram60 on 2011-05-25
Do you have your dns settings set up correctly?  If not, then if someone typed in yourdomaion.com into their browser it wouldn't work...

---

### Post by Skullclamp on 2011-05-26
I didn't set up a dns server because the place i buoyed the domain give a dns management system online..and i make record A to my external ip, thanks to google, but now i have problem because when access to the domain i give a 403 Forbidden error? 

Another thing did a make a good choose to ispconfig or ther is other thing better then ispconfig, free of course.

---

### Post by koenn on 2011-05-26
403: Forbidden
That's good, it means you can reach the server, and it replies.

---

### Post by Skullclamp on 2011-05-26
It's good or you are being ironic,[off]do not feel offended please...just saying this because i'm noob and experienced ppl make fun whit noob ppl[off]

Continuing on topic...

What i need to change to put everthing working? 

And if the error is good as you say, that means that the security part is working correct?

---

### Post by arrrghhh on 2011-05-26
> **Skullclamp said:**
> It's good or you are being ironic,[off]do not feel offended please...just saying this because i'm noob and experienced ppl make fun whit noob ppl[off]

Continuing on topic...

What i need to change to put everthing working? 

And if the error is good as you say, that means that the security part is working correct?

He's serious, that means the server is getting hit.

However I have a question - if you have a domain setup, do you also have a static IP (on your WAN, not LAN...)?  Most residential internet connections are dynamic, so you want to be careful when playing with this... If you're using a hosted solution that provides a static IP, then no worries.

Can you access the server OK from your LAN?  As in do you have everything setup correctly as far as Apache/web server goes, you can hit websites internally?

If so, then the only piece you'd need to take care of is port forwarding on your router & any firewall settings if you have one configured (which I would recommend configuring...)

Ubuntu doesn't come with a firewall enabled by default, as there's no services listening by default.  When you start turning up services, I would turn up a firewall so you can control what port the traffic is going thru, and only allow traffic you want to allow.  Also might want to do some research on fail2ban.

---

### Post by Skullclamp on 2011-05-26
My ISP says the ip is dynamic, but it only change if i reboot my modem and sometimes even i do reboot the modem is going to be the same ip...my isp is a litle bit s**ty.

If i hit the domain internely it gives the same error, probably because the apache is not going to the correct folder.

And the port fordwing is already done. it us the first thing i did after buy the domain.

But by doing the port fordwing, i'm already using the router firewall right...and i realy need the a software firewall?

If i need software firewall what is the best ufw or firesarter?

---

### Post by wake5269 on 2011-05-26
i know this is a little off topic, i am new to the forum and ubuntu, when i try to config a static ip to my server through the /etc/network/interfaces edit, there is no file.  I am using ubuntu 11.04 and when i type vi /etc/network/interfaces i get a blank page with blue dashes on the left hand side.  do i need to set up the file or should it be there?  Thanks for your help

---

### Post by arrrghhh on 2011-05-26
> **Skullclamp said:**
> My ISP says the ip is dynamic, but it only change if i reboot my modem and sometimes even i do reboot the modem is going to be the same ip...my isp is a litle bit s**ty.

If i hit the domain internely it gives the same error, probably because the apache is not going to the correct folder.

And the port fordwing is already done. it us the first thing i did after buy the domain.

But by doing the port fordwing, i'm already using the router firewall right...and i realy need the a software firewall?

If i need software firewall what is the best ufw or firesarter?

Uhm... I wouldn't recommend paying for a domain you are hosting on a residential internet connection.  Using DynDNS would be what I would recommend, but I still wouldn't 'drive traffic' to a site I'm hosting on my residential internet connection - read the terms and conditions, I can almost guarantee there will be a clause about how you will not host a website, etc on this connection...

So a little bit of traffic usually isn't a big deal, but if you get a ton your ISP might not be too happy...

You can always migrate the domain to another host at a later date.

As for firewall, Firestarter requires a GUI (a DE... or I guess you can forward X over ssh...)  UFW is what I use, it's pretty easy - but like any firewall configuration tool in Linux, they're just frontends for iptables.

> **wake5269 said:**
> i know this is a little off topic, i am new to the forum and ubuntu, when i try to config a static ip to my server through the /etc/network/interfaces edit, there is no file.  I am using ubuntu 11.04 and when i type vi /etc/network/interfaces i get a blank page with blue dashes on the left hand side.  do i need to set up the file or should it be there?  Thanks for your help

Please don't steal threads.  Search the forum, if you can't find an answer post your own thread please.

---

### Post by wake5269 on 2011-05-26
> **arrrghhh said:**
> .



Please don't steal threads.  Search the forum, if you can't find an answer post your own thread please.


I cant post a thread yet but i will remember than for next time sorry. this feels like xda

---

### Post by arrrghhh on 2011-05-26
> **wake5269 said:**
> I cant post a thread yet but i will remember than for next time sorry. this feels like xda

Forums are forums, it's rude to barge in on a thread and ask a completely irrelevant question.

---

### Post by Skullclamp on 2011-05-26
[QUOTE=arrrghhh;10867273]Uhm... I wouldn't recommend paying for a domain you are hosting on a residential internet connection.  Using DynDNS would be what I would recommend, but I still wouldn't 'drive traffic' to a site I'm hosting on my residential internet connection - read the terms and conditions, I can almost guarantee there will be a clause about how you will not host a website, etc on this connection...

So a little bit of traffic usually isn't a big deal, but if you get a ton your ISP might not be too happy...

You can always migrate the domain to another host at a later date.

As for firewall, Firestarter requires a GUI (a DE... or I guess you can forward X over ssh...)  UFW is what I use, it's pretty easy - but like any firewall configuration tool in Linux, they're just frontends for iptables.

I now about that clause that dosen't aloud doamin etc...but they give me unlimited trafic at least for download but probalby is for bout thing's...but for trafic i think i don't have problems.

And for now the home server it will be for one more blog about technolagy and stuff about that:P and my personal site.

---

### Post by arrrghhh on 2011-05-26
> **Skullclamp said:**
> I now about that clause that dosen't aloud doamin etc...but they give me unlimited trafic at least for download but probalby is for bout thing's...but for trafic i think i don't have problems.

And for now the home server it will be for one more blog about technolagy and stuff about that:P and my personal site.

Yea, they give you unlimited bandwidth to use your internet connection as you have agreed-upon to do - they do not provide unlimited bandwidth for hosting a website - so I guess if you don't plan on publishing the site, then you'll be fine but I don't get the point if you are paying for a domain name.

Also what will you do when the address changes?  It won't happen frequently, but it **will** happen.

Either way, don't be surprised if you get a nastygram from your ISP - or if they cut you off entirely.  You're almost certainly violating their terms and conditions.

---

### Post by tristram60 on 2011-05-27
If you get the 403 forbidden error then that means that the folder your webfiles are stored in is protected.  Try changing the permissions for that folder or something.

---

