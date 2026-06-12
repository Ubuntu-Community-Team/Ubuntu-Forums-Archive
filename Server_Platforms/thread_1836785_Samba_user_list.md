---
title: "Samba user list"
date: 2011-08-31
forum: Server Platforms
---

### Post by slotdoctor on 2011-08-31
So after much research I feel I have a better understanding of how my Ubuntu Server works. But, there are still questions running through my head.

Here I got a sample sheet to keep track of the users on my house. On file sharing. Could you guys tell me how could I improved? Or I am not understanding how is suppose to work. Any suggestions?

Thank you for the help.

SERVER = SERVER19
NAME = Tom-ADMIN 
PSSWD = tom19


		CLIENTS			TERMINALS
			
 SHARE -    USERS -PSSWD     -LOG IN	-NAME      -OS
									
 Tom_Share -Samson -19sam    -Samson -Tom_Desktop -Ubunutu10.10
                              Samy    Tom_Laptop   Win7
	    Lucy    luc19     Lucy    Lucy_Apple   X Lion
	    Jr      rocker19  Jr      Jr_Old_Desk  Win XP

									
Sudo	adduser		To set-up				
	smbpasswd -a	To authorize				
	smbpasswd -e	To enable

---

