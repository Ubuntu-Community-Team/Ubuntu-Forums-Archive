---
title: "Wine 1.1.17 release broken - no wine_pthreads exists?"
date: 2009-03-14
forum: Wine
---

### Post by aoanla on 2009-03-14
So, I just upgraded to Wine 1.1.17 via the budgetdedicated repository, as normal. I'm using 64bit Intrepid.

On trying to start steam in this release, I get:

```
$ wine steam.exe 
/usr/lib32/../bin/wine-pthread: could not open
```

And, indeed:
```
$ ls /usr/lib32/../bin/wine-pthread
ls: cannot access /usr/lib32/../bin/wine-pthread: No such file or directory
```

I notice that the list of changes in 1.1.17 includes "Obsolete LinuxThreads support has been removed", which seems like it may be related to this issue.

Does anyone else have this problem? 

(Obviously, I'm going to downgrade to 1.1.16 for the time being...)


edited to add: it appears that there's a copy of wine-pthread in /usr/local/bin/ which suggests to me that this may be a packaging issue, rather than a problem with Wine itself? Trying to run wine-pthread directly from that location doesn't work; astonishingly, it generates the same error about not being able to find the /usr/bin/ copy of wine-pthread and then dies, leaving child processes hanging.

---

### Post by aoanla on 2009-03-14
Fixed, by uninstalling wine, and reinstalling it.

Very very odd.

---

### Post by nicebloke on 2009-03-15
I had the same error :(

nicebloke@apc:~$ uname -a
Linux apc 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

Removal and re-installation didn't fix it for me.

Any other ideas?

---

### Post by poisonkiller on 2009-03-15
Same error here.
I tried reinstalling/removing, but nothing worked. Wine 1.1.16 works fine, though.

---

### Post by killpotts on 2009-03-16
I upgraded with no problems to anything.

It is a mystery.:-k

---

### Post by YokoZar on 2009-03-16
Packages, as a rule, don't ever put anything into /usr/local -- Did you at some point compile/install Wine by hand (eg with make install)?

---

### Post by poisonkiller on 2009-03-16
Yes, I did, but that was like 2 months ago. Can it be the reason? If yes, then how can I get rid of it? :D

---

### Post by aoanla on 2009-03-16
Delete the wine programs in /usr/local/bin/

(
rm /usr/local/bin/wine*
)

and then uninstall and reinstall wine.

I suspect that what's happening is that the removal of one of the two threading implementations in 1.1.17 results in the only "working" copy of wine-kthread being the one you compiled, hence madness ensues between that copy and the "real" copy of wine you installed (in /usr/bin ).

---

### Post by poisonkiller on 2009-03-16
Thank you! It worked perfectly, now my Wine 1.1.17 works just fine. :)

---

### Post by nicebloke on 2009-03-16
Sweet - that appears to have fixed it for me as well.

I'd also manually installed wine a while ago and forgotten about it.

---

### Post by kxmas on 2009-03-17
Despite all these so-called successes, wine-pthread does not exist in the wine 1.1.17 .deb package.

Try for yourself, [FONT="DejaVu Sans Mono"]dpkg-deb -c wine_1.1.17~winehq0~ubuntu~8.10-0ubuntu1_i386.deb | grep pthread[/FONT]

running [FONT="DejaVu Sans Mono"]dpkg-deb -c wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb | grep pthread[/FONT] produces [FONT="DejaVu Sans Mono"]-rwxr-xr-x root/root     26659 2009-02-28 00:38 ./usr/bin/wine-pthread [/FONT]

I'm curious what [FONT="Courier New"]wine-pthread --version[/FONT] would show.

and yes, I checked both the i386 and amd64 packages.  I'm not sure what to make of this.  Am I misreading this thread?

---

### Post by nicebloke on 2009-03-17
$ wine-pthread --version
The program 'wine-pthread' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: wine-pthread: command not found

---

### Post by kxmas on 2009-03-17
> **nicebloke said:**
> $ wine-pthread --version
The program 'wine-pthread' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: wine-pthread: command not found

That's what I would expect would happen :D

---

### Post by enyone on 2009-03-31
fixed.
```
sudo ln -s /usr/local/bin/wine-pthread /usr/bin/wine-pthread
```

---

