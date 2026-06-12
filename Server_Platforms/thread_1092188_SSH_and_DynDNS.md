---
title: "SSH and DynDNS"
date: 2009-03-10
forum: Server Platforms
---

### Post by mobbbx on 2009-03-10
:popcorn:Hi,

I have just installed Ubuntu 8.10 server edition. I wish to setup SSH so that i can remote access my server in the future. 

I have a dynamic ip address, so i applied for the free dynamic ip dns at dyndns.com. I have successfully installed ddclient and configured it as follows:

_Under /etc/ddclient.conf :_
pid=var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=members.dyndns.org
login=*****
passsword=*****
*****.blogsite.org
ssl=yes
daemon=300

_Under /etc/default/ddclient :_
run_ipup="false"
run_daemon="true"
daemon_interval="300"

My current network setup is as follows:
Internet-->ADSL router -->Ubuntu Server

I have opened the ports (22, 80, 443) of the ADSL router 2wire 2701HGV-E. Ping tests to my public ip address are also successful.

So my question is how do i check whether i can successfully SSH into my server because i am connected locally. And by the time i have to access remotely, it will be too late. 

And in the future i would like to make the ubuntu server into a web server. I have installed apache2 already. How to actually test whether it works?

---

### Post by windependence on 2009-03-10
Go to canyouseeme.org and test port 22 from the outside. If it says the port is open, that means the port is open AND a service is listening on that port. Then you should be good to go.

-Tim

---

### Post by issih on 2009-03-10
Just to mention that you should look at using something like denyhosts:

