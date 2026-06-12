---
title: "Tilda terminal"
date: 2007-05-20
forum: The Cafe
---

### Post by DarkN00b on 2007-05-20
I'm posting this here because it isn't a support question, more of a suggestion.

I came across a program called Tilda that is basically a terminal. The cool thing is that it works like the console in many FPS games like Quake, Tremulous and Alice. I've posted a pic and a link to someone using it on Youtube. It scrolls smoothly and I have fallen in love with it. 

I have it set to start on boot and have had no problems with it running alongside Beryl. I changed the key combo to bring it down to CTRL+j, but any key combo can be used as long as it doesn't conflict with other combos.

If you'd like to try something different, try Tilda.

Link to video (It runs much smoother than you see here): [Tilda on YouTube]("http://www.youtube.com/watch?v=tOxqEu7Pkk8")

PIC:

---

### Post by %hMa@?b&lt;C on 2007-05-20
reminds me a lot of that kde one that you press f12 and it comes down from the tom of the screen... for get the name

---

### Post by maniacmusician on 2007-05-20
> **jeffc313 said:**
> reminds me a lot of that kde one that you press f12 and it comes down from the tom of the screen... for get the name
yakuake. 

Tilda, in my experience, is not quite as good as yakuake. This will be even more true with the next version of yakuake; it will support "split" windows. so in one dropdown, you can have 4 terminals, and each of those terminals can have tabs, etc.

edit: and of course yakuake lets you choose different access and control keys as well, other than F12. Mine is Super + Space

---

### Post by Adamant1988 on 2007-05-20
I love Tilda, it's my always ready terminal, there to help me when duty calls.  It's just like Yakuake. :)

---

### Post by DarkN00b on 2007-05-20
The Stock keybinding for Tilda is SHIFT+F12. This may be the same program.

---

### Post by Adamant1988 on 2007-05-20
> **DarkN00b said:**
> The Stock keybinding for Tilda is SHIFT+F12. This may be the same program.

I'm sorry to hijack the thread, but I need to get this said...

[size=72] ALL HAIL LORD ILPALAZZO! [/size]

---

### Post by DarkN00b on 2007-05-20
> **Adamant1988 said:**
> I'm sorry to hijack the thread, but I need to get this said...

[size=72] ALL HAIL LORD ILPALAZZO! [/size]

Your tribute is acceptable. When A.C.R.O.S.S.'s  conquest of F City is complete, you shall have a place.

---

### Post by ticopelp on 2007-05-20
Looks really interesting, but I couldn't get it to work properly. The transparency and keybinding settings wouldn't "stick," and the text in the terminal would occasionally glitch out badly.

---

### Post by maniacmusician on 2007-05-20
> **ticopelp said:**
> Looks really interesting, but I couldn't get it to work properly. The transparency and keybinding settings wouldn't "stick," and the text in the terminal would occasionally glitch out badly.
I wonder if yakuake will work on Gnome? It may work out better for you if it does.

---

### Post by Adamant1988 on 2007-05-20
> **maniacmusician said:**
> I wonder if yakuake will work on Gnome? It may work out better for you if it does.

It's kind of buggy really, I'm not very fond of it on GNOME.. Tilda functions similarly for my needs though.

---

### Post by DarkN00b on 2007-05-20
To get values to "stick" close Tilda by typing "exit" and hitting enter. Then open a regular terminal and type ```
tilda -C
```

Make your changes there and then close the configuration window. Tilda should pop out and hide itself. Close the regular terminal and use ALT+F2 to start Tilda. Your settings should be applied. It seems like Tilda can't be reliably configured if the config program is launched from within itself.

---

### Post by ticopelp on 2007-05-20
> **maniacmusician said:**
> I wonder if yakuake will work on Gnome? It may work out better for you if it does.

I downloaded Yakuake and was going to compile it, but it said I needed kde-config. I'm kind of on the fence as to whether or not I want to try that or not.

---

