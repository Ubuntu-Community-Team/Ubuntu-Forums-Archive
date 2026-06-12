---
title: "user is not in the sudoers file"
date: 2011-03-15
forum: Security
---

### Post by richwils on 2011-03-15
This is strange.  I am the only user and could sudo just fine with no problems.  Suddenly I am not in the sudoers file.  I am not sure how to recover from this.   I have no grub screen at bootup, so I can't boot into single user.  I think I am going to have to boot a live version of ubuntu to start with.  Is that right?  What's next after that?

Also, how could this happen,  I haven't touched the sudoers file or added users or anything like that (well not that I am aware of)  I am a little concerned that this may be the result of someone breaking in?  Would this be a likely symptom?  

Help appreciated!

---

### Post by Dave_L on 2011-03-15
This is my (Ubuntu 10.04) /etc/sudoers file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

When you say that you're not in the sudoers file, do you mean that the "admin" group is not in that file?

Or do you mean that your user is no longer in the "admin" group? You can determine that by examining the file /etc/group.

If I recall correctly, you can get the grub menu to appear by holding down the shift key during boot.

In any case, booting with the Live CD and checking the files /etc/sudoers and /etc/group won't hurt anything.

---

### Post by wojox on 2011-03-15
[Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by richwils on 2011-03-16
Dave L, sorry, I should have mentioned that I got an error message "USER is not in the sudoers file. This incident will be reported." whenever I tried to sudo  


> **wojox said:**
> [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

Thanks very much indeed,  I managed to fix it using the linked article by going into recovery mode and doing "adduser username admin".  Job done! 

I'm still a bit concerned as to how it happened in the first place. I'm feeling paranoid that they're after me and hacking my system, so to speak.  

Any ideas?

---

### Post by hekastos on 2013-03-11
I had the same prob. , because I used usermod without option -a, I fixed it by booting in recovery mode dropping into root console and 
> # mount -o rw,remount /
to get it writable
> usermod -a -G sudo username
to get me back into sudoers list
gl to all searching for this like me...

---

### Post by oldos2er on 2013-03-11
Old thread closed.

---

