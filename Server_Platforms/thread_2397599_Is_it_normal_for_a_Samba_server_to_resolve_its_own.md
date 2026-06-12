---
title: "Is it normal for a Samba server to resolve its own hostname?"
date: 2018-07-31
forum: Server Platforms
---

### Post by cpplearner on 2018-07-31
The dnsmasq on my router indicates that **a Samba server on my subnet keeps trying to resolve its own hostname**. What I mean by "its own hostname" is the machine's hostname on which the Samba server reside. For some reason, it caused an initial delay to browsing, so I had to manually put a record on /etc/hosts.

What I don't understand is **why a Samba server needs its own hostname resolved**? _It's a server, not a client!_ Of course, the client certainly need an IP address, since it has to _connect_ to some server! But, in the case of a server, it suffices to just wait! It's a client that connects!

Let's suppose that the server needed its own IP address. Why does it ever need to make a DNS query, rather than to consult the interfaces available on kernel? Why not use a simple system call to inspect IP addresses assigned to its interfaces?

---

### Post by wyliecoyoteuk on 2018-08-01
It needs to announce itself to the other computers on the network.
Part of the SMB/CIFS network protocol involves distributed host data for browsing.
It also needs to take part in master browser elections.

[https://msdn.microsoft.com/en-us/library/cc224434.aspx](https://msdn.microsoft.com/en-us/library/cc224434.aspx)

---

### Post by 1clue on 2018-08-01
If you're using a service like that, it's probably a good idea to configure dns for your domain. And yes I realize this may just be 2 computers at your home.

I would configure an authoritative domain for your local network, with a static IP for servers and dynamic dns for clients, tied to your dhcp server. Which means you probably have to have one of those too, and stop dhcp from your home router.

I would recommend that you also have a caching dns for everything else. It will speed up your entire network.

---

### Post by slickymaster on 2018-08-01
Thread moved to **Server Platforms** for a better fit

---

### Post by cpplearner on 2018-08-01
> **wyliecoyoteuk said:**
> It needs to announce itself to the other computers on the network.

Can just making a DNS query act like an announcement? How does a DNS server knows that some DNS queries should be treated as such?

---

### Post by 1clue on 2018-08-01
> **cpplearner said:**
> Can just making a DNS query act like an announcement? How does a DNS server knows that some DNS queries should be treated as such?

The dns server does not make the announcement. The samba server does.

The thing is, all the systems in the network need to use the same names. /etc/hosts doesn't work well because even if you intend every file to have the same exact text, sometimes it does not happen for any number of reasons. That fact is the reason why DNS was invented in the  first place.

---

### Post by 1clue on 2018-08-01
Another option might be to turn off dns queries for the samba server, but I don't know for sure if that's possible. Other services like apache2 allow it. I wouldn't do that for samba personally but it would be a possible way to stop the queries you're talking about. You would need to do your shares by ip address then.

---

### Post by cpplearner on 2018-08-01
1. The thing is, when I use an IP address instead, the same problem occurs. The Samba server still make a DNS query, trying to resolve its own hostname.

2. I totally agree with you. The DNS server do not make an announcement for Samba. **That's exactly why I don't understand this situation.** The DNS server does nothing for the Samba server, but why does the server still make a DNS query? For resolving an IP address? The server can do this by itself. For advertising its existence for the sake of Samba protocol, it's clearly false, as you pointed out. Then, what? What's the purpose of the DNS query that the Samba server makes?

>> I just want to understand why this is happening. I'm just satisfied by the /etc/hosts solution.

---

### Post by 1clue on 2018-08-02
1. You would have to go into the samba configuration files and turn off DNS resolution. No matter what, in normal circumstances, it will try to resolve the name.

2. I think we're miscommunicating. I don't know what you're claiming is false.

The DNS server does these things for clients who ask:
[LIST=1]
[*]Find the IP address(es) to go with a domain name.
[*]Find the domain name(s) to go with an IP address.
[/LIST]

That's it. The response ONLY goes to the client. Nobody else sees the transaction.

Samba, by default, works with names. To use IP addresses only would be incredibly complicated for most people. Because of this, Samba by default tries to find out what its name is from DNS.

My comment was that it MAY BE POSSIBLE to turn off dns resolution for Samba through the config file. I don't know if that's possible for Samba, but it's possible for other services on Linux so I mentioned it.

Using names with Samba for any group of normal people is going to be required. I don't know of any sites where they would even consider doing otherwise. DNS is probably not technically necessary, but practically speaking it's the only way to go. That way every host has the same names matching up with the same IP addresses, so people can actually share files.

---

### Post by wyliecoyoteuk on 2018-08-02
>     
Host name resolution generally uses the following sequence:
    1.The client checks to see if the name queried is its own.
    2.The client then searches a local Hosts file, a list of IP address and names stored on the local computer.
    3.Domain Name System (DNS) servers are queried.
    4.If the name is still not resolved, NetBIOS name resolution sequence is used as a backup. This order can be changed by configuring the NetBIOS node type of the client.


Besides anything else, the DNS server is considered *Authoratitive*for the domain.
The local hosts file is used to override this.
Samba uses DNS these days, whereas it used to use WINS.

---

### Post by cpplearner on 2018-08-02
Guys, I think you're all talking about a Samba _client_. A DNS server can certainly be useful for a Samba client. Rather than typing an IP address, It conveniently asks a DNS server. Furthermore, as @wyliecoyoteuk pointed out, its behavior can be overridden by /etc/hosts. I do understand that.

However, my question is why a Samba _server_ needs a DNS server? Moreover, it tries to resolve its own hostname! What for? In order to connect itself? I don't know.

---

### Post by 1clue on 2018-08-02
Not talking about the client.

The server is making advertisements. Part of that advertisement is the name. The server does a dns lookup so it knows for sure that its configured name is reachable by name for other hosts on the network.

If the server's /etc/hosts looks like this:


192.168.1.21       fooserver.lan


and your client has an /etc/hosts like this:

192.168.1.21       barserver.lan


and dns has 192.168.1.21 as jefflaptop.lan

then your samba server is pretty much unreachable.

Servers generally make some sort of sanity test as they start up.

---

### Post by cpplearner on 2018-08-02
> **1clue said:**
> Servers generally make some sort of sanity test as they start up.

**Finally, the mystery solved. =D**

IMO, that part of the protocol seems nonsense to me. What differences could there be by doing that particular test? If the intention was to fix this, at least they should inform the user so that some kind of modifications to a DNS server or /etc/hosts can be made. Also, a Samba server **alone **can't do anything about it, even if they know it. Third, the client can connect to the server by an IP address, in which case a hostname lookup is not necessary in the first place.

---

### Post by 1clue on 2018-08-02
You assume a technically skilled operator at the client machine. You should instead picture your grandmother at the keyboard.

Most likely any discrepancies will result in an error logged to the system log, or to the samba log if there is one. For really bad errors they may blow an error on the command line, but those generally go to the system log for server processes anyway.

Samba, like most server software, requires no GUI. So it's not going to pop up a dialog telling you what's wrong or how to fix it. Like all system processes, it will write to a file in the /var/log directory. It's your responsibility to check your logs and ensure that anything of warning priority or higher gets addressed. I advise doing this for EVERY error in the log, so that when some actual failure happens (hardware for example) you can search on warnings and up and figure out what your problem is faster.

---

### Post by wyliecoyoteuk on 2018-08-03
The server/client relationship is two way.
The client connects to the server by IP address anyway, the hostname mapping is for convenience.
But the hostname, like the IP address, needs to be unique on the network.
The server also needs to know its FQN for example it might have the hostname fred, but in DNS that might be fred.somedomain.local

---

### Post by 1clue on 2018-08-03
FWIW the DNS lookup is really frequent in all sorts of situations you might not think it would be. For example, when you login to Linux there's a DNS lookup. If you don't have DNS or an /etc/hosts entry for your /etc/hostname, you're likely to have a minute or two of waiting while you login because the dns query needs to timeout before your login can continue.

---

### Post by irojas31 on 2018-08-05
Can I make the configuration of the recycle bin with the active directory? I did tests, deleting but it only gives me the information of a user that had deleted a folder, what other parameters are necessary so that they are shown of all the users who deleted some file or folder?
This is my configuration


----------------
# Global parameters
[global]
        workgroup = SOPORTE
        realm = SOPORTE.LOCAL
        netbios name = DC1
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbindd, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes
        winbind enum users = yes
        winbind enum groups = yes


[netlogon]
        path = /var/lib/samba/sysvol/soporte.local/scripts
        read only = No


[sysvol]
        path = /var/lib/samba/sysvol
        read only = No
[TI]
        path = /opt/sistemas
        read only = no


[RECYCLE BIN]
        comment = Recycle Bin
        path = /opt/recycle
        public = yes


# Recycle Bin
        vfs objects = recycle full_audit
        recycle:repository = /opt/recycle/recycle_TI/%u/%m
        recycle:versions = Yes
        recycle:keeptree = Yes
        recycle:touch = yes
----------------------------------------
root@DC1:/opt/recycle/recycle_TI# ll
total 12
drwx------ 3 SOPORTE\cmiranda users 4096 ago  4 19:13 ./
drwxrwxr-x 3 root             users 4096 ago  4 19:13 ../
drwx------ 3 SOPORTE\cmiranda users 4096 ago  4 19:13 SOPORTE\cmiranda/

---

### Post by wildmanne39 on 2018-08-05
Hello and welcome to the forum irojas31, please start your own thread instead of asking for help in someone else's. If you read what this thread is about it is not even the same topic as what you posted about.

Thanks

---

