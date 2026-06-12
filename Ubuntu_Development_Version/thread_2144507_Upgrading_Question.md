---
title: "Upgrading Question"
date: 2013-05-12
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-05-12
As most of you know, i went through the last 3 months of the 13.04 development cycle, and was going to continue into 13.10 development, but in trying to do the terminal upgrade process, things did get messed up for me and i ended up re-installing using 13.04 final iso, which i what i am currently running...so, at this point, i think i may just stay with 13.04...it was a lot of fun through, participating :)

What i thought i may do, is to run 13.04 until 13.10 goes final, and try doing an "upgrade" instead of re-installing...I've heard that if you do it within the first week or so, you have good chance of success...and if it doesn't work out i could always re-install with 13.10 final, though i am hoping i won't have to as i am trying to "cut back" on re-installs ;)

I know you guys here are pretty technically oriented...here's a question for you:

I only use 2 ppas...one is Google Chrome (which is not specific to the version of ubuntu of course) and the other is from web8's website for Oracle Java...the ppa puts an updater in the ubuntu software sources to get newer versions...

1) Now, if the 13.10 version of the ppa is not ready when i upgrade to 13.10, would that ppa still work if it still said raring rather the saucy?

2) Also, when they update that ppa to include saucy, can i simply edit it in ubuntu software sources and change the name part from raring to saucy? (without doing it in the terminal and bringing up the lists in there)...

3) Lastly, when doing the "upgrade" is it important to temporarily uncheck those 2 ppas (chrome updater and the java updater) while the upgrade is taking place?

Thanks...

---

### Post by grahammechanical on 2013-05-12
Something tells me that the upgrade process disables PPAs. It should give you notice about this. So, you will need some user input. You might find that there is not a PPA for Saucy. So, you will have to change the name part back to Raring. It should work.

Regards.

---

### Post by craig10x on 2013-05-12
@grahammechanical: thanks as always...and anyone who can give me some extra feedback on this would be appreciated :)

---

### Post by cariboo on 2013-05-12
If you use Software Updater (new name for update manager) to upgrade to a newer version, it will automagically disable the ppas. Once the upgrade is done, it's easy enough to go into Software & Updates (new name for Software Sources) and re-enable the ppas.

---

### Post by craig10x on 2013-05-13
Very good...thanks cariboo907...that clears it up for me...i have never done that before, so i wasn't quite sure....now i will know what to do at upgrading time ;)

---

### Post by craig10x on 2013-05-13
Oh, just two more questions...can you change the name (say from raring to saucy) simply by editing it in the software updater's sources....you don't have to do it through the terminal do you?
And if the saucy version of that ppa isn't ready at the time i upgrade, would it still work if i left it set to raring?

---

### Post by Elfy on 2013-05-13
> **craig10x said:**
> Oh, just two more questions...can you change the name (say from raring to saucy) simply by editing it in the software updater's sources....you don't have to do it through the terminal do you?

Try Edit in Software Sources, though I have to say I can open the file, edit and save it in the time it takes software sources to start ;)

> **craig10x said:**
> 
And if the saucy version of that ppa isn't ready at the time i upgrade, would it still work if i left it set to raring?

It might or it might not, at one point I remember having issues with packages that clementine wanted by doing that. Try - if it fails then no and you need to dig a bit.

---

### Post by cariboo on 2013-05-13
At this point in time Software updater won't give you the option to upgrade to Saucy, so you'll have to change the repositories from Raring to Saucy. The easiest way is to use this command in a terminal:

```
sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
```

The other way to do it, is to open /etc/apt/sources.list in gedit:

```
gksu gedit /etc/apt/sources.list
```

and use the search and replace function to change raring to saucy. Using either method won't change the ppas from Raring to Saucy, which is probably for the best, as they aren't usually updated to Saucy until it is released.

Unless there are some really major changes to the distribution, it won't make any difference if you use the raring ppas instead of the saucy ones.

---

### Post by craig10x on 2013-05-13
Thanks guys...:)

---

### Post by jerrylamos on 2013-05-14
In development of unstable ubuntu I expect to do a lot of installs.  I've done at least 3 saucy installs on netbook, notebook, desktop.  Installs are good for showing up bugs to report to launchpad.

On Quantal I did do gedit /etc/apt/sources.list and change precise to quantal to convert a fresh precise install to quantal because daily build wasn't available.

Saucy the daily builds came out pretty quick, so I did a cp precise-desktop-amd64.iso saucy-desktop-amd64 then  zsync which at that time got 74.8% identical.  Since then daily builds  have 'progressed a lot, so this technique was only good at the beginning.

Since then I just do zsync's from the daily build.

Someone else can test upgrades.  I've been burnt by "dread upgrade" so I prefer installs.  My experience upgrades take more disk space than installs.  In the days of gigabyte who cares, but to me it's a sign there's a lot of dead code laying around despite doing apt-get purges, apt-get removes, apt-get autoremove, etc.

So far ubuntu amd64 takes up more disk space than i386.  I'm testing both.  amd64 might be a little faster but not much.

---

