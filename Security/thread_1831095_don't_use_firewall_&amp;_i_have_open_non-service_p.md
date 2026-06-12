---
title: "don't use firewall &amp; i have open non-service ports anything safer than denyhosts?"
date: 2011-08-22
forum: Security
---

### Post by joelbue on 2011-08-22
don't use firewall & i have open non-service ports anything safer than denyhosts?

consider me paranoid, and wish to remain paranoid :)

---

### Post by Dangertux on 2011-08-23
Denyhosts works for authentication based apps like ssh to prevent brute force attacks. 

In your case using ufw would probably be best.

---

### Post by The Cog on 2011-08-23
I thought that denyhosts used log files to decide who to ban. Without knowing which services you are trying to protect, it is not possible to know if denyhosts will spot trouble and be any help at all.

What does "open non-service ports" mean? outgoing connections?

---

### Post by joelbue on 2011-08-23
yes i have outgoing connections.  they are non-service ports.  could someone lend me a hand configuring GUFW for a port range or for a single port ?  its system service's is easy enough to handle.  if anyone could manage a screenshot for a port range or single port on GUFW that would be originating from the same 192.168.1.130 ip address, i'd really appreciate that. no different ip ranges.  

thanks all.

---

### Post by Dangertux on 2011-08-23
> **The Cog said:**
> I thought that denyhosts used log files to decide who to ban. Without knowing which services you are trying to protect, it is not possible to know if denyhosts will spot trouble and be any help at all.

What does "open non-service ports" mean? outgoing connections?

This is correct : it does audit log files for failed login attempts to attempt to block them thus breaking a brute force attack.

As for ufw -- check the docs here.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by cariboo on 2011-08-23
If you don't have any services running, the default;t ufw settings should be enough. To test it, use nmap to do a port-scan from another system on your network.

---

### Post by wacky_sung on 2011-08-24
> **cariboo907 said:**
> If you don't have any services running, the default;t ufw settings should be enough. To test it, use nmap to do a port-scan from another system on your network.

Nmap only scan for open ports/services.Why use Nmap?Just the terminal with the command "netstat -tulnp" .Search for the state under the terminal for listen will do.That determine if you got any opening service/port.Beside that, use a vulnerability scanner to scan for known exploits.Upon doing so, make sure you have updated your update manager.Try to minimize to install the number of softwares when necessary only and this help to reduce the risk of an exploit which can be found within the software itself.There are more to go......I do not wanna get into details. Good luck.

---

### Post by The Cog on 2011-08-24
So is it the fact that you have outgoing connections that bothers you? If you want to block all outgoing connections, something like ```
sudo ifconfig eth0 down
``` will do the trick.

Otherwise, I still don't understand what you want to achieve.

---

### Post by haqking on 2011-08-24
> **wacky_sung said:**
> Nmap only scan for open ports/services.Why use Nmap?Just the terminal with the command "netstat -tulnp" .Search for the state under the terminal for listen will do.That determine if you got any opening service/port.Beside that, use a vulnerability scanner to scan for known exploits.Upon doing so, make sure you have updated your update manager.Try to minimize to install the number of softwares when necessary only and this help to reduce the risk of an exploit which can be found within the software itself.There are more to go......I do not wanna get into details. Good luck.

NMAP does alot more than scan only for open ports.

---

### Post by cariboo on 2011-08-24
Using nmap will also give the op peace of mind, as the system we not be seen by other computers.

---

### Post by wacky_sung on 2011-08-25
> **haqking said:**
> NMAP does alot more than scan only for open ports.

Isn't i wrote ports/services?Indeed it does more than just scanning port but it purpose is to prone the target.Nmap is usually deployed to an unknown network, otherwise it is kinda defeat the purpose to me.

---

### Post by Dangertux on 2011-08-25
nmap can be used on known or unknown networks. Honestly you can get a great deal of functionality out of nmap on a known network.

Such as service version detection, authentication enumeration, samba share enumeration, patch levels and operating system detection to name a few. Also -- not all port scans are created equal, most of the sites on the internet will do a simple tcp connect scan. However nmap is highly customizable, and depending on the type of firewall you use (stateless/stateful/dpi) nmap can give you a more complete picture of what an outside "visitor" might be able to see.

A side note : It hasn't been said yet but probably will be mentioned at some point in this thread. There is no such thing as a stealthed port (Steve Gibson while an awesome guy really created a nightmare with this catch phrase he created for shields up)

---

### Post by wacky_sung on 2011-08-25
@Dangertux Isn't i mention ports/services? Apart from that, those gather informative give you better chance to exploit into the network.Pardon me, i just do not like Steve Gibson. He is just marketing himself.

