---
title: "Ping by IP address but not by name"
date: 2007-03-08
forum: Server Platforms
---

### Post by Steve Smith on 2007-03-08
I've just installed Dapper from the server iso.  I can ping it by its IP address but not its name.  It can only ping other machines by their IP addresses too, not by their names.

Any ideas would be great!
Thanks :)

---

### Post by Nikron on 2007-03-08
The easy way do this would be to just associate the computers name in /etc/hosts.

---

### Post by Mr. C. on 2007-03-08
No, that is not the correct way to solve this.

Your DNS servers are not correctly configured:

System->Administration->Networking

and click the DNS tab.  Configure the DNS settings your ISP gave you.  If your router appliance is configured for DHCP and it is supplying the DNS servers to your system, configure the router with the correct DNS servers, or turn of the routers internal DNS service (if this is applicable to your case).  If you are not sure, show the DNS server that is listed in Networking DNS tab.

MrC

---

### Post by Steve Smith on 2007-03-09
Thanks for your replies.  I'm using the server install, so I don't have a GUI.  But in any case, yes, I'm on DHCP, and the router is correctly configured because the other Ubuntu machine I have works!  But that one was installed with the normal CD.  Is there any difference that might affect this problem?

---

### Post by dannyboy79 on 2007-03-09
> **Mr. C. said:**
> No, that is not the correct way to solve this.

Your DNS servers are not correctly configured:

System->Administration->Networking

and click the DNS tab.  Configure the DNS settings your ISP gave you.  If your router appliance is configured for DHCP and it is supplying the DNS servers to your system, configure the router with the correct DNS servers, or turn of the routers internal DNS service (if this is applicable to your case).  If you are not sure, show the DNS server that is listed in Networking DNS tab.

MrC

there is nothing wrong at all with using a host file on a small network!!!! this is how they used to do it prior to DNS being invented. I would rather have a local hosts file and have my name resolution be quick versus having my local name resolution done by some dns server that's on the other side of the world possibly. 

