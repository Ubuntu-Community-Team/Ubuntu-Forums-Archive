---
title: "Share VirtualBox OS With Multiple Ubuntu Users"
date: 2008-05-17
forum: Virtualisation
---

### Post by bhaigh on 2008-05-17
I have an Ubuntu install with user accounts for myself and my wife.  I installed VirtualBox and Windows XP on my side.  How can I let my wife have access to the same virtual Windows XP?

---

### Post by snappy46 on 2008-05-18
You could create a directory under home that you both have access to and put your vdi file in there.  Now you should both be able to access that virtual Window XP.  I use to do the same for vmware and it worked fine.

To make sure that you and your wife have access to the directory just create a new group with you and your wife in it.  Give that group you just created full access to the newly created directory under home.

Hope this help

---

### Post by Gotit on 2008-07-24
> You could create a directory under home that you both have access to and put your vdi file in there. Now you should both be able to access that virtual Window XP. I use to do the same for vmware and it worked fine.
I tried to do just that but when logging in as the user that did not create the .vdi file it does not show in Virtualbox.  I try to add it using the Virtual Disk Manager and it errors out saying the Disk is already registered.

I created the /home/shared directory as root and shared it.  As root I gave the folders and files within it both read and write ability to "other users".
Any thoughts on what else I need to do??  Thanks.

---

### Post by Gotit on 2008-07-26
OK, I stumbled across the solution via trial and error :)

The solution was simply to create a new virtual machine on my wife's login and give it a different name (XPV).  When I got to the part about a new or existing hard drive I selected the existing VXP MV from my login and finished the new set-up. This causes a new .xml file to be created in ~/.VirtualBox/Machines/YourVMname folder. This .xml file holds the config settings for the VM you are running.  

So, on my login when I select the VXP I get my VM setting for the XP.vdi file and when my wife logs in she selects XPV and gets her setting for the same XP.vdi!!  

Cool stuff!!!

---

### Post by jacw on 2008-07-27
Are there issues if you happen to both be accessing the image at the same time? For example, if on the same machine, you switch users without logging off? Is it important if doing this to choose NTFS rather than EXT3 when creating the XP image?

---

### Post by Gotit on 2008-07-27
Hmmm... good questions.
I would think two people running the same .vdi file at the same time (via log-in switching I guess) would pose some problems.

As far as the format goes (NTFS vs EXT3) I didn't specifically specify this any place when I created my XP VM.  In the VM set-up I simply selected XP from the list of OS types.

Perhaps someone else can help out more on on this.

---

### Post by jacw on 2008-07-29
Yes. When you install WinXP it is the WinXP install process that asks the format type. I was wondering if there was any difference in the ability to share based on that format but after some searching around I am not sure. Typically though, you can have multiple users logged in to XP at any time if Fast User Switching is enabled. Also, I have seen but never tried one of these devices that allows multiple users to access a single machine at the same time by plugging in an extra monitor and keyboard.

---

### Post by Gotit on 2008-08-30
Well, I finally got around to checking out how VB XP works for multiple Ubuntu user log-ins on the same system.  Basically, it doesn't. :(

When I'm logged into Ubuntu and open the VB XP drive and then switch Ubuntu users to my wife's log-in (without me logging out of Ubuntu or having closed/logged out of the VB XP drive) and try to access the VB XP drive it shows as unavailable.  I guess this shouldn't come as much of a surprise since the VB XP drive is really just a file in the /shared_directory/.VirtualBox/VDI folder and it's not a read only file.

---

### Post by blur xc on 2009-08-18
> **snappy46 said:**
> You could create a directory under home that you both have access to and put your vdi file in there. 

How do you put your .vdi file there?  I moved it from the command line, but then vbox told me it was missing and didn't give me any option to point it to the new location that I could find.

Thanks,
BM

---

### Post by Gotit on 2009-08-18
> **blur xc said:**
> How do you put your .vdi file there?  I moved it from the command line, but then vbox told me it was missing and didn't give me any option to point it to the new location that I could find.

Thanks,
BM

When you moved your drive.vdi it's new location became unassociated in VB and now you need to tell VB the new location.  You do this by removing the old association and establishing the new location as follows: 
First make a copy of your drive.vdi as a back-up.

