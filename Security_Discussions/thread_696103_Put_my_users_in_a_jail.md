---
title: "Put my users in a jail"
date: 2008-02-13
forum: Security Discussions
---

### Post by melange on 2008-02-13
I'm maintaining a small server at the university. But, I would like to restrict the users from having access to other peoples account. I know that users, in the traditional Linux security model, are responsible for maintaining the access control details of their own files - but my experience is that it just doesn't work like that in the real world :) A user reads that he needs to chmod his php-script to 777 and because he can't get it working he chmod everything to 777.

What I want is the same solution a lot of webhosts use. You have ssh-access, can run all the apps you like, but somehow you are just living inside a jail and can't see any other users on the system.

Any idea how to do that?

---

### Post by lloyd_b on 2008-02-13
> **melange said:**
> I'm maintaining a small server at the university. But, I would like to restrict the users from having access to other peoples account. I know that users, in the traditional Linux security model, are responsible for maintaining the access control details of their own files - but my experience is that it just doesn't work like that in the real world :) A user reads that he needs to chmod his php-script to 777 and because he can't get it working he chmod everything to 777.

What I want is the same solution a lot of webhosts use. You have ssh-access, can run all the apps you like, but somehow you are just living inside a jail and can't see any other users on the system.

Any idea how to do that?

Type "man chroot" in a terminal window - the chroot command is what programs like ftp daemons use to hide all but selected parts of the system from the user.

The first step in implementing it is to provide links, within the user's home directory, to directories that they will need access to.  For example, they'll need "/bin" (in order to run "bash"), "/tmp" (for temp files), and pretty much the entire "/usr" directory tree (for everything else).  Symbolic links will NOT work from within a chroot, so you'll either need hard links (which will not work across file systems), or use the remount capability of the "mount" command.

Once that's done, you just need to execute the chroot command to lock them in.

Here's a rough sample of a script:
```
mount --bind /bin /home/username/bin
mount --bind /tmp /home/username/tmp
mount --bind /usr /home/username/usr
chroot /home/username /bin/bash
```

Create this script in the "/bin" directory.  Call it "lockin".  Set its permissions to 755 (-rwxr-xr-x), so that everyone can execute it, but only root can modify it.

Then, create the "bin" "tmp" and "usr" mount points (directories) in the user's home directory.

Finally, in "/etc/passwd", change the user's default shell ("/bin/bash") to the script above ("/bin/lockin").

There are quite a few "gotcha's" with using chroot.  For instance, depending on how you filesystems are configured you may need to use "mount --rbind..." instead of "mount --bind", and the directories I've included may or may not be enough (again, depending on exactly what the users use, and how things are configured), so if you want to try this, plan on spending some time tinkering to get it configured correctly.

Lloyd B.

---

### Post by HermanAB on 2008-02-14
Hmm, bear in mind that it is possible to break out of a chroot jail, although most people don't know how.  So it is a good tool to manage honest users, but doesn't help much against real troublemakers.

Other systems, for example Mandriva, runs a security deamon (msec) that passes through the whole system once per hour fixing up bad settings.  I suggest that you do something like that in addition to the chrooting.  Write a little user permissions fix script and put it in cron.hourly.

Cheers,

Herman

---

### Post by Contess on 2008-02-14
> **HermanAB said:**
> 
Other systems, for example Mandriva, runs a security deamon (msec) that passes through the whole system once per hour fixing up bad settings.  I suggest that you do something like that in addition to the chrooting.  Write a little user permissions fix script and put it in cron.hourly.

Cheers,

Herman

Hi
can you point out on how a newbie would do this, by a step by step guide ?

Thanks so much

---

### Post by HermanAB on 2008-02-14
A newbie???  

Hmmm, I'd recommend that you install Mandriva or PCLOS and set the Security Level to High when you install it.  That will take care of most of your problems.

Cheers,

Herman

---

### Post by Contess on 2008-02-14
> **lloyd_b said:**
> Type "man chroot" in a terminal window - the chroot command is what programs like ftp daemons use to hide all but selected parts of the system from the user.

The first step in implementing it is to provide links, within the user's home directory, to directories that they will need access to.  For example, they'll need "/bin" (in order to run "bash"), "/tmp" (for temp files), and pretty much the entire "/usr" directory tree (for everything else).  Symbolic links will NOT work from within a chroot, so you'll either need hard links (which will not work across file systems), or use the remount capability of the "mount" command.

Once that's done, you just need to execute the chroot command to lock them in.

Here's a rough sample of a script:
```
mount --bind /bin /home/username/bin
mount --bind /tmp /home/username/tmp
mount --bind /usr /home/username/usr
chroot /home/username /bin/bash
```

Create this script in the "/bin" directory.  Call it "lockin".  Set its permissions to 755 (-rwxr-xr-x), so that everyone can execute it, but only root can modify it.

Then, create the "bin" "tmp" and "usr" mount points (directories) in the user's home directory.

Finally, in "/etc/passwd", change the user's default shell ("/bin/bash") to the script above ("/bin/lockin").

There are quite a few "gotcha's" with using chroot.  For instance, depending on how you filesystems are configured you may need to use "mount --rbind..." instead of "mount --bind", and the directories I've included may or may not be enough (again, depending on exactly what the users use, and how things are configured), so if you want to try this, plan on spending some time tinkering to get it configured correctly.

