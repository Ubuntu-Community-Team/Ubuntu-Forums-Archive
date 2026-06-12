---
title: "Is it time for Unity to go it alone?"
date: 2012-09-19
forum: The Cafe
---

### Post by Linux_junkie on 2012-09-19
Now we all know that Unity is a shell for Gnome 3 and with the recent changes announced by Gnome in to the direction that particular desktop is heading and with Canonical's decision to use an older version of Nautilus in its next version. Do you think it is time for Canonical to develop Unity in to a standard alone desktop environment?

Or just continue to use the Gnome 3 libraries?

---

### Post by thatguruguy on 2012-09-19
And break compatibility with all Gnome apps? Are you suggesting the creation of new a new toolkit as well?

---

### Post by whatthefunk on 2012-09-19
That sounds like a lot of work for very little benefit.

---

### Post by Glencore on 2012-09-19
> **Linux_junkie said:**
> Now we all know that Unity is a shell for Gnome 3 and with the recent changes announced by Gnome in to the direction that particular desktop is heading and with Canonical's decision to use an older version of Nautilus in its next version. Do you think it is time for Canonical to develop Unity in to a standard alone desktop environment?

Or just continue to use the Gnome 3 libraries?

If they have the manpower, why not. It will segment the movement further though (apps developed for 3 enviroments instead of 2). Then theres the question of is it wasting manpower (manhours used on yet another desktop enviroment). Ubuntu does have a nice ecosystem biulding though so it could work.

---

### Post by Linux_junkie on 2012-09-19
> **thatguruguy said:**
> And break compatibility with all Gnome apps? Are you suggesting the creation of new a new toolkit as well?

I forgot about the fact that you would need to re-develop all the Gnome apps to run on it.

---

### Post by whatthefunk on 2012-09-19
> **Glencore said:**
> If they have the manpower, why not. It will segment the movement further though (apps developed for 3 enviroments instead of 2). Then theres the question of is it wasting manpower (manhours used on yet another desktop enviroment). Ubuntu does have a nice ecosystem biulding though so it could work.

Considering that Unity, which is still incomplete in my opinion, has been in development for a couple years, I think its safe to say that they do not have the manpower.  Canonicals number one goal at the moment should be refining and building on unity, not starting from scratch all over again.

---

### Post by forrestcupp on 2012-09-19
> **Linux_junkie said:**
> I forgot about the fact that you would need to re-develop all the Gnome apps to run on it.

It's not about the apps as much as it is the toolkit and libraries. They need Gnome3. But I do think they should make it a little more standalone than it is, especially when it comes to Nautilus and other built-in apps. Maybe they should take a cue from Mint and Cinnamon.

IMO, they don't need to dump Gnome 3; they need to dump Compiz.

---

### Post by MG&amp;TL on 2012-09-19
> **forrestcupp said:**
> ...they need to dump Compiz.

That's exactly what I thought this thread was about from the title.

While Compiz is nice on X.org (most of the time), I thought Unity could make a nice clean break away from being a compiz plugin (and associated problems) with the instigation of Wayland; however, they seem to be employing the Compiz developer to port it. Annoyingly.

My thought was that they could keep the WM; just remove the dependency on it so you can run Unity with any WM and not have it break if compiz momentarily dies.

Oh well, I like Unity, however it's implemented.

---

### Post by Dragonbite on 2012-09-19
> **forrestcupp said:**
> It's not about the apps as much as it is the toolkit and libraries. They need Gnome3. But I do think they should make it a little more standalone than it is, especially when it comes to Nautilus and other built-in apps. Maybe they should take a cue from Mint and Cinnamon.

IMO, they don't need to dump Gnome 3; they need to dump Compiz.

Wouldn't they be able to use the GTK toolkit yet rebuild some key components (Unity, file manager, etc.) like how Xfce?

I thought Xfce was a GTK based desktop environment that has gone and built their own file manager (Thunar) and other applications but all other applications run just fine.

I'm wading into waters I don't know here, so if I am completely off base, let me know.

---

### Post by MG&amp;TL on 2012-09-19
> **Dragonbite said:**
> Wouldn't they be able to use the GTK toolkit yet rebuild some key components (Unity, file manager, etc.) like how Xfce?

I thought Xfce was a GTK based desktop environment that has gone and built their own file manager (Thunar) and other applications but all other applications run just fine.

I'm wading into waters I don't know here, so if I am completely off base, let me know.

You're right. There's just no reason to, as the apps are fine. :)

---

### Post by Dragonbite on 2012-09-19
> **MG&TL said:**
> You're right. There's just no reason to, as the apps are fine. :)

I think the proposed changes to Nautilus and removing of a number of desired features is what prompted this discussion.

So maybe Ubuntu needs to just fork Nautilus?

---

### Post by MG&amp;TL on 2012-09-19
> **Dragonbite said:**
> I think the proposed changes to Nautilus and removing of a number of desired features is what prompted this discussion.

So maybe Ubuntu needs to just fork Nautilus?

Maybe. But I was going on the thread title . :P

