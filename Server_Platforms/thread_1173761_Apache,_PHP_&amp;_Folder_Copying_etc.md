---
title: "Apache, PHP &amp; Folder Copying etc"
date: 2009-05-30
forum: Server Platforms
---

### Post by lynxdev on 2009-05-30
Hi,

Been running Ubuntu for just over a month now and very happy with it.

I've run into a bit of an issue however.
What I would like to do is be able to create sites much like the "Virtumin" (I think that's the right name) does. But having issues copying folders and files.
I have a template site which I would like to be able to copy as well as copy a Virtual Host file into the appropriate folder in my Apache config.

I can't do it using chmod() in PHP as it will leave a massive security hole in my server.
I tried using exec/system/passthru to copy a folder using the "sudo" command at the beginning which won't work because I need to enter a password to do that.

Is there any way of changing the user profile that Apache uses while looking at scripts in a certain folder?
For example, if I am using scripts in [http://www.site.com/admin/restricted/](http://www.site.com/admin/restricted/) can I force Apache to use a different user to the default one (I think is wwwdata, or something similar)

I know this kind of thing can be done in IIS as the company I work for does it, it would be really handy if I can set a similar thing up in my Ubuntu server.

If I haven't explained something properly, please ask but would really appreciate the help.
Thanks in advance.

P.S. There is a duplicate thread in "General Help", can some one close/delete please as it was getting lost in there.

---

### Post by Flare183 on 2009-05-30
Just using the WebDAV system to login.

---

