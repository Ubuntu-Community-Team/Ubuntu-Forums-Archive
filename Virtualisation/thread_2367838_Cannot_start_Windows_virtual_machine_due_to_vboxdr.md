---
title: "Cannot start Windows virtual machine due to vboxdrv related error"
date: 2017-08-03
forum: Virtualisation
---

### Post by AbleTassie on 2017-08-03
I have been able to run a virtual Windows XP machine for months using Virtualbox. But this stopped about 2 weeks ago. It looks like a pretty straightforward fix, but I don't want to mess it up. A screenshot of the error box is attached as well as an error message I copied to the clipboard below.

I had a problem similar to this a couple of years ago, which I posted to this forum,  but I was not able to solve it. So I think I ended up uninstalling Virtualbox and then reinstalling it as well as having to do all of the work required in allowing the virtual machine to communicate with the host OS, Lubuntu and reinstalling all the applications in the Virtual Machine-- a real pain.

 I am presently using VirtualBox Graphical User Interface Version 5.0.40_Ubuntu r115130

  

Can anybody give me exact instructions as to what to do?

Thank you,

A.

**Error message copies to clipboard:**

Failed to open a session for the virtual machine Able1.

The virtual machine 'Able1' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}


[ATTACH=CONFIG]276249[/ATTACH]

---

### Post by &amp;KyT$0P# on 2017-08-03
Try uninstalling VirtualBox and then reinstalling it.  This shouldn't touch your VM or VirtualBox config, you shouldn't have to set that up from scratch again.

If that doesn't fix it, you may need to
```
sudo apt-get install dkms
```
... and then retry the uninstall/reinstall.

---

### Post by Bucky Ball on 2017-08-04
You could make sure your machine's up to date:

```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
```

Then try following the instructions from the error message in the pic you posted:

```
sudo apt install dkms
sudo apt install virtualbox-dkms
sudo modprobe vboxdrv
```

Launch VBox and see what happens. ;)

---

### Post by AbleTassie on 2017-08-04
> **Bucky Ball said:**
> You could make sure your machine's up to date:

```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
```

Then try following the instructions from the error message in the pic you posted:

```
sudo apt install dkms
sudo apt install virtualbox-dkms
sudo modprobe vboxdrv
```

Launch VBox and see what happens. ;)

Hi BuckyBall,

I ran the commands you suggested above, and that took care of the problem, THANKS . Interestingly, when I got to the last command "sudo modprobe vboxdrv" the command seemed not to do anything. But as I said, the problem has been solved. [SOLVED]!

[B]Thanks also to you halogen.

[/B]A.

---

### Post by Bucky Ball on 2017-08-05
All good, good news and thanks for marking as solved to help others. Enjoy. ;)

---