[http://www.oreilly.com/catalog/samba/chapter/book/ch07_03.html](http://www.oreilly.com/catalog/samba/chapter/book/ch07_03.html)

or if you're using your winxp pro mahcine as the local master browser for the network (windows most always will be unless you set samba to be)

[http://support.microsoft.com/kb/119493](http://support.microsoft.com/kb/119493)

---

### Post by Steve Smith on 2007-03-09
That's fair enough, but I would like to know why it works on one machine but not the other!

---

### Post by Mr. C. on 2007-03-09
> **dannyboy79 said:**
> there is nothing wrong at all with using a host file on a small network!!!! this is how they used to do it prior to DNS being invented. I would rather have a local hosts file and have my name resolution be quick versus having my local name resolution done by some dns server that's on the other side of the world possibly. 

or if you're using your winxp pro mahcine as the local master browser for the network (windows most always will be unless you set samba to be)

Dannyboy - I was in this business when we were using host files, manually maintaining them.  There is a reason why we abandon that approach.

The OP has a *server* installation, and is likely safe to presume wanting to connect with more than a handful of sites.  In today's highly connected Internet, it is no longer possible to configure a hosts file for robust name lookups.  Many of today's sites have multiple IP address, roundrobin-ed for load balancing, and hosts allows only a single IP/hostname resolution.

Steve Smith: add the DNS servers the ISP gave you, or provides, or find someone who offers free DNS services.  Add them to:

/etc/resolv.conf:

```
domain *YOURDOMAN*
nameserver *YourISPsDNS1*
nameserver *YourISPsDNS2*
```

Place the fastest, most reliable ones first.

I cannot diagnose what or why things went wrong in your situation, or configuration.  We'd have to analyze what you did, what information you entered, where your installation got its network information, etc.

MrC

---

### Post by dannyboy79 on 2007-03-09
> **Mr. C. said:**
> Dannyboy - I was in this business when we were using host files, manually maintaining them.  There is a reason why we abandon that approach.

The OP has a *server* installation, and is likely safe to presume wanting to connect with more than a handful of sites.  In today's highly connected Internet, it is no longer possible to configure a hosts file for robust name lookups.  Many of today's sites have multiple IP address, roundrobin-ed for load balancing, and hosts allows only a single IP/hostname resolution.

Steve Smith: add the DNS servers the ISP gave you, or provides, or find someone who offers free DNS services.  Add them to:

/etc/resolv.conf:

```
domain *YOURDOMAN*
nameserver *YourISPsDNS1*
nameserver *YourISPsDNS2*
```

Place the fastest, most reliable ones first.

I cannot diagnose what or why things went wrong in your situation, or configuration.  We'd have to analyze what you did, what information you entered, where your installation got its network information, etc.

MrC

it's not like you only have an option to do 1 or the other, you can do both. you think that I have a hosts file that contains every single ip address to name resolution on the internet? I don't, I have a host file that merely contains the statically assigned ip addresses to their computer name and that's all. are you suggesting that I don't need the hosts file for this to work? so maybe I have done this for no reason and it's just because it works, I don't know but I can ping by hostname as well as ip.

this thread will definitely help you out:
[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

### Post by Brazen on 2007-03-09
view the /var/lib/dhcp3/dhclient.ethX.leases file (ethX is your ethernet device, probably eth0).  On a server you can use more, less, or nano to view this file.  Under the last "leases" entry, there should be one or more lines beginning with "option domain-name-servers".  Check the servers that are listed and verify if they are your correct DNS servers.  Even if they are not the correct ip addresses, do not edit this file, it will do you no good.  Let us know if they are correct or not.

---

### Post by Mr. C. on 2007-03-09
> **dannyboy79 said:**
> it's not like you only have an option to do 1 or the other, you can do both. you think that I have a hosts file that contains every single ip address to name resolution on the internet? I don't, I have a host file that merely contains the statically assigned ip addresses to their computer name and that's all. are you suggesting that I don't need the hosts file for this to work? so maybe I have done this for no reason and it's just because it works, I don't know but I can ping by hostname as well as ip.

I know how hostname lookup works.  In case you need a brush up, review my Week 3 "Network Services" lecture notes here:

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

and Week 8 and 9 DNS notes as well.

The ONLY hostname one needs in /etc/hosts is the localhost -> 127.0.0.1 mapping (this is required for early boot processes when a local DNS server is not available, and because "localhost" is a NFQD that has no domain).

What you place in your hosts file doesn't concern me.  Poor advice does.  I believe it is best to give reliable solutions, not "my way" solutions, or partial solutions.  Your advice solves only N-cases - those that you enter into the hosts table.  To make the solution work reliably, one needs DNS. Period.

MrC

---

### Post by Slim Odds on 2007-03-09
I love an apples and oranges discussion as much as the next guy. BUT, there are two different and unrelated issues here.

The OP asked about accessing HIS machine by name. Your ISP's DNS server does not contain a name-to-address relationship for YOUR local machine on YOUR local network. Put it in your /etc/hosts files. For accessing machines on the Internet by name, DNS.

---

### Post by Mr. C. on 2007-03-09
> **Slim Odds said:**
> The OP asked about accessing HIS machine by name. Your ISP's DNS server does not contain a name-to-address relationship for YOUR local machine on YOUR local network. Put it in your /etc/hosts files. For accessing machines on the Internet by name, DNS.

Hardly: "It can only ping other machines by their IP addresses too, not by their names."

MrC

---

### Post by Nikron on 2007-03-09
I thought he meant within his own network, that he couldn't ping his Dapper machine by its name.  Therefore, the quickest way would be just to add it to /etc/hosts/  If he can't ping _any_ machines by their names, then he of course needs to fix whatever DNS problem he has.  Sorry for misinterpeting the original question..

---

### Post by dannyboy79 on 2007-03-09
i think dns is for resolving "internet" ip addresses to hostnames and wins or netbios over tcp/ip is for resolving "intranet" ip addresses to hostnames, if I am wrong well than I guess it just shows that I haven't read much about it but am merely stating this based on what I have experienced and on logical reasoning. here is a great site to make my case:
[http://osr507doc.sco.com/en/samba_help/Integrating-with-Windows.html](http://osr507doc.sco.com/en/samba_help/Integrating-with-Windows.html)

---

### Post by Mr. C. on 2007-03-09
We cannot know what the OP has installed and running on his system.  Its a server machine, configured to run as a server.  He may have a cache-only DNS service running.  I don't know what was installed and what was configured.  I run my own split view DNS, which provides my LAN hosts with fully qualified names, as well as external DNS lookups.

Placing host names in /etc/hosts is fine.

Wins and Netbios have absolutely nothing to do with *nix's TCP/IP name resolution. Nada. There is no distinction between intra- and inter-net for TCP/IP and name resolution.  Its all hosts- or DNS looksup, or other DB as per specific configuration (NIS, LDAP, etc.).

MrC

---

### Post by Slim Odds on 2007-03-09
> **Mr. C. said:**
> Hardly: "It can only ping other machines by their IP addresses too, not by their names."

MrC

First part of the post: **I've just installed Dapper from the server iso.  I can ping it by its IP address but not its name.**

So pay attention next time MrC

---

### Post by Steve Smith on 2007-03-09
Gosh, I didn't know I was going to start anything like this! :)  And for a moment there I thought I was being called an [Obnoxious Preppie](http://www.answers.com/topic/op-abbreviation-1).  Anyway, back to business...

Mysteriously, although the machine couldn't initially be pinged by its name, after a while (possibly after installing samba) it now can.  So to clarify, here's the situation as it stands (I'll call the machines workinghost and newhost).

**workinghost**
Dapper from alternate CD, with Gnome, can be pinged by name from anything, can ping anything by name.
```

$ cat /etc/hosts
127.0.0.1 localhost workinghost

$ cat /var/lib/dhcp3/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 10.1.1.254;
  option subnet-mask 255.255.0.0;
  option routers 10.1.1.1;
  option dhcp-lease-time 259200;
  option dhcp-message-type 5;
  option domain-name-servers 194.168.4.100,194.168.8.100;
  option dhcp-server-identifier 10.1.1.1;
  option interface-mtu 1492;
  renew 0 2007/3/11 06:08:29;
  rebind 1 2007/3/12 15:06:22;
  expire 2 2007/3/13 00:06:22;
}

```


**newhost**
Dapper from server CD, so command line only.  Can now be pinged by name from anything.  Can ping anything by IP but not by name, so it cannot ping workinghost by name, nor any of the windows machines.  It has no problem with DNS on websites and never has had (it can ping google.co.uk).
```

$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       newhost

$ cat /var/lib/dhcp3/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 10.1.1.253;
  option subnet-mask 255.255.0.0;
  option routers 10.1.1.1;
  option dhcp-lease-time 259200;
  option dhcp-message-type 5;
  option domain-name-servers 194.168.4.100,194.168.8.100;
  option dhcp-server-identifier 10.1.1.1;
  option interface-mtu 1492;
  renew 6 2007/3/10 17:30:28;
  rebind 1 2007/3/12 01:05:57;
  expire 1 2007/3/12 10:05:57;
}

```

Sorry if I didn't make things clear from the start!  Let's play spot the difference... ;)

**Edit**
I'm going crazy now!  I've just gone through checking the info I just gave is right, and now the windows machine can ping anything by name, as before, but now neither of the ubuntu machines can ping anything on the local network by name.  I swear it wasn't doing that before.  But maybe it was.  Perhaps I just assumed I used to be able to ping from workinghost?  I was stressing about getting an email server working by the morning, after all...  Could someone with a farily recently-installed Dapper try doing some pinging for me, see what happens?  Thanks! :)

---

### Post by dannyboy79 on 2007-03-09
> **Mr. C. said:**
> We cannot know what the OP has installed and running on his system.  Its a server machine, configured to run as a server.  He may have a cache-only DNS service running.  I don't know what was installed and what was configured.  I run my own split view DNS, which provides my LAN hosts with fully qualified names, as well as external DNS lookups.

Placing host names in /etc/hosts is fine.

Wins and Netbios have absolutely nothing to do with *nix's TCP/IP name resolution. Nada. There is no distinction between intra- and inter-net for TCP/IP and name resolution.  Its all hosts- or DNS looksup, or other DB as per specific configuration (NIS, LDAP, etc.).

MrC
it's funny how a few threads ago you stated that putting host names within the /etc/hosts file was wrong and not you say, "Placing host names in /etc/hosts is fine" Also, he link I provided specifically stated, "Name Resolution in a pure Unix/Linux world
The key configuration files covered in this section are:
/etc/hosts"

and as far as your statement, "Wins and Netbios have absolutely nothing to do with *nix's TCP/IP name resolution." You have completely gone off your rocker here, you can specify a WINS server for name resolution for your Linux computer. and have you ever heard of nmbd daemon? Here is a snipit from the man page: nmbd - NetBIOS name server to provide NetBIOS over IP naming services to clients.How about we try to help this guy instead of trying to tell each other what can do what!! I mean, with all your expertes (i know it's spelled wrong and I don't care!) you'd think you'd be able to help him right away.

---

### Post by Brazen on 2007-03-09
> **Steve Smith said:**
> 
I'm going crazy now!

From the dapper server, can you ping internet sites by name?  Try pinging [www.google.com](www.google.com).  If it works, then your dns resolution is fine, and then we can concentrate on local resolution only.

I think the people arguing back and forth about /etc/hosts and dns are both right, they are just making different assumptions on your setup.  Personally, I don't like to argue based on assumptions; I would rather just ask you or help you find out what the setup is :D

By the way, the results of your .leases files look fine, I just wanted to make an easy check to be sure it wasn't a dhcp issue.  That also let us know that you do NOT have a local dns server (my dd-wrt router DOES use a built-in DNS server, and most businesses will set up a local dns server, so it is common, but should not be assumed).

---

### Post by Steve Smith on 2007-03-09
> **Brazen said:**
> From the dapper server, can you ping internet sites by name?  Try pinging [www.google.com](www.google.com).  If it works, then your dns resolution is fine, and then we can concentrate on local resolution only.


I've already said, yes, I can ping google.co.uk!

> **Brazen said:**
> 
By the way, the results of your .leases files look fine, I just wanted to make an easy check to be sure it wasn't a dhcp issue.

Thanks!

One thought I've had, which I'm too tired to try right now, is I've recently got a second router (which I'm just using as a switch, with no routing, no dhcp), which has the two servers pluged in it, and a cable running to the main router.  I guess that could be the problem?

---

### Post by Brazen on 2007-03-09
Ok, so, some more thinking here.  You don't have a local dns server...  Windows gets around not having a local DNS server by using Netbios over TCP/IP, but Linux does not include Netbios by default.  The way to use Netbios on your linux machine is with Samba.  The service that provides Netbios is the nmbd service, so one option is to install Samba and make sure nmbd is running.  However, Netbios is a Windows designed protocol and doesn't even work that well on Windows, plus it uses a broadcast mechanism to resolve machine names - very inefficient.

The other option is to use hosts files.  The more machines you have, the harder this becomes.  Every Windows machine will need your linux machines listed in it's hosts file and every linux machine will need every linux and Windows machine listed in it's host file.  DNS scales much nicer, but setting up hosts files is supe quick and easy on a network with only 3 to 5 or so machines.

Again, you MUST at least one mechanism for resolution: DNS, Netbios, or hosts files.  You appear to use Netbios on your Windows machines (by default) and nothing on your linux machines.  You need to pick one to use on your linux machines.

I hope I have explained this clearly and I hope I don't get lost in all the nonsense in this thread :D

---

### Post by Brazen on 2007-03-09
> **Steve Smith said:**
> I've already said, yes, I can ping google.co.uk!sorry I missed that.  Guess I'll eat crow on that one!


> One thought I've had, which I'm too tired to try right now, is I've recently got a second router (which I'm just using as a switch, with no routing, no dhcp), which has the two servers pluged in it, and a cable running to the main router.  I guess that could be the problem?
I think my previous post probably has your answer.  I take it you have logged into the second router's interface and disabled dhcp AND there is nothing plugged into the "internet" port on that router?  If so, then that should be fine.

---

### Post by Mr. C. on 2007-03-10
Steve - when you become tired of the endless battle, drop me a PM and I'll help you out.  I'm not going to continue to debate the differences between how and when DNS is used.

Cheers,
MrC

---

### Post by Steve Smith on 2007-03-10
> **Brazen said:**
> I take it you have logged into the second router's interface and disabled dhcp AND there is nothing plugged into the "internet" port on that router?  If so, then that should be fine.

Yes, that's right.

Well I'll try pulling the second router out anyway later, see what happens, then I'll post back and take it from there!

---

### Post by Brazen on 2007-03-10
> **Steve Smith said:**
> Yes, that's right.

Well I'll try pulling the second router out anyway later, see what happens, then I'll post back and take it from there!

I'm tella ya, the router is not going to matter if you don't have any resolution protocol set up.  You MUST use either a local dns server, Netbios (nmbd daemon), or hosts files.  If you don't have one of these then you will not be able to perform name resolution, no matter what else you try.

---

### Post by Steve Smith on 2007-03-11
I swear it used to work!

---

### Post by dannyboy79 on 2007-03-12
> **Mr. C. said:**
> Steve - when you become tired of the endless battle, drop me a PM and I'll help you out.  I'm not going to continue to debate the differences between how and when DNS is used.

Cheers,
MrC

this type of adolescent behavior doesn't help anyone else that comes here for help, if you are going to help him than post it in the thread so that everyone can benefit. it takes a special kind of person to be able to admit that they are wrong and or state the fact that earlier statements might have been incorrect.

---

### Post by Brazen on 2007-03-12
> **Steve Smith said:**
> I swear it used to work!

Are you certain of the point at which is stopped working?  Maybe your router has a built-in DNS server and for some reason it stopped advertising itself in the DHCP information.  When it stopped working, were you making any changes on ANYTHING?

OR, have you checked to see if nmbd is running on the dapper boxes?  Maybe you were using nmbd and it suddenly stopped working (not surprising, as I said it is a clunky Microsoft protocol).

You need to check these things out before I can help you fix this.  Or you can start setting up a local dns server, or configuring you hosts files.  You have to make a choice.

---

### Post by dannyboy79 on 2007-03-12
you can see if it's running by doing
**ps aux | grep mbd** (or is it **ps aux | grep *mbd**)
and it should return both *smbd* and *nmbd* if you're running samba.

---

### Post by Explosive_Cornflake on 2007-03-12
You need wins:
To ping other computers, edit you /etc/nsswitch.conf
```
ccoffey@Zoidberg:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns wins
networks:       files wins

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
To broadcast your name
You'll to install samba, and edit your /etc/samba/smb.conf.
Change
```
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no
```
to
```

   wins support = Yes
```

and then start nmbd
```

sudo /usr/sbin/nmbd start

```

Working 
```

ccoffey@Zoidberg:~$ ssh branigan
Password:
Last login: Mon Mar 12 20:56:35 2007 from 192.168.3.102
Have a lot of fun...
ccoffey@Branigan:~> ping zoidberg
PING zoidberg (192.168.3.103) 56(84) bytes of data.
64 bytes from 192.168.3.103: icmp_seq=1 ttl=64 time=0.156 ms
64 bytes from 192.168.3.103: icmp_seq=2 ttl=64 time=0.160 ms

--- zoidberg ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 0.156/0.158/0.160/0.002 ms

```

---

### Post by dannyboy79 on 2007-03-12
i don't have a wins server defined and I can ping all my boxes by ip and hostname so I would have to say that this isn't nessessarily true.

plus according to this thread here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS but I don't know if this is true.

---

### Post by Explosive_Cornflake on 2007-03-12
Well, without resorting to adding to /etc/hosts. I use dhcp here on anything not a server, and it works fine for me. All I can say is try those, and see how your mileage varies.

---

### Post by Brazen on 2007-03-12
> **Explosive_Cornflake said:**
> Well, without resorting to adding to /etc/hosts. I use dhcp here on anything not a server, and it works fine for me. All I can say is try those, and see how your mileage varies.

Now, I never use wins/netbios on linux (that's the Windows-way, DNS or hosts is the linux-way, which I prefer the latter), but I had _thought_ that all you needed was the nmbd daemon to run.  You may have wins set up, but I too thought your wins server had to have a static ip in order to take advantage of wins, plus you had to have the wins server defined on each of your hosts.

You may have wins partially configured, but I think your name resolution is being handled by plain old netbios (you don't need wins in order for netbios to work).  I'm not certain though, I'm just thinking out loud here.

---

### Post by Steve Smith on 2007-03-13
Right, here we go :).

First off, bypassing the second router had no effect (thought I ought to try just in case!).

I've been a bit daft, I only used to have one Ubuntu machine on the network, which could ping itself of course!  So the problem never showed up!

To clarifty, I can ping the linux machines by name from the windows machines, so of course, nmbd is running:

```

$ ps aux|grep mbd
root      4795  0.0  0.2   5772  1428 ?        Ss   19:19   0:00 /usr/sbin/nmbd
root      4797  0.0  0.3   8536  2340 ?        Ss   19:19   0:00 /usr/sbin/smbd
root      4866  0.0  0.1   8536   956 ?        S    19:19   0:00 /usr/sbin/smbd
root      5147  0.0  0.4   8820  3000 ?        R    19:20   0:00 /usr/sbin/smbd

```

I'm going to leave DNS/WINS untill I've finished [virtual mailboxes on postfix](http://ubuntuforums.org/showthread.php?t=381887), which is a saga in itself.  Thanks for all your help in showing me what does what, I think this thread's got all the pointers in it I'll need!

Steve :)

---

### Post by Mr. C. on 2007-03-13
Steve,

Postfix will require a working DNS in order to function properly.  I don't know how far along you've gotten with your setup, but it will save you a fair amount of frustration to ensure your name services are working as you expect and as required for other services.

Cheers,
MrC

---

### Post by dannyboy79 on 2007-03-13
> **Mr. C. said:**
> Steve,

Postfix will require a working DNS in order to function properly.  I don't know how far along you've gotten with your setup, but it will save you a fair amount of frustration to ensure your name services are working as you expect and as required for other services.

Cheers,
MrC
you don't need to set your computer up as a dns server so don't get confused here. For a mail server to be used, people/machines will have to know how and where to connect to deliver mail for your domains. You need to edit the MX records of your domains DNS. Whether you run your own DNS server, or use a free DNS service. they mostly act the same, even though some has been fluffed up with a nice GUI. 
he just means that you need to have a fqdn (fully qualified domain name) I suggest using [www.dyndns.com](www.dyndns.com) and get a free one. I don't know what guide you're using but this one is great, and it uses dapper as it's base. [http://flurdy.com/docs/postfix/#install_distro](http://flurdy.com/docs/postfix/#install_distro)

---

### Post by Steve Smith on 2007-03-14
Thanks, I'm already fully paid up to dyndns!  I can do everything I need to do for now without local DNS, so I'll let this problem slide to the bottom of the todo pile :).

---

### Post by xyrer on 2007-03-22
Actually I found something that helped me with the same problem, right here on ubuntuforums, install winbind, it's in the repos. 
the post is [here]("http://ubuntuforums.org/showthread.php?t=88206")

---

### Post by dannyboy79 on 2007-03-23
> **xyrer said:**
> Actually I found something that helped me with the same problem, right here on ubuntuforums, install winbind, it's in the repos. 
the post is [here]("http://ubuntuforums.org/showthread.php?t=88206")

Show us the output from findsmb.

If your output shows what I thinks it's going to show than this is ONLY if Windows XP is your Local Master Browser or Master Browser or maybe even a wins server. I have my Ubuntu box overrid Winbloz strong desire to become 1 of these because I don't always have my winbloz box on. So I use my hosts file for internal name resolution (i think) I also have the nmbd daemon running, which I believe broadcasts my machines name to the other machines. Windows does this broadcasting thing thru Netbios over TCP/IP I think. (some1 please correct me if I am wrong) I don't have a wins server defined and I don't have an internal DNS server. Ayway, according to man winbindd:

[I]The service provided by winbindd is called `winbind` and can be used to
       resolve user and group information from a Windows NT server.  The  ser-
       vice  can  also  provide  authentication services via an associated PAM
       module.

The following simple configuration in the/etc/nsswitch.conf file can be
       used  to  initially resolve hostnames from /etc/hosts and then from the
       WINS server.

       hosts:         files wins[/I]


so what this is saying is that resolving hostnames is done first by the hosts file (files) and then a wins server (wins). The guide you followed, the config line was files dns wins so that merely means that it would use the hosts file, then a dns server, then a wins server. So if you have a wins server and want to use winbind than do so but if you don't have a wins server than there is no need for you to add wins to the nsswitch.conf file. Just add your hostnames and their ip's to your /etc/hosts file. Much easier! This will only work of course if you have all static ips. You can setup static ip's 2 different ways if your router or dhcp server has this setting. (this is so easy, I don't know why people are so scared to set static ip's) I mean maybe if it's a laptop but if it's a desktop, you dont go around attaching it to different routers do you, so there is no reason for dhcp. Either set the ip static thru the actual OS and it's mask and gateway etc etc or you can config your router or dhcp server so it'll always "reserve" that ip based on the interfaces MAC address. I can do this also thru my netgear, I turn on all computers, then log into my router, then I go LAN IP Setup and tell the dhcp to always give that MAC address the same IP. Also, if you make all your machines static by using the OS (you don't need to disable the dhcp server or router) and still want the dhcp server set so that when you introduce a new computer it gets an ip automatically (say some1 with a laptop comes in to visit) make sure you change your dhcp server ip's so that the range no longer includes the ones that you have statically assigned at the machine's.

For example: 
My router's DHCP server hands out ip's from 192.168.5.20 thru 192.168.5.254
and then I can use 192.168.5.2 thru 192.168.5.19 for static ips and there will never be a same ip problem.

---

### Post by xyrer on 2007-03-23
I have a doubt about that, I'm not an expert, more like a newbie actually, findsmb shows me the 4 computers on my workgroup, but I have no wins server configured, the fact that there are 2 windows machines there automatically means they serve as wins? I mean, ANY windows machine is a wins server on it's own? because I don't know yet how to configure a DNS or WINS server so I don't have any of them.

---

### Post by dannyboy79 on 2007-03-23
I asked you to put the output of it not just tell me how many it found. It'd like to make a point here and or learn something. If you could please post the output I would appreciate that.

---

### Post by xyrer on 2007-04-27
sorry for the delay, got into a lot of things lately.

this is the output of findsmb:```
*=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION -B 192.168.15.255
---------------------------------------------------------------------
192.168.15.1    SATENAU        [SATENA] [Windows Server 2003 R2 3790 Service Pack 1] [Windows Server 2003 R2 5.2]
192.168.15.6    APPS          +[SISTEMAS] [Unix] [Samba 3.0.22]
192.168.15.9    SYSTEMLAB     +[MSHOME] [Unix] [Samba 3.0.24]
192.168.15.27   EMBRAER170     [EMBRAER170] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.34   ING03          [ING03] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.35   REPARAB1       [REPARAB1] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.36   PROGRAMACION   [        TECNICO       ]
192.168.15.48   IMPORTA1       [        TECNICA       ]
192.168.15.56   PRESUP4        [        FINANCIERA    ]
192.168.15.57   OUTPUT         [        MERCADEO      ]
192.168.15.60   RESERVAS3      [        ADMINISTRATIVO]
192.168.15.65   MERCADEO2      [MERCADEO2] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.66   CARTERA3       [        FINANCIERA    ]
192.168.15.67   JURIDI         [JURIDI] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.69   CINGRES        [        FINANCIERA    ]
192.168.15.72   CALI_SERV2    +[        ASESORES      ]
192.168.15.73   AVIONICA       [        SATENA        ]
192.168.15.79   CINTERNO1      [        DIRECTIVO     ]
192.168.15.80   CONFIABILIDAD  [        ADMINISTRATIVO]
192.168.15.81   ALM-AER1       [        TECNICA       ]
192.168.15.85   COMERCIAL4     [        WSATENA       ]
192.168.15.88   ING05          [        TECNICO       ]
192.168.15.103  JEFEALMACEN    [JEFEALMACEN] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.104  CINGRES8       [CINGRES8] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.117  MERCADEO1      [MERCADEO1] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.124  ALMACENG2      [        FINANCIERA    ]
192.168.15.130  CONTAB5        [        FINANCIERA    ]
192.168.15.131  DTECNICA      +[DTECNICA] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.132  ING01          [ING01] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.133  ANALISISEMB    [ANALISISEMB] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.134  ANALISISEMB2   [ANALISISEMB2] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.143  ALMACEN3       [        OPERACIONES   ]
192.168.15.144  REEMBOLSOS     [        WSATENA       ]
192.168.15.146  CALIDAD8       [        ADMINISTRATIVO]
192.168.15.147  TELECOM2       [TELECOM2] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.148  COMUNICACIONES [        ADMINISTRATIVO]
192.168.15.164  CCO2ZT        +[CCO2ZT] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.203  SANANDRES      [        ADMINISTRATIVO]
192.168.15.204  VENTAS6        [        MERCADEO      ]
192.168.15.212  AUXILIARES3    [        ADMINISTRATIVO]
192.168.15.216  CINGRES2       [        WSATENA       ]
192.168.15.225  MANTTO         [        TECNICO       ]
192.168.15.235  VENTAS5        [        MERCADEO      ]
192.168.15.239  CINGRES50      [        FINANCIERA    ]
192.168.15.246  PRESUP2        [FINANCIERA] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.15.248  PRESUP1        [PRESUP1] [Windows 5.1] [Windows 2000 LAN Manager]

```

---

### Post by dannyboy79 on 2007-04-30
alright, well this looks to be way over my head as you have 5 local master browsers and no domain master browser and also all your workgroup's have different names so of course you wouldn't be able to ping anything by hostname. With this complex of a setup I would think that you're going to need a dns server for your local lan so that all the hostnames get refgistered etc etc. This is just my guess as I said this is WAY over my head. I only have 1 local  master brwoser on my lan, and i use workgroup and NOT domains. sorry I can't be of more help.

---

### Post by xyrer on 2007-04-30
Well, acutally i can ping by hostname just making the changes i said before; the reason? dont know but glad it works, I would like to know how it works but maybe I should learn more about networks, the local master browsers you mention are like that by themselves, I don't know how to make them like that so I didn't, I have no domains and the workgroups are like that because I haven't been able to organize them all but I'm on it.
By the time being, I can ping by hostname and have no dns server, cause "again" I don't know very well how to set it up. :P

Thanks anyway, and I hope ANY of my experience is useful to someone.

---

### Post by dannyboy79 on 2007-04-30
well I am guessing that it's using broadcasting. where each machine broadcasts itself to other machines. that's what netbios over tcp/ip is for windows and I believe that's the default for windows and in linux, if you have nmbd running than that's similar. glad it's working for you. 

i am curious, what is the output of smbtree?? it should only show the computers that are within the same workgroup as the computer that you perform the smbtree on. (i think anyway)

---

### Post by xyrer on 2007-04-30
the ouput is huge, and it shows every computer that is sharing something on the network in every workgroup, I have 200 pcs connected so you can imagine.

---

### Post by dannyboy79 on 2007-04-30
WOW, i didn't think that the SMBTREE is going to show across different workgroups. I am so confussed I thought I was learning somehting about samba. almost every samba guide tells you that you need the be in the same workgroup for share to work. well I guess that doesn't mean that it can't see it, maybe it just can't connect to it. huh???

---

