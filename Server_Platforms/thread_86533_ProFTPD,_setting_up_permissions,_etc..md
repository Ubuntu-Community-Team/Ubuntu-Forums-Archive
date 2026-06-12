---
title: "ProFTPD, setting up permissions, etc."
date: 2005-11-05
forum: Server Platforms
---

### Post by Aven on 2005-11-05
Alright, I'm a newbie at FTP servers but I really need to set one up as soon as possible so please help!

I've read the ProFTPD docs but they won't bring a bell to me :\

So, could you show me an example on what to have in the config for the following:

To lock and set the user on /home/blah
To give user 777 chmod privillages
To give a user 50 MB space

What would I have to do to do the above?

Please help! and thank you :)

---

### Post by frodon on 2005-11-05
Maybe my [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=79588") could help you ;)

---

### Post by Aven on 2005-11-05
yeah, I've read that too, but it still doesn't explain on how to set certain MB space...

and it shows how to place permissions for directories, but isn't there a way to set permissions for certain users for certain directories? thanks

---

### Post by frodon on 2005-11-05
What do you mean by "how to set certain MB space" ? Do you mean to allow the user to write only 50Mo on your shared directory ?

I don't use different users for my server, however if you want some users to see more directories than others you can do it like that : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```With this configuration userftp is able to see and list all the folders and user2 is able to use the upload directory but isn't able to see the files in the download directories.

---

