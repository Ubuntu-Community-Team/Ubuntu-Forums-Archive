---
title: "error while trying to install amavisd for postfix"
date: 2007-10-20
forum: Server Platforms
---

### Post by maw1key on 2007-10-20
Hi All,

I have been following the guide from flurdy on installing postfix on my ubuntu server and have run into the following error while trying to install a few of the componenets like amavisd.

STARTING AMAVISD: HOSTNAME: HOSTNAME LOOKUP FAILURE.  tHE VALUE OF VARIABLE $MYHOSTNAME IS "", BUT SHOULD HAVE BEEN A FQDN, PERHAPS UNAME(3) DID NOT PROVIDE SUCH.  YOU MUST EXPLICITLY ASSIGN A FQDN OF THIS HOST TO VARIABLE $MYHOSTNAME IN AMAVISD.CONF OR FIX WHAT UNAME(3) PROVIDES AS HOST NETWORK NAME... RETURNED ERROR EXIT STATUS 1.

I edited my /etc/postfix/main.cf and corrected myhostname to the FQDN servername.domain.com, it was only the servername, but I got the same error message after I restarted postfix and tried to install amavisd again.

Any suggestions?  Where is this UNAME(3) stored, I imagine its a global setting.

Also what should the settings be for myorigin, mydestination, and mynetworks in the /etc/postfix/main.cf file?

Thank you...

---

