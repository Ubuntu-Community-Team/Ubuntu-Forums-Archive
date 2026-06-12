---
title: "Unable to aptitude install pure-ftpd-mysql"
date: 2010-07-20
forum: Server Platforms
---

### Post by Maradona on 2010-07-20
Hi all,

I am having trouble to "aptitude install pure-ftpd-mysql" with my ubuntu server 9 version.  Please give me a hand if anyone has a better idea.  

Thank you so much for your help.


> root@love:/# aptitude install pure-ftpd-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libcap1{a} pure-ftpd-common{a} pure-ftpd-mysql 
0 packages upgraded, 3 newly installed, 0 to remove and 36 not upgraded.
Need to get 352kB of archives. After unpacking 1061kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libcap1 1:1.10-14build1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe pure-ftpd-common 1.0.21-11.4ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe pure-ftpd-mysql 1.0.21-11.4ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcap/libcap1_1.10-14build1_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcap/libcap1_1.10-14build1_i386.deb:) Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

---

### Post by richardjh on 2010-07-20
Relevant line is 
```

Could not resolve 'us.archive.ubuntu.com'
```

Can you resolve this name now? It may have been a temporary error
Use

```
$ nslookup us.archive.ubuntu.com
```

You should see 

```

richardjh@ubuntu:~$ nslookup us.archive.ubuntu.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    us.archive.ubuntu.com
Address: 91.189.88.31
Name:    us.archive.ubuntu.com
Address: 91.189.88.40
Name:    us.archive.ubuntu.com
Address: 91.189.88.46
Name:    us.archive.ubuntu.com
Address: 91.189.88.45
Name:    us.archive.ubuntu.com
Address: 91.189.88.30
Name:    us.archive.ubuntu.com
Address: 91.189.92.166

```

You need to sort out your name resolution before you can continue.

---

### Post by Maradona on 2010-07-20
Dearest Rich,

Thank you so much for helping.  BTW I really got a situation.  

> root@server:/# nslookup us.archive.ubuntu.com
;; connection timed out; no servers could be reached

root@server:/# nslookup us.archive.ubuntu.com
;; connection timed out; no servers could be reached

root@server:/# nslookup us.archive.ubuntu.com
;; connection timed out; no servers could be reached

---

### Post by richardjh on 2010-07-21
To check your are online and this is just DNS issue, can you ping 91.189.88.31? 

If you can then you need to 

Either
* check your settings in /etc/resolv.conf and make sure you have the correct nameservers set.

Or if you are running a GUI 
* you can use nm-applet (looks like two arrows in the notification are). 
Right click on it, select "Edit Connections" highlight the connection and select "Edit" and set your DNS server in there.

---

### Post by Maradona on 2010-07-22
Thx Rich

I can ping without a sweat. 

> 
 ping 91.189.88.31
PING 91.189.88.31 (91.189.88.31) 56(84) bytes of data.
64 bytes from 91.189.88.31: icmp_seq=1 ttl=48 time=166 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=3 ttl=48 time=166 ms
64 bytes from 91.189.88.31: icmp_seq=4 ttl=48 time=170 ms
64 bytes from 91.189.88.31: icmp_seq=5 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=6 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=7 ttl=48 time=165 ms
64 bytes from 91.189.88.31: icmp_seq=8 ttl=48 time=164 ms
64 bytes from 91.189.88.31: icmp_seq=9 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=10 ttl=48 time=165 ms
64 bytes from 91.189.88.31: icmp_seq=11 ttl=48 time=165 ms
64 bytes from 91.189.88.31: icmp_seq=12 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=13 ttl=48 time=166 ms
64 bytes from 91.189.88.31: icmp_seq=14 ttl=48 time=176 ms
64 bytes from 91.189.88.31: icmp_seq=15 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=16 ttl=48 time=171 ms
64 bytes from 91.189.88.31: icmp_seq=17 ttl=48 time=165 ms
64 bytes from 91.189.88.31: icmp_seq=18 ttl=48 time=166 ms
64 bytes from 91.189.88.31: icmp_seq=19 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=20 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=21 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=22 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=23 ttl=48 time=165 ms
64 bytes from 91.189.88.31: icmp_seq=24 ttl=48 time=164 ms
64 bytes from 91.189.88.31: icmp_seq=25 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=26 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=27 ttl=48 time=168 ms
64 bytes from 91.189.88.31: icmp_seq=28 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=29 ttl=48 time=169 ms
64 bytes from 91.189.88.31: icmp_seq=30 ttl=48 time=167 ms
64 bytes from 91.189.88.31: icmp_seq=31 ttl=48 time=172 ms
64 bytes from 91.189.88.31: icmp_seq=32 ttl=48 time=166 ms
64 bytes from 91.189.88.31: icmp_seq=33 ttl=48 time=165 ms



