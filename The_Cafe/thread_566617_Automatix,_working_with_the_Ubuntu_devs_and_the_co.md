---
title: "Automatix, working with the Ubuntu devs and the community"
date: 2007-10-03
forum: The Cafe
---

### Post by jtbl on 2007-10-03
We, the Automatix Team, are currently making several changes for Gutsy.  I have already mentioned the technical changes, but I am also going to mention the non-technical ones as well.  Our main goal for Gutsy is to improve our collaboration efforts between us, the Ubuntu devs, and the community.  The way we are doing that is changing Automatix's purpose.  Automatix was originally designed to be an installation script that would help get a user's Ubuntu install up and running. We believe that it is pointless to make it an alternative to methods already in Ubuntu. So starting with Gutsy, Automatix will now be used to fill in the holes in which Ubuntu cannot fill.  We will work with the Ubuntu devs to get things that are in Automatix into Ubuntu, and as they get moved into Ubuntu they will be removed from Automatix.  As things are removed from Automatix more will be added to Automatix, and eventually Ubuntu.  This cycle will continue until users have decided that there is no longer a need for Automatix.  A launchpad spec has been created for this plan which can be found here:   [https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration]("https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration")

---

### Post by rsambuca on 2007-10-03
This sounds very positive to me.

---

### Post by smoker on 2007-10-03
looking forward to gutsy, and the new automatix :D

---

### Post by n3tfury on 2007-10-03
it's more fun learning how to install certain things than having something do it for me.

---

### Post by matthew on 2007-10-03
This sounds like a good step, glad to hear it. I applaud this idea.

**note to potential posters in the thread**
I would like to keep this thread open and where it is. Please help keep it that way by choosing not to rehash old, tired arguments and by choosing not to post in a negative manner in this thread. If you have nothing of value to say, please say nothing and move on Thanks!

---

### Post by jrusso2 on 2007-10-03
Now what will people find to complain about?

---

### Post by 23meg on 2007-10-03
Good news, albeit a bit late.

---

### Post by bodhi.zazen on 2007-10-03
\o/

---

### Post by starcraft.man on 2007-10-03
Whatever, had enough pointless fighting to get to this. Anyway, I'm with Aysiu on this, if I know someone doesn't want trouble/work I'll recommend something like Mint (and documentation if they want). If I know they're a tweaker/techie, I'll just point them to proper documentation. I don't really see a middle ground needed, I guess that's me.

---

### Post by stmiller on 2007-10-03
This is good news, but yes the core Ubuntu devs are already doing this same work. (Making codec and other installs user friendly, all from official repos.)

---

### Post by Polygon on 2007-10-03
sounds good, now there can be one less argument on the forums ;)

---

### Post by jtbl on 2007-10-03
The overall goal I had planned is for the entire community to come to an agreement on one, possibly two, ways for a user to do something that works well and is easy to understand and work with.  Constant fighting and arguing and having multiple solutions (good or bad) to a problem doesn't get us anywhere.  Having one or two solutions that everyone can agree on is the best way to get things done.

---

### Post by Polygon on 2007-10-03
i think as long as you make sure that you work with the devs / package maintainers  to make sure that it doesnt cause any problems with anyones system, then I'm sure there won't be any massive arguments about it anymore xD

---

### Post by jtbl on 2007-10-03
> **Polygon said:**
> i think as long as you make sure that you work with the devs / package maintainers  to make sure that it doesnt cause any problems with anyones system, then I'm sure there won't be any massive arguments about it anymore xD

Thats the plan.  :)

---

### Post by Paul820 on 2007-10-03
When i first started with ubuntu i thought automatix was excellent for me, a beginner in this strange linux world. It never broke my system once, as i have gained more experience i don't need it. I think it's great they are working with the ubuntu developers, because first time users still need a little helping hand to get started. It helped me, and i'm sure it will help others.

---

### Post by jimrz on 2007-10-03
GREAT ... never did fully understand all the previous animosity and am thrilled to see this step towards putting it behind the entire community.

---

### Post by forrestcupp on 2007-10-03
> **n3tfury said:**
> it's more fun learning how to install certain things than having something do it for me.

You could always use a harder distro like Gentoo that's not meant to be easy for people.

---

### Post by 3rdalbum on 2007-10-03
I'm glad that Automatix is going to be working with the Ubuntu developers. I was a little alarmed with some of the things that it did, but to be honest I'm sure my programs are just as badly behaved :-)

I think there will always be a need for Automatix, as there are always things that are bad, ugly, and fugly (libdvdcss :-)  )

