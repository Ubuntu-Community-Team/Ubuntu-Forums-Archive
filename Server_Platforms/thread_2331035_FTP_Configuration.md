---
title: "FTP Configuration"
date: 2016-07-17
forum: Server Platforms
---

### Post by thorftp on 2016-07-17
Hello!

I would like to please get your help because I'm desperate!
First of all i want to say sorry for my english and secondly, if i'm on the wrong tab or the wrong forum tell me where i need to ask. (I'm am trying to ask at different places right now)

I want to set up a FTP server which does the following:

This server has a website with listing and access to some folders in /var/www/html/.....
in this folders i want the site to display and list and give access to the files.This works.

1) Now i want a FTP server to allow putting files into these folders, but now allowing the user, which accessing, to view parent directories or any other part of the hard disk, not deleting files, make folders and access all the folders downwards from the folder i give him. 2) Further more i want some special files not to be displayed.

Are these two points possible? Which server do i take best? vsftpd or proftpd? or an other one?
how do i configure this?

I have read so many instructions please help me. thank you.

Best regards

---

### Post by howefield on 2016-07-18
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by thorftp on 2016-07-18
> **howefield said:**
> Thread moved to the "*Server Platforms*" forum, probably a better fit.


Thank you.
I may need to add. I want to run this on an Ubuntu Version, or if better or even possible, on a raspberry pi.

Please help me.

Tanks.

---

### Post by mastablasta on 2016-07-18
> **thorftp said:**
> 

1) Now i want a FTP server to allow putting files into these folders, but now allowing the user, which accessing, to view parent directories or any other part of the hard disk, not deleting files, make folders and access all the folders downwards from the folder i give him. 2) Further more i want some special files not to be displayed.



sorry but this is a bit confusing.

so you want the user to see from certain folder downwards and has all the rights in that folder, but at the same time they would not see certain files? furthermore the user owuld only see a certain specified folder and nothing else. to hide files you add "." before them. it's not a problem if english is giving you trouble. try shorter sentences instead of long ones. it should make it more clear what you want to do. also there might be a LOCO team thatcould help you in your native language.

have a look at this and then see what you can and what you can't do: [SIZE=2]https://help.ubuntu.com/community/FilePermissions#Changing_the_File_Owner_and_Group
[/SIZE]

you need to understand chown and chmod commands.

i use sFTP for file transfer. keys are used instead of password. SSH /sFTP is easy to setup.

---

### Post by thorftp on 2016-07-18
Sorry for my confusing English. I will try it more easy:

I want the FTP Configuration to be the following:

There is the folder: /var/www/html/FOLDER/

Then the User logging in to the FTP should have following rights:

.) Uploading files should be allowed.
.) Making directories should be allowed.
.) Deleting Files or Directories should NOT be allowed.
.) Accessing any other Parent Directories should NOT be allowed.
.) Downloading Files should NOT be allowed through the FTP, but through the Apache Server (the website) yes.
 (in a short i want them to use the website to download things and not to load everything at once through the ftp access)

The thing with the Files not to be shown you can neglect.

I hope this is more clear now. Thank you any way for your answer.

Best regards.

---

### Post by mastablasta on 2016-07-19
.) Uploading files should be allowed. - [COLOR=#ff0000]Not an issue - give write access to user.[/COLOR]
.) Making directories should be allowed. [COLOR=#ff0000]- not an issue again write access[/COLOR]
.) Deleting Files or Directories should NOT be allowed. [COLOR=#ff0000]- this will be a problem i think, unless ther eis a trick with groups. but the options are read, write and execute. [/COLOR]
.) Accessing any other Parent Directories should NOT be allowed. [COLOR=#ff0000]- not an issue, you will give them access only to FOLDER[/COLOR]
.) Downloading Files should NOT be allowed through the FTP, but through the Apache Server (the website) yes. 
 (in a short i want them to use the website to download things and not to load everything at once through the ftp access) [COLOR=#ff0000]- this could be an issue - as soon as you can read files, you can also download them[/COLOR]


Why not give them only Apache server /website access then? there are file managers for web, where you can upload, donwload files. there are also file services available. i am not sure why you do not want them to be able to delete the file, but file services (e.g. ownlcoud etc) will keep a copy (version) of file even when user delets it. versioning might solve you issue. hard ot say since i do not knwo the setup.

think about it.

read means you can see what is on server. e.g. when you type in google.com you then see google logo. you can't change it but you can always save the displayed website or certain file on the site to local hard disk.
write means you see what is on server, you can download it to local storage, but but you can also manipulate with the file that is on server. change it, rewrite it, move it or remove it.
excecute is not an issue here i believe. so it is safer if this option is off for the whole folder.

---

### Post by thorftp on 2016-07-19
Thank you for your answer.
But HOW do i do this? How do i set it up?

Maybe i used the wrong word, the should not read it, the should only be able to list it.

I know that most of these things are not an issue, but how do i set them up?

Please help me, i have read so many instructions and i dont get any further.

Thank you

---

### Post by thorftp on 2016-07-19
I have created a user following this instruction

[http://www.netcup-wiki.de/wiki/VSFTPD_Installation_und_Einrichtung](http://www.netcup-wiki.de/wiki/VSFTPD_Installation_und_Einrichtung)

and this one

[https://maximilian83.wordpress.com/2007/11/07/vsftpd-virtuelles-webhosting-ftp-zugang/](https://maximilian83.wordpress.com/2007/11/07/vsftpd-virtuelles-webhosting-ftp-zugang/)


Now i can login but now it writes me this:

500 OOPS: cannot change directory:/var/www/html/FOLDER/

what do i do now?

thank you

---

### Post by mastablasta on 2016-07-20
the file pemissions article should have all you need: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

500 error - are you trying to access directory via apache? probably user has to be in group www-data (just a guess).

what instruction did you follow then?

Virtuelles Webhosting + FTP Zugang - was written for a very old version of Ubuntu. Still with some modifications (start&stop daemons...) and on first glance it looks like it should work.

the other one also seems good. are there any erorrs when you do the steps? you did modify them to use your folders instead, right?

---

### Post by Habitual on 2016-07-20
How many "users" are you expecting a solution for?
"Editors" can upload content easily with a few short terminal commands, however,
if there's 5?. Then another approach/solution may be necessary.

To the veterans helping out:
Wonder if
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
might be the way to go for more than a couple of "users"?

References:
[azendale answer]("http://askubuntu.com/questions/19898/whats-the-simplest-way-to-edit-and-add-files-to-var-www").

---

