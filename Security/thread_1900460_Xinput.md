---
title: "Xinput"
date: 2011-12-26
forum: Security
---

### Post by DoUPod on 2011-12-26
Hi,

I read that Xinput (part of X graphic server) could be used as a keylogger on a Ubuntu system.
In fact, a regular user can launch xinput and monitor every text entered (just like a keylogger) and especially text entered as root (root password for example).

I didn't find any information about this threat on the forum or in the documentation.

Is it a real threat ? Is there any way to prevent it (for example, we can desinstall xinput but is this packet necessary...) ?

Thanks

Source : [http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html)

---

### Post by Dangertux on 2011-12-26
> **DoUPod said:**
> Hi,

I read that Xinput (part of X graphic server) could be used as a keylogger on a Ubuntu system.
In fact, a regular user can launch xinput and monitor every text entered (just like a keylogger) and especially text entered as root (root password for example).

I didn't find any information about this threat on the forum or in the documentation.

Is it a real threat ? Is there any way to prevent it (for example, we can desinstall xinput but is this packet necessary...) ?

Thanks

Source : [http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html)

This is not a vulnerability it's a feature. The author of that article demonstrated it to demonstrate that Xserver does not adequately separate system resources (like input devices) between GUI based applications. It's important to note that it must be run in the same Xserver instance. This obviously is a particular concern due to the nature of sudo. Yes this happens, yes it works. No there really isn't anything you can do about it unless you want to switch to something like Qubes, which is also hers and this is a plug for that.

Hope this helps.

---

### Post by DoUPod on 2011-12-26
Yes it helps. But, there's absolutely nothing we can do to prevent it ?

For example,
- Is it possible to uninstall xinput packet or is it necessary to keep this packet ?
- What are the exact possibilities of attack through xinput ? Can any program use this command to monitor everything I write ?

Thanks

---

### Post by Dangertux on 2011-12-26
> **DoUPod said:**
> Yes it helps. But, there's absolutely nothing we can do to prevent it ?

For example,
- Is it possible to uninstall xinput packet or is it necessary to keep this packet ?
- What are the exact possibilities of attack through xinput ? Can any program use this command to monitor everything I write ?

Thanks

Removing XInput will likely break your entire installation, since it's used my almost everything to configure and read input from devices. 

Obviously anyone with physical access or remote access to an X session could keylog, and or inject input to Xserver. This could be used to escalate permissions via keylogging, compromise of additional applications or injection of arbitrary code into memory for potential execution. 

The point she was making in her article was that XServer was designed in a more trusting ecosystem, and that XServer demonstrates a poor security posture. You could consider using something like Xephyr which does a slightly better job at GUI application seperation via nested X Sessions, or like I said something like QubesOS if this is a concerning threat to you.

As I said earlier , the way it's designed currently anything running in the current XSession can read/write to XInput and thus any other application running in that XSession.

Hope this helps.

---

### Post by DoUPod on 2011-12-27
Ok. I understand better how xinput works.

So, every application I run in a graphic mode with XServer can log my keyboard.

But, I must install such applications...

