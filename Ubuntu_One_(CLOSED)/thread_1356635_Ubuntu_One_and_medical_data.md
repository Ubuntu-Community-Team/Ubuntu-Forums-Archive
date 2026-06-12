---
title: "Ubuntu One and medical data"
date: 2009-12-16
forum: Ubuntu One (CLOSED)
---

### Post by Docaltmed on 2009-12-16
Does anyone know if the security provided by Ubuntu One is sufficient to meet the standards of HIPAA?

I am a physician, and would like to backup my electronic medical records database to Ubuntu One; however, HIPAA sets standards for data transmission security. Is this something that has been examined?

---

### Post by doas777 on 2009-12-16
don't do it. cloud storage is not appropriate for this usecase, and might expose you and your patients to litigation and personal danger.

---

### Post by emurphy on 2009-12-16
> **Docaltmed said:**
> Does anyone know if the security provided by Ubuntu One is sufficient to meet the standards of HIPAA?

I am a physician, and would like to backup my electronic medical records database to Ubuntu One; however, HIPAA sets standards for data transmission security. Is this something that has been examined?
Hi! I am not familiar with the HIPAA data transmission security standards. While I'm pretty confident that Ubuntu One will not lose data, it's not designed to be a failsafe backup for sensitive medical records. For example, if you accidentally deleted some documents from your computer, then Ubuntu One would do the same and delete the documents from the cloud. So I'd say you should not store electronic medical records database in Ubuntu One.

I think there are some classes of office data that might be usefully stored in Ubuntu One, for example using couchdb to store appointment records or something like that. Thats the sort of thing an application developer would need to build though, it's not a feature included right now.

---

