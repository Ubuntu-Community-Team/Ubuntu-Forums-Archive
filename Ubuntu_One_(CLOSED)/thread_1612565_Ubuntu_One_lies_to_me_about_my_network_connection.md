---
title: "Ubuntu One lies to me about my network connection"
date: 2010-11-03
forum: Ubuntu One (CLOSED)
---

### Post by Dynamic Man on 2010-11-03
Ubuntu One says I have no network connection, which I obviously have, writing here on the forums.

What I have done:

* Installed Ubuntu 10.10 
* Logged on to my wifi network
* Installed all the available updates
* Rebooted
* Installed the restricted nvidia drivers
* Rebooted
* Tried to log on to Ubuntu One (System -> Preferences -> Ubuntu One)
*** Email and password was accepted, but nothing more happens and I don't see my account details in the Ubuntu One Preferences window.
*** When looking in folders like ~/Pictures/ i get the message "Operations on this folder are disabled because there is no network connection"

---

### Post by duanedesign on 2010-11-06
Sorry to hear Ubuntu One is not working as expected. Could you please open a Terminal and run this command:
**NOTE:** the commands are u'one'sdtool, not ul

```
u1sdtool -c
```

give it a minute or so then run:

```
u1sdtool -s
```

Please post the output from the second command.

thank you,
duanedesign

---

### Post by jimbo99 on 2010-11-10
In my case, when I bring up the Ubuntu One preferences my system's CPU utilization would skyrocket for long periods.  It didn't make the system unusable, but it was noticeable.

In observing the preferences dialog box I see ALL of the fields that would display data about me and my account are blank.

After issuing the u1sdtool -c and then -s it seems to now display that information.  

Why don't you incorporate into that dialog box those two commands so that we don't have to go to the prompt to issue them and make the inevitable mistake of using the letter "l" instead of the numeric "1"?

---

### Post by Dynamic Man on 2010-11-11
Hello, and thank you for replying to my post. Unfortunately I "solved" the problem before I saw your reply, by logging in to [http://one.ubuntu.com](http://one.ubuntu.com) in my web browser, which appearantly made U1 understand that my network connection existed.

However I'm getting seriously fed up with the extremely long periods of time it takes to sync files, and this with a few other ugly bugs makes me unwilling to use U1 at all, at the moment. 

I used the instructions at [https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIStopSyncingAFolderOutsideTheUbuntuOneFolder]("https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIStopSyncingAFolderOutsideTheUbuntuOneFolder") to stop syncing my folders (since the GUI options didn't seem to work) and will try it out again in Ubuntu 11.04.

When U1 reaches a level of usability that is anything near acceptable to me, my intention is to become a paying customer ASAP, but right now I simply can not see myself give my support - moral or economical - to this product. I'll just make a general donation instead. ([http://www.ubuntu.com/community/get-involved/donate]("http://www.ubuntu.com/community/get-involved/donate") for anyone interested in doing the same..)

---

### Post by stmiller on 2011-01-17
For me I had to open System > Preferences > Ubuntu One

Then under the Devices tab click Connect (or restart).

Not sure why this is not happening automatically,

---

### Post by grahammechanical on 2011-01-18
I found that all I had to do was update a file or document in my local Ubuntu One folder and the update process will begin automatically. The system>Preferences>Ubuntu One method is there to give some kind of user control. In my opinion.

Things are slow the first time you sync and if you have a lot of files to upload but if you only update a few files then, I have found that slowness is not such a big issue.

Regards.

---

