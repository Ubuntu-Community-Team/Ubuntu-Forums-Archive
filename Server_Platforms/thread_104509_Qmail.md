---
title: "Qmail"
date: 2005-12-16
forum: Server Platforms
---

### Post by davebradford on 2005-12-16
has anybody managed to get qmail working on ubuntu server using the qmailrocks guide? or is there an easier way of getting a mail server without using qmail??

---

### Post by ubuntumaneh on 2005-12-16
I haven't use qmail in Ubuntu. I used to use it in debian.

In Ubuntu, I followed this [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by davebradford on 2005-12-16
whats the difference between postfix and qmail?

---

### Post by ubuntumaneh on 2005-12-16
the kind of license. Qmail is more restrictive. Also, postfix is way simpler. But that is not the problem. I believe there is no problem installing qmail in ubuntu. I have some programs that have restrictions and I had to build it (pine, for instance), and work nicely.

---

### Post by davebradford on 2005-12-16
so they both provide the same features? i just need a mail server that's going to be secure.. send recieve e-mails and provide spam protection.. maybe even a web client?

---

### Post by ubuntumaneh on 2005-12-16
If you are already familiar with qmail installation, try to do it.
For what I guessed, you were in the some foot I were (i was used to qmail), but postfix is here, installation is much easier, and everything you want is there. Follow that how-to.

---

### Post by LordHunter317 on 2005-12-16
Don't use qmail in new installations.

If you haven't learned postfix or exim4 already, please do so now.

Postfix is far eaiser to setup and I think you'll find superior.

---

### Post by davebradford on 2005-12-16
if i was to sit down complete the install in a perfect world how long do you think i mite take? when i first did the qmailrocks install it took me about a day.. :(

---

### Post by LordHunter317 on 2005-12-16
With Ubuntu or Debian?  You can have a basic server running instantly, at install.  It depends all what you need around it, but a day or so.  Details on your setup would be nice.

---

### Post by caraboy on 2005-12-17
By the way, I recently switched to Ubuntu from a rpm based distribution, such as red hat or mandrake (mandriva now). Well, I`ve been using sendmail and xinetd services to host a mail server since my first encounter with linux... so it is hard for me to switch to postfix. Do I have a chance with sendmail in Ubuntu?

---

### Post by davebradford on 2005-12-20
from what i've been readin rpm distros like q-mail deb like postfix.. seems to be the general feeling but i'm sure they're both run on both distros

---

### Post by Gowator on 2005-12-21
[QUOTE=LordHunter317]Don't use qmail in new installations.

If you haven't learned postfix or exim4 already, please do so now.

Postfix is far eaiser to setup and I think you'll find superior.[/QUOTE]

Yea and No....

Postfix is far easier to set-up, qmail is way superior if you have the time or if its set-up for you.

---

### Post by LordHunter317 on 2005-12-21
Superior how so?  It has to be patched; you can't distribute binaries; no one can legally mantain it in any useful way; it's slightly slower and less scalable; it's configuration is infinitely more complicated.

The only good thing going for qmail is vpopmail.

---

### Post by ubuntumaneh on 2005-12-21
It is very hard to say qmail is superior. I don't see where? What I sure know is that postfix is way easier to set up. Now, if you really know qmail, you may feel at easy installing it and its patches. At the end this is what matters, for both, qmail and postfix are good. I have installed both qmail (in my debian old days) and postfix (now in ubuntu), and next time I have to install I will go for postfix.

edit: Im afraid this discussion may become a emacs/vi, ubuntu/kubuntu type of discussion. It may be good in a sense, for we all may learn both program at least at information level, but in the end is a question of adaptability and taste.

---

### Post by LordHunter317 on 2005-12-21
[QUOTE=ubuntumaneh]Now, if you really know qmail, you may feel at easy installing it and its patches. At the end this is what matters, for both, qmail and postfix are good.[/quote]See, but there are more important issues than that.

No one can properly maintain the qmail codebase besides DJB, and he's not willing to do so.  If and when a bug is discovered, you're completely reliant on your own coding ability to patch it, the vain hope he'll patch it, or someone else in the community.  Not a situation I want to trust production software to.

That above all other reasons is why one should use postfix: you're stuck high and dry when there is a code problem.  And the code hasn't ever been externally audited by a trusted party so there's no way to say it won't have them.

---

### Post by ubuntumaneh on 2005-12-21
Thanks for the information. I was not so completely aware of all this. I used qmail for two years, and I had experienced no problem at all. However, I completely agree with you now. If I had a problem, I would be stucked and at least I would have learned the hard way all these informations you just told me about. Now, I know some people that use qmail, and they are not willing to give that up.

---

### Post by davebradford on 2005-12-22
i've been looking thru a good postfix guide and it looks very hardcore.. i might have to setup a test server for a little bit to see if this baby works.. wot do you guys suggest?

---

### Post by godlike on 2007-01-17
I dont know why ppl say postfix is simple to setup. If yer using it out of the box it is but if u want virtualhosts or other auth types its been a pain in the ***. All the howtos never seem to work =( Qmail on the rpm distros is simple if ya use qmail toaster guide.

---

