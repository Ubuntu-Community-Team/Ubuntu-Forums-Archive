---
title: "SAMBA: How to make a files undeletable and writable"
date: 2008-03-04
forum: Server Platforms
---

### Post by Mahiwaga on 2008-03-04
[LEFT]I have a SAMBA server running as a PDC for 10 workstations all in windows XP. My question is there a way that you could make the shared 
drive which is save on the home directory to be writable but undeletable? I already tried chattr +ah <filename> but it seems you could still delete the file. Please advised, Thank you.
[/LEFT]

---

### Post by Oldsoldier2003 on 2008-03-04
> **Mahiwaga said:**
> [LEFT]I have a SAMBA server running as a PDC for 10 workstations all in windows XP. My question is there a way that you could make the shared 
drive which is save on the home directory to be writable but undeletable? I already tried chattr +ah <filename> but it seems you could still delete the file. Please advised, Thank you.
[/LEFT]
writable means you can also delete it, read only means you can't write it. They're mutually exclusive.

---

### Post by Mahiwaga on 2008-03-04
Hi thanks for the reply. Before when I setup a SAMBA server running on FREE BSD i just used the chflags command on the directory or file and it works. User could write and edit the file but they can't delete. I hope it works also in Ubuntu. What do you think?

---

### Post by Oldsoldier2003 on 2008-03-04
> **Mahiwaga said:**
> Hi thanks for the reply. Before when I setup a SAMBA server running on FREE BSD i just used the chflags command on the directory or file and it works. User could write and edit the file but they can't delete. I hope it works also in Ubuntu. What do you think?
playing around with chattr on single files shows that it may be possible but the results arent exactly as expected. -a allows you to open in append mode only but you cant save. using the u flag doesnt do as you would expect either... there is no h flag in the version of chattr installed on Ubuntu 7.10 server

---

### Post by Oldsoldier2003 on 2008-03-04
After doing a little googling looks like chattr is not fully implemented on Ubuntu, well it probably isnt Completely implemented on any Linux distro. So for now I'm going to hazard a guess that using it isn't going to get you the desired effect.

---

### Post by Oldsoldier2003 on 2008-03-04
Here's a tidbit I found that may be relevant to your situation: [http://lists-archives.org/samba/26815-modify-only-not-deletable.html](http://lists-archives.org/samba/26815-modify-only-not-deletable.html)


Perhaps through the use of the sticky bit on the directory...

from 'man chmod':
"STICKY DIRECTORIES
       When the sticky bit is set on a directory, files in that directory may 
be unlinked or  renamed  only by root or their owner.  Without the sticky 
bit, anyone able to write to the directory can delete or rename files.  The 
sticky bit is commonly found on  directories,  such  as  /tmp,  that  are  
world-writable."

Look at using something like 
        create mask = 0664
        force directory mode = 01775
in your smb.conf file.

---

### Post by rickyjones on 2008-03-04
> **Oldsoldier2003 said:**
> writable means you can also delete it, read only means you can't write it. They're mutually exclusive.

I hope you are keeping that logic to SAMBA only. I say this because on my Windows server using NTFS permissions I can make a folder/file readable and editable but deny the user the ability to delete.

Does anyone know how to mimic this behavior correctly? I would also like to know how to make this happen.

Thanks,

-Richard

---

### Post by Mahiwaga on 2008-03-04
Thank you for the info. I'll try it later hopefully it works. :).

---

### Post by koenn on 2008-03-04
> **Mahiwaga said:**
> [LEFT]I have a SAMBA server running as a PDC for 10 workstations all in windows XP. My question is there a way that you could make the shared 
drive which is save on the home directory to be writable but undeletable? I already tried chattr +ah <filename> but it seems you could still delete the file. Please advised, Thank you.
[/LEFT]
I don't see the point ... If a file is writable this means a user can edit it, save changes to it. So a user can delete all contents and all that's left is an empty file. Having that file being 'undeletable' is of little use then, isn't it ?
Or am i missing something ?

---

### Post by Mahiwaga on 2008-03-05
I add the create mask = 0664 and force directory mode = 01775 in smb.conf:confused: Still doesn't work. Anyone has a better idea?

