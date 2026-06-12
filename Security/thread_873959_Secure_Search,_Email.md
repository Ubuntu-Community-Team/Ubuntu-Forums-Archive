---
title: "Secure Search, Email"
date: 2008-07-29
forum: Security
---

### Post by johntelthorst on 2008-07-29
I had a friend who recommended [cuil]("http://www.cuil.com") for search as a secure alternative to google.  First, how secure is cuil?  And is it worth using over google.  Secondly, the topic of secure e-mail came up, are there any secure e-mail clients that are worthy of recommendation?

---

### Post by Titan8990 on 2008-07-29
It is typically the mail server that is insecure not the mail client. This is because most free email services do not offer a connection over TLS or SSL. Many do have webmail over SSL which is probably the best you will be able to do.

---

### Post by hyper_ch on 2008-07-29
google will retain your ip and search keys for 18 months... cuil won't...

---

### Post by judge jankum on 2010-10-07
Has anyone used safe-mail.net? And if so how safe is it?

---

### Post by rookcifer on 2010-10-07
> **johntelthorst said:**
> I had a friend who recommended [cuil]("http://www.cuil.com") for search as a secure alternative to google.  First, how secure is cuil? 

I don't care for Cuil's results.  If I were you I would use Scroogle's SSL search.  It gets all its data from Google, except it doesn't record your IP.  Being SSL, it also encrypts all searches.  To use it, just download the Firefox plugin [here]("https://addons.mozilla.org/en-US/firefox/addon/12506/").


>  Secondly, the topic of secure e-mail came up, are there any secure e-mail clients that are worthy of recommendation?

Just use Thunderbird with Enigmail.  Of course, first you will need to generate a GPG keypair.  [Read here]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto").  After you do that, you simply setup Thunderbird/Enigmail to use the key.  You can then either send your key to all your contacts via email or just send it to a keyserver from where anyone can download it.  Of course, your contacts will also need to generate keys.  This is a much better alternative than relying on some third party email server to encrypt for you.  For instance, they might have master keys, etc.

---

### Post by tubbygweilo on 2010-10-07
+1
Thunderbird and Enigmail are rather fine but as rookcifer has suggested it is so hard to get contacts to adopt a GPG keypair let alone use of such technology when dealing with local authorities, banks or any other business where you would wish to keep notes away from unintended prying eyes.

---

### Post by anomie on 2010-10-07
Scroogle is one approach. I also recommend checking out [ixquick](https://www.ixquick.com/), which: 
[list]
[*] has good query results, IMO; 
[*] supports http/s searches; 
[*] allows you to visit hits via an http/s proxy (they provide). 
[/list]

---

