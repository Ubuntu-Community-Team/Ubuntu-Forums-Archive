---
title: "Does Ubuntu server support GUI? Any desktop environtment can install into it?"
date: 2009-03-07
forum: Server Platforms
---

### Post by Grey08 on 2009-03-07
I have just installed Ubuntu Server 8.10, and i m new to Linux, is there anyway to install a desktop environment into Ubuntu server since it is only black screen there.

Thanks

---

### Post by kestrel1 on 2009-03-07
This is normal for server editions, but you should be able to install gnome by typing:```
sudo apt-get install gnome
```
Be warned it is a large download from what I can remember.

---

### Post by Iowan on 2009-03-07
It's also possible to install only a window manager (GUI) without all the extra applications that come with standard Gnome install.  I can never remember the exact packages to install - something involving "gnome-core"... 

[http://ubuntuforums.org/showthread.php?t=1060966]("http://ubuntuforums.org/showthread.php?t=1060966")

---

### Post by DGortze380 on 2009-03-07
Absolutely. Whatever one you want.

For full 'ubuntu' desktops the following meta-packages are available-
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

or

For lighter weight, generic versions
(some of these may be off a bit)

sudo apt-get install xorg gnome
sudo apt-get install xorg kde4
sudo apt-get install xorg xfce
sudo apt-get install xorg fluxbox

---

### Post by hyper_ch on 2009-03-08
why do you want to run a gui on a server?

---

### Post by jeffsa12 on 2009-03-08
I have 8.04 server so not sure it'll be exactly the same. I used sudo apt-get install ubuntu-desktop. It loaded a bunch of stuff I didn't need or want. I ended up reinstalling after I got too carried away with removing packages but trying to maintain a basic gnome desktop GUI. I also installed Webmin to check it out. Webmin alone could would work for me, but for now, I prefer a real desktop. Perhaps later I'll wean off all GUI, but I'm not competent enough with CL yet to feel comfortable. 

I'm not convinced that in my case, with virtually no website traffic to speak of yet, a virtual LAMP server installed on top of a full Ubuntu desktop, that hardware resources are a problem what so ever. This is with an an older, Intel Pentium4 with 2G memory. Of course it would probably depend on your anticipated traffic load, hardware, and what else you use your server hardware for.

The apt-get install gnome sounds interesting....I think I'll make another virtual machine to test it out.

---

### Post by kestrel1 on 2009-03-09
Yes, Virtual machines are a very good way to test out things on an OS before implementing them on the machine you intend to use them on. I installed Ubuntu server a while ago on a VM environment, but haven't had the chance to do much with it as of yet.

---

### Post by Grey08 on 2009-03-09
Thanks to all of you, users at other forum usually will not reply my question, but users from ubuntuforums always reply way faster and better solutions, :)


Reply to hyper_ch,
Because i m new to Linux ubuntu server, i don't know what should i do. That's why i m installing a GUI on it.

Reply to jeffsa12,
Does your GUI now look exact as Ubuntu desktop(or it is Ubuntu Desktop now, but with server function?)

Reply to kestrel1,
Im new to linux, so i m not sure what is Virtual machine, :), but i m keen to learn.

---

### Post by Grey08 on 2009-03-09
Another further question, about this GUI.

At first i have tried [ sudo apt-get install gnome ], thanks to kestrel1's idea, it works very well.

After that, i was thinking is that anyway to install Ubuntu Desktop because wondering how does Ubuntu Desktop look like, thus, i tried [ sudo apt-get install ubuntu-desktop ], in result, it has two desktop within Ubuntu Server now, i guess.

This is what i see from the [System monitor]

Ubuntu
  Release 8.10 (intrepid)
  Kernel Linux 2.6.27-7-server
  GNOME 2.24.1



My question now, is this alright? Will it crash later?

---

### Post by kestrel1 on 2009-03-09
> Reply to kestrel1,
Im new to linux, so i m not sure what is Virtual machine, , but i m keen to learn.
If you download & install Virtual Box from this link: [http://www.virtualbox.org/](http://www.virtualbox.org/)
You can install OS's on a virtual hard drive & test drive them.

---

### Post by hyper_ch on 2009-03-09
> **Grey08 said:**
> Reply to hyper_ch,
Because i m new to Linux ubuntu server, i don't know what should i do. That's why i m installing a GUI on it.

Why do you want to install the server edition then if you don't want to use it as server?

---

### Post by hyper_ch on 2009-03-09
if you really want to run a server have a look here:  [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

But remember, the server edition is aimed at running it as server. If you don't intend on doing so, then install the normal desktop edition and just add the services you want.

---

### Post by kthxbai2u on 2009-03-09
> **Grey08 said:**
> 
My question now, is this alright? Will it crash later?
... ahahahhahahaha .... ahahahha no.... it wont crash later. It's UberBuntu dude! It never crashes :)


> **Grey08 said:**
> Thanks to all of you, users at other forum usually will not reply my question, but users from ubuntuforums always reply way faster and better solutions, :)


Reply to hyper_ch,
Because i m new to Linux ubuntu server, i don't know what should i do. That's why i m installing a GUI on it.

Reply to jeffsa12,
Does your GUI now look exact as Ubuntu desktop(or it is Ubuntu Desktop now, but with server function?)

Reply to kestrel1,
Im new to linux, so i m not sure what is Virtual machine, :), but i m keen to learn.

Of course the GUI is the same, its Gnome. You could put KDM on it the same way. The "Server" part to it is that most of the un-needed packages are not installed (like the desktop) so they dont take space or execute at boot.

You can of course disable the GUI from boot, by removing /etc/rc2.d/S30gdm and also the one in the rc3.d folder. Then reboot and to start the GUI just type "sudo gdm" in console and your in!

