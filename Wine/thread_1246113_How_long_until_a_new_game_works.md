---
title: "How long until a new game works?"
date: 2009-08-21
forum: Wine
---

### Post by Valok on 2009-08-21
So with a few new games coming out from blizzard next year, I'm really wondering how long it usually takes for a new game to get up and running through WINE.

I wonder because all I really do with my computer is gaming, but at the same time I prefer to use linux.  Mainly because of the principal of the matter.

So, will big name games like Diablo 3 and Starcraft 2 work right out of the box?  Or is it going to take a few weeks for WINE to update some things and get the game working solid.

---

### Post by u235sentinel on 2009-08-21
> **Valok said:**
> So with a few new games coming out from blizzard next year, I'm really wondering how long it usually takes for a new game to get up and running through WINE.

I wonder because all I really do with my computer is gaming, but at the same time I prefer to use linux.  Mainly because of the principal of the matter.

So, will big name games like Diablo 3 and Starcraft 2 work right out of the box?  Or is it going to take a few weeks for WINE to update some things and get the game working solid.

The answer is maybe.  It may work out of the box.  It may not.  But until someone tries it we won't know.  I wish I could give you a better answer.  

there are some games that were not on the wine appdb list that I tried and they just worked fine.  I'm thinking of adding them to the database so other's know that they work.  there are other's which won't work no matter what I try.  And hopefully they will be able to run in the future.

Never know.  Wine is updated regularly.

---

### Post by insane_alien on 2009-08-21
wine doesn't really get developed per application.

it provides a compatability layer from the windows api to the linux api that is independant of application.

true a specific application can point out bugs in this translation layer which can be targetted and fixed but it is applied across the board and not just for a single application.

if wine was complete then they would all work out of the box all the time. wine is not complete so its a hit or miss with some glancing blow options thrown in for good measure.

it can be guaranteed that some of it will work. but it cannot be guaranteed that ALL of it will work.

---

### Post by u235sentinel on 2009-08-21
> **insane_alien said:**
> wine doesn't really get developed per application.

it provides a compatability layer from the windows api to the linux api that is independant of application.

true a specific application can point out bugs in this translation layer which can be targetted and fixed but it is applied across the board and not just for a single application.

if wine was complete then they would all work out of the box all the time. wine is not complete so its a hit or miss with some glancing blow options thrown in for good measure.

it can be guaranteed that some of it will work. but it cannot be guaranteed that ALL of it will work.

True but I've heard there are certain games that they do heavily test against to make sure it works.  Stuff like WoW and StarCraft 1 to name a couple.

---

### Post by castlefox on 2009-08-21
Does anyone have a link to support the idea that Blizzard tests its games against WINE to make sure it works there?

---

### Post by hikaricore on 2009-08-21
> **castlefox said:**
> Does anyone have a link to support the idea that Blizzard tests its games against WINE to make sure it works there?

No.  This is 100% untrue.

The reason many blizzard games work well under WINE is that they offer OpenGL support.

---

### Post by u235sentinel on 2009-08-24
> **hikaricore said:**
> No.  This is 100% untrue.

The reason many blizzard games work well under WINE is that they offer OpenGL support.

I was unaware of that.  I've spoken to people who have been using Wine for many years and they have all said this.

---

### Post by naikon89 on 2009-08-24
The reason WOW works well is because of the opengl render path.

This removes the additional overhead of converting directX calls into native 
OpenGL. This does not mean that the game will work at the exact same frame rate however.

---

### Post by del_diablo on 2009-08-24
The reason blizzards game runs well under Wine is because they are not completely abusing the windows API and their not complete freaks on the copy protection.

---

### Post by donkyhotay on 2009-08-24
> **del_diablo said:**
> The reason blizzards game runs well under Wine is because they are not completely abusing the windows API and their not complete freaks on the copy protection.

I've heard that is starting to change since they got bought out and SC2 will have DRM in it.

---

### Post by castlefox on 2009-08-25
I guess its just wait and see how crappy the DRM is.  For SC2 that is....

---

### Post by del_diablo on 2009-08-25
I can't image why they would want that. Starcraft II will be mostly online, so a CD-key locking similar to what Starcraft and Warcraft III got would do more than a good enough job.

---

### Post by donkyhotay on 2009-08-25
I read somewhere that SC2 will have an online activation system requiring you to have an active internet connection in order to install the game. Admittedly I read this online somewhere and can no longer find the article I read this so I don't know how true it is.

---

### Post by del_diablo on 2009-08-25
Well if its just that, there is a chance it will run without effort. I hope.....

---

