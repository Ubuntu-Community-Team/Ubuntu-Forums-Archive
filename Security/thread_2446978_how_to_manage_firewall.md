---
title: "how to manage firewall"
date: 2020-07-10
forum: Security
---

### Post by goodstuff9 on 2020-07-10
I want to set up my firewall to start with by allowing all outgoing, but block all incoming.  

However, I *think* I have applications installed that require ports to be open for some incoming.  

I'd rather not just wait to see what doesn't work to find that out.  How can I go about determining which ports each application is designed to depend on being open?  

Also - When installing a new application, how can I know which ports it may depend on being open?

---

### Post by The Cog on 2020-07-10
> When installing a new application, how can I know which ports it may depend on being open? 
Read about it - check the documantation, google for it perhaps. That's the only way to know before you install it what an app will do.
> How can I go about determining which ports each application is designed to depend on being open? 
You can tell what ports an application is listening on once it is running by looking to see what ports it actually has open. This command will list all listenoing ports:
```
sudo ss -lntup
```

---

### Post by goodstuff9 on 2020-07-10
Thanks for the reply, I appreciate it.  

I ran the command you suggested.  

I think I'm going to have to throw in the towel, and just give up on firewall security in Linux.  

I had about four screens full of ports that I'd have to open up.  (Yes, all the applications I could recognize running were things that should be running.)  

I didn't even have all applications running; and, I know enough to realize that many applications can choose from among several ports.  This firewall management just seems far too onerous for the common user.  I don't want to spend all my time the next few weeks playing whack-a-mole - "whack-a-port"? - constantly trying to chase down additional ports I didn't realize needed to be opened up for a commonly used application.  

Add on top of that your advice that, when installing a new application, I would need to do internet research to figure out the ports it might need....  Now I'm afraid that I'd be moving from the computer existing for me, to me existing for the computer.  

I am not being critical of you, I appreciate hearing the truth - even if it is an unpleasant truth.  

Unless someone can explain how there'd be an easier way to approach this?????

---

### Post by SeijiSensei on 2020-07-10
Install nmap.

```
sudo apt install nmap
```

Now scan the localhost port on your machine and see what ports nmap reports as open.

```
sudo nmap localhost
```

You need to run nmap with sudo to do most scans beyond simply pinging the hosts on your network.

