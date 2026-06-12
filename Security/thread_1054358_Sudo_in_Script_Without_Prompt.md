---
title: "Sudo in Script Without Prompt"
date: 2009-01-29
forum: Security
---

### Post by Chuchaqui on 2009-01-29
Hello,

I have a script that I would like to run on several machines that requires root privilages. The passwords for all the machines are the same.

I was wondering if there was a way of passing the sudo password to sudo su or something of the sort. Like an argument to the command. Similar to:

```
$sudo su PASSWORD
```

that way I do not have to re-enter the password every time.

Thanks.

---

### Post by estyles on 2009-01-29
Might try "man sudo" to get more info.

I believe that the following should get you what you want:
```
sudo -S su < PASSWORD
```

---

### Post by kdorf on 2009-01-29
The best way I can think of would be to add all users you want to run this script to /etc/sudoers and allow them to run just that script without a password using sudo. You can see the sudoers manual for more information.

---

### Post by lensman3 on 2009-01-31
Once upon a time on a Sun 3 box one of the users used to be "sync".  It was on a line in /etc/passwd that had no password in the /etc/passwd file.  (This was before the shadow password file was implemented.  In the place of the shell part of the passwd file was "/bin/sync".  This allowed ANY user to execute the "sync" command on the disks without logging in to the system and from a login screen.

Then to run the script do "su <script name>".   Remember that su with no user name following defaults to root.  So if your script is called "xxx", then "su xxx" will try to become user "xxx".  Since there is no password and the "shell" is you script then it should run that script that you want. 

My suggestion is to create a special user, with no password, and link the shell part of the password file to your script.  Then when you login it would execute that script and then logout.

As you would expect there are probably lots of security "holes".  The script would have to be well tested before you released it.

Good luck.

---

