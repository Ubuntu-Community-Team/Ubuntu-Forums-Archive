---
title: "Does this sound like good little project to do?"
date: 2010-06-10
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-06-10
I want to make a pack of a bunch of shortcuts/launchers to do various tasks that you would do with the terminal. It's to help people transitioning over to linux and absolutely fear the terminal. In a way it'll help me learn more terminal commands, and it gives me something else to do to get to play around with GIMP more to create icons. I'll label them by their function and describe what they do in the most simplistic way.

---

### Post by ubunterooster on 2010-06-10
I'm actually making one for my sis to have one-click updates: ```
gksu apt-get update
```

---

### Post by Legendary_Bibo on 2010-06-10
Ah yes, I guess I should ask the community for several useful terminal commands and what they do. I'll admit this won't be the most convenient method of doing something but it'll make it easier for new users. It'll be like a one stop shop of a lot of help rather than googling a lot.

---

### Post by ubunterooster on 2010-06-10
Oh, and remember everyone; here replace sudo with gksu

---

### Post by Legendary_Bibo on 2010-06-10
How do you add PPAs with the terminal?

---

### Post by ubunterooster on 2010-06-10
not sure (I forgot Something [cries] :( )

---

### Post by Legendary_Bibo on 2010-06-10
Well I'm going to have a glossary...maybe. I might just make "Installers" for the the programs which is just where I have them run wget whatever or and then another launcher to run them. I'll have to make other launchers to add PPAs first and then have the installers.

---

### Post by Cuddles McKitten on 2010-06-10
echo "http://hoochiemomma.com karmic whatever goes here I forget" >> /etc/apt/sources.list

---

### Post by Legendary_Bibo on 2010-06-10
This is going to be bigger than I thought. Oh well. I would really like to make it where some of these commands don't even open up the terminal, but that would probably require making GUIs which is too much of a hassle.

---

### Post by Legendary_Bibo on 2010-06-11
Does this look right? It's to add the Opera ppa. When I tried it, it just closed my terminal, but I already have it installed.
```

sudo add-apt-repository http://deb.opera.com/opera/ lenny

