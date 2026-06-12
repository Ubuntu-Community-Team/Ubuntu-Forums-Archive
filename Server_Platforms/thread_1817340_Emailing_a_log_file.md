---
title: "Emailing a log file"
date: 2011-08-03
forum: Server Platforms
---

### Post by Jay89 on 2011-08-03
Hello,
   I'm looking for a way to have a log file automatically emailed after the last script finishes entering data into it. What would be the best way to do it?

Thanks

---

### Post by blind2314 on 2011-08-03
> **Jay89 said:**
> Hello,
I'm looking for a way to have a log file automatically emailed after the last script finishes entering data into it. What would be the best way to do it?
 
Thanks
 
 
Sendmail and mailx.

---

### Post by a2j on 2011-08-04
I have this done daily...

mail -s “Subject line” [email]you@youremailid.com[/email] < /path/to/logfile.log

works great, but I think I had to do basic postfix configuration. because my isp is blocking port 25... 

I hope this helps

---

### Post by SeijiSensei on 2011-08-06
You might be happier running [logwatch]("http://sourceforge.net/projects/logwatch/files/").  It will mail you a daily summary of all syslogs.  You can install it from the repositories.

---

