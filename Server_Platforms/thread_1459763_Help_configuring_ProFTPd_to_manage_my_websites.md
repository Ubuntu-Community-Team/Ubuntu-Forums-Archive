---
title: "Help configuring ProFTPd to manage my websites"
date: 2010-04-21
forum: Server Platforms
---

### Post by okitai on 2010-04-21
Hello,
First: sorry if this question was asked many time before - I tried to search for this problem.
Second: I have a server that hosts 2 (for now - there will be more in the future) websites. The websites use apache2 with virtualhosts and they are use the same IP and the same port. I created 2 users (each named the same as the website), each with his own group (same name as the username). Then I added the users to the 'ftp' and 'www-data' groups. each website is located under the '/var/www' directory (so that the website 'testsite.com' directory is: '/var/www/testsite.com/').
I would like to setup the ProFTPd so that 1. NO anonymous users (at all!), 2. an administrative user that can access the root of the server ('/') and can access the website's directory, 3. each website user can access his and ONLY his own website's directory (no access to the root and no access to the others directory), 4. if a user that isn't the administrator and/or isn't one of the websites named users tries to access, he'll get a "GO AWAY!" message (as do anonymous users).

Thank you in advance,
Ori...

---

### Post by jm2 on 2010-04-22
[http://www.proftpd.org/docs/](http://www.proftpd.org/docs/)

Has a faq section See the chapter about configuration. It has how to configure users.

---

### Post by sandinfo on 2011-04-06
Hi, We’ve started using ProFTPD and noticed that the response to a  download that the line which states “226 Transfer complete” does not  contain the period like many/most FTP programs.  The statement from  other FTP applications read: “226 Transfer complete.” The missing  punctuation mark is causing a client to my ftp server fail to recognize a  successful transfer because their software is configured to read only  the “226 Transfer complete.”   Can anyone provide assistance on how to  modify the message on my server?

---

