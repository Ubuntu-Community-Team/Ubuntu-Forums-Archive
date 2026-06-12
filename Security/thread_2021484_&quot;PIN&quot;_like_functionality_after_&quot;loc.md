---
title: "&quot;PIN&quot; like functionality after &quot;lock screen&quot;"
date: 2012-07-09
forum: Security
---

### Post by Gagarin24 on 2012-07-09
Hi, I use a reasonably secure/long password on my Ubuntu desktop to secure against off-line attack.  But I must say that it is rather inconvenient to type it every time the computer recovers from "lock screen" or from "suspend to ram".
I was wandering if there is any possibility to define a shorter password which would be valid only for a session. I could imagine that this "PIN" would be defined during a log in (after I type my secure password) and be active till I log out or computer loses power.

---

### Post by Cheesemill on 2012-07-09
I'm not sure if this is possible.

Do you use encryption at all on your machine?
If not then the longest password in the world will not protect your computer from anyone with physical access.

Without encryption physical access = root access.

---

### Post by Gagarin24 on 2012-07-09
Most parts are encrypted. I am not worried too much if someone steals my computer.  Bigger problem is that I don't want to leave my pc unattended, so I use "Lock screen" or "Suspend" like 20 times a day, that is more than 10 hours a year just writing the password :D, also for obvious reasons I can't use my wireless keyboard for it, which is another pain. Also writing the password so many times makes it easer for other people to see it (it is also annoying to say "look other way, I have to write my password").

Maybe there is some password manager or some application which would override "lock screen", or some way to temporally add a secondary password to the system.

It would be nice to set a PIN for the day knowing that if it becomes compromised or lost it's not a big problem. Even 3 letter PIN is almost impossible to guess with limited tries.


> **Cheesemill said:**
> I'm not sure if this is possible.

Do you use encryption at all on your machine?
If not then the longest password in the world will not protect your computer from anyone with physical access.

Without encryption physical access = root access.

---

### Post by needhelppeeps on 2012-07-09
Use biometrics.

---

### Post by Gagarin24 on 2012-07-12
Yeh sure, I'll buy a hundred dollar useless gadget which won't save me any time and makes mess on my table...

...but if biometry is possible, why not use some app which uses biometry interface and takes just password from the keyboard? 

Any ideas? I know it is summer...

> **needhelppeeps said:**
> Use biometrics.

---

### Post by Dave_L on 2012-07-14
What about creating a second user account with a short password, and locking the screen using that user via su or sudo? The screen lock can be invoked from the shell with "/usr/bin/gnome-screensaver-command -l". 

I did some experimentation with this, but was unable to get it to work. Maybe you or someone else can apply the method successfully.

---

### Post by Paddy Landau on 2012-07-14
I believe that this can be done with a simple script. I am not at my computer at the moment, so I shall have a look tomorrow.

---

### Post by Paddy Landau on 2012-07-15
Unfortunately, I have not managed to figure this out. I nearly got there; but there is one small glitch that I cannot get around, sorry.

---

### Post by needhelppeeps on 2012-07-15
In general, I think creating anything "short or easy" in the something you know category is going to a bad idea. The only acceptable answers I could come up with is something like voice or iris authentication or perhaps a card based solution such as a smart card reader. I'd make sure I could recreate the card somehow if it were lost (maybe an escrow agent?)

---

### Post by Dave_L on 2012-07-15
Another possibility:

xlock has an option -cpasswd for specifying an alternate password:

[http://manpages.ubuntu.com/manpages/gutsy/man1/xlock.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/xlock.1.html)

> xlock - Locks the local X display until a password is entered.
...
-cpasswd crypted-password
   The cpasswd option sets the key to be this text string to unlock
   xlock instead of password file.

xlock is available in the packages xlockmore and xlockmore-gl.

I haven't personally tried this.

---

### Post by BkkBonanza on 2012-07-15
Why don't you just use a shorter login password. If you're not concerned about physical access security and haven't used encryption then it's a bit pointless to use a long password. Something around 8 chars is easy to enter but not worth hacking when physical access is available.

ie. When you're gone I can power cycle your notebook and enter rescue mode to gain root access in less time than it likely takes you to enter your long password. So why have such a long password. It only makes sense if you need high security and in that case you should have an encrypted home or full-disk encryption.

---

### Post by Gagarin24 on 2012-07-25
**Dave_L** Than you, your second solution seems it could work, but I have a problem that my xlock version (xlockmore-5.31 64bit) can't recognise the -cpasswd option. I just installed the package with apt-get.

The first solution with sudo, I tried it but got some "bus" error. And even if it worked, it seems to me that login screen would require the long password.

**BkkBonanza** I use disk encryption, of course. I can see two possible scenarios of an attack: "hot" and "cold" or how I should call it?

*Cold* one is simple, someone steals my disk and runs brute-force or dictionary attack. To be safe I must have at least 60 bits of entropy in my password (for now), that is like 12 or more random characters, numbers and special chars. I can't change this password often, because it is difficult to remember and create.  I have to keep it from others, can't write it down, can't use wireless keyboard... 

The *hot* scenario is when someone "attacks" my computer when it is online. He/she can only guess the password and write it to a login box, if wrong he/she have to wait 5 seconds and than try again. (Maybe some vulnerability of linux can be exploited also, but I'm sure it would be fixed.) That 5 second delay is crucial, even like 15 bits of entropy password would take months to break. I don't need long password for this, actually I need short password so I can change it regularly and "lock screen" even when I go to the bathroom or answer the door.

There are also some ultra low-tech and high-tech scenarios how to obtain the password like torture, hidden camera, key-logger or memory dump... By the way computer speed doubles every year or so and that means that there should be added one bit every year to the long password to keep its strength. Short password don't have to change length.

---

### Post by Paddy Landau on 2012-07-25
> **Gagarin24 said:**
> ... my xlock version (xlockmore-5.31 64bit) can't recognise the -cpasswd option.
Hmm, I get the same result. I've been searching for an installable version of the latest (5.40), but found nothing. You can [download the source]("http://www.tux.org/%7Ebagleyd/xlockmore.html") and compile it yourself, but I don't know how to compile programs.

---

