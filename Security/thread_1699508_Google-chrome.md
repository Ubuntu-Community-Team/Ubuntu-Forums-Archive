---
title: "Google-chrome"
date: 2011-03-03
forum: Security
---

### Post by Muadib25 on 2011-03-03
Greetings!

I just migrated from Fedora 12 and I am new to Apparmor. The reason I am writing this post is because I have issues with Google-chrome, since the program cannot download due to some default restrictions that the system applies to it. 

I searched /etc/apparmor.d/ for any Google-chrome profiles but found nothing. 

Can U help me please?


Thanks in advance!
Muadib25

---

### Post by kerry_s on 2011-03-03
what? go here, click download, select 32 or 64, whatever your using, then click accept.

[http://www.google.com/chrome?platform=linux](http://www.google.com/chrome?platform=linux)

---

### Post by rookcifer on 2011-03-03
OP, you will need to provide more details as to what errors AppArmor is giving.

Also, are you trying to download Chrome from the repos?

---

### Post by Muadib25 on 2011-03-04
My apologies, I should clarify better...

I use Google-chrome now, the issue I am facing is when I am trying to download a file through Google-chrome. Example: a .deb file or whatever.

I tried to choose different download directories, the only thing that works is ".config/google-chrome/"

Is there any way to allow the program to download, say, in the Desktop?



Sorry for the mess...
muadib25

---

### Post by kerry_s on 2011-03-04
click on the wrench, select preferences, under the hood, in the download section click "browse".

---

### Post by Muadib25 on 2011-03-04
Hehe, I guess you didn't understand me...

Something is blocking Google-Chrome from downloading files...I know of course how to change DL dirs on Chrome! :P

---

### Post by kerry_s on 2011-03-04
> **Muadib25 said:**
> Hehe, I guess you didn't understand me...

Something is blocking Google-Chrome from downloading files...I know of course how to change DL dirs on Chrome! :P

does it throw a error? if so grab a pic & attach it.

---

### Post by Kobalt on 2011-03-04
How did you install Google Chrome, and what version of Ubuntu are you using ?

Also, apparmor logs are in */var/log/messages*

---

### Post by nrundy on 2011-03-04
> **kerry_s said:**
> what? go here, click download, select 32 or 64, whatever your using, then click accept.

[http://www.google.com/chrome?platform=linux](http://www.google.com/chrome?platform=linux)

Install Chromium from the repos. Don't download from Google.

---

### Post by rookcifer on 2011-03-04
> **Muadib25 said:**
> My apologies, I should clarify better...

I use Google-chrome now, the issue I am facing is when I am trying to download a file through Google-chrome. Example: a .deb file or whatever.

I tried to choose different download directories, the only thing that works is ".config/google-chrome/"

Is there any way to allow the program to download, say, in the Desktop?



Sorry for the mess...
muadib25

Unless you are using an AppArmor profile, Chrome should NOT be restricted in where it can download files within your /home directory.

So, are you using an AppArmor profile or not?

---

### Post by Muadib25 on 2011-03-04
Sorry people my mistake!

Although in my migration from Fedora I took the care to have the same name in my normal user, the directories copied did not have the permissions that they should. A 'sudo chown' corrected that!


My apologies, I was misdirected by an article I read about apparmor while browsing the net. :popcorn:


All best,
Muadib25

---

