---
title: "Configuring Subversion"
date: 2008-02-13
forum: Server Platforms
---

### Post by danasatriya on 2008-02-13
Hi all,

I am working on a project, which forced me to install subversion. I am a totally new user in using subversion, so I am totally confused of installing subversion. 

I am trying to do this line in my server :
svn checkout [http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims

My subversion is behind a proxy, that's why I believe I need to configure /etc/subversion/servers

and below are what I type in the configuration files :
> 
### The currently defined server options are:
   http-proxy-host            cache.something.edu
   http-proxy-port            8080
   http-proxy-username        myusernamehere
   http-proxy-password       mypasswordhere
   http-proxy-exceptions      *.edu, 
   http-timeout               0
###   http-compression           Whether to compress HTTP requests
###   neon-debug-mask            Debug mask for Neon HTTP library
###   ssl-authority-files        List of files, each of a trusted CAs
###   ssl-trust-default-ca       Trust the system 'default' CAs
###   ssl-client-cert-file       PKCS#12 format client certificate file
###   ssl-client-cert-password   Client Key password, if needed.
###
### HTTP timeouts, if given, are specified in seconds.  A timeout
### of 0, i.e. zero, causes a builtin default to be used.
###
### The commented-out examples below are intended only to
### demonstrate how to use this file; any resemblance to actual
### servers, living or dead, is entirely coincidental.

### In this section, the URL of the repository you're trying to
### access is matched against the patterns on the right.  If a
### match is found, the server info is from the section with the
### corresponding name.

[groups]
# group1 = *.collab.net
# othergroup = repository.blarggitywhoomph.com
# thirdgroup = *.example.com

### Information for the first group:
# [group1]
# http-proxy-host = proxy1.some-domain-name.com
# http-proxy-port = 80
# http-proxy-username = blah

### Information for the second group:
# [othergroup]
# http-proxy-host = proxy2.some-domain-name.com
# http-proxy-port = 9000
# No username and password, so use the defaults below.

### You can set default parameters in the 'global' section.
### These parameters apply if no corresponding parameter is set in
### a specifically matched group as shown above.  Thus, if you go
### through the same proxy server to reach every site on the
### Internet, you probably just want to put that server's
### information in the 'global' section and not bother with
### 'groups' or any other sections.
###
### If you go through a proxy for all but a few sites, you can
### list those exceptions under 'http-proxy-exceptions'.  This only
### overrides defaults, not explicitly matched server names.
###
### 'ssl-authority-files' is a semicolon-delimited list of files,
### each pointing to a PEM-encoded Certificate Authority (CA)
### SSL certificate.  See details above for overriding security
### due to SSL.
[global]
http-proxy-exceptions = *.
http-proxy-host = something.edu
http-proxy-port = 8080
http-proxy-username = myusername
http-proxy-password = mypassword
# http-compression = no
# No http-timeout, so just use the builtin default.
# No neon-debug-mask, so neon debugging is disabled.
# ssl-authority-files = /path/to/CAcert.pem;/path/to/CAcert2.pem



and what i get in my shell after typing this command : svn checkout [http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims

is
> 
svn: /etc/subversion/servers:5: Section header expected



What else do I have to configure, I have tried to search in many sources but I can't find a proper solution for my problem. 
Sorry for the troublesome, thank's a lot for your help

---

### Post by blackcougar on 2008-02-14
Put it back to this
```
### The currently defined server options are
#http-proxy-host cache.something.edu
#http-proxy-port 8080
#http-proxy-username myusernamehere
#http-proxy-password mypasswordhere
#http-proxy-exceptions *.edu,
#http-timeout 0
### http-compression Whether to compress HTTP requests
### neon-debug-mask Debug mask for Neon HTTP library
### ssl-authority-files List of files, each of a trusted CAs
### ssl-trust-default-ca Trust the system 'default' CAs
### ssl-client-cert-file PKCS#12 format client certificate file
### ssl-client-cert-password Client Key password, if needed.
###
### HTTP timeouts, if given, are specified in seconds. A timeout
### of 0, i.e. zero, causes a builtin default to be used.
###
### The commented-out examples below are intended only to
### demonstrate how to use this file; any resemblance to actual
### servers, living or dead, is entirely coincidental.

### In this section, the URL of the repository you're trying to
### access is matched against the patterns on the right. If a
### match is found, the server info is from the section with the
### corresponding name.

[groups]
# group1 = *.collab.net
# othergroup = repository.blarggitywhoomph.com
# thirdgroup = *.example.com

### Information for the first group:
# [group1]
# http-proxy-host = proxy1.some-domain-name.com
# http-proxy-port = 80
# http-proxy-username = blah

### Information for the second group:
# [othergroup]
# http-proxy-host = proxy2.some-domain-name.com
# http-proxy-port = 9000
# No username and password, so use the defaults below.

### You can set default parameters in the 'global' section.
### These parameters apply if no corresponding parameter is set in
### a specifically matched group as shown above. Thus, if you go
### through the same proxy server to reach every site on the
### Internet, you probably just want to put that server's
### information in the 'global' section and not bother with
### 'groups' or any other sections.
###
### If you go through a proxy for all but a few sites, you can
### list those exceptions under 'http-proxy-exceptions'. This only
### overrides defaults, not explicitly matched server names.
###
### 'ssl-authority-files' is a semicolon-delimited list of files,
### each pointing to a PEM-encoded Certificate Authority (CA)
### SSL certificate. See details above for overriding security
### due to SSL.
[global]
http-proxy-exceptions = *.
http-proxy-host = something.edu
http-proxy-port = 8080
http-proxy-username = myusername
http-proxy-password = mypassword
# http-compression = no
# No http-timeout, so just use the builtin default.
# No neon-debug-mask, so neon debugging is disabled.
# ssl-authority-files = /path/to/CAcert.pem;/path/to/CAcert2.pem
```

The problem is that you can't have options, (ie like http-proxy-exceptions = *.) without a header (ie [global])
also you only need to declare the values once down at the bottom of the file in the [global] section.

---

### Post by danasatriya on 2008-02-15
Yeah, i am managed to fix the problem with your help

Thank you very much :)

---

