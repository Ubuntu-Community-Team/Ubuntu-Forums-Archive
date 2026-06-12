---
title: "Gaim with game support"
date: 2006-02-09
forum: The Cafe
---

### Post by Virogenesis on 2006-02-09
This morning I ended up using a windows box infact I ended up using messenger now what strikes me is that Gaim offers no game support.
Now I know mercury offers game support but mercury doesn't have any many users as Gaim.

I see it beinmg quite important to offer games in a messenger client.
All the games need to be is simple java based games they don't have to be fancy all they need to do is provide another form of interaction.

My cousin who lives in the states shes plays yahoo pool with her friends for example such interaction is great for kids and adults too.

I think a fork off of gaim providing game support would be something people want and who knows it might well be adopted by Gaim in the future.

These are the games to provide:

connect 4 
chess 
pool 
black jack 
poker
battle ships 
Risk 
trivial pursuit (could get questions from a database online or could get downloaded to the system in a encrypted format.) 

Now games should be able to be added on so addon games can be provided.
Java has good network support and is cross platform so that is what the games should be written in.
Xml should be used to contain the version build and the author of the game.
Maybe have a repos 
Let me know what you think of the idea and suggest for some games.

---

### Post by TechSonic on 2006-02-09
Java you say?  The only programing language I know... <.<  I guess I could consider that as a project.  But I never had enough money to complete my schooling in Java.

---

### Post by Kvark on 2006-02-09
The purpose of a chat program is to hold conversations over the net through text, images, voice or video. A chat program doesn't have anything to do with games.

The main problems with building games into the chat program would be that:
1. People who want to talk don't want the games.
2. People who want to play games will often want to play other games then the ones that happen to be built into the chat program.

So keep the games entirely separated from the chat program please. Instead, add an option to invite everyone in the conversation to any game that you have installed and that the chat program can control with command line arguments.

When  you press the invite to game button and choose a game it could work like this... The chat program would run the game you invited your friends to with a command line option to start a match that the others can join ("gamename --server" or something). Then it would send the invitation to the others. If they have the game installed and accept then their chat programs run the game with a command line option to join your match ("gamename --joinip=your.ip.add.ress" perhaps).

---

### Post by Virogenesis on 2006-02-09
Well what I was thinking was having a plug in module for the games.
So basicaly the user right clicks on a user in their member list and that basicaly pop ups a dialog box with the games installed.

The user then clicks play game or invite other users to join the game.
Then the other user has to accept the game basicaly.
If the user clicks join game and hasn't got that certain game installed it will print  the url in which to download the game.

So basicaly what is being created is a plug in system to allow games over a network.

Now the hardest part will be working it into gaim.
The great thing about this is that it will all be modules allowing users to create their own java based games.

Messenger clients should allow the user to do interact that is the thing and even a game is interacting.
Many parents will agree with me that interaction between other kids is a important thing kids should be able to play games with other kids if they wish too.
GPL software is about giving and taking with a project like this we'll be taking Gaim and adding features into it that allow other features.
The user will have a choice to which games he/she wishes to install/remove.
This project should allow freedom to the user thats the most important part.
So a good api for the games is important.


The main problems with building games into the chat program would be that:
**1. People who want to talk don't want the games.**
Its all based on plugins so the user doesn't have to load them.

**2. People who want to play games will often want to play other games then the ones that happen to be built into the chat program.**
The games will not be built into the program itself but built as modules to be loaded giving freedom.

---

### Post by Kvark on 2006-02-09
[QUOTE=Virogenesis]**2. People who want to play games will often want to play other games then the ones that happen to be built into the chat program.**
The games will not be built into the program itself but built as modules to be loaded giving freedom.[/QUOTE]
Ok in that case people who want to play games will often want to play other games then the ones that are built as plugin modules for the chat program.

What if I want to play for example wesnoth, crack attack or unreal tournament with some friends I happen to be chatting with? If you pass command line options to separate programs then it will work with any game even if the game was not built to be started from a chat conversation. At least as long as the games supports command line options and the chat program has a list of the correct command lines for various games.

