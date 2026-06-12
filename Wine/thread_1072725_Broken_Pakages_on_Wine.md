---
title: "Broken Pakages on Wine"
date: 2009-02-17
forum: Wine
---

### Post by Da Mangaka on 2009-02-17
Hello, I'm trying to install Wine once again after me killing the repository and having to reinstall Ubuntu again.
So I'm following the steps on the page but all of a sudden, one error happens:
```

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
```


I have checked even in the repository if I have the libasound2 installed and I do have it. The question is that what's going on? Do I need to upgrade it or what?
That's just it for now, help would be really appreciated: I need to install Dreamweaver CS3 to work for a project.

:KS Thanks:KS


------

I have the same problem. For now, I followed your instructions david, and it was ok until I installed the libaudio. Just a heads up for those who are copy/pasting. The correct code is :

```
sudo apt-get install binfmt-support libaudio2 
```

Just missing one dash only.

But that's now really what it matters: after I put the command, the following comes up:

```
telnor@Telnor-Ubuntu:~$ sudo apt-get install binfmt-support libaudio2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libaudio2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libpurple0 libotr2 pidgin-data libhesiod0 libzephyr3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  binfmt-support
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.4kB of archives.
After this operation, 152kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com hardy/universe binfmt-support 1.2.10 [21.4kB]
Fetched 21.4kB in 1s (15.5kB/s)        
Selecting previously deselected package binfmt-support.
(Reading database ... 118007 files and directories currently installed.)
Unpacking binfmt-support (from .../binfmt-support_1.2.10_all.deb) ...
Setting up binfmt-support (1.2.10) ...
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
```

Not bad eh? It installed! 

Now I just put...

```
 sudo apt-get install wine
```

Sadly, the same thing happens again:

```
The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
```

So. . . what do I do? Do I have 1.0.17 and need to go down to 1.0.15? or how do I fix this? = w=;

---

### Post by hikaricore on 2009-02-17
It looks like you're installing a WINE package that is not for your release of Ubuntu.

```

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> **1.0.17**) but **1.0.15**-3ubuntu4 is to be installed
```

For example if you try to install the Intrepid version of WINE on Hardy you would get such an error.
Make sure you're installing the proper package.

---

### Post by Da Mangaka on 2009-02-17
Well, I did first try to install it with the Hardy Version
Then, just to see if I was wrong went with the Intrepid
Neither of the two got different results.
Perhaps I have to remove the packages and start all over?
And how do I do that?

Oh, and also: I tried installing via Synaptic and it throws the same error...

---

### Post by hikaricore on 2009-02-17
Please check which version the WINE repo you have in your sources.

I suspect you added the Intrepid repo instead of the hardy repo..

---

### Post by Da Mangaka on 2009-02-17
Ho snaps! They are for Intrepid after all!
How do I eliminate those packages from the Synaptic?

---

### Post by Da Mangaka on 2009-02-17
Ok, I have seen an option in the synaptic that says 'force version', that way I could select the one for Hardy
I'm installing it right now ' w '

---

### Post by hikaricore on 2009-02-17
You just need to edit your sources in synaptic to disable the intrepid version.

^_^

---

### Post by Da Mangaka on 2009-02-17
Done it!
Thanks!

---

