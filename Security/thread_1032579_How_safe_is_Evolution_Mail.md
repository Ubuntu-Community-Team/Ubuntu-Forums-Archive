---
title: "How safe is Evolution Mail?"
date: 2009-01-06
forum: Security
---

### Post by brandon88tube on 2009-01-06
I wanted to know how safe it was to use Evolution Mail. I saw that there was a critical flaw not to long ago that let attackers use crafted e-mails to exploit a programming flaw that allows them to execute their own code with the rights of the logged-on user when an e-mail is opened. This probably was fixed, but wouldn't it just be safer to use the actual site? I want to know because I was thinking of trying Evolution out, but I don't want any security issues or password grabbing etc. from using it.

---

### Post by cdenley on 2009-01-06
It's probably just as secure as using firefox to view your mail. I guess it depends on the security features of the webmail site you would use.

---

### Post by sub2007 on 2009-01-06
A lot of these are proof of concept things (or "good" finding) rather than actual threats. For malware writers to distribute that flaw they would have to find enough people who actually use Evolution in the first place, because for enough of their spam emails to reach Evolution users (because you don't receive every piece of spam that is sent in the World, the number of email accounts each spam email hits is probably still less than 1%) the return they get would probably not be worth it.

It's much easier to just use old exploits for Outlook Express or Internet Explorer, the number of users who are using unpatched versions of that will far exceed the number of Evolution users.

---

### Post by HermanAB on 2009-01-06
Depends on the protocol.

If you use IMAP over SSL, then it is secure.  If you use a plain text protocol, then it is insecure.

Your choice!

Cheers,

Herman

---

### Post by brandon88tube on 2009-01-06
> **HermanAB said:**
> Depends on the protocol.

If you use IMAP over SSL, then it is secure.  If you use a plain text protocol, then it is insecure.

Your choice!

Cheers,

Herman

Is that an option under Evolution? If not then it would be insecure for me.

---

### Post by cdenley on 2009-01-06
> **brandon88tube said:**
> Is that an option under Evolution? If not then it would be insecure for me.

Yes, it is an option. I've never heard of an e-mail client that doesn't support SSL. Not all servers support it, though.

---

### Post by HermanAB on 2009-01-06
If your favourite mail server doesn't support SSL directly, then you can use stunnel (or SSH) to wrap IMAP with SSL.  Alternatively, install Citadel since it does every protocol ever invented since the dinosaurs.

Cheers,

Herman

---

### Post by theozzlives on 2009-01-06
Follow common-sense, don't open mail you don't know about.

---

### Post by brandon88tube on 2009-01-06
> **theozzlives said:**
> Follow common-sense, don't open mail you don't know about.

Ugh, I know that, but that really isn't answering my question.

---