---

### Post by Virogenesis on 2006-02-09
[QUOTE=Kvark]
What if I want to play for example wesnoth, crack attack or unreal tournament with some friends I happen to be chatting with? If you pass command line options to separate programs then it will work with any game even if the game was not built to be started from a chat conversation. At least as long as the games supports command line options and the chat program has a list of the correct command lines for various games.[/QUOTE]

I believe a plug in exists for gaim that allows you to pass command line stuff already the idea is to bridge a gap in the market like what gaim-vv done.
Basicaly the concept is too help out parents, parents have kids that have friends on windows, now kids chat using msn, aim and yahoo.
Now a parent could well install mercury which supports games but then the other user has to have mercury now by having gaim with windows support the kid can go to his mate.... 
Use this it allows you to connect to yahoo, aim and msn at the same time, has webcam support and its got a ton more games.

Kid a) Lets play pool 
kid b) I can't I'm using linux
kid a) damn that sucks 
kid b) you could install gaim-games
kid a) whats that
kid b) well its gaim with game support its has alot more games
kid a) whats gaim?
kid b) gaim allows you to connect to msn, yahoo and aim
kid a) sounds good does it support webcams and chatting?
kid b) ofcourse its great its so much better than messenger 
kid a) where can i download it?
kid b) url..... 
kid a) its free and looks great 
kid b) it is, go check out the games 
kid a) wow its got so many 
kid b) best of all tom can play aswell 
kid a) tom says he can't he says his mac won't allow for that
kid b) nah made for mac aswell
kid a) i can't believe this...
kid b) invites kid a to play pool they both play pool 
kid a) tells his friends 
kid a's friends now play with gaim-games

Now its a win win for freesoftware it allows for a more standard world giving the user far more choices.

Imagine a world where a kid cannot play games with his mates o yeah that exists and its annoying not everyone using a standard.
I'm sure parents must face this problem where joe can't play with bob because hes on windows.
I bet the parent must find it so hard aswell I'm no parent but I do see this as a problem and I see this as a solution to a problem that exists.

Edubutu could even use a program like this teaching kids through chat.
Gaim-vv started off as a fork but now its being used in Gaim 2.

---

### Post by majikstreet on 2006-02-09
my solution: just don't use windows....

.... and don't play games, either....

gaim doesn't need games. it will just bloat up the damn program. I don't want a bloated gaim, and who gives a crap about games?

---

### Post by Virogenesis on 2006-02-09
[QUOTE=majikstreet]
my solution: just don't use windows....[/QUOTE]  
[QUOTE=majikstreet]
gaim doesn't need games. it will just bloat up the damn program. I don't want a bloated gaim, and who gives a crap about games?
[/QUOTE]
Did I call it gaim-game or gaim... .
Opensource is about sharing code and using it to what is required 
Just because you might like a feature doesn't mean everyone agrees with you.
**FACT!!!** You are a single entity not everyone will agree with you 

Read my posts more carefully in future I do understand you're a young user you aren't aware of some of the problems a parent faces when their child uses linux and tries to work with a windows user.
I ain't a parent myself either but I'm a mature enough human to understand that locking down something is bad.

The whole idea of Opensource is to use existing code to modify it to get it to do what you need it to do or to create software for what users need it to do.
Now to take the most popular and most mature GPL chat program and to add features that people want will take away the closed software side of things.

You think its right for people to tell little johny he can't play with susan next door because shes black? 
**_OFCOURSE NOT!!!!_**
So why should it be right for Microsoft to tell Little johny that he can't play with susan because susan is using Linux. 
Now Susan is the only black girl in her community now shes in a world full of hate shes going to feel lonely compared to all the other white kids.
Think of how little susan feels.

[QUOTE=majikstreet]don't play games[/QUOTE]
Please explain to little johny that hes not allowed to.....
That a good thing to teach a kid?

