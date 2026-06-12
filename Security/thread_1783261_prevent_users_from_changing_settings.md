---
title: "prevent users from changing settings"
date: 2011-06-15
forum: Security
---

### Post by cmwhidmore on 2011-06-15
I am administrating a system with about 40 or 50 users, and we recently jumped ship from windows to ubuntu. Most of my users are getting along fine, but it seems every few days, i have to help someone who accidentally changed something, and now their account (or more rarely, the machine) is unusable, and has to be reset. 

I know configuring /etc/sudoers is a huge step toward fixing my problem, but that still will not completely solve it. What I would like to do is prevent users from making ANY changes to the system (aside from their work files and the like), including themes, icons, desktop, background, etc.

Any suggestions?

---

### Post by ajgreeny on 2011-06-15
If the users are not members of admin group they should not be able to make any changes to the system other than those settings in their own home, so make sure that users other than yourself are only desktop users, not admin, and keep your admin password secret from them.

The only way I can think of to ensure that they can not change any settings to themes, wallpaper etc etc is to try making their users hidden ~/.gconf folder and files owned by root, though I am not even sure this is possible in a users home folder.  It should be easy enough to try it with command ```
sudo chown root:root /home/*<username>*/.gconf
```but don't blame me if it all goes to worms.

Thinking about it while answering, it may be easier to use the chmod command, and just remove the write permissions from that folder by ```
sudo chmod 555 /home/*<username>*/.gconf
```meaning only with root permissions could you change anything.

Once again, I am thinking as I write here, so perhaps it is more sensible to await other answers; there may be ways that I have not yet even thought about.  Food for thought, however.

---

### Post by cmwhidmore on 2011-06-16
That sounds like it might work. So what if it breaks a few small features (like, say.. a recent files list or something..)? They brought it on themselves. If you don't know what you are changing, DONT touch it. Since they insist on messing up my system, I think it's only fair.

And I think your approach might be best if you combine the two options...
chown everything as root (except their files), and then chmod 755... still allows root to change things if needed, while write protecting the settings and stuff...

Thanks so much- i'll try this when i go in tomorrow, and let you know how it works out.

---