---

### Post by dmizer on 2008-03-05
i'm with koenn ... i think what you're trying to do is both impossible and pointless.

can't delete the file, but you can delete the contents ... which is the same as deleting the file.

perhaps we're not understanding, but in what situation would it be benefitial to be able to edit a file, but not delete it?

---

### Post by Mahiwaga on 2008-03-05
One of  the benefits of having a file that is writable but undeletable is for  users to avoid accidentally deleting  important files, which is save on the shared drive or home drive. I do have some experienced users call us that they accidentally delete a file/folder and wish to restore it. Yes we do have a back procedure but again it's much better to secure files like this. What do you think?

---

### Post by Oldsoldier2003 on 2008-03-05
> **Mahiwaga said:**
> One of  the benefits of having a file that is writable but undeletable is for  users to avoid accidentally deleting  important files, which is save on the shared drive or home drive. I do have some experienced users call us that they accidentally delete a file/folder and wish to restore it. Yes we do have a back procedure but again it's much better to secure files like this. What do you think?
I think installing CVS is a better idea :) But then you'd have to teach them how to use it ...

---

### Post by Mahiwaga on 2008-03-05
Installing  CVS is a good idea but if it's possible to make a file or folder undeletable on the shared drive/home drive will be much better. It's like windows 2K/2k3/XP works. It have a  inherit permission settings for each file or folder but I can't set it up in SAMBA running in Ubuntu or other Linux Distro. Free BSD works though using the chflags command.

---

### Post by dmizer on 2008-03-05
> **Mahiwaga said:**
> One of  the benefits of having a file that is writable but undeletable is for  users to avoid accidentally deleting  important files, which is save on the shared drive or home drive. I do have some experienced users call us that they accidentally delete a file/folder and wish to restore it. Yes we do have a back procedure but again it's much better to secure files like this. What do you think?

okay ... but the problem is, even though you can't delete the actual file, you can still edit the file.

let's use a microsoft word document as an example:
1) user opens the document in microsoft word.
2) user accidentally hits "select all"
3) user panics because everything suddenly highlighted and they don't know why.
4) user presses random keys in an effort to clear the highlight
5) everything in the file is overwritten with random keystrokes
6) desperate ... the user closes microsoft word (reboot fixes everything)
7) out of habit, the user clicks "save" when prompted with "do you want to save your changes?"

result: file exists in name only.  but all data is lost.  it's made no difference that the file cannot be deleted, because its critical content has been erased.

so no, it is not better to secure files like this.  if files are critical and should not be deleted, they should be read only, or have limited access.

---

### Post by Mahiwaga on 2008-03-05
I understand but the good thing about making a file/folder undeletable is much secure. There could be a good chance that some one from their department have the same access and might delete the file intentionally.
I just want to make the files undeletable as per users request. :)

---

### Post by koenn on 2008-03-05
> **Mahiwaga said:**
> I understand but the good thing about making a file/folder undeletable is much secure. There could be a good chance that some one from their department have the same access and might delete the file intentionally.
I just want to make the files undeletable as per users request. :)
If someone wants to delete the file intentionally and find out he can't, it's a small step to just erase the contents. A simple output redirect (like echo " " > undeletable_file ) and there's nothing there but whitespace.
Still, if it can be done, why not give it a try. 
And in stead of requests to restore backups you're going to get requests to remove obsolete file that none of the users can delete. 

Have fun  :-)

---

### Post by jonabyte on 2008-03-05
> **koenn said:**
> I don't see the point ... If a file is writable this means a user can edit it, save changes to it. So a user can delete all contents and all that's left is an empty file. Having that file being 'undeletable' is of little use then, isn't it ?
Or am i missing something ?

Sometimes you want to give write access to files, but prevent users from accidentally deleting the file.

---

### Post by dmizer on 2008-03-06
> **jonabyte said:**
> Sometimes you want to give write access to files, but prevent users from accidentally deleting the file.

protecting the file from deletion is not protecting the important part of the file.  the important part of the file is its data/content.  if you can edit the content, you can delete its content.  therefore, the important part of the file is gone, and it means nothing that the file cannot be deleted.

