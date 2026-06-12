---
title: "Spell check should be built into the kernel."
date: 2009-07-24
forum: The Cafe
---

### Post by Mateo on 2009-07-24
Why not?

---

### Post by issih on 2009-07-24
I counter with... why?

In all seriousness, built into the kernel is overkill on a grand scale, it should be a system level service in my opinion, one which all apps have access to, but theres no earthly reason for it to be in the kernel, just have it run as a daemon.

---

### Post by Mateo on 2009-07-24
> **issih said:**
> I counter with... why?

In all seriousness, built into the kernel is overkill on a grand scale, it should be a system level service in my opinion, one which all apps have access to, but theres no earthly reason for it to be in the kernel, just have it run as a daemon.

If it's a service then other applications have to be programmed to use it.  I want it automatically part of every app.

---

### Post by OutOfReach on 2009-07-24
> **Mateo said:**
> If it's a service then other applications have to be programmed to use it.  I want it automatically part of every app.
It can't just automatically be in every app, even if it was programmed into the kernel (which does not make sense at all) it would still have to be implemented into the app.

---

### Post by Mateo on 2009-07-24
> **OutOfReach said:**
> It can't just automatically be in every app, even if it was programmed into the kernel (which does not make sense at all) it would still have to be implemented into the app.

why? when you program apps, do you have to implement characters appearing on the screen when someone presses a keyboard key?  I don't.  That's already being taken care of for me.

---

### Post by JillSwift on 2009-07-24
> **Mateo said:**
> why? when you program apps, do you have to implement characters appearing on the screen when someone presses a keyboard key?  I don't.  That's already being taken care of for me.
Strange.

You do realize that, under a GUI at least, it's not the kernel doing that. If I'm not mistaken, even on the CLI, it's the shell handling that.

Whither kernel or daemon, you do have to code your app to make use of the resource.

Some form of standardized spell-check daemon would be nice. In the kernel, it'd just be bloat for many applications. Leave the kernel to do kernel things.

---

### Post by utUtu on 2009-07-24
> **Mateo said:**
> If it's a service then other applications have to be programmed to use it.  I want it automatically part of every app.

Go ahead and build it.

---

### Post by pluviosity on 2009-07-24
Spell check for what, English?  What about every other language out there?  Considering that most people speak one or two languages, you either only include one or a few languages - thus leaving out a lot of languages and irking a bunch of people - or include all languages, which is completely unnecessary.

---

### Post by pastalavista on 2009-07-24
the more productive, logical choice would be to learn how to spell

---

### Post by keiichidono on 2009-07-24
> **issih said:**
> I counter with... why?

In all seriousness, built into the kernel is overkill on a grand scale, it should be a system level service in my opinion, one which all apps have access to, but theres no earthly reason for it to be in the kernel, just have it run as a daemon.

I agree that it should be a daemon that apps can make use of. And the daemon will install spell check languages depending on what language you use on the system. Meaning OpenOffice/Firefox/Chromium/Pidgin will all use the same spell check library and it'll probably lighten the load on the LiveCD because less multiple libraries of the same language is being installed. but sadly, no one is gonna actually do anything towards this so this idea is gonna fade away like all most other great user ideas. =\

---

### Post by stmiller on 2009-07-24
```
man aspell
```

:)

---

### Post by swoll1980 on 2009-07-24
> **pastalavista said:**
> the more productive, logical choice would be to learn how to spell

The best spellers in the world can't spell every word right.

---

### Post by MaxIBoy on 2009-07-24
Not a daemon, a dynamically-linked library. Otherwise, it would have to be designed to handle requests from multiple programs at once, which would make it more complicated than needed.


And, hey guess what, such libraries already exist! Problem solved.  (Although it would be nice if everyone could settle on just one, I'll be the first to admit that.)

---

### Post by sertse on 2009-07-25
> **CalvinB said:**
> Meaning OpenOffice/Firefox/Chromium/Pidgin will all use the same spell check library...sadly, no one is gonna actually do anything towards this so this idea is gonna fade away like all most other great user ideas. =\

Openoffice, Firefox and Pidgin all use myspell dictionaries iirc.

---

### Post by keiichidono on 2009-07-25
> **sertse said:**
> Openoffice, Firefox and Pidgin all use myspell dictionaries iirc.

Empathy? Chromium? It's not good unless most/all apps that need spell checker use it.

---

### Post by MaxIBoy on 2009-07-25
Didn't the Chromium developers invent a whole new graphics library (which was nearly the same as Cairo and served the same purpose,) then complain about how the graphics libraries in Linux are too fragmented? Isn't it just a little too much to expect Chromium *not* to reinvent the wheel?

---

### Post by sertse on 2009-07-25
> **CalvinB said:**
> Empathy? Chromium? It's not good unless most/all apps that need spell checker use it.

Empathy uses libenchant1c2a, which is a wrapper for many dictionary backends, including myspell. Evolution btw, uses it too. XChat also can also use myspell.

Yes, I am aware you can keep naming examples eventually till there's some I can't answer (You should of said Abiword ;) - it has to use aspell), but cmon, you've given 5 examples (and I added Xchat, Evolution making 7), I've shown 4 (6) of the 5 (7) can be used by the same dictionary. There probably countless more, do you wish to continue?

