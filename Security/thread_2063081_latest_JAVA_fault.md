---
title: "latest JAVA fault"
date: 2012-09-26
forum: Security
---

### Post by mike acker on 2012-09-26
an article on ArsTechnica today states in part

> Gowdiak wrote that Security Explorations successfully pulled off the  exploit on a fully patched Windows 7 32-bit computer in Firefox, Chrome,  Internet Explorer, Opera, and Safari. Although testing was limited to  Windows 7 32-bit, Gowdiak [told Computerworld]("http://blogs.computerworld.com/malware-and-vulnerabilities/21056/another-critical-java-vulnerability-puts-1-billion-users-risk")  that the flaw would be exploitable on any machine with Java 5, 6, or 7  enabled (whether it’s Windows 7 64-bit, Mac OS X, Linux, or Solaris).see [http://arstechnica.com/security/2012/09/yet-another-java-flaw-allows-complete-bypass-of-security-sandbox/](http://arstechnica.com/security/2012/09/yet-another-java-flaw-allows-complete-bypass-of-security-sandbox/)

~~~~~
I think Gowdiak is over-reaching here just a bit: if a Java program tried to install a program on a Linux/Ubuntu box it should trigger a request for authentication (needing administrator password) . Even Java -- should not be able to update anything -- except the libraries for the logged on user.

comments?  am I understanding right ?

please bear with me; I only have 1 U-box up so far (but the parts for my new monster U-box should start arriving today )

---

### Post by wacky_sung on 2012-09-26
Just as i mentioned in this [thread]("http://ubuntuforums.org/showthread.php?t=2061475") and people take my word lightly and accuse of creating FUD. In a simple word to say the admin here are just cannot accept me for being transparency. Good luck with such a conservative mindset through a open community and slowly i move away from here.I am here to warn and share but not take security for granted.:lolflag::lolflag::lolflag::lolflag

```
Gowdiak wrote that Security Explorations successfully pulled off the exploit on a fully patched Windows 7 32-bit computer in Firefox, Chrome, Internet Explorer, Opera, and Safari. Although testing was limited to Windows 7 32-bit, Gowdiak told Computerworld that the flaw would be exploitable on any machine with Java 5, 6, or 7 enabled (whether it&#8217;s Windows 7 64-bit, Mac OS X, Linux, or Solaris).

The bug lets attackers violate the &#8220;type safety&#8221; security system in the Java Virtual Machine. &#8220;A malicious Java applet or application exploiting this new issue could run unrestricted in the context of a target Java process such as a Web browser application,&#8221; Gowdiak told Computerworld. &#8220;An attacker could then install programs, view, change, or delete data with the privileges of a logged-on user.&#8221;
```


[Additional information Site]("http://www.pcworld.com/article/261748/researchers_find_critical_vulnerability_in_java_7_patch_hours_after_release.html")

---

### Post by jrog on 2012-09-26
This is a fault in **Oracle's** Java releases specifically, right? Wondering to what degree one should really be concerned.

---

### Post by mike acker on 2012-09-26
> **jrog said:**
> This is a fault in **Oracle's** Java releases specifically, right? Wondering to what degree one should really be concerned.

I don't think it applies to Linux at all -- not every report I read on this glitch referenced Linux.

the glitch seems to be in the JavaVM -- not the Java itself...

the question I am exploring is: when you open a browser: to what extent can the JavaScript, Java, php, C# , .NET etc manipulate your machine ??

My personal thinking is: I don't know.  Therefore I think, while I dig into this question, I'll take my own medicine and use a separate user logon for "General Surfing".   After I do that It won't matter one lick what the browser wants to do: it can't access anything other than the home directories for that General Surf User account

I regard this as a very serious topic. Like others I'm getting more and more pressure to do sensitive tasks via the 'Net -- which makes security essential.  To me it appears Linux is a solution to this.

on top of which: software seems to run better under Linux..... hmmmm

---

### Post by wacky_sung on 2012-09-26
@mike acker , Linux is open concept in which the code are seem many people while Microsoft & Apple are close concept.Linux indeed has a better control over it security but that does not meant it is bulletproof.

---

### Post by Hungry Man on 2012-09-26
Java exploits are typically cross platform as they're design issues with the sandbox. This is the case here as well.

OpenJDK may or may not be effected. Java 7 is based primarily on OpenJDK but I don't think 5/6 are. That makes it sound like it's Oracle specific.

I wouldn't count on OpenJDK being secure. 

I would suggest anyone looking to stay secure from Java creates an Apparmor profile for it.

---

### Post by CharlesA on 2012-09-26
> **Hungry Man said:**
> Java exploits are typically cross platform as they're design issues with the sandbox. This is the case here as well.

OpenJDK may or may not be effected. Java 7 is based primarily on OpenJDK but I don't think 5/6 are. That makes it sound like it's Oracle specific.

I wouldn't count on OpenJDK being secure. 

I would suggest anyone looking to stay secure from Java creates an Apparmor profile for it.
Agreed. Personally, I would not even have Java installed. I don't have it installed on any of the Windows boxes I use, and I think the only thing I need it for on my *nix box is a code validation program.

---

### Post by QIII on 2012-09-26
Apparmor.  Period.

This will affect OpenJDK as it is the open source reference implementation for Oracle Java 7.

Just like the last vulnerability that everyone thought would not be a problem for OpenJDK -- before Red Hat's testing showed otherwise.

---

### Post by Hungry Man on 2012-09-26
Generally it's safe to assume OpenJDK is effected. It isn't necessarily as this vulnerability goes way back to version 5 but you should always assume so.

If anyone has an OpenJDK profile they could post I'd appreciate that.

---

### Post by jrog on 2012-09-26
That's for the answers about OpenJDK. I don't have Java on my system at present (and it might remain that way!), so it's fortunately not a personal concern; was just curious.

---

### Post by rookcifer on 2012-09-28
I detailed my Firefox AppArmor profile setup on my [blog here.]("http://rookcifer.blogspot.com/")  My profile doesn't have any Ux rules anywhere.  It also profiles everything that touches Firefox (totem, transmission, and the Java plugin).  For this reason, I feel it is more secure than the default profile.

I have only tested it with 12.04 and the latest Firefox.  If you're on KDE or an older Ubuntu you might have to make slight changes.

---

### Post by Welly Wu on 2012-09-28
I read and carefully followed rookcifer's guide to creating several Novell AppArmor profiles for Mozilla Firefox:

[http://rookcifer.blogspot.com/](http://rookcifer.blogspot.com/)

Here is my output:

wellywu@System76:~$ cd /etc/apparmor.d
wellywu@System76:/etc/apparmor.d$  sudo aa-enforce usr.lib.firefox* usr.bin.transmission-gtk  usr.bin.gnome-mplayer usr.lib.totem.totem-plugin-viewer
Setting /etc/apparmor.d/usr.lib.firefox.firefox to enforce mode.
Setting /etc/apparmor.d/usr.lib.firefox.firefox.sh to enforce mode.
Setting /etc/apparmor.d/usr.bin.transmission-gtk to enforce mode.
Setting /etc/apparmor.d/usr.bin.gnome-mplayer to enforce mode.
Setting /etc/apparmor.d/usr.lib.totem.totem-plugin-viewer to enforce mode.
Cache  read/write disabled: /sys/kernel/security/apparmor/features interface  file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from stdin (line 1): /sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
AppArmor parser error, in stdin line 60: syntax error, unexpected TOK_END_OF_RULE, expecting TOK_ID or TOK_SET_VAR

wellywu@System76:/etc/apparmor.d$ sudo apt-get source apparmor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'apparmor' packaging is maintained in the 'Bzr' version control system at:
[https://code.launchpad.net/~]("https://code.launchpad.net/%7E")ubuntu-core-dev/apparmor/master
Please use:
bzr branch [https://code.launchpad.net/~]("https://code.launchpad.net/%7E")ubuntu-core-dev/apparmor/master
to retrieve the latest (possibly unreleased) updates to the package.
Skipping already downloaded file 'apparmor_2.7.102-0ubuntu3.1.dsc'
Skipping already downloaded file 'apparmor_2.7.102.orig.tar.gz'
Skipping already downloaded file 'apparmor_2.7.102-0ubuntu3.1.debian.tar.gz'
Need to get 0 B of source archives.
Skipping unpack of already unpacked source in apparmor-2.7.102
wellywu@System76:

I did a couple of searches, but I could not find the AppArmor 2.4 compatibility patch.

How do I solve this problem?

---

### Post by Hungry Man on 2012-09-29
In the first line of your apparmor profile you seem to have added some character that's not valid. Seems like the totem profile.

---

### Post by rookcifer on 2012-09-29
> **Hungry Man said:**
> In the first line of your apparmor profile you seem to have added some character that's not valid. Seems like the totem profile.

You talking to me or him?  If me, what character is not valid?

OK, I edited my post on the blog.  I just recopied my own profile again to make sure there were no errors in my original post.  See if that fixes it for you Welly.

(BTW, Welly, I cannot respond to your PM's because you have PM's disabled).

---

### Post by Welly Wu on 2012-09-29
What's wrong with the totem AppArmor profile? It seems to be the culprit, but I simply copied and pasted Rookcifer's custom AppArmor profile.

How do I fix this problem?

---

### Post by Welly Wu on 2012-09-29
Yes, this update fixed the totem AppArmor profile.

This is solved for me.

Thank you Rookcifer.

---

### Post by rookcifer on 2012-09-29
> **Welly Wu said:**
> Yes, this update fixed the totem AppArmor profile.

This is solved for me.

Thank you Rookcifer.

No problem.  Trying to paste code to blogs is a PITA.  I think the blog somehow mis-formatted it.  Let me know how it works for you.  If you have any issues you can PM me.

---

### Post by Welly Wu on 2012-09-29
I like your custom Novell AppArmor profiles related to Mozilla Firefox. I can't download any pictures to my data drives, but I use Opera to do that now.

Now, Mozilla Firefox is really really secure!

Thank you!

---

### Post by WhiteHatGuy on 2012-09-30
> **QIII said:**
> Apparmor.  Period.

This will affect OpenJDK as it is the open source reference implementation for Oracle Java 7.

Just like the last vulnerability that everyone thought would not be a problem for OpenJDK -- before Red Hat's testing showed otherwise.







Yep, but I am so freaking noob. What can I do? LOL:lolflag:

Just joking here.


AppArmor is defenatly the way to go

---

