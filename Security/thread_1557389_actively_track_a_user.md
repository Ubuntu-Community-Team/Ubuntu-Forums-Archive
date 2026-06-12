---
title: "actively track a user"
date: 2010-08-20
forum: Security
---

### Post by Murdoc_of_puts on 2010-08-20
Hello, 
I'm trying to figure out a way to see what one of my users are doing on my network.  This particular user has a habit of generally "messing things up", which is why I'm trying to teach the user to use Linux properly.  I however don't have the time to sit down and walk user through.  So I recommend these forums, and a couple others.  Here's the thing.  The user keeps making fatal system errors and crashing the computer, and then doesn't remember what she did, which makes it almost impossible at times to fix.  I've had to delete and reset her account several times this month.  So this is what I want to know.  Is there a way to set up some sort of logger or something that will automatically start when only this user logs in, runs in the background so as not to draw attention to it ( probably distract her), and have the output sent to my/root account?  This is mostly just so I can actually see what she's typing in the terminal, and what programs she's running in unison so I can try to stem the problem from the administrator's desk.  Thanks for any help in advance.

---

### Post by wacky_sung on 2010-08-20
Get a remote access of her desktop and visually see / record what she did causing the error.

Probably you gonna first checked out your company policy any remote / keylogging gonna cause any disciplinary violation.

---

### Post by JBAlaska on 2010-08-20
Since this person is messing up her account to the point you have to delete it, she must be using sudo, just check her /var/log/auth.log

---

### Post by uRock on 2010-08-20
> **Murdoc_of_puts said:**
> Hello, 
I'm trying to figure out a way to see what one of my users are doing on my network.  This particular user has a habit of generally "messing things up", which is why I'm trying to teach the user to use Linux properly.  I however don't have the time to sit down and walk user through.  So I recommend these forums, and a couple others.  Here's the thing.  The user keeps making fatal system errors and crashing the computer, and then doesn't remember what she did, which makes it almost impossible at times to fix.  I've had to delete and reset her account several times this month.  So this is what I want to know.  Is there a way to set up some sort of logger or something that will automatically start when only this user logs in, runs in the background so as not to draw attention to it ( probably distract her), and have the output sent to my/root account?  This is mostly just so I can actually see what she's typing in the terminal, and what programs she's running in unison so I can try to stem the problem from the administrator's desk.  Thanks for any help in advance.
It is much easier to take time to teach the user than to keep repairing the system.

Would restricting the user's permissions help prevent the problems?

---

### Post by OpSecShellshock on 2010-08-21
Restricting permissions is exactly what I was going to suggest. Also, if this is command line stuff then it might be available in ~/.bash_history in the user's home directory.

---

