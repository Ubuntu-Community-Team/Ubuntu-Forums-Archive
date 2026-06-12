---
title: "Too much stuff!"
date: 2006-05-04
forum: The Cafe
---

### Post by brentoboy on 2006-05-04
This is a controversial rant, so don’t get all heated like it is a debate, post comments, and don’t worry if other's disagree—keep it a discussion, not an argument.

That said, here's my rant:
---
Have you ever tried to find the "best" ftp client, or media player on Linux?

there is too much of what I call "stuff" out there, and not enough of what I would call "solutions".

It seems to me that we (the Linux development community) spend more time branching software into our own little solution, and not enough time making the original better than it was.  Take mousepad and leafpad for example.  Both are better (in my opinion) than gedit.  This is because both of them are the same program.  Try as I might, I cant see a single difference between the two.

but that's not the point.  the point is that, rather than join a project, people start a new one.  they do this because it is easy to write software when you are the only person who has to approve changes and enhancements.

but honestly, isn’t it better to have 2 or three major music players, and have all those guys who want to write their own contributing to the 2 or 3 major ones, rather than creating something with a different, but inferior, feature set?  If you want a player that shrinks down to a single button, then pick you r favorite player, and get with the dev team, study the code, and make the change.

unix software is better than other software sets out there, because each package is written for the unix variant.  the entire project is one big project, and each element is only written once (or at least that is the idea) if a particular element is not as good as it should be, you fix it--you don’t add another one that is mostly a duplicate of the same functionality, with a different twist.

but Linux apps lack united focus because each one tries to cater to a specific person, instead of meeting the needs of many people.  Certainly a "fixed" version of firefox is better than a new browser.

If you don’t like the way a particular app looks, then skin it, if it isnt skinnable, then look into making it skinnable.  You dont need a different app for kde and gnome, you just need one or two files that handle the user interface to be different, and a handful of conditional preprocessor decisions and you can compile it for whichever one you want.

apps like abiword should have abiword-gnome abiword-gtk abiwork-kde options, this might not be easy, but it is easier than rewriting the whole thing for a different toolkit.  and, code that gets cleaned up and separated from the UI in a predictable way (to allow other toolkits to be plugged in) is generally easier to maintain anyway.

--

whatever, I just figured I'd rant.
the unix philosophy is that you have one program to to each task, and it does that task well.  not have 10 programs that do each task, and each one does that task 75% of what is needed.

---

### Post by htinn on 2006-05-04
I agree about the music players. Way too damn many of those things.

---

### Post by neouser99 on 2006-05-04
i argee with you totally, its just for whatever reason some people have an issue doing things like this, of which i can't explain but wish there was one.

we should all take a note and realize that doing things similar to the kernel devs, gnome, gimp, kde, oo.org, etc. is truly a better way. i mean, just look at it, they are the unrefuted best, everyone trys to compare themselves to those.. then they turn around and walk away from the primary reason those projects succeed.

-neo

---

### Post by tristanbob on 2006-05-04
I agree that the number of Linux applications that do the same thing can be confusing sometimes, especially to new users. 

But that is why Ubuntu comes by default with only the "best of breed" applications.  Before Ubuntu, Linux distros would come several applications installed that perform the same function.  I found this frustrating!

I agree that it is beneficial for developers to pool their resources to solve similar problems, but it is also beneficial for them to be able to create a new application that meets their needs.

What you are really looking for is a list of the best applications for each specific purpose.  Does anyone know of such a list?  I don't mean a list of every application, I am talking about a list of the BEST applications for each purpose.  The best thing I have found is the Add/Remove Application tool in Ubuntu.  For example, if you are looking for the best diagram editor, you can quickly find Dia and install it in a few clicks.  You don't need to google "linux diagram editor" and then evaluate each one to determine that Dia is the most popular application for that function.

Tristan Rhodes

---

### Post by brentoboy on 2006-05-04
I see linux as a super-unix set.

you have distros each that want to have a set of apps that confirm to a certian way of doing things.  like Darn Small Linux, or Ubuntu, each has a philosophy.  But they dont need seperate apps, they need the same apps, compiled to remove or include certain features.

Linux the super project needs to try to have one app for each function. And then each app needs to have compile flags for each of several feature sets.  Then, distros just choose which set of features they want to make standard to their user base, and users can choose to recompile the code to include stuff they think is important that was left out.

a nice text editing app, or xterm app could have every possible feature, and then the person who compiles it could choose which ones to include.  rather than choosing which of 57 differnt xterminals you could use, you just use the default, and if you dont like it, you get on a forum, and find out which flags to set when you ./configure and then make it yourself.

xubuntu would have diffent compile settings than ubuntu, becuase it wants to be lightweight.  but the same basic apps should be in both of them.

why have a differnt textpad for each one?

---

