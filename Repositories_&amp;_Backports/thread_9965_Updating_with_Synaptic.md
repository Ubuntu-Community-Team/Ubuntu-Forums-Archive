---
title: "Updating with Synaptic?"
date: 2005-01-03
forum: Repositories &amp; Backports
---

### Post by javabiz on 2005-01-03
I'm trying to update using the Debian unstable with Synaptic.  Does anyone know why it doesn't go for the newest version of a program.
For example,  let's select a search for a program called GRAMPS.  Synaptic finds the 1.0.4 version but the Debian unstable shows a 1.0.8 version.   How do I get the newest version through Synaptic if I right click and update is not highlighted?

I'm having trouble--generally--realizing how Synaptic updates to the newest versions--if there's no highlighted update available--when in fact--there is!

Thanks in advance for any help

---

### Post by Sensebend on 2005-01-03
Press reload, then mark all upgrades and apply.

---

### Post by javabiz on 2005-01-03
I thought I did that and it didn't work.  In order to see if what I'm trying to do is doable--could you search on gramps and see if you can do an update on it?  Also--if I have all binary repositories selected and one of them is debian unstable--will it go to that repos to update from 1.0.4 to 1.0.8. 
I tried to do this from the console--but it said it needed a version = or greater to the one I had for Scrollkeeper--which was a dependency issue.

---

### Post by javabiz on 2005-01-03
I found this url with a pdf download that looks interesting.  It may help those coming from another package manager to compare synaptic/apt-get with other managers. 

[http://www.granneman.com/downloads/updatingWithAPT.pdf](http://www.granneman.com/downloads/updatingWithAPT.pdf)

Hope this helps someone. 
Now I just need to find out if 
A.  Synaptic is capable of doing everything apt-get does.
B.   Can Synaptic with ubuntu upgrade with all the new files apt-get does.

Help!

---

### Post by varunus on 2005-01-03
You can use Synaptic's "Force Version" option to select a certain version of the package if multiple versions are available.

Just select the package and choose Package-->Force Version.  (Or press CTRL-E.)

---

### Post by javabiz on 2005-01-03
Thanks!
I haven't tried this yet because I'm at work!   
So basically, is synapitic ap-get with a gui and may I do everthing with synaptic that apt-get may do--including update to any latest and greatest .deb binary?

Also, where I ran into dependency problems from the command line--will synaptic take care of all these automatically?

---

