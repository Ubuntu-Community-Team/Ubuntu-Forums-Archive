---
title: "Scanning for Windows viruses"
date: 2007-01-05
forum: Server Platforms
---

### Post by Pobega on 2007-01-05
I'm downloading Microsoft Frontpage for my father's computer, but he is very computer-anal. He has loads of Photographs (He's a photographer) and videos stored on his computer that he would kill if he lost, and it would be me he killed if my frontpage download got him!

So I'm wondering; Are there any virus scanners for Linux that can scan single directories (Just my /home/$USER/downloads directory) for **Windows** viruses?

---

### Post by jpeddicord on 2007-01-05
AVG Free for Linux scans for Windows viruses:
[http://free.grisoft.com/doc/5390/lng/us/tpl/v5](http://free.grisoft.com/doc/5390/lng/us/tpl/v5) (Warning: .RPM)

ClamAV is a more commonly used scanner, although it is terminal based:
[http://www.clamav.net/](http://www.clamav.net/) (Also available via APT, search Synaptic for 'clamav' and install whatever combination of packages you want)
You may be able to find a GUI for it however.

Jacob

---

### Post by kylevan on 2007-01-05
another option would be to not download things from warez sites and legally purchase software whose license requires it. [-X

---

### Post by chrisfay on 2007-01-05
From office.microsoft.com:
> After nine years of being an award-winning Web authoring tool, FrontPage will be discontinued in late 2006

The successor packages to Frontpage are offered in the 2007 Office trial Package. Free to download.

> another option would be to not download things from warez sites and legally purchase software whose license requires it.

Self-righteous banter.....

---

### Post by kylevan on 2007-01-05
what, because I have purchased licenses for commercial software that I have used and consider stealing wrong I'm self-righteous?

---

### Post by chrisfay on 2007-01-05
No, your moral projection reaks of it.

---

### Post by Pobega on 2007-01-06
He has the disc but he lost it when he moved out of the house, so I am getting him a new one. Why should he have to buy it twice?

---

### Post by tturrisi on 2007-01-06
> **Pobega said:**
> He has the disc but he lost it when he moved out of the house, so I am getting him a new one. Why should he have to buy it twice?
If he lost his car keys should the dealer give him another set of keys for free?  If he lost his driver's license should the state give him another one for free?  One needs to be responsible for one's posessions.  Thoughtlessness, carelessness, etc are things we all experience in our lives at some point, no one is perfect.  But we do need be responsible for our actions and our shortcomings.  "Stealing" can be justified a hundred billion ways.  The bottom line is always this:
The common denominator of ALL criminality is "something received for no exchange".
Anybody that "stomps" on someone's promotion of honesty is himself too a criminal, has low personal integrity and is NOT to be trusted.  No single person here has never done something they should not have done.  Every person is guilty of having done something they knew to be incorrect at some time or another.  But that too does not justify criminality.  And is the reason why honesty needs to be continually promoted by honest people.

note:  my words will ONLY be criticized by dishonest people!

re Front Page:   if you have proof of purchase you can get another disk from MS.

---

### Post by Biggus on 2007-01-06
Yes, but when his father paid for the software originally, he wasn't paying for the medium, he was paying for the licence to use the software. The 
chap already has a licence to use the software, so how can he steal that which he already owns?

---

### Post by Pobega on 2007-01-06
> **tturrisi said:**
> If he lost his car keys should the dealer give him another set of keys for free?  If he lost his driver's license should the state give him another one for free?  One needs to be responsible for one's posessions.  Thoughtlessness, carelessness, etc are things we all experience in our lives at some point, no one is perfect.  But we do need be responsible for our actions and our shortcomings.  "Stealing" can be justified a hundred billion ways.  The bottom line is always this:
The common denominator of ALL criminality is "something received for no exchange".
Anybody that "stomps" on someone's promotion of honesty is himself too a criminal, has low personal integrity and is NOT to be trusted.  No single person here has never done something they should not have done.  Every person is guilty of having done something they knew to be incorrect at some time or another.  But that too does not justify criminality.  And is the reason why honesty needs to be continually promoted by honest people.

note:  my words will ONLY be criticized by dishonest people!

re Front Page:   if you have proof of purchase you can get another disk from MS.

Internet != Real life. Comparing a software license to car keys is like comparing apples to horses, you just can't do it. I don't want to start an argument though, so let's stop here.

---

### Post by tturrisi on 2007-01-06
> **Biggus said:**
> Yes, but when his father paid for the software originally, he wasn't paying for the medium, he was paying for the licence to use the software. The 
chap already has a licence to use the software, so how can he steal that which he already owns?
Read the license agreement that is on the cd.  When you install the software you agree to the terms, else the software won't install!  There's also a copy of that license agreement placed into the install dir.
> Internet != Real life. Comparing a software license to car keys is like comparing apples to horses, you just can't do it. I don't want to start an argument though, so let's stop here
I don't want to argue either.  But to say the the Internet does not equal real life is pretty darn strange!  What exactly do you think the Internet is?  By definition, the Internet is nothing more than connected hardware & wires, satellites & cables, the infrastructure.  That's what the Internet is.  The WWW is all of the documents that reside on computers that are connected to the Internet, that's all the WWW is.  They are 2 distinctly separate things.

The Internet, as you know it, is a part of real life.  There is nothing unreal about it unless one lives in a fantasy world or does not really understand what real life is.  There can be fictional content on the WWW, but that fiction is still real fiction.  Just because the content on the WWW is digitized, it is still real content, it's specialy arranged-stored quantities of magnetized particles that can be manipulated.

---

### Post by chrisfay on 2007-01-06
> judge not lest he be judged

...You don't have to be a religious zealot to realize the overbearing tastelessness when someone forces their moral boundaries on another. I merely illuminated this fact, yet apologize for derailing a perfectly technical question, in a technical forum, that should have been fairly treated without social or moral criticism. 

OP,  jacobmp92 has suggested a good option, ClamAV is an AV that I use for scanning emails on my mail server and does a fantastic job. You can easily scan individual folders manually, or cron a job to do it for you. It is in the repositories.

---

### Post by Pobega on 2007-01-06
I installed Clamav, but I can't figure out how to run it from the command line. Clamav isn't found (As a command), and I couldn't find any documentation on the command to call. Any help?

---

### Post by chrisfay on 2007-01-06
Run:

```
sudo clamscan <directory>
```

....replacing <directory> with what you want scanned.

---

