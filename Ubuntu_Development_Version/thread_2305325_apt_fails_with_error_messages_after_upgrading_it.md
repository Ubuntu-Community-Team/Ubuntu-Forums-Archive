---
title: "apt fails with error messages after upgrading it"
date: 2015-12-04
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2015-12-04
After upgrading apt to version 1.1.3 and executing "apt-get update" I have noticed several errors. It ended up in cleaning /var/lib/apt/lists and now I'm getting error messages like "Couldn't create tempfiles for splitting up /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-securi" on executing "apt-get update". These error messages sum up in GPG errors at the end. Has somebody an idea how to fix this?

---

### Post by flocculant on 2015-12-04
that's why I don't install from -proposed

try grabbing apt from [http://packages.ubuntu.com/xenial/apt](http://packages.ubuntu.com/xenial/apt) if you've not got the old version in /var/cache/apt and installing it
> 
xnox	ThiagoCMC, humans should not run -proposed on the devel release.	00:36
xnox	ThiagoCMC, it's not meant for end user consumption, and only for automated systems. it has all abi transitions in progress, and shall be used by buildds only, and automated testing. once things are good, things migrate to release pocket. Hence for "rolling" release one should run devel release only, without -proposed enabled. -proposed has like 700 broken packages at the moment. Whereas devel without -proposed should be entirely installable.	00:37
xnox	and we remove things from -proposed when we realise we uploaded really broken things, that fail testing.	00:38
xnox	(e.g. autopackage tests, and britney transitions, arch skew etc.)

---

### Post by mc4man on 2015-12-04
If you want to revert  apt from -proposed back  to current then you'll need to first remove libapt-pkg5.0 or it won't happen

---

### Post by zika on 2015-12-05
I knew I'm not human... ;) Could I get that in writing (hard copy preferably)?... ;=)
> [COLOR=#000000][I]xnox	ThiagoCMC, humans should not run -proposed on the devel release.	00:36

[/I][/COLOR]

---

### Post by cariboo on 2015-12-05
> **zika said:**
> I knew I'm not human... ;) Could I get that in writing (hard copy preferably)?... ;=)


flocculant can be a bit obtuse at times, it looks like a quote from an IRC log. :)

---

### Post by flocculant on 2015-12-05
hah - I just assumed zika was a strawberry not human so didn't comment further :P

it was a #ubu-dev log from the other day

---

### Post by QDR06VV9 on 2015-12-05
That's what we love about [COLOR=#000000]flocculant.
Sometimes I need that cold slap of reality..[/COLOR]:D

---

### Post by zika on 2015-12-05
> **flocculant said:**
> hah - I just assumed zika was a strawberry not human so didn't comment further :P[img]http://thumbs.dreamstime.com/z/happy-strawberry-thumbs-up-character-funny-cartoon-smiling-isolated-white-background-eps-file-available-40375319.jpg[/img]

---

### Post by ventrical on 2015-12-05
> **runrickus said:**
> That's what we love about [COLOR=#000000]flocculant.
Sometimes I need that cold slap of reality..[/COLOR]:D

Ahahhaaa .. ! I finally get it ! :)

Regards..

---

### Post by grahammechanical on 2015-12-05
Machines don't have any fun.

My biological component enabled the proposed repository in the certain knowledge that the mechanical component will simply activate self-repair (otherwise known as re-install) when needed. Meanwhile, the logic component (A.K.A., the Mind) remains as befuddled as ever.

It is my guess that somebody went to the wrong place for help.

---

### Post by flocculant on 2015-12-05
> **grahammechanical said:**
> ...

My biological component enabled the proposed repository in the certain knowledge that the mechanical component will simply activate self-repair (otherwise known as re-install) when needed. ...

I pick and choose bits and pieces - generally when I've seen something and expect a fix.

I'd not pick apt ;)

---

### Post by ventrical on 2015-12-05
> **flocculant said:**
> that's why I don't install from -proposed

try grabbing apt from [http://packages.ubuntu.com/xenial/apt](http://packages.ubuntu.com/xenial/apt) if you've not got the old version in /var/cache/apt and installing it

On xubuntu xenial I had a pretty well busted desktop but i was able to get to terminal  and keep updating/upgrading and

```

sudo -i dpkg --configure -a

```

equals fixed desktop (xubuntu) but I doubt it would work with unity, mate or gnome.

Regards..

---

### Post by ventrical on 2015-12-05
ubuntu-gnome not affected either (here at least) and I have been updating/upgrading (using apt) from the proposed repo religiously. :)

---

### Post by QDR06VV9 on 2015-12-05
> **ventrical said:**
> ubuntu-gnome not affected either (here at least) and I have been updating/upgrading (using apt) from the proposed repo religiously. :)
Who is this masked man? Oh Yeah now I remember Ventrical..;)
Yeah pretty much the same here with Ubuntu, Mate, Gnome.
I have only had one Glitch since the beginning, Outside of me trying to tweak to hard on it.:D
You know if it aint broke   tweak it harder.LOL
Regards

---

### Post by ventrical on 2015-12-05
+1 :)

---

### Post by Sworddragon on 2015-12-05
> **grahammechanical said:**
> It is my guess that somebody went to the wrong place for help.

Not unlikely I went indeed to the wrong place but then not for the reason you might think :P


Downgrading does work as a workaround as expected but maybe somebody would had been known a workaround to fix this on apt 1.1.3.

---

