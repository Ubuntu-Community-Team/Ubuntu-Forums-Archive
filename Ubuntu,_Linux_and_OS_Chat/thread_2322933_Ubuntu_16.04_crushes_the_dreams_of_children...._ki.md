---
title: "Ubuntu 16.04 crushes the dreams of children.... kittens and puppies too."
date: 2016-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-05-01
So what's up!?! Where's Secret Maryo?!? My kids are devastated. This and other games, like inertia, have vanished!?! Is there a way to install these from 15.10's repository?

---

### Post by mikodo on 2016-05-01
I had a situation last new install from 12.04 to 14.04 where I couldn't open bcrypt. I used that then for my passwords.

I uninstalled bcrypt in 14.04. Then, went into Synaptic > Settings > Repositories > Updates and shut off all updates.

Then, went to[ this site]("http://wiki.ubuntu-it.org/Repository/SourcesList"), and copied over the old Repositories for 12.04 into Synaptic > Other Software. 

Then, un-ticked the present 14.04 repositories. 

Then, downloaded bcrypt from Synaptic again, which was the older version and dependencies and I could open it with my passphrase. 

I moved my data to gpg locked file and deleted bcrypt forever, Deleted the old repositories and set everything as before for 14.04 in Synaptic.

That worked for me with no ill side effects.

Addendum. Of course if you are comfortable doing this in /etc/apt/sources.list that would have worked for me too. I did it lots in Debian. I wanted to see it all graphically in Synaptic, to be sure I "covered all my bases". Funny, I just looked in mine and I don't see the un-commented  12.04 repos so, I must have removed them myself later. I can't remember. Oh, I just remembered. I had to re-installed after having to put in a new disk and again after a corrupted 14.04 install due to a power outage. Okay, I'll shut up ...

---

### Post by neu5eeCh on 2016-05-01
Well, I just spent the last two hours trying to compile Secret Maryo from their tarball and their (utterly useless to anyone but hackers) instructions. It was just one fractal rabbit-hole after another. I *have*  successfully compiled software before, but this is just way beyond my pay scale. This:

"If compiling a recent GIT version on Linux, you will be required to have  CEGUI 0.7, which is not included in most modern distros' package  managers. You will therefore be required to compile the libraries  yourself."

Brought me to my knees. Instructions for installing this anomaly are scattered higgelty piggelty, like the exploded pieces of the Tardis, in every possible time and dimension. The [developer's own instructions]("http://cegui.org.uk/wiki/CEED") don't work for god's sake--and for all I know these aren't even the right instructions. How would I know? Every time things get tough, the instructions get uselessly cryptic: something like "oh yeah, and be sure to enable OPENGL while you're compiling".

Funny how Linux devs may be brilliant developers but couldn't instruct their way out of a wet paper bag.

ANYWAY..........

I may try your method. I really thought there was an easier way though...

---

### Post by SuperFreak on 2016-05-01
[https://sourceforge.net/projects/smclone/]("https://sourceforge.net/projects/smclone/")

Would above deb file not work?

---

### Post by neu5eeCh on 2016-05-01
I'll try that, though it's a fairly old version. The current version is 1.9. The deb is 1.5 (and it may need dependencies). 

I just tried installing the Debian Jessie smc.deb but to no avail -- wrong dependencies. I can't fathom why SMC isn't in Xenial unless they're planning a Snappy package. As it is, I'm going to have to re-install 14.04 for my kids unless something turns up.

---

### Post by SantaFe on 2016-05-01
Checked the PPA page, but when the last version was successfully built 347 weeks ago, doubt it would work. 

But here's the link anyway: [https://launchpad.net/~smc-packagers/+archive/ubuntu/ppa](https://launchpad.net/~smc-packagers/+archive/ubuntu/ppa)

---

### Post by mc4man on 2016-05-01
Removed from xenial because it was removed from debian testing due to no longer being able to build with the new cegui libraries & no sign of further development 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=812096](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=812096)

---

### Post by neu5eeCh on 2016-05-01
Thanks mc4man. That explains it. What a pity... My daughter is/was really into it. Using it to build her own levels (which is why I don't think 1.5 would work).

I read the bug report. Makes me feel better. Thought I was a wretched fool for not getting beyond the "No package 'CEGUI-OPENGL' found" error while compiling. Turns out there are/were much bigger issues.

@ SantaFe. Saw that PPA, but no support for Xenial, let alone Precise. All old stuff. 

My solution is to keep 14.04 on a separate partition until the kids move on. It does seem, though, that SMC would be a prime candidate for snappy.

---

