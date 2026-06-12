---
title: "Directory Structure copy"
date: 2011-03-22
forum: Server Platforms
---

### Post by Vishal Agarwal on 2011-03-22
Hi,
I have one user in home directory. with that I want the following.

1. The same directory structure I want to copy for one other user.
2. Same file structure of zero bytes (blank files) I want to create like creating files with touch command.

any suggestions are welcome.

Thanks,
Vishal Agarwal

---

### Post by volkswagner on 2011-03-22
> **Vishal Agarwal said:**
> Hi,
I have one user in home directory. with that I want the following.

1. The same directory structure I want to copy for one other user.
2. Same file structure of zero bytes (blank files) I want to create like creating files with touch command.

any suggestions are welcome.

Thanks,
Vishal Agarwal

I'm sure not just myself is wondering, why?

I you should create the user first (if not already added) with [adduser or useradd]("http://www.go2linux.org/useradd-vs-adduser") command of your choice (I prefer additional function of adduser).

```
sudo adduser newuser
```

You can then change to the home directory.

```
cd /home
```

Tar up the directory, untar and transfer it to new user directory.  
```
sudo tar cf - userfolder | (cd /home/newuser && tar xfp - )
```

The copied files will now have the same ownership permissions as previous owner.  You will need to fix that.

```
sudo chown -R newuser:newuser /home/newuser 
```

---

### Post by SeijiSensei on 2011-03-22
When new users are created, their home directory structure is created by copying the files and directories in /etc/skel.  If you modify /etc/skel to match the user you want to replicate, new users will get the same structure.

The default files in /etc/skel are all "hidden," so you'll need to use "ls -a" to see them.  That doesn't mean you can't create normal items as well.  For instance, on IMAP servers I add a "mail" subdirectory to /etc/skel and tell Dovecot to put any user mail folders in that directory.

---

### Post by Vishal Agarwal on 2011-03-22
Thanks a Lot.

I need only one user to be created with the file structure with the other one, not for all.

I hope I will be able to do it now easily.

Thanks Again.

---

