---
title: "upload but not delete permission"
date: 2019-12-12
forum: Security
---

### Post by marchello_lippi2 on 2019-12-12
Hi all, 
Our admin is on sick leave and I'm trying to help.
Got peculiar task to give upload but not delete permission (it's vsftpd if matters, but permission is for regular linux user). Obviously, person who assigned this task is not any linux user. 

I understand how to provide write permission:
```
setfacl -R -m u:user1:rwx /sftp/folder1
```
But what in the world does it mean "not delete"?

Please advise.

---

### Post by TheFu on 2019-12-12
Really, using ACLs shouldn't be needed for 99.99999% of all permissions.  The normal chmod method is sufficient with a little pre-thought.  I've been a Unix admin 25 yrs and used ACLs 2 times in all those years.

There aren't separate permissions for create and delete in Unix.  For that, you need Novell Netware.  

Usually the way this is addressed is by allowing new files to be uploaded to a directory, but not allowing any users read access to that same directory.  After the upload finishes, using something like **inotify**, the new file would be processed to ensure it isn't a virus or malware, then moved to a different directory where no users can remove it, but can read the *safe* file, if that is desired.  I'd move the original upload file somewhere else completely so it could be archived and tagged with the upload userid should malware or a virus be traced back to that user later. It is important to have traceability.
That's how I would handle this problem.

BTW, I'm curious. Is this really plain FTP or is it sftp or FTPS?  They are very different underneath.  Plain FTP should have died around 2002.  vsftpd supports plain FTP and FTPS, which is different from sftp.  Eh - no matter. Just curious.

---

### Post by marchello_lippi2 on 2019-12-13
> **TheFu said:**
> [COLOR=#000000]moved to a different directory where no users can remove it, but can read[/COLOR]
That's exactly what I had in my mind, but needed to confirm that linux doesn't provide "write but not delete privileges".
Thanks.

---

### Post by marchello_lippi2 on 2019-12-13
> **TheFu said:**
> [COLOR=#000000]is it sftp[/COLOR]
It's sftp. I created .pem file and mentioned it in vsftpd configuration. Can't tell deeper, I'm not pro here, just helping our admin.

---

### Post by SeijiSensei on 2019-12-13
You can protect a file saved to a shared directory from being deleted by other users with rights to the shared directory using something called the "sticky" bit. I don't know of any way to allow a user to upload but not delete a file he or she creates. 

If the files were transferred using Samba, you can use the "[create mode]("https://www.linuxquestions.org/questions/linux-software-2/samba-share-with-write-but-not-delete-223222/#post1141852")" directive to allow uploads without deletes to a Samba share.

---

### Post by marchello_lippi2 on 2019-12-13
> **SeijiSensei said:**
> You can protect a file saved to a shared directory from being deleted by other users with rights to the shared directory using something called the "sticky" bit. I don't know of any way to allow a user to upload but not delete a file he or she creates. 

If the files were transferred using Samba, you can use the "[create mode]("https://www.linuxquestions.org/questions/linux-software-2/samba-share-with-write-but-not-delete-223222/#post1141852")" directive to allow uploads without deletes to a Samba share.
Thanks, I explained them about operating system limitation and they clarified the task, so that "upload but not delete" is not needed anymore. They are ok with just read/write for one group of users and read-only for the other one. Grin.

---

