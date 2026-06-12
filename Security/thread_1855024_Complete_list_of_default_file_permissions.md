---
title: "Complete list of default file permissions"
date: 2011-10-05
forum: Security
---

### Post by lorewap3 on 2011-10-05
Fellow Ubuntu Server users,


While I've used linux for years, I still consider myself a novice in many areas...and occasionally make fatal mistakes like running retarded commands like `sudo chmod -R 664 *` which have screwed my installation royally and made me reformat and start over from scratch...leading to hours and hours wasted.


What I want to know is whether there is a website or any type of resource that shows what the default permissions of each file should be on a vanilla installation of Ubuntu Server. Most importantly (in my case), the /etc directory, but knowing the rest of them wouldn't hurt either. I ran a `sudo chmod .*` in the /etc/skel directory...which went up to the /etc/ directory and changed every file in that directory (but not subdirectories luckily cause no -R). Sooo....I managed to change sudoers back and get into root, but am afraid to restart as I don't know what else in the /etc will bomb based on invalid permissions.


Any help would be most appreciated!

---

### Post by lcman on 2011-10-05
> **lorewap3 said:**
> Fellow Ubuntu Server users,


While I've used linux for years, I still consider myself a novice in many areas...and occasionally make fatal mistakes like running retarded commands like `sudo chmod -R 664 *` which have screwed my installation royally and made me reformat and start over from scratch...leading to hours and hours wasted.


What I want to know is whether there is a website or any type of resource that shows what the default permissions of each file should be on a vanilla installation of Ubuntu Server. Most importantly (in my case), the /etc directory, but knowing the rest of them wouldn't hurt either. I ran a `sudo chmod .*` in the /etc/skel directory...which went up to the /etc/ directory and changed every file in that directory (but not subdirectories luckily cause no -R). Sooo....I managed to change sudoers back and get into root, but am afraid to restart as I don't know what else in the /etc will bomb based on invalid permissions.


Any help would be most appreciated!

