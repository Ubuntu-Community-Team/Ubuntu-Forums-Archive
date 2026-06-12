---
title: "[Samba] username/pass issues"
date: 2009-08-22
forum: Server Platforms
---

### Post by MrBucket101 on 2009-08-22
I've got samba setup and working correctly for the most part. I can share files in a public directory and now I have moved onto private directories.

I have a user named brad, I already created a linux user named tom, he has access to the /bin/sh shell, and I did smbpasswd -a tom, and set his password (123456 for now)

I have created a samba share named Brad, and I setup some initial config options in the smb.conf.


When i try to access the share from my Vista64 PC, I get a login box which i was expecting, but when i type in Brad, and I type in 123456 for the password. I get an error message, and the prompt comes backup but this time with HOLLANBM-PC\Brad is in the login box.

I would like my users to be able to access their private shares independent of their computer.

Is their a way to do this short of renaming their samba names to be identical of their window login names? Also dave has a Mac

My ultimate goal is to have a public guest share for anyone on the network. And then two big private shares accessible to nate,tom,dave, and brad. (one would be an external hard drive and the other the internal) And then four private shares for each individual. 

here is my smb.comf:
```
[global]
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody

[public]
        comment = Public
        path = /home/samba/Public/
        read only = no
        guest only = no
        guest ok = yes
	veto files = .avi
[External]
	comment = external
	valid users = tom,nate,hollanbm,dave
	read list = tom,nate,dave,brad
	path = /home/samba/external_share
	write list = hollanbm

[Private]
	valid users = tom,nate,dave,brad
	writeable = yes
	path = /home/samba/local_share

[Brad]
	comment = Brad
	valid users = brad
	writeable = yes
	path = /home/samba/Brad

[Dave]
	comment = Dave
	valid users = dave
	writeable = yes
	path = /home/samba/Dave

[Nate]
	comment = Nate
	valid users = nate
	writeable = yes
	path = /home/samba/Nate

[Tom]
	comment = tom
	valid users = tom
	writeable = yes
	path = /home/samba/Tom


```

here is my smbusers file:
```
tom="tom"
nate="nate"
dave="dave"
brad="brad"
hollanbm="hollanbm"
```

---

### Post by windependence on 2009-08-22
Your users must exist and have the same password on the unix box as a unix user, and also in samba for this to work well. I would also suggest having all samba users exist on all Windows boxes (which may already be the case). Then, there are also Unix user permissions which can affect your SAMBA config.

-Tim

---

### Post by MrBucket101 on 2009-08-22
> **windependence said:**
> Your users must exist and have the same password on the unix box as a unix user, and also in samba for this to work well. I would also suggest having all samba users exist on all Windows boxes (which may already be the case). Then, there are also Unix user permissions which can affect your SAMBA config.

-Tim
I've got two out of the three done already.

I have created a linux user named Brad, and I assigned him a password of 123456, then i created a samba user Brad, and I assigned him a password of 123456. On his windows box though, his login is not Brad. I would like him to still be able to access his private share though, just by viewing the network neighborhood and typing in his user/pass that I assigned earlier.

---

### Post by Iowan on 2009-08-22
The "**username map=**" option should do that... Format (if I interpret help page correctly) is similar to: ```
unixBrad = windowsBrad
```
[This]("http://www.devshed.com/c/a/Administration/Handling-User-Accounts-in-Samba/1/") How-To didn't use quotes, [this]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/") one did.

---

### Post by MrBucket101 on 2009-08-22
> **Iowan said:**
> The "**username map=**" option should do that... Format (if I interpret help page correctly) is similar to: ```
unixname = windowsname
```

I will look into that option

One thing that concerns me though is, what if dave is using a guests laptop because his is upstairs, I would still like him to be able to access his private share while using the guests laptop.

If I use the above commands I'm sure that will resolve one of the issues I am having, but what of this concern. Is it not possible with the way samba works?

---

### Post by Iowan on 2009-08-22
My understanding (limited though it might be) is that if Dave is logged in to a guest's machine as "dave", he should still have access to "dave's" shares.

---

### Post by MrBucket101 on 2009-08-22
> **Iowan said:**
> My understanding (limited though it might be) is that if Dave is logged in to a guest's machine as "dave", he should still have access to "dave's" shares.

so if "dave" was logged into a guest machine as "john", "dave" could not access "dave's" shares?

---

