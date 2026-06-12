---
title: "Lubuntu 18.04.2 LTS - Terminal - root Prompt Colour"
date: 2019-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by electrosteam on 2019-04-29
On my system, my home folder prompt is an attractive green colour, but the root prompt is the standard white.

What do others use for the root prompt ?

John

---

### Post by DuckHook on 2019-04-29
Red. I seriously thought about *flashing* red but reconsidered before implementing. As a corollary observation, too many new users have a cavalier attitude towards root and get into heaps of trouble using it. With sudo, it is almost never necessary. It seems only fitting to invoke it with the equivalent of a three alarm fire.

---

### Post by wildmanne39 on 2019-04-29
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by yetimon_64 on 2019-05-02
> **DuckHook said:**
> Red. I seriously thought about *flashing* red but reconsidered before implementing...
My biggest problem with a flashing prompt is taking a screenshot of it, the next screenshot took 4 attempts to catch it; the red coloured "root" and "#" flash when logged into a root terminal in the GUI, on the console they stay solid red with no flashing thankfully...
[ATTACH=CONFIG]283146[/ATTACH]
Just out of interest, what made you reconsider the flashing prompt ?

I definitely agree that a root terminal is a dangerous thing, particularly for a new starter. I do set up a custom root prompt but tend to pay it the respect it deserves and only very rarely need to use it. The vast majority of my needs for root usage are quite well suited to using the sudo command with my normal user prompt also shown in the above screenshot.

Cheers, yeti.

---

### Post by DuckHook on 2019-05-02
> **yetimon_64 said:**
> …Just out of interest, what made you reconsider the flashing prompt ?
It would quickly become really distracting and hard on the eyes. Yes, I want to be reminded that I'm tooling around as root, but the flashing would drive me nuts.
> …I definitely agree that a root terminal is a dangerous thing, particularly for a new starter. I do set up a custom root prompt but tend to pay it the respect it deserves and only very rarely need to use it.
I have a few appliances—routers and one commercial NAS—that only have root accounts, so when ssh-ing into them, I need to be reminded that I am not in a local shell session. I have been caught out more than once typing something into the terminal only to be brought up short when I realize that I wasn't even working within my desktop rig. One can do a lot of damage with that sort of confusion, so an obvious root prompt is a necessity.

---

### Post by yetimon_64 on 2019-05-02
> **DuckHook said:**
> ... but the flashing would drive me nuts....

I can understand that, I actually have two lines for the "red/white background" root prompt in my /root/.bashrc file; one flashing the other static.

Because I so rarely need to use a root terminal for long periods the flashing one tends to be left on as an "extreme" reminder of where I a working from.

---

### Post by him610 on 2019-05-03
Personally, I have a difficult time reading red on black or black on red. Back in the days when we only had sixteen colors, my preference was for light blue (cyan?) on black. Nowadays, it's just white on black. I use *sudo su* only when absolutely necessary, and then keep an eye on the prompt.

---

### Post by yetimon_64 on 2019-05-03
> **him610 said:**
> Personally, I have a difficult time reading red on black or black on red...It is near impossible to see red text on a black background for me, even if the red flashes. I always set a white "highlight" bar when using red text as shown in the screenshot in post #4. The main terminal background is black with some transparency set in the screenshot. Setting a highlight bar behind the prompt is very useful when terminal background full transparency is used. You don't lose the prompt on a similar colored desktop background so easily with the highlight bar. Cheers, yeti.

---

### Post by ajgreeny on 2019-05-03
Like DuckHook I also use a red terminal prompt for the very few times I use a root terminal (from using command **sudo -i**), and for my normal user prompt I use the bright green that I think is the default, though I honestly can't remember if I had to uncomment the **force_color_prompt=yes** in my **.bashrc** file to get it.

It is simply a reminder that I'm using a root terminal which is dangerous to leave running just in case I make a mess of some command and cause big problems for myself.

PS:
I use yellow text normally on a black background rather than white as I find it less glaring.

---

