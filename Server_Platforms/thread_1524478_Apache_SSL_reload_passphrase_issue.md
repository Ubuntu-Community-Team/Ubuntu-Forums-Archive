---
title: "Apache SSL reload passphrase issue"
date: 2010-07-05
forum: Server Platforms
---

### Post by robowen on 2010-07-05
Greetings all
 
I have spent ages searching and cannot find what Im looking for either in the apache documentation, on forums or in 2 books so Im definitely stuck!
 
I have written a shell script which amongst a heap of other stuff creates virtual hosts, and consequently also reloads apache, however my problem is that unless I include a restart in the shell script, the reload is causing the apache to stop, yet restarting everytime a new vhost is created is not really an option since it will disrupt the service for other users.
 
I know this is directly to do with the SSL passphrase as simply restarting gets everything running again with no errors. I have configured mods-available/ssl.conf so the SSLPassPhraseDialog directive uses the passphrase file instead of bulletin, hence the restart can work fine from within the shell script, but obviously reload and force-reload must be running some sort of background process which involves reloading the SSL certs or something?? so my question is can I over ride this and if so what directive / params do I use?
 
Im on ubuntu lucid 10.04 server and apache v2.2.14.
 
Any help would be greatly appreciated.
 
Many Thanks
Rob

---

### Post by sjinks on 2010-07-05
If you don't want to reenter the passphrase, you will need to created an unencrypted version of your private key. See [http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#realcert](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#realcert) for more details.

---

### Post by robowen on 2010-07-06
Hi Sjinks

Thanks for your link, but I have already created the ssl and have managed to work round the passphrase for restarting apache, with the SSLPassPhraseDialog directive in ssl.conf so surely there must be a way of applying something similar to the reload.

Cheers
Rob

---

### Post by robowen on 2010-07-06
Hello

OK I have decided to chuck the towel in and get the SSL reissued without a passphrase.

Thanks for the help guys.

Cheers
Rob

---

### Post by sjinks on 2010-07-06
AFAIK you don't need to have your cert reissued. You just need to create a "passwordless" version of your key (the link I have posted will help).

---

