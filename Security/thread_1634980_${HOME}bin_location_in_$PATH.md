---
title: "${HOME}/bin location in $PATH"
date: 2010-12-01
forum: Security
---

### Post by hhhobbit on 2010-12-01
I installed Ubuntu 10.04 only be dismayed to find ${HOME}/bin FIRST IN THE PATH.  I blogged about it at my blog (I sudo an xterm rather than just sudoing to get a different background for the sudo'd xterm):

[http://SecureMecca.BlogSpot.com/2010/06/sudo-just-wont-do.html](http://SecureMecca.BlogSpot.com/2010/06/sudo-just-wont-do.html)

I agree that some new user should probably not be logging on as root.  But if the replacement for 'ls' is in their ${HOME}/bin/ the sudo'd shell inherits the same PATH, umask, and everything else! In general I take a dim view of a sudo only way of doing things.  It seems to cause more problems than it solves for disciplined, knowledgeable users. In the case of Ubuntu it caused me to create a /root folder for root to reset the umask back from 077 which is what I use over to 022 which is what root should use.  The /root/.profile of course made sure there is no /home/me/bin in the sudo'd PATH.  It didn't matter because somebody is not just SETTING the file perms and is instead calculating them based off of modifications to the umask.  JUST SET THEM! I ran into a problem with GRUB getting things fouled up because I was having to remove the new kernels and instead of using the command line option (much prefereable) used Synaptic Manager instead:

[http://SecureMecca.com/public/ChmodTable.txt](http://SecureMecca.com/public/ChmodTable.txt)

In fhe case of an infection living in a user's file space you really should want to go in to clean it out as some other user than the user that is infected.  Having said that the hackers seem to be going for the whole enchilada right off the bat.  A WARNING is in order here.  DO NOT USE A ROOT ACCOUNT OR SUDO FOR NORMAL TASKS!  But please put ${HOME}/bin last in the PATH or preferably don't even put it in the PATH at all.  Let users add it themselves if they want it. Also once hackers figure out that hijacking a sudo tty (from what I just read else-where here I would say several hackers are working on doing that right now - sendmail my ****) is a dandy way of doing things you really will need to provide for ways of cleaning a user infestation out by going at it some other way than through that infected user.  A lot of Ubuntu users have only one login account, the one they created when they set the machine up.

I am not some young idiot.  I have been using Unix / Linux since the late 1970s.  But there are always gotchas and things to learn. Personally I am happy with the work-arounds I have except for this cleaning out of a user infestation.  I think you would be much better off going at cleaning it out as ANY other user than the one that was infected.  Give it some thought.  But that ${HOME}/bin being first in the PATH HAS GOT TO GO TO THE END OR DISAPPEAR ALTOGETHER!

---

### Post by CharlesA on 2010-12-01
There is no $HOME/bin folder by default.

```
charles@lucid:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

It is only added to the path if you create a folder at $HOME/bin

What's the problem?

Also: Ubuntu doesn't have the root account enabled by default. You can use ***sudo -i*** to get to a root shell. See [here]("https://help.ubuntu.com/community/RootSudo").

EDIT: Why would you run something like ls with sudo? There's no real need to unless you need to list files that you don't have read access to.

EDIT2: I just checked to see what the umask was on my default install of Ubuntu 10.04 and it's set to 0022, which is the correct umask.

---

### Post by FuturePilot on 2010-12-01
> **CharlesA said:**
> 
What's the problem?


The problem is that it overrides the other paths. Someone could easily drop a malicious script called "ls" into ~/bin and the next time you run ls it executes the malicious script instead of the real ls. Now I could see how this could be convenient in certain situations. Say you want to install a newer version of something but you don't want to do it system-wide, so you install it to ~/bin and you can easily use it. But it appears this is a double edged sword because of the first situation I described.

```
$ ls
dir1  dir2  dir3  file1  file2  file3
$ mv ~/ls ~/bin/
$ source ~/.zshrc
$ ls
This is a malicious script
$
```

---

### Post by CharlesA on 2010-12-01
Makes sense. I guess the question should be: Would a normal user have a bin directory in their home directory?

In any case, @OP: File a bug report about it.

---

### Post by sisco311 on 2010-12-01
> **hhhobbit said:**
> But if the replacement for 'ls' is in their ${HOME}/bin/ the sudo'd shell inherits the same PATH, umask, and everything else! In general I take a dim view of a sudo only way of doing things.  It seems to cause more problems than it solves for disciplined, knowledgeable users. 


sudo is highly configurable. Check out **man sudoers**.

You can configure the environment variables with the env_reset, env_file,  env_check, env_delete and env_keep options. The umask with umask_override and umask. And the PATH with the ignore_dot and secure_path options.
   

> **hhhobbit said:**
> 
I think you would be much better off going at cleaning it out as ANY other user than the one that was infected.  Give it some thought.  


Single user mode or chroot...

> **hhhobbit said:**
> 
But that ${HOME}/bin being first in the PATH HAS GOT TO GO TO THE END OR DISAPPEAR ALTOGETHER!

I prefer having it at the end of the PATH.

---

### Post by cariboo on 2010-12-01
I'd like to know what strange kind of setup the op has, my path looks like this:

> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

My system isn't default by any means, as I'm running Natty, but it's pretty close. What did the op do to have ~/bin added to the path?

---

### Post by movieman on 2010-12-01
> **cariboo907 said:**
> My system isn't default by any means, as I'm running Natty, but it's pretty close. What did the op do to have ~/bin added to the path?

Nothing, from the look of it: I have a ~/bin in $PATH and I didn't realise that it had been added to the path until now. I'm sure it wasn't there in older versions of Ubuntu and I didn't add it.

Putting it in the path isn't a bad idea, but as mentioned above, it should be at the end of the path, not the start. Otherwise anyone who can write to your home directory can get you to run an arbitrary program by putting it into ~/bin with the same name as a real Linux program.

---

### Post by sisco311 on 2010-12-01
> **cariboo907 said:**
> I'd like to know what strange kind of setup the op has, my path looks like this:



My system isn't default by any means, as I'm running Natty, but it's pretty close. What did the op do to have ~/bin added to the path?

If you are using bash or dash as your shell and ~/bin exists, then, by default, it's is added to PATH. 

~/.profile: 
```
...
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

---

### Post by bodhi.zazen on 2010-12-01
> **sisco311 said:**
> If you are using bash or dash as your shell and ~/bin exists, then, by default, it's is added to PATH. 

~/.profile: 
```
...
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

I agree $HOME/bin should be last.

It is a very minor potential security problem, if an intruder can write to ~/bin you have already been cracked and they have access to at least your account (shell access) and quite likely root already.

Most modern crackers are no so sloppy as to leave tracks, let alone in a user's home directory.

---

### Post by CharlesA on 2010-12-01
> **bodhi.zazen said:**
> I agree $HOME/bin should be last.

+1 to that. Is that worthy of a bug report?

> It is a very minor potential security problem, if an intruder can write to ~/bin you have already been cracked and they have access to at least your account (shell access) and quite likely root already.

Indeed. The only way I can see this working is for someone to gain access to the user's home directory and do three things:

A) Create ~/bin
B) Put files in ~/bin/
C) Reboot/relaunch terminal

The most common would probably be cracking a weak password and gaining access that way. If that was the case, why even bother with messing with files in the user's home directory? You have root access, and can do more then just mess with someone's files.

---

### Post by sisco311 on 2010-12-02
> **CharlesA said:**
> +1 to that. Is that worthy of a bug report?


I think it worth a try. /etc/skel/.profile is installed by bash. The patch is trivial.

GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu)

**diff -Naur /etc/skel/.profile profile.patch**:
```
--- /etc/skel/.profile	2010-12-02 05:19:26.077506031 +0000
+++ profile.patch	2010-12-02 04:51:58.433339619 +0000
@@ -18,5 +18,5 @@
 
 # set PATH so it includes user's private bin if it exists
 if [ -d "$HOME/bin" ] ; then
-    PATH="$HOME/bin:$PATH"
+    PATH="$PATH:$HOME/bin"
 fi

```

---

### Post by bodhi.zazen on 2010-12-02
> **sisco311 said:**
> I think it worth a try. /etc/skel/.profile is installed by bash. The patch is trivial.

I agree with this. I have used a custom .bashrc (.zshrc) for a long time ;)

---

### Post by CharlesA on 2010-12-02
> **sisco311 said:**
> I think it worth a try. /etc/skel/.profile is installed by bash. The patch is trivial.

GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu)

**diff -Naur /etc/skel/.profile profile.patch**:
```
--- /etc/skel/.profile	2010-12-02 05:19:26.077506031 +0000
+++ profile.patch	2010-12-02 04:51:58.433339619 +0000
@@ -18,5 +18,5 @@
 
 # set PATH so it includes user's private bin if it exists
 if [ -d "$HOME/bin" ] ; then
-    PATH="$HOME/bin:$PATH"
+    PATH="$PATH:$HOME/bin"
 fi

```

So you'd file a bug against bash, itself?

---

### Post by SeijiSensei on 2010-12-02
> **CharlesA said:**
> So you'd file a bug against bash, itself?

No, it's distro specific.  On my CentOS 5.5 machine, /etc/skel/.bash_profile places $HOME/bin at the end of the PATH.  

This "feature" appears to be from Debian.  On a Debian Lenny server I manage, the code in /etc/skel/.profile is identical to that in Ubuntu.

---

### Post by CharlesA on 2010-12-02
> **SeijiSensei said:**
> No, it's distro specific.  On my CentOS 5.5 machine, /etc/skel/.bash_profile places $HOME/bin at the end of the PATH.  

This "feature" appears to be from Debian.  On a Debian Lenny server I manage, the code in /etc/skel/.profile is identical to that in Ubuntu.
That makes it something that they would have to deal with "upstream" then, I guess.

Fun times.

---

### Post by sisco311 on 2010-12-02
> **CharlesA said:**
> That makes it something that they would have to deal with "upstream" then, I guess.

Fun times.

I guess, one could report it at launchpad with the priority set as 'Wishlist".

---

### Post by CharlesA on 2010-12-02
> **sisco311 said:**
> I guess, one could report it at launchpad with the priority set as 'Wishlist".
To launchpad!

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/684393](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/684393)

---

