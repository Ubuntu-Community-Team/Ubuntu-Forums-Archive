---
title: "Installing Gnome alternative"
date: 2009-03-31
forum: Server Platforms
---

### Post by mtime2457 on 2009-03-31
Hello,

My boss wants me to install the gnome desktop on our current Ubuntu server running 8.04.  I don't want too as I would prefer an alternative like Ebox, Openbox, or Fluxbox.  He also wants me to install SNORT which he is going to manage and I believe this is the primary reason as to why he wants to desktop environment.  So here comes my questions:

1) If he is to run Snort which GUI should I recommend if any of the above?

2) Is Ebox, Openbox, or Fluxbox going to allow him to run Snort remotely?  I'm assuming that all of Snorts commands are going to command line based.

3) I don't have much experience using Snort and while checking their website I was not able to find information on whether or not Snort has a GUI option.

---

### Post by Vegan on 2009-03-31
Gnome is the standard desktop for Ubuntu, others may not work well as the repository is set up for Gnome.

---

### Post by doogy2004 on 2009-03-31
> **Vegan said:**
> Gnome is the standard desktop for Ubuntu, others may not work well as the repository is set up for Gnome.

Any of the GUIs would work, this has nothing to do with the repositories.  The repositories simply store packages that can be installed on Ubuntu.

> 1) If he is to run Snort which GUI should I recommend if any of the above?

Any would do, if his preference is Gnome he is your boss and may resist any other options.

> 2) Is Ebox, Openbox, or Fluxbox going to allow him to run Snort remotely? I'm assuming that all of Snorts commands are going to command line based.

The GUI that you choose has nothing to do with remote connectivity.  If he is going to use snort remotely he is either going to use the CLI (SSH), a web interface (HTTP), or if he uses a GUI for snort he could use X-forwarding.

> 3) I don't have much experience using Snort and while checking their website I was not able to find information on whether or not Snort has a GUI option.

[http://www.google.com/search?q=snort+gui](http://www.google.com/search?q=snort+gui) the first few results can point you to more information about snort GUIs.


My final recommendation is to install ssh and xauth.  SSH will allow him to login to the server remotely and over a secure connection.  xauth will allow GUI applications to use x-forwarding through ssh, without the need for a full desktop environment of anykind.

---

### Post by mtime2457 on 2009-04-01
He wants a GUI to run reports, reports via Snort and probably any other program he reads about while on the toilet....

---

