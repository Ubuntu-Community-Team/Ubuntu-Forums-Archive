---
title: "Project for PP: Quicklist Editor for Unity Launcher"
date: 2011-10-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-21
I just found out on Launchpad that a fellow countryman is working on a project that might ease some of the dislikes some people have with Unity.

[https://launchpad.net/unity-launcher-editor](https://launchpad.net/unity-launcher-editor)

Screenshots:
[ATTACH]205013[/ATTACH]

[ATTACH]205014[/ATTACH]

The interface seems very easy to play with. There are bugs, not a 100% mature project yet. But once it gets a little more solid, such an option should be the default on Unity.

I'm not sure it would get ready on time for PP...but have a look at it.

Regards,
Effenberg

---

### Post by tista on 2011-10-21
> **effenberg0x0 said:**
> I just found out on Launchpad that a fellow countryman is working on a project that might ease some of the dislikes some people have with Unity.

[https://launchpad.net/unity-launcher-editor](https://launchpad.net/unity-launcher-editor)

Screenshots:
[ATTACH]205013[/ATTACH]

[ATTACH]205014[/ATTACH]

The interface seems very easy to play with. There are bugs, not a 100% mature project yet. But once it gets a little more solid, such an option should be the default on Unity.

I'm not sure it would get ready on time for PP...but have a look at it.

Regards,
Effenberg

Hi effenberg,

Nice ideas... But I think there is something like more important thing...
Yeah We today didn't have any "theming tools" for unity-3d/2d. For example, launcher appearances, dash appearances, and so...

As far as I know how unity-3d could render the blurred dash, cairo rendering directly? and actually unity-2d puts only pixmaps without any customizable stuff instead of replacing pixmaps... That's horrible thing...

And I couldn't find any HIG "Human Interface Guideline" for Unity-3d/2d, or you knew that? I didn't really matter if its HIG seemed to be different from any other graphical shell, but if devs didn't have it, it's very problem. Since the "dash" and "unity-greeter" seems to be focued "glassy design", but on the other hand, how the "Ambiance" did? where that gtk theming want to go?

cheers.

---

### Post by effenberg0x0 on 2011-10-21
> **tista said:**
> Hi effenberg,

Nice ideas... But I think there is something like more important thing...
Yeah We today didn't have any "theming tools" for unity-3d/2d. For example, launcher appearances, dash appearances, and so...

As far as I know how unity-3d could render the blurred dash, cairo rendering directly? and actually unity-2d puts only pixmaps without any customizable stuff instead of replacing pixmaps... That's horrible thing...

And I couldn't find any HIG "Human Interface Guideline" for Unity-3d/2d, or you knew that? I didn't really matter if its HIG seemed to be different from any other graphical shell, but if devs didn't have it, it's very problem. Since the "dash" and "unity-greeter" seems to be focued "glassy design", but on the other hand, how the "Ambiance" did? where that gtk theming want to go?

cheers.
Hey Tista,

I've been looking for something in the lines of Gnome HIG or KDE3 UIG for Unity for a while... You know what? I'm lost. I imagine others are too.

I guess that the way the project was created (and we know it's hard to understand it when you're not "in the loop" because it's very political) it was more like a mix of ideas of some people, somewhat based on the netbook remix, OSx, and modern concepts of other devices. And many decisions were made by a few individuals without the whole process that we see in gnome, etc. It was fast but not as formal as others, lets say. Which is OK as we can see good results so far. I like Unity. 

And there's a lof of GUI inconsistency one can find, you're right about that. We can't expect the maturity of other desktops now, it would be a herculean challenge. I think human resources are limited in comparison to other desktops, mainly because of this lack of clear process, guidelines, doc, etc. It's hard to enter the process, understand what you can or can't do, etc. It demands too much time, too much talk, too much talking to people that not always are nice, etc. So it becomes more of a job than something you can put 2 hours a day as a contribution. 

I am convinced Unity won't change much for PP or PP+1. I feel like having a less customizable desktop has a little something to do with branding... (and I'm not a fan of that, but I can understand how that is sometimes needed and positive for a product). 

So I'm really accepting all that above, and thinking more about what are the small apps, configs, tiny fixes and changes that could help end-users to have a more friendly desktop. Things that people "Outside the loop" can do as third-part apps or unquestionable bug fixing. 

These can most time be implemented as standard apps, outside the whole  Unity discussion, approval process. Now, if one was to propose changes  to the dash/launcher... I'd say great changes of having your branch  merge refused. Not criticizing or anything, just saying it's impossible to take part of something that is not totally clear.    

I just hope that, in the long run, a friendly Unity Desktop don't get to be a mix of 100 indicators, 1.000 conky ways to see info, apps to hack the dash, apps to hack the launcher, apps to hack nautilus, to customize windows,  etc. I hope they see the need for built-in better customization, even if it is within a pre-defined set of acceptable standards,  sooner. 

Regards,
Effenberg

---

### Post by tista on 2011-10-21
> **effenberg0x0 said:**
> Hey Tista,

I've been looking for something in the lines of Gnome HIG or KDE3 UIG for Unity for a while... You know what? I'm lost. I imagine others are too.

I guess that the way the project was created (and we know it's hard to understand it when you're not "in the loop" because it's very political) it was more like a mix of ideas of some people, somewhat based on the netbook remix, OSx, and modern concepts of other devices. And many decisions were made by a few individuals without the whole process that we see in gnome, etc. It was fast but not as formal as others, lets say. Which is OK as we can see good results so far. I like Unity. 

And there's a lof of GUI inconsistency one can find, you're right about that. We can't expect the maturity of other desktops now, it would be a herculean challenge. I think human resources are limited in comparison to other desktops, mainly because of this lack of clear process, guidelines, doc, etc. It's hard to enter the process, understand what you can or can't do, etc. It demands too much time, too much talk, too much talking to people that not always are nice, etc. So it becomes more of a job than something you can put 2 hours a day as a contribution. 

I am convinced Unity won't change much for PP or PP+1. I feel like having a less customizable desktop has a little something to do with branding... (and I'm not a fan of that, but I can understand how that is sometimes needed and positive for a product). 

So I'm really accepting all that above, and thinking more about what are the small apps, configs, tiny fixes and changes that could help end-users to have a more friendly desktop. Things that people "Outside the loop" can do as third-part apps or unquestionable bug fixing. 

These can most time be implemented as standard apps, outside the whole  Unity discussion, approval process. Now, if one was to propose changes  to the dash/launcher... I'd say great changes of having your branch  merge refused. Not criticizing or anything, just saying it's impossible to take part of something that is not totally clear.    

I just hope that, in the long run, a friendly Unity Desktop don't get to be a mix of 100 indicators, 1.000 conky ways to see info, apps to hack the dash, apps to hack the launcher, apps to hack nautilus, to customize windows,  etc. I hope they see the need for built-in better customization, even if it is within a pre-defined set of acceptable standards,  sooner. 

Regards,
Effenberg

@effenberg

Thanks for your great article... ;)

I agree that Unity interface could be the good solutions an "impact" for end-users on graphical look&feel... :) As followed your opinions, it had been mixed a lot of graphical shell interfaces and based on their good advantages.