---

### Post by vexorian on 2012-09-19
I don't find any major issues with Nautilus' feature removal. The one feature that really made me angry is the removal of emblems. But we can sort of make it work again.

Dual panels is something I never used, but by using compiz' feature you can place one nautilus window to the left side and another to the right side anyway.

I think that replacing the menu bar with a gear icon is the one issue that is very relevant and very dangerous. And it seems GNOME is planning to take the same approach for other apps. This is a problem because both unity and GNOME 3 would have completely different approaches to removing the menu bar. It is more of a problem, because major apps like Firefox and LibreOffice are unlikely to take the gear approach. So unity cannot simply switch to using gears instead of global menu bars. Something will have to be done if we don't want the whole default OS to be horribly inconsistent.


> **Linux_junkie said:**
> Now we all know that Unity is a shell for Gnome 3 and with the recent changes announced by Gnome in to the direction that particular desktop is heading and with Canonical's decision to use an older version of Nautilus in its next version. Do you think it is time for Canonical to develop Unity in to a standard alone desktop environment?

Or just continue to use the Gnome 3 libraries?
There is a difference between GTK and gnome-shell and apps. I think it is quite reliable to use GTK3 as it will still be used by applications from cinnamon or unity as well as Gnome3 and probably XFCE/LXDE/OpenBox once they migrate. 

The specific Gnome apps are what are taking strange directions. But there will always be forks and alternatives even if the worst thing happens.

Since canonical has limited resources, I think it is more likely we'll see unity adapting managing itself to these changes rather than keep battling the changes to adapt them to unity.

---

### Post by Dragonbite on 2012-09-19
> **vexorian said:**
> Dual panels is something I never used, but by using compiz' feature you can place one nautilus window to the left side and another to the right side anyway.

See, now I use dual panels all of the time because it is more space-efficient on my 14" 4:3 screen than throwing multiple nautiluses on the two sides.

---

### Post by vexorian on 2012-09-19
To be honest I don't use that dual window thing either.

I just use tabs.

---

### Post by forrestcupp on 2012-09-19
> **Dragonbite said:**
> Wouldn't they be able to use the GTK toolkit yet rebuild some key components (Unity, file manager, etc.) like how Xfce?

I thought Xfce was a GTK based desktop environment that has gone and built their own file manager (Thunar) and other applications but all other applications run just fine.

I'm wading into waters I don't know here, so if I am completely off base, let me know.
Yeah, I think that's what they should do. That's basically what I meant by the toolkit and libs. But I don't think they want to invest that much into recreating everything. 

And I don't really think Nautilus needs to be forked. It's already been forked a couple of times. But honestly, I don't care. I use KDE. :)

---

### Post by MG&amp;TL on 2012-09-19
> **forrestcupp said:**
> But honestly, I don't care. I use KDE. :)

Smart-alec. :P

---

### Post by Primefalcon on 2012-09-19
> **vexorian said:**
> To be honest I don't use that dual window thing either.

I just use tabs.
I use that all the time, especially when dealing with remote systems

---

### Post by mamamia88 on 2012-09-19
Why reinvent the wheel and start completely from scratch?    Next thing you will be telling me that Ubuntu should come up with it's own kernel breaking complete compatibility with the rest of linux.  One of the things I love about linux is that anyone can see the source code and improve upon it.   This is a much better option than trying to create something completely from scratch.    Heck that's how linux got started.   A college kid was studying about minix and thought he could do it better.

---

### Post by vexorian on 2012-09-19
You sort of need to reinvent the wheel when all the wheels around you happen to be square shaped.

---

### Post by mr john on 2012-09-20
Ubuntu/Cannonical doesn't have enough manpower to pull that sort of thing off. To be fair I'm surprised that they actually managed to do Unity. Saying that, there are some performance issues with Unity that are yet to be resolved. It's slower than Gnome2 and less intuitive. Gnome 3 is a mess too. It seems that Linux on the desktop is in disarray, because nobody has a really good solution to replace gnome 2.

---

### Post by fontis on 2012-09-20
> **vexorian said:**
> You sort of need to reinvent the wheel when all the wheels around you happen to be square shaped.

+1

[quote=mr john] It seems that Linux on the desktop is in disarray, because nobody has a really good solution to replace gnome 2.[/quote]

KDE is a great solution :)

---

### Post by NormanFLinux on 2012-09-20
They can move to Gala - dump Compiz and Unity will run smoother and faster. Since they don't agree with GNOME's vision for the desktop, Ubuntu will try to adapt applications to its own needs. More or less its going to become another desktop environment - the break with GNOME was a long time in coming and Ubuntu is going on its own path. Linux Mint is doing the same with Cinnamon and GNOME is going its own way, too. So we have more choices than ever before in Linux and if you don't like what Canonical offers, someone else will have something more to your liking.

Its not like with Windows where you take or leave the desktop Microsoft offers for a particular version of Windows.

---

### Post by Jakin on 2012-09-20
> **fontis said:**
> +1



KDE is a great solution :)


:popcorn:

