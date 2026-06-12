---
title: "2 Users?!?! WTH?"
date: 2006-04-14
forum: Server Platforms
---

### Post by Farbi on 2006-04-14
Hello all, 
This may very well be the wrong thread to be posting in... Please correct if wrong to all you mods out there :~) (and with my apologise)

Onto the meat of the matter.
I'm using 5.10 (breezy) all current updates as of 4-13-06 ~1400 hours.  While waiting for a batch of .ogg's to convert to mp3's I noticed that I had 2 users logged into my computer.  I turned off my Eth controller ASAP.  Restarted the desklet that was telling me I had 2 people logged in.  and it said that I still had 2.  Restarted leaving the ethernet controller off.  said only one user for about 10 minutes turned ethernet controller back on.  Within 5 minutes I had 2 again.  What gives?

I fully offer that I am a complete noobie with Ubuntu and/or linux.  
I will be happy to offer any information that you might need to help me fix this (with some minor details that I will flatly refuse you :)  :p )  Anyhow I installed etherape and ethereal to see if any strange IP's were attached that I didn't recognize, just one but it's been there before without the 2 users problem.  

I look forward to any responces that you can offer.
Thank you in advance
Farbi

---

### Post by ubernoob on 2006-04-14
I guess you didn't try the commands "who" or "finger"?

If you log in to a terminal as well as gnome it is normal to have two users logged inn. Check those commands to see which users are online, and from what kind of terminal.

---

### Post by Farbi on 2006-04-14
No... No I did not use those commands... However in my defense I did not know that they exsisted.  Another case in point that I should RTFM a little more I guess.  I'll look into those commands and find the syntax and such for them.  It has not happend since I posted last night and I didn't change anything.  I'm wondering if I gnome-terminal and use sudo does the computer consider that 2 logins or am I chasing wild geese?  Anyhow I'll remember those two commands the next time I notice that it happens.  

Thanks for the quick response

farbi

---

### Post by ubernoob on 2006-04-14
I not able to check that now, but i think that there will be 2 users when you do that. Another solution is checking the log:
less /var/log/auth.log
I'm very sure you are fine.

---

### Post by 5-HT on 2006-04-14
[quote=Farbi]No... No I did not use those commands... However in my defense I did not know that they exsisted. Another case in point that I should RTFM a little more I guess. I'll look into those commands and find the syntax and such for them. It has not happend since I posted last night and I didn't change anything. I'm wondering if I gnome-terminal and use sudo does the computer consider that 2 logins or am I chasing wild geese? Anyhow I'll remember those two commands the next time I notice that it happens.

Thanks for the quick response

farbi[/quote] 
As ubernoob indicated, if you are logged on to your account in X, two users will be shown using the 'w' or the 'who' commands.

Why? One for the X session, and one for the subshell you run the command in. Each additional terminal you open will count as an additional user.

To test this out, open up a terminal in X and you'll see two users. Open up an additional terminal and you'll see three users. 

If you logout of your session and login to a virtual terminal (say, tty1), you will only see one user.

Nothing to worry about if this is what you are referring to.

HTH

---

