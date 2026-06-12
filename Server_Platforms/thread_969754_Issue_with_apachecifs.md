---
title: "Issue with apache/cifs"
date: 2008-11-03
forum: Server Platforms
---

### Post by killerdragon on 2008-11-03
I will try to explain my issue fully:

So, recently we had some users who wanted to edit a site, yet we wanted the ability to easily manage granularity of user/group access. Since we have a Windows Server 2003 environment with AD setup we figured we will have a share on one of the server 2003 boxes and mount that share onto our webserver using cifs. This way the end users will edit files on the server 2003 box, while all the files get served with the web server running Ubuntu server 8.04. We were able to get the share mounted onto the Ubuntu server no problem and we can cat all the files no problem AND all the files were mounted with 777 permissions AND www-data being the user/group. HOWEVER, there seems to be some setting that is fubared because if you try to open a large (5.6MB) PDF only the first 34.1KB seem to get transferred. This behavior also manafeists itself in other things like the header picture only gets halfway loaded, however, if I do a right click -> save as for the banner it saves the whole file...again however if I do a right click -> save as for the PDF file it will only save the first 34KB no matter what.

Does anyone know of any similar issues? Or anything I can look at? The part that makes this even stranger is that I have a little Windows Server 2003 network at home with AD and I did the same thing and it works perfectly fine.

Edit: Solved own problem see this bug report: [https://issues.apache.org/bugzilla/show_bug.cgi?id=42751](https://issues.apache.org/bugzilla/show_bug.cgi?id=42751)
Added EnableSendfile Off worked...

---