---

### Post by Dangertux on 2011-08-25
Yes that is true -- gathering information is crucial to exploiting a vulnerable network. However : you can't really secure your system if you don't know what exactly a potential intruder sees.

---

### Post by wacky_sung on 2011-08-25
At some point i may agree and disagree with your analysis.First of all,you need to start from basic of how you layout your network.The intruder can break through a dummy/honeyport and not knowing getting caught in the act.Usually that is the first layer of defense you shall be using. Apart from that, you gonna understand what type/kind of applications/services you wanna run it.

---

### Post by cariboo on 2011-08-26
@wacky_sung, unless I'm misinterpreting a whole lot of things, don't you have to have access to the kernel before you can run an exploit? Netfilter/iptables should be the first line of defense, if there is no way through it, then kernel exploits are pretty useless. If nmap can't give you the information you need about a system, eg: operating system, then running exploits against a system you nothing about, is pretty useless.

You may want to read [this]("http://nmap.org/book/osdetect.html#osdetect-reasons") before dismissing nmap.

---

### Post by wacky_sung on 2011-08-26
> **cariboo907 said:**
> @wacky_sung, unless I'm misinterpreting a whole lot of things, don't you have to have access to the kernel before you can run an exploit? Netfilter/iptables should be the first line of defense, if there is no way through it, then kernel exploits are pretty useless. If nmap can't give you the information you need about a system, eg: operating system, then running exploits against a system you nothing about, is pretty useless.

You may want to read [this]("http://nmap.org/book/osdetect.html#osdetect-reasons") before dismissing nmap.

An exploit does not mean it has to link with kernel and you gonna know what type of exploits are you using it at or exploring to find to find one. Nmap is just a tool but this is not the only tools. You can create tools of your own. Pardon me, i do not wish to explain further as this forum is not a pure security site and the forum administrators are very conservation toward in depth discussion. I bet i better end here.:guitar::guitar::guitar::guitar:

---

### Post by Dangertux on 2011-08-26
> **wacky_sung said:**
> At some point i may agree and disagree with your analysis.First of all,you need to start from basic of how you layout your network.The intruder can break through a dummy/honeyport and not knowing getting caught in the act.Usually that is the first layer of defense you shall be using. Apart from that, you gonna understand what type/kind of applications/services you wanna run it.

I am a little confused what the question even is anymore... 

Honeypots are...Well a great research tool, and if implemented properly on a large network can be a huge plus for security. 

However, in case you've never looked at a honeypot it's actually pretty easy to tell it's a honeypot as soon as you look at it. Particularly if it is something like honeyd. There are some sysadmins that roll their own honey pot. Those are actually very effective.

Again on nmap, it is not the catch all tool, and no it is not an exploitation framework like metasploit or core impact.  It doesn't do any exploitation, however it is a great discovery tool, bar none the best imho. As I said before nmap is capable of doing almost anything you want it to do, see the nmap scripting engine if you want further proof of this. 

As far as penetrating a system goes, if you have bad intelligence on the system (IE: your footprinting sucks) you're just going to be firing blindly at it anyway hoping desperately that something works right. Nmap is a great tool for filling in the gaps in information you might not have, among others like nessus, nikto, etc. 

As far as creating exploits go -- yes that is a topic that this forum frowns upon, because generally speaking with the exception of some professional reasons creating exploit code is generally done for malicious reasons. That being said , there are reasons that are completely valid to create exploit code (security research, application and network q/a testing,  and penetration testing) for example. 

However, back on topic ; I don't think any of that was originally brought up in the question. The original question is using  denyhosts a decent solution when I'm running some services (non registered ports?) without a firewall.

The answer is no, unless those services are inetd services or ssh denyhosts will not do much for you.  The truth of the matter is, neither will a firewall if you insist on running those services. Since the service is running, the socket is bound and the ability to connect is there. Unless of course you go really crazy and use a dpi firewall or something along those lines. 

The best solution imho if they want to run the services publicly is this.

- Make sure whatever services they are , are up to date.
- Make sure they are running valid apparmor profiles for the services (in case of that dreaded hand crafted 0 day exploit)
- Make sure the services have strong passwords or keys in place for all authentication types.
- Make sure the services have the least amount of permissions that they need to run.
- Make sure if the services can utilize end to end encryption that they do.
- Make sure that administrative access to said services is limited ONLY to those that need it. (IE: If you don't need an admin interface available publicly on the internet that it isn't)

Neither a firewall NOR deny hosts are comprehensive hardening measures when running a public service, even if it is SSH or an inetd service. 

That's just my opinion, and I think probably the best advice in this particular case.

---

