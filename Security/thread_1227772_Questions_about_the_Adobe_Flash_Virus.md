---
title: "Questions about the Adobe Flash Virus"
date: 2009-07-31
forum: Security
---

### Post by kwabena39 on 2009-07-31
Hello,

I have Ubuntu 8.04, 64 bit version, and I read that this new adobe virus can infect and disable ALL PC's Windows, Mac, AND Linux.


I am concerned about my PC being infected by the new Flash Adobe vulnerability.  When I clicked on one website, my browser froze up for a minute and I got a message saying that Flash was running scripts, and that my computer could become unresponsive.

I never had this problem with Linux before.

How do I know or tell whether my computer has been infected?  Is there some time bomb waiting to go off that will completely disable it?  I heard that this virus is really bad, and is very rare because it can affect every platform.

So we Linux users have to worry about viruses now...  The hackers have caught up to us.:confused::(

So I guess I should start thinking about anti-virus software.

What is the best anti virus software for Ubuntu 8.04, 64 bit?

Thanks

Your help is greatly appreciated

---

### Post by cariboo on 2009-07-31
The exploit affects Adobe Flash Player 9.0.45.0 and earlier, 8.0.34.0 and earlier, and 7.0.69.0 and earlier.

Just make sure you are running an up-to-date version of flash and you should be ok. 

To find out if you are running an affected version type:

```
about:plugins
```

in firefoxes address bar.

---

### Post by LimCore on 2009-07-31
What exactly is this virus infecting on Ubuntu? Some ~/.adobe/ files with scripting, or ~/.mozilla firefox scripting?

How to clean computer after such problem (apart from full reinstall etc)

---

### Post by bobince on 2009-07-31
> **kwabena39 said:**
> When I clicked on one website, my browser froze up for a minute and I got a message saying that Flash was running scripts, and that my computer could become unresponsive.

That's not necessarily an attack; any complicated scripting can have that effect. Whilst one potential cause of unresponsive scripting would be an attempt to heap-spray in connection with an exploit, it's far from the most likely one.

Even if you have the latest version of Flash Player, which is not vulnerable to the exploit, a script heap-spraying will still cause the unresponsiveness. So the message is not in any way diagnostic of a compromise. I wouldn't worry unless the message was followed by a browser crash. (And even then, it's uncertain it was a deliberate exploit; Flash isn't always the most stable of plugins...)

> I heard that this virus is really bad, and is very rare because it can affect every platform.

There's not one specific virus, it's an exploit through which arbitrary code can potentially execute on any platform.

But that code has to be crafted for each platform it wants to target; shellcode injected for Windows won't work on Linux and vice-versa. Whilst you could theoretically code a cross-platform exploit, it would be quite tricky and in reality no-one does it.

This situation is not at all rare, it's normal for cross-platform applications; exploitable bugs in eg. Firefox are routinely issues on all platforms. Exploitable bugs in plugins are also nothing new, which is why you should run as few plugins as possible and make sure each is kept up-to-date (which Ubuntu's Update Manager will do for you for software from the repos). The FlashBlock add-on for Firefox is also useful, allowing you to expose Flash only to sites you trust.

The vast majority of the current browser/plugin exploits out there are aimed at Windows and won't work on Linux, where they'll only cause a browser crash. This is partly because of Windows's greater popularity and partly due to technical and policy differences that make Linux a bit more work to attack.

At the moment it is very unlikely you  encountered an exploit targeting Linux. If, somehow, you did get compromised, it would initially only affect your user. So unless you deliberately allowed it to escalate privileges to root, your install itself is safe and you could just create a new user.

---

