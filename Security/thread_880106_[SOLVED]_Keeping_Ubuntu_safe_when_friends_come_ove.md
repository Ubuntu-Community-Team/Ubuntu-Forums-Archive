---
title: "[SOLVED] Keeping Ubuntu safe when friends come over."
date: 2008-08-04
forum: Security
---

### Post by nerd0795 on 2008-08-04
Well.  I have a friend who kills computers with what he does on them.  He manages to get thousands of viruses on his computer a day.  The thing is that same person might be using my computer soon (under UBUNTU)  I also want to keep my Ubuntu box safe since my family does online banking on it (under the Windows Vista partition though).  I want to protect my Ubuntu box from one of the extremely rare linux viruses.  Is there a good program (FREE only) to protect my ubuntu box from any changes from malicious web pages?  I don't think I have to worry about terminal because I have a password for the root.

---

### Post by sisco311 on 2008-08-04
Create a new user account for your friend
and don't add it to the admin group.

---

### Post by Jack-Frost on 2008-08-04
I'd just go to the Add/Remove programs and get a virus scanner. They exist...I've seen them. Also, why not just go into firefox and BLOCK some sites you know will give your Linux a virus. 

You may also want to tell your friend...In a nice way. That he should not click on random advertisements, or go watch too much porn >.> Because your computer is precious, and you don't want it F$($#@ with.

---

### Post by Jack-Frost on 2008-08-04
> **sisco311 said:**
> Create a new user account for your friend
and don't add it to the admin group.

That too. Just delete the account after he's done >.>

---

### Post by nerd0795 on 2008-08-04
> Create a new user account for your friend
and don't add it to the admin group.

That seems good, does it protect me a full 100%?  Can I still get a virus.

---

### Post by atoc on 2008-08-04
> **nerd0795 said:**
> Well.  I have a friend who kills computers with what he does on them.  He manages to get thousands of viruses on his computer a day.  The thing is that same person might be using my computer soon (under UBUNTU)  I also want to keep my Ubuntu box safe since my family does online banking on it (under the Windows Vista partition though).  I want to protect my Ubuntu box from one of the extremely rare linux viruses.  Is there a good program (FREE only) to protect my ubuntu box from any changes from malicious web pages?  I don't think I have to worry about terminal because I have a password for the root.
Create an "Unprivileged User" (Administration|Users and Groups) for them to use; it's the same as the limited "Guest" account on Windows.

When your friend is visiting, log out of your account when they want to use the machine and don't forget to log yourself out if you use it with your logon credentials.

That way the only damage they'll do is to the guest account home folder.

[How to create a limited (Guest) User Account in Ubuntu Linux]("http://blog.mypapit.net/2007/09/how-to-create-a-limited-guest-user-account-in-ubuntu-linux.html")
> Ubuntu provides the facility to create limited (and unprivileged) user account for conveniences in day-to-day Desktop experience. By creating users with limited privilege, you can prevent other users from messing up with your operating system configuration while giving them the freedom of using their own Desktop and workspace.

---

### Post by nerd0795 on 2008-08-04
> or go watch too much porn >.>

That's what that person does.  His friend which is on a much lesser degree of viewing that stuff had 65000 viruses.  The actual person I'm talking about actually had a virus that a smiley face appeared covering the whole screen saying "YOU R A NOOB".   UGHHH!!!

---

### Post by knightcoder on 2008-08-04
I guess you're pretty safe if you create an account for your friend. Just watch if he's trying to pop-in a Ubuntu CD and reinstalling the OS itself...hehe

---

### Post by nerd0795 on 2008-08-04
> I guess you're pretty safe if you create an account for your friend. Just watch if he's trying to pop-in a Ubuntu CD and reinstalling the OS itself...hehe

I don't think that person could even find the disk (I've hid it)...hehe

---

### Post by loboc on 2008-08-04
Most virus scanning applications for LINUX like CLAMAV are designed to scan the email that gets routed through a server for Windows Viruses 

If you are paranoid you could install some rootkit detectors the one i know by name is chkrootkit


If you are really paranoid you could install and configure bastille linux hardening system

But both of these are aimed at servers that are hosting websites or email

---

