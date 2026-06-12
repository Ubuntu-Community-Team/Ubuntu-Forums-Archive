---
title: "Adobe Air Security"
date: 2009-03-03
forum: Security
---

### Post by utherpendragonfly on 2009-03-03
Hi. I read an article about Adobe Air in Linux Journal and have looked around on the web and decided to install it. Installation was pretty easy, and there are lots of apps that now work with this version (1.5 B) in Linux. I think the concept is great to have apps that run on all platforms.
So I'm checking out apps to install and each one says that it has UNRESTRICTED access to the files on my computer & the internet.
Now I've only been using Linux (Ubuntu, Mint) for a few months now, and Macs before that, but this does not sound like a very good idea to me. But nowhere else does anyone seem to bring this up, like in the Linux Journal article, etc.
Does anyone have advice on this?
See screen shot.

---

### Post by utherpendragonfly on 2009-03-03
OK, I came across this from an InfoWorld product review, but I don't know enough to know if this quells my concerns:

...although security is thoughtfully addressed, it too could go further. First the good news. Local storage is protected by 128-bit encryption. AIR apps can be digitally signed and verified at runtime (via VeriSign or Thawte certificates). Administrators can control (via OS registry key) which AIR apps may be installed on a local system (trusted source only, for example, or none at all), and whether they can be updated automatically or uninstalled. And because AIR apps are treated as native, personal firewalls can examine and block AIR applications on an individual basis (versus merely identifying the AIR runtime).

However, given the level of potential exposure – AIR can write to any location on the hard disk and gain immediate network access – I would like to see Adobe tighten the controls over system access. Although self-signed apps alert users with an "unknown signature" warning, these unverifiable apps, if installed, gain the same permissions and unfettered access to the underlying OS as verified apps.

Because AIR is essentially a proxy, Adobe could implement ways to control, say, whether a cookie may be written outside the local directory, or when an existing file may be overwritten. Let the user decide what level of control to apply, but we could use something better than the existing open door policy. I hope Adobe will see fit in a future version to allow users to fine-tune permissions for each app during install.

Adobe does offer best-practice guidelines for developers. Nevertheless, I submit that many Web developers lack the technical savvy to effectively safeguard security. It's only a matter of time before some clever ne'er-do-wells begin exploiting remote data sources through local access vulnerabilities unknowingly left open to attack.

That said, AIR does fortify against malicious code injections. The two-level sandbox framework, which restricts the access of untrusted application routines to AIR's APIs, does help protect developers from themselves...

So far 4 of 4 apps I've started to install say " Publisher Identity: UNKNOWN". Does that mean it would not be a good idea to install?

---

### Post by bodhi.zazen on 2009-03-03
Not sure what you are asking and I do not think "unrestricted access" is accurate.

Permissions will always be a first line of defense and will restrict applications access to system files, alt least write access, unless you are running as root.

In terms of "restrictions" I think you should look at apparmor on Ubuntu or selinux. 

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by utherpendragonfly on 2009-03-03
I'll have to check out your info about apparmor.
I was just confused because it states "Unrestricted Access" in the installer. Knowing just about nothing of programming, that seemed like an undesirable thing. 
But as long as I don't run as root, which I certainly wouldn't, I should be safe running software from a stranger that by Adobe's definition can have unrestricted access to my files?

---

### Post by utherpendragonfly on 2009-03-03
I'm assuming they mean "unrestricted" in terms of what my permissions will allow.
Sorry if I sound a bit paranoid, I'm generally not. Thanks! I think that answers my concerns.

---

### Post by bodhi.zazen on 2009-03-03
Well, the "rule" is , do not install applications from untrusted sources.

As much as possible , stay with the Ubuntu repositories. Sure there are 3rd party applications, but take care that you only install apps from trusted sites and check the md5sum on the tar balls.

The reason is that applications are installed as root (sudo apt-get install foo / sudo make install) and so during the installation process there is indeed unrestricted access to the system (and this is of course 'normal").

See the security sticky as well as "Social engineering".

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

apt and the repositories have internal security and, IMO, the Adobe Air Security does not add much to the tools in place :

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

