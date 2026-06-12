---
title: "Issues Configuring suPHP with Ubuntu 8.04"
date: 2010-01-01
forum: Server Platforms
---

### Post by ebel3003 on 2010-01-01
Hello,

I am experiencing trouble configuring suPHP on my Ubuntu 8.04 web server. I've googled around quite a bit and the general consensus is that you first disable php5, then install the suphp module (I did that from the repo). I configured one of my Vhosts to use suPHP_UserGroup, but I get the following error:

Invalid command 'suPHP_UserGroup', perhaps misspelled or defined by a module not included in the server configuration

I know the module is loaded, so I'm not sure why I'm getting this error. Is a Vhost the right place for this setting? Note that I installed from the repository instead of compiling from source if that makes any difference. Any insight on this issue?  I can provide configuration files if need be.

**Edit:** After some extended googling, from what I understand I have to recompile suPHP using the 'paranoid' mode.  Am I correct?

Thanks,
Frank

---

### Post by majdi on 2010-03-12
I have a LAMP setup and running on Ubuntu Desktop 8.04.4 LTS. I have installed the following;

Apache/2.2.8 (Ubuntu)
PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch
Mysql 5.0.51a
libapache2-mod-suphp

I cant get suphp to work. I followed these instructions [http://www.pc-freak.net/blog/install...pache-2-2-9-2/](http://www.pc-freak.net/blog/install...pache-2-2-9-2/) but then php stopped working, so I reversed step 2 to have it working again.

I used phpinfo() script to check the php settings and I can see mod_suphp listed under Loaded Modules. Also in the PHP setting Server API = Apache 2.0 Handler, but from my search it should show; Server API = CGI if suphp is working.

ebel, did you manage to get it working? If so, please share...

---

