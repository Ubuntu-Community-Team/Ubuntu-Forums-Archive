---
title: "virtualbox, ran updates, now does not work  '/etc/init.d/vboxdrv setup'"
date: 2009-08-18
forum: Virtualisation
---

### Post by edwardtilbury on 2009-08-18
something about the Kernel driver...

Kernel driver not installed (rc=-1908)


It says I have to run   p, li { white-space: pre-wrap; }  
[COLOR=#0000FF]'/etc/init.d/vboxdrv setup' 
[/COLOR]

[COLOR=#0000FF][/COLOR]
[COLOR=#0000FF]as root, but I tried sudo-ing it from the terminal and it says command not found..[/COLOR]

[COLOR=#0000FF][/COLOR]
[COLOR=#0000FF]so I cannot run this script :([/COLOR]
[COLOR=#0000FF]
[/COLOR]

---

### Post by bodhi.zazen on 2009-08-18
Try running :

```
sudo /etc/init.d/vboxdrv setup
```

I assume that error is due to a typo on your part.

If not, check to see if it is installed.

```
ls /etc/init.d | grep vbox
```

---

### Post by edwardtilbury on 2009-08-18
I tried to cut and paste your sudo command, ALT F2, pasted it and clicked RUN, but it never prompted me for a password and no new windows popped up so I assume it didn't work, I tried Virtualbox again but I got the same error..

Here's my result from the ls command:
edward@edward-laptop:~$ ls /etc/init.d | grep vbox
vboxdrv
edward@edward-laptop:~$ 



so I guess it's there, it's just not executing for some reason.


Thanks for the quick reply.

I should mention that I'm on the x64 bit version of Ubuntu 9.04

---

### Post by bodhi.zazen on 2009-08-18
Open a terminal and run the command in a terminal.

This will show potential error messages.

---

### Post by Tigersmind on 2009-08-18
I just un-installed and reinstalled VBox, worked like a charm. Not a great option, but I am just running it to try out stuff.

---

### Post by edwardtilbury on 2009-08-19
Yep, uninstall , reinstall , reboot worked for me too.. I didn't have my icon back until I rebooted, but now I'm back on my virtual machine... 

I guess when the kernel updated , sun virtualbox had to recompile the drivers or some mumbo jumbo.. 

As far as I'm concerned it was fixed by magic, and now it works so I'm happy

---

### Post by gerkin on 2009-08-19
Yep the usual fix of: "sudo /etc/init.d/vboxdrv setup" run in terminal
does nothing here either (on Jaunty & virtualbox-3.0)

Had to reinstall with Synaptic as well

gerkin

---

