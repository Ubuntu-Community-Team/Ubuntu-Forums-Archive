---
title: "first look at 12.04"
date: 2012-06-17
forum: Testimonials &amp; Experiences
---

### Post by RH9R on 2012-06-17
I expect some adaptation time, but initial impressions are not favorable of the unity thing. 
While its fine to be able to search for apps, not having a place to go to see all the apps that come by default seems a big, gaping hole. Perhaps there is a way to do so, but it looks like eye candy is winning over what is straight forward and works.

---

### Post by coffeecat on 2012-06-17
Not a support request.

*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by MG&amp;TL on 2012-06-17
> **RH9R said:**
> I expect some adaptation time, but initial impressions are not favorable of the unity thing. 
While its fine to be able to search for apps, not having a place to go to see all the apps that come by default seems a big, gaping hole. Perhaps there is a way to do so, but it looks like eye candy is winning over what is straight forward and works.

Dash-Applications-Installed (see x more results)

Or Super+A, Installed(see x more results)

List of keyboard shortcuts if you hold the Super key.

---

### Post by zombifier25 on 2012-06-17
You can always to to the Applications lenses and choose to filter out the aps by categories, just like old GNOME.

---

### Post by RH9R on 2012-06-17
Thank you to each responder. I appreciate it. 
 
I'll spend some more time on the live CD. I've run ubuntu since 6.5, and have loved it. It would be a major pita to switch, but unity looks very much like glitz over function. 'Trying to 'outdo' apple at glitz seems an ill-chosen goal. 'D/l a live CD of Mint now also.

---

### Post by Myrddin Emrys on 2012-06-17
If you don't like Unity, you are spoilt for choice over the alternatives. Xfce, LXDE and KDE are all available from Ubuntu repositories (you don't even need to move to the spinoff distributions to install them). Both of the default desktops used by Mint are available directly from their developers as Ubuntu packages. MATE (an independent fork of Gnome 2) works exactly like Gnome in 10.x. Cinnamon is also worth a look. Either can be installed in just a few minutes. It's worth installing a copy of 12.04 in Virtualbox and playing around with the various options (MATE did it for me, with Xfce a close second).

---

### Post by thatguruguy on 2012-06-17
> **RH9R said:**
> I've run ubuntu since 6.5

Wait. What?

---

### Post by RH9R on 2012-06-18
Myrddin, this sounds promising. I appreciate your kind help here. 
I've not anything before w/ virtualbox - pretty ignorant about it. If you think its doable for someone who hasn't worked it before - I'd love to know how to follow this path. 'Would be nice to be able to run and work - do the evaluation of 12.04 w/out the slow live CD pace. 'Happy to do the necc. reading and such. 
Again, thanks for the kindness & especially with such good news.

---

### Post by RH9R on 2012-06-18
thatguruguy - yup, been using the LTS releases exclusively

---

### Post by ssulaco on 2012-06-18
> **RH9R said:**
> 
While its fine to be able to search for apps, not having a place to go to see all the apps that come by default seems a big, gaping hole.
I have very little experience with Unity,although it is Different,I like the looks,I agree,I like my application,places and sys tabs,Have you tried installing gnome-session-fallback from the software center? Im curious how well it does..

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by RH9R on 2012-06-19
I've not yet tried the fallback, and until the kind Myrddin told me about it - I didn't know that option existed. That's HUGE - and in the right way. I'm grinding through the needed learning curve to give unity every opportunity to prove itself. There are really good parts to be sure. I just have to get more time with it to give a fair evaluation.

---

### Post by Tamlynmac on 2012-06-19
> RH9R
I'll spend some more time on the live CD. I've run ubuntu since 6.5
> thatguruguy
Wait. What? 	
> RH9R
thatguruguy - yup, been using the LTS releases exclusively 	

I think what thatguruguy was trying to figure out was which version of  Dapper Drake you are referring to. Dapper (the first Ubuntu LTS release)  was released as 6.06 LTS in June of 2006. Edgy which was 6.10 (non LTS)  was released in October of 2006.

I've never heard of a 6.5 release of Ubuntu either. Perhaps, you would  share the name of that version? I've been Ubuntu only since 7.04 (Feisty  Fawn) and have never heard of a release that didn't include a .04 or  .10, except Dapper that was released in June (06/2006).

See [this]("https://en.wikipedia.org/wiki/List_of_Ubuntu_releases") for reference.

---

### Post by RH9R on 2012-06-19
Tamlynmac, apologies for the confusion - first Ubuntu was Dapper lts

---

### Post by Myrddin Emrys on 2012-06-19
> **RH9R said:**
> I've not anything before w/ virtualbox - pretty ignorant about it. If you think its doable for someone who hasn't worked it before - I'd love to know how to follow this path. 'Would be nice to be able to run and work - do the evaluation of 12.04 w/out the slow live CD pace.

Virtualbox is in the repositories, and is very easy to use - there's a nice GUI that prompts you for all the options. You use it to create a VM (virtual machine, complete with virtual hard disk stored in a file on your real disk, and the amount of RAM you specify), then grab a Linux ISO file (no need to burn it) and install it (or just boot as a live 'CD') inside the VM. No need to reboot your real ('host') machine and you can save the state of the VM at any time (and keep 'snapshots' to revert to a previous state).

That said, if you have a 12.04 installation you don't mind potentially messing up, you can just add any of the main desktops as packages, and choose which you want to use from the login menu (they generally co-exist quite well, but you can sometimes run into problems). The repositories have 'vanilla' versions of Xfce, LXDE and KDE (e.g. 'xfce4') as well as full-scale software collections equivalent to the spinoff distributions (e.g. 'xubuntu-desktop'). One easy thing to try is the gnome-panel package (the 'classic' or 'fallback' mode based on Gnome 3 mentioned above). If neither this nor the supported alternatives (Xfce, LXDE, KDE) suit you, you can look beyond the official repositories for MATE or Cinnamon packages for Ubuntu provided by their developers:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)

Both are trivial to install. MATE is my current favourite, and my standard desktop on 12.04 - it's basically Gnome 2 (as used in Ubuntu 10.x) under a different name. See:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

Mint also has MATE and Cinnamon versions of its current distribution (13) - out of the box, the MATE version is about the closest you can get in a modern mainstream distribution to Ubuntu 10.x (much closer than Ubuntu's own 12.04 unless you install MATE!).

---

### Post by RH9R on 2012-06-19
Myrddin, again, my thanks. I read about VM apps, installed virtualbox. All went well until loading 12.04. Msg said it needed 'pae' which is not on my cpu - said to run a kernel appropriate to my cpu. I opened another thread asking about this. Apart from the error msg, virtualbox was quite straightforward. 'Hope I can get it to work. 
 
I very much appreciate your kind help.

---

