---
title: "32 bit and 64 bit Linux"
date: 2007-09-27
forum: The Cafe
---

### Post by Dark Aspect on 2007-09-27
I am little confused on this,If I use 64 Ubuntu Linux then would I be able to use all of my 32-bit applications.Is compatibility an issue between 32bit code and 64 Ubuntu?How well would the 32 bit code work?Basically can I have Ubuntu 7.04 64 bit version and run applications like Cedega and Doom 3 natively?Would the 32 bit code run faster or at the same speed?

I am currently running 32-bit Ubuntu under the influence that all my 32-bit code will not work with a 64-bit OS.

---

### Post by ~LoKe on 2007-09-27
64 bit would be faster for crunching (folding), but not very noticeably faster otherwise.  The only issue could be codecs and flash.

---

### Post by o_fortuna on 2007-09-27
> **Dark Aspect said:**
> I am little confused on this,If I use 64 Ubuntu Linux then would I be able to use all of my 32-bit applications.Is compatibility an issue between 32bit code and 64 Ubuntu?How well would the 32 bit code work?Basically can I have Ubuntu 7.04 64 bit version and run applications like Cedega and Doom 3 natively?Would the 32 bit code run faster or at the same speed?

I am currently running 32-bit Ubuntu under the influence that all my 32-bit code will not work with a 64-bit OS.
If you do get 64-bit all open-source applications will work. However, binary packages may not work. You can install 32-bit libraries, which will allow those games and cedega to work, but it would involve dependency hunting.

32-bit on a 64-bit operating system is really not slower, but you should stick with 32-bit for now if you're using closed source applications (like Cedega and most games).

---

### Post by John.Michael.Kane on 2007-09-27
> **Dark Aspect said:**
> I am little confused on this,If I use 64 Ubuntu Linux then would I be able to use all of my 32-bit applications.Is compatibility an issue between 32bit code and 64 Ubuntu?How well would the 32 bit code work?Basically can I have Ubuntu 7.04 64 bit version and run applications like Cedega and Doom 3 natively?Would the 32 bit code run faster or at the same speed?

I am currently running 32-bit Ubuntu under the influence that all my 32-bit code will not work with a 64-bit OS.

I would suggest you try running ubuntu 64bit for a month without rebooting into 32bit. This will allow you to learn of it's benefits, and any short comings for yourself.

As for running 32bit applications it can be done,however. You the end user will have to be willing to do any of the work that 'might' be involved in getting the app in question working. Note: There might not be any extra work, As it will depend on the app.

For further reading:
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

> **~LoKe said:**
> 64 bit would be faster for crunching (folding), but not very noticeably faster otherwise.  The only issue could be codecs and flash.

This statement is not entirely true, With regards to codecs, and flash

There are methods listed in the link above that allow 64bit users to have flash,As well as codecs.

---

### Post by qazwsx on 2007-09-27
> **o_fortuna said:**
> However, binary packages may not work. You can install 32-bit libraries, which will allow those games and cedega to work, but it would involve dependency hunting.

getlibs solved all my troubles. 
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Well not all of them because I use nspluginwrapper for flash. 64 is the way to go if you are willing to do some some minor tweaks. There is also 64 bit wine repository. So no reason to look back. At least for me because I do lot of video encoding (dvb).

---

### Post by Seisen on 2007-09-27
It's not that hard to install flash and java on 64-bit Ubuntu basically you follow the directions and cut and paste. Here is the link that I used to do it. If you run into any problems we can help you fix them.

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%28amd64%29]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%28amd64%29")

---

### Post by Dark Aspect on 2007-09-27
> **o_fortuna said:**
> If you do get 64-bit all open-source applications will work. However, binary packages may not work. You can install 32-bit libraries, which will allow those games and cedega to work, but it would involve dependency hunting.

32-bit on a 64-bit operating system is really not slower, but you should stick with 32-bit for now if you're using closed source applications (like Cedega and most games).
OK is there a list of dependencies I can use to get 32-bit applications to work?I play a lot of windows game on Linux though wine and cedega so I don't know if thats a problem or not.I also need crossover to work and VMware.

Is getting the dependencies as easy as getting the dependencies to run KDE applications on Ubuntu because that was not too hard?

also would the restricted media dependencies work on Ubuntu,like the ones that allow MP3 use and video codecs?

Last question is there a chance that something might only work with 32-bit version of wine?

---

### Post by John.Michael.Kane on 2007-09-27
> **Dark Aspect said:**
> OK is there a list of dependencies I can use to get 32-bit applications to work?I play a lot of windows game on Linux though wine and cedega so I don't know if thats a problem or not.I also need crossover to work and VMware.

Regarding wine has a 64bit deb file

Regarding cedega should run under 64bit using the ia32-libs

vmware is listed in the 64bit repo, As well as it's dependencies.

> **Dark Aspect said:**
> Is getting the dependencies as easy as getting the dependencies to run KDE applications on Ubuntu because that was not too hard?