[http://denyhosts.sourceforge.net/faq.html#2_0](http://denyhosts.sourceforge.net/faq.html#2_0)

 to block any ip that repeatedly gets the log in details wrong, I think its in the ubuntu repositories. Obviously, you should also make sure that all user passwords on the box (especially those with sudo access) are strong, as you are now exposed to the less savoury side of the internet.

Hope that helps

---

### Post by mobbbx on 2009-03-10
Hi

thanks for the quick reponse. I have checked with canyouseeme.org to verify whether port 22 is open. It shows that it is open. 

Currently my network setup is as follows:

Internet--> ADSL Router -->[Laptop], [Ubuntu Server], [Desktop]

The free domain i created with dyndns.com is associated with the public dynamic ip address assigned (ADSL Router) to me by ISP. 

My question is.. when i try to ssh what is the code to type?

i have tried multiple ways:
[LIST] ssh [public ip address]
[/LIST]
[LIST] ssh [free domain by dyndns]
[/LIST]
[LIST] ssh [my username@public ip address]
[/LIST]
[LIST] ssh [localhost]
[/LIST]

All connections has either timed out or refused. I suspect it is the way i setup my network. I fairly new to Linux. Any Help is appreciated!

thanks!

---

### Post by windependence on 2009-03-10
You need to forward port 22 back to the IP address of your server. This is done in your router configuration.

-Tim

---

### Post by mobbbx on 2009-03-12
Hi Tim,
 
My ADSL router (2wire 2701HGV-E) configurations are as follows:

```

**Device: ubuntu-server**
Allowed Application           Protocol      Port            Public IP (Fictitious)
Web Server		         TCP	    80              116.14.161.33
SSH1		                 TCP	    22              116.14.161.33
HTTPS Server		         TCP	    443             116.14.161.33
HTTP Server		         TCP	    80-81           116.14.161.33
HTTP Server                      UDP	    80-81           116.14.161.33
SSH2		                 UDP	    22              116.14.161.33
SSH Server		         TCP	    22              116.14.161.33

```

Port 22 is open according to [http://canyouseeme.org]("http://canyouseeme.org"). Is there anything else i'm not doing or anything i'm doing wrong? 

the ubuntu server is currently set up at my home through wired ethernet connection.

Internet --> ADSL Router (Fictitious Public IP Address: 116.14.161.33) --> [Ubuntu Server (Username: AAA, Private IP 192.168.1.67)], [Desktop (Username: BBB, Private IP 192.168.1.68)]

I am able to ssh it within my home network by typing the following code:

```
ssh AAA@192.168.1.67
```

I am able to ping my public ip address from my home. 
```

rudy@ubuntu-server:~$ ping 116.14.161.33 (Fictitious Public IP Address)
PING 116.14.161.37 (116.14.161.37) 56(84) bytes of data.
64 bytes from 116.14.161.33: icmp_seq=1 ttl=255 time=6.10 ms
64 bytes from 116.14.161.33: icmp_seq=2 ttl=255 time=1.80 ms
64 bytes from 116.14.161.33: icmp_seq=3 ttl=255 time=2.81 ms
64 bytes from 116.14.161.33: icmp_seq=4 ttl=255 time=2.10 ms
64 bytes from 116.14.161.33: icmp_seq=5 ttl=255 time=1.32 ms
64 bytes from 116.14.161.33: icmp_seq=6 ttl=255 time=0.673 ms
64 bytes from 116.14.161.33: icmp_seq=7 ttl=255 time=1.78 ms
64 bytes from 116.14.161.33: icmp_seq=8 ttl=255 time=1.05 ms
64 bytes from 116.14.161.33: icmp_seq=9 ttl=255 time=6.25 ms
64 bytes from 116.14.161.33: icmp_seq=10 ttl=255 time=1.46 ms
^C
--- 116.14.161.33 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9077ms
rtt min/avg/max/mdev = 0.673/2.539/6.252/1.902 ms

```

i haven't had the chance to ssh it remotely. if i do not set it up correctly, by the time i need to access ubuntu server remotely it will be too late. 

Please Help!

Many thanks!

---

### Post by volkswagner on 2009-03-12
As Tim mentioned the router should be **forwarding** port 22 to your **internal** server ip.

Also where are you trying to access it from.  If the remote location does not allow traffic on port 22 that may be the problem.

There are only a few items to heed the process.

Software/hardware Firewall (both locations)
blocked port by ISP (both locations)
Router Port forward to server at home
Not to mention if you set up DenyHost


Note:  It appears you have port 22 mentioned twice for tcp on your router.

---

### Post by mobbbx on 2009-03-12
Hi guys..

thanks for all the help and advice! i am able to successfully ssh to my ubuntu server!

However i have another question... regarding sftp
I am currently using Mac OS X 10.5 (Leopard) so i ssh to the ubuntu server via its Mac terminal.
I am trying to sen
When i was trying to send files from local OS X to remote ubuntu server. The file is stored locally (Mac OS X) under Documents folder. But i can't seem to be able to do it. Please see the following code:

```

sftp> put /usr/local/Documents/<Directory>
stat /usr/local/Documents/<Directory>: No such file or directory

sftp> put /Macintosh HD/Users/Rudy/Documents/Interests
stat /Macintosh: No such file or directory

```

I'm sure there's something wrong with the path i typed in. 

Help anyone?

---

### Post by hyper_ch on 2009-03-12
are you trying to send by the command line?

---

### Post by Hobgoblin on 2009-03-12
> **mobbbx said:**
> 
```

sftp> put /usr/local/Documents/<Directory>
stat /usr/local/Documents/<Directory>: No such file or directory

sftp> put /Macintosh HD/Users/Rudy/Documents/Interests
stat /Macintosh: No such file or directory

```

I'm sure there's something wrong with the path i typed in. 


You'll need to use quotes around the file/pathname if you want to use file/folder names with spaces in them.

---

### Post by Saghaulor on 2009-03-12
Noob question.

Does the router have to support sshd? I've read in places that one should dl a custom firmware for one's router, say dd-wrt. I have a Belkin.

I'm trying to connect from a wan ip to my lan. I haven't had much success yet. I'm not sure what to do.

I've tried to forward the ports to my statically assigned server.
I can successfully connect via the lan, but I'm not sure what to do from wan to lan.

Also, when I connect it drops me into the root directory. If I want to do other things, aside from browsing files, say, use the terminal, what do I do?

---

### Post by windependence on 2009-03-12
> **mobbbx said:**
> Hi guys..

thanks for all the help and advice! i am able to successfully ssh to my ubuntu server!

However i have another question... regarding sftp
I am currently using Mac OS X 10.5 (Leopard) so i ssh to the ubuntu server via its Mac terminal.
I am trying to sen
When i was trying to send files from local OS X to remote ubuntu server. The file is stored locally (Mac OS X) under Documents folder. But i can't seem to be able to do it. Please see the following code:

```

sftp> put /usr/local/Documents/<Directory>
stat /usr/local/Documents/<Directory>: No such file or directory

sftp> put /Macintosh HD/Users/Rudy/Documents/Interests
stat /Macintosh: No such file or directory

```I'm sure there's something wrong with the path i typed in. 

Help anyone?

On my MacBook Pro I use either Fugu, or Cyberduck to transfer files through sftp. It works great! Give it a try.

-Tim

---

### Post by windependence on 2009-03-12
> **Saghaulor said:**
> Noob question.

Does the router have to support sshd? I've read in places that one should dl a custom firmware for one's router, say dd-wrt. I have a Belkin.

I'm trying to connect from a wan ip to my lan. I haven't had much success yet. I'm not sure what to do.

I've tried to forward the ports to my statically assigned server.
I can successfully connect via the lan, but I'm not sure what to do from wan to lan.

Also, when I connect it drops me into the root directory. If I want to do other things, aside from browsing files, say, use the terminal, what do I do?

No, you should be fine with the Belkin. I use several of these. I have never heard of a router not supporting ssh either.

If you are trying to access your external IP from inside your network, that won't work unless you have a router that does NAT reflection, and those are usually the corporate type.

Go to canyouseeme.org and check that it can see port 22. If so, you should be able to get in from the outside.

-Tim

---