> **hyper_ch said:**
> Why do you want to install the server edition then if you don't want to use it as server?

Theres no definition to server that says you cannot have a desktop. And even so, If your not concerned about a little HD space taken, you can benifit from using the GUI. Sometimes you know how to do it easy through the GUI, but dont know the console way. Thus it is a good idea (if your new or dont know much) to have the GUI installed and handy! As long as it is not executing all the time, it shouldn't take up system memory. Just shut it down when your done.

---

### Post by hyper_ch on 2009-03-09
> **kthxbai2u said:**
> The "Server" part to it is that most of the un-needed packages are not installed (like the desktop) so they dont take space or execute at boot.
There are more differences... you should compare the server kernel default setup to a desktop one.

> **kthxbai2u said:**
> Theres no definition to server that says you cannot have a desktop.
That's true, but if you look at what the server edition is aimed at even from the ubuntu homepage then you should ask yourself why you oppose to all that and insist on installing a gui? If you want a gui, grab desktop edition and install the according services that you want.

> **kthxbai2u said:**
> you can benifit from using the GUI.
Like?

> **kthxbai2u said:**
> Sometimes you know how to do it easy through the GUI, but dont know the console way.
Well, configuration is done by editing text files, how would a gui help you there?

> **kthxbai2u said:**
> Thus it is a good idea (if your new or dont know much) to have the GUI installed and handy!
And if you're mission critical and never learned how to get along in the gui and the gui fails then, what you're going to do?

---

### Post by kthxbai2u on 2009-03-09
> **hyper_ch said:**
> There are more differences... you should compare the server kernel default setup to a desktop one.

Yeah, there are far more differences. I am talking to them on *their* level. They need not know any more than what I told them. No need to confuse!

> **hyper_ch said:**
> 
That's true, but if you look at what the server edition is aimed at even from the ubuntu homepage then you should ask yourself why you oppose to all that and insist on installing a gui? If you want a gui, grab desktop edition and install the according services that you want.

Installing the GUI and removing it from startup is almost the same as not having it even installed. The only difference is the disk space. If you remove it from the rc*.d then it only affects the server itself when running the GUI... Using up memory and CPU resources. You start the additional services when you want to.

> **hyper_ch said:**
> 
Like?

What do you do when you need to do something you don't know how to do in console? You google in another computer for how to do that in console. IF there are any results matching your query, you'll be lucky to find a match to your problem with an answer.

It  is faster to just load the GUI and change network config or display config from the GUI applications. I myself know how to do this from console, but its quicker from a GUI. Or maybe you need the GUI to do things through SSH. Anyways, point is, once your in the GUI its smoother sailing from there for beginners.

> **hyper_ch said:**
> 
Well, configuration is done by editing text files, how would a gui help you there?

Like I said, I'm talking on their level. Which means I am *thinking* on their level as well. Most of the configuration that they need to do is just slightly hidden to people like you, It's under "System" -> "Administration" *or* "Preferences". You can even call them from console. Remotely, if you please. 

> **hyper_ch said:**
> 
And if you're mission critical and never learned how to get along in the gui and the gui fails then, what you're going to do?


Well, Console is definately not the better path to take, for someone new to Linux. Honestly, Anyone new to Linux who cannot use the Desktop should either google, learn/post off the forums, or just give up. I cannot predict the outcome of a wildcard like that. Most people reading this thread have a decent understanding of how to install and configure the Desktop version. The install and configuration processes are not much different than that...

Anything else to waste my time with? Why not contribute to the point of the thread, rather than come in and try to take on anyone you see?

By the way, any mistakes in any of my posts are likely caused by beer.

---

### Post by windependence on 2009-03-10
> **kthxbai2u said:**
> 
Anything else to waste my time with? Why not contribute to the point of the thread, rather than come in and try to take on anyone you see?


Because if he doesn't ask the question, it seems that the community is very willing to "dumb down" the server version and never point out the disadvantages of running a SERVER with a GUI on it. I see some trends in the Linux community I don't like very much and this is one of them. Seems everyone wants Linux to be more like "some other OS from Redmond" and is losing site of what Linux is about even in the server space. 

If you wanna run a home server with a GUI, load the desktop and just add the packages you need. You will probably never notice the difference between the kernel tuning if you're running a torrent server. There ARE some of us, however, that actually would like to use Ubuntu server the way it was intended - for REAL server applications and loads. If the folks at Canonical wanted a GUI on the server version, doncha think they would have integrated it into the product? 

I personally think we should politely direct folks who are just starting out to the desktop product until they gain enough experience to use the server version. This is not turning away n00bs, it's merely directing them to the correct resource. For many new users, using the server version is like using a chain saw to cut your grass. For a simple torrent box, or a personal web site, the desktop version is more than adequate.

-Tim

---

### Post by hyper_ch on 2009-03-10
> **kthxbai2u said:**
> If you remove it from the rc*.d then it only affects the server itself when running the GUI... Using up memory and CPU resources. You start the additional services when you want to.
Are you positive on that, that there's no more services added in the desktop installation that is not triggered by the gui?

> **kthxbai2u said:**
> What do you do when you need to do something you don't know how to do in console?
What do you do when you need something to do you don't know how to do in console? You google for how to do that in gui. IF there are any results matching your query, you'll be lucky to find a match to your problem with an answer.

Besides, I don't know anyone who usually physically connects directly to a server in order to do something on the server. Normally you just ssh into the box so you use "another computer with a gui" already.

> **kthxbai2u said:**
> It  is faster to just load the GUI and change network config or display config from the GUI applications. I myself know how to do this from console, but its quicker from a GUI.
It's faster to alter network directly from the cli. Before the gui has even started I would have reloaded the network already ;)

