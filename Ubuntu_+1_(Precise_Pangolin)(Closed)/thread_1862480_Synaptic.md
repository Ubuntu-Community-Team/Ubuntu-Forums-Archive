---
title: "Synaptic"
date: 2011-10-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cecilpierce on 2011-10-16
When I try to look at Repositories under settings I get "The repository information has changed. You have to click on the "Reload" button for your changes to take effect", click on reload and try again and get the same thing.
Any one know why ?

---

### Post by drs305 on 2011-10-16
I suspect you are getting errors for at least one repository and it isn't fully updating.

Close Synaptic, open a terminal, and run:
```
sudo apt-get update
```
You will probably see some errors. If they aren't obvious, post them and we can help you out.

---

### Post by cecilpierce on 2011-10-16
@drs305

I noticed the errors before but didn't think it would effect synaptic.
Heres what I got:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                           
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                      
  404  Not Found

---

### Post by drs305 on 2011-10-16
**[COLOR="Red"]ADDED: Do NOT run the upgrade command until you read my next post.[/COLOR]**

[s]It looks like it's in the "Proposed" repository.[/s] See *mc4man's* post.

Open Synaptic or Software Sources, go to the Settings, Repositories: [s]Updates[/s] Other Software tab and untick the [s]"proposed"[/s] *independent* repository. That will remove it from your sources.list. If you can't find it, you can directly edit your /etc/apt/sources.list and remove or comment the line(s) referencing [s]'proposed'[/s] 'extras/independent'.

Try Reload (or apt-get update) and it should work.

---

### Post by drs305 on 2011-10-16
You may have run the wrong command, as you are referencing the next version of Ubuntu (Precise) and you probably aren't using it.

If you ran a dist upgrade to the development version  *after* Oneric was released you ended up with Precise Pangolin. In any case, ALL your repositories are currently for Precise Pangolin and NOT any earlier release. The only one giving errors at the moment are the ones in [s]proposed[/s] extras/indepent.

If you mean to be using Pangolin, you should be posting in the Ubuntu + 1 forum.

If you are in an earlier version and update your packages with Precise Pangolin ones I'm not sure what you are going to end up with.

---

### Post by mc4man on 2011-10-16
Extras is the independent sources - get rid of them in software sources

---

### Post by VinDSL on 2011-10-16
> **cecilpierce said:**
> When I try to look at Repositories under settings I get "The repository information has changed. You have to click on the "Reload" button for your changes to take effect", click on reload and try again and get the same thing.

Any one know why ?
Here's the fix...  ;)

LINKAGE:  [http://ubuntuforums.org/showpost.php?p=11347739&postcount=14](http://ubuntuforums.org/showpost.php?p=11347739&postcount=14)

His problem was different, but the cure is the same...

---

### Post by drs305 on 2011-10-16
> **mc4man said:**
> Extras is the independent sources - get rid of them in software sources

I originally wrote the post to deselect *extras* from the Other Software tab. For some reason when I looked at the error messages again I saw "proposed" - I don't think I was working on another thread at the time and I'm pretty sure the images haven't changed. It may just be late.

---

### Post by cariboo on 2011-10-16
Have a look at [this]("http://ubuntuforums.org/showpost.php?p=11347739&postcount=14") post, there are instruction there to solve your problem

**Edit** Ooops, it looks like VinDSL beat me to it. :)

---

### Post by VinDSL on 2011-10-16
> **cariboo907 said:**
> Have a look at [this]("http://ubuntuforums.org/showpost.php?p=11347739&postcount=14") post, there are instruction there to solve your problem
Heh!  Brilliant minds think alike... (see post #7)

**Edit** Monty Python foot trumps beard!  LoL!  :D

---

### Post by drs305 on 2011-10-16
> **VinDSL said:**
> Here's the fix...  ;)

LINKAGE:  [http://ubuntuforums.org/showpost.php?p=11347739&postcount=14](http://ubuntuforums.org/showpost.php?p=11347739&postcount=14)

His problem was different, but the cure is the same...

The only problem I see for this poster is that the 'extras' repository doesn't yet exist for 12.04. Simply disabling the 'extras' repository looks like all that should be needed. 

On the other hand, I'm not conviced the current OP really means to be using Pangolin in the first place...

---

### Post by VinDSL on 2011-10-16
> **drs305 said:**
> The only problem I see for this poster is that the 'extras' repository doesn't yet exist for 12.04.
Agreed!

Here's a follow-up post:  [http://ubuntuforums.org/showpost.php?p=11350217&postcount=23](http://ubuntuforums.org/showpost.php?p=11350217&postcount=23)

I just went about it a little differently...  ;)

**Edit**

Maybe I should rephrase that...

I suffered the same problem as the OP with Synaptic (and Software Sources in System Settings) not displaying the repos.

Part 1 was fixing the sources list not appearing.

Part 2 was fixing the sources themselves.

---

### Post by mc4man on 2011-10-16
> **drs305 said:**
> I originally wrote the post to deselect *extras* from the Other Software tab. For some reason when I looked at the error messages again I saw "proposed" - I don't think I was working on another thread at the time and I'm pretty sure the images haven't changed. It may just be late.

For whatever reason in software sources they call it independent, but the actual source is extras, clicking edit on it shows.
As you said I'd just get rid of (disable or delete) the independent if now using PP sources  

(ot - some of the SRU upgrades are in 11.10 proposed, but I wouldn't willy-nilly install them all without checking the bug reports - the compiz are good & the ubuntuone ones solve the open-terminal issue

---

