---
title: "Cloned guests still seem to be using the parent /home"
date: 2011-01-24
forum: Virtualisation
---

### Post by thane1 on 2011-01-24
VirtualBox 4.0 with 4.0.2 guest additions on guests and cloned guests.  There seems to be some carry over from the original guest account.  On an ubuntu amd-64 clone (eg: named ubuntu3) at the top right of the Top Panel next to the ubuntu on/off button, the first (eg: ubuntu1) account name is displayed and in the drop down box, if I click on About Me it shows the username as ubuntu1.  
     If I click on Places-Home Folder, the resulting screen shows ubuntu1 in no less than three places.  I'm using samba file sharing with each guest account listed in the /etc/samba/smb.conf file under valid users.  But if I access the shared partition (mounted on the host), I'm given the suggested ubuntu1 default username at the samba network logon screen.  My .vdi filename for each clone reflects the name for each clone account.  
     Is this normal behaviour for displaying cloned account information?  I am able to access my share successfully on the host via samba.  I suspect though, that I may be piggy backing somehow on my initial guest account, due to having some setting improperly entered in the clone.  Many thanks.

---

### Post by CharlesA on 2011-01-24
What do you mean "cloned guests" ?

If they are exact duplicates, then of course, they'll have the same user and whatnot.

---

### Post by thane1 on 2011-01-24
I made 4 clones of the original with new virtual hard drives for each using the vboxmanage clonehd command.  Since they all have separate .vdi files, etc and are separate guest accounts in the left window of my Oracle VM VirtualBox Manager screen, I assumed they would have individual user names for each account the same as the name of the account each had been given.  My username on the first account is afterall the same as the account name.    Seemed reasonable to a relative noob.  It seems unnecessarily confusing to be able to make separate accounts and be forced to use the same username, when each clone has a unique name, .vdi, etc.  Maybe I just missed this in the documentation or maybe its just not explained adequately for someone, who's new to this stuff.  If the usernames are all the same, is there a way to make each unique?  Thanks.

---

### Post by CharlesA on 2011-01-24
You cloned each drive, which made an exact copy of the drive, OS and all. You would have to change the username on each install from the "users and groups" applet, under administration.

---

### Post by thane1 on 2011-01-24
Many thanks Charles.  I'll plug away at that.  Cheers.

---

### Post by CharlesA on 2011-01-24
by "change" I meant, create a new user, if what's what you want to do.

---

### Post by thane1 on 2011-01-24
Yes -- just got it.  Thank you so much.  Makes perfect sense, once its explained.  I had added new users for samba, but had completely not thought of the os part of users and groups.  I'll fix up the rest of them shortly.  Cheers.

---

