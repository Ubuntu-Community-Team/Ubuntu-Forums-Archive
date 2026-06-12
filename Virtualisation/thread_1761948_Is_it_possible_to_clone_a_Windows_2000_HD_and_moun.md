---
title: "Is it possible to clone a Windows 2000 HD and mount it in a virtual machine?"
date: 2011-05-18
forum: Virtualisation
---

### Post by diablo75 on 2011-05-18
I have a friend who has this really old program he uses for business purposes to figure up estimates for landscaping, and he lost the original software CD.  It's too costly to replace and he's wanting to move off the old computer it's stuck on at the moment.

I'm exploring my options for ways to get this program (or even the whole OS and the program) migrated over to his new computer.  Is it possible to mirror the hard drive and mount the image in a virtual machine?

---

### Post by practic on 2011-05-18
I'm not sure about the virtual machine question, but you can try two things as well:

1. Copy the program folder over (and any other folders belonging to it in "Documents and Settings->User->Local Settings->Application Data" and "Documents and Settings->User->Application Data" to the new computer. Then try and run it. If it complains about missing Dll's, and actually names them, then copy those from the old Windows->System32 to the new one. Keep trying until it either works, or doesn't give you a meaningful error message.

2. Use Registry Editor PE to load the registry off the old drive and save out the Local Machine->Software->Landscaping Program and Current User->Software->Landscaping Program entries to reg files. Then run these reg files on the new computer. That may help the program run.

---

### Post by lmarmisa on 2011-05-18
I recommend to use Clonezilla Live:

[http://www.clonezilla.org/clonezilla-live.php](http://www.clonezilla.org/clonezilla-live.php)

Do not use the clone option. Make a complete backup of the hard drive of the W2K computer with Clonezilla (maybe you can save the backuped files on the host computer using samba). Then create a virtual machine with a hard drive with the same size of the original (select dynamically expanding storage). Do not intall anything in that virtual machine. Finally restore the backup in this virtual machine using Clonezilla. If you select the bridge adapter mode for the network, you will be able to access the files of the backup using samba too.

I am not sure if W2K will run properly in the new environment.

---

