---
title: "IE explorer security"
date: 2006-10-25
forum: Windows
---

### Post by styven on 2006-10-25
Hi all,

I have just had to register with vodaphone to use a particular on line service, but could not complete registration it turns out because i was using firefox and this could only be done in IE, a bit challenging as I only use firefox in Ubuntu.
I asked why this was the case and the chap said that the "security was too high for firefox".
I don't understand what he means really, and I am under the impression that when it comes to security, using IE is by no means the best way forward.

Can anyone shed any light on this?

Steve.

---

### Post by spin2cool on 2006-10-25
It's an excuse many companies use to avoid having to develop for multiple platforms.  Truth be told, the security in firefox is generally better.  

There are instructions around for running Internet Explorer through WINE.  It's easy if you dual boot, and a little harder if you don't, but it can be done.

---

### Post by Dr. C on 2006-10-25
Then there are the options of 

1) Finding a competitor that does not require the purchase of a Windows license in order to use thier product.
2) Investigate if the requirement to obtain Windows license is in violation of tied selling laws in one's country and if so file a complaint against the company with the appropiate authority for violation of such laws. 

My understanding is that to use IE in WINE one has to purchase a license for Windows.

---

### Post by 3rdalbum on 2006-10-27
If you are being kept out of the site by some browser detection, try the User Agent Switcher extension. Or, of course, use IEs4Wine to install IE 6.

If that doesn't work, then take your business elsewhere. You wouldn't buy hardware that doesn't work with Linux, so why buy a service that is incompatible?

---

### Post by Sunnz on 2006-10-28
What is the web site? Maybe there is a way around it?

---

### Post by satori on 2006-10-31
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-871375-1";
urchinTracker();
</script>

---

### Post by 3rdalbum on 2006-11-01
You like Javascript? Try this one:

```
<script>

for(x in document.write){document.write(x);}

location.href = "http://www.google.com";

</script>
```

Try it on Firefox first, then on IE.

---

