---
title: "FTP Server issues"
date: 2007-10-22
forum: Server Platforms
---

### Post by valnour on 2007-10-22
I have an FTP server that is giving me some odd problems. It's setup on my network and I can access it from my network, from outside my network, and others can access it as well. However, I've had several complaints from people that they can not connect to it.

The Logs read like this for those that cannot connect:

anonymous (0.0.0.0)> 230 Logged in
anonymous (0.0.0.0)> opts utf8 on
anonymous (0.0.0.0)> 200 UTF8 mode enabled
anonymous (0.0.0.0)> 215 UNIX emulated by FileZilla
anonymous (0.0.0.0)> site help
anonymous (0.0.0.0)> 504 Command not implemented for that parameter
anonymous (0.0.0.0)> PWD
anonymous (0.0.0.0)> 257 "/" is current directory.
anonymous (0.0.0.0)> noop
anonymous (0.0.0.0)> 200 OK
anonymous (0.0.0.0)> CWD /
anonymous (0.0.0.0)> 250 CWD successful. "/" is current directory.
anonymous (0.0.0.0)> TYPE A
anonymous (0.0.0.0)> 200 Type set to A
anonymous (0.0.0.0)> PASV
anonymous (0.0.0.0)> 227 Entering Passive Mode (75,145,1,173, 4, 65)
anonymous (0.0.0.0)> disconnected

After Passive Mode is started, they cannot stay connected. Again this only happens on some clients. Here is a successful attempt:

anonymous (0.0.0.1)> 230 Logged on
...
...
...
...
...
anonymous (0.0.0.1)> PWD
anonymous (0.0.0.1)>  257 "/" is current directory.
anonymous (0.0.0.1)>  noop
anonymous (0.0.0.1)>  200 OK
anonymous (0.0.0.1)>  CWD /
anonymous (0.0.0.1)>  250 CWD successful. "/" is current directory
anonymous (0.0.0.1)> TYPE A
anonymous (0.0.0.1)> 200 Type set to A
anonymous (0.0.0.1)> PORT 0,0,0,1,213,132
anonymous (0.0.0.1)> 200 Port command successful
anonymous (0.0.0.1)> LIST


And then they are connected no problem... I'm not super familiar with the FTP Protocol so can someone please shine some light on this for me. Maybe explain why one is connecting but not the other. Why does one want to enter passive mode, but not the other? Any help will be greatly appreciated.

---

### Post by rickyjones on 2007-10-22
> **valnour said:**
> I have an FTP server that is giving me some odd problems. It's setup on my network and I can access it from my network, from outside my network, and others can access it as well. However, I've had several complaints from people that they can not connect to it.

The Logs read like this for those that cannot connect:

anonymous (0.0.0.0)> 230 Logged in
anonymous (0.0.0.0)> opts utf8 on
anonymous (0.0.0.0)> 200 UTF8 mode enabled
anonymous (0.0.0.0)> 215 UNIX emulated by FileZilla
anonymous (0.0.0.0)> site help
anonymous (0.0.0.0)> 504 Command not implemented for that parameter
anonymous (0.0.0.0)> PWD
anonymous (0.0.0.0)> 257 "/" is current directory.
anonymous (0.0.0.0)> noop
anonymous (0.0.0.0)> 200 OK
anonymous (0.0.0.0)> CWD /
anonymous (0.0.0.0)> 250 CWD successful. "/" is current directory.
anonymous (0.0.0.0)> TYPE A
anonymous (0.0.0.0)> 200 Type set to A
anonymous (0.0.0.0)> PASV
anonymous (0.0.0.0)> 227 Entering Passive Mode (75,145,1,173, 4, 65)
anonymous (0.0.0.0)> disconnected

After Passive Mode is started, they cannot stay connected. Again this only happens on some clients. Here is a successful attempt:

anonymous (0.0.0.1)> 230 Logged on
...
...
...
...
...
anonymous (0.0.0.1)> PWD
anonymous (0.0.0.1)>  257 "/" is current directory.
anonymous (0.0.0.1)>  noop
anonymous (0.0.0.1)>  200 OK
anonymous (0.0.0.1)>  CWD /
anonymous (0.0.0.1)>  250 CWD successful. "/" is current directory
anonymous (0.0.0.1)> TYPE A
anonymous (0.0.0.1)> 200 Type set to A
anonymous (0.0.0.1)> PORT 0,0,0,1,213,132
anonymous (0.0.0.1)> 200 Port command successful
anonymous (0.0.0.1)> LIST


And then they are connected no problem... I'm not super familiar with the FTP Protocol so can someone please shine some light on this for me. Maybe explain why one is connecting but not the other. Why does one want to enter passive mode, but not the other? Any help will be greatly appreciated.

It looks like their FTP client is defaulting to "Passive" mode. Your server is not configured for passive mode at this most likely. Either have your friends uncheck "Use passive mode" in their client or forward the necessary ports for passive mode.

I believe there is an option for passive mode ports in your server configuration file. I believe you specify a range of about 10 ports and make sure those ports are forwarded from your firewall to your server.

Hope this helps!

-Richard

---

### Post by MJN on 2007-10-22
Have a read (twice, at least!) of the following URL which discusses passive and active FTP connections and the problems they cause:

[http://www.slacksite.com/other/ftp.html](http://www.slacksite.com/other/ftp.html)

This is one of the many reasons why FTP is a protocol of last resort due to its multi-port arhitecture which doesn't sit well with NATs and firewalls.

As Richard says you will need to confine the data ports to enable passive clients to connect from outside your network.

Mathew

---

### Post by valnour on 2007-10-22
I set up the server's passive mode to use ports 1080-1180 and set up the router to route the packets accordingly. However, it still is not functioning like I want it to. I'll read the page at the link you posted again and see if I can figure this out. I wouldn't be using FTP if I didn't have to, believe me... But thanks for help, and helpful link.

---

### Post by MJN on 2007-10-23
I was going to suggest thinking about alternatives to FTP as, aside from the problems you're suffering, there also the issues of security (or lack of) that may be significant.
 
Is FTP definitely your only option (often it is)? Perhaps if you explained your situation there may well turn out to be a 'better' solution.
 
Mathew

---

### Post by valnour on 2007-10-23
Yes, I would much rather use something different. My problem firstly is that I'm forced to work in a Windows environment rather than Linux as I would want to. I've set up this ftp server so that Radio Stations in my area can download traffic reports that are recorded here (and then uploaded onto said server) to be played on the radio. The actual download has to be as simple as possible, because it's gonna be download by mostly radio DJs that aren't very computer-savvy. So this is used in a small business setting. I'm fine with dropping this damn server in the DMZ and just locking down everything else if that's what it takes, but as you mentioned, it's hard to keep this thing secured correctly from what I read from the previous post's link. I would much rather use SCP or something similar, but I'm not familiar with any way to access it from a web browser.

---

### Post by valnour on 2007-10-23
Thanks for all the help guys, this has been a major learning experience. I finally switched the server software from one program to another, and set all my settings to just like they were before, and it works fine now. So the problem must have been with the software, not with my configuration (or at least, that's what I'd like to believe). I'm still going to research an alternative to this FTP server, but it will work fine for now. Thanks again for the help guys.

---

