---
title: "E-Sword"
date: 2007-06-21
forum: Ubuntu Christian Edition
---

### Post by casawyer on 2007-06-21
I just got Christian Ubuntu installed on my computer.  I was trying to set up e-sword and it installed like it should and I used the manager to download bibles and other items, but when I click on e-sword to bring it up, nothing happens.  Any suggestions?  

Charles

---

### Post by tak1150 on 2007-06-21
Did you do a security update before you tried to install e-sword?
I noticed that the current version of Wine (which helps you run e-sword) does not let you install e-sword for some reason (version 0.9.39).

If this is the case, go to synaptics and find wine, then click on package and select force version.
Then set it to 0.9.33 (or anything other than 0.9.39).

After that you probably have to reinstall e-sword.

---

### Post by casawyer on 2007-06-23
Thanks for the help.  That worked great and now it is up and running.   

Charles

---

### Post by tmeier on 2007-06-26
I had a similar issue.  I also downgraded wine back to 0.9.33.  It looked as if it installed properly, but it did not change the launcher in the Accessories Menu.  When I try to Launch E-Sword it still shows E-Sword Installer.  I can go to : /usr/local/apps/esword4linux/runesword and run that application and with some errors esword runs but that is not ideal.  thanks for any ideas you may have.

Thomas

---

### Post by tak1150 on 2007-06-26
This is a cheap fix, but...

You can go to
System --> Preferences --> Main Menu --> Accessories

Right click on e-Sword (or e-Sword Installer) and select property.

Then where it says command, type
/usr/local/apps/esword4linux/runesword

where it says name, type "e-Sword"

Then hit close

You may have to logout/in. The button for e-Sword module installer might give you an error message saying you need to install e-Sword, but you could use the same trick as here.

---

### Post by benjoseph on 2007-06-26
Please I have only recently installed Linux Ubuntu, I do not understand the security thing. Can you be more specific? 

Thanks

---

### Post by tak1150 on 2007-06-26
What I meant by security update is the thing that looks like this:

[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/7/7d/Screenshot-Update_Manager.png/250px-Screenshot-Update_Manager.png[/IMG]

If you have done that, the update manager would have updated Wine to 0.9.39, which does not let you install e-Sword, but if you haven't done the update, the default version of Wine is 0.9.33, which allows you to install e-Sword.

Alternatively, you could wait till they come out with 0.9.40, which I'm sure won't have the same bug as 39 (they release new versions very often).

Tak

---

