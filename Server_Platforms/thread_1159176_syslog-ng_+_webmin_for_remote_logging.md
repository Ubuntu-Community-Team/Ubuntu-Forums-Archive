---
title: "syslog-ng + webmin for remote logging"
date: 2009-05-14
forum: Server Platforms
---

### Post by xkaliburx on 2009-05-14
My next task to take our 7 webservers and log them to one server.  Looks like syslog-ng is the right way to go.  My question is I see webmin has a module, is/has anyone used this to setup a remote syslog-ng server?

I simply installed syslog-ng to the machine I want as the logserver as well as the 1st webserver for testing.  I don't see anything in webmin that has to be selected to say "Hey, I'm the server and listening", so I am leaving him as is.

Now the questions.  Is this the right way to go, if not, please help a bit.
1. ON the webserver, I selected Log destination, and then said add. I gave it a name, then selected syslog server, added the IP and continued.

2. On the webserver, I first goto log source and select add.  I give it name, domain.com-access and I guess I select streamsocket, and select the file name;
/var/log/apache2/domain.com-access.  Keep the other defaults and say create. 
3. Went to log targets, selected add, for log source, I select my new one I just created, leave all the rest and change destination file to the remote host I made in step 1.

Does the above seem to be right?  If so, how can I test/debug as I still see the weblog's being written local to the webserver and not to the remote.

Thanks for any help, suggestions, etc.

Lr

---

