---
title: "Security updates and PHP version"
date: 2011-02-04
forum: Server Platforms
---

### Post by Saorex on 2011-02-04
Hi guys. I'm 90% sure of the answer I'll receive for this question, but I'm asking it because I need to be 100% sure.

I have automatic security updates "turned on" on my Ubuntu Server. PHP 5.3.2 is installed and running with a custom C++ module compiled locally. I want to make sure that by making security updates, Ubuntu will never upgrade PHP to another version, let's say 5.3.5, That would probably force me to recompile my module. Because this is a production server, I would have to do it on the week-end and I don't feel like it. Hahaha!

Thanks for your help!

---

### Post by Thirtysixway on 2011-02-04
> **Saorex said:**
> Hi guys. I'm 90% sure of the answer I'll receive for this question, but I'm asking it because I need to be 100% sure.

I have automatic security updates "turned on" on my Ubuntu Server. PHP 5.3.2 is installed and running with a custom C++ module compiled locally. I want to make sure that by making security updates, Ubuntu will never upgrade PHP to another version, let's say 5.3.5, That would probably force me to recompile my module. Because this is a production server, I would have to do it on the week-end and I don't feel like it. Hahaha!

Thanks for your help!

The version number reported by php should always stay at 5.3.2 as long as you don't upgrade the system from say 10.04 -> 10.10. When security updates are released for php, the ubuntu team will apply a patch. So the flaws will be fixed, your version just becomes patched.

That's why if you look at the php version it will say something like PHP 5.3.2-1ubuntu4.7

---

### Post by slakkie on 2011-02-04
Have a look at pinning:

```

sudo vi /etc/apt/preferences

```
```

# Use this specific version of the hello package
Package: hello
Pin: version 2.2-2
Pin-Priority: 1001

```

[http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

But, tbh, I would never auto-update a PRD machine, you want to know when something changed and have the change approved/tested before putting it live.

---

### Post by Saorex on 2011-02-10
Thanks for the explanation Thirtysixway.

I get your point slakkie. I will have to think about this again. We're refactoring the server park right now and we might have a real test environment for the first time.

---

