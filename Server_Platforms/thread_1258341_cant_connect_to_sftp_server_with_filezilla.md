---
title: "cant connect to sftp server with filezilla"
date: 2009-09-04
forum: Server Platforms
---

### Post by bilbo0a on 2009-09-04
i have a basic server setup (9.04) with openssh installed with default settings.
i use a static ip adress and i can connect to the server using putty. now i understand there is a sftp server running as well out of the box but when i try to connect using my username and password (same as i log into the server) i cant connect, error as below

Status:	Connecting to 192.168.1.100...
Response:	fzSftp started
Command:	open "XXXXXX@192.168.1.100" 22
Error:	Connection timed out
Error:	Could not connect to server

do i need to setup a user to use ftp, or allow it to this user?
Anything else to do here.

my goal is just to have access to the server for updating the weppage via dreamweaver.

any tips very much appreciated.:D

---

### Post by bear24rw on 2009-09-04
did you install openssh-server?

did you specify port 22 in filezilla?

---

### Post by bilbo0a on 2009-09-05
yes, i did install openssh and all seems to work ok as i can connect to the server via putty. i did specify port 22.

---

### Post by sahabcse on 2009-09-05
check whether any firewall enabled?

---

### Post by bear24rw on 2009-09-05
That really odd, can you filezilla to localhost? (assuming its not headless)

---

### Post by bilbo0a on 2009-09-05
i am not sure which firewall would block me since i am sitting behind the firwall.
i try to connect from my homepc (with windows firewall not running) to my linux server and both are connected to the router.
the router has a firewall running but i thought this is just for the connections over the internet.
as for the server, i did not install nor configure a firewall, so would there be any running?

---

