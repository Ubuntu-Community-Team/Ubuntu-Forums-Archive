---
title: "how to remove the desktop (GUI) environment from  ubuntu 10.10 server"
date: 2011-03-28
forum: Server Platforms
---

### Post by iconoclast hero on 2011-03-28
It was helpful in getting things set up, but I would like to go back to a ChUI-only environment.  Help in getting it removed is appreciated.

---

### Post by lz1dsb on 2011-03-28
What's ChUI-only environment?

---

### Post by rubylaser on 2011-03-28
I assume the OP meant CLI.  Here are directions to remove ubuntu-desktop from your server.
[http://ubuntuforums.org/showpost.php?p=9174671&postcount=3]("http://ubuntuforums.org/showpost.php?p=9174671&postcount=3")

---

### Post by iconoclast hero on 2011-03-28
ChUI is Character User Interface as opposed to Graphical User Interface (GUI).  I didn't make this up, I swear...

[http://acronyms.thefreedictionary.com/Character-Based+User+Interface](http://acronyms.thefreedictionary.com/Character-Based+User+Interface)

Thank you, I will look at the instructions posted by the second respondent.

---

### Post by lz1dsb on 2011-03-28
> **iconoclast hero said:**
> ChUI is Character User Interface as opposed to Graphical User Interface (GUI).  I didn't make this up, I swear...

[http://acronyms.thefreedictionary.com/Character-Based+User+Interface](http://acronyms.thefreedictionary.com/Character-Based+User+Interface)

Thank you, I will look at the instructions posted by the second respondent.
Wow! Amazing! Sometimes it's so crazy with all this achronyms (I've only heard about CLI - Command Line Interface). And they should make our lives easier :(

---

### Post by iconoclast hero on 2011-03-29
I think CHuI has been relegated to obscurity...  It wasn't in wikipedia.

Anyway, tasksel does not a) have an option for "Basic Server" in it for 10.10 server and I'd already seen that post, tried it, and it didn't work.  Any other options?

---

### Post by cariboo on 2011-03-29
If all you want is to stop the desktop from loading, just purge gdm/xdm/kdm, then you still have the option of starting the desktop if you need it, by typing:

```
startx
```

at the command prompt.

If you want to completely remove the desktop, if for instance you have the ubuntu-desktop meta package intalled, use the folloeing command:

```
apt-get purge ubuntu-desktop
```

---

### Post by iconoclast hero on 2011-03-29
> **cariboo907 said:**
> If all you want is to stop the desktop from loading, just purge gdm/xdm/kdm, then you still have the option of starting the desktop if you need it, by typing:
```
startx
```at the command prompt.


I have GDM.  How is that I purge them?  same code as below? with ubuntu-desktop replaced with GDM?


> 
If you want to completely remove the desktop, if for instance you have the ubuntu-desktop meta package intalled, use the folloeing command:

```
apt-get purge ubuntu-desktop
```

Does this have to be done from say the recovery bootup or can I do this or tasksel from a terminal prompt launched from the desktop?

---

### Post by Mr Stoozer on 2011-04-05
Do we have any updates for this thread? I'd be interested to hear if you accomplished your task as i am looking to do the same thing.

---

### Post by iconoclast hero on 2011-04-05
I believe I booted into the recovery console (although you could try from the CLI without doing so and see what happens) and then did the ```
sudo apt-get purge gdm
```.  It seemed like one of the things it did was also to purge or remove ubuntu-desktop...  I really am not sure exactly what it did.  I can still get into the desktop via startx which is really what I wanted anyway.  I can say that tasksel did not work for me, nor did ```
apt-get uninstall ubuntu-desktop
```.

---

### Post by Mr Stoozer on 2011-04-05
Thanks, i'll give that a go and report.

---

### Post by iconoclast hero on 2011-04-05
NP.  I was mainly using the desktop to screw with the wireless settings.  Eventually I realised that wasn't going to work and I had to just configure them manually.  If you're in the same boat, I'll send you my /etc/network/interfaces file.  It was tricky to get wireless working...  The sad truth is I just need to run the cat-6 through the basement and turn it back on which I probably could have done in the same amount of time if not less.

---

### Post by Mr Stoozer on 2011-04-05
**apt-get purge gdm** did the trick. No need for the NIC file, thanks anyway.

---

### Post by iconoclast hero on 2011-04-05
Can you still boot into the desktop via startx?

---

### Post by Mr Stoozer on 2011-04-08
Yes.  Just X in my case. 
That actually wasn't entirely what I was looking for as i thought removing gdm would remove gnome entirely. I realise my misconception.

---

