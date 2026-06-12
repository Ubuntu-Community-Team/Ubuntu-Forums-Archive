---
title: "Samba permissions for file,folder"
date: 2014-12-04
forum: Server Platforms
---

### Post by gardenair on 2014-12-04
I am using ubuntu server edition and successfully created samba server.Unfortunately there are few flaws  in it which i want to discuss with you guise.
My smb.conf which i have edited  is

```
Workgroup = WORKGROUP
server string = Samba Server Version %v

[public]
comment = Public Stuff
path = /srv/samba
valid users = smith
; force group = accounting
public = yes
writable = yes
printable = no
write list = +staf
```f



Create users
```
# useradd smith 
# useradd foo
```

Now i created a group accounting

```
#groupadd accounting
```

then useradd into group

```
# useradd -gaccounting smith

# useradd -gaccounting foo
```

Now adding samba password

```
# smbpasswd -a foo1
```

Now I set the permission 

```
#mkdir -p /srv/samba
#chown -R root:accounting /srv/samba
#chmod -R 0757 srv
```


I switch into windows xp and map the drive z
```
//192.168.1.10/public
```

Now in the dialog box i write user name and smb password only and it map the drive.

The thing i want to discuss.that if there are more than one users in accounting group then in smb.conf file i shall write all users users one by one ?
like

```
valid users = smith foo1 foo2 foo3 foo4 foo5 foo6

```
what is the professional way ?

2- thing i want to discuss each users should be owner of his own file and folder  and no body else can delete it ,he/she may only read and execute the file.Only root user can delete file of any user.

please guide me,
thanks
gardenair

---

### Post by bab1 on 2014-12-04
> **gardenair said:**
> I am using ubuntu server edition and successfully created samba server.Unfortunately there are few flaws  in it which i want to discuss with you guise.
My smb.conf which i have edited  is

```
Workgroup = WORKGROUP
server string = Samba Server Version %v

[public]
comment = Public Stuff
path = /srv/samba
valid users = smith
; force group = accounting
public = yes
writable = yes
printable = no
write list = +staf
```f



Create users
```
# useradd smith 
# useradd foo
```

Now i created a group accounting

```
#groupadd accounting
```

then useradd into group

```
# useradd -gaccounting smith

# useradd -gaccounting foo
```

Now adding samba password

```
# smbpasswd -a foo1  [COLOR=#FF0000]<--Do you mean foo or foo1???[/COLOR]
```

Now I set the permission 

```
#mkdir -p /srv/samba
#chown -R root:accounting /srv/samba
#chmod -R 0757 srv   [COLOR=#FF0000]<--Did you mean /srv/samba?  Which perms  0775 or 0757 ??? [/COLOR]

```

I switch into windows xp and map the drive z
```
//192.168.1.10/public
```

Now in the dialog box i write user name and smb password only and it map the drive.

The thing i want to discuss.that if there are more than one users in accounting group then in smb.conf file i shall write all users users one by one ?
like

```
valid users = smith foo1 foo2 foo3 foo4 foo5 foo6

```
what is the professional way ?

2- thing i want to discuss each users should be owner of his own file and folder  and no body else can delete it ,he/she may only read and execute the file.Only root user can delete file of any user.

please guide me,
thanks
gardenair
Did you really mean foo1?  Or did you mean foo.  These are two different users.  In the group accounting you added foo but I don't see it in your current valid users statement.

In any case the valid users parameters are all listed in the man page for smb.conf```
man smb.conf
```

The valid users section reads ```
To restrict a service to a particular set of users you can use the valid users
           parameter.

           If any of the usernames begin with a ´@´ then the name will be looked up first in the
           NIS netgroups list (if Samba is compiled with netgroup support), followed by [B]a lookup
           in the UNIX groups database and will expand to a list of all users in the group of
           that name.[/B]

           If any of the usernames begin with a ´+´ then the name will be looked up only in the
           UNIX groups database and will expand to a list of all users in the group of that name.
```

Unfortunately the use of @group is widely used even with no netgroups present.  Netgroups is a NIS feature.  You can safely use +group if you have no NIS.  You can use either of these formats in the share```
valid users = user,user1,user2,@group

valid users = user,user1,user2,+group 
```

