---
title: "how can I tell if I'm running server or desktop"
date: 2008-05-03
forum: Server Platforms
---

### Post by davidshere on 2008-05-03
Where I work, we have a large server running Ubuntu.  I recently updated it from 7.10 to 8.04, to take advantage of the five years of server support.  But then I got to thinking: This computer has the desktop GUI on it, and I can't remember if we initially installed Ubuntu Server and then put the desktop GUI on top of it, or if we installed Ubuntu Desktop and then installed the various packages we wanted for our server (apache, postgres, etc).

Then I did some more thinking.  Is Ubuntu Server actually a different *version* of Ubuntu, or is it just a different set of initial packages, like Kubuntu and Ubuntu Studio?  If the latter is the case, how can desktop be supported for three years and server for five?  Somewhere a "difference" has to exist between server and desktop for them to be supported for different time periods, right?

Sooooo.... If they really are different versions, and I want five years of support for my Ubuntu Desktop, all I have to do is install server, put the desktop GUI on top of it, remove the server packages I don't want, and presto!  I have five years of support for my custom-made desktop/server hybrid that isn't really a server anymore

Since the above seems somewhat goofy, I did yet more thinking.  Does the "three years of support" for desktop apply mostly to the desktop GUI-related packages, and the "five years of support" apply mostly to the server-related packages?  This would seem to make more sense, be simpler to implement, and easier to "enforce".

Is any of this close to reality, or is there another scenario I haven't considered?

---

### Post by LeoSolaris on 2008-05-03
I think it means they will keep sending updates for the server programs longer than they will continue updating the desktop programs. That would mean all of the desktop programs that ya use would have to be manually updated, but the server programs like apache would still update.

I may be wrong, but that's how it reads to me.

---

### Post by windependence on 2008-05-04
What is the ouput of *uname -a*  ?

-Tim

---

### Post by davidshere on 2008-05-04
> **windependence said:**
> What is the ouput of *uname -a*  ?

-Tim

```
Linux cadillac 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```

---

### Post by jc_emoon on 2008-05-04
I think output must be "Linux xxx 2.6.24-16-server ..." if server version is running.

---

### Post by windependence on 2008-05-04
Looks like desktop to me.

-Tim

---

### Post by nanog on 2008-05-04
If you want to switch just remove the generic kernel and install the server kernel.

---

### Post by pamchi on 2008-07-14
the most simple way to know it is looking in 

/etc/apt/sources.list

you can use "nano" to see the file in this way

nano /etc/apt/sources.list

So in the first line it will tell the information that you were looking for.

---

### Post by davidshere on 2009-12-03
Revisiting this issue ... my main question still being "How can I tell if I'm running server or desktop?"

the first line of my sources.list file looks like this:

```
# deb cdrom:[Ubuntu 7.04 _hardy Fawn_ - Release i386 (20070415)]/ hardy main restricted
```

and uname -a produces this:
```
Linux boxname 2.6.24-25-generic #1 SMP Tue Oct 20 07:31:10 UTC 2009 i686 GNU/Linux
```

I get the feeling here that this machine is desktop.

"What I'm really trying to do" here is determine upgrade requirements to get the box to Lucid next April.  I just realized that we'll have to upgrade the box to Intrepid before April anyway, since the support for Intrepid runs out then, regardless of whether the machine is server or desktop.

I plan on dragging a virtual machine through the process first, to get all (or most) of the packages in my apt-cacher, so it would be nice to make sure that machine is created as the right one (server or desktop) so that it caches the right packages.

---

### Post by The Real Dave on 2009-12-03
From [Ubuntu Docs]("https://help.ubuntu.com/community/")

> What's the difference between desktop and server?
The first difference is in the CD contents. The "Server" CD avoids including what Ubuntu considers desktop packages (packages like X, Gnome or KDE) but includes server related packages (Apache2, Bind9 and so on). Using a Desktop CD with a minimal installation and installing, for example, apache2 from the network, one can obtain the exact same result that can be obtained by inserting the Server CD and installing apache2 from the cd-rom.
The Ubuntu Server Edition installation process is slightly different then the Desktop Edition. Since by default Ubuntu Server doesn't have a GUI the process is menu driven, very similar to the Alternate CD installation process.
Ubuntu server install by default a server optimized kernel.
Ubuntu Desktop will receive a 3 years support, Ubuntu Server will be supported for 5 years.

It mentions that the kernel is server optimized. I remember reading more about it somewhere, but can't remember exactly where. This was the first Google result ;)

---

### Post by Cheesemill on 2009-12-03
> **davidshere said:**
> Sooooo.... If they really are different versions, and I want five years of support for my Ubuntu Desktop, all I have to do is install server, put the desktop GUI on top of it, remove the server packages I don't want, and presto!  I have five years of support for my custom-made desktop/server hybrid that isn't really a server anymore

The only packages that are supported for 5 years are the ones that are on the server installation CD (Apache, DHCP, DNS, MySQL, etc). Any packages that you install that aren't on the CD are only supported for 3 years.

---

