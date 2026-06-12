---
title: "Dovecot startup warnings"
date: 2007-01-24
forum: Server Platforms
---

### Post by ridz on 2007-01-24
I have just finished installing a mail-server for use in a home network which gets mail from our ISP. I used Ubuntu Server 6.06.1 with Postfix as the MTA and Dovecot IMAP as the MDA. All users on the LAN login using SSL based authetication to the server. Everything is working fine at the moment and the users (mainly family members) are happy :) However I (the unpaid administrator) am a bit concerned about recurring Warning messages when Dovecot starts up. The messages only appear during the startup process and is as show below:

---------------------
Starting mail server: dovecotWarning: Fixing permissions of /var/run/dovecot to be world-readable.
Warning: Corrected permission for login directory /var/run/dovecot/login
---------------------

Upon checking the permissions for /var/run/dovecot I find it IS world-readable and the permission for /var/run/dovecot/login seems to be OK. So I am perplexed on why these 2 warning messages keep appearing everytime I start up the server. Upon a hunch, I disable the 'dovecot' server (i.e. prevent it from starting at startup) and discovered that the /var/run/dovecot directory was NOT present - I assume that dovecot removes this directory upon shutdown and re-creates it upon startup - hence the recurring Warning messages. A quick peek at the 'dovecot' startup script confirmed this. So this is normal behavior for dovecot. What I want to know is - has anyone any idea how to supress the warning messages? The information available on the dovecot web site does not mention anything about this at all. Anyone using dovecot has had similiar experience?

BTW, it is not a critical issue - the server works fine - it is just annoying! 

ridz

---

### Post by MJN on 2007-01-25
Quite normal I believe - it sets the directory to 755 instead of the 700 that it's created with.
 
By the looks of reports on t'internet it seems this issue may have been resolved in a more recent version, however it's nothing to worry about as the self-fix checks/aligns everything how it should be as you guessed.
 
Mathew

---

