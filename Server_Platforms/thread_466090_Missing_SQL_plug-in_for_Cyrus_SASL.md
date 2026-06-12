---
title: "Missing SQL plug-in for Cyrus SASL"
date: 2007-06-06
forum: Server Platforms
---

### Post by The Foz on 2007-06-06
I have been going around in circles, trying to configure my server as an email server.

I have been following (in part) the How To at: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/). Mostly it is very good - it will be even better when it is finished.

I have been unable to get SASL authentication working with my SMTP daemon, even though the configuration parameters seem correct. 

I have just discovered that SASL doesn't believe that I have the SQL plugin. I installed the plugin from the repository, and the files are present in /usr/lib/sasl2, but 'saslpluginviewer -a' lists only:
  'Installed auxprop mechanisms are:
  sasldb
  List of auxprop plugins follows
  Plugin "sasldb" ,       API version: 4
        supports store: yes'

As a result, authentication always reverts to sasldb2, which is not what I want.

I am about to reinstall all the SASL modules, but I have low hopes. Anyone have any ideas why the SQL plug-ins are not recognised?

---

### Post by hawzor on 2007-06-11
Foz,

Did you **apt-get libsasl2-modules-sql  **?

Worked for me. :)

---

### Post by The Foz on 2007-06-12
Yes, I have libsasl2-modules-sql. I have re-installed it, both separately, and then together with all the other sasl modules.

Currently I have installed:
libauthen-sasl-cyrus-perl
libauthen-sasl-perl
libgsasl7
libsasl2
libsasl2-2
libsasl2-modules
li9bsasl-modules-sql
sasl2-bin

Any other ideas, anyone?

---

