---
title: "Amazon.co.uk site security certificate is not trusted"
date: 2017-02-05
forum: Ubuntu Phone and Tablet
---

### Post by naomibrown on 2017-02-05
I get the following error message when I visit the amazon.co.uk site on my phone:

This site security certificate is not trusted.
This site security certificate is not trusted
You attempted to reach [https://amazon.co.uk](https://amazon.co.uk) but the server presented a security certificate which failed our security checks for an unknown reason. 

Learn more (hyperlink)

You should not proceed, especially if you have never seen this warning before for this site. 

It then gives me the option buttons: Proceed anyway or Back to safety

I don't have this problem when I use the site on my desktop computer. I've tried restarting my phone and I've tried clearing the cache on my phone then restarting it, neither of which means that the message goes away.

Any ideas?
Thanks,
Naomi

---

### Post by dtarrant on 2017-02-05
Hi Naomi,
Take a look at recent thread "browser app no longer able to display........" Seems this is a known problem that should be fixed in OTA15 by the end of the month.

---

### Post by dtarrant on 2017-02-05
Title of thread should read "browser app failing to properly display website". Link as follows:

[https://ubuntuforums.org/showthread.php?t=2349778](https://ubuntuforums.org/showthread.php?t=2349778)

---

### Post by naomibrown on 2017-02-06
Thanks! I had read that post but didn't realise that it was talking about the same problem, because no one mentioned the text I had seen directly.

Am I right in thinking that the link between the two problems is that they both use https? 

Thanks,
Naomi

---

### Post by dtarrant on 2017-02-06
I think you're right Naomi. I've just noticed that I can't access Here Maps which is an https site. These are the sites I'm having trouble with:

Ebay; Amazon; Here Maps; Outlook Web App.

Hope this problem gets fixed soon.

David
BQ M10

---

### Post by dtarrant on 2017-02-06
See this OMG Ubuntu link:

[http://www.omgubuntu.co.uk/2017/01/ubuntu-ota-15-will-let-ubuntu-phone-owners-browse-amazon](http://www.omgubuntu.co.uk/2017/01/ubuntu-ota-15-will-let-ubuntu-phone-owners-browse-amazon)

David

---

### Post by howefield on 2017-02-07
> **naomibrown said:**
> I get the following error message when I visit the amazon.co.uk site on my phone:

Looks like OTA 15 update should be done by tomorrow evening..

> Hello everyone,

We have just copied OTA-15 security-update images to all the stable channels and started the phased upgrade procedures as with every release. This should take less then a whole day and all users should see the update on their phones tomorrow at latest.

You can find all the necessary information at the usual place:  * [https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-15](https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-15)

This is a security bugfix update only, actually only including changes to oxide and the webbrowser. The next future OTAs will most likely be very similar, concentrating only on critical security issues - until ubuntu-personal enters the touch world with its snaps.

Cheers,

---

### Post by dtarrant on 2017-02-07
Deep joy! OTA15 has arrived and I can now access all the htpps websites that have been recently unavailable. Hats off to Ubuntu!

M10 Tablet

---

