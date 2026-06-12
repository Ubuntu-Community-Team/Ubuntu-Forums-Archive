---
title: "How to access U1 from behind a proxy"
date: 2012-09-17
forum: Ubuntu One (CLOSED)
---

### Post by erasmusp on 2012-09-17
I am currently using DropBox quite effectively but would like to switch to Ubuntu One. However I cannot find any setting in U1 which allows me to access the Internet through a proxy server (unlike DropBox). Am I missing something?

Regards,
Phill

---

### Post by erasmusp on 2012-09-19
There are obviously no one here that could help me with this request - could someone perhaps guide me into where else I could post this question? 

Regards,
Phill

---

### Post by mparillo on 2012-09-19
> **erasmusp said:**
> There are obviously no one here that could help me with this request - could someone perhaps guide me into where else I could post this question? 

Regards,
Phill

You could try to report a [Bug on Launchpad]("https://bugs.launchpad.net/ubuntuone-client/"). Or you can ask a [Question on Launchpad]("https://answers.launchpad.net/ubuntu/+source/ubuntuone-client").

Or you could see if this [FAQ]("https://answers.launchpad.net/ubuntu/+faq/1763") helps.

Or you could try to install the Ubuntu One Proxy [Package]("http://www.ubuntuupdates.org/package/core/precise/main/base/ubuntuone-client-proxy").

Please post any success here.

---

### Post by erasmusp on 2012-09-20
Thanx for responding mparillo but no luck. The FAQ only tells me how to setup Gnome and Firefox's proxy settings, not Ubuntu One's settings. The Ubuntu One Proxy Package is only for the Ubuntu version of U1 not the Windows version (It is at work using my Win7 laptop where I am stuck behind a proxy server)

I suppose I will have to report a bug....

Regards,
Phill

---

### Post by mparillo on 2012-09-20
> **erasmusp said:**
>  (It is at work using my Win7 laptop where I am stuck behind a proxy server)

If you are on a Win7 laptop at work, can you try loading Ubuntu in a Virtual Machine? Maybe you can sync that way, as VMWare Player will simply pass the network packets through to Win7. If that works, then I believe there is a way to share folders between your host and client machines.

---

