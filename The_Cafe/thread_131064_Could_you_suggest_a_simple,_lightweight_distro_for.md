---
title: "Could you suggest a simple, lightweight distro for my folks"
date: 2006-02-15
forum: The Cafe
---

### Post by yb1011 on 2006-02-15
Hey Guys,
First of all I would like to thank all the guys who help us new users. Ive so far managed to fix ALL my problems using the SEARCH tool. And now have a stable, up-to-date system with all the programs I want configured that way I want :D  So for all the help...I say THANKS!

Now, Here is my question:
Im a student and I stay away from home (in a diff country). And though I call home, I chat using yahoo and voice using skype is a very important mode of communication between me and my family. I have a decent system so Ubuntu works great on my pc. But this is what my folks have:
A Pentium 2 - 450 Mhz
128Mb shared ram with 32mb alloted to memory
6Gb hard drive
Dialup connection 
OS- Windows ME (not working anymore)

So my question to you is, Which OS (Linux) do you guys suggest? Now there is nothing but  Ubuntu that I would them to use. But, looking at the system specs I really do not know if it would run at a usable level. So my dear friends, could you suggest any distribution that is simple and works on the above mentioned specs? 

So far on Searching I have found that:
1.Ubuntu is too heavy, but Xfce/fluxbox can be a way out
2.DamnSmall Linux is good
3.Puppy Linux runs great and I can create a custom ISO with all the programs custom added to the ISO (?)

I am currently leaning towards Puppy linux as it has the custom Iso feature (since I would have to download/burn the ISO and send it to them I can put all the applications that they would need). But since this is the only place I know that can give me a sincere suggestion..I ask you..what should I do... where should I look? Which distribution would you suggest?

Thank you for your time, suggestions and thoughts.

---

### Post by Bandit on 2006-02-15
If Ubuntu is to heavy, only thing other I can suggest is DSL (Damn Small Linux)
Cheers,
Joey

---

### Post by codejunkie on 2006-02-15
ubuntu and xfce should work just fine on that hardware you can even install and run nautilus and gnome-volume-manager in xfce so cd's, usbdisks, and other media will automount and it is still faster than gnome other than ubuntu id go with damsmall.

---

### Post by Virogenesis on 2006-02-15
maybe xubuntu may need more ram mind not sure

---

### Post by majikstreet on 2006-02-15
xfce may be too slow on that. when I had 256mb ram, xfce was slow... try openbox, fluxbox, blackbox, icewm, windowmaker, et al. there is a page on the wiki about low memory installations, I don't have the link right now, but there have been recent threads about this where I posted it.. you can search "low" on wiki.ubuntu.com and you should find that page..

---

### Post by yb1011 on 2006-02-15
First of all. Thank you for your response. You have no Idea how cool it is to see that there is someone who can tell you this stuff :-)
Coming back to my question:
I have used XFCE and ICEWM and they seem to be pretty easy on resources. So would it work if I installed Ubuntu (gnome) and installed XFCE and ICEWM and used them instead of gnome?  That way they can have the necessary applications and have a light-weight desktop too?

---

### Post by codejunkie on 2006-02-15
[QUOTE=yb1011]First of all. Thank you for your response. You have no Idea how cool it is to see that there is someone who can tell you this stuff :-)
Coming back to my question:
I have used XFCE and ICEWM and they seem to be pretty easy on resources. So would it work if I installed Ubuntu (gnome) and installed XFCE and ICEWM and used them instead of gnome?  That way they can have the necessary applications and have a light-weight desktop too?[/QUOTE]
you don't even have to install gnome with ubuntu to get xfce just do a server install after it finishes and when you reach the terminal just run 
```
sudo nano /etc/apt/sources.list
```uncomment the universe lines in the sources file save then run ```
sudo apt-get update
``` and
```
sudo apt-get install xubuntu-desktop
```

---

### Post by bored2k on 2006-02-15
On top of installing a light DM, make sure they use _light_ programs as well. You might want to change the resource-intensive Firefox for Opera (although some might say Firefox is lighter). Rox isn't too hard to move through and do basic operations with (file manager). Word processing (et al)? You'd want Abiword and Gnumeric for Spreadsheets. Instant messaging? If they use MSN, aMSN, if not, gaim (aMsn is lighter).

---

### Post by yb1011 on 2006-02-15
Thank you codejunkie. Now I have some Ideas.
Since they have a very slow dialup connection. I think I can download the xfce-desktop ISo and give the codes to install it from the CD.
By the way, would Gnome work better if I somehow figure a way to increade the RAM? I mean WindowsME was slow but it was usable. Does Gnome have a bigger foot-print that ME?
Thanks :-)

---

### Post by yb1011 on 2006-02-15
bored2k. thank you for the tips. NOTED! 
I am really overwhelmed here.. you guys are helping me so much here! THANK YOU!!

---

### Post by thekurst on 2006-02-15
Vector linux is supposedly made for older slower systems, based on slackware but supposedly blazing fast...

---

### Post by bored2k on 2006-02-15
[QUOTE=yb1011]Thank you codejunkie. Now I have some Ideas.
Since they have a very slow dialup connection. I think I can download the xfce-desktop ISo and give the codes to install it from the CD.
By the way, would Gnome work better if I somehow figure a way to increade the RAM? I mean WindowsME was slow but it was usable. Does Gnome have a bigger foot-print that ME?
Thanks :-)[/QUOTE]
You definitely do not want to try the Gnome beast on that computer. Ever. 

