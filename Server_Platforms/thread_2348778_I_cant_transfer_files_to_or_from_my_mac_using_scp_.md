---
title: "I cant transfer files to or from my mac using scp while connected to my server"
date: 2017-01-07
forum: Server Platforms
---

### Post by jaygtel on 2017-01-07
Hi, 

I have a bit of a strange problem using SSH and I am not sure how to solve it.  Hopefully someone here can help me.  I have both my Ubuntu 16.04 server and my iMac set up so that I can connect to both of them remotely using SSH and I have confirmed that I can connect to both from terminal using the terminal command ```
SSH username@userhost
```

While I am connected to my Mac either directly on my local machine or remotely via SSH I can copy files from my Mac to my server by using the following terminal command ```
scp /path/to/local/file username@hostname:/path/to/remote/file
``` and I can also copy files from my server to my Mac using the terminal command ```
scp username@hostname:/path/to/remote/file /path/to/local/file
```

However when I am connected to my server via SSH, I can neither copy files to my server from my Mac nor to my Mac from my server.

I don't think this is anything to do with my Mac as I can connect to my Mac remotely via SSH, so I that I can establish a connection but when I try to copy files to/from my Mac while logged into my server via SSH terminal freezes and then after about 5 minutes I get an error message saying that the connection has timed out.

I have set up port forwarding and port triggering on my router as well so it not that.

This has been driving me crazy for hours so I am really hoping someone can help me solve this.

As a side note I can connect to my server using SFTP via CyberDuck (graphical file transfer program) and transfer files back and forth without issue.  Super perplexed here guys and would really prefer not to need multiple terminal windows open so if anyone can solve my problem I will be much appreciative.

Cheer
Jay

---

### Post by darkod on 2017-01-07
I assume the server can reach the mac by hostname, right? You made an entry in /etc/hosts or local dns?
Does it resolve to the mac private ip?

---

### Post by TheFu on 2017-01-07
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has my ssh troubleshooting steps.  Add some verbose options to see the debug output.

---

### Post by jaygtel on 2017-01-08
Thanks guys, I have this working now.  After driving me crazy for hours it turned out I had set my domain to resolve to the wrong IP address.  So when I was trying to connect to my machine from outside my local subnet, using username@domainname it wasn't resolving correctly and so the connection couldn't be made.

I just can't believe it took me so long to figure that out

Thanks for all your help

---

### Post by darkod on 2017-01-09
Glad you got it fixed. Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

