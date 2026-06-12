---
title: "Cannot update to Firefox Version 2.0.0.4"
date: 2007-05-31
forum: Ubuntuzilla
---

### Post by apunc1 on 2007-05-31
I currenlty have Firefox 2.0.0.3 and installed through Ubuntuzilla script. When I try to update Friefox using the prescribed method I choose search for updates and there it searches and searches for awhile and never finds any updates or gives an error message.
I tried to update again and this time clicked "make firefox my default browser" as I thought that might be the problem. Then I received these messages in the terminal:
(Gecko:4596): libgnomevfs-WARNING **: Could not create per-user Gnome applicatio n-registry directory: /root/.gnome/application-info

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Cannot open '/root/.gnome/application-info /user.applications' for writing


What does these messages mean and how can I update Firefox?
Thanks,

---

### Post by apunc1 on 2007-05-31
> **apunc1 said:**
> I currenlty have Firefox 2.0.0.3 and installed through Ubuntuzilla script. When I try to update Friefox using the prescribed method I choose search for updates and there it searches and searches for awhile and never finds any updates or gives an error message.
I tried to update again and this time clicked "make firefox my default browser" as I thought that might be the problem. Then I received these messages in the terminal:
(Gecko:4596): libgnomevfs-WARNING **: Could not create per-user Gnome applicatio n-registry directory: /root/.gnome/application-info

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Deprecated function.  User modifications t o the MIME database are no longer supported.

(Gecko:4596): libgnomevfs-WARNING **: Cannot open '/root/.gnome/application-info /user.applications' for writing


What does these messages mean and how can I update Firefox?
Thanks,

edit: to clarify, when I try to download the updates the orange bar just goes back and forth and does not give me any error message.

---

### Post by nanotube on 2007-05-31
> **apunc1 said:**
> edit: to clarify, when I try to download the updates the orange bar just goes back and forth and does not give me any error message.

first, what exactly do you mean by "the prescribed method", could you please clarify, just to make sure we are all on the same page? :)

second, i'm not sure the 2.0.0.4 update has already been pushed out through the firefox updater. maybe it hasn't yet and you could try in another day or two? (i haven't checked it out yet myself) - i have too many tabs/windows open to be closing them all just now. ;)

---

### Post by apunc1 on 2007-05-31
> **nanotube said:**
> first, what exactly do you mean by "the prescribed method", could you please clarify, just to make sure we are all on the same page? :)

second, i'm not sure the 2.0.0.4 update has already been pushed out through the firefox updater. maybe it hasn't yet and you could try in another day or two? (i haven't checked it out yet myself) - i have too many tabs/windows open to be closing them all just now. ;)

the prescribed method to update the mozilla build of firefox on the ubuntuzilla site

> Update Official Mozilla Build of Firefox

If you already have the official build installed (e.g., by following the instructions above at some point before), you don't have to go through using the instructions in the previous section. You can use the built-in "Updates" functionality of Firefox.

In order for Firefox to update itself, it will have to be run as root. So quit all Firefox windows, and in a terminal, type:

gksudo firefox &

This will start Firefox as root. Select Help > Check for Updates from the menu, and it will find an update and download it. You will then get a message that says Firefox needs to be restarted to apply the update, and you can choose Later or Restart Firefox Now. Choose Restart Firefox Now. Firefox will restart again as root and tell you it's been updated. Now, you can close Firefox again, and then start it as normal from the menu, not as root. And you should be all good to go! 

It was pushed out to my windows work computer and my home mac so I figured I would go ahead and update my Ubuntu box while I was updating :p

Does anyone know what those gecko errors mean in the terminal?

---

### Post by DC@DR on 2007-05-31
I just tried out the installnewfirefox_3_2.0.sh from Ubuntuzilla project website and I can confirm that it works perfectly fine for me, updated to FF v2.0.04, copied all bookmarks and plugins to new FF version. So apunc1, you could give it another try, and btw, I'd like to thanks Ubuntuzilla for this painless, work-like-a-charm auto script, and keep up the good works! ;-)

---

### Post by nanotube on 2007-05-31
> **apunc1 said:**
> the prescribed method to update the mozilla build of firefox on the ubuntuzilla site



It was pushed out to my windows work computer and my home mac so I figured I would go ahead and update my Ubuntu box while I was updating :p

Does anyone know what those gecko errors mean in the terminal?

well, i'm not sure what those gecko errors mean, but they are just warnings, so presumably nothing fatal...
one way you could upgrade to 2.0.0.4 is to just run the ubuntuzilla script again and it will install the latest for you right on top of your 2.0.0.3.

---

### Post by nanotube on 2007-05-31
> **DC@DR said:**
> I just tried out the installnewfirefox_3_2.0.sh from Ubuntuzilla project website and I can confirm that it works perfectly fine for me, updated to FF v2.0.04, copied all bookmarks and plugins to new FF version. So apunc1, you could give it another try, and btw, I'd like to thanks Ubuntuzilla for this painless, work-like-a-charm auto script, and keep up the good works! ;-)

glad it worked out - thanks for your kind message. :)

