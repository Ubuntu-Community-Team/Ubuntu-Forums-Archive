---
title: "root servers"
date: 2013-03-22
forum: Server Platforms
---

### Post by sevensevenone on 2013-03-22
So, where do I find the root server list in ubuntu or (MS)winblows (the root server list(mostly in ubuntu)). I would really like to know atlease what I have  to google around for. I have not found anything relating to the list of root server IP addresses in ether of the two OS'es. I am hoping someone can point me to the placement of the file in one or both of the OS'es.

I plan on create a program that allows people to run it & them the addition of an IP addr to the list of DNS root servers for them. A RE-move-of-un-official-IP-addr program would be included (A list of all current not public DNS root servers). 

for EX: /file_path/OF/root_server/file_name.configuraition

Please help!, I really would like to know /*if anyone has any idea of*/ where it might be.

PS: I am currently learning C but a simplistic program for all CLI will come in the future.

---

### Post by Doug S on 2013-03-22
I think, but am not sure, that an Ubuntu computer would only have the DNS root servers list if it has is a DNS itself (or at least has one installed, maybe not running).
For bind9 at least, the file is /etc/bind/db.root
Please be aware the the file entry for the D root server is obsolete for all Ubuntu versions, other than raring. However, we are in the middle of the 6 months overlap period, and the old IP still works. For those that are interested, [bug report reference]("https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1090593").

I do not understand your description of what you want to do or why, but do not mess with root server stuff.

---

### Post by efflandt on 2013-03-22
Web search "get list of root servers with dig".

But it is not clear what you are trying to do. If you want to resolve your own private names or IPs, you should configure your nameserver(s) with "proper" zone files to resolve whatever non-public names to IPs or IPs to names (reverse lookup).  Then your nameserver(s) will use themselves for whatever zones they have, and public DNS for anything else. If you have multiple nameservers "properly" configured with one as master and other(s) as slaves, any updates to the master will propagate to any slaves.

---

### Post by sevensevenone on 2013-03-22
I am just trying to add my own IP addr to the list of DNS root servers so I can create my own personal TLD/web site names for the use of me and my friends.

Tho I am also wondering if the NS that I get from my ISP has anything to do with it.

If that is the case, would it be as simple as adding my own IP addr to the list of name servers.
8.8.8.8
8.8.4.4
Then setting up bind9 and adding my IP addr to the list of root servers in the software so that when when a URL request is typed in the query is sent to the public NS as well as my IP?

I am sorry if what I am saying is confusing, I am having a hard time putting what I am thinking into words.
Thank you for your patience and help.

---

### Post by dcstar on 2013-03-23
> **sevensevenone said:**
> I am just trying to add my own IP addr to the list of DNS root servers so I can create my own personal TLD/web site names for the use of me and my friends.
...........

```
sudo gedit /etc/hosts
```

---

### Post by sevensevenone on 2013-03-29
I have added my own IP addr to the list. I have also put the name "host" though not quite sure if it is needed. Is there anything else I need to know?

BTW Thank you very much dcstar.

---

### Post by darkod on 2013-03-29
If you only want a "private" website, editing the hosts file is enough. But note that you need to do that on the clients, not necesarily on the server machine. When on a client you type [http://mywebsite.privatedomain.com](http://mywebsite.privatedomain.com) it needs to know where to look for the webserver, the IP. That's why in the hosts file you would put something like:
192.168.1.15   mywebsite.privatedomain.com

Of course, the private IP needs to be the IP of your webserver.

That will work only from inside your LAN, if you want your friends to access it from outside, it's little more complicated. If the domain is private (not a real registered public domain), the entry in their hosts file needs to point to your public IP and your internet router has to be set to forward port 80 to 192.168.1.15. Now, your public IP might be dynamic and it can change over time, plus your ISP might be blocking port 80 to prevent you hosting home webserver.

---

