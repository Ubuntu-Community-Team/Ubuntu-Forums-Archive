---
title: "Tips for improvement"
date: 2008-02-04
forum: Testimonials &amp; Experiences
---

### Post by mikasjoman on 2008-02-04
Hi

Since the Ubuntu mission is to create a Linux for human beings, I think that Gutsy took a big step forward to that.

I have now completed about 7 installations on my friends computers, and they love what they have now. But, as totally new to Linux I would like to give you a big tip for improvement.

1. GRUB scares the **** out of my girl friend.
Its ugly, and it looks like ****. Compare it to my mac, that uses EFI to start up with nice symbols, can that be possible for Hardy? Its a bad "start" so to say when the door to Ubuntu looks scary.

2. New users to Ubuntu hate the Terminal
Its like going back to the 90-s for them. Since XP they are totally used never going back to DOS, so why should we force them with the Terminal? Installing AWN on their computer got some scary eyes. Of course hard core linux experts has to have it, but not the average user. Like apple says, they should not even be aware of its existence of the Linux underneath. 

3. Can Ubuntu go out with a new message to the developers?
When creating Apps for Hardy, please don't ask people to add lines to the repository, get it done inside a .install file and attach a nice vector graphics icon to it. It can´t be that difficult and it would make the user experience ten times nicer.

4. Change that ugly brow-sickish color theme
Brow aganist black and white is just wrong in menus. I don't say copy Mac/win, but please use a color with contrast. Try a mac and you understand in two seconds what I mean.

5. Get ALL the updates to download automatically
For a normal user, we just want the computer updated. And please, while dowloading 198 updates, don't lock me out of installing other software. In china where I am, the connection can go down to 10K a second, and that means that If i push the download updates, Ill be locked out of installing things for a LONG time. Don't think Europe high speed lines exist everywhere.

6. Its all about lowering the bar
Well, I have seen many nice things in the Hardy list, but is it getting through to the developers? Why don´t I see join the Ubuntu army on the ubuntu front page? To get developers going, goal focused, it should be one click away from the front page or under a top "developer" page to see how weI can contribute.
Why not a full list of the Hardy projects, where you see what has to be done. Then attach yourself to that project? I am learning python now, but I have no clue on how to get going with helping out.
The best people I have ever seen doing this is Mozilla with their songbird. They are SUPER goal oriented, and they understand how to get people to help out in different knowledge levels.

Thanks for a great operating system!

Sincerely yours

---

