---
title: "How to move a file from desktop to Wine program files?"
date: 2010-08-30
forum: Wine
---

### Post by judge jankum on 2010-08-30
How do I move a file from desktop in Xubuntu 8.04 to c program files in Wine? It wont cut and paste" 
 I downloaded extensions to a game (Aztec) that I need to replace a file with in Wine, if that's possible...
                               Thanks guys

---

### Post by Black Hawk on 2010-08-30
Open the file manager. Make sure you're in your home directory. Press ctrl + h to show hidden files. enter .wine/drive_c/Program Files/SomeDirectory and move the file there and copy/move the file there like it was any other directory.

---

### Post by ronnielsen1 on 2010-08-30
You shouldn't have any trouble with this.
Let's make sure you're going to the right place 


 Go to [COLOR=Blue]Places > Home[/COLOR]


Click on[COLOR=Blue] View > Show Hidden Files[/COLOR]

Navigate to[COLOR=Blue] .wine/drive_c/Program Files[/COLOR]

Now in another nautilus window navigate to where your folder is and try it again

---

### Post by skyork on 2012-10-15
> **Black Hawk said:**
> Open the file manager. Make sure you're in your home directory. Press ctrl + h to show hidden files. enter .wine/drive_c/Program Files/SomeDirectory and move the file there and copy/move the file there like it was any other directory.

Thanks...Just what I was looking for. Being new to Ubuntu, thought it was going to be a headache doing it from the terminal...Thx again

---

### Post by overdrank on 2012-10-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

