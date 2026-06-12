---
title: "Restricted access"
date: 2009-06-18
forum: Security
---

### Post by dunk on 2009-06-18
Hi All.

I want to know if there is a simple way I can lock down a few of our users PCs so that they can only really access the following:

Firefox
Evolution
Open Office

I've had a bit of a hunt around and not found anything particularly helpful. I'm sure someone must've done this somewhere.

Cheers all :)

Dunk

---

### Post by dunk on 2009-06-18
Ok, I've worked out how to edit the Menus to only show what I select, what I want to do now is just stop any of the users being able to edit the menus themselves.

Most of the users are not especially computer savvy anyway. But I just want it locked down for peace of mind...

Cheers

Dunk

---

### Post by munky99999 on 2009-06-18
Make a new user account whose privileges are what fits your needs?

---

### Post by Augsburg on 2009-06-18
Here's an Idea:

Create a group in /etc/group called, say, limitedAccess

Then, create a totally unprivelaged new user and add it to that group.

Then all you have to do is allow users of that group to run those programs, using the chown command.

---

### Post by bodhi.zazen on 2009-06-18
The easiest way, IMO, on Ubuntu, is to use AppArmor.

---

### Post by HermanAB on 2009-06-18
You can edit the /etc/sudoers file.

---

### Post by Lucky. on 2009-06-18
> **Augsburg said:**
> Here's an Idea:

Create a group in /etc/group called, say, limitedAccess

Then, create a totally unprivelaged new user and add it to that group.

Then all you have to do is allow users of that group to run those programs, using the chown command.

This intrigues me, but I don't understand...

Chown would change the owner of a file, but that doesn't have anything to do with the group class, does it?

Most likely (default), the "Group" and "Others" classes would likely still have read/execute rights on programs.  If you only ran chown (and left the rest as be), you wouldn't be limiting anybody at all.  However if you strip the "Group" and "Others" class permissions down to nothing, then only the owner could run the programs.  The owner isn't a group though, so I don't see how this would work for multiple people.

I'm sorry to be so critical.  I really want this to work, but it doesn't make sense to me at all.

In detail, what are the commands to make this happen, step by step?

---

### Post by bodhi.zazen on 2009-06-18
[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

sudo chown root.limited_users /usr/bin/firefox
sudo chmod 750 /usr/bin/firefox

now only root and members of the group limited_users can run firefox.

If you need finer grain control, use acl (access control lists).

Take care though as firefox is not the best example as it is a link ;)

I am not sure what happens when firefox is updated, you may need to manually set permissions.

---

### Post by Lucky. on 2009-06-18
> **bodhi.zazen said:**
> 
sudo chown root.limited_users /usr/bin/firefox
sudo chmod 750 /usr/bin/firefox

now only root and members of the group limited_users can run firefox.


Ahh, that was the piece I was missing.  I've always used chgrp...didn't know you could use chown to change the group as well.

Thanks!

---

