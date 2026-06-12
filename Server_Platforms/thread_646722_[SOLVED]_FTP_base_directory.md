---
title: "[SOLVED] FTP base directory"
date: 2007-12-21
forum: Server Platforms
---

### Post by dondad on 2007-12-21
I installed xampp, and it seems to be working fine. With the setup that came from the tutorial  on setting up xampp, the url is [http://localhost](http://localhost). That puts me at the equivalent of /opt/lampp/htdocs when I set up an FTP connection to [ftp://localhost](ftp://localhost) and I cannot get any higher. I would like to be able to have the top level of the ftp connection to be /opt/lampp so I can get to cgi-bin etc.. How can I do this? Thanks for any assistance.

---

### Post by HermanAB on 2007-12-21
i don't know that particular FTP server.  However, in general, you can configure the home directory on a per user or per group basis (best with proftpd).  So, if you configure a user as a FTP user, then all you usually need to do, is set that user's home directory to be wherever you want.

Read the man page for your FTP server, these things are simple and easy to figure out.

'Hope that helps!

Herman

---

