---
title: "write acces in win7 folder via samba/virtualbox"
date: 2010-11-22
forum: Server Platforms
---

### Post by Jovo2 on 2010-11-22
Hi everyone!

Not sure if this is the correct forum for this but...

I run ubuntu 10.04 server in virtualbox, and have samba running. I can see the files and read them in win7, but I want write access aswell! 

I need to do this in terminal only, and Im not that well versed in Linux or the terminal.

Anyways here is my smb.conf:

[COLOR=#000000][FONT=Courier New][global][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]security = share[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]workgroup = myworkgroupname
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]load printers = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]guest account = nobody
[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New][foldername][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] Comment = test var/www/foldername[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New]path = /var/www/foldername[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] browsable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] guest ok = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] read only = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] create mask = 0644[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] force create mask = 0644[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] directory mask = 0755[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New] force directory mask = 0755[/FONT][/COLOR]


Since "read only = no" I think i should have write permissions... and since I can read the files Im guessing the smb.conf is the problem?


Many thanks!

---

### Post by yettiman2208 on 2010-11-22
just a quick thought.

I was having a similar write problem, and it turned out not to be a samba problem.

you have probably already checked this, but are you certain that the smb user actually has write priveledge to the files?

My problem was an incorrect chmod settings to the files where the user I was using for the Samba actually only had read priveledges according to Ubuntu.

Another thing to try would be to replace read only = no to writeable = yes and see if that works.

Furthermore, try "testparm /etc/samba/smb.conf"
this will let you know if there are any errors in the file.

another thought, is that I do not have any of the "mask" lines you are using in my smb.conf. So, unless you have a particular need/use for them, they may be tripping things up. Again, I do not know whether you wrote the smb.conf settings yourself, or used a generic/tutorial file, so if I am being overly simplistic I apologize.

---

### Post by Jovo2 on 2010-11-23
> **yettiman2208 said:**
> just a quick thought.

you have probably already checked this, but are you certain that the smb user actually has write priveledge to the files?



No I had not. #-oNow I have, and it works fine.

Thanks for a polite and informative answer. I wish more places on the interwebs were like the ubuntuforums.

---

### Post by yettiman2208 on 2010-11-23
Certainly,

I am glad everything worked out.

Happy Sharing.

-a large yetti

---

