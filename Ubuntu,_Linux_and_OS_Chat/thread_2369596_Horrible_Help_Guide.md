---
title: "Horrible Help Guide"
date: 2017-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by vineyridge on 2017-08-24
Ubuntu 16.04 LTS, and a long time Windows user, brand new to Ubuntu

I needed to make a new folder on an external HD.  I opened the file drawer icon.  I looked for a way to make a new folder.  I went to the Help Guide, and there was nothing about creating folders.  There was lots of really basic information, but nothing about making a new folder.  I went to all of the help resources and searched for "create folder".  I got literally millions of responses for posts with "create folder", but the ones close up were not on HOW TO create a folder without using the terminal.  So I googled and found what I needed almost instantly on a site called Techwalla which explained the process in two sentences.

Why is something not that basic found in the Ubuntu Desktop Guide?

These forums are helpful, but something that basic needs to be in Help.

---

### Post by BenginM on 2017-08-24
Hiya , creating a folder is so basic that it doesn't need to be on the document , in Xubuntu the file manager is thunar if i open my external HD, right-click i get the option to create a folder , or from the file menu in the file manager you get that option too. if i clicl on help in thunar file manager it takes me to 
[http://docs.xfce.org/xfce/thunar/start](http://docs.xfce.org/xfce/thunar/start)
[http://docs.xfce.org/xfce/thunar/working-with-files-and-folders](http://docs.xfce.org/xfce/thunar/working-with-files-and-folders)

I don't know which file manager you're using , but i suppose if you select help in your file manager it should take you to a guide like the above!

feel free to send a request to the document team to add that.

---

### Post by vasa1 on 2017-08-24
No clear request for support.

---

### Post by &amp;KyT$0P# on 2017-08-24
> **vineyridge said:**
> So I ... found what I needed almost instantly on a site called Techwalla which explained the process in two sentences.
Link to that page?

---

### Post by vasa1 on 2017-08-25
Hmmm ... I wonder if it's this: [https://www.techwalla.com/articles/how-to-make-a-folder-in-ubuntu](https://www.techwalla.com/articles/how-to-make-a-folder-in-ubuntu)

> Step 5

Type "sudo mkdir /home/user/newFolder" in the terminal. The "mkdir" command creates a new folder in the location you specify after the command. Replace "/home/user/newFolder" with the location where you want to create the folder. If you want to create a folder on the desktop, the location is "home/user/Desktop/newFolder," where "user" is your username and "newFolder" is the name of the folder you are creating. Shudder!

---

### Post by again? on 2017-08-25
Right click in the file browser and select New Folder isn't a new concept to a "a long time Windows user".
Contribute or report a bug if you find something wrong with documentation.

---

### Post by Rocky_Bennett on 2017-08-25
> **guber2 said:**
> Right click in the file browser and select New Folder isn't a new concept to a "a long time Windows user".
Contribute or report a bug if you find something wrong with documentation.



As a long time Windows user and a recent convert to the world of Linux, the right click method just seems to be the easiest method to create a new folder in Ubuntu.

---

### Post by lisati on 2017-08-25
As well as the relatively intuitive right-click-on-folder approach, there's the [mkdir]("https://en.wikipedia.org/wiki/Mkdir") command when using the terminal/CLI. Unix, MS-DOS, Windows, and Ubuntu all have their own versions.

---

### Post by deadflowr on 2017-08-25
If you feel it's not properly documented or explained in the help guide, please contact the help guide team and explain to them the oversight.
[https://help.ubuntu.com/stable/ubuntu-help/get-involved.html]("https://help.ubuntu.com/stable/ubuntu-help/get-involved.html")

But basically all you need to so is in the Files program open the menu item File (access that with alt + F) and go to New folder or New Document > Empty Document.
(That should still work on 16.04, I don't have that currently but I remember it did when I did have it installed)

Note this is designed for Desktop users so if you need to create a new folder or document outside of your Home folder, then that's another issue; a more advanced issue.

---

### Post by cariboo on 2017-08-25
> **deadflowr said:**
> If you feel it's not properly documented or explained in the help guide, please contact the help guide team and explain to them the oversight.
[https://help.ubuntu.com/stable/ubuntu-help/get-involved.html]("https://help.ubuntu.com/stable/ubuntu-help/get-involved.html")

But basically all you need to so is in the Files program open the menu item File (access that with alt + F) and go to New folder or New Document > Empty Document.
(That should still work on 16.04, I don't have that currently but I remember it did when I did have it installed)

Note this is designed for Desktop users so if you need to create a new folder or document outside of your Home folder, then that's another issue; a more advanced issue.

If you read the original post, the poster was trying to create a directory on an external hard drive, which if you haven't got permissions set up properly is a little more than right-clicking and selecting create folder. Still even if you only use two fingers to type, creating a directory from the command line isn't all that hard, and you'll find directions a lot quicker in the Ubuntu documentation, how to do that, than finding a way to do it graphically.

---

### Post by kevdog on 2017-08-28
Maybe he didn't mount the external HD???

I'd honestly tell you to do everything from command line, however then I'd be sounding like one of those linux geeks ... er wait ... yea but the process is a lot quicker -- sorry it just is.

---

### Post by macbreak on 2017-09-04
Anything is easy... if you know how. Omitting a _**simple one sentence explanation**_ of how to do this, smacks of arrogance. Every little barrier wastes your time when you are trying to get on with something, and then shutdown your PC and continue real life. It takes what, 10 mins to create a CLEAR sentence (or 2... or 3?) explaining this step which - whoever is in charge of omitting it - clearly feels is *"beneath"* them to feel the need to explain.

We ALL learnt the trivial things once, through being taught or through trial and error, but purposely omitting a simple explanation just smacks of elitism (maybe their ego enjoys knowing that there's people out there stuck on this simple task, and they'll need to come and find the "experts" to find out how to achieve it.) Someone's got a kick out of omissions like this, or maybe some folk are completely detached from the REAL WORLD and normal people, and wanting to get on.

Wow.

---

### Post by again? on 2017-09-04
> **macbreak said:**
> Anything is easy... if you know how. Omitting a _**simple one sentence explanation**_ of how to do this, smacks of arrogance. Every little barrier wastes your time when you are trying to get on with something, and then shutdown your PC and continue real life. It takes what, 10 mins to create a CLEAR sentence (or 2... or 3?) explaining this step which - whoever is in charge of omitting it - clearly feels is *"beneath"* them to feel the need to explain.

We ALL learnt the trivial things once, through being taught or through trial and error, but purposely omitting a simple explanation just smacks of elitism (maybe their ego enjoys knowing that there's people out there stuck on this simple task, and they'll need to come and find the "experts" to find out how to achieve it.) Someone's got a kick out of omissions like this, or maybe some folk are completely detached from the REAL WORLD and normal people, and wanting to get on.

Wow.
Really.. you think someone is purposely omitting information so a user has to consult the "experts"????
Who are these "experts" creating dependency structures by writing help manuals omitting vital information on purpose???
Silliest thing I have heard in a long while.
Get involved and make the changes you think are necessary yourself. 
The issue isn't as trivial as it first looks and appears to involve permissions of the external HD.

Wow.

---

### Post by &amp;KyT$0P# on 2017-09-04
> **macbreak said:**
> Omitting a _**simple one sentence explanation**_ of how to do this, smacks of arrogance. 
macbreak, what _**simple one sentence explanation**_ do you have in mind and where do you think it should be added?

> purposely omitting a simple explanation
What makes you think the omission is deliberate?

---

### Post by oldos2er on 2017-09-04
Circling the drain, so closed.

Anyone is free to join the [documentation team]("https://wiki.ubuntu.com/DocumentationTeam/Organization") and edit the desktop guide.

---

