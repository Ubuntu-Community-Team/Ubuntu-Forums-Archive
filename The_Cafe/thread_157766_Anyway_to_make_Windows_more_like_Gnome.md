---
title: "Anyway to make Windows more like Gnome?"
date: 2006-04-09
forum: The Cafe
---

### Post by Nequeo on 2006-04-09
Hey guys,

I have to use WindowsXP at work for 8 hrs+ a day, and it's driving me absolutely bug crazy. 

Does anyone know any good apps that can:

1. Allow me to 'pin' windows. Equivalent to Metacity's 'always on top' option?

2. Decent multiple workspace support? I've tried the WindowsXP powertool and it blows chunks. Using it is worse than not using it. I've seen apps out there there that promise this - but they're all shareware. If anyone knows an open source/freeware utility, I would be grateful. 

The software that comes with Nvidia's windows drivers can do all this - and more, but we don't have nVidia cards in these work machines.

---

### Post by arcanistherogue on 2006-04-09
I was about to say nvidia window utitlity, but I see you already know about that...

Well, I know you can install clearlooks, search for it on DeviantArt.  They have multiple ports and multiple themes.  Some screenshots I can't tell the difference from GNOME or Windows.

---

### Post by Stormy Eyes on 2006-04-09
Making Windows act like GNOME requires that Microsoft make a Windows that doesn't suck. You're screwed.

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=Stormy Eyes]Making Windows act like GNOME requires that Microsoft make a Windows that doesn't suck. You're screwed.[/QUOTE]
lol, you are 100 % correct. :D

---

### Post by drizek on 2006-04-09
Check out litestep and windowblinds.

It is far from being as good as gnome/kde, but its better  than the default windows shell. Im not sure your boss would want you installing stuff like this on your computer though.

---

### Post by potrick on 2006-04-09
I use bblean in my Virtual Windows Machine. It's a windows port of Black Box. Makes windows much more usable (includes pin and fast multiple desktop) and is pretty easy to setup.  Check it out:

[http://bb4win.sourceforge.net/bblean/](http://bb4win.sourceforge.net/bblean/)

---

### Post by Nequeo on 2006-04-10
bbLean looks pretty cool... Although somehow I doubt they'll let me rip out the shell. There's a highly customized desktop environment here. Logon scripts, macros up the wazoo, etc. A little freeware utility that lets me pin windows would be wonderful - but litestep etc. are unfortunately out of the question.

Oh well... Thanks for the suggestions though.

---

### Post by PapaWiskas on 2006-04-10
[QUOTE=Stormy Eyes]Making Windows act like GNOME requires that Microsoft make a Windows that doesn't suck. You're screwed.[/QUOTE]


I am highly upset with you Stormy.  I just blew freakin Mt. Dew out of my nose when I read your comment.:evil: :mrgreen:

---

### Post by wmcbrine on 2006-04-10
[QUOTE=Nequeo]1. Allow me to 'pin' windows. Equivalent to Metacity's 'always on top' option?[/quote]I don't know how you'd do it, but I know it's possible -- the Task Manager does it.

---

### Post by Nequeo on 2006-04-10
[QUOTE=wmcbrine]I don't know how you'd do it, but I know it's possible -- the Task Manager does it.[/QUOTE]

I used to troubleshoot Windows clients from a Linux box...

Now I troubleshoot Windows clients from a Windows box, and I'm about ready to  pin those windows by sticking a thumb tack right through the screen.

My father always use to mouth off about how 'unusable' the Windows interface was. Something I never fully appreciated until switching over completely to Linux for a year, and then being forced back. 

The sad thing is that at home, where I can run any OS I want - I never even use windows pinning. But here at work where I need six programs to troubleshoot one PC, and three to handle incoming calls, and two more to log in service calls - not to mention Office, Outlook and Communicator... I'm simply going insane.

---

### Post by rejser on 2006-04-10
you could get kde for win, but that ain't gnome.
Can't you use a live cd?

---

### Post by Nequeo on 2006-04-10
Actually, I started downloading KDE for Cygwin - but while reading about it developed doubts that it would run the native windows apps I currently need. 

Unfortunately a liveCD is out of the question. My company's network relies on a Windows AD domain, ISA servers, and a whole host of interally developed Windows Only applications. 

I did get an Ubuntu laptop talking to the Internet at least - but the result after two days was 8GB of Ntlmaps logs in my root directory. :)

