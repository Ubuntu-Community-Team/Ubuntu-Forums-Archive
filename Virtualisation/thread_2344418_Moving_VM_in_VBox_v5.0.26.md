---
title: "Moving VM in VBox v5.0.26"
date: 2016-11-25
forum: Virtualisation
---

### Post by Rick St. George on 2016-11-25
Need to know if the following is the proper procedure in VBox v5.0.26 to move a VM to another Hard Drive. Want to clear up some room on my SSD main drive and MOVE my VM to another HD. Hoping this will prevent many Read/Writes on the SSD and make it last longer, as the VM is used for Trading with 1000s of data file updates every day.

Proposed Procedure:

1. Backup the VirtualBox.xml file before starting just in case of mistake/error.

2. Copy the "VirtualBox VM" folder to the new location,

3. Remove it from VirtualBox / machine / remove (without deleting it).

4. Then use the add feature to add it back (select the *.vbox file) in new location.

5. Open VirtualBox / File / Preference / General, and change the default location to the new place.

6. Test all working then delete the original VirtualBox VMs folder.

Will this work?  I know that there used to be an Error when attempting this. 
Something similiar to ...

```

Failed to open virtual machine located in /<path>/<machine_name>/<machine_name>.vbox.
Cannot register the hard disk /<path>/, because a hard disk /<path>/ already exists.

```


Thanks!

---

### Post by Habitual on 2016-11-25
Not sure exactly, I moved mine years ago to ~/VboxVMs/
and I think all I had to do was tell Preferences about it and restart Vbox.

You could also export to OVA and then setup the new location for Vbox Machines
then import the OVA into the new location.

I'd try either. :)
Good Luck.

---

### Post by &amp;KyT$0P# on 2016-11-25
> **Rick St. George said:**
> Proposed Procedure:

1. Backup the VirtualBox.xml file before starting just in case of mistake/error.

2. Copy the "VirtualBox VM" folder to the new location,

3. Remove it from VirtualBox / machine / remove (without deleting it).

4. Then use the add feature to add it back (select the *.vbox file) in new location.

5. Open VirtualBox / File / Preference / General, and change the default location to the new place.

6. Test all working then delete the original VirtualBox VMs folder.

Will this work?  
Looks like a good start.  But if I'm remembering right, this isn't a complete set of steps.  I think I also had to adjust a few paths manually and remove now-unknown media from VirtualBox's list.

May not be necessary for your case, just something to keep in mind.

---

### Post by Rick St. George on 2016-11-27
Here is what I did - and it worked. This will not only free up space on my main SSD HD, but make my Backup smaller and faster. Dont' need to backup ths VM as all files are also on my Laptop.

Steps Taken:

1. Copy folder "VirtualBox VMs" to HD2.

2. In VBox, select "Snapshots", Delete irrelevant snapshots.

3. Start VM and Test Current State for accuracy of data.

4. Delete copy in Step 1, ReCopy VM to HD2 after confirmation in Step 3.

5. Machine / REMOVE VM, selecting to Delete All Files (critical or it will see two of the same).

6. Machine / ADD, browse to location on HD2 select *VM-name*.vbox file.

7. Start VM to verify everything is OK.

DONE.

Thanks Guys! All is well. Hope this helps someone.

Peace!

---

### Post by Rick St. George on 2016-11-28
Thought it was done as it worked the first time. Now next day, after doing a backup which filled my #2 HD it said Error Disk Full. So using sudo opened Thunar and deleted the backup (not related to the VBox). Now I get the following Error;

> 
 Document is empty.

 Location: '/media/stephen/Data/VirtualBox VMs/XP32-1/XP32-1.vbox', line 1 (0), column 1.

 /home/vbox/vbox-5.0.26/src/VBox/Main/src-server/MachineImpl.cpp[740] (nsresult Machine::i_registeredInit()).

 [TABLE]
[TR]
[TD] Result Code: [/TD]
[TD] NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD] Component: [/TD]
[TD] MachineWrap[/TD]
[/TR]
[TR]
[TD] Interface: [/TD]
[TD] IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}[/TD]
[/TR]
[/TABLE]



Note - the "***.vbox" file is 0kb, but there is another one named "***.vbox-prev"!
Any clues ? ? ?

---

### Post by Rick St. George on 2016-11-28
Duh .... Copied and Renamed the File as original "vbname.vbox" and it seems to be running OK now.

Sorry! I panicked.
Case Closed ... Peace!

---

