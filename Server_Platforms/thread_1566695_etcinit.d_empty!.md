---
title: "/etc/init.d/ empty!"
date: 2010-09-02
forum: Server Platforms
---

### Post by daWsOn_s on 2010-09-02
Hello,
ubuntu 10.04 vps server here.
I don't know what happened but I lost EVERYTHING in it!
Since I'm running websites on my VPS I had to backup mysql, nginx and php5-fpm remove them and reinstall cause without init.d script I couldn't even start them. Now it's ok but they don't start on system startup along with other programs I had like cron, sendmail and others I dont remember. The only programs that start are sshd and vsftpd.

1- how the hell have I lost them? I'm certain I didn't delete the directory content! I also tried to check access log to see if someone did this but nothing.
2- how can I reput them there or put them in the startup list manually from the command line? what services should I start considering I had just installed mysql, nginx and php5-fpm and syslog-ng on 10.04 minimal?

Thanks

---

### Post by deoren on 2010-09-02
To select which services start at certain run levels, I found this to be helpful: [Debian or Ubuntu Linux runlevel configuration tool to start service]("http://www.cyberciti.biz/faq/howto-runlevel-configuration-tool-to-start-service/")

If you're certain the missing init.d scripts wasn't your goof, then I'd suggest putting in a support request with your provider. In regards to replacing them, my approach would be to setup a virtual machine and install the packages there and copy over the init.d scripts to your VPS.

You could use Virtual Box or VMware Player (Windows) to install Ubuntu and install the packages you have on your VPS. Then you could copy over a tarball of /etc/init.d and decompress on your VPS.

That said, I still encourage getting in touch with support to see if they can tell you anything further.

---

### Post by BkkBonanza on 2010-09-02
The /etc/init.d scripts also depend on other links in /etc/rc?.d where ? is the various runlevels. And there are other scripts that init and control this whole process. So if by chance any of those other things are missing then the process would be broken as well. On newer versions of Ubuntu there is also UpStart which uses scripts in /etc/init - and some services have transitioned to that and some not. So it's all pretty convoluted now. It will take some fancy footwork to determine the full extent of damage done and repair it.

---

