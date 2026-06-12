---
title: "Network printer won't work with windows clients"
date: 2009-08-16
forum: Server Platforms
---

### Post by fela on 2009-08-16
I have a strange problem here. Basically I have a Ubuntu (desktop edition) server running a CUPS print server, configured using the standard Ubuntu GUI app.

Now here's the problem: shared printing works fine from Linux or Mac OSX clients, but trying to print from a windows (XP or vista) client just gives an 'access denied, unable to connect' error, and fails to print anything.

What do you think the error could mean? Since printing from *NIX clients seems to work fine I'm wondering whether it's just (as ever ;)) windows behaving badly.

---

### Post by HermanAB on 2009-08-16
Howdy,

Before trying to do complex networking such as Samba and CUPS, you first have to have the basic networking settings done perfectly.

You can debug networks using the telnet program - it should be readily available on both Linux and Windows.  The CUPS server runs on port 631/TCP, so do this test:

On Linux:
$ telnet localhost 631
you should get a banner

Now try again using the real IP address:
$ telnet 192.168.1.100 631
and you should get the same banner.

Now go to the Windows machine and repeat it:
C:\> telnet 192.168.1.100 631

If at any one of the steps above it doesn't work, fix it, since it won't help going further if it doesn't.

Now try the same with a browser from Linux and Windows:
[http://192.168.1.100:631](http://192.168.1.100:631)

---

### Post by fela on 2009-08-16
Thanks for that.

Okay, I've fell at the first hurdle it seems, well something must need reconfiguring anyway. I tested it first on the server, by connecting via ssh and running:

```
telnet localhost 631
```

Here is the output:

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```

By the way, it just left me with a blinking cursor until I terminated with ^C. I don't think this is what should have happened. Would you say there's anything wrong with that? Sorry, I've never used telnet before :P

Thanks :)

EDIT: I think it's actually working (is that really what you meant by banner? lol). I went to 10.0.0.4:631 (server's IP) with my linux desktop on firefox, and it came up with the CUPS config page. I'll have a look thru all of it. Again, thanks so much for the help! Much appreciated.

EDIT 2: the CUPS config page seemed to have the same sort of info as the GUI app on GNOME. It all seems to be correct (and works for UNIX/Linux systems including OSX - is this because windows doesn't use CUPS?).

---

