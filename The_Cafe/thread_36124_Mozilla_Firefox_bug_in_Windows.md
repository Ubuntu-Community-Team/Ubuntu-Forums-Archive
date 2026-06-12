---
title: "Mozilla Firefox bug in Windows?"
date: 2005-05-21
forum: The Cafe
---

### Post by jiyuu0 on 2005-05-21
Internet Explorer
[img]http://myosc.org/jiyuu0/ie.jpg[/img] 

Mozilla Firefox in Windows
[img]http://myosc.org/jiyuu0/firefox.jpg[/img] 

The contents in the boxes are not shown in Firefox Windows. But if I tried the same in Internet Explorer and Firefox Linux, seems fine.

Is this bug?

---

### Post by kassetra on 2005-05-22
[QUOTE=jiyuu0] 

The contents in the boxes are not shown in Firefox Windows. But if I tried the same in Internet Explorer and Firefox Linux, seems fine.

Is this bug?[/QUOTE]

Maybe, but most likely it's a css issue...  What is the code you are using to markup the text in the box?  Does the text in the box have any css applied to it?  

If your pages are styled with css sheets, it's very possible that IE is rendering it incorrectly and Firefox is rendering it correctly - which accounts for the discrepancy in the two images...

---

### Post by jiyuu0 on 2005-05-22
[QUOTE=kassetra]Maybe, but most likely it's a css issue...  What is the code you are using to markup the text in the box?  Does the text in the box have any css applied to it?  

If your pages are styled with css sheets, it's very possible that IE is rendering it incorrectly and Firefox is rendering it correctly - which accounts for the discrepancy in the two images...[/QUOTE]

in the text box... i don't think there are any css
the content of the text boxes are in <pre></pre>

the thing is... why is firefox linux showing correctly but not firefox windows? IE is always correct :(

have tried on 1.0.4 (latest version of firefox)

---

### Post by jiyuu0 on 2005-05-22
reported to bugzilla

[https://bugzilla.mozilla.org/show_bug.cgi?id=295087](https://bugzilla.mozilla.org/show_bug.cgi?id=295087)

---

### Post by eBopBob on 2005-05-22
Hmm... I've just tried that and it works for me perfectly in Windows. I've tried it in both Opera and Firefox, and I don't have problems in either browser. :shock:

---

### Post by jiyuu0 on 2005-05-22
[QUOTE=eBopBob]Hmm... I've just tried that and it works for me perfectly in Windows. I've tried it in both Opera and Firefox, and I don't have problems in either browser. :shock:[/QUOTE]

that's weird... i've tested on 2 windows machine and the firefox seems to give me prob :(

---

