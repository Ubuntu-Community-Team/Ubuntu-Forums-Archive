---
title: "ssh cli app with bookmarks similar to minicom?"
date: 2013-06-24
forum: Ubuntu, Linux and OS Chat
---

### Post by wildweaselmi on 2013-06-24
I apologize if this has already been answered but I have been googling this for awhile and still haven't found what I am sure must exist somewhere.

Does anyone know of a cli application for ubuntu that has similar menu to minicom that you can launch and then go to the directory (or bookmarks) and open an ssh or telnet connection based on what you setup?

This seems to simple and practical.  Yes I know PuTTy is the way to go if you have a GUI installed but we aren't allowed to have a GUI but we are allowed to use applications like minicom (they don't consider that a GUI).

Any suggestions on how we could use favorites / bookmarks / directory to open ssh and/or telnet sessions?

---

### Post by Lars Noodén on 2013-06-24
If you are using plain ssh, then you can put a lot of short cuts and customizations into ~/.ssh/config  The ultimate reference for that is the manual page [ssh_config](http://manpages.ubuntu.com/manpages/raring/en/man5/ssh_config.5.html).  You can make bookmark-like shortcuts for users and hosts.  The same will also apply to sftp, since it uses the same configuration file.

There ought to be a way to automatically switch directories, too.  I'll have to think on that.  With sftp, you just specify it on the same line as you run it from:

```

sftp user@server.example.org:/path/to/some/dir

```

---

### Post by wildweaselmi on 2013-06-24
Thanks but I did try and use the config and it allows to create an alias which is nice but I have a bunch of devices and was hoping more for the gui front end like minicom offers or the gui version of putty.  It makes it easier in a way.

I was hoping to organize which network gear I need to connect to from our ubuntu jump box.  If i could put folders I would sort it by city like dallas would have all its network gear and san antonio would have all its network gear.

The problem with alias in the ssh config is trying to remember all them.  I realize this problably doesn't exist but you never know unless you ask.

---

### Post by Lars Noodén on 2013-06-24
You could use real folders containing short shell scripts that connect you to the remote machines, one script per remote host.  That would give you a hierarchy to browse.  You could even navigate using mc (midnight commander) if bash is not to your taste.

I don't know if it's relevant, but you can also embed shell scripts in the head of private keys, so you can run the key like a script to take a step or two out of the login process.

---

