---
title: "DOSEMU install problem dapper"
date: 2007-03-23
forum: Repositories &amp; Backports
---

### Post by monkeyfork on 2007-03-23
First post ever... sorry for inevitable infractions of protocol

I'm trying to install dosemu on dapper.  I see there's been activity with some sort of Xfont problem, then a dosemu recompile (??), then a proposed fix in a proposed 
repository (which I'm not familiar with).  Then finally it appears that the bug handler makes something available in dapper upgrades.  Most of this is uncharted territory for me so I don't really understand what's going on.

I _think_ I understand the synaptic and apt-get process of loading new packages but neither seem to be able to load dosemu.   I believe I've got the proper repositories enabled and If I use synaptic, dosemu isn't shown.  dosemu-freedos is shown but I think that's only the freedos image (to be used with dosemu).

If I use sudo apt-get install dosemu, I get;


```
Reading package lists... Done
Building dependency tree... Done
Package dosemu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dosemu-freedos
E: Package dosemu has no installation candidate

```

I don't believe that dosemu-freedos is intended to replace dosemu.

Any help will be greatly appreciated.

---

### Post by klytu on 2007-03-23
> **monkeyfork said:**
> First post ever... sorry for inevitable infractions of protocol

I'm trying to install dosemu on dapper.  I see there's been activity with some sort of Xfont problem, then a dosemu recompile (??), then a proposed fix in a proposed 
repository (which I'm not familiar with).  Then finally it appears that the bug handler makes something available in dapper upgrades.  Most of this is uncharted territory for me so I don't really understand what's going on.

I _think_ I understand the synaptic and apt-get process of loading new packages but neither seem to be able to load dosemu.   I believe I've got the proper repositories enabled and If I use synaptic, dosemu isn't shown.  dosemu-freedos is shown but I think that's only the freedos image (to be used with dosemu).

If I use sudo apt-get install dosemu, I get;


```
Reading package lists... Done
Building dependency tree... Done
Package dosemu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dosemu-freedos
E: Package dosemu has no installation candidate

```

I don't believe that dosemu-freedos is intended to replace dosemu.

Any help will be greatly appreciated.

I know this doesn't answer your question, but I use DOSBox and it seems to run every DOS app I throw at it with gusto. It's in the Ubuntu repositories and I had no problem installing it on my machine (Dapper, 386 kernel). More info on DOSBox may be found [COLOR="Red"]**_[here]("http://dosbox.sourceforge.net/news.php?show_news=1")_**[/COLOR] if you are interested.

---

### Post by monkeyfork on 2007-03-23
Thanks Klytu but I'm gonna try to stick w/ DOSEMU for now.  I'm trying to get an old borland compiler to work on it (bc3.1) for some legacy embedded dos app support.  I've had it working on RH9.1 before with no problem but now want to get it going on my laptop which is dapper.  Also DOSEMU seems to be more related to what's going on in the virtualization world, thought it might be a good benign learning experience that might have some relevance to the VM stuff that's all the rage.

---

### Post by mlind on 2007-03-23
You're right, there was a recent DOSEMU upload to dapper-updates repository. If you're not familiar with Ubuntu repository layout, check out [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

dapper-updates is a repository for stable updates.


You can query location of dosemu package using
```

apt-cache policy dosemu
apt-cache madison dosemu

```

Make sure you have
```

deb http://archive.ubuntu.com/ubuntu **dapper-updates** **multiverse**

```
if your /etc/apt/sources.list. Remember to refresh the package lists if you add new repositories.

For complete list
```

deb http://archive.ubuntu.com/ubuntu **dapper** main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu **dapper-updates** main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu **dapper-proposed** main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu **dapper-security** main restricted universe multiverse

```

---

### Post by monkeyfork on 2007-03-27
Thanks mlind,  
That got me closer.  I'm still a bit confused about the relationship between the sources.list and the synaptic tool.  It always seem that when I use the synaptic GUI way of modifying the sources.list things aren't quite as clear as they should be (for me at least).  I finally took the path of backing up my sources list and replacing it with a copy of what you had posted as "complete list" then followed the
more manual approach to package install like this;

sudo apt-get update
sudo apt-get install dosemu
sudo apt-get install xfonts-dosemu
sudo apt-get install dosemu-freedos

and that appeared to be successful

Unfortunately, now when I run dosemu, I get the following error indication;

ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option

I've seen other's with that gripe on DOSEMU so I'll go search for that elsewhere since I finally read the sticky post at top of Repositories & Backports that says this area is only for MAIN and RESTRICTED issues
see [http://www.ubuntuforums.org/showthread.php?t=6372](http://www.ubuntuforums.org/showthread.php?t=6372)  (ooops)

Thanks for your help.

---

### Post by mlind on 2007-03-27
I haven't used synaptic to add repositories in my  sources.list, so I can't comment on that. I guess does the job too, but I don't want gui applications to mangle my configuration files.

This might help with your DOSEMU problem
[https://launchpad.net/ubuntu/+source/dosemu-freedos/+bug/52857/comments/2](https://launchpad.net/ubuntu/+source/dosemu-freedos/+bug/52857/comments/2)

edit file /etc/dosemu/dosemu.conf with root privileges and define the **$_layout** option.

---

### Post by monkeyfork on 2007-03-27
mlind,

I'd already found similar hints within the forum posts when you wrote.  changing

# $_layout = "auto"  
to->  $_layout = "us"

seems to only remove the error indication left when a terminal session goes through
an attempted then aborted startup of DOSEMU.  What I see is freedos cranking up
in it's black screen then back to the terminal like it had exited normally.  It happens
so fast that I can't read  any error indication if there are any.

I see others have followed this path but the threads end with no resolution.  Appears I'm gonna have to drill down into the dreaded documentation.

Thanks

---

### Post by monkeyfork on 2007-03-27
Ok, found the solution.  Might I say, this was WAY WAY too painful (but admitedly,
I've got a very low threshold for computer pain).

See this bug report for fix and explanation;
[https://launchpad.net/ubuntu/+source/dosemu/+bug/48607](https://launchpad.net/ubuntu/+source/dosemu/+bug/48607)
The problem is evidently a bad comcom.com file that gets replaced if you follow
the instructions in the bug report.

Now that I've got my good old dos programs running, let me editorialize a bit.  This was my first experience at posting to a forum for support.  I was very pleased at the attempts at help, unfortunately I had to bail out of the forum and resort to google to finally find the bug report that led me to a fix.  Now, there may be some way that I could have included bug reports in my searches on the forum (since I'm just getting to know the system) but being new to the ubuntu support system, I don't have a clue.

I only mention this because it's my understanding that many are trying to use ubuntu on old hardware in situations where budgets are non-existant.  In those environments DOSEMU may have much more importance that we might imagine and I believe at least for LTS dapper the convolutions I went through should not be necessary.

Thanks

---

### Post by monkeyfork on 2007-03-27
Sorry to keep hammering away at this thread but I'm trying to be complete even though I'm not in the right forum to begin with.  

Ran into another problem.  Thought all was corrected but still have permissions or ownership screwed.  When in DOS everything appeared to work till I tried to write a file, all file creation
attempts fail.  Will ammend this post if solution found.

---

### Post by mlind on 2007-03-28
Sorry, I can't help you there. I'm a **dosbox** user myself and I don't recall having any major problems with it. I've never tried DOSEMU, so I don't know its quirks.

This might help though [http://www.jw-stumpel.nl/dosemu.html](http://www.jw-stumpel.nl/dosemu.html) (don't mind the article title ;))

> 
The RPM and Debian packages put the C: drive by default somewhere else in the filesystem, in a location **which is not writable by ordinary users** (who normally have write permission only inside their own home directory). So for doing actual work, installing programs, etc, you must use another (writable) location, which under MS-DOS will be the &#8216;D:&#8217; drive. I never liked this (several programs which I moved from an old DOS system assumed they were running from C:). &#8216;Standard&#8217; distributions can be set up, however, to give you a writable C: drive. **This document describes how to do this**.


Normal users don't and shouldn't have write permissions outside their /home directory. Create a local layout of the dos folder structure.

creating ~/.dosemurc and overriding  **$_hdimage** should probably work.
For example
```

$_hdimage = "${HOME}/dos"

```

---

### Post by monkeyfork on 2007-03-28
thanks again mlind,
  I haven't tried your work around yet but your post and the article (liked the title, most appropriate for me) got me to realize there was a drive D:  It's set up under my home so I  can write to that one and I believe that'll get me where i need to go (for real work!).  Hopefully, I'll get back to your suggestion and report back to the thread.

---

