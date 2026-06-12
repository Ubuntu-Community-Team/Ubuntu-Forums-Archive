---
title: "Basic iptables question"
date: 2010-08-03
forum: Security
---

### Post by baguahsing on 2010-08-03
As I am still new to linux, I have been reading about iptables.  When using --dport you can specify a port number or a protocol.  If I use:
 
code:
 iptables -A INPUT -p tcp --dport ftp -j ACCEPT
 
 will this open all designated ftp ports (20,21)?  Would it be best to designate each port by number rather than use the protocol?

---

### Post by The Cog on 2010-08-03
It turns the name into a number using the file /etc/services.
According to this, ftp is port 21, and port 20 is ftp-data.

---

### Post by bodhi.zazen on 2010-08-03
> **baguahsing said:**
> As I am still new to linux, I have been reading about iptables.  When using --dport you can specify a port number or a protocol.  If I use:
 
code:
 iptables -A INPUT -p tcp --dport ftp -j ACCEPT
 
 will this open all designated ftp ports (20,21)?  Would it be best to designate each port by number rather than use the protocol?

You may specify multiple ports with multiport. Saves on the typing.

You open a port by installing (and starting) a server, such as FTP.

Iptables does not open a port, it restricts access to a port (or not). Most people deny everything and then allow desired ports (http, ftp, etc) in iptables.

---

### Post by baguahsing on 2010-08-03
Thanks for both responses.  I guess that I should have used http as my example.  Looking up the ports on wikipedia, I noticed http had several alternated ports listed usually associated with some other program.  I was wondering if I wrote --dport http would it open just port 80 or could some of the alternated listed ports be opened as well.  Sorry if I seem a bit noobish, just trying to learn.

---

### Post by baguahsing on 2010-08-03
After reading your response a couple of times, bodhi.zazen, am I understanding you correctly that iptable allows a port to be opened, but it must be opened by a service ie server, browser, or irc?

---

### Post by bodhi.zazen on 2010-08-03
I think we have a failure to communicate =)

1. You open a port, say 80 for http, by installing a web server and then starting the web server.

2. You may then use iptables to restrict access to the port. Again this is admittedly a bit of semantics, but it is an important point.

By default , in Ubuntu, iptables is permissive and allows connections. You would then be configuring iptables to block some and and allow other connections.

3. In terms of your question, The Cog already answered your question.

There is a file on your computer, /etc/services

iptables uses that file to translate what you tell it.

So when you say 

--dport http  iptables looks in /etc/services and sees http == port 80

Try :

```
grep ^'http ' /etc/services
```If you grep http

```
grep http /etc/services
```Those are other services. For example, you will see https , port 443

--dport http allows only port 80
--dport https allows only port 443

--dport http-mgmt allows only port 280

and on ...

You should, IMO, think of opening and closing ports as installing and then starting / stopping servers.

I know it is semantics ;)

---

### Post by baguahsing on 2010-08-03
I humble myself before the Ubuntu guru.  LOL. Thanks for your response.  The light has come on and I understand.  Sometimes an old dog can learn new tricks.  On a serious note, do you recommend blocking responses to ping requests?  I am on a laptop which means I normally use wireless at home behind a router and its firewall.  If I go to a wifi hotspot, are there additional things that I should consider in developing my iptables?

---

### Post by bodhi.zazen on 2010-08-04
> **baguahsing said:**
> I humble myself before the Ubuntu guru.  LOL. Thanks for your response.  The light has come on and I understand.  Sometimes an old dog can learn new tricks.  On a serious note, do you recommend blocking responses to ping requests?  I am on a laptop which means I normally use wireless at home behind a router and its firewall.  If I go to a wifi hotspot, are there additional things that I should consider in developing my iptables?

IMO responding to ping is not that big a deal.

IMO, when I connect to an untrusted network (usually wireless) I advise two things ;

1. Activate UFW, the defaults are sufficient 

```
sudo ufw enable
sudo ufw default deny
```2. Do not perform any financial transactions or log into any web sites over http. Financial institutions will use https, which encrypts the traffic and is sufficient. If you must log on to a site (http, ftp, etc) tunnel the traffic over ssh or a VPN.

For example : [Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html")

---

### Post by baguahsing on 2010-08-04
Thanks bodhi, I have one last question which will be off topic and I will mark this post as solved.  In your security sticky, and your hids / nids guides you use apache either as a  dependency or mail reports.  I have an older laptop, P4 1.8GHz,& 1Gb ram, will the apache server eat up too much of my resources?  I am running the 10.04 netbook remix with a standard fresh install with no servers running.

---

### Post by wacky_sung on 2010-08-05
> **bodhi.zazen said:**
> I think we have a failure to communicate =)


```
grep ^'http ' /etc/services
```If you grep http

```
grep http /etc/services
```Those are other services. For example, you will see https , port 443

--dport http allows only port 80
--dport https allows only port 443

--dport http-mgmt allows only port 280



Is grep http /etc/services is also part of the iptables command?Any reference which i can read about it.Thank

---

### Post by bodhi.zazen on 2010-08-05
> **baguahsing said:**
> Thanks bodhi, I have one last question which will be off topic and I will mark this post as solved.  In your security sticky, and your hids / nids guides you use apache either as a  dependency or mail reports.  I have an older laptop, P4 1.8GHz,& 1Gb ram, will the apache server eat up too much of my resources?  I am running the 10.04 netbook remix with a standard fresh install with no servers running.

Apache is used to access web interfaces, namely base (snort) and the OSSEC web interface. IMO the web interfaces are helpful.

Both snort and OSSEC may be a bit of overkill for your setup, but you have sufficient resources if you wish to try it. If you install Apache, bind it to localhost or restrict access via iptables.

Personally I find the emails annoying, I always check the logs or the web interface with some regularity. Therefore I almost always disable the email options for HIDS and NIDS.

---

### Post by bodhi.zazen on 2010-08-05
> **wacky_sung said:**
> Is grep http /etc/services is also part of the iptables command?Any reference which i can read about it.Thank

Not sure what information you want exactly.

grep is it's own command and I posted the command to demonstrate the contents of /etc/services

/etc/services is a local listing of default ports used by servers.

See:

[http://www.codecoffee.com/tipsforlinux/articles/25.html](http://www.codecoffee.com/tipsforlinux/articles/25.html)

---

### Post by wacky_sung on 2010-08-06
Thank Bodhi :D

---

