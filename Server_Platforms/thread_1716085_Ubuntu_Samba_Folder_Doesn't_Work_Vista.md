---
title: "Ubuntu Samba Folder Doesn't Work Vista"
date: 2011-03-27
forum: Server Platforms
---

### Post by blsmit on 2011-03-27
I got ubuntu samba server on server 10.04
 
username:user1 , Home folder: /home/user1 This user connects from a macbook pro no problem.
 
I followed the same steps to set up user2
 
username:user2 , Home folder: /home/user2 This user does not connect from windows vista.
 
I have the correct ports open, 137-139 & 445, and can connect from the macintosh, but not vista.
The error says that the username or password is in correct.
If you need some log files or config files, just let me know where to go and they're all yours!
 
Thanks for the help in advance, 
Blsmit

---

### Post by Doug S on 2011-03-28
First, please know that I am not a Samba expert. I just made a new server with Ubuntu server 10.10 and Samba in January. While I have used Linux for more than 15 years now, I have never implemented Samba before.
 
Second, there was another similar thread on these forums just a few days ago, but I couldn't find it just now to provide a link.
 
The Mac wouldn't normally connect to your server via samba, it would normally use NFS (I think).
 
On my system, I can connect to the samba shares from windows XP, vista and windows 7 (and, actually, I can not connect from the MacBook Pro and haven't yet got around to trying to figure out why not). With Samba I did have some authentication issues and such at first. In the end I had to make the user names and passwords the same on the windows machines and the Linux server. I also had to set the passwords line in smb.conf to encrypted from the default of not encrypted, although I cann't recall why. This line:
   encrypt passwords = true

I also use a unique workgroup name for all of the windows computers on my network, and I used that workgroup name in smb.conf file. This line:
   workgroup = SHOME

---

### Post by metalf8801 on 2011-03-28
Apples OS X uses samba (At least for now. They are phasing it out) But of the time being OS X uses a very old version of samba that is still licensed under the GPLv2 

I've gotten my Windows boxes to work with samba by making the Samba share accessible to anyone (which is a really bad idea even if its only a home server) 
I did that by using the following command 

chmod -R 777 /name of your share 


Just a thought 
Dan

---

### Post by blsmit on 2011-03-28
For some reason I could not change the smb.conf, but no matter, later I will copy and edit and then use the original.
One of my issues is that the computer doesn't have a log in password, and windows won't let a blank password go through.
I changed the permissions to 777 on both folders and will check back with results tonight.  
Its quitn' time right now.

Thanks,
Blsmit

---

### Post by Z.K. on 2011-03-29
> **blsmit said:**
> For some reason I could not change the smb.conf, but no matter, later I will copy and edit and then use the original.
One of my issues is that the computer doesn't have a log in password, and windows won't let a blank password go through.
I changed the permissions to 777 on both folders and will check back with results tonight.  
Its quitn' time right now.

Thanks,
Blsmit


you need to be root to change /etc/samba/smb.conf.  In other words you need to> sudo chmod 777 /etc/samba/smb.conf.  Also, if you use passwords, you probably need to add the user and password of your windows machine to the linux machine.  

:)

---

### Post by blsmit on 2011-03-29
Heres where I'm confused.  The Vista machine is named User3-PC with the username of User3.

I've added User3 to the ubuntu server and attempted to connect to 192.168.x.xxx\User3, It askes for Username and Password, 
I put in User3 and blank password--no go
After this is spits out Username: User3-PC\User3
I enter blank for password--no go
I enter WORKGROUP\User3 blank password--no go


Next step is to change the samba group to User3-PC.

Changed the samba group. still doesn't work.



Thanks, 
Blsmit

---

### Post by Doug S on 2011-03-30
I do not allow use blank passwords on my network, so our systems are different that way. So, (and recall I am not a samba expert) I don't know if I can help. If you think it might help, I could post my smb.conf file here.
 
If you trust all of your users you can change the permissions on /etc/samba/smb.conf as suggested above. On my system no. I keep my working copy of smb.conf in my home directory and copy it over as super user, maintaining restricted access.

---

### Post by nosebreaker on 2011-03-30
I'm not sure if it helps, but I'm going through my samba config now, and I disabled SELinux and then it worked.  Don't forget to chmod 755 the /share you created as well!

I'm stuck on the part where nautilus can mount the share just fine, but I can't mount it via the command line!  I've tried many variations of the following on my client desktop:
```
sudo mkdir /mnt/public
sudo mount -t cifs //server/share /mnt/public
```

I've tried many variations of -o domain=something,username=anybody,password=foo

Nothing I do works from the command line, but the GUI does!

On the server's smb.conf
```

[public]
    comment = Public Stuff
    path = /public
    public = yes
    writeable = yes
    browseable = yes
    guest ok = yes

```

---

### Post by spynappels on 2011-03-31
Just a thought, Windows 7 sends a domain name along with the username and password if you try to map a SMB share. Not sure if Vista is the same but I suspect it might be.

I got round it by selecting "Sign in as different user" and escaping my username with a backslash, so my user name becomes \username and this stops the Win7 client trying to pass an incorrect domain during authentication.

---

### Post by Morbius1 on 2011-03-31
There's a good chance I'm misinterpreting your posts but if the Windows machine is passing a blank password then the Samba server has to be set up to accept a blank password.

You need to add a line to the [global] section of smb.conf:
```
null passwords = yes
```Then restart samba:
```
sudo service smbd restart
```You will also need to set up the samba password database with a blank password:
```
smbpasswd -a -n user3
```Finally there is a package that's installed by default on Ubuntu desktop called libpam-smbpass - I don't know if it's installed by default on Ubuntu server. It's function is to override the smbpasswd with the local login password at every boot. That needs to go:
```
apt-get remove libpam-smbpass
```

---

### Post by blsmit on 2011-03-31
Got this to work!

What I had to do was:
1. Add a password to the vista account
2. Remove the old ubuntu account with ```
sudo deluser --remove-home user3
```
3. Add the new account with ```
sudo adduser user3
``` I actually just ENTERed my way through the password and information.  4. Add password to samba list ```
sudo smbpasswd user3
```. Enter the same password as Vista User3 
5. open up the permissions with ```
sudo chmod 777 /home/user3
```6. Add the workgroup of user3-PC to /etc/samba/smbd.conf. ```
sudo vim /etc/samba/smbd.conf
```7. Restart the samba server with ```
sudo service smbd restart
```8. On Vista Machine Run \\192.168.xxx.xxxx\user3 enter samba username and password

Thank you all for the help!!
Hope this will help someone in the future!

Blsmit

---

