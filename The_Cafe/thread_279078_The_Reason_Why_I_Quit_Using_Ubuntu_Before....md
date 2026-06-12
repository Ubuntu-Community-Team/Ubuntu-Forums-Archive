---
title: "The Reason Why I Quit Using Ubuntu Before..."
date: 2006-10-17
forum: The Cafe
---

### Post by kenweill on 2006-10-17
Im not sure if this is the right place to post this topic.

I quit using Ubuntu 6.06LTS(with GNOME) before because I have had problems. Then I tried using Kubuntu 6.06LTS(with KDE).

Four months later, I tried installing ubuntu-desktop under Kubuntu. And now, I still encounter the same problem I have experience before. I guess no one but me, have only encountered this problem. And is the same reason, its not solved.

Well, heres my problem.

I always wanted to customize how my GNOME desktop looks by changing its THEME. Under Breezy before, I get used with Crux theme + Redmond window.

Now, under Dapper, I cant customize my GNOME desktop and have this problem.

Right after clicking the Crux theme, I got this message:

> 
WARNING:
"CLOCK" has quit unexpectedly.
If you reload a panel object, it will automatically
be added back to the panel.

with 2 buttons, "Dont Reload" and "Reload".

So I select and press the "Reload" button, having another message:

> 
QUESTION:
The panel encountered a problem while
loading "OAFIID:GNOME_ClockApplet".
Do you want to delete the applet from your configuration?

with 2 buttons, "Dont Delete" and "Delete"

Of course, I select "Dont Delete".

Then, it works just fine. Only, the clock is missing, and all icons are changed, which I think is normal. Icons really change when changing theme, i think.

The worst problem arises after a reboot, shutdown, or logout.

After signing in, it still displays the rectangle window(dont know whats the name of that), with buttons displaying below the Ubuntu word.

Then it just displays a brown background, and a white bar above and below blinking. Nothing happens. The only way I can do is to press the power button, turning off the computer.

Since I have 2 accounts in my computer, the sudoer account and another account, i tried doing the same procedure in my other account. 

Same problem arises.

Before, I have trouble logging in in both accounts since both accounts cant have a GUI already.

Now, since i started with Kubuntu, and installed ubuntu-desktop, after having this same problem like before, I can just switch back to use KDE instead of GNOME.

What should I do to solve the problem?
Is this problem only happened to me?
Is there any way around this kind of problem?

---

### Post by ComplexNumber on 2006-10-17
the crux theme is unmaintained (or so i've heard). i've also heard that they are getting rid of it from the next release of gtk-engines.
try using adifferent theme. honestly, crux really is an old and outdated theme and theme engine.

---

### Post by kenweill on 2006-10-17
> **ComplexNumber said:**
> the crux theme is unmaintained (or so i've heard). i've also heard that they are getting rid of it from the next release of gtk-engines.
try using adifferent theme. honestly, crux really is an old and outdated theme and theme engine.

So, it should not be there. If its unmaintained, and if it just causes problems, it should not be there. Its LTS. Which means it should not be there in 3 years.

My problem now is on how I can use GNOME again now that I cant get to the GUI of GNOME, on both accounts.

---

### Post by DoctorMO on 2006-10-17
[ctrl][alt][F1] will bring you to a basic logon prompt, logon with your normal user.

Type in > rm -fr ~/.gnome ~/.gnome2

that should remove all your gnome config and reset everything back to default.

---

### Post by ComplexNumber on 2006-10-17
> If its unmaintained, and if it just causes problems, it should not be there.thats what i said here:
[quote=ComplexNumber] i've also heard that they are getting rid of it from the next release of gtk-engines.[/quote]

---

### Post by toon on 2006-10-17
You stop using a distribution because you can't use *one* special theme? Wow..

---

### Post by fuscia on 2006-10-17
> **toon said:**
> You stop using a distribution because you can't use *one* special theme? Wow..

i'd do it. 

i've never had trouble with crux, at all. you could try using icewm, which also has a crux theme (blue and teal), as a replacement for metacity if you can't solve your problem.

---

### Post by kingjere on 2006-10-17
I personally think that with all of the time and effort going into theme production (i.e. [www.gnome-look.org](www.gnome-look.org)) it is our duty, no, responsibility to have incredible looking desktops. After all what good is using linux if you can't look good doing it?;) 

Seriously, kudos to all those folks developing themes for my favorite OS.

---

### Post by kenweill on 2006-10-17
> **DoctorMO said:**
> [ctrl][alt][F1] will bring you to a basic logon prompt, logon with your normal user.

Type in 

that should remove all your gnome config and reset everything back to default.

It doesnt work. Still the same problem. With a dialog box titled "Error" with no contents. Just blank.

I did create a new account from the terminal(tty1) and this new account can now login to GNOME without errors.

But how can I make this new account a sudoer user?
And can I still fix the 2 other accounts?

---

### Post by kenweill on 2006-10-17
> **toon said:**
> You stop using a distribution because you can't use *one* special theme? Wow..

Not exactly. Im using Kubuntu, still an Ubuntu with KDE setup.
I think its not a problem in Ubuntu in general but in GNOME. Works fine in KDE. But I prefer GNOME.

---

### Post by ice60 on 2006-10-17
> **kenweill said:**
> Not exactly. Im using Kubuntu, still an Ubuntu with KDE setup.
I think its not a problem in Ubuntu in general but in GNOME. Works fine in KDE. But I prefer GNOME.

you can use xfce with nautilus, i do that sometimes. xfce uses alot of the gnome libs so it will look more like gnome then KDE. maybe that will work, but maybe not :confused:

---

### Post by d3v1ant_0n3 on 2006-10-17
I use GNOME and KDE also, been having trouble with the panels' applets quitting out, and startup taking a silly amount of time...I think the last theme I had on was Crux. Would this explain it?

---

### Post by kenweill on 2006-10-18
Ok. Thanx for all your replies.
I just did reinstall everything. And avoid customizing my theme by removing the Theme shortcut through Alcarte Menu Editor. I did remove it in all user accounts.

It just took me about 10 hours to back-up, reinstall, then restore everything.

I'll just try to customize it later after downloading some updates from the repos. I just hope this would be fixed.

If Crux is the reason, then an update removing Crux would be a good idea.

Who knows? This same problem may frustrate other new Ubuntu users migrating from Windows.

---

### Post by Wolki on 2006-10-18
To people who have such problems with themes, did you ever set your gtk theme through KDE? They use different methods, and combining them may lead to bad results.

FWIW, Crux seems to work fine here on edgy... I think it did in Dapper, too, but I can't test it right now.

---

