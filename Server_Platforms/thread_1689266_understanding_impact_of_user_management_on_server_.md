---
title: "understanding impact of user management on server security"
date: 2011-02-16
forum: Server Platforms
---

### Post by Hawkoon on 2011-02-16
From what I understand, daemons (like mpd, daap, vsftpd) allow you to run them as a user other than the one starting them up to "improve" security. In what way exactly actually, and in which scenarios would it make a difference?

Background for my question is this: I configured client175 with the "run_as" option, but in order to get it to work I had to give r+x permissions for others on the application files, which feels wrong.

From the security point of view, my main concern is that it must not be possible to modify files served via mpd, daap and client175 (like tag editing, playlist deletion, all this must not be possible). So instead of messing with the "run_as" option, could I not achieve this simply by creating a second user on my server? First users owns all data files, which have read access for others, and the second user is the one logged in, running all the server apps? I should work, but perhaps I am compromising security by running several server apps with the same user?

Anyone who could shed some light?

Thanks,
~H

---

### Post by elico on 2011-02-16
there are couple of ways to make an application run as user.

the main concern about this option is not only but for most cases security.
the security feature in that is:
any application on the machine is actually doing things on the OS as a user and whatever that is allowed to the user that runs the application allowed to the application itself.

so if you have a user that have permissions as a member of a group to run delete or anything else on a file in the file system.
so if the let say "iptables"  command that managing the linux firewall can run using the user it's not good.
this is only one way but it's far more then just that.

in linux any hardware on the computer has a symbol on the file system.
so in the case a user can access a file that represents hardware device it means more then just "a file".

so now i hope you understand the meaning of the thing in one security perspective.

there is another mechanism other then the runas and it's called chroot.

this is a far more strict way of limiting an application.

most of the applications dont need more then just basic file system.
so using this idea you can create a folder on let say /var/chroot_postifx/
and link into this directory the basic FS and apps for the postfix application and as far as the application will run it has a root directory that the real place of it is  /var/chroot_postifx/ but the application sees this  directory as / means it cannot access /var/log/mail.log and in order for the application to access this file you will need to link this file into  /var/chroot_postifx/var/mail.log

this is a far more complex and far more secure way but have costs.

there is another way like in ftp and samba that the application must run as root user but the file system access to files is done as other user.

if you want the application to play the files in many cases you will need execution privileges but it's dosn't mean the file can be changed or erased.

hope it was something
 (im pretty tired now)

---

### Post by Hawkoon on 2011-02-17
That was very informative, thanks for taking the time, elico.
 
 It brings up some more questions.
 
 I understand the chroot idea. In the case of ftp, user access would be limited to what ever is inside their home directory.

But what about the rights of an application. Let's say a user somehow compromised my daap server and gains shell access (maybe that is even two different things?), he then would be limited to (or granted, depending how you look at it) the rights of the user running the daap service, and it would require a further exploit to do any harm to system if the daap user is "very unpriviledged"? Is this a correct understanding?

 You mention that chrooting an application has costs. Besides of some extra work to set it up, are there any other costs to bear in mind? Otherwise it would make sense to chroot every single service and link necessary outside files.
 
 > **elico said:**
> if you want the application to play the files in  many cases you will need execution privileges but it's dosn't mean the  file can be changed or erased.

 
 If you give read and execution rights to a data file, does that not increase the potential to abuse the file? I am obviously not an expert, so I don't know in what way exactly, but you allow the user more than just reading the file.

---

