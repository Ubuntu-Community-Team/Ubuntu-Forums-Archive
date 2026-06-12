---
title: "Remote web proxy server"
date: 2008-11-13
forum: Server Platforms
---

### Post by aparod on 2008-11-13
Hi,

I have a dedicated ubuntu server located in the data center. I'm trying to set it up as a proxy server so that my office computer can get an access to. This is because some websites are filtered at my office.

The idea is that I want my remote server to act as a proxy server like the one that’s posted on free proxy list web. Off course, I want to set it up so that password has to be provided to get an access to.  I tried to install squid and found out that it's probably not the right program I’m looking for. Squid is for inside out not outside in right?   

I tried to search this forum and it seems that tunnel via putty to squid may not be my solution. This is because I can’t get Putty to connect to the outside world at my office as port 22 is also blocked.At my office, only port 80 is allowed. I also have to connect to the corporate proxy server at port 8080 to connect to the outside.

Please point me out to the right direction as to which server software (Ubuntu off course) is the right one I’m looking for and how to set it up? Sorry if this has been discussed to dead I’m very new to ubuntu world.

Regards,

---

### Post by weiliang on 2008-11-13
have you tried rabbit?

[www.khelekore.org/rabbit/](www.khelekore.org/rabbit/)

---

### Post by aparod on 2008-11-13
Hi,
Thanks for the reply. I will look into it.

However, I think my problem is that at the office only port 80 is workable. I couldn't get putty to connect to the outside sever port 22. I tried to set up putty to connect to corporate proxy (port 8080) then connect to the outside server. But it failed to make a connection.

So I'm trying to figure it out how to get out of the corporate firewall where it seems only port 80 is available.

Any helps would be highly appreciated.

Thanks,

---

### Post by nmsmith on 2009-02-26
I know this thread is a little old, but I'm having exactly the same issues trying to connect to port 22 on my ubuntu home PC. My router isn't clever enough to redirect a different incoming port to 22, and I already run a webserver at home anyway on 8080 and 80. I'd like to be able to use ssh both as work proxy avoidance and in order to do remote maintenance, but our network is very heavily locked down, with only ports 80 and 8080 open.

I'd be using PuTTY from a Windows PC.

Any further thoughts on this matter?

---

### Post by 3L33T on 2009-02-26
> **nmsmith said:**
> I know this thread is a little old, but I'm having exactly the same issues trying to connect to port 22 on my ubuntu home PC. My router isn't clever enough to redirect a different incoming port to 22, and I already run a webserver at home anyway on 8080 and 80. I'd like to be able to use ssh both as work proxy avoidance and in order to do remote maintenance, but our network is very heavily locked down, with only ports 80 and 8080 open.

I'd be using PuTTY from a Windows PC.

Any further thoughts on this matter?

Change default ssh port of your ubuntu at home from 22 to something else (ie: 2222).

Here's [the link]("http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/") on how to do that.

Open port 2222 in your router and NAT it to your Ubuntu server where SSH is already waiting in port 2222.

Change ssh port in puTTY to 2222.

HTH.

---

### Post by nmsmith on 2009-04-25
Thanks, it might have done. My router doesn't allow specific ports; in an attempt to be 'user friendly' the only thing it has is a drop-down list of services (torrents, online gaming, mail servers etc).

In the end I found out from work that 443 (for obvious reasons) is available, and my router had an option for a https server on its network, so I opened ssh on 443 also. That's done the trick.

---

