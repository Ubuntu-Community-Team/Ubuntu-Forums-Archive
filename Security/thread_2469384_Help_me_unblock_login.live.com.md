---
title: "Help me unblock login.live.com"
date: 2021-11-27
forum: Security
---

### Post by joeldurham on 2021-11-27
I realize this a bit of a read but I am at a loss and would love all kinds of help.

Hello, I am trying to install Minecraft on my Ubuntu machine. For some unknown reason, the url login.live.com is blocked and refuses to connect on my computer. login.live.com is the link used to signin to a Microsoft account and thus a Minecraft account. The computer, for some reason, does not want to connect to that server. I have tried many troubleshooting things to get around this and now I am at a loss. Someone with a knowledge of linux please help me.
I have tried and failed at:
[LIST=1]
[*]Using different browswers (but this doesn't matter because the Minecraft launcher creates it's own pop-up) but they all tell me that login.live.com refuses to connect. This is with the notable exception of brave with tor mode which connects but that is not useful because I can't sign in in the browser
[*]Using VPNs, the only VPNs that seem to work are the ones built into chrome as extension and the larger ones that are downloaded onto the machine itself don't work to unblock it or stop it from happening
[*]changing my DNS settings to google's or openDNS
[*]disabling my firewall using "sudo uwf disable" (If I'm doing this wrong please someone explain to me)
[*]disabling the extensive parental controls built into my families router
[*]hardwiring the pc to the router
[*]changing the ip
[*]flushing the DNS
[*]trying to use torsock to open the launcher but it crashed
[/LIST]

If you see something that you think I might have done wrong or not fully, please let me know. If you think of something I did not do, please tell me it's steps in great detail. 

FYI, I am running Ubuntu 20.04.3 LTS and all I want to do is get Minecraft of the potato of a computer. Thanks!

---

### Post by Frogs Hair on 2021-11-27
I see no problem with the login in my location on my installed browsers. A work-around maybe to create a minecraft account and login that way, but this is no help the Microsoft login if needed for other reasons. Posting the results of the following terminal command may offer a clue.

   ```
ping microsoft.com

```

---

### Post by joeldurham on 2021-11-27
> **Frogs Hair said:**
> I see no problem with the login in my location on my installed browsers. A work-around maybe to create a minecraft account and login that way, but this is no help the Microsoft login if needed for other reasons. Posting the results of the following terminal command may offer a clue.

   ```
ping microsoft.com

```


I used the command
```
ping microsoft.com

```
and got this results
```
PING microsoft.com (13.77.161.179) 56(84) bytes of data.

```
I then tried 
```
ping login.live.com

```
and got this result 
```
PING login.live.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.034 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.042 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.066 ms

```
and it continues infinetly with increasing seq and varying degrees of time.  

For the record, I have a microsoft account, the problem is that whenever I click microsoft login in the minecraft launcher, the pop-up says 
"Failed to load page.
Please check your internet connection and try Reload again.
Error message: ERR_CONNECTION_REFUSED (code=-102)."

---

### Post by Doug S on 2021-11-27
microsoft.com does not reply to ping for me either. Many IP's do not reply to ping.
login.live.com does not reply to ping for me, and it seems to be an alias for login.msa.msidentity.com

Anyway, your system seems to think it is a local loopback IP address, 127.0.0.1

---

### Post by joeldurham on 2021-11-27
Okay, so how do I tell the system that it's not a local looback IP address and is instead a trusted website that I want to go to?
Is there a way to whitelist urls?

---

### Post by jeremy31 on 2021-11-27
Check ```
cat /etc/hosts
```

---

### Post by joeldurham on 2021-11-27
Okay so, I forgot I manually added login.live.com to my /etc/hosts which is probably why it was treating it like a local host. 
I undid that and now when I do
```
ping login.live.com

```
and I get
```
PING www.tm.a.prd.aadg.akadns.net (40.126.28.19) 56(84) bytes of data.

```

---

### Post by joeldurham on 2021-11-27
[Solved]
Okay guys, thank you for your help. I solved it by resetting the DNS again and changing the DNS to Google Public for both IPv4 and IPv6.

---

### Post by KBar on 2021-11-27
Great! 

Now, could you please edit the title of the thread instead and put the [SOLVED] tag there?

---