```
"Ubuntu" is an ancient African word, meaning "humanity to others". Ubuntu also means "I am what I am because of who we all are". The Ubuntu Linux distribution brings the spirit of Ubuntu to the software world.
```
Remember that!!

---

### Post by Deaf_Head on 2006-02-09
AOL instant messenger has this ... it is bloated malware.

---

### Post by Kvark on 2006-02-09
[QUOTE=Virogenesis]I believe a plug in exists for gaim that allows you to pass command line stuff already[/QUOTE]
But passing command line stuff would not do the trick. What I am talking about is a menu that is labelled invite to game and where one user clicks on a game to start it and the users' friends clicks an accept button to join. All the complicated stuff with IP-addresses and commands would be handled behind the scenes by the chat program.

Since it would just be some buttons and a list of the proper commands for various games it would be easy to add this functionality not only to gaim but to kopete, xchat and other open source chat programs.


But your idea about games sounds good too, except that it should not be dependant on gaim. How about making it a collection of stand alone games that are suitable for children and social interaction. That are ported to different platforms and can be started either by the user or by another program.

Then the game collection would work not only with gaim but on it's own or together with any chat program that you add a simple games menu and a list of proper commands to start various games to.

You could still be bundle it with gaim and distribute the two together of course.

---

### Post by joflow on 2006-02-10
Don't pay these guys any mind.  Everything is "bloat" to some of these people.

"We can't add games to GAIM!!  Thats BLOAT!!  It'll add 0.00000453 milliseconds of load time!  Are you crazy?"

And for the record, I think its a good idea.  I sometimes play games within yahoo with a friend out of mutual boredom.  Its alot easier, connecting and playing through the IM client then it is to start firefox, go to games.yahoo.com, log-in, tell your friend which room to join, join that room, create a game, find your friend's IM name in a list of about 100 people, and finally send him/her an invite.

Many people in linux aren't aware (apparently) of whats going on with the IM client in the windows world.  Its evolving into a client for consolidating MSN/Yahoo/AIM's respective services into one neat little package.  Its good for the companies (promotes use of more of their services) and good for the user (services are easier to use and access)

This whole "a IM client should be used for conversations and nothing else" is old school and quite frankly behind the times.  This whole era of web 2.0 has shown us that programs can be useful for more then just what they were originally intended to do.  Surely, the guy who invented the web browser didn't say to himself ("one day this will replace word perfect!") but [http://www.writely.com]("http://writely") now exists.

---

### Post by Deaf_Head on 2006-02-10
Have you used AOL instant messenger joflow? 

I'm just trying to remind everyone that a good idea can go very very bad. Personally I'd love to be able to play chess over gaim ... but I don't think that it should be at the cost of gaim's stability or overall reliability.

On a somewhat related note:

AIM's wildtangent malware is a perfect example of why web 2.0 can be a scary thing .. there is money in data mining ... and the kind of services that google, yahoo etc. are trying provide need to collect user information that can easily be perverted.

---

### Post by sword- on 2006-02-12
Yeah I tend to hate the approach of some linux users when a software doesn't have something, the answer is 'I don't use it' or 'Don't use it'.

Now I doubt I'd be using gaim for games myself, but I'd like to have the freedom to use it if I want to. I don't want to be limited to to not being able to play games, etc.

Virogenesis, good idea.

---

### Post by majikstreet on 2006-02-12
"Read my posts more carefully in future I do understand you're a young user you aren't aware of some of the problems a parent faces when their child uses linux and tries to work with a windows user."

wtf? I'm perfectly aware that some things just don't work between linux and windows.. Most of the people I know use windows, and think linux is crap. Well, that's because they haven't tried linux.

I'm leaving this thread.

---

### Post by sword- on 2006-02-17
Haha why are you leaving it?

---

### Post by Bragador on 2006-02-17
If the games are in a portion that loads only when you want to play games so it doesn't "inflate" the program I don't care.

I'm the kind of guy who like specialized software though so in order to pplay game, I would prefer a different program.

---

