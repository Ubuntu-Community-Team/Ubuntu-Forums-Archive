---
title: "xmonad desktop trusty"
date: 2013-12-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-12-04
Just found yet another gem of a desktop.  More simple than most, but unique and fast if you are willing to learn a few simple shortcuts.

I am testing to see if it threads through to my files by posting a screenshot.

edit:

Well... what do ya know ... cpu-usage shows up in psensors all of a sudden.. Hrmmmnn..

---

### Post by ventrical on 2013-12-04
Here is the link to install xmonad. It's in the repos.

[http://www.howtogeek.com/114728/how-to-use-xmonad-a-tiling-window-manager-for-linux/](http://www.howtogeek.com/114728/how-to-use-xmonad-a-tiling-window-manager-for-linux/)


Edit:

The above will tell you to wait for a black screen, but while using trusty you will see the background screen of lightdm and so just press SHIFT+ALT+ENTER and the terminal will come up.

Edit:

xmonad-gnome will give you background
xmonad standalone will give you the blackspace.

---

### Post by ventrical on 2013-12-04
The unity8 shell can use  full screen so the emulator can turn your desktop into a virtual slate with nothing else on the screen. Will try some other experiments.

Regards..

---

### Post by ventrical on 2013-12-04
Unity 8 screenshot on xmonad.

---

### Post by ventrical on 2013-12-05
I was able to run VirtualBox on xmonad with another commercial operating system on it on an earlier LTS of Ubuntu and virtually do a side by side, while a demo was going on I was able to shift through different terminals using the ALT+ Spacebar short-cut. When I closed the virtual OS , xmonad was only using 149MB of Ram with three terminals open , glxgears and virtualbox still loaded. Now to try VBox on Trusty with Xmonad desktop and see if  the memory-management behaves the same. Also using virtual box on xmonad will give the end_user a full screen virtual machine. 

Running startx in a terminal gives me the Unity panel so this little windows manager is very versatile and efficient,  and if the menu is installed it is even more efficient and user_friendly.

---

### Post by QDR06VV9 on 2013-12-05
I think I'll give this a go tonight!
Thanks Vent.

---

### Post by zika on 2013-12-05
Xmonad is great and it has been with us since 2007. or 2008. as far as I can remember...
It should shine even more with multimonitor environment...
Change of programming environment (as I can notice) did a nice boost to a great project...
One of the very rear DM/WM that work with each and every component just from bare X.
Stable as a rock. No surprise it is WM of choice for non-IT-researchers and programmers and any other such that they do want to think about other stuff than OS and WM...

---

### Post by ventrical on 2013-12-05
> **zika said:**
> Xmonad is great and it has been with us since 2007. or 2008. as far as I can remember...
It should shine even more with multimonitor environment...
Change of programming environment (as I can notice) did a nice boost to a great project...
One of the very rear DM/WM that work with each and every component just from bare X.
Stable as a rock. No surprise it is WM of choice for non-IT-researchers and programmers and any other such that they do want to think about other stuff than OS and WM...

 It has this neat little menu. When you hit ALT+P  and then at the top left you can enter anything, ie; firefox..etc.. and it will list  all the programs horizontally. Highlight them , hit enter and they will run.  However.. there are some programs that you have to be in #root to run. 

  It reminds me a little bit of the Vax-Unix terminal that I was trained on during my school years ;)

Regards..

---

### Post by ventrical on 2013-12-05
> **runrickus said:**
> I think I'll give this a go tonight!
Thanks Vent.

  Big problem here on an Intel MoBo Core2Duo. I chickened out and used the Software Center version of Virtual Box rather than downloading the Oracle version from their website.  Also I did not turn on the VT in BIOS before  I installed a version of Precise. I had had some problems previously with Virtual Box on Trusty and had to reinstall. It seems to have affected my graphics driver after I created that virtual machine. Also .. I could not get the full screen to come using the xmonad short-cut Alt+Spacebar as I was able to previously ... so ... I would be careful as I am not really sure what happened on this machine. I'll enable the VT and see what happens.

  The goal of this testing is to see if I can use xmonad to run two different virtual machines simutaneously (and be able to see them run side by side). I had some sort of a reasonable facsimile using an XP iso running it's demo ..etc... so I am sure others have gone before me on this. It is just a curiosity  to me to see if one can run two OSes on seperate tiles. ie; ubuntu trusty on one and Win8 (or other Ubutnu flavor) on the other without stopping the progression of the programs running on either tile.

 So I'll take a back-step on this and see if it will work on 12.04, then try it on 14.04.

Regards..

---

### Post by zika on 2013-12-05
> **ventrical said:**
> However.. there are some programs that you have to be in #root to run.??? Those programs need sudo priviledges anyway and we're used to use them with {gksu, sudo (where appropriate)} all the time... 

Apart from that:
For those wanting to use gmrun (as they're accustomed): Alt-Shift-P

---

### Post by ventrical on 2013-12-05
Two other separate desktops that I had installed xmonad on will now not load up xmonad. When I login they just recycle back to login, as if they had a 24 hour limit only :)

---

