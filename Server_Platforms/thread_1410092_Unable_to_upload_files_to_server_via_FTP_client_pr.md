---
title: "Unable to upload files to server via FTP client program"
date: 2010-02-18
forum: Server Platforms
---

### Post by programming.name on 2010-02-18
Hi, I am using ubuntu 9.10 desktop edition and I have got some uploading issues via 
 
ftp client program. The following are what I have done so far.
 
1. Installed ssh using "sudo apt-get install ssh"
 
2. Added the below code in the /etc/ssh/sshd_config file:
 
Subsystem sftp internal-sftp
UsePAM yes
Match Group programming
ChrootDirectory /home/%u
ForceCommand internal-sftp
 
3. Created an account with System>Administration>Users and Groups application. The account 
 
name is hd and is under the main group named programming. And Home directory is /, 
 
finally Shell is /bin/bash
 
4. Next, Entered "sudo[FONT=Malgun Gothic] chown root.root /home/hd" followed by "[/FONT]sudo[FONT=Malgun Gothic] usermod -d / hd". [/FONT]
 
[FONT=Malgun Gothic]5. /home/hd folder's permission status is as follows.[/FONT]
 
[FONT=Malgun Gothic]Owner: root[/FONT]
[FONT=Malgun Gothic]Folder Access: Create and deete files[/FONT]
[FONT=Malgun Gothic]File access: --[/FONT]
 
 
[FONT=Malgun Gothic][FONT=Malgun Gothic]Group: root[/FONT]
[FONT=Malgun Gothic]Folder Access: Access fiels[/FONT]
[FONT=Malgun Gothic]File access: --[/FONT]
 
 
[FONT=Malgun Gothic][FONT=Malgun Gothic]Others[/FONT]
[FONT=Malgun Gothic]Folder Access: Access files[/FONT]
[FONT=Malgun Gothic]File access: --[/FONT]
 
[FONT=Malgun Gothic]Here's the thing. I can access the home/hd foler through the ftp client software like putty but I'm[/FONT]
 
[FONT=Malgun Gothic]unable to upload any files. But downloadinng files from the folder just works. I thought it's [/FONT]
 
[FONT=Malgun Gothic]matter of pemmisions of the folder so I tried to change that folder's permmisions. After I tried[/FONT]
 
[FONT=Malgun Gothic]to change the permissions for both Owner and Group to "Creata and delete files" which is [/FONT]
 
[FONT=Malgun Gothic]775, I was not able to connect to the server again. Please HELP![/FONT]
 
[FONT=Malgun Gothic]Thanks in advance [/FONT]
[/FONT][/FONT]

---

