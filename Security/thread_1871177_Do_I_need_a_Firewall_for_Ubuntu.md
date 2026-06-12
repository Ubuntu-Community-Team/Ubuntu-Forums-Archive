---
title: "Do I need a Firewall for Ubuntu?"
date: 2011-10-28
forum: Security
---

### Post by Dangertux on 2011-10-28
The information in this thread has been moved to [https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12088432#post12088432](http://ubuntuforums.org/showthread.php?p=12088432#post12088432)

Thread closed.



I am writing this because the previously posed question is asked consistently on this forum. I am hoping that I can create something of a generally accepted answer that contains all the necessary links to appropriate resources. 


 So the question posed : Do I need a Firewall for Ubuntu?
 

 Truthfully, this is a subjective question. Ultimately it depends on your tolerance for risk and your use case. However, since it is impossible to tailor this discussion to fit everyone's needs we will focus on a model that is in line with best practices.  
 

 What I want to address are some assumptions, or misunderstandings about firewall methodology in general and in regard to Ubuntu Linux.  
  
 _**What firewall does Ubuntu have?**_  
 

 Ubuntu , as with all post 2.2/2.4 kernel Linux distributions comes with the netfilter/iptables framework. This framework is a set of kernel modules that can be utilized to create packet filtering rules at the kernel level. Rules are written in iptables format, which is the method of conveyance of instructions to netfilter, and in essence the Linux Kernel.  
 

 Ubuntu also includes an application called Uncomplicated FireWall (UFW). This application is a userspace application that essentially can be used to create iptables rules. There is also a GUI for UFW called GUFW. It provides a graphical interface for UFW. Again remember, UFW is simply writing iptables rules and sending them off to netfilter, and thus the kernel. It is NOT a firewall in and of itself.
 
There are other applications such as Firestarter, which essentially cover the same ground as UFW. The Firestarter project is out of development, and was bug prone even when it was developed actively. I do not recommend it, and it is not the default thus it will not be covered. It is important to know that there is nothing that Firestarter can do that you can not do with either UFW or by interacting directly with iptables.
 

 You need to realize that Ubuntu's firewall is not enabled by default. You have to enable it.
 

 [iptables documentation]("https://help.ubuntu.com/community/IptablesHowTo") 
[ufw documentation]("https://help.ubuntu.com/community/UFW")

 

 _**I have no open ports, so I don't need a firewall, right?**_
 

 Well, not really. This is a common misconception. First , let us understand what an open port actually is. An open port is a port that has a service (like SSH) bound and listening to it. When the SSH client tries to communicate with the SSH server it will send a TCP SYN packet to the SSH port (22 by default), and the server will ACKnowledge it, thus creating a new connection.  
 

 The misconception in how a firewall can help you begins here. Some users assume that since you are running no services, a connection can not be made. So you do not need a firewall. If these were the only things you needed to think about, this would be perfectly acceptable. However, this is only part of the picture.  
 

 There are two additional factors that come into play there. One, if you do not utilize a firewall on the basis that you have no open ports, you are crippling your own security because if an application that you do have is exploited and code execution occurs a new socket can be created and bound to an arbitrary port. The other important factor here is that if you are not utilizing a firewall you also have no outbound traffic control whatsoever. In the wake of an exploited application, instead of a new socket being created and a port being bound, another alternative an attacker can utilize is to create a reverse connection back to a malicious machine. Without any firewall rules in place this connection will go through unhindered.

[Article demonstrating how different types of firewall rules can be bypassed by an attacker.]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/")


 If you were setting up a desktop system with best practices in mind you would want both strict inbound and strict outbound firewall rules. This would minimize the impact of either a listening service being bound or a reverse connection being initiated.  
 

 [Strong Outbound Rules for UFW]("http://blog.bodhizazen.com/linux/firewall-ubuntu-desktops/")
[URL="http://ubuntuforums.org/showthread.php?t=1876124"]Strong Outbound rules using UFW, GUFW or iptables
[/URL] 
 

 _**You just said I have no services listening so then how can an application become compromised?**_
 

 You need to understand what I (and others) mean when we say a listening service. When we are saying listening service we are referring to a persistent service listening for incoming connections, examples would be SSH, Apache, MySQL, FTP, VNC, and a myriad of other services you may have running.  
 

 However, you are exposed to creating a new connection to your system many times every single day. In fact, the act of loading this post alone created no less than 1 new connection to your machine, possibly more.  
 

 Now for a moment, assume that this wasn't Ubuntu Forums, and that it was a malicious site you accidentally visited. If this site were crafted in such a way that it could take advantage of a flaw in your browser, it could be used to execute malicious code on your machine. If this occurs a possible outcome would be to open a connection to another machine, so that machine could remotely access yours. Strong firewall rules in some cases can help to mitigate that risk. If the packets used to create that connection are filtered by your firewall, the connection will never happen.  Another example that you are likely exposed to would be maliciously crafted media files, or perhaps a malicious ODT or PDF file. These are all common vectors of attack, and something you are relatively likely to encounter.  
 
As we can see our firewall can mitigate some of this, however there are ways around it. If you read the article in the section about inbound and outbound rules it demonstrated how even a strong firewall can be bypassed.  A firewall is a great tool for stopping automated exploitation, but as the article showed a dedicated attacker will find a way around this. Thankfully we have a number of tools at our disposal to help mitigate risk further.
 

 We can contain what our applications can do utilizing mandatory access controls through applications like Apparmor. Apparmor can essentially harden your applications against a zero day exploit. Limiting what an exploited application can do, to its core functionality. Even if your application were compromised the attacker in theory would only be able to execute the innate functionality of the application.


[URL="http://ubuntuforums.org/showthread.php?t=1008906"]Apparmor forum sticky
[/URL]


 Additionally, in terms of browser security we can take another step by using a browser extension like [NoScript]("http://noscript.net/getit") for Firefox or [NotScripts]("https://chrome.google.com/webstore/detail/odjhifogjcknibkahlpidmdajjpkkcfn") for Chrome. One of the most serious threats to the average desktop user are browser based exploits. These addons go a long way in limiting the ability of a browser based exploit to take place.
 

 If you utilize all three of these methods; a strong firewall, mandatory access controls, and browser based addons, you will see that we now have a strong 3 layer approach to desktop security. Which is preferable to any one of the approaches by itself. It now gives us three layers of protection a potential attacker has to circumvent. This reduces the odds of an automated attack being successful to almost 0 and greatly reduces the threat of an advanced attacker targeting you.  
 

 You can go a step further by protecting your private data via encryption. However that is outside the scope of this discussion. So I will leave you to research that on your own. 
 
 _**Well, I'm behind a NAT router so none of this is for me, right?**_
 

 Wrong again. A NAT router is a great addition to your security, but as I've been enforcing throughout this post, that there is no catch all solution.  
 

 A NAT router will prevent a service from being bound and accessible from the Internet. That being said, it works a lot like strong inbound only rules as we discussed earlier in this post. It does not provide protection against methods like a reverse connection designed to bypass a firewall. Another important thing to note is that the NAT router's protection is not host based. So if another machine on the network with yours is compromised the NAT router will offer your machine no protection.  
 

 When used in conjunction with the other topics we've discussed in this post a NAT router is an excellent hardening measure, however as a stand alone solution it is lacking in many ways.
 

 Hopefully this has been educational, and given you an idea of ways that you can utilize your firewall and other security applications to increase your level of protection.
  
 **Additional Resources :**

[Ubuntu Forums Security Sticky ]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by SparTacux on 2011-10-28
I think that covers about everything that has been mentioned in the last few threads on this subject.

STRENGTH IN DEPTH

The only thing I'd add to that is the usefulness of Firewall Logs especially SYSLOG from modem detailing ALL inbound & Outbound Traffic. Being able to SEE ( in Real-Time ) what is happening greatly adds to overall security.

---

### Post by PeteAsdf on 2011-11-02
Great post Dangertux, thanks a lot!

Following your advice (and bodhi.zazhen's) I modified my UFW rules- I previously had the default: deny in, allow out. I now defined stricter outbound rules i.e. deny all except web browsing, mail, skype, ssh and torrents.

Here is the ufw status. Am I doing this right, Masters, or have I botched it again? 


sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
22,25,80,443/tcp           ALLOW OUT   Anywhere
6881/tcp                   ALLOW OUT   Anywhere
4444/udp                   ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
995/tcp                    ALLOW OUT   Anywhere
465/tcp                    ALLOW OUT   Anywhere
61310/tcp                  ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
22,25,80,443/tcp           ALLOW OUT   Anywhere (v6)
6881/tcp                   ALLOW OUT   Anywhere (v6)
4444/udp                   ALLOW OUT   Anywhere (v6)
443/tcp                    ALLOW OUT   Anywhere (v6)
995/tcp                    ALLOW OUT   Anywhere (v6)
465/tcp                    ALLOW OUT   Anywhere (v6)
61310/tcp                  ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)

---

### Post by mikaelcrocker on 2011-11-02
I will have to agree with Security in layers, also too, it depends on what you have behind there? some Load Balancers aren't super secure so using a firewall is always a good idea, software or hardware :)

---

### Post by lovbuntu on 2011-11-02
Excellent post Dangertux. I hope this get sticked.

---

### Post by MrLeek on 2011-11-03
Yes, another great post. Vote for sticky

---

### Post by SparTacux on 2011-11-03
> **PeteAsdf said:**
> Great post Dangertux, thanks a lot!

Following your advice (and bodhi.zazhen's) I modified my UFW rules- I previously had the default: deny in, allow out. I now defined stricter outbound rules i.e. deny all except web browsing, mail, skype, ssh and torrents.

Here is the ufw status. Am I doing this right, Masters, or have I botched it again? 


sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
22,25,80,443/tcp           ALLOW OUT   Anywhere
6881/tcp                   ALLOW OUT   Anywhere
4444/udp                   ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
995/tcp                    ALLOW OUT   Anywhere
465/tcp                    ALLOW OUT   Anywhere
61310/tcp                  ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
22,25,80,443/tcp           ALLOW OUT   Anywhere (v6)
6881/tcp                   ALLOW OUT   Anywhere (v6)
4444/udp                   ALLOW OUT   Anywhere (v6)
443/tcp                    ALLOW OUT   Anywhere (v6)
995/tcp                    ALLOW OUT   Anywhere (v6)
465/tcp                    ALLOW OUT   Anywhere (v6)
61310/tcp                  ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)

I'd add ALLOW OUT UDP 123 to that list so your system gets the correct time from the Ubuntu NTP Server.

You could always be even more secure by restricting POP3S ( 995 ) and Secure SMTP ( 465 ) to the IP address of your mail server instead of 'Anywhere'. Same goes for SMTP ( port 25 ).

Some network functions won't work with this setup such as WHOIS  ( port 43 )and TRACEPATH. ( 44444-44544 ? ). Also Adobe Flash might have problems unless you open port 1935 but using this might expose you to Flash vulnerabilities :-).

If using a shared printer on your network then you might have to open port 631 too ( ALLOW both in and out ). Otherwise keep it closed.
Also maybe open port 5353 ( MDNS ). Although I'm not to sure about this.

Are you using static IP's or are you using DHCP. If using DHCP does it work with this configuration?

---

### Post by PeteAsdf on 2011-11-04
Thanks for the suggestions, SparTacux!

I enabled UDP 123. Flash is working fine even without 1935. 

I'm using DHCP and everything seems to be working OK with this setup. The one thing I noticed so far that's having a little trouble is Ubuntu One- it can't tell me how much space I'm using (gives some connection error message); however it is syncing fine so I'm not too worried. Do you know which port is it the U1 might be missing?

As for specifying IP addresses for the mail servers- I'm using Gmail via Thundrbird- I doubt I would be able to specify a single IP for that(?). I tried to look online for the IP of googlemail.com servers but couldn't find anything relevant.

---

### Post by SparTacux on 2011-11-04
> **PeteAsdf said:**
> Thanks for the suggestions, SparTacux!

I enabled UDP 123. Flash is working fine even without 1935. 

I'm using DHCP and everything seems to be working OK with this setup. The one thing I noticed so far that's having a little trouble is Ubuntu One- it can't tell me how much space I'm using (gives some connection error message); however it is syncing fine so I'm not too worried. Do you know which port is it the U1 might be missing?

As for specifying IP addresses for the mail servers- I'm using Gmail via Thundrbird- I doubt I would be able to specify a single IP for that(?). I tried to look online for the IP of googlemail.com servers but couldn't find anything relevant.

I'd check your UFW logs. If logs are enabled then you will see BLOCKS to port 1935 when using Flash Player ( Not always though - it depends if the content provider use this feature ) . I haven't quite worked out why it's needed as it does SEEM to work ok without. I've not used Ubuntu one but again if I was having problems I'd be looking at the UFW logs to see what ( if anything ) is getting BLOCKED.

---

### Post by BillyBoa on 2011-11-04
Maybe it's the first time I see such a concise explanation of the firewall problem.

---

### Post by SparTacux on 2011-11-04
> **PeteAsdf said:**
> 
As for specifying IP addresses for the mail servers- I'm using Gmail via Thundrbird- I doubt I would be able to specify a single IP for that(?). I tried to look online for the IP of googlemail.com servers but couldn't find anything relevant.

Here's an interesting article about Gmail hack done in Iran. If you are using a Firewall to restrict access to legit email servers then no-one is going to get you with such a hack and get your account and password details and go through your email to see what your political views are.

                                           ARTICLE

Iran has tricked a web firm into issuing fake security certificates for Gmail, Skype, Hotmail and more. 
 Comodo Group, a US-based certificate authority firm with 15% of the market, admitted that one of its affiliate's accounts in Southern Europe had been hacked, letting the attackers create fake SSL security certificates for six websites. 
 Such digital keys let websites offer secure services, and fake versions could be used to spoof sites, gather login details and watch user activity. 
 The fake certificates target Microsoft's Live platform, Gmail and Google, Skype, Yahoo, and Mozilla Firefox extensions. The attack was quickly discovered, with the attacker still using the account when it was shut down.
Comodo's CEO Melih Abdulhayogl said the attack appeared to originate in Iran, as it would have required access to the country's DNS infrastructure. "We believe these are politically motivated, state-driven/funded attacks," he said in a [blog post]("http://www.melih.com/2011/03/23/authentication-layer-for-internet-is-under-attack/"), adding it was the first such state attack he'd seen against the authentication layer of the web.  
 Phillip Hallam-Baker, principal scientist for Comodo, said the timing of the attack was no coincidence. 
 "It does not escape notice that the domains targeted would be of greatest use to a government attempting surveillance of internet use by dissident groups," he said in a [blog post]("http://blogs.comodo.com/it-security/data-security/the-recent-ca-compromise/"). 
 "The attack comes at a time when many countries in North Africa and the Gulf region are facing popular protests and many commentators have identified the internet and in particular social-networking sites as a major organising tool for the protests," he added.

---

### Post by secret resistor on 2011-11-04
> **SparTacux said:**
> If you are using a Firewall to restrict access to legit email servers then no-one is going to get you with such a hack and get your account and password details and go through your email to see what your political views are.


I don't know the specifics of how that particular Iran attack was implemented but in the general case this is **NOT** true. Using DNS is just one possible way of doing this attack and there is nothing stopping the ISPs from implementing a transparent proxy in which case from your end it would look like you are connecting to the real IP address but it will actually go through the malicious server at the ISP which will do the MITM on the SSL connection. And given the potentially grave consequences in this particular scenario I would be very careful not to give people a false sense of security.

---

### Post by SparTacux on 2011-11-04
> **secret resistor said:**
> I don't know the specifics of how that particular Iran attack was implemented but in the general case this is **NOT** true. Using DNS is just one possible way of doing this attack and there is nothing stopping the ISPs from implementing a transparent proxy in which case from your end it would look like you are connecting to the real IP address but it will actually go through the malicious server at the ISP which will do the MITM on the SSL connection. And given the potentially grave consequences in this particular scenario I would be very careful not to give people a false sense of security.

Ok - Don't use the internet ( full stop ) if you want privacy.

The idea was to add more levels of protection - in this context what I said holds true.

---

### Post by secret resistor on 2011-11-04
> **SparTacux said:**
> Ok - Don't use the internet ( full stop ) if you want privacy.

The idea was to add more levels of protection - in this context what I said holds true.

I'm not saying that limiting the IPs does not help - security in layers is always good. I was objecting to this part of your post: "If you are using a Firewall to restrict access to legit email servers **then no-one is going to get you with such a hack**". I interpreted this as meaning that if you restrict the IP addresses then the ISP cannot intercept your traffic which is false and in cases where people's lives are at stake is not a wise thing to be suggesting. If I misunderstood you then I apologize.

---

### Post by Dangertux on 2011-11-04
> **secret resistor said:**
> I don't know the specifics of how that particular Iran attack was implemented but in the general case this is **NOT** true. Using DNS is just one possible way of doing this attack and there is nothing stopping the ISPs from implementing a transparent proxy in which case from your end it would look like you are connecting to the real IP address but it will actually go through the malicious server at the ISP which will do the MITM on the SSL connection. And given the potentially grave consequences in this particular scenario I would be very careful not to give people a false sense of security.

This is true. In this case a firewall wouldn't do much to help you, especially since allowing only select ip's for your mail servers is difficult due to the fact that large providers are load balancing. So you would more realistically be filtering by hostname in which case a MITM would be successful.

In the particular attack the new CA's were pushed out almost immediately, this is why. Since the only real way to mitigate it was to insure the proper warnings were still thrown for non-matching certificates.

---

### Post by SparTacux on 2011-11-04
> **secret resistor said:**
> I'm not saying that limiting the IPs does not help - security in layers is always good. I was objecting to this part of your post: &quot;If you are using a Firewall to restrict access to legit email servers **then no-one is going to get you with such a hack**&quot;. I interpreted this as meaning that if you restrict the IP addresses then the ISP cannot intercept your traffic which is false and in cases where people's lives are at stake is not a wise thing to be suggesting. If I misunderstood you then I apologize.

 I think you are right to pull me up on that. It was probably a bad example to use and I understand the implications of giving a false sense of security on the internet. I stand corrected.   But...   From the write up it appears that the DNS infrastructure was hacked so that users were directed to a spoof site which gleaned their information.  For my mail server I use direct IP addresses so I have no problems resolving mail server names. I did a ping on the mail server and used that IP address. I've Never had any problems with it.

---

### Post by Soul-Sing on 2011-11-06
Not able to insert a rule for msn messaging (pidgin)
and jabber.So that is blocked....
Great howto by the way! :)

