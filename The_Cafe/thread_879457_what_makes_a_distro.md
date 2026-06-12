---
title: "what makes a distro"
date: 2008-08-04
forum: The Cafe
---

### Post by Riffer on 2008-08-04
With all the incredible tools we have and the amazing HOWTO's, we can take Ubuntu and customize it to our heart's content.  My question is where does customizing leave off and becoming a distro start?

---

### Post by RiceMonster on 2008-08-04
When you have an installer and/or livecd available for others to use. You have to distribute it for it to be a distribution.

---

### Post by Riffer on 2008-08-04
With remastersys thats incredibly easy.  In effect one could get rid of the standard Ubuntu wallpaper and splash screen and be able to call it a new distro?

---

### Post by TheSlipstream on 2008-08-04
> **Riffer said:**
> In effect one could get rid of the standard Ubuntu wallpaper and splash screen and be able to call it a new distro?

Uh, sure. If you like being flamed. ._.

---

### Post by LaRoza on 2008-08-04
> **Riffer said:**
> In effect one could get rid of the standard Ubuntu wallpaper and splash screen and be able to call it a new distro?

It would be a derivative.

---

### Post by Riffer on 2008-08-04
> **LaRoza said:**
> It would be a derivative.

Kinda my thought, but where is the line between distro and derivative?

---

### Post by LaRoza on 2008-08-04
> **Riffer said:**
> Kinda my thought, but where is the line between distro and derivative?

I would give the general advise if it has its own repos for most packages, it is a distro. Ubuntu has different repos from Debian, so it is a distro.

Ubuntu SE doesn't, it is a derivative.

---

### Post by original_jamingrit on 2008-08-04
> **Riffer said:**
> Kinda my thought, but where is the line between distro and derivative?

It's difficult to say.  Zenwalk, for example, started out as a Slackware derivative, but now it's considered a distro in its own right, although it still maintains 99% compatibility with Slackware's packages.  Slackware itself started out as a derivative of SLS (Softlanding Linux System), when SLS changed their binary format.  Now SLS is long gone, and now Pat pretty much only depends on package maintainers (As well as the rest of the Slackware team, of course).

I guess it mostly depends on how much they rely on an upstream project.

As for what makes a distro, I'd call any variation on GNU/Linux a distro.  But most distros are derivatives (ie: somewhat modified versions) of other distros, while other distros just use their upstream as a base to work from (More like what Ubuntu does from Debian, or SuSE did from Slackware).  Still other distros are complete remixes (like Linux From Scratch, Arch, Crux, and others).  It helps to think this way while looking at something like the [Distro Timeline]("http://futurist.se/gldt/").

But you have to keep in mind that there's special cases too.  It's not totally fair to call something like Kubuntu a derivative of Ubuntu, since the Kubuntu team actually does a lot of work on most of the KDE packages available for the Ubuntu distro family.

---

### Post by loell on 2008-08-04
people say there's a line between a costumized ISO , Distro and a derivative. 

but i say it is a distro, when you say it is and you stand by it.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> In effect one could get rid of the standard Ubuntu wallpaper and splash screen and be able to call it a new distro?

Is it possible to do that with Remastersys?

---

### Post by Riffer on 2008-08-04
> **armageddon08 said:**
> Is it possible to do that with Remastersys?

With my limited knowledge of remastersys, the short answer is yes.

The long answer is, remastersys is that you have to have a system up and running.  Using remastersys, you then have a choice of using the backup option which keeps your settings or making a distributed copy to share.  

A for instance, you could take a standard install of Ubuntu, install codecs and such, install perhaps a dock, change the themes, wallpaper and login screen.  Then by using the distribution option with remastersys, build a LiveCD that can install your system on another comp.

You see I'm building a lightweight Gnome desktop for a colleague to use for his classroom.  It will have very few apps.  So using the HOWTO's for building a low memory system, and adding just the programs he needs, I have built a simple kiosk type system.  Hence my question,  would this be considered a "distro".  At the moment it has no Ubuntu desktop themes and the login screen is a plain gnome screen.  The only thing it has of Ubuntu is the repos.  Well the kernel is Ubuntu to.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> With my limited knowledge of remastersys, the short answer is yes.

The long answer is, remastersys is that you have to have a system up and running.  Using remastersys, you then have a choice of using the backup option which keeps your settings or making a distributed copy to share.  

A for instance, you could take a standard install of Ubuntu, install codecs and such, install perhaps a dock, change the themes, wallpaper and login screen.  Then by using the distribution option with remastersys, build a LiveCD that can install your system on another comp.

You see I'm building a lightweight Gnome desktop for a colleague to use for his classroom.  It will have very few apps.  So using the HOWTO's for building a low memory system, and adding just the programs he needs, I have built a simple kiosk type system.  Hence my question,  would this be considered a "distro".  At the moment it has no Ubuntu desktop themes and the login screen is a plain gnome screen.  The only thing it has of Ubuntu is the repos.  Well the kernel is Ubuntu to.

But, I had tried to make a distributable copy once or twice. What I got was customised version of Ubuntu with all the apps pre-installed which I had installed in my HDD system. But it didn't make the themes, cursors, icons etc. which I had installed on my system default on the live CD version created with remastersys.

---

### Post by Riffer on 2008-08-04
> **armageddon08 said:**
> But, I had tried to make a distributable copy once or twice. What I got was customised version of Ubuntu with all the apps pre-installed which I had installed in my HDD system. But it didn't make the themes, cursors, icons etc. which I had installed on my system default on the live CD version created with remastersys.

