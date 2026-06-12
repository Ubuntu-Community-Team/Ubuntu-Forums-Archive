---
title: "Should I be using Ubuntu Server?"
date: 2009-03-17
forum: Server Platforms
---

### Post by dodle on 2009-03-17
I've got a server set up with Ubuntu 8.04.  Is it better to use the server version?  Also, does the server version have a desktop, or do I need to set up everything via console?

---

### Post by cariboo on 2009-03-17
The server install does not have a desktop, so if you need one I would suggest staying with what you have. I most cases you won't notice the difference between the server kernel and the desktop kernel.

Jim

---

### Post by HermanAB on 2009-03-17
The server edition is meant for a machine that is going to spend its life lurking headless in a dark corner of a dank data centre, doing something unspeakable.  If you have a keyboard and screen on it, then you are better off using the regular Ubuntu version.

Cheers,

Herman

---

### Post by netztier on 2009-03-17
> **dodle said:**
> I've got a server set up with Ubuntu 8.04.  Is it better to use the server version?  Also, does the server version have a desktop, or do I need to set up everything via console?

Ubuntu Server by design is console-only.

You *can* install a GUI, but widespread wisdom says that it's not recommended:

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

(now this URL's been posted half a dozen times in during the last two weeks. A bit of forum search would've helped to find it, easily)

If you just want to make some first steps in how to configure Apache, Samba, NFS, PHP, MySQL and all those services you might be interested in, you can always install and try them on an Ubuntu Desktop installation. Functionally, it won't make any difference - the main one being that the server kernel has other tuning parameters, making it better for server style workloads. Probably, you won't care about that when you're just starting off.

You'll soon notice that all of these tasks mainly involve the editing of text-based configuration files and calling start/stop scripts for the server programs from the command line. Editing config files can easily be done whithout a GUI: nano, vi, emacs, mcedit (the editor from midnight commander) are just a selection of text based editors. So why have a GUI in the first place? 

regards

Marc

---

### Post by dodle on 2009-03-17
Thanks for the quick responses.  From what you've told me, I think that I will hang on to my desktop for a while.  Maybe I'll give the server version a test run further down the road, when I am more experienced.

Thanks again.

---

### Post by mocoloco on 2009-03-17
Handy option for setting up server tasks, in Synaptic if you go to "Edit -> Mark Packages by Task"  you have a bunch of pre-configured meta-packages that make it easy to set up roles, server and non-server.

---

### Post by netztier on 2009-03-17
> **mocoloco said:**
> Handy option for setting up server tasks, in Synaptic if you go to "Edit -> Mark Packages by Task"  you have a bunch of pre-configured meta-packages that make it easy to set up roles, server and non-server.

er.. now I'm impressed. I didn't even know there was a synaptic version of the command line's **tasksel**!

We never stop learning!

regards

Marc

---

### Post by mocoloco on 2009-03-17
> **netztier said:**
> er.. now I'm impressed. I didn't even know there was a synaptic version of the command line's **tasksel**!

We never stop learning!

regards

Marc

And I didn't know there was a CLI way to do this. Thanks for passing the learning torch right back :)

---

### Post by Vegan on 2009-03-17
Learning the CLI can bring skills never anticipated. My own machine lives like a nonsecript rack mounted box with no keyboard, video or mouse. I manage it all remotely with telnet.

I could have 1 machine or 1 million, all run the same more of less. However I would have to manage the network a bit better than I have now.

Also each machine needs a unique name to be able to find each other. This is where domain controllers find their real power.

I run my IBM like a mainframe, I even have COBOL running on it. COBOL is still used here and there. FORTAN is another language I support.

This is because many shops still use mainframes as a super server. Who am I too argue with the boss, I simply fix the problems.

Mastering the CLI is not trivial but there are tons of books on Linix and UNIX that are worth adding to the library.

---

