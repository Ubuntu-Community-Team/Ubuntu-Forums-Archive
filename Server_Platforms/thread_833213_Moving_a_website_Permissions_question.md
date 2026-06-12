---
title: "Moving a website: Permissions question"
date: 2008-06-18
forum: Server Platforms
---

### Post by dvsjr on 2008-06-18
General question: 

I was hoping someone with experience moving a website from one server to another would be able to help me. I don't need specifics, just need some advice or instruction.
I have a PHP-Mysql site on my Ubuntu server that I want to move to another similar server. The site uses a CMS and has databases. I know the databases have to also be moved, my primary question is once I move the site, do I have to go through each and every directory and make sure the perms match the original site? Is there a tool or a way that developers move a site in this manner that I don't know about? What do others do? Is there a utility or software that would make this happen easier? I used FTP to download the site. Once moved, its reporting that it needs the databases (which I am exporting to bring over) but the functionality of the server and security is worrying me.
I know the CMS has permissions set the way it does to prevent people who access the site from the web from taking advantage of it security wise, and that why I'm posting. 

thank you for any suggestions. Pointers to web links, reading materials, etc welcome.

dvsjr

---

### Post by HalPomeranz on 2008-06-18
Pack up the site files using the tar command.  When you get them over to the remote side unpack them using the "-p" option to tar (which is the default if you run the tar command with root privs).  The "-p" option "preserves" all timestamps, ownerships, permissions, etc.

---

### Post by windependence on 2008-06-18
Another suggestion is to use scp to copy the entire site over. There are several other options such as dump and restore.

-Tim

---

### Post by Poleh on 2008-06-19
if u do it manually, most FTP clients allow easy, gui driven control over file/folder permissions so you can edit them ... it's a bit tedious tho.

---

### Post by dvsjr on 2008-06-20
I want to just thank the three of you for your extremely helpful suggestions. It was exactly what I needed and it really helped me out. I will investigate scp, and use tar to redownload the site. I also have a good FTP client, I'll use it to compare the permissions on the old site to the new. thanks again.

---

### Post by molotov00 on 2008-06-20
Expect error messages. Just don't freak out and be prepared to track down some config files for the various scripts you've installed. For instance, "absolute path" variables will need to be changed.

It will move fine but make sure you give yourself some time. Also check that the same apache modules are installed. I've moved from servers that support mod_rewrite to one that didn't -- that was messy because some installed scripts needed it.

---

