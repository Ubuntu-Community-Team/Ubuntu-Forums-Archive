---
title: "HTML not rendering in perl"
date: 2009-12-09
forum: Server Platforms
---

### Post by cablejimmy on 2009-12-09
Okay, so I have a simple cgi script that's supposed to be running in perl. When I open it up in Internet Explorer, it works perfectly, but when I open it up in Firefox, the html does not render, and instead I am just shown the code, which looks like this:```
#!/usr/bin/perl

# hello.pl -- my first perl script!

print "Content-type: text/html\n\n";

print <<"EOF";
<HTML>

<HEAD>
<TITLE>Hello, world!</TITLE>
</HEAD>

<BODY>
<H1>Hello, world!</H1>
</BODY>

</HTML>
EOF

```

How do I get the page to render correctly in Firefox?

---

