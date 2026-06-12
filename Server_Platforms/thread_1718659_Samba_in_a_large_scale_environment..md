---
title: "Samba in a large scale environment."
date: 2011-03-31
forum: Server Platforms
---

### Post by Roasted on 2011-03-31
I've used Samba heavily, but only for home use. I began to wonder about something. Let's say I work in a school where there are hundreds of students and we have 1 file server in question. The Linux samba server would be part of the Windows domain. Let's say it was structured like this:

[LIST]
[*]FileServer
[LIST]
[*]Students
[LIST]
[*]Class Of 2011
[*]Class of 2012
[*]Class of 2013
[*]Class of 2014
[/LIST]
[/LIST]
[/LIST]

What's the best way to add shares for all of the students, assuming there is 200 students per folder? Is there a way to add a wildcard like $(USER) (that's logged in) = //fileserver/students/classof2011/Bill_Gates?

Or would a directory path have to be created for each student?

Either way is fine. I'm just curious what the proper protocol is for completing that task.

---

### Post by Thund3rstruck on 2011-03-31
Samba supports logon scripts, roaming profiles, and all that. At least it does when used as a PDC. I don't have much experience using samba as a member server on a windows domain so I can't say for certain how well it works in that function. 

[http://daniel.fiser.cz/?samba]("http://daniel.fiser.cz/?samba")

---