my  /etc/resolv.conf is empty.   

Do I need to install anything for  /etc/resolv.conf?

---

### Post by richardjh on 2010-07-23
As I previously posted as you can ping by IP but not name you need to set your name server somewhere:

Either
* check your settings in /etc/resolv.conf and make sure you have the correct nameservers set.

For example, the contents of /etc/resolv.conf should look something like:

```
nameserver 192.168.1.1
```Or if you are running a GUI 
* you can use nm-applet (looks like two arrows in the notification are). 
Right click on it, select "Edit Connections" highlight the connection and select "Edit" and set your DNS server in there.

---

### Post by Maradona on 2010-08-24
Rich,

Thank you for sharing your expertise on that issue.  I am wondering what if I don't have my dns server but using afraid.org to point to my system?

---

### Post by arrrghhh on 2010-08-24
> **Maradona said:**
> Rich,

Thank you for sharing your expertise on that issue.  I am wondering what if I don't have my dns server but using afraid.org to point to my system?

There are several DNS options you have.  Most just use their router (which is why Rich suggested using 192.168.1.1, assuming that's the IP of your router/gateway).

Others use 208.67.222.222 and 208.67.220.220 as their DNS servers - which is what I do, that uses OpenDNS as your DNS provider.

I'm not sure what you mean you're using afraid.org to point to your system...  Ah, after a quick google search it appears that is a service similar to DynDNS.  So what Afraid.org does for you is basically the exact opposite of what your problem is.  Afriad.org makes it so people can type a friendly domain name (like google.com) and get your site.  You basically need the opposite, currently your server doesn't know how to convert google.com into an IP address (which is what a DNS server does for you).

Make sense?

---

### Post by Maradona on 2010-08-26
> **arrrghhh said:**
> There are several DNS options you have.  Most just use their router (which is why Rich suggested using 192.168.1.1, assuming that's the IP of your router/gateway).

Others use 208.67.222.222 and 208.67.220.220 as their DNS servers - which is what I do, that uses OpenDNS as your DNS provider.

I'm not sure what you mean you're using afraid.org to point to your system...  Ah, after a quick google search it appears that is a service similar to DynDNS.  So what Afraid.org does for you is basically the exact opposite of what your problem is.  Afriad.org makes it so people can type a friendly domain name (like google.com) and get your site.  You basically need the opposite, currently your server doesn't know how to convert google.com into an IP address (which is what a DNS server does for you).

Make sense?
Thank you for your help and I see what you mean.  I have been using linksys rounter to point http to port 8080 and ftp point to port 33 ... etc with local 192.168.1.100 as a result I set my /etc/resolv.conf as follow.  
    

> 
nameserver 192.168.1.100
             


~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
~                                                                          
"resolv.conf" [readonly] 4L, 28C                         3,0-1         All

However, I am still unable to set up my ftp server.  What next I should do???

---

### Post by arrrghhh on 2010-08-26
> **Maradona said:**
> However, I am still unable to set up my ftp server.  What next I should do???

Ok, one step at a time.  What is wrong with your FTP server?  You can hit it on your LAN I assume, but cannot hit it from the WAN?

With that said, your resolv.conf should not point back to your server, it should point to your router or perhaps the OpenDNS addresses I gave you - some prefer their ISP's DNS server because that in theory should perform the quickest lookups...

---

