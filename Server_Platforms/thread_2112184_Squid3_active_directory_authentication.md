---
title: "Squid3 active directory authentication"
date: 2013-02-04
forum: Server Platforms
---

### Post by viperce on 2013-02-04
Hi,

I have a squid3 transparent proxy(on Ubuntu Server 12.04) that i would like to setup to authenticate with Windows server 2008 Active Directory.

could someone please point me in the right direction here not sure what the best 
way forward is.

thanks in advance.

---

### Post by SeijiSensei on 2013-02-04
Umm, did you already read [this](http://wiki.squid-cache.org/ConfigExamples/Authenticate/WindowsActiveDirectory)?  It's the first thing to come up in a Google search for "squid active directory".

---

### Post by viperce on 2013-02-04
Hi,

Yes I did try that and got as far as

msktutil -c -b "CN=COMPUTERS" -s HTTP/adproxy.domain.local -k /etc/squid3/PROXY.keytab --computer-name ADPROXY -k --upn HTTP/adproxy.domain.local --server server1.domain.local --verbose  --enctypes 28
Error: Unknown parameter (HTTP/adproxy.domain.local)

For help, try running msktutil --help

---

### Post by viperce on 2013-02-08
bump

---

