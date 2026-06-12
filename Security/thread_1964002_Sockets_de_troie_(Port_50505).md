---
title: "Sockets de troie (Port 50505)"
date: 2012-04-23
forum: Security
---

### Post by latinlightning on 2012-04-23
Hello,  This morning I booted into my machine, opened up Firestarter and noticed an active connection on port 50505 with a service named "Sockets de troie." I did a ClamTK scan since I dual boot w/ Windows XP but it found nothing except for a PUA.JS.Xored in my home directory of my Ubuntu install under Firefox (home/jesse/.mozilla/firefox/vkra0r87.default/Cache/3/BF/596EDd01).

 I don't recall ever seeing this open until now. Recently I downloaded Metasploit and Metasploitable (vulnerable VM given by Metasploit) so I can start pen-testing. Could it be related to this? EVERY search result I saw for Socket de Troie turned out to be a trojan . . .

---

### Post by rookcifer on 2012-04-23
> **latinlightning said:**
> Hello,  This morning I booted into my machine, opened up Firestarter 

First of all, stop using Firestarter.  It has not been updated in like 5 or 6 years.  It is a defunct project.  Either use IPtables directly or UFW, which comes with Ubuntu.  Better yet is to use a router.

> and noticed an active connection on port 50505 with a service named "Sockets de troie." I did a ClamTK scan since I dual boot w/ Windows XP but it found nothing except for a PUA.JS.Xored in my home directory of my Ubuntu install under Firefox (home/jesse/.mozilla/firefox/vkra0r87.default/Cache/3/BF/596EDd01).

A google search says that PUA.JS.Xored is merely a piece of javascript code that redirects your browser to another site.  Since you're using Linux, this shouldn't be of much concern.  I am sure I have numerous pieces of such "malware" in my browser cache right now.  I am not concerned since 99.999% of it wont affect Linux.  Even if my browser gets redirected to a malicious site, I don't care.  My browser is updated, utilizes apparmor as well as Chromes sandbox.  So, you will be OK just deleting your browser cache every once in a while.


>  I don't recall ever seeing this open until now. Recently I downloaded Metasploit and Metasploitable (vulnerable VM given by Metasploit) so I can start pen-testing. Could it be related to this? EVERY search result I saw for Socket de Troie turned out to be a trojan . . .

Sockets de Troie seems to be a standard backdoor trojan that is well known and has been around for many years (going back to Win 95).  Since this trojan is so old and was written for Windows, I find it difficult to believe anyone still uses it, especially against Linux boxes.  Your theory of Metasploit seems reasonable to me because that project will often package old exploits like this for learning and testing purposes.  I would bet your hunch is correct.  

The only question is why is it connected?  I would bet it is only connected locally, which is why you need to look at netstat for a more accurate representation of what is actually connected where.

```
netstat -tlnp
```

should do the trick.

---

### Post by latinlightning on 2012-04-23
Thank you very much!

I have completely un-installed Firestarter and am now using Gufw 11.04.02. I tried looking for a way to update that since it looks like there's a newer version. Anyways, I will try to familiarize myself with this new firewall. I will give props though to Firestarter for at least letting me know of ALL my active connections.

The netstat -tlnp command definitely showed my local ip address (127.0.0.1:50505). Completely forgot about how valuable that command is. Thank you once again!

---

### Post by rookcifer on 2012-04-23
> **latinlightning said:**
> Thank you very much!

I have completely un-installed Firestarter and am now using Gufw 11.04.02. I tried looking for a way to update that since it looks like there's a newer version. Anyways, I will try to familiarize myself with this new firewall. I will give props though to Firestarter for at least letting me know of ALL my active connections.

The netstat -tlnp command definitely showed my local ip address (127.0.0.1:50505). Completely forgot about how valuable that command is. Thank you once again!

So it turned out to not be connected remotely but bound to localhost I take it?

---

### Post by latinlightning on 2012-04-23
Here's an exact screenshot of the result of netstat -tlnp:

---

### Post by rookcifer on 2012-04-23
I found this on google:

> The RPC service (:50505) on Metasploit Pro runs as ROOT, so any Metasploit Proaccount has privileged access to the system on which it runs. In malicious hands, this canlead to system or network damage. Please protect the service accordingly

So, yes, this is a result of Metaspolit.  Nothing to worry about.  Just be sure to secure port 50505, as it is listening to the outside world and is running as root!

---