Depends on the program.

> **Dark Aspect said:**
> also would the restricted media dependencies work on Ubuntu,like the ones that allow MP3 use and video codecs?
The link I posted above explains clearly how to install  codecs, As well as flash under 64bit.

> **Dark Aspect said:**
> Last question is there a chance that something might only work with 32-bit version of wine?

Again as said before it depends on the App,

Also your not giving use much info to go on. So far  all you said is you play games, and you want mp3 support.  If you really need help with this you need to list your exact needs the programs/games you want to use etc.

---

### Post by ~LoKe on 2007-09-27
> **SD-Plissken said:**
> 
This statement is not entirely true, With regards to codecs, and flash

There are methods listed in the link above that allow 64bit users to have flash,As well as codecs.

I said it wold be an issue, I didn't say it wouldn't work. o_O

---

### Post by John.Michael.Kane on 2007-09-27
> **~LoKe said:**
> I said it wold be an issue, I didn't say it wouldn't work. o_O

Please explain what the issue is. As there are clear and precise method to installing the codecs, and flash. 

On top of this Gutsy makes it easy to install flash on 64bit through synaptic.

---

### Post by aaaantoine on 2007-09-27
> **SD-Plissken said:**
> For further reading:
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")


I was wondering why my codecs weren't working.  Thanks for the link!

---

### Post by ~LoKe on 2007-09-27
> **SD-Plissken said:**
> Please explain what the issue is. As there are clear and precise method to installing the codecs, and flash. 

On top of this Gutsy makes it easy to install flash on 64bit through synaptic.

The issue is going through several extra steps in order to get them working.

---

### Post by John.Michael.Kane on 2007-09-27
> **~LoKe said:**
> The issue is going through several extra steps in order to get them working.

I can agree that currently users of 64bit Dapper/Edgy/Feisty do have some extra steps with regards to codecs/flash,however. They are not many, and for most part should be alleviated with Gutsy.

---

### Post by Dark Aspect on 2007-09-27
> **SD-Plissken said:**
> Also your not giving use much info to go on. So far  all you said is you play games, and you want mp3 support.  If you really need help with this you need to list your exact needs the programs/games you want to use etc.

I have a huge hard drive with a lot of stuff I am not sure I can list every application I use and not every single one of them is that big of a deal but here we go: 

AcetoneISO2
Open Office 2.3.0
Rhythmbox Music Player
gxine
aMSN
Konqueror (with KDE dependences) 

Crossover
      \---Photoshop 7
       \-------Internet Explorer
        \----------Winrar (must have)

Wine
  \--------Firefox (windows)
   \-----------Basic windows apps like wordpad

VMware (Must have for school and work)
NTFS Config (a tool for accessing NTFS drives on Ubuntu a must have)

and stuff like Java and flash but I can use the 32-bit Firefox so thats already solved.Photo shop 7 is not a must have but I would like to use it over Gimp.The games aren't as important as the programs I don't have time to play my life away with various games but I Installed for the kicks and grins to see if they would work:

Astromenace
Doom 3
ePSXe (any PS1 emulator will do)
Nexuiz
Postal 2
Alien arena
lxdoom
PRBoom
Return to the castle Wolfenstein
Open arena
Doomsday
Second Life
Tremulous
ZSNES (snes emulator)
warsow
mupen64 (N64 emulator)

Wine
  \-------Jedi Outcast
   \--------Splinter cell (does not work with the new version anyway)

Cedega
      \---Dungeon Siege
       \-------Grand Theft Auto 3
        \------- Grand Theft Auto Vice City
         \---------Grand Theft Auto San Andreas
          \----------Midnight Club II
           \------------Might and Magic VII
            \-------------Silent Hill 2
             \--------------Star Trek Elite force
              \---------------Star Wars Galatic Battlegrounds
               \ ---------------Star Wars Jedi Academy
                \ ----------------Star Wars Knights of the Old Republic
                 \ -----------------Star Wars Knights of the Old Republic 2
                  \------------------The Moon Project

As I said before I don't play as many games as I use to,I can only think of a few weekends I spent playing games on Ubuntu.If silent hill 4 worked better then I would probably spend more time gaming.So if most of those games don't work with the 64 bit version of Ubuntu then it would not bother me.I would like to have though Nexuiz and Postal 2 because I find myself playing these sometimes.

---

### Post by PatrickMay16 on 2007-09-27
An interesting thing about 64 and 32 bit: LAME is a little slower on 64 bit, while oggenc is much faster on 64 bit. I mean, seriously twice as fast.

---

### Post by Dark Aspect on 2007-09-27
Actually I think I am just going to keep what I have in till Ubuntu 7.10 comes out and then I can try the 64 bit version of the new Ubuntu thats coming out in a few months.After all its not a long wait and it avoids installing Ubuntu 7.04 64 bit version and then turning around to  update to Ubuntu 7.10.I'll keep the links though for when I do decide to use Ubuntu 64-bit.

---

