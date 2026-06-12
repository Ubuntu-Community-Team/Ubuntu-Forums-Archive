---
title: "SSL Certificates and Cookies"
date: 2010-11-29
forum: Security
---

### Post by OooBuntuRox on 2010-11-29
[SIZE=2]Hello everyone,

I was viewing my Firefox SSL certificates and I see **Japanese Government** listed. For the life of me, I have no idea why I would have this certificate.

Can anyone point me in the direction of understanding the how, what and why's of having certificates. How I determine which certificates are legitimate/ needed, etc? Can I delete them all and start over fresh? How do I decide what to keep? Does having a long unneeded list slow down the system any?

Basically, I would like to understand more about cookies and certificates. Some of my certificates say they are ROOT certificates. It seems, for security reasons, we should all have a better understanding of these items.

Can anyone help with this subject?

Thanks in advance, OoobuntuRox[/SIZE] :guitar:

---

### Post by movieman on 2010-11-29
Mozilla decide who's trustworthy and who's not, and then put those certificates into the browser.

Unfortunately SSL is fundamentally flawed in that any CA can sign keys for any domain, so a single corrupt CA can completely break the system; that was OK in the early days when there were only two or three CAs but now there are large numbers it's going to lead to disaster sooner or later.

SSL should at least allow you to say 'this CA is allowed to sign keys for these domains and nothing else'. For example, the 'Government Of Nowhereistan' CA should be allowed to sign any certificate for its servers, but not a fake certificate for my bank.

---

### Post by artie_effim on 2010-11-29
take a look at this:

[http://www.mozilla.org/projects/security/certs/included/#Japanese%20GPKI](http://www.mozilla.org/projects/security/certs/included/#Japanese%20GPKI)

---

### Post by OooBuntuRox on 2010-12-02
> **movieman said:**
> Mozilla decide who's trustworthy and who's not, and then put those certificates into the browser.

Unfortunately SSL is fundamentally flawed in that any CA can sign keys for any domain, so a single corrupt CA can completely break the system; that was OK in the early days when there were only two or three CAs but now there are large numbers it's going to lead to disaster sooner or later.

SSL should at least allow you to say 'this CA is allowed to sign keys for these domains and nothing else'. For example, the 'Government Of Nowhereistan' CA should be allowed to sign any certificate for its servers, but not a fake certificate for my bank.

Well that has to be to the shortest yet most helpful response I've had in a long time. Thank you very much for resolving my immediate concern. Also, I get your point about the long term concern. CA is something of a false sense of security. Perhaps a ticking bomb 8-[

Thanks very much !

OoobuntuRox :guitar:

---

### Post by OooBuntuRox on 2010-12-03
> **artie_effim said:**
> take a look at this:

[http://www.mozilla.org/projects/security/certs/included/#Japanese%20GPKI](http://www.mozilla.org/projects/security/certs/included/#Japanese%20GPKI)


I cross-checked the list vs the certs. Yes they match. Thank you as well for some relief to my immediate SSL concerns.

Regards, OooBuntuRox :guitar:

I will mark my post as **solv-ed**

---

### Post by OooBuntuRox on 2010-12-03
Again my thanks to both of you movieman &  artie_effim for the info and for the quick responses.

Ooobunturox, :guitar:

Also for anyone interested, I stumbled upon this link for ssl info from Verisign:  [http://www.verisign.com/ssl/ssl-information-center/index.html?sl=8UGNM-0000-01-00](http://www.verisign.com/ssl/ssl-information-center/index.html?sl=8UGNM-0000-01-00)

---

