---
title: "Re-install with more than 1 user..."
date: 2008-04-26
forum: Ubuntu Brainstorm
---

### Post by Rinzwind on 2008-04-26
--- Related to: [http://brainstorm.ubuntu.com/idea/7296/](http://brainstorm.ubuntu.com/idea/7296/)
--- A big thank you to peterjs. His post gave me the courage to post this (been thinking about it for a few days).

Let's say I have a system with 2 accounts. I have a ...
1. /home/rincewind/
2. /home/twoflower/

Nothing fancy right? Actually it has a lot more than 2 users but this will do for now. On we go!

Hardy Heron arrives (well it will be Intrepid Ibex next times) with some brand new features that are a must to have and I want to do a new install with my existing /home/ intact. What happens?

1. I format / and leave /home/ intact.
2. I create my rincewind and have the system install.
3. I reboot into my new system and have
/home/rincewind
/home/twoflower

Now I never ever got a chance to recreate twoflower, did I? Not a problem you think? Since we have 'users and groups' in administration you say? 
But you get an error stating that /home/twoflower/ already exists! And I didn't see a way to fix this without going commando-style (I solved this by moving my /home/twoflower/ to another location, creating user twoflower and moving back /home/twoflower/).

This happens because anything related to these 2 users that resides inside / was deleted (passwd for instance). To me that can be considered as a broken system.

IDEAS: 
1. The installer should ask for other users to be recreated.
2. or it should ask for passwords after install on the basis that there are more directories inside /home/ than there are users in /etc/passwd.
3. or 'add users' should ignore that /home/ already exists.
Any of these would work. I consider 1 and 2 to be more work than 3. 

But I think there's an even more elegant solution...

Inside /etc we have at least these 4 user related files (rooky alert: I do not know if there are more...):
/etc/password 
/etc/shadow 
/etc/groups 
/etc/gshadow

Now shouldn't user related files be where the users are? So inside /home/. For instance inside a /home/.users/. Of course with a symbolic link to the original location in /etc as to not to brake things.

So what do you think? Did I miss anything that would have made my re-install keep my current users or not? Or does anyone have a better idea? NEXT time I will be saving those 4 files in the hope I can overwrite them...

---

### Post by maybeway36 on 2008-04-26
I think you should be able to use the "advanced" button to make new users before installation. That would be a very good idea, IMO.

---

### Post by AbtZ on 2008-05-04
This is a good idea. It is such a pain to set up your old /home with a fresh install of Ubuntu.

---

### Post by Ardrias on 2008-05-05
An advanced button to make more than one user would indeed be quite nice. Pairing the account(s) with existing /home would be equally useful.

---

