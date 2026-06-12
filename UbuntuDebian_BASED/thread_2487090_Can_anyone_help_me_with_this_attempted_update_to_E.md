---
title: "Can anyone help me with this attempted update to Elementary OS operating system"
date: 2023-05-22
forum: Ubuntu/Debian BASED
---

### Post by straitsfan on 2023-05-22
Hello all --

It's been a while, and I think I need some guidance if anyone can offer it.  For the past few days i've tried to update my operating system, and I get this message:

Failed to update Operating System updates
This may have been caused by external or manually compiled software.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Not sure what is going on here.  I have done updates to the OS with no problem recently, so I'm not sure what's holding up this particular update.

One more thing:  I keep getting notifications from a website that I've not subscribed to or read.  The site is called Patheos.  I'm not sure where to look to stop these notifications.    Any advice for this as well?  I'm using Firefox if that helps or means anything.  Never had notifications pop up before.  All of a sudden I'm getting notifications from this site.   I think there may be something in Firefox that needs to be changed, but I don't seem to be able to find it.

---

### Post by MAFoElffen on 2023-05-22
Since yours is not an Ubuntu OS, and this is an "Official Ubuntu Support" Forum Section, this will most probably be moved to the Other OS discussion Section...

Shouldn't you rather be asking this question to other Elementary OS users on either:
[https://elementaryforums.com/index.php](https://elementaryforums.com/index.php)
[https://elementary.io/support](https://elementary.io/support)

---

### Post by straitsfan on 2023-05-22
My apologies.

---

### Post by QIII on 2023-05-23
Moved to *** Ubuntu/Debian BASED.***

---

### Post by Frogs Hair on 2023-05-23
Run the suggested command in the terminal without opening the software updater. As for the website, it reads as if permissions for notifications were granted and you can go to the privacy and security settings> manage data to clear any cookies from that site.  
```
sudo dpkg --configure-a  
```

---

### Post by straitsfan on 2023-05-24
Thank you so much -- it worked.   Wonder what was holding it up.

---

### Post by yancek on 2023-05-25
>  This may have been caused by external or manually compiled software.


The error message above which you had in your initial post was likely the problem.  Installing software from outside the repositories.  When you get a suggestion to run a command in a situation like yours, that is the best first option as you found out.  When you are having such problems it is also best to make note of what you have done and the results so if you have a similar problem again you know the solution.  Also if you try something and it fails, you know that isn't the solution and you can post that information here when you have a question.  You might take a look at your /etc/apt/sources.list file to see what software is installed.

---