### Post by smartboyathome on 2008-02-04
1. GRUB can be made to look nicer with GFXBoot, but other than that there hasn't been anything with images to boot (which I would be glad for).
2. I think that while SOME things can be done without touching the terminal, some things are faster done in it. Also, I don't think Mac's model is the best to follow, simply because they are more of a "do what we want you to do, but don't do what we don't want you to do" operating system.
3. This was discussed, but it would use the app included with Gutsy called "apturl" instead of a special file. It was decided not to do this, though, because it would be too much of a security risk.
4. This has gone on many times over, and Ubuntu will probably never change it from brown. Brown CAN look good if used right though (look at companies like hershy's and reses).
5. You have to be locked out of installing stuff because it would be dangerous to install two things when they don't know about each other. APT just doesn't work like that.
6. It is kind of late to be helping out with Hardy since it will be released in a couple months, but I would say try checking launchpad for some bugs you can triage to make it more stable.

---

### Post by atoponce on 2008-02-04
> **mikasjoman said:**
> Hi

Since the Ubuntu mission is to create a Linux for human beings, I think that Gutsy took a big step forward to that.

I have now completed about 7 installations on my friends computers, and they love what they have now. But, as totally new to Linux I would like to give you a big tip for improvement.

1. GRUB scares the **** out of my girl friend.
Its ugly, and it looks like ****. Compare it to my mac, that uses EFI to start up with nice symbols, can that be possible for Hardy? Its a bad "start" so to say when the door to Ubuntu looks scary.

What is your girlfriend doing editing GRUB?  Maybe you could be more specific as to what exactly is "scary".

> 2. New users to Ubuntu hate the Terminal
Its like going back to the 90-s for them. Since XP they are totally used never going back to DOS, so why should we force them with the Terminal? Installing AWN on their computer got some scary eyes. Of course hard core linux experts has to have it, but not the average user. Like apple says, they should not even be aware of its existence of the Linux underneath. Welcome to the world of Linux.  Fortunately, the terminal will be staying, and the average user should get used to it.  Just because some software vendor took several steps backwards away from the terminal, doesn't mean we all have to follow the same fate.

> 3. Can Ubuntu go out with a new message to the developers?
When creating Apps for Hardy, please don't ask people to add lines to the repository, get it done inside a .install file and attach a nice vector graphics icon to it. It can´t be that difficult and it would make the user experience ten times nicer.There should be no reason why you need to edit your /etc/apt/sources.list file.  If you are adding extra repositories, then you aren't aware of what is available to you in the default repos.  However, I have never seen an application that asks the user to add repositories.

> 4. Change that ugly brow-sickish color theme
Brow aganist black and white is just wrong in menus. I don't say copy Mac/win, but please use a color with contrast. Try a mac and you understand in two seconds what I mean.This the human theme that you are referring to.  Don't like it?  Change it to something else.  Maybe the Clearlooks theme is more your taste.  This is all opinion, and many people like it, while many don't.  Besides, this is open source software.  If it really bothers you that bad, then recompile the source that Ubuntu is built on, with your own theme.

> 5. Get ALL the updates to download automatically
For a normal user, we just want the computer updated. And please, while dowloading 198 updates, don't lock me out of installing other software. In china where I am, the connection can go down to 10K a second, and that means that If i push the download updates, Ill be locked out of installing things for a LONG time. Don't think Europe high speed lines exist everywhere.That's not a good idea, if you think about it.  What happens when someone is behind dialup?  Do you think that they want their updates coming down the pipe automatically, when they are answering an email, or surfing the web?  What if they are behind a T1 at work, and the automatic updates usurps the entire bandwidth?  Do you think their coworkers will be happy that the Internet is slow?  Of course not.  Updates should notify the user by default, but not download them by default.  Also, if you don't want to update 198 updates, then don't.  No one is forcing you.  Finally, when updates are being applied to the system, config files are changing, directories are being updated, and the dpkg database is being modified.  Of course it makes sense to have only one application taking the focus.  Doing anything other than that could cause disaster to your system.

> 6. Its all about lowering the bar
Well, I have seen many nice things in the Hardy list, but is it getting through to the developers? Why don´t I see join the Ubuntu army on the ubuntu front page? To get developers going, goal focused, it should be one click away from the front page or under a top "developer" page to see how weI can contribute.
Why not a full list of the Hardy projects, where you see what has to be done. Then attach yourself to that project? I am learning python now, but I have no clue on how to get going with helping out.
The best people I have ever seen doing this is Mozilla with their songbird. They are SUPER goal oriented, and they understand how to get people to help out in different knowledge levels.I don't understand this point, but I think you're trying to say that the Ubuntu developers need to change the way they are developing the distro?  Ubuntu is the hottest Linux distro on the planet.  Please explain to me what's wrong.  Further, I think you're confusing the application developers that Ubuntu is getting the software from with the Ubuntu developers that are responsible for compiling and packaging the distro.[/quote]

---

### Post by mikewhatever on 2008-02-04
> 1. GRUB scares the **** out of my girl friend.
Its ugly, and it looks like ****. Compare it to my mac, that uses EFI to start up with nice symbols, can that be possible for Hardy? Its a bad "start" so to say when the door to Ubuntu looks scary.

When does your girlfriend get to see GRUB, let along configure it? The default timeout is set to 3 secs, so what gives.

> 2. New users to Ubuntu hate the Terminal
Its like going back to the 90-s for them. Since XP they are totally used never going back to DOS, so why should we force them with the Terminal? Installing AWN on their computer got some scary eyes. Of course hard core linux experts has to have it, but not the average user. Like apple says, they should not even be aware of its existence of the Linux underneath.

I started using Ubuntu not too long ago, and do not remember hating terminal, so don't generalize. Terminal is a very efficient tool, but you don't have to use it. Why would you hate something you do not use?

> 3. Can Ubuntu go out with a new message to the developers?
When creating Apps for Hardy, please don't ask people to add lines to the repository, get it done inside a .install file and attach a nice vector graphics icon to it. It can´t be that difficult and it would make the user experience ten times nicer.

Ubuntu has file sources, take it or leave it. I think you are looking for a Windows way of doing things, completely forgetting that Ubuntu is Linux.

> 4. Change that ugly brow-sickish color theme
Brow aganist black and white is just wrong in menus. I don't say copy Mac/win, but please use a color with contrast. Try a mac and you understand in two seconds what I mean.

I may seem odd, but I kind of like the default theme. It's totally OK that you don't, go ahead and change it yourself.

> 5. Get ALL the updates to download automatically
For a normal user, we just want the computer updated. And please, while dowloading 198 updates, don't lock me out of installing other software. In china where I am, the connection can go down to 10K a second, and that means that If i push the download updates, Ill be locked out of installing things for a LONG time. Don't think Europe high speed lines exist everywhere.

You are contradicting yourself. Some users may not want updates at all, while others may want to choose what to update. Lastly, if your internet is slow, simply do not push the update icon if you know you want to install programs.

> 6. Its all about lowering the bar
Well, I have seen many nice things in the Hardy list, but is it getting through to the developers? Why don´t I see join the Ubuntu army on the ubuntu front page? To get developers going, goal focused, it should be one click away from the front page or under a top "developer" page to see how weI can contribute.
Why not a full list of the Hardy projects, where you see what has to be done. Then attach yourself to that project? I am learning python now, but I have no clue on how to get going with helping out.
The best people I have ever seen doing this is Mozilla with their songbird. They are SUPER goal oriented, and they understand how to get people to help out in different knowledge levels.

Do forgive me, but I was not aware an Ubuntu army existed. I got the impression that you really like to be spoonfed, don't you.

---

### Post by groupmsl on 2008-02-04
I personally like the > ugly brow-sickish theme of ubuntu, but maybe if a large number of people dont like it, the developers could include 2 themes with the default installation of Ubuntu?

---

### Post by mikasjoman on 2008-02-05
Well I guess I deserved that one ;)

