---
title: "Remove this string from all files"
date: 2010-10-12
forum: Security
---

### Post by OOzypal on 2010-10-12
Hello 

How can I remove this string from all files. I am not sure how it did get there

[PHP]<?php /**/eval(base64_decode('')); ?>[/PHP]


I tried this but It did not work

[PHP]find ./ -iname \*.php\* -exec sed -i 's/<?php /**/eval(base64_decode('')); ?> //g' {} \;[/PHP]

---

### Post by Barriehie on 2010-10-12
> **OOzypal said:**
> Hello 

How can I remove this string from all files. I am not sure how it did get there

[PHP]<?php /**/eval(base64_decode('')); ?>[/PHP]


I tried this but It did not work

[PHP]find ./ -iname \*.php\* -exec sed -i 's/<?php /**/eval(base64_decode('')); ?> //g' {} \;[/PHP]

Hey, I'm more familiar with gawk but do you have to escape the '/'s?  like \/ in sed???

---

### Post by OOzypal on 2010-10-12
I am not sure.

But that is ok, can you help remove this string using gawk?

---

### Post by OpSecShellshock on 2010-10-12
Are we talking about a web server? Because the line you're wanting to delete from files looks very similar to a line that has gotten added to a large number of compromised sites in the past few months. If that's what it is, then removing it alone won't do much good, I'm afraid. There's really high recidivism on these kinds of events.

[See here.]("http://blog.sucuri.net/2010/10/more-attacks-hilary-kneber-and-meqashopperinfo-com.html")

That's just one example of many on that site. They have removal tools as well as an email address for site owners looking for support, but I don't know if there's a charge.

Otherwise, just look around the site at the related posts.

---

### Post by Barriehie on 2010-10-12
> **OOzypal said:**
> I am not sure.

But that is ok, can you help remove this string using gawk?

This should work:

```

gawk '{ if($0 !~ /^<?php.*?>$/) {print $0} }' ***inputFile*** > ***outputFile***
```

I'ld make a copy of a file first and try it out/check it.  Should be good though.  :)

HTH,
Barrie

---