And IMHO, Unity is the "dash/lens" I suppose... although launcher/dock seems great and really smoothly, but the principal is the Dash. so if we want any tiny apps for tweaks to change/modify the dash, it would be great! Because each person never have an exactly same focus for "search"... someone might need "music search" instead of "contacts search", but an another might need such "contacs search". So this is the lack of unity's "flexibilities", I suppose today. But, I know such modular design might be caused the confusions for newbie users, they would say that "Hey! which one I should choose and apply for?!" ;) So sometimes the "built like a tank" design would be needed as desktop environments.

Finally I hope we could start everything from our beloved "Dash"...

regards.

---

### Post by effenberg0x0 on 2011-10-21
One of the things I don't like: I don't like searching over and over and over and over every day for the same thing :) 

On a standard OS: My apps are all there, my folders are all there, etc. I am probably one of the last people on earth that creates a directory structure like this example below and has it in his head. I probably had a 486 when this structure was created first time. Why the hell would I keep searching over and over for stuff instead of clicking them once I know where they are, and have been for the last 20 years? :)


Documents
- Personal Stuff
--Media
---Audio
---- Artists
---- Albums and Compilations
---Video
---- Movie Collection
---- New stuff
---- Anime
---Books
---- Science / Science Fiction
---- Technical
----- C and C++
----- ASM
----- etc
---Games
---Other
- Work Stuff
--Priorities
---Current Projects
----Git
--Past Projects
- Backup
-- Hourly
-- Daily
-- Weekly
-- Monthly
etc...


> **tista said:**
> @effenberg

Thanks for your great article... :wink:

You haven't seen me drunk :) It gets worse. I do bore people out of their minds.

---

