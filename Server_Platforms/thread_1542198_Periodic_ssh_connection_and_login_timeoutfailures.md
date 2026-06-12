---
title: "Periodic ssh connection and login timeout/failures"
date: 2010-07-30
forum: Server Platforms
---

### Post by atownley on 2010-07-30
Hi Everyone,

A few weeks ago, I upgraded one of our machines to the 64-bit server edition of 10.04.  All went reasonably well (after some hoops to get it to properly recognize/mount the RAID + LVM partitions), but one of the things that confounded the installation process was login timeouts.

From doing some research, I thought I'd gotten it solved by removing the checks for updated packages on login, but I either didn't get it done, or there's something else going on here.

The issue is that the machine is headless and is actually a file & application server, but I do need to connect to it via ssh on a regular basis.  However, the issue isn't related to SSH, as it also happens when I try and log in through the physical console too.

What happens is that every so often, login attempts will time out for a period of minutes, then they will suddenly start working again, instantly giving me my expected shell.  Again, I suspect it is something with the way the motd junk is being generated, but having a server that prevents you from logging in is totally unacceptable.

I've no idea how to go about debugging what happens because I don't see anything useful in any of the logs, and I don't have a way to trace the login process from outside.

I'd love to hear what the problem actually is and how to prevent this from happening.  It is extremely frustrating!

Thanks in advance,

ast

---

### Post by iponeverything on 2010-07-30
you can have both a listening server process and the client process in debug to see what is happening. 

To put the server into debug and not get logged out, open a ssh session and run the command:

```
pstree -up |grep ssh
```

you will get something like:

```

root@gateway:~# pstree -up |grep ssh
        |-sshd(2222)-+-sshd(7411)---bash(7413)
        |            `-sshd(9203)---bash(9205)-+-grep(9217)

```

kill off the root of tree and the children, one of which will be the session that you are doing this from, will be inherited by init. 

in this case process id 2222 is the root.

```
kill -9 2222
```

you can now restart the server in debug mode - It will be a non forking process, so you will have to restart it again in debug mode for every test:

```
/usr/sbin/sshd -d
```

It will run in the forground:

```

debug1: sshd version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.

```

now connect from a client in debug mode:

```
ssh -v server
```

Now both the client and server print out debugging information for you. You don't have send output to STDOUT you can send it to a file.

The server only allows one connection in debug mode, so after every test until you capture one of the problem sessions that times out, restart sshd in debug mode. After you get what you need -- resume normal sshd operation by restarting the forking sshd with:

```
service ssh start
```

> but having a server that prevents you from logging in is totally unacceptable.

I am glad you draw the line somewhere..

---

### Post by atownley on 2010-07-30
Thanks for the sshd debugging tips.  I wasn't aware of that approach.

However, from the research into the problem that I've already done to date, the problem isn't with sshd or the console login processes themselves.  Something seems to be running as a result of actually executing the login shell.  This is the part that I guess wasn't very clear.

You don't get any errors on the client side with ssh -v (which I've done before).  The connection is closed normally, but you don't get an actual interactive prompt nor do remote commands get executed.

What I don't have is a good understanding of why this behavior might happen, and I'm not presently prepared to run the ssh server in debug mode for days waiting to see when it will happen next.  It will work fine for several days (weeks) and then it will hang.  When it hangs, you need to keep making multiple attempts to log in until it works.  Seeming to wait until a spawned process completes doesn't seem to work.  I've waited over 30 min between attempts and still get the "Connection closed" message.

Also, this has happened from the point it was installed (a fresh install of 10.04), and it happens not only for my primary login, but I also experienced this behavior on the console after enabling direct root login from that tty.

I did see this forum post previously [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452) and followed their advice, but the problem doesn't seem to have been solved.

In trying to find the above link again, I did run across two other posts that I hadn't seen previously that seem to describe the issue I see:

[http://ubuntuforums.org/showthread.php?t=1449020](http://ubuntuforums.org/showthread.php?t=1449020) and [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1470011](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1470011)

I'm going to try to purge the landscape stuff and see if that works.  If so, I think this ought to go as a sticky post in the server forum.  I'm very curious why it seems to affect more people other than via the potential firewalling configurations.  Mine isn't set to limit outbound traffic, so that shouldn't be an issue.

However, I do heavily suspect the MOTD junk as the culprit since SSH and login display no errors and ssh -v doesn't indicate any strangness either.  Whatever it is happens as part of completing the login process after you've successfully authenticated your session.

Cheers for the reply,

ast

---