> **kthxbai2u said:**
> Or maybe you need the GUI to do things through SSH.[/QUOTE
??? care to explain?

[QUOTE=kthxbai2u;6868365]Anyways, point is, once your in the GUI its smoother sailing from there for beginners.
But is it also more helpful to dumb them down to the gui in longterm? Would you give a loaded gun to a kid? Isn't it better to educate and show them how to do things properly?

> **kthxbai2u said:**
> Well, Console is definately not the better path to take, for someone new to Linux.
I disagree. If they want to run a server then console is definitively better path to take from the beginning. You know, humans are habit creatures. Once you have done a thing a certain way you are very reluctant to change your behaviour. So by starting off "wrongly" it will be even harder for them at a later stage.

> **kthxbai2u said:**
> Anything else to waste my time with? Why not contribute to the point of the thread, rather than come in and try to take on anyone you see?
Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.

---

### Post by kthxbai2u on 2009-03-11
-------------------------------------------------------------------
For my friend hyper_ch:
-------------------------------------------------------------------
> **hyper_ch said:**
> Are you positive on that, that there's no more services added in the desktop installation that is not triggered by the gui?

You're putting words into my mouth! Thank you but I'd rather use my own :) I never said there were no other services that would be added. The point is that you could still remove all of the services and start them manually.

> **hyper_ch said:**
> 
What do you do when you need something to do you don't know how to do in console? You google for how to do that in gui. IF there are any results matching your query, you'll be lucky to find a match to your problem with an answer.

Besides, I don't know anyone who usually physically connects directly to a server in order to do something on the server. Normally you just ssh into the box so you use "another computer with a gui" already.

WTF?? Now, your stealing my words lol. The point I was making was that the support for the GUI is much better because of the desktop version. Most people use it. If you google for some help on how to do something in console, you get nothing most times. If you google for help on how to do something via the desktop, you get more results. Usually you will find an answer.

What if one had just got the server installed and wanted to configure it by connecting directly? Then all one has to do is remove those services and start connecting remotely. You have to connect to the machine physically anyways to install the distro you want. Well, you could rip the HD out and do it in another machine...

Yes, you could just set up an ssh server and ssh into it. But thats not what the dude in the 1st post wants. Because he would still be stuck to a console. He wants a desktop.

> **hyper_ch said:**
> 
It's faster to alter network directly from the cli. Before the gui has even started I would have reloaded the network already ;)

I agree with you, I would have reconfigured and restarted it through console before the GUI got loaded as well. But see, we know more stuffs than most people. 

This thread is not mine or yours, so everything usually relates to the first post. I think that's how it goes in forums, no? And if its something un-related you start a new thread? O_o Anyways the point of that was that it's the first guys thread, and if you read it clearly he doesn't like the console - obviously because he wants to install the GUI so he can run it _when he needs it_.

> **hyper_ch said:**
> 
[QUOTE=kthxbai2u;6868365]Or maybe you need the GUI to do things through SSH.
??? care to explain?[/QUOTE]
Yes, well I do. It is to my understanding that when you use X forwarding with SSH that the *applications* are run on the *server* and the display output is the *client*. Therefore you need the applications/GUI's installed on the *server*.

I believe if you disabled all the services that were added by installing the GUI, the GUI itself wont load, and you can do something like "gnome-network-preferences" or "gnome-display-properties". The second one, "gnome-display-properties" is a good one, because from what I understand you can no longer change the display properties through config files...


> **hyper_ch said:**
> But is it also more helpful to dumb them down to the gui in longterm? Would you give a loaded gun to a kid? Isn't it better to educate and show them how to do things properly?
**Oh please**, they will open consoles, or even try to do it through console first if they are somewhat intelligent. Then they will load the GUI. Why be stuck searching for answers for literally days when you could just load the GUI and fix the problem _now_? Then they can explore either methods of doing things. Once they solve the problem, and have time to waste, then you post in a forum asking how to do it properly in console.

> **hyper_ch said:**
> 
I disagree. If they want to run a server then console is definitively better path to take from the beginning. You know, humans are habit creatures. Once you have done a thing a certain way you are very reluctant to change your behaviour. So by starting off "wrongly" it will be even harder for them at a later stage.
Nice *opinion*! I disagree to that! Partially anyways... Your *assuming* all humans are the same habit forming creatures that you probably are or know of. When in reality, everyone is different. I naturally will try to do everything in console because i know it is better. You feel smart when you do too :) You just have to encourage them to do it in console if possible. If they decide otherwise, thats *their* decision.

> **hyper_ch said:**
> 
Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.

Very nice quote. And true. But that does not mean that the console way is teaching how to fish. Teaching how to fish is just showing whoever it is who needs the help how to do what they want - and making suggestions. Giving a man a fish would refer to _doing the work for them_.

There may be other interpretations out there but meh. This one is mine.


-------------------------------------------------------------------
Now, for my friend windependance:
-------------------------------------------------------------------


> **windependence said:**
> Because if he doesn't ask the question, it seems that the community is very willing to "dumb down" the server version and never point out the disadvantages of running a SERVER with a GUI on it. I see some trends in the Linux community I don't like very much and this is one of them. Seems everyone wants Linux to be more like "some other OS from Redmond" and is losing site of what Linux is about even in the server space.

Target the people who dumb it down by default, not me. If I know how to do something in console, I tell the person. Besides, its not our responsibility to control how one uses a version of Linux. And if one doesn't know how to do it in console, then someone else may come along and know how. The _sight_ or *vision* of what Linux is all about is **not ****only** that you can slim it right down, do everything remotely, or run it on the smallest processor you can find, it is *also* about being more user-friendly, open and free to everyone. I swear the last I checked, this was how <<heavenly music>>Mr. Linus Torvalds<</heavenly music>> wanted it! 