The colors of Ubuntu, well that is just a research issue. Not a "what I like, you like issue".

Same thing with the terminal. But the terminal does one thing, it adds to the complexity for new users to learn. I don't want to take it away, I just think it could be used less. Just installing awn for the first time took me long time to figure out (and it does tell me to add repositories).

I studied a great deal of polling, since I studied political science. I wonder if Ubuntu-poll.com could be something? The hard core Linux users can not really add to the understanding of new users since the apparently "like" the terminal - and it makes them more efficient.
 If we could get data from say 10.000+ users on their issues/preferences we could break down what is urgent to be fixed and what people really need to get fixed. Could this allocate resources more efficient?

And, since my posting was written as a "here is my newbie issues and tips", think about how some of you answered me. New people here seek advice and  come here to give their point of view (since they are asked for it in this category - their views are never wrong - just different from yours).

cheers!

---

### Post by bbqsandwich on 2008-02-05
> **groupmsl said:**
> I personally like the  theme of ubuntu, but maybe if a large number of people dont like it, the developers could include 2 themes with the default installation of Ubuntu?

Forgive my newbishness, but doesn't Ubuntu include several themes? Clearlooks... Mist... Crux...? Etc.? 

Or am I installing those in an update right away and merely assuming that they come with a fresh install?

---

### Post by smartboyathome on 2008-02-05
Other themes are included by default.