### Post by windependence on 2009-08-23
I am sure there is a way to do it, but in most organizations you log in as yourself so the assumption is that you will be logged in as Dave. I do this mostly using FreeNAS or in my local network I have all UNix machines so unfortunately I'm a bit rusty but I'm sure a little googling will do it.

-Tim

---

### Post by MrBucket101 on 2009-08-23
> **windependence said:**
> I am sure there is a way to do it, but in most organizations you log in as yourself so the assumption is that you will be logged in as Dave. I do this mostly using FreeNAS or in my local network I have all UNix machines so unfortunately I'm a bit rusty but I'm sure a little googling will do it.

-Tim

I'm running out of things to search for, which is why I finally came here.

I just don't like the idea of tailoring my samba share for a specific machine/login. If I could have users validate themselves when they are using it that would be the optimum setup IMO.

---

### Post by abaden on 2009-08-23
Make sure that all your users have permission to access your shares. I have a group called "sambashare", and all my samba users are in that group. You could create a group for each folder, and then put samba users you want to access that folder into that group. Just make sure your directories are group readable and writeable. 

As far as your configuration goes, how are you trying to connect? I can connect to my Samba machine just fine from Windows or Mac, regardless of what user I'm signed in as. All you need to do is enter the username and password as it is on the Samba machine. I think the permissions might be what's throwing off your installation.


Alex

---

### Post by HermanAB on 2009-08-23
Howdy,

If you start off with the user names and passwords exactly the same on Linux and Windows, then Samba will keep the passwords the same from then on - if the user would change his password on Windows, it will change on Unix also.

Oh, also don't use a '$' in a password - that doesn't work - it confuses Samba.

Hope that helps!

---

### Post by Iowan on 2009-08-24
> **MrBucket101 said:**
> so if "dave" was logged into a guest machine as "john", "dave" could not access "dave's" shares?Does "john" have login/Samba account? I'm not familiar enough with Samba to know if you can map multiple Windows users to a common Unix user.

---

### Post by abaden on 2009-08-24
> **MrBucket101 said:**
> 
I would like my users to be able to access their private shares independent of their computer.

The way you have configured Samba, this should be the way it works. You can either map network drive or go to My Network Places -> View Workgroup Computers. On your Mac it should be autodetected, but you can always go to "Connect to Server" in the Finder "Go" menu. Then just enter the username / pass of the user you want to connect with. It should be completely independent of the windows user the way you have it setup.


Alex

---

### Post by MrBucket101 on 2009-08-25
Thank you all for your help, I now have most everything working just the way i wanted. I really appreciate it.

Now I have just one last problem to resolve.

I created another share called private, I plan on having it be a "shared" share between the four of us.

here is my new revised smb.conf
```
[global]
	invalid users = root,bin,daemon,adm,sync,shutdown
	unix password sync = yes
	os level = 20
	username map = /etc/samba/user.map
	map to guest = bad user
	encrypt passwords = yes
	security = user
[External]
	valid users = Thomas,hollanbm
	read list = Thomas
	path = /home/samba/external_share
	write list = hollanbm
[Brad]
	writeable = yes
	valid users = hollanbm
	path = /home/samba/Brad
[Tom]
	writeable = yes
	valid users = Thomas
	path = /home/samba/Tom
[Private]
        writeable = yes
	path = /home/samba/Private

```

As it is right now, I have not restricted the Private share to a certain group or anything. But, for some reason I am unable to write files to the share. I get a permissions error, at first i thought it was a linux permissions error. So i chmod -R 0775 the directory and it still didn't fix things.

I used webmin to check the active connections to samba and here is what was shown.

[IMG]http://www.mrbucket101.info/hosting/samba.png[/IMG]

---

### Post by windependence on 2009-08-25
Can you post the output of ls -l on the directory?

-Tim

---

### Post by MrBucket101 on 2009-08-25
> **windependence said:**
> Can you post the output of ls -l on the directory?

-Tim
root@server:~# ls -l /home/samba/Private/
total 4
-rwxrwxr-x 1 root root 5 2009-08-25 12:13 test.txt

---

### Post by MrBucket101 on 2009-08-26
bump

---

### Post by Iowan on 2009-08-26
Have you tried adding a **valid users=** option for the four of you?

---

### Post by windependence on 2009-08-27
> **MrBucket101 said:**
> root@server:~# ls -l /home/samba/Private/
total 4
-rwxrwxr-x 1 root root 5 2009-08-25 12:13 test.txt
Sorry, I meant ls on the Samba directory. I want to see what permissions you have on the Private folder. Also, remember Linux is case sensitive.

-Tim

---

