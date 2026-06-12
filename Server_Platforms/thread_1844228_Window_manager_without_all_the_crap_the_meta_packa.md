---
title: "Window manager without all the crap the meta package installs?"
date: 2011-09-14
forum: Server Platforms
---

### Post by HittingSmoke on 2011-09-14
Is there a way to install only a light weight window manager without all the apps provided by the *buntu-desktop meta packages?

I'd like this on my server so I can start it up specifically when I want to run something that's easier to manage with a GUI, like Dropbox on my test server, then shut it down as soon as I'm done.

I'd like the OS to operate normally, booting to the command line requiring me to launch the window manager manually when I need it.

Gnome or XFCE would be fine, it doesn't really matter. I just need something light weight.

---

### Post by Blasphemist on 2011-09-14
Consider enlightenment. [http://www.enlightenment.org/](http://www.enlightenment.org/)

I've been using it on bodhi linux. It is lightweight and I think might meet your needs.

---

### Post by HittingSmoke on 2011-09-14
> **Blasphemist said:**
> Consider enlightenment. [http://www.enlightenment.org/](http://www.enlightenment.org/)

I've been using it on bodhi linux. It is lightweight and I think might meet your needs.

That looks nice, but I'm more interested in something that's already in the repos that I can install with apt-get. Provided I only need a WM for the ever so basic and rare function of running a couple of packages that require one to set up I'd like to keep things as simple as possible.

---

### Post by Entilza on 2011-09-14
try lxde?

[http://wiki.lxde.org/en/Installation](http://wiki.lxde.org/en/Installation)

[http://sourceforge.net/projects/lxde/](http://sourceforge.net/projects/lxde/)

A very lightweight one that installs almost nothign is FVM2 :-) [http://www.fvwm.org/](http://www.fvwm.org/)

---

### Post by HittingSmoke on 2011-09-14
I think I'm explaining this poorly.

What I want is what [this guy]("http://ubuntuforums.org/showpost.php?p=6229099&postcount=8") is suggesting, but up to date info on how to go about it.

If I install gnome-desktop I get all of the packages it comes with like Ooo, an email client, sound drivers, etc.

I just need a window manager that's in the repos that I can install without anything else.

Thanks.

---

### Post by kerry_s on 2011-09-14
You need to use the no reccommends switch, do man apt-get.

---

### Post by HittingSmoke on 2011-09-15
> **kerry_s said:**
> You need to use the no reccommends switch, do man apt-get.

So I'd do something like *apt-get install ubuntu-desktop --no-install-recommends* ?

How much exactly would that install out of the meta package?

EDIT: Nevermind. I found the package list [here]("http://packages.ubuntu.com/lucid/ubuntu-desktop") but I was looking at the wrong version so it wasn't listing the recommends.

I was hoping for something even more slimmed down (no need for ALSA, network GUI tools, etc) but I'll give that a try anyways.

However, my concern is wouldn't this package set the OS to boot into the window manager by default instead of to the command line?

---

### Post by kerry_s on 2011-09-16
Don't use meta packages, go straight for the package like gnome-core or better yet just install a window manager if all you need is a GUI.

---

### Post by arrrghhh on 2011-09-16
Why not just forward X over SSH?

I seriously see no reason for any DE on a server.  Just a waste of resources, and leaves a lot of packages to update.  Not to mention potential security holes...

---

