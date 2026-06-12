---
title: "Can't access my Server from Windows (samba)"
date: 2012-05-24
forum: Security
---

### Post by DRouleau on 2012-05-24
This is part of a Win 2k3 Domain with AD.  What I'm trying to do is set up the file share so that users can access it (kinda the point of a file share :) )  However when I try to access it from Windows Explorer it prompts me for a username and password and everything I try doesn't work.  This is the first time I've set up a samba share in AD so I'm sure I'm missing something and I know from the past in just a work group it was a pain in the butt to get working.  Any help will be greatly appreciated, Thanks!!

This server is part of the Windows Domain as that part seems to have gone ok, just can't get the users to be recognized.

---

### Post by DRouleau on 2012-05-24
Quick update if is use 
security = share 
I get \\Server is not accessible. You might not have permission...

security = ads
prompts me for the user name and password and nothing works

---

### Post by DRouleau on 2012-05-24
Ok, changed it to user and I can now get into the folder... I can't add or edit anything in it, but a "regular" user can which is pretty interesting.  Any ideas?

---

### Post by darkod on 2012-05-24
What exactly are you trying to do?

Shares open to all, or sort of each user has his folder and can't use others?

---

### Post by DRouleau on 2012-05-24
Well it would be nice to eventually have it so Group A can have one share, Group b another and so on.  Though right now I'd be happy so that any user can access the file share and create folders, open files and the like.

---

### Post by darkod on 2012-05-24
Having open for all share, is very easy. I have a home network storage so haven't gotten into different access security, I want it open to all.

What I have for example:
```

[global]
        workgroup = WORKGROUP
        netbios name = machine_name
        security = share
        hosts allow = 192.168.1.0/24

[share_name]
        comment = Share comment
        path = /path/folder
        guest ok = yes
        read only = no

```In the global section you can set the workgroup name, the machine name how it will be seen on the network, the range of hosts allowed to access it if you want.
Then create as many shares as you want.

Also make sure on the server that /path/folder has permissions for all to write, something like:
sudo chmod a+rw /path/folder

Otherwise the linux permissions can block you, not the samba permissions.

The above works for me just fine. After that you can try to tune it according to your security needs.

EDIT PS: Sorry, I forgot to specify, that is the content of the /etc/samba/smb.conf file but I guess you already know that. :)

---

### Post by DRouleau on 2012-05-24
I actually did that about 1 min before you posted :-) and it works though for some reason I have to refresh to see changes from a windows PC.  For example if I create a new folder I can't see it until I refresh the window (never had that happen before) and it's only happening on my XP PC not from a Terminal Server.  Guess I can work on that later.
I'll try and figure out the AD stuff later, I just need to get the web site back up and running before the employees start to complain too much.

---

### Post by anonymouschief on 2012-05-24
Take a look at Centrify Express: [COLOR="Blue"][http://www.centrify.com/express/free-active-directory-tools-for-linux-mac.asp]("http://www.centrify.com/express/free-active-directory-tools-for-linux-mac.asp")[/COLOR]

*Centrify Express is a comprehensive suite of free Active Directory-based integration solutions for authentication, single sign-on, remote access, file-sharing, monitoring and cloud security for cross-platform systems. It is the quickest and most proven solution for integrating UNIX, Linux and Mac systems with Windows, and delivers more functionality and more to upgrade to when compared to other free offerings.*

I have never used Centrify, but it took a lot of time and effort to evnetually discover it, when I did. I have no intentions of having my server join a domain, but if I did, Centrify would be my first choice.

---