edit: is it 5190 for AIM?

---

### Post by OpSecShellshock on 2011-11-06
> **leoquant said:**
> Not able to insert a rule for msn messaging (pidgin)
and jabber.So that is blocked....
Great howto by the way! :)

edit: is it 5190 for AIM?

Looks like the server side port for Jabber is 5222, and for Windows Live Messenger is 1863?

---

### Post by Soul-Sing on 2011-11-06
> **OpSecShellshock said:**
> Looks like the server side port for Jabber is 5222, and for Windows Live Messenger is 1863?

Thanks, but I  don't get the new rules: 43, 5222, and 1863 in the existing "line" of rules, which is:
25,53,80,110,139,143,443,465,843,995,1023,7000,7070/tcp
sudo ufw insert 58 allow out 43 (which is the whois server)
sudo ufw insert 58 allow out 5222
sudo ufw insert 58 allow out 1863
It creates new lines of rules. (Yes i got over 58 lines of rules)

source: [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
> Then block all other outbound traffic with:

```
sudo ufw deny out to any
```

Keep in mind, order of the rules is critical. So if you need to allow additional traffic, you will need to insert a rule.

List your rules by number with:

```
sudo ufw status numbered
```

---

### Post by Ms. Daisy on 2011-11-06
That was a great discussion, explained the basic concepts & made it far less mysterious. Thanks DT.

---

### Post by 1clue on 2011-11-08
+1 for putting the first post on the official Ubuntu documentation.  It's easy to read, it uses references with really good names and doesn't contain any extraneous information.

I don't think I've read anything so simple and concise on the topic, ever.  It's obviously not comprehensive, but it does what it should:  convince people that a firewall isn't a bad idea.

---

### Post by lambcrazy on 2011-11-19
thanks .. i don't know this much about ubuntu . I am trying to install ubuntu . Thanks a lot again ..

---

### Post by candtalan on 2011-11-24
Thanks for this. I had always thought IP tables were actively useful by default.

---

### Post by armorbear on 2011-12-15
Firewall is the which is required for each and every transaction.
there are different types of firewall.The firewall are different for LAN, WAN and MAN.
so according to that you can use the firewall.

---

### Post by UltimateCat on 2011-12-17
Incredibly helpful for a newbie with connection and firewall issue's.

And the golden globe goes to::D

---

### Post by OwnewQuon on 2012-01-28
Always use a Firewall. Within 4 mins of placing my new static IPs on the internet ARP request through Comcast business my IPs were scanned from non ARIN allocated IPs for various vulnerabilities. They dont even have DNS names associated with them yet.Antivirus alone is down to about 12 effectiveness against malware and infection. Its still a must, but your surfing habits and not running Javascript by default noscript on FireFox will go a lot further.

---

### Post by harshgsxr on 2012-02-01
still it is way to safer than windows:)

