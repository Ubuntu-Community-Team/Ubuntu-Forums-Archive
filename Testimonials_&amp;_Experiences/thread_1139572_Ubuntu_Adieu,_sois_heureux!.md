---
title: "Ubuntu: Adieu, sois heureux!"
date: 2009-04-27
forum: Testimonials &amp; Experiences
---

### Post by socola on 2009-04-27
I still hope that I don't have to write this entry but many thoughts about Ubuntu can't just go away from my head. They stay during my vacation and even I try to write by hand quickly some thoughts, but the others come out too. They are all about &#8220;why I am going to quit Ubuntu&#8221;.  
 There is no one pressing me to use Ubuntu of course. Linux, if not something else, then as Linus Toward said, is... just for fun! Two years ago, when I asked a friend of mine about one program and he asked me that I was using Windows or Linux. I was so confusing as I think that a computer means Windows (I guess that I am not only one in this type of people). I heard about Linux more frequently and realized its existence. And I still don't know why people need to use Linux. I thought those guys should be very professional with command line (it sounds like they are cracking the secret computer in Hollywood action films). My first attempt to go to Linux is when I was looking a job in financial analysis (where they use C++ on both Windows and Linux). So actually I have reason to go for Linux and amazingly, I don't feel that Linux is difficult anymore (I believe that I can use it). So I just go online and type &#8220;Linux&#8221; in Google. Goodness, it is too many variations and too many people say that their Linux version is the best. I still did not know how to start. I asked some friends to help me to install Linux. One guy told me, you can just download from Internet, it is free (Oh, men, I need somethings to start before I know how and what to download, to install and of course... to remove). Others asked me also a &#8220;too difficult&#8221; question: which one you want to install? No, I don't know anything and I don't care what is what, I just need Linux. In the end, I borrowed a DVD of Fedora 7. The installation made me wet (I was doing somethings for the first time). In the end I got Fedora 7 and this was my first Linux distro. Then what next? I did not know what I can do with &#8220;my&#8221; Linux. I start to go to Add/Remove applications then some updates. At that time, Fedora 8 was already released so I tried to upgrade. I follow the introduction in their [website]("http://fedoraproject.org/wiki/YumUpgradeFaq#Fedora_7_-.3E_Fedora_8") without any clue then I could not restart Fedora again after three command lines:  
 1.yum groupinstall sound-and-video gnome-desktop
2.rpm -e --noscripts avahi-0.6.17-1.fc7
3.yum erase dbus.i386
 First attempt to Linux was over!
 


 Recently I read the book of Keir Thomas: Beginning with Ubuntu Linux. I felt more confident with Ubuntu and I start with Wubi to install Ubuntu on my laptop. I was impressed by its simplicity and speed. The Ubuntu's idea is just to get the machine works and if you want to do somethings else, you can install yourself (great!). I start to move few steps forward as installing Ubuntu in a partition disk and now, the whole laptop without Windows. However, after a longtime of loyalty, I start getting tired to fix so many "simplicity" things:  
 
[LIST]
[*]Why Ubuntu does not include Time New Roman font     by default? So I have to install it: *sudo apt-get install     msttcorefonts.*
[*]Why Ubuntu     enables a REALLY REALLY **ANNOYING     **sound beep when I type     somethings &#8220;wrong&#8221;? Am I wrong when I just want to shutdown     Ubuntu? Who have golden hand that you can press Backspace in the     terminal without more that one time when the cursor reaches the end? It may have an explanation: Linux users are geek, they know     exactly what they do so the sound beep is to tease the bad geek.     So I have also to turn if off by adding to gedit     /etc/modprobe.d/blacklist: #*silly speaker beep, blacklist     pcspkr *or temporary with the command: s*udo modprobe -r     pcspkr. *Why do they enables     things that people will disable and vice versa?
[*]Why Ubuntu can't     just play a movie when I insert my DVD? The error message comes out     letting me know about the missing of codec and suggests me to let     Ubuntu search, download and install it. YES! I wait Ubuntu do it.     But still not! I am not able to play any DVD films since I used     Ubuntu.
[*]Why Ubuntu can't     just remember my wireless password without asking again about the     password to unlook the keying stuff?
[*]Why Ubuntu     can't just open a .rar file without going to use *sudo     apt-get install unrar?*
[/LIST]
 That is somethings I encounter as a normal user (who just want to enjoy multimedia, surfing the Net, possible writing somethings). But I am not just using Ubuntu for these reasons. I am doing research so I need to analyse the data, writing report etc. I am so happy to find the replacement for Origin with Qtiplot which works fully only in Linux. Actually, I don't have to care about the fees of Windows XP, Microsoft Office 2007 or Origin 8.0, so I come to Linux world not because of the price but the curiosity. So here I found somethings more:  
 
