---
title: "Chmod permissions"
date: 2016-05-01
forum: Server Platforms
---

### Post by kambiz2 on 2016-05-01
Hi,
There is a thing that I can't understand.

I've got Ebn folder with this permissions:

[IMG]http://www.tepui.cat/foro/permis1.png[/IMG]

And inside this folder this:

[IMG]http://www.tepui.cat/foro/permis2.png[/IMG]

I'd like to change the permission of all the folder. For this I do:

[IMG]http://www.tepui.cat/foro/permis3.png[/IMG]

But an error says operation denied

My question is: is I'm user ebnadmin, and ebnadmin has all permissions, why ebnadmin cannot change permissions?

Thanks

---

### Post by darkod on 2016-05-01
Sometimes you still need to use sudo in front of chmod even when the user running the command owns the folder. Try with sudo.

---

### Post by kambiz2 on 2016-05-01
Hi,
With sudo works fine, but I need to use it without sudo. I explain. I'm programming a script in Delphi. I need to copy all the information of our costumers from Windows to Ubuntu Server. 
Every costumer has his own folder. 
The program I've written creates some folders, and automatically copy some files to one of this folders.
Till here no problem. 
What I need now, is delete all permission for others. Delphi has a lot of components to work with FTP, but I can't do us root. 

Thanks

---

### Post by nerdtron on 2016-05-02
> **kambiz2 said:**
> Hi,
There is a thing that I can't understand.

I've got Ebn folder with this permissions:

[IMG]http://www.tepui.cat/foro/permis1.png[/IMG]

And inside this folder this:

[IMG]http://www.tepui.cat/foro/permis2.png[/IMG]

I'd like to change the permission of all the folder. For this I do:

[IMG]http://www.tepui.cat/foro/permis3.png[/IMG]

But an error says operation denied

My question is: is I'm user ebnadmin, and ebnadmin has all permissions, why ebnadmin cannot change permissions?

Thanks

Not all files are owned by ebnadmin. And also, the "+" sign indicates that you have setup ACL (access control list) for this folder and all files inside it. Who manages this folder and who set the permission beforehand?

---

### Post by kambiz2 on 2016-05-03
Thanks nedron for your answer and I apologize for the delay, I didn't see it.
I'm a developer Windows and it's my first adventure in Ubuntu. I didn't notice about '+', now I have been reading about it.
I think this is because some days ago I execute the follow commands:
- sudo chmod g+w /srv/samba
- sudo chmod g+s /srv/samba

---

### Post by nerdtron on 2016-05-03
> **kambiz2 said:**
> Thanks nedron for your answer and I apologize for the delay, I didn't see it.
I'm a developer Windows and it's my first adventure in Ubuntu. I didn't notice about '+', now I have been reading about it.
I think this is because some days ago I execute the follow commands:
- sudo chmod g+w /srv/samba
- sudo chmod g+s /srv/samba

You probably did this so that everything created inside the /srv/samba  will be owned by the group "ebnadmin", right? But some files are owned by user "Adminsrator". Although all the group permissions belong to ebndadmin, you cannot change the permissions of files/folder not owned ebnadmin. Hence, you'll get operation denied it you want to change the permissions of files owned by "Administrator.

---

