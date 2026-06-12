---
title: "Folder permissions and groups management."
date: 2011-01-10
forum: Security
---

### Post by lucacerone on 2011-01-10
Dear all,
I've a machine with Ubuntu 10.04 installed (though as far as I understand
this is more a Unix/Linux admin question than a specific Ubuntu one).

On my machine I have three users A, B and C, belonging to different
groups gA, gB, and gC defined as follows:
gA = {A,B,C}
gB= {A,B}
gC= {A,C}

I need some help in setting up the permissions for these user.

Say I create a folder /project1

I set the owner of /project1 to be A and the main group to be gB for example.

I give permissions for reading, writing and execution for the owner
and for the group. No permissions are allowed for all other users (not even reading).

Till here everything it's ok. The problem arises when an user writes some files into the /project1 folder.

Since gB is not the main group for A, every new file is created as owned by A but belonging to the group A (in Ubuntu the main group has the same name as the user).
The same it happens for user B.

So the question is: is it possible to create /project1
so that every new files or directories created in that directory is automatically owned by who created the file and belongs to the group gB?

If I go in project1 as user A and create a new file using 
> echo "test" > test.txt
the file test.txt has reading permission for all, writing for user and nothing else.
I would like the file test.txt to have permissions like: rwxrwx---

I read something about a flag "s" for directories to use with chmod,
and setting up the umask for a user but:
1) in the first case I couldn't manage to make it work properly,
2) umask change the behaviour system-wide and I'd just would like
have this behaviour in specific folders.

Hope some of you can help me, I think it's certainly possible to have such a feature, but I couldn't figure it out how.

Thanks a lot in advance,
Cheers, -Luca

---

### Post by mikewhatever on 2011-01-10
You could try setting up a local shared directory for the three users. Check out the howto below.
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)

---

### Post by lucacerone on 2011-01-10
Thanks a lot,
this is just what I was looking for 
and worked grand!!!
Cheers, -Luca

---

### Post by lucacerone on 2011-01-10
I just summarize the steps in the article:

1) install acl
2) mount your disk with acl option (modifying the file /etc/fstab if needed)
for example:
> UUID=b8c490d0-0547-4e1f-b052-7130bacfd936 /home ext4 defaults,**acl** 0 2
3) restart your computer
4) create folder project1 and assign permissions:
```
 mkdir project1
 chown owner:group project1
 chmod u+wrx project1
 chmod g+wrxs project1
 chmod o-rwx project1
 setfacl -d -m u::rwx,g::rwx,o::--- project1

```
After the setfacl command every user in the group
will be able to modify files in project1. Newly created
files will inherit the permissions from project1.

Thanks again for the suggestion,
Cheers, -Luca

---

