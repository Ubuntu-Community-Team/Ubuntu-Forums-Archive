---
title: "new distro: larchix"
date: 2009-03-02
forum: The Cafe
---

### Post by chris200x9 on 2009-03-02
Hi I have created a distro based on archlinux it is live and has xfce 4.6 :) I call it larchix, being version 0.1 there are many issues one being it boots without X you must login with the user name larchix and password larchix then do a 'startx'. You can get the torrent here: [http://linuxtracker.org/index.php?page=torrent-details&id=49f57e95cba17f403d9643df8b49a1fc41bd0e4a](http://linuxtracker.org/index.php?page=torrent-details&id=49f57e95cba17f403d9643df8b49a1fc41bd0e4a)

I will post a direct download link soon, here is a list of known bugs/stuff that's wrong.

*X is not started by default
* sound will NOT work out of the box (at least it shouldn't)
*wireless will not work on startup, and by on startup I mean without setting it up
-----------------------------------------------------------------------------

this is all I know of at the moment, I hope to here back from testers/users

edit: direct link [http://www.larchix.linuxdistroofthemonth.com/larchix-0.1.iso](http://www.larchix.linuxdistroofthemonth.com/larchix-0.1.iso)

---

### Post by jimi_hendrix on 2009-03-02
<OT>
where did you learn how to make a distro?
</OT>

---

### Post by chris200x9 on 2009-03-02
it's basically arch + larch scripts only instead of creating a custom in chroot and editing that way.... I'm a big n00b and installed into qemu then created my ideal enviroment in X that had none of my data then "larhified" the whole install. It still needs much work but I think it's pretty good if I do say so myself :P

---

### Post by jimi_hendrix on 2009-03-02
is that all one does to make a linux distro!?

how does it install?

---

### Post by chris200x9 on 2009-03-02
> **jimi_hendrix said:**
> is that all one does to make a linux distro!?

how does it install?

the larch scripts install a installer but having never used it I cannot vouch for it I'm thinking of studying other distro's installers and making my own eventually. Also the larch scripts only "livify" archlinux (which by the way is actually my fav) :P

edit: yea it was pretty easy to *make* that's why I named it larchix because all the credit really goes to archlinux and the larch scripts.

---

### Post by smartboyathome on 2009-03-02
Just to let you know, the larch install program is broken on most virtual stuff, and any hard drive without an ms dos partition table. Also, I feel as if too many distros are being based on Arch Linux now. :(

---

### Post by chris200x9 on 2009-03-02
> **smartboyathome said:**
> Just to let you know, the larch install program is broken on most virtual stuff, and any hard drive without an ms dos partition table. Also, I feel as if too many distros are being based on Arch Linux now. :(

why the sad face? What's wrong with arch, up to date kernels, rolling release, and more stable than ubuntu for me. Life is good.

---

### Post by namegame on 2009-03-02
> **smartboyathome said:**
>  Also, I feel as if too many distros are being based on Arch Linux now. :(

I think people are trying to take Arch and make it "easy." Which I don't agree with. 

Arch is one of the easiest distributions out there if you can read. I don't know why people are trying to fix something that isn't broken.

---

### Post by smartboyathome on 2009-03-02
> **chris200x9 said:**
> why the sad face? What's wrong with arch, up to date kernels, rolling release, and more stable than ubuntu for me. Life is good.

Because I was originally (several months ago, though still continuing today) making Maryan Linux 2, which is based on Arch. I feel that most people have found there is no room for any more Ubuntu-based distros, and so are moving on to Arch in order to take all the ideas possible from it. Then when there is every distro and then some for it, that same croud will move on to the next distro.

---

### Post by chris200x9 on 2009-03-02
> **smartboyathome said:**
> Because I was originally (several months ago, though still continuing today) making Maryan Linux 2, which is based on Arch. I feel that most people have found there is no room for any more Ubuntu-based distros, and so are moving on to Arch in order to take all the ideas possible from it. Then when there is every distro and then some for it, that same croud will move on to the next distro.

not trying to be arguementative but, isn't that good? More distros = more choice.

edit: also more niches filled more adopters = more attention = more development of say third parties

---

### Post by smartboyathome on 2009-03-02
> **chris200x9 said:**
> not trying to be arguementative but, isn't that good? More distros = more choice.

Arch Linux already *has* choice. At the rate it is going, the choice may be removed in order to dumb down the distro when used in the new ones (like Ubuntu started doing). :(

---

### Post by Valok on 2009-03-02
I'd really like to see a gaming oriented Distro, so if anyone is looking for something to do, I'd be willing to help out making a gaming distro

---

### Post by chris200x9 on 2009-03-02
> **smartboyathome said:**
> Arch Linux already *has* choice. At the rate it is going, the choice may be removed in order to dumb down the distro when used in the new ones (like Ubuntu started doing). :(

again not trying to argue, yes arch has choice. Personally I would never use larchix (if I can admit that) but invision this grandma or better yet the not so technical savvy dad wants an up do date system easy to install. Yes an *buntu is that but you have to upgrade distros every 6 month or 5 years. Why not just have a cron job doing a pacman -Syu every week? Bleeding edge system (because many people want the newest thing just 'cuz' myself included :P) Also pacman has never failed me, update manager in ubuntu has. But I'm going to stop here before this just digresses into why I don't like ubuntu.

---

### Post by wolfen69 on 2009-03-02
> **chris200x9 said:**
> Yes an *buntu is that but you have to upgrade distros every 6 month or 5 years.
who says you have to upgrade? i personally don't care about rolling releases, and seeing how many years i can keep 1 install going. i'm constantly trying new things and starting off fresh. it's too boring to stick with 1 thing. but that's just me.

good luck with larchix.

---

### Post by chris200x9 on 2009-03-07
hey, just letting you know larchix-0.2 is out! find out more at [http://www.larchix.linuxdistroofthemonth.com](http://www.larchix.linuxdistroofthemonth.com) :popcorn:

---

### Post by izizzle on 2009-03-07
> **chris200x9 said:**
> not trying to be arguementative but, isn't that good? More distros = more choice.


True, but as it is, there are so many choices that one would become overwhelmed with all the distros available to them.

Edit: You released a new version of your distro within 3 days? :confused:

---

### Post by chris200x9 on 2009-03-07
> **izizzle said:**
> 
Edit: You released a new version of your distro within 3 days? :confused:

yea like it says in my blog almost nothing has changed....the stupid not starting X right away was just really bugging me....

---

