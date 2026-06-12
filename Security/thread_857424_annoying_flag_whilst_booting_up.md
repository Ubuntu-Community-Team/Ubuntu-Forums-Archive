---
title: "annoying flag whilst booting up"
date: 2008-07-12
forum: Security
---

### Post by johnystevenson on 2008-07-12
hi there, i am an absolute beginner, this being my third day with the hardy version and 1st with linux.
I have an annoying flag whilst logging on! it reports "users $ HOME/.dmrc file is being ingored" and further on reads "owned by user and have 644 permissions" or there abouts

anyone out there able to tell me how to get rid of this flag....

thanks in advance,regards
johny

---

### Post by brian_p on 2008-07-12
> **johnystevenson said:**
> anyone out there able to tell me how to get rid of this flag....

Not quite - but a search with '.dmrc' in the Absolute Beginner and General Help forums will give you loads of advice.

---

### Post by shad0w_walker on 2008-07-12
Open up a terminal (Applications > Accessories > Terminal) and run this:

```
chmod 644 .dmrc; chown $USER:$USER .dmrc
```

---

### Post by johnystevenson on 2008-07-13
hi there, thanks both for your replys, after trying the code i got this up



john@johnys-desktop:~$ chmod 644 .dmrc; chown $USER:$USER .dmrc
chmod: cannot access `.dmrc': No such file or directory
chown: cannot access `.dmrc': No such file or directory
john@johnys-desktop:~$ 


not sure where to go from here but will try suggestion from first post

regards

---

### Post by simonapnic on 2008-07-13
Boot into recovery mode (if you don't know what that is, look at [this link]("http://www.psychocats.net/ubuntu/sudo")).

Type:

```

chown -R mike:mike /home/mike
chmod 700 /home/mike
chmod 644 /home/mike/.dmrc
reboot
```

Substitute in your actual username for *mike*, of course.

---

### Post by shad0w_walker on 2008-07-13
As he said in his last post, the file isn't found. 

Give this a try.

Press Alt + F2 and run this command:

```
gedit .dmrc
```

Then paste this into the file:
```

[Desktop]
Session=gnome

```

When you have done that, rerun this command from the terminal. Hopefully that will sort things out.

```
chmod 644 .dmrc; chown $USER:$USER .dmrc
```

---

