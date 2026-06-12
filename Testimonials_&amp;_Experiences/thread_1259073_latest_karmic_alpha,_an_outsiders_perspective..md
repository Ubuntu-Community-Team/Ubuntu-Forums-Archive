---
title: "latest karmic alpha, an outsiders perspective."
date: 2009-09-05
forum: Testimonials &amp; Experiences
---

### Post by adrenalinejunky on 2009-09-05
let me start by saying that i am an arch user, that said, i am not trying to compare ubuntu to arch as that is hardly an apples to apples comparison, they are different distro's with different goals. different philosophies, and different target users.

also of note is that i generally use KDE, but am writing this about gnome/ubuntu, i may try kubuntu later, but every time i have before its always seemed like an afterthought implementation.

my purpose for testing was to check the latest catalyst drivers that are available in ubuntu, but i figured i'd do this while i was at it, i'm not trying to knock ubuntu, just saying things as i feel it, ignore me, take it as constructive criticism, take it as you like... whatever.

also note that i understand this is an alpha - so some of my criticisms, while valid, should be taken with a grain of salt.

i think thats enough disclaimers and qualifications, on to my experience

the livecd didn't work - seemed like x was dieing/respawning continually during the gnome loading stage, so i restarted and chose the install option instead. probably just bleeding edge growing pains from being an alpha.

after install i booted up to find arch had not been imported to the new grub installed by ubuntu... while only an annoyance if you know your way around the config files, for an easy distro this is very bad behavior, and the only time i've ever had this happen with any distro.

also after the selection grub started booting and then dropped to a maintnence shell because fsck was complaining about a superbock write time in the future.... seemed rather an odd reason for a maintenence shell, but i ran fsck, which "fixed" the block time, then ran a "scan" that took all of about 45 seconds... computer restarted, and once again dropped to the command shell, complaining about the superblock time again. this time the scan successfully completed, and the system continued to load, not suprisingly, once again going into a loop that i couldn't break when x loaded

once again restarting i edited the grub boot and added a 3... to my suprise, i tried to load the gui again, i don't know if this is a change with the new grub, or if its because ubuntu loads gdm from mode 3 rather then booting to mode 5... but its obnoxious. also obnoxious is the lack of an /etc/inittab. haven't figured out where they switched the configuration for that too (yet)

anyway, i managed to switch to tty1 before x screwed up on this boot, installed catalyst drivers to see if that helped X, rebooted and everything loaded fine this time.

i must say, i'm suprised the ugly brown theme is still alive and well... i guess to each their own.

i noticed compositing was enabled by default, asumed compiz, and went to find the settings for it... which i didn't i figured it could be xcompmgr or something, so i went to install compiz... 

i must say, the add/remove is rather nice, with screenshots and popularity ratings... thats something that many more package managers should have. that  said, it told me compiz was not compatible with x86-64 architecture.... say what?

the really strange thing is, checking my system monitor, compiz IS running... don't understand that, but whatever, i installed the compiz settings manager, which i should think would be included... as by default xcompmgr seems a much better considering how few desktop effects are enable by default.

i also noticed that the catalyst control center is in "applications -> other" on the menu.... which is a really bad spot for it

i must say so far, this is probably the most problems i've run into for initial installation and configuration of any distro i've installed in -years- including alpha's.... but not all development cycles are the same, we'll see how things shape up in october.

some nice touches, and i rather like the add/remove, as noted. also i think the upcoming software store will be great, and i'm amazed it took someone other then linspire this long to set it up.

these are just initial experiences, i'll probably update a few times as i'm testing the catalyst drivers over the next couple days. then maybe (maybe) again with kubuntu as well.

---

### Post by HappyFeet on 2009-09-05
I didn't read the whole thing, but really, I'm not going to worry about it. I'm running Mythbuntu64 9.04 with the ubuntu desktop. It runs absolutely perfect for me just like most of the previous releases have. I ran 9.10 for a bit on a test machine and reported a few bugs, but could not run it as a production machine. In the next few weeks, changes will come fast and furious. That's why I'm not worried about it. I truly believe that 9.10 will be the best overall release to date. Anyway, before I get too long winded, I hope arch is working out for you as well as ubuntu is working for me, as if this is true, then you are definitely *extremely* happy with your machine. Or something like that. Cheers.

---

### Post by kreggz on 2009-09-07
Hey,

I am a Jaunty user and tried Karmic Alpha yesterday and had the same problems as you (I used VirtualBox) eg. fsck problem, X dying.

The Catalyst drivers can be installed from the ATI website, I haven't had to bother with the Ubuntu packaged driver.

Other than that, Karmic is still in Alpha stage and we will have to wait a bit longer to see more. I heard that the brown theme is being replaced according to a Shuttleworth interview.

If you interested in Ubuntu why not try Jaunty?

---

### Post by ad_267 on 2009-09-07
> **kreggz said:**
> I heard that the brown theme is being replaced according to a Shuttleworth interview.

If anything is replaced, it's still going to be orange/brown.

---

### Post by HappyFeet on 2009-09-08
> **ad_267 said:**
> If anything is replaced, it's still going to be orange/brown.

I would put my money on that they are going to change it to something more mainstream. I've seen some of the boot up screens being considered, and there was no hint of brown from what I saw. I have no doubt though, that it will be the best looking yet.

---

### Post by longtom on 2009-09-08
> **HappyFeet said:**
> I would put my money on that they are going to change it to something more mainstream. I've seen some of the boot up screens being considered, and there was no hint of brown from what I saw. I have no doubt though, that it will be the best looking yet.

I would miss it.  Not that I use any of it, but it is part of Ubuntu - kind of an icon.

---

### Post by mdsmedia on 2009-09-08
I haven't tried Karmic yet. Have had quite a few other PC related issues to deal with. Reinstalled Windows over Easter (first time since I installed Ubuntu in 2005), installed Arch on my play machine, bought a new laptop and triple booting Ubuntu, Arch and Vista, had an external HDD "die" on me and it's now installed as a 2nd HDD on my play machine, bought a new external 2.5" drive for storage/backup. 

So, that's my last few weeks (months). Now I've got more HDD space on the play machine and room to install Karmic.

This constant obsession with the "brown" Ubuntu theme kind of bothers me. When I first tried Ubuntu (Hoary (5.04) LiveCD in October 2005) the brown was a refreshing change from the Windows "blue". It was seriously nice. I installed Ubuntu because it was refreshing. The blues of Windows may well have made me look more closely at the OS and thought "better" of it.

If you don't like the "brown", change the theme. I know, first impressions and everything, but there's truly no accounting for taste. Heck, purple was my favourite colour for some short time. Now I like green....maybe it's the 15 year drought we're experiencing in SW Australia atm. If first impressions are anything to go by, my first impression of Ubuntu's brown was a positive. Then I liked the Debian blue when I tried it for the first time. I don't even know what colour my Arch desktop is LOL. Edit: OK it's xfce blue ;).

---

