---
title: "Seeking explanation of levels and generation for 'Backup2l' backup utilitly in Ubuntu"
date: 2016-11-30
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-30
Hi


I am seeking to use the 'Backup2l' utility to carry out backup for my data. Having looked at the various utilities pointed to by the various people on this forum, I am now looking at either Areca (almost there but not quite), 'UrBackup' and 'Backup2l'. I am leaning towards the last one - 'Backup2l' - I know its old and old fashioned (so am I) but it would suffice my needs.

I have gone through a lot of documents with reference to 'Backup2l' but I am still not clear as to how the various levels and generation come together and would greatly appreciate if somebody could please explain to me how does it all work with an example?

I will detail my needs here - please feel free to use this requirement or any another example for an explanaation of the above concepts of 'Max_Level', Max_Per_Level', 'Max_Full' and 'Generations'.

Here is what I would like to do with my backups :-

1. Create a full backup on day 1 - say on Sunday (week1)
2. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday) and retain them for completeness
3. Create a full backup on Sunday (week 2) - retaining the full backup and all the differential backups of week 1 for completeness
4. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday - week 2)and retain them for completeness
5. Create a full backup on Sunday (week 3) - retaining all the full and the differential backups from week 2 but none from week 1

The idea is to store 1 previous full set including the full and differential backups from the previous week and the full and the differential backups from the current week.

Hopefully, once I understand how to realize this, I might be able to automate the same using a cron job!


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-30
Hi



After doing some more reading about the 'Max_Level', 'Max_Per_Level', 'Generation' and 'Max_Full, this is how I think the process works (please either confirm or otherwise if I am on the right track so that I can specify these parameters correctly for my backup needs under varying circumstances) :-

Max_Per_Level	:	Number of differential backups made for each level of the ‘Max_Level’ backup
Max_Level     	:	Number of hierarchical levels for incremental backups.
                                Each differential backup at the 'Max_level'  or lower level forms the basis for the next differential backup for the next highest ''Max_Level' differential backups until the 'Max_Per_Level' number of differential backups have been reached for the 'Max_Level' differential backup

Detailed explanation to my understanding - for example, if Max_Per_Level = 5 and Max_Level = 4 and each differential backup is run once per day then :-

1.	The first day (day number 1) backup would be a full backup
2.	The next 5 daily backups would all be differential backups based on the above full backup. These backups would be assigned the highest ‘Max_Level’ number, in this instance, the number 4.
3.	The backups for the next 5 days from day number 7 through to 11, both inclusive, would all be differential backups based on the differential backup done on day number 2 that is, based on differential backup with identifier L4_1. These backups would be assigned the next highest ‘Max_Level’ number, in this instance, the number 3.
4.	The backups for the next 5 days from day number 12 through to 16, both inclusive, would all again be differential backups based on the differential backup done on day number 3 that is, based on differential backup with identifier L4_2. These backups would also be assigned the next highest ‘Max_Level’ number, in this instance, the number 3.

The process continues until ‘Max_Per_Level’ number of differential backups (in this instance 5) have been made using each of the differential backups at the next immediately higher ‘Max_level’, in this instance 4. Hence, at this point, there would have been 5 * 5 = 25 differential backups made at this ‘Max_Level’, in this instance 3. This is because, each of the 5 differential backups at the next immediately higher ‘Max_Level’ number of 4 forms the basis for the next 5 differential backups at the current ‘Max_Level’ of 3. This is reflected in the attached table.

		This process is repeated until all the differential backups at ‘Max_Level’ number of 1 are created. At the end of it, it would have created 5^4 + 5^3 + 5^2 + 5^1 = 625 + 125 +25 +5 = 780 differential backups. Following this, a new full backup would be created resetting the ‘Max_level’ and ‘Max_Per_Level’ counters to their start values.

A pdf file is attached to reflect the various differential backup generated at the relevant 'max_Level' and the 'Max_Per_Leve'.

Hopefully, this table would reflect my understanding of how these parameters are supposed to work together. 

However, what I still don’t fully understand is what makes up for a ‘Generation’ and how are ‘Generation’ number and ‘Max_Full’ number related.

Would it correct to presume that a 'Generation' in the above example would comprise of all of these 781 backups including :-
1 full back
5 differential backups at 'Max_Level' = 4
5 * 5 = 25 differential backups at 'Max_Level' = 3
5 * 5 * 5 = 125 differential backups at 'Max_Level' = 2
5* 5 * 5 * 5 = 625 differential backups at 'Max_Level' = 1

If that is the case, then wouldn't it be required that the 'Max_Full' number always be less than or equal to the 'Generation' number. Also, in the scenario, where the 'Generation' number equals 2, what purpose would be served with 'Max_Full' = 1. Wouldn't it be better to have 'Max_Full = 0 as the full backup then would anyway be a part of the'Generation'



Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-05
Hi All


Not chasing anyone - I fully realize that you all are busy!

I was just wanting to create the configuration file for my backup strategy and hence was trying to understand how it all works to ensure that I get the parameters values correct to realize my backup targets.


Best regards


Deepak

---

