---
title: "Is it worth using Ubuntu Server Edition?"
date: 2011-05-25
forum: Server Platforms
---

### Post by tristram60 on 2011-05-25
Currently, I am hosting my own website on ubuntu desktop edition 10.04 (I use 10.04 because I have found it to be the most stable).  Is it worth it for me to migrate to server edition?  My only problem is that I really know nothing about the terminal but is it worth it for me to try?  I haven't set up anything fancy, I am using it just for Apache.  Is it simple to configure the server to work just with apache?

Thanks

---

### Post by wojox on 2011-05-25
Sure. Learning command line Linux is where it's at. :P

---

### Post by kaldor on 2011-05-25
> **wojox said:**
> Sure. Learning command line Linux is where it's at. :P

For sure :)

It's daunting at first, but in the end it is well worth it and not that hard. There is also a load of info online. 

Though, if you are doing just fine with a GUI and you don't want to mess things up, there's not really any reason. However, being able to fly around using *only* the terminal is a very good skill to have.

---

### Post by snowpine on 2011-05-25
Apache is identical on the Server and Desktop editions. There is no reason to migrate, in my opinion.

If you want to learn more about the terminal, you can certainly do that from the Desktop edition. :)

---

### Post by kaldor on 2011-05-25
> **snowpine said:**
> Apache is identical on the Server and Desktop editions. There is no reason to migrate, in my opinion.

If you want to learn more about the terminal, you can certainly do that from the Desktop edition. :)

Agreed, except forcing yourself to rely entirely on the CLI is the best way to learn.

When I was learning Linux, I discovered Ctrl-Alt-F1 (*F7 to go back to desktop!*) and whenever I needed to do something like add a repo or manage files, I would go directly into that TTY and leave the task undone until I figured out how to do it. After that, I still feel more comfortable using a Terminal to do work; I always use cd, mv, mkdir, rm, ls, emacs... all that, as opposed to a GUI with Nautilus. Even on OS X I love using commands vs Finder.

Who knows. You might discover a new way to do things :)

Edit: Also, using a CLI for Apache/httpd will give more verbose output than a GUI. Might help troubleshoot errors more easily.

---

### Post by tristram60 on 2011-05-25
The only reason I would want to move to the Server edition is that it would use much less ram.  I only have 1gb on my machine and desktop edition uses 200mb or so just idling.  Do I need much ram to run a server?

---

### Post by kaldor on 2011-05-25
> **tristram60 said:**
> The only reason I would want to move to the Server edition is that it would use much less ram.  I only have 1gb on my machine and desktop edition uses 200mb or so just idling.  Do I need much ram to run a server?

I used to have Ubuntu Server Edition on an ancient PC with only 85 MB of RAM. Amazing that 10.04 would work, albeit slowly.

On the server edition, you can *always and easily add a Desktop Environment* if you decide you need it. There are also some very minimalistic environments that use low amounts of RAM that you can use. Since you seem interested enough, I'd say go for it; what's the worst that can happen? If you can't manage with the CLI, just install the regular GUI with *sudo apt-get install ubuntu-desktop* and you should be set.

---

### Post by tristram60 on 2011-05-25
If I installedl the desktop GUI would it essentially be just like the Desktop Edition?  Also, is it possible to dual-boot the server edition with windows?

---

### Post by kaldor on 2011-05-25
> **tristram60 said:**
> If I installedl the desktop GUI would it essentially be just like the Desktop Edition?  Also, is it possible to dual-boot the server edition with windows?

Yes, and yes.

However, the server edition has a different kernel with some optomisations for servers (someone can correct me if I am wrong here!).

Why would you dual boot a server with Windows, though?

---

### Post by tristram60 on 2011-05-25
Haha, I knew someone was going to ask that.  Well, I like windows because I use microsoft publisher to build my website, however, I could install publisher to a different computer.... Ok, well I think I am going to take the plunge into ubuntu server edition.  What is the most stable version out right now?  Should I download 11.04 or 10.04?

---

### Post by kaldor on 2011-05-25
Well, it wasn't an Anti-Windows comment I made :)

I'm just wondering why *any* server OS would be in a dual boot environment. Is it only temporary/certain times or something? Maybe the best idea would be to try to make a virtualized server under Windows; AKA, install VirtualBox and run Ubuntu Server on it, then configure the Virtual Ubuntu as a web server. It might be tricky and use a lot of RAM, but you'd never need to boot back into Windows or vice versa... it'd be always running inside Windows.

For servers, I always recommend an LTS release. In this case, 10.04. Ubuntu Server LTS releases get attention for 5 years vs 3 on the desktop. So, you should never need to worry about upgrading because it'll be 4 more years until the updates stop flowing in.

Edit: Oh, I assume you only use Windows because you have Publisher on it, and that you'd just boot into the server OS after editing your site? If that's the case, I'd also recommend using some Linux software and learning a little bit of code.. just so you don't need to dual boot.

---

### Post by tristram60 on 2011-05-25
Ok thanks I just misunderstood your question :)

Anyways, I have windows vista ultimate running on the other end and I have been meaning to get rid of it so this might be a good idea.  It can barely open a browser without it spiking to full ram usage :P

Thanks for taking your time to help me, I will mark this thread as SOLVED.

---

### Post by kaldor on 2011-05-25
Fair enough :)

As always, feel free to post for any more queries that come up and the people on these forums will be glad to help.

---

### Post by Ghosthaven on 2011-05-25
If your planning on running the server edition and then installing
the GUI on top of it, you should know there are a few bugs related
to setting things up like this.

The 100% confirmed one in 10.04/10.10 is a problem with gksu. It
doesn't function right after installing the ubuntu-desktop package.
Easy fix though, just run gksu-properties and change its auth mode
from su to sudo.

To prevent it from booting into the gui when you start the server,
you'll need to disable gdm (the user-chooser software that
automatically starts xwindows). This is also fairly simple, just
rename the /etc/init/gdm.conf file to something else.

All that being said, personally, I reinstalled from a
server+desktop install to just a normal desktop due to some "odd"
bugs that I couldn't figure out. I couldn't confirm for sure
that it was caused by this setup, or if it was a result of my
tinkering.

For me, I say the Desktop install can do everything the server
install can (to one-command install a LAMP install the tasksel
package, it can install a lot of other stuff as well. And
setting up Samba is MUCH easier with nautilus.) so why
bother with the server setup?

I also agree, setting up a VM is a good idea. But I'd suggest
going the other way around. Install virtualbox inside a ubuntu
desktop install, and run windows inside the VM for that one
program you use. You can also try WINE to get it running in
linux, but I haven't tinkered with WINE yet so I can't recommend
it.

---

