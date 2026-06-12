---
title: "Software removal for hardening desktop"
date: 2010-09-01
forum: Security
---

### Post by hedon on 2010-09-01
Hi

I use my desktop (VM) for online transactions only (it has no other purpose) & have removed most   software. In adidtion want to remove Archive Manager, Calculator,   Multimedia systems selector, Printing,  sound recorder, Terminal  (gnome-terminal), terminal server client,  Ubuntu One. When I attempt to  remove the listed software, I receive a  waring message "no future  desktop updates will include if you remove  this".** I want to know if  this will impact  the updates for Firefox as  this is the only app I  need. Can you please advise on any other consequences if I proceed with the above?**

Thanks in advance for your help

---

### Post by OpSecShellshock on 2010-09-01
Removal of Archive Manager will result in not being able to extract archived files, which is the form updates are in prior to installation. This would include updates for the web browser. The gnome-terminal is also quite essential. Honestly you don't gain anything from a security standpoint in removing any of those packages that you've listed. That's especially true if you're running this stuff in virtual machines, which can largely be treated as disposable (in fact, one could argue that a full installation is disposable enough as well, provided that your personal files and settings and things are stored on a separate drive).

Surely if you go that route, you'd want to update software first thing. There are no risks with the existing default setup because all of that software comes from the official repositories.

---

### Post by bodhi.zazen on 2010-09-01
IMO you are far better off starting with a minimal system and build up, installing only what you want, then you are removing applications.

If you do not know what an application is, you will need to look it up.

---

