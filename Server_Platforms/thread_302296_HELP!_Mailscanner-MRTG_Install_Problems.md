---
title: "HELP! Mailscanner-MRTG Install Problems"
date: 2006-11-18
forum: Server Platforms
---

### Post by gwong86 on 2006-11-18
I followed the guide from [http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5]("http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5") and seem to find myself having problems viewing it. When I run the following command: 

env LANG=C /usr/bin/mrtg /etc/mailscanner-mrtg.cfg 

I get the following error message:

Saturday, 18 November 2006 at 12:18: ERROR: Creating templock /var/lock/mrtg/_etc_mailscanner-mrtg.cfg_l_3661: No such file or directory at /usr/bin/mrtg line 1757.

Then, when I go to [http://servername/mailscanner-mrtg](http://servername/mailscanner-mrtg) it doesn't contain any graphs. I have attached a screenshot of what I see.

Any ideas?

---

### Post by gfowler on 2006-11-18
I'll let the gurus etc explain the 'Full Meal Deal' on why this happens but the temp solution is to create a the directory that it needs.  
  mkdir /var/lock/mrtg

Then it will work, until you reboot.
If I had been at this longer than 'arh day long' I could give you a more elegant solution and one that is permanent, but alas..

Jerry

---

### Post by gfowler on 2006-11-18
You got me off my 'backside' to Google this and the link below will update the problem along with some solutions.  
[https://launchpad.net/distros/ubuntu/+source/mrtg/+bug/30428](https://launchpad.net/distros/ubuntu/+source/mrtg/+bug/30428)

Jerry

---

