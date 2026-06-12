---
title: "Separating root privileges and filter admin. Help?"
date: 2006-09-06
forum: Ubuntu Christian Edition
---

### Post by drewu on 2006-09-06
I have just installed Ubuntu CE and wonder if it would be possible to separate root privileges (installing software, configuring stuff) and filter admin (what gets blocked) with two separate passwords (or acounts). I would like to keep the filter untouchable to the root user and to the regular user. Any way to do this? The my goal is to set up a box that my son can explore safely without danger (oxymoron?).
Thanks for your time and help.
Edit:
I have also noticed that the defualt root password is blank or empty.
Also, every time I try to acess the button at System -> Administration -> Users and Groups, the root password is asked, and upon pressing [Ok] my computer continues to silently do nothing. What is up here?
Edit # 2:
Oops. figured out the second problem. Just being a hairbrained.](*,)

---

### Post by mysticrider92 on 2006-09-06
In Ubuntu the first account that you make is root and all others have regular non-root permissions and I don't think you can change this. One thing you could try is making a password protected folder and putting the filter configuration files in it. I am not sure how to add a password to a folder, but someone else may know. In Linux, you can do just about anything if you know what to edit, so it is possible.

---

### Post by drewu on 2006-09-06
Thanks for the tip.

btw- I like your signature

---

### Post by mysticrider92 on 2006-09-06
Any time. I wish I could help you more, but I can't think of anything else.

I got the text in my signature from someone's sig on the Playstation Underground forums. He had a picture to go with it.

---

### Post by mhancoc7 on 2006-09-06
> **drewu said:**
> I have just installed Ubuntu CE and wonder if it would be possible to separate root privileges (installing software, configuring stuff) and filter admin (what gets blocked) with two separate passwords (or acounts). I would like to keep the filter untouchable to the root user and to the regular user. Any way to do this? The my goal is to set up a box that my son can explore safely without danger (oxymoron?).
Thanks for your time and help.
Edit:
I have also noticed that the defualt root password is blank or empty.
Also, every time I try to acess the button at System -> Administration -> Users and Groups, the root password is asked, and upon pressing [Ok] my computer continues to silently do nothing. What is up here?
Edit # 2:
Oops. figured out the second problem. Just being a hairbrained.](*,)

Yeah, I don't think this is possible. There may be a workaround like the one mentioned above, but I am just not sure.
Thanks, Jereme

---

### Post by joegeek on 2007-07-08
> **mysticrider92 said:**
> In Ubuntu the first account that you make is root and all others have regular non-root permissions and I don't think you can change this. One thing you could try is making a password protected folder and putting the filter configuration files in it. I am not sure how to add a password to a folder, but someone else may know. In Linux, you can do just about anything if you know what to edit, so it is possible.

So when I made the account "guest" during the install process, I accually made this guest account root?

---

### Post by mysticrider92 on 2007-07-08
So you named the first account 'Guest'? Then yes, it does have sudo/su privleges. I would make another account for guest and rename the first one you made.

---

### Post by TravMan63 on 2007-08-09
Yes - this is possible - but it's messy...

You will have to change permissions on home folders etc.

I did the same thing - set up 1st user as root, then demoted them - and placed new user as root.  I don't have as much hair left anymore tho ...

You can read more about my misadventures here 
[http://ubuntuforums.org/showthread.php?t=491489](http://ubuntuforums.org/showthread.php?t=491489)

actually - it all turned out alright.  It was just fun for a while...

>edit password protect
hmm - well - you can chmod to the folder in question - the root password would be needed then... unless you gave ownership to another user...
hmm - as long as your w/r/x permissions allowed you to use it (r I suppose) - then chmod should do it... 
what's the chmod # ? depends on what exactly you want to do...

---

### Post by urukrama on 2007-08-10
If you don't want the first account to have sudo privileges, change the settings in System > Administration > Users and Group (select the user and deselect administrative priviliges). It isn't very hard.

---

### Post by TravMan63 on 2007-08-11
I checked the repos for elive/debian - there are a couple of packages you might want to look into:

lockoutsecurity
and
lockedfile

TM

---

