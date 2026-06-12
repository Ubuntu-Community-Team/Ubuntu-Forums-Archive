---
title: "Saving &amp; Restoring Customizations"
date: 2007-05-03
forum: The Cafe
---

### Post by mlanza on 2007-05-03
Hello Ubuntu Community,

I am relatively new to Linux and I have to thank the Ubuntu team for making it so accessible!

I am wondering what techniques/tools are out there for saving customizations to Ubuntu to be restored later.  I am primarily concerned with all the software that I elect to install from the Synaptic Package Manager.  Is there some way for me to save an XML file (or something) that tracks my customizations so that later when I make a clean install of Ubuntu I can easily have my preferred software reapplied to the base image?

Thanks,
Mario T. Lanza

---

### Post by matthew on 2007-05-03
If you install using a separate hard drive partition for your /home directory, all these things will be saved. You can do a fresh OS installation on the main partition and tell the installer to leave /home alone and you will be set--all the config files you are thinking of are stored in /home as hidden files or in hidden directories.

---

### Post by mlanza on 2007-05-03
Interesting and nice to know. Thanks.

---

### Post by papercuts on 2007-05-03
> **matthew said:**
> If you install using a separate hard drive partition for your /home directory, all these things will be saved. You can do a fresh OS installation on the main partition and tell the installer to leave /home alone and you will be set--all the config files you are thinking of are stored in /home as hidden files or in hidden directories.

I don't doubt that this is true (since it's written by an admin), but heh? how is that?  

Are the programs you have really saved there? And even if they are, when you reinstall Linux does it say, "no you should have these programs installed, ". Also does it work when you have the config files but install the apps later? Aren't there conflicts and residue?  

I am asking because it would be awesome if it were that simple. Never tried it myself though so I don't know. What exactly does the home folder keep, which settings?

---

### Post by srt4play on 2007-05-03
> **matthew said:**
> If you install using a separate hard drive partition for your /home directory, all these things will be saved. You can do a fresh OS installation on the main partition and tell the installer to leave /home alone and you will be set--all the config files you are thinking of are stored in /home as hidden files or in hidden directories.

The OP is primarily concerned with automating the installation of extra software on a fresh install. Your suggestion is more or less a good one, but a little off-topic and already has confused another poster. 

To the OP - the best way I've found is on a fresh install, mark everything you want to install and then file --> save markings.  Then on the next fresh install you can file --> read markings instead of manually checking them all.

---

### Post by Wolki on 2007-05-03
```
dpkg --get-selections
```

will output a list with all your decisions regarding package installation/deinstallation. Save it to a file like this:

```
dpkg --get-selections > somefile
```

Then you can later resore the state with 

```

## clear default selections
sudo dpkg --clear-selections
## apply saved selections
sudo dpkg --set-selections < somefile

```

Note that occasionally package names and dependencies will need to change between different versions of ubuntu, so I would not apply selections from one version to another.

---

### Post by matthew on 2007-05-03
> **srt4play said:**
> The OP is primarily concerned with automating the installation of extra software on a fresh install. Your suggestion is more or less a good one, but a little off-topic and already has confused another poster. 
oops. I needed to read the post a little better before responding. Sorry about that.

Wolki's post has a good suggestion.

---