> **windependence said:**
> 
If you wanna run a home server with a GUI, load the desktop and just add the packages you need. You will probably never notice the difference between the kernel tuning if you're running a torrent server. There ARE some of us, however, that actually would like to use Ubuntu server the way it was intended - for REAL server applications and loads. If the folks at Canonical wanted a GUI on the server version, doncha think they would have integrated it into the product?
It is far easier to put this into practice at home first, and learn things at home. Then you can go set up some server-farm on a fiber connection. 

You use linux the way you want to. Just because they code the server version to not install the desktop does not mean you can't use the desktop.

This person that was asking for help was asking about a desktop on the server. No questions asked, you should only really be replying to help him achieve that. So, like I said, stop coming in here trying to take things over and attack me, just help the other guy. Don't you people understand this?

> **windependence said:**
> 
I personally think we should politely direct folks who are just starting out to the desktop product until they gain enough experience to use the server version. This is not turning away n00bs, it's merely directing them to the correct resource. For many new users, using the server version is like using a chain saw to cut your grass. For a simple torrent box, or a personal web site, the desktop version is more than adequate.
Exactly, but the originating poster probably *has* a desktop version installed and now wants to learn to install the server version.

And I laugh at you for this last half. Indeed, it is true, but how many times have you bought a v6 over a v8? Most (not all) would take the v8 because it has more power. Whether they need it or not. Its called exploration, one thing we humans *are all* is curious!


NOW, everyone, please, back on topic... Help the first poster. I'd rather not waste my time posting off topic stuff.

The fact of the matter is, that Ubuntu Server ***_DOES_*** support the use of a desktop. See for yourself "sudo apt-get install gnome-desktop". Whether it's using Linux "properly" according to other users definitions or not, the point of the thread is to help the user. Helping them use it right is something you do after you help them with their _specific needs_.

You guys remind me of the older kids that wont let the younger kids do anything... Grow up and let everyone play :P

---

### Post by hyper_ch on 2009-03-11
> **kthxbai2u said:**
> I never said there were no other services that would be added. The point is that you could still remove all of the services and start them manually.
> **kthxbai2u said:**
> Installing the GUI and removing it from startup is almost the same as not having it even installed. The only difference is the disk space. If you remove it from the rc*.d then it only affects the server itself when running the GUI... Using up memory and CPU resources. You start the additional services when you want to.
You said it's sufficient to just not let the gui start and then the only difference is that it uses more disk space ;) and I questioned that statement.

> **kthxbai2u said:**
> WTF?? Now, your stealing my words lol.
Not really. You said the gui is simpler if you don't know how to do something in the console. I merely pointed out that the same happens also on the gui.

> **kthxbai2u said:**
> The point I was making was that the support for the GUI is much better because of the desktop version. Most people use it.
Most people don't use a gui on a server and so the support is far less.

> **kthxbai2u said:**
> If you google for some help on how to do something in console, you get nothing most times. If you google for help on how to do something via the desktop, you get more results. Usually you will find an answer.
Then you don't know how to handle google. I've done extensive searches on how to do things on google and usually you get a direct cli answer.

> **kthxbai2u said:**
> What if one had just got the server installed and wanted to configure it by connecting directly?
The terminal's right there to configure it. Editing config files doesn't make a difference on gui or cli so you have no advantage of the gui.

> **kthxbai2u said:**
> Then all one has to do is remove those services and start connecting remotely.
Please enumerate all the services you don't need on a server that a gui installs.

> **kthxbai2u said:**
> You have to connect to the machine physically anyways to install the distro you want. Well, you could rip the HD out and do it in another machine...
There are otherways also.

> **kthxbai2u said:**
> Yes, you could just set up an ssh server and ssh into it.
See, it's that simple.

> **kthxbai2u said:**
> But thats not what the dude in the 1st post wants. Because he would still be stuck to a console. He wants a desktop.
Did it ever occur to you that the TO just doesn't know any better and is just trying to do the things he's used to. Before you started use Linux, did you use windows? How often did you try to apply Windows-ways of doing things only to find out that you are totally mistaken on how to get things done on linux?
Instead of just answering the questions people ask because they don't know any better yet, it is much better to give them support to find out how to do things the "proper" way on linux. In the longterm they'll profite a lot more from it. I often ask the motivation for a certain thing asked because my impression is that people just don't know what to properly ask.

Give a man a fish; you have fed him for today. Teach a man to fish; and you have fed him for a lifetime

> **kthxbai2u said:**
> This thread is not mine or yours, so everything usually relates to the first post. I think that's how it goes in forums, no?
Nobody "owns" a thread.

> **kthxbai2u said:**
> And if its something un-related you start a new thread?
It's not unrelated, it's dead to the point ;)

> **kthxbai2u said:**
> Anyways the point of that was that it's the first guys thread,
The point of this thread is how to run a server ;)

> **kthxbai2u said:**
> It is to my understanding that when you use X forwarding with SSH that the *applications* are run on the *server* and the display output is the *client*. Therefore you need the applications installed on the server.
But you don't need any xserver or so running on the server ;)

> **kthxbai2u said:**
> 
**Oh please**, they will open consoles, or even try to do it through console first if they are somewhat intelligent. Then they will load the GUI. Why be stuck searching for answers for literally days when you could just load the GUI and fix the problem _now_? Then they can explore either methods of doing things. Once they solve the problem, and have time to waste, then you post in a forum asking how to do it properly in console.
You really think they try the terminal first? I doubt it. And still my point stays: For running a server a gui gives no advantage what-so-ever (and very likely the gui can even cause more problems than it supposedly solves). And no, people won't take extra time to ask again how to do things properly in the console. 99.99% of all questions asked in these forums here can be easily solved by using google.

