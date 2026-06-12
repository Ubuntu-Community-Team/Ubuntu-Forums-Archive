---
title: "To those worried about &quot;bloat.&quot;"
date: 2010-04-13
forum: The Cafe
---

### Post by kevin01123 on 2010-04-13
```
aptitude -R install somepackage
```

---

### Post by Sporkman on 2010-04-13
Thanks for the tip.

I think "bloat" is overly obsessed over - so what if it takes an application 3 seconds to load instead of 1, or 1 second to move a window instead of 0.5. :)

Discuss.

---

### Post by toupeiro on 2010-04-13
> **Sporkman said:**
> Thanks for the tip.

I think "bloat" is overly obsessed over - so what if it takes an application 3 seconds to load instead of 1, or 1 second to move a window instead of 0.5. :)

Discuss.

When I think of bloat, I think of doing a process list and seeing a web browser (currently setting at 235MB) and a social network tool (gwibber siting at 206MB with one service configured) as the most memory absorbed app running on my PC.  And I mean, more than multiple MySQL and PostGRES databases.  Personally, I find this to be abusive.  Unfortunately, Aptitude can't recode them for me. :P

---

### Post by Crunchy the Headcrab on 2010-04-13
Nevermind, don't mind the bloat.

---

### Post by mikewhatever on 2010-04-13
> **kevin01123 said:**
> ```
aptitude -R install somepackage
```

Silly. Recommended packages have nothing to do with bloat.
And yes, -R= --without-recommends, thanks for explaining.:roll:

---

### Post by Sporkman on 2010-04-13
> **toupeiro said:**
> When I think of bloat, I think of doing a process list and seeing a web browser (currently setting at 235MB) and a social network tool (gwibber siting at 206MB with one service configured) as the most memory absorbed app running on my PC.  And I mean, more than multiple MySQL and PostGRES databases.  Personally, I find this to be abusive.  Unfortunately, Aptitude can't recode them for me. :P

Then don't look at the process list. :P

---

### Post by bruce89 on 2010-04-13
> **toupeiro said:**
> When I think of bloat, I think of doing a process list and seeing a web browser (currently setting at 235MB) and a social network tool (gwibber siting at 206MB with one service configured) as the most memory absorbed app running on my PC.

Have a look at [http://pino-app.appspot.com/]("http://pino-app.appspot.com/")Pino.

---

### Post by Rasa1111 on 2010-04-13
Kevin~ care to elaborate any more than..
aptitude -R install somepackage???

---

### Post by pickboy87 on 2010-04-13
> **kevin01123 said:**
> ```
aptitude -R install somepackage
```

Successful troll is successful.

Actually, if people are worried about bloat, install Ubuntu Minimal or another lightweight/minimal distro.

---

### Post by the yawner on 2010-04-13
How is having additional packages installed on your system - which most of the time will only consume a bit of your HDD resources - considered bloat?

---

### Post by pickboy87 on 2010-04-13
> **the yawner said:**
> How is having additional packages installed on your system - which most of the time will only consume a bit of your HDD resources - considered bloat?

Bloat in my opinion is having unnecessary packages installed. I don't have or own a scanner and that's installed by default. Essentially it's bloat. Going by your logic, why not install every one of the packages from the repository? Obviously it's a bit extreme, but you get my point.

---

### Post by bruce89 on 2010-04-13
> **pickboy87 said:**
> Bloat in my opinion is having unnecessary packages installed. I don't have or own a scanner and that's installed by default. Essentially it's bloat. Going by your logic, why not install every one of the packages from the repository? Obviously it's a bit extreme, but you get my point.

Switch off "install recommended packages automatically" in aptitude, and use aptitude. It's what I do on my Debian machines.

---

### Post by FuturePilot on 2010-04-13
> **bruce89 said:**
> Have a look at [http://pino-app.appspot.com/]("http://pino-app.appspot.com/")Pino.

Thanks, I'll have to try this. I got fed up with Gwibber and the enormous amount of RAM it eats.

---

### Post by the yawner on 2010-04-13
> **pickboy87 said:**
> Bloat in my opinion is having unnecessary packages installed. I don't have or own a scanner and that's installed by default. Essentially it's bloat. Going by your logic, why not install every one of the packages from the repository? Obviously it's a bit extreme, but you get my point.

My point simply meant that having recommends switched off does little effect in terms of trimming out the supposed bloat. When I run the installed application, it doesn't mean it will also run the recommended packages.

But perhaps it's because I'm no longer using a 20GB HDD. 10 years ago HDD space would have been an issue for me. If it takes too much RAM and CPU and the only thing it can do is render web content then that's certainly bloated for me.

---

### Post by Mr. Picklesworth on 2010-04-13
I consider stuff bloat if it is outside the realm of my package manager, in /opt (I have a completely irrational, unfounded hatred of that directory), or actually running when it isn't serving a purpose. Otherwise, I really don't care. The more packages the merrier! I'm installing stuff all the time, anyway, so it means I won't have to install that dependency later on :)

The beautiful thing with DPKG and RPM is that every single last file is being kept track of; nothing falls between the cracks.

---

### Post by pickboy87 on 2010-04-13
> **bruce89 said:**
> Switch off "install recommended packages automatically" in aptitude, and use aptitude. It's what I do on my Debian machines.

Thanks for the tip, but I use Arch.

[quote=the yawner]My point simply meant that having recommends switched off does little effect in terms of trimming out the supposed bloat. When I run the installed application, it doesn't mean it will also run the recommended packages. But perhaps it's because I'm no longer using a 20GB HDD. 10 years ago it would have been an issue for me. If it takes too much RAM and CPU and the only thing it can do is render web content then that's certainly bloated for me. [/quote]

I suppose bloat is different for each person. Having been on the Arch forums for a while now, when a program that installs 20 megabytes vs 10 megabytes is considered 'bloat' and 'huge', you kind of see where I'm coming from.

I do like a slimed down system though and having unnecessary packages installed by default is considered bloat to me. That, and when you update everyday, you don't exactly want 200+ megabytes of files to download. Just my 2 cents.

---

### Post by bruce89 on 2010-04-13
> **pickboy87 said:**
> Thanks for the tip, but I use Arch.

Oops, of course.

---

### Post by kevin01123 on 2010-04-13
> **mikewhatever said:**
> Silly. Recommended packages have nothing to do with bloat.
And yes, -R= --without-recommends, thanks for explaining.:roll:
> **aptitude man page]-R, --without-recommends
           Do not treat recommendations as dependencies when installing new
           packages (this overrides settings in /etc/apt/apt.conf and
           ~/.aptitude/config). Packages previously installed due to
           recommendations will not be removed.

           This corresponds to the pair of configuration options
           Apt::Install-Recommends and Aptitude::Keep-Recommends.[/quote]
