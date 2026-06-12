---
title: "samba and win 7 connection problem? can't ping server??"
date: 2010-04-06
forum: Server Platforms
---

### Post by gobbledigook on 2010-04-06
Hey!

i have karmic on a headless install.

a guy i live with recently purchased a win 7 machine, we got it connected to my samba share fine :) but after a few days it stopped connecting!! I've disable ipv6 and he is in the right domain :)

strange thing is that other users (xp,osx,ubuntu) connect fine! and also that when i ping the server from the win 7 machine i get an odd response??

192.168.1.1 = router with dd-wrt :)

192.168.1.120 = server

```
C:\Users\dude>ping 192.168.1.1

Pinging 192.168.1.1 with 32 bytes of data:
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms

C:\Users\dude>ping 192.168.1.120

Pinging 192.168.1.120 with 32 bytes of data:
Reply from 192.168.1.149: Destination host unreachable.
Reply from 192.168.1.149: Destination host unreachable.
Reply from 192.168.1.149: Destination host unreachable.
Reply from 192.168.1.149: Destination host unreachable.

Ping statistics for 192.168.1.120:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
```

Why do i get a response from .149  when i'm pinging .120 ? .149 is the win 7 machine i'm pinging from!!??

OK i figured the .149 bit out... just me being an idiot and not used to win cmd :0 but still can't work out why the win 7 machine cannot see the server :(

Any help greatly appreciated :)

---

### Post by n6yga on 2010-04-06
I, too, am having huge problems with Win7. I can't even see the netbios names of my servers. Also, I can't connect by ip address. I have done some research and there are a couple registry hacks that have to be done on the Win 7 side to reduce the version of NTLM from v2 to v1.

Do a google search for Win7 & NTLMv2. I don't have the info with me atm. Sorry.


Mark.

---

### Post by Jive Turkey on 2010-04-06
Some things I would check:
1. firewall on the win7 box (if its the windows firewall I cant help as they made it fairly incomprehensible) so try turning it off completely to test, then put it back on.  Also check if win7's network manager shows a picture of a house or an office building, if it shows a park bench that's likely the problem right there.

2. firewall on server, 

3. smb.conf, if you have any directives for allowed hosts in there (not present by default IIRC).

4. Any denyhosts or failtoban apps on the server.

5. The network browsing feature doesn't work very well in any OS.  Try connecting using the map network drive feature.

6. I find it helps a lot to have the username/pass on windows and samba identical.  mumble mumble.

---

### Post by gobbledigook on 2010-04-12
hi there!

thanx for you're input :) sorry for a delayed reply!! i couldn't figure it until i connected from a different machine dhcp'd the 149 address!!?? 

i have fail2ban, but have checked the logs and cannot find anything to do with that ip in them :( so as its the last address in my local ip table i just changed the ip table on my router to only assign up to .148... this solves the problem of win7 connecting on a short term... but over the long term i have a feeling the next ip that machine dhcp's will be blocked too!! 

I have the drive mapped and to log in using different user/pass

---

