---
title: "vsftpd umask/permission problem"
date: 2008-02-26
forum: Server Platforms
---

### Post by fornews on 2008-02-26
I've tried setting in vsftpd.conf

local_umask=022
anon_umask=022

and to other values

followed with both

./init.d/vsftpd reload
./init.d/vsftpd restart

with out any luck. The files are always 600

I've read through a number of web pages here looking for an answer and
nothing I've found is helping.

Also, in case this matter....

drwxrwxrwx 2 nobody root
-rw------- 1 nobody nogroup

Could the directory and/or file ownership/group be part of the problem ?

I can tftp to the server but always the files are 600.

Any ideas ?
Should I use some other tftp daemon since vsftpd seems to have a problem ?

TIA
__________________
Thanks Edit/Delete Message

---

### Post by fornews on 2008-02-26
More info that will hopefully help...

It does not appear that vsftpd is in control of the tftp.

Here is my /etc/inetd.conf

tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /srv/tftp -U 022


And I restart vsftpd and xinetd via the following


/usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive


Any thoughts before I give up on this ??

TIA

---

### Post by Mr. C. on 2008-02-27
TFTP is the Trivial File Transfer Protocol, which listens on port 69.
FTP is the File Transfer Protocol, which listens on port 21.

Vsftp supports FTP, not TFTP.

Permissions work just fine in vsftpd.

MrC

---

### Post by fornews on 2008-02-27
Thank you Mr C.

I did come to the realization that vsftpd isn't in control of my TFTP so now I wonder what it'll take to get something other then 600 for files TFTPed to my Ubuntu box. 

Should I ask this question again but the angle that I'm able to TFTP so how do I make the files 644 rather then 600 ?

---

### Post by Mr. C. on 2008-02-27
> **fornews said:**
> Thank you Mr C.

I did come to the realization that vsftpd isn't in control of my TFTP so now I wonder what it'll take to get something other then 600 for files TFTPed to my Ubuntu box. 

Should I ask this question again but the angle that I'm able to TFTP so how do I make the files 644 rather then 600 ?

The -U option controls the umask for **put** mode (eg. you put new files to the server).  It has no control over files created on the client with a **get**, as that is the client's job.

So, in **get** mode, you need to specify the umask if you want it changed upon invocation of your tftp client.  Eg:

```
( umask 022; atftp --get -r somefile someTFTPhost )
```

This creates a subshell, from when the atftp command is run with the umask of 022.  The current shell's umask remains unaffected.  Remember, umask only affects *newly* created files.

MrC

---

