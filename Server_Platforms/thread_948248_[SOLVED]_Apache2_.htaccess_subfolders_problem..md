---
title: "[SOLVED] Apache2 .htaccess subfolders problem."
date: 2008-10-15
forum: Server Platforms
---

### Post by Phoenixzeus on 2008-10-15
Hello,
My current situation is the following:
I have a server running apache2. Under the root folder, there is a subfolder named A, and under the subfolder named A there is another subfolder named B.

Example:
Root Folder >
            >    Folder A >     
                          >  Folder B >

I have a .htaccess file under the root folder, which is blocks access to "Folder A", however I would like to add a .htaccess file inside "Folder B" to allow access to "Folder B" while still blocking "Folder A"

I am not sure what code would go inside "Folder B"

My code for the .htaccess file inside the Root Folder is the following:

Options -Indexes
AllowOverride All
Order Allow,Deny
Allow from 127.0.0.1
Options None

Please let me know if you need me to clarify. I have looked around quite a few websites but nothing explains how to make a .htaccess file in a subfolder override the .htaccess file in the parent folder.

Thanks for any help,
Phoenixzeus

---

### Post by dgoosens on 2008-10-15
hi,

I think the easiest way is to block the access to folder A by placing the .htaccess file in it and removing the ones in your root and B folder...

---

### Post by Phoenixzeus on 2008-10-16
Thanks dgoosens for the post,
Only problem is, if I put a .htaccess file inside folder A to block access to it, the permissions follow down through Folder B and block access to folder B.  :(

Is there an apache2 setting that you know of that will prevent this?

Thanks again,
Phoenixzeus

---

### Post by dgoosens on 2008-10-16
it is impossible that the .htaccess file in the A folder has any influence on the B folder...

I think you might have some issues with your folder permissions...
You might want to check if folder B is accessible... you should check it's permissions

---

### Post by Phoenixzeus on 2008-10-16
I think I might not have explained my folder layout well enough :)
Under the root folder there is a folder called folder A, and then under folder A there is a folder called folder B, So B is under A. And from what I have seen, .htaccess files follow down through subfolders, and this is why folder B is inheriting its .htaccess file from its parent folder (Folder A).

I have made for the purposes of this task, all folders and files 777 permissions.

Thanks again,
Phoenixzeus

---

### Post by lykwydchykyn on 2008-10-16
Can I ask why folder B needs to be inside folder A?
How about just symlinking B into the root?

---

### Post by dgoosens on 2008-10-17
> **lykwydchykyn said:**
> Can I ask why folder B needs to be inside folder A?
How about just symlinking B into the root?

my point... exactly

---

### Post by Phoenixzeus on 2008-10-20
I haden't tried symlinking due to the fact that it made the page a little messier than I thought it had to be, however as .htaccess files don't seem to want to overwrite each other's read permissions it will have to do.

Thanks a lot for the responces
Phoenixzeus

---

