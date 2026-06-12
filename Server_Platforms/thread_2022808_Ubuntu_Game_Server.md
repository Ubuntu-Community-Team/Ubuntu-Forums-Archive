---
title: "Ubuntu Game Server"
date: 2012-07-11
forum: Server Platforms
---

### Post by Anvil 31 on 2012-07-11
Hello, I'm thinking of creating a video game with OpenGl, SDL, and C++, But the only problem i have is to come up with the networking. How am i going to route data packets to clients and receive their packets which comes from my game and then use their actions to change the game's parameters? Basically, How do you create a video game server with Ubuntu Server? Ubuntu looks very foreign to me and I've only worked with Windows in the past, All other threads talked about creating FTP servers, but used tools with existing video games such as Half-Life, but i want to create a First-Person Shooter, which is heavily multiplayer based. I've installed Ubuntu Server on my Server PC, but i don't know where to go from there. I know little of Coding with Ubuntu, I have not seen any good tutorials lately because of everyone trying to make game servers for counter-strike and MineCraft which is drowning the other web pages with it's own weight.

Please no negativity, i know at least one of you will say if you don't know how to (x) then you should not be asking us.

---

### Post by LHammonds on 2012-07-11
You are building a game engine from scratch rather than using a framework such as Unity?

---

### Post by Anvil 31 on 2012-07-13
> **LHammonds said:**
> You are building a game engine from scratch rather than using a framework such as Unity?

Yes, that's right, I'm not building some crazy game server for a AAA Company. It's just a simple game server for my game, and i will be using Visual C++ Express.
Qt is rather OK, but i don't have much cash to spare on software.

---

### Post by d4m1r on 2012-07-13
What exactly is your question? Are you just wondering how to do a basic setup of Ubuntu on your server now or?

---

### Post by Anvil 31 on 2012-07-16
> **d4m1r said:**
> What exactly is your question? Are you just wondering how to do a basic setup of Ubuntu on your server now or?

Yes, and how to get it to work with my game, such as **receiving input from a user** ([COLOR=DimGray]ex: who is maybe 200 miles away connecting to my server to play, I have to change my code 
accordingly to his actions such as detecting how many players he killed just like any other multiplayer video game[/COLOR].) and so on. Do i use the traditional FTP server? or something else?
 I am really new to Ubuntu server, I've only worked with Windows 2000/XP/Vista/7.

Using: C++, SDL, and OpenGL.

[SIZE=3]Basically[/SIZE] :

I would like to know how to **setup**, and how to use it to **work with my game**,
Please keep in mind this is** my** **game** and **not** Minecraft or Battlefield 3.
It is a **First-Person Shooter I made**. It also would be great if i can do this [B]multiple
times[/B] in the future if i make any more games.

---

### Post by Anvil 31 on 2012-07-25
Well is anyone going to help? Please? I can't find any other question like mine?
#-o](*,)](*,)

---

### Post by LHammonds on 2012-07-26
> **Anvil 31 said:**
> Well is anyone going to help? Please? I can't find any other question like mine?
#-o](*,)](*,)
Keep in mind that you are trying to get the attention of a VERY small handful of people that even know what you are talking about.  And of those, they might not answer because they might see you as a potential competitor.  It may take a while to get a response (if any at all).

If you were wanting help setting up a Minecraft server, there are probably a couple dozen people that would be able to help you out (including me). hehehe.

If you don't get any replies, see if there are any professionals you can contact/contract to help you out...such as Canonical or one of [their partners]("http://www.ubuntu.com/partners").

LHammonds

---

### Post by Anvil 31 on 2012-07-26
> **LHammonds said:**
> Keep in mind that you are trying to get the attention of a VERY small handful of people that even know what you are talking about.  And of those, they might not answer because they might see you as a potential competitor.  It may take a while to get a response (if any at all).

If you were wanting help setting up a Minecraft server, there are probably a couple dozen people that would be able to help you out (including me). hehehe.

If you don't get any replies, see if there are any professionals you can contact/contract to help you out...such as Canonical or one of [their partners]("http://www.ubuntu.com/partners").

LHammonds

No, I played too much Minecraft it's starting to bore me a little, but will seeing how to setup a Minecraft server will help me in creating my own game server? Please note that my game[SIZE=2]** will be free**[/SIZE] for a quite a while, so there will be less competition.

