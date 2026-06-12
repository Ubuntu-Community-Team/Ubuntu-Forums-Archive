---
title: "Download Directory From Apache"
date: 2008-09-24
forum: Server Platforms
---

### Post by cantdrive55 on 2008-09-24
I've got my server at home running smoothly and now that I'm at school 4hrs away when I want to download a whole directory I can't. I might not be wording it right but basically when I go to a directory and it contains both files and more directories I want to be able to download all of it including the files in the directories. 

I made a screenshot of a listing that I would want to download all of it. Ideally I would like for me to be able to download it in a tar or rar format as a package then I can just unpack it locally.

---

### Post by alastair on 2008-09-24
A simple way to do this is using SSH i.e. run an ssh sergver at home :

Install : openssh-server

You can then use the scp (secure cp) command to copy entire directories locally e.g.

scp -rp <you>@<home>:/path/to/folder .

If your local system is Windows, Putty SSH includes scp (pscp).

Security - use /strong/ passwords (or a key). Be careful of security.

Alastair

---

### Post by doogy2004 on 2008-09-24
you could also use wget and use the follow or recurssive flag to download everything.

---

### Post by cantdrive55 on 2008-09-24
There are time when I'm not on my own computer and I don't really feel like downloading putty or winscp to the computer I'm working with. I know that torrentflux has the option I'm looking for where you can download the whole directory as a tar file.

---

