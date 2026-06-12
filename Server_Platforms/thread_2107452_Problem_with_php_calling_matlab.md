---
title: "Problem with php calling matlab"
date: 2013-01-21
forum: Server Platforms
---

### Post by keith121290 on 2013-01-21
Hello,
I am using php to build a website that can calculate some convex programming. However, when I tried to connect php and matlab, I can ebxecute matlab and some of its command, but I cannot run any matlab function. :'( 

I am using SSH, Windows 7, Matlab R2012a. The following are some of my observation:
 
1. I cannot execute any matlab function(function in .m file) via php, but I can run simple command such as cd, 3*3 by matlab via our php code. I also try to run matlab in UNIX using SSH. I can successfully run both matlab function and command.
One more thing is that when I cd in php calling matlab, it shows a directory (/misc/uac_std/fyp/y13/fyp_dt/public_html/) which is different from the normal directory (/uac/std/fyp/y13/fyp_dt/public_html)

2. In php, every time I run matlab, I have this warning message - Check directory permissions.Warning: failed to create prefere nce directory /root/.matlab/R2012a. I have searched in google for it and try to make directory manually to create .matlab/R2012a in the home directory (cd~), but it did not help.

3. When running matlab in both SSH and php, I found that we run different version of matlab. When I run it in SSH, the version is R2009a. When php, the version is R2012a. I do not know whether it is related to our problem or not, but it's just strange. And also, the matlab I use in my college is R2011b...

Can someone help me:'(

---

### Post by cariboo on 2013-01-24
Moved to server platforms.

---

