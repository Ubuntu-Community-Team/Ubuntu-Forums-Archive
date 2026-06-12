---
title: "Access Control Lists - Eiciel - Questions."
date: 2009-11-22
forum: Security
---

### Post by Roasted on 2009-11-22
I'm trying to set up Eiciel with ACL on my system, but I'm not sure on how to get things rolling. I already edited my fstab to enable ACL on my hard drive in question that I want to set up ACLs on.

When I fire up Eiciel, it is empty and asks me to open a file. Okay. That's cool. But - what file? What file do I need to select? Is this a file I create previously to using Eiciel or what? Is this the file that contains the ACL settings on it? How do I get started with it?

Also - If I am setting up ACLs to be used on a hard drive mounted to /media/storage, how do I finish things out in an intelligent manner? This is the way my drive is structured.

/media/storage

Within storage = Fred, Bob, Jane, David, Landon, Jim

Each user needs rwx writes to their share. Sure I can set this up with UGO rights but I want to do this through ACL since it will be a small scale test in case I ever have to set it up in a larger environment later.

What UGO permissions do I assign to /media/storage if I'm going to integrate ACLs? Do I assign 770? 700? I'm not entirely sure how ACLs integrate to Linux permissions so I'm not sure if the drive needs to be locked down with 700 permissions or if I need 777 or what. Any help is appreciated!!

---

### Post by cariboo on 2009-11-22
From the [User Guide]("http://rofi.roger-ferrer.org/eiciel/doc/ar01s02.html") you just have to open the file or directory you want to set the ACL on.

---

### Post by Roasted on 2009-11-23
I'm still not sure I follow, exactly.

So I have to open the directory within the menu. Okay.. fine. I do that. But when I make changes to it in Eiciel, and go back into it, it doesn't bring up that directory again. 

I'm just not entirely sure I follow how ACLs are integrated to Linux. Within Eiciel I set user permissions. Okay, but what about the folder? Does the folder need certain permissions for ACLs to work? Do I just set the perms to 700 or what? 

I've looked for YouTube videos and other how to guides. I'm not sure if I'm just being an idiot or if this is much easier than I anticipated.

---

