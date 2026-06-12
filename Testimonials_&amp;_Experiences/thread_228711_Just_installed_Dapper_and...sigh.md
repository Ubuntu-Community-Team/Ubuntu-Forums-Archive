---
title: "Just installed Dapper and...*sigh*"
date: 2006-08-03
forum: Testimonials &amp; Experiences
---

### Post by ABEZ on 2006-08-03
I am a long time Windows user and I have tried most of Microsoft OS versions. I have been getting tired lately of the whole philosophy that Windows are based upon and been considering a switch to a free software platform. A few years ago I had tried Mandrake Linux but could not get my hardware to work with it so I gave it up. Just the other day though, I checked the Ubuntu site and because I found good feedback from the community I decided to venture once again into the Linux world. So after a little research on drivers for my hardware I launched the CD to see how far I would get in terms of basic functionality. I was really impressed that the Live-CD mode got almost all of my hardware to work automatically. I also found the graphic interface very good so I went on with the installation right away.

Now here is where the disappointments start hitting:

1. The partitioning setup routine is really confusing and I do not understand why it could not be more explanatory. It led me into some trouble and unnecessary time waste.

2. The password with non latin characters I entered during installation was not recognised when I tried to log on for the first time. This forced me to go through the installation loop once more which although impressively fast, was still irksome.

3. What on earth happened to network support? It worked just fine in the Live-CD mode! I am using Windows to get in the forum right now :roll:

4. Why do I need to go into so much trouble to get access to non-Linux partitions? Why do I need to delve into a heap of How-to's and search for that magic shell command to copy and paste just to get the default file exploring functionality that Windows offer? This is basic stuff people. I just want to browse my files on other drives/partitions and not have the OS arbitrarily decide that I do not have the right to. This is my computer and I should not have to read a How-to explain that to Ubuntu! :confused: 

I respect people who try to offer a platform free of proprietary bidding but I think free software lacks a sense of direction. There is no merit in being free if it is not connected...to users' basic needs. 

I struggled between posting a help request on the newbies' section and bringing this here for discussion. I guess it got to me that the effort I put the last couple of days into preparing and installing this OS was a waste because of a non comprehensive implementation of an otherwise good idea for a software platform. It is not as if I have not done my homework and am too lazy to configure my machine. It is just too disheartening to constantly have to turn to the forums to get answers that a help file associated to the real world could answer a lot more efficiently.

:-?

---

### Post by FenrisAbraxas on 2006-08-03
> 

1. The partitioning setup routine is really confusing and I do not understand why it could not be more explanatory. It led me into some trouble and unnecessary time waste.


I agree, for intermediate Linux users is pretty intuitive but not for the novice.

But there are documentation, dont expect to have a 10 pages introduction to the partitioner.

> 
2. The password with non latin characters I entered during installation was not recognised when I tried to log on for the first time. This forced me to go through the installation loop once more which although impressively fast, was still irksome.

That's a risk you should take, that's why most pages and systems warn you to just use latin chars and just some special chars.
> 
3. What on earth happened to network support? It worked just fine in the Live-CD mode! I am using Windows to get in the forum right now :roll:


That's indeed a problem, if the installer worked well with the network it should load the same modules as the live cd.

> 
4. Why do I need to go into so much trouble to get access to non-Linux partitions? Why do I need to delve into a heap of How-to's and search for that magic shell command to copy and paste just to get the default file exploring functionality that Windows offer? This is basic stuff people. I just want to browse my files on other drives/partitions and not have the OS arbitrarily decide that I do not have the right to. This is my computer and I should not have to read a How-to explain that to Ubuntu! :confused: 


Try to acces non windows partitions with a standard Windows XP SP2 install.... no, you can't :-k , try again.... :-k  nope, you still can't acces ext3 partitions, or reiserFS.

Now that's the windows philosophy you got tired right? Here on Linux you can acces every type of partition (or near almost every file system) and is not the OS is deciding for you that you can't access those drives, the OS is just waiting for you to tell /etc/fstab where is the partition and where to mount it (weird thing, when i installed ubuntu on a friends box the installer adjusted all the drives in fstab and configured with no problems the dual boot).

If you got tired with Mirosoft ideology and want to try something different don't expect to work exactly the same as windows :P. No offense but you sound like :

"Im tired of Windows, installed GNU/Linux but it's not windows so i'll return to Windows."

If you want to stay in the Penguin world there's a huge community ready to help and solve your problems. In the other hand if you want to stick with the windows world, theres a tech support department that will be 24/7 ready to rip off your money out.

Good luck in YOUR CHOICE :)

Edit: Adjusting the post (thanks Lord Illidan last time i need windows to see my linux partitions i had to pay).

> **Lord Illidan said:**
> You are misguided. Ext3 and reiserfs access can be done for free from Windows. Stop saying stupid things like this.