---

### Post by mikewhatever on 2008-02-05
> **bbqsandwich said:**
> Forgive my newbishness, but doesn't Ubuntu include several themes? Clearlooks... Mist... Crux...? Etc.? 

Or am I installing those in an update right away and merely assuming that they come with a fresh install?

Total 8 themes are pre-installed and ready to use, but I think Mr. Never Wrong wants the default one changed. A wild guess, but I'd bet it's blue he fancies.

---

### Post by blairbeckwith on 2008-02-05
> **mikewhatever said:**
> Total 8 themes are pre-installed and ready to use, but I think Mr. Never Wrong wants the default one changed. A wild guess, but I'd bet it's blue he fancies.

That's kinda harsh...

---

### Post by wolfen69 on 2008-02-05
> 1. GRUB scares the **** out of my girl friend.
priceless. :lolflag:

---

### Post by Tuxoid on 2008-02-05
honestly, people have gotta stop by default telling people to use the terminal. Ya, the terminal is here to stay, but the terminal is going to scare the average-user away. I don't care how "easy" people say it is, the average user will always have the preconceived notion thats its hard. Don't ever tell anyone to do something in the terminal unless they don't mind. At least before telling them how to do something in the terminal, give them the GUI alternative. Ubuntu was designed to be targeted for average-users, not nerds.

---

### Post by wolfen69 on 2008-02-05
if copying and pasting commands once in a blue moon is difficult and scary, then people shouldnt use it. then again, there are distros like mint and pclinuxos where you almost never have to use the command line. 

i'll gladly use the cli once in a while if it means not having bsod's, virii, spyware, and activation schemes. i dont think most people will have a problem with actually having to learn a little. that's what makes linux what it is. it has a personality all its own, and should stay this way. 

i personally dont care if Joe Shmoe finds linux difficult and goes running back to windows. i find it perfect as is. linux is growing by leaps and bounds everyday, and is here to stay.

---

### Post by mikewhatever on 2008-02-06
> **Tuxoid said:**
> honestly, people have gotta stop by default telling people to use the terminal. Ya, the terminal is here to stay, but the terminal is going to scare the average-user away. I don't care how "easy" people say it is, the average user will always have the preconceived notion thats its hard. Don't ever tell anyone to do something in the terminal unless they don't mind. At least before telling them how to do something in the terminal, give them the GUI alternative. Ubuntu was designed to be targeted for average-users, not nerds.

There are several good reasons to use Terminal I can think of:
1. It's a trditional way of doing things, so lots of guides and how-tos are already written for Linux CLI. If you want to rewrite them, start now, you have much work to do.
2.Terminal is more efficient in terms of computer resources and would also work if, for some reason, no GUI can be obtained or run.
3.Gui how-tos and instructions are more time consuming to write as opposed to Terminal ones. It is quicker to tell a person to open a Terminal window and run this and that command, then to open that program and press this button and in the new window ... etc. Most, if not all forum users are volunteers trying to help others as best they can. This is not a payed support. (This reminds me of my dad calling his ISP for support for an XP machine, so the first thing they asked for was to run netstat /all command.)
4.There are lots of different GUIs for Linux with different buttons and windows. Linux Terminal is more or less unifying, at least on Debian derived distros.

I consider myself new to Linux world, and yes, Terminal was confusing in the beginning as anything new usually is. I think most computer literate ussers wold have no problem copying a few commands and would not be intimidated by Linux Terminal. The following two groups should not use it:
1. Completely computer illiterate users that do not know how to type, copy and past, and use the mouse. They should get a friend or relative to set up and administer their systems, or go for payed support.
2. Long long long term Windows users, too intrenched in the Windows way of doing things. They should stick with Windows and be happy.

---

### Post by Nirevus on 2008-02-06
> **mikasjoman said:**
> 1. GRUB scares the **** out of my girl friend.
Its ugly, and it looks like ****. Compare it to my mac, that uses EFI to start up with nice symbols, can that be possible for Hardy? Its a bad "start" so to say when the door to Ubuntu looks scary.

