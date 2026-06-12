---
title: "i might be cracked unless this is a bug"
date: 2009-06-29
forum: Security
---

### Post by cmay on 2009-06-29
hi.
last night i was just about to be going to bed  so i wanted to turn of the computer. 
this message appear that system policy prevents me from shutdown the machine and wants password. 
so i figure i had to be able to prove someone had been into my machine so i took a screenshot  of the message  and a terminal running the command w which shows nothing abnormal. 

i attached the screenshot and i would very much like your opinion on this. 

thanks.

---

### Post by Nepherte on 2009-06-29
As far as I can see, there's nothing odd to it. You're logged in twice, so to speak:
- tty7 which is the default virtual terminal where x starts itself
- pst0 because you have a terminal window open.

I get the same output for users on my system.

---

### Post by cmay on 2009-06-29
> **Nepherte said:**
> As far as I can see, there's nothing odd to it. You're logged in twice, so to speak:
- tty7 which is the default virtual terminal where x starts itself
- pst0 because you have a terminal window open.

I get the same output for users on my system.

yes i agree there is nothing wrong on the output of w.
but i never before had to give a password to shutdown and the message is pretty clear that a other user is logged into to the system. 

the message and the output of w does not add up so i think maybe a bug somewhere but on the other hand if a cracker really got in before the w command could be modified so it will not report anything. 

i am not sure still what to make if this. 
the message is that i can not be allowed to shutdown as long as ohter users are logged on to the system. this has never happen before .

what could be the caurse of this unless this is really some one logged in. i did not use the terminal or anything at the time. i was listing to music and i just ran a quick google search before turning of the music. then i went to the bathroom and got back to shutdown. when trying to shutdown the messagebox told me there was someone logged in. i have also never logged in twise on the system. 

this is not normal behavior  as far as i can see.

---

### Post by cmay on 2009-06-29
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/287715](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/287715)

its a bug. 
there was simply somethings that did not add up in the message versus the output of w so i asked at the new os talk also. 

the good guys found this above link for me and if i can remember the passwd for my launchpad account i will let them know i am affected by this bug also.

---

