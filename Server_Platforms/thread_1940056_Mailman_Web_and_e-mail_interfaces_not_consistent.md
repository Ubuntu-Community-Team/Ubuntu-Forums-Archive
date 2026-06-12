---
title: "Mailman Web and e-mail interfaces not consistent"
date: 2012-03-12
forum: Server Platforms
---

### Post by MidnightJava on 2012-03-12
I'm running Mailman 2.1 on Ubuntu 11.04, installed from apt-get. Postfix is my mail server. After some initial troubles, I have the Malman-Postfix integration apparently working, except for one thing. It seems that the lists being managed by the web admin interface are entirely separate from the lists available via the email interface.

For example, if I create a list via the web interface, i doesn't exist if I run bin/list_lists to see all existing lists. And of course there are no aliases set up, so email to the list bounces with "no such local user" message. If I run bin/newlist, giving it the same name as the list I created via the web interface, the web and email interfaces are still not consistent. Members added via the web interface are not recognized as members when sending e-mail to the list, and members successfully added via email do not appear in the list of members vai the web interface.

I'm running the mailman web interface behind apache, and I have ScriptAlias /mailman pointing to /usr/lib/cgi-bin/mailman. I do see the executables such as admin, confirm, create, listinfo, etc. there. I wonder if for some reason the mailman daemon is pointing somewhere else for scripts to run when incoming mail is received.

The mailman process to run is specified in Postfix's master.cf file. The executable is named mailman. Per the man pages for master(5) the executable will run relative to the path specified by postfix config parameter queue_directory. This value is set to /var/spool/mailman as determined by executing  ```
postconf queue_directory
``` I don't even see a mailman executable at that location, so I don't understand how the mailman process is executing.

I also noticed that there is a postfix-wrapper for managing multiple instances of postfix. Do I need to configure this explicitly? I've been starting postfix by running ```
/etc/init.d/postfix start
``` but now I'm using just ```
postfix start
``` since I understand that will invoke the multi-instance wrapper.

I'd greatly appreciate it if someone could help me sort all this out and get a consistent web/email environment running.

---

### Post by MidnightJava on 2012-03-14
This was caused by a silly cockpit error. I was using the wrong IP port, thus hitting a mailman instance on a different server from the one with the live postfix installation. The mind is a terrible thing.

It was pointed out on the mailman list that if the web app does not return an error when creating a list, then the list files will exist somewhere on the server, and can be used as a reliable marker if there's any concern that the web app i snot working.

```
find / -name config.pck
```

was useful for showing me that the files that had to gave been created were not there, thus cluing me in to the fact that I was hitting the mailman web app on the wrong server.

---

