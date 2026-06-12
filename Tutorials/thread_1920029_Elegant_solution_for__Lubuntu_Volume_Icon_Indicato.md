---
title: "Elegant solution for  Lubuntu Volume Icon Indicator lxpanel applet not working"
date: 2012-02-04
forum: Tutorials
---

### Post by ronniew on 2012-02-04
I have recently become a huge Lubuntu fan... I work with a ton of old hardware and regularly setup machines with lubuntu... 

One of the ongoing problems seems to be the volume control in the lxpanel, sometimes it works, sometimes it doesn't, sometimes it stops working... 

I've found installing different packages and using different programs can sometimes tie your volume control to something besides Master. Currently the default sound control provides no way of adjusting settings or accessing a mixer.

I went searching for a solution. To my surprise many things either didn't want to build correctly or if the installation was successful didn't really work or used a ton of memory. Some solutions want to install entirely different sound system to the os. Defeats the purpose of Lubuntu.

I successfully tested pnmixer and voiti. To my surprise voiti was using 30mb just to run volume and mixer... good grief!    Pnmixer used 15mb still terrible and sometimes hung up.

i then installed alsamixergui which is a sweet lil light mixer program for alsa.... i first toyed with and tested adding a new application launch bar to the lxpanel and then added alsamixergui to it..

This solution worked but wasn't very elegant or what we want or expect from volume control... but it did work so I kept the idea as a last resort option. Especially if I run into really troublesome machines.... but I kept looking...

I tried installing volwheel but it wanted to install 24 extra packages,, all kinds of sound stuff and extra libraries. I noticed this was the 2.8 version and it was fairly new and thought lets try an older version.. I tried the next one down. Version 2.6

Perfect volwheel 2.6 needed no extra dependencies,,, at least on my existing system.... I installed it,,, launched it and boom ok volume control again...

Took a look at memory consumption... and it was 1.2mb, SWEEEEEET!  Took a look around right clicked to enter preferences and I noticed I could pick the command for my own mixer.... AWESOME.. 

Since I already installed alsamixergui  I decided to add that command to the preferences mixer box, then noticed that I could also change the default channel.... VERY SWEET,,, I took a look at alsamixergui found which one controlled my volume then entered the exact name in the preferences box asking for default channel.. In this case PCM, i also took a look at the different types of icons for volume control then clicked save.

I noticed it did not put an autostart entry to startup automatically so I created my own... pretty easy just make a .desktop icon file to point to volwheel, in your /home/*YOURUSERNAME*/.config/autostart  directory/folder. (must show hidden files to see it) 

HINT open other files using leafpad as examples then create your own .desktop icon based on the simplest example you can find. Make sure it runs the volwheel command.  Then run lxsession-edit and tick your new entry for startup.

Ex
[http://pastebin.com/Ev1pYQhA]("http://pastebin.com/Ev1pYQhA")

Works perfect.. if you ask me this sould become the default for lubuntu or lxde.. you get a working volume icon that you can control complete with a mixer and different icons to pick from. Scroll volume also works and uses very little memory.

Now remove the default volume control icon by right clicking on the panel somewhere where the menu says add/remove panel items,,, find volume control in the list and remove.

DONE!

You can download the VolWheel 2.6 version deb file from

[HERE]("https://launchpad.net/~neosofti/+archive/ppa/+build/1796929/+files/volwheel_0.2.6%7Eppa1%7Elucid1_all.deb")

*alsamixergui can be install using synaptic or lubuntu software center or sudo apt-get install alsamixergui from the terminal

Hope it works for you like it has me. This ongoing problem is now SOLVED in my playbook.

[http://picpaste.com/volwheeliconcontrol-rWUAkMX2.png]("http://picpaste.com/volwheeliconcontrol-rWUAkMX2.png")

[http://picpaste.com/preferencesandmixer-Xo4Jc6gO.png]("http://picpaste.com/preferencesandmixer-Xo4Jc6gO.png")


P.S.

If you like this solution, share a sweet Lubuntu or LXDE trick or cool light program / solution! Would luv to hear it and learn it.

---

### Post by Rodney9 on 2012-02-04
The LXPanel Volume Control works well for me on my laptop and desktop.
I like the way the mouse wheel works with it and the multimedia keyboard  controls.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ronniew on 2012-02-04
I don't understand,,, if lxpanel volume works well for you why are you reading this post and replying... looks like your here just to promote some other post.

sheesh you can't even post things in the forum anymore without someone advertising something else.

good grief was simply providing a solution to an ongoing problem that I experience with Lubuntu. Hopefully some will find it useful.

---

### Post by Jiraya_90 on 2012-06-19
thanks @ronniew for the hint ;)

---

