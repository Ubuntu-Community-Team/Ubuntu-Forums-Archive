---
title: "Apache 2 Server Side Include functionality migration failing"
date: 2010-01-22
forum: Server Platforms
---

### Post by Lars_mn on 2010-01-22
Am migrating an apache2 web from CentOS to Xubuntu, due to a server&service change. 
 
All is working smoothly, except server side includes, ssi. 
 
The include module is loaded (apache2 -M), apache2.config was OK (ssi enabled including XbitHack On  - /server-status saying ssi directives read), the web page imported strait of the CentOS server.  I even have disabled the std Ubuntu apache2.config, replacing it with a path corrected version of the CentOS httpd.conf file, loading all missing modules. Have checked a couple of less noted things (<!--# correct and ' used instead of ") with the ssi include statement)
 
But zero respons on the include directive, working fine on the CentOS, completely dead on the Xubuntu. And no error messages in neither access.log nor error.log, not even with the debug directive. Have also checked that the two implementations have the same ownerships of files.
 
But still, ssi directives is only working on the CentOS server. Any ideas what can be the catch on the xubuntu? Am running out of ideas, what to check.
 
Cheers Lars

---