```

---

### Post by uRock on 2010-06-11
Here are a couple of the ones I use regularly. The snort fix one is to restart snort after suspending. Without restarting snort a CPU will get maxed out. The Nautilus one is obvious. I had more, but as I deleted them as I realized they were of no real use to me.

---

### Post by earthpigg on 2010-06-11
gnome-terminal -e htop

instead of using the resource-hogging panel app.

---

### Post by uRock on 2010-06-11
> **earthpigg said:**
> gnome-terminal -e htop

instead of using the resource-hogging panel app.

That's a good one which I hadn't thought of. I do prefer to run it as sudo so I can kill root processes when needed.

---

### Post by juancarlospaco on 2010-06-11
**Thats already done.**

Dont reinvent the whell and help [APT-Icons]("http://apticon.wordpress.com/")

---

### Post by Legendary_Bibo on 2010-06-11
> **juancarlospaco said:**
> **Thats already done.**

Dont reinvent the whell and help [APT-Icons]("http://apticon.wordpress.com/")
I don't understand spanish. And from what I could tell, it doesn't look like that's what they're doing.

I want to get a big list of commands first. I did a few, but I also want to know how to set up launchers to add PPAs

This might give you a better picture of what I'm doing.

---

### Post by del_diablo on 2010-06-11
I like using xterm -e "*command*
```
xterm -e 'sudo add-apt-repository http://deb.opera.com/opera/ lenny'
```

---

### Post by Legendary_Bibo on 2010-06-11
> **del_diablo said:**
> I like using xterm -e "*command*
```
xterm -e 'sudo add-apt-repository http://deb.opera.com/opera/ lenny'
```
what does the xterm -e part do?

---

### Post by earthpigg on 2010-06-11
> **Legendary_Bibo said:**
> what does the xterm -e part do?

starts a terminal session and immediately runs the command after -e. this way, if there is an error of some sort with the command/program, it will be displayed in a terminal instead of the icon simply mysteriously not working.

if the program runs fine, the terminal will automatically close. here, run this as an example:

```
xterm -e "sudo apt-get update"
```

and for comparison,

```
gnome-terminal -e "sudo apt-get update"
```

xterm is a bare-bones alternative to gnome-terminal - the big difference for us here is that virtually every distribution that includes a GUI also includes xterm.

gnome-terminal, on the other hand, is generally only included in gnome or gtk distributions. kubuntu, for example, almost certainly does not include gnome-terminal. a .desktop file that runs "xterm -e whatever" will work in xubuntu, lubuntu, kubuntu, etc. one that runs "gnome-terminal -e whatever" will only work in ubuntu.

so, as the *de facto* [benevolent dictator]("http://en.wikipedia.org/wiki/Benevolent_dictator#Open_Source_Usage") of this project, it is decision time for you: do you want this project to be for *buntu, or Ubuntu only?

if you use "gksu" anywhere, you are already limiting it to gtk-only... things with gksu will work in lubuntu, xubuntu, ubuntu... but not kubuntu.

---

### Post by itcotbtoemik on 2010-06-11
>xterm is a bare-bones alternative to gnome-terminal 

not really - xterm implements far more control sequences,
and is more configurable.  gnome-terminal is targeted at
people who want something that fits with their desktop's
decor.

---

### Post by earthpigg on 2010-06-11
> **itcotbtoemik said:**
> >xterm is a bare-bones alternative to gnome-terminal 

not really - xterm implements far more control sequences,
and is more configurable.  gnome-terminal is targeted at
people who want something that fits with their desktop's
decor.

i stand corrected, sir.

---

### Post by juancarlospaco on 2010-06-11
apt-icons got a big list of commands, some of them are launchers to add PPAs and such.

---

### Post by itcotbtoemik on 2010-06-11
:p

---

### Post by Legendary_Bibo on 2010-06-11
> **earthpigg said:**
> starts a terminal session and immediately runs the command after -e. this way, if there is an error of some sort with the command/program, it will be displayed in a terminal instead of the icon simply mysteriously not working.

if the program runs fine, the terminal will automatically close. here, run this as an example:

```
xterm -e "sudo apt-get update"
```and for comparison,

```
gnome-terminal -e "sudo apt-get update"
```xterm is a bare-bones alternative to gnome-terminal - the big difference for us here is that virtually every distribution that includes a GUI also includes xterm.

gnome-terminal, on the other hand, is generally only included in gnome or gtk distributions. kubuntu, for example, almost certainly does not include gnome-terminal. a .desktop file that runs "xterm -e whatever" will work in xubuntu, lubuntu, kubuntu, etc. one that runs "gnome-terminal -e whatever" will only work in ubuntu.

so, as the *de facto* [benevolent dictator]("http://en.wikipedia.org/wiki/Benevolent_dictator#Open_Source_Usage") of this project, it is decision time for you: do you want this project to be for *buntu, or Ubuntu only?

if you use "gksu" anywhere, you are already limiting it to gtk-only... things with gksu will work in lubuntu, xubuntu, ubuntu... but not kubuntu.

I'll use xterm for things that'll need it :D
All the Ubuntu distros come with Synaptic right?
I'm going to call this project "Training Wheels" Which I plan on making it a dropdown menu next to the System menu. I hope it goes upstream. And because it's just a dropdown menu that can be removed with a couple of clicks.
To juancarlospaco, I would help with your project, but it looks like you're making a whole new program like Ubuntu Tweak. I'm trying to make a menu integrated within the menu. I'm including ways on fixing common problems that usually involve entering commands into the terminal.

---

### Post by forrestcupp on 2010-06-11
This sounds like the beginnings of Automatix3. :-\"

---

### Post by Bachstelze on 2010-06-11
> **ubunterooster said:**
> I'm actually making one for my sis to have one-click updates: ```
gksu apt-get update
```

Update Manager, anyone?

> **forrestcupp said:**
> This sounds like the beginnings of Automatix3. :-\"

I lol'ed. That's really how it sounds, I had forgotten about Automatix.

---

### Post by Legendary_Bibo on 2010-06-11
> **forrestcupp said:**
> This sounds like the beginnings of Automatix3. :-\"
oh my no! It's just a menu bar with launchers for various terminal commands. It's not an actual program, it just uses what's already available. It's just tedious for someone to make, but it makes it easier on new users.

I LOVE DOING TEDIOUS THINGS!!! :D

It's using the terminal, without the terminal. To people who use the terminal it's slow, but to the new user it makes things more comfortable. Oh I made a launchpad thingy... If you guys want to help all I need is basically terminal commands for popular programs that you can't get through the Ubuntu software center, or the minimal Synaptic.
I'm looking for adding PPA's, installing the programs, typical system commands (i.e. top, htop, etc.), and commands for troubleshooting (i.e. compiz -replace, metacity -replace, sudo gedit '/usr/share/icons/default/index.theme' (for fixing mouse issue when compiz is on)).

[https://blueprints.launchpad.net/ubuntu/+spec/training-wheels](https://blueprints.launchpad.net/ubuntu/+spec/training-wheels)

---

### Post by Dustin2128 on 2010-06-11
well a few useful things to do with the terminal that could be added for me are
```
chmod +x binfileneedstobeexecuted.bin 
./binfile.bin
``` you need to use bin files to install google earth among other programs. Also: ```
tar xvzf tarpackage 
cd tarpackage, 
./configure
make && make install

```

---

### Post by forrestcupp on 2010-06-11
> **Legendary_Bibo said:**
> oh my no! It's just a menu bar with launchers for various terminal commands. It's not an actual program, it just uses what's already available. It's just tedious for someone to make, but it makes it easier on new users.

That's basically how Automatix started.

---

