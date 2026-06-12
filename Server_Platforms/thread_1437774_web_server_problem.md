---
title: "web server problem"
date: 2010-03-24
forum: Server Platforms
---

### Post by ronhagley on 2010-03-24
Hi all,

I'm sure this is something I'm getting wrong but I have spent over a week trting to get this working and failing.
I have set up Ubuntu server with EHCP on an old laptop. This appears to be functioning as far as I can tell.
The server will only ever be used as a test platform on a local network - never needing to serve to internet.
The server IP details are as follows:
IP address 192.168.0.4
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
Version is Karmic Koala

I have set up a domain using EHCP called mydomain (this is a local domain)the ftp username is letmein and the ftp password is cats.
When I use filezilla with the host set to 192.168.0.4 and use the appropriate password and username I get access and can see mydomain and the httpdocs folder etc.
However I cannot ftp the server using mydomain as the host
nor can I access the server from a browser. I tried the IP address and just get the EHCP control panel if I use mydomain  I get directed to an external website.

I'm sure I am missing something fundamental here but cannot understand what!
Can anyone kindly help a dumbo newbie please. Many thanks in anticipation

---

### Post by KB1JWQ on 2010-03-24
Computers can't read minds.  They need to have some method of translating between IP addreses and hostnames-- we call it DNS.

Set your local DNS server to equate server.domain.com with 192.168.0.4, and this should start working.

---

### Post by terazen on 2010-03-24
If filezilla client works then web browser should work like this:
```
ftp://192.168.0.4
```

Also, in addition to what KB1 said, you could add something like this in your /etc/hosts```
192.168.0.4    somesitename
```

Playing with bind is probably cooler though if you're just trying to learn stuff.  Editing the hosts file on the laptop is kinda cheating. ;)

---

### Post by ronhagley on 2010-03-25
OK I understand the concept of DNS when finding web addresses -but where do I find the LOCAL dns server you mention?
Is this on the Ubuntu server or on the client PCs?
If on client PCs then I cannot use that method as I do not have access to change any files on them
If on the Ubuntu server - where do I find it and how do I edit the file please.

Sorry to be so dumb - but we all start somewhere - its just that my start point is so much lower!

Ron

---

### Post by new_tolinux on 2010-03-25
Ok, if you have a local DHCP server from which your webserver is getting it's IP, then the name to use would be: [http://webserver.domain](http://webserver.domain)
For example: my webserver is called webserver and the domain/group is just workgroup then it would be:
[http://webserver.workgroup](http://webserver.workgroup) should work fine from every browser running on a machine that gets its IP from the same DHCP server

If the webserver has a static IP, then you shoud edit the /etc/hosts file (or in Windows C:\Windows\System32\drivers\etc\hosts) on every client you're going to use, adding this line:
```
192.168.0.4 webserver
```

Where you can replace webserver with almost anything you want, unless it's not the name of another computer in your network. Also don't use dots in the name.

---

### Post by ronhagley on 2010-03-26
> **new_tolinux said:**
> Ok, if you have a local DHCP server from which your webserver is getting it's IP, then the name to use would be: [http://webserver.domain](http://webserver.domain)
For example: my webserver is called webserver and the domain/group is just workgroup then it would be:
[http://webserver.workgroup](http://webserver.workgroup) should work fine from every browser running on a machine that gets its IP from the same DHCP server

If the webserver has a static IP, then you shoud edit the /etc/hosts file (or in Windows C:\Windows\System32\drivers\etc\hosts) on every client you're going to use, adding this line:
```
192.168.0.4 webserver
```

Where you can replace webserver with almost anything you want, unless it's not the name of another computer in your network. Also don't use dots in the name.

Hi,

I cannot edit the settings on the clients as I do not have admin rights to them. Can I do anything to the server settings instead?

---

### Post by ronhagley on 2010-03-26
Hi, and thanks for the reply and help. I have tried editing the /etc/hosts file as suggested but when I do so I am prevented from saving it.

Your suggestion re the web address works OK, but I really need http access to view the files not ftp.
The server is intended to be used in a small classroom environment where students have to demonstrate an ability to publish a site to a server using ftp. They also have to prove its existance via http.
As the venue has locked down external ftp access they have to work on a local server rather than an existing web hosting company.



Any suggestions please - sorry to appear thick but all this Linux is new to me.

Ron

---

### Post by kamaji792 on 2010-03-26
> **ronhagley said:**
> Hi, and thanks for the reply and help. I have tried editing the /etc/hosts file as suggested but when I do so I am prevented from saving it.

Have you tried:
```
sudo gedit /etc/hosts
```
You can replace *gedit* with your favourite editor.  I use **vim**.

Atb

---

### Post by spynappels on 2010-03-26
> **kamaji792 said:**
> Have you tried:
```
sudo gedit /etc/hosts
```
You can replace *gedit* with your favourite editor.  I use **vim**.

Atb

I think the /etc/hosts file he needs to edit is on a Windows client......

---

### Post by kamaji792 on 2010-03-27
Ah...  OK

Host file on Windows PC is:
```
%SystemRoot%\system32\drivers\etc\hosts
```
probably.
```
C:\Windows\system32\drivers\etc\hosts
```

Check out this like for hosts file location:

[http://en.wikipedia.org/wiki/Hosts_file#Content_and_location](http://en.wikipedia.org/wiki/Hosts_file#Content_and_location)

---

### Post by endkill on 2010-03-29
If you are using a standard Linksys house/wireless 4 port router. You need to set the DNS and static IP in the router. 192.164.0.4 is off the dynamic range. 

Generally the dynamic range is between: 192.164.0.100 - 192.164.0.200. 
Or if a newer router between: 192.164.1.100- 192.164.1.200.

Any thing that you put out of the range has to go in to the static table otherwise it's likley to be ignored. Also you need to try to figure out how to set the Windows to check the router for DNS.

---