> **kthxbai2u said:**
> Nice *opinion*! I disagree to that! Partially anyways... Your *assuming* all humans are the same habit forming creatures that you probably are or know of. When in reality, everyone is different. I naturally will try to do everything in console because i know it is better. You feel smart when you do too :) You just have to encourage them to do it in console if possible. If they decide otherwise, thats *their* decision.
Most people are complacent with what they know and don't want to invest time in "boring" things such as setting up a computer. I again refer to my above statement about 99.99% of all questions to be answered by simple search of google.


> **kthxbai2u said:**
> Very nice quote. And true. But that does not mean that the console way is teaching how to fish.
On a server it is the same as teaching how to fish.

> **kthxbai2u said:**
> Besides, its not our responsibility to control how one uses a version of Linux.
But it's nice of you if you tell them that there are much better ways on doing things ;)

> **kthxbai2u said:**
> It is far easier to put this into practice at home first, and learn things at home. Then you can go set up some server-farm on a fiber connection.
Bad habits are hard to get rid off. 

> **kthxbai2u said:**
> You use linux the way you want to. Just because they code the server version to not install the desktop does not mean you can't use the desktop.
That's right. But before you do as you want you should know what you do - informed choice.

> **kthxbai2u said:**
> This person that was asking for help was asking about a desktop on the server. No questions asked, you should only really be replying to help him achieve that.
I refer again to the man/fish quote. This person has no clue about servers. That's why he asked how to install a gui. If you care a bit then you should tell him why it's generally considered a bad thing to do and help him to get it done the "right" way.

> **kthxbai2u said:**
> NOW, everyone, please, back on topic... Help the first poster.
I'm right on topic.

> **kthxbai2u said:**
> The fact of the matter is, that Ubuntu Server ***_DOES_*** support the use of a desktop. See for yourself "sudo apt-get install gnome-desktop".
The fact of the matter is that they use the same repos but if devs would have wanted a server to have a gui then they would not have created the server edition ;) just because you can install a desktop doesn't mean you should. Even if hey had seperated repos (which gives them a lot more work of administration to and hence less time on improving things) you still could install a desktop. Just grab the source and compile it ;)

> **kthxbai2u said:**
> Whether it's using Linux "properly" according to other users definitions or not, the point of the thread is to help the user. Helping them use it right is something you do after you help them with their _specific needs_.
The point of the thread is that the TO has no clue what a server does. He may think that it's cool to have one and because of that he applies his mind-set of "must-have-a-gui". If he's serious about running a server the only proper answer is to give him an informed choice.

---

### Post by kestrel1 on 2009-03-11
> The point of the thread is that the TO has no clue what a server does. He may think that it's cool to have one and because of that he applies his mind-set of "must-have-a-gui". If he's serious about running a server the only proper answer is to give him an informed choice.
Totally agree with you here. The idea of the forums is to help others & point them in the right direction if they seem to be going astray.

---

### Post by kthxbai2u on 2009-03-12
> **hyper_ch said:**
> You said it's sufficient to just not let the gui start and then the only difference is that it uses more disk space and I questioned that statement.

Which I do not know why you questioned that statement. If there are no desktop related services ruinning, what amount of memory do you think the desktop is using? NONE! because the desktop and its services are not running. If you are a "guru" then you would know that you can completley modify the system to do what you want it to do... If the services are not running, the CPU is not being used (or wasted) running or loading the GUI off disk.

> **hyper_ch said:**
> 
Not really. You said the gui is simpler if you don't know how to do something in the console. I merely pointed out that the same happens also on the gui. The point is that its a hell of a lot harder to find help on something console related. Refer to "Google" below lol.


> Most people don't use a gui on a server and so the support is far less.
Yes, in a production environment. The guy is in his own home for Christ's sake...

As well, I meant it supports the GUI as in you can install it with no problems. I didn't mean that the entire community would support your decision on installing the GUI in a server version. 

Basically, any help you need with the GUI is *already there* because of the extensive amount of information/how to's on the desktop edition. The desktops are the same, on either server or desktop edition.

> **hyper_ch said:**
> 
Then you don't know how to handle google. I've done extensive searches on how to do things on google and usually you get a direct cli answer.

Obviously I do know how to handle Google, because i know resources for information on methods of doing things through console are scarce. I assume by you saying "cli" you mean the server version? Google one thing for console, then compare it to googling for how to do the same thing in desktop.

**GUARENTEED** you will find 150% or more answers related to the desktop. If you don't, you dont know how to google. not me.

> **hyper_ch said:**
> 
The terminal's right there to configure it. Editing config files doesn't make a difference on gui or cli so you have no advantage of the gui.
 The original poster of this thread is trying to stay away from console and use the GUI. The guy does not know HOW to use the console. So don't give him that answer unless you going to step him through modifying each config file and teach him extensivley how to use a console.

> **hyper_ch said:**
> 
Please enumerate all the services you don't need on a server that a gui installs.
You joker. The point was not that I know each and every service that is there that is added on after installing the gui, but was more that I was letting people know it is possible to remove them and start them manually. Although if I chose, I could either google, or just install on 2 HD and compare them. I'm not stupid :)

> **hyper_ch said:**
> 
There are otherways also.

Like what? You have to put in some sort of bootable medium.,,  Which means a cdrom or usb device of some sort. Which means physical access. To install a distro, at this point there is nothing on the machine, so you cannot just ssh into it.

> **hyper_ch said:**
> 
See, it's that simple.

  yes, for you and I maybe. Not for the original poster. S/He is however, the one responsible for learning how to do that. 


