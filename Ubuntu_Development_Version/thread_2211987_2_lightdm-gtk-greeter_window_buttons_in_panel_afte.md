---
title: "2 lightdm-gtk-greeter window buttons in panel after login."
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-03-18
I have both the 64 and 32 bit versions of Lubuntu 14.04 running in VMs of VirtualBox.  The 32 bit system is running fine, and sometimes the 64 bit system also is OK, but mostly after logging in to the 64 bit OS I am left with two window buttons in the panel, which I have put at the top of the screen, both for lightdm-gtk-greeter, but neither of which do anything, and also a white empty space in the middle of the screen where the lightdm login box was showing previously.

I have managed to get a screenshot which is attached showing what happens.

I have never seen this in the 32bit system, only the 64bit.

Any thoughts; has anyone else seen this?  I have searched launchpad but can find nothing.

This is using an Intel i5-3570K cpu machine with 8GB ram and only the intel cpu graphics, no separate graphic card.

---

### Post by Elfy on 2014-03-19
[https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1290575](https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1290575)

---

### Post by ajgreeny on 2014-03-19
Thanks Elfy.

I have no idea why my search did not find that launchpad bug when I searched, but I've added myself to it now.

---

### Post by Elfy on 2014-03-19
The ways of searching Launchpad are arcane and not for the little people like us :p

I only know about that bug because it's reported on Xubuntu tracker's which I watch ...

---

### Post by ajgreeny on 2014-03-19
Interestingly, I had not seen the problem on my Xubuntu VM 14.04 64bit until today, but nearly always when using Lubuntu 64bit, never the 32bit system.

In Xubuntu a left click on the desktop seems to close those two zombie greeter processes, but the same does not happen in Lubuntu, where I have to logout and in again, sometimes several times; very annoying.

---

### Post by su:bhatta on 2014-03-20
Glad I keep a lookout on U+1 threads everyday.
I have the exact same thing when I login to Ubuntu Studio session. 
But when I use Gnome or KDE sessions in the same install it is not there. Xfce bug, as pointed out by Elfy I guess.
[ATTACH=CONFIG]251306[/ATTACH]

Attaching my screenshot.

---

### Post by Elfy on 2014-03-20
> **ajgreeny said:**
> Interestingly, I had not seen the problem on my Xubuntu VM 14.04 64bit until today, but nearly always when using Lubuntu 64bit, never the 32bit system.

In Xubuntu a left click on the desktop seems to close those two zombie greeter processes, but the same does not happen in Lubuntu, where I have to logout and in again, sometimes several times; very annoying.

I'm waiting to have it happen again here to get lightdm logs into the report - if you see it perhaps you could do that. You'll need to get the lightdm logs as root though.

The report needs lightdm.log x-0.log x-0-greeter.log 

TIA

---

### Post by ajgreeny on 2014-03-20
> **Elfy said:**
> I'm waiting to have it happen again here to get lightdm logs into the report - if you see it perhaps you could do that. You'll need to get the lightdm logs as root though.

The report needs lightdm.log x-0.log x-0-greeter.log 

TIA
I'll try that when I next get the problem.

PS: This is all using VMs in VirtualBox, fully updated, both VB itself and guest VMs.

---

### Post by Elfy on 2014-03-20
Just a footnote - when you get the logs - check for sensitive information before uploading them.

re vm's - I've not actually seen it in a VM - but I do get it in this 'real' install.

---

### Post by ajgreeny on 2014-03-20
I haven't forgotten your request; it's just that the problem has not occurred again since I said I would attach the logs, and I've cold booted many, many times.  Has it been fixed, do you think, by other package updates?

---

### Post by Elfy on 2014-03-20
> **ajgreeny said:**
> I haven't forgotten your request; it's just that the problem has not occurred again since I said I would attach the logs, and I've cold booted many, many times.  Has it been fixed, do you think, by other package updates?

I'm in the same boat - waiting for it to happen again :)

Not at all sure if it's been fixed by something else - the only recent lightdm* package I saw update was the -settings one.

---

### Post by ajgreeny on 2014-03-24
Last night the greeter problem was back for me just after updating my VM Lubuntu 64bit to kernel 3.13.0-19 and rebooting.  I have attached the three log files to the launchpad bug, as requested.

A second kernel update to the same numbered kernel this morning did not result in the problem over several subsequent boots.  Could the specific kernel be the cause?

PS: Is it possible to edit a launchpad comment that I have already uploaded with incorrect information; I could not find any way to do so and therefore had to correct myself in yet another comment.

---

### Post by Elfy on 2014-03-24
> **ajgreeny said:**
> Last night the greeter problem was back for me just after updating my VM Lubuntu 64bit to kernel 3.13.0-19 and rebooting.  I have attached the three log files to the launchpad bug, as requested.

A second kernel update to the same numbered kernel this morning did not result in the problem over several subsequent boots.  Could the specific kernel be the cause?

PS: Is it possible to edit a launchpad comment that I have already uploaded with incorrect information; I could not find any way to do so and therefore had to correct myself in yet another comment.

excellent :)

as far as editing comments - I've never found a way to do that ...

---

### Post by ajgreeny on 2014-03-24
> **Elfy said:**
> excellent :)

as far as editing comments - I've never found a way to do that ...

I spoke too quickly!
I just booted to the VM again and got the two greeter window buttons stuck in panel again, so obviously not just that particular kernel.

PS: Another question about launchpad comments; is it possible to add three attachments to a comment or would I need to tar them into one archive file?  I could not add the three together, nor one after the other as it simply replaced the already attached file, hence my multi posting.

---

### Post by Elfy on 2014-03-24
I really can't answer that - I tend to do what you did - add them seperately.

Funnily enough - I've not had the issue at all since I posted on the bug and then in here.

I'd hope that we get some with the beta testing due to start.

---

### Post by su:bhatta on 2014-03-27
This is now affecting KDE sessions too. After todays update on restart I had this on my KDE session of Ubuntu Studio. 
That had not been the case so long.

Marked it as 'Affects me too'  along with 8 other people!

[ATTACH=CONFIG]251505[/ATTACH]

---