### Post by ventrical on 2013-12-05
> **zika said:**
> ??? Those programs need sudo priviledges anyway and we're used to use them with {gksu, sudo (where appropriate)} all the time... 

Apart from that:
For those wanting to use gmrun (as they're accustomed): Alt-Shift-P


That's what I was implying.. ie;

```

$ gksu synaptic

```

Synaptic or Nautilus will not run from the menu but firefox and gnome-system-monitor will .. etc.. so my meaning when I said 'you have to be root' is you have to use 'gksu in terminal' and thanks for making that clear..


Regards..

---

### Post by ventrical on 2013-12-05
1 Result so far:

 Upon logging into xmonad I opened a terminal and entered the code:

```

gksu startx

```

This brought me to a raw root session of Ubuntu Unity, Trusty Tahr dev with no icons on top or bottom panels but all the icons on the unity panel and the dash were working. To switch back to xmonad session is Ctrl+Alt+F7 but you will close the unity session. Also , if you add an extra terminal just after boot and run your virtual box install (which in my case is 12.04) it will still be there after you open a <gksu startx> unity session. The thing about all of this is that once you switch back to your xmonad session the 14.04 unity session is gone and Ctrl+Alt+F1 will only give you a login prompt and if you have gnome-system-monitor running on xmonad you will see that the xsession has not been dumped from memory. So this is either a bug or , admittedly , something I am doing wrong ... but sure having fun !:)

Regards..

---

### Post by oldos2er on 2013-12-05
Are you a programmer, ventrical? One of the reasons I like i3 over awesome and xmonad (which I haven't tried, btw) is it's configured with plain text files. Xmonad does sound interesting though.

---

### Post by ventrical on 2013-12-05
> **oldos2er said:**
> Are you a programmer, ventrical? One of the reasons I like i3 over awesome and xmonad (which I haven't tried, btw) is it's configured with plain text files. Xmonad does sound interesting though.


Yes I am .. or , I was at one time. The newer scriptings, I have a hard time with ...python .. etc... ya know ... a performance pianist is trained in a certain technique and once that technique is ingrained it is hard to change the resultant styles that come with it. It's like trying to compare Arthur Rubenstien with Lang Lang :) I guess that same can be said for programming.. so I am trying to draw flowcharts with words so everybody can understand.

 I'll check those others that you mentioned.

Regards..

---

### Post by oldos2er on 2013-12-05
Awesome's written in Lua, and while it looks nice I'm having a lot more fun with i3.

---

### Post by ventrical on 2013-12-05
I did install i3, chose defaults and not much from there :)  I'll set config the next reboot :)

---

### Post by ventrical on 2013-12-05
> **oldos2er said:**
> Awesome's written in Lua, and while it looks nice I'm having a lot more fun with i3.


I was formally trained with this programming language.


[http://en.wikipedia.org/wiki/Turing_%28programming_language%29](http://en.wikipedia.org/wiki/Turing_%28programming_language%29)

and took up some other on my own, ASM86, Qbasic, BASIC , ASIC etc.. we used monochrome monitors on the Vax Unix and colored scripting is just not my forte, but I'm learning :)

Regards..

---

### Post by zika on 2013-12-06
Beware: offtopic but the one started by FM and UM...
Did You do programming three-address-machines even two address ones?
Did You work with drum-disks and punched tape? 
If not You're too young... ;) Started programming in early '70s...
Even though, after all that (Assembler, Fortran, Cobol, etc) Python and such are piece of cake. Just going forward and learning with every bit of my body. But doing it with purpose and saving energy where possible. Picking battles to take.
Simply put, do not try to plug microphone jack into power socket... ;)
I would like to try i3, also, I mean BMW... ;)

---

### Post by ventrical on 2013-12-06
Thanks for words of wisdom zika.
I started radio and tv service repair apprentinceship in 1963.
IBM Cash Register repair
Repaired and programmed (single adress) pinball machines -electromechanical/electronic.1975
space Invader repair (no program)
Official data entry level service tech/Reflex database/1988
1990 / Turing etc..

---

### Post by zika on 2013-12-06
> **ventrical said:**
> Thanks for words of wisdom zika.
I started radio and tv service repair apprentinceship in 1963.
IBM Cash Register repair
Repaired and programmed (single adress) pinball machines -electromechanical/electronic.1975
space Invader repair (no program)
Official data entry level service tech/Reflex database/1988
1990 / Turing etc..„Wisdom“ is the word that could hardly, very hardly, be associated with any segment of me. Many other come to mind but, as all this is deep offtopic I'll just stop here.

---

