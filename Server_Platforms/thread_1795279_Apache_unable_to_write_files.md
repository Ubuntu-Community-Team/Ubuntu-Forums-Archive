---
title: "Apache unable to write files"
date: 2011-07-02
forum: Server Platforms
---

### Post by ryanrobinson on 2011-07-02
Hi guys,

I am writing some PHP scripts that should be able to create text files on the server. However, I am getting permission denied.

I am guessing this is something to do with the permissions on the www folder in my Apache installation. When I installed Apache I used chown and chmod commands to change the permissions on the www folder to a group I created called www-users. I did this as I was configuring a Samba share for that folder.

After realising this I tried to add the apache group to the permissions list on that folder but I wasn't able to as there was no apache group on my server. I checked this by using the command:

sudo cat /etc/group | more

Does anyone have any ideas?

Thanks.

---

### Post by SeijiSensei on 2011-07-02
> **ryanrobinson said:**
> After realising this I tried to add the apache group to the permissions list on that folder but I wasn't able to as there was no apache group on my server.

If you run the command "ps aux | grep apache" you'll see that the Apache processes are owned by user "www-data" on Ubuntu.  Add that user to your group, and make sure the group has write privileges in the directory.  You should be fine.

---

### Post by Dangertux on 2011-07-02
The above post is correct with permissions : However, when doing this be VERY careful about validating and sanitizing user input in your script. If you give apache permission to write as opposed to just reading, you're giving up a security measure.

---

### Post by ryanrobinson on 2011-07-02
That group add fixed it thank you.

In terms of security I'm not too fussed. The server is a local one for developing sites before they go online.

---

### Post by donniezazen on 2011-07-02
Please remind me of how groups and user permission works.

All users (from same or different group) in a group have same permissions as the group. I have had problems with permission before. I have a home user with its group and Ajaxplorer uses www-data group and user. So i add www-data to my home user group. WIll it have same permissions as my group.

I use 750 as permission values. 7 for read, write and execute for user, 5 for read and write for group and 0 with no permission for other. Is this the safest and usable value?

Thanks.

---

### Post by SeijiSensei on 2011-07-02
> **Dangertux said:**
> The above post is correct with permissions : However, when doing this be VERY careful about validating and sanitizing user input in your script. If you give apache permission to write as opposed to just reading, you're giving up a security measure.

I rarely give the Apache user write permissions except in a few limited cases.  Sometimes I'll have a PHP script write a file that it uses for internal purposes.  I'd never simply copy user input directly to such a file though.  I also prefer to store most things in a PostgreSQL database rather than files.  I also write files to store website content that authorized users create via a management interface with an editor like [TinyMCE]("http://tinymce.moxiecode.com/").  Authorization in these cases requires a username and password.

I would recommend storing any created content outside the DocumentRoot, though.  I keep all my PHP code outside the DocRoot as well to protect it from prying eyes and meddling fingers.  Most of my index.php files contain a few directory definitions and a require() statement or two.

@soham_1207:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Dangertux on 2011-07-02
> **SeijiSensei said:**
> I rarely give the Apache user write permissions except in a few limited cases.  Sometimes I'll have a PHP script write a file that it uses for internal purposes.  I'd never simply copy user input directly to such a file though.  I also prefer to store most things in a PostgreSQL database rather than files.  I also write files to store website content that authorized users create via a management interface with an editor like [TinyMCE]("http://tinymce.moxiecode.com/").  Authorization in these cases requires a username and password.

I would recommend storing any created content outside the DocumentRoot, though.  I keep all my PHP code outside the DocRoot as well to protect it from prying eyes and meddling fingers.  Most of my index.php files contain a few directory definitions and a require() statement or two.

@soham_1207:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Most people do something along those lines, but you wouldn't believe what I've seen out there lol.

It's always good to remind individuals of potential risks. Some get very excited about making something work, so much so that they didn't even think if they SHOULD make it work ;-)

---

