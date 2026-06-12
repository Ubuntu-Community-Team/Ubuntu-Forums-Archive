---
title: "How to make a windows start menu in ubuntu?"
date: 2008-07-12
forum: The Cafe
---

### Post by Markissocoollike on 2008-07-12
I want to make a start menu to replace the applications menu so its easier to access them I had previously been confused about the display of the applications menu so I'd like to revert to the one in Windows XP does anyone know of any ways of doing this I've heard of something called MenuDrake but unfortunately I can't find the download... some how I doubt it's what I'm looking for anyway.

---

### Post by scragar on 2008-07-12
try using the **main menu** instead of the **menu bar** which is installed be default, it offers a vista style button.

[http://rpm.pbone.net/index.php3/stat/4/idpl/4405280/com/menudrake-0.6.1-5mdk.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/4405280/com/menudrake-0.6.1-5mdk.i586.rpm.html) <-- you can download the rpm, but that can be converted to a debian package(which ubuntu uses) using **alien** (```
sudo apt-get install alien
```), I don't know how compatable it is with the gnome menus though.

---

### Post by easybake on 2008-07-12
Download the ubuntu system panel. It's fairly similiar to the xp menu. But if can be a little bit harder to customize.

---

### Post by Markissocoollike on 2008-07-12
DING DING DING DING! found one!!! yay!!!! man that took forever

---

### Post by Markissocoollike on 2008-07-12
okay I found a vista like start menu it's located here: [http://linux.softpedia.com/progDownload/Vista-like-Start-Menu-Download-33794.html](http://linux.softpedia.com/progDownload/Vista-like-Start-Menu-Download-33794.html)
once downloaded extract to desktop follow the read me in the extracted file if you are unsure of what to do and there ya go! the only thing I hate about it is that theres a little black box that sticks out... but whatever yay! Now all I need to do is add window shortcuts!

Here's an upgrade:
[http://www.gnome-look.org/content/do...=1&tan=4461126](http://www.gnome-look.org/content/do...=1&tan=4461126)

---

### Post by Markissocoollike on 2008-07-12
does anyone know of a way to fix the top of the logo? its quite annoying :(

---

### Post by aktiwers on 2008-07-12
Could you upload a screenshot of it? I would like to see it..  (press the "prt sc" button) :)
Or type:
```
gnome-screenshot
```

in terminal

Would be nice of you.. thanks!

---

### Post by Markissocoollike on 2008-07-12
hang on a sec, gonna find a decent image editor

---

### Post by Markissocoollike on 2008-07-12
k fine ill just post it wishd I had paint on here :(

---

### Post by Markissocoollike on 2008-07-12
I can't seem to printscreen when the start menu is clicked on... hmm any suggestions on how to get round that?

---

### Post by abn91c on 2008-07-12
for image editing install Gimp, for a windows-like menu try mint menu you can find it in softpedia.com

---

### Post by TSS on 2008-07-12
> **Markissocoollike said:**
> I can't seem to printscreen when the start menu is clicked on... hmm any suggestions on how to get round that?

```
gnome-screenshot -d 3
```

That will give you a delay of 3 seconds, during which you can click on the start menu.

---

### Post by Markissocoollike on 2008-07-12
ok managed to screenshot it yay!

---

### Post by aktiwers on 2008-07-12
Thanks a lot! I had never seen that one :)

---

### Post by Markissocoollike on 2008-07-12
This is so much better than the old menu I was using for ubuntu everything is now so neat and organised ^^

---

### Post by Markissocoollike on 2008-07-12
> **aktiwers said:**
> Thanks a lot! I had never seen that one :)

no problem ;) you can add my first thanked number if you want ^^

---

### Post by mdsmedia on 2008-07-12
> **Markissocoollike said:**
> This is so much better than the old menu I was using for ubuntu everything is now so neat and organised ^^I hate the Windows START menu. I prefer how it's setup in Ubuntu. It's so neat and organised ;).

Each to their own. It's just what you're used to I guess. Mind you, I haven't used Vista.

---

### Post by SunnyRabbiera on 2008-07-12
One I can suggest is mintmenu from linux mint, its found here:
[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

---

### Post by Markissocoollike on 2008-07-12
> **mdsmedia said:**
> I hate the Windows START menu. I prefer how it's setup in Ubuntu. It's so neat and organised ;).

Each to their own. It's just what you're used to I guess. Mind you, I haven't used Vista.

I'm pretty sure you'd like this one it would get rid of a whole taskbar and you'll be able to access your files easier... it comes with a search so I'd say it's better than having three menus the only thing I dislike its a little buggy with the logo :( but other than that it's great!

---

### Post by aktiwers on 2008-07-12
There you go.. 

You could also check this out, they also have a XP like menu
[http://sourceforge.net/projects/auroraproject/](http://sourceforge.net/projects/auroraproject/)
[see the screenshot on that page]

---

### Post by Markissocoollike on 2008-07-12
> **SunnyRabbiera said:**
> One I can suggest is mintmenu from linux mint, its found here:
[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

It's pretty much the same but it's not as good (design wise) I'm sure this would be for the user with not as much space on their computer but I'm quite curious to know what those blank execution files are :/

---

### Post by ChameleonDave on 2008-07-12
> **Markissocoollike said:**
> I want to make a start menu to replace the applications menu so its easier to access them I had previously been confused about the display of the applications menu so I'd like to revert to the one in Windows XP does anyone know of any ways of doing this I've heard of something called MenuDrake but unfortunately I can't find the download... some how I doubt it's what I'm looking for anyway.
The current menu is perfectly good.  There is no reason to change it.  Linux is not Windows.

We have seen your questions before on the forum.  You led us on a wild goose chase regarding ruby.  You are an absolute beginner, and have trouble with a lot of things.  I really, really, really, really believe that you should not try to do all these customisations and installations.  Simply use Ubuntu.  Just use it.  Surf the web, use applications, and get a feel for how stuff works.  Don't try to change anything until you have explored a bit more and learnt a thing or two.  That is my sincere advice.

---

### Post by SunnyRabbiera on 2008-07-12
> **Markissocoollike said:**
> I'm pretty sure you'd like this one it would get rid of a whole taskbar and you'll be able to access your files easier... it comes with a search so I'd say it's better than having three menus the only thing I dislike its a little buggy with the logo :( but other than that it's great!

I never had an issue finding my way with the standard menu in ubuntu, come on links to your computer and files is in a list called "places"... seems simple enough to me.

---

### Post by Markissocoollike on 2008-07-12
> **aktiwers said:**
> There you go.. 

You could also check this out, they also have a XP like menu
[http://sourceforge.net/projects/auroraproject/](http://sourceforge.net/projects/auroraproject/)
[see the screenshot on that page]

wow nice! But does it have a search?

---

### Post by aktiwers on 2008-07-12
Sorry I never used it.. I just found it so I dont know:)
I am pretty happy with the default one in Gnome, else I just open apps through the terminal - that is the fastest way I guess!

---

### Post by Markissocoollike on 2008-07-12
> **ChameleonDave said:**
> The current menu is perfectly good.  There is no reason to change it.  Linux is not Windows.

We have seen your questions before on the forum.  You led us on a wild goose chase regarding ruby.  You are an absolute beginner, and have trouble with a lot of things.  I really, really, really, really believe that you should not try to do all these customisations and installations.  Simply use Ubuntu.  Just use it.  Surf the web, use applications, and get a feel for how stuff works.  Don't try to change anything until you have explored a bit more and learnt a thing or two.  That is my sincere advice.

I know what I'm doing here... besides judging by how you didn't even fix the issue I'd say you don't have much experience either I've had this operating system for three days now and already getting the hang of it so i'm not the one at fault here

---

### Post by SunnyRabbiera on 2008-07-12
> **Markissocoollike said:**
> wow nice! But does it have a search?

ubuntu has a built in search tool called the deskbar, you can add it by right clicking your panel and selecting "add to panel"
really if you want linux to be like windows you should not have switched over to it in the first place, the two work in completely different ways...

---

### Post by Markissocoollike on 2008-07-12
Besides it would be better if linux was more like windows if this is suppost to be for beginners sure I like how smoothly it runs but there is need to change things in order to get your operating system the way you want it to be but lets just say it was a draw there is no right or wrong answer when you are dealing with problems

---

### Post by Markissocoollike on 2008-07-12
> **SunnyRabbiera said:**
> ubuntu has a built in search tool called the deskbar, you can add it by right clicking your panel and selecting "add to panel"
really if you want linux to be like windows you should not have switched over to it in the first place, the two work in completely different ways...

think ill stick with what I've got its close enough to windows in my opinion

---

### Post by LaRoza on 2008-07-12
> **mdsmedia said:**
> I hate the Windows START menu. I prefer how it's setup in Ubuntu. It's so neat and organised ;).


The Vista Start menu is much better than its previous versions, however, it reminds me of other operating systems...

> **Markissocoollike said:**
> Besides it would be better if linux was more like windows if this is suppost to be for beginners sure I like how smoothly it runs but there is need to change things in order to get your operating system the way you want it to be but lets just say it was a draw there is no right or wrong answer when you are dealing with problems

Ubuntu is Linux for Humans, not Linux for Windows users. You can try a different distro if you want. Vixta (looks like Vista, but better): [http://vixta.sourceforge.net/](http://vixta.sourceforge.net/) has a lot you'll find familiar. LinuxMint is also an option.

---

### Post by SunnyRabbiera on 2008-07-12
> **Markissocoollike said:**
> Besides it would be better if linux was more like windows if this is suppost to be for beginners sure I like how smoothly it runs but there is need to change things in order to get your operating system the way you want it to be but lets just say it was a draw there is no right or wrong answer when you are dealing with problems

But the two are supposed to be different, thats my point...
Linux is not windows nor it ever be windows.
Honestly does linux have to have a start menu, a my computer and a little blue E for people to understand it?
You dont see apple having complaints like this, linux is a alternative system it is meant to be different...

---

### Post by jerome1232 on 2008-07-12
> **Markissocoollike said:**
> Besides it would be better if linux was more like windows if this is suppost to be for beginners sure I like how smoothly it runs but there is need to change things in order to get your operating system the way you want it to be but lets just say it was a draw there is no right or wrong answer when you are dealing with problems

Well Linux is based on Minix, which was a small UNIX OS, it's older than windows and very different, you will find very little in common between Windows and Linux, it's just a whole different way of doing things. Actually Windows is the minority, in that it's not based on UNIX (most OS's are).

With Windows you can get nowhere near the different looks and flavors you can on the variety of Linux DE's (Desktop Enviroments) and Distro's.

edit: I keep making typo's lol

---

### Post by ChameleonDave on 2008-07-12
> **Markissocoollike said:**
> I know what I'm doing here... besides judging by how you didn't even fix the issue I'd say you don't have much experience either I've had this operating system for three days now and already getting the hang of it so i'm not the one at fault here
Don't get defensive.  The very fact that you can say that I didn't "fix the issue" with Ruby on your computer shows that I am right.  The issue was that you didn't even understand what Ruby was.  That's an issue that only you can resolve.  You're claiming I don't have much experience?  Look to the left.  I have been thanked a hundred times by people whom I have helped with tech support.

But this isn't a matter of bragging about who knows what.  I'm honestly and sincerely telling you that you ought not to try customising and fiddling with your operating system at this point.  Just learn to use it.  That is what is fundamental.  Otherwise, you will be a burden to people who are donating their free time to help people use Ubuntu.  Give it a week at least.

---

### Post by LaRoza on 2008-07-12
> **jerome1232 said:**
> Well Linux is based on Minix, which was a small UNIX OS, it's older than windows and very different, you will find very little in common between Windows and Linux, it's just a whole different way of doing things. Actually Windows is the minority, in that it's not based on UNIX (most OS's are).

No, Linux is not based on Minix. It was made because Minix developers wouldn't accept changes from the community (the source to it was open, but you couldn't change it).

Minix was a complete rewrite of a Unix. None of them share code. (BSD does/did have some of the original Unix code)

---

### Post by Markissocoollike on 2008-07-12
> **ChameleonDave said:**
> Don't get defensive.  The very fact that you can say that I didn't "fix the issue" with Ruby on your computer shows that I am right.  The issue was that you didn't even understand what Ruby was.  That's an issue that only you can resolve.  You're claiming I don't have much experience?  Look to the left.  I have been thanked a hundred times by people whom I have helped with tech support.

But this isn't a matter of bragging about who knows what.  I'm honestly and sincerely telling you that you ought not to try customising and fiddling with your operating system at this point.  Just learn to use it.  That is what is fundamental.  Otherwise, you will be a burden to people who are donating their free time to help people use Ubuntu.  Give it a week at least.

Of course I'll be defensive if you try to insult me... are you saying i don't have denfences built in? lol! I do understand what Ruby is I am studying a BTEC ND in software development I'm not a total noob... lets just leave it at that okay? Or we could have a spamming competition which will lead nowhere plus to be precise thats 98 thanks not a hundred sure you have got alot of post and thanks but bragging is not something to be proud of even though alot of people don't even notice they are doing so and by the way my teacher taught me to learn by doing so you'll probably have a different learning style than me... I had learn that in key skills eugh horrible!

---

### Post by jerome1232 on 2008-07-12
> **LaRoza said:**
> No, Linux is not based on Minix. It was made because Minix developers wouldn't accept changes from the community (the source to it was open, but you couldn't change it).

Minix was a complete rewrite of a Unix. None of them share code. (BSD does/did have some of the original Unix code)

My mistake :) I guess I should read more carefully.

---

### Post by LaRoza on 2008-07-12
> **jerome1232 said:**
> My mistake :) I guess I should read more carefully :)

I have the source for Minix (in a book, nothing like reading source code on a book...) and I have Linus's original code for Linus. Someday I will have to look into them and see how similiar they are. I have read them to some degree and noticed nothing too similiar (as far as code, they are both meant to be Unix like)

---

### Post by Markissocoollike on 2008-07-12
> **LaRoza said:**
> No, Linux is not based on Minix. It was made because Minix developers wouldn't accept changes from the community (the source to it was open, but you couldn't change it).

Minix was a complete rewrite of a Unix. None of them share code. (BSD does/did have some of the original Unix code)

so is it based on Unix? Cos I think it was unix which linux was based around we had to do presentations for different operating systems but I'm still unsure

---

### Post by Markissocoollike on 2008-07-12
wow you have alot of posts on this forum :P

---

### Post by Alaxandar on 2008-07-12
I am sorry guys but I read the read me, and installed python.Then when I double click it it ask me if i wan to run it or cancel or display or in terminal. When I click run nothing happens when I click in terminal the terminal appears for a second then disappears. So what ever is going on please help!

---

### Post by LaRoza on 2008-07-12
> **Markissocoollike said:**
> so is it based on Unix? Cos I think it was unix which linux was based around we had to do presentations for different operating systems but I'm still unsure

Unix, a while ago, was an operating system by itself. Now it is just a specification. Mac OS X is a "Unix", meaning it has been officially certified by the committee.

[http://en.wikipedia.org/wiki/Unix](http://en.wikipedia.org/wiki/Unix)

Linux follows the standards but isn't certified. 

> **Markissocoollike said:**
> wow you have alot of posts on this forum :P

Some people have more :-)

> **Alaxandar said:**
> I am sorry guys but I read the read me, and installed python.Then when I double click it it ask me if i wan to run it or cancel or display or in terminal. When I click run nothing happens when I click in terminal the terminal appears for a second then disappears. So what ever is going on please help!

See: [http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)

---

### Post by Markissocoollike on 2008-07-12
> **Alaxandar said:**
> I am sorry guys but I read the read me, and installed python.Then when I double click it it ask me if i wan to run it or cancel or display or in terminal. When I click run nothing happens when I click in terminal the terminal appears for a second then disappears. So what ever is going on please help!

alright it should be installed right click your task bar at the bottom and add to panel type in vista double click and you're done easy ^^

---

### Post by Markissocoollike on 2008-07-12
by the way I found an upgrade yay! 
[http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126](http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126)
:guitar:
so don't forget to upgrade it!

---

### Post by ChameleonDave on 2008-07-12
> **Markissocoollike said:**
> ol! I do understand what Ruby is I am studying a BTEC ND in software development I'm not a total noob... 
That reminds me of a guy on here the other day who just couldn't understand how to partition a hard drive, and then claimed to have had several years' experience employed as a Unix administrator.  It just really makes you wonder...  perhaps I'll meet a mechanic who doesn't know how to fill a car with petrol, or a dentist who's never bought a tube of toothpaste.

---

### Post by Markissocoollike on 2008-07-12
> **ChameleonDave said:**
> That reminds me of a guy on here the other day who just couldn't understand how to partition a hard drive, and then claimed to have had several years' experience employed as a Unix administrator.  It just really makes you wonder...  perhaps I'll meet a mechanic who doesn't know how to fill a car with petrol, or a dentist who's never bought a tube of toothpaste.

lol! Yeh I can partition a drive I've even got a disk with software to but theres really no point with resizing and splitting the drive up cos I managed to get windows without doing that which I thought was weird! Anywho... How can a unix administrator not know how to partition a hard drive!? Obviously lying but I am not I assure you :P

---

### Post by Lostincyberspace on 2008-07-12
Install windows in vmware.

---

### Post by Markissocoollike on 2008-07-12
> **Lostincyberspace said:**
> Install windows in vmware.

err do you even know what we are talking about? We are talking about getting a start menu that looks like windows XP not vmware I don't want that!

---

### Post by LaRoza on 2008-07-12
> **Markissocoollike said:**
> lol! Yeh I can partition a drive I've even got a disk with software to but theres really no point with resizing and splitting the drive up cos I managed to get windows without doing that which I thought was weird! Anywho... How can a unix administrator not know how to partition a hard drive!? Obviously lying but I am not I assure you :P

> **Lostincyberspace said:**
> Install windows in vmware.



> **Markissocoollike said:**
> err do you even know what we are talking about? We are talking about getting a start menu that looks like windows XP not vmware I don't want that!

It looks like a valid post after that one you made. It would allow you to use Windows on Linux without partitioning.

---

### Post by Alaxandar on 2008-07-12
I read it twice I tried to run in terminal, I coppied the thing sorry I have no Idea what to do

---

### Post by bikeboy on 2008-07-12
> **Markissocoollike said:**
> by the way I found an upgrade yay! 
[http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126](http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126)
so don't forget to upgrade it!

It would be better if you didn't link directly to the download. Try editing your link to go to the project's information page.

---

### Post by Gripp on 2008-07-12
why would you do that to a linux machine!! its like blasphemy! aaarrrrgggggg

j/k, yet another reason linux rocks

---

### Post by madjr on 2008-07-13
> **Markissocoollike said:**
> by the way I found an upgrade yay! 
[http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126](http://www.gnome-look.org/content/download.php?content=71425&id=1&tan=4461126)
:guitar:
so don't forget to upgrade it!

hey thanks

this is very cool, i used the old version , but the developer mae it even cooler.


Gnome has 2 built in program search functions:

**Alt + F2** brings up run/search application menu


i also use **deskbar** (just click add to panel to add it) can do some cool stuff:

check a screencast
[http://blogs.gnome.org/nigeltao/2006/03/13/my-babys-all-grown-up-now/](http://blogs.gnome.org/nigeltao/2006/03/13/my-babys-all-grown-up-now/)


[IMG]http://philwilson.org/images/deskbar-screenshot.png[/IMG]



**write to twitter**:

[IMG]http://philwilson.org/images/twitter-deskbar-screenshot.png[/IMG]

[http://www.philwilson.org/blog/2007/03/post-to-twitter-from-ubuntu-deskbar.html](http://www.philwilson.org/blog/2007/03/post-to-twitter-from-ubuntu-deskbar.html)



**Calculate stuff**:

[IMG]http://www.kryogenix.org/photoimages/pictures/random/566.png[/IMG]

[http://www.kryogenix.org/days/2006/09/06/converter-deskbar](http://www.kryogenix.org/days/2006/09/06/converter-deskbar)



**search for applications** (even ones that get lost or without a shortcut) even **search the web**

[IMG]http://www.builderau.com.au/i/g/gnome216/deskbar.png[/IMG]



even **search flikr** (or others) directly

[IMG]http://fabione.files.wordpress.com/2007/05/deskbar-photo-plugin.png[/IMG]

[http://fabio.corneti.com/?s=rdp](http://fabio.corneti.com/?s=rdp)




You may also want to try **Gnome-do**

[http://do.davebsd.com/](http://do.davebsd.com/)

[IMG]http://gabuntu.files.wordpress.com/2008/03/gnome-do-nueva.png[/IMG]


also, if you want an **Ubuntu for windows users**, try **[COLOR="Green"]linuxmint[/COLOR]** (i use both :)) . Linuxmint also has gnome-do by default.

[http://www.linuxmint.com/](http://www.linuxmint.com/)


and remember that linux is about **working smarter** not **copy** Vista. In a month you'll forget all about the "**windows ways**", i know i did and couldn't been happier!

i like your way of figuring stuff on your own, it's great to learn new stuff, enjoy!

---

### Post by Markissocoollike on 2008-07-13
Dunno if anyone is still active on this thread but I'm finding trouble installing a new "xp" theme which would be useful to replace the other menu with since its a little dodged (no applications appearing) 
Heres the link: <snipped />
Any ideas on how to install?

---

### Post by Markissocoollike on 2008-07-13
> **Markissocoollike said:**
> Dunno if anyone is still active on this thread but I'm finding trouble installing a new "xp" theme which would be useful to replace the other menu with since its a little dodged (no applications appearing) 
Heres the link: [http://fc05.deviantart.com/fs16/f/2007/179/0/c/Ubuntu_XP_by_ShamusHand.rar](http://fc05.deviantart.com/fs16/f/2007/179/0/c/Ubuntu_XP_by_ShamusHand.rar)
Any ideas on how to install?

actually, this looks more like a patch that makes xp look like ubuntu which is stupid concidering how slowly it would run in comparision to the original

---

### Post by LaRoza on 2008-07-13
> **Markissocoollike said:**
> Dunno if anyone is still active on this thread but I'm finding trouble installing a new "xp" theme which would be useful to replace the other menu with since its a little dodged (no applications appearing) 
Heres the link:
Any ideas on how to install?

Please provide links to pages, not downloads.

---

### Post by Markissocoollike on 2008-07-13
> **LaRoza said:**
> Please provide links to pages, not downloads.

its no good anyway man... tried it (it's for windows!)

---

### Post by Markissocoollike on 2008-07-13
...how come my posts suddenly went down to one?

---

### Post by issih on 2008-07-13
Given that you seem hell bent on having Ubuntu behave in a manner as close as possible to a windows machine, may I reccomend you consider installing a kde based distro (kubuntu for example). kde is closer to windows in how it operates in terms of the start menu and a centralised control panel etc. As a general rule unreconstructed windows refugees seem more comfortable with it than gnome.

In the end though there is nothing wrong with gnome as it is, you just aren't use to it, so you don't like it. The advice to try it as it is for a while first, before tinkering, is actually very sound advice. You like many many others have grown up used to the windows way, so you think that is right, it isn't its just one way to do things. Be open minded and try things the gnome way for a while, once you come to understand what is available and how it works, you may well come to prefer it. If not, then change it (linux is hugely customisable, and it is in the end your choice). It really is worth spending a week or so trying things as they are though, yes its different, yes its uncomfortable, so what, try it you might come to like it in the long run.

I now have various computers running odd mish mashes ranging from pure gnome to one that is an odd hybrid of gnome and mac os style interfaces, and at one point I, like you, only really knew the xp way. Once you've gone as far as installing an entirely new OS, you may as well enjoy the new experiences it offers :)

P.S. your post count dropped because your threads were moved to community cafe or a similar forum... posts in those forums don't count towards your post count.

---

### Post by linfidel on 2008-07-13
> **Markissocoollike said:**
> wow you have alot of posts on this forum :P
Are you talking to yourself?  Your post is the one right before this; otherwise, there's no way to know who you are talking to.

BTW, if you think 3 days is a long time to be using linux, you have no idea how much you don't know!  :-)

I used Unix for a year or more (before WWW, to read newsgroups), and have installed about a dozen different linux distros before Ubuntu, which is the easiest to use, IMO.  Still, it took me months to reach the level of novice, and I didn't do it by wasting all my time trying to make it look like windows.

---

### Post by aktiwers on 2008-07-13
> **Markissocoollike said:**
> ...how come my posts suddenly went down to one?

Almost all your posts where moved to the Cafe, as they where not considered support requests anymore. You only get beans (post counts) in support forums and not in the Cafe. Thats why.

I once found a script that made Ubuntu look exactly like XP, I just dont seam to be able to find it right now.

---

### Post by Markissocoollike on 2008-07-13
> **linfidel said:**
> Are you talking to yourself?  Your post is the one right before this; otherwise, there's no way to know who you are talking to.

BTW, if you think 3 days is a long time to be using linux, you have no idea how much you don't know!  :-)

I used Unix for a year or more (before WWW, to read newsgroups), and have installed about a dozen different linux distros before Ubuntu, which is the easiest to use, IMO.  Still, it took me months to reach the level of novice, and I didn't do it by wasting all my time trying to make it look like windows.

obviously i was talking to the mod/administrator (they seem the same to me!) he/she has 10000+ posts which makes me impressed lol!

---

### Post by Markissocoollike on 2008-07-13
> **aktiwers said:**
> Almost all your posts where moved to the Cafe, as they where not considered support requests anymore. You only get beans (post counts) in support forums and not in the Cafe. Thats why.

I once found a script that made Ubuntu look exactly like XP, I just dont seam to be able to find it right now.

yeh I found something like that but you have to pay plus you have to reboot the new operating system which I bet takes looooong! I'm going to create my own start menu I decided just for the fun of it ^^ Looks very simple to me I could simply replace the images in vista start menu but where would the fun be in that? :P

---

### Post by aktiwers on 2008-07-13
Hey I found it..  I think it will do good with your menu. Though I will say, back when I tried this thing, it did seam to make my system as unstable as Windows XP. :(
[http://ubuntu.online02.com/node/14](http://ubuntu.online02.com/node/14)
[Just remember it deletes you panels, meaning you would have to remove this start button, and add your own again]

Before:
[IMG]http://ubuntu.online02.com/files/u_desktop.jpg[/IMG]
After:
[IMG]http://ubuntu.online02.com/files/n_desktop.jpg[/IMG]

Scary, eh?

---

### Post by LaRoza on 2008-07-13
> **Markissocoollike said:**
> ...how come my posts suddenly went down to one?

What does it matter? See the guide to forum features link in my sig to learn about beans ;)

> **Markissocoollike said:**
> obviously i was talking to the mod/administrator (they seem the same to me!) he/she has 10000+ posts which makes me impressed lol!

I am a mod. The way to get beans (although it is not what I try to do) is just to help people. I make no special efforts. There are people here with way more beans than I do.

---

### Post by Markissocoollike on 2008-07-13
> **aktiwers said:**
> Hey I found it..  I think it will do good with your menu. Though I will say, back when I tried this thing, it did seam to make my system as unstable as Windows XP. :(
[http://ubuntu.online02.com/node/14](http://ubuntu.online02.com/node/14)
[Just remember it deletes you panels, meaning you would have to remove this start button, and add your own again]

Before:
[IMG]http://ubuntu.online02.com/files/u_desktop.jpg[/IMG]
After:
[IMG]http://ubuntu.online02.com/files/n_desktop.jpg[/IMG]

Scary, eh?

yeh it is its almost like looking at a real windows bar except it isn't of course hehe

---

### Post by the_darkside_986 on 2008-07-13
Wow, that script doesn't apply everything system-wide (besides login manager) does it? I want to create a new user account just to try that script lol.

---

### Post by jerome1232 on 2008-07-13
[http://vivalinux.com.ar/desktop/ubuntu-transformation-pack.html](http://vivalinux.com.ar/desktop/ubuntu-transformation-pack.html)

now that site looks interesting time to pull an os reversal on my wife.

---

### Post by madjr on 2008-07-13
@Markissocoollike

were you able to try my suggestions ?

[http://ubuntuforums.org/showpost.php?p=5376169&postcount=52](http://ubuntuforums.org/showpost.php?p=5376169&postcount=52)

i would like to see what new users think

thanks

---

### Post by linfidel on 2008-07-13
> **aktiwers said:**
> Hey I found it..  I think it will do good with your menu. Though I will say, back when I tried this thing, it did seam to make my system as unstable as Windows XP. :( ...
Scary, eh?
Why should that make your system unstable?  It's mainly a standard gnome menu with a custom graphic button, a Windows background, and a Windows decorator.  Functionally, it's not that different than mine.  I changed the "menu bar" to a "main menu", which is the all-in-one menu.  I like it because it takes less room, and it's not really harder to drill down one more level when I need to get to the system menus.  Changing the button style wasn't particularly hard, either, although I forget where I changed it.

Personally, I like the ubuntu UI much better than Windows.  It's not that different, but I like being able to configure the panel and make it transparent, something that can't be done with Windows without running another program.

---

### Post by Mateo on 2008-07-13
> **ChameleonDave said:**
> Don't get defensive.  The very fact that you can say that I didn't "fix the issue" with Ruby on your computer shows that I am right.  The issue was that you didn't even understand what Ruby was.  That's an issue that only you can resolve.  You're claiming I don't have much experience?  Look to the left.  I have been thanked a hundred times by people whom I have helped with tech support.

But this isn't a matter of bragging about who knows what.  I'm honestly and sincerely telling you that you ought not to try customising and fiddling with your operating system at this point.  Just learn to use it.  That is what is fundamental.  Otherwise, you will be a burden to people who are donating their free time to help people use Ubuntu.  Give it a week at least.


Why don't you leave this guy alone.  If he wants to make his computer look like windows then let him make it look like windows.  When i started using gnome i put two panels on the bottom of my screen but eventually tried out the generic top/bottom format and liked it.  This guy is just trying to make things familiar.  Maybe he'll learn to like the "normal" way, maybe not.  Either way, it's his computer and if you don't want to help him then don't.  But this "try this other OS" stuff is just lousy.

---

### Post by aktiwers on 2008-07-13
> **linfidel said:**
> Why should that make your system unstable?  It's mainly a standard gnome menu with a custom graphic button, a Windows background, and a Windows decorator.  Functionally, it's not that different than mine.  I changed the "menu bar" to a "main menu", which is the all-in-one menu.  I like it because it takes less room, and it's not really harder to drill down one more level when I need to get to the system menus.  Changing the button style wasn't particularly hard, either, although I forget where I changed it.

Personally, I like the ubuntu UI much better than Windows.  It's not that different, but I like being able to configure the panel and make it transparent, something that can't be done with Windows without running another program.

Hey I do that with my menu too. I use the all-in-one, one.

But that script did make my system more unstable and I do not know why. It does create new files on the desktop (My Computer, network places .. etc..) and does delete your panels and what else it does I dont know. But it did make my install unstable when I tried it some months ago. Not that I like the Windows look, I just tested it for the fun of it.

Im pretty sure you wont get a unstable system if you apply these themes manually.

Or maybe the XP look just made me extra aware of bugs and crashes? :lolflag:

---

### Post by linfidel on 2008-07-13
> **aktiwers said:**
> Hey I do that with my menu too. I use the all-in-one, one.

But that script did make my system more unstable and I do not know why. It does create new files on the desktop (My Computer, network places .. etc..) and does delete your panels and what else it does I dont know. But it did make my install unstable when I tried it some months ago. Not that I like the Windows look, I just tested it for the fun of it.

Im pretty sure you wont get a unstable system if you apply these themes manually.

Or maybe the XP look just made me extra aware of bugs and crashes? :lolflag:
The New files like "My Computer", etc, can be enabled via the gnome configuration editor (from "system tools" menu), under "apps/nautilus/desktop".  And you can delete your panels yourself. :)
  
Seriously, I don't care if my panel looks like XP - I like the transparent panel, although I had to edit some config file to get white text, since my background is often dark - not unlike the world in general.:(

But my one concession to Windows is I have my menu button on the bottom left; I still use Windows often enough that it's easier on my brain if it's in the same place.  But most things I run have a hotkey, so I don't really use it that much.

I think you're probably right about the awareness of bugs and crashes - when I see XP, my expectations go down, too. :)

---

### Post by fatality_uk on 2008-07-13
Usually, people who have requested that I create an Ubuntu install for them, often want a single, bottom menu bar. The ("dayna" is it called?), menu bar from Linux Mint repos is a quite nice substitute , but I usually find that after a short while they feel restricted using the 7 year old XP-alike interface style.

Having that "dayna"(?) menu and moving things like window content list and some custom launchers will create the effect, but it's limiting as I say.

---

### Post by SunnyRabbiera on 2008-07-13
> **fatality_uk said:**
> Usually, people who have requested that I create an Ubuntu install for them, often want a single, bottom menu bar. The ("dayna" is it called?), menu bar from Linux Mint repos is a quite nice substitute , but I usually find that after a short while they feel restricted using the 7 year old XP-alike interface style.

Having that "dayna"(?) menu and moving things like window content list and some custom launchers will create the effect, but it's limiting as I say.

Its called the mintmenu actually.

---

### Post by fatality_uk on 2008-07-13
> **SunnyRabbiera said:**
> Its called the mintmenu actually.

Which is why I stuck a question mark round it ;)

---

### Post by Markissocoollike on 2008-07-13
> **madjr said:**
> @Markissocoollike

were you able to try my suggestions ?

[http://ubuntuforums.org/showpost.php?p=5376169&postcount=52](http://ubuntuforums.org/showpost.php?p=5376169&postcount=52)

i would like to see what new users think

thanks

I wasn't really interested in your device even though it does that it kinda seems pointless having two menus which do just about the same thing if you know what I mean ;)

---

### Post by Markissocoollike on 2008-07-13
> **Mateo said:**
> Why don't you leave this guy alone.  If he wants to make his computer look like windows then let him make it look like windows.  When i started using gnome i put two panels on the bottom of my screen but eventually tried out the generic top/bottom format and liked it.  This guy is just trying to make things familiar.  Maybe he'll learn to like the "normal" way, maybe not.  Either way, it's his computer and if you don't want to help him then don't.  But this "try this other OS" stuff is just lousy.

respect dude... respect! *nods head in acknowledgment* Yeh I've heard of non computer geeks usually complaining about how computer geeks say you haven't given this thing a chance they usually give up and say that's what everyone says... but you are so much different from that I'm glad theres more people like me around these forums ^^

---

### Post by Markissocoollike on 2008-07-13
> **linfidel said:**
> The New files like "My Computer", etc, can be enabled via the gnome configuration editor (from "system tools" menu), under "apps/nautilus/desktop".  And you can delete your panels yourself. :)
  
Seriously, I don't care if my panel looks like XP - I like the transparent panel, although I had to edit some config file to get white text, since my background is often dark - not unlike the world in general.:(

But my one concession to Windows is I have my menu button on the bottom left; I still use Windows often enough that it's easier on my brain if it's in the same place.  But most things I run have a hotkey, so I don't really use it that much.

I think you're probably right about the awareness of bugs and crashes - when I see XP, my expectations go down, too. :)

All that really needs changing is the run directory it should be changed to the terminal so it's easier to access that's my advice on the topic anyway!

---

### Post by Markissocoollike on 2008-07-13
> **fatality_uk said:**
> Usually, people who have requested that I create an Ubuntu install for them, often want a single, bottom menu bar. The ("dayna" is it called?), menu bar from Linux Mint repos is a quite nice substitute , but I usually find that after a short while they feel restricted using the 7 year old XP-alike interface style.

Having that "dayna"(?) menu and moving things like window content list and some custom launchers will create the effect, but it's limiting as I say.

if only there was an easier way of running the applications than to run them through wine...

---

### Post by fatality_uk on 2008-07-13
> **Markissocoollike said:**
> if only there was an easier way of running the applications than to run them through wine...

WINE? What would I need WINE for?

---

### Post by clanky on 2008-07-13
> **Markissocoollike said:**
> if only there was an easier way of running the applications than to run them through wine...

There is... Windows.  If you want to run windows applications and have a windows start menu why not just dual boot with windows?

---

### Post by madjr on 2008-07-13
> **Markissocoollike said:**
> All that really needs changing is the run directory it should be changed to the terminal so it's easier to access that's my advice on the topic anyway!

Run is **Alt + F2**

---

### Post by madjr on 2008-07-13
> **clanky said:**
> There is... Windows.  If you want to run windows applications and have a windows start menu why not just dual boot with windows?

well in linux you can do everything you want.

and thats the point of having wine + many types of menus.

linux adjusts to you as you adjust to it.

also i use AWN dock, that doesn't mean i want to be in macOS

anyway you got to give the fella a **month** for him to get used to everything, i did the same

once you replicate something or archive a "look" you then lose interest and want to try new things

when i replicated Vista i soon lost interest in that look

then i made XP and Vista look like ubuntu :)

---

### Post by Markissocoollike on 2008-07-13
> **clanky said:**
> There is... Windows.  If you want to run windows applications and have a windows start menu why not just dual boot with windows?

*bangs head against wall* I - BANG! - DON'T - BANG! - WANT! - BANG! - WINDOWS - BANG! - CRUMMY - BANG! - OS!

---

### Post by SunnyRabbiera on 2008-07-13
> **Markissocoollike said:**
> if only there was an easier way of running the applications than to run them through wine...

well wine is getting better by the version, but if you need a "easy" wine use crossover, its not free but does a decent job.
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Riffer on 2008-07-13
> **Markissocoollike said:**
> *bangs head against wall* I - BANG! - DON'T - BANG! - WANT! - BANG! - WINDOWS - BANG! - CRUMMY - BANG! - OS!

Ok I'll bite.  You don't like windows, yet you want to make your desktop look like windows, why?

---

### Post by fatality_uk on 2008-07-13
> **Riffer said:**
> Ok I'll bite.  You don't like windows, yet you want to make your desktop look like windows, why?

Is biting against the Code Of Conduct? :lol:

---

### Post by linfidel on 2008-07-13
> **fatality_uk said:**
> WINE? What would I need WINE for?
A glass or two helps put this discussion into perspective! :)

---

### Post by Markissocoollike on 2008-07-13
Because I prefer the windows version so that you don't have so many menus hogging space on the panel, however I've already found something suitable for it, now all I need is a better way to access my windows and I'll have the "ultimate linux" but lets not get carried away here I don't know whether or not there are better versions of linux than ubuntu but it seems to be going smoothly for me after all that hassle just wish'd it was easier to use :(

---

### Post by Markissocoollike on 2008-07-13
> **fatality_uk said:**
> Is biting against the Code Of Conduct? :lol:

In a boxing match yes in an electronic forum where your imagination runs free defiantly not!

---

### Post by Riffer on 2008-07-13
> **Markissocoollike said:**
> Because I prefer the windows version so that you don't have so many menus hogging space on the panel, however I've already found something suitable for it, now all I need is a better way to access my windows and I'll have the "ultimate linux" but lets not get carried away here I don't know whether or not there are better versions of linux than ubuntu but it seems to be going smoothly for me after all that hassle just wish'd it was easier to use :(

Really!  I find the standard lay out to be quite straight forward and quick.  I like having things at my finger tips so to speak.  I find the window way is having things buried 3 or 4 clicks away to be a bit frustrating.  To each their own I suppose.

After 14 years with all versions of windows, I found Linux/Ubuntu to be strange at first.  It took me a month before I really started to feel comfortable with how "things were done".  And in the end I find the standard Gnome Desktop to much more intuitive.

The beauty of Gnome is that you can set up YOUR desktop anyway you feel like.  I 'm sure many wouldn't like my basic look.  So enjoy tweaking yours.

---

### Post by linfidel on 2008-07-13
> **Markissocoollike said:**
> Because I prefer the windows version so that you don't have so many menus hogging space on the panel, however I've already found something suitable for it, now all I need is a better way to access my windows and I'll have the "ultimate linux" but lets not get carried away here I don't know whether or not there are better versions of linux than ubuntu but it seems to be going smoothly for me after all that hassle just wish'd it was easier to use :(For your sake, I hope English is not your native language - it's often hard to interpret your posts.

But if you are trying to save space on the panel, you can make a couple of easy, standard gnome changes.  
1.  Delete the "Menubar" and add a "Main Menu".  The Main menu is much more space efficient, by putting the other two menus at the bottom of the main menu.
2.  Remove the "Window List" and add a "Window Selector".  The window selector give you a pop-up menu of you windows, instead of individual buttons for each window.

You might try getting a panel app called "Gimmie", which gives you a host of features in a fairly small amount of space.

HTH.

---

### Post by Markissocoollike on 2008-07-14
> **linfidel said:**
> For your sake, I hope English is not your native language - it's often hard to interpret your posts.

But if you are trying to save space on the panel, you can make a couple of easy, standard gnome changes.  
1.  Delete the "Menubar" and add a "Main Menu".  The Main menu is much more space efficient, by putting the other two menus at the bottom of the main menu.
2.  Remove the "Window List" and add a "Window Selector".  The window selector give you a pop-up menu of you windows, instead of individual buttons for each window.

You might try getting a panel app called "Gimmie", which gives you a host of features in a fairly small amount of space.

HTH.

I already did that if you were reading what I had said you would had realized that I made my own windows vista menu :P

---

### Post by fatality_uk on 2008-07-14
> # Total Posts: 4
# Posts Per Day: 141
Just tell me if theres anything wrong with those last sentences ^^ 
You missed your decimal point ;)

---

### Post by madjr on 2008-07-14
@Markissocoollike

can you attach a pic of your desktop when you are done.

---

### Post by Markissocoollike on 2008-07-14
> **madjr said:**
> @Markissocoollike

can you attach a pic of your desktop when you are done.

umm k! But I'm still editing icons on the start menu they have gone a bit dodged :P

---

### Post by LaRoza on 2008-07-14
> **fatality_uk said:**
> Is biting against the Code Of Conduct? :lol:

I don't see it, so I guess it isn't :-)

---

### Post by Markissocoollike on 2008-07-14
> **LaRoza said:**
> I don't see it, so I guess it isn't :-)

mine was funnier :P

---

### Post by LaRoza on 2008-07-14
> **Markissocoollike said:**
> mine was funnier :P

I was serious.

---

### Post by Markissocoollike on 2008-07-14
> **LaRoza said:**
> I was serious.

Well you didn't need to be it was a rhetorical question :P

---

### Post by Markissocoollike on 2008-07-14
> **fatality_uk said:**
> You missed your decimal point ;)

but then that would confuse people you would then be mistaking it as 1.41 instead of 141 :P

---

### Post by Markissocoollike on 2008-07-14
sides I can barely even see the decimal point in the last sentence XD

---

### Post by fatality_uk on 2008-07-14
> **Markissocoollike said:**
> sides I can barely even see the decimal point in the last sentence XD

Because you never placed it there! :|

---

### Post by Markissocoollike on 2008-07-14
> **fatality_uk said:**
> Because you never placed it there! :|

On the contrary my dear Watson! If you highlight it you can just see it even though its really small, ill try a space to make it clearer 

1.41 1 .41

---

### Post by Markissocoollike on 2008-07-14
the problem is the "1" makes it look as if its camouflaged perhaps the forums admin should change the default font of this decimal point :P

---

### Post by fatality_uk on 2008-07-14
> **Markissocoollike said:**
> the problem is the "1" makes it look as if its camouflaged perhaps the forums admin should change the default font of this decimal point :P

Oh I agree. Perhaps you should suggest it ;)
I looked and found an email for you
[email]ihaveasuggestionaboutdecimalpointsizesonubuntuforum@canonical.com[/email] :lol:

---

### Post by Markissocoollike on 2008-07-14
> **fatality_uk said:**
> Oh I agree. Perhaps you should suggest it ;)
I looked and found an email for you
[email]ihaveasuggestionaboutdecimalpointsizesonubuntuforum@canonical.com[/email] :lol:

thanks ill email him

---

### Post by Markissocoollike on 2008-07-14
heeeeey... wait a minute did you make that email up?

---

### Post by Markissocoollike on 2008-07-14
Don't do that lol you confused me!

---

### Post by Scotty Bones on 2008-07-14
I don't think the point here is to make linux look like windows; but rather, to have a menu that looks at least half descent.  lets face it, gnome's menu is just plain ugly (so too for KDE and mintmenu for that matter).  The **look** is too plain and simplistic, almost Amish-like. It really is a sore thumb to a modern, stylish OS.  The appeal to the windows-like menu is strictly visual. Call me vain if you like, but I prefer things to be as visually appealing as they are functional.  

[personal rant]
It's the one thing that I find to be lacking in this OS's desktop that really seems to annoy the heck out of me.  I don't think it should look exactly like windows; what would be the point to that, we need something distinctive that sets us apart.  However, it does need visual appeal.  Every time I look at that menu, I feel like I'm in the stone-age of computing.

---

### Post by clanky on 2008-07-14
> **Markissocoollike said:**
> *bangs head against wall* I - BANG! - DON'T - BANG! - WANT! - BANG! - WINDOWS - BANG! - CRUMMY - BANG! - OS!

Why is it crummy, you were complaining that there isn't a better way than wine to run windows applications in Linux, but windows runs them without any problems what is so crummy about that?

I am assuming from the fact that your join date on these forums is July '08 you have been using ubuntu for roughly a month, so why do you feel that it is necessary to bitch about windows?  It's not big, it's not clever and no-one's impressed.

---

### Post by Markissocoollike on 2008-07-14
> **Scotty Bones said:**
> I don't think the point here is to make linux look like windows; but rather, to have a menu that looks at least half descent.  lets face it, gnome's menu is just plain ugly (so too for KDE and mintmenu for that matter).  The **look** is too plain and simplistic, almost Amish-like. It really is a sore thumb to a modern, stylish OS.  The appeal to the windows-like menu is strictly visual. Call me vain if you like, but I prefer things to be as visually appealing as they are functional.  

[personal rant]
It's the one thing that I find to be lacking in this OS's desktop that really seems to annoy the heck out of me.  I don't think it should look exactly like windows; what would be the point to that, we need something distinctive that sets us apart.  However, it does need visual appeal.  Every time I look at that menu, I feel like I'm in the stone-age of computing.

Amen to that!

---

### Post by Markissocoollike on 2008-07-14
> **clanky said:**
> Why is it crummy, you were complaining that there isn't a better way than wine to run windows applications in Linux, but windows runs them without any problems what is so crummy about that?

I am assuming from the fact that your join date on these forums is July '08 you have been using ubuntu for roughly a month, so why do you feel that it is necessary to bitch about windows?  It's not big, it's not clever and no-one's impressed.

okay windows is crummy because it is slow, it has low security against viruses, BSOD (need I say more), Linux is fully editable as I've just changed the menu to my liking, I don't like having to boot every time I want to run a windows program and loads of people will say the same, I'm not bitching about windows (sorry for swearing as I don't normally do that!) it's just that now I've got a better version of it I don't see any reason to revert to it although all those points are obvious so why you asking me I do not know and I've only been using this os for 3 days now and 20 more minutes will make it 4 lol! I don't know why you think i'm bitching about it when i just don't want to boot to windows every two seconds which would be very annoying.

---

### Post by madjr on 2008-07-14
> **Scotty Bones said:**
> I don't think the point here is to make linux look like windows; but rather, to have a menu that looks at least half descent.  lets face it, gnome's menu is just plain ugly (so too for KDE and mintmenu for that matter).  The **look** is too plain and simplistic, almost Amish-like. It really is a sore thumb to a modern, stylish OS.  The appeal to the windows-like menu is strictly visual. Call me vain if you like, but I prefer things to be as visually appealing as they are functional.  

[personal rant]
It's the one thing that I find to be lacking in this OS's desktop that really seems to annoy the heck out of me.  I don't think it should look exactly like windows; what would be the point to that, we need something distinctive that sets us apart.  However, it does need visual appeal.  Every time I look at that menu, I feel like I'm in the stone-age of computing.

amen to that too

**Raptor menu**:

[http://raptor-menu.org/](http://raptor-menu.org/)

but thats for the [COLOR="Olive"]**bottom**[/COLOR] menu

now, for the [COLOR="RoyalBlue"]**top**[/COLOR] menu i love my **normal gnome menu**, just needs a better theme

check it out:

[IMG]http://gnome-look.org/CONTENT/content-m1/m71993-1.png[/IMG]
[http://gnome-look.org/content/preview.php?preview=1&id=71993&file1=71993-1.jpg&file2=71993-2.jpg&file3=71993-3.jpg&name=SlicknesS](http://gnome-look.org/content/preview.php?preview=1&id=71993&file1=71993-1.jpg&file2=71993-2.jpg&file3=71993-3.jpg&name=SlicknesS)

now **that** has style

---

### Post by Jim! on 2008-07-14
> **Markissocoollike said:**
> okay windows is crummy because it is slow, it has low security against viruses, BSOD (need I say more), Linux is fully editable as I've just changed the menu to my liking, I don't like having to boot every time I want to run a windows program and loads of people will say the same, I'm not bitching about windows (sorry for swearing as I don't normally do that!) it's just that now I've got a better version of it I don't see any reason to revert to it although all those points are obvious so why you asking me I do not know and I've only been using this os for 3 days now and 20 more minutes will make it 4 lol! I don't know why you think i'm bitching about it when i just don't want to boot to windows every two seconds which would be very annoying.

All of your posts are very contradictory. I think clanky makes a good point, one minute Ubuntu is great but you wish it "was more like windows" the next minute your talking about the BSOD. I definitely think Ubuntu is better then Windows (personal preference) but in reality there both very good Operating Systems and Windows even has many advantages over Ubuntu (as does Ubuntu over XP). As for the BSOD, don't be so quick to think Ubuntu doesn't experience a similar problem.

---

### Post by Markissocoollike on 2008-07-14
> **Jim! said:**
> All of your posts are very contradictory. I think clanky makes a good point, one minute Ubuntu is great but you wish it "was more like windows" the next minute your talking about the BSOD. I definitely think Ubuntu is better then Windows (personal preference) but in reality there both very good Operating Systems and Windows even has many advantages over Ubuntu (as does Ubuntu over XP). As for the BSOD, don't be so quick to think Ubuntu doesn't experience a similar problem.

I was mainly focused on the windows menu but whatever its your opinion

---

### Post by Markissocoollike on 2008-07-14
> **madjr said:**
> amen to that too

**Raptor menu**:

[http://raptor-menu.org/](http://raptor-menu.org/)

but thats for the [COLOR="Olive"]**bottom**[/COLOR] menu

now, for the [COLOR="RoyalBlue"]**top**[/COLOR] menu i love my **normal gnome menu**, just needs a better theme

check it out:

[IMG]http://gnome-look.org/CONTENT/content-m1/m71993-1.png[/IMG]
[http://gnome-look.org/content/preview.php?preview=1&id=71993&file1=71993-1.jpg&file2=71993-2.jpg&file3=71993-3.jpg&name=SlicknesS](http://gnome-look.org/content/preview.php?preview=1&id=71993&file1=71993-1.jpg&file2=71993-2.jpg&file3=71993-3.jpg&name=SlicknesS)

now **that** has style

well it looks cool but unfortunately its still based around three tabs which I don't really like i'm afraid sorry but i'm still gonna stick with mine ^^

---

### Post by jonian_g on 2008-07-14
> As for the BSOD, don't be so quick to think Ubuntu doesn't experience a similar problem.

I'm not sure what you mean by that. If you mean that your computer doesn't respond then you can press Ctrl+Alt+Backspace and then login again. Though it never had happen to me.
Even if Ubuntu had something like that then it would be OSOD. First O is for orange :)

> I am assuming from the fact that your join date on these forums is July '08 you have been using ubuntu for roughly a month

Join date doesn't mean that someone is using ubuntu for that long. That would mean I use ubuntu for 6 months but I'm an ubuntu user for about 2 years.

---

### Post by Jim! on 2008-07-14
Do you mind sharing what your reason for switching to Ubuntu from Windows was in the first place?

---

### Post by Jim! on 2008-07-14
> **jonian_g said:**
> I'm not sure what you mean by that. If you mean that your computer doesn't respond then you can press Ctrl+Alt+Backspace and then login again. Though it never had happen to me.
I'm not talking about the X-server crashing I'm talking about Ubuntu's tendency to experience kernel panics - It seems it's a common occurrence these days. ([http://en.wikipedia.org/wiki/Kernel_Panic](http://en.wikipedia.org/wiki/Kernel_Panic))

> **jonian_g said:**
> Even if Ubuntu had something like that then it would be OSOD. First O is for orange :)
Clever;)

---

### Post by jonian_g on 2008-07-14
Never happen to me... Thanks for sharing the info though

---

### Post by Jim! on 2008-07-14
No worries;) Ubuntu has not once experienced a kernel panic on me either. In my experience it appears to be quite a stable OS.

---

### Post by clanky on 2008-07-15
If ctrl alt del doesn't work then try holding ctrl+alt+prt scrn and type REISUB (busier backwards)  Sometimes this works when ctrl-alt-del doesn't.

I found gutsy quite unstable, but since upgrading to hardy I haven't had any problems, many problems with stability seem to be hardware related, but the same is often the case with windows.

---

### Post by zipperback on 2008-07-15
> **Markissocoollike said:**
> Besides it would be better if linux was more like windows

Linux IS NOT Windows. It isn't intended to be like Windows. Linux is Linux, and there isn't any reason why it should be anything else.

I'm sorry, but I hear that all the time from people "why can't it be more like windows?"




- zipperback
:popcorn:

---

### Post by Jim! on 2008-07-15
> **zipperback said:**
> Linux IS NOT Windows. It isn't intended to be like Windows. Linux is Linux, and there isn't any reason why it should be anything else. Damn straight!:popcorn: If you want something "more like Windows" then use Windows.

---

### Post by jonian_g on 2008-07-15
Or use ReactOS, if it ever gets ready. Linux is linux and we are using it because we don't like Windows.

---

### Post by clanky on 2008-07-15
Speak for yourself, I am using it for a variety of reasons, none of them are anything to do with not liking windows.

---

### Post by madjr on 2008-07-15
> **zipperback said:**
> Linux IS NOT Windows. It isn't intended to be like Windows. Linux is Linux, and there isn't any reason why it should be anything else.

I'm sorry, but I hear that all the time from people "why can't it be more like windows?"




- zipperback
:popcorn:

exactly is like wanting to make the **TUX** penguin look like the **MSN butterfly**

now that would be **personal** !

---

### Post by jonian_g on 2008-07-15
Ok... Sorry if you got offended. So I'm speaking for me and others that have only linux on their pc.

---

### Post by lazertek on 2008-07-15
Everybody has their own reasons...

Some use it because they don't like windows and others because linux gives them the power windows can't but because you use linux even as you main OS doesn't have to mean you hate it...

I personally use linux as my main OS (ubuntu specifically) and yes I think linux is better than windows... Only problem is everybody doesn't that's why there are these controversies... 

If everybody used linux and devolped for linux i'm sure you all would agree things would be more stable and would have worked better....

---

### Post by jonian_g on 2008-07-15
> Some use it because they don't like windows and others because linux gives them the power windows can't but because you use linux even as you main OS doesn't have to mean you hate it...

When I say I don't like windows, I don't mean I hate them. I mean that I don't prefer them and since I can do what I need to do with linux. Don't need Photoshop, GIMP does the jod for me. Don't need Illustrator, Incscape has what I need. Don't need Dreamweaver, Kompozer does my job. Don't need many games, the ones I play can play with wine and I'm planning to get a PS2 because I don't want to pay 300-400 euros to get the newest nvidia to play the latest games, the video tools do what I want them to do (rip, split, join, convert, avi to dvd).
In other words the alternatives of the windows programs that I used, satisfy me + I have a stable os that doesn't need a nurse + my hardware doesn't need a stiker to confirm that I can run my os on it.
Thats why I don't prefer windows and that's why they don't have a place in my hard drive. When I buy a new cellphone that doesn't mean I hate the old one but I prefer the new one because it's better.

PS. I agree with the rest you said

---

### Post by lazertek on 2008-07-16
I have to admit though programs such as photoshop are unbeatable atm... Gimp is an ok alternative but not good enough at a very productive level... Wish photoshop had better support for linux...

---

### Post by olhat on 2008-09-03
> **Markissocoollike said:**
> okay I found a vista like start menu it's located here: [http://linux.softpedia.com/progDownload/Vista-like-Start-Menu-Download-33794.html](http://linux.softpedia.com/progDownload/Vista-like-Start-Menu-Download-33794.html)
once downloaded extract to desktop follow the read me in the extracted file if you are unsure of what to do and there ya go! the only thing I hate about it is that theres a little black box that sticks out... but whatever yay! Now all I need to do is add window shortcuts!

Here's an upgrade:
[http://www.gnome-look.org/content/do...=1&tan=4461126](http://www.gnome-look.org/content/do...=1&tan=4461126)


I liked the look of that one but when I try to install it there must be some kind of problem.  The process seems to go fine until I'm asked for my password.  After that the process just vanishes.  No error messages no nothing.  There seems to be no info in the internet over this. I run Ubuntu 8.04 that has or has not all the necessary libraries etc. installed. 

What is the command to run this "Vista-like..." on Gnome desktop so as to see if it exists in my computer at all.:confused:

---

### Post by Chame_Wizard on 2008-09-03
stick it with Linux :popcorn:

---

### Post by Malac on 2008-09-03
> **olhat said:**
> What is the command to run this "Vista-like..." on Gnome desktop so as to see if it exists in my computer at all.:confused:
Right-click on panel, choose Add to panel, scroll down to Vista-Menu (or something like that) then click Add.

Hope this helps.

---

