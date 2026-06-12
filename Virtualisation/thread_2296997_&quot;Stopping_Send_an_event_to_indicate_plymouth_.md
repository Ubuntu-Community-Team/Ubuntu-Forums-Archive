---
title: "&quot;Stopping Send an event to indicate plymouth is up&quot; after trying to login"
date: 2015-09-30
forum: Virtualisation
---

### Post by Jos_Luis on 2015-09-30
Virtual Box with Windows 8.1 as host. Fresh installed Ubuntu 14.04 LTS 

After trying to login as administrator or as guest, i get this error: 

[IMG]http://i.imgur.com/X2gICpL.png[/IMG]

I don't get any error until i choose one of the users. After choosing one of them, the system takes a while to process only to then show the error (above) for a small instant. After that, he shows again the users login screen. 

Here's how the system is configured:

[IMG]http://i.imgur.com/RxbEx06.png[/IMG]

Is there any way to fix this? Thanks in advance.

---

### Post by vica2 on 2015-09-30
Hello, I have the same error as listed above, and I'm not able to log in into graphical interface of Ubuntu. And I have two more lines on that screen as follows:
"* Starting Mount network filesystems  [OK]
 * Stopping Mount network filesystems  [OK]".
I have Virtual Box 5.0.2 with Windows 7 Ultimate 32-bit as host. Fresh installed Ubuntu 14.04.03 LTS 32-bit. On the host notebook, I have AMD 64-bit CPU "Turion RM75" (k8) & videochip ATI AMD Radeon IGP RS780M.

I can log in and work in the Command Line Interface of Ubuntu. Startx command gives me a mistake about x.org server.

Thank you in advance for your prompts on how to log in into GUI of Ubuntu.

---

### Post by lci2 on 2016-02-13
I had exactly the same problem as Jos_luis: Virtualbox on Windows 8.1 and Ubuntu 14.04 LTS (32-bit version, as 64-bit version failed to install), login aborted after message "Stopping Send an event to indicate plymouth is up", and no way to get into Ubuntu.
The problem went away after I followed instructions to solve the other problem I had: to be able to install the 64-bit versions of guest OS. Procedure: enable virtualization technology in the BIOS (ESC and F10 at boot of real computer; on HP BIOS it was in the 'power options' tab, but other BIOSes appear to have it in the 'security' tab). The 32-bit version of Ubuntu now works (I haven't bothered with the 64-bit version yet).

---