---

### Post by LHammonds on 2012-07-26
> **Anvil 31 said:**
> No, I played too much Minecraft it's starting to bore me a littleHa!  If you have not setup a CraftBukkit server, you don't know what you are missing.  There are tons of fun things to do with a modded server.  Here is my [how-to thread]("http://forums.bukkit.org/threads/how-to-setup-a-custom-craftbukkit-server-1-2-5-r1-0.69825/") for setting up a CraftBukkit server in case you are interested.  It is probably a bit dated by now but the process should still be the same.

Some of the really cool mod addons (which do not require ANY updates to the client!) are BleedingMobs, FoundDiamonds, TreeAssist, KonseptGate, mcMMO, Catacombs, CHDistantFarm, MachinaCraft, Appleseed, Citizens, ChestShop, BloodMoon, MonsterHunt, Multiverse, MyWolf, etc.

> **Anvil 31 said:**
> will seeing how to setup a Minecraft server will help me in creating my own game server? Please note that my game[SIZE=2]** will be free**[/SIZE] for a quite a while, so there will be less competition.Probably not...unless you are making a Java-based game.  But even then, I would not try to replicate what they have done...in terms of coding.  It is a great game with some pretty awesome features but the code behind the scenes is not that great/optimized.

LHammonds

---

### Post by Anvil 31 on 2012-07-26
> **LHammonds said:**
> Ha!  If you have not setup a CraftBukkit server, you don't know what you are missing.  There are tons of fun things to do with a modded server.  Here is my [how-to thread]("http://forums.bukkit.org/threads/how-to-setup-a-custom-craftbukkit-server-1-2-5-r1-0.69825/") for setting up a CraftBukkit server in case you are interested.  It is probably a bit dated by now but the process should still be the same.

Some of the really cool mod addons (which do not require ANY updates to the client!) are BleedingMobs, FoundDiamonds, TreeAssist, KonseptGate, mcMMO, Catacombs, CHDistantFarm, MachinaCraft, Appleseed, Citizens, ChestShop, BloodMoon, MonsterHunt, Multiverse, MyWolf, etc.

Probably not...unless you are making a Java-based game.  But even then, I would not try to replicate what they have done...in terms of coding.  It is a great game with some pretty awesome features but the code behind the scenes is not that great/optimized.

LHammonds

No, I would never copy someone else's source code from their game, i'm just saying can i just make a .exe file and when the user connects to the server it initializes it and starts to load files? And if so how do receive input from the user? 

Also Ill try the mods... BTW have you played Morrowind, oops, getting off-topic...

---

### Post by LHammonds on 2012-07-26
> **Anvil 31 said:**
> No, I would never copy someone else's source code from their gameI wasn't implying that you would copy/paste.  I was just talking about "how" they implemented their netcode and rendering options.  You probably know what I'm talking about if you've played it.  The rendering engine draws EVERYTHING above, below, in front and behind the player and proceeds to draw farther and farther out as it loads.  That is very inefficient and not how modern 3D games do it.  But in his defense, not all games can build/destroy blocks on every square inch of realestate like Minecraft.

> **Anvil 31 said:**
> i'm just saying can i just make a .exe file and when the user connects to the server it initializes it and starts to load files?Of course.  That is the basics of most any network-based game.  How it is designed/implemented/used is different for each game though.

Minecraft for example will login to their authentication servers and part of that process will check to make sure you are using the current version of the game.  If an out-dated client is detected, it goes through the process of downloading the new files.

Your game could do that as well...but you need to design it that way from the start.  I'd recommend that your game launcher is coded in such a way that it can update any data file of your game, especially the .exe engine.  Having a stable update engine will make it easier to maintain your remote clients.  But you also have to decide if your clients need to all be the same version in order to play together or, like iPhones, if they can continue to play with version 1.0 and simply not get the benefits of the updates (e.g. bug fixes vs new content)

> **Anvil 31 said:**
> And if so how do receive input from the user?

[ offtopic ]
> **Anvil 31 said:**
> have you played Morrowind
No, but as you can see in my profile image, I have played Oblivion (the armor is from "Lost Paladins of the Divines").  I am an admin at the Nexus modding site.  I've made some [mods for that game]("http://oblivion.nexusmods.com/users/128909").
[ /offtopic ]