Yes, increasing RAM always helps, but it still wouldn't "allow" to use gnome in a satisfactory way. Thus, it would only make your IceWM/Fluxbox experience better.
Creating a custom disc for them is a great idea. After making sure you install Synaptic on them, creating a repository disc with XFCE and everything else they need (music codecs, etc) would be great and easier for them (note: if you do not know how to do this, ask in a separate thread ;)).

---

### Post by bored2k on 2006-02-15
[QUOTE=thekurst]Vector linux is supposedly made for older slower systems, based on slackware but supposedly blazing fast...[/QUOTE]
Ok, thekurst, great tip. That could work. From the Vector wiki entry:
> SOHO and Standard differ in a number of respects. SOHO assumes fairly modern hardware and includes larger applications, notably the KDE suite and OpenOffice.org. Moreover, choice of certain application versions is conservative in terms of stability, so as to prevent difficulties with newer, possibly bleeding-edge software. SOHO chose to stay with the 2.4 series kernel, considered more stable, than the newer 2.6 line of kernels, until 5.0.1. SOHO 5.1.1 was released with the 2.6.13 kernel. The Standard Edition includes the new 2.6 kernels since version 4.3 and chooses leaner applications, omitting KDE in favor of **IceWM and XFce**, and OpenOffice in favor of programs like **AbiWord.** Generally, Standard is a better choice for intermediate or expert users who want greater performance, while SOHO works well for newer users with recent hardware, or greater office needs.
If yb1011 were to try that one, he'd **first** want to test for himself how to maneuver a Slackware-based distribution, something that might and might not be as pretty as it sounds to configure. And by the way, Vector is pretty cute too :).  The standard install is what you would arguably want (the other one has KDE... very bad for those specs) [http://www.vectorlinux.com/mod.php?mod=userpage&menu=10&page_id=10](http://www.vectorlinux.com/mod.php?mod=userpage&menu=10&page_id=10)

---

### Post by yb1011 on 2006-02-15
Whoa... bored2k. Thanks! now this seems to be something that would work well with my situation. So this is what I have understood so far (Ubuntu-wise)
-Ubuntu would run well.. if I install/use ICEWM, Fluxbox
-I can do the above by creating a custom disc and also add all the applications they need (I will search the forums before I ask away... it helped me a lot so far and I dont see why it shoudnt work)

But I have one question, so as code junkie suggested should it be a server install first and then install all the other goodies?

EDIT: Looking into Vector as I speak. thanks thekrust!

---

### Post by bored2k on 2006-02-15
He suggested a server install because that way, the Ubuntu installer will **only** install the base system. If you do not select that option, you would have Gnome and a bunch of stuff your parents would never use. Ever. On top of that, the regular install would take quite a big chunk of their -I imagine- *petite* hard-disk drive. By the doing a server install, manually installing the graphical interface (not as hard as it sounds), you make sure their install will be a lot less bloated.

**Note:** If you decide to go use IceWM, although I would try to look for a distribution that pays a little more attention to this DM (just look how pretty it looks on Vector... I'm jealous), the selling point for IceWM+Ubuntu would be its *fantabulous* package manager (apt-get). But from the screenshots I see of Vector, it has gslapt, which looks like a very simple way to deal with packages.
[CENTER][[IMG]http://img295.imageshack.us/img295/6069/vl51stdgslaptrox4cy.th.jpg[/IMG]](http://img295.imageshack.us/my.php?image=vl51stdgslaptrox4cy.jpg)[/CENTER]

I'd find out how easy would setting Vector up would be (if you won't be able to set it up, neither would they). Second, google up how well does it behave on your parents specific hardware (if you don't find anything, I'm sure they a forum you could ask on). 

Anyways, if you decide for Ubuntu+IceWM/Flux, we're here :-).

---

### Post by poofyhairguy on 2006-02-15
[QUOTE=bored2k] (although some might say Firefox is lighter). [/QUOTE]

And they would be wrong, LOL.

---

### Post by TrailerTrash on 2006-02-15
This would work great! STX Linux on older systems. 

[http://www.stibs.cc/stx/](http://www.stibs.cc/stx/)

---

### Post by bored2k on 2006-02-15
[QUOTE=poofyhairguy]And they would be wrong, LOL.[/QUOTE]
LOL

---

### Post by yb1011 on 2006-02-15
Ok guys. I am downloading vector linux and will see how it works. Im also looking into installing Ubuntu with IceWM. thanks for your help guys.Let me see how things go...
In the End. Thank you for your help guys. You guys have been nothing but supportive! Thank you once again!

---

### Post by bored2k on 2006-02-15
[QUOTE=yb1011]Ok guys. I am downloading vector linux and will see how it works. Im also looking into installing Ubuntu with IceWM. thanks for your help guys.Let me see how things go...
In the End. Thank you for your help guys. You guys have been nothing but supportive! Thank you once again![/QUOTE]
That's what we do :). Heck, no one's even allowed to do otherwise *LOL*.

Remember to one day, anywhere, with whoever, to [pay it forward]("http://en.wikipedia.org/wiki/Pay_it_forward") though ;).

---

### Post by papangul on 2006-02-15
You might want to take a look at this also: [http://ubuntulite.org/](http://ubuntulite.org/)

---

