---
title: "Can't chmod on nouser:nogroup files"
date: 2009-04-03
forum: Server Platforms
---

### Post by PryGuy on 2009-04-03
Good day!
This is probably the best section to ask this question. Say, I have a folder on server called 'public' and it is shared and all the files copied there via Samba there belong to nobody:nogroup. I tried to make one of the files there executable using chmod without root privileges. I did it this way:```
chmodchmod 775 /home/peter/shares/piblic/file
```But I failed of course 'cause 'peter' did not belong to 'nogroup'! I added the user 'peter' to the 'nogroup' group so the 'groups' output now looks like this:```
peter adm dialout cdrom plugdev lpadmin **nogroup** admin sambashare
```But it didn't help! It still says 'Operation not permitted' :icon_frown:
Where's my problem? Thank you in advance!

P.S. In other words the question is fundamental. Can a group member (but not owner) change permissions on files?! I feel lost. :)

---

### Post by BkkBonanza on 2009-04-03
you need to be root to change perms. Use sudo chmod

---

### Post by PryGuy on 2009-04-03
I changed it with sudo perfectly, thank you! You mean I can't change rights for the files that do not belong to me, even if I belong to the group they belong to? Just want to make sure...

---

### Post by BkkBonanza on 2009-04-03
I think you have to own the file or be root. I could be off a bit though. 
My memory is fading faster nowadays...

---

### Post by PryGuy on 2009-04-03
Well, that's a fundamental thing I HAVE to know :). Thank you!

---

### Post by PryGuy on 2009-04-03
Yes, I found it!> The chmod command can only be sucessfully executed by either the current owner of the file or by a super-user. Group membership or directory ownerships mean nothing in this case. If it worked any other way, there would be a huge security problem.[The source]("http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1238774164307+28353475&threadId=1008588")

---

