---
title: "SLOW logins"
date: 2007-08-27
forum: Server Platforms
---

### Post by iskatyel on 2007-08-27
OK, so Monday morning and logins from XP clients are incredibly slow to the Samba server (Dell PE650 running Ubuntu 6.06.1, Samba 3.0.22 and Apache 2.0.55) but the login will succeed.  Everything worked great on Friday...

I started by thinking this is a Samba issue, but at the console I still get a reallly slow login, sometimes it times out (returns the took longer than 60 seconds message).  It does the same thing when I sudo or su as well.  I run top and usage is less than 1% most of the time with occasional jumps into the single digits.  The average load in uptime is 0.00.  df shows the drive as less than 1% utilization.  The logs don't show any errors I can relate to authentication.  I can stop Samba and Apache and run netstat so that the only connections are to the dns servers on 53 and to ssh, but the login performance is still just as poor, please help!  

I am pulling my hair out on this one. :confused:

---

### Post by ddrichardson on 2007-08-27
How is the network topology configured - routers especially.

---

### Post by iskatyel on 2007-08-28
Network topology is not ideal (I have already talked them into changing it, but that is still coming down the pipe).  We route to a NetWare 6.5 box as the gateway which has a static route to the internet via a pix 501 and a static to an archaic router that connects to the WAN network.  DNS is currently all being done by the ISPs servers outside and we have just used WINS inside.  I checked out the pix and after doing a diff on the most recent config and the previous working config I found minimal changes and reverted them with no luck.

Along the lines of your question, a friend suggested that I look at resolv.conf - perhaps the dns resolution is a problem.  I stripped resolv.conf down to just the name servers, no search info, and still had this problem.  Watching throughout the day I found that after I had left smbd and nmbd off for a while the local logins did pick up and were processed normally.  I also found that right after I started them up I could log in quickly, but was having problems after one or two XP machines attempted to log in.  I looked more closely at the syslog with samba back on and observed the following error occurring:
```
smbd[5264]:   Denied connection from  (0.0.0.0)
```

Which I found a solution for in the following thread.  This solution seems to be working, but I will not know until it is stress tested in the morning by my users.  The thing I really don't like here is that this configuration, minus the smb ports = 139 directive, has been working wonderfully.  Why did it break?
[http://forums.gentoo.org/viewtopic-t-304678-highlight-.html](http://forums.gentoo.org/viewtopic-t-304678-highlight-.html)

The other weird thing that has just started is my ssh access to this and my other ubuntu server has seemed to go up and down, apparently in sync with this server being inaccessible.  Right now the other server is timing out when I try to connect over ssh so I hope I am not just headed for a disaster again in the morning.  I hate intermittent errors.  -- wait -- now it came up and ssh connected just as quick as you please.  And there, after a long wait, I sshed to the PDC as well.

Okay, so looking over the logs and reading a lot more on the net, I don't think this is fixed.  
nmbd.log gives this over and over again (from different ip addresses, though)
```
[2007/08/27 23:16:59, 1] lib/util_sock.c:open_socket_out(892)
  timeout connecting to 10.18.250.101:139
[2007/08/27 23:16:59, 1] libsmb/cliconnect.c:cli_connect(1332)
  Error connecting to 10.18.250.101 (Operation already in progress)
```
the machine's ip address log gives this:
```
[2007/08/15 20:07:01, 0] lib/access.c:check_access(328)
[2007/08/15 20:07:01, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
  Denied connection from  (0.0.0.0)
[2007/08/15 20:07:01, 1] smbd/process.c:process_smb(1187)
[2007/08/15 20:07:01, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
  Connection denied from 0.0.0.0
[2007/08/15 20:07:01, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 10.18.250.101. Error Connection reset by peer
[2007/08/15 20:07:01, 0] lib/util_sock.c:send_smb(765)
  Error writing 5 bytes to client. -1. (Connection reset by peer)
```
the machine's netbios name log gives this also repeatedly:
```
[2007/08/27 15:29:34, 0] lib/util_sock.c:read_data(529)
  read_data: read failure for 4 bytes to client 10.18.250.101. Error = Connection reset by peer
[2007/08/27 15:41:36, 0] lib/util_sock.c:read_data(529)
  read_data: read failure for 4 bytes to client 10.18.250.101. Error = Connection reset by peer
```
Notice that the errors nmbd is logging are not duplicated in the logs for the ip/netbios of the machine cited.

The only solutions I have seen so far were in this thread:
[http://www.linuxquestions.org/questions/showthread.php?t=186532](http://www.linuxquestions.org/questions/showthread.php?t=186532)
But they are 1) upgrade 2)weird dual NIC issues (I do have a dual NIC card, but only eth0 is configured) 3)Novell client bug (we do have the Novell client installed, but it has not been updated or changed).  The really big question is why this started this weekend.

So, there's a really long post.  Please help if you can, this is bad for user morale. ;)
Dan

---

### Post by ddrichardson on 2007-08-28
Just a quick one - where are you and your ISP located?

---

### Post by iskatyel on 2007-08-28
You mean geographically?  Southern Utah, the Western United States.  Why?

---

### Post by ddrichardson on 2007-08-28
There was some DNS issues in Europe at the weekend, related to a number of the bigger torrent trackers rejecting US IP addresses. Read a few problems that had had knock on effects is all.

---

### Post by ddrichardson on 2007-08-28
Following on from the link you posted that has helped, has there been an XP update over the weekend?

---

### Post by iskatyel on 2007-08-28
Update:

It looks the smb ports = 139 directive fixed the 30 minute wait for XP desktop logins, but the question 'why' still remains.  It also appears that the errors in log.nmbd went away once the uses authenticated this morning.  Well, this has turned out more like a blog entry, but I hope it helps someone else.

dd: I will check out the update option, M$ usually does their updates on Tuesday nights, but they like to mix it up for us once in a while :)  If they changed something related to the selection of port 139/445 that could be the cause of the problem.  Everything is set to auto update since we don't have an SMS server (that is definitely on my Samba wishlist).  Thanks for your comments.

Dan

---

### Post by ddrichardson on 2007-08-28
I had a look through th MS Knowledge Base and there are a few articles reference the two ports in question - that they should be closed. This contradicts Microsoft's own policy document on interopperabilty with UNIX and as I can't find a specific vulnerabilty update I'm not sure.

Mind you, the networking team is a law unto itself - look at the debacle over throttling network performance when playing MP3 in Vista - up to 90% packet loss!

---