---

### Post by amilypotter on 2012-02-13
Hie. I am suffering with same problem. Thanks for the great information.
Regards
Amily :)

---

### Post by hildenbrandsteven on 2012-02-13
A firewall can be used for a lot of things... You don't need an anti-virus, but by default Ubuntu doesn't have any ports open... However, sometimes it's good to block apps from accessing the internet, so a firewall can be useful.

---

### Post by nrundy on 2012-02-17
> **Dangertux said:**
> 
 Additionally, in terms of browser security we can take another step by using a browser extension like [NoScript]("http://noscript.net/getit") for Firefox or [NotScripts]("https://chrome.google.com/webstore/detail/odjhifogjcknibkahlpidmdajjpkkcfn") for Chrome. 


NotScripts is a poor performing application and does not provide adequate security. Instead use ScriptNo: [https://chrome.google.com/webstore/detail/oiigbmnaadbkfbmpbfijlflahbdbdgdf](https://chrome.google.com/webstore/detail/oiigbmnaadbkfbmpbfijlflahbdbdgdf)


> **SparTacux said:**
> 
The only thing I'd add to that is the usefulness of Firewall Logs  especially SYSLOG from modem detailing ALL inbound & Outbound  Traffic. Being able to SEE ( in Real-Time ) what is happening greatly  adds to overall security.

This is where Ubuntu is seriously lacking compared to Windows and Mac. Ubuntu can't even create a log of what applications attempt to make internet connections.

---

### Post by CivilizationII on 2012-02-17
> **Dangertux said:**
> I am writing this because the previously posed question is asked consistently on this forum. I am hoping that I can create something of a generally accepted answer that contains all the necessary links to appropriate resources. 


 So the question posed : Do I need a Firewall for Ubuntu?
 

 (...)


Your post is very interesting, but you don't cover the case of an external firewall/router, which is the standard for any company seriously involved in security.

---

### Post by nrundy on 2012-02-17
> **CivilizationII said:**
> Your post is very interesting, but you don't cover the case of an external firewall/router, which is the standard for any company seriously involved in security.


He covers routers, look here:

> **Dangertux said:**
> 
 _**Well, I'm behind a NAT router so none of this is for me, right?**_
 

 Wrong again. A NAT router is a great addition to your security, but as  I've been enforcing throughout this post, that there is no catch all  solution.  
 

 A NAT router will prevent a service from being bound and accessible  from the Internet. That being said, it works a lot like strong inbound  only rules as we discussed earlier in this post. It does not provide  protection against methods like a reverse connection designed to bypass a  firewall. Another important thing to note is that the NAT router's  protection is not host based. So if another machine on the network with  yours is compromised the NAT router will offer your machine no  protection.  
 

 When used in conjunction with the other topics we've discussed in this  post a NAT router is an excellent hardening measure, however as a stand  alone solution it is lacking in many ways.
 


---

### Post by Dangertux on 2012-02-17
> **CivilizationII said:**
> Your post is very interesting, but you don't cover the case of an external firewall/router, which is the standard for any company seriously involved in security.

Well -- this can become an extremely in depth discussion very quickly, but I'll try to hit the high points for you briefly.  The first thing to understand about the original post is that this is meant for the use case of a home user or small - mid size company. Which by and large is the vast majority of use cases particularly as far as Ubuntu is concerned. In terms of large enterprises you are right, they do use external firewalls and routers, they also rarely use (only) host based firewalls. Another thing that is true of large enterprises is they RARELY use Ubuntu, the bottom line is it's just not stable enough yet for most production shops to put any serious thought into, and some of the larger scale enterprise tools aren't there yet. That , though is a discussion for a different thread.

By and large if you're simply talking about standard firewalling and ACLs (not IPS, I'll get into that in a moment). You have to major factors to deal with when dealing with a large enterprise network. This is obviously taken from the perspective of an external attacker, so there may be limited if any internet facing systems. Which is where client side attacks come in, social engineering etc...  In most cases if the methods discussed in the original post are carried out properly, IE a reverse shell, it will still bypass most corporate firewalls. NAT routing is NAT routing, and if the machine internal to the router has access out , an attacker can get a shell back. That being said, most CCNE's are rather clever (or so they think) and like to do things like IP whitelisting, and port whitelisting. Two things on that.