Again I have limited knowledge.  I think thats because your themes cursors etc., are found in you /home folder.  The distributed option removes that /home folder, you would need to install place your themes and such into the system folders where the Ubuntu themes are stored.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> Again I have limited knowledge.  I think thats because your themes cursors etc., are found in you /home folder.  The distributed option removes that /home folder, you would need to install place your themes and such into the system folders where the Ubuntu themes are stored.

That means, I should copy the theme folders to /usr/bin/themes. Then they should work....won't they?

---

### Post by Riffer on 2008-08-04
> **armageddon08 said:**
> That means, I should copy the theme folders to /usr/bin/themes. Then they should work....won't they?

/usr/share/themes/ is where I find them.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> /usr/share/themes/ is where I find them.
okay......so they become available in the live CD but how do I make 'em the default theme. There are so many other themes in the folder. Also is it possible to get custom apps to be at startup in the live CD and after the installation from that CD?

I know I'm hijacking your thread, but this was the only active thread I found on distro-creation and customization. I'm sorry. Hope you don't mind!

---

### Post by Riffer on 2008-08-04
> **armageddon08 said:**
> okay......so they become available in the live CD but how do I make 'em the default theme. There are so many other themes in the folder. Also is it possible to get custom apps to be at startup in the live CD and after the installation from that CD?

I know I'm hijacking your thread, but this was the only active thread I found on distro-creation and customization. I'm sorry. Hope you don't mind!

Not at all.  Again my knowledge is limited.  You're coming at this in a different direction then from what I've tried.

My suggestion is to be prepared to waste a few cd's.  Once you've put your themes etc. into the right system folder I would think that you would have to reset your defaults again to your themes etc.
Once that is done try remastersys again and see what happens.  If it works, great.  If not you could move the other themes into another folder and try again.

Let me know how it goes, good luck.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> My suggestion is to be prepared to waste a few cd's. 
Yeah....i can do that;no problem. I've quite a few rewritable CDs and DVDs at my disposal.  
> **Riffer said:**
> Once you've put your themes etc. into the right system folder I would think that you would have to reset your defaults again to your themes etc.
So....how do I reset the defaults to my themes?

> **Riffer said:**
> Let me know how it goes, good luck.
Thanks for your support man! I'd given up when you gave me these new brilliant ideas. Thanks again!:)

---

### Post by Riffer on 2008-08-04
> **armageddon08 said:**
> 
So....how do I reset the defaults to my themes?


If you move your themes etc. I would think that they would disappear from your desktop, because the "path" has changed.  You would have to reload/install them again, this time pointing to the new place that you stored them (/usr/share/themes/).  It can all be done using the gui.

---

### Post by armageddon08 on 2008-08-04
> **Riffer said:**
> If you move your themes etc. I would think that they would disappear from your desktop, because the "path" has changed.  You would have to reload/install them again, this time pointing to the new place that you stored them (/usr/share/themes/).  It can all be done using the gui.

Thanks....I get it now. I'll keep you informed abt my progress.:)

---

### Post by init1 on 2008-08-04
There are way too many Ubuntu based "distros" already IMHO. Everyone has a right to make their own though, I suppose.

---

### Post by Riffer on 2008-08-04
> **init1 said:**
> There are way too many Ubuntu based "distros" already IMHO. Everyone has a right to make their own though, I suppose.

Well with the big 3 (Debian, Redhat, and Slackware, I hope I got that right) being the basis for pretty much all other distros, what makes the others separate?

Case in point, LinuxMint.  Built from the kernel and perhaps the desktop of Ubuntu, it is considered a separate distro.  Yes it has its own limited repos and its own way that you can get a few apps, but it still relies on the Ubuntu repos for a lot of the other apps you can get.  I of 2 minds.

---

### Post by chris4585 on 2008-08-04
correct me if i'm wrong, but i thought in livecd's files such as things that are usually in ~/ are stored in /etc/skel/ or something, it depends on the process you make a livecd though, at least i think, i could be wrong, will someone correct me?

---

### Post by Riffer on 2008-08-04
> **chris4585 said:**
> correct me if i'm wrong, but i thought in livecd's files such as things that are usually in ~/ are stored in /etc/skel/ or something, it depends on the process you make a livecd though, at least i think, i could be wrong, will someone correct me?

You could be right, never the less for the personalized themes which you have stored in your ./home folder would not come up as the path then would be incorrect.

---

### Post by init1 on 2008-08-04
> **Riffer said:**
> Well with the big 3 (Debian, Redhat, and Slackware, I hope I got that right) being the basis for pretty much all other distros, what makes the others separate?

Case in point, LinuxMint.  Built from the kernel and perhaps the desktop of Ubuntu, it is considered a separate distro.  Yes it has its own limited repos and its own way that you can get a few apps, but it still relies on the Ubuntu repos for a lot of the other apps you can get.  I of 2 minds.
Yeah, Mint is it's own distro, but I was more referring to the distros where all they did was change the theme and add a few apps. And yes, those 3 are what most distros are based upon.

---

### Post by pbpersson on 2008-08-04
> **LaRoza said:**
> I would give the general advise if it has its own repos for most packages, it is a distro. Ubuntu has different repos from Debian, so it is a distro.

Ubuntu SE doesn't, it is a derivative.

Does this mean that Mint is not really a distro since it uses Ubuntu repositories?

OOPS....did not read far enough :(

---

### Post by armageddon08 on 2008-08-06
> **init1 said:**
> There are way too many Ubuntu based "distros" already IMHO. Everyone has a right to make their own though, I suppose.
That's the joy of using open-source, that's the joy of using linux and that's the joy of using Ubuntu!

---

### Post by chris4585 on 2008-08-06
maybe a distro is when everyone sees it as a distro?

---

