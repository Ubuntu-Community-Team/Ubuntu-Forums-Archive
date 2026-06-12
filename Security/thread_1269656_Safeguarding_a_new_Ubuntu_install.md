---
title: "Safeguarding a new Ubuntu install"
date: 2009-09-18
forum: Security
---

### Post by lordewoks on 2009-09-18
I recently reformatted my sister-in-law's computer.  Rather than reinstall Windows, I decided to try Ubuntu on them instead.  They aren't technical at all (most basic user) and mostly use the computer for web browsing, email, uploading pictures, etc.  They also occasionally use the computer to do some sensitive financial transactions over the web, so I want to make sure that the computer is secure for them. 

What steps can I take to safeguard their computer after a fresh install?  How can I restrict root access from them?  What sort of functionality will they be without if I do take away root access?  How can I protect them from inadvertently executing malware? Does it make sense to install AV for them?

---

### Post by imbjr on 2009-09-18
For my folks, I gave them an admin account for updates and for each of them a restricted users account where they can't b0rk anything.

---

### Post by phillw on 2009-09-18
Don't let them near a root login !!! - Best practice is to disable it. 

As mentioned, set up an admin account for updates, and leave them as normal users.

You'll be using Firefox, so put on NoScript (It's an 'add-on') - as suggested above.

As a matter of habit I also put on WOT (Web Of Trust) - that way, when you use popular search engines, it flags the returned sites like traffic lights.

'Teaching' NoScript takes a little while, but it's well worth the effort.

As for AntiVirus - If it's a Ubuntu only machine - you need not bother.

You *can* instal the likes of BitDefender if they are going to share downloads **TO** a windoze machine, but, if they're sticking to Ubuntu - It's one less thing to worry about :P

Welcome to Ubuntu & I'm sure your folks will be really impressed with how smoothly it runs :lolflag:

Regards,

Phill.

---

### Post by tripolitan on 2009-09-21
1-Give the user "root" a password (from gnome admin/users)
2-Dont give the root password to your sister-in-law.
3-Remove sudo (using synaptic)

Note that when you do that, you'll have to use su (then password) to switch to root console, all programs that require root access will not function with the user's password and will only function with the newly-created root password from step 1.

4-Firefox is very secure with financial transactions the way it is. You need not slow it down with any addons.

"Safeguarding" is a windows term, as far as desktop computers are concerned. There are no known trojans or viruses or malware for GNU/Linux apps. If your sis-in-law knows the difference between phishing and genuine, you shouldn't have anything to worry about, if not then no operating system can help.

---

### Post by bodhi.zazen on 2009-09-21
> **tripolitan said:**
> 1-Give the user "root" a password (from gnome admin/users)
2-Dont give the root password to your sister-in-law.
3-Remove sudo (using synaptic)

Note that when you do that, you'll have to use su (then password) to switch to root console, all programs that require root access will not function with the user's password and will only function with the newly-created root password from step 1.

4-Firefox is very secure with financial transactions the way it is. You need not slow it down with any addons.

"Safeguarding" is a windows term, as far as desktop computers are concerned. There are no known trojans or viruses or malware for GNU/Linux apps. If your sis-in-law knows the difference between phishing and genuine, you shouldn't have anything to worry about, if not then no operating system can help.

I am sorry, but that ^^ is horrible advice.

There is no need for any of that, simply configure sudo properly. Users in the admin group have root access. If a user needs root access to some commands, but not others, again configure sudo, that is what sudo does best.

Out of the box Ubuntu is more secure then a hardened Windows installation.

If you wish to go beyond that, see the security sticky ;)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by MechaMechanism on 2009-09-21
> **tripolitan said:**
> 1-Give the user "root" a password (from gnome admin/users)
2-Dont give the root password to your sister-in-law.
3-Remove sudo (using synaptic)

Note that when you do that, you'll have to use su (then password) to switch to root console, all programs that require root access will not function with the user's password and will only function with the newly-created root password from step 1.

4-Firefox is very secure with financial transactions the way it is. You need not slow it down with any addons.

"Safeguarding" is a windows term, as far as desktop computers are concerned. There are no known trojans or viruses or malware for GNU/Linux apps. If your sis-in-law knows the difference between phishing and genuine, you shouldn't have anything to worry about, if not then no operating system can help.The better and right way would be to create a non-admin account for the user and restrict the admin sudo account to those qualified.  What you are suggesting is unsupported on the Ubuntu forums.  In addition the removal of sudo risk a tremendous amount of breakage and greatly complicates the maintenance of the machine.  To the original poster, I would do a fresh install and the default acount is an admin account.  I would then create a second account that was non admin.

---

### Post by MechaMechanism on 2009-09-21
> **bodhi.zazen said:**
> I am sorry, but that ^^ is horrible advice.

There is no need for any of that, simply configure sudo properly. Users in the admin group have root access. If a user needs root access to some commands, but not others, again configure sudo, that is what sudo does best.

Out of the box Ubuntu is more secure then a hardened Windows installation.

If you wish to go beyond that, see the security sticky ;)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")You beat me to it.  Listen to bodhi.zazen, he is a good authority.

---

