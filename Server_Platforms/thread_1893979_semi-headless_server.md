---
title: "semi-headless server?"
date: 2011-12-11
forum: Server Platforms
---

### Post by DanH42 on 2011-12-11
I've had a server that ran Ubuntu 10.04 desktop with VNC for quite a while. I recently changed it over to 10.10 server, and I've been running it headless. The one thing I miss is being able to do ssh -X user@myserver and run GUI programs off the server. Is it possible to install something like Firefox that I could use that way, but have the server run normally (without X running) the rest of the time? Is this a completely idiotic question?

My thinking is that it would go something like this:
```
ssh dan@myserver.net
# startx
# firefox
( ... do some things ... )
^C# stopx
# exit
```

---

### Post by Lars Noodén on 2011-12-11
The X server actually resides on your desktop so the [font=Courier New]startx[/font] is not going to do anything if run on the server.  That said, you could run firefox from the server.

```

ssh -X dan@myserver.net
# firefox
( ... do some things ... )

# exit

```

---

### Post by DanH42 on 2011-12-11
I tried running Chrome, and I get this error:

```
# google-chrome
third_party/tcmalloc/chromium/src/system-alloc.cc:422] (null) failed.

(google-chrome:11952): Gtk-WARNING **: cannot open display: 
#
```

---

### Post by CharlesA on 2011-12-12
ssh -X should be working even without a GUI installed.

---

### Post by arrrghhh on 2011-12-12
> **CharlesA said:**
> ssh -X should be working even without a GUI installed.

This ^^.

So long as you have an xserver on your client, you should be able to forward X apps to it.  xmming on Windows, you should be good on Linux.

---

### Post by Lars Noodén on 2011-12-13
You can get [xming](http://sourceforge.net/projects/xming/) from Sourceforge.  You won't need it if you've already upgraded your desktop to Linux.

---

### Post by CharlesA on 2011-12-13
> **Lars Noodén said:**
> You can get [xming](http://sourceforge.net/projects/xming/) from Sourceforge.  You won't need it if you've already upgraded your desktop to Linux.
I always points people to the [developer's site]("http://www.straightrunning.com/XmingNotes/") when looking for XMing. They have an updated version that isn't available on sourceforge, but you do have to donate to get access to it.

---

### Post by gordintoronto on 2011-12-13
Is there some advantage to running Ubuntu Server over Ubuntu Desktop? I can see it, if you're running a high-volume web site, but not many people do that. For many things, Desktop is just a lot more productive.

---

### Post by CharlesA on 2011-12-13
> **gordintoronto said:**
> Is there some advantage to running Ubuntu Server over Ubuntu Desktop? I can see it, if you're running a high-volume web site, but not many people do that. For many things, Desktop is just a lot more productive.
I suppose the main difference is that Ubuntu server does not have a GUI installed and uses the server kernel.

If you need a GUI, then just install Ubuntu Desktop.

---