---

### Post by Frak on 2007-10-03
w00t \o/

---

### Post by jtbl on 2007-10-03
The success of this plan will require the support of the Ubuntu devs and members of the community.  Unless we get support from them this plan will go nowhere.

---

### Post by AlphaMack on 2007-10-03
And what about Medibuntu?

---

### Post by jtbl on 2007-10-03
> **alphasubzero949 said:**
> And what about Medibuntu?

What about Medibuntu? 

This is how the plan works.  Everyone needs to express their opinions.

Heres mine:

Medibuntu should be used for what Ubuntu can't host for legal reasons, stuff like libdvdcss2, w32/w64codecs, and software with serious patent issues.  Other software like Acrobat Reader and Skype would be better off in the commercial repository (called partner in Gutsy) run by Canonical.  This would require two things one being the demand of the community and two the willingness of Canonical to go through the steps of getting these packages in the commercial repository.

---

### Post by jtbl on 2007-10-04
The final feature list for Automatix for Gutsy:  [http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks]("http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks")

As you can see, most of the items that are also found in gnome-app-install/synaptic/adept have been removed leaving only the ones you cant find in the Ubuntu repos.

---

### Post by fuscia on 2007-10-04
arnieboy and i had a brief conversation a while back, while he was helping me get beryl running on kde. do you all have more things going on with kde for gutsy (at that time, he suggested that most of the automtix folks tended to be gnome users)?

---

### Post by jtbl on 2007-10-04
> **fuscia said:**
> arnieboy and i had a brief conversation a while back, while he was helping me get beryl running on kde. do you all have more things going on with kde for gutsy (at that time, he suggested that most of the automtix folks tended to be gnome users)?

As far as I know, everyone on the Automatix Team uses GNOME.  As far as adding KDE apps, with Gutsy we started off on a more desktop environment generic path.  Things can change however, the current feature list isn't set in stone.  Most of the KDE options we had in previous versions all were apt-get install from the Ubuntu repos, and in this version of Automatix we are trying to move away from that.

---

### Post by lionel47 on 2007-10-05
I'm glad to hear the Automatix folks are not going to stop developing.  I wrote about this at [www.5thwind.com.:](www.5thwind.com.:))

---

### Post by jtbl on 2007-10-05
There are still a lot of codecs and plugins Ubuntu-Restricted-Extras doesn't include, although it does get the most used ones installed.  The ones it leaves out are the xine codecs and plugins, which many people will say works better that the gstreamer codecs and plugins.  Also, its leaves out a few smaller ones like xvid, faac/faad, etc.

---

### Post by PartisanEntity on 2007-10-05
This is good news, glad to hear that the community is working together. Wishing you the best of luck.

---

### Post by justin whitaker on 2007-10-05
> **jtbl said:**
> There are still a lot of codecs and plugins Ubuntu-Restricted-Extras doesn't include, although it does get the most used ones installed.  The ones it leaves out are the xine codecs and plugins, which many people will say works better that the gstreamer codecs and plugins.  Also, its leaves out a few smaller ones like xvid, faac/faad, etc.

Sounds like a great plan.

---

### Post by Paqman on 2007-10-05
It'll be interesting to see what Automatix morphs into during this process.

---

### Post by Banny706 on 2007-10-05
I think the Automatix Team are heading in the right direction.  To me it isn't about making it simple for me (that's cool too), its about making it simple to the Windows users who are sick and tired of the baggage that goes along with that OS.  These people decide to take a chance with Linux and Ubuntu in particular but have no knowledge of Linux.  Automatix is for them.
 
For me, it allows me to go catch a flick while all the goodies get installed with a few clicks of my mouse.  Thank you Automatix.

---

### Post by BigSilly on 2007-10-05
> **Banny706 said:**
> I think the Automatix Team are heading in the right direction.  To me it isn't about making it simple for me (that's cool too), its about making it simple to the Windows users who are sick and tired of the baggage that goes along with that OS.  These people decide to take a chance with Linux and Ubuntu in particular but have no knowledge of Linux.  Automatix is for them.
 
For me, it allows me to go catch a flick while all the goodies get installed with a few clicks of my mouse.  Thank you Automatix.

I agree. For me, after gaining the knowledge I need to progress with Linux, I won't need to use Automatix on the next Ubuntu release, but I'll certainly recommend it to anyone who wants to move to Linux from Windows.

---