[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://yareg.akucom.de/](http://yareg.akucom.de/)

Windows doesn't give you Ext2-3 ReiserFS read/write support by default, and Linux does for vfat and read acces to ntfs (write support is experimental), it's just a matter of minutes to configure /etc/fstab if it's not configured by default after the installation progress.

---

### Post by eXisor on 2006-08-03
Your network problem is probably easy to fix. Every time I've seen a post saying it worked on the Live CD but not installd it's been because two network drivers have been loaded for your card. They are dfme and tulip. In a terminal window, type 

```
lsmod
```

if you see dfme and tulip, type

```
sudo gedit /etc/modprobe.d/blacklist
```

and add 'tulip', without the quotes, to the bottom. Save and reboot and your network should work.

---

### Post by eXisor on 2006-08-03
Give yourself a chance. Remember how you first struggled with windows way back when? 
New users to windows find it difficult, counter-intuitive and highly unstable. Oddly, the more they know it the more stable it becomes and the less service/help requests they send. Expect the same of any linux distributuon. It is different, and counter-intuitive and some things are a down-right hasstle. 
Windows networking also doesn't work right out the box, you have to set it up pretty exactly to get any joy out of network neighborhood. 
Just be paitient and have fun with it. Once your box is all set it I'm sure you'll enjoy the very difference you now find so infuriating. It's not just the same old thing, but a fundamentally different OS and philosophy.

---

### Post by Lord Illidan on 2006-08-03
> Try to acces non windows partitions with a standard Windows XP SP2 install.... no, you can't :-k , try again.... :-k nope, you still can't acces ext3 partitions, or reiserFS. Hmmmm use paypal to pay a hundred bucks to get some app that let you use ext3 partitions! yeah great idea!. And oooh damn, you installed ubuntu in reiser, how about another hundred bucks to browse reiser partitions? Yeah paying for things that the OS should do by default is BASIC STUFF (quoting yourself).

You are misguided. Ext3 and reiserfs access can be done for free from Windows. Stop saying stupid things like this.

[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://yareg.akucom.de/](http://yareg.akucom.de/)

---

### Post by ABEZ on 2006-08-03
> That's a risk you should take...
How about the installer warning me when I entered it during setup. I gave me all sorts of warnings on the other fields, except the name. Anyway, that is just an annoyance.

> Try to acces non windows partitions with a standard Windows XP SP2 install.... 

I expect Linux to come as a better alternative compared to Windows. Would you not agree that if Linux wishes to establish itself as a popular platform it has to take into account that this is a world of users who keep their data on a windows filesystem. If the free software community wishes to help the average user break free from proprietary slavery then at least the transition should be made more straight forward in this regard. Why should there be a need for a How-to on such a trivial matter? The interface ought to be more intuitive in my opinion.

> "Im tired of Windows, installed GNU/Linux but it's not windows so i'll return to Windows."



That is inconsiderate to tell to a person who has put so much effort into trying to make this platform transition. I suggest you should read again what I wrote. My complaints are not about an unpleasant unfamiliarity but rather about poor functionality.

> If you want to stay in the Penguin world there's a huge community ready to help and solve your problems.

What I wish is this community would start conveying this spirit of helpfullness into a more thorough working-out of the user interface in Linux. Help people help themselves through a more comprehensive UI and a better implementation of built-in help functions! Unless the community is nothing but undiagnosed computer elitists who are content with their narrow audience of How-to's and "copy and paste" shell commands. 

Open up free software community and do not rush into dismissing  well-intented criticism.

---

### Post by Lord Illidan on 2006-08-03
I apologise in the name of the community, it's just that your criticism has been levelled so many times at us that we get on edge.

On the otherhand, researching a few howtos, and looking at the wiki [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/)

will not kill you.

---

### Post by ABEZ on 2006-08-03
> On the otherhand, researching a few howtos, and looking at the wiki [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/)

will not kill you.

That is what I am trying to communicate here. I do not mind doing my homework. I have done it many times in the past and I am doing it now with Ubuntu. But there are some issues that I think...you know... they should not be issues!

---

### Post by eXisor on 2006-08-03
Abez...
Look, I agree with you. Some of the things I had to do to get my box going on ubuntu should not have been necessary. But then again, some of the things I had to do on windows years ago should also not have been necessary. Nowadays windows is a little better. Ubuntu is getting there, milestone by milestone. By Edgy or the version thereafter it'll be right up there on ease of installation.
Meanwhile, accept the current state and give yourself a break. This is fun stuff, a whole new world and it doesn't cost a dime... apart from bandwidth and a few cd's.
Also recognise that windows doesn't work on old hardware anymore. They just don't support it, whereas xubuntu resurrected by 233mhz 64mb ram piece of junk and is giving me a lot of joy. Without linux it'd still be sitting in the garage.
The linux community has a never say die attitude which means many of these forum users are working away at making things better, automating this and that, sorting and helping where they can.
Yes, they do get a bit passionate and proprietory about linux sometimes and I'm frankly sick of the inherent and neverending competition with windows. 
I believe give windows its due... we wouldn't be as far with pc's without them. But linux is great too. Something new and different and fresh. I'm loving it. Give it a chance and you will too.
Spend a few days on the forums helping people resolve the problems you've overcome and see how soon you're won over.

---

### Post by GuitarHero on 2006-08-03
All your problems can be fixed with the help of the community.  This forum is a wonderful resource for almost all of your problems.  Don't give up, it's better in the end for most.  Have you ever partitioned a hard drive before? Ever installed windows?  If you have then I don't know what the problem with the partitioner was, because windows is much more confusing to install.  If you hadn't partitioned before or didn't even know what it was it would have been a good idea to find an ubuntu installation tutorial.  pcmech.com had a couple I think.  Don't be afraid to ask questions.  You may get a couple of people with attitudes that will turn you away but most of the people on here are here to help.

---

### Post by 3rdalbum on 2006-08-03
Most Linuxes mount Windows partitions by default. I'm not sure why Ubuntu doesn't, but some people have said that it mounts theirs by default.

I'm surprised I seem to be the only person who's written a script to automate the mounting of these partitions. If you want it, PM me.

---

### Post by ABEZ on 2006-08-04
We just go around in circles here. Everybody, your offer to help is well appreciated but this is not what this thread is for. It is all about Dapper's (Linux in general if you may) user friendliness. My argument is that it should not be expected from new users to go through all this trouble just to browse their files or have net access.

Take my example into thought for a moment: 
I go through a lot of unecessary trouble* to install Linux and in the end can not get any elementary usability. I have no net access to use online help efficiently because I have to use Windows to find some info and switch back to Dapper to try it out, back to Windows if it does not work and so on. I am an experienced computer user who has gone through many hours of seting up and configuring hardware and software components on a Windows environment and has helped others with similar problems, an enthusiast of technology. Even if I insist and finally get Dapper to work after some days what would make an average inexperienced Windows user go through this ordeal? I believe he would not get past installation. I know that even if I set it up right, I cannot recommend it as a viable platform transition to any of my acquaintances.

 You can turn a blind eye all you want, but the fact is that Linux, after so many years of development, remains a very abstract experiment and cannot gain mass appeal due to poor basic functionality.




(*= mainly, the installer should have explained the partitioning options in a more straightforward, comprehensive manner without leaving into obscurity whether and how this will affect existing data structure etc.)

---

### Post by eXisor on 2006-08-04
You say you help windows users with their problems, so you acknowledge windows is also not perfect. Why expect linux to be?

But ok, I'll stop trying to help you.

---

### Post by ABEZ on 2006-08-04
> **eXisor said:**
> 
But ok, I'll stop trying to help you.

 Someone puts forth some constructive criticism and all you can respond with is some "Fine whiner, no more help for you then" attitude. I am bringing a topic for discussion here. If you want to join do it with an argument.

---

### Post by eXisor on 2006-08-04
ABEZ: I have. 
I said repeatedly, albeit subtely, said you are not approaching ubuntu with the same attitude you used with the various windows incarnations. I said you forget how difficult windows was. I said you acknowledge you have to help some windows users, but expect linux users to need no help. You refuse to address these points, and simply repeat what you said at the start.
I pointed out how different your attitude is now to what it used to be and how contradictory you are being. You ignore that.
I encouraged you to be patient and to show a little respect/gratitude for something that is altogether free and a lot of people have contributed towards, and you ignore that too.
I tried, subtely at first, but then more directly, to show you it is your attitude and bad memory that is the stumbling block. You ignored both.
You are not the first to make these points, and I even said I agree these things should not be difficult. If you know linux, they aren't. If you know windows the various windows issues aren't. If you don't, welcome to the learning curve. That's life. What do you expect?
If you don't address the various ppoints people make in your threads of cource they are going to give up on you as a hopeless case.
You presume to be constructive, but see it only in yourself.
Reread all the posts and judge for yourself.

---

### Post by ABEZ on 2006-08-04
Exisor I think you do not know what you are talking about. Anyway, I will not allow this thread to end in a flame war.

---

### Post by eXisor on 2006-08-04
Sigh... And still you do not address the points.
Goodbye.

---

### Post by kriding on 2006-08-04
I think the point people are trying to make is that you are just inexperienced with Linux. I am a long time windows user as well, and I found Ubuntu an absolute pig to set up, however, after many hours of playing around and breaking my install, I am more then proficient at reinstalling and repartitioning Linux, however, there are many thing I cannot do with it yet...that does not make it bad, it just means I don't know it yet.

Linux is different and on a distro level, very much a work in progress, and to compare it in anyway to windows is unfair, for example, Linux is so much better for security and configuration then windows has aspired to...does that make linux better?...by your arguments, no, because windows is easier to set up.

More importantly..why should Linux emulate Windows in anyway? yes things can be more user friendly, but why go to the hand holding levels of windows, where by comparison, it controls your machine, it says how things go and how they work..Linux is freedom and in many respects a far superior OS despite it's shortcomings.....and windows has far more

---

### Post by ABEZ on 2006-08-04
> **eXisor said:**
> Sigh... And still you do not address the points.

The points ellude you. 
Farewell

---

### Post by dgold1958 on 2006-08-04
In fairness to the Linux community, you obviously have a lot of experience with MS Windows and this skews your view a bit.   There are millions of people using MS Windows who are entirely clueless about using computers and have great amounts of difficulty when MS Windows decides to not play nicely anymore.

I doubt that the average MS Windows user could partition his/her hard drive.  When they get slammed with a virus, they are completely helpless.  Installing software is not always an easy proposition, either.

I just spent hours on the phone with my dad.  He is running W2K pro on his computers at home. He somehow managed to get a very nasty virus on his computer and I was trying to help him get the problem solved.  The ru to the entire thing is that I am 5,000 miles away.  After trying to guide him through some possible solutions, we had to give up.  He did not understand what I was trying to get him to do.

I told him that he should reinstall W2K pro, since this would be the easiest solution.  I explained to him that all of his data would be gone, since he had to format the harddrive, in order to ensure that the disk was clean.  I instrucuted him to stop using IE, install an anti-virus program and a firewall.

He tried to install W2K, but it asked for drivers for his hardware and the only possibility was by downloading the drivers from the internet.  Difficult to do when you have no OS installed.  He gave up and took the computer to a specialist and paid $150US for the guy to format the drive and reinstall W2K for him.

Of course, I told him that it would have been cheaper for him to buy XP Home, but he did not listen to me--the specialist was a friend of his son-in-law and he expected the price to be around $25 for the service.

Now, you can claim that he should have upgraded long ago; however, he did not feel the need to, since his computer was running just fine.  It is hard to fault his decision, since paying the MS tax everytime they come out with a new version of their "OS" does not make sense, either.

Can Linux be frustrating at first?  Sure.  So is MS Windows, and that does not change over time.  I think your issues could have been readkly solved on this forum.  There are some pretty knowlegable people here. I have asked question--I have been using Linux since 1996--and always gotten quick responses with solutions that worked.  Is Linux perfect?  Of course not.  Is MS Windows perfect?  Of course not.  I do like the fact that I can operate my computer, and surf the internet without worrying about spyware, virii, ad-ware, etc....   I do like the fact that I have infintely more options about how I want to set up my computer.  I do like the fact that Linux, with the help of KDE and Gnome, plus the work done on the installation and setup process, has become a very user-friendly OS.

---

### Post by FenrisAbraxas on 2006-08-04
> **ABEZ said:**
> 

 You can turn a blind eye all you want, but the fact is that Linux, after so many years of development, remains a very abstract experiment and cannot gain mass appeal due to poor basic functionality.



Well linux is ready for the masses already, it's just that people start to learn that nothing is easy, and nothing will work 100% out of the box. You also have to remember that ALL program will have bugs for 90% of the Linux users windows partitions are recognized and ready to use by default. If that was not your case, sorry.

But saying that a software that have bugs is not ready for the masses is telling that software should dissapear because a newbie will not know how to use it.

Edit: Linux is not an experiment, Linux is a PROYECT, developed and maintained mostly by volunteers. Growing fast with companies supporting it (IBM, Novell for example), and remember that the choice is yours, mine is staying with Linux and the GNU, i've seen the evolution of Linux and i think right now Linux is a better choice than Windows for desktops and servers.

But it all depend on your needs. Anyway remember that this community will be ready to help you, and probably if you are a programmer you can help with the development of the installer, if you aren't a programmer or don't want to get involved you can always submit bug reports.

---

### Post by ABEZ on 2006-08-04
dgold1958,
your point is understood. But I do not think Windows is as frustrating as Linux for the first time user. I know I have been through devastating computer panics and managed to restore functionality. But the problems I am facing with Linux leave me hopeless. I can not even post a help request because I have no idea where to begin. And it seems to get worse with each attempt to re-install. Add this to the fact that I have to go back and forth from Linux to Windows to apply any idea for a solution I find online and you should get a complete picture of my idea of "frustration". And to think that I really want to make the transition and have come prepared with drivers and everything! Maybe I will get this to work, but what can I say to any clueless Linux-curious person who asks me: "So what about this Linux thing?" "Well...uhhh...you know, there is a lot of help out there..."

---

### Post by ComplexNumber on 2006-08-04
**ABEX**
go and make yourself a cup of cocoa and chill out for a bit. given what you've said, it appears that you are just being too hard on yourself(and linux). 


> 
But I do not think Windows is as frustrating as Linux for the first time user.the only reason why you find windows user friendly is because you are used to it. if you can remember the first time you used the windows OS, would you honestly say that you would intuitively and instinctively try to find the 'Start' button to shut down the computer? i doubt it - the interface alone is a complete ill-designed mess. even the experts agree. i can tell you for a fact that windows noobs experience similar frustration to linux noobs. why? because its something that they aren't used to.

---

### Post by ABEZ on 2006-08-05
> **ComplexNumber said:**
> 
 if you can remember the first time you used the windows OS, would you honestly say that you would intuitively and instinctively try to find the 'Start' button to shut down the computer? 
No, but as I was exploring around the various aspects of the computer (because in the begining it's just that: the computer, not the operating system) I came across this feature and it was bundled with a tiny bit of information which gave me a clue about its function. And this is the main process through which I educated myself on the use of Windows. Exploring, trial and error, explanatory texts in the UI, right click-"What is this?" menus and whatnot. At first I did not even have access to the Internet to search for help. But during this course I never bumped onto a ridiculous situation where the OS would not allow me basic computer functionality like exploring my drives. This is what I am facing with Linux. Had that happened to me back then, I would have given up with the computing world. 

So I guess my argument here focuses on the crippling factor of Linux's lack of a comprehensive, elementary built-in help function and a self explanatory user interface. Something which will introduce you to the basics, put you into prospective. The existing how-to's and help files seem inefficient and nonsensical at this early stage of my introduction to the Linux world. 



> go and make yourself a cup of cocoa and chill out for a bit. 
I never understood the culture of people who use stimulant substances to...[COLOR="Cyan"]reLAX[/COLOR]. :-k It certainly does not relate to my biochemistry.

---

### Post by gannic on 2006-08-05
ABEZ I echo your sentiment - I was instantly impressed with ubuntu; my first linux system. However, when I it came to connecting to the internet to get help, I couldnt because my wireless card, while claiming to be active, didnt include the activity of connecting to my router amoung its endeavours. I was not upset by this one bit - I am experienced with windows and things rarely work first time on it either.

Anyway off I go to the forums - using....windows and after reading pages and pages on ntwrapper (or what ever its called) I  am still none the wiser on how to fix my problem. Help was along the lines of 'take the file and....'(assume you know exactly how to use the linux shell and use one word to describe 15 steps). I had decided to head out and find a book...then i find some wizzkid has written a special driver for the ACX111 wireless chipset - great. However once again there are no less than 8 ways of using it, and the download file is totaly different for each....then I see a post talking about the driver folder...I go looking...and find it...and find my firmware is already on Dapper!...but its using the USB drivers (as default)...So now all I have to do is delete the contents of default and copy the contents of the right folder in....oh dear...copy and paste doesnt work...look for admin login to enable paste or delete...nowhere to found. Back to the forums..read some more...I can change the module.d (or something) option file to load the right firmware...no I cant..I cant save it once I have changed it. So in total now I have spent around 2 hours trying to get around not having cut, copy and paste. I will stick with it, and surely get there in the end....but it shouldnt be like this. I am talking about copy and paste!

---

### Post by ComplexNumber on 2006-08-05
>  I never understood the culture of people who use stimulant substances to...[COLOR=Cyan]reLAX[/COLOR]
the "cup of cocoa" was merely a metaphore.

---

### Post by ABEZ on 2006-08-05
> **ComplexNumber said:**
> the "cup of cocoa" was merely a metaphore.
Ah, allow a man some digression! :)

---

### Post by gannic on 2006-08-05
Hooray - I have copy, paste AND edit. Its just a matter of time until I break something permanently now.

[http://www.psychocats.net/ubuntu/permissions.php](http://www.psychocats.net/ubuntu/permissions.php)

By the by -  as a result I also have wireless internet access from Ubuntu - but copy and paste made me happiest.

---

### Post by ezsit on 2006-08-05
> We just go around in circles here. Everybody, your offer to help is well appreciated but this is not what this thread is for. 

So is this a troll question?

> It is all about Dapper's (Linux in general if you may) user friendliness. My argument is that it should not be expected from new users to go through all this trouble just to browse their files or have net access.

Ever install Windows, any version? It ain't user friendly. I've installed Windows, versions 3.1 through XP, on various computers and I almost never had a working network card, optimized graphic drivers, and sound working immediately after installation. Windows has never natively supported filesystems other than FAT and NTFS (OK, they did support HPFS briefly, but only because they co-owned the code for OS/2). Good luck getting Windows to recignize your Linux partitions without jumping through some configuration hoops.

> Take my example into thought for a moment: 
I go through a lot of unecessary trouble* to install Linux and in the end can not get any elementary usability. I have no net access to use online help efficiently because I have to use Windows to find some info and switch back to Dapper to try it out, back to Windows if it does not work and so on. 

I've used Windows for years. I've used OS/2 for years. I've tried BeOS, QNX, Solaris for x86, Unixware, NeXTstep, FreeBSD, and probably a couple others. Now its Linux. I had to make sure my hardware was compatible BEFORE I attempted installation. I had to assemble the collection of driver software and be prepared during installation for any problems. Windows is no exception. Linux has finally gotten to the point of recognizing AND setting up MOST hardware automatically - a feat that Windows still cannot do.

> I am an experienced computer user who has gone through many hours of seting up and configuring hardware and software components on a Windows environment and has helped others with similar problems, an enthusiast of technology. Even if I insist and finally get Dapper to work after some days what would make an average inexperienced Windows user go through this ordeal? 

No one is forcing anything on anyone. This is all voluntary. It is also free. I suggest you ask yourself what you really want (expect) from a free, hobby oriented, operating system. 

> I believe he would not get past installation. I know that even if I set it up right, I cannot recommend it as a viable platform transition to any of my acquaintances.

No matter how easy the installation and setup of Linux becomes, it will never appeal to the masses of computer users. If every computer user were forced to install their operating system and get it working properly, we'd have a substantial drop in the number of computer users. Most people do not care to be bothered with this chore and I would bet most people couldn't understand the basic concepts required.

> You can turn a blind eye all you want, but the fact is that Linux, after so many years of development, remains a very abstract experiment and cannot gain mass appeal due to poor basic functionality.

Back in 1995 when I picked up a copy of SuSE 5.2 at a local Borders bookstore, the installation was nightmarish. Eventhough I selected English as the language, the entire Sax (XFree86 setup program) was in German. I made it through the first time and got a screen that filled 3/4 of the monitor and a German keyboard layout. My next install attempt was much better, I got a working X system. I could never get the PPP dailer to connect, my printer and scanner didn't work. I gave up to easy.

I tried different versions of Linux through the years, each one had it's quirks. I finally settled on Mandriva a couple of years ago. Now its Ubuntu. It took almost ten years of other people developing the software for ME to find it useful. I am grateful and happy to have opensource software available. Now that I am Windows free (except for work), I feel free.

---

### Post by Steggy on 2006-08-05
Okay, I'm probably going to come off as a Linux zealot or something this post. That's not the case. I still use Windows. I want to continue using Windows. I LIKE Windows. I just like Ubuntu better. I have no problem with people liking an OS (whether another Linux distro, Windows, MAC OS or any others) better than my favorite. What I do have a problem with is them misrepresenting--either through ignorance or falsehood--what their OS of choice can do.

So, I'd like you to try a little experiment: Format your harddrive. Now, put in your Windows install disc. Install it. Boot up. How much functionality do you have, now, right out of the box? 

None, that's how much. Nothing will work the way it's supposed to. Unless you're running normally at incredibly low resolution, your monitor won't be working quite correctly. You likely won't be connecting to the Internet. That's easy, you say, I'll just put in my driver CD(s)... Wait, no, that's cheating. This is straight out of the box.

Okay, what programs do you have to work with. You have IE (without the ability to connect to the Internet.) You have Wordpad and Notepad. You have Paint. You have Solitaire I guess if that's all you need, you're ready to go right out of the box.

Now, format your computer again. Install Ubuntu. Dump everything on to one partition (NOTE: I do not suggest doing this. You should always put your /home directory [if nothing else] on a separate partition. This is only to simulate what Windows does by default.) When it's up and running, how is everything running?

If you're using an ethernet card, and using a connection that's always on (like cable), you'll probably be able to connect to the Internet fine (I've installed Ubuntu on 3 computers with this set up and the Internet has always worked.) If your using an ethernet card with a PPPOE connection, you'll have to run a setup program, but then you'll be fine. In both those cases you're ahead of Windows.

If you're using wireless, you'll likely have more trouble than this. You'll have to get the right drivers and get them installed--however, you'd have to do this in Windows as well. At this point, I'd say they're pretty much even. Windows may have the advantage here, if you consider that a lot of companies foolishly don't make drivers for Linux, so you have to get another program (ndswrapper in my case, which was on the Ubuntu installation disc) in order to get those drivers to work with your card.

Your monitor should be working well. If you're like me, and you use a high resolution (1280x1024) you might need to edit a file to get it working. By default, Ubuntu detected up to 1024x768 for me. I think that's pretty good compared to Windows's default of 800x600 whenever I reinstall it.

Now, what programs do you have? You have a web browser, so you're on par with Windows there. You have an entire Office Suite--as well as your basic text editors (GEdit for GUI and more than one on the command line, though I personally only use pico/nano.) You have a bittorrent client. You have the ability to make and mount ISOs built in. There's more, but that's all I can come up with off the top of my head. (To be fair, I've probably missed some programs that come by default with Windows as well.)

Now, let's try a third and finally experiment. You have leave this Ubuntu installation on, or reinstall it and put your /home directory on a separate partition. Whatever the case, just have Ubuntu installed on your computer.

Put in your Windows install disc, boot up, and start installing. How much instruction do you get on how to partition? In fact, I'm pretty sure your can't actually install Windows without destroying your Ubuntu installation. But let's pretend for a second that you went ahead and carved out a big enough chunk for Windows beforehand, either during your Ubuntu installation or by using another partitioning tool later.

So, install Windows... Reboot your computer, and then try to boot into Ubuntu. You can't do it. Windows wrote over your MBR, and now it's the only operating system you can boot into. Finish booting into Windows. Now, go and get a file from your / or /home partition. What's that? Windows can't find those partitions? But I thought only *Linux* wouldn't let you see all of your harddrive (or harddrives) by default!?

To sum up: you've never installed Windows with another operating system already on the system. You've never installed Windows without the drivers for all or most of your hardware at hand. I've done both those things. Neither is anywhere near as smooth as doing those things on Ubuntu.

You talk about a "normal" user switching to Ubuntu: How did this "normal" user switch to or start on Windows? They bought the computer from someone who had already installed Windows on it, including all the drivers the computer needed. Same things with Mac OS. Now, imagine buying a computer with Ubuntu (or any other distro of Linux) already installed, along with any drivers it needs. Just as simple, no?

A final word: I use Windows and Ubuntu. I like them both. I know a lot of each's strengths and weaknesses. They both have them. There's no denying that. Just don't misrepresent what those strengths and weaknesses are.

---

### Post by em3raldxiii on 2006-08-05
Kay, I want to defend ABEZ a little here.
 
ABEZ:  I sincerely appologize for the frustrations you are going through, both with Ubuntu and with the forum.  I feel your pain, and I know what you are getting at.  Luckily, it's folks like *you* who really help the development of Ubuntu (and linux in general).  Just that I don't think veryone realizes this.
 
One of the critical aspects here is that in many situations, when you install Windows, it came with the computer and may actually be a "special" version of the OS that is intended for that boxed system.  I am sure you understand this, so I won't milk it to death.  Everything just works in that situation.  (well, sometimes it doesn't but 'technically' it does)
 
