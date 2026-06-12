---
title: "Generating installation CD w/up-to-date patches?"
date: 2012-03-06
forum: Security
---

### Post by christian.convey on 2012-03-06
I have a catch 22.  After installing Ubuntu, I'm not allowed to connect that computer to any network at all until it passes a vulnerability scan from a 3rd-party tool.

My current solution, which I don't like, is this:
(1) Do the scan, get the report.  If there are any vulneratibilities:
(2) Guess at which packages I'll need to update to make satisfy the reported vulnerabilities.
(3) On another computer, download the packages I think I need from Ubuntu's repositories, and burn them to a CD.
(4) Install those new packages from the CD onto the computer I'm setting up.  GOTO (1)

This process would get a lot easier if I could efficiently update the packages on the newly-configured computer to what's currently present in Ubuntu's repositories.  Getting up-to-date with the repositories generally addresses 90% of the reported vulnerabilities.

Does anyone know how I can get a Ubuntu installation CD/DVD whose packages have already been updated to reflect the most recent security fixes that are present in the repositories?

Or, alternatively, is there a tool I can use to take stock of the packages (and versions) installed on one computer, and ultimately have a DVD that contains every new/updated package needed to bring that computer up-to-date with respect to the current Ubuntu repositories?

---

### Post by CharlesA on 2012-03-06
Have you looked into checking out remastersys? It can create a custom livecd. Not sure if you can install from it tho.

---

### Post by Cheesemill on 2012-03-07
Check out Keryx for installing and updating packages on an offline computer.

[http://keryxproject.org/](http://keryxproject.org/)

---