---

### Post by forrestcupp on 2012-09-20
> **fontis said:**
> 
KDE is a great solution :)
+1

KDE sure doesn't get enough love around here. Maybe people don't know that it runs a lot lighter with the latest version in the repos. I honestly can't see why anyone is fussing over Unity, Gnome Shell, and Cinnamon, when we have KDE right in front of us.

---

### Post by vasa1 on 2012-09-20
> **forrestcupp said:**
> .. I honestly can't see why anyone is fussing over Unity, Gnome Shell, and Cinnamon, when we have KDE right in front of us.
And Lubuntu, over which I'm fussing right now ;)

---

### Post by Primefalcon on 2012-09-20
Well XFCE is more like old gnome 2 than KDE is.... and honestly I have been seeing a lot of the Unity & Gnome 3 haters go there... To be fair XFCE is a really good desktop.

I love my Unity Desktop though....

---

### Post by Dragonbite on 2012-09-20
> **forrestcupp said:**
> +1

KDE sure doesn't get enough love around here. Maybe people don't know that it runs a lot lighter with the latest version in the repos. I honestly can't see why anyone is fussing over Unity, Gnome Shell, and Cinnamon, when we have KDE right in front of us.

Try the openSUSE forums... it is almost the opposite :)

---

### Post by forrestcupp on 2012-09-20
> **Primefalcon said:**
> Well XFCE is more like old gnome 2 than KDE is.... and honestly I have been seeing a lot of the Unity & Gnome 3 haters go there... To be fair XFCE is a really good desktop.

I love my Unity Desktop though....True. But in my opinion, modern KDE is much greater than Gnome 2.

> **Dragonbite said:**
> Try the openSUSE forums... it is almost the opposite :)
I'll have to go check it out. ;)

---

### Post by forrestcupp on 2012-09-20
> **vasa1 said:**
> And Lubuntu, over which I'm fussing right now ;)

Lubuntu has a real purpose for people with low specs. Even Xfce is starting to get a little fat, compared to what it was.

---

### Post by fontis on 2012-09-20
> **forrestcupp said:**
> Lubuntu has a real purpose for people with low specs. Even Xfce is starting to get a little fat, compared to what it was.

True. I remember back in the dayz Xfce was kind of like a tiny step more than blackbox lol. Nowadays Xfce reminds me more of gnome2.

---

### Post by Artemis3 on 2012-09-21
Pure XFCE can take about 50MiB of ram, its Xubuntu that bundles a lot of junk with it.

To test: Install ubuntu minimal, (command line) then apt-get the xfce4 package instead of xubuntu-desktop.

---

### Post by forrestcupp on 2012-09-21
> **Artemis3 said:**
> Pure XFCE can take about 50MiB of ram, its Xubuntu that bundles a lot of junk with it.

To test: Install ubuntu minimal, (command line) then apt-get the xfce4 package instead of xubuntu-desktop.

Fair point. I'll change my statement to say that Lubuntu has a real purpose over *Xubuntu* for people with low specs.

---

### Post by Gremlinzzz on 2012-09-21
Unity 6.6.0 Released, Gets New Animations And 2 New Lenses
seems to be improving,
Unity 6.6.0 has just been uploaded to the Ubuntu 12.10 Quantal Quetzal proposed repositories, bringing some polish for various aspects like the Dash Previews, animations, 2 new default lenses and more.

Unity 6.6.0 introduces a new animation for Dash previews as well as a new minimize animation. You can see them both in action in the video below:

[http://www.webupd8.org/2012/09/unity-660-released-in-ubuntu-1210.html](http://www.webupd8.org/2012/09/unity-660-released-in-ubuntu-1210.html)

---

### Post by josephmills on 2012-09-21
New Unity 6.6 + built in compiz effects + metacity = stand alone DE 
I mean now that unity can run of off metacity alone is that not enough ?  Also With Unty standalone. There is always going to be gtk code in there or so I think. But with NUX getting better and better each day. It is only a matter of time till unity will act and feel like it is coming from a gaming engine.

---

### Post by vexorian on 2012-09-21
> **josephmills said:**
> New Unity 6.6 + built in compiz effects + metacity = stand alone DE 
I mean now that unity can run of off metacity alone is that not enough ?  Also With Unty standalone. There is always going to be gtk code in there or so I think. But with NUX getting better and better each day. It is only a matter of time till unity will act and feel like it is coming from a gaming engine.
Is that true? If we can run unity with metacity then that's great news for performance.

---

### Post by josephmills on 2012-09-21
> **vexorian said:**
> Is that true? If we can run unity with metacity then that's great news for performance.

That would be the future or so it seems  :) 

I would also say keep a eye on 

[http://www.linaro.org/linaro-blog/2011/07/22/linaro-11-06-release-features-unity-3d-port-for-arm/](http://www.linaro.org/linaro-blog/2011/07/22/linaro-11-06-release-features-unity-3d-port-for-arm/)

---

### Post by litiform on 2012-10-12
Canonical would need a lot more financing to do this.

---

