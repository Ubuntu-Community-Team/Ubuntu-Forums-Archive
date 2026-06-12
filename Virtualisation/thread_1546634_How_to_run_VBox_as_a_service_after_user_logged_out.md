---
title: "How to run VBox as a service after user logged out?"
date: 2010-08-05
forum: Virtualisation
---

### Post by JKyleOKC on 2010-08-05
As part of a total system rebuild (forced by a probable rootkitting event) I've converted my last VMWare Server 2.0 VM over to VirtualBox, which I find to be far easier to work with -- except for one thing:

With VMWare Server, I could start a VM at boot time, running in the background like a service or daemon, and have it continually monitor my Email. I could access the VM via VNC from any station on my SOHO LAN, making it quite convenient.

Now that the Email VM has been moved to VirtualBox, I have to be logged onto the system in order to launch it, and since the "switch users" applet seems to have gone away in Lucid, that makes the whole machine unavailable for any other use.

Is there a way to run VBox in background, perhaps from another virtual terminal (such as Ctl-Alt-F6, for instance), without tying up the GUI login of that box for other users? If so, what apps are recommended on other machines to access the VM through its remote desktop interface?

Answers to these questions will make me a much happier camper -- and may be useful to others as well!

---

### Post by TheFu on 2010-08-05
vboxheadless - OSE version
VboxHeadless (guess at PEUL version)

If by "service" you mean daemon.  I have no idea whether this works on Windows Hosts. The way that Windows works with user accounts is a mystery to me.

---

### Post by JKyleOKC on 2010-08-05
The hosts are all Lucid; only the Email guest is WinXP, since I'm used to "The Bat!" as my email client.

Running the VM headless from tty6 leaves the GDM logon open for other uses, as I had hoped, and the rdesktop-vrdp program that comes in the VBox package does nicely for the remote workstations. The only remaining problem is that when I start the VM from tty6 without being logged in via GDM as well, then switching back to tty7 doesn't get the X server. Instead it shows some error messages and it doesn't seem to have any means of getting back to the GUI or to a CLI prompt. However the ctrl-alt-Fx still works to switch to yet another console, whence I can stop the VM via "VBoxManage controlvm WinXP-1 savestate" and then force a reboot to clean up the GDM interface.

If I'm logged into tty7 before launching the VM, I can then go back to tty7 and log out, and all works as expected.

---

### Post by JKyleOKC on 2010-08-07
Problem solved: I installed vboxtool and it's working exactly the way I wanted...

---

