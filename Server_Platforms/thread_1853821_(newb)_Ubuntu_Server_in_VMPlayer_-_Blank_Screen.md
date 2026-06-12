---
title: "(newb) Ubuntu Server in VMPlayer - Blank Screen"
date: 2011-10-03
forum: Server Platforms
---

### Post by DJS2 on 2011-10-03
Hello all, I am new to this and am not sure what's going wrong.  I downloaded "ubuntu-11.04-server-i386" and opened it as a new VM in VMPlayer.  It seems to install fine and I have full control over the terminal after it first installs.  But when I go to Virtual Machine > Power > Power off, and then try to start up the server again (play virtual machine), I get a completely blank screen with no terminal.  It doesn't seem to respond at all.

Sorry if this is a dumb question, but thanks for the help.

---

### Post by DJS2 on 2011-10-03
Is there a better place to ask this question? Not sure if this is the right place.

---

### Post by Dangertux on 2011-10-03
Have you tried it a second time or only the first? Sometimes VMWare player is kinda crummy and randomly fries your image under Ubuntu 11.04.

You might try reinstalling. Also did you use the easy install or the "install operating system myself" option? I find the install myself tends to be less glitchy. As well as breaking it up into multiple files.

Hope that helps.

---

### Post by DJS2 on 2011-10-03
> **Dangertux said:**
> Have you tried it a second time or only the first? Sometimes VMWare player is kinda crummy and randomly fries your image under Ubuntu 11.04.

You might try reinstalling. Also did you use the easy install or the "install operating system myself" option? I find the install myself tends to be less glitchy. As well as breaking it up into multiple files.

Hope that helps.

I am using easy install.  I have tried installing 3+ times and tried redownloading the iso but same thing happens.  It's weird because it works perfect after install but after i power off my VMplayer and load the VM I just cant get the terminal to show up again.

Also, I never saw an "install yourself" option.  When I create a new VM it takes in basic information like name, password, etc. and then starts up easy installer.

---

### Post by pjd99 on 2011-10-03
I can confirm that this problem exists on 11.04 x86_64, VMPlayer 3.1.4 build-385536. Using 11.04 Server (x86) as the guest OS.

vcpu-0| serial0: Overrun

If you look in the VMPlayer log file you will see this line repeated. A suggestion on the VMWare forums is to set
```

serial0.present = "FALSE"

```in your .vmx file, but doesn't help in my case -- in the sense that the same error appears in the log, even though it should be disabled.

EDIT: Link to VMWare forums: [http://communities.vmware.com/thread/324430?tstart=45](http://communities.vmware.com/thread/324430?tstart=45)

---

### Post by pjd99 on 2011-10-03
Currently installing without using the easy install method. Will let you know how it goes.

Got rid of the serial0 overrun problem by disabling the ports in the BIOS (spam F2 when launching the VM) with serial0.present = "FALSE" in the .vmx file. Was then getting VGA problems. I'd hacked the VM to pieces by this stage, so I've deleted it and started again.

---

### Post by DJS2 on 2011-10-03
> **pjd99 said:**
> I can confirm that this problem exists on 11.04 x86_64, VMPlayer 3.1.4 build-385536. Using 11.04 Server (x86) as the guest OS.

vcpu-0| serial0: Overrun

If you look in the VMPlayer log file you will see this line repeated. A suggestion on the VMWare forums is to set
```

serial0.present = "FALSE"

```in your .vmx file, but doesn't help in my case -- in the sense that the same error appears in the log, even though it should be disabled.

EDIT: Link to VMWare forums: [http://communities.vmware.com/thread/324430?tstart=45](http://communities.vmware.com/thread/324430?tstart=45)

Thanks for your post!  So I edited my vmx file, removed the VM from the VMPlayer library, readded it, started it up, and still get a blank screen which receives no input.

Would an earlier version of vm player work or I could even try virtualbox?

edit - please keep me updated. also if you can think of anything that you would like me to try im willing. thanks

---

### Post by pjd99 on 2011-10-04
Working now, just have to install the slow and painful way.

Instead of easy install, select "I will install an Operating System later."

Once the blank drive is created, edit the VM's settings and change the DVD/CD (IDE) hardware to use the .iso image of Natty Server 32 bit. Then just run through the server install as per normal.

EDIT: Before installing, I disabled the serial ports in the BIOS. Don't know if this will affect installation.

---

### Post by DJS2 on 2011-10-04
> **pjd99 said:**
> Working now, just have to install the slow and painful way.

Instead of easy install, select "I will install an Operating System later."

Once the blank drive is created, edit the VM's settings and change the DVD/CD (IDE) hardware to use the .iso image of Natty Server 32 bit. Then just run through the server install as per normal.

EDIT: Before installing, I disabled the serial ports in the BIOS. Don't know if this will affect installation.

Amazing! Followed your instructions and I have successfully powered off my VM and powered it back on and everything is working still.

I did NOT disable any serial ports just for future reference if anyone else sees this thread and has the same problem.  Thanks very much for your help pjd99, I'm glad you got yours working as well.

---