---

### Post by apunc1 on 2007-05-31
> **nanotube said:**
> well, i'm not sure what those gecko errors mean, but they are just warnings, so presumably nothing fatal...
one way you could upgrade to 2.0.0.4 is to just run the ubuntuzilla script again and it will install the latest for you right on top of your 2.0.0.3.

ok i'll try that. i thought i may have to unisntall and then install again :p

---

### Post by nanotube on 2007-05-31
> **apunc1 said:**
> ok i'll try that. i thought i may have to unisntall and then install again :p

well, you could run the script with -remove first, to clean out your /opt/firefox directory, "just in case", but that really is not a necessity, afaik.

---

### Post by apunc1 on 2007-05-31
update: before reinstalling the script i thought i'd try to update again by opening firefox as root and updating. the first time i tried it looked like the update went through, told me to restart firefox. when i did, it then said the update had failed.
so i closed out, and tried again. this time the update finished successfully and i am now using v2.0.0.4. ;)  

nanotube, thanks for your help and interest. i agree, ubuntuzilla is much appreciated by me as well! 
am i the only one that had trouble updating? the script worked flawlessly for me during the initial install some weeks ago, but this was my first update attempt.

---

### Post by nanotube on 2007-05-31
> **apunc1 said:**
> update: before reinstalling the script i thought i'd try to update again by opening firefox as root and updating. the first time i tried it looked like the update went through, told me to restart firefox. when i did, it then said the update had failed.
so i closed out, and tried again. this time the update finished successfully and i am now using v2.0.0.4. ;)  

nanotube, thanks for your help and interest. i agree, ubuntuzilla is much appreciated by me as well! 
am i the only one that had trouble updating? the script worked flawlessly for me during the initial install some weeks ago, but this was my first update attempt.

i'm glad it all worked out at the end. :)
i have not had any trouble using the firefox updater, either using the "sudo" method, or the "gksudo" method, (several times back on the 1.5 branch, as well as all the minor updates from 2.0.0.0). you are the first one to report having problems with it... so it certainly doesn't seem like a pervasive problem. doesn't mean that you did anything wrong, could have been something on the network or whatever... there are so many things that can go wrong for no reason... :)

---

### Post by matchstich on 2007-05-31
i used the root command to update firefox and it went thru with no problems.
i have 2.0.0.4 now.
 saved that command  for the next update
thanks

---

### Post by nanotube on 2007-05-31
> **matchstich said:**
> i used the root command to update firefox and it went thru with no problems.
i have 2.0.0.4 now.
 saved that command  for the next update
thanks

cool. :)
no need to save the command though, it's posted up on the ubuntuzilla project site (see first link in my sig) under update instructions. :)

---

### Post by trishacupra on 2007-06-01
I updated to the latest version as root, it did a partial download but then fixed itself when it restarted, then I had to log out and log back in with my normal username to get Firefox to become the updated version. But not the type of problem you had.

---