Then give this a try (it's looks worse than it really is :))
1. Move your drive.vdi to its new location
2. Launch VirtualBox
3. Pop-up message that the virtual hard disk is no longer registered click "Check"
4. "Release" the unregistered drive (will have a yellow caution sign)
5. "Remove" the unregistered drive [this removes the link, doesn't delete the drive.vid] (from the old location)
6. Select "Add"
7. In the pop-up browse to the new location/drive.vdi
8. Select the drive.vdi
9. On Virtual Disk Manager screen click "Refresh"
10. OK and close
11. On the main VirtualBox screen select the virtual machine for the associated drive.vdi
12. Settings > Hard Disks (it will probably be blank)
13. Click the "add" icon (little disk with a +)
14. your drive.vdi should show up 
15. Click OK 
You should now be able to launch your virtual machine.
Let us know how it turns out.  Remember, as long as you have your "drive.vdi" you haven't lost any data.

---

### Post by topoguide on 2009-08-19
I am also having issues with this, although mine is with sharing Win 7 RC with my wife.

I have not tried to move the .vdi file to a new folder yet, but I did try to share the folder it is currently in... with no success.  Is there a limitation that is keeping the existing folder \.VirtualBox from being shared?  I am guessing there is since others are moving the file instead of trying to share the existing \.VirtualBox folder.  Any thoughts on this?

Full disclosure:
I am like many others learning how to administer a linux machine.  I have used Nautilus to set sharing and privelages... like many who have been using Windows and Mac for too long I have lost most of my command line skills.  I have found that command line commands seem to work better than nautilus commands overall, so am working on learning more.  If setting sharing rights is one of those I would appreciate a point to a good thread on sharing via command line.

---

### Post by Gotit on 2009-08-19
To make the shared folder following is how I went about it.  I'm not sure this the the best way, but it seemed to work.

Make a new group that will be shared by who ever you select
1. Go to Systems > Admin > Users and Groups
2. On the Users Settings window select Unlock
3. Select Manage Groups
4. Select Add Group
5. Give it a name and select the users who will have shared access
6. Close the windows

Now create a folder that will be shared (where the drive.vdi will go)
1. Press Alt+F2 to bring up the "Run Application" form.
2. Enter ```
gksu nautilus
``` 
3. Press Run.  This will bring up a root file browser window (you may have to enter your password).
4. Browse to /home and create a new folder
5. Right click the new folder and go to Properties > Permissions
6. In the Group setting select the shared group you created above.
7. Set Folder Access to Create and delete files
8. Close out 

I think at this point you can move the drive.vdi file there and make the associations as detailed in my other post and it should be good to go.

---

### Post by harrisheatair on 2009-08-28
Can someone help me?  I have xp on my virtualbox but i can"t share my xp.vdi with other users on their linux accounts.   please explain in laymen terms if possible.  I am somewhat new to this.

---

### Post by Gotit on 2009-08-29
> **harrisheatair said:**
> Can someone help me?  I have xp on my virtualbox but i can"t share my xp.vdi with other users on their linux accounts.   please explain in laymen terms if possible.  I am somewhat new to this.

Did you follow my posts #12 and 10 (in that order) to set up:
1. a new group that contains the users that will be using the virtual XP
2. create a new folder in /home and give the new group permissions to create and delete
3. move the xp.vdi file to the new folder under /home
4. in VB disassociated the xp.vdi from its old location
5. in VB associate the xp.vdi with its new location

if you gave it a try, and still have problems please post where you are getting stuck and we'll see if we can help.

---

### Post by harrisheatair on 2009-08-30
I'm stuck at finding my xp.vdi.  it is in there because i use it.  but i cant find it to move

---

### Post by Gotit on 2009-08-30
> **harrisheatair said:**
> I'm stuck at finding my xp.vdi.  it is in there because i use it.  but i cant find it to move

That's probably because it's in a hidden directory.  Give this a try:
Places > Home Folder
Once it opens press Ctrl+h to toggle showing hidden directories and files (they start with a dot, that is .VirtualBox).
Then scroll down to .VirtualBox/VDI there you should find your vdi files.

If you always want the hidden folders/files to show, when your are in the File Browser (Places > Home Folder) go to Edit > Preferences > Views and check "Show hidden and backup files".

---

### Post by blur xc on 2009-09-01
> **Gotit said:**
> When you moved your drive.vdi it's new location became unassociated in VB and now you need to tell VB the new location.  You do this by removing the old association and establishing the new location as follows: 
First make a copy of your drive.vdi as a back-up.

Then give this a try (it's looks worse than it really is :))
1. Move your drive.vdi to its new location
2. Launch VirtualBox
3. Pop-up message that the virtual hard disk is no longer registered click "Check"
4. "Release" the unregistered drive (will have a yellow caution sign)
5. "Remove" the unregistered drive [this removes the link, doesn't delete the drive.vid] (from the old location)
6. Select "Add"
7. In the pop-up browse to the new location/drive.vdi
8. Select the drive.vdi
9. On Virtual Disk Manager screen click "Refresh"
10. OK and close
11. On the main VirtualBox screen select the virtual machine for the associated drive.vdi
12. Settings > Hard Disks (it will probably be blank)
13. Click the "add" icon (little disk with a +)
14. your drive.vdi should show up 
15. Click OK 
You should now be able to launch your virtual machine.
Let us know how it turns out.  Remember, as long as you have your "drive.vdi" you haven't lost any data.

I'm finally getting around to doing this- Thank you for the detailed answer.

I moved my .vdi file, but now I have a new problem.  The realease and remove virtual hard disk right click menu options (steps 4 and 5) are greyed out.  How do I un-grey them?

Thanks,
BM

---

### Post by harrisheatair on 2009-09-01
Thanks for the help.  I did what you said with a few detours.  I deleted my vbox file once and had to reinstall it.  Then i deleted my xp.vdi (totally missed what you meant).  But after I set up the group and the file like you said, and deleted my xp.vdi by accident, when I reinstalled, I chose that file for the xp to be stored in.  Thanks again.

---

### Post by Gotit on 2009-09-01
@ blur xc
I'm not at my machine right now to double check, but the vdi file may have already gotten un-registered.  Did you try to move fwd with step 6...?

---

### Post by blur xc on 2009-09-02
> **Gotit said:**
> @ blur xc
I'm not at my machine right now to double check, but the vdi file may have already gotten un-registered.  Did you try to move fwd with step 6...?

Could it be because I have a snapshot of my drive?  But when I try to remove the snapshot, it tells me that it can't because I have more than one child hard disk.

I've tried step six, and it tells me that that hard drive is already registered.  Maybe this is a question for the vbox forums.

Thanks,
BM

---

### Post by zarthon on 2009-09-02
There are ways to make using separate image files take up much less than twice the hard drive space of a single image. Create a samba share on Ubnutu, map a network drive in windows to this samba share. In windows drag your data files over to the network drive. From the samba share you can use the data from both windows instances and Ubuntu as well. You will be able to share files and easily collaborate with your wife.
Test the data in the new place,make a back up of anything very important and then delete it from the original image. Downsize your windows image. Create two copy-on-write images that use the resized image as a base.To simplify keeping track of the images include name or initials of the primary user in the file names.
 
You can take the samba share further by copying your whole user settings and data folders in windows over to the share then set your windows user to use the mapped drive.

***Test drive the setup and compare it to alternatives.***
How much RAM do you have ? [B]
[*]Just because you share the image does not mean that the machines will share memory.They will each use separate RAM regardless of how you configure the disk images.
[/B] As you probably know Windows (not sever versions) only supports a single terminal at one time so you will not be able to share a single instance like you can with Ubuntu.Run two instances of windows using separate images with just your regular user. Open up all the programs you intend to use at the same time. You and your wife could take turns test driving the comptuer. While you won't get the full effect of the all the activity of the other person the user interaction will probably not take up that much overhead. Compare adding extra hardware to getting an inexpensive secondary computer.
:confused:
Excuse me for jumping in late. I am having my own visualizing problems and was reading up before posting... I had a few suggestions for you. If I have missed something and they are way off base I am sorry. I am a  bit tired.

---

### Post by blur xc on 2009-09-03
> **blur xc said:**
> Could it be because I have a snapshot of my drive?  But when I try to remove the snapshot, it tells me that it can't because I have more than one child hard disk.

I've tried step six, and it tells me that that hard drive is already registered.  Maybe this is a question for the vbox forums.

Thanks,
BM


Wicked awesome- I got the snapshots removed and the .vdi file moved.  All is great- All I have to do now is set up VBox on my wife's user account.  

Thanks for all the help!

BM

---

### Post by Gotit on 2009-09-03
Happy to hear you figured it out and got it working!

I haven't tried to share a .vdi file with an associated snapshot, but if I do I will remember this.  

Also, I should make note to all that I am running v1.6.2 if any of the steps above seem odd because you are on a different version of VB.

---

### Post by Verzweifler on 2009-10-23
I am still having trouble sharing a Windows XP guest on my VirtualBox:

If one of the users allowed to access the virtual machine, i.e. my wife, [COLOR="Red"]suspends[/COLOR] the VM instead of [COLOR="Red"]shutting it down[/COLOR] when logging out of Ubuntu, the other user, i.e. myself, will not be able to tell the actual status of the machine.

Consider the following scenario:
[LIST]
[*]User A uses the VM and properly shuts it down (VM is shown "powered off" in user A's VirtualBox dialog)
[*]User B uses the VM and supends it (VM is shown "saved" in user B's VirtualBox)
[*]User A powers on the VM (it is still shown "powered off" in his VirtualBox)
[*]User A uses VM (and thus modifies it) and shuts it down again
[*]User B restores the VM (VM still shown "saved")
[/LIST] 
Will there be a corrupted system afterwards? If so, how can this be handled other than telling all users to NOT suspend a VM that might be used by other users?

---

### Post by Gotit on 2009-10-24
@ Verzweifler
I'm not sure you can suspend an active VM in one profile and access the same VM from another.  I think you need a "server" version of a program to something like that.

I have re-read zarthon's post (#21) but I don't think that gets to what you are trying to do either.  However, you may want to re-read it too as I'm no expert in shared drives.  If you ever figure it out, please post your solution!

---

