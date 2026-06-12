---
title: "Does dated java pose major security risks?"
date: 2012-05-08
forum: Security
---

### Post by OpenSourceRules on 2012-05-08
Someone on Linux Mint forum suggests that, and dated java makes browsing a little tricky.

---

### Post by billyseth on 2012-05-08
wasn't the recent mac osx virus a java issue that Apple didn't patch  after Oracle issued a patch?

---

### Post by OpSecShellshock on 2012-05-09
Yes, out of date Java is currently the most frequently exploited software by the most widely used kits.

---

### Post by Soul-Sing on 2012-05-09
indeed RequestPolicy is a nice rel. new firefox add-on to disable/manage all kinds of "troubleware" as java.

---

### Post by Hungry Man on 2012-05-09
Java on Windows is the Oracle JVM, which is statistically the most commonly exploited program. OSX also recently had nearly 700,000 infections in just a few days due to an unpatched Java vulnerability.

Ubuntu provides the OpenJDK JVM, which could potentially be more secure than the Oracle JVM. I'm not sure how they differ.

If you're using the Oracle JVM and it's out of date you're likely vulnerable to the same exploits (some of them at least) as Windows/OSX since Java, by its nature, is multiplatform (I can run the same Java code on Linux/Windows/OSX) and therefor payloads can be dropped on any system.

On Windows your options are limited. Same goes for OSX. On Ubuntu, not so much. Ubuntu lets you use Apparmor, which will sandbox your Java plugin both  preventing and restricting exploits you run across. For more info on Apparmor you can see the sticky.

---

