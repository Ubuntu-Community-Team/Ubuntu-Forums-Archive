---
title: "Configure hostfingerprints Mercurial option on Ubuntu 12.04"
date: 2012-09-18
forum: Server Platforms
---

### Post by razor7 on 2012-09-18
I'm having a really hard time configuring [hostfingerprints] option on mercurial 2.3.1

On my /etc/mercurial/hgrc file I have this, after following the answer of this question [http://stackoverflow.com/questions/5164804/get-certificate-fingerprint-of-https-server-from-command-line/5165073#5165073](http://stackoverflow.com/questions/5164804/get-certificate-fingerprint-of-https-server-from-command-line/5165073#5165073)

> [hostfingerprints]
it.mgscreativa.com.ar = XX:XX:A1:28:49:24:21:1D:7E:9E:2B:E9:E7:CD:1C:E0:40:A3:XX:XX


But after trying to clone a repository from that server, I get

> SSL: Server certificate verify failed

I really don't know what I'm doing wrong.

Please advise.

PS: I have a StartCom Free class 1 certificate for mgscreativa.com.ar and it.mgscreativa.com.ar and is correctly installed because accessing thoose domeins through HTTPS Mozilla recognices the certificate.

---

