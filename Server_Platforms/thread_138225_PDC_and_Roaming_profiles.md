---
title: "PDC and Roaming profiles"
date: 2006-03-01
forum: Server Platforms
---

### Post by 1oki on 2006-03-01
Hello all! Now I know this topic has been discussed to death, but I still cant find a solution to my problem... :(  I have setup a PDC using the howto on HOWTOForge. Works great... I would like there to be roaming profiles. Now there are, technicaly, roaming profiles but when these users logon to the domain under their profile and save somthing to the desktop its not there on another computer!!! For example, I created a text file named "test" under a domain user account. I saved this file to the desktop. I then logged off and logged on with another computer. That "test" file wasnt there! I checked in the PDC under the users actual profile (/home/samba/profile/user) and the information that was saved on the desktop is there!  It just wont show up on another computer... but when I log back on with the original computer its there, like its being saved localy... :-k Maybe I am not understanding fully the idea of roaming profile, but I thought this is a part of it.  Any suggestions? 
-Luke

p.s. this is the howto I used:

[http://www.howtoforge.com/book/print/917](http://www.howtoforge.com/book/print/917)

---

### Post by gpredrag on 2006-03-01
What do EventViewer logs say on those windows computers? Failure to load roaming profile usualy print some usefull hints in logs.
Roaming profile is saved both localy and copied on server.
When user logs on to different station local copy is synchronized with server copy.
There is similar problem explained in samba howto with XP SP1, where Windows machines check for ownership of roaming profiles, and fail to load them if owner doesn't match current user.

---

### Post by 1oki on 2006-03-01
[QUOTE=gpredrag]What do EventViewer logs say on those windows computers? Failure to load roaming profile usualy print some usefull hints in logs.
Roaming profile is saved both localy and copied on server.
When user logs on to different station local copy is synchronized with server copy.
There is similar problem explained in samba howto with XP SP1, where Windows machines check for ownership of roaming profiles, and fail to load them if owner doesn't match current user.[/QUOTE]

Thanks for the response gpredrag!
Event Viewer doesnt show anything. The roaming profiles are being loaded... If they werent, at logon there would be a message stating "your roaming profile can not be found. bla bla bla using a local profile instead". I know its being saved as well because when you log off if it wasnt being saved you would get a messages stating: "your profile could not be saved to the server. Bla bla bla". Its just not loading the profile exactly the way I left it... Event viewer doesnt show anything for today at all... only yesterday... I know this doesnt sound right.........................

---

### Post by gpredrag on 2006-03-02
Have you checked ownership/permissions on per user profile subfolders?
Enough permissions to save copy on server is not enough to load on workstation, user must be owner.
Workstations can be configured not to load roaiming profiles for some users, have you checked that also?

Roaming profiles may be found (no error messages at logon) but some parts of it may silently fail (like folder redirection), leaving only message in Application log in Event viewer.

---

### Post by LordMerlin on 2006-04-13
[quote=1oki]Thanks for the response gpredrag!
Event Viewer doesnt show anything. The roaming profiles are being loaded... If they werent, at logon there would be a message stating "your roaming profile can not be found. bla bla bla using a local profile instead". I know its being saved as well because when you log off if it wasnt being saved you would get a messages stating: "your profile could not be saved to the server. Bla bla bla". Its just not loading the profile exactly the way I left it... Event viewer doesnt show anything for today at all... only yesterday... I know this doesnt sound right.........................[/quote]

This is the exact problem I am experiencing. Any suggestions?

---

