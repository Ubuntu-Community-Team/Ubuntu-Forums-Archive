---
title: "Conky config RSS"
date: 2012-05-29
forum: The Cafe
---

### Post by curiousx on 2012-05-29
[FONT="Comic Sans MS"][COLOR="Teal"][CENTER][SIZE="4"]Sharing mah conky config[/SIZE][/CENTER][/COLOR][/FONT]

[FONT="Comic Sans MS"]Aloha all this is mah first post maybe this is not the place to post stuff related to conky but anyway the idea is that someone can use it if you like [/FONT] :P

[FONT="Comic Sans MS"]Ok, it's is based in conky lunatico [COLOR="red"][http://goo.gl/oZlyw]("http://goo.gl/oZlyw")[/COLOR] but i add some features like incoming mail from Gmail, Yahoo or Hotmail, and i add an RSS feed at left side.[/FONT]

example: [IMG]http://i.imgur.com/LUHZv.jpg[/IMG]

[FONT="Comic Sans MS"]So, let go to the point [/FONT]

[FONT="Comic Sans MS"][COLOR="Red"]Dependences:[/COLOR][/FONT]```
sudo add-apt-repository ppa:conky-companions/ppa ; sudo apt-get update ; sudo apt-get install conky-all conkyemail conkykeyring
```
[FONT="Comic Sans MS"]More info about conky companions[/FONT][COLOR="Red"] **--->**[/COLOR] [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")

[FONT="Comic Sans MS"][COLOR="Red"]Setting up:[/COLOR][/FONT]

[FONT="Comic Sans MS"]Well... i'll paste mah three configurations files, and i tell what to do with that [/FONT] :D

[FONT="Comic Sans MS"][COLOR="Red"]File:[/COLOR] "conkyrc_lunatico"[/FONT] [http://paste.ubuntu.com/1012360/]("http://paste.ubuntu.com/1012360/") [COLOR="Red"]Note:[/COLOR] Change "USER", "MAIL" and "PASSWD" values in order to fetch the incoming mails

[FONT="Comic Sans MS"][COLOR="Red"]File:[/COLOR] "conky_lunatico.lua"[/FONT] [http://paste.ubuntu.com/1012612/]("http://paste.ubuntu.com/1012612/")

[FONT="Comic Sans MS"][COLOR="Red"]File:[/COLOR] "conkyrc_rss"[/FONT] [http://paste.ubuntu.com/1012603/]("http://paste.ubuntu.com/1012603/")

[FONT="Comic Sans MS"][COLOR="Red"]File:[/COLOR] "RSS scripts"[/FONT] [http://ubuntuone.com/6FpSBESJAa6tFcrlAZkfhC]("http://ubuntuone.com/6FpSBESJAa6tFcrlAZkfhC")

[FONT="Comic Sans MS"]Now, create a hidden folder in your $HOME called ".conky" and move the "conkyrc_lunatico" file and "conky_lunatico.lua" into it[/FONT]```
mkdir $HOME/.conky
```

[FONT="Comic Sans MS"]Then, create a hidden folder in your $HOME called ".conky_rss" and move the "conkyrc_rss" file into it[/FONT]```
mkdir $HOME/.conky_rss
```

[FONT="Comic Sans MS"]Finally, create a folder called "scripts" into the ".conky" folder and move all the RSS scripts into it[/FONT]```
mkdir $HOME/.conky/scripts
```

[FONT="Comic Sans MS"][COLOR="Red"]You are done!! :) [/COLOR]from here, you can start up conky calling the "conkyrc_lunatico" and "conkyrc_rss"[/FONT]```
conky -c $HOME/.conky/conkyrc_lunatico
``````
conky -c $HOME/.conky_rss/conkyrc_rss
```

[FONT="Comic Sans MS"][COLOR="Red"]Starting up conky automatically:[/COLOR][/FONT]

[FONT="Comic Sans MS"]So, if you wish, you can start up both conky automatically, making two smalls scripts and calling them using "Startup Applications"[/FONT]

[FONT="Comic Sans MS"][COLOR="Red"]Script One:[/COLOR] ".run_conky"[/FONT][ http://paste.ubuntu.com/1012657/]("http://paste.ubuntu.com/1012657/")

[FONT="Comic Sans MS"][COLOR="Red"]Script Two:[/COLOR] ".run_conky_rss"[/FONT] [http://paste.ubuntu.com/1012661/]("http://paste.ubuntu.com/1012661/")

[FONT="Comic Sans MS"]Once you have those script, run them with "Startup Applications" at boot, clicking on "add" button and completing the fills this way for ".conky_lunatico"[/FONT]: 

[IMG]http://i.imgur.com/FAop3.png[/IMG]

[FONT="Comic Sans MS"]and this way for ".conkyrc_rss"[/FONT]

[IMG]http://i.imgur.com/d0Og9.png[/IMG]

[FONT="Comic Sans MS"]Sorry for mah english i helped mah self using google translate :P have fun, hope it usefull, greetings lovely comunity [/FONT]

---

