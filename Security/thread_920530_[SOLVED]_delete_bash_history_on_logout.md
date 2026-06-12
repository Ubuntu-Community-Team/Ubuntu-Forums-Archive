---
title: "[SOLVED] delete bash history on logout?"
date: 2008-09-15
forum: Security
---

### Post by sternkanz on 2008-09-15
Hi. I want to make ubuntu (heron) forget my bash history when I logout. How can I do this?

Thanks,

Stern

---

### Post by sternkanz on 2008-09-15
Alternatively, is there some way I can have the bash history stored encrypted?

Thanks,

Stern

---

### Post by kevdog on 2008-09-15
Although not created by default, if you create a .bash_logout file within the $HOME directory, the commands in this file are executed upon logout.  I suppose you could delete the .bash_history file using the simple
rm .bash_history 

command, or you could encrypt the contents of the file using gpg or some such method.  If you choose to encrypt, you are going to have to make a corresponding decrypting command with the .bashrc file (or .bash_profile), to restore the .bash_history file so it can be read again (if you want to do this).

---

### Post by forger on 2008-09-15
> ls -la $HOME/.bash*
-rw------- 1 user user 17352 2008-09-15 17:13 .bash_history
-rw-r--r-- 1 user user   220 2006-10-04 22:18 .bash_logout
-rw-r--r-- 1 user user   416 2008-06-26 22:03 .bash_profile
-rw-r--r-- 1 user user  2825 2008-08-19 12:06 .bashrc

The file $HOME/.bash_history can only be seen by the root(administrator) and the user in question.

You can disable/limit the lines in the .bash_history file: [http://gentoo-wiki.com/SECURITY_Adjusting_The_Way_Bash_History_Funtions#Disabling_Bash_History_Per_User](http://gentoo-wiki.com/SECURITY_Adjusting_The_Way_Bash_History_Funtions#Disabling_Bash_History_Per_User)
or here: [http://forums.fedoraforum.org/showthread.php?t=67306](http://forums.fedoraforum.org/showthread.php?t=67306)

---

### Post by sternkanz on 2008-09-15
Well I hardly -ever- use bash history. I think I've used it about twice in my entire life (not that I've been using linux my entire life but hey). So if I have a .bash_logout file, I can continue using bash history until I logout. Then once I log back in again it will create a new .bash_history file which will get deleted again once I log out?

---

### Post by tollboy on 2008-09-15
i think this will help u 


type these commands ```
gedit ~/.bash_logout
```


now add a this line at the end of this file 

```
rm -rf ~/.bash_history
```


save the file



it is done

---

### Post by moonpup on 2008-09-15
You could also use the history command itself to empty it's contents...

```
history -c
```

---

### Post by Dr Small on 2008-09-15
> **kevdog said:**
> Although not created by default, if you create a .bash_logout file within the $HOME directory, the commands in this file are executed upon logout.  I suppose you could delete the .bash_history file using the simple
rm .bash_history 

command, or you could encrypt the contents of the file using gpg or some such method.  If you choose to encrypt, you are going to have to make a corresponding decrypting command with the .bashrc file (or .bash_profile), to restore the .bash_history file so it can be read again (if you want to do this).
That is really an excellent idea. I never thought about doing that! :)

---

### Post by ronmuzzi on 2011-01-10
Another simpler way to do this is to add this to .bashrc:

    HISTFILESIZE=0

History will work for the current session only and not be saved to .bash_history.

---

### Post by Archon810 on 2011-11-23
Alternatively, you could chown .bash_history to root. I was actually having a problem where my bash history wasn't being saved, and this turned out to be the issue - it was owned by root for some reason.

```
sudo chown root.root .bash_history 
```

---

