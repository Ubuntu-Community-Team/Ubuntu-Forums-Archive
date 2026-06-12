---
title: "Firefox confined profile with AppArmor Ubuntu's default. What's your experience?"
date: 2016-02-14
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-02-14
I just enabled it. I won't say how. My VPN loads and works, I can log into the forums, access my encrypted web-mail service, broke precedence and opened a YouTube video of reviewing Ubuntu 15.04, so far everything is working.

What is your experience having with this? Anything you can't access with it?

```
apparmor module is loaded.
20 profiles are loaded.
20 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
4 processes have profiles defined.
4 processes are in enforce mode.
   /sbin/dhclient (954) 
   /usr/bin/freshclam (1337) 
   /usr/sbin/cups-browsed (1117) 
   /usr/sbin/cupsd (2226) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---

### Post by maglin2 on 2016-02-15
I've had it enabled and set to enforce since 12.04. Never had a problem following FF updates. 
Unlike Chromium default profile, where every Chromium update seemed to require a profile tweak. The first I managed, the second seemed to require something beyond my aa skills, and I gave up on it.

---

### Post by mikodo on 2016-02-15
@maglin2. Thanks, for sharing!

 I'm happy to hear it hasn't been a problem for you with FF. Good to know your experience with the Chromium Browser. I don't use it but, I have been thinking of possibly using it, as an adjunct. Now, I won't bother.

So far, FF just keeps ticking as before.

---

### Post by maglin2 on 2016-02-15
You're welcome.
The fact that FF apparmor profile never causes issues may imply that it's very lax. I take the view that even so FF must be slightly more secure against some issues with it than without it (though I don't claim to understand it).

FF and Chrome (I switched from Chromium to Chrome) are both also sandboxed:

FF
Sandbox
Seccomp-BPF (System Call Filtering)    true
Seccomp Thread Synchronisation    true
User Namespaces    true
Media Plugin Sandboxing    true

Chrome
**Sandbox Status**

[TABLE]
[TR]
[TD]SUID Sandbox[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]Namespace Sandbox[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]PID name spaces[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]Network namespaces[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]Seccomp-BPF sandbox[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]Seccomp-BPF sandbox supports TSYNC[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]Yama LSM enforcing[/TD]
[TD]Yes[/TD]
[/TR]
[/TABLE]
[COLOR=green][FONT=Times New Roman]You are adequately sandboxed.[/FONT][/COLOR]

(again I've no idea what all this means, but it sounds like 'a good thing' for browser security, and presumably having similar intent to apparmor profile in that respect).

and then there's Noscript etc.

---

### Post by mikodo on 2016-02-15
Hi again. 

Did that need to have input from you, or is it default in Ubuntu?

How does one check for the results you posted? Is there commands?

Thanks, again.


> **maglin2 said:**
>  Snippet
FF and Chrome (I switched from Chromium to Chrome) are both also sandboxed:

---

### Post by maglin2 on 2016-02-15
Those are sandbox status outputs for default install.

To see them for FF use Help-Troubleshooting Information and scroll to the bottom of the page.

For Chrome (or Chromium) type chrome://sandbox into the address box of the browser (I think you type chrome even for chromium, but I'm not sure)

---

### Post by mikodo on 2016-02-15
@maglin2

Thank you again.

Addendum:

Interesting information in Help-Troubleshooting.

Shows the add-ons I have including NoScript.

Sandbox
-------

Seccomp-BPF (System Call Filtering): true
Seccomp Thread Synchronization: true
User Namespaces: true
Media Plugin Sandboxing: true

---

### Post by sabina2 on 2016-02-15
Same thing here. I've been using Firefox with an AppArmor profile for 2 years without any problem. I also guess the out of the box Firefox profile is not totally restrictive.

---

