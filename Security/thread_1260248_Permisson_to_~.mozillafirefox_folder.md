---
title: "Permisson to ~/.mozilla/firefox/* folder"
date: 2009-09-07
forum: Security
---

### Post by satya61229 on 2009-09-07
Hi 
**Reason for Error:**
I want to see the password I have saved in Firefox.
I have visited Firefox Preferences -> Security.
Security tab was not showing anything. It was not giving any error either.
So, I went to command line and started firefox by giving this command:
#sudo firefox_file
and, then I can see the saved password.

When I closed FF then I got segmentation fault. I restarted FF as general user then I got bookmark related problem:
*[SIZE="3"][SIZE="2"]The bookmarks and history system will not be functional because one of Firefox's files is in use by another application. Some security software can cause this problem[/SIZE][/SIZE]*.

**Solution I have adopted:**
I fixed it after visiting to the folder and issued this command:
#sudo chmod o+w -Rv .

**PROBLEM I am facing**:
This has resulted in the Security tab visible even if I start FF as normal user. Is this right or a security problem?
I think when it was not visible as normal user then it was more secure!

What need to do to hide security tab content invisible/hidden as normal user.

Note: As I remember I have installed FF not as a deb installation. I just dumped the folder. I need to uninstall it earlier possibly due to similar reason earlier. 

Thanks!

---

### Post by lovinglinux on 2009-09-07
You shouldn't use Firefox with sudo. If you really need to do it, use gksudo instead.

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by aysiu on 2009-09-07
Close Firefox completely.

Then, issue the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

That will solve your problem.

Then read this to make sure it never happens again:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2009-09-07
Close Firefox completely.

Then, issue the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

That will solve your problem.

Then read this to make sure it never happens again:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by satya61229 on 2009-09-08
Thank you, Lovinglinux!

Is this solution for hiding the security tab content!

I will check what gksudo do.




> **lovinglinux said:**
> You shouldn't use Firefox with sudo. If you really need to do it, use gksudo instead.

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by satya61229 on 2009-09-08
right now, I am only concerned with Security tab(userid-password) visibility. I found it good feature in Linux. So, I want to enable it back.

Anyway I will try this as well. 
right now i am on winXP in office desktop.
I use Ubuntu at home. :)

> **aysiu said:**
> Close Firefox completely.

Then, issue the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

That will solve your problem.

Then read this to make sure it never happens again:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lovinglinux on 2009-09-08
> **satya61229 said:**
> Thank you, Lovinglinux!

Is this solution for hiding the security tab content!

I will check what gksudo do.

No, this is the solution to fix the problem with the bookmarks and other problems you didn't notice yet, that were created by starting Firefox with sudo. Nevertheless, it should also fix the issue about the security tab not showing. 

About the visibility of the security tab, there is no such thing as being visible as normal user or not. It was a problem that you probably could fix it with **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the same tutorial I have pointed to you.

The security tab should be visible to all users. Firefox works in a way that each user has it's own profile and they have total access to it's contents and configurations. If you start Firefox as sudo, then you are using Firefox as root, but still using your normal user profile. This will mess with the file permissions, assigning them to root. So when you start Firefox again as normal user, it can't save anything because your profile is now owned by root. That's why you started to experience problems with your bookmarks.

You should NEVER start Firefox with sudo, otherwise you will get all sorts of problems. If you need to use Firefox as root, then use gksudo instead, but I don't see any good reasons why you would need to do that. Fix the problem and then never start Firefox with root privileges again.

---

