---
title: "FTP problem - 550 no such file or directory"
date: 2014-01-17
forum: Server Platforms
---

### Post by Pascal_Paquin on 2014-01-17
Hi, I have try to setup a FTP server using gadmin-proftpd.
Everything is working fine, I can connect, I have setup the account to go in the folde /home/LinuxUsername, there's already some folder there, like Desktop, Video, Music, etc. and I have add another folder call sounds.
In gadmin, I have check every option related to the folders.
When I connect, if I try to go in any of the Linux created folder, it's working fine, but if I try to go in the sounds one, it tells me 550 /sounds: No such file or directory
Another problem is that if I try to upload a file in any of the other folders, it tells me that I don't have the permission.. Again, everything is check in gadmin for the folder permission

Also if I test the server with ftptest.net I get that result :

```
Error: Malformed directory listing 
       Error: Line feed received without preceding carriage return 

              Results

Error: Line feed received without preceding carriage return 
       
[LIST]
[*]The replies sent by your server are violating the FTP specifications. 
[*]You have to upgrade to a proper server. 
[/LIST]


```
Is there anything I should do to correct that ?
Also, I'm starting to use Linux, so that's why I have use gadmin-proftpd, I have try in the last days to setup something using only proftpd and I wasn't able to at least connect, I was following some online tutorial with no luck.

Edit : If I have understand correctly, it seems to create new user on the pc, is it possible that if my "Linux username" is all in lower case and that I have create a FTP username that is the same but with some letters in uppercase that it will conflict ?

---

### Post by Pascal_Paquin on 2014-01-17
I have made some test on my lunch time.. I have create another user (call testtest) that have acces directly to the sounds folder.
I can see all sub-folder and files, I can rename file/folder, create new folder but I can't acces any subfolder or move a file in a subfolder, it tells me there is no file or folder of that type
Also, my first account can now acces the sounds folder without a problem but cannot do anything like my testtest account.
The only thing I have done other than create an account is to disable/enable the server

---

