---
title: "Samba server 3.6.3 very SLOW opening Word and Excel files"
date: 2013-12-09
forum: Server Platforms
---

### Post by jporras on 2013-12-09
Dear all,

I recently installed an Ubuntu server in my organization and I configured it like a files server but I have a very big problem, when clients (Windows Vista) try to open a word or excel file it is very slow and thye maybe have to wait more than a minute to see the content, if they try to open another kind of file like PDF or MP3 its works normally.

I read a little bit about this problem and I did some changes in smb.conf (socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192). Unfortunately it doesn't work.

Can someone help me please.

Thank you so much in advance.

---

### Post by rackit on 2013-12-09
How large are the files that open normally vs the slow ones?

---

### Post by jporras on 2013-12-10
Hello rackit, thanks for reply.

Files that open normally can be bigger than the others for exemple in case of mp3 files. It is not a problem of the file size. 
For example to open a 12mb mp3 file you need less than a second, less than a second to open a 2mb PDF file, 38 seconds to open a 56kb excel file and more than 2 minutes to open a 856kb word file.

Regards,

jporras

---

### Post by rackit on 2013-12-10
Is it just vista clients, or do other Windows OS have issues?

---

### Post by jporras on 2013-12-11
I'm just discover that this problem appears with Windows Vista clients and Windows 7 clients with Office 2003, if I try it with Windows XP client with Office 2003 its works correctly and if I try it with Windows Vista clients with Office 2010 also works correctly.
The problem seems to be only with Office 2003 running in Windows Vista or later.

I have just Office 2003 licenses so I can't upgrade the Office of all clients to solve the problem.

Thank you very much, regards,

jporras

---

### Post by SeijiSensei on 2013-12-11
There's always [LibreOffice for Windows]("http://www.libreoffice.org/download/?type=win-x86&version=4.1.3&lang=en-US"). How long does it take to open the files with that?

---

### Post by jporras on 2013-12-12
Hello SeijiSensei,

With OpenOffice or LibreOffice there aren't this problem. Files opens in seconds.

Regards,

jporras

---

### Post by jporras on 2013-12-12
Hello everyone,

I finally found a solution, if I add the following keys into the registry of the Windows Vista clients the problem disappears and they can open the same files without delays:

reg add HKCU\Software\Microsoft\Office\11.0\Excel\Security\FileValidation /v EnableOnLoad /t REG_DWORD /d 0 /f
reg add HKCU\Software\Microsoft\Office\11.0\Word\Security\FileValidation /v EnableOnLoad /t REG_DWORD /d 0 /f
reg add HKCU\Software\Microsoft\Office\11.0\Access\Security\FileValidation /v EnableOnLoad /t REG_DWORD /d 0 /f
reg add HKCU\Software\Microsoft\Office\11.0\Publisher\Security\FileValidation /v EnableOnLoad /t REG_DWORD /d 0 /f

Thanks to everyone!

jporras

---

### Post by rackit on 2013-12-12
Thanks for posting the solution, jporras - may come in handy someday!

---

