---
title: "WebSVN + enscript"
date: 2012-01-23
forum: Server Platforms
---

### Post by lviggiani on 2012-01-23
Hi Everybody,
I've recently installed websvn + enscript package on Ubuntu server 10.04LTS to view my svn repo via apache2.
Everything works fine except for a problem in syntax highlighting while viewing source files on line.

For example, while viewing a .java source file, all *String* occurences are shown like this:

```
public BirdCageAssetException(1.5.0/docs/api/java/lang/String.html">String sms){ 
```

...instead of just "[COLOR="Blue"]String[/COLOR]" it prints out "[COLOR="blue"](1.5.0/docs/api/java/lang/String.html">String[/COLOR]"
and the hyperlink is also wrong "http://java.sun.com/j2se/%3Cspan%20style="

To me it looks like an HTML formatting issue.
Is it actually a bug or is a configuration problem?
Thanks in advance for any help!
Cheers

---

### Post by lviggiani on 2012-01-23
Ok problem solved by installing latest websvn 2.3.3
I don't know what exactly the thing was, but with websvn 2.3.0 and source code in utf-8 the formatting was wrong.

> **lviggiani said:**
> Hi Everybody,
I've recently installed websvn + enscript package on Ubuntu server 10.04LTS to view my svn repo via apache2.
Everything works fine except for a problem in syntax highlighting while viewing source files on line.

For example, while viewing a .java source file, all *String* occurences are shown like this:

```
public BirdCageAssetException(1.5.0/docs/api/java/lang/String.html">String sms){ 
```

...instead of just "[COLOR="Blue"]String[/COLOR]" it prints out "[COLOR="blue"](1.5.0/docs/api/java/lang/String.html">String[/COLOR]"
and the hyperlink is also wrong "http://java.sun.com/j2se/%3Cspan%20style="

To me it looks like an HTML formatting issue.
Is it actually a bug or is a configuration problem?
Thanks in advance for any help!
Cheers

---

