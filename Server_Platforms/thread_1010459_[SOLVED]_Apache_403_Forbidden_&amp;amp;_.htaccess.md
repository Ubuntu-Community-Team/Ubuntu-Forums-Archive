---
title: "[SOLVED] Apache 403: Forbidden &amp;amp; .htaccess"
date: 2008-12-13
forum: Server Platforms
---

### Post by allspiritseve on 2008-12-13
I have been trying all day to fix a problem on my local testing server. No matter what page I load, I get a 403: Forbidden error. My apache error log has this:

> [Sat Dec 13 19:33:19 2008] [crit] [client 192.168.1.3] (13)Permission denied: /home/spirit/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

Which is really weird, because my site root is /home/spirit/Workspace/ and I don't have a .htaccess file in /home/spirit/.

I've searched as much as I can, most people seem to have permissions problems, but that doesn't seem to be the problem here. Any ideas?

Cory

**Edit: I'm not sure why, but it's working now.**

---

### Post by martien on 2008-12-15
> **allspiritseve said:**
> I have been trying all day to fix a problem on my local testing server. No matter what page I load, I get a 403: Forbidden error. My apache error log has this:


Which is really weird, because my site root is /home/spirit/Workspace/ and I don't have a .htaccess file in /home/spirit/.

I've searched as much as I can, most people seem to have permissions problems, but that doesn't seem to be the problem here. Any ideas?

Cory

**Edit: I'm not sure why, but it's working now.**
You can have .htaccess and the system can still hide it from you. 
Try to vi/nano/other_editor /dir/.htaccess and see if it exist
You must see the permissions of the folder, so apache must have at least read permissions. If /home/spirit/...'s owner group is not joined to the apaches, then you have to see the "everybody permissions"

---

