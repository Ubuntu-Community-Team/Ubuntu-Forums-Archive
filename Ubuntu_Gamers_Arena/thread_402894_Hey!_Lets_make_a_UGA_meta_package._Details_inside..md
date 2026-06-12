---
title: "Hey! Lets make a UGA meta package. Details inside."
date: 2007-04-06
forum: Ubuntu Gamers Arena
---

### Post by MetalMusicAddict on 2007-04-06
With all the development work I've been doing with [Ubuntu Studio]("http://ubuntustudio.org") I've learned a thing or two about packages, metas and disk creation.

I was wondering if anyone here would be interested in helping me get together a list of packages that could be used for 2 possible metas.

Heres my ideas.

_**Meta 1:** [COLOR="Red"]ubuntugaming-desktop[/COLOR]_
This would grab things for a minimal desktop. Xserver, a DE (I'm thinking Fluxbox). a logon manager and any support files needed for games. Libraries and such.

Theres a package or so that is needed for some common installers I can never remember. :(


_**Meta 2:** [COLOR="Red"]ubuntugaming-data[/COLOR]_
Now Im unsure about the specifics of this one but this could be a list of games currently in the Ubuntu repos. ie: Open-Arena, Nexuiz, Neverball and so forth.

So my thinking is: create these metas that ONLY pull from the Ubuntu repos. Host the .debs somewhere and wget/install them.

Now for Feisty+1 we could even get these into the Ubuntu Repos so all have access to them.

Well its just a idea. Any thoughts?

---

### Post by Perfect Storm on 2007-04-06
Uber cool idea!

+1

I got artisian skill I can contribute with.

---

### Post by compiledkernel on 2007-04-06
Keep talking, im listening. =)

---

### Post by MetalMusicAddict on 2007-04-06
Artificial Intelligence Ive been trying to get you on Jabber. :)

So what we're gonna need to come up with is a list of packages needed in the metas.

Ill let people brainstorm. Im playing Quake4 atm. :)

---

### Post by hikaricore on 2007-04-06
Definately a great idea.

One thing we may want to consider, I can't remember if it's openbox or
fluxbox which has a "desktop icons" program that works along side it.  

We'd want to include something like this if we wanted it to look well
made to new and current linux gamers.  I don't wanna be the one
who has to explain for the 34th time:

"oh yea well the games should be in your flux/open menu, try right clicking".

---

### Post by hikaricore on 2007-04-06
Something else just occured to me.  It would be great to include a dropdown style terminal by default with the desktop environment.  Something like [Tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page") would be awsome.  Personally I use yakuake, but it uses kde libraries and is a memory hog.

Just throwin out an idea :P  as that guy who hates having to open a terminal in fluxbox because I'm lazy.

---

### Post by Perfect Storm on 2007-04-06
> **MetalMusicAddict said:**
> Artificial Intelligence Ive been trying to get you on Jabber. :)

So what we're gonna need to come up with is a list of packages needed in the metas.

Ill let people brainstorm. Im playing Quake4 atm. :)

