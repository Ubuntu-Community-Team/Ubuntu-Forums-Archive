---
title: "Running Windows progs via VMWare + 2X Publishing?"
date: 2008-08-24
forum: Virtualisation
---

### Post by Doc Hoss on 2008-08-24
I found a guide that looks pretty interesting, and so I tried it out and got almost all the way through it...all the way to the last step, actually.  Check it out...

[Running Windows as VM on Linux]("http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html")

Admittedly, I could just run the programs inside the VM, and they run fine like that.  But I was wanting to follow this guide and make conversion to Linux easy for my girlfriend who isn't super computer-literate.  

When I get to the last step in the guide, 

```
--This line is the example from the guide-- ./appserverclient –s ip address of 2X server  –u username –p password –a name of application as defined in the publishing setup

XXX@XXX-desktop:~/Desktop/2x/opt/2X/applicationserverclient/bin$ ./appserverclient -s 172.16.20.128 -u XXX -p xxxxxx -a EXCEL -o 2 
Socket connection timeout reached

XXX@XXX-desktop:~/Desktop/2x/opt/2X/applicationserverclient/bin$ ./appserverclient -s 172.16.20.128:902 -u XXX -p xxxxxx -a EXCEL -o 2 
Socket connection timeout reached

```

The 3 code snippets are: 1) the example from the guide, 2) trying to run EXCEL via the 2x application with the default ports, 3) trying with port 902, as the VMWare setup told me it's connected to the host-only network on port 902.  I've also tried this with the ip address of the virtual XP machine, same results.

It seems I simply can't get the two OS's to talk to one another.  They can ping each other (WindowsXP in VM, and Linux host) and can both connect to the internet.  I feel I'm just missing something in the setup options.  

Any ideas?  Has anyone else used this combination of programs?  If not, can anyone recommend a similar solution?

---

### Post by Doc Hoss on 2008-08-27
Anyone have a clue?  This seems like a good solution to running Windows programs almost-kinda-natively in Linux...if I can get the darn thing working!

---

### Post by tastybrains on 2008-08-27
i was doing this a few years ago and it worked great. i'll give it a shot again when i get back from vaca next week. from what i remember the biggest problem was making sure all the necessary ports were reachable

---

### Post by Doc Hoss on 2008-10-07
Any luck, tastybrains?

---

### Post by edmondt on 2008-10-07
Make sure the application name you have is correct and case sensitive. When I first tried it, it automatically set my application name as excel.exe and I had a tough time figuring out what the heck was wrong...

I save mine as a script:

```
#! /bin/bash
#open treodesktop...

/opt/2X/applicationserverclient/bin/./appserverclient -s 10.0.1.2 -u "username" -p "password" -a treodesktop &

exit
```

> **Doc Hoss said:**
> I found a guide that looks pretty interesting, and so I tried it out and got almost all the way through it...all the way to the last step, actually.  Check it out...

[Running Windows as VM on Linux]("http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html")

Admittedly, I could just run the programs inside the VM, and they run fine like that.  But I was wanting to follow this guide and make conversion to Linux easy for my girlfriend who isn't super computer-literate.  

When I get to the last step in the guide, 

```
--This line is the example from the guide-- ./appserverclient &#8211;s ip address of 2X server  &#8211;u username &#8211;p password &#8211;a name of application as defined in the publishing setup

XXX@XXX-desktop:~/Desktop/2x/opt/2X/applicationserverclient/bin$ ./appserverclient -s 172.16.20.128 -u XXX -p xxxxxx -a EXCEL -o 2 
Socket connection timeout reached

XXX@XXX-desktop:~/Desktop/2x/opt/2X/applicationserverclient/bin$ ./appserverclient -s 172.16.20.128:902 -u XXX -p xxxxxx -a EXCEL -o 2 
Socket connection timeout reached

```

The 3 code snippets are: 1) the example from the guide, 2) trying to run EXCEL via the 2x application with the default ports, 3) trying with port 902, as the VMWare setup told me it's connected to the host-only network on port 902.  I've also tried this with the ip address of the virtual XP machine, same results.

It seems I simply can't get the two OS's to talk to one another.  They can ping each other (WindowsXP in VM, and Linux host) and can both connect to the internet.  I feel I'm just missing something in the setup options.  

Any ideas?  Has anyone else used this combination of programs?  If not, can anyone recommend a similar solution?

---

