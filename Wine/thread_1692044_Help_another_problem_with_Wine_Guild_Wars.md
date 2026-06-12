---
title: "Help another problem with Wine: Guild Wars"
date: 2011-02-20
forum: Wine
---

### Post by Mao Brutus on 2011-02-20
I'd appreciate any help I could get on installing and running Guild Wars through Ubuntu 10.10 32 bit. However my specific problem is: Not even being able to start Guild Wars.

NOTE: I'm following the guide on:

[http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)

Bring up to speed how the guide runs(things that I followed at least):

wget [http://www.guildwars.com/downloads/gwsetup.zip](http://www.guildwars.com/downloads/gwsetup.zip)

unzip gwsetup.zip

wine GwSetup.exe /complete

...Then click install, blah blah, the data loads to the C:\ through Wine, takes about 15 minutes to load, all that.

This has worked out half decently so far, its simple. Whenever I go through the Applications > Wine > Programs > Guild Wars, to run the program, nothing happens. I've been restarting my system after every attempt so I haven't been duplicating processes. 

It was working using:

wine "C:\Program Files\Guild Wars\Gw.exe"

[FONT=Verdana]...and now has suddenly stopped again, and Terminal has been posting:[/FONT]

*** glibc detected *** C:\Program Files\Guild Wars\Gw.exe: corrupted double-linked list: 0x7cdadc40 ***

[LEFT][FONT=Verdana]I've reinstalled Guild Wars, I've reinstalled Wine(As best as I know how), and I still get this message 9/10 attempts.[/FONT]

Keep in mind:
-I'm fairly new to Ubuntu(still learning).
-Provide as many details in, if, you post a possible solution.

[FONT=Verdana] If anyone could shed some light on this I would be massively in debt to you, and you would have my millions of thanks.[/FONT]


[/LEFT]

---

### Post by Mao Brutus on 2011-02-20
**Another, NOTE:**
 -I'm only using Ubuntu as my OS, no dual-boots with Windows or any other OS. That being said things like "try to reboot with windows and mess with full screen options, graphics, etc" is out of the question, as I've seen others post in problems with Guild Wars loading.

_**"Things to include when asking for Help" -(Sticky):**_

***Wine and Ubuntu version - ***Wine 1.2 Package ("Stable Version"), Ubuntu 10.10
***Terminal output - ***Yes, I have as posted.
***Wine configuration - ***Everything is default, except the 4 Options under 'Graphics(Windows Settings)' which I have un-selected all 4, which I have had the most luck with. (9/10 times). 
***Hardware specs/drivers - ***VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1). All stock drivers, except my Sound card which is: Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0).
***Other Wine applications*** - None. No winetricks or PlayOnLinux.

---

### Post by Mao Brutus on 2011-02-21
Problem self-solved, completely uninstall Wine, then without using the website download link I did everything through Terminal. Therefore I did not install Wine through the main website directly and only used Terminal following the recommended updates etc. 
sudo apt-get install wine
<Enter your password>

---