### Post by maniacmusician on 2007-05-20
> **Adamant1988 said:**
> It's kind of buggy really, I'm not very fond of it on GNOME.. Tilda functions similarly for my needs though.
I prefer to keep it on kde as well. I only suggested it since tilda wasn't working well for him.

---

### Post by jiminycricket on 2007-05-20
Hmm yakuake should be in the repositories, no need to compile.

I wish tilda had a better configuration; yakuake is a lot easier to position on the screen.

---

### Post by Adamant1988 on 2007-05-20
> **jiminycricket said:**
> Hmm yakuake should be in the repositories, no need to compile.

I wish tilda had a better configuration; yakuake is a lot easier to position on the screen.

It's in Feisty's repos, I know that much.

---

### Post by ticopelp on 2007-05-20
> **DarkN00b said:**
> To get values to "stick" close Tilda by typing "exit" and hitting enter. Then open a regular terminal and type ```
tilda -C
```

Make your changes there and then close the configuration window. Tilda should pop out and hide itself. Close the regular terminal and use ALT+F2 to start Tilda. Your settings should be applied. It seems like Tilda can't be reliably configured if the config program is launched from within itself.

Oh, this was quite helpful. Thanks. I got it working a little better now. 

[QUOTE="jiminycricket"]Hmm yakuake should be in the repositories, no need to compile.[/QUOTE]

Whoops, you're right. Looks like I misspelled the filename. Well, I'll try both for a laugh.

---

### Post by DarkN00b on 2007-05-20
I found it on [GnomeFiles.org]("http://www.gnomefiles.org/index.php") but installed it from the Feisty repos.

To reiterate: Tilda configures and works well if it is not running when you configure it. Kill Tilda before you try to run the configuration program.

EDIT: OOPS, I was typing this when you posted your reply. ^

---

### Post by Tundro Walker on 2007-05-20
Another Tilda thread...LOL!  You can always tell the good programs by how many threads show up for them.

I've done Tilda over Yakuake.

I just liked Tilda more...not sure why.  I guess because it pretty much has the same options as a normal terminal screen, except it also includes animation options.  So, if you're used to messing with terminal screen options, you can easily get into Tilda.

Only issue I've had with it was when I switched on Compiz in Feisty.  I noticed the text in the Tilda screen would get all mucked up...like it was getting screen artifacts all over it, blocking out some of it.  It seemed like this would only happen if I had animated "dropdown" turned on.  If I turned it off, so Tilda would instantly appear when hot-key was pressed, no more issue.

