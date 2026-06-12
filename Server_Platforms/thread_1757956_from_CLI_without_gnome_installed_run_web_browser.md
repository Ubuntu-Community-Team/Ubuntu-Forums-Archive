---
title: "from CLI without gnome installed run web browser"
date: 2011-05-14
forum: Server Platforms
---

### Post by red1916 on 2011-05-14
hi,

servers management is made (or I want to do it that way) form comand line so my ubuntu server 10.10 has no gnome installed, and I dont want start any windows manager.

But I installed ubuntu server for learning, so I still need very frequently google information about commands and lots of staff. access to ubuntu forums, etc.

since I run from the command line what I want is been able to start a web browser "window" like firefox but so far I could not do it. 

is that possible?  very important conditions.

1) in an environment from command line (ubuntu server 10.10 LAMP)
2) without having gnome or similars installed 

thxs in advance

---

### Post by Lars Noodén on 2011-05-14
Rather than sitting at the server while you work on it, sit at your desktop computer and connect to the server with SSH.  You can then use your desktop's browser and even cut-and-paste into the shell.  To do all that, you'll need the package [openssh-server](http://packages.ubuntu.com/natty/openssh-server) installed on the server.

---

### Post by red1916 on 2011-05-27
yes, I usually do that but the question is, if in front of the server, on the CLI, is it possible to open a web browser under the conditions I mentioned?

I know is twicked but in my house now a days, I have only the ubuntu server I use for testing learning so accessing from other computer is not possibility.

thx for the reply

---

### Post by Lars Noodén on 2011-05-27
> **red1916 said:**
> yes, I usually do that but the question is, if in front of the server, on the CLI, is it possible to open a web browser under the conditions I mentioned?

I know is twicked but in my house now a days, I have only the ubuntu server I use for testing learning so accessing from other computer is not possibility.

thx for the reply

If you tunnel X from your server, the graphical programs you run there will be displayed on your local machine.  So instead of the regular SSH connection, add **-X**

```

  ssh -l user [-X](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Remote_Processes#X11_Forwarding) server.example.org

```

---

### Post by Ron Jones on 2011-05-27
> **red1916 said:**
> yes, I usually do that but the question is, if in front of the server, on the CLI, is it possible to open a web browser under the conditions I mentioned?

I know is twicked but in my house now a days, I have only the ubuntu server I use for testing learning so accessing from other computer is not possibility.

thx for the reply
If I understand correctly, you have an Ubuntu server with a text-only interface, and you want the capability to open a browser window from said interface?

Under that assumption, I would suggest a program called Lynx. It's a text-only browser that you can use at the command line. However, I have to warn you that it's a bit "cumbersome." ;-)

---

### Post by arrrghhh on 2011-05-27
Indeed, there's a couple of text-only browsers - Lynx probably being one of the most popular ones.

But I don't think cumbersome captures it - you're trying to browse feature-rich sites on a text-only interface...

---

### Post by Lars Noodén on 2011-05-27
> **arrrghhh said:**
> Indeed, there's a couple of text-only browsers - Lynx probably being one of the most popular ones.

But I don't think cumbersome captures it - you're trying to browse feature-rich sites on a text-only interface...

If the site was designed with any competence and with attention to fulfilling accessibility requirements then the site should be perfectly usable (albeit a bit cumbersome) in a text-only interface.  The concept is to 'degrade gracefully'

However, I got the impression that the question was about graphical browsers and [forwarding/tunneling X](http://support.cs.toronto.edu/wiki/RemoteAccess/SSHTunneling/XWindowsMac) will provide the capability to run the browser on one machine and have it displayed on another.

Edit - Your major text only visitors are the search engine spiders.  You need for them to be able to use your site.

---

### Post by lykwydchykyn on 2011-05-27
If you can enable the [framebuffer](http://tldp.org/HOWTO/Framebuffer-HOWTO/) on your hardware, the "links2" browser will give a reasonably good browsing experience on the CLI (run it like "links2 -g").

However, it's probably far simpler to just install xorg and a minimal windowing environment like LXDE, openbox, or fluxbox and run the browser of your choice.

---