Also:  Linux is still not perfectly supported by hardware vendors, so drivers can be an issue, especially with latest hardware, so voila, it doesn't work!  What a pain this is, especially for those of us who are not really familiar with Linux.  Especially in the case of a network card!  But then, as others have said, this problem still occurs commonly in Windows (it even happened to me with XP and an onboard nVidia network controller a while ago)
 
One of the problems too, is that Ubuntu, and Linux, since it is written and edited by people who *know* linux, often assumes that the user *knows what is going on* when in fact this is rarely the case of new users.  And you are right, a little more explanation during installation could alleviate some of this.
 
Also, I think the installation should have a "super-simplified" option for new users, with some explanation here and there about what is giong on.  For example, using this super simple installation path, don't ask me if this is the right way to partition my drive ... cuz maybe I don't know ... just do it, if it's default, I trust Ubuntu.  Don't ask me about Hostname ... I mean, as a newbie user, maybe I don't understand that at all (even with the included explanation).  Instead, just ask "what do you want to call the computer, use a pet name if you are not on previously established network".  During installation, have Ubuntu scan the computer for other partitions, if they exist then have a prompt:  "Ubuntu has discovered you have another hard drive or partition that is formatted in Microsoft's NTFS format.  Do you want Ubuntu to connect to these drives and make them accessible within Ubuntu?"  And if you select YES, then put an icon on the desktop for access to that drive, as well as in the "places" menu.
 
