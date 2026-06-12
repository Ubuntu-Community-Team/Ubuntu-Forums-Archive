---
title: "Need to create a password for my userid"
date: 2011-02-13
forum: Security
---

### Post by Bernie Gallagher on 2011-02-13
I live alone, so when I installed Ubuntu on my machine a while ago, I didn't elect to require a password to log on.  

I will soon need to put password protection on my userid.  I used the Administration function go put a password on my userid, but it doesn't ask for the password when I start my machine.  It only asks for the password when I do admin stuff or log on to my wireless network, but it'll let anyone turn on the machine and snoop into my email and whatnot.  

Is this the way Linux works?  Or is there another step I need to do to lock down my machine with a password?

---

### Post by s.fox on 2011-02-13
Hello.

Try this:

**System -> Administration -> Users & Groups**

You should then see an option to change/ add a password next to your user.

Hope this helps.

-s.fox

---

### Post by Bernie Gallagher on 2011-02-13
Thanks, but that's exactly what I did do.  I created the password just fine, but it won't prompt for the password when I log on.  It only requires the password when I do admin stuff.  But I need to lock people out of my computer altogether.

---

### Post by rvchari on 2011-02-13
check the option in user and group to see if it is configured to log in without password. if so then uncheck that option or choose "uner needs to log in or something like that

---

### Post by Iowan on 2011-02-13
Depending on which version you use, you might check System>Administration>Login Screen to see if your username is set to login automatically.

(Slow typing again...)

---

### Post by Bernie Gallagher on 2011-02-13
> **rvchari said:**
> check the option in user and group...

I did that, and here's the steps I take:

I click on "Click to make changes."
It prompts for my password.
I type in my password and click Authenticate.
I click on my user name and click on Properties.
The box at the bottom is unchecked that says "Don't ask for password at login."

---

### Post by Bernie Gallagher on 2011-02-13
> **Iowan said:**
> ...check System>Administration>Login Screen to see if your username is set to login automatically.

Yes!  That was it.  It now prompts for my password when I turn my computer on.  Thanks!

(But now it asks for my password twice.  Once to log in.  Then again to unlock my keyring after I'm logged in.  But hey, my system is really secure now :-D

---

### Post by rvchari on 2011-02-13
> **Bernie Gallagher said:**
> Yes!  That was it.  It now prompts for my password when I turn my computer on.  Thanks!

(But now it asks for my password twice.  Once to log in.  Then again to unlock my keyring after I'm logged in.  But hey, my system is really secure now :-D

this might happen only if your key ring password and log in password are different. nevertheless, its good to get you back to your secure system.

---