### Post by ventrical on 2013-12-06
> **ventrical said:**
> Big problem here on an Intel MoBo Core2Duo. I chickened out and used the Software Center version of Virtual Box rather than downloading the Oracle version from their website.  Also I did not turn on the VT in BIOS before  I installed a version of Precise. I had had some problems previously with Virtual Box on Trusty and had to reinstall. It seems to have affected my graphics driver after I created that virtual machine. Also .. I could not get the full screen to come using the xmonad short-cut Alt+Spacebar as I was able to previously ... so ... I would be careful as I am not really sure what happened on this machine. I'll enable the VT and see what happens.

  The goal of this testing is to see if I can use xmonad to run two different virtual machines simutaneously (and be able to see them run side by side). I had some sort of a reasonable facsimile using an XP iso running it's demo ..etc... so I am sure others have gone before me on this. It is just a curiosity  to me to see if one can run two OSes on seperate tiles. ie; ubuntu trusty on one and Win8 (or other Ubutnu flavor) on the other without stopping the progression of the programs running on either tile.

 So I'll take a back-step on this and see if it will work on 12.04, then try it on 14.04.

Regards..

I created a work-around by uninstalling xmonad, then, installing gdm and reinstalling xmonad. There seems to be a bug (or bork) of somesort with lightdm while running a virtual machine on one tile and 'gksu startx' on another.  Otherwise .. all is well .. so back to experiementing.

note on i3 and awesome: I am sure they are great wms but I'll keep them in my backpocket for now:)

---

### Post by zika on 2013-12-06
Is there some apparent reason why You use gksu with startx?
Not going into reason of other things going on in that experiment of Yours...

---

### Post by ventrical on 2013-12-06
> **zika said:**
> Is there some apparent reason why You use gksu with startx?
Not going into reason of other things going on in that experiment of Yours...

Because of this (see screenshot) and not able to get out.

I know conventionally we should startx from terminal (Ctrl+Alt+F1) but then this is not a conventional experiment. Pointers always welcome..

Edit:

 I get the same error  from (Ctrl+Alt+F1) unless I use gksu.  When I do use 'gksu startx' (as i had stated previously) I will get the ubuntu (unity) desktop on F1 terminal. When I switch back to Ctrl+Alt+F7 I am back in xmonad but the F1 terminal (with ubuntu-unity-desktop) is gone with only login prompt.

---

### Post by ventrical on 2013-12-06
My result then (hypothetically speaking because I currently cannot document it) would be that if xmonad, which is running on F7 terminal and if that terminal were ported out to another display monitor (dual mode)  with a virtual machine running then two kernels are actually  time/sharing on a singular form factor and while one monitor would be displaying trusty ubuntu the other would be displaying the virtual machine. I know that this is not new news but I just wanted to test this theory and xmonad gave me a few clues or ways and means .. and I am still in progress with this ..

---

### Post by zika on 2013-12-06
> **ventrical said:**
> Because of this (see screenshot) and not able to get out.

I know conventionally we should startx from terminal (Ctrl+Alt+F1) but then this is not a conventional experiment. Pointers always welcome..

Edit:

 I get the same error  from (Ctrl+Alt+F1) unless I use gksu.  When I do use 'gksu startx' (as i had stated previously) I will get the ubuntu (unity) desktop on F1 terminal. When I switch back to Ctrl+Alt+F7 I am back in xmonad but the F1 terminal (with ubuntu-unity-desktop) is gone with only login prompt.when You run startx with root priviledges it creates .Xauthority file and that file perevents You from runnung it as &#8222;regular&#8220; user. Erase that file and try again. If that fails You've created a bigger ,ess with X with priviledges and it could be (re)solved but it takes a greater insight into past Your actions... Let alone that I still do not grasp idea that leads You into exepriment like the one You describe. Back to microphone and socket.

---

### Post by zika on 2013-12-06
> **ventrical said:**
> My result then (hypothetically speaking because I currently cannot document it) would be that if xmonad, which is running on F7 terminal and if that terminal were ported out to another display monitor (dual mode)  with a virtual machine running then two kernels are actually  time/sharing on a singular form factor and while one monitor would be displaying trusty ubuntu the other would be displaying the virtual machine. I know that this is not new news but I just wanted to test this theory and xmonad gave me a few clues or ways and means .. and I am still in progress with this ..You do not need xmonad to do that. That could be done easily and I think it was done not once.
Excuse my writing in two consecutive messages, I thought I did click on multi-quote but obviously I did not. Mea culpa.

---

### Post by ventrical on 2013-12-06
Thanks for your replies.

 I removed .Xauthority and I am able to log back on normally.

I think it still worth the while to keep on experimenting to see if I can get this to execute on just one monitor with a different kernel  on each seperate tile running synchronistically.

Regards..

---

### Post by ventrical on 2013-12-06
ehehehe .. I'm spitting into the wind here ...:) lol

[http://lifehacker.com/5623313/how-to-run-windows-mac-and-linux-side-by-side-and-pain+free-with-virtualbox](http://lifehacker.com/5623313/how-to-run-windows-mac-and-linux-side-by-side-and-pain+free-with-virtualbox)

---

### Post by zika on 2013-12-07
> **ventrical said:**
> ehehehe .. I'm spitting into the wind here ...:) lol

[http://lifehacker.com/5623313/how-to-run-windows-mac-and-linux-side-by-side-and-pain+free-with-virtualbox](http://lifehacker.com/5623313/how-to-run-windows-mac-and-linux-side-by-side-and-pain+free-with-virtualbox)There are even easier ways but this one seems OK on a brief look.

---

