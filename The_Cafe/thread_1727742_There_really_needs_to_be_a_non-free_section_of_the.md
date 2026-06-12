---
title: "There really needs to be a non-free section of the Software Center."
date: 2011-04-12
forum: The Cafe
---

### Post by nerdy_kid on 2011-04-12
I think there should be a special non-free "store" in the software center, for apps such as Google Chrome and Skype.  Basically any non-opensource "free" app.  Are there any plans to implement something like this?

thanks!

---

### Post by 3Miro on 2011-04-12
Last time I checked they were listed as "free" and "non-free" appropriately. Also, is Google Chrome in the Software Center, I think only Chromium is there and Chromium is "free".

Maybe have an option to "search" by criteria of "free" and "non-free".

---

### Post by CraigPaleo on 2011-04-12
There is a filter in KPackageKit.

[IMG]http://img23.imageshack.us/img23/5034/kkit.png[/IMG]

---

### Post by Darth Penguin on 2011-04-12
I think it would be a bad idea to have such an option by default. It defeats the purpose of GNU. My two cents.

---

### Post by uRock on 2011-04-13
> **nerdy_kid said:**
> I think there should be a special non-free "store" in the software center, for apps such as Google Chrome and Skype.  Basically any non-opensource "free" app.  Are there any plans to implement something like this?

thanks!

Are you meaning that you'd like to be able to just enable to install things such as Chrome and Skype without downloading and installing?

Example, you search for and select Chrome, then select to install it, then from there USC adds the Chrome ppa, then installs Chrome?

I think that would be cool.

---

### Post by Ctrl-Alt-F1 on 2011-04-13
I think that would be cool too.  I'm assuming the reasons we don't do this are:

1- Companies want control of their own repositories.

2- Canonical doesn't have the right to distribute software that doesn't belong to them, unless it is explicitly granted to them in the license.

---

### Post by CraigPaleo on 2011-04-13
If it added the company's own PPA then the company would have control over its product. The problem is then that Ubuntu wouldn't have control over the PPA's that are added through the Software Center.

Since the "free" non-free software is free to use, I don't see too big a problem with the companies offering a pre-packaged binary for inclusion in the official repos.

As for Chrome, I'm 100% certain that Chrome was once offered on Ubuntu. I don't know what's going on that front. The latest package I see for Skype is for 10.04. So, they aren't even concerned with keeping their own packages updated.

---

### Post by nerdy_kid on 2011-04-13
> **uRock said:**
> Are you meaning that you'd like to be able to just enable to install things such as Chrome and Skype without downloading and installing?

Example, you search for and select Chrome, then select to install it, then from there USC adds the Chrome ppa, then installs Chrome?

I think that would be cool.

Yeah, that would be really cool, but they won't do the ppa thing simply because it would trash the distro upgrade process.  Closed source apps need to be added to the repos -- I don't think ppas would work well enough in the long term.  Updates for certain applications should be backported too, maybe have a policy that as long as a program doesn't require new versions of core system libraries then a backported update would be ok.

Me having to manually go download and install google chrome is no big deal, but as Ubuntu gets more popular there is going to be more closed source apps being ported, and I think they (and application updates in general) should be integrated into the Software Center far better then they are currently.  If users are told to go to the respective websites and download the .deb how is that any better then Windows?  Having trusted software in the repos in a huge security plus, but if users want apps that aren't in the repos they are going to go download them, just like in Windows.

Also, I think that only select applications should be findable in the software center, for instance Unity now has this nice feature where it shows downloadable apps, but to a new user seeing an app like "ggz-txt" is really not helpful.  There needs to be a standard for (re)naming applications so that the names actually make sense to non-savy users.  Perhaps a simple intelligent popularity-based application sorting system for both the software center and Unity would solve the above problem, but I still think having a usability standard for application names would be a good idea.


And one last thing I think could be improved, and that is the screenshots.  The screenshots thing is really cool, but alot of the screenshots are shot with non-ubuntu themes.  Some (like gparted) are shot with the default GNOME2 theme (that aweful win98 'theme')  All the screenshots should be shot on Ubuntu, with one of the light themes imo.

Maybe I should have named this thread "critique on the Ubuntu Software Center" but oh well...

What do you guys think, am I crazy?

[edit]
About the legal stuff (Canonical doesn't have the right to distribute software that doesn't belong to them) how about acquiring permission?  I don't think there would be any issues as long as credit is given where credit is due, its more exposure for the application.

