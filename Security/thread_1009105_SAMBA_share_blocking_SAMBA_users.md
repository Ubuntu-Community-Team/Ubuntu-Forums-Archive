---
title: "SAMBA share blocking SAMBA users"
date: 2008-12-12
forum: Security
---

### Post by dm993 on 2008-12-12
I've been searching the forums for this particular problem but I can't find it anywhere. I am a Linux newbie but have enjoyed putting together a Linux server that we're going to run as a Proxy with Squid-cache and DansGuardian (all gone great)

I've set up SAMBA on Intrepid 8.10 purely to share out the contents of a single shared folder. 

Within smb.conf with **guest ok = yes** I (every XP client) can access the share.

But I want only approved SAMBA users to access the share, **guest ok = no**, I have created the users to match those in the Linux system already using **smbpasswd -a username** then setting the password as required.

When I try and connect from my XP machine I get the logon box but I am always denied.

Any ideas would be awesome, thanks!

---

### Post by albinootje on 2008-12-12
Did you add a line in that share section with for example :
valid user = joyce andrew sue georg maria nelson elisa johnny

---

### Post by dm993 on 2008-12-12
Hey thanks for the reply

I hadn't tried that line but I had tried
**admin user = username**

I have edited smb.conf to include the **valid user** line, I do not get a permission denied message from my XP client, but the login box never accepts the login credentials.

any more ideas? Thanks, Dave

PS: Is it possible that the encryption method for the passwords might be inconsistent between XP/Ubuntu or that I need to further edit other smb files?

---

### Post by albinootje on 2008-12-12
Do you have the following in /etc/samba/smb.conf ?

security = user
encrypt passwords = true

Check also the samba logfiles.
Try ls -latr /var/log/samba/ on your samba-server.
Then check those logfiles which are at the bottom of that listing.
You can temporarily higher the log level by adding for example :
log level = 2
And then restart Samba.

Here's an example of a share which works fine with MS-Windows 2000 :

  [office]
    comment = Office Share
    path = /home/samba/office
    valid users = user1,user2,user3
    public = no   
    writable = yes
    printable = no

---

### Post by albinootje on 2008-12-12
By the way, from a Linux-box (or with "localhost" on the server itself) you can test whether your samba-user can manage to log in succesfully :

$ smbclient //192.168.22.22/software -U user1

Password: 
Domain=[OFFICE] OS=[Unix] Server=[Samba 3.0.22]
smb: \> ls

  .                                   D        0  Tue Dec  9 17:23:48 2008
  ..                                  D        0  Sun Nov 30 17:52:28 2008
  some_data                           D        0  Tue Jul  8 19:15:23 2008

smb: \> quit

---

### Post by dm993 on 2008-12-12
/etc/samba/smb.conf
**security = user**yes
**encrypt passwords = true** yes

/var/log/samba/log.myPCname
[B]
[2008/12/12 15:24] lib/util_sock.c:write_data(1059)
[2008/12/12 15:24] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error connection reset by peer
[2008/12/12 15:24] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2008/12/12 15:24] smbd/ipc.c:api_fd_reply(333)
  api_fd_reply: INVALID PIPE HANDLE: 74a5 [/B]

/var/log/samba/log.smbd (seems unhappy about the 'valid user' statement in smb.conf)
[B]
[2008/12/12 15:23] param/loadparm.c:map_parameter(6110)
  unknown parameter encountered "valid user"
[2008/12/12 15:23] param/loadparm.c:lp_do_parameter(7196)
  ignoring unknown parameter "valid user"
[2008/12/12 15:23] printing/print_cups.c:cups_connect(68)
  unable to connect to CUPS server localhost:631 connection refused
[2008/12/12 15:24] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
[/B]

I also tried connecting from the box itself using the command you mentioned
**$ smbclient //192.168.22.22/software -U user1**
but I got a message back as follows
"The program 'smblient' can be found in the following packages:
* samba4-clients
* smbclient
"
It then suggests I install these packages, which is strange because I can use SAMBA, just not with a username to login

Am I missing somethihng, thanks again for looking this, Dave

---

### Post by albinootje on 2008-12-12
To see whether your smb.conf syntax is OK, run :

testparm

And you can install smbclient by running : sudo apt-get install smbclient

---

### Post by albinootje on 2008-12-12
Sorry. I just checked with my working samba-config. It should be "valid users", and not "valid user".

---

### Post by dm993 on 2008-12-12
TestParm has told me it does not know about the "valid user" parameter and ignores it

I have installed smbclient and it fails to login using smbclient //localhost/software -U username
from the box itself giving this error

**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**

Update:
on the samba server this command does not work
$ smbclient //localhost/software -U username

but this does
$ smbclient -L 127.0.0.1 -U username

Also I have corrected valid user to valid users (ok :) )

---

### Post by albinootje on 2008-12-12
Okay :)

The "software" share was just an example.

With : smbclient -L localhost
you should be able to see the names of the shares.
Just press enter when it asks for a password.

Then try again with a valid share from your samba-server.

---

### Post by dm993 on 2008-12-15
Morning!

Thanks for the advice, I can now login from the samba server box to the share I setup using
**smbclient //localhost/share -U username**

Windows XP client still doesn't like it though giving some permission error, once I ok this message I can keep trying to log in unsuccesfully but no error message is produced

---

### Post by albinootje on 2008-12-15
Check the last bit of the logfiles in /var/log/samba/ for errors.
You might need to put the log level higher in /etc/samba/smb.conf and restart samba.

---

