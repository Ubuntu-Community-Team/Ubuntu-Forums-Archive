---
title: "Problem with virtual hosts, ubuntu 20.04"
date: 2020-09-10
forum: Ubuntu Dev Link Forum
---

### Post by zargathronax on 2020-09-10
Good afternoon, im going to summarize my problem, as a developer i  moved to ubuntu i use and i need that my project folder be located on my  localhost environment for php to run, reading the Lampp documentation  it explains that i must make a "virtual host" in which i put my project  files and i open it from the explorer through the ServerName of my  "virtualhost" after reading and following the lampp dpcumentation guide,  a lot of askubuntu, stackoverflow, and guides on the internet i keep  getting or a 403:Forbidden or a 404:Not found, so i come asking help on  solving this or any way where i can open my dev files on my IDE(atom)  and in my localhost through apache webserver throgh the webexplorer of  my choice
 thanks in advance, any further information that may be need im going to provide it, only ask

---

### Post by TheFu on 2020-09-11
Likely a directory or file permissions problem. Please post the **ls -al** for the directory were the files are located. Need to see the owner, group, and permissions for a few of the files, assuming they all have the same values.  This is basic knowledge for running a website on any Unix-like system.  The permissions need to allow the userid running the webserver, usually www-data, to have read-only access.

As for directly editing a website with an IDE, no way would I do that. I wouldn't allow it.  Edit the files somewhere else, then use rsync to mirror into the live website and if it is a webapp, may need to bounce the webapp server for changes to be seen.

And lastly, if you think the issue is with the web server configuration, post the config files.

When posting any of this data, please, please, please use "code tags".  The advanced editor has a button for that. Use it just like the bold and quote tag buttons.

---

### Post by SeijiSensei on 2020-09-11
Start by looking at the logs in /var/log/apache2.

---

