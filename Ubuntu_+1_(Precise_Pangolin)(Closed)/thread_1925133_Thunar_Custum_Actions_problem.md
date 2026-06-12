---
title: "Thunar Custum Actions problem"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ranch hand on 2012-02-14
I used the gui supplied with Thunar to add a custom action.

I really like to be able to open my browser as root in a directory as you could do in Nautilus with nautilus-gksu installed.

This works very easily in Thunar and they even have a premade example in their wiki for this.

So I have for Name "Open As Hephaestus"

Nothing in discription

In command I have  "gksu thunar %f" as per the wiki and the working custom action in all my Debian installs.

Nothing happened at all.

So I dig up my Debian entry in ~/.Thunar/uca.xml
```

</action><action><icon>Thunar</icon><name>Open As Hephaestus</name><command>gksu thunar %f</command><description></description><patterns>*</patterns><startup-notify/><text-files/>

```
and add this to the file.

This has helped a bit.  The thunar hammer shows up in the custom actions dialog box along with the entry.

Nothing shows up in the menu.

This really needs to work.  Great feature.

For those not familiar with custom actions in Thunar see;
[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)

It is really just neater than bug $hit.

---

### Post by Elfy on 2012-02-14
Mine's set with 

gksudo exo-open %F

First time it asks what file manager to use.

---

### Post by ranch hand on 2012-02-14
> **forestpiskie said:**
> Mine's set with 

gksudo exo-open %F

First time it asks what file manager to use.
I will give that a whack.  Might be a Xubuntu thing that is different than standard Xfce.

As long as something works it is fine with me.

---

### Post by Jose Catre-Vandis on 2012-02-14
Not in 12.04 but I only use
```
gksu thunar
```

---

### Post by ranch hand on 2012-02-15
@forestpiskie and Jose Catre-Vandis

I figured with 2 different  alternate commands something should work.  It does not work with either of those commands either.

Not sure where to go with this from here.

I have the other problems with Apport not working and cups not installing in a chroot environment to consider here.

The idea of reinstalling is, frankly repugnant.  While they are now converted to Debian I have 2 installs on here that started life as 9.10-testing.  I got them through some rough times without reinstallation.

I have to wonder, though, if that may not be a good idea.  I have no other install of 12.04 to check against.  All these problems may just be the result of "age" and slight dpkg errors.

Too tired to think.  Guess I will go home to Debian and think about it over night.  Could be that I just need to get an image and redo this thing before filing bugs.

---

### Post by mr_pouit on 2012-02-15
Did you check 'directories' on the second tab of the custom action dialog? (otherwise the action will only show on text files, not really useful...)

---

### Post by ranch hand on 2012-02-15
> **mr_pouit said:**
> Did you check 'directories' on the second tab of the custom action dialog? (otherwise the action will only show on text files, not really useful...)
Yupper, I sure did.

As I said I have this working in several instances of Xfce4.8 and I forgot that I also have in on 4.6 on a Squeeze install.

I have the daily for today and it is set up on my grub menu so I will check it to make sure it boots.  Then I need to make sure I have everything I want in the / partition of my install backed up.  After that I will do a clean install on the / and see if a number of things are working correctly that seem to have errors creeping in.

---

### Post by ranch hand on 2012-02-16
Finally got around to reinstalling this puppy.

Thunar now has no trouble with the entry I used in the first place from the wiki.  Pretty happy about that.

Now has the option to "Open as The Big Cheese".  Works great.  Have no idea what the problem was.

---

