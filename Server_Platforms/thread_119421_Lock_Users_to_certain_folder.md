---
title: "Lock Users to certain folder"
date: 2006-01-19
forum: Server Platforms
---

### Post by noob_Lance on 2006-01-19
Hey, 

I reciently set up my server and am looking to host a few friends web sites... but i dont want them to access anything else except for there web folder. so i want to map there FTP access, SSH access and web access to there folder and theres alone... how can i go about this? Aswell... how can i go about setting up sFTP on my server aswell?

any other things i should know.. please tell me, it would be apreciated.

~Lance

---

### Post by brk3 on 2006-01-19
Maybe im on the wrong track here, but could you not just put all the users you want to restrict in their own user group, and then give that group permissions to only the folder you want..?

---

### Post by noob_Lance on 2006-01-19
each of them has there own folder though..

---

### Post by SSTwinrova on 2006-01-19
My *guess* would be that for each server (FTP, SSH, etc.) you'll need to set the root directory to the home directory of the user logging on. This would probably be found in some configuration file, so look at the man pages or Google for the specific server you're using.

---

### Post by noob_Lance on 2006-01-19
the server im using... is Ubuntu :) and ill try to find the settings..

---

### Post by LordHunter317 on 2006-01-20
Chrooting depends on the specific application.  For Apache, you cannot, but don't enable DAV and it's not an issue.  Each FTP daemon is different. For SSH, look at rssh.

---

### Post by yanik on 2006-01-20
about sftp, here an how-to

[http://www.howtoforge.net/chrooted_ssh_howto_debian](http://www.howtoforge.net/chrooted_ssh_howto_debian)

---

### Post by jchau on 2006-02-11
If you are still trying to setup the chrooted sftp and you dont want to get chrootssh & compile it , try this HOWTO: [http://www.ubuntuforums.org/showthread.php?t=128206](http://www.ubuntuforums.org/showthread.php?t=128206)

---

