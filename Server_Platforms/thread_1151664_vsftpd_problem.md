---
title: "vsftpd problem"
date: 2009-05-07
forum: Server Platforms
---

### Post by artheus on 2009-05-07
Hi!

I've got a problem with my vsftpd on my ubuntu 8.10 server.

When I connect to it from a local user I get in without problem.. But when try to log in (via ftp) through an external computer I get the response

```
Status:	Resolving address of myserver.org
Status:	Connecting to 123.456.789.10:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Ubuntu server FTP Deamon.
Command:	USER myusername
Response:	331 Please specify the password.
Command:	PASS *******************
Response:	230 Login successful.
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,100,62,83)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```


What is the problem!?


Thanks!
/Artheus

---

### Post by artheus on 2009-05-07
uuuhm.. the solution was very weird!
I tried to change the port to 22.. and it worked..

hmm... why might that be??

---

### Post by LiQuidAiR on 2009-05-10
Connecting to port 22 sounds like it's connecting over an SSH socket.  I've read that connecting to port 22 using an FTP client is bad for business.  It allows a connection or a user to access all files on your server.

Check this out, [http://ubuntuforums.org/showthread.php?t=1152705&highlight=VSFTPD](http://ubuntuforums.org/showthread.php?t=1152705&highlight=VSFTPD)

---

### Post by artheus on 2009-05-26
Yeah that was correct! Thanks!
After I checked now, I could actually see that any user could access any file on my server.. Which, as you said, is bad for bussiness. So I've now closed the SFTP on my OpenSSH.. So then my regular problem still remains.. :(

So What might be the problem with my ftp?
I've opened port 21 on my router. But the problem might maby lay in the router anyway.. Because when I connect to my FTP locally it works! But externally.. nope..

Help?

//Artheus

---

### Post by artheus on 2009-05-26
BUT!! The router cant be the problem!?

Cause Filezilla tells me as you see in the first post that my login is successfull, but I just can't resieve the directory listing..

So what is the problem!? :3

//Artheus

---

### Post by Alekz_ on 2009-05-26
FTP doesn't use ONLY the port 21...

Try to open the port 20 on your router and make a new test...

EDIT: Port 20 is common used to Passive Mode (coincidently, your problem! :))

---

### Post by artheus on 2009-05-26
Thanks! But that port was already open!
I've opened 20, 21 and 22.

But the FTP doesn't work :S

//Artheus

---

### Post by Alekz_ on 2009-05-26
Can you try to connect without the Filezila client? I mean.. Use your OS ftp client from the CLI.. 

```
ftp YOUR_SERVER
```

Sometimes GUI applications use another range of ports to connect (i.e.: browser).

One more thing... Can you post your vsftp conf file? And... Are your running the daemon stand-alone or is it starting with inetd?

---

### Post by artheus on 2009-05-26
Well yes. It connects.

From Local computer it works fine.. But still If I use an external computer it's an error.

Is says :

227 Entering Passive Mode (192,168,1,1,131,61)
ftp: connect: No route to host

So it works fine to login. But whenever I try to see the file list, it gives an error.

---

### Post by artheus on 2009-05-26
And I guess this must have something to do with that I've moved the Server from my apartment to my parents house?
Cause the IP range on the DHCP have changed from 192.168.1.XX to 198.0.0.XX..
But there is nothing wrong with anything other than the FTP..

hmm.... ?

---

### Post by LiQuidAiR on 2009-05-26
Sound like you need to add the following lines to your vsftpd.conf and open up the same port numbers as what you put in your config


add 

pasv_min_port=32000
pasv_max_port=33000

now open and forward 32000 - 33000 on your firewall/router to go to your ftp server computer.  BOOM SHAKALAKA!

Don't forget to restart vsftpd.  The next thing you need to configure (I'm guessing) is permissions.  You may be able to connect now but your sending and downloading of files may not work right.

---

