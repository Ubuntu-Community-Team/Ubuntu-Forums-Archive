---
title: "Cron Job not working"
date: 2012-10-16
forum: Server Platforms
---

### Post by zaio on 2012-10-16
Hello

I add a cron job form webmin

When i run it i have no problem 
but on the schedule time the cron is not working 

I try to run it from the terminal and i didn't have problems 

the command is 
```
/usr/bin/php /webbroot/cli/akeeba-backup.php --profile=1    
```

I add webroot to hide my real path 


Can some one help me

---

### Post by papibe on 2012-10-16
Hi zaio. Welcome to the forums! ):P

cron has a very limited environment. Several environment variables are either not present or very limited (for instance the path).

Check your script so there is no calls to programs without a full path. Also, double check is you are taking advantage of any environment variable.

Let us know how it goes.
Regards.

---

### Post by zaio on 2012-10-16
I'm sorry but i'm new in the linux world


i don't know how to make this test like i said 
i add the cron job in Webmin 

i try to run it directly from the terminal and it is working but when it it comes time for the schedule time it is not working i read in somewhere that i can see the cron job in crontabs 
with
```
crontab -l 
```the result is this 

```
2,16 21-22 2,4,6,8,10,12,14,16,18,20,22,24,26,28,30 * * /usr/bin/php /webbroot/cli/akeeba-backup.php --profile=2    #My automated backup
35 22 1,3,5,7,9,11,13,15-17,19,21,23,25,27,29,31 1-12 * /usr/bin/php /webbroot/cli/akeeba-backup.php --profile=1      #My automated backup

```I apologize for my english

---

### Post by papibe on 2012-10-16
I'm not much of an expert on php, but if you post your script, either me or other forum's users may come up with specific suggestions.

Regards.

---

### Post by zaio on 2012-10-16
the script i use is commercial and i don't think it from the php script they have very specific instruction 
how to setup the cron job 

the strange think is that if i manually start the command for the cron job it is **working**

---

### Post by papibe on 2012-10-16
> **zaio said:**
> the strange think is that if i manually start the command for the cron job it is **working**
That's a very common sign of the situation that I described before. In other words, the person/team who wrote the script assumed an interactive environment.

If correcting the script is not an option for you, you may want to try this: create a bash script that tries to get as much of the interactive environment as possible and from there call the php script.

Let us know how it goes.
Regards.

---

### Post by zaio on 2012-10-17
I fix it thanks for the fast support

---

