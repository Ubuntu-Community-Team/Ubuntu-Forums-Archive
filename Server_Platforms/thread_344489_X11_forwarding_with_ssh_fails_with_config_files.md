---
title: "X11 forwarding with ssh fails with config files"
date: 2007-01-23
forum: Server Platforms
---

### Post by e1geo on 2007-01-23
I have set up an ssh server on a system named house and am connecting to it from a system named hog.
My objective is to get trusted Xll forwarding to work using configuration files. It works fine with the -Y command line option but fails with config files. What am I doing wrong? (I am running 6.10 on both systems,) Thanks for your help.

# hostname
hog
# tail -3 /etc/ssh/ssh_config
# 0701
ForwardX11Trusted yes
-------------
# hostname
house
# tail -3 /etc/ssh/sshd_config
# 0701
X11Forwarding yes

root@house:~# /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server...                                                                                 [ ok ]
root@house:~# /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                                                                                 [ ok ]
-------------
e1geo@hog:~$ ssh house
Linux house 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Last login: Mon Jan 22 21:12:02 2007 from 192.168.0.12
e1geo@house:~$ echo $DISPLAY

e1geo@house:~$ xclock
Error: Can't open display:
e1geo@house:~$ exit
logout
Connection to house closed.

e1geo@hog:~$ ssh -Y house
Linux house 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Last login: Mon Jan 22 21:28:10 2007 from 192.168.0.12
e1geo@house:~$ echo $DISPLAY
localhost:10.0
e1geo@house:~$ xclock
[works]

---

### Post by jtc on 2007-01-23
> **e1geo said:**
> 
hog
# tail -3 /etc/ssh/ssh_config
# 0701
ForwardX11Trusted yes

Is 0701 the chmod values of ssh_config? If so, then there's the problem.

Since ssh_config is accessed by the ssh-client running as a user, the config-file needs to be globally readable. It's say 0644 would be a nice value.

If that is not the issue, then perhaps it is not associted with a or any hostname? Is the ForwardX11Trusted just laying around alone or is it sorted below a host-setting?

Like this?

```

Host *
     some settings
     some settings
     some settings
     ForwardX11Trusted yes

```

Or perhaps more specific?

```

Host house
      ForwardX11Trusted yes

```

---

### Post by e1geo on 2007-01-23
Whoops, no, sorry. the # 0701 is a comment -- a date to remind me when I made the change. No host is specified in the file so that all statements should apply to all machines.

---

### Post by jtc on 2007-01-23
Do you know if your ssh-client reads /etc/ssh/ssh_config at all? Tried putting some other settings in it to see if they take effect?

---

### Post by e1geo on 2007-01-23
Yup, it reads it -- I put a string of x's right before the ForwardX11Trusted yes line, ran ssh, and got the following:

/etc/ssh/ssh_config: line 47: Bad configuration option: xxxxxxxxxxxx
/etc/ssh/ssh_config: terminating, 1 bad configuration options

---

### Post by jtc on 2007-01-23
Duh!

Now I know why things aren't working the way we think they should.

-Y is **not** the same thing as 
ForwardX11Trusted yes

-Y is actually equal to these **two** lines.
ForwardX11 yes
ForwardX11Trusted yes

In other works, the ForwardX11Trusted is simply an addon to ForwardX11.

---

### Post by e1geo on 2007-01-23
First -- It works with both set to **yes**:

ForwardX11 yes
ForwardX11Trusted yes

Thank you.

Second -- something is fishy here. according to the man page, the default for ForwardX11 is **no** and the default for ForwardX11Trusted is **yes** (Debian-specific). What is the point of setting things that way if only setting both to **yes** works? On the other hand, the entry for ForwardX11 also says, "... An attacker may then be able to perform activities such as keystroke monitoring if the ForwardX11Trusted option is ***also*** enabled." So someone thinks both should be set to **yes** if you want trusted X11 forwarding.

Can you think of any reason to set ForwardX11 to **no** and ForwardX11Trusted to **yes**? Is this a Debian/Ubuntu glitch?

Thanks again for solving the problem.

---

### Post by jtc on 2007-01-23
> **e1geo said:**
> Can you think of any reason to set ForwardX11 to **no** and ForwardX11Trusted to **yes**?

Yes, I can see a reason. I'm not sure if it is a good reason, but I can see it.

The way debian/ubuntu has it is that X-forwarding is disabled by default (ForwardX11 no). When you enable it thought (ForwardX11 yes) you get X-forwarding all the way (including the preset ForwardX11Trust yes). If you on the other hand have ForwardX11Trust no as default then the user first has to set ForwardX11 yes to get basic X-forwarding and then ForwardX11Trust yes to get the full trusted X-forwarding.

---

### Post by e1geo on 2007-01-23
I guess that makes sense. It would make more sense to have one parameter that you could set three ways: **off**, **on**, or **trusted**. But this setup evolved from on being trusted, basically adding the untrusted mode.

---

