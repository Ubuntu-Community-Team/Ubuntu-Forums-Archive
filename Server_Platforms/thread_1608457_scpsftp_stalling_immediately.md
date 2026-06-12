---
title: "scp/sftp stalling immediately"
date: 2010-10-29
forum: Server Platforms
---

### Post by DevgruSeal on 2010-10-29
I'm trying to upload a ~650kb file to Ubuntu Server 10.04.

sshd is running, and I can connect fine.

If I do: ```
scp file.zip user@host:~
```it never copies the file; it just sits there.

If I do:```
sftp user@host
sftp> put file.zip
```
I get:
```
file.zip       0%    0     0.0KB/s - stalled - 
```

P.S. I have already tried adding "[those lines](http://ubuntuforums.org/showpost.php?p=5839296&postcount=3)" to my /etc/sysctl.conf file, as well as changing my MTU to 1492.

---

### Post by the_original_billq on 2010-10-29
Can you go the other way?  (ssh to the target, then do the scp/sftp from there?)

If you ssh to the target, can you create files where you are trying to do the copy? (do you have write permission there?)

I'm not sure why you reduced the MTU...  are you on a VPN?

-Bill

---

### Post by aeiah on 2010-10-29
do ```
 scp -v file.zip user@host:~/file.zip
```

maybe your scp issue is just that it doesn't recognise user@host:~ and you need to put user@host:~/

either way, adding the verbose flag should yeild some information

---

### Post by DevgruSeal on 2010-10-29
> **the_original_billq said:**
> Can you go the other way?  (ssh to the target, then do the scp/sftp from there?)

If you ssh to the target, can you create files where you are trying to do the copy? (do you have write permission there?)

I'm not sure why you reduced the MTU...  are you on a VPN?

-Bill

I'm on a Windows machine, so I can't ssh in reverse like that. The ubuntu server is on the same machine, in a VM. I can create files; the folder I'm uploading to is owned by user:user with 755 rights. I reduced the MTU just to test, in case it magically fixed everything - it was suggested in a thread I read through.

> **aeiah said:**
> do ```
 scp -v file.zip user@host:~/file.zip
```

maybe your scp issue is just that it doesn't recognise user@host:~ and you need to put user@host:~/

either way, adding the verbose flag should yeild some information

Adding the verbose flag didn't yield much information related to the stalling:
```
>scp -v file.zip user@192.168.0.99:/home/user/file.zip
Executing: program /usr/bin/ssh host 192.168.0.99, user user, command scp -v -t /home/user/
OpenSSH_4.7p1, OpenSSL 0.9.8g 19 Oct 2007
[..snip..]
debug1: Next authentication method: password
user@192.168.0.99's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending command: scp -v -t /home/user/
Sending file modes: C0500 677695 file.zip
Sink: C0500 677695 file.zip
file.zip                                                  100%  662KB 661.8KB/s   00:00

```
This is new, by the way. This morning I wasn't even getting a 100%. This is false, anyway. It continues to stall at this point, and when I check the server, file.zip is 0 bytes.

Doing verbose mode in sftp results with this:
```
sftp> put file.zip
Uploading file.zip to /home/user/file.zip
Couldn't get handle: Permission denied
```

/home/user/ is owned by user:user, with 755 rights.

---