Lloyd B.

Hello Lloyd
I followed your instructions precisely but the chroot shell doesnt work. The user (in my case) is called "owner" and when logging into this account, I am still able to navigate above the /home/owner directory, into other users home directories.

Here's what I tried:
created a script using the ubuntu text editor:
mount --bind /bin /home/username/bin
mount --bind /tmp /home/username/tmp
mount --bind /usr /home/username/usr
chroot /home/owner /bin/bash

..placed it into /bin , named "lockin" (no quotes of course.
..set the permissions to 755 and chmod it to root:root

Then changed the /etc/passwd line to:
/bin/lockin

Then logged in, but no avail of chroot.

Then I went on and chnged the script to use --rbind instead:

mount --rbind /bin /home/username/bin
mount --rbind /tmp /home/username/tmp
mount --rbind /usr /home/username/usr
chroot /home/owner /bin/bash

.. but still, the user account still functions as if there were no restrictions at all

PS: I did reboot after each change, just to make sure.

Any ideas ??

Thx

---

### Post by lloyd_b on 2008-02-14
Okay, problem....

The instructions I posted are COMPLETELY USELESS:(

Setting up the chroot is a *lot* more complex.

Here's a link to some [good instructions]("http://www.howtoforge.com/chroot_ssh_sftp_debian_etch"), but it involves a lot of work.  The link is for Debian rather than Ubuntu, but the instructions should work since Ubuntu is derived from Debian.  Note that this only affects ssh logins - if a person can get to the console, they can bypass the gaol.

I don't particularly care for this solution, as it requires copying every executable and library into the jail (potentially a LOT of files, depending on what the user needs). 

I've got some ideas for a simpler solution, but I need some time to play with it.  Maybe by the weekend I'll have had a chance to test it, but if you want something that's guaranteed to work, follow the provided link.

My apologies for leading you astray.

If my ideas actually work, I'll post the results in this thread.

Lloyd B.

---

### Post by Dr Small on 2008-02-14
I would love to see your followup, since I have longed for a simple, down to earth chroot jail example.

Dr Small

---

### Post by manpaz on 2008-02-14
I have used MySecureShell, that is bases in OpenSSH.  It will deny ssh access but will get the user sftp access that is enough manipulate files and folders like create, edit, remove, change ownership and so on.

You can get the .deb package from its site:

[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

or download direct:

```

# wget http://superb-west.dl.sourceforge.net/sourceforge/mysecureshell/mysecureshell_1.0_i386.deb
# sudo dpkg -i mysecureshell_1.0_i386.deb

```

It will install all the files needed to run the daemon, that you can restart easy with:

```

#sudo /etc/init.d/mysecureshell restart

```

Then you can edit the config file /etc/ssh/sftp_config.  Finally, to chroot the users you just need to change the shell for every user, I mean for the user client1 you should do:

```

#sudo /usr/sbin/usermod -s /bin/MySecureShell client1

```

By default the chrooted jail is defined as /home/$USER, but you can modify it as you want in the configuration file.

I hope this be helpfully.

    -Manuel

---

### Post by kevdog on 2008-02-15
Im no jail expert, but I used the linux jailkit utility that made setting up a jail really easy (its just a series of scripts that automate setting up the jail): [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

The user mailing list is not that active, however oliver the creator is very good at answering questions within a day or so.  I managed to get this up and running in a few hours since I did a bone head move at first.  The instructions are very thorough although if you are like me, you enjoy tweaking, that sometimes gets you lost until you become really familiar with how jails work.

---

### Post by honeydew on 2008-02-15
just a question.. what processor are you utilizing? virtual environments have proven themselves quite a bit over chrooting when it comes to the linux environment I would suggest reading up on [KVM]("http://kvm.qumranet.com/kvmwiki"), [openVZ]("http://openvz.org/"), and [XEN]("http://www.citrixxenserver.com/Pages/default.aspx").   Now I cant promise you that users with root on there virtual machines will not figure a way to break out of there shells..  but I think it may be a more secure option then chrooting everyone.

---

### Post by Contess on 2008-02-16
> **lloyd_b said:**
> Okay, problem....

The instructions I posted are COMPLETELY USELESS:(

Setting up the chroot is a *lot* more complex.

Here's a link to some [good instructions]("http://www.howtoforge.com/chroot_ssh_sftp_debian_etch"), but it involves a lot of work.  The link is for Debian rather than Ubuntu, but the instructions should work since Ubuntu is derived from Debian.  Note that this only affects ssh logins - if a person can get to the console, they can bypass the gaol.

I don't particularly care for this solution, as it requires copying every executable and library into the jail (potentially a LOT of files, depending on what the user needs). 

I've got some ideas for a simpler solution, but I need some time to play with it.  Maybe by the weekend I'll have had a chance to test it, but if you want something that's guaranteed to work, follow the provided link.

My apologies for leading you astray.

If my ideas actually work, I'll post the results in this thread.

Lloyd B.

Ahh.. no problem.
Looking forward to your next reply.

BTW, The solution I am looking for is for local users on a local machine, not remote users through ssh. Sorry I didn't mention it earlier.

---