The 2nd question you asked was already answered by @redmk2 at [http://ubuntuforums.org/showthread.php?t=2254557&p=13178271#post13178271](http://ubuntuforums.org/showthread.php?t=2254557&p=13178271#post13178271).   The answer @redmk2 provided is correct.  The ability to delete a file is set in by the directory above where the file is created.  That permission is the [s] read [/s] [COLOR="#0000FF"] write [/COLOR]permission.  If you can [s]read[/s] [COLOR="#0000FF"] write [/COLOR] it you can delete it.  The only way to stop that from happening is to set the sticky bit on the directory above the file.  In octal notation that is 1 in the 1777 permissions.  This **allows any user **read (but not delete), write and execute permissions.   Bear in mind that this has **_no effect on the permissions of the files created_** in that directory.  The files created will always be 0664 which allows the user read and write permissions while all others have read only permission.  This is set by umask.  There are parameters in Samba to alter the umask.  Look for the *create mask* and *directory mask* section of the smb.conf man pages.

[COLOR="#0000FF"]Edit:  I misspoke above re: read permissions and deletion.  I have corrected that to state ***write ***permissions and deletion.  [/COLOR]

---

### Post by gardenair on 2014-12-04
Thnaks for the reply. Well i just want to correct 

```
#smbpasswd -a foo
```


Well the main thing is sticky Bit.This is a new thing for me and without it i think any user can delete other user data.Tough i am new in sticky bit but i want to discuss things regarding it.
My parents folder is /srv/samba and all of the users will dump their files in this common share folder. The sticky bit will implement on " /srv/samba " ? or only on "/samba" ? Please just elaborate it . 

Thanks.

---

### Post by bab1 on 2014-12-04
> **gardenair said:**
> Thnaks for the reply. Well i just want to correct 

```
#smbpasswd -a foo
```


Well the main thing is sticky Bit.This is a new thing for me and without it i think any user can delete other user data.Tough i am new in sticky bit but i want to discuss things regarding it.

My parents folder is /srv/samba and all of the users will dump their files in this common share folder. The sticky bit will implement on " /srv/samba " ? or only on "/samba" ? Please just elaborate it . 

Thanks.
The sticky bit is set on a specific directory that you want users to have read only permissions on all files even it the permissions are set to 1777.

Rather than me restating what is already published on the web, you can read all about it with this [google search]("https://www.google.com/search?q=ext4+stickybit&btnG=Go!&gws_rd=ssl").

If you still have questions you can post back here.

---

### Post by gardenair on 2014-12-05
Thanks for your,I just use sticky bit and  it show me

drwxr-xrwt root accounting   4096  Dec 5 15:55 samba

Now with it each user can only delete his own  file.My this face is also finish.

thank

---

### Post by gardenair on 2014-12-08
I just play around with the samba folder for permission.The thing which i get is if i assign samba folder permission as

```
# chmod 007 samba 
```

and then i implement sticky bit

```
# chmod +t samba 
```

the security works file.

Each users is own of his own file and folder and no body can delete other things in the common share.

Why this go to "other".I have implemented the security at the group "**accounting**" level   but it works on "others" which have wrx permission. If i do

```
# chmod 770 samba 
```

the permission not work on samba share folder.


Well my second query is if there are 20 users then  under valid users I shall write that 20 users name one by one ?


```
Workgroup = WORKGROUP
server string = Samba Server Version %v


[public]
comment = Public Stuff
path = /srv/samba
**valid users =**
; force group = accounting
public = yes
writable = yes
printable = no
write list = +staf

```


please guide me .

thanks

---

### Post by bab1 on 2014-12-08
> **gardenair said:**
> I just play around with the samba folder for permission.The thing which i get is if i assign samba folder permission as

```
# chmod 007 samba 
```

and then i implement sticky bit

```
# chmod +t samba 
```

the security works file.

Each users is own of his own file and folder and no body can delete other things in the common share.

Why this go to "other".I have implemented the security at the group "**accounting**" level   but it works on "others" which have wrx permission. If i do

I misspoke above at post #2.  The correct sentence should  state "** if you can write it you can delete it**" not read permissions.  Does this matter in your case?  I can't tell.  You are not using the configuration I would use.  if you use permissions of 007 I believe everyone but the owner/group has permissions to both read and write files.  Adding the sticky bit then disallows all "***others***" to delete the files created by someone else. 
> 

```
# chmod 770 samba 
```

the permission not work on samba share folder.

You need to use the sticky bit with all users having read and write permissions (777).  Therefore you will have 1777 (a+s) if you want this to work.  Here is the section from the man pages of chmod```
man chmod
...
RESTRICTED DELETION FLAG OR STICKY BIT
       The  restricted  deletion flag or sticky bit is a single bit, whose interpretation depends
       on the file type.  For directories, it prevents unprivileged users from removing or renam&#8208;
       ing  a file in the directory unless they own the file or the directory; this is called the
       restricted deletion flag for the directory, and is commonly found on world-writable direc&#8208;
       tories  like  /tmp. 

``` 
> 

Well my second query is if there are 20 users then  under valid users I shall write that 20 users name one by one ?


```
Workgroup = WORKGROUP
server string = Samba Server Version %v


[public]
comment = Public Stuff
path = /srv/samba
**valid users =**
; force group = accounting
public = yes
writable = yes
printable = no
write list = +staf

```


please guide me .

thanks
I think that was answered above also.  Read post #2 again.  You can use either a user group (valid users = +some_group) or individual users (valid users = bill, jane, bob, pam) or a combination of both (valid users =  +some_group,bill, jane, bob, pam).

I don't mind helping you, but you should to learn to read the documentation and follow the advice given.  Asking the *same* question over and over isn't helpful.

---

### Post by gardenair on 2014-12-09
I am too much thankful to ubuntu forum that there is a place were professional users are guiding each others. I am still in learning processing and on my ubuntu machines i am doing work on it.

One thing more i want to discuss that when i have 90 users using windows xp,windows 7 and windows 8 on laptop and desktop computers. All these users will share /srv/samba folder.The users will authenticate with windows server 2003 Active Directory and DNS is also configured in it.For these 90 users should I also add the workstations name in samba,like i kave workstation as wks1,wks2,wks3.......wks90.

thanks

gardenair

---

