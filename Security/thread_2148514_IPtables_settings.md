---
title: "IPtables settings"
date: 2013-05-25
forum: Security
---

### Post by pedrommone on 2013-05-25
Hello guys, Im trying to setup a few simple rules

```

root@washington:~# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
root@washington:~# iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
root@washington:~# iptables -P INPUT DROP
root@washington:~# iptables -P OUTPUT DROP
root@washington:~# iptables -P FORWARD DROP
root@washington:~# iptables -A INPUT -i lo -j ACCEPT
root@washington:~# iptables -A OUTPUT -o lo -j ACCEPT
root@washington:~# iptables -A INPUT -p tcp --dport 22 -j ACCEPT
root@washington:~# iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT
root@washington:~# iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT
root@washington:~# iptables -A OUTPUT -o eth0 -p tcp --dport 3306 -j ACCEPT
root@washington:~# wget google.com
--2013-05-25 12:59:52--  http://google.com/
Resolving google.com (google.com)... 173.194.43.8, 173.194.43.14, 173.194.43.6, ...
Connecting to google.com (google.com)|173.194.43.8|:80... failed: Connection timed out.
Connecting to google.com (google.com)|173.194.43.14|:80... failed: Connection timed out.

```

And its giving me this error in all output connections, someone understand why? In another ubuntu 12.04 vps its working well, but recently i've bought a softlayer vps and its buggyng.

---

### Post by kevdog on 2013-05-26
First I don't like the way you entered your firewall commands. Put them in a script file and do it that way so its easy to change things and reload the rules.

Next iptables works like a dumb script, one it matches a ruleset and an action occurs such as drop or accept, the rule set is finished. I think based on your post that your output chain is working because google.com gets resolved. I'd probably make your output chain accept for default ruleset for now.

Something is telling me you need to flush your iptable ruleset and start over sudo iptables -F

---

### Post by pedrommone on 2013-05-26
> **kevdog said:**
> First I don't like the way you entered your firewall commands. Put them in a script file and do it that way so its easy to change things and reload the rules.

Next iptables works like a dumb script, one it matches a ruleset and an action occurs such as drop or accept, the rule set is finished. I think based on your post that your output chain is working because google.com gets resolved. I'd probably make your output chain accept for default ruleset for now.

Something is telling me you need to flush your iptable ruleset and start over sudo iptables -F

Well, ive ran it on a new server, without any config, dont know whats wrong, I cant connect to mysql port aswell!

---

### Post by CharlesA on 2013-05-26
You aren't allowing port 80 out...

I don't deal with the output side of my firewall at all. I only care about the input.

This [post]("http://ubuntuforums.org/showthread.php?t=2144451&p=12653231&viewfull=1#post12653231") also has good advice.

---

### Post by pedrommone on 2013-05-26
> **CharlesA said:**
> You aren't allowing port 80 out...

I don't deal with the output side of my firewall at all. I only care about the input.

This [post]("http://ubuntuforums.org/showthread.php?t=2144451&p=12653231&viewfull=1#post12653231") also has good advice.

Ofc I'm

```


root@washington:~# iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT
root@washington:~# iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT
root@washington:~# iptables -A OUTPUT -o eth0 -p tcp --dport 3306 -j ACCEPT
```

---

### Post by CharlesA on 2013-05-26
Derp. Change the output policy to accept and see if you still get the time out message.

---

### Post by pedrommone on 2013-05-26
> **CharlesA said:**
> Derp. Change the output policy to accept and see if you still get the time out message.

What do you mean? I can understand what you are trying to say

---

### Post by CharlesA on 2013-05-26
Run this:

```
sudo iptables -P OUTPUT ACCEPT
```

---

### Post by pedrommone on 2013-05-26
> **CharlesA said:**
> Run this:

```
sudo iptables -P OUTPUT ACCEPT
```

But I need to filter all the output rules, I cant allow them all!

---

### Post by CharlesA on 2013-05-26
> **pedrommone said:**
> But I need to filter all the output rules, I cant allow them all!

You need to do it if you want to troubleshoot why it isn't working.

---

### Post by Doug S on 2013-05-26
> **pedrommone said:**
> And its giving me this error in all output connections, someone understand why? In another ubuntu 12.04 vps its working well, but recently i've bought a softlayer vps and its buggyng.Myself, I think you have answered your own question, there are issues with your softlayer vps (or, and as kevdog said, you might need to flush some old stuff , which I do).

I ran your rules on a test computer and they worked fine.```
doug@test-smy:~$ [COLOR=#ff0000]cat fw_05[/COLOR]
#!/bin/sh

sudo iptables -F INPUT
sudo iptables -F OUTPUT

sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP

sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT -o lo -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT
``````
doug@test-smy:~$ [COLOR=#ff0000]wget google.com[/COLOR]
--2013-05-26 17:42:31--  http://google.com/
Resolving google.com (google.com)... 173.194.33.41, 173.194.33.46, 173.194.33.32, ...
Connecting to google.com (google.com)|173.194.33.41|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2013-05-26 17:42:31--  http://www.google.com/
Resolving www.google.com (www.google.com)... 74.125.129.105, 74.125.129.106, 74.125.129.147, ...
Connecting to www.google.com (www.google.com)|74.125.129.105|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.ca/ [following]
--2013-05-26 17:42:31--  http://www.google.ca/
Resolving www.google.ca (www.google.ca)... 74.125.129.94, 2607:f8b0:400e:c02::5e
Connecting to www.google.ca (www.google.ca)|74.125.129.94|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: "index.html"
2013-05-26 17:42:32 (741 KB/s) - "index.html" saved [11003]
``````
doug@test-smy:~$ [COLOR=#ff0000]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy DROP 16 packets, 1217 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     246    29951 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       2      144 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy DROP 14 packets, 1824 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     306    35795 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
       3      180 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            0.0.0.0/0            tcp dpt:80
      18     1172 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0            udp dpt:53
```

---

