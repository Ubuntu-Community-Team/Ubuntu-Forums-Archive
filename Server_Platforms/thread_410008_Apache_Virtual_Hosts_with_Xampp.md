---
title: "Apache Virtual Hosts with Xampp"
date: 2007-04-15
forum: Server Platforms
---

### Post by Nalum on 2007-04-15
[FONT=Lucida Console]Hello all,
I've been trying to set up virtual hosts on apache for the last 2 days and have gotten two to work but the rest don't work.

This is how my virtual hosts are set up currently
> 
NameVirtualHost *:80

<VirtualHost *:80>
    ServerName [www.site1.nd]("http://www.site1.nd")
    DocumentRoot /opt/lampp/htdocs/site1
</VirtualHost>

<VirtualHost *:80>
    ServerName [www.site2.nd]("http://www.site2.nd")
    DocumentRoot /opt/lampp/htdocs/subdir/site2
</VirtualHost>

<VirtualHost *:80>
    ServerName [www.site3.nd]("http://www.site3.nd")
    DocumentRoot /opt/lampp/htdocs/subdir/site3
</VirtualHost>

<VirtualHost *:80>
    ServerName [www.site4.nd]("http://www.site4.nd")
    DocumentRoot /opt/lampp/htdocs/subdir/site4
</VirtualHost>

<VirtualHost *:80>
    ServerName [www.site5.nd]("http://www.site5.nd")
    DocumentRoot /opt/lampp/htdocs/subdir/site5
</VirtualHost>

I have no idea why **site4** and **site5** work and not the others.
I have restarted xampp numerous times since making the changes to the conf file.

Any help greatly appreciated.
[/FONT]

---

### Post by SlowYaRoll on 2007-05-02
This is all setup in
/opt/lampp/etc/extra/httpd-vhosts.conf
???

---

### Post by Nalum on 2007-05-02
No, it is in the httpd.conf file. I tried to put it into the httpd-vhosts.conf but it didn't work at all when I did that.

---

### Post by SlowYaRoll on 2007-05-02
Ohhhhh!  Okay. . .I think I may know what hte problem is.  With XAMPP, all of those virtual hosts won't work.  XAMPP sort of works like base Apache installs in Ubuntu; where it tries to make the httpd.conf file less confusing by splitting it up into multiple files.

Put your virtual hosts in the /opt/lampp/etc/extra/httpd-vhosts.conf file.

To make XAMPP actually look for the extra Apache settings (i.e. virtual hosts), make sure that the followiong lines are uncommented in your httpd.conf file

```

# Virtual hosts
Include etc/extra/httpd-vhosts.conf

# Various default settings
Include etc/extra/httpd-default.conf

# XAMPP
Include etc/extra/httpd-xampp.conf

```

After that, give Apache a restart

```

sudo /opt/lampp/lampp stopapache
sudo /opt/lampp/lampp startapache

```

Sometimes it'll kick back errors if the directories don't exist.  Also, I used to always have typos.  :(  That'll also cause Apache to fart on your configs and not start.  

:lolflag: 

Let me know if that helps.

P.S.
When I said make sure the lines are uncommented, ofcourse it's okay to leave the purpose of the line commented.  You just want to make sure what's below the description is uncommented.  Just thought I should clarify that.

---

### Post by Nalum on 2007-05-02
Cool, I'll give it a try when I get home.

---

### Post by SlowYaRoll on 2007-05-02
[CENTER]> **Nalum said:**
> Cool, I'll give it a try when I get home.

Wait until you get home?!?!  You don't have ssh access to the system setup?

You are my hero!  [/CENTER]

I've never been able to wait until I get home to work on my linux box(es).  I worked for one place that actually blocked port 22 for SSH.  I almost had a heart attack!  Luckily for me, I did have webmin installed so I logged in via that and made SSH run on the telnet port (23).  After that, I kept the puTTy.exe file on a USB Flash drive and played until I couldn't play anymore.  =)

People always tried to catch me too.  Gotta love the hotkey combination of 'Windows Key' + 'D'

---

### Post by elainevdw on 2008-04-18
Speaking of SSH -- I don't suppose you could help me figure out how to set up my XAMPP install (on Windows) so that I can terminal in (using Putty) here on my local machine? Since it's on Windows, it's not like I can just open a terminal and go at it. :/

---

