---
title: "SSH Connection working but not working"
date: 2013-01-08
forum: Server Platforms
---

### Post by brent1975 on 2013-01-08
Okay, so here is what I am working with. I have a ubuntu server 12.04 headless server sitting in the darkest cold spot in the basement. I have ssh installed on the server naturally so I can perform maintenance on the server as needed with out having to sit down there.  I did change the ssh port from the default of 22  to 5555. I recently gave up on windows on my laptop's and desktop computers and decided to come over to Linux and must say very happy with the transition.  However when I was in windows I had putty to use for the server and the Virtual box that I had test servers on.  I also have a galaxys3 that I can connect via web or local network to the server via ssh to work on it.... 

On the desktop computer I have ubuntu 12.04lts installed and is working fine. however I am unable to use terminal to connect to the server via ssh.

This is what I am doing
```
ssh brent@192.168.2.105:105
```

Here is what I am getting when trying

```
ssh: Could not resolve hostname 192.168.2.105:5555 Name or service not known
```

and yes I have ssh installed.  :)

Now I have set up staic network configuration on my desktop and all is working well. even added the dns entrys into the network/interface and checked to see if /etc/resolf.conf reflected the changes that I had applied to the /etc/network/interface file and everything looks good.

So Here is an odd deal. I went to the ubuntu app store and actually downloaded putty. configured the client to the ip and port and I am able to connect.

Does anyone know why I would not be able to use the default shell to connect via SSH?

I am confused as to why I can use putty to connect but plain default terminal is not working

Thank you in advance,

 -Brent

---

### Post by Lars Noodén on 2013-01-08
> **brent1975 said:**
> ... I did change the ssh port from the default of 22  to 5555....
This is what I am doing
```
ssh brent@192.168.2.105:105
```



If you have openssh-server installed on the remote computer, then it should be set if you change your syntax.  The [non-standard port is specified with -p](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh.1.html)

```

ssh -p 5555 brent@192.168.2.105

```

---

### Post by brent1975 on 2013-01-08
That is great! That was the issue.

How about changing where I don't have to throw the -p 5555 in the connection? Is there something that I can change or modify that will look at 5555 as default and wont require me to use that switch? if not that is okay.

---

### Post by Lars Noodén on 2013-01-08
You could modify ~/.ssh/config

```

Host 192.168.2.105
     Port 5555

```

There are a lot of other options available.  I'd recommend skimming through the manual page for [ssh_config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) to see if anything of use pops up.

---

### Post by brent1975 on 2013-01-08
Thank you! This helps alot...

---

### Post by Lars Noodén on 2013-01-08
You can add other options, to make a shorter shortcut.

```

Host foo
     User brent
     HostName 192.168.2.105
     Port 5555

```

That will allow you to just type *ssh foo* and the rest, like user name, port and IP number, is taken care of for you.

---

