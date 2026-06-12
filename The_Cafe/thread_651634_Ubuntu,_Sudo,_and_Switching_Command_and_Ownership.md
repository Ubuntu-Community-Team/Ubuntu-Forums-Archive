---
title: "Ubuntu, Sudo, and Switching Command and Ownership"
date: 2007-12-27
forum: The Cafe
---

### Post by P235 on 2007-12-27
&#65279;I have an idea that I wish to share and hopefully my thoughts will be communicated properly with minimal confusion.

It's my understanding that users of Ubuntu, in order to complete administrative tasks, need to use the sudo command in order to temporarily exercise root like powers. By using the sudo command, users avoid logging into the computer under a root account and all of the potential pitfalls that entail. For instance, users may forget that they are still logged into their root accounts and leave themselves vulnerable to attacks and/or serious command typo errors.

Now here's what I'm thinking: Can a user have a 'sudo'-like command without the administrative properties which involves specified users who are not associated with the admin group? For instance, there is one user named Jack, who has a shadow account named Jill. Jack wishes to use this 'sudo'-like command to quickly log into Jill's account while remaining logged in as Jack. In doing so, he moves his files into Jill's account, alters these files so that only Jill can read, write, and execute them, and then logs off as Jill. In doing so, even if Jack forgot to log off from the computer, passersby still cannot access Jack's protected files as they are locked away in Jill's account and the permissions of Jack's files belong to Jill. Further, I'm imagining that neither Jack nor Jill are associated with the admin group. Thus, even if Jack forgot to log off from his computer, passersby will be unable to even contemplate using sudo.

In a practical sense, the users involved would not be Jack and Jill, but maybe Jack and a user account named 'Jack's QuickSafe'. The main idea being that the user Jack will be able to quickly insert or access his files in the 'QuickSafe' user account with the 'sudo'-like command, or by double clicking an icon and providing a password, without being involved in the admin group. I imagine this would be achieved by associating two accounts together through this 'sudo'-like command without actually using sudo powers. Jack may even further protect his files by encrypting them in the 'QuickSafe' user account if he so wishes, as 'QuickSafe' is simply another user account which exists to obstruct anyone from accessing them too easily under Jack's account.

In search of a method to achieve the effect of the idea above, I did try to use su. Unfortunately, and probably due to my own ignorance, su did not turn out to be the answer as moving a file from one account to another was not a permitted action. From an account without an association with the admin group, there was no way I could move a file owned by one user into the home of another user. Then again, Linux is known to be a safer OS because of its use of file permissions, so I suppose my inability to put my idea into practice is reassuring. However, my idea involves associating only two users. I do not mean to encroach - and possibly ruin - file permissions, one of the pillars of the OS. My idea relies upon file permissions anyway!

Ultimately, the idea of a 'QuickSafe' would be simple to perform and easy to understand and the tasks associated with a user in the admin group - in theory - would be reduced even further.  I think the goal would be to have ordinary users functioning without admin group powers enjoying the most secure, private Linux OS imaginable, yes?

In any event, any ideas? Is my idea clearly insane?

---

### Post by Dngrsone on 2007-12-27
Look at  [FONT="Fixedsys"]su *username*[/FONT]

---

### Post by nowshining on 2007-12-27
sudo nautilus

gksudo nautilus

sudo mv /home/username/file /home/username/file

also cp works

cp is copy
mv is move and both u can when copying into another folder or place specify a diff. name than the original.

then u'll need to chmod the desired UID or whatever numbers,

going thru nautilus lets u do it the graphical way - that way u can right click - properties and change em' that way...

u can also

gksudo nautilus

u can do a menu item as well with the command gksudo nautilus

on gnome-looks.org there is a script under nautilus that allows a right-click - scripts - open current folder in nautilus and as root.

---

### Post by nowshining on 2007-12-27
oh and in nautilus

right-click in browser mode on the desired folder and click open in new windows :P i have root as defualt browser, but not in my account.

U cannot move files onto the desktop due to permission but only between any nautilus folders open via root. :P

---

### Post by P235 on 2007-12-29
Thanks for the posts.  Dngrsone, I don't think you can use the 'su' command to move files between two users when both do not have admin group permissions.  

Also, thanks to nowshining for those suggestions, but the idea is to avoid using 'sudo'.

---

### Post by bigbearomaha on 2007-12-29
you want to avoid sudo, then activate root and set login to allow admin login.

Big Bear

---

