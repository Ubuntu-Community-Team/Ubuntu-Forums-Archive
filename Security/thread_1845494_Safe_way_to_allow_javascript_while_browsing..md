---
title: "Safe way to allow javascript while browsing."
date: 2011-09-17
forum: Security
---

### Post by arroy_0209 on 2011-09-17
I use firefox with noscript addon. Javascript is not allowed by default. However many websites make use of javascript for full functionality, though this is a well-known security threat. In case I am forced to allow javascript for some site, how can I do that in a safe manner?

---

### Post by Lars Noodén on 2011-09-17
> **arroy_0209 said:**
> ...how can I do that in a safe manner?

You can't really.  That's part of the conundrum.

---

### Post by arroy_0209 on 2011-09-17
some people suggest using "sandboxie". Does anybody have any experience with that? I am sot sure if this is meant for ubuntu.

---

### Post by Lars Noodén on 2011-09-17
AppArmor is under development but can do set some application level controls.  You won't stop the tabs from accessing each other that way but you can prevent the browser from messing with the rest of the system.

---

### Post by vasa1 on 2011-09-17
> **arroy_0209 said:**
> some people suggest using "sandboxie". Does anybody have any experience with that? I am sot sure if this is meant for ubuntu.

SandboxIE is excellent for MS Windows! I don't think there's a **simple** equivalent in Linux.

---

### Post by Paddy Landau on 2011-09-20
I have browsed the Internet for years, on Windows until nearly three years ago, and since then on Linux, *never* disabling Javascript.

To the best of my knowledge, I've never had a security problem as a result of Javascript.

---

### Post by dave01945 on 2011-09-20
i've never used **noscript** either and never had any problems because of it

---

### Post by SparTacux on 2011-09-20
> **Paddy Landau said:**
> I have browsed the Internet for years, on Windows until nearly three years ago, and since then on Linux, *never* disabling Javascript.

To the best of my knowledge, I've never had a security problem as a result of Javascript.

 :-) :-) :-) really made me smile that one. Some guys in the security and intelligence business love to hear statements like that ;-)

---

### Post by Dangertux on 2011-09-20
> **SparTacux said:**
> :-) :-) :-) really made me smile that one. Some guys in the security and intelligence business love to hear statements like that ;-)

+1

Ok OT : JavaScript and NoScript/NotScripts. There are a couple of things to keep in mind here. The primary use for NoScript is going to be do stop malicious javascript from running. A secondary function of the application is to prevent things like Cross Site Scripting and Cross Site Request Forgery.

To understand why NoScript will still protect you even if you are on a site for which you allow scripts to run requires a little understanding of the [same origin policy.]("http://en.wikipedia.org/wiki/Same_origin_policy") However, clever security researchers came up with a few ways to circumvent the same origin policy via XSS and CSRF. That being said applications go a step further then the browser. If vulnerable code is present and an XSS vulnerability is exploited NoScript will still block it even if the code is being run on a trusted site. The reason being the site that the code was initiated on will call external code, while the original site was trusted the new one will not be. 

So it's still a good idea to run NoScript, and that is how it protects you even if you're allowing javascript from a particular site. Also NoScript does alot more than just blocking javascript and flash. It can stop NAT pinning attacks, and some other DNS related web based attacks.

---

### Post by OpSecShellshock on 2011-09-20
To be clearer, javascript in and of itself is not a security problem. It's just the bad ones you have to worry about, but you don't really know they're bad until after they've run. Still, it's pretty low risk on a Linux desktop, because the script itself is just a starting point, and what comes after tends to be targeted elsewhere. The primary benefit I get from NoScript is that I am able to load the scripts and content I want to load, and not anything else. Makes pages load faster and I can learn more about how sites are structured. It's kind of a niche interest. Also, not every site I use really needs full functionality. All I need are the parts I'm interested in (not that I don't appreciate all the work developers do, of course).

NoScript does allow for scripts to be enabled site-by-site, which takes some work up front, but will eventually cover most sites that most people browse regularly. If you really want to do some tedious up-front work, check out an extension called RequestPolicy. Really messes with things. Fun stuff.

---

### Post by bodhi.zazen on 2011-09-20
> **Paddy Landau said:**
> I have browsed the Internet for years, on Windows until nearly three years ago, and since then on Linux, *never* disabling Javascript.

To the best of my knowledge, I've never had a security problem as a result of Javascript.

It of course varies with one's browsing habits, lol.

Firefox certainly has it's share of security vulnerabilities.

> **vasa1 said:**
> SandboxIE is excellent for MS Windows! I don't think there's a **simple** equivalent in Linux.

If you do not know , then look it up before you make claims, especially when it comes to security.

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

---

### Post by Dangertux on 2011-09-20
> **bodhi.zazen said:**
> It of course varies with one's browsing habits, lol.

Firefox certainly has it's share of security vulnerabilities.



If you do not know , then look it up before you make claims, especially when it comes to security.

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

It might be important to note here that SELinux and Apparmor (which ships with Ubuntu by default) do NOT play well together, so make sure if you go enabling SELinux (which is supported by the Ubuntu kernel) that you disable Apparmor first. Bad things happen otherwise and nothing but heartache awaits :-P

Also important to note that SELinux sandboxes or otherwise do nothing for XSS/CSRF.

---

