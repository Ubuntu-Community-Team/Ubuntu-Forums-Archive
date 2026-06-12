---
title: "Set independant user permissions on files and folders"
date: 2012-05-07
forum: Security
---

### Post by zaR2ro1zie on 2012-05-07
Hello,

I'm in this case:
3 users: 

- John (u)
- Pierre (u)
- Tom (admin/su)

2 folders:
- John's folder
- Public folder

The thing I want to do is give John the rights to r/w in his folder
And give Pierre read access but not write.

To the public folder, both have read acces, none can write.

How can this be easily achieved like in Windows?

---

### Post by codemaniac on 2012-05-07
Dear tompirlet ,
 
In unix every file and directory has its pwn set of tight security policies .
You need to understand the group concep also along with the user .here is tutorial for you .
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)
 
In your case , you have not mentioned whch user belongs to which group .
You need to know if john and Pierre belongs to the same group or different ones to set permissions for the first scenerio.
 
For the second scenerio 
```
chmod -R 444 Public folder
```
will give read permissions to everyone .

---

### Post by zaR2ro1zie on 2012-05-07
> **codemaniac said:**
> Dear tompirlet ,
 
In unix every file and directory has its pwn set of tight security policies .
You need to understand the group concep also along with the user .here is tutorial for you .
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)
 
In your case , you have not mentioned whch user belongs to which group .
You need to know if john and Pierre belongs to the same group or different ones to set permissions for the first scenerio.
 
For the second scenerio 
```
chmod -R 444 Public folder
```
will give read permissions to everyone .

So, if I want to do this, I have to create 2 different groups for the users?

---

### Post by codemaniac on 2012-05-07
It depends upon your security and access control requirement basically ,say John is a part of development team and Pierre belongs to the QA team .in this scenario you might not want placing them both in same group .

---

### Post by Morbius1 on 2012-05-07
First, Octal chmods aways have to have odd values so that directories have the execute bit enabled.

But you don't want to do a "chmod -R 555 / path" either since that makes every file within it executable as well. It's best not to do a recursive chmod in octal at all but that's another discussion.

> The thing I want to do is give John the rights to r/w in his folder
And give Pierre read access but not write.You lost me on that one since it's already set up that way. If john created the folder then it's going to have the following permissions:
> drwxrwxr-x john john /path/to/John So every subdirectory will have those permissions and every file will have "rw-rw-r--". John can read and write - everyone else can only read.
> To the public folder, both have read acces, none can write.
```
sudo chmod 555 /Public
```Don't use the R switch.

---

### Post by codemaniac on 2012-05-07
Morbius1 , is there any severe issues if we turn off the executive bit of a directory ?

---

### Post by redmk2 on 2012-05-08
> **codemaniac said:**
> Morbius1 , is there any severe issues if we turn off the executive bit of a directory ?

The execute bit is set on the directory so that the user (u,g, or o) can traverse (see inside or descend into) the directory. An example would be```
7 user (owner) = read, write and directory rights
5 groups = read and directory rights
5 others = read and directory rights

```

---

### Post by Jonathan L on 2012-05-08
[I deleted my post because it wasn't good advice!]

Kind regards,
Jonathan.

---

### Post by Morbius1 on 2012-05-08
> **Jonathan L said:**
> Put pierre in john's group:
... The home directories will normally be '755'
You might want to create a new group and have both john and pierre  be members of that group but you don't want to have pierre be a member of john's group.

That was always true but especially true with 12.04 because Ubuntu changed the default umask to 002 from 022 so by default home directories and everything that a user creates now has directories / files set to 775 / 664.

Putting pierre in john's group will give him write access to everything john owns.

Remember the original requirement:
> The thing I want to do is give John the rights to r/w in his folder
And give Pierre read access but not write.
That happens by default. Now if I misunderstood the requirement and he wants John's folder to allow Pierre read access access but not Tom then he needs to create a separate group and have both John and Pierre in the same group, change the group of the folder to this new group, and change permissions to 750. But since Tom has sudo rights it's academic since if he really wanted access he has it.

---

### Post by Jonathan L on 2012-05-08
> **Morbius1 said:**
> 12.04 because Ubuntu changed the default umask to 002 from 022.

Morbius --

I stand corrected about the defaults in 12.04, and completely agree with what you're saying: I deleted my advice above as it's clearly not correct for current releases.

Thanks for pointing it out.

Kind regards,
Jonathan.

---

### Post by codemaniac on 2012-05-08
> **redmk2 said:**
> The execute bit is set on the directory so that the user (u,g, or o) can traverse (see inside or descend into) the directory. An example would be```
7 user (owner) = read, write and directory rights
5 groups = read and directory rights
5 others = read and directory rights

```

Should have realized that .. :/

---

