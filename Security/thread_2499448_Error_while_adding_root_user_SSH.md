---
title: "Error while adding root user SSH"
date: 2024-07-27
forum: Security
---

### Post by theyikes on 2024-07-27
Hi guys!
OK I have a question (well obviously) any way here it goes. I'm trying to add a root user account through SSH using adduser.

which i've done numerous times in the past but today i keep running into trouble.

Here's what i get when i try to ssh [email]user@192.168.x.xxx[/email]

[FONT=monospace][COLOR=#000000]proot@yikes-a320ms2h:/home/yikes# adduser freak [/COLOR]
info: Adding user `freak' ... 
info: Selecting UID/GID from range 1000 to 59999 ... 
info: Adding new group `freak' (1014) ... 
info: Adding new user `freak' (1014) with group `freak (1014)' ... 
info: Creating home directory `/home/freak' ... 
info: Copying files from `/etc/skel' ... 
New password:  
Retype new password:  
passwd: password updated successfully 
chfn: PAM: Authentication failure 
fatal: `/bin/chfn freak' returned error code 1. Exiting. 
proot@yikes-a320ms2h:/home/yikes#  

is there a fix to this or am i screwed??

I tried adduser from the terminal as root but i'm getting the same message.

For what it's worth I'm running [/FONT][FONT=monospace][COLOR=#000000]Kubuntu VERSION="24.04 LTS (Noble Numbat)"[/COLOR]

[/FONT]
[FONT=monospace] 

[/FONT]

---

### Post by theyikes on 2024-07-27
Ok i think i found a workaround. I used the KDE User management and i added the account, the i opened a terminal as root and changed the password. I'm sure there has to be an easier way to do but for now this works. Should i mark this as solved or will i wait to see what kind of constructive advice i get?

---

### Post by theyikes on 2024-07-27
change of plan it didn't work I can't add ftp users

---

### Post by currentshaft on 2024-07-27
What happens if you run "/bin/chfn freak" as root

---

### Post by TheFu on 2024-07-27
> **theyikes said:**
> I'm trying to add a root user account through SSH using adduser.

I don't understand this statement.  Can you saying differently so it will be clearer?

In general, "root" is prevented from remote access to Ubuntu Systems.  I believe forum policy dislikes people helping others to enable it.  Basically, if you have to ask how, then ... 

So, if we completely remove the ssh aspect (though you can ssh into any system you like), then I'm left with 
> **theyikes said:**
> I'm trying to add a root user account using adduser.

Well, there is already a root user on every Linux system already, so that shouldn't be allowed.  I didn't test it.  Duplicate usernames aren't allowed.  

**adduser** and **useradd** - are the normal ways to create new users on Linux using a CLI.  I always have to look up the manpage for which command "handles" everything and which one only does exactly what the options request.  Looks like adduser is the "friendlier" tool.

So, I'm back to trying to understand what, exactly you want the results to be?  Also, is there any LDAP or other external user management involved?

I really hope you aren't trying to add a "root user account", but just another user.  If you want that other user to have some sudo capabilities or full sudo capabilities, that's a little different question.

---

