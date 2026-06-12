---
title: "Tomboy Will Not Complete Authorization for Sync"
date: 2011-10-14
forum: Ubuntu One (CLOSED)
---

### Post by kernelles on 2011-10-14
In Tomboy preferences, when I try to authorize sync with Ubuntu one, after I receive confirmation in browser from Ubuntu One that machine is added, I cannot click on "Save" button to complete auth, because it's grayed out. 

I am running a fresh install of 11.10 x64, and I have tried purging/reinstalling Tomboy. Any help would be appreciated. 

Thanks!

---

### Post by krackersk on 2011-10-14
I am also getting this problem.

I've just done a fresh install of ubuntu 11.10 x64

---

### Post by Paulgirardin on 2011-10-15
Me 3  11.10 x32

---

### Post by krackersk on 2011-10-15
Check out:

[http://askubuntu.com/questions/66276/no-ubuntu-one-sync-in-my-tomboy-notes-sync-preferences](http://askubuntu.com/questions/66276/no-ubuntu-one-sync-in-my-tomboy-notes-sync-preferences)

You need to edit the server field to get the save to be able to be pressed

---

### Post by Paulgirardin on 2011-10-15
Thanks.

That worked ,though I had to make several attempts to synch before I stopped getting error messages.:)

---

### Post by krackersk on 2011-10-16
This bug for this seems to be:

[https://bugs.launchpad.net/ubuntuone-servers/+bug/845321](https://bugs.launchpad.net/ubuntuone-servers/+bug/845321)

If you keep getting errors one work around is to put in the server field:

[https://edge.one.ubuntu.com/notes/](https://edge.one.ubuntu.com/notes/)

It suggests this in at the bottom of the bug report.

---

### Post by poltiser on 2011-10-17
> **krackersk said:**
> This bug for this seems to be:

[https://bugs.launchpad.net/ubuntuone-servers/+bug/845321](https://bugs.launchpad.net/ubuntuone-servers/+bug/845321)

If you keep getting errors one work around is to put in the server field:

[https://edge.one.ubuntu.com/notes/](https://edge.one.ubuntu.com/notes/)

It suggests this in at the bottom of the bug report.

it worked well! ;)

---

### Post by ballantony on 2011-10-18
> **krackersk said:**
> This bug for this seems to be:
 
[https://bugs.launchpad.net/ubuntuone-servers/+bug/845321](https://bugs.launchpad.net/ubuntuone-servers/+bug/845321)
 
If you keep getting errors one work around is to put in the server field:
 
[https://edge.one.ubuntu.com/notes/](https://edge.one.ubuntu.com/notes/)
 
It suggests this in at the bottom of the bug report.
 
 
Making any change in the server field seems to enable the save button.  Tried this on three installations

---

### Post by duanedesign on 2011-10-18
To resolve this you have to edit the server field for Tomboy Web. After authenticating in the browser it tells you to go back to the Preferences window and press Save. Go back to the Preferences and remove the trailing slash '/' from the server address. It will read https:one.ubuntu.com/notes/ and change it to https:one.ubuntu.com/notes . You can add the trailing slash back if you want. What is important is that a change is made to the field.

**NOTE:** I do not recommend anyone use the Ubuntu One edge server for daily use. That server is used for testing and updated hourly, You are more likely to run into an issue using this server.

---

### Post by mclode on 2011-10-19
Thank you, now I do not have any outstanding issues with 11.10

---

