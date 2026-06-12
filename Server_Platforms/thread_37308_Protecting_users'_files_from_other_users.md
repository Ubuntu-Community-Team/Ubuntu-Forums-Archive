---
title: "Protecting users' files from other users"
date: 2005-05-26
forum: Server Platforms
---

### Post by Zifnab on 2005-05-26
Hi. I've got some experience as a Linux user, but very little as an administrator of a machine running it. After a failed attempt at Gentoo (I think I'm just not hardcore enough yet), I installed Ubuntu, and so far I love it.

Anyhow. I set up Apache both for my own amusement and so that a few friends could play around with PHP, something they both want to learn. Having fallen in love with PHP the last few months, I'm happy to feed that interest. 

What I'm trying to do is make it so they don't have permission to directly view each other's (or my!) web source code, but still let Apache display it to the world. Not that I think anyone will act maliciously - we're all friends, as I said, but as a matter of principle and my own knowledge of Linux, I'd really like to set up these protections.

My basic setup is this: 
Under /var/www/ are two user directories, we'll call them user0 and user1. I have them each symlinked to from their respective /home directories. The owner:group of each is user0:user0 and user1:user1, respectively. So if it weren't for making the files available to the web, I could just set permissions on the folders to xwrx-r---. But then Apache can't read them... or rather, it needs to execute them. 

So when I ran "ps aux", I saw that the Apache processes were being run by a user called www-data, so I added www-data to the groups user0 and user1, but that didn't work either, unfortunately.

The best I have right now is taking out read access for non-group users, so they can't transfer the files or view them but could easly open them in Vi or some other editor simply by knowing the file name.

*sigh*

Am I missing something, or is there just a completely different and easy way to go about this?

---

### Post by LordHunter317 on 2005-05-26
[QUOTE=Zifnab]After a failed attempt at Gentoo (I think I'm just not hardcore enough yet), [/quote]Hardcore has nothing to do with that waste of time.

> What I'm trying to do is make it so they don't have permission to directly view each other's (or my!) web source code, but still let Apache display it to the world.Doing it for the shell is easy.  Preventing PHP code from reading other's PHP code is much harder.  I've never done it, but I believe the standard way is to run PHP as a CGI script using safe_mode and Apache suExec, perhaps with some other PHP trickery.

> Under /var/www/ are two user directories, we'll call them user0 and user1. I have them each symlinked to from their respective /home directories.This is your first mistake, IMO.  Setup userdirs via mod_userdir and make them keep their files in /home.  Failing that, setup virtual hosts or Aliases to those dirs.  Keep  their stuff out of your main webroot.

> But then Apache can't read them... or rather, it needs to execute them. Apache doesn't need to execute PHP files, just read them.  It'll need the execute bit on directories, but that means access in that case.

> So when I ran "ps aux", I saw that the Apache processes were being run by a user called www-data, so I added www-data to the groups user0 and user1, but that didn't work either, unfortunately.You'd have to restart Apache after giving it group membership.  Membership changes do not apply to already running processes.

> Am I missing something, or is there just a completely different and easy way to go about this?You're on the right track, but hte real solution is much more complicated.

Just fixing the filesystem permissions isn't enough.  That prevents me from viewing another user's file in the shell, but not with a PHP script.  Since PHP runs as the Apache user, I can write a script to view anything Apache can.  Hence, the nasty CGI/suExec hack solution.

Apache's 2 perchild MPM would be a great solution if it wasn't threaded.

---

### Post by Zifnab on 2005-05-27
Hah, I wouldn't say Gentoo is a waste of time. I really love the measure of control it provides, and the installation process taught me a LOT about the inner-workings of Linux. Stuff I'd never know after installing a bunch of self-installing binaries.
That said, Ubuntu does fit my needs better, and I'm quite happy with it.

Anyhow. Thanks for the advice! 

When I said "it just needs to execute them" I meant that when I gave www-data r-- access it didn't work, but it did work with --x. 

What I ended up doing is putting a www directory in each user's /home and having /var/www/ symlink to them instead of the other way around. And restarting Apache let www-data use them, as you said.
Still not entirely secure, but good enough for me, hah.

---

### Post by LordHunter317 on 2005-05-27
Don't use symlinks, use the Alias directive in Apache's configuration. It's less open to certain forms of abuse.  Really.

Exceute means access on a directory.  To see the contents of a directory 'r'.  To get a file inside a directory you need 'x' plus 'r' on the file you want.  Thus if you give someone access but not read permissions to a directory they can read files inside of it, but only if they know the name ahead of time.

This is how user dirs are typically setup.  The world gets access permission to the user's home directory, but not read.  That way apache can access /home/user/public_html but can't see what's inside /home/user.

---

