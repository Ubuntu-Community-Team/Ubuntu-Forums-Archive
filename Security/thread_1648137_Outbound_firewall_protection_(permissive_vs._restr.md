---
title: "Outbound firewall protection (permissive vs. restrictive) - what's your setup?"
date: 2010-12-18
forum: Security
---

### Post by nrundy on 2010-12-18
Using Windows, I always set a Restrictive firewall policy with a third party firewall. But I also had all ports set to Stealth, something that appears to not offer any security benefits (as I've learned from reading Ubuntu forums). I'd like to learn about best security practices (under Ubuntu) for outgoing firewall protection. I will be using the built-in Ubuntu firewall that is configured via Firestarter. Outgoing filtering offers privacy as well as security benefits. But I thought I needed my ports stealthed to be safe too, so I'm open to learning new things.

I wanted to start a poll to find out how many folks use permissive/restrictive, but no polls allowed here apparently.

Could Ubuntu users knowledgeable about firewalls enlighten me on whether I should go Outbound-Restrictive and what applications I will need to allow so Ubuntu "housekeeping" is not affected negatively? I basically just use the internet for software updates, web-surfing and e-mail. One question I have is whether there is something comparable in Ubuntu to Window's "DNS Client" service? I always disabled Window's "DNS Client" and forced each application to request port 53 DNS lookups itself.

I only had to allow four programs to accomplish all internet traffic that I engage in. I set all other programs/applications to be either Blocked or to have to Ask for an outgoing connection as needed. 

Here is my former Windows XP setup:

svchost.exe: allow UDP for ports 53, 67, 68, 123 (time) and TCP for ports 80, 443
Avast: allow UDP for port 53 and TCP for port 80
firefox: allow UDP for port 53 and TCP for ports 80, 443
IE: allow UDP for port 53 and TCP for ports 80, 443

---

### Post by OpSecShellshock on 2010-12-18
Firestarter is no longer maintained, and it's not really necessary. A default installation of Ubuntu will not have any listening services, so there's really nothing to restrict. As for outgoing connections, there's not much of a point in placing any restrictions on those. The only processes that will establish connections from your local machine to the web will have to be run by your user. I know that with Windows there are all kinds of background processes and applications that make connections or worse, listen for incoming connections without giving you any control over it. Ubuntu isn't like that and does not have any such processes (at least not by default).

---

### Post by The Cog on 2010-12-18
I see no point in trying to block outgoing connections.

For incoming connections, on my server (where SSH is port-forwarded to) I have a firewall setting that only allows SSH from the local LAN or from work. It also accepts OpenVPN connections from anywhere, and provides routing to the rest of the LAN.

For other computers, they all accept SSH but since they're not accessible from the internet, I don't use any firewall.

---

### Post by bodhi.zazen on 2010-12-18
> **nrundy said:**
> Using Windows, I always set a Restrictive firewall policy with a third party firewall. 

In windows this is wise, but Ubuntu is not windows.

> But I also had all ports set to Stealth, something that appears to not offer any security benefits (as I've learned from reading Ubuntu forums).

Probably been reading my posts as I do not like the term "stealth". The important thing is that you understand what "stealth" means. It is the difference between DROP and REJECT. While "stealth" sounds cool, both DROP and REJECT are equally secure, they bock the attempted connection.

> I'd like to learn about best security practices (under Ubuntu) for outgoing firewall protection.

You do not need to write rule for outbound traffic in Linux as the OS does not suffer from malware the way Windows does.

You can either take the work of experienced users, or install wireshark and watch for yourself, up to you.

> I will be using the built-in Ubuntu firewall that is configured via Firestarter.

The "built in firewall" is iptables which is a front end for netfilter.

Firestarter is no longer maintained and you are much better off either learning iptables or ufw. If you want a graphical front end, use gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)


> Outgoing filtering offers privacy as well as security benefits.

In windows perhaps, but please list the "benefits" in Linux.

> But I thought I needed my ports stealthed to be safe too, so I'm open to learning new things.

Start by reading the security sticky and at least understand the difference between "DROP" and REJECT".

> I wanted to start a poll to find out how many folks use permissive/restrictive, but no polls allowed here apparently.

Most people use a router, which already has a firewall built in. By default there are no significant listening servers in Ubuntu, thus a firewall is overkill for the vast majority of Desktop users.

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)
[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

> Could Ubuntu users knowledgeable about firewalls enlighten me on whether I should go Outbound-Restrictive and what applications I will need to allow so Ubuntu "housekeeping" is not affected negatively? I basically just use the internet for software updates, web-surfing and e-mail. One question I have is whether there is something comparable in Ubuntu to Window's "DNS Client" service? I always disabled Window's "DNS Client" and forced each application to request port 53 DNS lookups itself.

I do not know about windows DNS client or why you would disable it.

> I only had to allow four programs to accomplish all internet traffic that I engage in. I set all other programs/applications to be either Blocked or to have to Ask for an outgoing connection as needed. 

Here is my former Windows XP setup:

svchost.exe: allow UDP for ports 53, 67, 68, 123 (time) and TCP for ports 80, 443
Avast: allow UDP for port 53 and TCP for port 80
firefox: allow UDP for port 53 and TCP for ports 80, 443
IE: allow UDP for port 53 and TCP for ports 80, 443

Learn to use Apparmor and confine any network aware applications.

---

### Post by HermanAB on 2010-12-19
Howdy,

Note that Linux is not Windows.  You don't need to do all the stupid tricks that Windows may need in a mostly useless effort to keep it somewhat safe.

Turn your firewall cruft off, then relax and enjoy your Linux system.

---

### Post by nrundy on 2010-12-19
> **OpSecShellshock said:**
> As for outgoing connections, there's not much of a point in placing any restrictions on those. The only processes that will establish connections from your local machine to the web will have to be run by your user. I know that with Windows there are all kinds of background processes and applications that make connections or worse, listen for incoming connections without giving you any control over it. Ubuntu isn't like that and does not have any such processes (at least not by default).

 I did not know this about Ubuntu. One of the things I HATE about Windows is how any application will just connect to the internet by itself without user input.  If the only outgoing connections in Ubuntu are user initiated, then outgoing filtering would appear to be unneeded. I'll go ahead and not setup any rules per you guys' advice. Thanks!

---

### Post by nrundy on 2010-12-19
Do you guys enable/run IPtables? or do you leave it disabled (it's disabled by default, right?)  Is your advice basically only to enable IPtables if you are running services (server)? So for a common Desktop under Ubuntu, there is no need to even turn on IPtables?

---

### Post by bodhi.zazen on 2010-12-19
> **nrundy said:**
> Do you guys enable/run IPtables? or do you leave it disabled (it's disabled by default, right?)  Is your advice basically only to enable IPtables if you are running services (server)? So for a common Desktop under Ubuntu, there is no need to even turn on IPtables?

Assuming you are behind a router and you are not forwarding any ports they yes running a firewall is overkill.

If you feel you "need" to run a firewall, simply run```
sudo ufw enable
```and be done with it. Unless you know about iptables it is unlikely you can write a better set of rules for your firewall then the default settings for ufw.

If you are interested, start reading the security thread, read on iptables, and start monitoring your network traffic (wireshark).

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by nrundy on 2010-12-19
I am not behind a router, so I'll go ahead and enable UFW like you suggest.  Thanks.

---

### Post by ester4 on 2010-12-19
> **bodhi.zazen said:**
> 
If you feel you "need" to run a firewall, simply run```
sudo ufw enable
```and be done with it. Unless you know about iptables it is unlikely you can write a better set of rules for your firewall then the default settings for ufw.


bodhi, what about the ICMP Echo setting? The default setup allows Echo Requests (ping) and my understanding is that it is best to disable this for a system not behind a router. Assuming user is not behind a router, is it better security practice to disable the Echo Request ICMP packet? Does your answer change if user is behind a router and still chooses to enable UFW?

Is there a command for the UFW that tells its status? Like how does one find out if the UFW is enabled or disabled?

---

### Post by bodhi.zazen on 2010-12-19
> **ester4 said:**
> bodhi, what about the ICMP Echo setting? The default setup allows Echo Requests (ping) and my understanding is that it is best to disable this for a system not behind a router. Assuming user is not behind a router, is it better security practice to disable the Echo Request ICMP packet? Does your answer change if user is behind a router and still chooses to enable UFW?

Is there a command for the UFW that tells its status? Like how does one find out if the UFW is enabled or disabled?

You can disable ping requests if you wish, hard to feel it increases security.

Perhaps in 1980 this may have been a part of security, but if you monitor your internet traffic there is an almost ongoing barrage of automated attacks, aka "script kiddies" as they are called, although they can be dangerous. Disabling a ping response and using DROP rather then reject do little if anything to shelter you or hide from such things.

They know you are there with DROP or "Stealth" because of the delay and no one will ping you before they hit your ip with a script.

I covered blocking ping on this blog page:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

and it is on the ufw wiki as well

[https://help.ubuntu.com/community/UFW#Advanced%20Syntax](https://help.ubuntu.com/community/UFW#Advanced%20Syntax)

---

### Post by ester4 on 2010-12-21
Is there a way to block pinging using the GUFW?  Is there a way to configure ICMP in general using GUFW, there was with Firestarter.

---

### Post by bodhi.zazen on 2010-12-21
> **ester4 said:**
> Is there a way to block pinging using the GUFW?  Is there a way to configure ICMP in general using GUFW, there was with Firestarter.

Not that I know of. IMO it is trivial to edit the ufw config file.

Edit the file, enable ufw, and forget about it. You do not need to micromanage your firewall.

Server side you can use itpables. I know the learning curve is steep, but half of that is learning the underlying networking.

```
sudo -A INPUT -p icmp -m limit --limit 1/sec -j ACCEPT
```

My 2c is that if you are interested in security, you should take an interest in education and look under the graphical interface.

If you are not inclined to do so:

```
sudo ufw enable
``` is sufficient for you needs. If not, please explain ...

---

### Post by ester4 on 2010-12-21
Assuming I understand what ping is used for correctly, I have absolutely no use for it. Therefore, I'd like to block the requests. Since the Firestarter interface gave users this ability, I was wondering why the GUFW doesn't. It is a configuration setting that GUFW needs to add.

Is there any harm in using the firestarter GUI to configure the firewall since the GUFW can't do what I want. And I don't want to mess with command lines in a terminal?

---

### Post by bodhi.zazen on 2010-12-21
There is nothing wrong with using firestarter if you prefer.

Understand that Firestarter has not been maintained for several years and if you run into a bug you will have no support from developers.

At some point, once firestarter fails, you will need to migrate.

A simple edit to a configuration file is not, IMO, that big a deal.

```
gksu gedit
```

Navigate to file -> edit -> save and quit.

---

### Post by ester4 on 2010-12-21
Is there a way to request that GUFW add ICMP settings for configuration in a future version?

I'm not following you with gksu gedit? Do I type this into a Terminal and it brings up a file I can edit to disable ping response?

---

### Post by bodhi.zazen on 2010-12-21
> **ester4 said:**
> Is there a way to request that GUFW add ICMP settings for configuration in a future version?[quote]

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

[quote]I'm not following you with gksu gedit? Do I type this into a Terminal and it brings up a file I can edit to disable ping response?

yes.

I can see from your post you are new here and my last piece of advice is that this is not Windows and you would do well to learn some new things rather then apply things you learned in Windows to Linux.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by ester4 on 2010-12-21
I'm open to learning new things, I wouldn't be here using Ubuntu if I wasn't. 

Not sure what you mean by, "rather then apply things you learned in Windows to Linux." Do you mean my preference for GUI instead of command-line? I'm new and don't feel comfortable with commands yet. I hope to eventually though.

---

### Post by bodhi.zazen on 2010-12-21
> **ester4 said:**
> I'm open to learning new things, I wouldn't be here using Ubuntu if I wasn't. 

Not sure what you mean by, "rather then apply things you learned in Windows to Linux." Do you mean my preference for GUI instead of command-line? I'm new and don't feel comfortable with commands yet. I hope to eventually though.

The best way to learn commands is to use them. When I teach Linux I like to show people how to solve various problems with the gui and with the command line.

In this case I am guessing you are applying some piece of knowledge you learned about ping or perhaps something someone told you perhaps many years ago without stopping to examine why one would block ping or if it even applies to modern security techniques.

Likewise you are using Firestarter as it is familiar and thus easy.

There is no problem with either decision, but, in the process, you seem to have sacrificed on the learning.

Security is an active process and the best defense you have is to educate yourself.

---

### Post by cariboo on 2010-12-21
Another thing to keep in mind is that ping is one of the most basic networking troubleshooting tools. It can help solve all sorts of network problems from DNS to dropping connections.

---

### Post by ester4 on 2010-12-21
Can you give me a specific "everyday" example of ping use on a standalone computer that is not part of a network? You said DNS, so like if I can't connect to a site I might ping the site and see what the reply kicks back? By disabling ping response I take away my ability to do this or just someone else's ability to ping me and get a response?

---

### Post by bodhi.zazen on 2010-12-21
> **ester4 said:**
> Can you give me a specific "everyday" example of ping use on a standalone computer that is not part of a network?

Can you give me a specific "everyday" example of how and why such a computer needs a Firewall ?

> You said DNS, so like if I can't connect to a site I might ping the site and see what the reply kicks back?

lolwut ? ping is a tool most often used to test networking.

ping localhost
ping router
ping google
ping broken site
traceroute ...

I do not know that these are "everyday" tools, but I also do not understand why you think you somehow need to disable ping either.

Can you give a (credible) modern reference to a security citation as to why disable ping? I could not find such a reference with a google search.

Just to be clear, I am not asking for some blog somewhere from some unknown entity spouting FUD, I am asking for a credible site :

[http://nvd.nist.gov/](http://nvd.nist.gov/)

I searched here:

[http://web.nvd.nist.gov/view/vuln/search](http://web.nvd.nist.gov/view/vuln/search)

For ping, last 3 years, nothing comes up.

Seriously, you are chasing your own shadow.

> By disabling ping response I take away my ability to do this or just someone else's ability to ping me and get a response?

Depends on how you configure the rules, could be either or both depending on if you use the input or output chain.

I highly suggest you stop and do a little research :p

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://www.linuxtopia.org/Linux_Firewall_iptables/index.html](http://www.linuxtopia.org/Linux_Firewall_iptables/index.html)

[http://www.linuxtopia.org/Linux_Firewall_iptables/x265.html](http://www.linuxtopia.org/Linux_Firewall_iptables/x265.html)

[http://www.linuxtopia.org/Linux_Firewall_iptables/x270.html](http://www.linuxtopia.org/Linux_Firewall_iptables/x270.html)

---

### Post by bodhi.zazen on 2010-12-21
Input:

```
#This rule drops [size=3]**[color=darkred]incoming echo requests**[/color][/size]
iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

#This rule drops [size=3]**[color=darkred]incoming echo replies**[/color][/size]
iptables -A INPUT -p icmp --icmp-type echo-reply -j DROP
```

OUTPUT:
```
#This rule drops [size=3]**[color=darkgreen]outgoing echo requests**[/color][/size]
iptables -A OUTPUT -p icmp --icmp-type echo-request -j DROP

#This rule drops [size=3]**[color=darkgreen]outgoing echo replies**[/color][/size]
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j DROP
```

=)

---

