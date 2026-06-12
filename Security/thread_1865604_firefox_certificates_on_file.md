---
title: "firefox certificates on file"
date: 2011-10-20
forum: Security
---

### Post by max1e6 on 2011-10-20
This has a Ubuntu Security spin but really this belongs in a Mozilla forum. I tried this but only questions like "how do I close my browser" get answered. I assume that my question is stupid too, but I cannot find an answer anywhere.

I have several installations of Firefox 7.0.1 on machines running Ubuntu (Lynx & Natty). In each, in a fresh profile, I have entries in “Preferences -> Advanced -> View Certificates -> Servers.” This tab is headed with “You have certificates on file that identify these servers.” Examples(yahoo.com "global trustee” and “kuix.de”). I assume these are fakes. I am guessing that Mozilla put these there deliberately and flagged them as untrusted. But, I do not know this as a fact.

Is my assumption correct? Do these certificates belong there?

---

### Post by lovinglinux on 2011-10-20
Those come by default. I suppose they are there so you can't add exceptions.

Whenever you access a https site, which has a certificate that cannot be authenticated because the authority is missing in Firefox, you can add an exception, to tell the browser that you trust it. I suppose those entries prevent you from adding exceptions for the sites listed there.

---

### Post by max1e6 on 2011-10-21
Thanks,

That's what I thought. I hope there will be more detailed info about the server tab on the Mozilla site soon. 

The radio buttons on the "servers" tab under "edit trust" are a bit buggy. If you click it they start with the radio for "Untrusted" selected. If you leave "untrusted" selected at click ok, it changes it to trusted when you reopen it. A word of warning for the unsuspecting, always click "cancel" if you want the radio button to stay on "Untrusted."

---

