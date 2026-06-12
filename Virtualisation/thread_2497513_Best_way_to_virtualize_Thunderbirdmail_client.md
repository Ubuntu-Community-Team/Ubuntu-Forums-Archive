---
title: "Best way to virtualize Thunderbird/mail client"
date: 2024-05-08
forum: Virtualisation
---

### Post by currentshaft on 2024-05-08
o3

---

### Post by &amp;KyT$0P# on 2024-05-08
What purpose do you have in mind for this level of isolation?

Can you just use Thunderbird via the VM's own screen?

---

### Post by TheFu on 2024-05-08
I use the remote-X method and don't have performance issues.  Here's my script:

$ more ~/bin/thunderbird.sh 
```
#!/bin/bash

# FJ_OPTS="--dns=172.22.22.81 --rlimit-as=3500000000 --ignore=seccomp --ignore=protocol"   # This doesn't work anymore

FJ_OPTS="--dns=172.22.22.81 --rlimit-as=4700000000 "
TB_OPTS="-no-remote "

# limit RAM VSS to 4.7G
PID=$(/usr/bin/ssh   -X  deneb    /usr/bin/firejail   $FJ_OPTS     /usr/bin/thunderbird    $TB_OPTS    $@ & )
exit;
```

Deneb is a VM running Linux Mint.  It runs thunderbird, Firefox, and a few other desktop apps that I don't like Ubuntu to run.  When I'm traveling, it is the remote desktop I use via x2go - this leaves the data at home, not traveling with me.

The VM looks like this:
```
$ inxi 
CPU: 2x 1-core AMD EPYC-Rome (-SMP-) speed: 4200 MHz
Kernel: 5.15.0-105-generic x86_64 Up: 11d 18h 3m
Mem: 5318.6/5873.9 MiB (90.5%) Storage: 76.16 GiB (27.6% used) Procs: 241
Shell: Bash inxi: 3.3.13
```

I suppose you could use a Linux Container, but allowing a GUI to work inside a container is a little more complex.  Others here have done it.  I don't use Wayland, so perhaps that's the issue?  IDK.

---

### Post by currentshaft on 2024-05-08
asdf

---

### Post by currentshaft on 2024-05-08
censorship

---

### Post by #&amp;thj^% on 2024-05-08
> **currentshaft said:**
> 

I know I can run Thunderbird with firejail, but I really don't want it to have access to anything on the host OS.

Thanks

netblue30 might have some insight: [https://github.com/netblue30/firejail/issues/995](https://github.com/netblue30/firejail/issues/995)

---

### Post by currentshaft on 2024-05-08
fu

---

### Post by #&amp;thj^% on 2024-05-08
Thanks for the clarity, TheFu is pretty wise on this type of help.

I'm not sure why you hit such a lag in performance though with A KVM//

---

### Post by &amp;KyT$0P# on 2024-05-08
Would it not be sufficient to use the [flatpak version of Thunderbird]("https://flathub.org/apps/org.mozilla.Thunderbird") and set restrictive permissions with [flatseal]("https://flathub.org/apps/com.github.tchx84.Flatseal")?

For the performance issue:

1) How have you installed Thunderbird and Chromium?

2) Does Thunderbird have an option to disable hardware acceleration equivalent to [this option in Firefox]("https://support.mozilla.org/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration")?  Chromium has such option in [FONT=Courier New]chrome://settings/system[/FONT] , "Use graphics acceleration when available".  Does it help to turn off this option?

3) What desktop environment are you using on the VM host?  Is it running under X11 or Wayland?  Are you able to test whether the performance problem occurs in a Xephyr on the host?

4) How do you have networking set up for the VM?

(I tested [FONT=Courier New]ssh -X (me)@(my-vms-ip) -t flatpak run org.chromium.Chromium[/FONT] to a virt-manager/KVM guest, which I connect to using a bridge interface, and did not see any performance issue in Chromium.)

---

### Post by TheFu on 2024-05-08
I don't use virt-manager, except to setup new VMs or destroy them when I'm done.  Definitely NOT for daily use as a remote desktop.

