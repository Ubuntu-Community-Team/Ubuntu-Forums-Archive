---
title: "Best host for VirtualBox"
date: 2013-09-05
forum: Virtualisation
---

### Post by Dan_Joyce on 2013-09-05
I'd like to set up a Windows VM in VirtualBox and would like opinions as to what is the best Linux distro as far as lowest system resources while still meeting my requirements. The VM will be the only thing the users interact with. I'm only running this as a VM to have snapshots to quickly get back to previous states—this runs some very finicky software that constantly breaks itself, so clicking a few times to be back to two days ago is huge.


[LIST]
[*]Must be a stable or LTS distro that will just work
[*]Must be able to easily get into the VM. The users will expect to turn on the machine and have it boot into Windows or, at most, to have to type one command or click a couple times to be into Windows.
[*]Must run Windows in a full-screen mode. Ideally it would be very difficult to switch to the Linux environment.
[*]Must be reliable when it comes to hardware sharing. I'm thinking USB and Ethernet, mostly (see next)
[*]The Windows VM should always have access to the LAN and Internet and if I need to use NAT it must pass along TeamViewer requests to Windows.
[/LIST]

In short, this should be dead simple for a user who just needs to get in, do their work, and get out.

So, what distro do you all recommend? I'm not savvy enough yet to know if I could accomplish this by just installing a CLI-only distro, if I'd need a window manager, or if I'd need a full desktop environment. If the latter, Lubuntu LTS or maybe Debian Stable seem logical. All advice appreciated.

---

### Post by TheFu on 2013-09-05
Why allow local access at all?
Put Windows into a VM and only allow RDP access. That solves most of your external security issues. You can use snapshots to put the entire OS back to any point you like.

BTW, if you don't expect to allow local physical access, then I wouldn't use virtualbox at all - I'd use kvm, libvirt and virt-manager.

I don't know of any way to prevent a knowledgeable end-user from breaking out of a full screen virtualbox VM.  If all this box does is run Windows, I'm sorta at a loss for the virtualbox part. Why not run Windows directly on the physical hardware?

For the most stable VM, you want debian server - without a GUI. GUIs add more complex software, X/Windows, and that leads to instability. If you need slightly newer packages, but not unstable versions, Ubuntu Server 12.04.3 is what I'd run - actually, it is what I do run. See my signature.  Servers don't have any GUIs, so people will not walk up and use a mouse to access any client OS. All client OS access must be through the network.  For Windows, RDP is the normal way, provided this access is NOT over the internet.

Update - if you want "dead simple" hardware sharing, then you **DO NOT WANT** any virtualization.

---

### Post by Kevin_Arnold on 2013-09-05
Exactly, I'd just set up a a machine that either auto-starts and RDP connection or has it on the desktop so they can just double click it. No reason to have them on that physical machine.

---

### Post by houstonbofh on 2013-09-05
Here is some food for thought.  These are striped down Ubuntu installs that just run one app on boot, the RDP client.  It could just as easily be virtualbox or a firefox, or chrome.

