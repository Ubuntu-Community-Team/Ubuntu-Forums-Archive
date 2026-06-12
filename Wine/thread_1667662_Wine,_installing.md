---
title: "Wine, installing"
date: 2011-01-15
forum: Wine
---

### Post by Spyderkid on 2011-01-15
How can you make it so I can install something on one user on wine and then that makes it installed on all other users?

I have full admin permissions.

---

### Post by Verbeck on 2011-01-15
haven't tried this myself but;
try creating a symbolic link in each of the user's home directory to one main .wine folder some where
(the permissions of the real folder should be changed to read/write/execute by all i guess)

---

### Post by Spyderkid on 2011-01-15
So Instead of having each own users .Wine I can make a shortcut to my .Wine folder? how can I do this if this is right?

Can i enable folder sharing? would that work or not

---

### Post by Spyderkid on 2011-01-15
Bump

---

### Post by Spyderkid on 2011-01-15
bump

---

### Post by Spyderkid on 2011-01-15
[SIZE="1"]a tiny bump[/SIZE]

---

### Post by Spyderkid on 2011-01-15
[SIZE="1"]a tiny bump[/SIZE]

---

### Post by Tony Flury on 2011-01-15
Why not try the suggestion - create a symbolic link.

look at 

```

man ln

```

You will also have to give everyone a copy of the Launcher so they can run the application.

---

### Post by Tony Flury on 2011-01-15
Ignore - forum problems.

---

### Post by Tony Flury on 2011-01-15
Ignore - forum problems.

---

### Post by Spyderkid on 2011-01-15
I didn't mean to repeat Internet was slow clicked on button too many times when the first time wasn't succsusfull (which apparently it was) sorry

---

### Post by Spyderkid on 2011-01-16
I don't quite understand the entry for [FONT="Courier New"]ln[/FONT] also I don't know how to make a copy of the launcher and where to put it.

So could you give me a bit of code which I can use and how to and where to copy the laucher to please

---

### Post by Spyderkid on 2011-01-16
I don't quite understand the entry for ln also I don't know how to make a copy of the launcher and where to put it.

So could you give me a bit of code which I can use and how to and where to copy the laucher to please




bump

---

### Post by Spyderkid on 2011-01-19
A slightly [SIZE="3"]Larger[/SIZE] than a [SIZE="1"]small[/SIZE] Bump

---

### Post by Verbeck on 2011-01-19
you could make a symbolic link by middle-click>drag>drop and selecting 'link here'
or from a terminal
ln -s /path/to/original/file /path/to/link

---

### Post by Spyderkid on 2011-01-21
I can't access the other users folders, how can I acess them without using a terminal.

---

### Post by Spyderkid on 2011-01-22
Bump?

---

### Post by Spyderkid on 2011-01-24
So if I wanted to make a link to a folder called .wine from a user name called USER1 and the .wine folder is in USER2 what would be the bit of code (sorry verbeck I don't quite understand what you've written)

---

### Post by Verbeck on 2011-01-25
sorry for the late reply
the command should look like
sudo ln -s /home/user1/.wine /home/user2/.wine
then* sudo chown user2:  /home/user2/.wine*
as i said before, you'll also need to adjust the permissions of the user1's home directory so that user2 could access  his .wine folder normally

hope this helps

---

### Post by Spyderkid on 2011-01-29
i need some help now ive just ended up locking my .wine folder so i can delete it and re-install wine also none of the programs will run either

---

### Post by Spyderkid on 2011-01-29
bump?

---

### Post by Elfy on 2011-01-29
Closed for 24 hours

---