> **hyper_ch said:**
> 
Did it ever occur to you that the TO just doesn't know any better and is just trying to do the things he's used to. Before you started use Linux, did you use windows? How often did you try to apply Windows-ways of doing things only to find out that you are totally mistaken on how to get things done on linux?
Instead of just answering the questions people ask because they don't know any better yet, it is much better to give them support to find out how to do things the "proper" way on linux. In the longterm they'll profite a lot more from it. I often ask the motivation for a certain thing asked because my impression is that people just don't know what to properly ask.
Give a man a fish; you have fed him for today. Teach a man to fish; and you have fed him for a lifetime

Yes, I did start with winblowz. That does not matter. No, I do not do things "Windows ways" because you can't. It is Linux... Completley different. No one knows everything about linux, there is too much to know. Everyone will be mistaken about how to do something at some point... I agree to teach one to do things the proper way, but using the GUI does not by any means mean it is improper. Because it could be done properly. And if its a private connection at home or something, there is no reason he cant plug in directly. What if ssh fails? you can't for the life of you ssh into the box. The server is right in front of you so just plug in to the machine. Now you find "Oh, I am now stuck at BusyBox". You get the point. You sometimes have to do that. You cannot deny the fact that you have to do it at some point. Unless it's colo and someone else is watching it. Servers go down. Especially while making changes to them.



> **hyper_ch said:**
> 
Nobody "owns" a thread.

No, but someone starts the thread. It is just polite forum etiquett to stay on topic and help the original poster rather than try to out smart the person helping him. If you have the ways to do every single little thing he wants in console, and you want to spend a year or two teaching him, go ahead. The idea of the forum is to help him get through the single problem he posted about - maybe give extra pointers - and let him/her be on his/her jolly way! then s/he will come back to ask another question. Yay! people like to come back because they got their answers. Not because of one person attacking another person for helping him O_o I dont even think he is around anymore so when this is done im outta here because this is stupid waste of time.

> **hyper_ch said:**
> 
It's not unrelated, it's dead to the point 

It is unrelated. Look at the topic of the thread... He clearly wants to know if he can install a GUI on the server. And he can. Question answered. Yes, he is advised to do things in console, but if he is at his whits end with things, he has an escape route. However proper or improper this is does not matter.

> **hyper_ch said:**
> 
The point of this thread is how to run a server 

No, thats the point that ***_you want it to be_*** Look **closeley**:
**Thread: [ubuntu] Does Ubuntu server support GUI? Any desktop environtment can install into it? **

> **hyper_ch said:**
> 
But you don't need any xserver or so running on the server 

no one said you do. not for ssh. but in the case of pluging into the machine like the original poster probably is, then s/he does need it running. Like I said though, s/he can start it manually.

> **hyper_ch said:**
> 
You really think they try the terminal first? I doubt it. And still my point stays: For running a server a gui gives no advantage what-so-ever (and very likely the gui can even cause more problems than it supposedly solves). And no, people won't take extra time to ask again how to do things properly in the console. 99.99% of all questions asked in these forums here can be easily solved by using google.

Most people are complacent with what they know and don't want to invest time in "boring" things such as setting up a computer. I again refer to my above statement about 99.99% of all questions to be answered by simple search of google.

Doesn't matter, that is not my problem, that is theirs. I always try to do things in terminal first. You cannot say there is NO advantage. There are. I have been outlining it all to you. I agree with your point in regards to leaving a GUI running all the time, and on a production server. Otherwise, I disagree with your statement. It uses no more than the HD space. I'm not responsible for anyone having to google anything or not googleing anything at all. If it is console related problem, it's more like less than 50% chance you find an answer... Trust me, I have at times had to do something in console, and never found an answer with google. Google is not the God of ALL information... Not everything can be found with google. And not many people setting up a production server ask about things in console so the people that are just playing around have less information to feed off. Most people setting up a production server know what they are doing.



> **hyper_ch said:**
> 
On a server it is the same as teaching how to fish.

You didn't read my interpretation of that at all did you? I believe it was more proper.

> **hyper_ch said:**
> 
But it's nice of you if you tell them that there are much better ways on doing things ;)
 
... I never said it wouldnt be nice to do that... Again, if you clearly read my post, I said you could show him how to do it his way as well as help him out that extra step by telling him how to do it in console, the better way. That is what you want to do. So do it. Dont come attack me while I am trying to help him achieve his main goal. He has a reason to plug into it directly and use the GUI.

> **hyper_ch said:**
> 
Bad habits are hard to get rid off. 

I smoke, drink, and yeah so I am one who knows this already. By the way, your quoting seems off... Whats the bad habit? Setting up a server farm on a fiber connection? If your going to argue with me do it properly. I dont want to waste my time replying to your attacks on me and then doing all the work to figure out what this stuff means... Id rather go take care of my bad habits :)

> **hyper_ch said:**
> 
That's right. But before you do as you want you should know what you do - informed choice.

Thanks for agreeing with me lol but what does the rest of that mean? I'm not sure it's English! If one does what one wants, one already knows what one wants to do. The thought or decision process has already taken place!


> **hyper_ch said:**
> 
I refer again to the man/fish quote. This person has no clue about servers. That's why he asked how to install a gui. If you care a bit then you should tell him why it's generally considered a bad thing to do and help him to get it done the "right" way.

Yes, but no. If you care, but do not know exactly what he wants to do in the console, you cannot help him other than show him to install the GUI and also reccomend not using it in a production environment. Im not going to dig in, pitch a tent and stay here and teach him every little thing in console. That is his responsibility.

> **hyper_ch said:**
> 
I'm right on topic.

No, your topic seems to be "attack kthxbai2u who is helping this other person".

> **hyper_ch said:**
> 
The fact of the matter is that they use the same repos but if devs would have wanted a server to have a gui then they would not have created the server edition ;) just because you can install a desktop doesn't mean you should. Even if hey had seperated repos (which gives them a lot more work of administration to and hence less time on improving things) you still could install a desktop. Just grab the source and compile it ;)

