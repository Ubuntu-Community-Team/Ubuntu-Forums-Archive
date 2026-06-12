---
title: "I'm completely new to ubutu!"
date: 2008-07-12
forum: The Cafe
---

### Post by Markissocoollike on 2008-07-12
Hi, I've only just downloaded this new operating system yesterday, I think it is pretty cool that it found my NVDIA 8800 GTX driver and all but I'm still finding trouble with a few things :(

1. I'm not used to where the Applications and settings menus are, is there a way to move it? Oh wait! never mind lol! That'll teach me to think more clearly (I dragged the menus)

2. I'm finding it hard to run Warcraft 3 I've tried wine but I can't seem to find any exe files in the folder... am I missing an extension to wine? Cos there are other files with the .ink extension strangly I've never heard of such an extension before which is strange...

3. I've noticed on a few videos theres a way to give Ubuntu fancy effects, different backgrounds stuff like that... is there a place you can suggest or should download from or use a menu option (I've noticed on a youtube video someone used the system menu then preferences and then the 3rd item down strangly I found that I got Assistive technologies instead not the same user interface tho :(

4. I don't like having an applications menu which looks un-windows like as I want to be able to run mostly windows programs on linux, not sure if that made sense but is there a way to make a start menu of some kind in linux so that it looks more like windows... I want it this way so that my mother can have this operating system on hers as well (my god intel pentium 4 is so old ^^) I'm hoping that this will speed that computer up and also my laptops however sacrificing the windows menu which I'm so used to is hard and also wine doesn't seem to give me the right browsing menu anyway it says browse in C: but it doesn't seem to have anything there however when I look in another folder called mark (which is the username XD) I find that all my programs and files are there which is a bit strange.

5. I've also seen some kind of transparent layer box which hovers over the desktop (and unsure whether it does that to appication windows as well) I know I'm saying windows instead of browsers, applications and so on but what do you expect? I'm a noob lol!

Please help as I bet alot of newbies are having the same problems as me :P

---

### Post by AnLGP on 2008-07-12
3.  Right click, change desktop background, visual effects.  (I believe).

If you want the real fancy stuff go all the way down to the bottom and click the last option available.  I can't quite remember how to configure the compiz settings because I turn them all off but I believe there's a default menu now installed in the latest version of ubuntu.

4.  There are themes at gnome-look.org that would make it look more like windows.  There's also Kubuntu which has a blue look to it.  You can find a screenshot here 

[http://upload.wikimedia.org/wikipedia/commons/3/3f/Kubuntu.png](http://upload.wikimedia.org/wikipedia/commons/3/3f/Kubuntu.png)

or if you'd just like to install KDE under Ubuntu there's this:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

--

The other questions I can't help you with.

---

### Post by red_Marvin on 2008-07-12
You seem to have answered no 1 yourself so I'll have a go at the others.

**2:** You run a program with wine in the terminal [COLOR="DarkGreen"]*wine /pathto/program.exe*[/COLOR].

So if you have your w3 cd mounted you should be able to do something like [COLOR="DarkGreen"]*wine /media/cdrom/install.exe*[/COLOR], you have to check the path so it is correct though.
If you install a program with wine it will end up in a hidden directory in your home folder called .wine/drive_c (press ctrl+h to view hidden files in nautilus).
So you should be able to run the game with in the console with something like [COLOR="DarkGreen"]*wine /home/yourname/.wine/drive_c/program[COLOR="Red"]\ [/COLOR]files/more_directories/w3.exe*[/COLOR] -check the path so it is correct of course.
(note that you have to put "\" before any " " in directory names.)
If you get stuck post any error messages and I'll try to help, if it works you can add a launcher to your panel (post and I'll tell you how if you want).

**3:** [www.gnome-look.org](www.gnome-look.org) has a lot of backgrounds and themes. For fancy effects, do as AnLGP said, if it works, you might also want to install [apt:compizconfig-settings-manager](apt:compizconfig-settings-manager) which will give you access to more effects settings. You can then start it by going to the system menu->preferences->advanced desktop effects.

**4:** Honestly I think it will be easier to adapt to the new system if you give it a little time, instead of making it looking as much as windows as possible, however I think there's a couple of themes floating around if you search the forums and/or google. I haven't used them though so I can't tell you how good they are.

**5:** What do you mean, can you link to a screenshot? Is it awn (avant window navigator) you talk about?

---

### Post by Markissocoollike on 2008-07-12
> **AnLGP said:**
> 3.  Right click, change desktop background, visual effects.  (I believe).

If you want the real fancy stuff go all the way down to the bottom and click the last option available.  I can't quite remember how to configure the compiz settings because I turn them all off but I believe there's a default menu now installed in the latest version of ubuntu.


I've already tried that but its not that much different still kinda boring I'll have a look at those themes tho! Thanks... hopefully they'll be more answers...

---

### Post by AnLGP on 2008-07-12
see below

---

### Post by AnLGP on 2008-07-12
System - Preferences - Advanced Desktop Effects Settings

Hopefully someone will be able to answer your other questions.

EDIT:

It seems like the OP is talking about AWN Marvin I agree :).  Is this what you're talking about Mark?  [http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

also,

since you're new (welcome!) you may want to read this thread:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

it has lots of tips ticks and advice for the new ubuntu/linux user

---

### Post by cariboo on 2008-07-12
I'll answer question 4. first. Most windows programs will not run on Linux. Your best bet if your mother uses the computer also is to dual boot and set Windows as the default operating system. That way when she wants to use the computer all she has to do it start it up and everything that she is use to is there. There are many programs available that do the same thing as windows programs. Have a look here:

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

Question 2. Howto install WOW look here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Question 3. Desktop affects howto:

[http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2)

Question 5. I'm not sure what you mean. Can you possibly post a link to show us what you mean.

Jim

---

### Post by Markissocoollike on 2008-07-12
> **red_Marvin said:**
> 
**2:** You run a program with wine in the terminal [COLOR="DarkGreen"]*wine /pathto/program.exe*[/COLOR].

So if you have your w3 cd mounted you should be able to do something like [COLOR="DarkGreen"]*wine /media/cdrom/install.exe*[/COLOR], you have to check the path so it is correct though.
If you install a program with wine it will end up in a hidden directory in your home folder called .wine/drive_c (press ctrl+h to view hidden files in nautilus).
So you should be able to run the game with in the console with something like [COLOR="DarkGreen"]*wine /home/yourname/.wine/drive_c/program[COLOR="Red"]\ [/COLOR]files/more_directories/w3.exe*[/COLOR] -check the path so it is correct of course.
(note that you have to put "\" before any " " in directory names.)
If you get stuck post any error messages and I'll try to help, if it works you can add a launcher to your panel (post and I'll tell you how if you want).

So is there a way to make a desktop shortcut by this method? I'm not sure whether or not you said something like that as theres alot of writing there talking about a long way round running the program through the terminal which I wouldn't look forward to do every time I want to run a windows application :P

> **red_Marvin said:**
> 
**3:** [www.gnome-look.org](www.gnome-look.org) has a lot of backgrounds and themes. For fancy effects, do as AnLGP said, if it works, you might also want to install [apt:compizconfig-settings-manager](apt:compizconfig-settings-manager) which will give you access to more effects settings. You can then start it by going to the system menu->settings->advanced desktop effects.

There's alot of themes there 0.o I don't know where to start! Which one's your favorite?

> **red_Marvin said:**
> 
**4:** Honestly I think it will be easier to adapt to the new system if you give it a little time, instead of making it looking as much as windows as possible, however I think there's a couple of themes floating around if you search the forums and/or google. I haven't used them though so I can't tell you how good they are.

Would have been more helpful If you did that for me but oh well! Lets see what junk and useful information my search engine finds ^^

> **red_Marvin said:**
> 
**5:** What do you mean, can you link to a screenshot? Is it awn (avant window navigator) you talk about?

Theres a youtube video which will show you I WILL NOT go through the hassel of making some damn upload which takes ages to do! I hate uploading them! 

Heres a link similar to the youtube video (it aint that clear though gimmie a moment to find a clearer one...)

[http://www.youtube.com/watch?v=EjQ4Nza34ak](http://www.youtube.com/watch?v=EjQ4Nza34ak)

---

### Post by Markissocoollike on 2008-07-12
> **cariboo907 said:**
> 

Question 2. Howto install WOW look here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


Lol! That's the boring version I hate the MMORPG it's long and boring! I'm talking about Warcraft 3!

---

### Post by AnLGP on 2008-07-12
The video you linked to shows a program called looking glass.

[http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/)

---

### Post by Markissocoollike on 2008-07-12
I can't seem to find any youtube videos with the hover menu like that ARG!

---

### Post by Markissocoollike on 2008-07-12
> **AnLGP said:**
> The video you linked to shows a program called looking glass.

[http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/)

but no download on the site? weird 0.o

---

### Post by Markissocoollike on 2008-07-12
> **Markissocoollike said:**
> but no download on the site? weird 0.o

hang on here it is nasty little buggers hidding lol! 
[https://lg3d-core.dev.java.net/](https://lg3d-core.dev.java.net/)

---

### Post by Markissocoollike on 2008-07-12
> **Markissocoollike said:**
> hang on here it is nasty little buggers hidding lol! 
[https://lg3d-core.dev.java.net/](https://lg3d-core.dev.java.net/)

my god the instructions are hard! I hope I manage to make this work!

---

### Post by Markissocoollike on 2008-07-12
> **Markissocoollike said:**
> my god the instructions are hard! I hope I manage to make this work!

screw that I can't even get it working in the terminal what rubbish instructions!

---

### Post by Markissocoollike on 2008-07-12
> **cariboo907 said:**
> I'll answer question 4. first. Most windows programs will not run on Linux. Your best bet if your mother uses the computer also is to dual boot and set Windows as the default operating system. That way when she wants to use the computer all she has to do it start it up and everything that she is use to is there. There are many programs available that do the same thing as windows programs.

Thats a stupid idea the reason I want to use linux is because its faster I don't want to have 2 operating systems at the same time that would be a joke! It would be like opening a tin of tuna and leaving it out in the rain completely useless either I find a way to use windows in linux otherwise there is no point in making mum have to use the same OS with slow capabilities... and I ask you why would you say this anyway? It is already setup like that when you boot the computer you've just wasted your time typing that!

---

### Post by Markissocoollike on 2008-07-12
> **AnLGP said:**
> System - Preferences - Advanced Desktop Effects Settings

Hopefully someone will be able to answer your other questions.

EDIT:

It seems like the OP is talking about AWN Marvin I agree :).  Is this what you're talking about Mark?  [http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

also,

since you're new (welcome!) you may want to read this thread:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

it has lots of tips ticks and advice for the new ubuntu/linux user

Thanks for that I got the "cube" working it looks like 2d square that rotates to me! :lolflag: anyway I can't get the other thing to work, the terminal is causing me problems either saying its not there or doesn't recognise command thats just stupid...

---

### Post by avtolle on 2008-07-12
Ah, the arrogance of youth. 

Which commands are not being recognized?

---

### Post by TSS on 2008-07-12
I'm going to answer your question #2, about installing Warcraft 3 (because I installed Warcraft 3 along with a few other games last night :-p).

First, I suggest checking out the Wine Application Database ([http://appdb.winehq.org/](http://appdb.winehq.org/)).  Sometimes you can find fixes to problems you are having if you look up your specific game.

What I did was I put in the Warcraft 3 CD, and Ubuntu automatically opened the CD.  Double click Setup.exe or Install.exe and Wine will automatically run it.  My install went by just fine, with no problems, so I do not see why yours should not.  After Warcraft 3 is installed, you can find it (assuming Gnome) under Applications > Wine > Programs > Warcraft III.

Hope that helps!

TSS

---

### Post by nothingspecial on 2008-07-12
> **Markissocoollike said:**
> Thanks for that I got the "cube" working it looks like 2d square that rotates to me! 


Go to system > preferences > advaced desktop settings
Click on the first option - general
click the 3rd tab - Desktop Size
The 1st line "horizontal virtual size" change the figure on the far right to 4 and you will have your cube;)


Quote -
"Thats a stupid idea the reason I want to use linux is because its faster I don't want to have 2 operating systems at the same time that would be a joke! It would be like opening a tin of tuna and leaving it out in the rain completely useless either I find a way to use windows in linux otherwise there is no point in making mum have to use the same OS with slow capabilities... and I ask you why would you say this anyway? It is already setup like that when you boot the computer you've just wasted your time typing that!"

Try not to be so rude. People are trying to help. Most people (especially people like your Mum who have had linux thrust upon them) find dual booting alot easier during the transition process.

---

### Post by red_Marvin on 2008-07-12
The instructions I posted on warcraft 3 is what you would need to do to install it, and when running it you would need to use the command I posted later in the text. However there's nothing stopping you from putting it in a launcher later so you can start it by just clicking a button.
I didn't post that part yet though because you'd first need to get the commandline install and launching correct.

---

### Post by Markissocoollike on 2008-07-12
> **nothingspecial said:**
> Go to system > preferences > advaced desktop settings
Click on the first option - general
click the 3rd tab - Desktop Size
The 1st line "horizontal virtual size" change the figure on the far right to 4 and you will have your cube;)


Quote -
"Thats a stupid idea the reason I want to use linux is because its faster I don't want to have 2 operating systems at the same time that would be a joke! It would be like opening a tin of tuna and leaving it out in the rain completely useless either I find a way to use windows in linux otherwise there is no point in making mum have to use the same OS with slow capabilities... and I ask you why would you say this anyway? It is already setup like that when you boot the computer you've just wasted your time typing that!"

Try not to be so rude. People are trying to help. Most people (especially people like your Mum who have had linux thrust upon them) find dual booting alot easier during the transition process.

Tried the your cube idea still 2d im afraid I've even tried increasing to 8 XD!

As for your comment on rudeness yes i was rude to put it bluntly, but since it was already setup like that on installation there was no point in it! I apologize but to be fair there isn't anything to apologize for as we're simply talking about this "dual boot" which already exists why anyone would want to talk about it when I want a built in windows linux is beyond me, though I understand how useless it is to me when I'm not interested in having two operating systems... whatever!

Anyway I'm still looking for a windows like start menu, although the one I have already got is good it confused my sister so obviously I need to either work on making one myself which I laugh at the thought of me actually understanding the stupid terminal which doesn't recognize commands (the irony!) or actually finding something which will make a windows start menu in linux (no luck yet X( ) 

As for these unrecognizable commands it seems to either to not recognize the path or command, I try to run a bin file for example which seems to work but then gives me some kind of error message which quite frankly is annoying, as a windows user I'm not very pleased that I haven't managed to do anything I want yet so it looks like I'm going to have to read a manual on how to program linux... great... :mad: If anyone sees a something please let me know I've heard they are making something like windows taking 10 years or something 0.o but still haven't finished it :P I think i'll carry on messing with stuff until I get it to work :lolflag:

---

### Post by Markissocoollike on 2008-07-12
> **red_Marvin said:**
> The instructions I posted on warcraft 3 is what you would need to do to install it, and when running it you would need to use the command I posted later in the text. However there's nothing stopping you from putting it in a launcher later so you can start it by just clicking a button.
I didn't post that part yet though because you'd first need to get the commandline install and launching correct.

Don't want to reinstall it as I won't have any saved games -.-

---

### Post by Markissocoollike on 2008-07-12
> **Markissocoollike said:**
> 
Anyway I'm still looking for a windows like start menu, although the one I have already got is good it confused my sister so obviously I need to either work on making one myself which I laugh at the thought of me actually understanding the stupid terminal which doesn't recognize commands (the irony!) or actually finding something which will make a windows start menu in linux (no luck yet X( ) 


I dragged the menu for my taskbar to the bottom of the screen with the "application menu" the irony of how simple it was really ticks me off >.>

---

### Post by Markissocoollike on 2008-07-12
Anyways I'll try reprogramming the start menu woop... this is gonna take a looooooong time :(

---

### Post by cariboo on 2008-07-12
You seem to want your cake and eat it too. Remember Linux is not Windows. Read this article about [Linux]("//http://en.wikipedia.org/wiki/Linux") and you might understand why you can't do everything you want. The reason I brought up dual booting , is that you didn't mention how you installed Ubuntu. There are a lot of people here that went whole hog and deleted Windows completely. 

Jim

---

### Post by Markissocoollike on 2008-07-12
I have another question I need an answer to how do I get rid of this stupid security password I always get when installing something, sure its helpful in some ways but its unnecessary any ideas?

---

### Post by cariboo on 2008-07-12
You can't. You don't run as an administrator all the like you do in Windows. You only need to run as root when you are installing programs. The rest of the time you run as a normal user. Any time you need to install something you use sudo (Super User Do). In a Applications-->Accessories-->Terminal type

```
man sudo
```

for more info

Jim

---

### Post by Markissocoollike on 2008-07-12
well according to this guy I can change the GUI with ruby...might as well try!

---

### Post by nothingspecial on 2008-07-12
> **Markissocoollike said:**
> Tried the your cube idea still 2d im afraid I've even tried increasing to 8 XD!

As for your comment on rudeness yes i was rude to put it bluntly, but since it was already setup like that on installation there was no point in it! I apologize but to be fair there isn't anything to apologize for as we're simply talking about this "dual boot" which already exists why anyone would want to talk about it when I want a built in windows linux is beyond me, though I understand how useless it is to me when I'm not interested in having two operating systems... whatever!

1st did you get my edit, got it wrong 1st time sorry. This is how it should look [ATTACH]77504[/ATTACH

---

### Post by cariboo on 2008-07-12
It has nothing to do with the gui. Using sudo is system wide, even if you run without a gui you still have to be root to install a program.

THe reason Ubuntu uses sudo instead or root, is that Ubuntu is considered a good way for a newbie to get started with Linux. Most newbies have no idea what they are doing and if they ran as root all the time they could render the system unusable in no time flat and then blame their lack of knowledge on the os.

Jim

---

### Post by Markissocoollike on 2008-07-12
that looks exactly the same to me no difference

---

### Post by Markissocoollike on 2008-07-12
> **cariboo907 said:**
> It has nothing to do with the gui. Using sudo is system wide, even if you run without a gui you still have to be root to install a program.

THe reason Ubuntu uses sudo instead or root, is that Ubuntu is considered a good way for a newbie to get started with Linux. Most newbies have no idea what they are doing and if they ran as root all the time they could render the system unusable in no time flat and then blame their lack of knowledge on the os.

Jim

I said i'd try I didn't say I'm going to muck up the os I'm watching a youtube video on how to do it sides if it doesn't work you can be all smug with yourself that I didn't listen to you so I'm just going to carry on what I'm doing now...

---

### Post by nothingspecial on 2008-07-12
Hey, spent that long getting a screenshot I forgot the second issue. Thanks for saying sorry. But guess what. I`ve never had a dual boot, I`ve never had windows but some people really mess up during install and nuke windows when they didn`t mean to - all their data, photos, music the lot.
 Like I said, people are only trying to help. Now, I know f all about windows but I do know that when I bought a laptop with Vista on it I didn`t have a clue, I nuked it before 2 weeks were up so I can see the issues. 
I couldn`t be bothered to learn a new os. That`s why I have sympathy with your mum & sister.


Anyway you have enabled desktop effects haven`t you?
system > preferences > appearance > desktop effects - then click on the bottom option

---

### Post by Markissocoollike on 2008-07-12
yep I feel like I'm having a spot of deja-vu recently on these forums! Maybe I can only have 2 screens? Does that give you any clues?

---

### Post by nothingspecial on 2008-07-12
You have enabled both "desktop cube" and "rotate cube" haven`t you.

This[ATTACH]77514[/ATTACH]

+ This[ATTACH]77515[/ATTACH]

+ This[ATTACH]77516[/ATTACH]

= This[ATTACH]77517[/ATTACH]

---

### Post by Markissocoollike on 2008-07-12
> **nothingspecial said:**
> You have enabled both "desktop cube" and "rotate cube" haven`t you.

This[ATTACH]77514[/ATTACH]

+ This[ATTACH]77515[/ATTACH]

+ This[ATTACH]77516[/ATTACH]

= This[ATTACH]77517[/ATTACH]

hang on... I don't have a custom!

---

### Post by nothingspecial on 2008-07-12
> **Markissocoollike said:**
> hang on... I don't have a custom!

Well, go to system > administration > restricted drivers manager

!!!!!This may be different in Hardy 8.04 (I still use Gutsy 7.10) and see if there`s any drivers you need to enable.

---

### Post by Markissocoollike on 2008-07-12
> **nothingspecial said:**
> Well, go to system > administration > restricted drivers manager

!!!!!This may be different in Hardy 8.04 (I still use Gutsy 7.10) and see if there`s any drivers you need to enable.

nothing like that under administraition

---

### Post by nothingspecial on 2008-07-12
There is something in Hardy that does the same thing. Have a look in your menus for "drivers" or something like that.

Also, have you got compiz turned on? try

```
compiz --replace
```

---

### Post by Markissocoollike on 2008-07-12
> **nothingspecial said:**
> There is something in Hardy that does the same thing. Have a look in your menus for "drivers" or something like that.

Also, have you got compiz turned on? try

```
compiz --replace
```

I tried your little code but i don't think it did anything

the only thing which is near the name driver is hardware drivers which is not what we are looking for as it just tells me my NVDIA driver is install *yawn*

I was a little scared that compiz replace might have booted my computer I had alot of applications running which I were using :lolflag:

---

### Post by LaRoza on 2008-07-12
I see redundant threads. Please keep threads focused on real issues and do not make more than one thread per issue.

---