### Post by brentoboy on 2006-05-04
[QUOTE=tristanbob]...that is why Ubuntu comes by default with only the "best of breed" applications.  [/QUOTE]

that's true, but best of breed doesnt get better as fast as it would if people would contribute.

all these one man opensource developer shops need to contrubute to the main product rather than make thier own.

I admit, as a life long dev, that it is more fun to start a new project with no existing complications and no codebase to work around and fix than it is to study out changes and make improvments to existing stuff, but honestly, improving old stuff generally ends up with a better end result than starting over.

and keeping group discussion on a project gernerally produces better results than having several independant projects.  groups create well rounded results.

---

### Post by fuscia on 2006-05-04
>  they do this because it is easy to write software when you are the only person who has to approve changes and enhancements.


people doing something creative, on their own time, want to do as much of it by themeselves as possible. and it's not just about ego. it's about personal satisfaction. things will probably go on as they are.

---

### Post by brentoboy on 2006-05-04
[QUOTE=fuscia]...things will probably go on as they are.[/QUOTE]

i'm sure they will.
things always continue as they are until something significant changes.  that is natural--in all areas of life.

I'm just ranting.

I do know however that it is personally satisfying to add a single feature to a well accepted "large" app, and know that others are using it.  It is very satisfying because more people end up benefiting.

but you are right, when you write software as a hobby, you dont want to have to take time to care about what other people on the same project want to do, its natural to want a "no strings attached" "just my project" "go play in your own sandbox" project.

im just put off a little bit by the sheer number of them that pop up, as though it is a contribution to the whole system, rather than a distration.

---

### Post by briancurtin on 2006-05-04
people have new ideas, new goals, so they go for them. judd vinet could have just went and worked on crux instead of creating arch, but he had goals and ideas. mark shuttleworth could have just sent people to work directly on debian, but he had goals and ideas. i say bring on more of everything. if you cant find something you like, well then you need to learn some decision making skills.

---

### Post by nickle on 2006-05-04
Creativity is an endless path with many dead ends and we never know which ones in advance...

---

### Post by brentoboy on 2006-05-04
[QUOTE=briancurtin]...mark shuttleworth could have just sent people to work directly on debian, but he had goals and ideas...[/QUOTE]

im not talking about major forks here. Im talking about splinters.
mark shuttleworth put millions of dollars into a new idea.  he organized a team, and created a valid branch.

im talking about the difference between xubuntu and ubuntulite.  xubuntu stayed with the main project, added to ubuntu. ubuntulite tried to make its own distro, but didnt have the resouces to sustain its own distro, so it got abandoned (or so it seems, who knows what actually happened to it)

when you are a one man show, starting a new project just doesnt contribute, a single person rarely has the resources or discipline to create something lasting, but a single person could have the time and energy to add something valuable to a project that is already accepted and will continue to grow long after that single person moves on to more interesting things.
--
I dont know, im not offering ideas on how to help, im just ranting.
I wish i had some ideas on how to make the situation better, but I dont.

---

### Post by aysiu on 2006-05-04
GPL and open source can't stop people from forking... or splintering.

Such is the nature of the beast, and that model has its pros and cons. 

You're pointing out a con--that's a legitimate beef, but what can you do besides email the developers of splinters and slap their wrists?

That said, I find KFTPGrabber and AmaroK to be fine programs.

---

### Post by Virogenesis on 2006-05-04
If a program is good it won't need to be forked look at the kernel.
Forking allows for programs to aim features into a app that might not want those features.

Good example would be gaim-vv I see nothing wrong with having choice.
Choice is good, some programs are written better than others for example pureftpd is better than proftpd.

---

### Post by brentoboy on 2006-05-04
[QUOTE=Virogenesis]If a program is good it won't need to be forked look at the kernel.
Forking allows for programs to aim features into a app that might not want those features.

Good example would be gaim-vv I see nothing wrong with having choice.
Choice is good, some programs are written better than others for example pureftpd is better than proftpd.[/QUOTE]


There is a difference between forking a program because some devs want it one way and others want it another.  ususally when groups of devs devide against eachother each they each represent a decent userbase.  like firefox and flock (or whatever it was called) a dev didnt start his own firefox, a group of them started a fork.  That sort of thing can lead to progress and like nickle said: "Creativity is an endless path with many dead ends and we never know which ones in advance..."

---

### Post by dcraven on 2006-05-04
The fact that you can fork an existing project or start a new one on your own so easily is the reason Linux is so fun for many people. If you couldn't, or the culture were against such practises, then you'd probably find a lot less of the evolution that you see now. All of the projects you use daily started this way. Sometimes people just want to play and try new things. Sometimes those things work out, and become popular or even mainstream. Sometimes they don't, development stops, and the bits rot.

It's just evolution, and without this trait I don't think FOSS would be where it is today at all.

Cheers,
~djc

---