[QUOTE=Rasa1111 said:**
> Kevin~ care to elaborate any more than..
aptitude -R install somepackage???
Installs only what's needed for the application to run.

> **pickboy87 said:**
> Successful troll is successful.

Actually, if people are worried about bloat, install Ubuntu Minimal or another lightweight/minimal distro.
I'm not trolling, and yes, a minimal install would be ideal.

---

### Post by toupeiro on 2010-04-13
> **Sporkman said:**
> Then don't look at the process list. :P

Yes, because ignorance is bliss? :lolflag:

---

### Post by Irihapeti on 2010-04-13
Bloat = stuff that I don't want on my system, and therefore you shouldn't want on yours.

Bloat = BAD!!!
If a system is accused of being bloated, its devs/users etc are supposed to hang their heads in shame.


Seriously, one person's bloat is another person's "good, that's there if I need it."

---

### Post by Rasa1111 on 2010-04-14
cool thanks kevin.

 now , my peers....
lol

 i have a question that i consider being related to "bloat"..
and would rather not post a whole thread for it... 
so i will attempt it here...   lol

 After I have deleted whatever packages i no longer want/need... 

Why do they (some of them) still show up in "menu editor" ?
the programs are no longer there ( i dont think..as i have deleted them i am sure)
but the option to "check it" is there, in menu editor, to add it to the applications menu. 

 i understand using synaptic to go in and "completely remove" all deleted programs/apps and associated packages...

 but some of them are still there...

 did i even make that clear?
if not, 
please ignore me. lol

thanks

---

### Post by Tristam Green on 2010-04-14
[img]http://images.businessweek.com/ss/06/08/plane_products/image/gas-x_strips.jpg[/img]

Oh....wrong kind of bloat :(

---

### Post by Irihapeti on 2010-04-14
In extreme cases, there's always the good old trocar and cannula.

Oh, sorry, we're not on a dairy farm.

---

### Post by Sporkman on 2010-04-14
Remember, folks: "bloat" is just "boat" with an extra "l".

Think about it.

---

### Post by pommie on 2010-04-14
To me 'bloat' is the same as a weed, that is any plant growing where you do not want it to, even the rose is a weed if it is growing where you do not want it to.
So anything you have on your hdd that you do not want is bloat, no matter how full/empty the drive, same for running apps/processes, if you want them then it is not bloat.
Its a case of *whatever floats your bloat*. #groan#

Cheers David

---

