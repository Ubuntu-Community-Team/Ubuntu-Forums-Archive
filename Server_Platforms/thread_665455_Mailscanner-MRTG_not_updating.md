---
title: "Mailscanner-MRTG not updating"
date: 2008-01-12
forum: Server Platforms
---

### Post by gwong86 on 2008-01-12
I am having some problems getting Mailscanner-MRTG to update with the latest info. It seemed like it was working when I first setup the server but has since stopped. The website says it was last updated on Jan. 8 at 7:40 and had been up for 32 minutes. That is not the case anymore

I followed the instructions at [http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5]("http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5") to get it up and running.

Mailscanner is running and email is flowing. When I try to run /etc/init.d/mrtg start there is no service that exists. Is this normal? Any ideas on why I can't get the graphs and stats to update?

Thanks.

---

### Post by gfowler on 2008-01-12
> **gwong86 said:**
> I am having some problems getting Mailscanner-MRTG to update with the latest info. It seemed like it was working when I first setup the server but has since stopped. The website says it was last updated on Jan. 8 at 7:40 and had been up for 32 minutes. That is not the case anymore

I followed the instructions at [http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5]("http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu_p5") to get it up and running.

Mailscanner is running and email is flowing. When I try to run /etc/init.d/mrtg start there is no service that exists. Is this normal? Any ideas on why I can't get the graphs and stats to update?

Thanks.


You need a mrtg directory in /var/lock/ for it to work. Reboot will remove the directory and MRTG will fail to update. I put mkdir /var/lock/mrtg in /etc/rc.local and it makes the required /var/lock/mrtg on reboot. 

Jerry

---

### Post by gwong86 on 2008-01-13
Thanks for the feedback. I created /var/lock/mrtg and also added the line to make the directory in rc.local. I rebooted the server but it doesn't seem like its working. It still says the server has been up for 32 minutes and last updated on Jan. 7.

Any other ideas? Thanks.

---

### Post by gfowler on 2008-01-13
> **gwong86 said:**
> Thanks for the feedback. I created /var/lock/mrtg and also added the line to make the directory in rc.local. I rebooted the server but it doesn't seem like its working. It still says the server has been up for 32 minutes and last updated on Jan. 7.

Any other ideas? Thanks.

Will it update by running the manual update?

 env LANG=C /usr/bin/mrtg /etc/mailscanner-mrtg.cfg

If it will then check the crontab entry, mrtg.cfg, otherwise ......

Sorry you've exceeded my expertise. 

Jerry

---

