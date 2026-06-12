---
title: "Minimal install vs normal install?"
date: 2015-07-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Higgins909 on 2015-07-20
I'm thinking about doing a install soon, as my old gaming computer looks like its going to become my new server.
(way faster cpu + 2gb more ram... not as many ide ports tho)

What is the difference?  I've heard it has way less ubuntu packages, but even then I'm not sure what those exactly are.

Does minimal still have firewall, top, ssh?  those are pretty much the only things that I use until I install samba, squid and maybe webmin.
Was also thinking about trying out virtual machines on it. one just for file server then one for proxy... just if anything ever happens as I tend to break things, I only lose one.
+ for better logging.

Thanks,
Higgins909

---

### Post by Bashing-om on 2015-07-20
Higgins909; hey, hey

A true minimal install is a "roll your own" install . In that install, all and I do mean all you have is the very minimum to boot the kernel and a wired internet connection. All else is at your discretion what is installed .

But let me tell you, when done; that system is lean mean and some kind of fast !

If you are to build a server, why not start as a server install ?

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-20
I do not know the difference between Minimal & server, but server includes tasksel. I just pulled up screen shot in synaptic. You could add to to minimal to choose groups of packages.

---

### Post by Higgins909 on 2015-07-20
Does anyone know why when I put it on my usb drive that I can't do any of the F keys to select minimal install?

---

### Post by Bucky Ball on 2015-07-20
A minimal contains no apps. It is the base kernel. You install the rest. See here. 

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

You don't install the mini from a regular desktop install (hit F key to select minimal install?). You download the mini.iso, create install media and boot from that. You need an ethernet connection to install.

After your first boot you will get a login cursor. Login. The rest is up to you. This is where you would 'sudo install ...' your server bits. As oldfred suggests, you can also use tasksel and take what defaults you are given. 

When it comes to the mini.iso, enjoy the learning curve. I only do mini installs and what Bashing-om says is correct. Sleek and fast with no bloat and only what I want/need. :)

---

### Post by Higgins909 on 2015-07-20
I've got a server iso and did it on a virtual machine real quick to test it out.  Its different when I try to boot off my usb with the same iso.  I get no F key options... one of them was what install mode to do. normal some manufactor and a virtual machine or a minimal... think those were the options.

---

### Post by Higgins909 on 2015-07-21
... Now whats the difference with minimum cd vs minimum install?
One annoying thing that I noticed is that the minimum cd downloads a TON TON TON of crap when installing... hate that so much and its not even that fast download (like 200KB vs my 3MB internet yes byte).

---

### Post by Bucky Ball on 2015-07-21
I have no idea what a minimum CD or a minimum install is so can't help with the differences. 

You download the mini.iso> you create live media from it> you boot from the live media> you install the mini.iso. That's it.

You install the minimal install from the mini.iso if that is what you're getting at. ALL you will end up with is the base Ubuntu kernel, no desktop environment, no file manager, no nothing else. :-k

If you are needing to ask these questions about the mini.iso I'm wondering if you might be better of installing a regular desktop. The mini is a learning curve and if you are heading that way you need to do some solid research regarding a minimal install. There is a LOT of information online regarding installing the minimal. I already gave you a couple of places to start in my last post. [Here's]("http://www.psychocats.net/ubuntu/minimal") a reminder. :)

Knowing what the differences are is a start I guess, and that's simple. The mini.iso gives you the base Ubuntu kernel, you do the rest. The desktop gives you the base Ubuntu kernel PLUS all the default software that comes with a Ubuntu desktop .iso already there. It can also be installed offline. The mini cannot be. 

If you install Lubuntu, you get the base kernel PLUS all the defaults that the Lubuntu team has decided to include with that flavour. Ad infinitum for other flavours. They've basically plopped whatever they want on top of the Ubuntu kernel, which is exactly what you'll be doing if you proceed with a minimal install, so jump on the curve. :)

I think that covers your original support request and as it is not related to a direct Ubuntu server issue,

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldfred on 2015-07-21
I have not installed mini, and only did a test install of server several years ago. But they were the older command line/text install, not gui installers. 
And they were not live systems, just installers.

There used to be a text installer to allow RAID or LVM in Desktop and that was the Alternative installer. But Ubuntu's last version of that was 12.04, as they are adding LVM and RAID support to standard live Desktop installer.

---

### Post by v3.xx on 2015-07-21
> I noticed is that the minimum cd downloads a TON TON TON of crap when installing
The mini.iso is as small as it gets, something like 30M.  It has to download everything from the internet, nothing to do with a 3x ton of crap.

---

### Post by anakai on 2015-07-21
> **Higgins909 said:**
> I'm thinking about doing a install soon, as my old gaming computer looks like its going to become my new server.
(way faster cpu + 2gb more ram... not as many ide ports tho)

What is the difference?  I've heard it has way less ubuntu packages, but even then I'm not sure what those exactly are.

Does minimal still have firewall, top, ssh?  those are pretty much the only things that I use until I install samba, squid and maybe webmin.
Was also thinking about trying out virtual machines on it. one just for file server then one for proxy... just if anything ever happens as I tend to break things, I only lose one.
+ for better logging.

Thanks,
Higgins909

Install it in a vm, just so you know the mini iso have no support for UEFI. I use the server to install my desktop on UEFI. Then I just use tasksel to remove all server apps and install my desktop of choice wich is KDE or Plasma with the --no-install-recommends.
As far as I remeber ucf,top and ssh is on the mini iso. Try it and experiment, I have a my plasma desktop using only 2,9 gig. 

If you ask why I don't use Kubuntu or any other it is because they install a lot of drivers,fonts and apps that I don't use. So i prefer the minimal and install what I need.

They both install a minimal base with no X and nothing. If you use wireless it can be a pain to setup, so if I were you I would use a cable just to get the desktop setup.

---