I'm not sure what you're looking for but maybe it's ```
ls -l
```

---

### Post by The Cog on 2011-10-05
As far as I know, that information is stored in the .deb packages. To know the proper settings would require examining every paclage in the repositories. Worse, I think some files are created by scripts, so even examining the archives of every .deb in the repo won't tell you everything. If you're in the habit of mucking up the permissions, then keeping good backups is probably the best solution.

---

### Post by lorewap3 on 2011-10-05
I hope the first post was ironic, but even if it wasn't, I deserved it for the mistake. 

I was just hoping there would be some place on the net that had listed the directory structure and permissions of just a standard Linux install. They're all pretty much the same before you start adding globs of packages, and even then messing up permissions on those would only affect the package, not the kernel or core OS.


Ex. I know that /etc/sudoers REQUIRES 440 or it doesn't work at all. There are a few similar rules but I have no clue how to find out what they would be. That one will pretty much shut you down for good unless you've already enabled the root account which most distributions don't recommend or sometimes even allow. Even with a root account enabled, without some guide to the default permissions you have to sit there and just keep troubleshooting every part of the OS until it works. Most of the time it's just easier to re-install the entire thing, which is neither educational nor time efficient. 

A simple webpage with a recursive 'ls -l' on a default installation would at least tell you what the permissions start as in Ubuntu's eyes. 

As I said I'm slowly learning more and more about each package and its own quirks but it's a slow process and I'm certainly never going to have the permissions mysql requires on its db files memorized a year from now. Months ago I moved the mysql db files to a different location and it took unnecessary hours figuring out the perfect owernship/groups/permissions it wanted to work properly. Man pages almost never touch on this.

---

### Post by bodhi.zazen on 2011-10-06
Boot the live CD and run a script that puts the permissions of all the files into a database =)

---

### Post by lorewap3 on 2011-10-06
Yeah...I know...stop passing the monkey. :) If thought I could do it in a few hours  I would but definitely not that good. Maybe a few days probably more like a few weeks good, but I'm ok now so I apologize for my selfishness but I probably won't do it now. Next priority is getting connectivity to my storage on my server yet discover the perfect balance of permissions to prevent a potential attack if one goes awol or like me doesn't know what he/she is doing. Alas..

---

### Post by Jonathan L on 2011-10-07
> **lorewap3 said:**
> Yeah...I know...stop passing the monkey. :) If thought I could do it in a few hours  I would but definitely not that good. Maybe a few days probably more like a few weeks good, but I'm ok now so I apologize for my selfishness but I probably won't do it now. Next priority is getting connectivity to my storage on my server yet discover the perfect balance of permissions to prevent a potential attack if one goes awol or like me doesn't know what he/she is doing. Alas..

Hi Lorewrap

Well we've all done it, hopefully only once.  Don't forget chmod -R ugo+X is your friend for fixing the directories.

Attached is the compressed output of
```
sudo find / -ls
```It was done on a 32-bit Ubuntu 10.04 system booted cleanly at Amazon from Canonical's image ami-311f2b45.

Is that what you needed?

Kind regards,
Jonathan.

---

### Post by lorewap3 on 2011-10-10
Thanks Jonathan,

I really appreciate this. I had fixed the problem (only by luck) so I kinda dropped the subject, but I'm glad I'll have this for the next time I do something stupid like this.

In the end I knew I only changed the /etc directory and no sub-directories, so I just did 755 on the directories and 664 on most of the files, except for sudoers and a few others. It seemed to work fine. The only way I didn't have to start over is I was lucky enough to have a console in one of my 'screen's that had 'sudo -i' to root. Had I not done that before my mistake I would have had to boot into safe mode, etc... doable...,but definitely not remotely which is how I use this thing 99% of the time. 

Thanks for your time in doing this for me man, not many people would have.

Will

---

### Post by dodo3773 on 2011-10-10
Wouldn't reinstalling your applications change the file permissions back (As in creating a list of installed apps and reinstalling from that list)? I don't know. I am just curious.

---

### Post by bodhi.zazen on 2011-10-10
> **dodo3773 said:**
> Wouldn't reinstalling your applications change the file permissions back (As in creating a list of installed apps and reinstalling from that list)? I don't know. I am just curious.

In theory, yes. I have not tested this at all.

---

### Post by Dangertux on 2011-10-10
> **bodhi.zazen said:**
> In theory, yes. I have not tested this at all.

In theory but I think the original idea of liveCD plus accurate permissions list which was provided in this thread is a better idea.

Think about it depending on how bad you toast your permissions you may not be able to install anything, or login or boot. So I would go with the LiveCD + permissions list if you absolutely need to recover the install, or just reinstall.

Personally, I would boot to a LiveCD recover any personal data (you can change those permissions easily) and do a full reinstall, will probably be less time involved and much less trial and error.

---

### Post by dodo3773 on 2011-10-10
> **bodhi.zazen said:**
> In theory, yes. I have not tested this at all.

I think that is the route I would take personally. It does not seem like it would take that long to figure out if it worked or not (dependent on how many packages were in your cache or stored locally). If it worked it seems like it would save a lot of time in the long run. 

If a configuration file already exists for a certain application then would it be written over when reinstalling said application? I do not think that is the norm but it would probably be the biggest drawback to doing it this way.

Edit: Also, if reinstalling did not change a configuration file would it still change the permissions on that file?

---

### Post by bodhi.zazen on 2011-10-10
> **dodo3773 said:**
> I think that is the route I would take personally. It does not seem like it would take that long to figure out if it worked or not (dependent on how many packages were in your cache or stored locally). If it worked it seems like it would save a lot of time in the long run. 

If a configuration file already exists for a certain application then would it be written over when reinstalling said application? I do not think that is the norm but it would probably be the biggest drawback to doing it this way.

Edit: Also, if reinstalling did not change a configuration file would it still change the permissions on that file?

Well installing all the packages is a re-install, does not really matter if you are going to do it with apt-get or with a live CD.

apt-get would be more complex as you would probably need to start with a few key files, such as sudoers, and some of the apt config files, and then gcc. You would almost certainly need to force a few packages.

A master list of files from a live CD would be "OK", you just need to devise an easy method one can then script to read the permissions and set the proper permissions.

Sounds like we need someone to write a script, but to me manual list does not do much.

Might be easier to simply assume system directories are 755 and files are 644 and then list only the exceptions.

knock yourselves out =)

---

### Post by dirtrider1 on 2011-10-11
.

---

### Post by Jonathan L on 2011-10-11
> **lorewap3 said:**
> Thanks Jonathan,

I really appreciate this. I had fixed the problem (only by luck) so I kinda dropped the subject, but I'm glad I'll have this for the next time I do something stupid like this.

Hi Will

Just to close this off, I thought I'd take a look at a script to fix the permissions back to defaults, as  it occurred to me it mightn't be as easy as it looks.  The tricky bit is to deal with "unusual filenames", get all the quoting correct, remember that chown switches off setuid, and most important, do it before you need it!  Attached are the results.

Plan: When everything is in good shape (ie, immediately after installation) run a script (mkcheckperms) which produces a checking script (checkperms).  This script checks everything is as it should be; if a file/directory has the wrong owner, group, or permissions (all considered numerically), say we should fix them (as a script, of course).

This script, mkcheckperms,  is run as root in /
```
#!/bin/sh