So in fact, the major problem is to trust author of applications I installed (and not to install strange apps I don't know) ? For some evil people, there's no possibility of using this "threat" without installing an application ?

Thanks

---

### Post by Dangertux on 2011-12-27
Well not exactly. For instance if your browser were compromised and it yielded the attacker an interactive shell they could use Xinput to keylog you. Hope this clarifies.

---

### Post by DoUPod on 2011-12-27
Thank you for all the informations.

---

### Post by pling on 2012-09-21
> **Dangertux said:**
> This is not a vulnerability it's a feature.   This reply is so stunningly uninteligent and evasive it has provoked to raise a dead thread from the ground: many, many things are vulnerabilities and features! Being one does not preclude the other.  >   The author of that article demonstrated it to demonstrate that Xserver does not adequately separate system resources (like input devices) between GUI based applications. It's important to note that it must be run in the same Xserver instance. This obviously is a particular concern due to the nature of sudo. Yes this happens, yes it works.    So any app running under X can steal your sudo password - but this isn't a vulnerability.... Because it is a feature, so that's alright.  >  No there really isn't anything you can do about it unless you want to switch to something like Qubes, which is also hers and this is a plug for that.

Hope this helps.

 Nice hint of an ad hom attack there. Anyway...  But, yes, there is something you can do to make yourself effectively immune from such attacks: do all your admin and anything involving paypal etc, even indirectly (eg using the email acc your paypal account is linked too) from account that you only a very minimal and trusted set of X apps from. Or even do such things only from a X-less boot. Yes, this is hassle and not worth it for most people - but it is possible, and probably what should be done for servers.

---

### Post by Hungry Man on 2012-09-21
Dangertux is back? >_> edit: awwwww old posts.

And yes, because X has processes register hotkeys they can register any key and sniff or input them to any other key.

Wayland, for example, does not do this. New hotkeys require administrative rights and are registered through the OS.

I don't think Xinput is required, it's purely used to show how it works. With or without Xinput you can register the hotkeys.

As Dangertux said there is unfortunately very very little that can be done about this.

> This reply is so stunningly uninteligent and evasive it has provoked to raise a dead thread from the ground: many, many things are vulnerabilities and features! Being one does not preclude the other.

I think vulnerability implies an unintended weakness whereas both a vulnerability and a feature can be exploited. Regardless, it's semantics. His point is that it's an intended behavior.

> So any app running under X can steal your sudo password - but this isn't a vulnerability.... Because it is a feature, so that's alright.

I don't think he said it's alright. 

> Nice hint of an ad hom attack there. Anyway... But, yes, there is something you can do to make yourself effectively immune from such attacks: do all your admin and anything involving paypal etc, even indirectly (eg using the email acc your paypal account is linked too) from account that you only a very minimal and trusted set of X apps from. Or even do such things only from a X-less boot. Yes, this is hassle and not worth it for most people - but it is possible, and probably what should be done for servers.
That's not Ad Hominem. Also, just so you don't expect a response back, Dangertux doesn't post here any more.

Unfortunately, as you said, you'd have to boot into an X-less Ubuntu to be protected.

I think that that's assuming you've been compromised, which is why focusing on prevention is so important.

---

### Post by BlinkinCat on 2012-09-21
> **Hungry Man said:**
> Dangertux is back? 

Is he? I haven't seen him lately - :D

---

### Post by pling on 2012-09-21
> **Hungry Man said:**
>  I don't think Xinput is required, it's purely used to show how it works.    

Indeed: xinput doesn't patch over the x server and add this capability but uses an api fn. The problem is not xinput but the x server api.   

>  I think vulnerability implies an unintended weakness whereas both a vulnerability and a feature can be exploited.    

A vulnerability is quite simply an an opening to harm, which this is.

>  I think that that's assuming you've been compromised, which is why focusing on prevention is so important.  

Users have to understand that widely encouraged assumptions about Linux security based on privilege level are worthless. This is awful: nothing is worse than encouraging users to operate according to a false security model. Having appalling security and being clear about it would be better even!  

Also, WTF is wrong with the software process here??? This bug report discussion is terrifying:  [https://bugs.launchpad.net/suse/+source/xorg/+bug/800172](https://bugs.launchpad.net/suse/+source/xorg/+bug/800172)  

I also just found this, but it was deeply buried in my google searches:

[I][https://bugs.freedesktop.org/show_bug.cgi?id=38517](https://bugs.freedesktop.org/show_bug.cgi?id=38517)  

We already have an XSECURITY extension (and have had for years) which allows you to specify policies such as these in a SecurityPolicy file.  It's pretty neglected since no-one bothered using it, but it should work.  The well-maintained X-SELINUX extension allows full and powerful SELinux label-based matching, and works great.  If you search for blog entries and/or talks by Eamon Walsh, he's repeatedly demonstrated it and provided some examples.  As it is, not only would you break shortcuts, but also keys like brightness up/down, pop-up menus (including, e.g. the address bars in browsers), any window manager shortcut (e.g. the Windows key to provide the overview in GNOME Shell), the clipboard, a lot of input methods (e.g. virtual keyboards), and a whole lot else.  So it's pretty impractical to provide a 'please break my desktop badly' option.
[/I]
Perhaps worst of all is the realization that a software community that will brush over a vulnerability like this is capable of any bloody thing. And the countless variations of "But no one live malware has been seen using this, so you don't have a point" I have seen today just make me feel worse. This is a serious and obvious security flaw of the first magnitude, and it seems obvious to me that the only reason it hasn't been widely exploited is that linux desktops are too rare to make it profitable.

---

### Post by Hungry Man on 2012-09-21
I'm not trying to say that this issue isn't serious. It quite clearly is - this could lead to near effortless privilege escalation. Thankfully if you're running an internet facing service you can set it to a separate user account and then remove its X11 access. At that point it's more about the browser/ other internet facing services that the user interacts with graphically. And, root or not, you can contain those processes with LSM.


I wouldn't say the software community is brushing over it. Maybe on the X side of things, but we're talking about it here. I've talked about it in the past. Plenty of others are talking about it and I see this issue brought up often.

For me, I'll just move to Wayland ASAP. It doesn't suffer from this issue from what I understand. You can always just Apparmor graphic programs. It won't stop them from keylogging but it'll contain them whether they're root or not.

---

### Post by pling on 2012-09-21
> **Hungry Man said:**
> I'm not trying to say that this issue isn't serious. It quite clearly is - this could lead to near effortless privilege escalation. Thankfully if you're running an internet facing service you can set it to a separate user account and then remove its X11 access. At that point it's more about the browser/ other internet facing services that the user interacts with graphically. And, root or not, you can contain those processes with LSM.


How many users have any form of LSM enabled?

> 
I wouldn't say the software community is brushing over it. Maybe on the X side of things, but we're talking about it here. I've talked about it in the past. Plenty of others are talking about it and I see this issue brought up often.


In several hours of googling the only semi-adequate response I saw was in a response to the original blog post, amounting to "Use SE Linux."

---

### Post by Hungry Man on 2012-09-22
> How many users have any form of LSM enabled?

Any Ubuntu user has Apparmor profiles available and some are enforced by default.

> In several hours of googling the only semi-adequate response I saw was in a response to the original blog post, amounting to "Use SE Linux."

Right. The response has been terrible but it's definitely talked about. I see X keylogging brought up at least once a month somewhere or other. I wish it were brought up more - feel free to try to talk to the people who make decisions about these things.

---

### Post by pling on 2012-09-22
> **Hungry Man said:**
> Any Ubuntu user has Apparmor profiles available and some are enforced by default.


Default apparmoring is minimal, and apparmor does not in any way restrict access to keystrokes via x-windows.

> 
Right. The response has been terrible but it's definitely talked about. I see X keylogging brought up at least once a month somewhere or other. I wish it were brought up more - feel free to try to talk to the people who make decisions about these things.

I think at this stage we can already say that the decision makers are incompetent and beyond hope. As is, frankly, the community tech collaborative response. Because this is what a decent discussion should have looked like:

1. Decent definition of the problem, including which API functions are responsible and what sort of attacks this facilitates in terms a non-technical user can understand. At the least this allows any x-windows app running to steal passwords, so downloading a game or midi editor is suddenly a security risk. Naive users need to be told that an x-windows app might not have a window! And that such apps can install themselves so they autostart, so you can't assume that you are safe just because you haven't started any x-windows apps.

2. Clear discussion of options like SELinux and Apparmour, in each case saying whether they can stop the sniffing, and what else they can do that might help.

3. An absence of bs like this:

[I][https://bugs.freedesktop.org/show_bug.cgi?id=38517](https://bugs.freedesktop.org/show_bug.cgi?id=38517)  

We already have an XSECURITY extension (and have had for years) which  allows you to specify policies such as these in a SecurityPolicy file.   It's pretty neglected since no-one bothered using it, but it should  work.  

[/I]This doesn't tell anyone what this does. Is the poster referring to an extension for application writers? If so, does it allow them to create apps that lock other apps out so they can't sniff, or does it merely let them write apps that lack sniffing privileges? Or is this something a user can use to define which apps have sniffing privilges?

[I]The well-maintained X-SELINUX extension allows full and powerful  SELinux label-based matching, and works great.  If you search for blog  entries and/or talks by Eamon Walsh, he's repeatedly demonstrated it and  provided some examples.  

[/I] Try googling for X-SELInux and see what you get - stuff from 2005 saying "This isn't working properly yet." The most recent information I could find was
***[http://plash.beasts.org/wiki/X11Security](http://plash.beasts.org/wiki/X11Security)***

 ***One  such extension is XSELinux, which uses SELinux to make security  decisions according to SELinux's centralised policy.  When a process  connects to the X server, XSELinux finds out its identity (security  context) using getpeercon(), a SELinux-specific system call.  (Plash  does not provide anything analgous to getpeercon() because it is not an  identity-based security system.) *
[I]It  is not clear how XSELinux will provide secure labelling of windows (eg.  via title bars).  This requires changes to window managers.  It  presumably requires a new X request for getting the "security context"  of a window, analagous to getpeercon().  If this is added, will it be  SELinux-specific? 
[/I]
I.e. the only thing the author knows for sure is that nothing is clear or working yet!

Back to Radio The Japanese Will Never Attack Pearl Harbour:[I]
As it is, not only would you break shortcuts,  but also keys like brightness up/down, pop-up menus (including, e.g. the  address bars in browsers), any window manager shortcut (e.g. the  Windows key to provide the overview in GNOME Shell), the clipboard, a  lot of input methods (e.g. virtual keyboards), and a whole lot else.  So  it's pretty impractical to provide a 'please break my desktop badly'  option.[/I]

This is a pathetic response. Some users would be willing to give up such things to get security - at least part of the time. What the guy really means is that giving users such a drastic choice might scare them and cause them to realize that linux as it stands is not secure and can't be without considerable inconvenience.

---

### Post by pling on 2012-09-22
> **Hungry Man said:**
> 
For me, I'll just move to Wayland ASAP. It doesn't suffer from this issue from what I understand. 

People keep telling each other this, but I haven't seen anyone quote any evidence for the belief.  In fact the evidence seems to point in the opposite direction:

- None of the Wayland docs seem to mention improved security as a design goal

- And when someone asked about this on the Wayland mailing list no answered:

[http://www.mail-archive.com/wayland-devel@lists.freedesktop.org/msg03704.html](http://www.mail-archive.com/wayland-devel@lists.freedesktop.org/msg03704.html)

I think that lack of an answer says pretty strongly that Wayland is messed up too.

---

### Post by Hungry Man on 2012-09-22
I'm not sure Wayland does. I've heard it before.

The issue here is not Wayland or X so much as the security model of Windows, Linux, and OSX. Applications are not segregated. 

The big issue here is that X is bridging the separation between separate user groups. If one application in one user group could read another applications keys in that same user group I wouldn't care nearly as much - this is the security architecture of Linux, Windows, and OSX. The issue is that this pretty much removes that separation.

So hopefully Wayland fixes it. Maybe it won't. I believe Wayland registers global hotkeys differently but I don't know.

---

### Post by Ms. Daisy on 2012-09-23
> **pling said:**
> This reply is so stunningly uninteligent and evasive it has provoked to raise a dead thread from the ground: many, many things are vulnerabilities and features! Being one does not preclude the other.    So any app running under X can steal your sudo password - but this isn't a vulnerability.... Because it is a feature, so that's alright.  

 Nice hint of an ad hom attack there. Anyway...  But, yes, there is something you can do to make yourself effectively immune from such attacks: do all your admin and anything involving paypal etc, even indirectly (eg using the email acc your paypal account is linked too) from account that you only a very minimal and trusted set of X apps from. Or even do such things only from a X-less boot. Yes, this is hassle and not worth it for most people - but it is possible, and probably what should be done for servers.
Just because the FUD is so damn thick today I'll respond as well.  

If you have an Ubuntu desktop/server in a highly sensitive environment like a bank or a defence contractor, then you should be concerned about this.  If you're running an Ubuntu desktop at home and you use it to browse the web, then it's _**fantastically unlikely**_ that a skilled attacker would target you and exploit this particular vulnerability on  your system.

It's great to discuss vulnerabilities in Ubuntu. It's FUD if you don't give it some context in the real world.

---

### Post by Hungry Man on 2012-09-23
While it's unlikely it is legitimate. I think if we were talking about BIOS malware or some really unlikely scenario it'd be important to give context.

But this specific vulnerability bridges the Linux security model - the separation of users basically doesn't exist because an attacker can send and receive commands. I can use Apparmor to restrict Pidgin but if it's exploited and I happen to type in my root password to sudo Pidgin will read it. More importantly if I type my root password into Gksudo Pidgin will read it.

Pidgin can then send commands to that same terminal. It can type in ssh blah blah blah and suddenly I'm connected to an attackers terminal. It can UFW Allow.

Anything I can do with my keyboard an attacker can then do.

I think that's a legitimate issue worth talking about.

But as I said the issue isn't that an application can talk to another, this happens. It's that registering global hotkeys is possible, and worse it's possible from a standard account, which allows UID1 to talk to UID2 when they should be separate.

---

### Post by Ms. Daisy on 2012-09-23
> **Hungry Man said:**
> I think that's a legitimate issue worth talking about  Agreed. I'd just like to quantify the concern that the average user should have about it.  (Plus I got my panties all in a bunch and posted my response without even realizing there was a second page to this thread- lol)

If we're going to discuss it, I just want to clarify whether it's been actually exploited in the wild. Is there an exploit packaged in Metasploit or anything?  This is NOT something that an attacker uses directly to get on my computer, rather it is something he takes advantage of once he's already in my machine after first using some other exploit. Correct?

Help me understand the issue from a user's perspective: from what I've gathered so far it seems like it's a vulnerability that has no patch because its function is required for Linux to work.  If I patch/fix it I will totally break Linux.  If that's the case then it seems that this is more of an appeal to developers to fix the problem than a support thread for users in which to find a solution.

---

### Post by Ms. Daisy on 2012-09-23
[QUOTE=pling]I think at this stage we can already say that the decision makers are  incompetent and beyond hope. As is, frankly, the community tech  collaborative response. Because this is what a decent discussion should  have looked like:

1. Decent definition of the problem...

2. Clear discussion of options... [/QUOTE] Sounds like a perfect opportunity for you to write the documentation you want to see.  I would read it.  Developers apparently haven't found a way to solve the problem, perhaps you can suggest one or several for them.

---

### Post by Hungry Man on 2012-09-23
There's no metasploit module - there wouldn't be. It's not any code error or something. You can use xinput to test/ do what any metasploit module would do. Any shell can send/ receive through the APIs that allow xinput to work.

I doubt it's been used to attack anyone in the wild. Servers will run an x-less session so it won't matter. But it could easily.

An attacker would exploit some code. Let's say its DNSCrypt, which runs in a separate user account. Normally an attacker would be stuck in that user account, only able to access other processes running in that account to any meaningful extent.

X would allow it to communicate with any process, including root processes. Even with DNScrypt confined by apparmor it would be able to. It could then read my terminal input, input its own commands into the terminal, and basically do whatever it wants. MY apparmor profile could deny it access to /blah/blah.txt but if I have a terminal open it could cd/ ls to it. I could block access to ps but it can run it from that terminal.

DNScrypt is a poor example as it actually doesn't have X access but, regardless, it's clear to see the issue here.

The solution would be to require root to create a global hotkey (or have global hotkeys handled separately by a process that can make security decisions, or have some type of access control) and to run a separate X session (or treat it as a separate session) for each UID that has X access.

---

### Post by Ms. Daisy on 2012-09-23
Perhaps one of the more salient points to derive is that you should **never install a GUI on a server** because of this problem.

---

### Post by Hungry Man on 2012-09-23
Yep. And if you do you should only run X sessions for maintenance. When you're online you should be running an X-less session.

---

