---
title: "LTSP - setting up large number of users"
date: 2012-07-04
forum: Server Platforms
---

### Post by ricmat on 2012-07-04
I'm setting up a school network with LTSP for 40+ computers, and about 170 users.  I'm using Edubuntu 12.04, defaulting to the Gnome desktop.

I have not found an easy way to en-masse create a large number of accounts where the default menus, desktop icons, Firefox bookmarks, etc. are predefined.

What I have tried:

1.  Set up a defaultaccount user, and copy to /etc/skel.  This works as I would like except it is very time consuming to manually create 170 users, and manually copy all 170 passwords to another document so I can give it to the teachers, etc.  This just isn't practical, there must be an easier way.

Also, whenever I install some new "admin only" sort of software, it appears as a menu item in all the student accounts as well.  So I need to go back and remove it from all 170 accounts manually.  

2.  I've also done this.   Use a school spreadsheet with the students' names, which automatically creates a password based on the name, save as a CSV file, and then use the newusers command with the CSV file to en-masse load the system.

This works great to create the accounts with correct passwords (and I have a record of the password from the spreadsheet), except that none of these users get the default menus, desktop, etc. from the  /etc/skel folder.  I'm not sure where the template is that's supplying the standard defaults instead of the /etc/skel defaults.

3.  I've tried Sabayon profile editor (on previous versions of Edubuntu) but it seemed to have problems, and in any case has disappeared in 12.04.

4.  I've tried the Edubuntu menu editor and profile editor on previous versions, but had problems.  And in any case, it doesn't affect desktop icons or browser bookmarks, etc.

If there is no way to create large blocks of users with custom menus and icons, it seems to me that it is generally speaking a large impediment to the acceptance of LTSP in an environment with lots of users.  And isn't that the purpose of LTSP to begin with?  Lots of users?

If newusers could be modified to use the template already stored in /etc/skel, I think it would meet most of my needs (except the post facto addition of menu items after the accounts are created).

Any ideas?  Anybody?

Thanks in advance.

---

### Post by jumpyjester on 2012-07-04
Hi Ricmat,

you try using the adduser command in terminal it should be quicker it should also allow you to create a mass number of accounts when you seperate each user name by a space this can be done by pasting as well.

hope this helps

---

### Post by ricmat on 2012-07-04
> **jumpyjester said:**
> Hi Ricmat,

you try using the adduser command in terminal it should be quicker it should also allow you to create a mass number of accounts when you seperate each user name by a space this can be done by pasting as well.

hope this helps
Thanks jumpyjester - but this isn't any better than adding users with the built-in GUI tool.  I would still need to manually add the usernames and passwords, 170+ times as in my item 1.  

The newusers approach is nice in that it works with a spreadsheet, literally invoke it once and all 170 accounts and passwords are created at once.  But with the wrong menus and icons.  I can't believe that there isn't some easy way to do both.  I have 170 accounts.  What about those people who need to add thousands at a time? 

Maybe others have found a better way.  I'm still looking.

---

### Post by elico on 2012-07-04
> **ricmat said:**
> Thanks jumpyjester - but this isn't any better than adding users with the built-in GUI tool.  I would still need to manually add the usernames and passwords, 170+ times as in my item 1.  

The newusers approach is nice in that it works with a spreadsheet, literally invoke it once and all 170 accounts and passwords are created at once.  But with the wrong menus and icons.  I can't believe that there isn't some easy way to do both.  I have 170 accounts.  What about those people who need to add thousands at a time? 

Maybe others have found a better way.  I'm still looking.
you can use a simple script to add all these users and a single or more passwords for a set of users.
try to look at:
[http://www.cyberciti.biz/tips/linux-how-to-create-multiple-users-accounts-in-batch.html](http://www.cyberciti.biz/tips/linux-how-to-create-multiple-users-accounts-in-batch.html)

good luck

---

### Post by georgehuang on 2012-10-02
Hi,

After I changed the password settings to allow for very short passwords, I created this script to create 40 users in one shot.  They are cl00 to cl39 with the password being the same as the username.

I couldn't figure out how to define their real names, however.  I eventually fixed that but didn't quite save the code...

Hope this helps.

George H.



#!/bin/bash

addgroup clients

for i in {0..3}
do

  for j in {0..9}

  do

    echo "creating user cl$i$j"

    useradd -d /home/cl$i$j -c "CL$i$j" -m cl$i$j

    passwd cl$i$j

    chmod 750 /home/cl$i$j

    adduser cl$i$j clients

    echo "---"

  done

done

---