find . -xdev \( -type f -o -type d \) \
 -printf "if [ \`stat -c '%%u:%%g:0%%a' '%h/%f'\` != %U:%G:%#m ]; then echo \"chown %U:%G '%h/%f' ; chmod %#m '%h/%f'\"; fi\n" \
| sort

```Which means:[INDENT]Find, from current directory (don't cross any mount points): all files and directories[INDENT]For each one, output a line (part of a shell script) which says[INDENT]If the current user/group/permissions for this file are not U/G/P then output a command which says[INDENT]Change the owner to U/G for file F
Change the permission to P for file F
[/INDENT][/INDENT][/INDENT][/INDENT]You run that
```
cd /
sudo sh /path/to/mkcheckperms.sh > /tmp/checkperms
```It makes a big script, one line per file or directory (ie, 27,424 lines), which has this function:[INDENT]
[LIST]
[*]if user and group and perms for this file aren't the right thing then chown and chmod
[/LIST]
[/INDENT]Concretely, the lines for /etc, umount (typical setuid program) and (chatscripts, an unusual one), look as follows:
```
if [ `stat -c '%u:%g:0%a' './etc'` != 0:0:0755 ]; then echo "chown 0:0 './etc' ; chmod 0755 './etc'"; fi
if [ `stat -c '%u:%g:0%a' './bin/mount'` != 0:0:04755 ]; then echo "chown 0:0 './bin/mount' ; chmod 04755 './bin/mount'"; fi
if [ `stat -c '%u:%g:0%a' './etc/chatscripts'` != 0:30:02750 ]; then echo "chown 0:30 './etc/chatscripts' ; chmod 02750 './etc/chatscripts'"; fi

```This big script, checkperms, checks permissions and produces a script to fix them if they're wrong.  You run it from the root of the filesystem, as root:
```
cd /
sudo sh /tmp/checkperms > /tmp/FIXIT
```For example, if the values for /bin/mount and /etc/networks were wrong, FIXIT might look like this:
```
chown 0:0 './bin/umount' ; chmod 04755 './bin/umount'
chown 0:0 './etc/network' ; chmod 0755 './etc/network'

```To fix them, you clearly do
```
sudo sh /tmp/FIXIT-READITFIRSTPLEASE
```Attached are mkcheckperms (the little script), and checkperms (for Ubuntu 10.04, produced on 32-bit Ubuntu 10.04 system booted cleanly at Amazon from Canonical's image ami-311f2b45).

It's not a 100% solution as it's a little weak against unusual filenames (see find(1)), but survives all the files which are on a default installation, including the occasional '(', ')' and the UTF8 in /usr/share/doc/kbd/utf/.

Perhaps they'll be of use to someone, some day.

Kind regards,
Jonathan.

---