Also, I'm not on Debian, though I have a few debian servers for things like VPNs and email gateways, but not much else.  When Deb12 was released, I installed it and found the networking didn't meet my needs. Perhaps I had a too early version and networking setup wasn't working.  I never came back around.  My VM host is Ubuntu server 20.04 running on a different system.  The ssh and X-forwarding are over a GigE LAN connection.  On the same LAN, I generally don't use virt-viewer either.  Generally I use ssh and remote X11 to my workstation.  So much more convenient.  Most of my daily use applications actually run over remote X11 on different systems and many are either containers or VMs, not a physical host ... mostly.

I don't force a tty. It isn't needed.  I had to look that option up. Never noticed it before.

Also, I don't use wifi except on devices that have no other connection method. Laptops that don't have ethernet ports use USB3-to-Ethernet adapters.  On the wire, iperf3 tests to 920-944 Mbps.

I don't see how thunderbird in a firejail can break out.  Ever run bash with the same firejail settings?  Lots of other things are disabled both in standard and private modes.  Thunderbird in private mode isn't very useful, since prior address books, emails, and connection settings wouldn't exist.

I don't use any flatpaks and won't be using a snap package for browsers or email. I like the added control I get with firejail and I like NOT having extra bloated dependencies that aren't needed.

---

### Post by undecidable on 2024-05-09
Unless I misunderstand you host and guest are on the same machine.

fwiw, and as another option,
I run multiple VMs at the same time on different virtual desktops,
accessing their desktops via virt-viewer,
switching between them / their virtual desktops  with a mouse roll.  

Two of these VMs have Thunderbird clients accessing different classes of email.
The VMs are clones so easy to set up as many as I need.  

Was fast under Virtualbox and is equally fast under virt-viewer/libvirt/qemu/kvm.

---

### Post by currentshaft on 2024-05-09
dada

---

### Post by #&amp;thj^% on 2024-05-09
Not to argue here, and I just can't imagine that exploit as an easy task by an attacker, seems to me you would at some point have to help the attacker.
> Exploit prediction scoring system (EPSS) score for CVE-2022-31214

Probability of exploitation activity in the next 30 days: 0.04%	

Percentile, the proportion of vulnerabilities that are scored at or less: ~ 6 %
> A Privilege Context Switching issue was discovered in join.c in Firejail 0.9.68. By crafting a bogus Firejail container that is accepted by the Firejail setuid-root program as a join target, a local attacker can enter an environment in which the Linux user namespace is still the initial user namespace, the NO_NEW_PRIVS prctl is not activated, and the entered mount namespace is under the attacker's control. In this way, the filesystem layout can be adjusted to gain root privileges through execution of available setuid-root binaries such as su or sudo.
My version seems to be fixed: firejail --version
firejail version 0.9.72

Please Note, I don't use Thunderbird personally.
I do understand your concerns though.  I kind of subscribe to "Do I feel safe enough" knowing all the while nothing is bullet proof.
I also run heavy security audits bi-monthly.

But I wish I could help with your performance over X.

Interesting Thread please keep us updated.

---

### Post by TheFu on 2024-05-09
> **currentshaft said:**
> Firejail is a setuid-root program. An exploit of it is going to lead to existential consequences.

