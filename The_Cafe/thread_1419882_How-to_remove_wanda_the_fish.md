---
title: "How-to remove wanda the fish?"
date: 2010-03-02
forum: The Cafe
---

### Post by samh785 on 2010-03-02
So I help out in the middle school computer lab in my school (high school middle school combo). The entire middle school lab runs ubuntu, but we are finding that wanda the fish gnome panel app isn't completely appropriate for the kids. Is there anyway to remove this, or at least disable it? 

Thanks in advance,
Sam

---

### Post by The Toxic Mite on 2010-03-02
Can I ask _why_ you find it inappropriate?

---

### Post by Enigmapond on 2010-03-02
Too Cute...you can disable it by, I believe, just right clicking on it and removing it from the panel...

---

### Post by Arkitekt on 2010-03-02
I was wondering the same thing, can't imagine how an animated swimming fish would be considered inappropriate by some

But if you right click it in the panel and unlock it, then you should be able to remove it from the panel

---

### Post by Tristam Green on 2010-03-02
Because it's a distraction...

---

### Post by Post Monkeh on 2010-03-02
i think he wants to remove it as in stop the kids being able to add it to the panel.

---

### Post by xpod on 2010-03-02
> **The Toxic Mite said:**
> Can I ask _why_ you find it inappropriate?

Whatever it is i just hope they dont discover "free the fish", or worse, the Compiz atlantis plugin.

---

### Post by The Toxic Mite on 2010-03-02
> **xpod said:**
> Whatever it is i just hope they dont discover "free the fish", or worse, the Compiz atlantis plugin.

What's so bad about the Atlantis plugin?

---

### Post by xpod on 2010-03-02
> **The Toxic Mite said:**
> What's so bad about the Atlantis plugin?

More fish of course.

---

### Post by juancarlospaco on 2010-03-02
***Wanda is Nude !!!***

:)

---

### Post by steindor2 on 2010-03-02
im not really sure, but you can right click in preferances and change the command that is run when you click the fish to something else that doesn't bother you.

---

### Post by jwbrase on 2010-03-02
> **The Toxic Mite said:**
> Can I ask _why_ you find it inappropriate?

Not inappropriate as in "it will corrupt the kids". Inappropriate as in "the kids are playing with the fish and not getting any work done".

---

### Post by ubunterooster on 2010-03-02
> **steindor2 said:**
> im not really sure, but you can right click in preferances and change the command that is run when you click the fish to something else that doesn't bother you.
+1

---

### Post by ubunterooster on 2010-03-02
> **ubunterooster said:**
> +1
or

```

whereis fortune

```

Delete the given wanda file. Otherwise a student just pushes alt-f2 and types 
```

fortune

```
and wanda starts right up.

---

### Post by The Toxic Mite on 2010-03-02
```

calvinps@the-toxic-mite:~$ whereis wanda
wanda: [COLOR=Silver]# is nowhere to be seen[/COLOR]
calvinps@the-toxic-mite:~$ 

```

---

### Post by ubunterooster on 2010-03-02
oops replace "wanda" w/ "fortune"

---

### Post by haydoni on 2010-03-02
When you click on Wanda the fish I'm given an error message: "unable to find command to execute", is this a bug shared by all?

---

### Post by LowSky on 2010-03-02
Hasn't fortune been removed from 9.10 and I think on 9.04 too, at least it is on mine. I had to re-add the packages to get Wanda to speak again.

How much of a distraction can Wanda be if she does nothing much but swim?

---

### Post by ubunterooster on 2010-03-02
It's expected for them to be using an LTS [8.10] in a school enviroment.

---

### Post by tgalati4 on 2010-03-02
We could modify wanda to say every 20 minutes:

"Did you take your pills today?"

That would help turn distraction back into focus.

---

### Post by Kai69 on 2010-03-02
Just for a laugh put Wanda on my panel. Why does it say "Wanda the fish, the fortune teller" Whats that about ??

---

### Post by ubunterooster on 2010-03-02
wanda is supposed to tell jokes, it got parts taken out so unless you put them back in all it does is swim

---

### Post by Kai69 on 2010-03-02
> **ubunterooster said:**
> wanda is supposed to tell jokes, it got parts taken out so unless you put them back in all it does is swim
Thanks I never bothered with it before I just have temp sensors and a weather app on mine :)

---

### Post by juancarlospaco on 2010-03-02
> **ubunterooster said:**
> wanda is supposed to tell jokes, it got parts taken out so unless you put them back in all it does is swim

*But still naked, maybe we can fork it, to dress her up, pr0n-less wanda* :)

---

### Post by dragos240 on 2010-03-02
killall gnome-panel

---

### Post by ubunterooster on 2010-03-02
> **dragos240 said:**
> killall gnome-panel
not a good idea

---

### Post by ibuclaw on 2010-03-02
Hmm, just for clarification, what are you trying to do?

1) Prevent users from adding applets to the panel.
or
2) Prevent users from doing Alt+F2 and running "free the fish".

Either way, it should be doable via this general guide:
[http://library.gnome.org/admin/system-admin-guide/stable/lockdown-manual.html.en](http://library.gnome.org/admin/system-admin-guide/stable/lockdown-manual.html.en)

Regards
Iain

---

### Post by samh785 on 2010-03-03
> **jwbrase said:**
> Not inappropriate as in "it will corrupt the kids". Inappropriate as in "the kids are playing with the fish and not getting any work done".
this
> **ibuclaw said:**
> Prevent users from adding applets to the panel.

Preventing *certain applets *from being added to the panel.

---

### Post by ubunterooster on 2010-03-04
****** bad/dangerous advice removed by staff *****

---

### Post by Mr. Picklesworth on 2010-03-04
> **ubunterooster said:**
> ```

**** bad/dangerous advice removed by staff ***
```

Eek! Don't do that :o
It hurts Debian's feelings when you tinker with the files it manages.

Remove the package "fortune-mod" and you're done. (sudo apt-get remove fortune-mod , or find it in Synaptic and mark it for removal).

---

### Post by mcduck on 2010-03-04
I agree with ibuclaw, if you want to prevent the users from messing with panel applets then the best way to do that it to *prevent the users from messing with panel applets* (lock the panel, Gnome sure does have such option).

edit: the original message got edited so I removed my response as well... :)

---

### Post by handy on 2010-03-04
It has probably been posted a dozen times already; but when I read the title of this thread, I see Kevin Kline eating Wanda (the fish).

---

### Post by nothingspecial on 2010-03-04
You`d better not tell them about xpenguins then.

---

### Post by ubunterooster on 2010-03-04
> **ubunterooster said:**
> ****** bad/dangerous advice removed by staff *****

sorry [roosters have little brains].
Thanks for editing it, Staff..

---

