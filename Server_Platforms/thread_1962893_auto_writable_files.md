---
title: "auto writable files"
date: 2012-04-21
forum: Server Platforms
---

### Post by PsyclonJohn on 2012-04-21
Hi, 

How can have LAMP auto write files correctly? Now, I'm not sure how this works, but on my LAMP server whenever I want to install a new open source script, it'll display a list of files that I need to change permissions on. 

When I used to have premium web hosting, when I uploaded an open source script, all the files would be set to the right permissions and I didn't have to change anything with permissions. 

How can I do that on LAMP?

Thanks, 

John

---

### Post by DJ_Max on 2012-04-21
This had nothing to do with your webhosting, it has to do with how the files were compressed.

Most of the time if the software is compressed correctly, and you extract it correctly, you retain the permissions.

Also, LAMP is just a term for a software setup, not a script itself.

---

### Post by PsyclonJohn on 2012-04-22
Did I say LAMP was a script? Sorry.

When I upload a zip file to the webhost and extract, everything is set to the right permissions. When I upload to localhost (my computer), I need to go through a list of hundreds of files to set permissions for.

I'm looking to find out how I can save time and not have to keep setting file permissions for every script I install.

-
John

---

### Post by elico on 2012-04-22
it's a zip file so permissions or not inherited from the zip.
you can use the "-R" option to do a recursive ownership and permission changes.
a 744 chmod will do also most of the tricks for webhosting.
if you dont want to change all the other files in this directory you can extract the files in a temp location change the ownership and permissions recursively and move the files to the /var/www folder.

---

### Post by DJ_Max on 2012-04-22
> **PsyclonJohn said:**
> Did I say LAMP was a script? Sorry.

When I upload a zip file to the webhost and extract, everything is set to the right permissions. When I upload to localhost (my computer), I need to go through a list of hundreds of files to set permissions for.

I'm looking to find out how I can save time and not have to keep setting file permissions for every script I install.

-
John

No you didnt directly say LAMP was a script but the inital sentence suggested it. I said that because I wanted to make sure you understood what it was because it makes things easier to explain. No insult to your intelligence, just wanted to verify we are on the same page. :-o

To many times have I tried to help people, only to find out they didnt understand what I was talking about.

---

