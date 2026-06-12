---
title: "shell server"
date: 2007-06-14
forum: Server Platforms
---

### Post by Robert12345 on 2007-06-14
Hello, im setting up a shell server and i was wondering if it is possible to limit what users can do by editing their bash_profile can some tell me how to to do this?

---

### Post by craigp84 on 2007-06-14
Hi Robert12345,

It depends how far you want to go. Also depends how much functionality you need to leave for them for your shell server still to be a useful service.

Do you trust your users, i.e. are they friends of yours or are they complete strangers but whom you have credit card details of, or are they totally anonymous and getting your service for free?

In the latter case, you're probably going to want to impose snail mail registrations and such like to try and eliminate spammers etc. For these types of users you probably want to chroot / jail them on login, and only copy specific binaries into their chroot jail.

For the persons with credit card details, a strict permissioning scheme (i.e. tightening up /sbin /usr/sbin & setuid / setgid binaries) is probably the way to go. You'd probably want to mount /home on a seperate partition with the noexec,nodev,nosuid etc. flags set.

For friends who mean no harm, but possibly a bit short on understanding of the impacts of certain commands, you really just want to make sure they don't accidentally trash the system. Things like aliasing cp, mv and rm to cp -i, mv -i... etc. from /etc/profile would be sensible. It might be wise to still tighten up on some permissions too.

There's a handy tool called bastille, which not only steps through a whole load of stuff to harden your server, it also explains the reasoning for each change, so you learn at the same time.

You can impose further limits (such as limiting logon times) using pam (/etc/pam.d) or files in /etc/security etc.

Hope this helps,

-c

---

### Post by Robert12345 on 2007-06-14
Hey thanks for the info mate. Yeah i've just installed bastille on my server but i just want to know how you can also stop people using commands by editing the /etc/profile ?

---

### Post by craigp84 on 2007-06-15
> i just want to know how you can also stop people using commands by editing the /etc/profile ?

You can't. If you've got a list of commands you don't want to be run (normally stuff under /sbin or /usr/sbin etc.) then just change the permissions on them :-)

-c

---