I never said he should install a desktop. S/He simply asked me how to do it and I told him. S/He was also obviously aware that its not the ideal choice, but for whatever reason s/he still wants to do this.

> **hyper_ch said:**
> 
The point of the thread is that the TO has no clue what a server does. He may think that it's cool to have one and because of that he applies his mind-set of "must-have-a-gui". If he's serious about running a server the only proper answer is to give him an informed choice.
I see and understand that. He is here because he has _already made_ his choice. His mindset may not be "must-have-a-gui", you don't know that. He already knows one choice is console. I showed him how to do the other choice, which is what he asked how to do. That is more on topic than you. 

BAHHH kthxdone    I am not wasting anymore time with you ... I give up, You will never change. Just because you never have. You think its outrageous to use a GUI which you are wrong, it is not. If it is your only way out of searching for a day or so on something then you are smarter to take that path. To save time. And this guy is at home, probably has a real job, etc. Speaking of, I have a real job too. Gotta get ready to bust *** tomorrow. I my friend am a Genius :)

  Im sure buddy will get around to console eventually. Stop being so tight. It is the natural movement for a server. You eventually learn to ssh in console and then set that up. Until then it does not matter. He is not some massive serverfarm or anything.

Gotta go ...

Goodbye :)

Just go have a smoke and relax. Or if thats not your thing, grab a beer. Or several. :D

---

### Post by hyper_ch on 2009-03-12
> **kthxbai2u said:**
> Which I do not know why you questioned that statement. If there are no desktop related services ruinning, what amount of memory do you think the desktop is using?
So, if you deactivate the launch of the desktop are you 100% sure that all services that ware installed with ubuntu-desktop are being deactivated? I have my doubts on that... and that's why I questioned your statement. There's a lot more going on with a ubuntu-desktop install.

> **kthxbai2u said:**
> The point is that its a hell of a lot harder to find help on something console related. Refer to "Google" below lol.
No, the point is that it's a hell of a lot harder to find help on something gui related.

> **kthxbai2u said:**
> Yes, in a production environment. The guy is in his own home for Christ's sake...
So? Humans are creatures of habit. Use a single word 6 letter password for your samba server.. how many do you think will use the same word time and again? You might want to have a read here: [http://www.out-law.com//default.aspx?page=9860](http://www.out-law.com//default.aspx?page=9860) . So, telling even the "home server" guys what should properly be done doesn't hurt them. It can hurt them if they learn bad habits from the beginning.

> **kthxbai2u said:**
> As well, I meant it supports the GUI as in you can install it with no problems.
Just because it's in the repos and that is done because it uses less man power to manage a single repo stack fro server and desktops hence more work can be done on improving things...

> **kthxbai2u said:**
> Basically, any help you need with the GUI is *already there* because of the extensive amount of information/how to's on the desktop edition.
Basically any help you need with a server is already there because of the extensive amount of information on howto setup and manage server.

> **kthxbai2u said:**
> Obviously I do know how to handle Google, because i know resources for information on methods of doing things through console are scarce. I assume by you saying "cli" you mean the server version? Google one thing for console, then compare it to googling for how to do the same thing in desktop.
By "cli" I mean "cli". If you ever looked at this forum extensively you'll find that most help is done in "cli" form. Same goes for google.

> **kthxbai2u said:**
> **GUARENTEED** you will find 150% or more answers related to the desktop. If you don't, you dont know how to google. not me.
See above!

> **kthxbai2u said:**
> The original poster of this thread is trying to stay away from console and use the GUI.
Which is already the first serious mistake if he wants to setup a server...

> **kthxbai2u said:**
> The guy does not know HOW to use the console.
That guy switched from Mac or Windows to Linux. So he's willing to learn and he can learn. Not knowing now is no reason to not show him how to do thing properly.

> **kthxbai2u said:**
> So don't give him that answer unless you going to step him through modifying each config file and teach him extensivley how to use a console.
Or he could first conduct some research himself and then when he encounters a problem he can ask for the specifics ;) There's plenty of info out there, one just needs to know how to use google.

> **kthxbai2u said:**
> You joker.
???

> **kthxbai2u said:**
> The point was not that I know each and every service that is there that is added on after installing the gui, but was more that I was letting people know it is possible to remove them and start them manually.
If you have total control over your computer you can do anything with it... but the question still is, do you know what services are needed for what? what services are added by ubuntu-desktop install? which of those services will still be started even if you "deactivate" the desktop to start at boot? ....?