Though I should bring what I'll proving back on topic: I think it's more of a sign that a lot of apps *are* using the same spell check, and more the case why the remaining ones aren't. The one that aren't are the exception, not the rule as you're been trying to make out.

---

### Post by Giant Speck on 2009-07-25
Why add bloat to the kernel itself?  While we're at it, why don't we just build Evolution right into the kernel so that everyone can enjoy it!  :roll:

---

### Post by hessiess on 2009-07-25
Spell checking definatly should not be built into the kernel, though there should be a system-wide spell checking lib. This would avoid the current situation where most apps have an absolutly awful spell checker, and the best one I have found in *ANY* desktop application on Linux lives in Vim.

---

### Post by magmon on 2009-07-25
Spell check doesn't recognize many names. For example, my last name is Ciancio (pronounced Chan-cho), no spell check I've ever seen has said it was spelled right, and if it is built into the kernel, wouldn't it auto correct misspelled words? If so, I would be unable to correctly spell my last name while using ubuntu.

---

### Post by keiichidono on 2009-07-25
> **sertse said:**
> Empathy uses libenchant1c2a, which is a wrapper for many dictionary backends, including myspell. Evolution btw, uses it too. XChat also can also use myspell.

Yes, I am aware you can keep naming examples eventually till there's some I can't answer (You should of said Abiword ;) - it has to use aspell), but cmon, you've given 5 examples (and I added Xchat, Evolution making 7), I've shown 4 (6) of the 5 (7) can be used by the same dictionary. There probably countless more, do you wish to continue?

Though I should bring what I'll proving back on topic: I think it's more of a sign that a lot of apps *are* using the same spell check, and more the case why the remaining ones aren't. The one that aren't are the exception, not the rule as you're been trying to make out.

Yeah well I guess you're right. I'm just irked at the fact that [Linux is too fragmented]("http://bagoflies.wordpress.com/2009/07/21/abundance-of-minor-things/"). But not here.

---

### Post by gn2 on 2009-07-25
> **swoll1980 said:**
> The best spellers in the world can't spell every word right.

Neither can the best spell checkers.

---

### Post by phrostbyte on 2009-07-25
Spell check built in the kernel is nonsense.

You probably want spell check to be built into text entry related GTK+ widgets.

---

### Post by sanderella on 2009-07-25
**No, it shouldn't!**

I hate spell check, it's so intrusive. I always switch it off.

---

### Post by t0p on 2009-07-25
> **pastalavista said:**
> the more productive, logical choice would be to learn how to spell

Indeed.  Incorporate spell check into *your* kernel.  The one in your bonce. 

I find spell check to be an irritating nonsense.  When spell check claims that I've 'misspelt' a word, it is generally because I *want* that word 'misspelt'.

---

### Post by Viva on 2009-07-25
Do you mean built into GNOME? They can add an "Enable Spell Check" flag for text controls. Won't be too difficult, but I don't think it is worth it.

---

### Post by toupeiro on 2009-07-25
no no no no no no no no NO NO NO NO **NO!**

The last thing we need is all this arbitrary stuff getting thrown in the Kernel.  A Kernel, fundamentally, has a very specific job to do, which shouldn't include teaching people how to spell.  Look at how bloated and ridiculous the windows Kernel is because of this mentality?!

---

### Post by 23meg on 2009-07-25
> **CalvinB said:**
> Yeah well I guess you're right. I'm just irked at the fact that [Linux is too fragmented]("http://bagoflies.wordpress.com/2009/07/21/abundance-of-minor-things/"). But not here.

You'll find various rebuttals of that "fact" [here]("http://ubuntuforums.org/showthread.php?t=328824").

---

### Post by SuperSonic4 on 2009-07-25
Certainly not. Even in English there are different variants not to mention other languages. For example *colour* and *color* are both English although only the former is acceptable in England.

If German were to be put in would it put a upper case letter for every noun? It's much better to let the user install whichever they like (including more than one - I have English (UK) and German (Germany) on my  computer)

---

