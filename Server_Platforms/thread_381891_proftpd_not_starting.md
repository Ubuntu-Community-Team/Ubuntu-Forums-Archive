---
title: "proftpd not starting"
date: 2007-03-11
forum: Server Platforms
---

### Post by mzracer360 on 2007-03-11
I followed [this how-to]("http://ubuntuforums.org/showthread.php?t=79588&highlight=proftpd+setup") for creating an FTP server.  I have it all configured the way I want it, but I can't get it to start up.  I get this message whenever I try: 

ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

---

### Post by DraZtiK on 2007-03-11
What error messages are in your /var/log/proftpd/proftpd.log?

posting your config may allow some to inspect it for any errors.

---

### Post by mzracer360 on 2007-03-11
The program has never run yet, so that file is empty.  the config file is the default one from the installation but with port 77 set and with the info from the tutorial at the end:

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

---

### Post by DraZtiK on 2007-03-11
Sounds like you have it set to start in inetd mode. 

change that line to

> ServerType 			standalone

or do a 

sudo dpkg-reconfigure proftpd

and set to standalone

---

