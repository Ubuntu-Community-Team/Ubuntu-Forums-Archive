---
title: "iptables"
date: 2014-06-25
forum: Server Platforms
---

### Post by Pierre_P. on 2014-06-25
This is my very first interaction on a public internet forum (and I am 30 years old) - so please bear with me!

My goal is to create an iptables rule for requests coming into port 22 for an SSH connection.  I desire to know why the following command did not work, and what the output message means:

root@ubuntu:~# [B]iptables -I INPUT -m dccp --dport 22 -j ACCEPT

[/B]*...x_tables:  ip_tables:  dccp match:  only valid for protocol 33...*

I also used iptables-save and then iptables-apply (with no success) and my terminal stalled on iptables-restore.  

why did it stall?

Thanks in advance for any consideration on this topic.

-Pierre

---

### Post by nerdtron on 2014-06-25
For a newbie, why use iptables? Allowing only ssh port for incoming connection is very easy when using ufw.

Anyway, shouldn't the rule be like this: 
iptables -A INPUT -p tcp --dport [COLOR=#000000]22[/COLOR] -j ACCEPT

---

### Post by Pierre_P. on 2014-06-25
I actually just logged back in here to say that I figured it out...and am frankly astonished at how quick a reply was posted.  I thank you sincerely.

I am a newbie, yes, but I am using iptables because I want to become an expert ;)

NOW the problem I am having is that I do **iptables-save** which works, but when I do the suggested **iptables-restore**, my system stalls, and when I restart, my rules are gone and I'm back to square 0.  Judging from this: [https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables)   things are a bit more complicated than simply typing in **iptables-save**...

---

### Post by Pierre_P. on 2014-06-25
I figured it out for now, thanks in large part to the IptablesHowTo.  Thank you,

-Pierre

---

