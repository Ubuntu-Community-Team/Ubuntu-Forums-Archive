---
title: "Samba and share permissions"
date: 2007-08-03
forum: Server Platforms
---

### Post by Anteaus on 2007-08-03
Only peripherally a Ubuntu question, as we use Windows desktops... :-/

Basically, replacing an ageing NT server with Samba. User-level security, one Samba PDC only. Share access is through Drive-mappings, which are set-up by a common logon script. Everything works fine except for a difference in behaviour in respect of shares to which the user has no rights. These cause the logon-script to 'choke.' For example, suppose we have a share: 


[management]
   comment = Confidential
   path = /home/samba/management
   guest ok = no
   browseable = yes
   writeable = yes
   create mask = 2770
   force group = users
   directory mask = 2770
   valid users=@management

The 'valid users' line restricts who has access to this share. But, if the site's logon-script contains the line:

net use x: \\servername\management

-then this will result in prompts telling the user to enter a username and password for the share -Which of course they have already done in logging-on, and repeating the credentials will not solve the problem.  Apart from being a nusiance this is bound to generate numerous techsupport-calls to 'have passwords fixed' 

On the NT server this problem didn't arise; a share to which the user had no rights could be mapped, and would appear empty. Which was acceptable behaviour, while causing the script to 'choke' on the mapping is not acceptable.  

It's possible I should be restricting the access to the share some other syntax instead of by 'valid users' - any suggestions here?

---

### Post by cdenley on 2007-08-03
```

net use x: \\servername\management /USER:%username%

```

---

### Post by Anteaus on 2007-08-03
> **cdenley said:**
> ```

net use x: \\servername\management /USER:%username%

```

Will try that when I get back to base, but I have feelings it wouldn't work, I suspect it would just result in a repeat demand for the password.

A partial workaround is:

echo .|net use....

This sends a CR to the net use command's stdin, which is ignored if the command is successful, but treated as a null password if the question pops. Not ideal as it still leaves a trail of error-messages, but at least the script doesn't hiccup.  

Still looking fora complete solution, though.

Thx for advice.

---

### Post by cdenley on 2007-08-03
You're right, it doesn't work. I was working on that same problem a while ago, and I thought I fixed it, but apparently not. Your workaround seems to work, though. 

Another fix I just figured out is to add %G to the netlogon share path. Then you can create seperate logon scripts for each group.

---

### Post by koenn on 2007-08-03
Assuming that the authentication dialogs ask for samba passwords, you could probably remove the valid users=@management from smb.conf so the net use statement doesn't hang, and use Unix permissions to block access to the directory for anyone not "management". 
It does make your file share security less consistent so maybe the echo. | workaround is preferable.

---

### Post by Anteaus on 2007-08-07
> **koenn said:**
> Unix permissions

I just don't want to even think about going there. 

Big advantage of share permissions is that they are 100% predictable in action, and their action is not dependent on who moved or copied the files into the share- from where- or with what software-  as it is wth filesystem permissions. 

Anyway, think the echo .| workaround should be satisfactory.

-Hit another snag in that even when already connected to one or more samba shares, the user still cannot browse the server in Network Places, or with 

NET VIEW \\servername 

This despite there being browseable shares. -Is there any global smb.conf setting that inhibits browsing?

---

### Post by Anteaus on 2007-08-17
Just as an upate, I'm going onsite to commission the server tomorrow, so tonight after the users had gone home I logged-in with VNC to do a final data migration from the old NT box. 

Only to have my data transfer "trip over its sholeaces" once more, when it hit a bunch of old files in the samba share that couldn't be deleted. Again, for some inexplicable reason these files had acquired unix permissions which restricted them to being written by only one user's ID. :mad:

Having tried every possible permutation I can think of, I'm just about at my wits' end with this - Is there ANY way - short of making all users root - which will make shared file-access work properly, such that any account which is a legitimate Samba user can read **and write** to all files in the share, and *preferably*  (but not essentially) also allow files to be put into the share from CD or memory stick at the server console, without users randomly being denied write-access to them? :confused:

Basically it's a very, very simple file-sharing requirement we have here, I could set it up in minutes on an M$ platform. I do need this to work **properly** though, and I'm starting to regret ever having gone the Linux route. If this snafu's on me it could lose the client, which will cost me a lot more than a Windows Server licence would have. 

Exasperated, Ian.

---

