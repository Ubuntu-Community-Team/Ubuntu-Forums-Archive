---
title: "Trying to mount CIFS volume via fstab"
date: 2018-12-09
forum: Server Platforms
---

### Post by mn1247 on 2018-12-09
I am running an Ubuntu 18 server, and am trying to mount a CIFS network volume in fstab.  I've tried...

'''
//192.168.1.25/media /mnt/PlexFiles cifs username=user1,password=pppppp,iocharset=utf8,file_mode=0777,dir_mode=0777 
 '''

and I get the following error...

'''
CIFS VFS: validate negotiate protocol failed: -13
'''
Here's the strange part.  It works fine as long as I open a share name that happens to be the same as the linux server username, but fails otherwise.  But, the settings for all the shares are identical on the CIFS server end.

I tried adding uid=1000 (the uid of the Ubuntu server user), but no effect.

Where am I going wrong? 

Thanks
Eric

---

### Post by darkod on 2018-12-09
1. Do you have the package cifs-utils installed on the client?

2. Is the share on the server named 'media'? You can only use that mount command if that is the actual share name. You say you can mount share with another name so maybe you are not using the correct share name in this case.

---

### Post by Morbius1 on 2018-12-09
What is not entirely clear to me is who is doing the mounting. The Ubuntu 18.04 server? Some Linux client running an unknown version of Ubuntu? And what OS is running on 192.168.1.25?

Anyhoo:
>  CIFS VFS: validate negotiate protocol failed: -13
I suspect the "protocol" refers to the smb dialect used by the client to access the server.

Start with the oldest
>  //192.168.1.25/media /mnt/PlexFiles cifs username=user1,password=pppppp,iocharset=utf8,file  _mode=0777,dir_mode=0777[COLOR=#0000ff]**,vers=1.0**[/COLOR] 
And work your way up to the most current by replacing [COLOR=#0000cd]**vers=1.0**[/COLOR] with [COLOR=#0000cd]**vers=2.0**[/COLOR] then [COLOR=#0000cd]**vers=2.1**[/COLOR] and finally [COLOR=#0000cd][B]vers=3.0
[/B][/COLOR]

---

### Post by mn1247 on 2018-12-09
Thanks for the replies.  I'm afraid all of the versions give the same error.  To answer some questions...

1) cifs-utils is installed
2) The share on the (CIFS) server is named "media" and the username and password are the ones for a user of the CIFS server.  That user has full access to the media share.
3) Ubuntu Server 18.04 is generating the error while trying to mount the CIFS share, from fstab during boot.  The CIFS share is being served up by Universal Media Server (also running on Linux).  Notably, I can access the shares on the CIFS server from my Mac.

In reviewing the boot logs, I found a bit more detail regarding the error.  It originates from the kernel during boot...

CIFS VFS: Send error in QFSUnixInfo = -13
CIFS VFS: Send error in QFSAttributeInfo = -13

Any ideas?
Thanks again
Eric

---

