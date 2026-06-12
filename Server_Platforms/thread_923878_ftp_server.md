---
title: "ftp server"
date: 2008-09-18
forum: Server Platforms
---

### Post by gishaust on 2008-09-18
hi

I want to know if I have the following theory right because I am having trouble with an ftp server I am trying to get working.

1. Install ftp server  sudo apt-get install proftpd

2. Create a fake shell in /etc/shells by adding bin/false (or other)

3. Then
   ```

   sudo mkdir /home/ftp/joesfolder
   sudo mkdir /home/ftp/marysfolder
   
```

4. If you want to create users for your ftp server you add users to the server an example of this would be,
```

   sudo useradd joe -p joespassword /home/ftp/joesfolder -s /bin/false
   sudo useradd mary -p marypassword /home/ftp/marysfolder -s /bin/false

```
5. Then in the the /etc/proftpd/proftpd.conf file you would add
```

#VALID LOGINS
<Limit LOGIN>
AllowUser joe
AllowUser mary
DenyALL
</Limit>

<Directory /home/ftp/joesfolder/*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
		Order Allow,Deny
		AllowUser joe
		Deny ALL
	</Limit>

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
<Directory /home/ftp/marysfolder/*>
Umask 022 022
AllowOverwrite off

        <Limit ALL>
		Order Allow,Deny
		AllowUser mary
		Deny ALL
	</Limit>

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>


```



If I do the following should I be able to log into the ftp server and only access that folder. Because I can't get it to work?

---

### Post by baudday on 2008-09-19
I use vsftpd. I explain in my blog how I set that up. Link in sig

---

### Post by gishaust on 2008-09-19
The above will work. from the terminal I can login to ftp server using a user name and password that I selected above however it will not let me upload anything when I use gftp. The logs say that I log in fine but when I try to upload gftp keeps skipping files i select. Does anyone suggestions why this might be happening?

---

### Post by baudday on 2008-09-19
That sounds like a permissions issue. Make sure the above directory and all sub-directories are either writable by the user you're using, or owned by that user.

---

### Post by gishaust on 2008-09-19
Yes they are I did check thanks for the idea. I think I know what the issue is. I found a similar issues on another forum it has to do with these commands

<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>


Some of them I think have to go up into 

        <Limit ALL >
		Order Allow,Deny
		AllowUser joe
		Deny ALL
	</Limit>


I can't seem to find what they mean on google. I only get howto

---

### Post by gishaust on 2008-09-19
It is fixed but I don't know why is anyone able to tell why it is work and is the server safe what I did was change

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>


to

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	AllowAll
	</Limit>

And gftp worked first go!!! is some one able what these mean
           MKD STOR DELE XMKD RNEF RNTO RMD XRMD

---

### Post by lazyart on 2008-09-19
those are commands used by ftp clients.  if you deny MKD and STOR for instance, the user won't be able to make directories or store files.  Google will help you with the others...

---