Sorry, been busy (It's hollyday here so I'm on/off continously, but didn't bother shutting my comp off).


Padman would be an obvious candidate, I know the Quake 3 engine open source, but I'm not sure the graphic is (other than that we could ask for permission to add it).

Astromenace is a freeware, but I know the CEO of the game company, so if we ask I'm sure we get permission.

Memonix for the kids?

---

### Post by Perfect Storm on 2007-04-06
> **hikaricore said:**
> Something else just occured to me.  It would be great to include a dropdown style terminal by default with the desktop environment.  Something like [Tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page") would be awsome.  Personally I use yakuake, but it uses kde libraries and is a memory hog.

Just throwin out an idea :P  as that guy who hates having to open a terminal in fluxbox because I'm lazy.

+1

---

### Post by MetalMusicAddict on 2007-04-06
As far as what it "looks" like we cant touch anything atm. And branding it will be a whole lot more work that you realize. So for now we just need to get a default set of packages down for the environment.

As far as adding games we need to work with the Ubuntu-games team. Actually it might be the Ubuntu-multimedia team.

---

### Post by hikaricore on 2007-04-06
> **Artificial Intelligence said:**
> 
Padman would be an obvious candidate, I know the Quake 3 engine open source, but I'm not sure the graphic is (other than that we could ask for permission to add it).

[http://sourceforge.net/projects/wop-engine](http://sourceforge.net/projects/wop-engine)
[http://sourceforge.net/projects/wop-gamecode](http://sourceforge.net/projects/wop-gamecode)

I'm not sure what all this entails, but it seems most of it is open.

---

### Post by hikaricore on 2007-04-06
Sorry if we're getting a little ahead of ourselves.  >.<

I just got so many damn ideas when I started reading this
I couldn't help it. hehe

---

### Post by hikaricore on 2007-04-07
Assuming this would be from the Feisty repos:

abuse
beneath-a-steel-sky *
blobwars
chromium
crack-attack
flight-of-the-amazon-queen *
fluxbox
fluxconf
frozen-bubble
gl-117
neverball
nexuiz
openarena
pingus
* scummvm
solarwolf
supertux
supertuxkart
torcs
tremulous
wesnoth-all
wormux

This should give the user a great selection of games, direct from the stardard repos (includes universe and multiverse).

If we were able to use the viewizard repos:

astromenace
memonix (and one for the kids)

Just my take on the idea.  :)  I know I missed some greats but I'm in a hurry :P

---

### Post by Sammi on 2007-04-08
An idea:

Make the metapackage create a new separate log on possibility, maybe based on fluxbox or openbox, that only loads the bare minimun of a working enviroment that can list and lets the user launch the games that are installed. It would sort of create a cool gaming console like user experience and save RAM space at the same time, something that people with old machines love.

---

### Post by mrazster on 2007-04-09
Well I can't contribute with any haxxing or programing skillz...but I'd be more than willing to beta test for you if you need.
and mabye coem up with one or tow ideas.

One idea that popped in my head is..*(don't know if it would be possible thou)*..to provide installers for non natvie linux games...like "Loki Installers" i.e...there might be other installers out there to.
Also if it's possible to make "Wine" come preconfigured or atleast installed and the only thing needed would be to run "winecfg".

---

### Post by Dark Damo on 2007-04-09
I cant program but i could beta test maybe? I'm not too experienced in Linux but i suppose if something crapped out on me i could post the error?

---

### Post by sk8dork on 2007-04-10
i think fluxbox would be a great candidate for WM. usually fluxbox works well with rox, which is a great ultra fast file manager that can make icons on the desktop. as far as i know the fluxbuntu distro is using rox with fluxbox.

---

### Post by compiledkernel on 2007-04-10
1 clear issue - 

1. Installation of .run mediums (loki installers) - can these installers be converted into debs? 

example would be 

enemy territory, WoP, True Combat Elite, etc etc

2. Use of 3rd party debs. 

Getdeb dot net is providing debs for a variety of installs that could be converted into metas. They have a deb for sauerbraten now for instance. As well as a few others. Ufo Alien invasion would be another -- formerly installable only via loki installer, which assumes that the answer to number 1 is yes we can.

---

### Post by MetalMusicAddict on 2007-04-10
> **compiledkernel said:**
> 1 clear issue - 

1. Installation of .run mediums (loki installers) - can these installers be converted into debs? 

example would be 

enemy territory, WoP, True Combat Elite, etc etc


I'm unsure. For now though I think its outside the scope of what I was thinking but it would actually just be best to have someone grab the source and make .debs to begin with. ;)

.runs I always thought were rather easy to install. :)

> 2. Use of 3rd party debs. 

Getdeb dot net is providing debs for a variety of installs that could be converted into metas. They have a deb for sauerbraten now for instance. As well as a few others. Ufo Alien invasion would be another -- formerly installable only via loki installer, which assumes that the answer to number 1 is yes we can.

Absolutely not. EVERYTHING should come from the Ubuntu repos. Any games that aren't there should be worked on to be placed there. This benifits everyone. The Ubuntu devs and MOTU have been in contact with the guy who runs Getdeb but he doesn't have the time to make fully compliant Ubuntu .debs so he provides his diffs.

And the answer to #1 isnt *necessarily* a yes. Like I said, you can just get the source and make a .deb.

---

### Post by compiledkernel on 2007-04-10
Heres the problem. I think we are going to run into underflow. The main complaint that I get from users as a whole is that the games they want to play dont appear on the repos, or appear on the repos too slowly. Its taken 3 releases for Tremulous and Nexuiz to appear on the repos list (and they are community packages). It would seem prudent to me, to try to get said packages on the repos , even if it at all possible. That would provide for a much more enriched game experience outside of gnome-games and the few good games that are actaully offered on the repos themselves.

---

### Post by MetalMusicAddict on 2007-04-10
> **Sammi said:**
> An idea:

Make the metapackage create a new separate log on possibility, maybe based on fluxbox or openbox, that only loads the bare minimun of a working enviroment that can list and lets the user launch the games that are installed. It would sort of create a cool gaming console like user experience and save RAM space at the same time, something that people with old machines love.

You can already do this. Just install Fluxbox and you can choose it from GDM. You change your session. :) This is on a existing machine.

Giving old machines love is tricker and is what [Fluxbuntu]("http://fluxbuntu.org") is aimed at. Its lead also works on [Ubuntu Studio]("http://ubuntustudio.org") with me.

---

### Post by MetalMusicAddict on 2007-04-10
> **compiledkernel said:**
> Heres the problem. I think we are going to run into underflow. The main complaint that I get from users as a whole is that the games they want to play dont appear on the repos, or appear on the repos too slowly. Its taken 3 releases for Tremulous and Nexuiz to appear on the repos list (and they are community packages). It would seem prudent to me, to try to get said packages on the repos , even if it at all possible. That would provide for a much more enriched game experience outside of gnome-games and the few good games that are actaully offered on the repos themselves.

Then the best way at the moment is to become part of the Debian-games team and then make sure the packages are synced for Ubuntu. The Ubuntu-games team is kinda dead atm. This way everyone benefits though.

Thing is games arent that important when you have a complete distro to run so its best that if users really want games in the repos faster they need to get involved. complaining doesnt help. :) Its all a question of manpower.

---

### Post by MetalMusicAddict on 2007-04-16
Ok. Time to report after some testing.
[U]
Heres my HW[/U]:
[LIST]
[*]nForce 4 mobo
[*]AMD AM2 4600+ CPU
[*]nVidia 7950GT GFX card
[*]1GB RAM
[*]Dell 24" LCD @1920x1200
[/LIST]

So I did a command-line install and then grabbed fluxbox, xorg, nvidia-glx and tremulous.

On 1st boot Im using 70mb of RAM in the minimal setup. In a full Ubuntu/Gnome setup I use 130mb. Not really a big deal when you have a GB.

I can run Tremulous with the exact same settings in Gnome with the same results I get in Fluxbox.

So with no real performance difference that I can see I'm starting to rethink the idea. If you want a minimal environment you could install Fluxbox and change your session at GDM. I did this as well. There I used 90mb of RAM on startup.

Maybe UGA could head up getting more games into Debian? That way more people benefit. I could help with this.

I would suggest starting a IRC channel. It all depends on how serious/involved you want to get I guess.

---

### Post by hikaricore on 2007-04-16
You forget those of us who have 512mb of ram >.< @ PCI video cards (or integrated cards).

70mb of ram and 130mb of ram are a huge leap on lower end systems.

---

### Post by MetalMusicAddict on 2007-04-16
> **hikaricore said:**
> You forget those of us who have 512mb of ram >.< @ PCI video cards (or integrated cards).

70mb of ram and 130mb of ram are a huge leap on lower end systems.

Sure but I honestly think systems like that are in the minority for gamers. Mostly the PCI GFX card. Ive never known anyone using them for gaming. Obviously people do but I really don't thing running Fluxbox over Gnome in this instance would help. You still have well over 300mb of RAM available to you. I think the hardware itself would be the biggest limiting factor.

Also this stand alone system would work great for us but normal gamers this wouldn't work out well as you would be configuring everything by hand. People looking for ease-of-setup wouldn't get it.

I think its best to use Ubuntu/Gnome that way you can set up everything then use Fluxbox for when you want to game/cut overhead. However minimal I might think it is.

---

### Post by compiledkernel on 2007-04-16
Hmmmm, should use sysv-rc-conf to go in and remove whats not utterly nessecary?

---

### Post by mrazster on 2007-04-17
> **compiledkernel said:**
> Hmmmm, should use sysv-rc-conf to go in and remove whats not utterly nessecary?

Yeah...have a GUI tool like that installed...and provide a little "readme" on what could be removed and what not.

Better yet..not have them installed at all...if it's possible.

---

### Post by MetalMusicAddict on 2007-04-17
> **mrazster said:**
> Yeah...have a GUI tool like that installed...and provide a little "readme" on what could be removed and what not.

Better yet..not have them installed at all...if it's possible.

Im not at all suggesting we create new apps.

I also think memory usage is less critical then having newer hardware.

If you on a 192mb RAM system freeing up 20-30 mb wont help you run games any better. Chances are the rest of the system isnt up to the task. I'm sure some smart-a$$ will chime in but its not going to be the typical case.

---

### Post by mrazster on 2007-04-17
Well..personally I don't/won't have problem with performance for quite some time, as I have pretty decent hardware.
However I am a bit of a tweaker and gamer...and as far my computing interesst goes, gaming has always been the one thing that could eat performance.
So if your going to make this happend why not try to squeeze every ounce of performance ot off the hardware and make the games have the ablility to run at best possible settings for best gaming expirience.

And as for the GUI tools...I'm not stating that new toosl should be made...more inline of providing them in the meta package, as they already exist

---

### Post by MetalMusicAddict on 2007-04-17
> **mrazster said:**
> So if your going to make this happen why not try to squeeze every ounce of performance out of the hardware and make the games have the ability to run at best possible settings for best gaming experience.

Because in the grand scheme of things you get minimal performance gains for turning off things like services. I would gather most people just gain some RAM.

I don't think that makes much difference on most users systems. Not for the work anyway.

If you want an instant 30mb drop in RAM usage **sudo apt-get install fluxbox**.


Its just the more I think about this the more I think its not necessary. :-k

Really. If your a gamer typically you have a decent setup. On startup I use 130 some odd MB of RAM. I *might* hit 300 with a hell of alot running. If I turn all that off and just run a game I'm still not using anywhere near my 1gb of RAM. I think this is typical of most gamers.

---

### Post by Sokraates on 2007-04-24
[quote=MetalMusicAddict;2462254]Sure but I honestly think systems like that are in the minority for gamers. Mostly the PCI GFX card. Ive never known anyone using them for gaming. Obviously people do but I really don't thing running Fluxbox over Gnome in this instance would help. You still have well over 300mb of RAM available to you. I think the hardware itself would be the biggest limiting factor./quote]

I use my HP nx6110 laptop for gaming, which has an Intel 910i integrated graphics card sharing 512 MB of RAM. So 60 MB would make a difference. Though I must admit, that I run Kubuntu, some background apps and I've never had significant speed-problems.

The system is definitely not the fastest in the world, but it's more than enough to play games like Warzone 2100 (which should be included, if possible).

---

### Post by Nikusan on 2007-05-05
Would it be wise to create separate meta packages for shooters, strategy, arcade, etc? Similar to how ubuntu studio breaks up audio, video, etc.

Maybe not initially because the selection of games available from the repos is depressingly small, but in the future?

---

### Post by Sokraates on 2007-05-08
That's a great idea. I don't know how GNOME handles this, but KDE already has folders for Action, Boardgames, Strategy etc within the Games-folder. So it would only make sense to also have meta-packages for the genres.

---

