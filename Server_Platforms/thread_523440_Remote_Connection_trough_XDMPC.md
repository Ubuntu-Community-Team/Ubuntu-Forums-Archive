---
title: "Remote Connection trough XDMPC"
date: 2007-08-11
forum: Server Platforms
---

### Post by sidimaiga on 2007-08-11
Hi, 

I just installed Ubuntu 7.04 and would like to use it as a file server, torrent downloaded,.... I can only access to it trough the network (no monitor, no  keyboard)
I'd like to be able to remotely connect to the server using XDMPC service from my other Linux box. 
So how can I disconnect my self from the server and at the same time stay be log in (so my downloads keep running)? . 
Anytime I try to leave the server, the user log out, which stop all the process i started.

Thanks,

---

### Post by netlogic on 2007-08-11
For torrents, I use **screen** and **rtorrent**. Also, the latest version of rtorrent offers a compatible encryption (I believe it is RC4) with utorrent and Azerus clients. You think utorrent is tiny, try rtorrent.

---

### Post by netlogic on 2007-08-11
I am sorry. I forgot to answer your management connection question. Run a firewall like shorewall. Enable ssh,  DNS, and choose NFS or SMB, You might need to enable other service ports as your needs fit, Block VNC, so others can't listen to your VNC connections, but wrap VNC over ssh. VNC is very insecure by itself. When you disconnect your VNC session, the process will be still running on the remote machine. I think that's the answer you want to hear. Still, something like torrent, rtorrent just kicks butt.

---

### Post by steve.horsley on 2007-08-12
I know a couple of ways to leave terminal programs running as you disconnect, but I dknot know a way to do it with GUI programs.

The text ways I know are:
1) launch the program with nohup. e.g.
nohup wget <url>

2) Start, background and disown the process. e.g.
nohup wget <url>
Ctrl-Z
bg
disown

3) run **screen** and launch applications in there. You can disconnect, reconnect later, run screen again and pick up the old screen contents along with prompts, progress bars etc.

---

### Post by steveneddy on 2007-08-12
UH - access your machine through VNC, start the process, and close the window. Don't log out, just close the window that opens with the vnc session.

I access my server from anywhere on my laptop by typing in terminal

```
xvncviewer ip.address.of.the.server:1
```

The :1 at the end logs you on to a separate session.

I have a DSL connection with a dynamic IP address, so I registered at [DYNdns.com]("http://dyndns.com/") to monitor my IP address -  I loaded ddclient, which is in the repos, to send dyndns.com my ip address every few minutes. Now, when I want to log on to my server, whether at home or away from home, I type in the address of my server. 

Something like - myserver.dyndns.org - and you can choose your name of your server.

So actually you are typing

```
xvncviewer myserver.dyndns.org:1
```

To access my server. This way I don't have to know the IP address, since it's dynamic, so I don't have to be home to check my IP address - heck, you know the rest.

AND - it's free. It's easy.

It works really well if you have a Linksys router that supports dynamic dns services.

---

### Post by sidimaiga on 2007-08-12
> **steveneddy said:**
> UH - access your machine through VNC, start the process, and close the window. Don't log out, just close the window that opens with the vnc session.

I access my server from anywhere on my laptop by typing in terminal

```
xvncviewer ip.address.of.the.server:1
```

The :1 at the end logs you on to a separate session.

I have a DSL connection with a dynamic IP address, so I registered at [DYNdns.com]("http://dyndns.com/") to monitor my IP address -  I loaded ddclient, which is in the repos, to send dyndns.com my ip address every few minutes. Now, when I want to log on to my server, whether at home or away from home, I type in the address of my server. 

Something like - myserver.dyndns.org - and you can choose your name of your server.

So actually you are typing

```
xvncviewer myserver.dyndns.org:1
```

To access my server. This way I don't have to know the IP address, since it's dynamic, so I don't have to be home to check my IP address - heck, you know the rest.

AND - it's free. It's easy.

It works really well if you have a Linksys router that supports dynamic dns services.

Ok I try that, but nothing happen
Are you not required to be log in before using VNC? The reason I'm asking is because the only way to log in to my server is to use XDMPC (no keyboard, mice or display just the box).
So how to log in using VNC?

---

### Post by conjur3r on 2007-08-13
Yes, you will need to log into the server at least once before VNC will work.  I have my headless server automatically logged in during boot.  It's working fine over VNC.

I tried XDMPC but ran into the same issues you did.

---

### Post by netlogic on 2007-08-13
Have you also tried a package called, conspy (remote control of Linux virtual consoles)? You might enable to launch VNC that way remotely.

---

