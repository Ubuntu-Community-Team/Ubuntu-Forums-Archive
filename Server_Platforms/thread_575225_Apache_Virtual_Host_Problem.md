---
title: "Apache Virtual Host Problem"
date: 2007-10-13
forum: Server Platforms
---

### Post by tgs1952 on 2007-10-13
Hello,

I have set up a virtual host on Apache2 following the directions Here [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2]("http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2")

It actually works fine - serves both html and php pages from a directory in my home directory.

However, shortly after the requested page loads, I get an very annoying Firefox error popup that says: "Url is not valid and cannot be loaded". I downloaded Epiphany and the same message appears.

What do I need to do to get rid of this problem?

Thanks in advance for any help.

---

### Post by MJN on 2007-10-14
Do you have a public URL that we can test and reproduce the error against? Without this the error could be in your config, HTML coding or browser so we're stabbing in the dark.

Mathew

---

### Post by tgs1952 on 2007-10-14
No there is no public URL. I set up the virtual host simply to create a development environment.

---

### Post by MJN on 2007-10-15
Ah, okay - that kind of makes it more difficult.
 
Have you tried a different browser?
 
Mathew

---

### Post by dmizer on 2007-10-15
if the client is linux, just enter your server's host name in your client's /etc/hosts file (as root).

it will end up looking something like this:
```
127.0.0.1 localhost tokkyu
127.0.1.1 tokkyu
192.168.0.16 [COLOR="Red"]server-hostname-here[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

192.168.1.50 printer
```

of course, replace 192.168.0.16 with your server's actual ip address.  this should work on a remote client, or if your server is local.

if your client is windows, you'll have to configure smb.conf on your server so that the "netbios name" option is datafilled with your server's hostname.

---

### Post by MJN on 2007-10-15
The initial page is loading so it's not a name query issue.
 
(Incidentally, Windows has a hosts file too)
 
Mathew

---

### Post by dmizer on 2007-10-15
> **MJN said:**
> The initial page is loading so it's not a name query issue.
 
(Incidentally, Windows has a hosts file too)
 
Mathew

i still think this is a quiry issue, i've run into it before.  setting up /etc/hosts on both the server and the client should fix the issue.

i was not aware that there was a hosts file on windows.  where is it, and does it function the same?

---

### Post by MJN on 2007-10-15
As things stand I suppose your suspicions cannot be ruled out entirely given we haven't got much to go on (I just don't think it is this given the request page **is** loading hence a name query must have been successfull. An easy way to rule it out is obviously to use the IP address instead).
 
The location of the hosts file on Windows depends on which version you are using - see [here]("http://en.wikipedia.org/wiki/Hosts_file#Location_and_default_content") for a list. Its purpose is indeed the same.
 
Mathew

---

### Post by dmizer on 2007-10-15
> **MJN said:**
> The location of the hosts file on Windows depends on which version you are using - see [here]("http://en.wikipedia.org/wiki/Hosts_file#Location_and_default_content") for a list. Its purpose is indeed the same.
 
Mathew

sorry for the hyjack ... i've been looking for that forever.  my vmguest machine can now visit my local server! :)

---