i'm still not understanding why this would be desirable, except for what Mahiwaga said earlier:
> **Mahiwaga said:**
> 
I just want to make the files undeletable [COLOR="Red"]as per users request[/COLOR]. :)

but this seems to be a case of a technically inept customer making unreasonable demands because of a lack of understanding.  the customer should be educated as to how pointless this request is, and offer an acceptable and actually functional alternative.

otherwise ... later, when one of the employees accidentally deletes the contents of the file, the customer will come back to you and scream at you for not making the file undeleteable.  at that point, no matter how many times you demonstrate to the customer that the file system is functioning exactly as requested, the customer will still see the lost data as a failure on your part.

CYA

---

### Post by Mahiwaga on 2008-03-06
Thanks for the feedback. What would be the best options you could 
suggest to avoid deletion and protect the data?

---

### Post by dmizer on 2008-03-06
my best suggestion would be to include several methods:

1) limit access to sensitve data.  by that i mean, limit the number of people who can write to it.
2) incremental backups.  linux can be configured for yearly, monthly, weekly, daily, hourly ... etc. backups via chron.
3) make sure your backups preserve change history. take a look at [subversion](http://subversion.tigris.org/). this way you have access both to the current file, as well as all changes made to it.  if a mistake is made, just pull an older good copy out of subversion and go on with life.
4) keep an access log to the sensitive directory so you can track who changed what, when.  this can be configured through samba.

---

### Post by jonabyte on 2008-03-06
dmizer:

BUT in some cases you do still want to prevent users from deleting it.

I support users that accidentally delete their files and I need to restore it from a backup.

When they change the data and don't like it, I don't restore it. Company policy, so they delete it.

This sometimes isn't a security issue, just a pain in the but.

---

### Post by Mahiwaga on 2008-03-06
Thanks for the suggestion! I appreciate it. :)

---

### Post by Oldsoldier2003 on 2008-03-06
> **jonabyte said:**
> dmizer:

BUT in some cases you do still want to prevent users from deleting it.

I support users that accidentally delete their files and I need to restore it from a backup.

When they change the data and don't like it, I don't restore it. Company policy, so they delete it.

This sometimes isn't a security issue, just a pain in the but.
SVN/CVS is really the best option, but the learning curve for users is what stops most people. Honestly you cant stop people from doing stupid things, hell you can't stop sysadmins from doing them either... 

Thats why I tend to agree with the folks that say preventing deletion while allowing editing is pretty pointless. RO for critical informational files, limit access to critical data to those that truly need it, backups backups backups for backups. SVN/CVS for places that have the userbase that can handle working with it.

 All pointless though unless the customer understands the security model and is willing to work within it... You have to get the customer to understand the reasoning behind the model and convert them. Because in the end they sign the checks and some will blame you even after the explanations of the flawed system saying, " damn it I don't pay you to listen to what I want, I pay you to give me what I NEED"

---

### Post by Oldsoldier2003 on 2008-03-06
But all quibbling over the reasoning aside, just for informational purposes, has anyone managed to get the OPs request working? I tried but couldn't find a combination that worked as the Op's request...

---

### Post by koenn on 2008-03-06
> **Oldsoldier2003 said:**
> But all quibbling over the reasoning aside, just for informational purposes, has anyone managed to get the OPs request working? I tried but couldn't find a combination that worked as the Op's request...

Actually, the reason this is so hard or (near) impossible to implement, is that this request consists of 2 contadicting requirements - something that the pretty straightforward (and arguably quite basic) Linux file modes can't represent (easily).

You might find a way to resolve this using file and directory modes, with some creative use of user, group and other, and posibly "sticky" the directory (man chmod, mode 't') or maybe set userID or set groupID (mode 's'). I'm not motivated enough to try and find a working combination here.

Alternatively, you could apt-get install acl, 
this installs posix-compliant Access Control Lists (ACL), not unlike the ones NTFS uses. They are more elaborate than the linux file modes, so maybe there is a combination of posix acls that does the trick. 
Added bonus : when used through samba from a Windows client, you can use the security tab in the file/directory properties as if you were talking to a Windows file server - that makes things easier when you're trying to mimic Windows behaviour.

---

