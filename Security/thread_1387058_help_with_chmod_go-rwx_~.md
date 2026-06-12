---
title: "help with chmod go-rwx ~"
date: 2010-01-21
forum: Security
---

### Post by Michaeljs1990 on 2010-01-21
I am on the admin account of my computer and am trying to remove all privileges from CWD i have tried

chmod go-rwx ~
sudo chmod go-rwx ~

but when i pull up

ls -l ~

It is still showing permission in the g and o column. Help much appreciated.

---

### Post by cdenley on 2010-01-21
> **Michaeljs1990 said:**
> I am on the admin account of my computer and am trying to remove all privileges from CWD i have tried

chmod go-rwx ~
sudo chmod go-rwx ~

but when i pull up

ls -l ~

It is still showing permission in the g and o column. Help much appreciated.

If you're trying to change the permissions on the files and directory inside your home folder (not just the home directory itself), you need to make it recursive.
```

chmod -R go-rwx ~
man chmod

```

---

### Post by Sarmacid on 2010-01-21
Are you trying to prevent other users from accessing your home folder? If that's the case then ```
chmod 700 /home/$USER
``` And add the -R flag if you want it recursive.

---

### Post by Lars Noodén on 2010-01-21
> **Michaeljs1990 said:**
> ... remove all privileges from CWD ...

Current working directory (CWD) is a dot (**.**) not a tilde (**~**)

```

# remove *all* privileges from CWD, which may not be what you want
chmod u=,g=,o= **.**

# remove *all* privileges from CWD, except for the owner
chmod u=rwx,g=,o= **.**

```

---

### Post by rookcifer on 2010-01-21
> **Michaeljs1990 said:**
> I am on the admin account of my computer and am trying to remove all privileges from CWD i have tried

chmod go-rwx ~
sudo chmod go-rwx ~

but when i pull up

ls -l ~

It is still showing permission in the g and o column. Help much appreciated.

What do you mean by "removing **all** permissions?"  If you want to just stop others from seeing your files, you need to do as the guy above said:

```
sudo chmod -R 0700 <directory>
```

This will result in only the owner (and root) of the directory having access.

---

### Post by Michaeljs1990 on 2010-01-21
Thank you for the help the command that finally worked was
sudo chmod -R go-rwx /home/michael
For some reason as i am not a unix expert so it probably makes sense when i use ~ or . as Lars said it wont change my CWD. However when you write it out chmod -R says "chmod: cannot access `./.gvfs': Permission denied" even with sudo in front it does the same thing. also to Lars i would like to say in my unix shell 
ls -l ~ 
&
ls -l .
both bring up the same list
thank you for your help if someone could clear up why ~ and . wont work when changing permission it would be much appreciated. also why chmod -R brings back that error message ever time.

---

### Post by cdenley on 2010-01-21
That error about ~/.gvfs is normal. That hidden directory is used for mount points when you mount a network share with nautilus. You cannot change the permissions on it, nor should you. Also, root cannot access that directory. If you have mounted shares with nautilus, you might want to be careful what recursive commands you use on your home directory, as they could modify those shares as well.

"~" and "." will work, and probably did, you simply weren't listing the permissions of that directory when you first tried to use it.
```

chmod 700 ~
ls -ld ~

```

---

### Post by Michaeljs1990 on 2010-01-21
as you can see from my last post  i was a little confused about what was going on i must have been putting in something wrong because now it works perfectly
sudo chmod -Rv go-rwx ~ (~ . and /home/(name of your CWD) all work)
sudo chmod -Rv go+rwx ~ (to give all permission back)

the -v argument just shows that it is actually changing it and gives you a print out. Thank you again (lol) it was really bugging me that i couldn't get it to work right. I will sleep well tonight:D . Ubuntu community = AWESOME

---

### Post by cdenley on 2010-01-21
> **Michaeljs1990 said:**
> as you can see from my last post  i was a little confused about what was going on i must have been putting in something wrong because now it works perfectly
sudo chmod -Rv go-rwx ~ (~ . and /home/(name of your CWD) all work)
sudo chmod -Rv go+rwx ~ (to give all permission back)

the -v argument just shows that it is actually changing it and gives you a print out. Thank you again (lol) it was really bugging me that i couldn't get it to work right. I will sleep well tonight:D . Ubuntu community = AWESOME

CWD = current working directory. This can be your home directory, depending on if you have changed the CWD with the "cd" command. In the terminal, a "." means the CWD.

recursive = Traversing the contents of a directory to perform an action on all files or directories contained within a directory. A "-R" switch is often used by commands to make it recursive. Refer to the command's manpage.

~ = home directory. This is typically a directory named after the user contained in /home. When you start a new terminal, the CWD is your home directory initially, but can be changed at any point.

---

### Post by Lars Noodén on 2010-01-22
> **Michaeljs1990 said:**
> ... also to Lars i would like to say in my unix shell 
ls -l ~ 
&
ls -l .
both bring up the same list

That would be because when you are in your own home directory the two *are* the same. **~** is a shortcut for the value stored in the environment variable $HOME.  By the way "[**ls**](http://linux.die.net/man/1/ls)" by itself without any parameters is a shortcut for "**ls .**"

```

# print name of current (working) directory
pwd

# print name registered as home directory
echo $HOME

```

To see the difference:

```

# change directory
cd /usr/bin

# see what's there
ls **.**

# see what's in your home directory
ls **~**


```

---

