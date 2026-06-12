---
title: "Samba and shares on Ubunutu"
date: 2010-06-01
forum: Server Platforms
---

### Post by Cristabelle on 2010-06-01
Hi everybody,
I'm a newbie in Samba and Ubunut.
I've on my Ubuntu Server, a Samba server is installed.
I'm working on a project that helps share a directory tree of a project. This tree contains the diffrent files attached to a project.
To control the sharing the directories of the project, I've created a group (let's call it "TreeGroup") that contains the diffrent users of the tree and this group has the rights of reading, writing and executing. And then to restrict the rights on a specific directory named "dir_n", I think of creating an other group (named "dir-n-group") attached to this directory that allows only a part of the members of the group "TreeGroup" to access to this directory.
I think of doing the same for all the directories but I don't know if it will create a conflict or not.
If somebody has an idea, even a little one, I'll be grateful.
Thank you in advance :)

---

### Post by new_tolinux on 2010-06-01
Setup group "treegroup"
Setup group "dir_n"
Grant rights to someuser:treegroup on the folders you'll need to be accessible for members of "treegroup"
Grant rights to someuser:dir_n on the folder you'll need to be accessible for members of "dir_n"
Add users to "treegroup" or "dir_n" as you like.
Setup samba-access for all users as you like.

Every user has his/her own account (username+password), but it can produce problems with newly created files as their creator is set as their owner.

---

### Post by Cristabelle on 2010-06-01
I see. Thank youy for the quick answer.
I'll try it and then I'll post the result.
Thank you again :)

---

### Post by Cristabelle on 2010-06-01
Now I see other problems.
To make it easier to imagine the situation I'm in, I'll give a scenario to be clearer:
Imagine we have a project named "test", this project's tree is composed of four directories:
ths main directory called "test" (as the name of the project), it's composed of three directories "test1", "test2" and "test3" (let's not consider the files inside for the moment).
I have three member ("user1", "user2" and "user3") who need to access this tree. I want that the directory 
- "test1" be accessed only by "user1" and "user2"
- "test2" be accessed only by "user2" and "user3"
- "test3" be accessed only by "user3" and "user1"
So, the solution I've proposed is to create a group "group_test" which contains all the three users, and setup the rights of reading writing and executing, then create three groups "group_test1", "group_test2" and "group_test3" that contains of course the users as shown above 
(I mean : -group_test1 : user1 and user2 (with the rights of reading writing
                                                              and executing and the user3 only with the 
                                                              right of reading)
               -group_test2 : user2 and user3 (with the rights of reading writing
                                                              and executing and the user1 only with the 
                                                              right of reading)
               -group_test3 : user3 and user1 (with the rights of reading writing
                                                              and executing and the user2 only with the 
                                                              right of reading)
)
You see my problems??
One that is so clear, the owner of each directory, how can it be precise which group is meant, etc..

---

### Post by new_tolinux on 2010-06-01
> **Cristabelle said:**
> You see my problems??
I see exactly the major reason I think *nix isn't meant to be used as a fileserver.

In Windows (and Netware, which is also partly linux/unix-based) you can give multiple users rights to each file in each folder. You also can specify groups and give them rights.

*nix only has "user:group:world" as options to set rights. That means that it's almost impossible to get it right without an admin constantly monitoring the creation/editing of files and modify the rights.
In my opinion *nix is the worst thing you can have as a fileserver for the project you describe.

---

### Post by JimmieC on 2010-06-01
Hi Cristabelle,

Check this out, should help you.
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html)

Cheers,

Jim

---

### Post by redmk2 on 2010-06-01
> **new_tolinux said:**
> I see exactly the major reason I think *nix isn't meant to be used as a fileserver.

In Windows (and Netware, which is also partly linux/unix-based) you can give multiple users rights to each file in each folder. You also can specify groups and give them rights.

*nix only has "user:group:world" as options to set rights. That means that it's almost impossible to get it right without an admin constantly monitoring the creation/editing of files and modify the rights.
In my opinion *nix is the worst thing you can have as a fileserver for the project you describe.

You can use ACL's for that in *nix.  See [**_here _**]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists")and  [**_here_**]("http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls") and **[_here_]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3077971/Fine-Tuning-Linux-Administration-with-ACLs.htm")**.

---

### Post by new_tolinux on 2010-06-01
> **redmk2 said:**
> You can use ACL's for that in *nix.  See [**_here _**]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists")and  [**_here_**]("http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls") and **[_here_]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3077971/Fine-Tuning-Linux-Administration-with-ACLs.htm")**.

