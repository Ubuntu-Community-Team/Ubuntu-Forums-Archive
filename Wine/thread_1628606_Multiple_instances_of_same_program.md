---
title: "Multiple instances of same program?"
date: 2010-11-22
forum: Wine
---

### Post by inga2 on 2010-11-22
I like Eudora, and I have multiple instances in my current Windows setup to keep things organized. (Yes, I use personalities, etc.)

Wine does not allow the usual way of running multiple instances from one install, the best I can figure out. (A shortcut similar to the Windows shortcut prefaced with the code for executing in Wine does not work.)

So I figured, fine, I'll just install multiple instances in separate directories and thus use Eudora as I've done for the last 25 years or so. **However,** Wine doesn't seem to allow the installation of multiple instances of the same program, or does it?

Is there a workaround, or have I missed something? (Okay, I know about *Thunderbird*, but it doesn't do clean "redirects" as *Eudora* does. Nor does Evolution. There are features of Eudora that I use and cannot find in any other email program.)

***Can anyone help, please?***

---

### Post by bobwyajnr on 2010-11-24
> **inga2 said:**
> 
***Can anyone help, please?***

I stumbled across this [link]("https://wiki.mozilla.org/Eudora_OSE") while looking up **Eudora**. Might be of interest?

Also [**Claws Mail**]("http://www.claws-mail.org/features.php?section=general") is a very fully featured native GNU/Unix email client. Thunderbird may be popular but it's code-base is relatively new and it is not yet as powerful as more established clients. I personally plan on migrating from the **TheBat!** to **Claws Mail** as soon as I get a chance...

Wine will allow multiple installations of a program. That is the whole point behind the [WINEPREFIX]("http://wiki.jswindle.com/index.php/Wine_Prefixes") system. However doing this for an email client sounds like a bit of mess to me - if you need to run multiple instances of an email client then it's broken (in my books anyways)... :popcorn:

BTW [**Q4Wine**]("http://sourceforge.net/projects/q4wine/") is a useful (and little known) Qt GUI application for managing multiple Wine prefixes. I think it's in the repositories (certainly will be in a PPA anyway). I use it quite a lot - since it shows what Wine processes are running (on your Ubuntu system) and which prefix they are associated with (plus letting you shut them down, etc.).

Bob

---

### Post by inga2 on 2010-11-24
Thanks so much, Bob!

It looks like I have a bit of studying to do, and you gave me a sense of direction.

I was aware of the OSE of Eudora, but it seemed to be mainly stagnant, and I stopped checking up on the project. I'll have to see if they did anything significant lately. I'm delighted that they seem to be working on a Ubuntu version!! If they do a good job, all my dreams will come true -- at least in email land. ;) 

As for the multiple instance of an email program -- let's just say I have my finger in way too many pies, and it just helps to have various email addresses together in logical groups. But I'm re-thinking my strategy. ;)

Thanks again.

---

### Post by inga2 on 2010-11-25
Just want to say THANKS!! ):P[FONT=&quot] [SIZE=1]again to Bob![/SIZE][/FONT]
Your reply was helpful on so many fronts. I'm just switching over to Kubuntu, and Eudora was a primary concern. It looks like a Ubuntu version is finally ready! But the links to the WinePrefix system and Q4Wine will doubtless be useful.

I'm even looking at CLAWS. ;) Looks impressive, except that I can't tell whether or not it does transparent "redirects" or "bounces." IOW, I want to be able to redirect an email to a different recipient without the "Reply-to" automatically being my address (as it is in evolution.)

Inga
[FONT=&quot][SIZE=1]
[/SIZE][/FONT]
[FONT=&quot] 
 [/FONT]

---