I think what Ubuntu really needs is a super-newbie like ... my dad ... to fire it up while sitting with some Ubuntu Admins.  As it goes along, the admins can make notes about what my dad screws up, so that in the next release this doesn't happen.  Especially when you consider that LOTS of people in the world do not have high-speed internet, and you have to admit, without highspeed, Ubuntu would have serious issues.
 
So there you are ... ABEZ, I feel your pain :D

---

### Post by ABEZ on 2006-08-06
That was brilliant. You just restored my hope in the free software community. Thank you em3raldxiii. It is detrimental to the advancement of the Linux world that constructive criticism is drowned in the prevalent fruitless confrontation of OS patriots. I see now how easy it is to get sucked into this.

Your suggestions on the development of Ubuntu is the kind of feedback I was aiming to incite when starting this thread. Now, how do we get those Administrators working on those splendid ideas...

---

### Post by Upochapo on 2006-08-06
Dear Abez,

First of all hello!  I am glad that even after your level of frustration with getting Ubuntu installed that you are at least still here.  I am still new to this operating system as well.  I hope that you take the time to reread the posts in this thread.  Emerald was not the only one who defended you.  All the others did as well.  Reread and you will see.  They acknowledged the problems and understood what you were saying.  Maybe it was just emeralds wording that really hit home.  But he didn't really say anything differently than what the others did.  Read steggs experiment.  You don't have to do them, just play out the scenarios in your head.