rdp (I like this one)
[http://www.linuxjournal.com/content/using-ubuntu-thin-client](http://www.linuxjournal.com/content/using-ubuntu-thin-client)

Firefox to Citrix
[https://rin.no/2013/04/replace-windows-xp-with-a-minimal-ubuntu-based-thin-client/](https://rin.no/2013/04/replace-windows-xp-with-a-minimal-ubuntu-based-thin-client/)

ltsp and pxe boot
[http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients](http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients)

---

### Post by Dan_Joyce on 2013-09-06
Sorry I didn't explain this well. This is a workstation that has to be accessed locally. It's a print station with custom software and the printer right beside it, whereas the users' machines are far from it. 

Right now we do have Windows on there, but this custom software breaks rather often and the vendor is, well, working on it. And has been for a long time. However, each time it breaks we could just roll back to a day or two previous using a snapshot. I can easily train one or two of the users to take and use snapshots. These users won't be a problem as far as host vs. vm and getting into/out of the VM. The other users are a different story, thus the trying to protect them from seeing the host OS bit. 

The other option is to create local, fast incremental backups of Windows, but I have yet to see any such software that makes it as easy as snapshots to create a restore point now before updating the software then another just after the update, then roll back-and-forth as needed for testing and comparison. This may sound complicated, but the client knows this software well and being able to flip back-and-forth is beneficial. 

Plus, the added benefit of being able to just move a virtual box to another machine if they need a second client running the software is a nice addition, albeit requiring some re-working of network interfaces, etc.

Does that clear some of it up? The short version is: remote can't work here and I don't know of Windows backup/restore software that's as easy to jump around to restore points as snapshots.

I may have an answer to the host question though. I planned to use Lubuntu for resource footprint but they don't offer an LTS edition. Xubuntu only has a 3-year LTS version. So, I think I'll end up with straight Ubuntu 12.04 LTS or maybe Debian's latest stable. Leaning toward Ubuntu now.

---

### Post by Dan_Joyce on 2013-09-06
Unless Acronis Workstation can do what I want. I somehow missed this offering from Acronis. I'll read a bit on it. Maybe it's the silver bullet.

---

### Post by SeijiSensei on 2013-09-06
Your best bet might be software that automatically restores a known good image upon reboot.  I browsed around a bit and came up with this one: [http://www.raymond.cc/blog/reboot-windows-and-automatically-restore-to-its-original-state/](http://www.raymond.cc/blog/reboot-windows-and-automatically-restore-to-its-original-state/)

Here's a link to the product's website: [http://www.returnilvirtualsystem.com/](http://www.returnilvirtualsystem.com/)

---

### Post by TheFu on 2013-09-06
Any ubuntu 12.04 install is "supported" for 5 yrs.  Just remove all the extra cruft after the install, then add back the minimal stuff you want.
Or start with the "server" and add the GUI you want.
**sudo apt-get install lxde**

Allowing physical access to any server by joe-user is bad. Just sayin'.  Sometimes telling a client "no, that is a bad idea" **is** the right answer.

---

### Post by Dan_Joyce on 2013-09-06
> **SeijiSensei said:**
> Your best bet might be software that automatically restores a known good image upon reboot.  I browsed around a bit and came up with this one: [http://www.raymond.cc/blog/reboot-windows-and-automatically-restore-to-its-original-state/](http://www.raymond.cc/blog/reboot-windows-and-automatically-restore-to-its-original-state/)

Here's a link to the product's website: [http://www.returnilvirtualsystem.com/](http://www.returnilvirtualsystem.com/)

Hmm. This is a little like I'm looking for, but it's simpler than that. They have a special printer with special software to interact with a database and print templates. Things are great until the vendor updates the software or until it breaks on its own. That may be a week or 6 months. Between updates and breaks, we're just fine and the machine should be updated as any Windows client. But, just before an update to the software we need to take a snapshot and after we think it works, another. Then we can roll back to the last good snapshot if we discover trouble.

---

### Post by Dan_Joyce on 2013-09-06
> **TheFu said:**
> Any ubuntu 12.04 install is "supported" for 5 yrs.  Just remove all the extra cruft after the install, then add back the minimal stuff you want.
Or start with the "server" and add the GUI you want.
**sudo apt-get install lxde**

Allowing physical access to any server by joe-user is bad. Just sayin'.  Sometimes telling a client "no, that is a bad idea" **is** the right answer.

I think I see now why the disconnect: This has nothing to do with servers. This is a workstation. I don't know how the discussion turned to server, but I was only asking about desktop distros. 

As for your suggestion, yes, adding a desktop environment to a server distro or stripping back a desktop are the options I'm chasing if Acronis Workstation doesn't quite cut it.

---

### Post by houstonbofh on 2013-09-06
If you follow my first link...  [http://www.linuxjournal.com/content/using-ubuntu-thin-client](http://www.linuxjournal.com/content/using-ubuntu-thin-client)  And install KVM locally with the printer port passthrough (I assume that is why the things in not on a VM server in the computer room) and make it autoboot...  Now for the standard user, make it autologin, and have it RDP to the KVM guest OS.

All on one box, remotely manageable, and transparent to the user.

---

