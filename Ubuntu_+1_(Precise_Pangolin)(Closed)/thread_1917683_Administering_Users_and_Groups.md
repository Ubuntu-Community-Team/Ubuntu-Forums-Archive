---
title: "Administering Users and Groups"
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fballem on 2012-01-30
I must be showing my age.

In prior versions of ubuntu - such as 10.04, there was a very simple option, Users and Groups, that would allow me to setup groups and associate users to them, as well as being able to easily add users.

In 12.04, I do see an option to Add Users, but nothing about groups and nothing about being able to edit existing users. I don't know if this is due to Unity or Gnome 3, but either way, I would appreciate it if someone could tell me how to do this through a GUI please.

Thanks,

---

### Post by zika on 2012-01-30
> **fballem said:**
> I must be showing my age.

In prior versions of ubuntu - such as 10.04, there was a very simple option, Users and Groups, that would allow me to setup groups and associate users to them, as well as being able to easily add users.

In 12.04, I do see an option to Add Users, but nothing about groups and nothing about being able to edit existing users. I don't know if this is due to Unity or Gnome 3, but either way, I would appreciate it if someone could tell me how to do this through a GUI please.

Thanks,[http://askubuntu.com/questions/70076/wheres-admin-tools-gone-in-11-10](http://askubuntu.com/questions/70076/wheres-admin-tools-gone-in-11-10)

---

### Post by Derek Karpinski on 2012-01-30
I hope it comes back.
 
In the name of simplifying the OS, Ubuntu is forcing people to spend 30 min googling for a solution, or worse, forcing them to use a terminal to change settings.

---

### Post by jbicha on 2012-01-30
*cough* GNOME *cough*

Actually, I think most home users only need to be set as admin or non-admin which the new System Settings does very easily without cluttering it with a bunch of obscure Unix group names. Sysadmins have other ways to manage permissions for large, complex installations. Therefore, there isn't a bug to be fixed here :)

Or you can read the fine print on the AskUbuntu link which points out that you can just install gnome-system-tools to get the old users-admin tool back.

---

### Post by zika on 2012-01-31
> **Derek Karpinski said:**
> I hope it comes back.
 
In the name of simplifying the OS, Ubuntu is forcing people to spend 30  min googling for a solution, or worse, forcing them to use a terminal to  change settings.
30 minutes! Slow connection?
> **Derek Karpinski said:**
> or worse, forcing them to use a terminal to change settings.CLI is the only real way of solving matters. GUI is just fancy want-to-be-a-tool... ;)

---

### Post by fballem on 2012-01-31
> **zika said:**
> [http://askubuntu.com/questions/70076/wheres-admin-tools-gone-in-11-10](http://askubuntu.com/questions/70076/wheres-admin-tools-gone-in-11-10)

Thanks!

---

### Post by grahammechanical on 2012-01-31
Do not forget to click Unlock. You can then click on the user name, account type, password etc., to get the option to change them.

Personally, I find this method less intimidating. I am with jbitcha on this.

Regards.

---

### Post by Derek Karpinski on 2012-01-31
> **zika said:**
> 30 minutes! Slow connection?
CLI is the only real way of solving matters. GUI is just fancy want-to-be-a-tool... ;)
 
I'm not arguing.  But now users are forced to the CLI to do this.
 
I once borked my system because I forgot to append a new group to myself......I instead made the new group my ONLY group.  Recovering from that was almost impossible without admin rights.
 
So, which is easier for new people, a GUI that has a lock, or missing the '-a' flag on usermod?
 
Sure, I learned from my mistake, and I continue to use ubuntu, and learn and love the command line.
 
But, a new user that typed in the wrong command in CLI....90% chance they're gone for good.
 
Point is, dumbing it down forces many new users to enter commands in Terminal which they don't fully understand.  I know.........I did it.

---

### Post by fballem on 2012-01-31
The best solution would be to put the right program (the gui mentioned above whose name is escaping me at the moment) by default instead of the very limited User tool that is there now.

Fortunately, the gui tool can be installed through the Software Center and once installed, it's pretty easy to use.

---

### Post by ml2mst on 2012-02-02
The solution is installing the package **gnome-system-tools**.

After rebooting I was finally able to manage usergroups by typing users in the dasher and finaly clicking on the icon users and groups.

---

