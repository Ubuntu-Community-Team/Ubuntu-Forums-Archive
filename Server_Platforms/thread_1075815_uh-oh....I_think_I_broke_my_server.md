---
title: "uh-oh....I think I broke my server?"
date: 2009-02-20
forum: Server Platforms
---

### Post by mistypotato on 2009-02-20
First time this has happened....

instead of the username box, the screen stays black and the following message appears.....

**Cannot start the greeter application.  you will not be able to log in.  This display will be disabled.  Try logging in by other means and editing the configuration file.**


last thing I remember doing was changing permissions and I may have accidentally changed the permissions on the /etc/lib folder....maybe

thanks for your advice  :D

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> First time this has happened....

instead of the username box, the screen stays black and the following message appears.....

**Cannot start the greeter application.  you will not be able to log in.  This display will be disabled.  Try logging in by other means and editing the configuration file.**


last thing I remember doing was changing permissions and I may have accidentally changed the permissions on the /etc/lib folder....maybe

thanks for your advice  :D

Can you get to the terminal login before the desktop starts?  If so you can login there and change the permissions back.

---

### Post by mistypotato on 2009-02-20
Since Ive never interrupted the boot before, when do you get the opportunity to do that ?  should you press F8 like in Windows or something ?

thx

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> Since Ive never interrupted the boot before, when do you get the opportunity to do that ?  should you press F8 like in Windows or something ?

thx

On restart you can hit the escape key (goes by really quick) and you should be able to boot in recovery mode.  Since you say you changed some things that now do not allow you to boot up this is where I would go.  Not sure you can get it fixed any other way without editing the grub file.  Maybe somone else will have a better answer, but that is what I do.

---

### Post by mistypotato on 2009-02-20
ok.
thx.

I'm able to get to the shell prompt.

I can move around in the directories and see the permissions using ls -al (gee I've come a long way in 2 weeks :-)

But how can I tell what directories or files have the wrong permissions now?


thx

---

### Post by E_K on 2009-02-20
# type: sudo vim /etc/gdm/gdm.conf (or use your favorite text editor)
# Search for 'Automatic login'. Type: '/Automatic login'
# Change AutomaticLoginEnable to true
# Cange the AutomaticLogin to your username
# In vim use 'i' to get into insert mode, then 'esc :wq' to quit

---

### Post by mistypotato on 2009-02-20
I potentially see something....

It looks like in the root directory "/" that the folder called "lib"
has me as the owner?  shouldn't root be the owner of "/lib" ?

Currently it is as follows....

Owner = Me
Group = root
Owner permissions rwx
Group Permissions rwx
Other ---

or is that not an issue?


thz

---

### Post by mistypotato on 2009-02-20
well, I changed lib to owner = root and that didnt fix it

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> I potentially see something....

It looks like in the root directory "/" that the folder called "lib"
has me as the owner?  shouldn't root be the owner of "/lib" ?

Currently it is as follows....

Owner = Me
Group = root
Owner permissions rwx
Group Permissions rwx
Other ---

or is that not an issue?


thz

Mine says root for owner and group.

Is this one of the files you changed?  Do you remember which ones you were changing?  This would help.

---

### Post by mistypotato on 2009-02-20
The reason I can't rememeber is because I was probably in the wrong directory and didnt realize I was making changes where I actually was.

Here is the actual permissions to that same folder on another Ubuntu 8.10 machine sitting right next to it...

drwxr-xr-x  16 root root 12288 2009-02-11 10:28 lib

So, I wonder if it's important to give that folder the same permissions on my server?

What would be very helpful is a command to list files changed (permissions anyway) in the last hour to hour and a half.

**AND - a utility that scans all files and directory permissions for obvious no-no's**

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> The reason I can't rememeber is because I was probably in the wrong directory and didnt realize I was making changes where I actually was.

Here is the actual permissions to that same folder on another Ubuntu 8.10 machine sitting right next to it...

drwxr-xr-x  16 root root 12288 2009-02-11 10:28 lib

So, I wonder if it's important to give that folder the same permissions on my server?

What would be very helpful is a command to list files changed (permissions anyway) in the last hour to hour and a half.

Have you looked in the syslog to see? (under system - administration) There may be an entry there, but if not then I don't know what to tell you.  As I said when I get a machine in that is messed up I usually run the recovery and go on.

---

### Post by mistypotato on 2009-02-20
SUCCESS !!!!!!!!!


WOOOO HOOOO !!!!


it WAS the permissions on the lib folder.


I just had to chmod it back to 755/


I'm giving Ubuntu a BIG hug   :p

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> SUCCESS !!!!!!!!!


WOOOO HOOOO !!!!


it WAS the permissions on the lib folder.


I just had to chmod it back to 755/


I'm giving Ubuntu a BIG hug   :p

Congrats.

You are the lucky one.  A lot of times people do not remember what they changed and where.  Pat yourself on the back.  Have fun with Ubuntu.

---

### Post by mistypotato on 2009-02-20
PerryG,
thanks for the assist.

Your recommendation to press ESC while booting got me where I needed to be.


THANKS !

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> PerryG,
thanks for the assist.

Your recommendation to press ESC while booting got me where I needed to be.


THANKS !

You are very welcome.

Enjoy Ubuntu.  It is sooooo  Cooool!

---

### Post by mistypotato on 2009-02-20
Hey Perry,

Ubuntu needs a "File Checker" that comes with ubuntu that will scan all critical system files for proper permissions and so forth.

this could be a lifesaver for many.

It could scan for files that **usually** have certain permissions and ownership / execute characteristics and just display a list of files that fall outside the "norm"

it should be called.....ummmmm..the POTATO scanner. :p

What do you think?

---

### Post by Perryg on 2009-02-20
> **mistypotato said:**
> Hey Perry,

Ubuntu needs a "File Checker" that comes with ubuntu that will scan all critical system files for proper permissions and so forth.

this could be a lifesaver for many.

It could scan for files that **usually** have certain permissions and ownership / execute characteristics and just display a list of files that fall outside the "norm"

it should be called.....ummmmm..the POTATO scanner. :p

What do you think?

Oh Man!  Potato scanner.  Sounds like you should write the script to do that.  I know it can be done.

---

