---
title: "Umask for shared folders"
date: 2010-02-06
forum: Security
---

### Post by emma_peel on 2010-02-06
Hello.

Quite a common question, but did not google a solution after a couple of days.

I want to share a folder, and I want everybody with access to the folder (managed by groups) to be able to add, modify and delete files. All files of the folder. So someone should be able to delete a file dropped by someone else. That means that any new created files or folders should have a specific authorization status, like 661.

I guess ACLs should do the job ... but I'm still thinking a simple solution could exist.

Does anybody has an idea ?

Thank you in advance for your help !

---

### Post by rookcifer on 2010-02-06
```
setfacl -d -m mask:007 /path/to/shared/folder
```

That will allow the GROUP all permissions to newly created files in that folder.  If you want to also include sub-folders within that directory, be sure to add the **-R** flag to the above command.

Now, you need to make sure the right group is assigned to the directory:

```
chgrp <group name> /path/to/shared/folder

```

Then set sgid bit:

```
chmod g+s /path/to/shared/folder
```

---

### Post by falconindy on 2010-02-06
In order for the above to work, you'll need to add 'acl' to that partition's options in /etc/fstab.

---

### Post by emma_peel on 2010-02-07
Excellent !! Thank you both of you for the help. This is precisely what I wanted to do !! :guitar:

And for the fstab, that's right, if the option is not added, the following error message is displayed :

```
emma@box:/$ setfacl -d -m mask:007 /path/to/shared/folder
setfacl: /path/to/shared/folder: Operation not supported

```

Thank's again.

---

### Post by tanoloco on 2010-02-19
I hope not to be wrong in saying that if you don't want to edit /etc/fstab file,
which is not so easy and you can create yourself many troubles,
you can always remount the partition in which the folder is contained with acl specified

```
sudo mount -o remount,acl /partition_containing_your_folder
```At least it worked for me :)

Cheers

---

