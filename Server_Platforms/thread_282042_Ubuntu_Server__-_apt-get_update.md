---
title: "Ubuntu Server  - apt-get update"
date: 2006-10-22
forum: Server Platforms
---

### Post by trunning on 2006-10-22
I just installed Drapper Drake and can access the sever via SSH via the internet. However when I try to run an apt-get update I get the following error messages? Any ideas?
 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

TIA,

Trunning

---

### Post by az on 2006-10-22
Maybe the repos were down at the time?

---

### Post by trunning on 2006-10-22
When I type in any of the following repo url in a webbrowser I am to reach the site with a directory listing.  With this I can probably conclude that that site is not down.  On my server, what can I check it see that I am able to go out to the internet. I tired a ping from the server, but it timed out.   Any suggestions to resolve this would be greatly appreciated.

A newbie,

Trunning

---

### Post by Tasu on 2006-10-22
hmmm! it looks like you didn't setup a dns server in:

/etc/resolv.conf

you have to add a line like: 

nameserver put-here-the-ip-of-the-dns

regards

---

### Post by Ronbo on 2006-10-22
Strangely enough I was just having the same problem when using
apt-get update.  I realized, after checking everything else, that I have been experimenting with Firehol and when I turned it off it solved my problem.  Not sure why, I could get to the net and browse any sites I visited but couldn't apt-get anything.  So if your running a firewall try disabling it.  Anyone know what rule I need in my conf file to let apt-get pass thru.

---

### Post by trunning on 2006-10-22
How do I setup a DNS server? 

Why would I have to setup a DNS server if my IP provider provides this service for me already?

TIA, 

Trunning

---

### Post by Tasu on 2006-10-23
Nono, not setup a DNS Server, but just tell your computer where is one... ok! you tell me that your provider should send dns informations via dhcp as well as ip informations, but from the errors you reported in the first post, it doesn't look like that... hmm! I have to investigate more, can you please ls /etc/resolv.conf and paste the result here?

Bye

---

### Post by trunning on 2006-10-23
I did an ls in the /etc/ directory and did not see any resov.conf file.  I have the  server edition installed and not the desktop. 

Thanks,
Trunning

---

### Post by trunning on 2006-10-26
It has been a week now and still haven't been able to get updates. Does anyone have an suggestions. 

Trunning

---

### Post by hortimech on 2006-10-26
if you have not got a /etc/resolv.conf file then you cannot connect to the internet! it holds the ip addresses of your nameservers, these you should be able to find out from your ISP.
can you please try this command "ifconfig eth0" and posting the outcome.

---

### Post by qra on 2006-10-26
I have got the same problem while trying to update with [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com)
I connect to the above site with Firefox if I deleete the "//":confused:

---

### Post by trunning on 2006-10-26
This is the outpu that I get when I run ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:01:02:7D:78:4E
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe7d:784e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98662 errors:0 dropped:0 overruns:1 frame:0
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32048907 (30.5 MiB)  TX bytes:59310 (57.9 KiB)
          Interrupt:9 Base address:0x6000

Thanks,

Trunning

---

### Post by Tasu on 2006-10-26
This ifconfig seems ok to me, but the lack of /etc/resolv.conf is really a problem, I cannot understand how it could have disappeared... O_O However, I own about 10 servers with ubuntu server installed and /etc/resolv.conf is always there, well it's important... without that your computer cannot know where a website is from it's name... hmmm!
if you don't have it you have to write one... but DHCP client have to fill it for you... can't understand what can be happened, so strange... O_O

---

### Post by trunning on 2006-10-26
How do I manually create this file?

Trunning

---

### Post by psycho78 on 2006-10-26
simply do a:

touch /etc/resolv.conf

and after this edit the file with:

sudo vi /etc/resolv.conf

and insert something like this:

nameserver 192.168.0.1 (this address is just an example, put the namserver address of your provider instead of this address)

close and save the file....that's it....

---

### Post by trunning on 2006-10-26
Sweet! Sweet! It works now. Thanks for the all the replies and suggestions. I am very very happy right now!!!

Trunning

---

### Post by Tasu on 2006-10-28
> **trunning said:**
> Sweet! Sweet! It works now. Thanks for the all the replies and suggestions. I am very very happy right now!!!

Trunning

Well I'm not, I would like to understand why in your installation the /etc/resolv.conf was not created... but I think I'm a bit too pedantic! O_O ^_^

---

