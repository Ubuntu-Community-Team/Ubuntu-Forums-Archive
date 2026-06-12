---
title: "Easy Samba Permissions Issue"
date: 2014-09-14
forum: Server Platforms
---

### Post by Michael_Knight on 2014-09-14
I have a samba share setup on several windows 7 machines. I have 1 share in particular called Document_Control that I want to be viewable and readable by all users, but writable only by document control personnel.

The configuration file and permissions are below

   [Document_Control]
path = /samba/Document_Control
valid users = @doc_control, @allaccess
browsable = yes
guest ok = yes
read only = yes
writable = no
write list = @doc_control, @allaccess

drwxr-xr-x 2 nobody doc_control 4096 Sep 14 11:16 Document_Control
drwxr-xr-x 2 nobody nogroup     4096 Sep 13 09:25 Engineering
drwxrwx--- 2 nobody management  4096 Sep 13 09:23 Executive
drwxr-xr-x 2 nobody management  4096 Sep 12 22:18 Financial
drwxr-xr-x 2 nobody nogroup     4096 Sep 13 09:24 HFR_Submit
drwxr-xr-x 2 nobody nogroup     4096 Sep 13 09:24 IT
drwxr-xr-x 2 nobody management  4096 Sep 12 22:27 Legal
drwxr-xr-x 2 nobody management  4096 Sep 12 22:25 Marketing
drwxr-xr-x 2 nobody nogroup     4096 Sep 13 09:24 QA
drwxr-xr-x 2 nobody nogroup     4096 Sep 13 09:24 Resources


The result is that when I try to add a file or folder to Document_Control I get a message saying that I do not have permission to do this, however, additionally I am not prompted for a password or any credentials when opening Document_Control.

Any thoughts??

---

### Post by cariboo on 2014-09-14
Is /samba/Document_Control the full path to the directory, or is it a sub-directory of something else?

---

### Post by volkswagner on 2014-09-15
I'm no expert, but some things that come to mind.

```
drwxr-xr-x 2 nobody doc_control 4096 Sep 14 11:16 Document_Control
```

The above show's Directory "Document_Control" is not writeable via linux group permissions for @doc_control. 
Although you have owner 'nobody' writeable, I don't think an authenticated user will be covered by "nobody" (SAMBA will
compare against actual logged/authenticated username). The user nobody will only come into play if the user accessing
the share does not have an account on the server (user is guest).

You may want to start by leaning out permissions in SAMBA config (it's good practice to start simple then add more restrictions when necessary).

For example, when you specify the write list, I don't think you'll need/want the following two lines:
```
read only = yes
writable = no
```

Your Linux file permissions should not be more restrictive than SAMBA permissions.  For example, even if
you set Linux permissions rwx for the group @doc_control, a user that is a member of @allaccess still will not be able
to write unless the everyone bit was set to writeable ie: rwxrwxrwx

I also believe "valid users = @doc_control, @allaccess" and "guest ok = yes" are conflicting. If you want guest access, you don't want
to restrict users to certain groups.

---

