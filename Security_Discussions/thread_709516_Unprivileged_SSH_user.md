---
title: "Unprivileged SSH user"
date: 2008-02-27
forum: Security Discussions
---

### Post by benpage26 on 2008-02-27
Hello, I searched the forums for what exactly an unprivileged user is and I couldn't find much info.

I want to make a Public SSH user that can ssh into my machine and only view files that i choose (IE the files inside my ~/public similar to my webserver) 

I also want a user that can do all the normal stuff my user can do (run programs and the like) but not use the sudo command or access any system files.  Can anyone give me any tips/HOWTOs on this?


One reason I am doing this is that I want to give others access to my files, but I don't have an external IP so a webserver will not work.  I have found that i can SSH to a machine that has an external IP and use port forwarding to 'borrow' that machines IP for a ssh connection.  Can a similar thing be achieved with an Apache server?

Thanks for any help you can offer me.

---

### Post by jeffus_il on 2008-02-27
Control the read access through regular file and folder permissions, read, write, execute ... 
A user who is not a member of the "admin" group will not be able to run sudo.
You can easily view files using a gui like thunar,nautilus,dolphin using sshfs running over ssh. It's lightweight, and is much easier to setup than Apache.

---

### Post by k_grdn on 2008-02-27
Hi,

Have you considered chrootssh patch or jailkit?

Regards,

k_grdn

---

### Post by benpage26 on 2008-02-27
> **jeffus_il said:**
> Control the read access through regular file and folder permissions, read, write, execute ... 
A user who is not a member of the "admin" group will not be able to run sudo.
You can easily view files using a gui like thunar,nautilus,dolphin using sshfs running over ssh. It's lightweight, and is much easier to setup than Apache.
Hello jeffus_il,
The setup of apache would have been to allow my friends and coworkers (who are non-linux users) access to my files.  Is sshfs usable by Windows?  I

I created a new unprivileged user sshguest, and it appeared that he could run sudo, (when i ran sudo it asked for my password and then let me run commands, will sudo always ask for a password?).  Is there a way of setting something on the sshguest user such as no reading/writing/executing except these few files, or would i have to change the permissions for every folder on my computer that i want root/admin access only to?


> **k_grdn said:**
> Hi,

Have you considered chrootssh patch or jailkit?
Regards,

k_grdn

Hello k_grdn,

I did look at jailkit, but it seemed like a roundabout way to do it, and its not really the system files that i don't want people touching, more my private files in my home drive



Thank you people.

---

### Post by jeffus_il on 2008-02-28
> Hello jeffus_il,
The setup of apache would have been to allow my friends and coworkers (who are non-linux users) access to my files.  Is sshfs usable by Windows? I think sshfs is not available on Windows, but you can access files using the ssh protocol using filezilla, a gui ftp and sftp (ssh ftp) client. The is also an ssh application called "Putty".

> I created a new unprivileged user sshguest, and it appeared that he could run sudo, (when i ran sudo it asked for my password and then let me run commands, will sudo always ask for a password?).  Is there a way of setting something on the sshguest user such as no reading/writing/executing except these few files, or would i have to change the permissions for every folder on my computer that i want root/admin access only to? No you don't have to change permissions of all files, you can use groups, if regular users are members of users, you can have a group guests for example, who do not have read permissions on the users group. you can change permissions of a whole directory tree with the command ```
chmod -R
``` which works recurively, an easy and quick command.

---

### Post by kevdog on 2008-02-29
ssh provides an executable shell -- so by its very nature you are introducing some possible security vulnerabilities.  I know apache can list files (through indexing).  FTP can provide indexing, downloading and uploading capabilities.  If you want to allow other users to run programs in the box I would suggest a chrooted environment (such as a jailkit), although this method is not exactly airtight.  File permissions work to limit access, but there is no way to stop users from installation of a program that would create vulnerabilities.

---