> **kthxbai2u said:**
> Like what? You have to put in some sort of bootable medium.,,  Which means a cdrom or usb device of some sort. Which means physical access. To install a distro, at this point there is nothing on the machine, so you cannot just ssh into it.
Wrong... here a few clues (look especially at the network section): [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

> **kthxbai2u said:**
> yes, for you and I maybe. Not for the original poster. S/He is however, the one responsible for learning how to do that.
Either it's simple or it's not.

> **kthxbai2u said:**
> Yes, I did start with winblowz. That does not matter.
Of course it does, I explained this before.

> **kthxbai2u said:**
> I agree to teach one to do things the proper way, but using the GUI does not by any means mean it is improper.
Look at the forum section here.

> **kthxbai2u said:**
> What if ssh fails? you can't for the life of you ssh into the box.
ssh doesn't fail ;) before ssh fails you'll have a whole lot of other problems.

> **kthxbai2u said:**
> Unless it's colo and someone else is watching it.
not necessarily...  actually in most cases personell at the DC does not look whether you're server is running - unless it's a managed server...

> **kthxbai2u said:**
> No, but someone starts the thread. It is just polite forum etiquett to stay on topic and help the original poster rather than try to out smart the person helping him.
I am right on topic as to point out what is the proper way to do thing. You're the done getting offtopic here.

> **kthxbai2u said:**
> The idea of the forum is to help him get through the single problem he posted about - maybe give extra pointers - and let him/her be on his/her jolly way! then s/he will come back to ask another question. Yay! people like to come back because they got their answers. Not because of one person attacking another person for helping him O_o I dont even think he is around anymore so when this is done im outta here because this is stupid waste of time.
Actually, the point of this forum here is:
> The Ubuntu Server team is working to make Ubuntu Server the best GNU/Linux server platform on the market.

This means working on simplifying the system administrator's life, while focusing on advanced features, rock-solid stability, and high performance. We want Ubuntu Server to be an attractive platform for the entire range of servers -- from makeshift, converted desktop machines, to carrier-grade server hardware. While our CD already comes with a list of standard setups, thus satisfying the most common use case, we're working on incorporating clustering and virtualization technologies for the higher end, and are developing software for simplified management of many Ubuntu servers.
Discussion regarding Ubuntu Server Edition. You get to the wiki page if you click on the "For more information on the Ubuntu Server Team, please visit their wiki page or Launchpad page."

> **kthxbai2u said:**
> It is unrelated. Look at the topic of the thread... He clearly wants to know if he can install a GUI on the server.
Look at the forum description, it's totally related.

> **kthxbai2u said:**
> Does Ubuntu server support GUI?
It's clearly about running a server.


> **kthxbai2u said:**
> no one said you do. not for ssh. but in the case of pluging into the machine like the original poster probably is, then s/he does need it running. Like I said though, s/he can start it manually.
Actually, you did:
> **kthxbai2u said:**
> Originally Posted by kthxbai2u  View Post
Or maybe you need the GUI to do things through SSH.

> **kthxbai2u said:**
> You cannot say there is NO advantage. There are. I have been outlining it all to you.
Sure I can... running a server is editing config files. No advantage of a GUI whatsoever.

> **kthxbai2u said:**
> It uses no more than the HD space.
Plus all the services that run that you didn't shut down.

> **kthxbai2u said:**
> Trust me, I have at times had to do something in console, and never found an answer with google.
Example?

> **kthxbai2u said:**
> Google is not the God of ALL information...
It's pretty close to it.

> **kthxbai2u said:**
> Not everything can be found with google.
Example?

> **kthxbai2u said:**
> You didn't read my interpretation of that at all did you? I believe it was more proper.
Of course in this topic learning cli is teaching how to fish ;)

> **kthxbai2u said:**
> ... I never said it wouldnt be nice to do that...
You never said it wouldn't be nice... but then you didn't do it either ;)

> **kthxbai2u said:**
> Dont come attack me while I am trying to help him achieve his main goal. He has a reason to plug into it directly and use the GUI.
You catch a fish for him; I teach how to fish.

> **kthxbai2u said:**
> If your going to argue with me do it properly.
That is your argument?

> **kthxbai2u said:**
> I dont want to waste my time replying
Then don't reply.

> **kthxbai2u said:**
> Thanks for agreeing with me lol but what does the rest of that mean? I'm not sure it's English! If one does what one wants, one already knows what one wants to do.
If one doesn't know what options are available how can one tell it's the best choice he made?

> **kthxbai2u said:**
> Yes, but no. If you care, but do not know exactly what he wants to do in the console, you cannot help him other than show him to install the GUI and also reccomend not using it in a production environment.
It's like giving kids alcohol and tell them it's bad for them. Or give kids a loaded gun and say don't play with it... If I don't know what someone wants I just ask. I'm sometimes as plain as "I have no clue what you want. Please rephrase". Actually, that's not even that uncommon for me ;)

> **kthxbai2u said:**
> Im not going to dig in, pitch a tent and stay here and teach him every little thing in console. That is his responsibility.
Nobody asks you to. But remember, this is the server forum. Don't hand him a loaded gun.

> **kthxbai2u said:**
> No, your topic seems to be "attack kthxbai2u who is helping this other person".
I'm just plainly disagreeing with the "oh I need a gui on my server" and those that "to get your gui on the server do ...."

> **kthxbai2u said:**
> S/He was also obviously aware that its not the ideal choice, but for whatever reason s/he still wants to do this.
Really? where? this person only said "on cli please..." that's no sign of it not being the ideal choice. IMHO it's rather a sign of not knowing any better.

> **kthxbai2u said:**
> His mindset may not be "must-have-a-gui", you don't know that.
Sure I know. Why else whould he ask for a gui?

> **kthxbai2u said:**
> He already knows one choice is console. I showed him how to do the other choice, which is what he asked how to do. That is more on topic than you. 
Please check again the ubuntu dev. wiki page.

> **kthxbai2u said:**
> I am not wasting anymore time with you ... I give up, You will never change. Just because you never have.
I still have hopes for you that one day you stop fishing for other people but teach them how to fish.

> **kthxbai2u said:**
> You think its outrageous to use a GUI which you are wrong, it is not.
There's nothing wrong with guis. there is something wrong with putting a gui on a server.

> **kthxbai2u said:**
> If it is your only way out of searching for a day or so on something then you are smarter to take that path. To save time. And this guy is at home, probably has a real job, etc. Speaking of, I have a real job too. Gotta get ready to bust *** tomorrow. I my friend am a Genius :)
That's you're argument?

  Im sure buddy will get around to console eventually. Stop being so tight. It is the natural movement for a server. You eventually learn to ssh in console and then set that up. Until then it does not matter. He is not some massive serverfarm or anything.

Gotta go ...

Goodbye :)

Just go have a smoke and relax. Or if thats not your thing, grab a beer. Or several. :D[/QUOTE]

---

### Post by bapoumba on 2009-03-12
Time to let the servers cool down, for 24 hours. See you tomorrow :)

---

