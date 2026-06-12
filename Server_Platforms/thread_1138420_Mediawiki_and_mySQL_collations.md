---
title: "Mediawiki and mySQL collations"
date: 2009-04-26
forum: Server Platforms
---

### Post by tkhobbes on 2009-04-26
Hi everybody

I know this is not an Ubuntu specific questions, but maybe someone around here has had a similar problem in the past and can help out.

I just upgraded my server to 9.04; now, my existing mediawiki installation is somehow completely blown to bits, as I get a lot of errors about collation errors, like this:
```
A database query syntax error has occurred. This may indicate a bug in the software. The last attempted database query was:

    (SQL query hidden)

from within function "MathRenderer::_recall". MySQL returned error "1267: Illegal mix of collations (latin1_bin,IMPLICIT) and (utf8_general_ci,COERCIBLE) for operation '=' (localhost)".
```

I already changed the collation of all my tables (and the wiki-db) to utf8_general_ci (and also back to latin1_bin), but the error persists.

Any way in how to tackle this? - I guess I somehow have to convert all existing data into UTF8, change all collations to UTF8 and set the configuration for the mysql-server and for mediawiki also to UTF8?

---

### Post by tkhobbes on 2009-04-27
Found the solution - see [http://www.hobbes.ch/2009/04/mediawiki-madness/](http://www.hobbes.ch/2009/04/mediawiki-madness/)

---

### Post by muha on 2010-11-16
> **tkhobbes said:**
> Found the solution - see [http://www.hobbes.ch/2009/04/mediawiki-madness/](http://www.hobbes.ch/2009/04/mediawiki-madness/)

Hi Hobbes, your site seems to be down. Can you post the solution here? I'm running into similar problems.

---

### Post by tkhobbes on 2010-11-18
I put up the text of the old site again.
The link you wanted is now here:
[http://www.hobbes.ch/oldsite/?p=504](http://www.hobbes.ch/oldsite/?p=504)

hth

---

### Post by RJARRRPCGP on 2010-11-18
> **tkhobbes said:**
> I put up the text of the old site again.
The link you wanted is now here:
[http://www.hobbes.ch/oldsite/?p=504](http://www.hobbes.ch/oldsite/?p=504)

hth

Thanks. (Getting sick of error 404 and error 403) (seems that's what I usually get)

---