### Post by RAV TUX on 2007-10-05
> **jtbl said:**
> We, the Automatix Team, are currently making several changes for Gutsy.  I have already mentioned the technical changes, but I am also going to mention the non-technical ones as well.  Our main goal for Gutsy is to improve our collaboration efforts between us, the Ubuntu devs, and the community.  The way we are doing that is changing Automatix's purpose.  Automatix was originally designed to be an installation script that would help get a user's Ubuntu install up and running. We believe that it is pointless to make it an alternative to methods already in Ubuntu. So starting with Gutsy, Automatix will now be used to fill in the holes in which Ubuntu cannot fill.  We will work with the Ubuntu devs to get things that are in Automatix into Ubuntu, and as they get moved into Ubuntu they will be removed from Automatix.  As things are removed from Automatix more will be added to Automatix, and eventually Ubuntu.  This cycle will continue until users have decided that there is no longer a need for Automatix.  A launchpad spec has been created for this plan which can be found here:   [https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration](https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration)

Awesome news!, I wish the union between Automatix and Ubuntu a long and happy one.

---

### Post by xWHEELSx on 2007-10-05
Well done Automatix, nice move

---

### Post by Hobbsee on 2007-10-06
looking forward to seeing this published in a place that the majority of ubuntu developers actually read - where this is not it.

How do you respond to [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html) ?

---

### Post by jtbl on 2007-10-06
> **Hobbsee said:**
> looking forward to seeing this published in a place that the majority of ubuntu developers actually read - where this is not it.

How do you respond to [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html) ?

Where do you recommend I publish this information?

About the analysis, I read through it and fixed all the major bugs, a few minor cosmetic bugs still exist, and the Gutsy release will include all of these bugfixes.  I could go into greater detail but I think the fact that they have been fixed is whats important.

---

### Post by LuisC-SM on 2007-10-06
> **23meg said:**
> Good news, albeit a bit late.

Yup

---

### Post by kitterma on 2007-10-07
> **jtbl said:**
> Where do you recommend I publish this information?

About the analysis, I read through it and fixed all the major bugs, a few minor cosmetic bugs still exist, and the Gutsy release will include all of these bugfixes.  I could go into greater detail but I think the fact that they have been fixed is whats important.

