---
title: "File and Proxy Server"
date: 2009-11-06
forum: Server Platforms
---

### Post by X1R1 on 2009-11-06
Hello all. I have a question regarding setting up ubuntu as a file server (using samba) and as a Proxy Server (transparent proxy).

Currently at work, we have a proxy server (Microsoft Proxy Server, completely obsolete) running that every machine connects trough. On every machine at work you have to manually set up the proxy Ip and port in order to access the internet. Also the file server is allocated on this same machine.

What I want to do is to setup an Ubuntu File and Proxy server instead of the one we currently have, BUT I have to first prove that everything works so that the change can be made, so here is the deal:

- how do I setup another proxy server so that if I remove the proxy settings from a workstation, it picks up the ubuntu proxy (which will be transparent) and connect trough it?

-What do you think its the best guide to setup a samba file server on a windows network?

I wanna have this file server on the ubuntu machine also, and running with clamav checking files continuously and mail (smtp) checking.

My goals:

-I want to prove a simple and FREE OPEN SOURCE setup can be far more efective than a lousy microsoft one.

-I want to avoid the hassle of getting calls everytime someone internet fails because they remove/changed the poxy settings we have at the moment.

Hopefully with your help I can achieve that and more :D

PS: Whats the best ubuntu server version for doing this?
PS2: Please give detailed instructions as I dont have vast knowledge of ubuntu server installs.

Regards and thanks in advance :KS

---

### Post by madverb on 2009-11-06
Check out ebox. I've deployed it at a few places as a proxy/fileserver.

Works damn well and it's development over the past year have been incredible.

Support is pretty decent too.

It is built on top of Ubuntu Server and is in the repositories.

