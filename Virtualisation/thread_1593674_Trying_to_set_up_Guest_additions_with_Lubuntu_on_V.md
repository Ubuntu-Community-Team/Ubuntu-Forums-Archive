---
title: "Trying to set up Guest additions with Lubuntu on VBox"
date: 2010-10-11
forum: Virtualisation
---

### Post by migs73 on 2010-10-11
As it says in the title, I am trying to get the Vbox Guest Additions on Lubuntu. When I do the first stage of the instructions and try to install the DKMS package, the terminal returns that the package couldn't be found. Any ideas?

---

### Post by emoguitarist06 on 2010-10-11
May sound like a dumb questions... but you're running Lubuntu as your Guest OS? What are you running as your Host? Ubuntu? Windows?

---

### Post by bodhi.zazen on 2010-10-11
> **migs73 said:**
> As it says in the title, I am trying to get the Vbox Guest Additions on Lubuntu. When I do the first stage of the instructions and try to install the DKMS package, the terminal returns that the package couldn't be found. Any ideas?

I posted how I installed on VBox here :

[Known Maverick Meerkat issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1588889")

---

### Post by migs73 on 2010-10-12
Thanks guys, still no joy though.
I am using the PUEL non free(?) version from the website, for 10.10 (which is my host).
Bodhi, tried the x11 code on the other thread, on my host and it ran ok, and said as part of its output that DKMS was installed.
Started the VB and tried to install DKMS there but still says it couldn't be found.
Was I right to run it on the host?

Anyway found the problem was that I had not enabled all the repositiories (doh!)in Lubuntu. So DKMS now installed.

BUT (there is always a but!) now on the guest, when I change directory to the guest additions and try to do this;
```
sh ./VBoxLinuxAdditions-x86.run
```
 I get;
```
sh: Can't open ./VboxLinuxAdditions-x86.run
```
Also tried the command with sudo but same response.
The image is mounted and I can browse to the file using the file manager (but also can't open it, double click and nothing happens).
I only put Lubuntu on to give it a look, as I might put it on an old desktop. So far it looks really buggy in boot (lots of scripts running up and the splash screen looks hellish), so if this is looking like a lot of hassle I'll just bin it and try something else, Puppy maybe.

Thanks

Mike

---

### Post by s.fox on 2010-10-12
Thread moved to  [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") as per op request.

---

### Post by bodhi.zazen on 2010-10-12
I do not know why you are getting that error, but you do not need to call the script with sh.

just ./VBoxLinuxAdditions-x86.run

```
[FONT=monospace]./[/FONT]VBoxLinuxAdditions-x86.run
```

---

### Post by migs73 on 2010-10-18
Sorry to have let this lie for a while, had problems on my host OS which took over for a bit.
Anyway, looks like I am sorted, downloaded the latest Guest Additions iso as the one I had was a bit out of date (thought it would update with Vbox??) and tried again.
I have no idea why it would not run the older version, as it was definitely working with my windows guest.
Never mind, computers eh!

Thanks for all your help.

---

