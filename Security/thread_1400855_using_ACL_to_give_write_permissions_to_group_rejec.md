---
title: "using ACL to give write permissions to group rejects one of the members"
date: 2010-02-07
forum: Security
---

### Post by dodonpalex on 2010-02-07
I'm using access control lists to specify access to a git repository on my local machine. I have created a group called "git" which currently contains three users. These are the commands I used to create the folder:

sudo mkdir folder
sudo chmod 700 folder
sudo setfacl -Rm group:git:rwx folder

The output of ls -l is now:
drwxrwx---+ 7 root root 4.0K 2010-02-07 18:00 folder

And the output of getfacl is:
# file: folder/
# owner: root
# group: root
user::rwx
group::---
group:git:rwx
mask::rwx
other::---

After those commands the two newly created users can access the folder however when I try to change to or list the contents of the folder as my normal user I get a permissions denied.

Output if id on one of the new users:
uid=1001(annika) gid=111(ssh) groups=111(ssh),1001(git)

Output of id on my normal user:
uid=1000(alex) gid=1000(alex) groups=1000(alex),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(fuse),108(lpadmin),111(ssh),114(admin),123(sambashare),127(kqemu),1001(git)

I don't get why my user "alex" can't access the folder, it's a member of the "git" group but still it get a "permission denied" error message. I don't what to add specific access for any users other than adding them to the group git.

---

### Post by amac777 on 2010-02-07
This may not have anything to do with it, but did you logout/login again as Alex to make sure the new group settings for alex take effect?

---

### Post by dodonpalex on 2010-02-07
That solved it, thanks.

---

