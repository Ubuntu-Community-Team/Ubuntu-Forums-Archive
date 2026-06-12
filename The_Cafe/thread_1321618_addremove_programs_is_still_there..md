---
title: "add/remove programs is still there."
date: 2009-11-10
forum: The Cafe
---

### Post by Ms_Angel_D on 2009-11-10
I don't know if anybody else knew this(I'm sure a bunch of people did), but I just discovered that I can get add/remove programs back by running

```
sudo apt-get install gnome-app-install
```

Of course I had to create my own menu item for it but, honestly I'm glad for now it's still there because I think the software center needs more work.

---

### Post by The Funkbomb on 2009-11-10
Good to know.  Now, I hope for 10.04, they give the user the option if they want to use Software Center or Add/Remove.

I prefer Add/Remove.

---

### Post by Tibuda on 2009-11-10
[apt:gnome-app-install]("apt:gnome-app-install")

---

### Post by Ms_Angel_D on 2009-11-10
> **The Funkbomb said:**
> Good to know.  Now, I hope for 10.04, they give the user the option if they want to use Software Center or Add/Remove.

I prefer Add/Remove.

That would be nice but I honestly don't see it happening unless there is a bunch of people calling for it.

---

### Post by ZankerH on 2009-11-10
You realise both gnome-app-install and the software centre are essentially dumbed-down versions of Synaptic, right? Just use that, if you must have a gui for apt-get.

---

### Post by RiceMonster on 2009-11-10
> **ZankerH said:**
> You realise both gnome-app-install and the software centre are essentially dumbed-down versions of Synaptic, right? Just use that, if you must have a gui for apt-get.

So because it's a "dumbed down" version, they're not allowed to prefer it and shouldn't use it?

---

### Post by The Funkbomb on 2009-11-10
Yes, I realize you can do the same thing through synaptic.  I just prefer add/remove for browsing applications.

---

### Post by Ms_Angel_D on 2009-11-10
> **ZankerH said:**
> You realise both gnome-app-install and the software centre are essentially dumbed-down versions of Synaptic, right? Just use that, if you must have a gui for apt-get.

I use synaptic too but for just browsing software add/remove programs is the way to go for me. Synaptic doesn't break it down into categories and doesn't give it a very browse-able interface.

---

### Post by ZankerH on 2009-11-10
> **Ms_Angel_D said:**
> Synaptic doesn't break it down into categories and doesn't give it a very browse-able interface.


[IMG]http://img140.imageshack.us/img140/1301/synapticcategories.png[/IMG]

> So because it's a "dumbed down" version, they're not allowed to prefer it and shouldn't use it? 

Use what works for you.

---

### Post by Ms_Angel_D on 2009-11-10
> **ZankerH said:**
> [IMG]removed to keep from double loading[/IMG]



Use what works for you.

That's hardly an easy on the eyes interface. Synaptic is great if you know what your searching for, but for browsing it has to be possibly the worst interface I have ever seen.

---

### Post by ZankerH on 2009-11-10
> **Ms_Angel_D said:**
> That's hardly an easy on the eyes interface. Synaptic is great if you know what your searching for, but for browsing it has to be possibly the worst interface I have ever seen.

protip: Use your browser for browsing. A package manager isn't a supermarket.

---

### Post by Ms_Angel_D on 2009-11-10
> **ZankerH said:**
> protip: Use your browser for browsing. A package manager isn't a supermarket.

Why does this thread even matter to you?

---

### Post by RiceMonster on 2009-11-10
> **ZankerH said:**
> protip: Use your browser for browsing. A package manager isn't a supermarket.

> **ZankerH said:**
> Use what works for you.

...

---

### Post by Simian Man on 2009-11-10
[quote=ZankerH]You realise both gnome-app-install and the software centre are essentially dumbed-down versions of Synaptic, right? Just use that, if you must have a gui for apt-get.[/quote]

You realize apt-get is just a dumbed down version of dpkg right?  Just use the [package database]("http://packages.ubuntu.com/") to browse pacakages, wget to download them and dpkg to install them - if you need any dependencies, dpkg will tell you and you can get those with wget as well!!

---

### Post by ~sHyLoCk~ on 2009-11-10
protip: ```
sudo apt-cache search package

sudo apt-get install package
```

:lolflag:

---

### Post by The Funkbomb on 2009-11-10
Here's an even better idea!  Let's just get rid of all GUIs.  We can do everything via CLI.

I don't see why you're breaking off on people because they prefer add/remove.  The more options people have the freer they are.

---

### Post by Ms_Angel_D on 2009-11-10
> **the funkbomb said:**
> the more options people have the freer they are.

This is QFT

---

### Post by RiceMonster on 2009-11-10
> **Simian Man said:**
> You realize apt-get is just a dumbed down version of dpkg right?  Just use the [package database]("http://packages.ubuntu.com/") to browse pacakages, wget to download them and dpkg to install them - if you need any dependencies, dpkg will tell you and you can get those with wget as well!!

lol win

---

### Post by ~sHyLoCk~ on 2009-11-10
Somehow I think ZankerH uses slackware. :p

---

### Post by Mr. Picklesworth on 2009-11-10
> **The Funkbomb said:**
> Good to know.  Now, I hope for 10.04, they give the user the option if they want to use Software Center or Add/Remove.

I prefer Add/Remove.

You do have an option. (Even via Software Centre itself). It is not necessary for options to leap at our users' faces.

---

### Post by The Funkbomb on 2009-11-10
> **Mr. Picklesworth said:**
> You do have an option. (Even via Software Centre itself). It is not necessary for options to leap at our users' faces.

I meant like a part in the menu that said "Classic Add/Remove View"

---

### Post by Tibuda on 2009-11-10
> **The Funkbomb said:**
> I meant like a part in the menu that said "Classic Add/Remove View"

You mean you want both installed by default? No, they should not.

---

### Post by The Funkbomb on 2009-11-10
Why not?  You'd never know it was there.

---

### Post by Tibuda on 2009-11-10
> **The Funkbomb said:**
> Why not?  You'd never know it was there.

Why have two apps to do the same thing? That's wasted space and will surely confuse new users.. If someone wants the old add/remove, install it and remove USC.

This also applies to Synaptic, but USC is not ready yet to replace it.

---

### Post by The Funkbomb on 2009-11-10
That's not what I'm saying at all.

It would be on entry under applications.  You open it up and go to Software Center.  You look and don't like it.  All you'd have to do is click View>View Classic and it would switch over the classic add/remove view.

---

### Post by CharlesA on 2009-11-10
> **The Funkbomb said:**
> Yes, I realize you can do the same thing through synaptic.  I just prefer add/remove for browsing applications.

This is what I do as well. I'll remove them with Synaptic or apt-get tho.

---

### Post by Tibuda on 2009-11-10
> **The Funkbomb said:**
> That's not what I'm saying at all.

It would be on entry under applications.  You open it up and go to Software Center.  You look and don't like it.  All you'd have to do is click View>View Classic and it would switch over the classic add/remove view.

Sorry, I misunderstood you... Now I see what you are suggesting.

---

### Post by lukjad on 2009-11-10
> **Ms_Angel_D said:**
> I don't know if anybody else knew this(I'm sure a bunch of people did), but I just discovered that I can get add/remove programs back by running

```
sudo apt-get install gnome-app-install
```

Of course I had to create my own menu item for it but, honestly I'm glad for now it's still there because I think the software center needs more work.
Heehee. I thought you meant that programs you removed were still installed. :lol:

---

