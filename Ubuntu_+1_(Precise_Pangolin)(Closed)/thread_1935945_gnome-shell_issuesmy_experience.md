---
title: "gnome-shell issues/my experience"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by creata.physics on 2012-03-05
i firstly would like to say how very impressed I am with my experience with 12.04 has been.

I booted the live cd and went to install, the installer asked me if i'd like to replace my linux mint partition and only that.  I also had a fedora 17 partition on as well that it did not detect and went ahead and deleted that, it was as lvm partition, not a big deal.

I was immediately surprised how everything worked immediately, unity was very fast and responsive, and I went ahead and started configuring my directories, preferences, etc, no issues at all.  I did an update and it ran even faster, I also installed gnome shell, which to my surprise worked on my intel 865G card which does not have hardware acceleration.  

Gnome-shell runs very fast and everything seems to work perfectly, my only issue is the way the main panel is displayed, the layout is all twonky.  i've attached a screenshot of my issue.  my question is that will i for now on be able to run gnome shell with my non openGL card or is this a bug and will it go away eventually? also would there be any way to go about fixing this issue? If i knew the css files for the theme i'll modify it myself, but since some of the text isn't appearing i'm worried it may be more than a design issue.

---

### Post by shuttleworthwannabe on 2012-03-05
Oi! does not look good at all; BTw did you format the linux mint drive when installing Ubuntu? if not, I suspect it retained some of your Mint Cinnamon desktop--you have a bottom bar that sorta gives it away.

You may want to choose "something else" at disc partitioning during installation so you can choose which partition to install Ubuntu and whether you want to format it or not.

I am assuming you have backed up all your data before installing afresh!

---

### Post by forrestcupp on 2012-03-05
Have you tried changing the theme to see if that takes care of it?

> **shuttleworthwannabe said:**
> Oi! does not look good at all; BTw did you format the linux mint drive when installing Ubuntu? if not, I suspect it retained some of your Mint Cinnamon desktop--you have a bottom bar that sorta gives it away.
It's possible that's just the notification area. In Gnome Shell when you go to the dash, it shows the notification area at the bottom. If the bottom bar is always there, though, then there's either something wrong, or he installed an extension to make it that way. But I am interested to know if the OP had a separate /home folder that could have carried over some old settings.

---

### Post by creata.physics on 2012-03-05
@shuttleworthwannabe - Mint/ the entire drive was formatted properly.  When I went to choose something else the installation crashed and did not let me use the advanced partitioning tool, that was no big deal as I use ubuntu one so i'm always backed up.  I've checked and the home folder does not contain anything from my mint installation, the bottom panel is a gnome shell extension that I installed from extensions.gnome.org. I was running mint 11 so I never used cinnamon.  All those problems aren't even an issue for me, it's just the theme that's an issue.

@forrestcupp - I've tried installing a few themes and changing them via advanced settings (gnome-tweak-tool) but in the themes section shell themes aren't enabled and when I change the GTK-Theme option the top bar does not change at all.  The missing text is everywhere, not just the notifications area, it's in the activities menu and every other menu. I thought I needed gnome-shell-extensions-user-theme to properly changed the theme ( this worked in fedora 17 ) but that extension doesn't seem available for 12.04.  Also I should have disabled the bottom bar extension, that is meant to be there and is just a regular extension allowing me to have that bar, that is not a bug or error in any way.

---

### Post by jbicha on 2012-03-06
What graphics driver and card are you using? I know that fglrx had bad issues with gnome-shell and it may still be broken for some people.

---

### Post by creata.physics on 2012-03-06
an intel 865G which does **not** have hardware acceleration.  This post was to find out if I was even meant to have the full gnome 3 experience ( which i think i should considering it is very fast and runs great ) and if my issue was a bug and how to fix it.  i may just hope the user-theme shell extension will be available soon and stick with this exact copy of ubuntu so I can have full gnome 3 without hardware accel.

---

