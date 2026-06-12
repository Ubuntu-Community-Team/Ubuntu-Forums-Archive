---
title: "Create private GPG key server"
date: 2011-01-25
forum: Security
---

### Post by SeijiSensei on 2011-01-25
One of my clients is considering implementing GPG or a similar technology to encrypt internal emails. (They have a different system in place already for external mail.)  I've done some reading on the subject but can't seem to find any information about how one might set up a keyserver.  All the discussions I've seen so far talk about uploading the public keys to a server like keyserver.ubuntu.com.  

Does anyone know what software packages might be used to set up our own private keyserver on a Linux machine?

---

### Post by artie_effim on 2011-01-26
this should work [http://www.openca.org/projects/openca/docs.shtml]("http://www.openca.org/projects/openca/docs.shtml").  But rolling this out is not a trivial event.  Plan, plan, plan, test, test, test, implement.

---

### Post by SeijiSensei on 2011-01-26
Thanks, but OpenCA seems designed to handle certificates rather than GPG/PGP keys.  However I found this project today:

[http://code.google.com/p/sks-keyserver/](http://code.google.com/p/sks-keyserver/)

I also looked at the older project, [PKS](http://sourceforge.net/projects/pks/).  While it compiled fine, it threw an error when I executed the binary.  I searched on Google for the error string and was directed to the SKS server as a better implementation.  SKS does look more up-to-date and better supported, so I'm going to give that a try.

Thanks for the suggestion!

---

