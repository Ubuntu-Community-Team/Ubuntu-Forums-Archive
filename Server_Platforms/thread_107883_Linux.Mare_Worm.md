---
title: "Linux.Mare Worm"
date: 2005-12-24
forum: Server Platforms
---

### Post by kenweill on 2005-12-24
For more details:
[http://securityresponse.symantec.com/avcenter/venc/data/linux.mare.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.mare.html)

Linux.Mare is a worm that spreads by exploiting the PHP-Nuke "phpbb_root_path" Arbitrary File Inclusion vulnerability. The worm opens a back door and downloads and executes remote files on the compromised computer
	
Type: 	Worm
Systems Affected: 	Linux

Question:
Are we protected from this worm?

---

### Post by Koybe on 2005-12-24
> spreads by exploiting the PHP-Nuke "phpbb_root_path" Arbitrary File Inclusion vulnerability

I think you've got your answer in your question ;)

Question is : Are you using PHP-Nuke? I guess not oterhwise you would know. [PHP-Nuke](http://phpnuke.org/) is a Content Management Site. Anyway, maybe when connecting to such a site but i see this :
> Opens a back door by connecting to the following servers:
    * 81.223.104.152
    * 24.224.174.18 
So having a firewall should be enough.

---

