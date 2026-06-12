---
title: "chmod File Permissions UGH!"
date: 2012-03-12
forum: Security
---

### Post by Hank_The_Dog on 2012-03-12
I know this might be a bit repetitive, but I am just not getting this.

I have read and re-read the [chmod]("https://help.ubuntu.com/community/FilePermissions") guide over and over.

I understand the numbering system, and the letters.

My question is:

If I had the directory "/dir/" 
And I had a user named "fakeuser"
And I had a super-user named "sudouser"

My goal is to only allow 'fakeuser' to access '/dir/' and **NO** other files/folders


In other words...

basically I would like to create a user account that can only access a single folder (and its contents -R)

Any help would be great!

Thanks

---

### Post by Morbius1 on 2012-03-12
I may be taking your requirement too literally but I don't think you can do what you want.

First, by definition "fakeuser" would have access to at least two directories: /home/fakeuser and /dir

Second, even if you could pull this off, "fakeuser" wouldn't be able to do much since he wouldn't have access to any applications or other resources on the machine.

You can make it so that "fakeuser" has access to his home directory and no others by changing permissions on every other users' home directory:
```
sudo chmod 0770 /home/morbius
```"morbius" would have access to his home directory but not anyone else.

But you can't do this sort of thing system wide.

---

