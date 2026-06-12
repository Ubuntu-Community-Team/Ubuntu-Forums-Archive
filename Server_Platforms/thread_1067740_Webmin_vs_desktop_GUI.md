---
title: "Webmin vs desktop GUI"
date: 2009-02-12
forum: Server Platforms
---

### Post by p.becks on 2009-02-12
Hello,

I recently installed Ubuntu 8.1 server on a old pc. I had a difficult time to configure samba shares but then i found webmin! (brilliant!)

In the mean time i installed a GUI (sudo apt-get install ubuntu-desktop) to get me through the difficulties of configuring samba. (but then, as i already said, i found webmin!)

NOW: I think that i don't need a GUI on the server anymore! BUT: i do want (from time to time) access the server with vnc (so i do need a GUI then)

What to do?

sudo apt-get remove ubuntu-desktop?
changes runlevel?

?

---

### Post by Neural oD on 2009-02-12
if u want to access with vnc - then you will need an xserver running - why don't u connect via ssh?

---

### Post by Neural oD on 2009-02-12
oh - yes if you want to remove it - then that command should work > sudo apt-get remove ubuntu-desktop

---

### Post by hyper_ch on 2009-02-12
you can do X11 forwarding without having xserver running there. Why would you want to vnc to the server?

---

### Post by p.becks on 2009-02-12
I think i need a GUI to fall back to in case things go wrong. VNC is not my favourite (i would prefer freenx but that one is bugging me...)

---

### Post by bigbearomaha on 2009-02-12
With webmin, you are able to do at least 90% or more of all the adimn tasks you will need to do.from file management to eth connections, config changes in servers, etc...

if you insist on having a GUI on a server, instead, start up the pc while sitting at it, do yor startup config, get t it going the way yuo want.

after you have it the way you want, switch to runlevel 3 ( at console type "telinit 3")

now, xserver and other services are not running.

You can do other access functions via ssh.  If you want GUI usage, even while in runlevel 3, you can "ssh -Y user@serverip"  this will allow you to type the name of the gui app you want to run on your remote pc.  for example, if you have Xfce as a lighter GUI, you can ssh -Y in and type "thunar" after logging in.  on your remote desktop, the thunar file manager will pop  up and your on your way.

Have fun, learn lots.

Big Bear

---

### Post by hyper_ch on 2009-02-12
> **p.becks said:**
> I think i need a GUI to fall back to in case things go wrong.
and if the gui goes wrong and webmin fails? what will you do then?

---

### Post by Dr Small on 2009-02-12
> **hyper_ch said:**
> you can do X11 forwarding without having xserver running there. Why would you want to vnc to the server?
You can? I tried that several times and was never able to get it to work.

---

### Post by hyper_ch on 2009-02-12
> **Dr Small said:**
> You can? I tried that several times and was never able to get it to work.

jdong said it so it must be true ;)

---