This is quite true, while many people just see it as an aesthetics issue, aesthetics has a huge part to play in making new users feel comfortable. The average computer user does not like seeing that kind of console text. Completely irrational, but still a part of human nature.

> **mikasjoman said:**
> 2. New users to Ubuntu hate the Terminal
Its like going back to the 90-s for them. Since XP they are totally used never going back to DOS, so why should we force them with the Terminal? Installing AWN on their computer got some scary eyes. Of course hard core linux experts has to have it, but not the average user. Like apple says, they should not even be aware of its existence of the Linux underneath. 

I'd have to agree again. There is no reason whatsoever that a user should have to use the terminal, while I use it regulary and agree that it improves efficiency, the majority of users won't understand that and are scared off by it. A lot of people simply prefer an aesthetic GUI to cryptic commands, however time saving those commands are.

It's an excellent tool, I probably use it for administration more than I use GUIs, however I also have a lot of experience getting other people set up with Ubuntu. There is just an inexplicable fear among a large majority of people about using a command line. It's completely and utterly irrational, people just don't like using it. My girlfriend did however (after lots of screaming) manage to get Stepmania installed on my EEE PC with the command line, and use shell/gedit to put a link inside the EEE's interface to launch it.

> **mikasjoman said:**
> 3. Can Ubuntu go out with a new message to the developers?
When creating Apps for Hardy, please don't ask people to add lines to the repository, get it done inside a .install file and attach a nice vector graphics icon to it. It can´t be that difficult and it would make the user experience ten times nicer.

I haven't really seen this much, if at all. The only applications I've needed that weren't in the repositories were available in .deb packages.

> **mikasjoman said:**
> 4. Change that ugly brow-sickish color theme
Brow aganist black and white is just wrong in menus. I don't say copy Mac/win, but please use a color with contrast. Try a mac and you understand in two seconds what I mean.

It's already been said, but I'll repeat it. The colour scheme is neutral, a lot of people like it a lot, some don't. As the default theme it's a refreshing change from the other large distributions; it's so easy to change the theme that it's really a non-issue.

> **mikasjoman said:**
> 5. Get ALL the updates to download automatically
For a normal user, we just want the computer updated.

