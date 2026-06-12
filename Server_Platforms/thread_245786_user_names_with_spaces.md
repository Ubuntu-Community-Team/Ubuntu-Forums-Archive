---
title: "user names with spaces?"
date: 2006-08-28
forum: Server Platforms
---

### Post by Pitt Stains on 2006-08-28
Hello,

I am trying to set up a Windows XP user to access to the Ubuntu file server I pretend to administer, using Samba.

In order to save the user the trouble of having to log in each time she needs to access the server, I want to make her Linux and Samba usernames the same as her Windows username.

However, her Windows username has a space in it, and I'm not sure how to represent the equivalent in her Linux and Samba usernames.

Anyone?  Thanks!
-Frank

---

### Post by x64Jimbo on 2006-08-28
Save yourself the hassle. Just change her username in windows.

---

### Post by Pitt Stains on 2006-08-28
Thanks for your response.  I'm glad you suggested that.  I previously set up other Windows users that way--I changed their Windows usernames to match what I had already set up in Samba--and for some reason they have to log in each time they want to access the file server.  For that reason I've been wary of renaming this new user.

Any idea why they might not be automatically logged in?

---

### Post by x64Jimbo on 2006-08-28
I know that windows usernames have 2 incarnations - the regular username and the full name of the user... is there any chance that you might have changed the full name rather than the actual username? Also, you might want to have a look at your samba configuration file and make sure that you've followed all of the instructions from this tutorial: [http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

---

### Post by Pitt Stains on 2006-08-28
Checking out the tutorial now...

I looked at the Windows user accounts options, and I don't see anything about any full name, just the name that appears on the welcome screen and start menu.  So I suppose it is possible I thought I was changing the username when I wasn't.

How would you recommend I change the username?

---

### Post by Pitt Stains on 2006-08-28
Decided to Google changing a Windows XP username.  I think this may answer the question:

[http://www.thomas.edu/it/faq/WinXP_username.htm](http://www.thomas.edu/it/faq/WinXP_username.htm).

---

### Post by Pitt Stains on 2006-12-19
I'm not sure how I came across this, but here's the correct way to make Samba understand a Windows username with spaces.

In the [global] section of your smb.conf file, add this line:
```

username map = /etc/samba/smbusers

```

Then create a file called smbusers, put it in the appropriate directory, and write this to it:
```

#Unix_name = "Windows name with spaces"
pittstains = "Pitt Stains"

```

The line that begins with a # is just a comment, if you're new to all this, and obviously you should use your usernames and not mine!

---

### Post by elst on 2006-12-19
It's worth remembering that Linux systems often provide Web hosting and email facilities, so account names really ought to be Internet-friendly (letters, number and hyphens only).

The case-sensitivity thing can bite too, if you don't consistently use lower-case letters in account names.

---

