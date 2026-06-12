---
title: "SFTP Read Access Only and Not Delete"
date: 2009-02-17
forum: Security
---

### Post by stoi2m1 on 2009-02-17
I am looking for some help and some clarification of securing some directories I want to allow SFTP access too.

I'm using SSH for SFTP (I think I said that right) with MySecureShell to lock users into their home directories. I want to share folders in the users home directory that are not owned by the user and give them read access only.

I have made a folder in user1 home and made it owned by user2 and group user2 and I have set the permissions to rwxr-xr--.

I am using filezilla to access the SFTP and and when I try to edit the folder permission I am told permission denied. Works like I want it to. But if I try to delete the folder it gets deleted. So it seems the rmdir command still executes on the folder which was not owned by user1. How is this possible and how do I fix this.

Basically I want to give users the right to download some content but not delete or change anything and at the same time allow them to do anything they want with the directories they own.

Thank You,
Jesse

---

### Post by HermanAB on 2009-02-17
Howdy,

I believe you need to set the sticky bit on the directories in question.

Cheers,

Herman

---

### Post by stoi2m1 on 2009-02-17
I have set the sticky on the folder but I am still able to delete the folder even when the owner and group are root and the permissions are rwxr-xr--.

-Jesse

---

### Post by HermanAB on 2009-02-17
Ten you need to look Access Control Lists:
[http://linuxcommando.blogspot.com/2007/12/basic-linux-permission-model-lets-you.html](http://linuxcommando.blogspot.com/2007/12/basic-linux-permission-model-lets-you.html)

Cheers,

Herman

---

