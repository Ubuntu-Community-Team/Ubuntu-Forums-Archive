---
title: "Sharing Files Windows &amp; Ubuntu"
date: 2012-01-22
forum: Virtualisation
---

### Post by Stvnx7 on 2012-01-22
Hello everyone. I am using VMPlayer to run Ubuntu in a Virtual Machine. Ubuntu is the guest OS, and Windows 7 is the host.

I can't seem to find an easy way to have Ubuntu recognize my Windows file system. 

I did a quick search, and [found this thread]("http://ubuntuforums.org/showthread.php?t=973756").and it seems that there are a couple of options, and I am not sure what the pros and cons are of each. 

If I want my Windows file system to be mounted like it would if I did a dual-boot of Windows / Ubuntu, would the NFS option be my best bet? Since I am the only user on my computer, I am willing to sacrifice some security for convenience since that seems to be the give-and-take situation. 

Thank you all for your help, and I hope I used the terminology correctly.

---

### Post by japzone on 2012-01-22
Wait what are you tryin to do? If your trying to access your Windows files from Ubuntu within the VM then here's what you can do:

-Setup Windows Network Sharing on your PC and choose Folders you want to share(Right-Click-->Properties-->Sharing tab)

-Setup SMB sharing in Ubuntu
1)Make sure samba is installed: ```
sudo apt-get install samba nautilus-share
``` 
2)then reboot
3)then open Nautilus(File Explorer) and find Folders you want to share(Right-Click-->Sharing Options)

-(Optional)Switch Network Adapter From NAT to Bridge. This will remove the Network Sandbox around the Guest OS making it less secure, but will allow Network access to the Guest OS from other Computers on your Home Network(useful for Serevers)



_Now to access your Host Windows 7's files from Ubuntu:_
1)Open Nautilus and click "Network" in the Left-Pane
2)Open "Windows Network"
3)Now open "WORKGROUP" for the Name of your Windows PC(If it's not there try one of the other folders)
4)Once you locate your Windows PC open it and you should be presented with Shared Folders, PRinters, ect.
5)Simply open the Shared Folder you wish to access

_Now to Access your Guest Ubuntu's Files from Windows 7:_
1)Click Start, and search for "Network", then click the Result
2)The Window may take a while to work as it scans your Network, but Eventually your Ubuntu Guest should appear in the "Computer" Category(If not refer to the Last Section)
3)Open the Computer and you should be presented with Shared, Folders, Printers, ect.(If it asks for a username and password use your Ubuntu login)
4)Open the Folder you want.

_If you can't find Your Guest in Windows or Windows i your Guest do this:_
-In Windows:
1)Right Click "Computer" in the Start Menu(or Desktop) and click Properties
2)Find "Workgroup" and Check if it's set to "WORKGROUP" if not take note of it's Name
-In Ubuntu:
3)_Open Shared Folder Settings:_
Gnome Classic:
4)System-->Administration-->Shared Folder
5)Switch to the General Properties tab
6)Change the Workgroup name to WORKGROUP or whatever the Name of the Workgroup was back in Step 2
The Host and Guest should now be able to see each other.
Unity:
4)Open Software Sources, and Enable the Universe Repository
5) Run in Terminal:```

sudo apt-get update
sudo apt-get install system-config-samba
sudo system-config-samba

```
6)Prefferences-->Server Settings, change workgroup name to whatever the Name of the Workgroup was back in Step 2
Hope this is helpful if you have anymore questions just ask

---

### Post by Stvnx7 on 2012-01-22
@japzone, thank you so much for your incredibly detailed response. I think I will definitely be able to do as you have suggested. I will post my progress here but today I am busy with essays.

Thank you very much!

---

### Post by japzone on 2012-01-22
Glad to be of Service ;)

---

### Post by Rebelli0us on 2012-01-24
Well said! And also** Windows can read/write the Linux ext4 file system** -- try sharing your Home folder exactly as mentioned above in post #2.

---