[LIST]
[*]Why Ubuntu can't     recognizes my printers as openSUSE does? I will need to install the     specific printer myself.
[*]Why Ubuntu     puts KDE4 to the end-user without giving people a choice of going     back to KDE3? If you want a &#8220;devolution&#8221;, you can, really, as I     did following this website: [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/).
[*]Why Ubuntu 9.4 puts     Kile 2.1 (for Latex writing) in its repositories? Kile2.1 crashes     many times and it does not keep my setting. I have also no way to go     back to the stable Kile2.0 (unless I reinstall Ubuntu 8.10 where in     its repositories, Kile is still 2.0).
[*]Each time I login to     Ubuntu9.4 now, there is always a message: *User's Home/.dmrc file     is being ignored. This prevents the default session and language     from being saved. File should be owned by user have 644 permissions.     User's Home directory must be owned by user and not writable by     other users. *What the hell is that? I need 644 permission or 644     permission_s_? Both are meaningless to me and I still don't     know how to get rid of this message (Actually I know one solution     that I will use soon: NOT using Ubuntu).
[/LIST]
                                  Linux is a factor of choice, I can't complaint because one answer is waiting for me: Ubuntu does not own me anything. I don't know if Ubuntu developers do listern the users? Should I give a clever criticism that makes them feel happy to fix the bugs? Before that happens, I have to go with my own solution for my laptop in this week: reinstalling Windows first (where I can use skype with webcam, yahoo chat, poivy to phone, DVD movies etc). Then I will also install openSUSE in one partition where I know I can use KDE3, Qtiplot and Kile 2.0 without crash report message. Also with the YaST in openSUSE, I will use less command line in the terminal (It looks very professional but I am tired for being that professional too long). I know that almost problems you can find the solution in ubuntuforum.org. I appreciate the forum as I can solve many things from the member posts. I know that ubuntuforum is the biggest one. I thought the bigger is better because when I have problem, I can easily found the solution. But when I think back, why Mac's user forum is small? Is that true that ubuntuforum is big because of the number of problems? Why so many people are going to borrow ubuntuforum for help? In the end, I am not a developers (I have no clue to read the source code of any program), I am just a user. I need to do my work, not to spend whole day to read about how to fix problems.

---

### Post by spiderbatdad on 2009-04-27
sorry for your woes.
relating to .dmrc:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by El Zoido on 2009-04-27
If you think openSuse (or any other Distro) is better suited to your taste, then by all means use it!

