---
title: "Potentially Malicious Commands"
date: 2012-01-13
forum: Security
---

### Post by bitf on 2012-01-13
Hi everyone, I'm sure this is the right forum for this but I was unable to find one more suitable.

I recently noted a problem with my computer in a reply to a thread. This morning I received a PM from a user that reads as follows:
> I have the solution to the ubuntu problem... since im new i cant reply but if you could do it it would be nice the other hundreds jeje


1) Hit ctrl+alt+f1 at rhe blank screen to get you to a non-x terminal (tty1)

2) Login with your username and password

3) Change to root with:  sudo -i   (press enter and enter ur password)

(For all the following steps type exacly the same as here with spaces included and then press enter)

4) mkdir -p /run /run/lock

5) rm -rf /var/run /var/lock

6) ln -s /run/lock /var

7) ln -s /run/lock /var

8) reboot

(Press enter and you should have 11.10 back again)
***************

This message raised several red flags:

1. The use of the PM system rather than a post on the forum, the user claims he cannot reply to the post, which is a rule I could not find anywhere.

2. The non-specific reference to the issue as "the ubuntu problem."

3. The deletion of a folder full of files related to security and essential software.

4. The 6th and 7th commands are the same

Could I get my suspensions confirmed or denied?

---

### Post by spynappels on 2012-01-13
I would not run any code if it was not posted in the open forum, and I would NEVER run a rm -rf command without understanding what it does.

DO NOT RUN THIS CODE, please link to the original problem so we can see what is going on.

Also, you may want to make the Mods aware of the identity of the person who sent you this so they can be dealt with/educated.

---

### Post by bluexrider on 2012-01-13
> **spynappels said:**
> I would not run any code if it was not posted in the open forum, and I would NEVER run a rm -rf command without understanding what it does.

DO NOT RUN THIS CODE, please link to the original problem so we can see what is going on.

Also, you may want to make the Mods aware of the identity of the person who sent you this so they can be dealt with/educated.

+10 

I agree with spynappels. [SIZE=4][COLOR=Red]DO NOT RUN THESE COMMANDS[/COLOR][/SIZE]

---

### Post by 2F4U on 2012-01-13
New users can reply on this forum, so this is definitely suspicious. I would strongly suggest to not run this code.

---

### Post by Elfy on 2012-01-13
We've seen it - no need to report it - unless you already have.

> I would not run any code if it was not posted in the open forum, and I would NEVER run a rm -rf command without understanding what it does.

DO NOT RUN THIS CODE, please link to the original problem so we can see what is going on.+1 or more to that.

---

### Post by bitf on 2012-01-13
> **forestpiskie said:**
> We've seen it - no need to report it - unless you already have.

+1 or more to that.

Thanks everyone. The original thread is [here]("http://ubuntuforums.org/showthread.php?t=1745793"). It's marked as Solved but there are still some outstanding issues. I *think* I have fixed my problem using a solution found in the same forum.

---

### Post by CharlesA on 2012-01-13
> **2f4u said:**
> new users can reply on this forum, so this is definitely suspicious. I would strongly suggest to not run this code.
+1.

---

### Post by emiller12345 on 2012-01-13
> **spynappels said:**
> DO NOT RUN THIS CODE
+1
this begs the question, what implications could these commands have?
Making a /run directory, etc, will still have the owner of the original (root), but may have different permissions depending on what the umask is set as.  
In step #5, deleting all of the current locks and runs may be a way of hiding certain processes or open files? I will most probably mess up the organization of things. Maybe even cause a Denial of Service. If this deletion is an attempt to correct a problem, why change the location of the lock or run directories? Some computers have /var in a different file system then that of /, but I don't know how that effects things. Anyone else have an idea?

---

### Post by CharlesA on 2012-01-13
> **emiller12345 said:**
> +1
this begs the question, what implications could these commands have?
Making a /run directory, etc, will still have the owner of the original (root), but may have different permissions depending on what the umask is set as.  
In step #5, deleting all of the current locks and runs may be a way of hiding certain processes or open files? I will most probably mess up the organization of things. Maybe even cause a Denial of Service. If this deletion is an attempt to correct a problem, why change the location of the lock or run directories? Some computers have /var in a different file system then that of /, but I don't know how that effects things. Anyone else have an idea?
It looks fishy, that's for sure.

It looks like that it is deleting the lock files from /var and moving them to /run/lock

I don't know the implications of that move though, but it shouldn't have to be done in the first place.

---

