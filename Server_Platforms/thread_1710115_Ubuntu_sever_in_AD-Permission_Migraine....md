---
title: "Ubuntu sever in AD-Permission Migraine..."
date: 2011-03-19
forum: Server Platforms
---

### Post by j_talbain on 2011-03-19
Hello all. I'm fairly new to linux and apparently have jumped into the deep end when it comes to linux configuring... So here is what I have done and what I am attempting to do.

   I have successfully installed Ubuntu Server 10.10 in VBox and using the script provided by SerbisS ([http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)) I was able to join the domain. The script threw an error saying it couldn't resolve dns but the server is joined and using samba I can share files with the network. The server's role will simply be that of a file server to store my users directories. Also I loaded the Gnome gui so I could use the server. Sorry I'm just not a big terminal guy.
   
   Where I am having trouble is trying set permissions. I understand that linux and windows don't have  the same permission scheme. I can manage the permission well enough through linux. The layout is simple enough. Each user has a folder that has permissions set for all users to rwx. In each dir is another folder that is private. Only the user and domain admins have access.

   Being a windows guy I rely on the gui (though I wouldn't mind a few pointers on how to do this next time in  the terminal...). I right clicked on each dir and changed the permissions so that each folder is owned by its respective AD member. At this point everything worked fine. I could navigate to the server from windows. I can access the shared folders and it blocks users without the appropriate permissions.

   The problem I'm having now is when files are created by windows users... They don't carry the permissions of the dir. The permissions are set as Owner = rwx, Group = r--, Others = r--. You can imagine my frustration if u,g,o is supposed to be rwx in all dir except "Private." And as far as I can tell, because it is a linux server, the permissions cannot be managed through windows. 

   I am stuck. Any help (in layman's terms please) would be greatly appreciated. Trust me, I have tried to read some of the documentation on the Samba site and other places, but my eyes started glaze over due to the jargon contained within. Plus the sites I have been to seem to take for granted that if you are at their site, you already understand the underlying principles of linux. 

   If you need to see my .config files let me know. Thanks for reading. (If this in the wrong section either let me know or please notify a mod and have them move it to an appropriate area.)

Edit:

Okay I may have solved one part of my problem. After more research, I edited my smb.conf and included inherit permissions = yes. I then added a block for my domain according to the example provided by SerbisS in the .conf file itself. Then I used 
sudo chmod 777 -R /path/to/someDirectory
 to set the permission where I want them. 

Now I can create files on the server from windows and everyone has rwx abilities. And when a file is created in and subsequent directories they inherit the appropriate permissions. Interestingly enough now files created in linux do not follow this scheme. The roles reversed and linux creates everything as rwxr--r--. I don't care that it does that I just need it work properly for my windows users.

Hmm I was going to say that I was still having a problem but I just tested something. I had forgotten that when a file is copied or moved the permissions are not carried with it. So if my user places something in their private folder and then moves it to a public dir the permissions change accordingly.

An interesting sidenote. When you share a folder the icon changes to reflect this setting. It displays a couple of arrows over the icon. Now the icon doesn't change and when I check the share properties, it does not show that it is being shared. I can still see/access the folders across the network so I'm not that concerned about it. If anyone knows the fix for this I would appreciate the help.

---