---

### Post by ice60 on 2006-04-10
[http://users.forthnet.gr/pat/efotinis/programs/deskpins.html](http://users.forthnet.gr/pat/efotinis/programs/deskpins.html)

there is a freeware multiple workspace tool too, not the powertools one but something else. i'll have a look for it.

---

### Post by Nequeo on 2006-04-10
You. Are. My. Hero.

I cannot express how much angst and frustration that one little link has saved me. I dedicate this smiley to your ancestors. :-D 

And may the Force be with you always.

---

### Post by ice60 on 2006-04-10
yeah, i totally rock :mrgreen: 

i didn't like virtuawin, if it's the program i'm thinking about, but i don't use virtual desktops :rolleyes: 
[http://virtuawin.sourceforge.net/](http://virtuawin.sourceforge.net/)

---

### Post by Nequeo on 2006-04-10
[QUOTE=ice60]yeah, i totally rock :mrgreen: 

i didn't like virtuawin, if it's the program i'm thinking about, but i don't use virtual desktops :rolleyes: 
[http://virtuawin.sourceforge.net/](http://virtuawin.sourceforge.net/)[/QUOTE]

Brutal. I'll give it a shot. The windows Power Tool had no way of sending programs from one desktop to another. It *could* be done, but only by telling it to show every program on every desktop, switching to the desktop you wanted to place the program on, minimising everything *except* the programs you want on that desktop, and then unticking the 'show programs on all desktops' switch again.

Yech. Plus - if for whatever reason the program decided to grab focus, it would pop back onto your current desktop, and you had to go through the whole darn process all over. 

Blarg!

---

### Post by darkmatter on 2006-04-10
If you're feeling lazy, you can always install Litestep and grab [GNOME for Litestep](http://www.deviantart.com/deviation/28988222/) ;)

---

### Post by ice60 on 2006-04-10
well, i hope you find it useful :) 

BTW here's a really great link. it's lots of DOS programs which act the same as *nix commands. just put them in Windows\system32

[http://www.infonomicon.org/text/cmd_linux.txt](http://www.infonomicon.org/text/cmd_linux.txt)

i really like this bit from the link.
```
Something that I love from the *nix world is tab completion. CMD.EXE has that 
although its not always enabled. This is very easy to change. Type 'regedit' 
in CMD.EXE and it will open up the registry editor. Then go to:

HKEY_LOCAL_MACHINE> SOFTWARE> Microsoft> Command Processor> CompletionChar
and
HKEY_LOCAL_MACHINE> SOFTWARE> Microsoft> Command Processor> PathCompletionChar

Then change these values to 9 with the hexidecimal radio button selected. When
you click ok, the next time you open CMD.EXE you will have tab completion.
```

---

### Post by Nequeo on 2006-04-10
I dun believe it - but the Cisco Agent Desktop program I so desperately wanted to pin is designed to minimize itself every time you hang up the phone... I never noticed it before under all the desktop clutter. 

But it kind of defeats the purpose of pinning it in the first place. 

So. Perhaps I will simply heave a great big sigh, retreat into a dark place deep within my soul, and hibernate until such time as I can tell Microsoft to bend over for a change.

---

### Post by Wallakoala on 2006-04-10
If you go to deviantart.com and do a search quite a few things come up. I found a theme that makes windows have a clearlooks theme, and it even replaces the start menu with an ubuntu symbol! I also found some scripts that replace the default icon set with a gnome icon set. Now my windows looks a lot nicer than before!

Btw I don't usually use windows, it's just that whenever I go into windows to play oblivion I don't want to see ugliness.

---

### Post by egon spengler on 2006-04-11
[QUOTE=drizek]Check out litestep and windowblinds.

It is far from being as good as gnome/kde[/QUOTE]

As far as a window manager litestep is FAR better than gnome/kde. As that link showed litestep can look identical to gnome, gnome can't do what litestep can though.


I guess it's somewhat academic now but [shell enhancer](http://www.nuonsoft.net/shellenhancer/features.php) allows you to pin windows among many other things

---

