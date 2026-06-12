---
title: "Disappearing Email"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-09-21
I've been happily using the same mail directory for the last several years, moving from version to version as each new development version is ready for use. 

This morning, I started up my computer after I got home from work, and as usual the second thing I started up was Thunderbird, All my new messages where downloaded, but they disappeared as soon as I clicked on a folder. They didn't completely disappear, as they are still in the Local Folders directory, but it's a bit of a hassle being able to read them using mc, but I can't reply to anything.

Has anyone else run into something similar? 

BTW the Local Folders directory contains about 3.8GiB of data, but I've haven't heard of any data limits.

---

### Post by mcellius on 2012-09-21
I've not had that problem, but there are some things to check.  

Since there appear to be errors both in receiving and sending, it's possible your connection to your e-mail provider is acting up.  Does the problem also occur in Thunderbird in another version of Ubuntu (such as 12.04), or is it peculiar to Quantal?

Or is it possible your incoming (POP or IMAP) and outgoing (SMTP) servers are incorrect?  Either changed in Thunderbird, or else changed on your e-mail provider's end of things?

---

### Post by cariboo on 2012-09-21
> **mcellius said:**
> I've not had that problem, but there are some things to check.  

Since there appear to be errors both in receiving and sending, it's possible your connection to your e-mail provider is acting up.  Does the problem also occur in Thunderbird in another version of Ubuntu (such as 12.04), or is it peculiar to Quantal?

Or is it possible your incoming (POP or IMAP) and outgoing (SMTP) servers are incorrect?  Either changed in Thunderbird, or else changed on your e-mail provider's end of things?

I've been using the same ~/.thunderbird directory for several years without a problem. I back up most of the important directories in /home/cariboo daily, and when I do a fresh install, I restore ~/.thunderbird before starting Thunderbird for the first time, this method has worked well for me until today. Sending and receiving isn't the problem, as the emails are still stored in ~/.thunderbird/7ao8bx7y.default/Mail/Local Folders, they just don't show in Thunderbird.

---

### Post by effenberg0x0 on 2012-09-21
> **cariboo907 said:**
> I've been using the same ~/.thunderbird directory for several years without a problem. I back up most of the important directories in /home/cariboo daily, and when I do a fresh install, I restore ~/.thunderbird before starting Thunderbird for the first time, this method has worked well for me until today. Sending and receiving isn't the problem, as the emails are still stored in ~/.thunderbird/7ao8bx7y.default/Mail/Local Folders, they just don't show in Thunderbird.

I think I would check:

nano ~/.thunderbird/profiles.ini
- StartWithLastProfile must be set
- Profile0 must point to the right dir (7ao8bx7y.default)

Important: Is the profile in profile.ini pointing to "7ao8bx7y.default" or "7ao8bx7y.Default User" (with first letters on Caps and a space between "Default" and "User")? I believe this was inherited from Windows and it's not glib friendly (actually it is, but I wouldn't stick with it).

Also check Permissions, It's probably something like:
- chown $USER:$USER ~/.thunderbird -R
- chmod 775 ~/.thunderbird 
- chmod 700 ~/.thunderbird/7ao8bx7y.default (assuming this is the exact name of your default profile dir)
- Maybe chmod 664 for files within the profile dir, not sure what the default is, 664 will do.

Thunderbird rewrites settings on exit. You gotta do the stuff above with all instances of it closed. Then you can start with "thunderbird -ProfileManager" to load the Profile Manager dialog. (just to be sure it's seeing and loading the correct profile).

Regards,
Effenberg

---

### Post by cariboo on 2012-09-21
Profiles.ini looks like this:

```
cat profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=7ao8bx7y.default
```

When I restore the directory, I usually check ownership of all files and directories, and set permissions using:

```
chmod -R 700 ~/.thunderbird/7ao8bx7y.default 
```

The default directory name is one that was created on another installation and populated with the files and directories from the real xxxxxxxxx.default. 

I'm just a little paranoid about posting the real directory name here. :)

---

### Post by houseworkshy on 2012-09-21
This is almost certainly wrong but if you are backing up everything each time to a FAT32 drive, such as a flash stick or an external hard drive, then you may have hit FAT32's  file size of limit of 4gig and it can't copy.  You were at 3.8 already so it wouldn't take much more.  Probably irrelevant but as I had a related though differant issue due to not knowing about that file size limit thought it worth a mention.

---

### Post by cariboo on 2012-09-22
I back up to a 1TB hard drive using the XFS file system, so the size of the archive isn't a problem.

---

### Post by effenberg0x0 on 2012-09-22
- If the accounts show on Thunderbird (only the messages do not:
Go to Edit / Account Settings / TheAccount / Server Settings / Local Directory. Does it point to /home/you/.thunderbird/666tnotb/ImapMail/YourServerName?

- If not even the accounts show on Thunderbird: I still think it is not reading from the correct profile folder for some reason we're missing, but it might also be a problem with ProfileName.default/prefs.js. Maybe it's failing to parse it. What if you create a new profile with your correct account settings but then manually adjust Account Settings / TheAccount / Server Settings / Local Directory?

- Or you could just let it create a new something.default and then just recursively cp ImapMail/* from your backup to the same folder in the new profile dir.

Regards,
Effenberg

---

### Post by Bowmore on 2012-09-22
It might have to do with that TB earlier had that 4GB limit (fixed from version 12) and running an older mailbox structure.
> Thunderbird 12 added support for a "pluggable mail store", and removed the 4GB local folder size. Those two changes supposedly removed the 4GB limit for all folders. 
[http://kb.mozillazine.org/Limits_-_Thunderbird#Folders_and_messages](http://kb.mozillazine.org/Limits_-_Thunderbird#Folders_and_messages)

---

### Post by cariboo on 2012-09-22
> **effenberg0x0 said:**
> - If the accounts show on Thunderbird (only the messages do not:
Go to Edit / Account Settings / TheAccount / Server Settings / Local Directory. Does it point to /home/you/.thunderbird/666tnotb/ImapMail/YourServerName?

- If not even the accounts show on Thunderbird: I still think it is not reading from the correct profile folder for some reason we're missing, but it might also be a problem with ProfileName.default/prefs.js. Maybe it's failing to parse it. What if you create a new profile with your correct account settings but then manually adjust Account Settings / TheAccount / Server Settings / Local Directory?

- Or you could just let it create a new something.default and then just recursively cp ImapMail/* from your backup to the same folder in the new profile dir.

Regards,
Effenberg

I'm using a combination of pop and imap, email is stored in /home/cariboo/.thunderbird/7ao8bx7y.default/Mail/Local Folders.

I should explain my setup a bit, I have 3 email addresses from my isp, 2 gmail addresses, I was using Google to host email for my domain, that has since been discontinued and an alias for my ubuntu.com email address. The 3 addresses from my isp are accesses via pop3, and all email is sent via their smtp server, Three Google hosted addresses were accessed via imap.

It looks like Bowmore, may have the answer to the problem, with his link to mozilla.

---

