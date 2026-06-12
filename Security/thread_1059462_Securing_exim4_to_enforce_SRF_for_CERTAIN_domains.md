---
title: "Securing exim4 to enforce SRF for CERTAIN domains"
date: 2009-02-03
forum: Security
---

### Post by ensnare on 2009-02-03
Hi -- I'm using exim4 and I'd like to secure it so the server will ONLY relay emails for my domain, example.org, originating from hosts defined in my SRF record.  How can I do that for only a specific domain?

Thanks.

---

### Post by brian_p on 2009-02-04
> **ensnare said:**
> 

Hi -- I'm using exim4 and I'd like to secure it so the server will ONLY relay emails for my domain, example.org, originating from hosts defined in my SRF record.  How can I do that for only a specific domain?

Does /usr/share/doc/exim4/spec.txt.gz not provide any guidance?

---

### Post by ensnare on 2009-02-05
Sorry, meant SPF records.  I checked the man pages, not really much in there.  I basically want to make sure that the only hosts authorized to send e-mail through my server using my domain name are authenticated in some way.  I'm running a mailing list using mailman and I'm trying to limit forgeries.

---

### Post by brian_p on 2009-02-06
> **ensnare said:**
> Sorry, meant SPF records.  I checked the man pages, not really much in there.  I basically want to make sure that the only hosts authorized to send e-mail through my server using my domain name are authenticated in some way.  I'm running a mailing list using mailman and I'm trying to limit forgeries.

```
apt-cache show spfquery

```

Maybe.

---

