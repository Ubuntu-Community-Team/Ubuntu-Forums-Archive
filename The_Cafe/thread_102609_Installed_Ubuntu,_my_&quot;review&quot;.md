---
title: "Installed Ubuntu, my &quot;review&quot;"
date: 2005-12-12
forum: The Cafe
---

### Post by anlari on 2005-12-12
Okay, I installed Ubuntu. I like the overall desktop and applications and such so I am going to concentrate on what I did *not* like. :p This is not a rant, nor a troll. Feel free to suggest alternatives and fixes. If you can, please improve these things in Ubuntu for all new users on the next versions. I tried to look at things as an "average Joe". Some things here are "upstream" problems but uhm.. Anyways.. Here it goes!

**Installation**

XFS & Grub installation failed, as suggested by the installer. How come? I have used XFS earlier with Grub on Gentoo, Fedora and Kubuntu. (I can't recall how I installed them but it worked in the end very well.) XFS would be nice because it in many cases performs better, especially with larger directories. (At least I can notice the difference in certain cases.)

It was quite positive that the installation detected my Server 2003 and added it automatically on the Grub menu. It is very good for the people who want to casually try Ubuntu out with dual booting. Otherwise the installer is asking all kinds of funny questions an ordinary user couldn't care less about or has no understanding about. I'd ask at the beginning wether to do a &#8220;for dummies&#8221; installation (which would be VERY for-dummies version) or a more &#8220;advanced one&#8221; and act accordingly.. Now it's a slightly funny mix.

**The looks**

The Grub works by default in plain vanilla text mode. Yuch. The bootsplash is ugly and before that there is some rude text about the kernel booting. I used to play some games when 8086 was hot and they had extremely advanced CGA graphics. The bootsplash reminds me of those games for some reason every time I see it. Brown blocky text? Woohoo. Even Windows 95 looked better :razz: 

I kind of like the GDM theme. It's neat. Also I like the default mouse pointer theme. It's simple and nice. The default brown look is a bit bad otherwise. The tan would fit nicer as someone pointed on the Wiki. But that isn't the bad part yet. The default gnome icon set looks 90s. There are many other icon sets available but usually they do not change all the icons in menus which is irritating. Getting a consistent modern and good looking icon set seems to be extremely hard task. It's work for hours and hours.

One of the best things KDE has got is their glassy new icon set. No, I don't like what it looks like. It's like those older Imacs and it looks somehow too candyish. It is however quite consistent and replaces pretty much everything. Something like that would be required on Ubuntu.

Furthermore mixing qt and gtk applications can look absolutely horrible. There should be some basic work done that brings them at least slightly closer, preferably get them to look 100% same. (I know it isn't easy task, but on the other hand qt-gtk way it seems to work quite well &#8211; getting gtk applications qt'ified...)

I managed to tweak (thanks to the Ubuntu forums) my Opera (which beats Firefox about 100-0) to look consistent enough for the Gnome desktop so I am happy :cool: 

I don't want &#8220;candy&#8221;. I want a stylish simple look. Simple the default look is but it's not very stylish. Perhaps it was that in -95 or so. Does the look matter? Well, I get a working software if I have to select between working and beautiful. But I'd really rather have working AND beautiful. 

People throw in screenshots of Vista when they talk about blingbling and start raving about the transparency and enabling composite on x.org. I have been looking at the Vista designs and the transparency is just one part of them. They just have been Designed. They are not perhaps finished and I don't like everything about them but it's a bit fresh yeah.

Quite honestly, if I was Canonical I would throw in some real money to get real designers to make up one simple but good looking consistent theme for all the aspects of the default desktop and booting process. Nerds don't have graphic skills, really. It hurts my eyes. It's inconsistent and plain amateurish all the way. 

**Default applications**

The &#8220;add applications&#8221; on Gnome menu is a great idea. Users want to get one good software for certain task without getting deep under the hood. That's simple and works very well. I don't agree here with some of the offered applications. Because the mix kde/qt and gnome/gtk stuff. They can look very inconsistent and they pull in &#8220;a few&#8221; extra libraries. Please, try to stay on either side always when there's a chance.

Also the added menu editor is a good one. Lack of it on default Gnome is a horrible mistake by that project. 

Automated updating tool is superb. Thanks for that. Also the synaptic otherwise is good when/if you need more power than what the easy &#8220;add applications&#8221; offers.

The PDF Cups printer driver would be a great addon. I don't have a printer myself but make documents and such for others to read. Using Linux and they Windows usually PDF is the safe bet. It's also a safe bet to print at work etc from the PDF instead of trying to get other file formats work. (No, OOo isn't the only application I use.) I didn't find easy way to add it myself either. 

I installed Beagle via apt. Not having used it before I wanted to give it a try. Yes, it works. What I am bugged about is that such tool should integrate with the desktop seamlessly. Meaning a search window applet on the Gnome panel. You know, you could either launch Google (or whatever) search from it on a new browser or Beagle search or whatever. It could be very convenient but I couldn't find a way to get such thing working.

Gnome doesn't support any easy way on how to change the looks of GDM and the Gnome splash? Or then it isn't just on the menus or I just can't find it for some weird reason. All that stuff is still way too hard :-( (But you HAVE to do it or it'll all blow your eyes off.)

I tried Planner when it was an earlier version. Whoa. That's sweet. Evolution is aok too though I have got one personal gripe with it. 

(I can't use my national electronic ID card to sign&encrypt email. It just isn't possible because Evolution doesn't use the opensc-pkcs11 and the next generation PGP will be really working earliest somewhere around 2050 it seems. I can use Mozilla Thunderbird for email though if I need the feature. The same goes for Firefox, I need Mozilla to be able to get into the official governmental services with the card.) 

Ooh, some more administration tools too. Guisguisguis. Good. More, for every task. Setting up a samba share (if it really worked, I got no Windows here to test with) was pleasant. 

**Hardware support**

The only piece of  hardware just didn't just start working was my webcam. Labtec Webcam Pro. I've used it earlier on Gentoo and Fedora, with self compiled drivers from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) . The ones that are on default Ubuntu installation cause a hard lock of kernel when I try to use the webcam. Oof.

**Sound stuff**

It would be nice if by default all the applications could play the sounds simultaneously so that no application could block others. Read some howtos and since esd is buggy old software (which is being replaced, I heard rumor that Cox is going to take a look on it for Fedora project) and with alsa it might have weird side effects it's not hard. I'd like to be able to set default alsa (not all applications are Gnome/esd aware) device via some gui and optionally try to enable the software mixing so that all the applications could try to use it at the same time. 

**CD Burning & medias**

I can find the CD burning from Nautilus menus. More intuitive way to start burning couple files for average users would be via right click context menu. That feature doesn't exist it seems. I have seen some chatter about including K3b/gnomebaker/whatever. All those applications are good examples of how one should never implement such application for an average user. They do not want to use applications. They have a problem, they want a task accomplished. &#8220;I have this file, I want it on CD&#8221;. Asking for stuff like all kinds of settings and showing a GUI that has enough buttons and menus to fly a shuttle is definitely murderous for usability. If someone ASKS at that stage to get a more powerful solution it should be possible (for the ~1% of the burning cases, or the nerds) but for default user it should be as straightforward as automatic as ever possible.

I plugged in my USB memory stick and a new icon appeared on desktop. I got to use it instantly very well. Good.

**Non-free stuff**

What did I have to add manually? Well, Sun's Java stuff with Netbeans. That installation is quite smooth and simple. Umm, flash from multiverse. Acroread. (Though I think evince would work just fine?) Then some codecs. The eternal and slowly worsening thing about patents and such.. But anyways, wether you like or don't like that laws - they are here. And libdecss (or whatever) **is** afaik illegal to use on Linux around where I live.

I would pay for legal working DVD player on Linux if someone would sell. I got my music as OGGs and I rarely watch fun video clips (yes, it's fun but I'm glad sparing my time, hehe) and I don't pirate movies... So all I am missing really is the DVD player. So yeah, since no one seems to be offering I took the cough hinted route for getting it to work. 

When I heard about Cyberlink making a Linux version I was thrilled. But they made it only for embedded stuff and not for consumer sales. I would have bought their stuff for DVD playing because their player has at least on Windows platform been just superb. 

**Other**

I selected as living in Europe/Finland when I installed Ubuntu. Why is my Gnome panel clock applet using 12 hour format by default? We use 24 hour format. (Yes, it took only ~5 seconds for me to &#8220;fix&#8221;.)

The complete lack of a good diagram drawing program on Linux. Dia and Kivio are the only ones but both of them draw so ugly widgets (they are pure 70s, man) that if you draw something with it and go to a meeting or such with your diagram guess what happens? Everyone laughs at you. Also the arrows/lines between the widgets act quite bad on those applications. One wouldn't need much. Just a few simplish SVG widgets and an arrow/line system between them. But it doesn't seem to exist in usable working and non-dog-ugly form. (I rather pay for the Visio, which then again just plain can rule if you know how to tickle it.)

---

### Post by stuporglue on 2005-12-12
> 
The complete lack of a good diagram drawing program on Linux. Dia and Kivio are the only ones...

Check out Inkscape, possibly a development version. It's getting connectors between shapes. It's not Visio level yet, but it's still very nice.

---

### Post by anlari on 2005-12-12
[QUOTE=stuporglue]Check out Inkscape, possibly a development version. It's getting connectors between shapes. It's not Visio level yet, but it's still very nice.[/QUOTE]

It kind of works. I made one organizational chart with it... But it isn't really originally meant for that task and it feels :???:

---

### Post by Knomefan on 2005-12-12
> I installed Beagle via apt. Not having used it before I wanted to give it a try. Yes, it works. What I am bugged about is that such tool should integrate with the desktop seamlessly. Meaning a search window applet on the Gnome panel. You know, you could either launch Google (or whatever) search from it on a new browser or Beagle search or whatever. It could be very convenient but I couldn't find a way to get such thing working.

Check out deskbar applet.
[http://gnomefiles.org/app.php?soft_id=780](http://gnomefiles.org/app.php?soft_id=780)
It does exactly what you are looking for and it is in backport iirc.

Also, today beagle integration in nautilus has been commited in cvs and will be in the next gnome release.

---

### Post by anlari on 2005-12-12
[QUOTE=Knomefan]Check out deskbar applet. Also, today beagle integration in nautilus has been commited in cvs and will be in the next gnome release.[/QUOTE]

Woot *2! :cool: This is THE stuff.

---

### Post by gil-galad on 2005-12-12
> Furthermore mixing qt and gtk applications can look absolutely horrible. There should be some basic work done that brings them at least slightly closer, preferably get them to look 100% same. (I know it isn't easy task, but on the other hand qt-gtk way it seems to work quite well &#8211; getting gtk applications qt'ified...)

Well, ubuntu only comes with GTK apps, so its consistent as far as that is concerned.  While I agree that it would be a nice idea, it is better to just stick with GTK or gnome apps, as I do.    

> Quite honestly, if I was Canonical I would throw in some real money to get real designers to make up one simple but good looking consistent theme for all the aspects of the default desktop and booting process.

What are you talking about?  They have thrown some real money at it and it **does** look consistent.  Whether or not you like it is another story, but it **is** consistent.  Its not my favorite theme in the world, but its a good default and unique.  

> Also the added menu editor is a good one. Lack of it on default Gnome is a horrible mistake by that project. 

Gnome does include a menu editor now, just so you know.  It was a mistake in 2.10, however.

> The default gnome icon set looks 90s. There are many other icon sets available but usually they do not change all the icons in menus which is irritating. Getting a consistent modern and good looking icon set seems to be extremely hard task. It's work for hours and hours.

Seems to me that the icons are pretty good, much better than the windows ones at least, but I realize it is subjective.  Do you have any actual complaints about the icons? And changing the icons takes about 10 seconds with the Gnome theme tool.

> I have seen some chatter about including K3b/gnomebaker/whatever. All those applications are good examples of how one should never implement such application for an average user. They do not want to use applications. They have a problem, they want a task accomplished. &#8220;I have this file, I want it on CD&#8221;.

I completely agree, and not just for average users.  I love the nautilus burner.  When I put a blank cd in the cd folder pops up and I simply drag files to it.  Burning an iso is as simply as right clicking it.  Much better than any burning program.

---

### Post by anlari on 2005-12-12
I just happen to like good looking stuff. It doesn't mean heavy nor über-BLINGBLING. Just elegant simple stylish modern stuff. For instance this theme Tango, which unfortunately is very far from complete :(

[QUOTE=gil-galad]Well, ubuntu only comes with GTK apps, so its consistent as far as that is concerned.  While I agree that it would be a nice idea, it is better to just stick with GTK or gnome apps, as I do.[/QUOTE]

That's what I'll try. Not everything exists for GTK though :(

[QUOTE=gil-galad]
What are you talking about?  They have thrown some real money at it and it **does** look consistent.  Whether or not you like it is another story, but it **is** consistent.  Its not my favorite theme in the world, but its a good default and unique.  [/QUOTE]

As far as I can see most of the icons are stock Gnome icons in the menus and they look at best embarrassing. Not money used there. There are red ones, there are blue ones, there are round ones, there are... Ah. The only good one perhaps is the ubuntu starter icon :D (Which is not stock Gnome)

And they are not consistent with the background which is brown (far from the Gnome default background) nor with the mouse pointers (which are damn fine pieces of art). 

[QUOTE=gil-galad]Seems to me that the icons are pretty good, much better than the windows ones at least, but I realize it is subjective.  Do you have any actual complaints about the icons? And changing the icons takes about 10 seconds with the Gnome theme tool.[/QUOTE]

They are blocky, have too varying schemes and look just simply non-modern. They are not stylish or elegant in any way. More like children's drawings. They look like using an os from earlier 90s. Compare with some others to see what I mean *cough* 

It takes MORE than 10 seconds to change them with the Gnome theme tool. More like 10 hours since most of the good looking themes are incomplete (don't replace every one to be consistent) and it's a great amount of work trying to find and set up individually all the bad looking icons to good looking versions. Which is not Ubuntu's fault naturally but bugs me majorly. 

[QUOTE=gil-galad]I completely agree, and not just for average users.  I love the nautilus burner.  When I put a blank cd in the cd folder pops up and I simply drag files to it.  Burning an iso is as simply as right clicking it.  Much better than any burning program.[/QUOTE]

It is. I would just like to see that one more intuitive way to start it up via right click context menu. (Not perhaps for myself but it's what many people most likely try, especially after having done the same with positive results on other platforms.)

---

### Post by gil-galad on 2005-12-12
Good reply.  I still say that the icons are not hard to change.  Simply go to [http://art.gnome.org/](http://art.gnome.org/) and look at their icon themes.  You can install them by simply dragging the download link onto the install button in the themes folder.    Ubuntu even comes with several icon themes.  Try human if you want some different looking icons.  I fail to see how the icon theme is not consistent, unless you have installed extra applications that have their own icon.  Do you want every icon the same color?  That makes no sense.  And what are you comparing it to?  What OS has consistent icons for all the applications?  Gnome actually has the most consistant icons I have seen.

The same person that made the mouse pointer made the Gnome icon theme, and he is very consistent.  [http://jimmac.musichall.cz/icons.php](http://jimmac.musichall.cz/icons.php)         

One more thing, the gnome print tool **does** allow you to print to PDF.  It is a very handy feature.

> 
It is. I would just like to see that one more intuitive way to start it up via right click context menu. (Not perhaps for myself but it's what many people most likely try, especially after having done the same with positive results on other platforms.)

I am not sure.  You don't want those right clicks to become too cluttered.  Are you supposed to randomly right click on a file and expect a cd burning option?  Right clicking on an iso image and finding out that I could burn it suprised me.  I just happend to find it.  The windows method of right click -> send to -> cd drive does not seem very intuitive to me.

---

### Post by anlari on 2005-12-12
[QUOTE=gil-galad]Good reply.  I still say that the icons are not hard to change.  Simply go to [http://art.gnome.org/](http://art.gnome.org/) and look at their icon themes.[/QUOTE]

I'd go to gnome-look.org if it wasn't down for some reason.. They have got better stock... But I found this: 
[http://tango-project.org/Image:Screenshot_GNOME.png](http://tango-project.org/Image:Screenshot_GNOME.png)
[http://tango-project.org/Image:Screenshot_Tango2.png](http://tango-project.org/Image:Screenshot_Tango2.png)
There's before and after screenshots. The after screenshot desktop icons are  what I am after :p (Yes, going to test that out.)

[QUOTE=gil-galad]You can install them by simply dragging the download link onto the install button in the themes folder.[/QUOTE]

Yes, and then spend hours trying to fix the last ones to look decent :(     

[QUOTE=gil-galad]One more thing, the gnome print tool **does** allow you to print to PDF.  It is a very handy feature.[/QUOTE]

How? I'm here hmm trying to print from my browser (Opera) and umm doesn't seem possible.. Let's see some Gnome application. Ahh **there**. Okay, this argh. Typical. What I will need is that Scribus too, it's similar most likely in this matter. It'd have to be specifically cups PDF driver to support those too?

[QUOTE=gil-galad]The windows method of right click -> send to -> cd drive does not seem very intuitive to me.[/QUOTE]

Myself I can stand even K3B (lol) but that's a matter of your experiences. Windows migratees might really search for the burning application for a while. Or install K3B and scratch their heads with it if they couldn't find the nice Nautiful way :D

---

### Post by gil-galad on 2005-12-12
The tango icon theme might indeed be what are you looking for.  It is 100% consistent, they have very strict guidlines in place for their icons.  It is trying to become a good default for linux interfaces, and may become so.

I would recomend art.gnome.org over gnome-look.org.  It may have less stuff, but it is much better organized and has less junk.

As far as opera goes, I wouldn't use it.  Its not a gnome application or even a kde application.  It is not going to interface well with your desktop.  Have you tried epiphany or firefox?

---

### Post by anlari on 2005-12-12
[QUOTE=gil-galad]The tango icon theme might indeed be what are you looking for.[/QUOTE]

Some day. It's missing too many icons it seems.

[QUOTE=gil-galad]TI would recomend art.gnome.org over gnome-look.org.  It may have less stuff, but it is much better organized and has less junk.[/QUOTE]

gnome-look is down :rolleyes: 

I also managed to find out that usplash can be removed easily with one nice apt command.. No more a "splash screen" that looks like drawn by 8 year old :p I can't understand what they were thinking when they added that. I'll also ask the kernel to blank the screen absolutely until the x starts. That'll spare my nerves :KS

---

### Post by prizrak on 2005-12-12
Since this seems to be more or less graphics discussion does anyone know how to change the default system colors? For instance I'd like the default background on my applications to be grey (i.e. IM Windows, Thunderbird, Firefox) I know how to set separate color in FF but can't find the global options on TBird and Gaim, Tbird only lets me choose the background for emails not the entier app.
I personally like Gnomebaker for burning the interface seems like a good mix between advanced (Nero) and simple. Though Nero for Linux still ows but you gotta pay :(

---

### Post by gil-galad on 2005-12-12
Well, many users on this forum whined that they didn't want to see the kernel text, so they implemented a clean solution that didn't require kernel patches or X to start.  

I think they did a pretty good job myself, and it looks alright to me.  Does it really look that bad?  The windows XP splash is only 256 colors at most, its not the greatest loading screen in the world.

---

### Post by gil-galad on 2005-12-12
[QUOTE=prizrak]help with application background[/QUOTE]

For GTK applications, it should be fairly easy.  Either use a theme that has a grey background, or you can add a gtk config option to a file that will set it to grey. 

I don't know the exact config off the top of my head, but hopefully someone will stop by and post, or I can look it up later for you.

Now, firefox and thunderbird are not exactly GTK applications, although they obey some its rules, so I am not sure if they will respect setting the background color.

---

### Post by prizrak on 2005-12-12
[QUOTE=anlari]Some day. It's missing too many icons it seems.



gnome-look is down :rolleyes: 

I also managed to find out that usplash can be removed easily with one nice apt command.. No more a "splash screen" that looks like drawn by 8 year old :p I can't understand what they were thinking when they added that. I'll also ask the kernel to blank the screen absolutely until the x starts. That'll spare my nerves :KS[/QUOTE]
Actually it will still have a little of the screen. You need to pass the no-splash parameter to your kernel or just plain remove the word splash. To do that you do the following 
```
sudo gedit /boot/grub/menu.lst
```
change 
```
kernel          /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
```
to 
```
kernel          /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet **no-splash**
```
no more splash :)

---

### Post by prizrak on 2005-12-12
[QUOTE=gil-galad]For GTK applications, it should be fairly easy.  Either use a theme that has a grey background, or you can add a gtk config option to a file that will set it to grey. 

I don't know the exact config off the top of my head, but hopefully someone will stop by and post, or I can look it up later for you.

Now, firefox and thunderbird are not exactly GTK applications, although they obey some its rules, so I am not sure if they will respect setting the background color.[/QUOTE]
Oh I see, thanks. FF and Gaim is probably the most important ones since those are the ones I stare at all the time :) Would be nice if there was an easy way to set background color for GTK apps

---

### Post by anlari on 2005-12-12
[QUOTE=gil-galad]Well, many users on this forum whined that they didn't want to see the kernel text, so they implemented a clean solution that didn't require kernel patches or X to start.  

I think they did a pretty good job myself, and it looks alright to me.  Does it really look that bad?  The windows XP splash is only 256 colors at most, its not the greatest loading screen in the world.[/QUOTE]

I still with it can see many lines before it and while it see all kinds of meaningless "xxx and yyy starting" lines. And yes, it's just plain HORRIBLE looking. So it failed in it's purpose in any case.

---

### Post by anlari on 2005-12-12
[QUOTE=gil-galad]As far as opera goes, I wouldn't use it.  Its not a gnome application or even a kde application.  It is not going to interface well with your desktop.  Have you tried epiphany or firefox?[/QUOTE]

That's a dilemna, yes. It is a qt application and I can set the font/theme to match the GTK uhm reasonably well. Not perfectly but aok. 

It has got a lot less memory management problems, is faster and more rugged than Firefox. The overall quality just is majorly better :???:

---

### Post by cowlip on 2005-12-12
I  like Opera too :D

Anyways I also like how Gnome's default icons look, and I don't mind KDE's either.  In comparison I can usually understand what Gnome icons are and they look nice so I think it's a great theme.

---

