---
title: "Problems setting up Tomcat6 during Openbravo install"
date: 2009-06-17
forum: Server Platforms
---

### Post by getdown on 2009-06-17
Hello, I'm having trouble getting through the installation of Openbravo 2.50 as outlined in their [Wiki.]("http://wiki.openbravo.com/wiki/ERP/2.50/Openbravo_ERP_Installation") I have installed PostgreSQL, and am now attempting to install Tomcat6 from the package distribution and have run into some inconsistencies/problems. I was hoping someone might be of help.

The instructions I'm in the middle of following for installing and setting up Tomcat are [linked here.]("http://wiki.openbravo.com/wiki/ERP/2.50/Openbravo_environment_installation#Installing_Apache_Tomcat_on_Debian_.28Ubuntu.2FKubuntu.2FLinux_Mint.29") Here are my issues:

**Step #2:** My Tomcat installation is not running on port 8180, rather 8080 (I don't know if this is an issue, and know that I can change the port).

[S]Step #4: Edit /etc/default/tomcat6 file does not exist after I have installed tomcat6 and tomcat6-admin with apt-get. Is this normal? Should I just create the file and insert the Java option into it? Or has it been moved to another location or something...[/S]

[INDENT]*Removed tomcat6 and tomcat5.5, purged with apt-get -purge, and updated the apt-get resource list, cleaned all old apt-get packages and re-installed. File now exists.*[/INDENT]

**Step #7:** *cp $JAVA_HOME/lib/tools.jar /var/lib/tomcat6/lib/* this gives the error: ```
cp: cannot create regular file `/var/lib/tomcat6/lib/': Is a directory
``` should the /var/lib/tomcat6/lib/ directory be created and have tools.jar inserted into it?
**I created /var/lib/tomcat6/lib directory and copied tools.jar into it, and changed the permissions to match the other directories in /var/lib/tomcat6 I have no idea if this is correct.**

[S]**Step #8:** *Edit /etc/tomcat6/tomcat-users.xml* When I edit this file to add a user "admin" with a password as instructed, the user/login information still does not work from the Tomcat web interface, even after I have restarted the ap/rebooted.[/S]

[INDENT]*I deleted everything in tomcat-users.xml and re-created the file, I can now log into the manager app (must have had an error in the xml file or improper code ect..)*[/INDENT]

Thanks for any help

---

