---
title: "file sharing issue"
date: 2013-12-08
forum: System76 Support
---

### Post by threezero on 2013-12-08
This is a repost from the Ubuntu network forum:

New Ubuntu guy, 13.10.
I recently purchased a system76 computer and trying to share  folders/files.  I have other Ubuntu and Windows systems on my home  network so I've gone the samba route.  I've got all the other computers  talking...except the new system76 computer.  I go though the normal  routine (right click to sharing and set it up) and all seems normal but I  continue to get an "Unable to access location, Failed to mount windows  share: permission denied" error when trying to access the files from  another ubuntu or windows system.  I can access all the other computers with the system76 but they cannot access the files on it.  probably something simple I'm missing (could it be somthing I did on initial set up?)...smbtree posted below.

thirty@Linux76a:~$ smbtree
Enter thirty's password: 
WORKGROUP
    \\LINUX76A               Linux76a server (Samba, Ubuntu)
        \\LINUX76A\Dave's on Linux    
        \\LINUX76A\Sharetest          
        \\LINUX76A\PhotosBackup       
        \\LINUX76A\EPSON-WF-3540-Series    EPSON WF-3540 Series
        \\LINUX76A\print$             Printer Drivers
        \\LINUX76A\IPC$               IPC Service (Linux76a server (Sa

---

### Post by PHP_Learner on 2014-02-21
I have similar problem, on my laptop. It has an Ubuntu 13.10 OS.

I shared a folder: /home/user/Downloads using right-click-> Sharing options...-> Share this folder-> Share name: "Downloads", Comments: "my downloads", both of **Allow others to create and delete files in this folder **and **Guest access (for people without ****a user account)** options are checked.

After applying above changes, whenever I want to access the shared folder from another computer (on my home WiFi network) I open a nautilus window and press "Connect to Server" then enter smb://192.168.0.102/ in the "Server Address" box. Nautilus shows two folders: "Downloads" and "Print$"

If double click on "Print$", a new dialog opens and asks me for username and password as follows:

I do not know if I must enter my connecting computer username/password or username/password of the computer the folder belongs to? Also I do not know how I should enter my username: just "**username**" or "**username@computername**" or other pattern? However any username and password lead no success:
the dialog is opened again. An interesting thing is that if I press "Cancel" (instead of  connect") the dialog is closed and opened again and if I press "Cancel" for the second time the dialog is closed forever!

If double click on newly shared folder "Downloads", then I receive an error: "**Unable to access location:** Failed to mount Windows share: Permission denied".

I searched the web to find a solution, but not found any working one.
 
I checked /etc/samba/smb.config and found no entry about "Downloads" folder! so I added following lines manually to smb.config
```
[Downloads]
   comment = my downloads
   path = /home/user/Downloads
   browseable = yes
   read only = no
   guest ok = yes
   locking = no
```
and then restarted smbd service. But adding above lines to smb.config did not solved the problem!

---

### Post by PHP_Learner on 2014-02-21
I have similar problem, on my laptop. It has an Ubuntu 13.10 OS.   </br>
       
      I shared a folder: /home/user/Downloads using right-click-> Sharing options...-> Share this folder-> Share name: "Downloads", Comments: "my downloads", both of **Allow others to create and delete files in this folder **and **Guest access (for people without ****a user account)** options are checked.   </br>
       
      After applying above changes, whenever I want to access the shared folder from another computer (on my home WiFi network) I open a nautilus window and press "Connect to Server" then enter smb://192.168.0.102/ in the "Server Address" box.  </br>
       
      Nautilus shows two folders: "Downloads"; and "Print$" </br>
       
      If double click on "Print$", a new dialog opens and asks me for username and password as follows:   </br>
       
      I do not know if I must enter my connecting computer username/password or username/password of the computer the folder belongs to? Also I do not know how I should enter my username: just "**username**" or "**username@computernamd"** or other pattern? However any username and password lead no success: the dialog is opened again. An interesting thing is that if I press "Cancel" (instead of connect" the dialog is closed and opened again and if I press "Cancel" for the second time the dialog is closed forever!   </br>
       
      If double click on newly shared folder "Downloads", then I receive an error: "**Unable to access location:** Failed to mount Windows share: Permission denied".  </br>
       
      I searched the web to find a solution, but not found any working one.  </br>
       
      I checked /etc/samba/smb.config and found no entry about "Downloads" folder! so I added following lines manually to smb.config    </br>
      ```
[Downloads]  
comment = my downloads  
path = /home/user/Downloads   
browseable = yes  
read only = no  
guest ok = yes  
locking = no  

```
       
      and then restarted smbd service. But adding above lines to smb.config did not solved the problem!</br>

---

