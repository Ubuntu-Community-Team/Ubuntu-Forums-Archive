---
title: "Another smb not working in windows thread"
date: 2014-04-16
forum: Server Platforms
---

### Post by monkey10120 on 2014-04-16
So I finally decided to post a thread after going though 31! google pages of similar threads. I have tried all that I could and I hope one of you can help me. 

I set up my first samba ubuntu server at work so that me and the IT's can access our own folder for files we want hidden. I set up the server, got it configured and was even able to get my other ubuntu desktops to open the share and write to it no problem. However, after getting all hyped up I went to a windows machine and I get \\******* is not accessible. You do not have permissions. So I googled and googled, changing permissions, changing rules adding lines to the conf but still no luck but I was still able to access it no problem on my other ubuntu desktops.

Also all windows pc's here are on a domain and I think that is what is causing this issue. All I know is that it does work just not with windows. I try to connect by IP too.

Just let me know what info you need!!

Here is my conf:

[global]
   workgroup = hhc.hyattdir.net
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no
   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   local master = yes
   preferred master = yes
   ntlm auth = no
   lanman auth = no
   usershare allow guests = yes


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes


[Storage]
comment = Storage
path = /storage
browseable = yes
public = yes
writeable = yes
available = yes
guest ok = yes

---

### Post by houstonbofh on 2014-04-17
It is using your AD user to connect.   You need to connect as a local user, or tie samba to AD with Winbind and Kerbos.

---

### Post by monkey10120 on 2014-04-18
> **houstonbofh said:**
> It is using your AD user to connect.   You need to connect as a local user, or tie samba to AD with Winbind and Kerbos.

I tried connecting as a local admin and it still does not work but I then created a blank Win 7 image and did not connect it to the domain and it worked just fine. I was hoping AD wasnt going to conflict even if I had guest allowed to access it but I guess not. Would you know why it was not working when I logged in as a local admin though?

---

### Post by houstonbofh on 2014-04-18
Actually, convincing Windows to log in as a local user when you are on a domain is a real chalange. :)  You could just use Winbind and Kerbos to join your server to the domain...

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

---

### Post by monkey10120 on 2014-04-21
> **houstonbofh said:**
> Actually, convincing Windows to log in as a local user when you are on a domain is a real chalange. :)  You could just use Winbind and Kerbos to join your server to the domain...

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

Thanks for the guides!:P I will definitely look through those today and see what it takes to setup. I am only working on this in between tickets so I am really in no hurry. I will update this thread after I try out Winbind.

---

