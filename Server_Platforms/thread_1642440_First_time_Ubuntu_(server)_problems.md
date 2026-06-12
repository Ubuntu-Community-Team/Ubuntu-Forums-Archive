---
title: "First time Ubuntu (server) problems"
date: 2010-12-10
forum: Server Platforms
---

### Post by mark_1987 on 2010-12-10
Hello,

First things first. I am Mark and live in the netherlands. Recently i installed ubuntu on my netbook and it works great even better then Windows XP. I am in possesion of a Windows Home Server that i am not happy about. I figured trhat i could install a linux os to replace the Home Server OS. I'm fairly new to Ubuntu and Linux in general, but i love to give it a try.

[B]Goals

[/B]1. Share my files and folders for windows pc's and Ubuntu pc's
2. Remote Client backup for Windows and ubuntu pc's
3. Streaming media to remote location (now using orb)
4. A newsgroup server and bittorent client.
I've tried ubuntu server, but i don't know how to handle it. Do guy have suggestions about what distro to use and where to start to accomplish my goals?

---

### Post by HermanAB on 2010-12-10
Howdy,

Ubuntu is not the easiest Linux - that honour belongs to Mandriva, with OpenSuse a close second.  However, Mandriva is now a Russian company and the Mageia fork is not ready yet. 

So if you want a distribution where you can go click happy and never need to use a command line, I'd recommend OpenSuse.

---

### Post by CharlesA on 2010-12-10
I'll give a +1 to OpenSUSE.

You can get all those to work with some effort. Do you want a GUI or do you want to do everything from the command-line?

For the file sharing bit, you can check out the [tutorial]("http://charlesa.net/tutorials/linux/samba.php") I wrote up about it.

It's not the only way to do it, but it's the way I found that works.

---

### Post by ingeva on 2010-12-11
> **mark_1987 said:**
> Hello,

First things first. I am Mark and live in the netherlands. Recently i installed ubuntu on my netbook and it works great even better then Windows XP. I am in possesion of a Windows Home Server that i am not happy about. I figured trhat i could install a linux os to replace the Home Server OS. I'm fairly new to Ubuntu and Linux in general, but i love to give it a try.
I agree about Windows. It gives you nothing but trouble. However, Linux also require some learning, like Windows does (Do you remember when you were a newbie with Windows? :) )

I recommend that you make yourself aquainted with the Ubuntu desktop first.  Learn how to install NFS (for Linux shares) and Samba (until you can use NFS with Windows 7).
Build script files to replicate what you need to do. This is useful when you install the server edition, because, after all, when you have got things going, you don't need the resource-consuming desktop software.
One nice thing about Samba (for Windows shares) is that you can use Linux partitions and share them with Windows, but NFS is faster and should be the preferred method.

You can control a remote server using ssh, so make sure you install that. Then you don't need a keyboard or display for the server. All you need is one cable for power and one for the network.

---

### Post by mark_1987 on 2010-12-11
Thank you for your input. I am running Opensuse in VMware for testing, but i find it very difficult to share files with samba. I cant find a good HowTo on the internet either.

---

### Post by pepsifx357 on 2010-12-11
I've noticed that everything that is listed in your goals has a setup page on Ubuntu Documentation.  If you can cut a paste or copy commands from the screen to the server then you can do it.  There is something to be said about a headless server.  After I got into command line, I was pretty fluent in about a month.  Still learning though.

---

### Post by CharlesA on 2010-12-11
> **mark_1987 said:**
> Thank you for your input. I am running Opensuse in VMware for testing, but i find it very difficult to share files with samba. I cant find a good HowTo on the internet either.

Check out the one I linked to in my previous post.

There are a ton of Samba documentation out there.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by HermanAB on 2010-12-11
Howdy,

Note that of all network systems, Samba is the most difficult and arcane.  It requires hundreds of lines of configuration.  You really should buy and read the Samba book if you want to use it seriously and the book is a good two inches thick.

NFS is the simplest network system and it requires only 1 line of configuration on a machine.  Windows Services for UNIX is a free download from Microsoft and it is easy to install.

---