Y'know.  As far as documentation is concerned, windows isn't a heap better.  Do you know how many times I have had to research only because I end up at the "start the troubleshooter over" link in windows help system?

In all honesty, are you really being fair to the linux community?  How much did you pay for Ubuntu?  You are placing expectations on people who for the most part don't get paid very much or anything at all to contribute.

One of linux's greatest weaknesses is documentation/user friendliness.  You are right.  I too have gotten frustrated with it and getting things to run correctly or finding an answer to my specific problems.

No one was confrontational.  This is exactly how this thread played out.  You posted a topic with a high amount of recently acquired level of frustration.  Why?  Probably because you so desperately wanted to really give this operating system a real chance, only to end being defeated by lack of information that you did not have on hand.  Some people came to the call and responded by acknowledging your frustration and trying to get you to understand at the same time that yes, there is a problem but...

So, what happens?  These "buts" are thrown in there and so many often times are misinterpreted. As was in this case.  On both sides if you still see that there were two different sides here.  There was only ever one side and that was your side, which others came to.

It is my sincerest wish that you be able to get a working Ubuntu OS so that you may give it a real try.  Expect some compromises and differences.

I do not know the links right off hand, but I'm sure there is a way to contact the proper individuals to address this issue.  And, yes, I was just as mystified about the install process as you were, except I hosed my windows OS...oops lol.  And, no not everything went according to plan the first try through.

A suggestion might be would be to hardwire to ur router, if you have an ethernet card installed or on hand?  Ubuntu seems to be pretty good with those and that may allow you to help surf the net for answers for the wireless part.  Just a suggestion as I don't know your whole setup.  After hosing many installations of different operating systems I have learned to be creative with solutions.  Take care.

Upo.

---

### Post by Bragador on 2006-08-06
Well I don't know what you did but I installed for the first time Linux 3 days ago and it went well. It did take me 3 or 4 hours though. Especially since I had to go online and read about partitionning and why I had something classified as a hidden partition on my laptop. I killed my D: and gave it to Linux on my xp laptop and kept my C: for windows. I decided not to kill my hidden partition just in case and voilà ! The rest was smooth.

As for media support I simply installed vlc media player (I was already using it on windows) and everything works out of the box. 

So for me the installation was easy. I did freak out in front of the partitionning screen at first though so I back your claims for that.

---

### Post by em3raldxiii on 2006-08-06
Yeah, sometimes it's just the wording.  I think the big issue isn't that "well, Windows is tough so you shouldn't place expectations on Ubuntu", it's not about that at all.

Pretend for a second that Windows doesn't exist.  Imagine that ALL you had to choose from are Linux distributions and we want to make Ubuntu the best one.  Now, how can we make it better so you don't have to "understand" it on the level of a computer hobbyist to make it all work.

I am one of those computer hobbyists, so I tend to roll up my sleeves and get into it whether I have troubles or not.  But I know a vast number of people who run businesses, work as secretaries, etc etc.  They don't want to have to deal with all this stuff.  Now, in the case of Windows we have computer techs to pay who come fix stuff and make it all work, but we aren't to that level with Linux.  Not to mention that being that there are so many different distributions it presents a fundamental problem with paying a computer tech to fix our troubles on-site.  Even most computer vendors are all-thumbs when it comes to Linux.

So, as I said, I think there should be three options for installing Linux.  1.  Express = asks you next to nothing and installs everything to a default configuration with the assumption that the person installing might not know how to answer all the questions.  2.  Standard = the way we currently install it.  3. Advanced = for those of us who want to maybe edit the repositories ahead of time PRIOR to installation, maybe want to pre-arrange for bleeding-edge drivers, that sort of thing.

I think THAT could solve a lot of troubles.

The other thing that happens on the forums (I do it too) is that we all want to defend our favorite distribution.  It's totally normal, and kinda to be expected.  But sometimes (like this thread), defense is not what is called for at all ... more like, "yeah, I see what you mean, it would be nice if ...." and then we all get together and petition the developers to make some changes for the next release.  That's what community is all about :D.

Last point (sorry for being so long winded).  The Ubuntu community is by FAR the most respectable forum I have ever been party to.  It becomes a very substantial asset to Ubuntu and Linux in general, and it remains one of the primary reasons I use Ubuntu.

Cheers!

Mike

---

### Post by DoctorMO on 2006-08-06
As a developer I would like to defend my position

Spending time programming tools for people out of pure kindness to the world takes a mindset very few humans have; espcialy when the developer will never use those tools, would never get paid for making them, has no motivation in fact to spen precious free time doing it.

As for documentation, what are you waiting for? Linux isn't a thing you use, it's a thing you help develop thats what community means. and you should be helping fill those gaps you can identify by not only writing bug reports and documentation but also use cases for the very functionality you would like to see implimented. getting friendly with the developers of the projects, making them cups of tea and testing their newest release, giving them a pat on the back (directly if required).

