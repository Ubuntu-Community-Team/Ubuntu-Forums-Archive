---
title: "[SOLVED] Can't ssh server name can ssh ip of server"
date: 2007-09-23
forum: Server Platforms
---

### Post by volkswagner on 2007-09-23
Please forgive me if this has been posted.  I have made several search request on the forum but no results.

Problem:  New server installed 6.06 lamp at install.  When i 
```

ssh "myusername"@server1
```

I get this in return

> ssh: server1: Name or service not known

when I

```
ssh "myusername"@"ipaddress"
```

I get password prompt and i am in

my prompt looks like this and i am sure the name is correct

> eric@server1:/$ 

any suggestions?

---

### Post by Raymond Day on 2007-09-23
I would install webmin. Then you can go to users and edit or add.

-Raymond Day

---

### Post by conjur3r on 2007-09-23
We kinda take that simple name resolution for granted when working in a Windows environment.  That is taken care of by a WINS server which maps netbios names to their IP addresses (only works in the same subnet).  There is a WINS component in Samba but I'm not quite sure it has the same effect for linux boxes.

Before trying SSH, try a simple ping.  If that doesn't work then no service will using the name.

If it really peaves you alot, try either adding entries into your /etc/hosts file or running a local DNS server and adding a record in there with the mapping.

---

### Post by volkswagner on 2007-09-23
Thanks for the replies.

> I would install webmin. Then you can go to users and edit or add

I wanted to install anyway, I really dig it.  I still need to enter ip in the address bar, the server1 does not work under Webmin.

> 
Before trying SSH, try a simple ping. If that doesn't work then no service will using the name

Only ping of ip works not the server name.
> 
If it really peaves you alot, try either adding entries into your /etc/hosts file or running a local DNS server and adding a record in there with the mapping.

Does not peave me at all.  I thought something was broken.  Both the webmin documents and the lamp/ssh documents I have read use the name as an option to access.  I will research the local DNS.  
What entry shall I add to /etc/hosts to get name resolution.

---

### Post by MJN on 2007-09-23
```
<ip.address.of.server1> server1
```Check out **man hosts** for the full lowdown.

Mathew

---

### Post by steve.horsley on 2007-09-23
The file you need to edit is **/etc/hosts**. This is used to look up name->address even before asking a DNS server. The format is address first, then names on the same line.

---

### Post by volkswagner on 2007-09-23
Well I edited the /etc/hosts file and verified changes. See below

I still can only ssh using ip address.  

Maybe there is problem with bind9 itself?  Will check it is running.

Here is /etc/hosts.....See any problems? 192.168.1.109 is fixed to the server. Server is connected to same router as my network machines.

127.0.0.1       localhost.localdomain localhost
192.168.1.109   server1.example.com server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
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
~                                                                               
~                                                                               
"/etc/hosts" 10L, 289C                                        1,1           All

---

### Post by MJN on 2007-09-23
That looks fine. Just to confirm though, you are editing /etc/hosts on the client?

Also, BIND has nothing to do with it as we're not using DNS here.

Mathew

---

### Post by volkswagner on 2007-09-23
I did not do anything to the client.  All edit has been on server.

---

### Post by volkswagner on 2007-09-23
Thanks for the help.  I did not know I needed to edit the client.  I added server ip and name all is well!

Ubuntu and the forum ROCK!

---

