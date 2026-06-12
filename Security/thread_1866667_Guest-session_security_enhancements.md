---
title: "Guest-session security enhancements"
date: 2011-10-21
forum: Security
---

### Post by twipley on 2011-10-21
prologue: [http://brainstorm.ubuntu.com/idea/28372/](http://brainstorm.ubuntu.com/idea/28372/)

> Idea #28372: Guest-session security enhancements

Rationale:

The "guest session" feature provides one "a convenient way, with a high level of security, to lend their computer to someone else." It also features automatic "purging," in such a way that every guest session starts fresh and clean. However, not being completely isolated from the rest of the system, since it might be possible for an external attacker to achieve root access through privilege escalation through specific-application vulnerability exploits, the guest-session feature should provide enhanced security. Furthermore, while one may be careful concerning the way they run their own system, including browsing using no-script-type extensions, and not opening dubious-origin external files, the person they choose to lend their system to might not be as careful, or might not possess a similar conscience of computing threats, and thus might spend their time in somewhat-dangerous-for-system-health activities. For example, they might, without being aware of related risks, run potentially malicious files (for example, untrustable media files), which might be able, through ingenious crafting, to compromise the system further than the outside boundaries of the temporary guest-session user.

Solution: Confine the guest session using proper software

The guest account should be confined from the rest of the system using proper software (such as AppArmor and SELinux), providing an extra layer of sandboxing from the rest of the system. Indeed, such a proposed user-level sandboxing is just part of the picture, the current application-level sandboxing already having proved its worth in contributing to the prevention of system exploits. However, much more could be done, in that practical world of ours, so as for us to move towards, albeit one step at a time, further such prevention.

some relevant questions:

1) does such an implementation idea make any sense to you?

2) someone told me the guest session already is relying on such a device for security sandboxing -- is that person right in their claim?

3) any relevant thoughts, comments, suggestions, or ideas?

---

### Post by Dangertux on 2011-10-21
> **twipley said:**
> prologue: [http://brainstorm.ubuntu.com/idea/28372/](http://brainstorm.ubuntu.com/idea/28372/)

some questions (or just points):

1) does such an implementation idea make any sense to you?

2) someone told me the guest session already is relying on such a device for security sandboxing -- is that person right in their claim?

3) any relevant thoughts, comments, suggestions, or ideas?

Guest sessions and or accounts can go two ways. They can be a great security feature or a giant security hole. If they are properly cared for and maintained they can be an asset in certain situations. However, where they more often than not end up is a poorly administered account to be used for local escalation.

Now IF I were going to condone guest sessions which I do not. I would suggest putting the minimum in place.

-- The guest session/user would ABSOLUTELY have to be confined properly using discretionary access controls. 

-- In addition to proper DAC configuration , I would highly suggest Mandatory Access Controls such as Apparmor or SELinux, in terms of a guest account of any type I would recommend SELinux of the two. The granularity SELinux provides in terms of user confinement is far superior to Apparmor's path based controls. In terms of confining a specific user this is preferable. 

-- The user/group would absolutely not EVER have access to any type of compiler. Also Ruby, Python and Perl need to be off limits. 

-- Absolutely LIMIT device access, stay away from things like pulse-audio, as it is a great avenue for exploits tailored to bypass SELinux/Apparmor. 

-- Absolutely NO setuid/setgid applications ever. 

These would be my recommendations and even then I would shy away from a "guest account" of any type.

---

### Post by bodhi.zazen on 2011-10-21
> **Dangertux said:**
> Guest sessions and or accounts can go two ways. They can be a great security feature or a giant security hole. If they are properly cared for and maintained they can be an asset in certain situations. However, where they more often than not end up is a poorly administered account to be used for local escalation.

Now IF I were going to condone guest sessions which I do not. I would suggest putting the minimum in place.

-- The guest session/user would ABSOLUTELY have to be confined properly using discretionary access controls. 

-- In addition to proper DAC configuration , I would highly suggest Mandatory Access Controls such as Apparmor or SELinux, in terms of a guest account of any type I would recommend SELinux of the two. The granularity SELinux provides in terms of user confinement is far superior to Apparmor's path based controls. In terms of confining a specific user this is preferable. 

-- The user/group would absolutely not EVER have access to any type of compiler. Also Ruby, Python and Perl need to be off limits. 

