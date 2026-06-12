---
title: "PXE Server, Error 67"
date: 2011-08-30
forum: Server Platforms
---

### Post by SoronZero on 2011-08-30
Hey all got a problem thats stumped me and need help. I'm making a PXE imaging server to deploy windows 7 over the network here at work but I am running across a "system error 67, the network name cannot be found" when using "net use z: \\192.168.0.1".

The server is setup with PXE, WinPE 3.0 custom boot image, DHCP, TFTP, DNS and Samba. Folder permissions currently set at 0664 for samba folders involved. The client PC is able to boot WinPE to the command prompt and ping the PXE/Samba Server by both IP and hostname but is unable to connect to it when using the above command, and using smbclient on the server reveals that the shares are listed and netstat shows its listening. Any help appreciated on this as its been driving me nuts for days!

---

### Post by maikel.b on 2011-08-30
[COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When you make a backup with Clonezilla, you can put the backup in the home partition folder.....[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Please follow this site, and maybe it will help you..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Let me know if it works...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Kind regards!!![/FONT][/COLOR]
[COLOR=black][FONT=Verdana][[COLOR=#0000ff]http://mb.homelinux.net/linuxsite/node/195[/COLOR]]("http://mb.homelinux.net/linuxsite/node/195")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Succes!!![/FONT][/COLOR]

---

### Post by SoronZero on 2011-08-30
Its actually the other way around, im trying to deploy windows 7 across around 100 desktops, not use the samba server as a backup.

---

### Post by maikel.b on 2011-08-30
Are all the desktops the same??
 
If this is true, you can make a image of one desktop, and the 99 are clone.. ??

---

### Post by SoronZero on 2011-08-30
Yes they are all the same and thats what I was trying to accomplish, but each PC has to be deployed rather than imaged as they have to have unique names to join a domain. Either way if I can't connect to the server to retrieve the image ....

I have added the servers config files (with sensitive data removed) if it will aid in trouble shooting in any way,

---

### Post by SoronZero on 2011-08-31
Figured it out, had to put Samba in user instead of share mode, create a samba account, and log into the correct share.

---

