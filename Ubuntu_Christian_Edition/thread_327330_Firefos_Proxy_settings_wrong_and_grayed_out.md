---
title: "Firefos Proxy settings wrong and grayed out"
date: 2006-12-29
forum: Ubuntu Christian Edition
---

### Post by chaplanger on 2006-12-29
Firefox will not connect to the Internet. Mozilla works fine -- difference is in the Proxy settings. Firefox page for Proxy settings has all choices grayed out and has checked "Manual Proxy configuration" and added an HTTP address with a 4 digit port number. This occurred after updating to Ubuntu Edgy CE -- prior to this there was no problem with Firefox. As I stated, Mozilla works fine.

Below is the error message:
The proxy server is refusing connections

Firefox is configured to use a proxy server that is refusing connections.

* Check the proxy settings to make sure that they are correct.

* Contact your network administrator to make sure the proxy server is
working

---------------------------
Any ideas on correcting this will be appreciated.

---

### Post by mhancoc7 on 2006-12-29
> **chaplanger said:**
> Firefox will not connect to the Internet. Mozilla works fine -- difference is in the Proxy settings. Firefox page for Proxy settings has all choices greyed out and has checkec "Manual Proxy configuration" and added an HTTP address with a 4 digit port number. This occurred after updating to Ubuntu Edgy CE -- prior to this ther was no problem with Firefox. As I stated, Mozilla works fine.

Below is the error messge:
The proxy server is refusing connections

Firefox is configured to use a proxy server that is refusing connections.

* Check the proxy settings to make sure that they are correct.

* Contact your network administrator to make sure the proxy server is
workin

---------------------------
Any ideas on correcting this will be appreciated.


What are the proxy settings? They are greyed out because Ubuntu CE locks the proxy settings in Firefox to make it more difficult to get around the filtering. You can unlock the settings with the Dansguardian GUI (System>Administration>Configure Parental Controls)

Hope that helps, Jereme

---

### Post by chaplanger on 2006-12-29
> **mhancoc7 said:**
> What are the proxy settings? They are greyed out because Ubuntu CE locks the proxy settings in Firefox to make it more difficult to get around the filtering. You can unlock the settings with the Dansguardian GUI (System>Administration>Configure Parental Controls)

Hope that helps, Jereme

This would help. . .if "Configure Parental Controls" appeared in System>Admin -- but I can't find it anywhere.  Is my installation of CE corrupt?  What do I do now?
Help!  ](*,)

---

### Post by mhancoc7 on 2006-12-29
Ok, let me ask a few questions:

Did you run the convert_me script for Edgy?

Did you run it on Ubuntu Edgy or another flavor (ie Kubuntu)?

If you ran the convert_me script for Edgy on Ubuntu Edgy then you should probably try running the script again. It may have missed a step for some reason.

God Bless, Jereme

---

### Post by chaplanger on 2006-12-29
> **mhancoc7 said:**
> Ok, let me ask a few questions:

Did you run the convert_me script for Edgy?

Did you run it on Ubuntu Edgy or another flavor (ie Kubuntu)?

If you ran the convert_me script for Edgy on Ubuntu Edgy then you should probably try running the script again. It may have missed a step for some reason.

God Bless, Jereme

WOW! Running the Script again resolved the issue completely.  Evidently I did not let the conversion process run long enough originally .  Having come from a WIN world -- (Guess I expected to see either an hourglass or something hinting that a process was underway) and rebooted too soon the first time.

:D

---

### Post by mhancoc7 on 2006-12-29
Great, glad to see that you have it working. I hope you enjoy Ubuntu CE.

God Bless, Jereme

---

