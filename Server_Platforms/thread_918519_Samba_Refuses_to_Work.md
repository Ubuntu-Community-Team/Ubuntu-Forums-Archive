---
title: "Samba Refuses to Work"
date: 2008-09-13
forum: Server Platforms
---

### Post by snick512 on 2008-09-13
Hi. 

I'm trying to setup Samba to obviously share files from linux. But I'm trying to share from linux to my windows laptop.

And when I try to connect from Windows it will sometimes give me a user/pass, but when i type in the correct information it still doesn't work. Sometimes it won't even prompt me for the user/pass it'll just ignore the request.

I'm confused about this, because I've even copied a working configuration from a friend, and just edited the paths/computer names to my needs.

I've tried using the GUI in Gnome, and even in KDE. Both fail. Even tried doing it bare in the console, which I had first tried it in console anyway.

does anyone have any solutions for this? much appreciated.

---

### Post by Sef on 2008-09-13
moved to server platforms.

---

### Post by windependence on 2008-09-13
Well, since you've done so many things at once you may it screwed up but let's try a few things.

Change the following in your smb.conf:

In the [global] section add this line:

```
security = share
```

In each of your shares sections make sure they read like this:

```
[sharename] 
guest ok = yes 
guest only = yes 
guest account = ftp 
path = /home/username/FilesToShare 
writeable = yes 
```

Then, you need to restart samba:

```
sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start
```

smb.conf is located at /etc/samba/smb.conf 

Just a tip. When troubleshooting any issue, do only ONE step at a time, and if it does not work, change things back to the way they were before you made the change. That way, you don't break other things trying to fix the current issue. ;)

-Tim

---

### Post by trmentry on 2008-09-13
> **snick512 said:**
> Hi. 

I'm trying to setup Samba to obviously share files from linux. But I'm trying to share from linux to my windows laptop.

And when I try to connect from Windows it will sometimes give me a user/pass, but when i type in the correct information it still doesn't work. Sometimes it won't even prompt me for the user/pass it'll just ignore the request.

I'm confused about this, because I've even copied a working configuration from a friend, and just edited the paths/computer names to my needs.

I've tried using the GUI in Gnome, and even in KDE. Both fail. Even tried doing it bare in the console, which I had first tried it in console anyway.

does anyone have any solutions for this? much appreciated.

did you check the samba server option box during the install of the server?

the reason i ask, is I've had this happen on both gusty and hardy...

o install server 
o select samba server on that screen during install
o once server is up, modify my smb.conf file to what i want to have access to what shares.
o shares are seen by windows clients yet, when trying to access, get challenged for user/passwd.  
o correct user/passwd is entered that was entered in smbpasswd but no access is granted.

so then I did a

o apt-get purge samba-common samba
o apt-get install samba
o modify smb.conf back to what it was before, works just liek it should.

so when I install servers now I dont' install samba during install.  I apt-get update and apt-get install it after I get into the server for the first time.

my smb.conf is fairly straight forward.   a share I have looks liek:

```

[fileserv]
        path = /shares/fileserv
        valid users = @users
        admin users = @admin
        write list = @admin

```

---

