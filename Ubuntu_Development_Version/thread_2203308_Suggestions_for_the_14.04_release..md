---
title: "Suggestions for the 14.04 release."
date: 2014-02-02
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2014-02-02
Let me begin by saying that, even at this embryonic stage, I am absolutely amazed by this release... so much so that I have relegated my main OS and keep booting into trusty.

I am yet to experience any significant system errors or even a mere one of those annoying "ubuntu experienced an internal error" pop ups.

Not only is this the best version of ubuntu ever made it's also the best linux distro I have used and it is certainly one of my top 5 OS's.

Being so, even if you find this post OCD, just remember it was written because I care:

 
   - Unity:  I'm afraid unity is still plagued by broken aesthetics and a gnomish heritage that does not favour it...

    Example:  the sidebar in Files 3.10.1... it is absolutely hideous and I have no choice but to keep pressing F9 as it does not let me hide it by default
  
    Those gnome unelegant small black icons clash with the orange theme and are absolutely atrocious.
    
    This can easily be remedied:

   [IMG]http://farm9.staticflickr.com/8448/7839240868_6fb50e2e01_b.jpg[/IMG]


 [IMG]http://www.linuxmint.com/pictures/screenshots/olivia/nemo.png[/IMG]  


   - The radiance theme: I would tone down the reddish/pinkish hue on the upper bar. Make it flatter and lighter... I have also noticed that fonts/icons appear a little jagged in need of antialising in the upper bar, fortunately changing fonts with unity tweak fixes this (could be this thinkpad).

[IMG]http://www.bestubuntu.com/wp-content/uploads/2012/04/df972__elementary-os-pantheon-notify.png[/IMG]


   - One more theme option wouldn't be bad, you could call it brilliance and have the selection color etc be blue instead of orange (or any other color instead of orange really, at least you would have the option)

  - The new icon theme and anti aliased borders are minor things that will go a looooooooooong way on making using ubuntu a enjoyable experience (most people here complain about the orange and dark grey look).

________________________________________________________________________________________________________________________________________________________________________

 - A services control panel that would allow one to quickly and easily disable/enable indicators, services like cups/bluetooth and search scopes... messing with sysv rc conf is no fun, neither is removing packages that can brick unity. Semplice has implemented this and gives a degree of choice/control that it's absolutely wonderful

 [IMG]http://tallinux.altervista.org/blog/wp-content/uploads/2014/01/semplice6-23.png[/IMG]


 - some bundled software, like 'startup disk creator' and 'brasero', is not very good. There are much better alternatives.

 - software like apparmor utils or gufw should be bundled with the iso. 

 
 I do believe I have this system completely up to date: "ubuntu 3.13.0-6-generic #23-Ubuntu SMP Thu Jan 30" ... yet:

 firefox 25 :(  libre office 4.1something ... seeing as this is the alpha stage, isn't it a bit too early to be this conservative?

 I do really believe 14.04 should have the 3.14 kernel. There are some nice intel acpi and other power etc code that could be really useful for laptops, not to mention fs patches and what not...

 3.14 should have 6 or 7 release candidates so the final release would happen mid march, that would give you a full month to test it...

 I know that it might sound bad but if you start pushing 3.14 rc1 from the get go you will have lots of people testing it from the get go so there should be no major surprises... 

 release 14.04 with kernel 3.14 - it's more zen than 14.04 with kernel 3.13  ;) thx for reading

---

### Post by sammiev on 2014-02-02
I think your a little late for 14.04

Great to see you are testing and good luck on the next one. :) Be sure to fill out bug reports.

---

### Post by Yellow Pasque on 2014-02-02
[http://www.phoronix.com/scan.php?page=news_item&px=MTU4OTY](http://www.phoronix.com/scan.php?page=news_item&px=MTU4OTY)

---

### Post by grahammechanical on 2014-02-03
Here is a kind of contradiction

> [COLOR=#000000]I am yet to experience any significant system errors or even a mere one of those annoying "ubuntu experienced an internal error" pop ups.[/COLOR]

> [COLOR=#000000]if you start pushing 3.14 rc1 from the get go you will have lots of people testing it from the get go so there should be no major surprises... [/COLOR]

We cannot have it both ways. Do we want a stable development version that can be a base for developers to write code for? We cannot get that if upstream code is pushed out too quickly. And believe me we will get major surprises. We get them now even with small increment changes to the kernel.

See what happens with a push too far

[http://ubuntuforums.org/showthread.php?t=2203330](http://ubuntuforums.org/showthread.php?t=2203330)

Regards.

---

### Post by nomenkultur on 2014-02-03
"For likely inclusion into Ubuntu 14.10"  :(  thanks for the link Temujin, this was a really smart move by canonical.

 
 I understand that gmechanical... but let's say that 14.04 ships with kernel 3.13, people that buy newer haswell laptops won't have as pleasant experience (battery life, gfx, etc) as they would if it would come with 3.14, ditto for anyone with a laptop etc...

 mind you this is still the alpha stage, right? shouldn't the aim of the alpha stage to be as bleeding edge as possible?

 
 I understand the balancing act and compromise this entails, but if they started pushing 3.14 rc1 tomorrow then you would have months to see what crashed and burned.

 think about it ubuntu 13.10 shipped with 3.11 and 14.04 only jumps 2 kernel versions????

 ubuntu 12.04 3.2  +3   ubuntu 12.10  3.8
 ubuntu 13.04 3.8  +3  ubuntu  13.10  3.11

---

### Post by mc4man on 2014-02-03
12.04.4 - 
linux-generic-lts-saucy	3.11.0.15.14

So 14.04 will also  get lts upgrades...

---

### Post by kansasnoob on 2014-02-03
> **mc4man said:**
> 12.04.4 - 
linux-generic-lts-saucy	3.11.0.15.14

So 14.04 will also  get lts upgrades...

Yes :guitar:

There may be a shift in just how the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") is handled in Trusty but AFAIK the goal remains the same :D

---

### Post by nomenkultur on 2014-03-02
This has been plaguing my ocd also:

 in 13.04/13.10 when you installed UGFW it would simply integrate beautifully into the system settings panel...

 why was this removed from 14.04???

---

### Post by Mateusz Stachowski on 2014-03-02
In 13.04/13.10 we had gnome-control-center and now in 14.04 we have unity-control-center. I think that programs which integrated with system settings need to be adjusted for this change.

---

### Post by nomenkultur on 2014-03-09
ok, I get it... so it's not canonical that needs to enable this but the GUFW devs need to code support for unity control center

---

### Post by quentin3 on 2014-03-10
One thing I'm waiting for years... A better FONT RENDERING. When we will have a great font rendering? I have to install infinality and do some tweaks to get "pretty" good fonts...

---