[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by X1R1 on 2009-11-06
Can I configure that with the current proxy we have (the microsoft one) still working? I mean, like having 2 proxy servers working at the same time, one with manual configuration (the microsoft one) and the other with the auto-conf (ebox)?

---

### Post by Thirtysixway on 2009-11-06
I don't know what you're doing with the proxy, if it's filtering you may want to look at openDNS.  Makes it very easy to control filtering etc.

I'd go with Ubuntu server 8.04.  Since it's in a business, you'll want stability and security updates for the next 4 years instead of 18 months with 9.10.

Not knowing how your current proxy server is setup exactly, is it possible to just change IPs of the server?  That way the Ubuntu server takes over the old microsoft IP and all the client machines stay configured correctly.  Behind the scenes change that nobody should notice.

---

### Post by X1R1 on 2009-11-06
> **Thirtysixway said:**
> I don't know what you're doing with the proxy, if it's filtering you may want to look at openDNS.  Makes it very easy to control filtering etc.

Only thing current proxy does is being a pain in the *** and blocking things it SHOULD NOT block. But indeed I want to setup filtering on the ebox/new proxy. 

> **Thirtysixway said:**
> Not knowing how your current proxy server is setup exactly, is it possible to just change IPs of the server?  That way the Ubuntu server takes over the old microsoft IP and all the client machines stay configured correctly.  Behind the scenes change that nobody should notice.

Your approach is what I would do if I was 100% sure it going to work correctly and that would require me to have experience doing it (which I lack :lolflag:).

So, I was wondering If I could add this ebox server to the network with a different IP and configure it to require no client-side configuration, that way I could test it (with manual settings-> current proxy, dinamic settings -> ebox)

Also, I think I was misusing the term, by "transparent proxy" I meant a proxy configuration that did not requires client configuration (I want to avoid configuring all clients manually, there are 50+ computers and its practically myself doing all the work:popcorn:

---

### Post by madverb on 2009-11-08
A transparent proxy just means the proxy runs on port 80 and 443 and not on a different port that requires reconfiguration on the client computers.
If there is Domain Controller's in place you could just set the proxy settings in group policy to point to the ebox server.

---

### Post by koenn on 2009-11-08
> **madverb said:**
> A transparent proxy just means the proxy runs on port 80 and 443 and not on a different port that requires reconfiguration on the client computers.
If there is Domain Controller's in place you could just set the proxy settings in group policy to point to the ebox server.

YOu're right about GPO being the easiest way to set proxy config for clients.

But a transparent proxy is more than changing the port your proxy listens on  : that's not going to do any good if the clients attempt to connect directly to oitside servers; they'll never reach the proxy unless you have a firewall redirecting this traffic towards the proxy. So a transparent proxy is usually implemented as a proxy server + the default gateway doing REDIRECT / DNAT (eg with iptables) 

@OP
besides GPO and transparent proxying, you should also look up PAC and WPAD. Wikipedia is a good place to start for those.

---

### Post by kewlrichie on 2009-11-08
Well I can help out with the proxy part. I just recently did this twice and currently use it in a production environment and works very well. First of all I mainly installed this proxy with the main reason of using it for web filtering/virus scanning with Dansguardian (which is a great piece of software) so this will have settings regarding that setup, but could also not be used. Let me also mention there is this guide that will do auto proxy detection at [http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

but i chose to do a transparent proxy. I am just going to be brief on what i did but if you have any questions or need more details be sure to contact me with any questions you might have and I am also going to do a guide and submit it to howtoforge...maybe I'll start tomorrow at work..will see

I installed squid 

```
apt-get install squid
```and added transparent to the end of the http_port section of squid.conf

```
http_port 3128 transparent
```restart squid ```
/etc/init.d/squid restart
```Also it is always good practice to only allow localhost access to squid directly if you are using dansguarding for filtering this is so users cant bypass the filter in a browser and type the proxy IP with the squid port of 3128 and not get any filtering by doing this and make sure its above the deny all statement

```
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

```So if your not planning on using dansguardian you need need to allow your localnet acl in squid.conf whatever it may be.

```
acl localnet src 192.168.0.0/16
```then make sure you give it access. make sure its above http_access deny all

```
http_access allow localnet
```I installed Dansguardian (which now has antivirus scanning for files being downloaded using clamav)

```
apt-get install dansguardian
```edit /etc/dansguardian/dansguardian.conf and make sure filter port is set to 8080

```
filterport = 8080
```and proxy port is set to 3128

```
proxyport = 3128
```now for the transparency magic. This will listen for all traffic from port 80 (web traffic) on the 192.168.1.0 network and redirect it to port 8080 which will get filtered through dansguardian then that will be passed off to squid on port 3128 for the proxying.

```
iptables -t nat -A PREROUTING -i eth0 -s 192.168.1.0/24 -p tcp --dport 80 -j REDIRECT --to-port 8080
```If you weren't using filtering you would of course just forward it to 3128 instead of 8080

```
iptables -t nat -A PREROUTING -i eth0 -s 192.168.1.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128
```Also VERY IMPORTANT this gave me headache for a few days there is IP forwarding that has to be setup or your users wont be able to access SSL/HTTPS sites. Set ip_forward to 1 like this.

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```I also made a script that runs at start up and flushes iptables and sets everything up again just in case something goes wrong. (optional of course) 

```
#!/bin/bash
# /etc/set-iptables-script
# iptables script for rerouting all port 80 web traffic to port 8080 for web fitering using transparent proxying
# also settings ip_forward to 1 for HTTPS/SSL traffic to be handed over to squid

# Shell "debug" on
set -x

# Flush all firewall and NAT rules
iptables -t filter -F
iptables -t nat -F
iptables -t mangle -F
iptables -t raw -F

# Delete  user defined chains
iptables -X

# Define default policies
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

# Allow all locally
iptables -t filter -A INPUT -i lo -j ACCEPT
iptables -t filter -A OUTPUT -o lo -j ACCEPT

# Activate IP FORWADING (to allow HTTPS/SSL to be passed through to squid, otherwise HTTPS/SSL will NOT work!)
echo 1 > /proc/sys/net/ipv4/ip_forward

# Re-route port 80 (web traffic) to 8080 (dansguardian) for web fitlering and virus scanning
iptables -t nat -A PREROUTING -i eth0 -s 192.168.1.0/24 -p tcp --dport 80 -j REDIRECT --to-port 8080
```Now i chose to go this way cause i also use DHCP on this server and I can choose what gateway to give users. I could give a user no filtering at all and send them out the normal gateway 192.168.1.1 or users that I need filtering on all the time I can change their gateway to the ip address of the proxy/filtering server eg: 192.168.1.2 and they will be forced to use the proxy server whether they like it or not. You can also setup groups in dansguardian to allow certain groups to restricted access or full access etc but that's a whole another story but still pretty easy to do.

Anyways that was a quick overview what i did and it works very very well and pretty easy to setup.

Thanks for reading
Rich

---

### Post by X1R1 on 2009-11-09
sorry about the late reply, had some matters to attend to and didnt have time to log in the forums.

Amazing insights, I have heard about squid before, but I read somewhere that its pretty hard to get it to work, but with your guide it doesnt seem that hard. And about the domain controller, we do have one setup here so it is just a matter to change the proxy server address in group policy????

---

### Post by kewlrichie on 2009-11-15
as for a domain controller you can either do Windows NT style domain controller (PDC) with samba 3 and you can checkout these links [http://www.opensourcehowto.org/how-to/samba/openldap-lam-samba-as-pdc.html]("http://www.opensourcehowto.org/how-to/samba/openldap-lam-samba-as-pdc.html") and [http://www.opensourcehowto.org/how-to/samba/samba-primary-domain-controller-with-group-policies.html]("http://www.opensourcehowto.org/how-to/samba/samba-primary-domain-controller-with-group-policies.html") it will show you how edit group polices manually then you can store it on the linux PDC and it will apply those settings to 2000/XP style computers. Then there is Samba 4 is very very new but that will be a active directory style domain controller like Windows 2000/2003. [http://wiki.samba.org/index.php/Samba4/HOWTO/Ubuntu_Server_9.04]("http://wiki.samba.org/index.php/Samba4/HOWTO/Ubuntu_Server_9.04") and [http://wiki.samba.org/index.php/Samba4/HOWTO]("http://wiki.samba.org/index.php/Samba4/HOWTO")

Theres alot of info there but you should be able to get something out of that. if you just need simple authentication with alittle group policy stuff i would stick with samba 3 PDC style. Its been around for a while and you will be able to get alot of support.

---

### Post by X1R1 on 2009-11-15
but the domain controller is in another server, at least I wont change that at the moment, just proxy and file server for the time being, but I plan on the near future to setup everything in the ubuntu server.

---

### Post by kewlrichie on 2009-11-16
Sorry i believe I misread your post wrong. When I seen Domain controller I thought you were also trying to build a Linux PDC. If your using your current dc you should be able to setup proxy information via group policy for the browser, but you said you want to do transparent proxying/filtering...I'm not too sure about specifying a gateway through GP. I would think that would be done through DHCP, atleast that's the way I do it

---

### Post by X1R1 on 2009-11-16
Let me elaborate a little to explain things further. Currently, We have a proxy server, file server, some work specific programs and and domain controller with microsoft windows server. What I want to do is to take out the proxy and file server from this server into the ubuntu one, to speed up connections and setup webfiltering (currently we dont have any).

Also I want to avoid having to manually configure the proxy settings on each machine.

The help provided here have been very helpfull so far, I just wanted to clear things up a little.

---

### Post by kewlrichie on 2009-11-17
I think this still shouldn't be too hard. You might want to also checkout this guide which will show how to setup a samba file server with intergratiom into your existing active directory to check for users and groups [http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory]("http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory") As for forcing everyone to use the proxy the easiest way i can think of is doing it through DHCP specify everyone to use the proxy IP as there gateway, when you get squid/dans/iptables part setup of course.

Do you want everyone to use thr filtering or will some users be unfiltered like the boss or user that need full access to the Internet?

See at my job I leave some people that I can trust unfiltered by giving them our normal gateway out to the Internet and for eveyone else that is filtered I put together a small cronjob to open certain site catagories during lunch hours (like facebook etc) and closes when lunch is done. I could of make it easy and force everyone through the proxy and setup dansguardian groups and choose which users could get what because I also have squid doing some bandwidth throttling so even if everyone gets on web and starts streaming videos at lunch I will never fully max out my bandwidth. Also would be easier on me because if everyone is forced through the proxy dans also does virus scanning and block file types like exes etc...

So if I had to do it again I would probably force all users through the proxy and setup groups in dans to give certain users more access then others. 

I don't remember if DHCP on windows server let's you specify different gateway, i've always used Linux dhcpd-server, so i'm not too sure about that part

sorry if this sounds a bit choppy I'm typing on my iPhone and it's late :)

---

### Post by X1R1 on 2009-11-17
wow, about half the things you said there I tought they were impossible to do using only a linux server (LOL), and yeah, some people will have less/no filtering so I would indeed need to setup groups for them. Also, another thing to consider, how much processing power will I need for this? I am guessing not much because Im not putting to many services on it, but on the other side, webfiltering and file/virus checking can get very resource intensive. I want to provide this service for 44 computers after its completely tested on a smaller field (like 15comps). 

So, will a normal computer be able to handle this? by normal I mean a standard workstation.

---

### Post by X1R1 on 2009-11-17
wow, about half the things you said there I tought they were impossible to do using only a linux server (LOL), and yeah, some people will have less/no filtering so I would indeed need to setup groups for them. Also, another thing to consider, how much processing power will I need for this? I am guessing not much because Im not putting to many services on it, but on the other side, webfiltering and file/virus checking can get very resource intensive. I want to provide this service for 44 computers after its completely tested on a smaller field (like 15comps). 

So, will a normal computer be able to handle this? by normal I mean a standard workstation.

---

### Post by koenn on 2009-11-17
> **X1R1 said:**
> 
So, will a normal computer be able to handle this? by normal I mean a standard workstation.

how old a computer / what sort of computer in terms of ram and CPU ?

---

### Post by X1R1 on 2009-11-17
Probably a pentium 4 with 1 GB of ram or so, it what I have available at the moment, but I can upgrade it if its needed. If that doesnt cut it in terms of CPU and RAM can you suggest  some PC to get/assemble?

---

### Post by koenn on 2009-11-17
It'll work, I think.
See how it feels and behaves (eg run 'top') while you're testing with 15. 

For a file server, your network and disk throughput will be a bottleneck long before RAM or CPU becomes an issue.

Squid is quite efficient, even with (simple) accesscontrols.

virus -and content filtering might be a bit of a challenge, 
and of coures the baviour of your users is also a factor : if they all start copying massive amounts of files from and to your file server and doing full text searches on the shares, while doing some extensive web surfing to kill the time, your server might not always keep up with them

---

### Post by X1R1 on 2009-11-26
I have an update on the machine I will use. Will be a Dell Poweredge 500SC server. Currently it haves only 256mb memory but I will buy the memory upgrades to 2 Gigs pretty soon.

This server comes with a Pentium III@1Ghz, will this be enough?

---

