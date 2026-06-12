---
title: "httpd runs w/o Apache installed"
date: 2012-06-12
forum: Server Platforms
---

### Post by worldInd on 2012-06-12
I'm installed the Ubuntu Bitnami Wordpress image, which installed most things for me, but now I'm thinking it was maybe a mistake, and it'd be smarter to uninstall everything and start over, but I figured I'd see here if there were any suggestions first. 

So, after install, I tried to edit my apache2.conf and the sites in sites-available, using the command "sudo a2ensite ___ " to enable my site. all goes well. 

However, when I go to restart or even just start my Apache server, I am not getting a cannot bind to port 80 error. 

I've tried killing all processes on port 80, or even stopping apache 2 (sudo service apache2 stop), which works, but when I go to start apache again, I just end up getting a [fail] (sudo service apache2 start). 

When I send "sudo fuser -v 80/tcp" I get: 
80/tcp:              root        837 F.... httpd
                     daemon      839 F.... httpd
                     daemon      840 F.... httpd
                     daemon      841 F.... httpd
                     daemon      842 F.... httpd
                     daemon      843 F.... httpd

but directly after this, I send: "sudo service apache2 status" I get: "apache2 is NOT running". 

Any ideas with this? Any thoughts on something I can try to do to uninstall whatever is running httpd? I know that typically this is an apache specific file, but before I installed apache2 it wasn't showing in the directory and the webserver to me was unknown.. 

Thanks.

---

### Post by nsnidanko on 2012-06-14
I suspect you do have 2 httpd services starting simultaneously. I would check your /etc/init.d directory and make sure you have only one service.

Maybe even disable "working" apache by editing /etc/init.d script and than reboot server and see if something listens on port 80. If that's the case dig for any startup scripts and get rid of them or use[FONT=Ubuntu] update-rc.d command
[/FONT]

---

### Post by worldInd on 2012-06-14
hmm, thanks nsnidanko.. but when i look into init.d I have a kajillion process running in there, and one of them is not httpd.. 

I installed the bitnami "wordpress" install, hoping that everything would be rolled out for me nicely, but that didn't seem to be the case... 

I'm installing a clean install manually right now.. think I'm going to abort this effort.. Thanks.

---

