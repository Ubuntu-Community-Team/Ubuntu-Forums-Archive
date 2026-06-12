---
title: "can't use gedit on remote"
date: 2010-07-02
forum: Server Platforms
---

### Post by zdarova on 2010-07-02
hi, I have 8.04 installed on virtual on a remote machine, also I installed apache2. 
I would like to istatall and configure other things, but I get this:

root@mobix:~# gedit /etc/vsftpd.conf
cannot open display:
Run 'gedit --help' to see a full list of available command line options.

I use putty for ssh connection

---

### Post by limestone on 2010-07-02
sounds like it wants you to specify a display to use... :/

---

### Post by mbsullivan on 2010-07-02
You need to tunnel X11 over SSH in order to run a graphical application (anything that launches a GUI, like GEdit).

If you're SSHing in from a Linux machine, forward X with the -X flag:

```
ssh -X user@machine
```

In Putty, there is a place for X11 Forwarding. BUT, you need to have an X server running on your local machine. That means if you're running Putty under Windows, then you need to find and run an X server (there's software out there, most of it is trialware to my knowledge).

Mike

---

### Post by zdarova on 2010-07-03
> **mbsullivan said:**
> You need to tunnel X11 over SSH in order to run a graphical application (anything that launches a GUI, like GEdit).

If you're SSHing in from a Linux machine, forward X with the -X flag:

```
ssh -X user@machine
```

In Putty, there is a place for X11 Forwarding. BUT, you need to have an X server running on your local machine. That means if you're running Putty under Windows, then you need to find and run an X server (there's software out there, most of it is trialware to my knowledge).

Mike
i could do that from a Ubuntu live cd?


do yout know other tool to install on my remote server that chould help me to view/edit text/config files?

---

### Post by CharlesA on 2010-07-03
> **mbsullivan said:**
> 
In Putty, there is a place for X11 Forwarding. BUT, you need to have an X server running on your local machine. That means if you're running Putty under Windows, then you need to find and run an X server (there's software out there, most of it is trialware to my knowledge).

Mike

I use XMing, which has both a paid and a free version.

> **zdarova said:**
> i could do that from a Ubuntu live cd?


do yout know other tool to install on my remote server that chould help me to view/edit text/config files?

You can do it from a live cd, yes.

I just use vi/vim/nano to edit config/text files on a machine with no GUI installed.

---

### Post by FuturePilot on 2010-07-03
> **mbsullivan said:**
> You need to tunnel X11 over SSH in order to run a graphical application (anything that launches a GUI, like GEdit).

If you're SSHing in from a Linux machine, forward X with the -X flag:

```
ssh -X user@machine
```

In Putty, there is a place for X11 Forwarding. BUT, you need to have an X server running on your local machine. That means if you're running Putty under Windows, then you need to find and run an X server (there's software out there, most of it is trialware to my knowledge).

Mike

This works great with Putty and X forwarding on Windows [http://sourceforge.net/projects/xming/]("http://sourceforge.net/projects/xming/")

---

