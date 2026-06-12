---
title: "403 Forbidden - Nginx - Loss of access to the folder"
date: 2021-02-03
forum: Server Platforms
---

### Post by sed_faster on 2021-02-03
Hello everyone,

I have a machine on VirtualBox with Ubuntu Server 20.4.1 LTS to develop my codes php (I am leaning PHP).
To get run this script on my browser I decided create and configuration a virtual machine with nginx as server HTTP.

I shared a folder between my host (windows 10) and guest (Ubuntu Server). On the host the share folder it's located on this path "C:\Users\User\Downloads\share" and on the guest the share folder it's located on this path "/home/usteste/public/". I directed the nginx to the file public, so what when I accessed the IP VM on my browser I can see the files in the folder "Downloads\share", on my host system.

Before I configure the Virtual Box to connect the folder "share" (host) with the folder "public" (guest) I can run/execute normally file html or php on this folder "public" (guest). But after I configured the system to the connect this two folders I started receiving error page 403 Forbidden. This error is relative to the server understood the request but refuses to authorize it (source: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403)).

I consulted the permission and users (owners) referring to the folder "public" and I see this (please see the image attached).

[ATTACH=CONFIG]287898[/ATTACH]

I tried changed owner or permissions to this folder, but I can't change anything. What could I do to solve this problem?

Thanks

---

### Post by TheFu on 2021-02-04
You cannot expect Linux programs to run when they reside on Windows storage. It doesn't support the needed permissions and there is no way to modify permissions from the Guest OS. There are some other problems too.

You could have the code/programs inside the VM, on a native linux file system, and share that directory with Windows using Samba, however.

Remember, every popular OS in the world today, except 1, has case-sensitive file and directory names. This is very important when developing webapps that need to run on any Unix-like OS. They also have owner, group, ACLs, xattrs, and normal Unix permissions. nginx cares about permissions.

BTW, whenever coding, always use '/' as the directory separator, never '\' or '\\' or your code won't work.

If you want to show permissions, please use **ls -al**, not images.
You shouldn't need root on a properly setup web-app system. Use sudo.

---

