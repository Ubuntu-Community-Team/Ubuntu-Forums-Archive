---
title: "Where is the smb password file?"
date: 2009-05-23
forum: Server Platforms
---

### Post by RobertL on 2009-05-23
I'm pulling my hair out trying to get samba working for the first time. I thought it would help if I could see what's in the smb password file but I don't know what it's called or where it is. This is on jaunty. Could someone please point me to it?

"/usr/bin/smbpasswd -a xxxx" doesn't complain so the password file must exist somewhere. I did a 'find' on various plausible sounding filenames that I could think of but didn't find it. It seems that the smbpasswd program ought to have an option to display the contents of the file as plain text (when run as root) but apparently it doesn't.

<flame> I think samba is too complicated to exist in its present form. It needs to be broken down into a few separate programs, or else abandon a lot of the legacy stuff it's supporting.
</flame>

---

### Post by capscrew on 2009-05-23
> **RobertL said:**
> I'm pulling my hair out trying to get samba working for the first time. I thought it would help if I could see what's in the smb password file but I don't know what it's called or where it is. This is on jaunty. Could someone please point me to it?

The file is at /var/lib/samba.  It is a binary file and thus is not human readable (no text).  The only data in it is the samba user name and password.  This name should also be a user in the local hosts passwd file.  This means that you have to create the user on the host and then add that user to the smbpasswd file. 
> 

"/usr/bin/smbpasswd -a xxxx" doesn't complain so the password file must exist somewhere. I did a 'find' on various plausible sounding filenames that I could think of but didn't find it. It seems that the smbpasswd program ought to have an option to display the contents of the file as plain text (when run as root) but apparently it doesn't.

I don't agree.  There is no reason for that information to be readable.> 

<flame> I think samba is too complicated to exist in its present form. It needs to be broken down into a few separate programs, or else abandon a lot of the legacy stuff it's supporting.
</flame>

<retort>Samba is what it is.  Complicated is a relative term.  I configure it with only one file.  Got it right the first time.  I did however spend the time reading the documentation at samba.org.  

What "*separate programs*" are you referring to.  Samba consists of  2 daemons (smbd and nmbd) that provide smb file sharing services. There are other utilities but they can be considered separate and require no configuration.  

What do you mean by "*legacy stuff it's supporting*"?  Samba supports the SMB protocol.  The other utilities or not needed for the basic Samba server to operate.  No winbind, no nsswitch file, no netbios.  If you have all the standard network connectivity building blocks in place the system works.  

Are you referring to the ability for AD integration?  That's not legacy at all. </retort>

---

### Post by albinootje on 2009-05-23
> **RobertL said:**
> I'm pulling my hair out trying to get samba working for the first time. 
What are you trying to do ?

*) Share files ?
*) Setting up a PDC ? 
*) or .. ?

This might help : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
I find smbclient very useful to debug possible Samba problems.

Apart from that there's samba management GUIs like Swat and Webmin's samba module.

---

### Post by RobertL on 2009-05-23
> **capscrew said:**
> The file is at /var/lib/samba.  It is a binary file and thus is not human readable (no text).  The only data in it is the samba user name and password.  This name should also be a user in the local hosts passwd file.  This means that you have to create the user on the host and then add that user to the smbpasswd file. 
I don't agree.  There is no reason for that information to be readable.

<retort>Samba is what it is.  Complicated is a relative term.  I configure it with only one file.  Got it right the first time.  I did however spend the time reading the documentation at samba.org.  

What "*separate programs*" are you referring to.  Samba consists of  2 daemons (smbd and nmbd) that provide smb file sharing services. There are other utilities but they can be considered separate and require no configuration.  

What do you mean by "*legacy stuff it's supporting*"?  Samba supports the SMB protocol.  The other utilities or not needed for the basic Samba server to operate.  No winbind, no nsswitch file, no netbios.  If you have all the standard network connectivity building blocks in place the system works.  

Are you referring to the ability for AD integration?  That's not legacy at all. </retort>

If I understood samba better I could argue with you better, or maybe I would see that you're right. But I think most people would consider any program with almost 400 config parameters, many of which interact with each other, to be pretty complicated. I have spent many hours reading documentation and how-tos, some of which are terribly written. But I guess I need to read some more because it isn't working even though I think I have everything in place.

As to reading the smbpasswd file, I'd like to read it so I can see what usernames were added. For example, were they spelled right? Unless there's a reason to keep it concealed that I haven't learned about it seems to me just common sense to be able to look at it. Maybe there's a security reason?

---

### Post by RobertL on 2009-05-24
> **albinootje said:**
> What are you trying to do ?

*) Share files ?
*) Setting up a PDC ? 
*) or .. ?

This might help : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
I find smbclient very useful to debug possible Samba problems.

Apart from that there's samba management GUIs like Swat and Webmin's samba module.

Many thanks for this reference. I read about a dozen other write-ups on configuring samba but couldn't get file sharing to work. But about 2 minutes after reading this it was working!

---