---

### Post by CraigPaleo on 2011-04-13
I don't think you're crazy. :) I'm just not sure what you mean when you say that only select apps should be shown. You use Kubuntu, right? I take it you're trying out Unity? KPackagekit has an option to only show applications and even only graphical apps if you want. It should probably be enabled by default since experienced users will know how to turn it on anyway. 

 It's hard to believe the SC wouldn't have those features. I've used it before but I don't remember the specifics of it. 

As for the screenshots of apps, they are kept here: [http://screenshots.ubuntu.com/](http://screenshots.ubuntu.com/)  It appears to be a Debian mirror, which is probably the reason for the inconsistencies. You can always add your own if you like. :)

---

### Post by Johnsie on 2011-04-13
Certainly as a developer I would never want Ubuntu/Cannonical being able to choose when I can or cannot update the software I have written. That should be between the user and the developer, not controlled by some sort of repo middleman who has nothing to do with the software itself. I like the idea of a centralised repository system, but it needs to be more developer friendly. The version control needs to be at the user/developer sides.

---

### Post by uRock on 2011-04-13
> **Johnsie said:**
> Certainly as a developer I would never want Ubuntu/Cannonical being able to choose when I can or cannot update the software I have written. That should be between the user and the developer, not controlled by some sort of repo middleman who has nothing to do with the software itself.

Nothing is stopping you from upgrading software.

---

### Post by Quadunit404 on 2011-04-13
I would like to see Opera in the repos as Opera Software WANTS people to distribute their freeware browser freely. They even had to change the EULA for Opera for Linux to reflect this want. That probably won't happen though due to Opera maintaining two repos - one for stable Opera releases and the other for alpha/beta releases.

---

### Post by nerdy_kid on 2011-04-13
> **CraigPaleo said:**
> I don't think you're crazy. :) I'm just not sure what you mean when you say that only select apps should be shown. You use Kubuntu, right? I take it you're trying out Unity? KPackagekit has an option to only show applications and even only graphical apps if you want. It should probably be enabled by default since experienced users will know how to turn it on anyway. 

 It's hard to believe the SC wouldn't have those features. I've used it before but I don't remember the specifics of it. 

As for the screenshots of apps, they are kept here: [http://screenshots.ubuntu.com/](http://screenshots.ubuntu.com/)  It appears to be a Debian mirror, which is probably the reason for the inconsistencies. You can always add your own if you like. :)


I'm actually switching from Kubuntu, I love unity :)

By "select apps" I mean that only "user friendly" applications would be readily available to the end user.  So, for instance using this new system a new user would only see in the software center:

1. Mature applications
2. Applications that follow the naming standards I suggested in my previous post.


This would avoid a lot of the "scary" sounding programs from being shown to new users, who have absolutely no idea what to do with them.  Some example of scary sounding applications:

Gurl
cournol
DebGTD
bpython
Spout
Euler
etc etc

These names would simply confuse new users, heck I have no idea what some of those do until I click on them.  The name should be self explanatory, like "Moovida Media Center".

For people who want access to the full list of apps, maybe there could be an option in Software Sources or something.


And sure, I could go and take a screenshot of every app and submit it to the debian screenshots or whereever, but if everyone got together and helped it would be way better.  Maybe I'll drop a bug report on launchpad about this.


@Johnsie they already do (which may be a good thing), which is why there are ppas...

---

### Post by HermanAB on 2011-04-14
Howdy,

There is a 'non-free version of the software installer'.  It is called Medibuntu.  

The Medibuntu repo is a fork of the Mandriva based Penguin Liberation Front repos in France:
[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by pi3.1415926535... on 2011-04-14
My idea is for some company to maintain a commercial repo, where all of the apps are checked for stability and security. Also, they would all have generic names for the main title, such as Media Player and Text Editor. For all of the changes, the company could submit them to the main project after a month or so.

---

### Post by slackthumbz on 2011-04-14
> **pi3.1415926535... said:**
> My idea is for some company to maintain a commercial repo, where all of the apps are checked for stability and security. Also, they would all have generic names for the main title, such as Media Player and Text Editor. For all of the changes, the company could submit them to the main project after a month or so.

Generic names are a terrible idea, generic descriptions however might be better. The problem is is that there are loads of different media players and text editors. You can't name 7 programs the same thing but you could categorise them via generic type and feature parity.

---

