---
title: "using live cd and security"
date: 2005-08-30
forum: The Cafe
---

### Post by Lambert on 2005-08-30
I see many questions on security and from what I've read I see where linux and it's basic structure makes it more secure.

In other threads though I see where if there's a problem advice is given to use a livecd like knoppix. In doing this they can perform tasks on an installed os as if they had root capabilities on the installed os (adjusting config files etc..)

So I'm curious to how this fits in and what problems it could cause (if any)

Can anybody drop a livecd in my pc and cause havoc this way as if I let them log in as a root user?

---

### Post by macgyver2 on 2005-08-30
[QUOTE=Lambert]Can anybody drop a livecd in my pc and cause havoc this way as if I let them log in as a root user?[/QUOTE]
Simply, yes.

Which is why any sound security solution must include physical security.

---

### Post by aysiu on 2005-08-30
[QUOTE=Lambert]
Can anybody drop a livecd in my pc and cause havoc this way as if I let them log in as a root user?[/QUOTE] In my experience, you don't even have to *let* them log in as a root user--the live CD itself will let them do that. If someone has a Linux live CD, knows what she's doing, is malicious in intent, and has physical access to your computer, you're screwed.

---

### Post by UbuWu on 2005-08-30
[QUOTE=Lambert]
Can anybody drop a livecd in my pc and cause havoc this way as if I let them log in as a root user?[/QUOTE]

There are only two things you can do about this:
* Take appropriate physical measures
* Encrypted filesystems to protect your privacy sensitive data... it could still be destroyed however.

---

### Post by UbuWu on 2005-08-30
Oh and of course you can disable booting from cd in the bios (don't forget to set a password for the bios). This is never 100% secure however.

---

### Post by mstlyevil on 2005-08-30
If you take a hard drive out of a windows XP computer and put it on another XP computer, You can basically do the same thing as a live linux cd. I have done this a time or two to recover data on a unbootable XP hard drive.

---

