---
title: "Changed group but can't see the difference"
date: 2011-01-19
forum: Server Platforms
---

### Post by feezin on 2011-01-19
Hello people, I am completely new to this so please forgive me if I am asking the wrong thing in the wrong place... 

I have set up Ubuntu 10.04 and am running it on a VPS. I have everything the way I want it but I have encountered a problem. When I created my user, I did this:

[FONT="Courier New"]adduser myname
[/FONT]
that worked fine, it also assigned me to group called myname, which isn't what i wanted. so i tried to change my group to staff with the following:

[FONT="Courier New"]sudo usermod -g staff myname[/FONT]

it works fine and i can verify my new group by:

[FONT="Courier New"]groups myname[/FONT]

and get:

[FONT="Courier New"]staff[/FONT]

but...now here come the bit I don't understand, when I make a new file/folder and then look at their ownership it is the old group (ie. myname). is this right? shouldn't the ownership of the file now be myname staff? not myname myname.

this is what i did to create a new file, while logged in under myname:

[FONT="Courier New"]touch a 
mkdir da
ls -al[/FONT]

What am I doing wrong? Any suggestions would be greatly appreciated. Thanks.

---

### Post by egpetrich on 2011-01-22
When you make changes to your group membership, you typically have to log out and log back in to have the changes take effect. You didn't say if you did this, so I figured I should mention it.

It's possible (though I think not typical) that the home directory for "myname" has the set-group-id bit set. If this is the case, then new files or directories created in the home directory will be in the "myname" group by default. Here's an example showing what you would see in this case:
```

ls -ld $HOME
drwxr-sr-x 17 myname myname 4096 2011-01-15 10:27 /home/myname
```

The commands you showed in your e-mail have removed the user "myname" from the group "myname". This sets up the odd situation where the "myname" user is operating in a directory where it is the owner but it is not in the group. I think this is legal, but it might have odd side effects. I suggest that you keep the user in both groups but make the "staff" group the default.:
```

usermod -g staff -G myname myname
```
Also, if you feel that the user "myname" should be in the "staff" group by default, I would change the group of "/home/myname" to be "staff":
```

sudo chgrp staff /home/myname
```

---

### Post by feezin on 2011-01-23
egpetrich, thank you so much for your help, it is exactly the way i wanted it now. absolutely perfect. cheers.

---

### Post by bearly230 on 2011-01-23
I have a similar issue. The problem with this resolution if what if I belong to several groups. Each group has it's own directory tree. How do I make each directory tree default to the group ownership by default. Instead of assigning a different group ownership.

Example:

Directory: user1, groupx. Everthing in this group needs to be assigned to groupx
Directory2: user1. groupy. Everything in this group needs to be assigned to groupy.

I wouldn't want to be in groupx and have the files saved under groupy.

---

### Post by samosamo on 2011-01-23
> **bearly230 said:**
> I have a similar issue. The problem with this resolution if what if I belong to several groups. Each group has it's own directory tree. How do I make each directory tree default to the group ownership by default. Instead of assigning a different group ownership.

Example:

Directory: user1, groupx. Everthing in this group needs to be assigned to groupx
Directory2: user1. groupy. Everything in this group needs to be assigned to groupy.

I wouldn't want to be in groupx and have the files saved under groupy.

You're looking to inherit group from parent directory on new files/folders, yes?

Create the directory.
# mkdir test
Change group ownership
# chgrp group1 test
Apply setgid flags
# chmod g+s test

---

### Post by bearly230 on 2011-01-24
I've tried that, however it still doesn't work. I've even rebooted both server and client to verify.

I've been trying to resolve this for the last several days.

---

