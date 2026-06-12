---
title: "Shell Issue"
date: 2008-10-13
forum: Server Platforms
---

### Post by yeaitsdark on 2008-10-13
The other day I inadvertently overwrote my /bin/sh file. I simply made a script and issued:

(Do not execute this on your system else you'll have same issue as me)
```
sudo cp script1 /bin/sh
```

(Granted, you prolly won't just happen to have a script1 file, still don't execute the above)

What I meant to issue was:
```
sudo cp script1 /usr/bin
```

My mind wasn't quite working properly that night...Alas, end of the back story.

At any rate, I have tried to recopy the links and files from another installation of Ubuntu Server 8.04 however, I am at a loss as to how exactly I can repair this.

The error(s) I receive is:
```
sh
```
Result: "-bash: /bin/sh: No such file or directory"
```
sudo sh
```
Result: "sudo: unable to execute /bin/sh: No such file or  directory."

Any way to resolve this issue without reinstalling? Thanks in advance for your help/advice.

---

### Post by pjbgravely on 2008-10-13
/bin/sh is simply a soft link to the default shell. Depending on your release it could be bash or dash. I believe it was bash ending with 6.06. If you are using 8.04 then dash is your target.

To restore:

sudo ln -s /bin/dash /bin/sh 

You may need to sudo rm /bin/sh first to clear any failed attempts at fixing.

Paul

---

### Post by yeaitsdark on 2008-10-14
Excellent. That indeed worked perfectly, I swear I did that before, but I have no clue. 

Note, (not sure if this is just me or not), but I created the link for bash, not dash and it worked fine. Perhaps I have a corrupted dash file or something. I'll do more playing around.

Thank you for the help :D

---

### Post by Krupski on 2008-10-14
> **pjbgravely said:**
> /bin/sh is simply a soft link to the default shell. Depending on your release it could be bash or dash. I believe it was bash ending with 6.06. If you are using 8.04 then dash is your target.

To restore:

sudo ln -s /bin/dash /bin/sh 

You may need to sudo rm /bin/sh first to clear any failed attempts at fixing.

Paul

Isn't *bash* supposed to be linked to "sh"?

---

### Post by yeaitsdark on 2008-10-14
Well, I've gone and broke it lol. Eventually, I think I'm going to have to redo the system. 

As long as it's running - it's doing what I need it to do. Hopefully the power won't go out for more than an hour in the next week, because at the moment I'm far to lazy to go to the machine and reinstall.

(It's getting some hardware upgrades in a week or so I shall do it then)

In the future, haha my advice is to not overwrite one's shell files... as well I have learned how bad it can be :P

---

### Post by iponeverything on 2008-10-14
This might work:

cd /var/cache/apt/archives
dpkg -i bash_*deb

---

### Post by pjbgravely on 2008-10-14
> **Krupski said:**
> Isn't *bash* supposed to be linked to "sh"?


[[COLOR="Red"]Dash is now sh on Ubuntu[/COLOR]]("https://wiki.ubuntu.com/DashAsBinSh")


yeaitsdark, pointing sh to bash instead of dash can break your system too.

Paul

---

