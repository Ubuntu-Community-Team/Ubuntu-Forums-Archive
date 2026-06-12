---
title: "Please test out my gnome-lite remix cd"
date: 2009-10-05
forum: The Cafe
---

### Post by Lukios on 2009-10-05
First the Disclaimer: This is not meant to be another "Ubuntu Clone" however, if you would like to use this for your own computer that is fine by me. 


And I will include the openbox link as soon as it finishes uploading. Right now its taking a long time (3 hrs) to load.[/QUOTE]


> The ISO is finally done uploading to dropbox and you can download it here 

[http://dl.getdropbox.com/u/2339113/customdist.iso](http://dl.getdropbox.com/u/2339113/customdist.iso)

I have also included a screen shot since everyone seems to like them. Hopefully it will stir some interest.

Next time I have to do an update I will do it over-night so that there will be no broken download links.

Currently I'm a student attending college that does computer work on the side to help keep some finances flowing. Lately I have been doing a lot of work on older computers which have required me in most cases to install Linux in order to restore any use to the computer. For most of these computers I have been building them from the Mini.iso and only adding what is needed (bare essentials plus whatever else they say they need). This is one of 3 main remixes I will be making. The first which I have not uploaded yet will consist of LXDE the second which you see here is what I call Gnome-lite and I have yet to decide what I will do for newer computers, maybe you can suggest something. In any case this Gnome-lite cd is incomplete. This CD is simply a test to see what computers it can run decently on. This is where you come in. As of this last week, business has been slow, which has kept me from being able to test this on but a few computers. So what I would like for the Ubuntu community to do is to pull out your old computers and test this and tell me what the results are. 

As of now this is what the CD consists of

gnome-core
openbox WM (repacing metacity)
PCMandfm for both desktop and filemanager (replacing nautilus)
tint2 for the task manager - uses 1/4 of the resources of gnome-panel's task manager
preload
openoffice
firefox
epiphany
exaile
vlc
proprietary drivers
codec

Now I understand that FireFox is on the heavy end, but it is probably the best web browser available, and most computers that can run the gnome-lite set-up can probably run it fairly decent. In any case please post your results as well as your suggested browsers that will be able to run flash decently.

The other programs like openoffice, exaile and vlc should also work fine on most older computers, at least they have on the ones I have installed them on. Again this is where you come in and tell me your results along with your suggestions. My main goal is to have something that not only runs well but runs well out of the box requiring only a few changes to meet individual needs.

If there is enough interest in the project and people would like to use it as their main distro, I will consider maintaining this for that purpose as well as supplying my own repositories. If this becomes the case I will have them tailored more towards the needs of the general public. 


I almost forgot to leave a credit to the artists of the wallpaper


[http://dl.getdropbox.com/u/2339113/customdist.iso](http://dl.getdropbox.com/u/2339113/customdist.iso)


I almost forgot to leave a credit to the artists of the wallpaper

marcogoni

---

### Post by Lukios on 2009-10-06
Just updated the iso

---

### Post by Tibuda on 2009-10-06
Why do you have both Firefox and Epiphany?

---

### Post by credobyte on 2009-10-06
> **Oops! (403)**

 It seems you don't belong here!  You should probably try **[logging in]("https://www.getdropbox.com/login")**?

What the hell .. ?

---

### Post by Lukios on 2009-10-06
> Why do you have both Firefox and Epiphany?

Its a matter of choice. Firefox is more stable and complete, but epiphany is lighter

---

### Post by Lukios on 2009-10-06
> **credobyte said:**
> What the hell .. ?

let me try and edit the link

---

### Post by Tibuda on 2009-10-06
> **Lukios said:**
> Its a matter of choice. Firefox is more stable and complete, but epiphany is lighter

I know, but why both?

---

### Post by Lukios on 2009-10-06
If that answer doesn't satisfy you then I don't know what to tell you. I would appreciate it if you would take the time and test the iso and use what ever browser you like

---

### Post by Lukios on 2009-10-06
credobyte, the link has been updated BTW

---

### Post by Lukios on 2009-10-06
there seems to be a conflict with the new version of remastersys (which is what is used this time) and 9.04 with boot hanging at configuring network interface. Please allow me some time to fix this issues and update the iso. I will keep you updated.

---

### Post by AllRadioisDead on 2009-10-06
I agree, I would personally vote firefox out for epiphany, which does have plugins of its own and should not sacrafice any functionality for the average user. If they choose to install firefox later, that is their choice. 
Just my $0.02.

---

### Post by Lukios on 2009-10-06
what web browser would you suggest overall. I have tried midori and liked it, but its way to buggy and crashes alot.

---

### Post by Lukios on 2009-10-06
EDIT: The ISO has been updated with GDM and network-manager instead of wicd and slim to solve the hanging problem remastersys has with jaunty

The torrent is hosted here

[http://www.mininova.org/tor/3021378](http://www.mininova.org/tor/3021378)

And I will include the openbox link as soon as it finishes uploading. Right now its taking a long time (3 hrs) to load.

EDIT: Now that the ISO has been updated on the dropbox website I would go ahead and use this link since it will be faster then the torrent.

[http://dl.getdropbox.com/u/2339113/customdist.iso](http://dl.getdropbox.com/u/2339113/customdist.iso)

---

### Post by anonymous_user on 2009-10-06
If you use these PPAs:

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

You will have a more stable Midori. Plus it will have new features (since its a newer version).

BTW why do you include Openbox in your remix cd? Openbox = light, Gnome = not light

---

### Post by Lukios on 2009-10-06
> **anonymous_user said:**
> If you use these PPAs:

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

You will have a more stable Midori. Plus it will have new features (since its a newer version).

BTW why do you include Openbox in your remix cd? Openbox = light, Gnome = not light

I replace metacity with openbox to make gnome lighter. Same for nautilus which i replaced with pcmanfm.

oh and I tried midori from those ppa's and thats the one that kept crashing

---

### Post by Tibuda on 2009-10-06
> **Lukios said:**
> EDIT: The ISO has been updated with GDM and network-manager instead of wicd and slim to solve the hanging problem remastersys has with jaunty

I have switched back from Slim to GDM, because it was removed in Karmic due to a [bug allowing root access]("http://osdir.com/ml/ubuntu-devel-discuss/2009-09/msg00097.html").

---

### Post by Lukios on 2009-10-06
Good to know for future reference. As soon as the stable release of 9.10 comes out I will be making my new and hopefully complete/stable iso. This is just a test on the current 9.04 to make sure I have everything squared away for 9.10

---

### Post by SomeGuyDude on 2009-10-06
> **Lukios said:**
> If that answer doesn't satisfy you then I don't know what to tell you. I would appreciate it if you would take the time and test the iso and use what ever browser you like

I think the intention is that if you want light, put light stuff on there but give users the option of installing other stuff if they want.

---

### Post by Lukios on 2009-10-06
I want light, but I don't expect it to be super light. I expect it to be somewhere in the middle. The first remix that I am working on is going to be the lightest which consists of a modified lxde for really old computers. The second which is gnome-lite is supposed to be a bit heavier offering a bit more substance while still being lighter and faster then the standard Ubuntu install for old computers. Either way, I would like people to test it out to see how well the whole set up works on different computers of different specs so that I can adjust and make changes. If the set-up works great on most older computers except the firefox then I will get rid of it, but if the set up only works fine on computers that can handle firefox decently anyways, then there is no reason to get rid of it. When I said lite, I didn't really mean hd space, I was referring to resource usage. In any case this is mainly aimed for people I do computer work for, which in most cases are windows users. Im trying to make it as user friendly as possible. If people are interested in this project and would like me to make a version that is lighter both in hd space and resources then I will make one for that purpose as well.

---

### Post by Lukios on 2009-10-06
The ISO is finally done uploading to dropbox and you can download it here

[http://dl.getdropbox.com/u/2339113/customdist.iso](http://dl.getdropbox.com/u/2339113/customdist.iso)

I have also included a screen shot since everyone seems to like them. Hopefully it will stir some interest.

Next time I have to do an update I will do it over-night so that there will be no broken download links. 

Thank you for you patience and for testing this remix for me

---

### Post by Quick Silver on 2009-10-06
I just tried out your remix cd and I have to say I'm pretty surprised. It runes pretty good on my computer, however, my computer is not that slow.   P4 2.4 ghz 512 ram  Fire Fox runs decent enough, but I would suggest replacing it with Midori if you can find a stable release and if you plan on maintaining it for the public. I will keep you updated as I continue to test it out.

---

