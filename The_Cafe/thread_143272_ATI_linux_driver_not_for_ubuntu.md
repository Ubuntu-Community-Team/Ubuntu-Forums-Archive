---
title: "ATI linux driver not for ubuntu ?"
date: 2006-03-12
forum: The Cafe
---

### Post by newbie2 on 2006-03-12
> he latest version of the ATI Proprietary Linux driver is designed to support the following Linux distributions:

    * Red Hat Enterprise Linux suite
    * Novell/SuSE product suite 
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.23.7-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.23.7-inst.html)
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=1177](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=1177)
:confused:

---

### Post by evilgold on 2006-03-12
That just means thats what ATI offically supports, they arent going to alienate users of other distros (unless they are retarded). It would really be impossible to expect for any hardware maker to support ALL linux distros. 

Unfortunetly RPM is still the standard.

---

### Post by knalle on 2006-03-12
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by bjweeks on 2006-03-12
Use the drivers in the repos

---

### Post by knalle on 2006-03-12
[QUOTE=bjweeks]Use the drivers in the repos[/QUOTE]

i dont know, does universe contain ati drivers that gives ati opengl support? i have tried the repro ati drivers and they only gives me mesagl software support, what do i do wrong?

---

### Post by bjweeks on 2006-03-12
[QUOTE=knalle]i dont know, does universe contain ati drivers that gives ati opengl support? i have tried the repro ati drivers and they only gives me mesagl software support, what do i do wrong?[/QUOTE]

Yes, they are in restricted.

---

### Post by knalle on 2006-03-12
[QUOTE=bjweeks]Yes, they are in restricted.[/QUOTE]

thanks!, i haven't enabled **restricted** i think, only universe and multiverse

it would be great if you could enligthen ous with perhaps a little bit more info since both of us OP seems to be in the gray here, Ubuntu Breezy doesnt enable opengl hardware for ati by default so it is a valid question

---

### Post by bjweeks on 2006-03-12
[QUOTE=knalle]thanks!, i haven't enabled **restricted** i think, only universe and multiverse

it would be great if you could enligthen ous with perhaps a little bit more info since both of us OP seems to be in the gray here, Ubuntu Breezy doesnt enable opengl hardware for ati by default so it is a valid question[/QUOTE]

It is enabled by default. So use the fglrx package from restricted not from ati site.

---

### Post by knalle on 2006-03-12
[QUOTE=bjweeks]It is enabled by default. So use the fglrx package from restricted not from ati site.[/QUOTE]

well ok, but i have done the ubuntu breezy 5.10 installation on my 4 computers that got 3 ati cards, it autodetects ATI and finnishes up.

on all my 3 ati computer fglrxinfo says mesagl and wont run opengl games as ET, then i change to fglrx drivers, from restricted and still only mesagl.

the previous posted how-to is the only way i have found to play open gl games like ET, so please tell me how i can do this simpler because i have 3 computers with ati cards :confused:

---

### Post by knalle on 2006-03-12
oh well, saved by someone that actually know what she/he talks about;

[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

---

### Post by bjweeks on 2006-03-12
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

---

### Post by knalle on 2006-03-12
thanks, that was helpful, was it that hard to post that link in the first plase? or have we played out your game right now so you can boost your ego by just sating the RTFM obious en the end of a thread where you have refused to come up with this easy esxlpanation in more than 3 posts, troll!

---

### Post by bjweeks on 2006-03-12
Sorry I lost my spoon. Also this is a thread in Community Chat about ATI driver surport not a help thread. Thinks I love being a troll:rolleyes:

---

### Post by bjweeks on 2006-03-12
[QUOTE=knalle][http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)[/QUOTE]

The best way to install the ATI drivers is follow the guide drivers [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver"), unless you have a issue that is fixed by newer

---

### Post by knalle on 2006-03-12
[QUOTE=bjweeks]Sorry I lost my spoon. Also this is a thread in Community Chat about ATI driver surport not a help thread. Thinks I love being a troll:rolleyes:[/QUOTE]

opps, MY MISTAKE, i didn't see this was a community discussion, i thought it was a support question.... :oops: please ignore my rant

---

### Post by bjweeks on 2006-03-12
no problem...

---

### Post by knalle on 2006-03-12
so are the binary modules in the restricted repro just precompiled versions of ati.com's binary modules?

---

### Post by bjweeks on 2006-03-12
[QUOTE=knalle]so are the binary modules in the restricted repro just precompiled versions of ati.com's binary modules?[/QUOTE]

Yep but they are pre-configured and tested so your better off running the repo drivers.

---

### Post by knalle on 2006-03-12
you know i thought the ati drivers wasn't even in restricted, but thats because i'm used to debain sarge where nothing is included because of lisensing issues. thats why i have started to use ubuntu anyway, to get a little looser on the restrictions :-) thanx!

and, [http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283) this? can i just ingore that too if i use the info in the help.ubuntu, i tried it and that fixed ati opengl on my last ati machinae while we spoke?

---

