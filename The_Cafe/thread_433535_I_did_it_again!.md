---
title: "I did it again!"
date: 2007-05-05
forum: The Cafe
---

### Post by FoolsGold on 2007-05-05
This is the second time in two months I've typed **rm -rf *** when inside my home folder, while stupidly assuming I was in another folder, the one I actually *wanted* to clear.

I'm such a n00b, and my n00b-poking-stick broke already. Maybe I got punished via karma for abusing other Linux n00bs. :mad:

---

### Post by runningwithscissors on 2007-05-05
n00bs should use the GUI for file-management. No shame in that.

---

### Post by zvacet on 2007-05-05
You are learning hard way,but you are learning.No irony.Here are pages with CLI options
  
[https://help.ubuntu.com/community/HowToGetHelp]("https://help.ubuntu.com/community/HowToGetHelp")

[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

### Post by igknighted on 2007-05-05
you should really alias the rm command to "rm -i".  This way it always asks "are you sure?" before deleting things adn you can catch mistakes.

---

### Post by saulgoode on 2007-05-05
Get into the habit of using BASH's tab completion to display which files are to be deleted:

[INDENT]**$ **rm -rf [tab][tab][/INDENT]

will present you with all of the files and directories (top-level) and it will usually become obvious if you are in the wrong directory. Once you have seen the output, you can add the asterisk.

I have also gotten into the habit of always explicitly stating a directory if I wish to delete it or its contents. For example, if I am in my 'Images' directory and wish to delete all of its files and subdirectories:

[INDENT]**$ **cd ..
**$ **rm -rf Images/[tab][tab][/INDENT]

It may sound difficult but it soon becomes second nature. It has been years since I have deleted the wrong files and I use CLI for all of my file managing.

---

### Post by EndPerform on 2007-05-05
Another useful command is : pwd.  That will tell you the full path of where you are.  Use that if you aren't sure where you are :)

---

### Post by plb on 2007-05-05
> **runningwithscissors said:**
> n00bs should use the GUI for file-management. No shame in that.

go back to gentoo forums :)

---

### Post by Sunnz on 2007-05-05
> **FoolsGold said:**
> This is the second time in two months I've typed **rm -rf *** when inside my home folder, while stupidly assuming I was in another folder, the one I actually *wanted* to clear.

I'm such a n00b, and my n00b-poking-stick broke already. Maybe I got punished via karma for abusing other Linux n00bs. :mad:
No worries people learn from their mistakes - at least you are not afraid to try the CLI.

---

### Post by runningwithscissors on 2007-05-05
> **plb said:**
> go back to gentoo forums :)
On your forum, trolling your community.

---

### Post by 3rdalbum on 2007-05-05
Rather than alias "rm" to "rm -i", maybe you should have the following:
```

alias rm=echo "Not until you've learnt your lesson about rm'ing!"

```

It might force you to use the GUI a bit more :-P

Sorry mate, I hope you had a backup.

---

### Post by weatherman on 2007-05-05
one that happens quite often to me using autocompletion is:
gcc -o something.c something
instead of
gcc -o something something.c
I've learned I should use different names for the binary and the source :-)

---

### Post by harlan on 2007-05-05
If you want your deleted files from CLI go to your trash, do as follow:
 $ gedit ~/.bashrc

and add this line at the end of the file
alias rm='mv --target-directory=/home/your_username/.Trash'

---

### Post by DoctorMO on 2007-05-05
```
sudo echo "alias rm='mv --target-directory=~/.Trash/'" >> /etc/bash.bashrc
```

This should solve it for most people, even works for root if you mkdir /root/.Trash

---

### Post by teet on 2007-05-05
Or you could just 

gksudo nautilus

and delete the folder through a gui.  Probably is easier/safer.

Don't feel too bad though...I once accidentally rm -rf *'ed a folder containing every episode of Seinfeld.  Serves me right I guess. 

-teet

---

