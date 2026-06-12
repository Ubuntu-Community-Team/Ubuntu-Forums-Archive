---
title: "VMware Outlook 2007 copy to Linux bug"
date: 2008-08-19
forum: Virtualisation
---

### Post by mrbrice on 2008-08-19
Linux darkhelmet 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

Hardy Ubuntu 8.04.1

VMware Server 1.0.6 build-91891

----

I've searched for this, but I can't seem to get anywhere. I've come across a strange bug in VMware when copying text from an Outlook email that contains a form/pasted excel table (whatever you want to call it). 

For example, I have a vmware session that runs Windows XP SP3 with Office 2007. In Outlook, I have an email that has a pasted row from excel. If I try to copy any text within the table, or if I try to copy any text at all from the email itself, and then try to paste somewhere (anywhere) in linux, it disables the ctrl/alt/shift keys, and if I try to open any other windows in linux, be it a terminal, or anything, and then I hit any keys on my keyboard it closes the window.

To solve this, I've just been logging out and logging back in again, which solves the problems in linux, but if I were to try to copy anything out of the email in Outlook it would do it again. This only occurs with emails with forms/tables in them. Any other email I've come across, any other other time copying and pasting from my windows session works fine. 

If I go into excel or access or anything having to do with Office 2007, it doesn't have any issues. It's strictly when copying from an email containing such a form/table.

This all might sound confusing, but I'm curious if anyone has come across anything like this before. -- shot in the dark tbh.

Any insight would be great.

Cheers

---

### Post by mrbrice on 2008-08-20
bump

---

