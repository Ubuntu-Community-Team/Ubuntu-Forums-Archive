---
title: "Ubuntu Server as X windows client"
date: 2008-08-19
forum: Server Platforms
---

### Post by macsmith on 2008-08-19
I'd like to install the necessary software to allow my Ubuntu 8.04 server to be able to open xwindows on another xwindows server.

What software packages do I need to install?  Everything I've found so far adds X server abilities rather than just X client abilities.

TIA

Ian
[www.festivalpreviews.com](www.festivalpreviews.com)

---

### Post by MJN on 2008-08-19
It sounds like you may be getting confused about what is required (granted this can be confusing at first given the apparent swap of client/server terms).
 
An X 'server' is the graphical environment you would run on the machine you sit at, whereas the X 'clients' are the applications that you are wishing to access.
 
So, let's say you've got your Ubuntu server sat there with all your GUI(X)-enabled applications sat on it. If you want to access those applications from a remote machine then you must install an X server on that remote machine (e.g. X.Org in Linux, Xming/eXceed on Windows etc).
 
Hence, in the above scenario, you don't have to do anything with your Ubuntu server to support this.
 
Mathew

---

### Post by macsmith on 2008-08-19
Hi,

thanks for the reply.

I don't think I am confused but rather that I haven't explained the problem well.  Taking an example: I want to execute the programme xterm on the Ubuntu server and for the resultant window to open on a remote machine.

Obviously the remote machine will have to have an X server running to be able to serve the request (open up the xterm on its screen).  The problem I have is that having created an Ubuntu server, there are none of the client X programmes (like xterm).

So, what package(s) do I need to install on the Ubuntu server to get the likes of xterm but without installing the X server itself?

Perhaps it would be easier just to install the windows gui and disable the server (?)

Thanks

Ian
[www.festivalpreviews.com](www.festivalpreviews.com)

---

### Post by MJN on 2008-08-19
Oh I see. I'm not sure if it is possible to install xterm with X itself as no doubt they share so many libraries etc that the former requires the majority of the latter.

By 'windows GUI' do you mean the graphical X display? If so, yes, you could just not run it (I think).

Mathew

---

### Post by Ximbiot on 2008-08-19
The X Server is what you need.  There is no such thing as an X client in the sense you are talking about.  Each and every program which opens an X window anywhere is considered to be an X client.

So, just install the X server locally if it's not installed already, then just open a shell to the remote machine via ssh and run the x command you want via your remote shell.  If you get errors or don't see the window for your remote command open locally, then read about the ForwardX11 host config key of SSH and the X11Forwarding SSHD key in the ssh_config and sshd_config man pages, respectively.

Notice that you don't need an X server on the *remote machine* in this scenario.

---

### Post by MJN on 2008-08-19
I think Ian wants to sit at his remote machine and run xterm (i.e. it runs on his server and he sees the output on the remote machine) hence he will need an X server running on the remote machine.

(Man this is getting confusing!)

Mathew

---

### Post by macsmith on 2008-08-19
thanks for the reply, so coming back to the begining: *So, just install the X server locally*, which package would this be?

Thanks

Ian
[www.festivalpreviews.com](www.festivalpreviews.com)

---

### Post by Ximbiot on 2008-08-19
> **MJN said:**
> I think Ian wants to sit at his remote machine and run xterm (i.e. it runs on his server and he sees the output on the remote machine) hence he will need an X server running on the remote machine.

Hrm, okay, so I'll try to answer the following question in a much less verbose way.  :)

> **macsmith said:**
> Hi,
So, what package(s) do I need to install on the Ubuntu server to get the likes of xterm but without installing the X server itself?
[www.festivalpreviews.com](www.festivalpreviews.com)

The machine that you want the GUI window to open on needs the X server.

The machine you want to actually run `xterm' (not display it) just needs `xterm' and its dependencies.  Use `apt-get install --fix-broken xterm' to install it with all the files you need.

---

### Post by MJN on 2008-08-19
(Edit: Oops - you beat me to it!)

If you want xterm to be an available app then just install it - the dependencies will handle the rest.

Mathew

---

### Post by macsmith on 2008-08-19
Hi,

apt-get is new to me but I cut and pasted the command.  Unfortunately it seems to have failed:

root@macsmithServer:~# apt-get install --fix-broken xterm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  emacs: Depends: emacs21
  pgplot5: Depends: libx11-6 but it is not going to be installed
  xterm: Depends: libfontconfig1 (>= 2.4.0) but it is not going to be installed
         Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
         Depends: libsm6 but it is not going to be installed
         Depends: libx11-6 but it is not going to be installed
         Depends: libxaw7 but it is not going to be installed
         Depends: libxext6 but it is not going to be installed
         Depends: libxft2 (> 2.1.1) but it is not going to be installed
         Depends: libxmu6 but it is not going to be installed
         Depends: libxt6 but it is not going to be installed
         Depends: xbitmaps but it is not going to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).
root@macsmithServer:~#

---

### Post by Ximbiot on 2008-08-19
> **macsmith said:**
> thanks for the reply, so coming back to the begining: *So, just install the X server locally*, which package would this be?

That would be `xorg', but I'd recommend installing the `gnome' package as well for a more comfortable desktop experience.

---

### Post by Ximbiot on 2008-08-19
> **macsmith said:**
> Hi,

apt-get is new to me but I cut and pasted the command.  Unfortunately it seems to have failed:

root@macsmithServer:~# apt-get install --fix-broken xterm


Sorry, I usually let `dselect' handle dependency management for me and didn't want to explain dselect's interface.  Use the apt-get command I gave you without `--fix-broken'.  I just ran the command to be sure here and it worked:

  $ sudo apt-get install xterm

---

### Post by macsmith on 2008-08-19
forget my last question.  I didn't realise that apt-get suggested remedies and dowloaded the stuff it needed, all by itself!  I grew up with the likes of slackware when there was only a big thick Linux book on the shelf.  The internet was just being born!

xterm -display ipaddress:0.0  works just fine now.

Thanks

---

### Post by macsmith on 2008-08-19
apt-get install x11-apps seems to have loaded all the other X applications I need.

Ian
[www.festivalpreviews.com](www.festivalpreviews.com)

---