I will dive into that tomorrow. Thanks for mentioning.

---

### Post by Cristabelle on 2010-06-02
Hi everybody,
Thank you for yoyr answers. I've tryed ACL like this:
 - I've created 3 users (linux and then used them as Samba's)
 - I've followed the Ubuntu tutoriel to make ACL work, and it worked, I can attribute different rights to each directory in the tree dependently of the users meant to access it.
(Thank you again, that helped me sava a lot of time creating a never ending number of groups imbricated one in an other)
So, the (I hope) last question, Samba considers these rights while accessing a directory or it can only see the first mask applied by chmod?
Thank you again :)

---

### Post by redmk2 on 2010-06-02
> **Cristabelle said:**
> Hi everybody,
Thank you for yoyr answers. I've tryed ACL like this:
 - I've created 3 users (linux and then used them as Samba's)
 - I've followed the Ubuntu tutoriel to make ACL work, and it worked, I can attribute different rights to each directory in the tree dependently of the users meant to access it.
(Thank you again, that helped me sava a lot of time creating a never ending number of groups imbricated one in an other)

I'm glad this worked out for you.

> 

So, the (I hope) last question, Samba considers these rights while accessing a directory or it can only see the first mask applied by chmod?

It is more proper to consider that Samba ***[COLOR="Blue"]authenticates [/COLOR]***the users as they attempt to mount the share (access).  By this I mean that Samba checks that the user is who they say they are (via password).  The underlaying directory and file permissions (including ACL's) provide the final say.  The Linux permissions ***[COLOR="Red"]authorize [/COLOR]***the users actions (as you say, it provides rights).

Bottom line Linux rights are always enforced in the end, regardless of what Samba configuration you might have.

---

### Post by Cristabelle on 2010-06-03
Oh! I understand now! It's becoming clearer! Thanks again!! :)

---

### Post by Cristabelle on 2010-06-03
Oh non! I have an other problem! I've created 3 users: u1, u2 (these two users are in the sama group "share")and u3 and a simple tree with the big directory sh1 that contains sh2, sh3 and sh4, all directories.
I made the user u1 the owner of the tree and I gave the mask 770.
Then I used ACL  with this command : setfacl -m d:u:u3:rx /sh1/sh2
I made also a Samba share with this code:
```

[share]
        sync always = yes
        writeable = yes
        delete readonly = yes
        locking = no
        path = /home/share
        guest ok = yes
        create mask = 0770
        directory mask = 0770

```
Now, it seems as if everything is quite well (I tested with testparm and restarted Samba and everything is alright).
Now I connect to samba this way:
```

 smbclient //10.73.42.12 -U u3

```
Then I give the password and every thing is alright, I get the prompt
```

smb: \>

```
But when I execute
```

cd ./sh3

```
I doesn't work [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
I gives me this error : 
NT_STATUS_NETWORK_ACCESS_DENIED listing \-1ap

0 blocks of size 0. 61680 blocks available

And when I try 
```

getfacl ./sh3

```
It gives me : 
Can't get UNIX CIFS version from server.
I've serached for this error on the web, and I got nothing [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
Please helpppppppppppppp !!

---

### Post by redmk2 on 2010-06-03
@Cristabelle,

What OS are you using to connect with?  I believe you should connect with this format:```
smbclient //<COMPUTERNAME>/share -U <username>
```

Once you have connected to the share the the proper command to change directory is > cd ToHere

There is no "." (dot) needed.  

Here is the sequence of me connecting to my server```
smbclient //rincon/cmax -U redmk2 
```

After logging in I can use this to see the directory contents ```
smb: \>ls
```

This shows that I have four directories ( . = current and .. = the directory above)
```
  .                                   D        0  Wed Nov 11 11:39:48 2009
  ..                                  D        0  Sun Sep 13 18:38:30 2009
  redmk2                              D        0  Tue Jul 21 14:51:54 2009
  vaio-disks                          D        0  Wed Nov 11 11:53:51 2009
  pictures                            D        0  Tue Jul 21 15:39:08 2009

		47320 blocks of size 2097152. 24581 blocks available

```
Once again -- to change directory you do not need to use a dot in front of the command.  The proper command is like this```
cd vaio-disks
```

That would take you to the directory *vaio-disks*.

---

### Post by Cristabelle on 2010-06-04
Thank you redmk2 for answering me, but I suppose this is not my problem.
I'll suppose this problem comes from the installation of Samba itself.
So I'll remove it and reinstall it and retry everything from the begginning then I'll post the result.
Hope it works :P

---