---

### Post by Anvil 31 on 2012-07-26
> **LHammonds said:**
> 
Of course.  That is the basics of most any network-based game.  How it is designed/implemented/used is different for each game though.

Minecraft for example will login to their authentication servers and part of that process will check to make sure you are using the current version of the game.  If an out-dated client is detected, it goes through the process of downloading the new files.

Your game could do that as well...but you need to design it that way from the start.  I'd recommend that your game launcher is coded in such a way that it can update any data file of your game, especially the .exe engine.  Having a stable update engine will make it easier to maintain your remote clients.  But you also have to decide if your clients need to all be the same version in order to play together or, like iPhones, if they can continue to play with version 1.0 and simply not get the benefits of the updates (e.g. bug fixes vs new content)



OK I found this great video that works with SDL, 
[http://www.youtube.com/watch?v=iJfC4-yNnzY](http://www.youtube.com/watch?v=iJfC4-yNnzY)

So I'm getting the idea of how this is all coming together, but what type of server do 
I choose when setting up Ubuntu, I know LAMP is for web servers and that, but what about my game server? 

[SIZE=3]**1 **[/SIZE] **What do I check at the start of Ubuntu server installation? **DNS server won't do.

[IMG]http://www.multimediaboom.com/wp-content/uploads/2012/04/lamp-for-ubuntu1.jpg[/IMG]

[SIZE=3]**2** [/SIZE]**Also is there a guide to all Ubuntu Server commands?**

OK, I create a source code that creates an .exe file, i let the user download it and install it then when they are done they can lauch it and my .exe file will run, 
check for updates and user authentication right?

Then it will proceed to the menu, and when they click Multiplayer then select server they connect to my server to see if there are any game server instances on, 
and if they join I send data to the user to setup everything when he joins, then when he joins the game...

[SIZE=3]**3**[/SIZE] **Umm... do .exe files even work with Ubuntu?**

 How do i get the server to send me the input the user sent *(ex: User moves 5m right)* and how do i use the server to send input back to the user like, 
the server will send the movement change so that the player is 5m to the right?

[B][SIZE=3]4[/SIZE] Does the [COLOR=Red]server[/COLOR] [SIZE=3]or[/SIZE] the [COLOR=Blue]source code[/COLOR] receive data and send data to the user to change what is going on in the game server?
[/B]

---

### Post by LHammonds on 2012-07-26
> **Anvil 31 said:**
> what type of server do I choose when setting up Ubuntu, I know LAMP is for web servers and that, but what about my game server?
During the initial install, I would just select OpenSSH so you can connect to it via PuTTY.  Check my signature for a link on how I setup an Ubuntu server.

Once you have the basic server setup and ready, you then need to bolt on whatever you need.  You mention SDL (...a quick google search...).  It seems Simple Directmedia Layer can be installed on Windows or Linux ([their Linux FAQ]("http://wiki.libsdl.org/moin.cgi/FAQLinux")) so I would venture to guess you need to download the source and compile it...or grab the RPM and convert it into a DEB package and install it ([link]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/")).

> **Anvil 31 said:**
> 
[SIZE=3]**2** [/SIZE]**Also is there a guide to all Ubuntu Server commands?**

There are a LOT of books on Linux/Ubuntu ([here is one list]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html")).  There's not a single "cheat sheet" page for all commands, however, there are probably a lot of cheat sheets for various aspects...such as for the VI editor, command-line navigating,  security commands, etc.

> **Anvil 31 said:**
> 
OK, I create a source code that creates an .exe file, i let the user download it and install it then when they are done they can lauch it and my .exe file will run, 
check for updates and user authentication right?

You're the programmer.  You are in control of the events.  You could have it set where it only checks for updates after they have authenticated their account...you may not want to use accounts and be 100% anonymous or a mix of both.  It all depends on how you want it to work (and it also depends on the programming framework as to what you can do).  Come up with a design/workflow and make your program work how you designed it.  It can be something fairly new/unique or simply pick a game that works how you would like yours and mimic the same workflow.

Always have a workflow for how you expect things to work.  I generally start off writing on a piece of paper and have all kinds of processes listed out.  Once I finish brainstorming and have a nice list of things that I'd like to have, I then cut them out and arrange how they flow together...what is first, second, what works in parallel, what requires something else, etc.  Once I get enough data where it looks fairly complete for a high-level overview, I then open up LibreOffice Draw and start dropping down boxes with the text on the paper and then using connectors to tie everything together.

I tend to have about 3 "levels"...the high-level overview is the 1st level, the 2nd level typically breaks down what happens in each box at the high-level.  If a 3rd level is done, it tends to be very detailed...almost pseudo-code or just comments for how everything should work.

The high-level should give you enough detail to figure out if your software solution will allow what you are shooting for...such as when authentication can occur, software updates, multiplayer lobby, etc.

> **Anvil 31 said:**
> 
[SIZE=3]**3**[/SIZE] **Umm... do .exe files even work with Ubuntu?**

What you are talking about is compiled machine language which every operating system has.  Windows works a bit different than Linux.  In Windows, a program's filename must have an extension of .com or .exe but in Linux, the filename extension does not dictate what is inside.  The file permissions must have the "executable" flag set before it will allow running it but when you try, it needs to be a compiled program or a script that can be interpreted by an installed/compiled program...like Bash.

So, a .exe you compile for Windows will not work on Linux by simply copying it over.  You would need to have a Linux-compiled version...and that needs to be compatible with the flavor of Linux you intend to run it on.  It gets even more complicated if you are supporting both 32-bit and 64-bit machines.  I think you've downloaded and seen enough programs to have seen all the various links to different platforms that the author is supporting (and compiled for).

> **Anvil 31 said:**
> 
 How do i get the server to send me the input the user sent *(ex: User moves 5m right)* and how do i use the server to send input back to the user like, 
the server will send the movement change so that the player is 5m to the right?
That is out of my realm since I don't program games but I would think that your game would be running as a service/process on your server.  For Windows, they are called services so they can be started up whenever the server boots up but does not require somebody to login and start it up.  On Linux, everything is considered a "process" and you would configure startup scripts to load your process which would then listen on certain ports you define in your program.  When the client app starts, it tries to connect to your server via a DNS name and port.  Example: game.ddiggler.com:10055

Your game (client app) would need to be setup to connect over a certain port (or ports or port ranges).  The server would also need to be setup to work on these same ports.  This may be something you want to allow your end-users to configure.  Such as having the server and game client read the port numbers from a config file.  The config file can be initially created with "defaults" but still allow people to setup their own servers/games using different ports.

> **Anvil 31 said:**
> 
[B][SIZE=3]4[/SIZE] Does the [COLOR=Red]server[/COLOR] [SIZE=3]or[/SIZE] the [COLOR=Blue]source code[/COLOR] receive data and send data to the user to change what is going on in the game server?
[/B]
Not sure what you are talking about here.  I think you are confusing source code and compiled code.  You develop software using source code, then compile it into executable machine code.  What is stored on the server is completely dependent upon your game design.  If the world is static, you may only be sending user coordinates back and forth or you might have a ton of changes that you need to keep up with and have a kind of database record of changes.  As I said, I don't program games so I don't know the details behind the scene.  Someone else will need to answer this.

---

### Post by Anvil 31 on 2012-07-27
> **LHammonds said:**
> During the initial install, I would just select OpenSSH so you can connect to it via PuTTY.  Check my signature for a link on how I setup an Ubuntu server.
.

**[SIZE=3]Wow, very helpful post[/SIZE]** =D>, So during installation I would use OpenSSH right, **you also mentioned DNS**, should I create a DNS server for users that try to connect to my server?

So, with all the .cpp and .h files and the executable as well as the SDL files, I would have to **convert them** into a format in which Linux understands? I'm using a** rack server**, so should i just transfer via **Ethernet port** and how would i go and do so?

I'm targeting both** Window** users and** Linux** users which are using **32-bit** Operating systems.

If I got everything right I want to ask this question, how would i create **multiple instances of some server on one physical server**, for example, see all those servers down there? They are on just one physical server how do i do that? because buying a $600 rack server and just running one server on it would be a waste of money right?

**Different maps and servers, but it's on just one physical server, so how would I go and make 20 servers on one machine?** :confused:

[IMG]http://www.gotfrag.com/files/upload/delight_cs101_hltv_001.jpg[/IMG]

---

