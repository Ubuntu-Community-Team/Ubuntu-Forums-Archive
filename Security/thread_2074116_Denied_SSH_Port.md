---
title: "Denied SSH Port"
date: 2012-10-21
forum: Security
---

### Post by Onefreshfish on 2012-10-21
I've created a server on a computer and I am trying to connect to it through a Linux terminal on another computer running Ubuntu.
 
To connect I'm using the command:
[LEFT]    ```
ssh username_of_server@server_ip_address
``` and it gives me an error message:
    ```
connect to host: server_ip_address port 22: no route to host 
```I'm fairly new to the commands of networking (and Ubuntu forums, I apologise if this post thread is in the wrong area), but how can I solve this problem? 
**Is there a command I need to run on the server to allow traffic through port 22? Or do I need to connect to a different port?**
[/LEFT]

---

### Post by steeldriver on 2012-10-21
o are you trying to do this over your LAN or over a larger network (including routers)?

o how did you set up / configure SSH on the remote machine?

---

### Post by mr-woof on 2012-10-21
if you're qute new to the command line and setting up servers, you probably haven't changed the default port for ssh server from 22 to something else. It sounds like your trying to connect to a machine that remote, you'll need to forward port 22 on your router to the server.

Regardless of how your connecting, you'll need to do some other changes to ssh before you open it up to the outside world, disable root etc. We'll go through the changes, once you can connect.

---

### Post by cariboo on 2012-10-21
I'd suggest pinging the server, to see if you can actually connect to it.

---

### Post by robtygart on 2012-10-21
In order for me to ssh into my other pc I type ```
ssh User-name@Computer-name.local
``` 

So try adding .local at the end. You can use the computer name or the computers ip addtess

---

### Post by The Cog on 2012-10-21
No route to host generally means just that. There is no known route to send packets to the host.

Actually, I think the most common cause of this is when you try to talk to an address on the local LAN when there is no machine at that address (like if it's switched of). It can also happen if you try to connect to a remote machine but don't have a default gateway/router in your routing table.

Try using ping instead of SSH - I guess you'll see the same answer. I don't think this an SSH issue.

---

### Post by robtygart on 2012-10-21
After connecting as I said it should ask to accept a key... Type "Yes". Then it should make a connection to the host.

If I omit .local this is what I get 
```
ssh: connect to host family-desktop port 22: Connection timed out
```

---

### Post by cariboo on 2012-10-21
> **robtygart said:**
> After connecting as I said it should ask to accept a key... Type "Yes". Then it should make a connection to the host.

If I omit .local this is what I get 
```
ssh: connect to host family-desktop port 22: Connection timed out
```

Do you have family-desktop in your /etc/hosts file? This is what mine looks like:

```
cariboo@alexis:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	alexis
192.168.0.250	willy
192.168.0.240	likely
```

willy and likely are both servers.

---

### Post by robtygart on 2012-10-21
I am not the OP but

```
family@family-desktop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       family-desktop

```

```
127.0.0.1       localhost
127.0.1.1       mobile
```

The OP showed what commaned he used. When I SSH into Family-desktop I use .local at the end. 

I think he is missing this part.

```
rob@mobile:~$ ssh family@family-desktop.local
family@family-desktop.local's password: 
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-31-generic i686)

 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
6 updates are security updates.

Last login: Sun Oct 21 15:32:13 2012 from mobile.local
family@family-desktop:~$ 


```

---

### Post by bab1 on 2012-10-22
> **robtygart said:**
> I am not the OP but

```
family@family-desktop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       family-desktop

```

```
127.0.0.1       localhost
127.0.1.1       mobile
```

The OP showed what commaned he used. When I SSH into Family-desktop I use .local at the end. 

I think he is missing this part.

```
rob@mobile:~$ ssh family@family-desktop.local
family@family-desktop.local's password: 
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-31-generic i686)

 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
6 updates are security updates.

Last login: Sun Oct 21 15:32:13 2012 from mobile.local
family@family-desktop:~$ 


```

The Cog answered the OP's initial problem.  Until the OP answers no progress can be made to resolve it.

But, in your case @robtygart your set of circumstances are a little different.  When you map an IP address to hostname it is useful for you to do it to an IP address that communicates with others at least at the LAN level.  The IP address range 127.0.0.0 /8 (all of the 127 range) is internal to the host you are at (the local host).  In you case mDNS (zeroconf) is auto configuring your IP address to the hostname of your machine and adding the suffix .local.  If you were to map the hostname *family-desktop* to the LAN IP you are using you wouldn't need the .local suffix.

In the end if it works for you then all is well and good.  But, it might be better for the OP to configure the system correctly if he/she is learning how the system behaves.

[COLOR="Blue"]Edit: to clarify a bit.  Here is the output from my host malibu and malibu.local to ping[/COLOR]```
bab@malibu:~$ **ping malibu**
PING malibu (192.168.1.3) 56(84) bytes of data.
64 bytes from malibu (192.168.1.3): icmp_seq=1 ttl=64 time=0.015 ms

bab@malibu:~$ ping **malibu.local**
PING malibu.local (192.168.1.3) 56(84) bytes of data.
64 bytes from malibu (192.168.1.3): icmp_seq=1 ttl=64 time=0.013 ms

```

[COLOR="Blue"]The /etc/hosts file looks like this[/COLOR]```
bab@malibu:~$ cat /etc/hosts
127.0.0.1	localhost
192.168.1.3	malibu 

```

---