- Most client side systems (not production systems unless it's something like a globally accessible webserver) will have access to the Internet, so pretty much every IP is fair game when it comes to whitelisting. 

- Ports... Okay, even if you block the obvious outbound on 7777 , you're not blocking (can't block) 53 UDP , and probably aren't blocking 53 TCP (zone transfers and large DNS requests). 


When you get more in depth and start talking about IPS you need to get more creating to bypass them. You start getting into things like encoding payloads to evade IDS/IPS and staged payloads. Most of these will effectively bypass even the best enterprise class IPS solutions if carried out properly (IE: your payload isn't signatured) now...If you toss back a reverse netcat or an unencoded meterpreter, you probably won't have a whole lot of success with a decent IPS. Though, some older appliances won't pick them up.

Hopefully this helps, but by and large the basic principles in the original article will scale quite well to any size network, bearing in mind that you would be attacking an internet facing system or data management zone.

---

### Post by nrundy on 2012-02-18
> **Dangertux said:**
> In terms of large enterprises you are right, they do use external firewalls and routers, they also rarely use (only) host based firewalls. Another thing that is true of large enterprises is they RARELY use Ubuntu, the bottom line is it's just not stable enough yet for most production shops to put any serious thought into, and some of the larger scale enterprise tools aren't there yet. 

Dangertux, do large enterprises use RHEL? Is RHEL stable enough for Enterprise use? I thought Ubuntu LTS was equivalent to RHEL in terms of stability. Is RHEL more stable than LTS?

---

### Post by Dangertux on 2012-02-18
> **nrundy said:**
> Dangertux, do large enterprises use RHEL? Is RHEL stable enough for Enterprise use? I thought Ubuntu LTS was equivalent to RHEL in terms of stability. Is RHEL more stable than LTS?

I work for a large corporation we use RHEL, AIX, and Solaris as well as Windows server.

We dont use debian or Ubuntu . For a lot lf reasons. The main being that RHEL is the industry stabdard in terms of stability and support. Also bleeding edge distros like Ubuntu tend to be avoided in production shops.

If you are interested in learning more about businesses that do use Ubuntu or Debian, I know that on the west coast they are becoming pretty popular with small to mid size 
companies.

Hope this helps

---

### Post by nrundy on 2012-02-18
> **Dangertux said:**
> yet for most production shops to put any serious thought into, and some of the larger scale enterprise tools aren't there yet. 

Does RHEL have "larger scale enterprise tools" that Ubuntu doesn't have? Or is RHEL used primarily just because it's super stable and is the industry standard? I'm assuming that tools available on Linux would be available to all the distros.

Fedora is at 16 currently. Do you know what version number RHEL is at now if it was loosely compared to a Fedora version? Like is RHEL roughly equivalent to Fedora 10?

---

### Post by Bucky Ball on 2012-02-18
> **Dangertux said:**
> Also bleeding edge distros like Ubuntu tend to be avoided in production shops.



Even LTS releases? I understand where you're comin' from, Dangertux, but just curious about your thoughts. Know I'm a tad off track, but ... ;)

PS: Shame that Win is like a leaky bucket so RHEL and a million other things need to be there in the first place for big corps using both. Catch 22/28 I guess. The story is never ending, that I understand also ...

---

### Post by Dangertux on 2012-02-18
To answer both questions RHEL does have some pretty spiffy tools for enterprises. things like kickstart, satellite server, red hat virtualization, tight integration of jboss etc.

That being said, Ubuntu does have some similar tools. Landscape, tighter cobbler support in 12.04 etc. The LTS versions are more stable, but Ubuntu is the new kid on the block, and when corporations have been using RHEL for 8 or more years its going to  be hard to push a conversion. You can make the finance argument but a few thousand dollars for RHEL entitlements is a drop in the bucket for companies like that  

As far as Windows goes it can be rather successful in a corporate environment and there is no better MTA than Exchange so you get kind of stuck there

Hope thus helps

---

### Post by mraandtux on 2012-03-16
Firewall on Ubuntu? No if you want to use it like normal user, Yes if you afraid of privacy very much.

---

### Post by raja.genupula on 2012-03-16
well while coming to my opinion having Firewall is a best thing even though we are not a user who does sensitive things on the computer , because we are in web .

---

### Post by ubunbu on 2012-03-19
Thanks for this, I remember when I first discovered Ubuntu in 2008 I was consumed with the desire to secure it. I'm not sure why and for my needs it was technically overkill. All the time I would see people saying "Ubuntu is secure by default" "There's no ports open so a firewall is redundant." I didn't think that made sense as there is no such thing as redundant security, it will almost always just mean more secure. So basically, ha-ha-ha to those people ;)

---

### Post by roffisserver on 2012-04-06
Firewalls of definitely necessary. I made a custom firewall for my server. It is great! I had a friend try to hack into it, he failed :p!

---

### Post by BitShark on 2012-04-27
What do you lose by implementing a few firewall rules? A few minutes of your life? Minimal processor cycles? Not much really when you consider how much you value your data and all that might be associated with it.

---

### Post by Johnny3 on 2012-05-12
I just have a desktop PC and I use this site to set up mime.
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

All I use is sudo ufw enable and sudo ufw default deny. I known I could do more but this is OK for me and better than what most people that us windows default fire wall. 
Thanks and God Bless Johnny3 65+++

---

### Post by IronArjen on 2012-05-30
Great post, really good introduction for laymen like me.

So how about if you want to have remote access? I have a small network with a powerful machine that I would like to access from where ever I am, as well as that I need it open for some my co-workers that work elsewhere. Would there be anything special to do? Use special settings in the UFW or install an additional thing?

I feel like including somehow the MAC address, then it would be dependent on the machine not the IP I have in a hotel.....

---

### Post by 1clue on 2012-05-30
In IPV4 the mac address is local network only.  The MAC address isn't mapped to anything in a normal IPV4 packet.

In IPV6 the original spec used the mac address because the IPV6 address space is plenty big enough to use that as a key.  Privacy advocates poo-poo'd that (rightfully so IMO) so even there it's not a reliable key.

IMO the remote access thing is no big deal.  You open a port on your external hardware, then send that to a specific IP and a specific port inside.

The more layers you can get the better within reason, and it's best for small office/home office (SOHO) routers to have completely separate hardware so you're positive no software flaws let the bad guys get around some security flaw.  I have the cable modem plus 2 completely separate routers, the "inside" one having the radios turned off so it's much more secure.

For me, my inside network has no penetration from the outside.  I can connect out on a few ports, but nothing outside can initiate a connection in.

The key to remember here is to enable what MUST be there, and deny everything else.  If you turn on a service, make sure you understand what that service is and know what its weaknesses are.

---

### Post by youknowme on 2012-06-08
Humm - seems a bit paranoid to me. Script kiddies would not know how to bypass my router even if they had the admin password to it.  If a serious attacker really wanted to get you, they would probably get you regardless with some zero day exploit.

I think a firewall is good if you have the time to configure / understand it. But how far do we take security? IDS, snort, tripwires, reading logs every day??? Router security is often enough for a home user IMHO - But this was a jolly good thread.

---

### Post by 1clue on 2012-06-08
Every security measure seems a bit paranoid until you get owned for not implementing it.

So really what you need to ask is, what's more valuable:  The time to set up decent security, or the value of everything you keep on your computers at home, the ability to do everything you do with them, the value of whatever is in your bank accounts that you access online, and/or whatever might be seen or heard when they turn on your webcam(s) without your knowing it.

It's up to you really.

---

### Post by youknowme on 2012-06-10
> **1clue said:**
> Every security measure seems a bit paranoid until you get owned for not implementing it.

So really what you need to ask is, what's more valuable:  The time to set up decent security, or the value of everything you keep on your computers at home, the ability to do everything you do with them, the value of whatever is in your bank accounts that you access online, and/or whatever might be seen or heard when they turn on your webcam(s) without your knowing it.

It's up to you really.

You seem to miss the point i am making. What you call 'decent security' implemented by your firewall is an illusion. A real cracker - NOT a script kid, would not really be challenged. How long do you think it would really take for a group of (for example) state sponsored ultra smart Chinese hackers or secret intelligence services to 'own' your home pc - if that was their intention? Firewalled or not? 

Btw - if my webcam is switched on, a bright blue light illuminates!:lolflag:

---

### Post by 1clue on 2012-06-11
> **youknowme said:**
> You seem to miss the point i am making. What you call 'decent security' implemented by your firewall is an illusion. A real cracker - NOT a script kid, would not really be challenged. How long do you think it would really take for a group of (for example) state sponsored ultra smart Chinese hackers or secret intelligence services to 'own' your home pc - if that was their intention? Firewalled or not? 

Btw - if my webcam is switched on, a bright blue light illuminates!:lolflag:

No I'm not missing your point.  Yes, somebody who was truly skilled could probably get in no matter what you tried, especially since the US military can't seem to keep the bad guys out.  But those guys are mostly interested in bigger fish.

A good setup has multiple layers of security, generally on multiple physical machines.  Several layers of mediocre security CAN BE better than a single layer of good security.  The idea is to block any single compromised device from easily getting information out in an unconventional fashion.

The biggest mistake you can make is to leave your device running with the default configuration, or to leave it with mostly default settings.  That sort of thing enables a black hat to "profile" your lax settings, correctly assuming most people take it out of the box, plug it in and leave it alone.

Web cam:  A good share of web cams have no light, and a good share of the ones that do have the light have a separate software switch to turn on the light which is independent of the one to turn on the camera.  They SHOULD all have a light, and they SHOULD all have the light wired to the same switch as the camera, but assuming yours is wired that way is a really dangerous mistake.

---

### Post by samiux on 2012-07-05
> **youknowme said:**
> Humm - seems a bit paranoid to me. Script kiddies would not know how to bypass my router even if they had the admin password to it.  If a serious attacker really wanted to get you, they would probably get you regardless with some zero day exploit.

I think a firewall is good if you have the time to configure / understand it. But how far do we take security? IDS, snort, tripwires, reading logs every day??? Router security is often enough for a home user IMHO - But this was a jolly good thread.

I don't think script kiddies, they may have different level of skill, cannot bypass your firewall or router.  

Intruder can attack your box not only by using zero day exploit.  They have many methods to do so.  They can bypass IDS/IPS, Anti-virus, firewall and WAF.  Please don't look them down or you may felt a great regret.

Intruder attacks home users for many reasons.  Sometimes, they do that are not for stealing data or money.

How about intruder captures images from your webcam when your webcam is turned on.

---

### Post by foobantu on 2012-07-09
Hi,

Thank you Dangertux for such an informative article.

There were many things I had taken for granted, but your article has really made me aware.

Thank you once again.

---

### Post by nothingspecial on 2012-07-09
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12088432#post12088432](http://ubuntuforums.org/showthread.php?p=12088432#post12088432)


Support threads regarding the wiki and it's content should be created in a suitable forum.
__________________

---