I don't use Compiz, though, so wasn't much of an issue.  (Compiz is nice and all, but it's a resource hog, which slows down gaming, like Tremulous or Tenebrae Quake.)

One annoyance is that you need a pretty decent machine to run the transparent dropdown at a reasonable speed.  On my old 800mhz, it was slow to dropdown.  Even with the speed set pretty high (like 15 milliseconds, which is almost instantaneous), it would still take 3-4 seconds to choppily dropdown.

As flashy as the dropdown animation is, I turned it off, because I just want my terminal to show up "on demand" without any delay.  Plus, I made the tilda key my hot-key for the user terminal, and Ctrl+(tilda) for my root terminal (which I used to get my Ubuntu to auto-start when I was doing lots of tweaking, but don't anymore.)

---

### Post by Ender Black on 2007-05-20
When I try it the text gets corrupted until you hit the return key

I really like the idea though.. just couldn't figure out which setting I need to adjust to make it usable.

---

### Post by ticopelp on 2007-05-20
Thanks again, DarkN00b. Tilda is treating me quite well now.

Another newbie question, if possible; I installed Yakuake and got it running, and it cheerfully told me to hit F12 to configure it. Unfortunately, I have Beagle running, and the shortcut for Desktop Search is... F12. Any ideas on how best to work around this?

---

### Post by jiminycricket on 2007-05-20
> **Tundro Walker said:**
> 

Only issue I've had with it was when I switched on Compiz in Feisty.  I noticed the text in the Tilda screen would get all mucked up...like it was getting screen artifacts all over it, blocking out some of it.  It seemed like this would only happen if I had animated "dropdown" turned on.  If I turned it off, so Tilda would instantly appear when hot-key was pressed, no more issue.

Enable double buffering in Tilda configuration, and it fixes the text issue :)

---

### Post by jariku on 2007-05-20
I've never tried yakuake, but I have tilda installed in both of my Ubuntu boxes. I changed the default key to F1, though. :)

---

### Post by maniacmusician on 2007-05-20
> **ticopelp said:**
> Thanks again, DarkN00b. Tilda is treating me quite well now.

Another newbie question, if possible; I installed Yakuake and got it running, and it cheerfully told me to hit F12 to configure it. Unfortunately, I have Beagle running, and the shortcut for Desktop Search is... F12. Any ideas on how best to work around this?
```

sudo nano ~/.kde/share/config/yakuakerc

```

There's a section labeled Global Shortcuts, and under it, an option called AccessKey. Just change it to whatever you want. For example, mine is:

```

[Global Shortcuts]
AccessKey=Win+Space

```

---

### Post by ticopelp on 2007-05-20
Thanks, maniacmusician, that did it. Much appreciated.

They're both quite pretty. Yakuake strikes me as slightly prettier, but they both work equally well. I'm going to play around and see which one I prefer in the long run.

---

### Post by maniacmusician on 2007-05-20
> **ticopelp said:**
> Thanks, maniacmusician, that did it. Much appreciated.

They're both quite pretty. Yakuake strikes me as slightly prettier, but they both work equally well. I'm going to play around and see which one I prefer in the long run.
np. If they both work well for you, it may be wiser to go with tilda since you're in Gnome. I use Yakuake because I use KDE, and it just works very well for me

---

### Post by Tundro Walker on 2007-05-20
To configure Tilda when it's already started, just right-click in the middle of its terminal screen, and select "Preferences".  Change what you want, and you'll be good to go.

---

### Post by DouglasCaixeta on 2009-06-25
Is it possible to get the transparency working on Tilda, without having the special effects enabled?

---

### Post by monsterstack on 2009-06-25
I always change the keybinding to **`**. Now it's just like Quake!

---

### Post by starcraft.man on 2009-06-25
> **DouglasCaixeta said:**
> Is it possible to get the transparency working on Tilda, without having the special effects enabled?

I'm not sure what your referring to by special effects. Do you mean the appearances option to turn on visual effects (i.e. compiz) if so, the answer is yes. Right click on an open tilda terminal > Preferences > Appearance tab > Extras > Enable transparency (set with level at right).

Don't enable this with visual effects on, it causes conflict if I'm not mistaken.

A good app for the record.

---

### Post by DouglasCaixeta on 2009-06-25
> **starcraft.man said:**
> I'm not sure what your referring to by special effects. Do you mean the appearances option to turn on visual effects (i.e. compiz) if so, the answer is yes. Right click on an open tilda terminal > Preferences > Appearance tab > Extras > Enable transparency (set with level at right).

Don't enable this with visual effects on, it causes conflict if I'm not mistaken.

A good app for the record.

Yes, that's exactly the special effects that I'm talking about.
But when I enable the transparency on tilda, I can see part of my wallpaper, not the current windows behind.
When I enable the visual effects, the transparency works ok.

But I don't want the visual effects. Even on minimal I dont like it.

---

### Post by starcraft.man on 2009-06-25
> **DouglasCaixeta said:**
> Yes, that's exactly the special effects that I'm talking about.
But when I enable the transparency on tilda, I can see part of my wallpaper, not the current windows behind.
When I enable the visual effects, the transparency works ok.

But I don't want the visual effects. Even on minimal I dont like it.

I believe that's just the way Tilda does it. To get the realtime window transparency allowing you to see under windows requires the gfx card and 3d effects, Tilda simply isn't designed to do that to my knowledge. I'm afraid your stuck choosing between the one or the other.

---

### Post by DouglasCaixeta on 2009-06-25
Yes. I already try guake and tilda, and its the same.
I have an Intel graphics card, and the visual effects are not very nice here.
I guess I will have to live without this :)

---