As for some of your complaints:
[LIST]
[*]Ubuntu does not contain certain components and programs (fonts, unrar, dvd-playback, etc.) out-of-the-box for legal/licensing reasons. How much you get right away depends strongly on the policy of each distro ( btw. I don't think Windows will unpack .rar by default either)
[*]The beep indeed is very annoying. It's one of the first things I disable. It seemed easier to do in pre 9.04 though. It used to be possible to disable it by turning off the system bell in audio settings. I don't understand why they had to complicate this in 9.04
[*]Passwords seem inconvenient sometimes, but are there for a reason. I'm afraid we are used to lazy but risky security behaviour.
[/LIST]
    
Anyway, I hope you'll have more fun with your next OS!

---

### Post by Alterax on 2009-04-27
I'm not sure if I am amused or insulted.

One thing that always irritates me and countless others are people that can't be bothered to make a simple request for help, but decide out of the blue to create an account so they can write a 900 page novel whining about all the supposed failures of an operating system that they took no part in co-creating and made no effort to remedy.

Seriously.  Every single one of the honest support issues you mentioned were easily reparable--had you bothered to ask.  You did not.

The lack of the msttcorefonts and DVD decryption codec by default aren't due to some imagined fault by the Ubuntu developers, they are missing because they don't belong to us.  MSTTCorefonts is still the property of Microsoft--a company that has a 20+ year track record of suing over the slightest possibility of a  copyright/trademark infringement.  And libdvdcss (the DVD decryption software) is missing because it could be interpreted in many areas as a means of circumventing the Digital Millenium Copyright Act and its local equivalents.  Have a problem with it not being part of the distribution?  Write a novel to your lawmakers and tell them that these laws (such as software patents and the DMCA) prevent interoperability and actually help to enforce and entrench anticompetitive behavior and illegal monopolies.

Now if you don't mind, there are people all over this forum that are honestly interested in learning, improving, and using this operating system.  I will be assisting them--which I am happy to do, free of charge so long as they're willing to make an effort to learn for themselves.

--Alterax

P.S.  Who is Linus Toward?  Does he work at Redmond too?

---

### Post by Sef on 2009-04-27
Since the OP is not asking for help, the thread has been moved to the Community Cafe.

---

### Post by jespdj on 2009-04-27
> **socola said:**
> Why Ubuntu does not include Time New Roman font     by default?
Because the Times New Roman font is not free. You can get it from Microsoft without paying money, but it is not free as in freedom according to the license.

> **socola said:**
> Why Ubuntu can't just play a movie when I insert my DVD? The error message comes out letting me know about the missing of codec and suggests me to let Ubuntu search, download and install it.
Again, because the algorithms and software to decode DVDs is patented and copyrighted, and in some countries it is illegal to copy the codecs without paying for them.

> **socola said:**
> Why Ubuntu can't just remember my wireless password without asking again about the password to unlook the keying stuff?
That's a problem specific to your system, for most people this works without problems.

> **socola said:**
> Why Ubuntu can't just open a .rar file without going to use *sudo apt-get install unrar?*
Because not *everything* can be installed by default. In fact, I don't know any operating system that comes with an unrar program installed by default! And again, as far as I know, RAR is a proprietary licensed, non-free format.

---

### Post by spiderbatdad on 2009-04-27
> **Sef said:**
> Since the OP is not asking for help, the thread has been moved to the Community Cafe.

oh no! did I loose my bean? I posted before it was moved!

---

### Post by dragos240 on 2009-04-27
I hope wherever you go, open source follows you. Ubuntu is not for everyone, but arch is, I recommend it, very customizable, and very easy too. Please by all means, switch if you wish. But just every once in a while, just stop by, we are all linux goers here, and many of us don't even use ubuntu.  I hope you have a great time on what you want to do!

---

### Post by Methuselah on 2009-04-27
Thanks Alterax for saying what I was thinking.

And 
:-({|=

.

---

### Post by Methuselah on 2009-04-27
> **dragos240 said:**
> I hope wherever you go, open source follows you. Ubuntu is not for everyone, but arch is, I recommend it, very customizable, and very easy too. Please by all means, switch if you wish. But just every once in a while, just stop by, we are all linux goers here, and many of us don't even use ubuntu.  I hope you have a great time on what you want to do!

He's complaining about Ubuntu not pre-installing the universe and you're recommending arch?

lol

---

### Post by Quake on 2009-04-27
> **jespdj said:**
> Because the Times New Roman font is not free. You can get it from Microsoft without paying money, but it is not free as in freedom according to the license.


Again, because the algorithms and software to decode DVDs is patented and copyrighted, and in some countries it is illegal to copy the codecs without paying for them.


That's a problem specific to your system, for most people this works without problems.


Because not *everything* can be installed by default. In fact, I don't know any operating system that comes with an unrar program installed by default! And again, as far as I know, RAR is a proprietary licensed, non-free format.

Lol, A lot of the stuff he's asking aren't even there on a Windows Fresh install. A user can't view xvid, mp4 videos until he install the correct codecs. In fact, Ubuntu is much easier since it will download them for you.

And about rar... you have to be kidding me. Zip is the universal format therefore windows supports it but there too, you need to download rar in windows.

---

### Post by entr3p on 2009-04-27
I understand your complaints and I guess Ubuntu is wrong for you. If you want something that just works then your looking in the wrong place. If you didn't know, Ubuntu is the HARDEST OS to learn. It's the worst Linux OS to use. You have to click too many times to get what you want so I recommend two OS.

Their called **FreeBSD** and **Gentoo**. Their so easy to use :D! They automagically play your DVDs and even have UnRAR packed in because they don't care if they get sued! So remember. **FreeBSD** and **Gentoo** are the OS you're looking for. My dog can use those OS!

---

### Post by yoasif on 2009-04-27
i hope you filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/kile/+filebug") about kile crashing. it works fine for me, but if there is a real problem, it ought to be fixed.> **entr3p said:**
> I understand your complaints and I guess Ubuntu is wrong for you. If you want something that just works then your looking in the wrong place. If you didn't know, Ubuntu is the HARDEST OS to learn. It's the worst Linux OS to use. You have to click too many times to get what you want so I recommend two OS.

Their called **FreeBSD** and **Gentoo**. Their so easy to use :D! They automaigacally play your DVDs and even have UnRAR packed in because they don't care if they get sued! So remember. **FreeBSD** and **Gentoo** are the OS you're looking for. My dog can use those OS!this guy is being facetious, don't listen to him. you may want to try [linux mint]("http://www.linuxmint.com/") instead, it's a bit more lax than ubuntu when it comes to adding "non free" stuff by default.

---

### Post by Ericyzfr1 on 2009-04-27
Why Ubuntu can't do this? Why Ubuntu doesn't do that? You should read the post on this forum before complaining about issues you can solve in less than 5 minutes. If you really want to watch DVD, you can find a way really not that difficult.....5 minutes including a break!!!

---

### Post by bryncoles on 2009-04-28
> **dragos240 said:**
>  Ubuntu is not for everyone, but arch is.

its not often a forum post makes me laugh. i doff my cap to you, sir!

---

### Post by maheshjr2000 on 2009-04-28
Dude just set the keyring to remember your password for gods sake!
It takes me a good 10 minutes to setup a brand new FRESH install of 8.10 to get to where I was with my install of 8.10. Medibuntu is a lifesaver and so are the guides on this forum. Its not that hard.

---

### Post by HappyFeet on 2009-04-28
> **Alterax said:**
> 

The lack of the msttcorefonts and DVD decryption codec by default aren't due to some imagined fault by the Ubuntu developers, they are missing because they don't belong to us.

I know, it's real tough to do
```
sudo apt-get install non-free-codecs
```
Heaven forbid someone should read up on their OS, and how it works.
People forget that a fresh install of windows does not come with anything. You are literally helpless when you boot windows for the first time.

---

### Post by growled on 2009-04-28
Some people. :(

---

### Post by stchman on 2009-04-28
Lets take a look at your rants.

Is installing the msttcorefonts that difficult?

Windows XP fresh install does not play DVDs at all.  You have to add that ability to it.

Ubuntu does remember your wireless password.  When I power up my laptop it connects to my WPA2 WAP without fail.

Neither XP or Vista can deal with .rar files out of box, you have to INSTALL software.

You second set of whining:

What model printer do you have?
Does Windows give you a choice of different GUIs?  NO.


So all in all it seems you are more than willing to accept Windows shortcomings but Ubuntu cannot have any shortcomings or you will post on the forum.

By looking at your post count of ONE and just making a profile to whine no one will take you seriously.

Goodbye.

---

### Post by socola on 2009-04-29
It is true, sorry to make you feel angry about my post. Actually I am not so active in learning Linux and I really prefer somethings easy to do (I still think to convince my wife and my mother to use Linux, but will they need to spend one year like me to learn about many things in order to use it?). Linux Mint is really a perfect solution for us now. I already install it in my laptop (of course with Windows too). You are right, fresh install of Windows brings nothing (except without annoying beep).
 

 I have some specific interests in doing research. I come to see a PC as a tool to do things rather than learning too much about it (although it is fun to learn somehow). It can be that I was too emotional in writing the first post. However, you guys also seem to have even over emotional when someone talks bad about Ubuntu. Whenever someone complaints about Ubuntu (whether it is true or not), it is immediately meant that he/she is stupid.  
 

 Once again, thanks                    ** yoasif **for introducing me Linux Mint (after one year using Ubuntu with love, I don't quit it that easy!).

---

### Post by Sophont on 2009-04-29
> **socola said:**
> 
Why Ubuntu does not include Time New Roman font     by default? So I have to install it: *sudo apt-get install     msttcorefonts.*


Legal reasons. MS so far has not granted Ubuntu redistribution rights.
And as you already found out it's easy to install and you only do that once.
Meanwhile on Windows youl'd have to buy/install a whole lot of software that comes out of the box with Ubuntu (Office, Image editor, etc...)

> **socola said:**
> 
Why Ubuntu     enables a REALLY REALLY **ANNOYING**sound beep when I type     somethings “wrong”?


This is the one point where I totally agree with you. :-) That beep *is* annyoing.

> **socola said:**
> 
Why Ubuntu can't     just play a movie when I insert my DVD? The error message comes out     letting me know about the missing of codec and suggests me to let     Ubuntu search, download and install it. YES! I wait Ubuntu do it.     But still not! I am not able to play any DVD films since I used     Ubuntu.


Again - legal reasons.
But it's easily fixed. Add the Medibuntu repository ([http://medibuntu.org/](http://medibuntu.org/)) and install libdvdcss2. For better menu support install totem-xine via Synaptic. Voila - not only can you watch your DVDs - you don't even have to worry about the damn region codes anymore (unlike windows dvd players).

Alternatively there is at at least one DVD player app you can buy for Linux that would also solve the problem.

I have watched DVDs on Ubuntu for years.

> **socola said:**
> Why Ubuntu can't     just remember my wireless password without asking again about the     password to unlook the keying stuff?


Something is wrong on your setup. It usually does remember the password. Things like that happened a lot during the alphas. Did you upgrade during alpha/beta phase perchance?

> **socola said:**
> Why Ubuntu     can't just open a .rar file without going to use *sudo     apt-get install unrar?*


Again you only have to do that once - I don't get what the big deal is here. And finding rar via Synapitic would also have been very easy.

I dunno why it's not included OOB - but with the requirement that Ubuntu has to fit on a CD they have to make the cut somewhere to keep within the 600 MB limit. So perhaps the decision is just based on saving a bit of CD space.

And you can't use rar and many other compression formats on windows OOB either.

> **socola said:**
>  That is somethings I encounter as a normal user (who just want to enjoy multimedia, surfing the Net, possible writing somethings). 


I'm doing all that and more. Been doing so for over 3 years. And - on a fresh machine - getting Ubuntu into that state is faster than setting up windows to be able to do all that. A fresh windows install has no office. The browser (IE) is a malware magnet missing many of the great extensions Firefox has so I need to replace the browser. Notepad is a sorry excuse for an editor - so I have to replace that too. Don't get me started on Paint. Meanwhile many windows installations requite reboots (less these days - but still annoyingly often). Don't forget the AV app - or your windows is doomed to be an enslaved zombie.
After I hunted windows drivers and setup programs via google (while avoiding suspicious links that might spread malware versions) and possibly having a DLL or 2 clash due to version conflicts I have to update them all individually (except for office and some other MS apps that update via windows update).
Why can't windows software be open source, open protocol, mostly free and come from a central repository that resolved conflicts and provides security updates for everything? :-)

Why can't windows setups be as easy and safe and auto-upgrading as Ubuntus?
 
> **socola said:**
> 
Why Ubuntu can't     recognizes my printers as openSUSE does? I will need to install the     specific printer myself.


Problem with that particular printer. I plug in printer - wait a few moments - done - printer is ready to use (don't buy Lexmark until they provide proper Linux support). I don't remember when I last had a problem with an Epson or HP printer on Linux.

> **socola said:**
> Why Ubuntu     puts KDE4 to the end-user without giving people a choice of going     back to KDE3?

Ubuntu didn't. That was a decision by the Kubuntu team. I guess there was nobody available to do the necessary work of providing that option.
Dunno - haven't looked much at KDE for years.

> **socola said:**
> 
Why Ubuntu 9.4 puts     Kile 2.1 (for Latex writing) in its repositories? Kile2.1 crashes     many times and it does not keep my setting. I have also no way to go     back to the stable Kile2.0 (unless I reinstall Ubuntu 8.10 where in     its repositories, Kile is still 2.0).

Again - *K*ubuntu - not Ubuntu. Sure - the distros are closely linked siblings - but Ubuntu (without the K) is the primary platform getting the most attention, testing and bugfixing.

> **socola said:**
> Each time I login to     Ubuntu9.4 now, there is always a message: [I]User's Home/.dmrc file     is being ignored. 


I got that on the machine I installed the alpha version of 9.04 on.
That didn't happen with the release version of 9.04.

Again - did you upgrade during alpha/beta phase?
If that's so than you have to expect and being able to deal with much worse than a couple of bugs that are easily fixed with typing a line or 2.

Don't get me wrong - feel free to use Windows or OpenSuse if you prefer. Whatever works best for you.
But the examples you provided puzzle me. They are almost all small and easily fixed. Actually you listed the fixes yourself so you already know and applied them. And as that didn't take much time and is already done - what exactly is the problem and why did it bother you enough to start a thread about it?

If power gamers complain about their shiny new fresh-off-the-shelve games not working fully or at all on Linux I get what the problem is and that group is about the only one I wouldn't recommend Linux to.

---

### Post by socola on 2009-04-29
Thanks Sophont,
You are more patient than others when you read my post. I confess that I have posted it in being too emotional (too much addicted in playing with Ubuntu but still don't see an easy way for really new user like my wife or my mother). Now thanks for Linux mint, it does all these things right the beginning (although MSfont or annoying beep are easy to deal with). The rest is perfect! I can use the logitech webcam with skype (that I even can't use in Windows because whatever reason), I can also use web with java (like upload picture to photobucket). When I insert a DVD, it works right away. This is exactly what I am looking for (for me to not bother much about setting Ubuntu and perhaps for my wife to benefit more the taste of Ubuntu). The installation of printer is not so hard by the way. 

Opensuse however can't write on NTFS partition of Windows (maybe it can, but it is not default as Ubuntu). But KDE3 works very stable on it and I don't want to replace it with Linux mint now (I need to focus on my own works as long as the PC still works). 

To conclude: I still see Ubuntu community is very friendly. Thanks you all and I know that I will still use Linux (or Ubuntu in particular) in the long future. 
Best regards,

---

### Post by Sophont on 2009-04-30
I'm glad you found a solution that works for you.

Have fun

---

### Post by starcannon on 2009-04-30
> I am just a user. I need to do my work, not to spend whole day to read about how to fix problems.
Buy a computer with Ubuntu preinstalled; some websites that offer this are:
[Zareason]("http://www.zareason.com/shop/home.php")
[System76]("http://www.system76.com/")
[Dell]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs")

You will still have to do like on ANY OTHER OS, and install software that is not there by default, it's just not reasonable to expect that every possible thing that you may want is preinstalled, there are to many variations to account for. Further, things like Codecs can be handled a couple different ways, though you may like the [Fluendo]("http://www.fluendo.com/") approach best.

GL and have fun.

---

