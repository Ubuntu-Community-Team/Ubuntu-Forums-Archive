---
title: "Crunchbang Linux-like setup for Lucid and any Ubuntu after?"
date: 2010-04-14
forum: The Cafe
---

### Post by user1397 on 2010-04-14
What about those of us that want the option of having an ideal openbox setup, like crunchbang 9.04, but won't be able to anymore due to their change from ubuntu to debian?  By that I mean of course those of us that want ubuntu to remain as the base system for our comps, for whatever reason.

Does anyone want to take it upon themselves to make an install script perhaps, much like the official crunchbang 'alternate install' method on their website, but just call it something like 'openbox desktop' or something?

I'd try it out.

---

### Post by Paqman on 2010-04-14
> **ubuntuman001 said:**
> 
Does anyone want to take it upon themselves to make an install script perhaps, much like the official crunchbang 'alternate install' method on their website, but just call it something like 'openbox desktop' or something?


I'm writing one right now that (amongst other options) will build you your own basic Lubuntu desktop. Watch this space.

---

### Post by user1397 on 2010-04-14
> **Paqman said:**
> I'm writing one right now that (amongst other options) will build you your own basic Lubuntu desktop. Watch this space.Awesome man, thanks!

Now, were you already working on this before seeing this thread, or did this thread motivate you to start the project? :guitar:

---

### Post by Paqman on 2010-04-14
> **ubuntuman001 said:**
> 
Now, were you already working on this before seeing this thread, or did this thread motivate you to start the project? :guitar:

Maybe you sent me a psychic thought bubble from the future. I bashed it out over the weekend, it just needs some polish. And someone to find all the millions of bugs, due to my extreme lack of 1337.

---

### Post by user1397 on 2010-04-14
> **Paqman said:**
> Maybe you sent me a psychic thought bubble from the future. I bashed it out over the weekend, it just needs some polish. And someone to find all the millions of bugs, due to my extreme lack of 1337.
haha, well you definitely possess some 1337ness for bashing it out :popcorn:

oh and I would be honored to test it out.

---

### Post by snowpine on 2010-04-14
Why not just upgrade your CrunchBang install to Lucid? Or back up your /home, do a fresh install of Lucid, install openbox and whatever apps you want, and restore /home?

---

### Post by user1397 on 2010-04-14
> **snowpine said:**
> Why not just upgrade your CrunchBang install to Lucid? Or back up your /home, do a fresh install of Lucid, install openbox and whatever apps you want, and restore /home?
well as far as I understand it crunchbang also uses some repos of its own, and is made from scratch each time from a minimal ubuntu base.  I don't know how upgrade friendly it is.

Also, the second thing you said would not work for me as I do not have a /home partition, and I don't know how to configure openbox+ all the apps *well enough* as compared to a crunchbang setup, hence the install script I inquired about.

---

### Post by nothingspecial on 2010-04-14
That`s kind of what I do.
[B]
I have an heavily edited version of the default crunchbang rc.xml and menu.xml[/B]

I found it alot easier to strip down those than build new one from scratch.

Then (with a seperate /home) install ubuntu-minimal, then install xinit, openbox, ncurses-base and wicd for a base system with wireless.

Then nirogen, feh, chromium-browser etc etc until I have my custom system.

---

### Post by snowpine on 2010-04-15
Well, I have 2 computers running CrunchBang 9.04. It is still a viable operating system, nice and stable, and will be supported through October. You are correct that there is a small CrunchBang repository, separate from the Ubuntu repos, and I have no idea what will happen to that after October.

I've been testing the new Debian-based CrunchBang as well, and it is very, very nice. The Debian base means it will be very stable with many years of support. So if you change your mind... :)

---

### Post by user1397 on 2010-04-24
Any word on your script yet Paqman?

---

