---
title: "proftpd connection problems"
date: 2009-07-09
forum: Server Platforms
---

### Post by artheus on 2009-07-09
Hi! I've got some major problems connecting to my ftp.. Localy it works fine to connect to the ftp using 192.168.1.100 (which is the lan-ip of the ftp-server) but whenever using the wan-ip it fails.
I have configured my router, portforwarding and everything. I've even tried to disable the firewall completely and using my server as my networks DMZ-server. But nothing works.. I've configured the firewall on the server, and I've tried to disable that too.. But nothing seems to help..

here is the response I get from Filezilla when trying to connect via my domain, or my wan-ip (doesn't matter which, same reponse)

```
Status:	Resolving address of mydomain.com
Status:	Connecting to 123.456.789.10:2121...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.1 Server (The server) [123.456.789.10]
Command:	USER myusername
Response:	331 Password required for myusername
Command:	PASS **********
Response:	230 User myusername logged in
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PORT 192,168,1,185,192,247
Response:	500 Illegal PORT command
Command:	PASV
Response:	227 Entering Passive Mode (123,456,789,10,218,57).
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

I've both tried MasqueradeAddress as my lan-ip, wan-ip and my domain name. Nothing helps.

And as you can see I've set the port to 2121 instead of default 21, I've tried them both, no change. In the proftpd.conf I've changed it to the correct port number for each connection attempt. And I've restarted the proftpd standalone with "sudo /etc/init.d/proftpd restart". Still no luck..

What is the cause of this problem!?

I really don't understand!

Thankful to any help I can get!

Cheers,
Artheus


P.S : In the Filezillaresponse-field I've changed my wan-ip to 123.456.789.10 and my domain to mydomain.com, for security reasons.

---

### Post by loudog23 on 2009-07-13
I suggest you this excellent thread -> [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

-If you connect with your file browser and you can log in and list but it fails only when retriving your files, it's prolly your passive ports.
Open a port range 60000-65535 in your router and firewall
Also uncomment the PassivePorts line inside proftpd.conf and set the ports to te same in your router & firewall
```
PassivePorts                    60000 65535
```

-If you get kicked by a connection time out at (or right after) login, you then need to make sure you have this in your proftpd.conf (happens when using a ddns service and or router)
    ```
IdentLookups			off
UseReverseDNS                   off
```

-I also remember having the "500 Illegal PORT command" when not using port 21. (the only reason why i got it)

-Also make sure you have correct permision in the folder. If you cannot acces the folder, proftpd will kick you out since he cannot list the folder.

if all this dosen't help you, please refer to the thread i linked, i found all my answer in there and now have it running smoothly.... or tell me exactly when you get kicked and why if you **try to dwl from your web browser**. Be more precise and i might be able to help you.

cheer
lou

---

### Post by artheus on 2009-07-14
Thanks for that!

It seems that I also had to use "MasqueradeAddress mydomain.com" to get it to work properly! The UseReverseDNS made no change when not having the masquerade address..

Cheers,
Artheus

---

