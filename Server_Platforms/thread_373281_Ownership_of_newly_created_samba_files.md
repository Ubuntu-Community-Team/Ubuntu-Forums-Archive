---
title: "Ownership of newly created samba files"
date: 2007-03-01
forum: Server Platforms
---

### Post by lutzky on 2007-03-01
```
ohad@dekel:/mnt/matlab_jobs/ohad$ mount | grep cifs
//siglab/matlab_jobs on /mnt/matlab_jobs type cifs (rw,mand)
ohad@dekel:/mnt/matlab_jobs/ohad$ whoami
ohad
ohad@dekel:/mnt/matlab_jobs/ohad$ ls -ld
drwxr-xr-x 7 ohad nobody 0 2007-03-01 13:02 .
ohad@dekel:/mnt/matlab_jobs/ohad$ touch file
touch: setting times of `file': Permission denied
ohad@dekel:/mnt/matlab_jobs/ohad$ ls -ld file
-rw-r--r-- 1 root Domain Users 0 2007-03-01 13:10 file
ohad@dekel:/mnt/matlab_jobs/ohad$ echo > file
-bash: file: Permission denied
```

Note that the owner of the newly create file is root... this happened after reinstalling the server. What could cause this?

---

### Post by yota on 2007-03-01
You can control the owner of the created files (assuming that there's no authentication) in /etc/samba/smb.conf with the directive:
```

guest account = <your_user_of_choice>

```
moreover adjust the file permissions with:
```

create mask = 0666
directory mask = 7777

```
just choose the approrpiate mask.

Hope this helps!

---

### Post by lutzky on 2007-03-01
But I want the owner of the new file to be, well, the user who created it - like any normal filesystem... It used to work this way.

---

### Post by yota on 2007-03-01
Ok, in this case you have to setup authentication (security=user) and enable users with smbpasswd.

Look at 'man smbpasswd' & 'man smb.conf' for details.

---Edit:
I saw that also "security=share" can be used (without a guest directive), and still have named logon via samba, but as the documentation says it can become quite confusing to understand bindings between given credentials and matching local unix user chosen by the server...
Anyway here's an extract about this possibility:
> 
 SECURITY = SHARE

              When  clients connect to a share level security server they need
              not log onto the server  with  a  valid  username  and  password
              before attempting to connect to a shared resource (although mod&#8208;
              ern clients such as Windows 95/98 and Windows  NT  will  send  a
              logon  request with a username but no password when talking to a
              security = share  server). Instead, the clients send authentica&#8208;
              tion  information  (passwords) on a per-share basis, at the time
              they attempt to connect to that share.

              Note that smbd  ALWAYS uses a valid UNIX user to act  on  behalf
              of the client, even in security = share level security.

              As  clients are not required to send a username to the server in
              share level security, smbd uses several techniques to  determine
              the correct UNIX user to use on behalf of the client.

              A list of possible UNIX usernames to match with the given client
              password is constructed using the following methods :

              ·  If the guest only parameter is set, then all the other stages
                 are missed and only the guest account username is checked.

              ·  Is a username is sent with the share connection request, then
                 this username (after mapping - see username map), is added as
                 a potential username.

              ·  If the client did a previous logon  request (the SessionSetup
                 SMB call) then the username sent in this SMB will be added as
                 a potential username.

              ·  The  name  of  the service the client requested is added as a
                 potential username.

              ·  The NetBIOS name of the client is added  to  the  list  as  a
                 potential username.

              ·  Any  users on the user list are added as potential usernames.

              If the guest only parameter is not set, then this list  is  then
              tried  with  the  supplied password. The first user for whom the
              password matches will be used as the UNIX user.

              If the guest only parameter is set, or no username can be deter&#8208;
              mined  then  if  the  share  is marked as available to the guest
              account, then this guest user will be used, otherwise access  is
              denied.

              Note that it can be very confusing in share-level security as to
              which UNIX username will eventually be used in granting  access.

              See also the section NOTE ABOUT USERNAME/PASSWORD VALIDATION.


---

### Post by lutzky on 2007-03-01
Actually, I have security=ads - this is an active domain environment.

---

### Post by yota on 2007-03-07
> **lutzky said:**
> Actually, I have security=ads - this is an active domain environment.

It would have been usefull if you stated this early...

Anyway I think that this thread can be handy to you:
[http://ubuntuforums.org/showthread.php?t=280702](http://ubuntuforums.org/showthread.php?t=280702)

---

