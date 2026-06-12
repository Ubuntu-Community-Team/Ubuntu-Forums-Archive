---
title: "I need to forward X11 for a single app"
date: 2018-02-02
forum: Server Platforms
---

### Post by timonoj on 2018-02-02
Hi guys, I believe I'm going to need to get X11 forwarding in order to run a single app, the new Crashplan for small business. How can I go about it? Do I need to install a whole DE? Can I just install the bare minimum X11 libraries in order to just run that app forwarding to my actual desktop/laptop? What should I install in order to do this?

Thank you!

---

### Post by TheFu on 2018-02-03
No DE needed.

X/Windows has a client-side and a server-side. The X/server is huge and runs on the machine you sit behind it.  The X/client is the application running on the remote box and communicating to your X/server.

So, if you are already running an X11 server locally, then you do not need much on the other side (the client) for it to work.  On the client-side, just install the single X application via the package manager and that should install any client-side dependencies automatically.  I like to install the xterm application to get a bare minimal X/Client setup. Plus that is helpful for troubleshooting.

After you get it installed, the easiest way to run it, assuming this is a 100Mbps connection or better, is to use ```
ssh -X userid@server-ip /path/to/application/on/remote-system
```  If the application is in the userid's PATH, then that will work over ssh too.

---

### Post by timonoj on 2018-02-03
Thanks for your fast reply! Sorry if I got a bit confused. So you mean the X-Server runs in the machine I sit behind...Say, my laptop? So the X-Client is/should be in the Ubuntu server? 
Do you know of an easy app I could use in the Ubuntu server to test it works? I tried xeyes, but it depends on X11 libraries, which are not installed at the moment (on the Ubuntu server).

---

### Post by TheFu on 2018-02-03
[https://unix.stackexchange.com/questions/6205/must-an-x11-server-be-installed-for-x11-forwarding-over-ssh-to-work](https://unix.stackexchange.com/questions/6205/must-an-x11-server-be-installed-for-x11-forwarding-over-ssh-to-work)
X11 client libs are necessary for a client to work, if the program isn't statically linked (which would be HUGE and bloated). xeyes dependencies should have installed them.  No way around that.

---

### Post by timonoj on 2018-02-03
> **TheFu said:**
> [https://unix.stackexchange.com/questions/6205/must-an-x11-server-be-installed-for-x11-forwarding-over-ssh-to-work](https://unix.stackexchange.com/questions/6205/must-an-x11-server-be-installed-for-x11-forwarding-over-ssh-to-work)
X11 client libs are necessary for a client to work, if the program isn't statically linked (which would be HUGE and bloated). xeyes dependencies should have installed them.  No way around that.

Perfect, thanks for the help, I'll give it a shot tomorrow :)

---

### Post by timonoj on 2018-02-04
OK, so it works! Here's a few things I needed to do in order to get it working:
Edit /etc/ssh/sshd_config and add the two following (I only added the first one initially and DISPLAY wasn't getting set):
```

X11Forwarding yes
X11UseLocalhost no

```

Xauth was installed, but I needed to ssh with the -X -A options. There wasn't an .Xauthority file, so it created one. After that, I could launch Xeyes and it would throw the image onto my laptop. Perfect!

Thank you guys!

---

### Post by TheFu on 2018-02-05
If solved, please mark the thread "solved" (thread tools above) to help the community.

---

### Post by NotQuiteSU on 2018-05-03
> **timonoj said:**
> OK, so it works! Here's a few things I needed to do in order to get it working:
Edit /etc/ssh/sshd_config and add the two following (I only added the first one initially and DISPLAY wasn't getting set):
```

X11Forwarding yes
X11UseLocalhost no

```

Xauth was installed, but I needed to ssh with the -X -A options. There wasn't an .Xauthority file, so it created one. After that, I could launch Xeyes and it would throw the image onto my laptop. Perfect!

Thank you guys!

I'm running this from a windows computer, so a little different. How were you able to get the desktop to display?

---

