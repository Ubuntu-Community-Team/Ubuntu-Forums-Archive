---
title: "Install squid from repository with compile parameters"
date: 2011-06-08
forum: Server Platforms
---

### Post by ene_dene on 2011-06-08
I want Squid3 to switch browser user-agent of a user connecting to some site. For example from:
"Mozilla/5.0 (Windows; U; Windows NT 6.1; ro; rv:1.9.1.19) Gecko/20110420 Firefox/3.5.19"
to
"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.91 Safari/534.30"

For that I need to put "request_header_replace" directive in squid.conf file.
However, for that directive you need to compile squid3 with this parameter:
--enable-http-violations parameter

Is there a way to install it the usual way with apt-get/aptitude but to use this parameter?

If not, could you explain to me how to compile squid3 with that parameter?

---

### Post by brettg on 2011-06-08
No, you can't do that using the repositories (packages are all precompiled)

You need to download the source and manually compile. There should be instructions for doing that in the source package.

---

### Post by ene_dene on 2011-06-08
> **brettg said:**
> No, you can't do that using the repositories (packages are all precompiled)

You need to download the source and manually compile. There should be instructions for doing that in the source package.

Ok, thank you.

---

