---
title: "Hardy vs. Etch?"
date: 2008-05-05
forum: Server Platforms
---

### Post by Luke has no name on 2008-05-05
Which is better on:

-Stability
-Ease of Installation (Including initial server installs, like LAMP/mail/SSH/etc.
-Ease of package installation
-Performance

I have my hypotheses, but I'd like to see what others have to say before I chime in.

---

### Post by hyper_ch on 2008-05-05
Etch

Not as new packages as Hardy but Debian is rockstable. Installtion and package management is the same (Ubuntu is Debian based).

As this is the server section then i assume, you will not install gui on it. For package management sue then apt-get or aptitude from the cli.

---

### Post by Luke has no name on 2008-05-06
Anyone else?

---

### Post by agim on 2008-05-06
two different animals, though of course related.

If you want stability and performance, certainly Etch. If you want the latest and greatest programs and technologies, then Hardy is the choice.

Thats oversimplified, but I think its what you are looking for.

---

### Post by FakeOutdoorsman on 2008-05-06
It depends on what you are planning on using the machine for.  If it is for home or hobby use, then Ubuntu Server is great.  If it is for business, especially if you will have client data on the machine, go with Debian Etch.

Stability: Debian
Ease of Installation: Ubuntu, but fairly similar
Ease of package installation: Same
Performance: Either. Depends on the "heft" or customization of your install.

---

### Post by koenn on 2008-05-06
> **agim said:**
> two different animals, though of course related.

...  If you want the latest and greatest programs and technologies, then Hardy is the choice.

Etch is quite recent, so the difference in "latest and greatest" is going to be relatively minor. 
If you're planning to track LTS (not unusual unless you're planning on upgrading/re-installing that server every six months), "latest" is of relative importance anyway.

Ubuntu may be more advanced / soffisticated in integration, especially the pre-defined tasks (eg LAMP), but the basic tools (apt, dpkg) and the software are the same as debian's.

As long as we're talking servers without GUI, you'd have trouble telling the difference between one and the other once they're setup, except maybe for the difference in su / sudo.

---

### Post by songshu on 2008-05-07
etch +1

no doubt about it

---

### Post by juan@forum on 2008-05-08
etch is a excellent choice, but maybe it is not what you want

i used a lot in my office in all my servers


but...

one cool thing about ubuntu is that you can get official support from canonical

for an organization or company is really nice to know you can get some support in the case you will need it

i would use ubuntu server TLS edition, in that way your server will be stable for at least five years


etch will be old stable at the end of this year.

---

### Post by songshu on 2008-05-08
> **juan@forum said:**
> 


etch will be old stable at the end of this year.

lol ;)

you want to make a bed that it isn't ?

---

### Post by juan@forum on 2008-05-08
> **songshu said:**
> lol ;)

you want to make a bed that it isn't ?

Taken from the the debian lists:

-------------
Now on to the draft of the timeline:

August 2007
  Start of the first BSP marathon for Lenny, lasting till November. [1]

Early September 2007
  The list of release blockers for Lenny is frozen.

Early March 2008
  Very soft freeze: Please be extra careful with new versions, and new
  transitions.  At this point, the list of release goals is frozen.

  Start of the second BSP marathon for Lenny.

Early April 2008
  Freze of the essential toolchain.

Mid of June 2008
  Freeze of the non-essential toolchain and all libraries.

Mid of July 2008
  Full freeze.

Early September 2008
  Release!

Of course, "Early September" is only an internal goal as of now, the
official communications is "in the second half of 2008".
-------------

---

### Post by Monicker on 2008-05-08
Debian has always been noticeable faster than Ubuntu on my laptop.  I'm running a combination of Etch and Lenny packages at the moment.  I use apt-pinning to have the Lenny packages available, but only install them when I want or need them.  Stability has been great.  I do all my package management from the command line, but you can still install Synaptic.  I run mysql, apache, postfix, and a number of other services on it.

---

### Post by songshu on 2008-05-08
> **juan@forum said:**
> 
Of course, "Early September" is only an internal goal as of now, the
official communications is "in the second half of 2008".
-------------

great, 

that would mean release somewhere mid 2009
lenny will not ship intil its ready and bugs are squashed

---