I know the propritory world has programed people to simply use things and complain when they don't work, but to be honest you've not given anything very much back to the comunity. (apart from perhaps pointing out how dificult mounting a windows drive is) but we'll continue to try and help your problems any way because there are a lot of kind people here who give back by helping others with problems.

---

### Post by em3raldxiii on 2006-08-07
Very well said, DoctorMo.  It's definitely one thing to identify problems and lament about them and to say "I won't use it until it works better."  It's another thing entirely to say, "thanks for everything guys, this is an awesome product that is well worth continuing work ... here's what I would like to see ... is there something I can help with?"

Developers get a LOT of complaints and criticism.  A HELLUVALOT.  "This doesn't work, and why can't I do this, and using your thing broke my other thing ..." but they don't get a lot of, "well this is great, and to make it better *this* would really help".  And like I said, it's even rarer for someone to say, "hey, can I help with *this*?

For a user, sometimes it's not immediately apparent that a developer actually "does" want feedback.  In some cases the developers never reply (understandable because they are busy and sometimes get more email than they can deal with), but without any sort of reply, a user giving feedback cannot be 100% sure the developer got the message, or even *cares* if they got the message.

So, DoctorMo, in the spirit of this thread:  Thanks for whatever it is you are working on, it's worth it, keep it up, and if there is any way I can help I would be more than willing!  Sadly, I am not a programmer and have no aptitude for programming (the best I can do is HTML and Javascript), but I do have an active webserver ([www.anxietyofinfluence.ca](www.anxietyofinfluence.ca)) and I am great at writing tutorials, howtos, and tips.  Among other things.  How can I help?

Cheers!

Mike

---

### Post by ABEZ on 2006-08-07
> **DoctorMO said:**
> but to be honest you've not given anything very much back to the comunity. (apart from perhaps pointing out how dificult mounting a windows drive is) 

There are some other difficulties I did mention and as for suggestions I have made some as well, if you care to read all my messages in this thread. But anyway, what did you expect, I have yet to get some basic functionality under Ubuntu!

---

### Post by BlaineM on 2006-08-07
I personally enjoy the process of getting something to work in Linux, and the ability to make something new if need be, or help in the dev process anyway.  I guess its kind of a different world in open source, from what I've seen so far, although it has not been very much or for very long yet.  I started somewhere, not so far away from where I am now...:)   I guess if you think about it, maybe this open source sense of development is what Microsoft is kinda shooting for by doing open to public betas like they have been lately...

---

### Post by ABEZ on 2006-08-07
> **Upochapo said:**
> 
 Emerald was not the only one who defended you.  All the others did as well.  Reread and you will see.  They acknowledged the problems and understood what you were saying.  


I must clarify that I did not thank him for defending me. But rather because he was the only one who appeared to understand my arguments.

---

### Post by Upochapo on 2006-08-07
I must clarify that I did not thank him for defending me. But rather because he was the only one who appeared to understand my arguments.

hehe...understood and acknowledged.  If I had the resources myself, I'd hop on a jet and physcially come to your location to help figure this little pickle out.  Take care.

Upo.

---

### Post by Bragador on 2006-08-07
> **Upochapo said:**
> I must clarify that I did not thank him for defending me. But rather because he was the only one who appeared to understand my arguments.

hehe...understood and acknowledged.  If I had the resources myself, I'd hop on a jet and physcially come to your location to help figure this little pickle out.  Take care.

Upo.

You know it's not a bad idea. There are physical linux groups in most of the big cities. Since the members are usually computer hobyists that love linux they tend to help everyone for free just for the challenge of it.

Abez could try looking in his area to see if there is someone that could physically help. It might just work...

---

### Post by DoctorMO on 2006-08-07
I know I offer that very support in Surrey, UK :-)

---

### Post by FenrisAbraxas on 2006-08-07
> **ABEZ said:**
> I must clarify that I did not thank him for defending me. But rather because he was the only one who appeared to understand my arguments.

Everyone understand your arguments, it's just that not everyone will agree with you (and you should get used to that :-?), i'm a developer and you know how hard is to expectate EVERY SINGLE situation some user might run across (as an example: a field say "price" and i forgot to validate the field what i got in the database? a value called "five bucks" i was like "WTF? ](*,) ")

I agree there are newbies but must newbies in windows as in linux must read if they are going to try something new. Everyone here tried to help you but you only wanted to find someone who supported you, saying the installer is wrong (or at least to me it looks that way).

I'm going to say again, bugs will always be there, MS takes months to fix them, Linux probably will take weeks or even days. But if you don't fill bug reports how do you expect the bugs to be fixed? :-k 

I hope you one day will realize that Linux is ready for the masses and not because you had a problem (which i consider minor problem) means Linux is bad or the installer sux :P. I can tell you about million problems i ran across installing windows but you already know that i think.

If you ask my personal opinion about Linux vs MS is just about personal preferences and NEEDS. Linux (im a Gentoo user) just satisfy 100% all my needs. and MS just give me more problems than help me in my everyday work. I'm a intermediate Linux user (Windows a little more advanced) I understand how booting an OS works, what is and how dual boots works, partitioning and file systems. But you should know i learned all that with screwing up lot's of time my computer (hehe i know i never liked to sit and read a 100 page manual) but i never blamed the developers for not making a "100% idiot proof installer".

I hope you have the time and will to learn something new without blaming other for not making it 100% error free :)

---

### Post by ezsit on 2006-08-07
> That was brilliant. You just restored my hope in the free software community. Thank you em3raldxiii. It is detrimental to the advancement of the Linux world that constructive criticism is drowned in the prevalent fruitless confrontation of OS patriots. I see now how easy it is to get sucked into this.

Just because some people do not agree with your comments does not make them "OS patriots." My first reply to this thread merely pointed out that installing Ubuntu, when compared to Windows, isn't all that hard and/or more error prone. Ubuntu does a better job at detecting and installing the operating system than just about anything on this planet. Sure, there are always areas in need of improvement.

I think you are coming to Ubuntu with expectations that may or may not be realistic at the present. The development of drivers and hardware detection accuracy is hampered by companies that DO NOT provide documentation and/or reference code to opensource developers. All drivers under linux are the result of hard working programmers who reverse engineer the driver software as best they can for the components they have at hand. Sometimes drivers are less than ideal, sometimes they provide partial functionality, and sometimes they take ages to get written for unpopular hardware components. These are all problems, but not the Linux programmers fault, and they are certainly not under the Linux programmer's control.

Accessing Windows NTFS formatted partitions from outside Windows is difficult since Microsoft does not release the specs for the NTFS filesystem. NTFS access is looking brighter, but it takes time to reverse engineer a filesystem, allowing read/write access to said filesystem without destroying it and corrupting the data. The next release of Windows will surely set all non-Windows users back again as Microsoft may release yet another filesystem which will take years to safely crack. FAT32 filesystems are easily and safely used under Linux. All I had to do was go into the Disks program under the Settings menu and add my drives that I needed.

Partitioning a harddrive is not difficult once you get the concepts down. Do some reading, there is plenty of help on this subject online. This is the hardest step for newbies. I cut my teeth on OS/2 fdisk and using the OS/2 Boot Manager. Once I got to Linux, I had the partitioning stuff down. I remember it was a learning curve at first, but one I had to master before I could successfully install two operating systems on the same harddrive. Installing two or more operating systems on more than one disk today is even harder with SATA/PATA, RAID, etc. This is not something that can adaquately be covered on a help screen during the installation process. If the user requires a custom layout over multiple drives, the user has to be responsible for learning what they are doing before installation. The installer offers a basic step of auto-partitioning and gives the user a chance to edit the partition table themselves. This is really all that is required from an operating system installer.

