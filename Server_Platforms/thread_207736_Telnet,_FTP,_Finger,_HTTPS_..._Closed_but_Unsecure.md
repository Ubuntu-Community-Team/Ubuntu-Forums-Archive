---
title: "Telnet, FTP, Finger, HTTPS ... Closed but Unsecure"
date: 2006-07-02
forum: Server Platforms
---

### Post by Isoss on 2006-07-02
I entered [http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp), which scans my ports and sees which ports are open and which are closed. I have a firewall so no port is open, but it said that telnet and some other ports are closed but unsecure! it said that this port is not being blocked, but there is no program currently accepting connections on this port. 

I am not an expert in security and ports, and I konw -correct me if I am wrong- that closing them to be secure means to block them and so I wouldn't be able to use ftp or http or telnet ...etc. no more. 

But still this word makes me a little bit concerned: unsercure! to what degree? that's my question. 

Another question: What do these ports do? 79 (Finger) 139 (Net BIOS)  

Thanks.

---

### Post by ynef on 2006-07-02
As the page you linked says, they use the term "closed but insecure" in the sense that their packets aren't dropped (disregarded, thrown away) by your firewall -- they reach the computer which responds that the computer in fact exists, but doesn't have a server at that port. Your computer is basically responding that it doesn't want to be contacted, instead of just ignoring it completely. The difference is, of course, that if it wouldn't respond at all a (very stupid) hacker might think that your computer isn't online and try to hack someone else. Someone a bit more determined will find out anyway.

You are wrong about ports -- blocking your HTTP port (port 80 on your machine) will NOT block your surfing. When you use a browser and try to connect to a server, the browser will ask for a random port number from the operating system and use that to connect to the server's port 80. Your port 80 is safe to block completely if you don't intend to run a server there.

You don't have any active servers running, thus these servers cannot get hacked. You are safe.

The finger port is used for the program "finger" to get information on users. It is usually disabled and I'd be surprised if you have it enabled anywhere. To see what kind of information you can get, try "finger $USER" in a terminal to see the information it gives out about you. If all hosts on the Internet ran the finger deamon, you could, theoretically, get information on all the users that way. Nobody does (anymore) and finger is basically only used in small corporations and the like.

Find out about NetBIOS at Wikipedia.

---

### Post by RavenOfOdin on 2006-07-02
I believe Firestarter has options available to "drop silently" and "reject" packets. . .You should choose the former, and disable services such as Echo Reply and Timestamping.  

Word of warning, though -- Disabling any network services might cause some utilities to either work piecemeal or not at all.

---

