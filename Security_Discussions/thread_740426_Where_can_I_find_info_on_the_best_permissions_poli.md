---
title: "Where can I find info on the best permissions policy for files folders and drives?"
date: 2008-03-30
forum: Security Discussions
---

### Post by 3pinner on 2008-03-30
Hello,
As a new user, I am just figuring out the permissions policies for files directories and drives.
I'd like to know where the best source of info is in figuring out the best policy to use (in other words - which groups to allow etc)
Thanks!

---

### Post by brian_p on 2008-04-02
> **3pinner said:**
> Hello,
As a new user, I am just figuring out the permissions policies for files directories and drives.
I'd like to know where the best source of info is in figuring out the best policy to use (in other words - which groups to allow etc)
Thanks!

There's tons of information about this on the net. Relate this to how Ubuntu sets file and group permissions in, for example, /usr/bin or /var or /etc and ask yourself why it is done that way for particular files. For instance, why is /etc/passwd readable by anyone but /etc/shadow isn't?

You would be very unwise to change any system files. You can do what you want in your /home directory but even there doing so may produce unwanted side effects.

Brian.

---

### Post by 3pinner on 2008-04-02
thanks for the reply Brian, I have no interest in changing permissions for system files, but I do want to understand Linux permissions.

I'll give you an example.
I recently used gparted to make a partition out of some unformatted disk space.
When I got done creating the partition, formatting it, and mounting it, only root could access it. I posted a question on how to change that (its going to be used to store backups) and that just spawned an interest in understanding how Ubuntu sets default permissions on a directory or a file; and what is the best policy when changing them so other users can access them.

I have had similar issues when downloading sofware that I want to install with my admin account, and make available to me when logged in as a user.

With windows, I would download a file ( say some software)  logged in as a user, relog in as admin, go to my user desktop, grab the software, install it, and it was available to me both as admin and as user.
With Ubuntu I can't so that. If I download somethng as user, log on as admin, go to my user desktop and drag it to the admin desktop, I can't even open it as admin, because the owner is set as my user account.
I just want to understand how that works.

---

### Post by hyper_ch on 2008-04-03
you don't download software like you do in Windows...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by vanadium on 2008-04-03
You just need to ask yourself who is allowed to do what with a file. It is your decision. "who", that is the user that owns the file, the group that owns the file, or any other people. "what" is reading the file (r), writing to the file (w) or executing the file (x). If you set all permissions open, then any user can do anything with the file. If you want to be more restrictive, you have to disable rights for the groups of people you do not want to have these rights. Essentially, it is your call and your responsibility and your freedom to decide on file permissions.

For your hard disk example, indeed only root is allowed to install fixed storage space. The most powerful way to make the storage space available to users on the system is to create directories on that hard disk, and change the owners of the directories to the respective users. With a symbolic link in the users directories, you can provide for convenient access to the hard disk from within the users home directory. By default, the user and group can do anything in his own dir (permissions 775), and others can read, but you might make that more restrictive if you want, for example to make sure that users cannot see each others files.

For installing programs after you dowloaded them - however, a regular Ubuntu user should, as hyper_ch pointed out, rarely need this - you should never log in as an administrator, but temporarily act as root by using the sudo command.

---

