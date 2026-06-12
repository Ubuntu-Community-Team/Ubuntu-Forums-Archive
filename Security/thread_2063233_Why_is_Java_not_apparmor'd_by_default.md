---
title: "Why is Java not apparmor'd by default?"
date: 2012-09-26
forum: Security
---

### Post by Hungry Man on 2012-09-26
There are a few services running apparmor by default. Why aren't there enforced profiles for Java by default? The profile for Firefox is there but it's only for Firefox (why?) and it's on complain by default.

So would it be the apparmor maintainers who should be talked to about this?

---

### Post by rookcifer on 2012-09-26
> **Hungry Man said:**
> There are a few services running apparmor by default. Why aren't there enforced profiles for Java by default? The profile for Firefox is there but it's only for Firefox (why?) and it's on complain by default.

The default firefox profile *does* confine Java.  From the profile itself:

```
# Addons
  #include <abstractions/ubuntu-browsers.d/firefox>
```

If you follow that abstraction it leads to a file named "java."  If you look at that file:

 ```
profile browser_openjdk {
```

As you can see it profiles Java for the browser (both OpenJDK and Oracle Java).  

BTW, I tested one of these Java exploits against the AppArmor'ed Firefox and the exploit failed.  When I turned off AA, it succeeded.

EDIT: If you are talking about confining the JVM itself, then no it's not.  However, since the browser is the #1 attack vector for Java exploits on a desktop machine, then it makes sense to confine Java for the browser only.  That means Java needs to be confined on a per application basis.

---

### Post by Hungry Man on 2012-09-26
Yes, I know the default Firefox profile does. Like I said, the profile is there but only for Firefox.

There's no separate profile for the JVM. There's no profile for Chromium or Opera by default.

---

### Post by rookcifer on 2012-09-27
> **Hungry Man said:**
> Yes, I know the default Firefox profile does. Like I said, the profile is there but only for Firefox.

Probably because Firefox is the default browser in Ubuntu.

> There's no separate profile for the JVM. There's no profile for Chromium or Opera by default.

Profiling the JVM and make it work with every possible configuration would be tough.  

As for Chromium, there is indeed a default profile for it.  You may have to install it though. 

```
sudo apt-get install apparmor-profiles
```

---

### Post by Hungry Man on 2012-09-27
> Probably because Firefox is the default browser in Ubuntu.

Right. But it's also not enforced by default when it really should be.

> Profiling the JVM and make it work with every possible configuration would be tough. 

Outside of for developers (who would be competent enough to disable it) it shouldn't be.

---

### Post by Soul-Sing on 2012-09-28
> There's no separate profile for the JVM. There's no profile for Chromium or Opera by default.

on lubuntu chromium is....

The question is imho, do you need java.
otherwise use the quickjava add-on for firefox.

---

### Post by rookcifer on 2012-09-28
> **Soul-Sing said:**
> .

on lubuntu chromium is....

The question is imho, do you need java.
otherwise use the quickjava add-on for firefox.

Some people do need Java in the browser.  Unfortunately some sites require it.  Some people say their banking site requires it (fortunately mine doesn't).

I think one solution would be if the Chrome developers would implement the Java plugin into their sandbox like they do with Flash.  Right now Chrome/Chromium does nothing to protect Java.

---

### Post by Hungry Man on 2012-09-28
I don't know what Chrome does on Linux. On Windows it limits IPC to Java.

---

### Post by WhiteHatGuy on 2012-09-30
> **Hungry Man said:**
> There are a few services running apparmor by default. Why aren't there enforced profiles for Java by default? The profile for Firefox is there but it's only for Firefox (why?) and it's on complain by default.

So would it be the apparmor maintainers who should be talked to about this?








Its a great idea Hungry Man, this will be like a request for ubuntu developers, to add this by default, this will help a lot the new users who dont know how to use apparmor.

---

### Post by Soul-Sing on 2012-10-01
apparmor is a application based protocol, with profiles for many apps. so every application which uses java should be limited/restricted by a apparmor profile afaik. 
The only way to restrict java in a general way, is to disable it.

---

### Post by Hungry Man on 2012-10-01
Java is a runtime environment. It takes class files, translates them to byte code, and then interprets the byte code into native code. You can restrict the JRE, which will in turn restrict an applications access to the system through the JRE.

Most of the exploits that make use of Java vulnerabilities are sandbox escapes. Normally only signed code gets the right to run without prompt and with higher rights - the sandbox escapes bypass this allowing unsigned code to run. Because of this modern mitigation techniques like ASLR, DEP, etc are largely irrelevant (along with Java's JIT'd code having to stay executable).

That's why there should be a focus on getting an apparmor profile for it deployed by default. Sandboxing and patching are pretty much the only ways to protect yourself once you've hit an exploit page.

The one issue here is that Java as a web plugin requires different rights than Java as a desktop application. The profile has to be reworked and web browsers would probably have to call Child Java profiles instead. For developers the profile would have to be disabled but that's fine they can figure that out.

---

### Post by rookcifer on 2012-10-01
It's easier just to create profiles for individual apps that use Java.

---

