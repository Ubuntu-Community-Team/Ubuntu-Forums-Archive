---
title: "VSFTP local_mask problem"
date: 2008-10-01
forum: Server Platforms
---

### Post by orotrev on 2008-10-01
I have vsftp setup on a development server with access being granted to local users. The local users are all part of the same default login group. The problem I have is that I want the uploaded files to have the following permissions:
rwxrwxr--
Currently I have my set to local_umask=0002 but the uploaded files still have rwxr--r--. Am I messing something up here? Am I rusty with my umask skills? What umask should I set to get the permissions I want?

---

### Post by windependence on 2008-10-02
Looks like 774 to me.

-Tim

---

### Post by voodooxombie on 2008-12-02
umask work like this...

Read - 1
Write - 2 
Execute - 4
total - 7

Now if you want rwxrwxr--
then total for user its 7, group 7 and others 7
umask is reduced when the file is created so to get 
rwx for user 7-1-2-4 = 0
rwx for group 7-1-2-4 = 0
r-- for other 7-1 = 6;

this should give you what permission you want.
Hope this was helpful.

---

### Post by allengeer on 2009-09-12
Make sure the client you are uploading with is not setting the permissions of the file after the upload. This is the default option in Cyberduck for example.

---