If your server also has a public facing IP address, you can run an nmap scan against it from here:  
[https://hackertarget.com/nmap-online-port-scanner/](https://hackertarget.com/nmap-online-port-scanner/)

Show us one or both lists inside of [noparse]```

```[/noparse] tags, and we'll go from there.

---

### Post by goodstuff9 on 2020-07-10
Thanks for your help.  I post the results here.  But....  Now I'm confused, this list is FAR shorter than the list produced by the ss -lntup command......  

```
Starting Nmap 7.60 ( https://nmap.org ) at 2020-07-10 14:13 CDTNmap scan report for localhost (127.0.0.1)
Host is up (0.000017s latency).
Not shown: 982 closed ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
631/tcp   open  ipp
1025/tcp  open  NFS-or-IIS
1042/tcp  open  afrog
2049/tcp  open  nfs
3689/tcp  open  rendezvous
5054/tcp  open  rlm-admin
5900/tcp  open  vnc
8000/tcp  open  http-alt
8080/tcp  open  http-proxy
8085/tcp  open  unknown
9050/tcp  open  tor-socks
10000/tcp open  snet-sensor-mgmt


Nmap done: 1 IP address (1 host up) scanned in 1.65 seconds
```

---

### Post by TheFu on 2020-07-10
The way i attack this depends on the risk level for each system and the network it sit on.
For a desktop, I’ll start with:
[LIST]
[*]allow all outbound
[*]allow inbound from the LAN
[*]block inbound from the WAN
[/LIST]

From that point, I’ll tighten as needed.  Things like outbound email can only be sent to 2 servers - my email server and 1 external provider.

My router only allows a few ports inbound and directs those to specific systems with static ips.  Nothing on a client computer can change the router. I’ve never allowed UPnP to dynamically open ports on the router. UPnP has always been a terrible idea.  The inbound ports allowed are a few ssh and openvpn connections and some website and email to my web and email server systems.  if you don't run those things, block all inbound.

No need for whack-a-port for 99.9995% of end-users.

---

### Post by SeijiSensei on 2020-07-11
> **goodstuff9 said:**
> Thanks for your help.  I post the results here.  But....  Now I'm confused, this list is FAR shorter than the list produced by the ss -lntup command......  

```
Starting Nmap 7.60 ( https://nmap.org ) at 2020-07-10 14:13 CDTNmap scan report for localhost (127.0.0.1)
Host is up (0.000017s latency).
Not shown: 982 closed ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
631/tcp   open  ipp
1025/tcp  open  NFS-or-IIS
1042/tcp  open  afrog
2049/tcp  open  nfs
3689/tcp  open  rendezvous
5054/tcp  open  rlm-admin
5900/tcp  open  vnc
8000/tcp  open  http-alt
8080/tcp  open  http-proxy
8085/tcp  open  unknown
9050/tcp  open  tor-socks
10000/tcp open  snet-sensor-mgmt


Nmap done: 1 IP address (1 host up) scanned in 1.65 seconds
```

Whatever the results of that other command, those are the TCP ports that are open on your machine.  You only get TCP services from the basic nmap command.  To see if you have UDP listeners, run

```
sudo nmap -sU localhost
```

nmap only scans about 1500 commonly used ports by default. If you want to be comprehensive, run

```
sudo nmap -p 1-65535 -sT localhost
```

for a TCP scan of every one of the 65,535 available ports.  This can take a while so running it overnight makes sense.



If you don't have any publicly-facing interface, then I'd just move on.  Otherwise you need to determine why all those services are running on your machine, whether they are in fact needed, and whether they are used by other people connecting to this machine.

---

### Post by TheFu on 2020-07-11
Below, I'll be getting into the weeds.  Ignore if you don't want to worry about this stuff.  

OTOH, if you want to understand networking, there are a few episodes of the _Security Now!_ podcast where they explain "how the internet works" - which is really how IPv4 networking works.  Start with Episode 25. I don't recall if they did them back to back or skipped a week; 25, 27, 29.  Google will find that podcast pretty easily. Then go into the archives. They have human-transcribed the voices, if that works better for you. The hosts do a bunch of extra chatting well outside the topic, which can drive people crazy.

Computers use lots of methods to talk between different programs running on the same machine.  Because of the way Unix is designed, often using an internal-only network connection is the easiest. The **ss** command ran above probably showed all the connections, including the connections that are just the machine talking to itself on a private network connection.

There are some of those that use the public network connections too, so that some programs can talk both locally or to other partner systems on the network.  Filtering out those local-only connections is easy. On one of my systems:
```
$ sudo netstat -tulpn |grep LISTEN|grep -v 127
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      31537/smbd      
tcp        0      0 0.0.0.0:5906            0.0.0.0:*               LISTEN      19489/qemu-system-x
tcp        0      0 10.161.241.1:53         0.0.0.0:*               LISTEN      4905/dnsmasq    
tcp        0      0 0.0.0.0:4949            0.0.0.0:*               LISTEN      3672/perl       
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3540/sshd       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      31537/smbd
```
That machine is running a Samba server, ssh, and I know the 'perl' code is my systems monitor so another machine can pull statistics.  [LIST]
[*]It is restricted in the munin config file to this machine or 1 other. Inside the /etc/munin/munin-node.conf file:
```
allow ^127\.0\.0\.1$
allow ^172\.22\.22\.4$
```
[*]The 10.161.x.x:53  DNS connection is to support lxd systems; it is non-routed.
[*]The 5906 connection is to manage all the virtual machines running on the box. It is a type of VNC, but it can only be accessed through an ssh tunnel.
[*]I'm positive about the connection filters for each of those processes. They are all limited to my subnet or even just localhost.  
[/LIST]

The ssh connection isn't actually restricted to any subnet, but the router doesn't pass ssh traffic to the machine at all. All my ssh-servers (which is every Unix system here), have brute force denial protection and won't allow any connections without ssh-keys from outside the subnet. At the bottom of the /etc/ssh/sshd_config file:
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes
```

The "Match Address" line shows some of the subnets here. I wanted to ensure ssh access from my different LANs to this specific server machine.  Desktops get a little messier because of all the crap that Canonical and the DEs run automatically so things will "just work". I 
disable much of those programs.

On a 20.04 Mate-desktop that I do not have an active "X/Session" on, 
```
$ sudo netstat -tulpn |grep LISTEN|grep -v 127
tcp        0      0 0.0.0.0:4713            0.0.0.0:*               LISTEN      1318/pulseaudio     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      822/sshd: /usr/sbin 
tcp        0      0 0.0.0.0:6010            0.0.0.0:*               LISTEN      1321/sshd: tf@pts/0 
tcp        0      0 0.0.0.0:6011            0.0.0.0:*               LISTEN      2845/sshd: tf@notty 
```

First, I've disabled IPv6, so daemons cannot use any IPv6 stuff. I'm just not ready for it.
Three of those lines are ssh. I remote into systems over ssh all the time to run programs remotely.
The pulseaudio thing is just for listening to audio or sounds.  Pulse has some really weenie security to prevent remote users - actually, I wouldn't call it security.  
That's the total list of non-private services. I have 2 filters to the output - that's what those 'grep' commands do.  There are lots of outbound connections for different purposes - moslty avahi announcements for printers, mdns, and some other service (DLNA?).  Because they are broadcast on the LAN and not specific connections to external systems, I don't worry about them.

To see active tcp connections, use:
```
$ netstat -t 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 regulus:35860           zcs45:imaps             ESTABLISHED
tcp        0      0 regulus:36026           zcs45:imaps             ESTABLISHED
tcp        0      0 regulus:6011            localhost:55066         ESTABLISHED
tcp        0      0 localhost:55066         regulus:6011            ESTABLISHED
tcp        0      0 regulus:ssh             hadar:53492             ESTABLISHED
tcp        0      0 regulus:ssh             hadar:39562             ESTABLISHED
tcp        0      0 regulus:35862           108.177.122.16:imaps    CLOSE_WAIT 
```

regulus, zcs45, hadar are all systems on the LAN that I control.
108.177.122.16 is google.com ... actually gmail.  imaps is an encrypted connection to an email server.  The way these connections work is that 1 side has a standard port and the other side picks a random port.  Almost always, the random port is from a **client** and the standard port is to a **server**.  From that list above, it is clear that 
```
regulus ---> IMAP ---> zcs45
regulus ---> IMAP ---> zcs45
regulus ---> IMAP ---> gmail
```
and
```
hadar ---> ssh ---> regulus
hadar ---> ssh ---> regulus

```
Those are all expected since I use IMAP for email and use ssh for almost everything else.  But the bidirectional regulus and localhost connections are a little mystery.  Since I'm on regulus, that means regulus == localhost so the system is using a private network to talk to the public network interface.  Hummm.  I talk to myself sometimes too. I'm not going to worry about it.

BTW, the normal ports for the most popular daemons is stored in a text file - /etc/services. Take a look at it.  Any service can decide to listen on any port, but most follow those numbers in that file.  Any ports below 1024 must have the port opened by root.  Any userid can open a port over 1024. It is a security thing.

Clear as mud? My intent by showing all the nitty details wasn't to confuse. It was just to show why my three global firewall rules work, in general, for almost all situations.

---

### Post by TheFu on 2020-07-11
```
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
631/tcp   open  ipp
1025/tcp  open  NFS-or-IIS
1042/tcp  open  afrog
2049/tcp  open  nfs
3689/tcp  open  rendezvous
5054/tcp  open  rlm-admin
5900/tcp  open  vnc
8000/tcp  open  http-alt
8080/tcp  open  http-proxy
8085/tcp  open  unknown
9050/tcp  open  tor-socks
10000/tcp open  snet-sensor-mgmt

```
These aren't the normal programs a typical desktop user would run.  Many are high risk and shouldn't be available over the internet without significant security wrappers.  If you ran the nmap against "localhost", then you'll see both the ports available on the subnet AND only available to that specific machine.  For someone running TOR, a bunch of those daemons seem anti-privacy and should be disabled.  Running a web server and DNS server and VNC and NFS server and samba server on the same system just seems non-secure to me.  But if they all only allow access no the local machine, then it isn't THAT big of a deal.

I am concerned that you have VNC, but not ssh running. Please say that ssh is running on a non-standard port? Please.

---

### Post by goodstuff9 on 2020-07-14
Thank you.  

Sorry for the delay, I was away for a couple days.  

I will admit, I am unable to follow 90% of what you wrote.  I need far more education to understand what you are saying, and what conclusions I should draw from it.

---

### Post by goodstuff9 on 2020-07-14
Thank you. 

Sorry for the delay, I was away for a couple days. 

I will admit, I am unable to follow 90% of what you wrote. I need far more education to understand what you are saying, and what conclusions I should draw from it.

---

### Post by goodstuff9 on 2020-07-14
Well, I don't know what any of these programs are, to be honest.  So, I have no way to evaluate them.  I do not know which applications I have installed that depend on these ports.  

I also don't know what is meant by "localhost" and by "subnet" in my situation.  (I did look up the definitions, but they only raised more questions for me.)  

"[COLOR=#000000]Running a web server and DNS server....."  I am?????  [/COLOR]

"[COLOR=#000000]But if they all only allow access no the local machine, then it isn't THAT big of a deal."  How would I determine that access is limited to just the local machine?  [/COLOR]

I have absolutely no idea if ssh is running.  How would I know that?  More importantly, why would I care?  And, what makes it have a special relationship with "VNC", but not with anything else?  

I am not saying this in a critical or ungrateful way:  The responses here only raise more questions in my mind, and leave me more confused.  These responses confirm how I felt when I made the first post in this thread:  Firewall management in Ubunut is, practically speaking, not something that an ordinary layman is expected to do.  

Here is what I did several years ago:  I installed Ubuntu.  Then, I installed applications to get things done.  Seems logical, huh?  Never once in the installation of any application do I recall any text/warning/message about ports or security, etc. - Why would I have had such thoughts?  I never gave it any thought until recently when I stumbled across some articles.  So, my computer is now in the state it is in, and I don't know what to do at this point, or if I even need to do anything at all.

---

### Post by TheFu on 2020-07-14
By default, ubuntu desktop doesn't have any network daemons running that exit the lan. 

Unix systems expect the admin to setup a firewall when needed.  It only says something when we ask it to do something it cannot do.  it doesn't know how smart or how dumb the request is.  The user is expected to know that.

I don't know what a typical end user should or shouldn't know, sorry.  

A bunch of those service shouldn't be running on a non-developer system.  You should remove those.  Keep the list and remove them. if something you need stops working, put it back and read up on the security implications.
If you aren't using nfs, the you don't want that running.  
Same the the web server(s) running.
Especially for vnc.

In theory, a properly maintained home router would block most attacks to these services.  If your router hasn't been patched in the last month, it is time to patch it.  Sadly, many very popular routers have terrible security.  [https://www.fkie.fraunhofer.de/en/press-releases/Home-Router.html](https://www.fkie.fraunhofer.de/en/press-releases/Home-Router.html)  Asus, netgear, tplink, d-link, zyxel ...linksys, cisco....

My mother was a typical 1-computer home user.  She wouldn't need VNC or any of those other services.  If you didn't install them, who did?

---

### Post by SeijiSensei on 2020-07-15
If you don't know what those programs are, then I suggest you reinstall a clean version of Ubuntu 20.04 and start afresh.  You shouldn't be running applications whose purposes you don't understand.

For instance, I have no idea what "afrog" is. It's described as "subnet roaming" in its [official definition](https://www.adminsub.net/tcp-udp-port-finder/1042) by the Internet Assigned Names and Numbers (IANA).  It's not a service most ordinary users would ever install.

You still haven't told us whether this is a server or a desktop machine. Is it directly connected to the public Internet, or does it go through a router?

---

### Post by TheFu on 2020-07-15
Perhaps the real question is much simpler?
Maybe the OP really just wanted to know which program would be easiest to use to control iptables for his needs?
Answer: **gufw**
This is a simple interface into the most commonly used interface for the firewall on Ubuntu systems. It doesn't provide all the controls and capabilities that iptables provides, but it is more than sufficient for almost all desktop users.
For a desktop, I’ll start with:
[LIST]
[*]    allow all outbound
[*]    allow inbound from the LAN
[*]    block inbound from the WAN
[/LIST]
gufw can do those things.

But the idea to > reinstall a clean version of Ubuntu 20.04 and start afresh is a good one. Be certain to backup any settings, data, and perhaps the list of manually installed programs.

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]A bunch of those service shouldn't be running on a non-developer system. You should remove those."  

Ok.  How do I do that?  I am assuming that those are services, as opposed to applications.  

I know how to uninstall an application.  How do I "remove" a service?  
[/COLOR]

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]You still haven't told us whether this is a server or a desktop machine. Is it directly connected to the public Internet, or does it go through a router?"

[/COLOR]Sorry.  It is a desktop computer.  It connects to the internet via a router.

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]If you didn't install them, who did?"  

I don't know.  I guess I did.  

This system is seven years old.  I cannot remember everything I've installed in the past seven years.  [/COLOR]

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]If you don't know what those programs are, then I suggest you reinstall a clean version of Ubuntu 20.04 and start afresh."  

Let's say I did that.  

Then, on my "clean" system, I need to install a new application.  Someone earlier in this thread suggested that the only way I can know which ports that new application needs to operate is by doing online research.  Is that the expected way to know how firewall settings may need to be adjusted?  That seems very unwieldy and impractical to me, especially for the common user.  [/COLOR]

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]Maybe the OP really just wanted to know which program would be easiest to use to control iptables for his needs?"  

No, that is not what I am asking.  

I am asking how, in some practical fashion, does a person who is not a tech expert determine which ports need to be "opened" for the applications he has installed on his system - both for existing applications, and for any new applications he may install in the future.  

In other words, How does a person know whch firewall rules need to be created using a tool like gufw?  [/COLOR]

---

### Post by goodstuff9 on 2020-07-17
"[COLOR=#000000]Be certain to backup any settings, data, and perhaps the list of manually installed programs."

How does a person compile a list of manually installed programs?  [/COLOR]

---

### Post by The Cog on 2020-07-17
> **goodstuff9 said:**
> Thanks for your help.  I post the results here.  But....  Now I'm confused, this list is FAR shorter than the list produced by the ss -lntup command......  
The ss command will also list processes that are listening on the loopback addresses 127.0.0.1 and ::1 - you can ignore those lines because they are not reachable from outside the box.

---

### Post by TheFu on 2020-07-17
> **goodstuff9 said:**
> "I know how to uninstall an application.  How do I "remove" a service?  


Same way you installed it.  If you used **apt install** for the install, use **apt remove** to remove it.  If you used **snap install** then use **snap remove**.

---

### Post by TheFu on 2020-07-17
> **goodstuff9 said:**
> Sorry.  It is a desktop computer.  It connects to the internet via a router.

If there is a router and that router is properly maintained and using typical home-user settings, then I'm not nearly so worried about your security. OTOH, if the router is not properly maintained, i.e. hasn't been patched since May, then I am concerned.  Every few months, I new batch of router security failures gets listed on the internet and automatic tools are created to breach those systems. The latest list is above, as I've posted.

When it comes to computer security, I want a fully functioning router+firewall and a fully functioning computer+firewall. This is so when I make a small mistake in configuring 1 or the other by accident, my computer(s) aren't naked on the internet.

---

### Post by TheFu on 2020-07-17
> **goodstuff9 said:**
>  

Then, on my "clean" system, I need to install a new application.  Someone earlier in this thread suggested that the only way I can know which ports that new application needs to operate is by doing online research.  Is that the expected way to know how firewall settings may need to be adjusted?  That seems very unwieldy and impractical to me, especially for the common user.

No. You should start by having the 3 firewall rules as spelled out twice above on any system that has network listeners (i.e. network services).  These are the 'server-side' of a client-server connection.  A web browser is a client.  An email program is a client.  An IRC program is a client.  Almost all programs with a GUI that you want to do work using, are clients, so they are NOT "network services" and you don't need to worry.
  [/COLOR]
But somehow you have a web server, NFS server and a few other "network services" running.  Those things don't happen by accident. The NFS server is for allowing other computers to access files on this system.  Without configuring it, it is useless.  There isn't any GUI to configure NFS or apache or ngxinx (those are web servers), so whoever installed them would have manually had to edit system files using sudoedit in very specific ways.  Same for Samba - that's a CIFS network file sharing protocol so Windows systems (and some media players) can access files.

If all you have at home is this 1 desktop computer, then there is little reason at all to run a web server or nfs server or ... most (all?) of the other network services.

A "common user" would never have installed all these things at all.

---

### Post by TheFu on 2020-07-17
> **goodstuff9 said:**
>  In other words, How does a person know whch firewall rules need to be created using a tool like gufw? 
Already answered

For a desktop, I’ll start with:

[LIST]
[*]    allow all outbound
[*]    allow inbound from the LAN
[*]    block inbound from the WAN
[/LIST]

That's what you should do.

---

### Post by TheFu on 2020-07-17
> **goodstuff9 said:**
>  

How does a person compile a list of manually installed programs? 

**apt-mark showmanual**

---

### Post by goodstuff9 on 2020-07-17
Ok, if I'm understanding all this correctly.....  

"[COLOR=#000000]For a desktop, I&#8217;ll start with:[/COLOR]


[LIST]
[*]allow all outbound
[*]allow inbound from the LAN
[*]block inbound from the WAN
[/LIST]


[COLOR=#000000]That's what you should do."  

So, I'll do that, and see which applications fail.  Then, I need to decide if I want to create a rule to allow the application through the firewall, or, if I should uninstall the application.  

Going forward, if I feel I need to install a new application, I guess I need to do some online research to figure out firewall impacts, in any, I need to consider for the application.  

Sound like the right way to approach things?  

(And, thank you for your help with this!)  [/COLOR]

---

### Post by goodstuff9 on 2020-07-17
Are you sure the command

apt-mark showmanual 

shows only the list of manually installed programs?  


I ask because, when I run that command, I get about 500 applications listed, including applications like "apt" and "sudo" and "ubuntu-desktop", etc.  I know I never manually installed them.

---

### Post by TheFu on 2020-07-17
```
showauto
           showauto is used to print a list of automatically installed
           packages with each package on a new line. All automatically
           installed packages will be listed if no package is given. If
           packages are given only those which are automatically installed
           will be shown.

       showmanual
           showmanual can be used in the same way as showauto except that it
           will print a list of manually installed packages instead.
```

is how the manpage describes it. apt-mark can toggle packages as auto or manual so perhaps the package manager you use does too?

Sorry i don't have a better answer.

---

