---
title: "Default Desktop for Windows User's"
date: 2008-07-07
forum: Server Platforms
---

### Post by Benismyhorse on 2008-07-07
Hi, thanks everyone for all the help, I am so close to using Ubuntu in our school environment, but I need one last bit of help, I really need to give the network users a default desktop, but one that they wouldn't be able to change things on.
Info:
Windows 2003 domain
Used Likewise to join
Change a samba file so can just logon using USERNAME not DOMAIN/USERANME
Ubuntu 8.04

Thanks so much.

---

### Post by Tomatz on 2008-07-07
Open a terminal and type:

```
sudo apt-get install Pessulus
```

Now you will have a nice gui to lock down different parts of your gnome (ubuntu) desktop.

To run it go to **System, Administration, Lockdown Editor**

;)

---

### Post by Benismyhorse on 2008-07-07
Hi, have tried that program, but what I am really looking for is a way to make a default desktop for the domain users with all the icons to programs they would need and then I would just uninstall the Gnome Panel Thanks

---

### Post by ad_267 on 2008-07-07
The package sabayon allows you to set up the default desktop.

---

### Post by Tomatz on 2008-07-07
> **Benismyhorse said:**
> Hi, have tried that program, but what I am really looking for is a way to make a default desktop for the domain users with all the icons to programs they would need and then I would just uninstall the Gnome Panel Thanks

The beauty of gnome (gtk2) is that you can drag and drop anything...

Just drag launchers of the apps you want to use from the menu, on to the desktop. Its as simple as that.

You can even r-click on the desktop and create a launcher using a command. E.g. **gnome-terminal** will create a launcher that will launch the terminal ;)

---

### Post by Benismyhorse on 2008-07-07
Thanks, So with Sabayon can I create a default desktop and get it to load on everyones account? and where would I get the latest version of Sabayon,
Thanks for all the help

---

### Post by ad_267 on 2008-07-07
You can install Sabayon from the repositories. Just "sudo apt-get install sabayon" or use synaptic.

I haven't actually used sabayon myself but yes that's what it's supposed to do. [http://www.gnome.org/~seth/blog/sabayon](http://www.gnome.org/~seth/blog/sabayon)

---

### Post by Benismyhorse on 2008-07-07
OK will try that and hope to god it works because it's the only thing holding me back from installing it all round the school

---

### Post by Benismyhorse on 2008-07-07
Hi,
Have tried Sabayon and looks like it is all good and working, make a desktop how I want it, then save, make it the default for all users, but when I log on nothing is like the one I setup in sabayon.
Does anyone have any other ideas, 
Thanks for the help so far,

---

### Post by Benismyhorse on 2008-07-07
OK, rebooted my Ubuntu Box I am working on and logged on and :)The things I have changed have been changed (But not the desktop Background :confused:Help Please:confused:) now the only problem there is which is still holding be back is that we have a couple of students at the school who like to try and change things on computers, and I would like to make the icons on the desktop locked so the can't be deleted.
If they are deleted atm they come back after a log off & in but is there anyway for the students to be able to use the shortcut/luncher but not be able to delete it.
Please help,
Thanks Shane

---

### Post by ad_267 on 2008-07-08
I guess you could make them read only, but if the user owns it then they could change the file permissions. So you would want to somehow make the users desktop owned by root. Not sure how you would get this set up for all users though, someone else might know.

---

### Post by Tomatz on 2008-07-08
```
gksu nautilus
```

Then open the home folder (root nautilus). Then r-click on the Desktop folder and click properties. Then change permissions to read only.

---

### Post by ad_267 on 2008-07-08
> **Tomatz said:**
> ```
gksu nautilus
```

Then open the home folder (root nautilus). Then r-click on the Desktop folder and click properties. Then change permissions to read only.

He wants to set it up so that this is done by default for all users.

---

### Post by Benismyhorse on 2008-07-08
Yea, I hope that this can be done Thanks for the help so far.

---

### Post by Benismyhorse on 2008-07-08
bump

---

