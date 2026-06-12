---
title: "Squid with --enable-ssl"
date: 2005-09-22
forum: Ubuntu Backports
---

### Post by bens on 2005-09-22
How whould i go about creating a squid package with the --enable-ssl flag set.  I would also want this package to override the defualt ubuntu one.

Thank You
Ben

---

### Post by Divan Santana on 2007-05-11
Like so:

apt-get source squid
apt-get  build-dep squid
apt-get install devscripts build-essential fakeroot
cd squid-2.6.1
vim debian/rules
Add --enable-ssl \ to &#8220;# Configure the package&#8221; section
./configure
debuild -us -uc -b
cd ..
dpkg -i squid??? squid-common???

---

### Post by nsr79 on 2008-01-28
Hi,

I have almost the same problem enabling ssl in Squid.

I'm trying to setup reverse proxy with squid 2.6STABLE14 running on Ubuntu server 7.10 and it's already active. But now I found that the SSL has not been enabled during initial installation because I have this error after configuring squid and restart service:
> 2008/01/28 11:57:00| parseConfigFile: line 2 unrecognized: 'https_port 443 vhost ......

Is there any way to enable SSL in Squid without having to rebuild? If there's no such way, what steps do I have to take to get SSL enabled?

I tried running a command "apt-get install squid -enable-ssl" but didn't work.

cheers,
N

---

### Post by mozkill on 2008-01-28
i posted a request for this hint on UbuntuGuide

---

### Post by nsr79 on 2008-01-28
Hi mozkill, can you provide a shortcut link to the post you mentioned?

---

### Post by williammeyer3 on 2011-02-15
I figured this one out the long and hard way. I had been searching for this answer for a while for both ubuntu versions 10.04 and 10.10 so I can only hope this helps. since this was the first result I received from google when looking up the error lets try this. 
I also installed all open ssl projects by using the command

apt-get install openssl*

prior to performing my squid installation. I had tried these commands below before with no luck but after attempting when running the command above I achieved success. Which package I needed Im not sure yet I am still weeding them out.

I followed these steps from earlier.

1 - apt-get source squid
2 - apt-get build-dep squid
3 - apt-get install devscripts build-essential fakeroot (if running debian you must install dpkg-dev first before this step I tried debian as well with the same issues)
4 - Edit the rules file by running vim debian/rules
5 - In the # Configure the package section add the following two lines in sequence and spacing as the lines in the section

--enable-ssl \
--with-open-ssl=THIS LOCATION MUST CONTAIN THE OPENSSL.CNF file \ 


(ex: mine in 10.10 was located at /usr/lib/ssl)
you must make sure to include the \ symbol spaced one space from the file or command. 



6 - ./configure
7 - debuild -us -uc -b
8 - cd ..
9 - apt-get install squid-langpack
10 - dpkg -i squid-package-version-#-.deb squid-common-package-version-#.deb

This will install the entire package and its working in my configuration. Which is a standalone reverse proxy server sitting behind a firewall proxying both http and https requests. If you miss step 9 step 10 will report errors with missing dependencies.

---

### Post by treacl on 2012-01-08
Thanks to everyone for putting together this how-to. I've rebuilt squid with ssl, confirmed with "squid -v". But it does not appear to be caching any SSL content. So the question is:

--How do I configure squid as a forward proxy to cache static SSL content?

--Do I have to turn off connect forwarding?

--Which of the SSL options do I need to set?
```
# ssl_unclean_shutdown off
# ssl_engine
# sslproxy_client_certificate
# sslproxy_client_key
# sslproxy_version 1
# sslproxy_options
# sslproxy_cipher
# sslproxy_cafile
# sslproxy_capath
# sslproxy_flags
# sslpassword_program
```

--Is there anything else I need to do?

The documentation in the config file is minimal, and I can't find instructions or an example anywhere that seems to apply. (Perhaps because it's bloody obvious, though obviously not to me.)

Many thanks,
treacl

---