This would be a good option to have, but it should definitely only be an option and it can on occasion be rather catastrophic. I know that it would be a good option for many people (I currently check my mum's computer every so often as she just ignores it when Ubuntu tells her there are updates available); although if anyone remembers the issues with xserver-xorg a while back.

> **mikasjoman said:**
> And please, while dowloading 198 updates, don't lock me out of installing other software. In china where I am, the connection can go down to 10K a second, and that means that If i push the download updates, Ill be locked out of installing things for a LONG time. Don't think Europe high speed lines exist everywhere.

This is a valid point, as is the fact that it would be dangerous to allow two things to be installed at once. A good solution would be to allow downloading concurrently and only apply the lock to the actual install process; there's no harm in simply downloading the files to a temporary location as long as whichever one finishes downloading first locks the other out from installing.

> **mikasjoman said:**
> 6. Its all about lowering the bar 
Well, I have seen many nice things in the Hardy list, but is it getting through to the developers? Why don´t I see join the Ubuntu army on the ubuntu front page? To get developers going, goal focused, it should be one click away from the front page or under a top "developer" page to see how weI can contribute.
Why not a full list of the Hardy projects, where you see what has to be done. Then attach yourself to that project? I am learning python now, but I have no clue on how to get going with helping out.
The best people I have ever seen doing this is Mozilla with their songbird. They are SUPER goal oriented, and they understand how to get people to help out in different knowledge levels.

I do agree with this point, it isn't as easy as it could be to get involved with any level of Ubuntu development. Development isn't truly transparent, not because the information isn't out there, it's just badly presented. It should be exceptionaly easy to find out how to help out, what needs doing etc.

---

### Post by Fanless_Puppy_Fan on 2008-02-06
> **atoponce said:**
> ....  Besides, this is open source software.  If it really bothers you that bad, then recompile the source that Ubuntu is built on, with your own theme......

Is it any wonder?

---

### Post by azimuth on 2008-02-06
I can understand someone not loving the default Ubuntu Brown theme. When you reflect on it though, it is easily changed, Experienced users will already have their favorites and have them in place in seconds. The default theme does have one use that has not been discussed here. When it first hits the screen it's like "hey Toto, We're not in Windows anymore". The shock value is nessessary to set the stage for a completely new computer experience.

---

### Post by wolfen69 on 2008-02-06
> The shock value is nessessary to set the stage for a completely new computer experience.

never thought of it that way. well said.

---

### Post by mivo on 2008-02-06
The default theme will change in the version after Hardy. 

I think the only real issue is that during installation the user isn't offered different themes to choose from.

---

### Post by azimuth on 2008-02-07
> **mivo said:**
> 
I think the only real issue is that during installation the user isn't offered different themes to choose from.

You are pulling my leg, right? Anybody who can't tolerate Ubuntu Brown for the 30 minute install, has a lot more serious problems than the color of his screen.

---

### Post by wolfen69 on 2008-02-07
> **azimuth said:**
> You are pulling my leg, right? Anybody who can't tolerate Ubuntu Brown for the 30 minute install, has a lot more serious problems than the color of his screen.

amen.

---

### Post by mivo on 2008-02-07
If you look at the number of people who criticise Ubuntu for the brown/orange theme, there seem to be quite a few users, and probably a lot more potential users, who would benefit from the option to choose a theme during installation. And why not? You can choose and configurate a whole lot of other stuff as well that you could do after installation.

I use the human theme, but I understand that it may not be what most people prefer - and the default system should appeal to the largest number of users. On a side note, the other themes that currently come with Ubuntu are not fully tweaked and consistent for use with Ubuntu.

---

### Post by azimuth on 2008-02-07
> **mivo said:**
> If you look at the number of people who criticise Ubuntu for the brown/orange theme, there seem to be quite a few users, and probably a lot more potential users, who would benefit from the option to choose a theme during installation. And why not? You can choose and configurate a whole lot of other stuff as well that you could do after installation.

I use the human theme, but I understand that it may not be what most people prefer - and the default system should appeal to the largest number of users. On a side note, the other themes that currently come with Ubuntu are not fully tweaked and consistent for use with Ubuntu.

I sorry, but I just can't see the value in the Ubuntu Development Community squandering it's scarce resources in something as frivolous and subjective as this, when there are so many things that really matter in need of their attention.

---

### Post by erfahren on 2008-02-07
you can put a splashimage in to use with GRUB and change the text colors - not as nice as using GFXBoot, but it makes it more appealing without much configuration. see: [hermanzone's GRUB page](http://users.bigpond.net.au/hermanzone/p15.htm)

downloading updates would be a problem with a slow connection - maybe there should be a way to limit the bandwidth it uses, but of course it would take a lot longer. Personally, I've never liked the Windows automatic updating *because* it limits to "downloading and installing in the background". On a slow connection, updating a fresh install of Windows is a pain as well.

- one thing a person could do if installing on a few different PCs - download the updates to one computer then copy the contents of /var/cache/apt/archives and put the packages on a CD. (they can be copied as a normal user - then on the other computer just open the file browser as root and paste them into that same directory. Apt will install from there first - instead of downloading.

As for the theme - an easier way for a new user to browse and install themes is by using the "gnome-art" package. It provides a nice GUI to browse and install themes from the site.

... but, I truly can understand the problems with having a slow internet connection. It seems that almost everything on computers these days *expects* a user to have broadband. I've installed WinXP a couple times on PCs with just a dial-up connection. It was annoying and frustrating (I slept over at someone's house once just because I had to wait hours for updates.)

---

