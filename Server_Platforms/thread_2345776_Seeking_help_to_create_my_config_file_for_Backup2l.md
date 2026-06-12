---
title: "Seeking help to create my config file for Backup2l"
date: 2016-12-08
forum: Server Platforms
---

### Post by agarwaldvk on 2016-12-08
Hi Everybody

I am now looking at using Backu2l to create a scheduled backup job to realize the following backup strategy for my home network drives :-

I will detail my needs here - please feel free to use this requirement or any another example for an explanaation of the above concepts of 'Max_Level', Max_Per_Level', 'Max_Full' and 'Generations'.


1. Create a full backup on day 1 - say on Sunday (week1)
2. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday) and retain all of these 6 differential backups
3. Create a full backup on Sunday (week 2) - retaining the full backup and all the differential backups of week 1
4. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday - week 2)and retain all of these 6 differential backups
5. Create a full backup on Sunday (week 3) - retaining all the full and the differential backups from weeks 1 and 2
6. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday - week 3)and retain all of these 6 differential backups
7. Create a full backup on Sunday (week 4) - deleting the full and the differential backups from week 1 but retaining all the backups weeks 2 and 3

In other words, I want to retain 2 backup sets (in this case, I would think that that a backup set comprises of the full backup and all the subsequent differential backups based on the immediately previous full backup - this would facilitate the restoration of the files as they were on any day between any 2 full backups - and the current partial backup set which should comprise of the full backup and as many differential backups as have been done this far. 

I just want to know what the values for the various parameters viz 'Max_Level', Max_Per_Level', 'Max_Full' and 'Generations' should be.

I believe to realize my above backup strategy, these values will do (but please feel free to correct me) :-
Max_Level = 1
Max_Per_Level = 6
Max_Full = 3
Generations = 2

The intent is to then create a cron job (to be setup later) to run this backup script everyday.

Any assistance on this would be highly appreciated. 


Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-18
Hi Everyone


Any suggestions on this please or no one uses this application any more? I do realize that this is an old one but I think it will do for me.


Best regards


Deepak

---