-- Absolutely LIMIT device access, stay away from things like pulse-audio, as it is a great avenue for exploits tailored to bypass SELinux/Apparmor. 

-- Absolutely NO setuid/setgid applications ever. 

These would be my recommendations and even then I would shy away from a "guest account" of any type.

Dangertux outlined some valid considerations.

You sort of have two options,

Ubuntu uses gdm-guest-session and there are some restrictions built in.

> It creates a temporary guest account with a temporary home directory and some restricted privileges (such as not being able to read any home directory or do any permanent change to the system).

But I do not know the details.

[http://packages.ubuntu.com/natty/gdm-guest-session](http://packages.ubuntu.com/natty/gdm-guest-session)

If you like you can customize the account

[http://ubuntuforums.org/showthread.php?t=1566078](http://ubuntuforums.org/showthread.php?t=1566078)

and you can restrict the guest account with apparmor (if it is not already)

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

The defaults are probably sufficient for most users, keep in mind if someone has physical access they can always boot a live CD.

Along those lines, you should encrypt any sensitive data you have ;)

Fedora uses xguest which is a similar concept, but xguest is confined by selinux.

---

### Post by twipley on 2011-10-21
Thanks for the info, both of you.

Keep in mind also that the Ubuntu-brainstorm idea is for a typical installation of Ubuntu to default to secure guest-account features.

The issue the way I had it in mind was more for a way to prevent a trusted although ignorant guest in a home to compromise the machine. In other words, even if the session he uses gets compromised, the attacker (from the other side of the world, for example) would not be able to escalate up to the root.

One could see this topic as a petition: *if the guest session already is not secured in such a way, for God's sake, then it should be.*

I heard Fedora is more secure out of the box (xguest, the kiosk mode you were talking about), but I am just too at ease with Ubuntu to switch over at the moment.

TL;DR: guests are ignorant, although trusted -- they have to get some help in protecting themselves. The Internet is a dangerous place. Condom browsing for the winner. etc.

---

### Post by Dangertux on 2011-10-21
> **twipley said:**
> Thanks for the info, both of you.

Keep in mind also that the Ubuntu-brainstorm idea is for a typical installation of Ubuntu to default to secure guest-account features.

The issue the way I had it in mind was more for a way to prevent a trusted although ignorant guest in a home to compromise the machine. In other words, even if the session he uses gets compromised, the attacker (from the other side of the world, for example) would not be able to escalate up to the root.

One could see this topic as a petition: *if the guest session already is not secured in such a way, for God's sake, then it should be.*

I heard Fedora is more secure out of the box (xguest, the kiosk mode you were talking about), but I am just too at ease with Ubuntu to switch over at the moment.

TL;DR: guests are ignorant, although trusted -- they have to get some help in protecting themselves. The Internet is a dangerous place. Condom browsing for the winner. etc.

As far as Fedora being more secure OOTB I'm not sure that is necessarily true. What I will say is that Fedora's security features (for instance SELinux) are much more accessible to the average end user OOTB.

Something I really hope Ubuntu catches on to. Make Apparmor useful for something other than super paranoid sec dorks. Just my humble opinion.

---

### Post by twipley on 2011-10-27
> **Dangertux said:**
> Something I really hope Ubuntu catches on to. Make Apparmor useful for something other than super paranoid sec dorks. Just my humble opinion.

Good to know that about Fedora. An argument that will make me stick to Ubuntu for what it is longer.

What you are saying makes sense. Because, for example, one could picture a guest installing a malicious add-on through Firefox (because AppArmor is not by default protecting Firefox in a guest session). That way, there is no need for the guest to install software (requiring admin password), in that installing add-ons may do the job in achieving privilege escalation up to root. That is the thought that made me open up this topic in the first place.

---

### Post by twipley on 2011-11-08
Jamie, representing the head of the Ubuntu Security Team, replied to posted concerns:

[QUOTE=Jamie]Thanks for your interest. The guest session is already sandboxed via apparmor. If you would like to make improvements to the sandboxing, I encourage you to file a bug against the lightdm and/or gdm packages (the packages providing the sandboxing).[/QUOTE]

So, as he mentioned, *the thread suggestion is already implemented*, which makes sense from a security point of view.

---

