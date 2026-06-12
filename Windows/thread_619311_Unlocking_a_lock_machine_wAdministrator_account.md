---
title: "Unlocking a lock machine w/Administrator account"
date: 2007-11-21
forum: Windows
---

### Post by adampyre on 2007-11-21
Hello,

My colleagues are telling me there is a way to unlock a locked pc or log into a pc as any user using the admin credentials. Apparantly you do not need to know the users password, but just log in somehow using the administrator password. I am not speaking of logging the user off and logging in as the administrator as you can easily do, but unlocking the workstation when the user locked it, with the administrator account and or password. Anyone know the format/method of doing this?

Thanks!

---

### Post by mellowd on 2007-11-21
I only know of a way of cracking the password when the user is logged off. What version of Windows are you referring to and did your colleague actually show this being done or he just "heard about it" ?

---

### Post by adampyre on 2007-11-21
This is for Windows XP at least. 2 of my colleagues who I respect and trust mentioned they heard of a way to do this, but don't know how. It's built into the OS, not using a third party app. According to them, there must be a format of entering the administrator log in credentials to unlock the pc a user has locked, and stay on that users log in. This would be helpful when we need to get into a users account to modify an app running on their log in but they are away from their PC. It also seems like a good way to make changes to their PC without logging them out and potentially making them lose any data they have open.

Thanks!

---

### Post by mellowd on 2007-11-21
The problem with this setup is that its a giant security risk. Yes it could be useful but then anyone who knows the method could be destructive with it. I know of a way to take ownership of files, even those you don't have access to but not this.

---

### Post by adampyre on 2007-11-21
Well, really, I don't see it being a huge security risk. To do this method you would have to already know what the administrator password is. I'd say your security has already been compromised at that point so it wouldn't hurt to have a method for this...

---

### Post by mellowd on 2007-11-21
Wait a minute, I'm not reading your question correctly.

Of course this is possible. If the person has locked their computer all you need to do is ctrl+alt+delete then remove their user name. Enter the administrator name and password and you'll get to the desktop.

---

### Post by adampyre on 2007-11-21
That's not quite what I am looking for. Using the method you describe above, it will log that user off and allow you to log onto the workstation as the administrator. What I am attempting to do is log in as the user who locked the computer without logging them off, but I don't know their personal password. I would log into their existing session but using the administrator password/login.... see what I mean?

---

### Post by mellowd on 2007-11-21
I see, but that would then allow you to send emails from their exchange account because they would still be logged in. I don't see any good in that.

---

### Post by LaRoza on 2007-11-22
You could just restart the computer if it were locked.

---

### Post by inversekinetix on 2007-11-22
just switch user, you dont need to log anyone out, you can have multiple users logged in at the same time on xp.

---

### Post by mellowd on 2007-11-22
I think what he is trying to do is log on as the logged on user. i.e. user a has locked his desktop. I come round and using my admin password I unlock the user a's desktop.

I really don't think it's possible this way

---

### Post by smoker on 2007-11-22
you could log on as admin, go to users accounts and change his/her password, then access the account,  could you not? of course you would have to advise the user of the password change!

---

### Post by rickyjones on 2007-11-23
The only solution I know of is if this is a domain. In that case through Active Directory just reset the users password to something that you want to use. Then unlock the computer with that new password. Then tell the user to change it again.

---

### Post by adampyre on 2007-11-23
We thought of this idea, but this would be annoying for most users who have trouble remembering their original password in the first place. If I have to log into a CPU several times a month this could be a problem. The user would have to change their password that many times.

I spoke with another person who claims they used to know how to do this, but they can't remember.... so the myth and legend lives on.... I guess I'll keep waiting for the guru who has the answer...

---

