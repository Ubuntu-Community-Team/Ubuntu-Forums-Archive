---
title: "enough is enough"
date: 2006-10-13
forum: The Cafe
---

### Post by fuscia on 2006-10-13
i did a clean install last night and i am resolving to do my best *not* to hose my system anymore, or, if i do decide to do something that might screw it up, i will at least read the instructions beforehand. (i think i can keep this up at least until tomorrow. any bets?)

---

### Post by dannyboy79 on 2006-10-13
> **fuscia said:**
> i did a clean install last night and i am resolving to do my best *not* to hose my system anymore, or, if i do decide to do something that might screw it up, i will at least read the instructions beforehand. (i think i can keep this up at least until tomorrow. any bets?)

I have had to reinstall once due to a hard drive going dead, luckily maxtor is covering it free of charge. I can tell that after I did the reinstall and started editing files, I ALWAYS first create a backup of that file and I also am keeping a running tab of what files I always change just so that I know and remember what I did to get something working so I can possibly help others and obviously so I can repeat what I did if I need to. Hopefully I won't need to as I am going to be backing up my system very soon. Just need to find the best solution.

---

### Post by detgar on 2006-10-13
Good on you, fuscia.



(You'll last a week, tops. =p)

---

### Post by fuscia on 2006-10-13
> **detgar said:**
> (You'll last a week, tops. =p)

that might be a bit optomistic, but thanks for the encouragement.

dannyboy, you describe a most practical procedure. hopefully, that thought will be in the back of my mind the next time i start screwing around.

---

### Post by ComplexNumber on 2006-10-13
> **fuscia said:**
> i did a clean install last night and i am resolving to do my best *not* to hose my system anymore, or, if i do decide to do something that might screw it up, i will at least read the instructions beforehand. (i think i can keep this up at least until tomorrow. any bets?)
how did you screw it up this time to make you need to reinstall? 

make your home directory as large as possible and put all necessary files in there.

---

### Post by GarethMB on 2006-10-13
What did you do?

I haven't reinstalled in months, I'm pleased to say.

---

### Post by Lord Illidan on 2006-10-13
Come on, fuscia, just do a ```
sudo rm -rf *
``` in the terminal...

---

### Post by fuscia on 2006-10-13
that's the bad part: i don't remember what i did. part of it was using gtk-chtheme in openbox (which messes up the theme thing in gnome) and then using kde theming for gtk apps in kubuntu. when i used them in gnome, they still had the kde theming even after i had dumped kubuntu and gotten rid of its files. i had just installed last week, for some other reason, so it was no big loss to get a fresh install.

---

### Post by fuscia on 2006-10-13
> **Lord Illidan said:**
> Come on, fuscia, just do a ```
sudo rm -rf *
``` in the terminal...

what's that do?

---

### Post by GarethMB on 2006-10-13
So your love affair with KDE is over then?

---

### Post by Lord Illidan on 2006-10-13
> **fuscia said:**
> what's that do?

Erm.. don't try it out..please...or you'll kill me!

---

### Post by detgar on 2006-10-13
> **fuscia said:**
> what's that do?

It deletes everything in the current working directory.

But wouldn't:
```
rm -rf /*
```
be meaner? (deletes everything in root dir)

---

### Post by Chayak on 2006-10-13
Careful with jokes of that kind.  I had someone happly comply with it once when logged in as root on an active server... needless to say the server happily ate itself and he gave me the deer in the headlight look 'oops'.  That was a long night :P

---

### Post by ComplexNumber on 2006-10-13
>   That was a long night :P
oops :D. glad i wasn't in your shoes that night.

---

### Post by siacs on 2006-10-13
> **fuscia said:**
> that's the bad part: i don't remember what i did. part of it was using gtk-chtheme in openbox (which messes up the theme thing in gnome) *SNIP*
If you go back to Gnome and the theme is messed up just run [gtk-theme-switch]("http://packages.ubuntu.com/dapper/x11/gtk-theme-switch") (switch2), select/apply Clearlooks and all should be well.


~

---

### Post by siacs on 2006-10-13
> **fuscia said:**
> then using kde theming for gtk apps in kubuntu. when i used them in gnome, they still had the kde theming even after i had dumped kubuntu and gotten rid of its files.
When using KDE theming for GTK apps you need to make sure to switch back to no theme (leave it blank in Kcontrol) before logging out of KDE if you want to go back to regular GTK themes.

---

### Post by fuscia on 2006-10-13
> **GarethMB said:**
> So your love affair with KDE is over then?

it has gone the way of many a summer romance.

---

### Post by ComplexNumber on 2006-10-13
> **fuscia said:**
> it has gone the way of many a summer romance.
what? you've promise to write(erm, reinstall), but never do? :D

---

### Post by raublekick on 2006-10-13
i reinstalled Ubuntu yesterday. i had Kubuntu for the past almost 2 months. i got sick of using it exclusively and wanted to test Xubuntu and Ubuntu on my laptop. after installing (x)ubuntu-desktop, i realized for probably the 7th time that just isn't a good idea. nothing is like a good clean, 1 DE only install. so this time i chose gnome. 

i think i'm gonna make a live CD with reconstructor to make reinstalling even easier.

---

### Post by Anonii on 2006-10-13
> **Lord Illidan said:**
> Come on, fuscia, just do a ```
sudo rm -rf *
``` in the terminal...
in b4 "omfg you ****** up my linux"

---

### Post by justin whitaker on 2006-10-13
> **fuscia said:**
> i did a clean install last night and i am resolving to do my best *not* to hose my system anymore, or, if i do decide to do something that might screw it up, i will at least read the instructions beforehand. (i think i can keep this up at least until tomorrow. any bets?)

If you haven't hosed your system, well, you just aren't trying! Back to it! :mrgreen:

---

### Post by ComplexNumber on 2006-10-13
**fuscia**
maybe you should try having a romance with gnome this time. she's lovely looking, genuine, dependable, very easy to get along with, and she can take the rough with the smooth.

---

### Post by justin whitaker on 2006-10-13
> **detgar said:**
> It deletes everything in the current working directory.

But wouldn't:
```
rm -rf /*
```
be meaner? (deletes everything in root dir)

Yeah, that's mean. :twisted:

---

### Post by Lord Illidan on 2006-10-13
> **ComplexNumber said:**
> **fuscia**
maybe you should try having a romance with gnome this time. she's lovely looking, genuine, dependable, very easy to get along with, and she can take the rough with the smooth.

But she doesn't have a very large wardrobe of options from which to choose, leaving her rather .... drab. And of course, she is human, and loves dancing the tango, which I personally abhor.

---

### Post by ComplexNumber on 2006-10-13
> **Lord Illidan said:**
> But she doesn't have a very large wardrobe of options from which to choose, leaving her rather .... drab. And of course, she is human, and loves dancing the tango, which I personally abhor.
hehe yeah, i couldn't think of a simile for less configuration options :D. to sum up:
> maybe you should try having a romance with gnome this time. she's lovely looking, genuine, dependable, very easy to get along with, and she can take the rough with the smooth, but she doesn't tend to wear a lot of clothes.

---

### Post by skymt on 2006-10-13
> **justin whitaker said:**
> Yeah, that's mean. :twisted:

Not as mean as:```
nohup sudo rm -rf /* &
```That one won't stop unless you use kill or killall to stop it. Or, if you like:```
nohup sudo dd if=/dev/random of=/dev/hda bs=1024 &
```That one will erase your system *and* prevent trivial data recovery.

Again, [COLOR="Red"]DO NOT EVER[/COLOR] use any of these commands. They are only here to show... something or other.

---

### Post by fuscia on 2006-10-13
the thing that hooks me with kde is the icons. the window decorations and styles are a let down, though. i like a lot of the gtk and metacity themes quite a bit and there are some icon sets that i like, as well (dapper human and its ultra variants, OSX, snowish and most recently, this 'inspector matt' set). until i got my laptop, i was using openbox on my old desktop, so i was used to scrollable workspaces and right-click menus. kde has these features, so that was another lure.

---

### Post by fuscia on 2006-10-13
> **Lord Illidan said:**
> But she doesn't have a very large wardrobe of options from which to choose, leaving her rather .... drab. And of course, she is human, and loves dancing the tango, which I personally abhor.

just how many pairs of capri pants does one need?

"do these widgets make me look fat?"

---

### Post by croak77 on 2006-10-13
> **fuscia said:**
> that's the bad part: i don't remember what i did. part of it was using gtk-chtheme in openbox (which messes up the theme thing in gnome) and then using kde theming for gtk apps in kubuntu. when i used them in gnome, they still had the kde theming even after i had dumped kubuntu and gotten rid of its files. i had just installed last week, for some other reason, so it was no big loss to get a fresh install.

All you had to do was delete your ~/.gtkrc-2.0. KDE, gtk-theme-switch, and gtk-chtheme use that file to set gtk2 theme, gtk2 icons, gtk2 font, etc. The GNOME theme manager does not use ~/.gtkrc-2.0. So there is a conflict when you have your theme set in GNOME theme manager and written in your ~/gtkrc-2.0 when using GNOME.

---

### Post by ComplexNumber on 2006-10-13
> **fuscia said:**
> the thing that hooks me with kde is the icons. the window decorations and styles are a let down, though. i like a lot of the gtk and metacity themes quite a bit and there are some icon sets that i like, as well (dapper human and its ultra variants, OSX, snowish and most recently, this 'inspector matt' set). until i got my laptop, i was using openbox on my old desktop, so i was used to scrollable workspaces and right-click menus. kde has these features, so that was another lure.
you can get crystal icons for gnome if they're the icons that you're wanting. alternatively, it may sound as if xfce may suit you given what you've said.

---

### Post by justin whitaker on 2006-10-13
> **skymt said:**
> They are only here to show... something or other.

That we should never steal your lunch money and then leave our terminal unattended? :mrgreen:

---

### Post by Lord Illidan on 2006-10-13
> **skymt said:**
> Not as mean as:```
nohup sudo rm -rf /* &
```That one won't stop unless you use kill or killall to stop it. Or, if you like:```
nohup sudo dd if=/dev/random of=/dev/hda bs=1024 &
```That one will erase your system *and* prevent trivial data recovery.

Again, [COLOR=Red]DO NOT EVER[/COLOR] use any of these commands. They are only here to show... something or other.

Ok...something to try on the linux firewall at school :)

---

### Post by K.Mandla on 2006-10-13
> **fuscia said:**
> i did a clean install last night and i am resolving to do my best *not* to hose my system anymore, or, if i do decide to do something that might screw it up, i will at least read the instructions beforehand. (i think i can keep this up at least until tomorrow. any bets?)
Don't feel bad. I reinstall twice, sometimes three times a week. It makes me feel *clean*. ... :mrgreen:

---

### Post by Lord Illidan on 2006-10-13
Hey, fuscia, if you want a challenge..let me give you an easy one to start with...Linux from Scratch would be a piece of cake...

---

### Post by fuscia on 2006-10-13
> **croak77 said:**
> All you had to do was delete your ~/.gtkrc-2.0. KDE, gtk-theme-switch, and gtk-chtheme use that file to set gtk2 theme, gtk2 icons, gtk2 font, etc. The GNOME theme manager does not use ~/.gtkrc-2.0. So there is a conflict when you have your theme set in GNOME theme manager and written in your ~/gtkrc-2.0 when using GNOME.

there were other issues, as well, just harder to define. 

[quote=complex number]
you can get crystal icons for gnome if they're the icons that you're wanting. [/quote]

i love the black+white set, OS-L, realistiK, vuitton, etc. i would use konqueror just because of the icon.

---

### Post by ComplexNumber on 2006-10-13
> i love the black+white set
do you mean this one?
[http://art.gnome.org/themes/icon/1281](http://art.gnome.org/themes/icon/1281)

its also available on kde.

---

### Post by fuscia on 2006-10-13
> **ComplexNumber said:**
> do you mean this one?
[http://art.gnome.org/themes/icon/1281](http://art.gnome.org/themes/icon/1281)

its also available on kde.

no, i meant this one - 
[http://www.kde-look.org/content/show.php?content=24645](http://www.kde-look.org/content/show.php?content=24645)

(why did i go over to kde look??? stupid, stupid, stupid!!!)](*,)

---

### Post by ComplexNumber on 2006-10-13
> **fuscia said:**
> no, i meant this one - 
[http://www.kde-look.org/content/show.php?content=24645](http://www.kde-look.org/content/show.php?content=24645)

(why did i go over to kde look??? stupid, stupid, stupid!!!)](*,)
oh i see.
they look rather nice actually. i don't think they're available on gnome.

---

### Post by ComplexNumber on 2006-10-13
**fuscia**
what exactly put you off kde? are you sure its merely kubuntu thats the problem and not kde?

---

### Post by fuscia on 2006-10-13
> **ComplexNumber said:**
> **fuscia**
what exactly put you off kde? are you sure its merely kubuntu thats the problem and not kde?

no, it's kde. after a while, decorating kde can be like playing with mr. potato head (or mr. ktuberling).

---

### Post by ComplexNumber on 2006-10-13
> **fuscia said:**
> no, it's kde. after a while, decorating kde can be like playing with mr. potato head (or mr. ktuberling).
hehe nice imagery :D. i know its a hassle, but i've seen lots of people make their kde desktop look reasonably nice.

---

### Post by Anonii on 2006-10-13
This thread has changed so many topics in so little time, that I will take a   deep breath and say that Godwin's law is soon to be seen once again.

---

### Post by skymt on 2006-10-13
> **Anonii said:**
> This thread has changed so many topics in so little time, that I will take a   deep breath and say that Godwin's law is soon to be seen once again.

I've never actually seen anyone invoke Godwin's law on these forums. Other forums, but not these. That's probably a good sign. ;)

---

### Post by psycosmyth on 2006-10-14
just install xubuntu, don't even change the background, heck just use a live disk. :mrgreen: 

Been there, I had a windows moment once and reinstaled xp, deleting ubuntu, that was like having an affair! Then I instaled kubuntu cause kde is so cool, then i screwed everything up, not sure how, then reinstaled xubuntu and taged gnome back on. i'll probaly do it again by messing with xgl or some other mess:p

---

### Post by fuscia on 2006-10-14
well, that lasted longer than i thought it would...

[[IMG]http://img80.imageshack.us/img80/4484/kdescrmd6.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=kdescrmd6.jpg)

i blame aysiu - [http://ubuntuforums.org/showthread.php?t=277090](http://ubuntuforums.org/showthread.php?t=277090)
he led me astray

edit: ha! dumped it. back on the wagon...

---

### Post by Lord Illidan on 2006-10-14
> **skymt said:**
> I've never actually seen anyone invoke Godwin's law on these forums. Other forums, but not these. That's probably a good sign. ;)

Only fuscia could be so evil to change allies twice over a few days..reminds me of Hit*** and his Na** as*

---

### Post by ahaslam on 2006-10-14
> **fuscia said:**
> that's the bad part: i don't remember what i did. part of it was using gtk-chtheme in openbox (which messes up the theme thing in gnome) and then using kde theming for gtk apps in kubuntu. when i used them in gnome, they still had the kde theming even after i had dumped kubuntu and gotten rid of its files. i had just installed last week, for some other reason, so it was no big loss to get a fresh install.
I also found that changing gtk themes in other DE's screwed up my themes. 
After a lot of fustration, I found that dellting hidden files starting with  '.gtk' from my home directory sorted it out. If you want to set different gtk themes under different DE's, you'll have to make a simple script to run when logging in. If you want more info on this, let me know.

Tony.

---

### Post by fuscia on 2006-10-14
> **Lord Illidan said:**
> Only fuscia could be so evil to change allies twice over a few days..reminds me of Hit*** and his Na** as*

evil? i'm nothing but a great joy in all your lives.

---

