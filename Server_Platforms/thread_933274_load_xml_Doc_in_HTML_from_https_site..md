---
title: "load xml Doc in HTML from https site."
date: 2008-09-29
forum: Server Platforms
---

### Post by randomnote1 on 2008-09-29
I've searched Google high and low and can't seem to solve this problem.  I am attempting to pull an RSS feed from an intranet site to post on my department's web page.  Unfortunately, it isn't working because it won't accept or ignore the certificate.  I was able to download the file using

```
wget --no-check-certificate https://file.xml
```

and my Javascript is able to parse the file.

This is the code I'm using to pull the XML doc:

```
var xmlDoc=null;
if (window.ActiveXObject)
{// code for IE
xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
}
else if (document.implementation.createDocument)
{// code for Mozilla, Firefox, Opera, etc.
xmlDoc=document.implementation.createDocument("","",null);
}
else
{
alert('Your browser cannot handle this script');
}
if (xmlDoc!=null)
{
xmlDoc.async=false;
xmlDoc.load("https://file.xml");
```

Does anybody know how to make xmlDoc.load ignore or accept a certificate?

---

