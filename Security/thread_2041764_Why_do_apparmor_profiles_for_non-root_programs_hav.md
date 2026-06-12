---
title: "Why do apparmor profiles for non-root programs have rules outside /home/?"
date: 2012-08-13
forum: Security
---

### Post by Alex1357 on 2012-08-13
I understand that an apparmor profile for a program that is usually run by root can be used to define precisely what file permissions, network permissions and Linux capabilities the program can use. These profiles may need to be quite complicated.

On the other hand, if a program is just run by a non-root user, IMO there is (almost) nothing to restrict outside this user's home directory as the user cannot do much out there. So why are the default profiles for non-root users so long and contain so many rules refering to files outside the home directories? To take an example, look at firefox. 
The firefox profile shipped with Ubuntu 12.04 has 156 lines, among which are many #include directives, thus even more rules that are applied to firefox processes.

What would be wrong with something like the following (not checked nor tested nor recommended) profile?


[PHP]/usr/lib/firefox/firefox{,*[^s][^h]} {
# allow network capabilites
network,
# allow anything outside the home directories
/ rwix,
/[^h]** rwix,
# restrict permissions in the user's home directory
@{HOME}/ ix,
@{HOME}/Public/ r,
@{HOME}/Public/\** r,
@{HOME}/Downloads/ rw,
@{HOME}/Downloads/\** rw,
@{HOME}/.{firefox,mozilla}/ rw,
@{HOME}/.{firefox,mozilla}/\** rw, }[/PHP]It has just 11 lines but seems to protect my personal files effectively against read and write access. In that style, it would be easy to confine non-root programs which are not fully trusted with short apparmor profiles. 

Am I wrong?

---

### Post by Hungry Man on 2012-08-13
Non root programs have more access than the /home/ directory.

example:

Pidgin needs access to certificate information in /etc/ssl/certs
It needs access to itself in /usr/bin/pidgin
It needs access to multiple other programs in /usr/bin/
It needs read access to multiple areas of the system like /proc/ and python libraries.

And then it also needs access to /home/ on top of that. A profile for Pidgin can easily be 40+ lines.

Your profile seems to give Firefox a lot of access to the system. Full access nearly.

---

### Post by Alex1357 on 2012-08-13
> **Hungry Man said:**
> Non root programs have more access than the /home/ directory.

Of course they have *some* access outside /home/. But there they are already sufficiently restricted by the user permissions. For example, they cannot change anything in /usr/bin/, because only root has write permission there. They can read there, but that's ok as there is nothing secret there, given that the content to be found there is the same as on millions of other computers. 

My point is that outside /home the file permissions per user are enough to protect the system, and just the access to /home has to be restricted on per process base.

---

### Post by movieman on 2012-08-13
> **Alex1357 said:**
> My point is that outside /home the file permissions per user are enough to protect the system, and just the access to /home has to be restricted on per process base.

So you're happy that malware in your web browser can upload any file from any user account on your system which doesn't deny you read permission?

---

### Post by Hungry Man on 2012-08-13
> Of course they have some access outside /home/. But there they are already sufficiently restricted by the user permissions. For example, they cannot change anything in /usr/bin/, because only root has write permission there. They can read there, but that's ok as there is nothing secret there, given that the content to be found there is the same as on millions of other computers. 

My point is that outside /home the file permissions per user are enough to protect the system, and just the access to /home has to be restricted on per process base.
But they can execute other programs, which they may not need access to. They can also read sensitive information both in /home/ and outside of it - while the files may not contain personal information they can contain information on:
1) The system itself ie: hardware, software, etc
2) Running processes/ information that can lead to ASLR data leak

both of which make further local exploitation (or remote even) much easier.

---

