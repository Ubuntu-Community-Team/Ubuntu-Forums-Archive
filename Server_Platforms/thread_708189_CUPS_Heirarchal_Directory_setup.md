---
title: "CUPS Heirarchal Directory setup?"
date: 2008-02-26
forum: Server Platforms
---

### Post by paradexes on 2008-02-26
I am having a bit of trouble finding any info on how to do this. I am thinking I am missing something or terminology here.

I am rearchntechting  my company's multi-site print infrastructure. I would like to have the following setup (if it is possible to do with CUPS/SAMBA printing)

The share directory structure from a windows machine would show the following:
HOST
*Building1
**printer1
**printer2
**printer3

*Building2
**printer1
**printer2
**printer3
 etc. 


I am hoping someone has some info on how this could be done. Thanks. This is mainly for Windows users. BUT if this can be done for Linux users as well under CUPS that would be gravy. 

My intended setup at the moment is a CUPS/SAMBA setup with the drivers being pushed to the client. The only undocumented portion (that I could not find that is) of what I am doing is what I am asking about. 

Thanks in advance for any help that is provided.

---

### Post by paradexes on 2008-02-27
No answer at all for this?

---

### Post by faulkes on 2008-02-27
I think you would need to integrate LDAP (or Active Directory) into that mix to control / assign printers as well as authorization.

Faulkes

---

### Post by paradexes on 2008-02-28
I will look into that. Thanks. I will post if I need further help with anything else there.

---

