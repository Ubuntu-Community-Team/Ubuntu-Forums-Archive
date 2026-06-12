---
title: "Virtualbox file associations"
date: 2008-10-22
forum: Virtualisation
---

### Post by Alexander42 on 2008-10-22
This is probably a long shot, but here goes.  I'm using an Ubuntu 8.10 host for a Windows XP virtualbox guest.  I have Microsoft Office installed in the virtual WinXP.  Is it possible to open an office 2007 file within Ubuntu and have it automatically load in the virtual WinXP?  Thanks!

---

### Post by neilengineer on 2008-10-22
My idea:
1. Setup network between the Host Ubuntu and the Guest WinXP.
2. Share the Office document in Win XP.
3. Access using Samba in Ubuntu.

Or:
1. Setup network between the Host Ubuntu and the Guest WinXP.
2. Share the Office document in Ubuntu, add it to samba share path.
3. Access using in WinXP.


Even, you can setup a FTP server in either of them:
In Ubuntu, I use vsftpd.
In WinXP, I use servU.

---

### Post by Greyed on 2008-10-22
> **neilengineer said:**
> My idea:
3. Access using Samba in Ubuntu.

Errrrr, isn't Samba a bit heavy for this?  Doesn't the Linux version of VBox have Shared Folders like the Windows version does?  Shared Folders takes a directory on the host and makes it a partition from the view of the guest.

But to answer the OP's question.  No, I don't believe that is possible.  While you could have VBox open up on a file association I know of no trivial way to tell the OS inside the VBox to do anything meaningful.  You cannot pass command-line options to the OS.

Is it possible if you're determined enough?  Yes but it would involve scripting in at least two different languages and only work if you didn't have the VBox open at the time.  Otherwise, no.

---

### Post by Alexander42 on 2008-10-22
For the record, I do have a folder shared between the host and guest that allows me to access files.  So it's not accessing the files I'm concerned about it, it's ease of opening certain file types in the correct program.  Thanks for the replies!

---

### Post by Ducatiboy Stu on 2008-10-22
Short Answer...NO, because Xp in VBox is actually isolated from Ubuntu...


But office should operate in WINE. I know office 2003 works, and I think 2007 will as well....

If 2007 does work, you can set it so that when you click on an .doc/.xls/.ppt file it will open with office...

---

### Post by Greyed on 2008-10-22
> **Ducatiboy Stu said:**
> Short Answer...NO, because Xp in VBox is actually isolated from Ubuntu...

Except for shared folders and network connectivity you mean.  ;)

---

### Post by stonecoldjha on 2008-10-22
you need to share a folder between the host ubuntu and the guest xp.for that power on the xp virtual machine.go to Devices in the virtual machine window.and click it.then click on install Guest additions.let it install itself on xp,and then reboot the virtual xp.now go to settings of xp in virtualbox,and there go to shared folders,create one and name it.then power on xp,go to my computer icon on the desktop,right-click it and click on map network drive,then click on browse,soon you would see the shared directory that you created,open it and assign a drive letter of your choice to the shared drive that is gonna be created.click OK.next time,when you open my computer,you see the shared drive,the contents of which are accessible to both ubuntu and xp.

---

### Post by Ducatiboy Stu on 2008-10-22
> **Alexander42 said:**
> This is probably a long shot, but here goes.  I'm using an Ubuntu 8.10 host for a Windows XP virtualbox guest.  I have Microsoft Office installed in the virtual WinXP.  Is it possible to open an office 2007 file within Ubuntu and have it automatically load in the virtual WinXP?  Thanks!

As I said before, you cant click on an Office doc in ubuntu and make it open in Virt XP.....you can share easy enough, but you cant make it open. You have to be in XP to open it.


I would try WINE...if it works, it will be a lot easier...

---

### Post by Greyed on 2008-10-23
> **Ducatiboy Stu said:**
> As I said before, you cant click on an Office doc in ubuntu and make it open in Virt XP.....you can share easy enough, but you cant make it open. You have to be in XP to open it.

Yes, you can.  Here's how.

Associate the document with a script that would check if VBox is running and, if not, start it.  Then also have it place a semaphore file onto the shared folder which contains the file that you want opened.

Inside the VBox have another script which looks for that semaphore file and, when found, opens up the appropriate application & document inside VBox.

Once you have a method of communicating between the two machines it is possible to kudge together a script to do it.  However, I don't think most people would want to go through the effort of building those scripts to do it.  IE, it is possible, just not worth it to most people because, you know, OOo or Wine work far better or one just opens the VBox and double clicks on the file in there.

---

### Post by Ducatiboy Stu on 2008-10-23
> **Greyed said:**
> Yes, you can.  Here's how.

Associate the document with a script that would check if VBox is running and, if not, start it.  Then also have it place a semaphore file onto the shared folder which contains the file that you want opened.

Inside the VBox have another script which looks for that semaphore file and, when found, opens up the appropriate application & document inside VBox.

Once you have a method of communicating between the two machines it is possible to kudge together a script to do it.  However, I don't think most people would want to go through the effort of building those scripts to do it.  IE, it is possible, just not worth it to most people because, you know, OOo or Wine work far better or one just opens the VBox and double clicks on the file in there.

Well..yes....but not for the average user.....its a bit of work to do it

---

### Post by 1011101 on 2009-03-22
It's too bad there is no simple way to do this in virtualbox. I have this feature when I use Parallels under OS X and it works great.

---

