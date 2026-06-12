---
title: "Status of Mir and Wayland"
date: 2015-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by montag dp on 2015-03-09
I haven't been following too closely lately, but I did a search and didn't find too much info.  Does anyone know the current status of Mir and Wayland?  How actively are they being developed, what are the projected timelines for phasing out X, etc.  I'm just curious.

---

### Post by grahammechanical on 2015-03-09
Projected timelines?

I hope developers have learned enough not to set time limits. I causes disappointment as time targets are not met.

The phasing out of X will taken place when the developers of distributions decide to not use X any more and to use something else. Some of those distributions will hold back to see how things work out when other distributions switch over and what complaints users make.

The Gnome developers are working on a Gnome Wayland compositor. It is available for testing with Ubuntu Gnome. Why not get involved yourself and then you will be up to date.

[http://ubuntuforums.org/showthread.php?t=2264340](http://ubuntuforums.org/showthread.php?t=2264340)

Ubuntu is running on Mir on the Ubuntu phones and when Ubuntu tablets are released Ubuntu will then be running on Mir on Ubuntu tablets. As for the desktop, Ubuntu Vivid Vervet (15.04 development) does get updates to Wayland libraries. So, it is not an either or situation for the Ubuntu family of distributions.

A lot of work is being done on convergence of the Ubuntu phone code base into the Ubuntu desktop code base. When that is completed then Ubuntu desktop will be running on Mir. But I have heard conflicting reports. With Mir comes Unity 8. I have heard that 16.04 will have Unity 7 as a default with Unity 8 as a login option. Then again I have also heard that Unity 8 could be with us by the release of 15.10.

There is a Ubuntu Desktop Next ISO image that we can install. That will give us the Ubuntu phone code running on Mir and we can track the convergence of the Ubuntu desktop right there. But there is a long way to go.

This thread has videos showing the development progress. Look at the last video by Will Cook, the Ubuntu Desktop Manager. That shows a Ubuntu desktop with desktop apps like Libreoffice running under Unity 8 running on Mir. This code is running on a tablet and the switch from phone/tablet style UI to desktop style UI happens when a bluetooth mouse is connected. It holds future promise of desktop apps which are coded for X being able to run on Ubuntu desktop running on Mir.

[http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986/24](http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986/24)

Regards.

---

### Post by deadflowr on 2015-03-09
Both are under extreme development right now, which I think is great.
You can test either.
You can install a mir session on Ubuntu
[https://wiki.ubuntu.com/Unity8Desktop](https://wiki.ubuntu.com/Unity8Desktop)
and even try out an lxc version
[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

And for Wayland all I can says is it's [Friday!]("http://sourceforge.net/projects/rebeccablackos/")
you can also follow [nerdopolis' Wayland Live Cd]("http://ubuntuforums.org/showthread.php?t=1906762") on that one's development.

As far as phasing otu X, that will depend on programs being rewritten to run natively on either mir and/or wayland.
The sooner that happens the sooner X fades away.

---

### Post by montag dp on 2015-03-09
Thanks for the information, everyone.  For projected timelines, I didn't mean official ones; I was just wondering how close things are to being ready for prime time.  Perhaps that part of the question wasn't phrased correctly.  Of course, it will probably be decades before X is completely phased out, since it has been the standard for so long.

---

### Post by ssam on 2015-03-09
Fedora 22 will probably be using wayland to display the login screen by default.

[https://blogs.gnome.org/uraeus/2015/01/19/planning-for-fedora-workstation-22/](https://blogs.gnome.org/uraeus/2015/01/19/planning-for-fedora-workstation-22/)

---

### Post by bodhi.zazen on 2015-11-04
Fedora 23 includes gnome-wayland

Gnome applications (gedit) are running on wayland.

Applications that do not run on wayland use Xwayland.

You can use looking glass to see if an application if using wayland or Xwayland.

See [https://blogs.gnome.org/uraeus/2015/08/19/fedora-workstation-next-steps-wayland-and-graphics/](https://blogs.gnome.org/uraeus/2015/08/19/fedora-workstation-next-steps-wayland-and-graphics/)

[http://fedoramagazine.org/update-wayland-support-fedora-23/](http://fedoramagazine.org/update-wayland-support-fedora-23/)

Fedora is targeting Fedora 24 for wayland by default.

---

### Post by grahammechanical on 2015-11-04
@ bodi.zazen

Good to hear from you again. Thank you for the update about the "competition." :) It is strange, how for years people talk about how secure Linux is especially in comparison to some other OS and then after revealing plans to replace X we hear how vulnerable X is. Ignorance lets us sleep at nights. :)

I have just heard on the Ubuntu Online Summit that the plan is to bring Gnome 3.18 DE into Ubuntu 16.04. That should be useful to the Ubuntu Gnome developers as they transition to a Gnome Wayland compositor.

Since this thread was first started six months ago plans have most certainly been modified. We now hear of a traditional Ubuntu (Linux+X+Compiz+Unity7) and Personal Ubuntu (Linux+Mir+Unity8+Snappy packaging). And a few hours ago when Jane Siber was asked: "When will Unity 8 become the default?" The reply was: When it is ready and when the users are happy about it? Or something close to that. They do not want to surprise the users like they did with Unity.

Regards.

---

### Post by mikodo on 2015-11-04
> **bodhi.zazen said:**
> Fedora 23 includes gnome-wayland

Gnome applications (gedit) are running on wayland.

Applications that do not run on wayland use Xwayland.
It is so nice to see you here. :)

Yes. XWayland provides for functionality of X as transitioning to Wayland is progressed:  [http://wayland.freedesktop.org/xserver.html](http://wayland.freedesktop.org/xserver.html)

> **grahammechanical said:**
> 
I have just heard on the Ubuntu Online Summit that the plan is to bring Gnome 3.18 DE into Ubuntu 16.04. That should be useful to the Ubuntu Gnome developers as they transition to a Gnome Wayland compositor.
So, Ubuntu providing for XWayland support for X supported Desktops, as they move towards using the Wayland compositor.

The plan for transition from XMir. Cool. I knew the "Flavors" are important to the Ubuntu landscape. This exemplifies their commitment.

Then, all the work towards "convergence" for, Unity.

Amazing ...

Addendum: I hope I got that right on "the plan" using XWayland for transitioning. Nevertheless, XMir or XWayland to the possibility of Wayland for the flavors wanting its' use eventually, is welcomed to read.

---

