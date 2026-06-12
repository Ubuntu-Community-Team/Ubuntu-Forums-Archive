---
title: "can't upgrade, dpkg error 1, old failed install keeps trying to -configure"
date: 2011-05-26
forum: Server Platforms
---

### Post by cornflake000 on 2011-05-26
Greetings!

I have been running a jaunty server for years.  It is still running fine with a couple of problems I am finally trying to iron out.

I can't upgrade or update because there is an old failed installation that keeps trying to re-configure so apt will not get passed it; lock files are not a problem.  I can't upgrade using do-release-upgrade or by way of the CDs either server or alt.

Before I trash the root partition and start over, I want to see if there is a way to get rid of this old installation program that keeps on coming up and stopping the upgrades.  I don't think it matters but the failed program is snort.  I could not get rid of it the conventional way so I have also tried getting rid of all the snort and oink files manually including referenced in the rc. and init.d files.  I have no idea where apt keeps keying into this program to reinstall it.

apt-get upgrade says there are unmet dependencies for snort.  apt-get -f only tries to install those dependencies and fails.  When I try to install any other program I get the snort failing to install error.  I have tried dpkg configure to no avail.

If I do reinstall the OS to karmic then lynx, is there a way to do it keeping my home and var partitions intact?  The installation cds have a warning that all system files (etc, var, usr) at any mount point will be erased since I am choosing not to format root.  That is a little ambiguous. Do they mean any mount points that exist within the root directory that is being installed or do they mean the possibility of a different designated var partition being erased?

I could format root, then change the var and home partitions from the default to the correct partitions but that means reinstalling a whole lot of difficult programs....

If I could just get rid of that repeating failed installation (apt/dpkg) maybe it would save me a lot of headaches.

Sorry for this convoluted question.  I'm a bit convoluted myself ;)  The server is on another machine with no floppy or writable cdrom so I can't cut and paste the errors or logs.

any takers?  Thanks

---

### Post by Toz on 2011-05-26
Can you post the actual output of:```
sudo apt-get upgrade
```

and

```
sudo apt-get -f install
```

---

### Post by cornflake000 on 2011-05-27
Thanks for the reply...  I can't copy it directly as that server has no floppy or writable cdrom but I can try to remember the gist from memory...

it says:

building dependency tree
reading state information... done
you might want to run apt-get -f to fix these
unmet dependencies...
.. then it lists 3 long snort dependencies that end with "but is not installable"
E: unmet dependencies. try using -f

That's it.  If I run with -f, it runs the whole upgrade list like normal but when it begins to install it immediately goes into the snort install routine which fails and causes the upgrade to fail and I am back at the prompt.

adding edit:  after running apt-get install -f, it says: 1 to remove snort, 248 to upgrade Y/n.  I choose Y and it goes into the snort install routine asking which eth card to use.  I am forced to choose eth0, 1, 2, or 3 or none.  no matter which I choose, the install fails then I come back to E: sub process /usr/bin/dpkg returned error code (1) 

Then I am back to the prompt.

---

### Post by fdrake on 2011-05-27
> **cornflake000 said:**
> If I run with -f, it runs the whole upgrade list like normal but when it begins to install it immediately goes into the snort install routine which fails and causes the upgrade to fail and I am back at the prompt. 

what does the snort routine says, when it starts installing?

---

### Post by cornflake000 on 2011-05-27
i just stepped on you... I wrote your question's answer in the edit above...

thanks

the snort install routine asks which eth card to use. I am forced to choose eth0, 1, 2, or 3 or none. no matter which I choose, the install fails then I come back to E: sub process /usr/bin/dpkg returned error code (1)

Then I am back to the prompt.

---

### Post by fdrake on 2011-05-27
have u tried to remove snort and upgrade with 'dselect'?

---

### Post by cornflake000 on 2011-05-27
> **fdrake said:**
> have u tried to remove snort and upgrade with 'dselect'?

No I haven't.  I don't know what that is actually.  How's it work? Is that a command, flag, program?

---

### Post by cornflake000 on 2011-05-27
I just looked up dselect.  Sounds nice but I can't install anything on my server.  That's the problem... :cry:

---

### Post by fdrake on 2011-05-27
```
sudo dselect
```

you actually select and configure the package you want to install and remove... it doesn't really have options flags, you use ur arrows to select the packages and the dependencies... 

but other than that I can't think of another way to solve this dependencies issue.. sorry!

---

### Post by cornflake000 on 2011-05-27
After looking a little deeper, it seems the snort program is in a "half installed state".  "postinst abort-remove failed" is another error message when I run apt-get remove -f snort.

If anyone knows what this means or how I can purge this snort install program from trying to install every time I upgrade or install another program, I would appreciate it.

---

### Post by koenn on 2011-05-27
```
dpkg --remove snort
```


if that too complains about dependencies
```
dpkg --force-depends --remove snort
```

---

### Post by cornflake000 on 2011-05-27
Well... I fixed it myself...

This may be useful information for anyone else with a problem like this.

The problem was with the directory /var/lib/dpkg/info/. All I had to do was remove any instances referring to snort.  I just did "sudo rm snort*" and removed all the snort files.

Afterward, I did sudo apt-get remove -f snort then I updated and upgraded accordingly and all is well.

My server is now running 10.04 as planned!

---

### Post by cornflake000 on 2011-05-27
> **koenn said:**
> ```
dpkg --remove snort
```


if that too complains about dependencies
```
dpkg --force-depends --remove snort
```

koenn, thanks.  I didn't see your post on the second page till I replied.  I wonder if your method does the same thing?  Too late for me to find out.  Oh well.. :)

---

### Post by fdrake on 2011-05-28
thanks for sharing your solution! next time I will keep it in mind. :)

---

### Post by koenn on 2011-05-28
> **cornflake000 said:**
> koenn, thanks.  I didn't see your post on the second page till I replied.  I wonder if your method does the same thing?  Too late for me to find out.  Oh well.. :)

They don't do exactly the same thing, but the net result would be the same : you get something like "there is no snort whatsoever on this system", so the higher level tools such as apt stop obsessing over it and go about their business of installing and updating.

---

