---
title: "A little help with the launcher management logic on PP please?"
date: 2011-10-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-24
Can anyone teach me the logic for managing Launcher Items? It seems to be different in PP than in Oneiric.

I thought the launcher would display .desktop file placed in /usr/share/applications (Global/System Shortcuts, root:root, 644) and $HOME/.local/share/applications (Users Shortcuts, $USER:$USER, 644). I'm pretty sure I was copying, moving, removing, links the way I wanted to in Oneiric, but I can't in PP.

I have verified that manually moving .desktop files (via CLI) in and out of these two directories does not change the launcher anymore. The only way to put an item on launcher is to drag it from a nautilus windows and release it over the launcher, as now advised everywhere.

Ok, you do it, but then when you go look at /usr/share/applications, surprise: your .desktop file is there...yey. So why can't I just move it normally via cli (no mouse)?

What else is being updated when I drag and release a .desktop over the launcher? Something else must be involved, otherwise it makes no sense at all.

Thanks,
Effenberg

---

### Post by mc4man on 2011-10-24
Don't see any change here, atm PP & OO are using the same unity/compiz

Do you mean launcher or dash?

No .desktop's  are 'auto' added to the launcher though if the same name .desktop's are in ~/.local .. or /usr/local/... they will trump those that are /usr/.. automatically & will reflect any mods. 

Ex. 
I was just now setting up PP & changing the launcher icons a bit from the defaults.
I copied all my custom .desktops to ~/.local/share/local/applications.

After a log out/in any of the same name ones that were already in the launcher where automatically changed to the ones in ~/.local/.., in this case the home-folder & terminal

Any other ones will have to be added, either thru D&D or gsettings/dconf-editor (gsettings is the easier of the 2) - Ex here are the 2 below Firefox - Utilities & Multimedia which I D&D from ~/..

If you mean the Dash - any .desktop that is properly constructed should show up, even custom ones

---

### Post by seeker5528 on 2011-10-24
> **effenberg0x0 said:**
> Can anyone teach me the logic for managing Launcher Items? It seems to be different in PP than in Oneiric.

When you say 'the launcher' do you actually mean the laucher or do you mean 'More Apps' AKA the application lens in the dash?

I was not aware of any technique that would allow placement of applications on the launcher without running the application and pinning it to the launcher or locating/creating the .desktop file and dragging it to the launcher.

Seems to be some discrepancy in the available information on whether the .desktop file needs to be in '~/.local/share/applications' or relevant system wide location or whether you can drag the .desktop file to the launcher from any directory.

Whether the applications will reliably show up in the applications lens over the long haul if there is no 'catergories' line might also be a question.

[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

Later, Seeker

---

### Post by mc4man on 2011-10-24
> 
Seems to be some discrepancy in the available information on whether the .desktop file needs to be in '~/.local/share/applications' or relevant system wide location or whether you can drag the .desktop file to the launcher from any directory.
A .desktop can be added from anywhere - the only caveat is that **after adding** it's location can't be changed
Any installed app's .desktop should show up even if not in a typical applications folder, ex. google-chrome (/opt

gsettings will show that nicely, installed .desktops in the launcher are just .desktop name, added custom or copied .desktops will have path
```
gsettings get com.canonical.Unity.Launcher favorites
```


One can use gsettings set to add or remove launchers though it's a bit more suited to restore a list
```
gsettings set com.canonical.Unity.Launcher favorites "[list of desktops in top to bottom order here]"
```
When using the set command any .desktop added that was either installed or in an typical applications directory can just be done with <name>.desktop.
gsettings will add path as need be
(the 'pecking' order for applications dir.'s is typical - ~/ : /usr/local : /usr

> Whether the applications will reliably show up in the applications lens over the long haul if there is no 'catergories' line might also be a question.

Definitely should be done for custom .desktops if you want them to show thru the filter,  an installed .desktop's line can be adjusted to suit if desired

Edit:
for custom .desktops added  to launcher,  if the drag filetype to launcher feature would be useful then a Mimetypes= line is needed

---

### Post by effenberg0x0 on 2011-10-24
I'm sorry, I wasn't clear enough. The language can be a barrier when I type too fast. Very bad day here. But its solved now, mc4man explanations nailed it.

> **seeker5528 said:**
> 
I was not aware of any technique that would allow placement of  applications on the launcher without running the application and pinning  it to the launcher or locating/creating the .desktop file and dragging  it to the launcher.
Well, that makes no sense. In some level we are just talking about files  being placed somewhere in the system and/or settings placed in a gconf  like structure, etc. There must be non gui methods for just about  anything one can do visually. Otherwise remotely managing a large amount  of machines would be impossible (one wouldn't be able to run remote  scripts over a large installed base). No visual feature / setting can not be specifically depending on files;files content, otherwise, where / how would they be stored?

> **seeker5528 said:**
> When you say 'the launcher' do you actually  mean the laucher or do you mean 'More Apps' AKA the application lens in  the dash?
I mean the launcher as in what we are supposed to call the launcher lol
[http://design.canonical.com/2010/06/introduction-to-unity-launcher/](http://design.canonical.com/2010/06/introduction-to-unity-launcher/)

> **mc4man said:**
> 
Do you mean launcher or dash?
I don't know what either is. I'm new to Linux. That colorful bar with fun symbols :P How can I run dreamweaver and my favorite game inside Grub?

Now seriously:
> **mc4man said:**
> A .desktop can be added from anywhere - the only caveat is that **after adding** it's location can't be changed

> **mc4man said:**
> 
```
gsettings get com.canonical.Unity.Launcher favorites
```

> **mc4man said:**
> 
for custom .desktops added  to launcher,  if the drag filetype to launcher feature would be useful then a Mimetypes= line is needed

> **mc4man said:**
> 
No .desktop's  are 'auto' added to the launcher though if the same name .desktop's are in ~/.local .. or /usr/local/... they will trump those that are /usr/.. automatically & will reflect any mods. 

These 4 advices made me realize the internal structure of the thing, all fixed now. 

Thanks,
Effenberg

---