Posting to ubuntu-devel-discuss was a good place (that's how I found this thread).

About your response to the analysis, please point us to the source so we can have a look.

---

### Post by jtbl on 2007-10-07
> **kitterma said:**
> Posting to ubuntu-devel-discuss was a good place (that's how I found this thread).

About your response to the analysis, please point us to the source so we can have a look.

[http://ubuntuforums.org/showthread.php?t=562550](http://ubuntuforums.org/showthread.php?t=562550)

---

### Post by kitterma on 2007-10-08
> **jtbl said:**
> [http://ubuntuforums.org/showthread.php?t=562550](http://ubuntuforums.org/showthread.php?t=562550)

I didn't see a link to source there.  The getautomatix forum link is currently dead.  Please post a link to where the actual source can be gotten from.

---

### Post by LuisC-SM on 2007-10-08
> **kitterma said:**
> I didn't see a link to source there.  The getautomatix forum link is currently dead.  Please post a link to where the actual source can be gotten from.
**[COLOR="DarkRed"]dismiss this this comment please[/COLOR]**
I think this wil be the next response:
[http://ubuntuforums.org/showpost.php?p=3451744&postcount=16](http://ubuntuforums.org/showpost.php?p=3451744&postcount=16)

I wonder why this move wasn't made at the correct time?
The only thing I can thank automatix is that they teach me how to reinstall ubuntu a dozen of times ...:guitar:
I'm not up against this move BTW, it's just that I cannot understand why the team rejected all the feedback given then, bad or good it was always feedback,.How can I be jealous of a program when the program is hosing my pc? 
What does'nt kill you ... gives you more strenght!!! IF by the time when these problems happened would've been fixed, Mr. Garret's comments would be a lot different.(Maybe they wouldn't even exist)
Cheers
Luis

PS. I don't have anything against automatix, but personally I will Never use it for the rest of my ubuntu life

---

### Post by OldTimeTech on 2007-10-08
As a noob (and still sorta one), automatix saved me a couple of times....I will not badmouth.  

I´m glad they are now working with the devs and hope that the flamewars and such can be a thing of the past.

Congrats Automatix team.

---

### Post by kitterma on 2007-10-08
OK.  I can get to the automatix forums now.  No link to source in that thread that I could find.

BTW, why is the new policy (from the Automatix forum thread) "Won't install software from Ubuntu repos unless the package is broken".  If the package is broken, how about working with us to fix it?  Even after release, if a package is in fact broken we can get an SRU done to fix it.

---

### Post by boast on 2007-10-08
I saw  Automatix2 as a tool used for new linux users to learn of programs that exist for linux, and have it easily installed. Or course a simple 'apt-get install' will get the program installed, but how would a beginner learn of the programs existing in the first place?

---

### Post by notwen on 2007-10-08
Although I'm not a Automatix user, I'm glad you guys are working w/ the Ubuntu devs to make things roll a bit smoother. Good luck with your future releases. =]

---

### Post by b0ng0 on 2007-10-08
Good to hear. I have always had to end up using Automatix when for example, Azureus just doesn't work via normal install but the Automatix one always seems to :)

---

### Post by Palmyra on 2007-10-08
I like the positive attitude of the Automatix team.  It's definitely a model team; superb members, I say.

---

### Post by jtbl on 2007-10-08
> **kitterma said:**
> OK.  I can get to the automatix forums now.  No link to source in that thread that I could find.

BTW, why is the new policy (from the Automatix forum thread) "Won't install software from Ubuntu repos unless the package is broken".  If the package is broken, how about working with us to fix it?  Even after release, if a package is in fact broken we can get an SRU done to fix it.

Automatix for Gutsy isn't up yet because we still need to get our repos for Gutsy setup.  I can however post the code for people to look at.

Our plan is to work with the Ubuntu devs in getting the package fixed.  If the Ubuntu devs refuse or cannot fix the package, then we will place a working package in our repos.

EDIT: I have posted the code for both the i386 and AMD64 versions of Automatix for Gutsy.

---

### Post by kitterma on 2007-10-08
> **jtbl said:**
> Automatix for Gutsy isn't up yet because we still need to get our repos for Gutsy setup.  I can however post the code for people to look at.

Our plan is to work with the Ubuntu devs in getting the package fixed.  If the Ubuntu devs refuse or cannot fix the package, then we will place a working package in our repos.

EDIT: I have posted the code for both the i386 and AMD64 versions of Automatix for Gutsy.

Thanks for that.  I'll have a look.

  If you have fixes for major bugs (e.g. package broken) type bugs in Universe packages feel free to ping me on #ubuntu-moto IRC (ScottK).  This applies to all releases and not just Gutsy.  If you have anything on your broken package radar for Gutsy, please let us know NOW.

---

### Post by kitterma on 2007-10-08
I notice you are shipping a checkgmail .desktop and other files.  How about we work out fixing whatever you think it wrong with Gutsy's checkgmail?

---

### Post by picpak on 2007-10-08
This isn't directly related to the topic per se, but it is Automatix related:

From [http://www.getautomatix.com/forum/index.php?showtopic=1558](http://www.getautomatix.com/forum/index.php?showtopic=1558) :

> ANOTHER UPDATE: Automatix will no longer use third party repos, thus they will no longer be added to a user's sources.list. The only repos Automatix will add to a users sources.list is the Automatix repo and any Ubuntu repo that is disabled (except for proposed-updates, we wont add that.) We are enacting this new policy to try and keep sources.list editing to a minimum. An example sources.list can be found here: [http://getautomatix.com/wiki/index.php?tit..._i386_and_AMD64](http://getautomatix.com/wiki/index.php?tit..._i386_and_AMD64)

Why is Automatix still tinkering with the sources.list anyways? Wouldn't it make more sense to create a file, /etc/apt/sources.list.d/automatix.list, that stores the repo information?

Another bug I had with Automatix: when using a repo with the same package version as Automatix's, Automatix refuses to work (case in point: aMSN 0.97). Any ideas of fixing that? (It could just be done by specifying the repo in sudo apt-get install.)

Once again, I realize this isn't directly related to the topic on hand, but seeing as how I had found the original link I was referring to in this topic I posted it here anyway.

---

### Post by jtbl on 2007-10-08
> **kitterma said:**
> I notice you are shipping a checkgmail .desktop and other files.  How about we work out fixing whatever you think it wrong with Gutsy's checkgmail?

That sounds like a good idea.  Also I need to speak with the developers about adding libsigc++-2.0-0c2a to the ia32-libs package, which will allow Skype to work on AMD64, and about updating nspluginwrapper to 0.9.91.5, which is supposed to improve compatibility with the new Flash plugin currently in development. 

> **picpak said:**
> Why is Automatix still tinkering with the sources.list anyways? Wouldn't it make more sense to create a file, /etc/apt/sources.list.d/automatix.list, that stores the repo information?

That is something we will have to look into.

---

### Post by kitterma on 2007-10-09
> **jtbl said:**
> That sounds like a good idea.  Also I need to speak with the developers about adding libsigc++-2.0-0c2a to the ia32-libs package, which will allow Skype to work on AMD64, and about updating nspluginwrapper to 0.9.91.5, which is supposed to improve compatibility with the new Flash plugin currently in development. .

We are trying to do an ia32-libs upload today.  This would be a good time to show up on IRC and try to coordinate this.

---

### Post by joep on 2007-10-09
Glad to hear your going to be working together. Automatix is what made me become a Linux user and I will always be grateful it was there when I needed it.:)

---

### Post by kitterma on 2007-10-10
If we are going to include the .desktop in the repositories, we need some licensing information on the associated artwork.  Please show up in #ubuntu-motu again and give us a hand.

---

### Post by kitterma on 2007-10-11
OK.  nspluginwrapper, checkgmail with .desktop (different icon due to lack of licensing info on the Automatix icon), and including libsigc++-2.0-0c2a in ia32-libs are all uploaded. 

Not sure if the release managers will accept it all this close to RC, but it's all uploaded.  Next time, lets have this conversation earlier in the development cycle.

---

### Post by EdThaSlayer on 2007-10-11
I never though that Automatix would change. Very nice to hear this.

---

### Post by stinger30au on 2007-10-11
sounds good. if it wasnt for automatix i would never have swapped from XP Pro

---

### Post by kitterma on 2007-10-11
> **kitterma said:**
> OK.  nspluginwrapper, checkgmail with .desktop (different icon due to lack of licensing info on the Automatix icon), and including libsigc++-2.0-0c2a in ia32-libs are all uploaded. 

Not sure if the release managers will accept it all this close to RC, but it's all uploaded.  Next time, lets have this conversation earlier in the development cycle.

All in the archive now.

---

### Post by jtbl on 2007-10-16
Automatix for Gutsy has been released.

[http://www.getautomatix.com/forum/index.php?showtopic=1558](http://www.getautomatix.com/forum/index.php?showtopic=1558)

---

### Post by Ripfox on 2007-10-17
Thanks for the Gutsy release. I don't care what anyone says, even if you just use it for a few things this is an awesome tool. Good work guys!

---

### Post by Ripfox on 2007-10-17
> **Paul820 said:**
> When i first started with ubuntu i thought automatix was excellent for me, a beginner in this strange linux world. It never broke my system once, as i have gained more experience i don't need it. I think it's great they are working with the ubuntu developers, because first time users still need a little helping hand to get started. It helped me, and i'm sure it will help others.

Same exact experience here.

---

### Post by Frak on 2007-10-17
> **ripfox said:**
> Same exact experience here.
+2

---

### Post by jtbl on 2007-10-18
We will be offering upgrade assistance for Automatix users today, Thursday October 18, starting at 6 A.M. Central Time on our irc channel #Automatix on irc.freenode.net

---

### Post by Frak on 2007-10-18
Great package, awsome choices. :)

---

### Post by jtbl on 2007-10-23
A blog has been created where I will write about Automatix. This is where you will be able to find my daily reports from UDS in Boston. The blog is not to be used for filing bug reports and getting support.
[http://www.getautomatix.com/blog/](http://www.getautomatix.com/blog/)

---

### Post by Emerzen on 2007-11-30
I am also glad and relieved to hear it.  I've been using Automatix all along and have never had any breakage whatsoever.  In fact,the only breakage I've experienced is when trying to do it myself from source, etc...  Even when I can do something myself, the first thing I do after a new install is head over to Automatix and get all the bells and whistles I want in one fell swoop.  It's also helped me win over a few converts to Ubuntu over the years.

---

### Post by estaticd on 2008-03-11
Just wondering what the status of this is, has Automatix been in collaboration with the Ubuntu devs?

---

### Post by LCC on 2008-05-07
I think the Automatrix team was great when I didn't know much and when some (but important)Ubuntu programs were hard to install but with time Automatrix stared to loose its purpose (for me) but if they let to synaptic all the stuff it can do and start using Automatrix for proprietary stuff that Ubuntu legally couldn't touch it would be not just helpful but also shown that it doesn't need to "compete" with core Ubuntu features instead it would work with them. Sounds great! 
  
 I also would like to thanks the Automatrix team that always though about the new users and have been always kind and helpful here in the forums .:

---

### Post by PartisanEntity on 2008-05-08
Automatix is dead, so this thread has lost any relevance.

---

