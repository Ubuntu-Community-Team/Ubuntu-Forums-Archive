---
title: "Enabling Tomcat's Apache Auto-Config"
date: 2010-04-20
forum: Server Platforms
---

### Post by scawa on 2010-04-20
I have a basic Apache2 <=> Tomcat site up with mod_jk as described in the Ubuntu Community Docs on Apache2/Tomcat.  One of the nice things about a straight Tomcat, though is that when I add a webapp to Tomcat, it automagically recognizes it and it is available for access on the web.  With an apache2/Tomcat instance, one has to create a new context for each webapp in the apache2.conf or httpd.conf files.

The Tomcat documents talk about an "Auto-Config" option as described here : [Configuring Apache to use mod_jk]("http://tomcat.apache.org/tomcat-3.3-doc/mod_jk-howto.html#s7").  In the section on Configuring Tomcat, one starts Tomcat with the **jkconf** option and it generates a *TOMCAT_HOME/conf/auto/mod_jk.conf* file in the described location.  One then includes the location in the apache2.conf or httpd.conf file.

I would like to use this option but I have a couple of questions on how to do so under Ubuntu (since there is no TOMCAT_HOME directory and the configuration files are under /etc/apache2 or /etc/tomcat6 ).

[LIST=1]
[*]How do you start Tomcat with a jkconf option?  The /etc/iniit.d/tomcat6 file does not have the ability to take parameters other than start, stop, restart.  Should I modify the /etc/init.d/tomcat6 file and if so, how?
[*]Where is the mod_jk.conf file going to be created?  I don't see where tomcat is pointing to this file.  If it creates it in a different location than I expect, I can always to a ln -s to it but I don't see where this file is created?
[/LIST]

Thanks a lot for the help.

Stephen McConnell

---

