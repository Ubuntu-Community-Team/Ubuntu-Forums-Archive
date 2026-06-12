---
title: "Permissions on shared sftp folder"
date: 2019-10-28
forum: Security
---

### Post by thehappiestturtle on 2019-10-28
Hello, 

Ubuntu 18 Server

I am setting up an SFTP server using openssh and am running into a permissions issue.   I have two folders.  User 1 needs to be able to upload and delete from both folders, which user 2 only has access to upload and delete on one folder, and user 3 only has access to upload and delete on the other folder. 

The folder path is at /var/sftp/uploads/Folder1 and /var/sftp/uploads/Folder2.  Root currently chown /var/sftp.  Then chown /var/sftp/uploads to user1.  I then did chown /var/sftp/uploads/Folder1 for user1 and the same for user 2 but on folder 2. While User 1 can now see Folder 1 and Folder 2, User 1 cannot access these folders. I have tried chmod 755, but that does not give the desired results.

I would greatly appreciate any help!

Thank you,

---

### Post by SeijiSensei on 2019-10-28
Create a group with users 1 and 2 as members, and another group with users 1 and 3 as members.  Assign those groups ownership of the appropriate directories and grant them full privileges.

---

### Post by thehappiestturtle on 2019-10-28
Thank you.  Would I just grant each group chown of the folder, then chmod 777?

---

### Post by TheFu on 2019-10-28
In addition to SeijiSensei's technique, use the setgid to ensure any files/directories created retain the group.

---

### Post by thehappiestturtle on 2019-10-28
Awesome thank you both! I was able to test the new solution and all is working perfectly.

---

### Post by TheFu on 2019-10-28
If you used 777 permissions, you have no security.

---

### Post by SeijiSensei on 2019-10-28
group12 = user 1 and user 2
group13 = user 1 and user 3

```

cd /var/sftp/uploads
mkdir Folder1 Folder2
chown root:group12 Folder1 
chown root:group13 Folder2
chmod 770 Folder1 Folder2
chmod g+s Folder1 Folder2

```
Now both root and members of the appropriate group have full control over their respective folders. Everyone else has no access. The last line enables the setgid bit for both folders.

---

