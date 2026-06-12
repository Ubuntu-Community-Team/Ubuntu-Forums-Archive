---
title: "clamtk issues, clamav scan engine out of date."
date: 2009-04-11
forum: Security
---

### Post by cruiserlinux on 2009-04-11
1. The version of clamtk in software channel is 3.11, current distro in sourceforge is 4.11. calmtk 3.11 will not update virus signatures, period.
2. there is a bug, supposedly reported, for freshclam update. the user is required to login as root, deactivate apparmor, update virus defs, and then reactivate apparmor. 
3. the clamav scan engine in the current distro is 094.2, but the current stable release is 095, is there a time line on incorporation of the new scan engine?

---

### Post by defaultusername on 2009-04-12
cruiserlinux,

ClamAV 0.95 and ClamTK 4.08 are both available in the Jaunty repositories for me.

---

### Post by cruiserlinux on 2009-04-12
i re-checked the software channels on add/remove programs, the clamtk version was still 3.11, and there was no clanav for install. according to the help forum at the clamtk develpper's page on sourceforge.net, the clamav scanning engin is hardwired in the ubuntu system, and he or she was waiting for someone to update it.

if there is a package for installation of clamav 095 scan engine, where can i find it?

if not, does someone have a quick tutorian for installation strait from clamav source code?

---

### Post by JerryP04 on 2009-04-12
Ditto on the problem

According to ClamTk this is a three step process
   Stop apparmor
   update signatures manually
   Start apparmor

I am a Linux newbie, dumber than a brick.  Step one an three are not a problem, but how do you do step two.  

Forty seven years as a computer operator, programmer and systems analyst and sporrt of unis servers and I feel like I am back at step one.  

Old but still learning

---

### Post by hyper_ch on 2009-04-12
are you even sure you need antivirus?

---

### Post by chipppy on 2009-04-13
I have the same problem.  I would like to run clam to help stop virus running through friends windoze emails.

Also being a dumb newbie.
How do I login as root?

Cheers
chipppy

---

### Post by hyper_ch on 2009-04-13
it is against forum policies to tell how to login as root on Ubuntu. Please have a read at the sticky threads in the security section.

---

### Post by Thelasko on 2009-04-15
Same problem here.  I needed to scan some removable media that might be infected.  I installed the clamtk 4.0 .deb file from the sourceforge page, because it was supposed to have a streamlined method of installing updates.  It said it worked, but now I'm not so sure.  

This needs to be easier

---

### Post by cariboo on 2009-04-15
Clamav is a command line tool, to make sure it updates the signatures every day you run in a terminal:

```
sudo freshclam
```

this will create a cron job that starts up every day, and checks for new virus signatures.

As far as it being hard to use. There is really no need for a virus scanner, as there aren't any Linux viruses in the wild. If you think you need to run a av scanner, in order to protect your friends. If their systems don't already have av scanners, they have far larger problems than getting a virus from you.

Jim

---

### Post by chipppy on 2009-04-15
While the lack of linux virus is great.  I feel that each person should take responsibility for cleaning of there own house.

By that i mean that each person should ensure that they dont propergate maliscious software to other users.  This is one of the fundermentals of open source.  

Yes Windoze user and the main target but we as a community should take reasonable steps to help out those poor lost soles in Windoze land.

---

### Post by Thelasko on 2009-04-16
> **cariboo907 said:**
> There is really no need for a virus scanner, as there aren't any Linux viruses in the wild.

Well, I think I just demonstrated a good reason to have a virus scanner, to scan removable media before mounting it on Windows machines.

Anyway, thanks for the advice!

---

### Post by Windsurfer619 on 2009-04-16
Keep in mind that if you keep something like ClamAV running in the background, it can ***severly*** impact system performance. Due to the fact that linux stores many more files of smaller size than windows, your drive access time will be at least 50% slower.

---

### Post by Thelasko on 2009-04-16
> **Windsurfer619 said:**
> Keep in mind that if you keep something like ClamAV running in the background...

I don't think that's possible without some hacking.  Clam is not a real time scanner.

---

### Post by Windsurfer619 on 2009-04-16
Ah. My bad. Then ClamAV sounds good :P

---

### Post by cruiserlinux on 2009-04-16
ok, back to the original question, does anyone have, or can point me towards a description:D on how to update the clamav scan engine?[CENTER][/CENTER]

---

### Post by Thelasko on 2009-04-16
Oh yeah, I almost forgot to mention.  An update came through last night that was supposed to solve this issue.  I'm not sure if it worked.

---