Sorry for being so long-winded, but most readers do understand where you are coming from, we have been there before.

---

### Post by kubupak on 2006-08-07
I do not think you can compare windows to linux : MS cannot install more than notepad and paint or it will have to face a lot of trials !
MS by a very clever strategy won the battle of "hardware support" (at least support from manufacturer). On the other hand, I think that they are not winning the "easy install battle". Partitionning is nearly impossible, you have very little possibilities to "troubleshoot" the install. 

Anyway, I have to say that I'm very impressed and gratefull for the work done to have so much pieces of hardware (100% for me) working under ubuntu with a wery simple install stage to my point of view. I use 95% linux now and I belive I won't go back.

I have to admitt that I do not dare recommand it to friends or familly since probably you have to be volunteer to use linux. You also have to drop some windows habbits. "reinstalling ubuntu serveral time" is probably not the right way ;) usually you can rid off the problem by typing some word in a shell or waiting some days for an upgrade.

---

### Post by em3raldxiii on 2006-08-07
> **kubupak said:**
>  "reinstalling ubuntu serveral time" is probably not the right way ;) usually you can rid off the problem by typing some word in a shell or waiting some days for an upgrade.
 
This I think, is one of the hardest things for Linux Newbies to understand.  In most circumstances, you never have to re-install Ubuntu ... you can fix most things with the command line interface if you care to take the time.  (and it ends up being much faster anyway)

---

### Post by kingbilly on 2006-08-08
I agree with your points ABEZ.
In the first couple replies everyone was telling you to check out HOW-TO's.  Some missed your point about things should have worked in the first place.  A few got a little attitude.  Just some mixed ideas and communication.
This is because you are on the forums.  While big on support, the people that can make the changes in Ubuntu (devs) rarely come here.  The people that are here works together to solve problems using the methods that are applicable. Which is support.

Of course, this was posted in the Ubuntu Cafe, so you were not coming for support answers.  You were just expressing you idea.
However,  you can only repeat it so many times in the forum before its beaten into the ground.  The people in the forum do not have the power to change Ubuntu installs.  They can't make things "just work" from the start, as you believe (and we all) they should.  

 	
> Quote:
Originally Posted by DoctorMO View Post
but to be honest you've not given anything very much back to the comunity. (apart from perhaps pointing out how dificult mounting a windows drive is)

There are some other difficulties I did mention and as for suggestions I have made some as well, if you care to read all my messages in this thread. But anyway, what did you expect, I have yet to get some basic functionality under Ubuntu!

Posting on the forums is not enough, as I stated above that we can not change the initial product from here.  The most constructive thing you could do for yourself, and to refute others saying you haven't given anything back to the community, is to put your ideas where developers can see them.  File bug reports for your non-latin character problem.  A warning during the install would be great. If you search the forum you can find information on where to contribute ideas.

---

### Post by ABEZ on 2006-08-08
I choose not to respond to some messages on this thread because they keep repeating things that seem based on poor understanding of my thesis here. I do not want to come across as snobish, it is just that trying to explain what should be obvious is creating a lot of clutter in a thread and makes it cumbersome to read. And what should be obvious is that I am not advocating for Windows here. And I see many people consumed into arguing that Linux is better. I AGREE! But this is not intended to be another run-of-the-mill Windows vs Linux thread! It is about creating discourse which may further the user friendliness of Ubuntu. I see some people get patriotic about it and keep juxtaposing the various problems associated with Windows use. To my mind this is out of focus and I see as pointless engaging in. 

One other thing. Judging from the feedback on the re-install option I followed, I think you are jumping into conclusions here to accentuate the "Windows mentality". There was a reason I had to resort to a start-from-scratch approach, so if I may ask for some slack here. My decision to go to this free software platform is an educated one and I am as open minded about it as you can reasonably get.

---

### Post by ABEZ on 2006-08-08
> **kingbilly said:**
> 
Posting on the forums is not enough, as I stated above that we can not change the initial product from here.  The most constructive thing you could do for yourself, and to refute others saying you haven't given anything back to the community, is to put your ideas where developers can see them. 

I have given that some consideration but I figured this is not something that is not already happening and just one more improvement proposal will not make a difference. Instead I chose to engage into a dialogue which will first of all help me understand a few things about the mentality permeating this community. And maybe it can be a better platform to get my ideas about the development communicated. I think public discourse conducted under the right aura has great power and is crucial to the community's future direction.

---

### Post by em3raldxiii on 2006-08-08
Friendly discourse can be highly constructive.  Unfortunately, a post on the Cafe forum of this sort somewhat attracts "OS Patriots" ... and those who feel most passionately about defending their OS will be the most likely ones to read and post in a thread of this sort.  Which is not to say anything derogatory about those who *have* posted.  It's an interesting dynamic, reallly, from a sociological point of view.  Those who have worked hardest at getting their own OS working, and those who have helped others to do the same, are very likely the same folks who are proudest of what they have done and therefore potentially the most likely to defend the OS.  It all makes perfectly clear sense, and it really is to be expected.  I mean, *I* am one of them, and this was the reason why I read the post to begin with ;)

As far as the bug reports go, I would suggest against the notion that, *"... just one more improvement proposal will not make a difference."*  We as users have no difinitive way of knowing whether the developers have recieved feedback on the particular aspect for which you may have suggestions.  So I default by sending a plethora of feedback when and if I have a problem (which I admit is increaslingly rare).

Perhaps an alternative way to get these ideas across without attracting defensive discource by "OS Patriots" like me, we could start a fresh new thread titled something like, "A fresh pair of eyes:  A discussion about making Ubuntu better" or some such.  Then your first post could introduce the thread with something like, "New Ubuntu users often find awkward elements to Ubuntu that we experienced users now overlook ..." or some such.  I think you probably get where I am going.  Perhaps this would encourage the friendly discourse you are looking for?  Objectivity perhaps?  Just a thought. :D

Anyhoo ... there I went being long-winded again.  Sorry 'bout that.  Cheers!

---

### Post by em3raldxiii on 2006-08-09
So far I haven't seen any examples what you are referring to.  At this point, I am able to do everything as I did before, only everything works more stably.

Give me a good example of something that we've lost and cannot get at all any more.

*EDIT:  It appears, folks, that we may have a troll on our hands. The preceding two users appear to be the same person posting the same defamatory remarks in several places.  And they both appeared today.  Just a fair warning *

*EDIT:  I guess the user has been removed*

---

### Post by ezsit on 2006-08-09
> I choose not to respond to some messages on this thread because they keep repeating things that seem based on poor understanding of my thesis here. 

You do not give anyone any credit here. Your initial post outlined some very basic issues during installation. Your two main problems were no net access and difficultly accessing your Windows partitions. Obviously these two problems were very important to you since you deemed the entire Ubuntu experience as "a waste because of a non comprehensive implementation of an otherwise good idea for a software platform."

Now, some kind soul told you how you might get your net connection back the same day you posted. That is very quick community tech support. Your other issues are quite minor since you managed to install successfully. Your problems with the non latin characters in the password and the partitioning confusion you solved yourself. Accessing your Windows partitions is easily doable.

You, however, decided that because of your minor frustrations that Ubuntu and Linux, and the entire community of opensource developers, was engaging in fruitless activity producing software that did not meet your needs. I think you received about the most polite response imaginable.


> I do not want to come across as snobish, it is just that trying to explain what should be obvious is creating a lot of clutter in a thread and makes it cumbersome to read. 

But you are not coming off as snobish, just a newbie.

> And what should be obvious is that I am not advocating for Windows here. And I see many people consumed into arguing that Linux is better. I AGREE! But this is not intended to be another run-of-the-mill Windows vs Linux thread! 


This thread started out a basic rant against some minor annoyances. Nothing more.

