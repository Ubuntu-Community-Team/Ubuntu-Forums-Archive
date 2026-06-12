---
title: "help me know if i got hacked"
date: 2008-08-23
forum: Security
---

### Post by nephish on 2008-08-23
Hey there all,
i run a data processing station that gets info automatically via email. So i have a user set up and in my software, i have the user log in (dovecot) and check the email and process anything there. There are actually two users on the system that do this. 
Today, both lost permission to check their Maildir. 
I can't find anything in the auth log that looks suspicious, or the .bash_history of either user. Not even the main user of the system.
The way it got fixed was with a sudo chown mailuser /home/mailuser -R

I don't get what could have don't this. I have not been running any maintenance or anything else, it has just been happy running along.

Is this a cracker that did something? 
Has anyone seen this before? 

thanks for any tips, i wonder if it's ok to breathe now, or if it will happen again.

thanks

---

### Post by Gamma746 on 2008-08-24
Try installing and running chrootkit or rkhunter.

---

