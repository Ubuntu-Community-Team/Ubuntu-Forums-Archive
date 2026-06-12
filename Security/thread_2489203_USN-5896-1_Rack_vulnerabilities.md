---
title: "USN-5896-1: Rack vulnerabilities"
date: 2023-07-21
forum: Security
---

### Post by dani32 on 2023-07-21
Hi Forum Mates,

I am trying to find more information regarding the following vulnerability:  

[https://ubuntu.com/security/notices/USN-5896-1](https://ubuntu.com/security/notices/USN-5896-1)

I have the following package installed:

[COLOR=#33363F][FONT=Courier]Installed package : ruby-rack_2.0.7-2ubuntu0.1    Fixed package     : ruby-rack_2.0.7-2ubuntu0.1+esm2

[/FONT][/COLOR]Does anyone know what the difference is between both packages outside of needing a ESM subscription? Was something additionally patched in the ESM version of the package?

Thanks!

---

### Post by ian-weisser on 2023-07-21
Security patches rarely do anything "additional".

The only difference should be the two mitigated CVEs. The USB page links to CVE pages, each of which in turn links to the upstream patches if you want to audit them.

What leads you to believe that there might be "additional?"

---

### Post by dani32 on 2023-07-21
Thanks for the response. Let me phrase my question differently - What is the difference between the two packages> **ruby-rack_2.0.7-2ubuntu0.1 **vs.** ruby-rack_2.0.7-2ubuntu0.1+esm2**

Is there a page where I can see compare what has been patched.

---

### Post by ian-weisser on 2023-07-21
Sure: Use the links to those two patches (one link on each CVE page). That's what was patched.

The patches are text files. Open them in a text editor or a web browser.

Example: [https://github.com/rack/rack/commit/d286516cbd58fbb2ad6944ce9040e9ba96d9371a](https://github.com/rack/rack/commit/d286516cbd58fbb2ad6944ce9040e9ba96d9371a)

If you need more context, then see the source code for the whole package: [https://github.com/rack/rack](https://github.com/rack/rack)

---

