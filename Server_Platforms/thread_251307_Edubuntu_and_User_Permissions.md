---
title: "Edubuntu and User Permissions"
date: 2006-09-05
forum: Server Platforms
---

### Post by cesera on 2006-09-05
I have recently helped setting up an Edubutu system at my son's school and they are generally very happy with it. There are however a few issues that could be improved.
 
First of all they would like to set up a system where different classes have access to different resources (shared areas, programs, etc). In order to avoid changing every users account at the end of each year to match the permissions of the next class, they would like to be able to group users by entry or exit year and then apply those permissions to the whole group in one go, that way they only need to make one change to permissions per class at the end of the year.
 
I could also not find an easy way to modify the menu system on a per class basis, i.e. all the users in one group (or profile, or whatever).
 
Is there an easy, preferably GUI driven, way to do this kind of things? If not can it be done from the command line (I probably would have to write some scipts, but that is not a problem as long as I know what needs to be done to accomplish this).
 
Finally the default user admin tool seems to be very limited as to what groups a user in a profile gets added to. Can I easily add new groups/permissions to that? Also is it possible to change a user's profile after they have been created, and so change all their permissions? Or change a profile and thereby all the users in that profile? I presume this comes back to my first question.

 
I know these are a lot of questions, but I cannot imagine no-one has ever come across the same problems before, so instead of re-inventing the wheel I hoped I could draw on someelse's experience.
 
Thank you very much.

---

### Post by sysops on 2006-09-05
I don't know what exactly you mean when you use the term 'profile' but in user management (as i know it atleast) it refers to a directory where each users settings are saved, things like desktop menus, backgrounds, browser histories, etc are saved. I have found that it is easier to setup group profiles rather than individual user profiles whereby an entire group shares the same profile. So, if for e.g. you wanted all year 8 students to migrate over to year 9 and inherit the year 9 profile, you would initially setup a user, change things like the desktop, menus, etc etc, set that user's homedirectory (/home/group09 maybe) as read only and then set everyone in the group #09 to use that directory as their homedirectory. Note, it has to be set _readonly_ otherwise you have conflicts across different users' logons, certain files however need to be writable, but their status could be reset once the user has logged off (via scripts again).

So ultimately you could have something like this

user:JDoe - group:07 - homedir:/home/group07 - personaldir:/home/users/jdoe
user:Bsmith - group:09 - homedir:/home/group09 - personaldir:/home/users/bsmith
user:ADonald - group:10 - homedir:/home/group10 - personaldir:/home/users/adonald

This way, you set permissions and administer students as a whole via the groups and each student gets to keep files in their personaldirs across the many years they will be at the school.

---

### Post by sysops on 2006-09-05
also have a look at this, perhaps more to what you're looking for

[https://wiki.edubuntu.org/EdubuntuDynamicMenus](https://wiki.edubuntu.org/EdubuntuDynamicMenus)

---