---

### Post by bobbybobington on 2006-08-10
i dont think the whole argument of "linux isn't windows we shouldn't try to be like them" is just stupid.What hes trying to get at is ubuntu needs to be more user friendly. Its linux for human beings and we have to always work to achieve it. We cant just sit in our own little linux bubble and say "its not like windows just read the docs". If windows is good at any thing, its stupid simplicity. Now im not saying that ubuntu should totally emulate windows just to make it "easier", every os has its own idiosyncracies, but that doesn't mean that we cant refine it. And many of u guys are just oblivious to what hes trying to say. I remember my first linux install was freaking scary and i was fairly competent and was using suse 10's gui installer (which is uber easy). we absolutly must make it so ubuntu **is** linux for human beings.

---

### Post by ezsit on 2006-08-10
I never said that Ubuntu shouldn't be easy to install and use. It is easy to install and use. It is easy because of the infinite wisdom and generosity of the users who help others in online forums. Further development will hopefully improve the situation. My point was that Windows is NOT "stupid easy" to install. It only appears that way since most of us have been doing it for years. 

I am a relative newbie myself, mostly because I don't have the patience I used to have when I played around with other operating systems years ago. Now I just want most things to work. Caldera OpenLinux was the first Linux that was easy for me to use without too much trouble. RedHat and Mandriva were very good as well. Now Ubuntu has taken the cake. Is it me (having played with different distributions for eight years), or is it the progress of Linux? I'd like to think it is both, but Linux has progressed much faster than my abilities.

What I am saying is that Ubuntu IS easy. But its ease of use is in part due to my knowing some basic CLI and having a good understanding of hardware. I gave up on several distributions over the years, sometimes for very similar reasons as the OP. I do not blame the OP for feeling frustrated, and I understood what he was writing. 

Partitioning, password conventions, and access to non-native filesystems are all issues that every and any operating system installation procedure will demand of the user. That is why the comparison to Windows was a natural. Asking Ubuntu to become easier on these fronts is hard since the user really should know what is involved during the partitioning of a hard drive BEFORE attempting to install an operating system. I learned the hard way, as I am sure many did, that a wrong move during partitioning can result in the ultimate data loss. That is how I learned what to do and what not to do. I had never thought to use non latin characters for passwords, but I made the mistake early on of trying a mixed case username (never made that mistake again). As for access to non native filesystems, one reason why I never liked Redhat was simply because it refused to construct an fstab that included my Windows partitions. Now that I am all Linux on this box, that is not a problem.

Sorry for the essay. I did not mean to sound so negative towards to OP, but what he/she wrote was clear and understood, I just didn't agree that some of the issues mentioned really qualified as areas that needed improvement since a user will quickly learn what to do at those steps. 6.06 had enough problems (like not getting a working network after installation) for devs to worry about including a massive help screen to hand-hold someone through the partitioning process.

---

### Post by ABEZ on 2006-08-10
> **em3raldxiii said:**
> Friendly discourse can be highly constructive. Unfortunately, a post on the Cafe forum of this sort somewhat attracts "OS Patriots" ... and those who feel most passionately about defending their OS will be the most likely ones to read and post in a thread of this sort. Which is not to say anything derogatory about those who have posted. It's an interesting dynamic, reallly, from a sociological point of view. Those who have worked hardest at getting their own OS working, and those who have helped others to do the same, are very likely the same folks who are proudest of what they have done and therefore potentially the most likely to defend the OS. 

OS patriots are on every side. Reverse that analysis and you might just understand why people who find too hard to make Ubuntu/Linux work, come here and complain. They are people who were open minded enough to endeavour such a transition but frustration has set them back. They (us if you may) turn a little patriotic about their own frustration when they are constantly met with the urge to go through a tome of how-to's to perform the simplest function. They seem to instictively defend their own working platform by the same mechanism of Ubuntu users. One thing leading to another, you get a tit for tat kind of situation which ends in a flame war. In my mind it is a vicious circle in which the development of Linux has been entangled into. The community seems like a close circuit of the few who had the luck to get things running smooth in their computer or the time and inclination to educate themselves through an ocean of technical documentation. This excludes a critical mass of enthusiasts who are willing to follow and effectively help propagate Linux to the masses and scares average unempowered Windows users who happen to give it a try.
 

> Perhaps an alternative way to get these ideas across without attracting defensive discource by "OS Patriots" like me, we could start a fresh new thread titled something like, "A fresh pair of eyes:  A discussion about making Ubuntu better" or some such.  Then your first post could introduce the thread with something like, "New Ubuntu users often find awkward elements to Ubuntu that we experienced users now overlook ..." or some such.

That is something that not only could be done but SHOULD be done...eventually. I think it is not what a sub-newbie like me could initiate though. I must understand more about the mindset of the people around here so that I may effectively contribute to the dialogue. It would be best to have an experienced user bring this forth for various reasons. For one, it would be an acknowledgement on behalf of the influential old guard of the very need for this discourse. And right now I see that there is no such consensus. And I strongly believe the community should orient towards that direction.

---

### Post by greenbean on 2006-08-10
Well, I just want to thank all involved in this thread for their contributions.  I am a "sub-newbie"; ergo the login ID ("greenbean"); and this thread has helped me regain some of my shredded confidence after trying to keep Ubuntu 6.06 from locking up constantly.  Although I haven't figured out the problem (yet), this thread has given me the courage to keep looking.  I've been employed in the I.T. industry for 35 yrs in one form or another and I think that any prolonged exposure to computers turns one into a tenacious bulldog when it comes to figuring out problems (with computers or otherwise).  I now wish I'd persued Linux sooner, before I had a client waiting for results.  I too, tried to figure out how to manually do the partitioning, but finally let the default take over, hoping to explore that at a later date.  Much of what I see (so far) with the way things are done in Ubuntu takes me back to my old DOS and assembler language coding days of total control over the computer and I didn't think I'd like it (Windows has put so many abstraction layers between me and the computer that I got spoiled) but I'm finding it mostly enjoyable to get back to the roots.  Anyway, thanks to all.

---

### Post by redboar on 2006-08-10
> **ABEZ said:**
> Exisor I think you do not know what you are talking about. Anyway, I will not allow this thread to end in a flame war.

Abez, it's obviously their way or the highway.  The Linux philosophy is the same across all distributions, in that whatever is appealing, makes sense and functions very well for a developer or computer scientist is the way things should be.  Oh, and you should enjoy lenghty online discussions about why your device can't do what Windows lets you do out of the box, or you're an ungrateful simpleton.  Then again, XP and Vista are really looking to suck, so what other choice do we have?

My personal advice: download and install Breezy, follow the forum's instructions to install and run Automatix and for the most part you should be good to go.  Dapper is slower and functionality seems to be downgraded in certain areas from Breezy (again, to appease nerdy developers).

---

### Post by DoctorMO on 2006-08-11
redboar I refute your claims, There is hardly a difference between Breeze and Dapper to use nerdy developers, almost all the changes are in the GUI, the graphics, sounds, themes and 'extras' that are used my normal users.

I know because I'm a nerdy developer.

---

### Post by em3raldxiii on 2006-08-13
I actually tend to agree with DoctorMO.  While I am not a developer, I have generally found that Dapper (particularly since the point release & updates) is substantially stabler and more automated than breezy.  In fact, I did a LOT more "mucking about" than I do now.
 
And not all of us believe that "our way or the highway" philosophy.  In fact, if you read my posts, you will see I quite welcomed Abez's input and actually suggested a new thread to solidify his concerns.
 
So, Redboar, before you get belligerent with other users on the forum, please try to retain a certain level of decorum, mmkay? :D  Dats whut I'm talkin 'bout.
 
Cheers!

---

