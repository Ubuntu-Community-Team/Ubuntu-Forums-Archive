---
title: "Bind 9.8.0 Dynamic Update."
date: 2011-09-12
forum: Server Platforms
---

### Post by ewtesterman@cox.net on 2011-09-12
I am setting up a bind server for an active windows domain. Bind is running and working fine with the exception of dynamic updates. The sticking point here is I need a dns.keytab file for this to work. The only doc's I could find are from the Samba4 wiki and this file is created automatically when you prevision Samba4 as a PDC. I cannot do that as this is an existing domain and I really do not want this box to do anything but Bind ie no samba. So how do I generate this dns.keytab file? The only other doc I found was a Red Hat doc and it uses a Red Hat tool to build this file so that was not helpful either.

---

### Post by Dangertux on 2011-09-12
> **ewtesterman@cox.net said:**
> I am setting up a bind server for an active windows domain. Bind is running and working fine with the exception of dynamic updates. The sticking point here is I need a dns.keytab file for this to work. The only doc's I could find are from the Samba4 wiki and this file is created automatically when you prevision Samba4 as a PDC. I cannot do that as this is an existing domain and I really do not want this box to do anything but Bind ie no samba. So how do I generate this dns.keytab file? The only other doc I found was a Red Hat doc and it uses a Red Hat tool to build this file so that was not helpful either.

If you have kerberos installed you can use ktutil to generate a keytab file.

---