[https://www.cvedetails.com/vulnerability-list/vendor_id-16191/product_id-36171/Firejail-Project-Firejail.html](https://www.cvedetails.com/vulnerability-list/vendor_id-16191/product_id-36171/Firejail-Project-Firejail.html)

A capable adversary literally just has to send you an email (you don't even have to open or interact with it) to get root on your system.

So I basically want to isolate and containerize all such programs which receive and execute untrusted code from strangers all day.

I just can't figure out why the performance of X over SSH on localhost is so miserable.

localhost?  That seems like it wouldn't work.  Every VM has a different idea about "localhost".  127.x.x.x/8 is localhost, by definition.

Since I've been running my own email servers 25+ yrs, I doubt any badness will arrive.  My gateway blocks emails from huge parts of the world. I never see them.  Sometimes that can cause problems.  Usually less than 1-2 times a year.  Last week, a contractor send a proposal for work using a 3rd party email that I had gotten nasty spam messages through about 5  yrs ago.  Back then, I blocked all emails from that domain.  A slight hassle for them and for me, but we worked it out.  That's before the email even hits my email server.  Then my clients are setup to only show 7-bit ASCII, so anything else, especially HTML/mime email just shows up blank.  The SMTP standards REQUIRE 7-bit ASCII as the main email and allow for attachments.  

A few minutes ago, I saw a spam email for watches ... from 103.70.114.0/23 MOZ TECHNOLOGY JOINT STOCK COMPANY. That domain is in Vietnam.  Blocked now through an ipset rule. I never expect to deal with them ... ever. They allowed a client to become a spammer.  1 time, is too many.

Anyway, I've never been hacked via email. Not once.  But I don't open attachments, especially PDF files, unless they are expected.

My mother was hacked through an email message on WinXP.  The spearfishing targeted her perfectly.  New Baby Photos from a granddaughter's email who just had a baby less than a week earlier.  No mother/grandmother could have resisted opening that email or the attachments.  She knew immediately that something was wrong and pulled the power cord from the wall.  It was too late.  I moved her to Linux a few months later.  She had great fear of Linux because she'd seen my minimal desktop.  For 10+ yrs before, I'd had her using Firefox, thunderbird, and OpenOffice already, so it was less about a new OS and more about seeing the same applications she'd been using already.  Afterwards, she was running Ubuntu with LXDE and the icons for her programs on the side-bar.  Additionally, I setup constant backups (hourly via Back-in-Time) and weekly off-site pulled backups to my home for the most critical stuff.  There were a few MS-Windows-only programs, which we solved with an App Window into a VM.  She didn't need to know anything about a hypervisor.

We also moved her email from the ISP over to a domain run by a brother-in-law.  My family has a number of computer nerds with admin experience.

---

### Post by argguy on 2024-05-15
I just created an account to reply: I'm trying to achieve the same as **currentshaft**[COLOR=#000000] : Not for myself, but for an office full of cavemen with zero tech knowledge. They've already been hacked through malicious emails, and even if they attend a thousand courses on good computer practices I won't sleep well...
Virtualizing email client and making them remotely use it seems a nice way to keep nastiness contained.[/COLOR]

---

### Post by TheFu on 2024-05-15
For cavemen, 
[LIST]
[*]No attachments.
[*]7-bit ASCII email only. No MIME attachments.
[/LIST]
Period.

---

### Post by currentshaft on 2024-05-15
dk

---

### Post by #&amp;thj^% on 2024-05-15
> **TheFu said:**
> For cavemen, 
[LIST]
[*]No attachments.
[*]7-bit ASCII email only. No MIME attachments.
[/LIST]
Period.

+1 Period

---

### Post by TheFu on 2024-05-15
> **currentshaft said:**
> That won't prevent thunderbird, or frankly most software made to executed untrusted code, from getting owned.

Like I said, a skilled adversary needs only to send you an email message - you do not even have to open or click on anything in it to get owned.


Do you have a link for this attack on Linux?  I've never heard nor seen it.
On Android and iPhones, where we don't have control, I can see it and on MS-Windows where they have MS-DOS and Win3 image handling complete with bugs, I can see it happening, but not in Linux.  I've searched and find nothing.

How can an email own a system when the client is running as a normal user?  To that, I'd say stop using root for email.

Now, if someone clicks a link in a message or opens an attachment, then I can see owning the account, but not the system.

---

### Post by currentshaft on 2024-05-16
k

---

### Post by TheFu on 2024-05-16
And none of that works against emails that are 

7-bit ASCII 
and 
no attachments (including MIME attachments).  Block them all.

Which is what my email servers allow.

---

### Post by currentshaft on 2024-05-16
kk

---

### Post by TheFu on 2024-05-16
Certainly a quality hacker would trivially be able to find one of my email addresses - I have hundreds.  That should make it even easier.

---

### Post by argguy on 2024-05-20
Uhm guys this has derailed from topic... 
What about focusing on the question as a mere thought excercise? I appreciate your willingness to address the issue we are trying to resolve the best and easiest way possible, but I propose forgetting the "why" and focusing on the "how" or "what".
I'm really interested in this approach of containerizing apps as a security measure.

---

### Post by argguy on 2024-05-22
> **currentshaft said:**
> I'd like to isolate my mail client (Thunderbird) from the rest of my system.

I've found this:

[https://mailcow.email/](https://mailcow.email/)

Have to do some tests yet, but leaving alone the server-side apps and only using the client may work as we want.

---

### Post by currentshaft on 2024-05-23
1

---

