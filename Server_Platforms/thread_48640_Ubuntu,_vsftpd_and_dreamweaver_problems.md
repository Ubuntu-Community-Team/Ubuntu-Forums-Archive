---
title: "Ubuntu, vsftpd and dreamweaver problems"
date: 2005-07-13
forum: Server Platforms
---

### Post by Caspa on 2005-07-13
Hi All,

I have my ubuntu installation running apache2, php4, mysql4 and vsftpd. I use Dreamweaver from a remote machine which automatically uploads files via ftp to the ubuntu box for previewing of pages. I have set up vsftpd with a umask of 022. When I upload a file manually by ftp it gets the permissions that i want (rw-r--r--) but when Dreamweaver uploads dependent files (such as images etc) when previewing a page the permissions are all wrong - images get 000 or (---------) and some files get (rw-------), it is different for every file, but the actual file you are previewing will get 744 which is what I want. I've converted to ubuntu from a fedora core 4 box (also running vsftpd) which never had this problem. Anybody have any ideas why this might be happening? Bit annoying to have to chmod all files so they can be accessed by apache.

Cheers :)

---

### Post by flade on 2005-07-13
I had similar problems just 10 minutes ago, ang figure it out. I was not using Dreamweaver but FileZilla fith PASV. Anyway this is what i did.

In vsftpd.conf I added:

file_open_mode=0766
local_umask=022
chmod_enable=YES


And all files and directories gets 755 or 744 (for files).

Hope this helps.

I have another question. I can't CHMOD from FTP client ? Why's that ?


Regards,

Flade

---

### Post by Caspa on 2005-07-13
[QUOTE=flade]I had similar problems just 10 minutes ago, ang figure it out. I was not using Dreamweaver but FileZilla fith PASV. Anyway this is what i did.

In vsftpd.conf I added:

file_open_mode=0766
local_umask=022
chmod_enable=YES


And all files and directories gets 755 or 744 (for files).

Hope this helps.

I have another question. I can't CHMOD from FTP client ? Why's that ?


Regards,

Flade[/QUOTE]

Thanks for the reply Flade...
I used the following settings:

file_open_mode=0666
local_umask=0022
chmod_enable=YES

All is working exactly as I want (except PASV definately isn't working through dreamweaver but I can live without it)...

Thanks :)

---

