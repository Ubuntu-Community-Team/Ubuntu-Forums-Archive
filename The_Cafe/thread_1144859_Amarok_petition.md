---
title: "Amarok petition"
date: 2009-05-01
forum: The Cafe
---

### Post by dentaku65 on 2009-05-01
Hi all,
many of us have sadly discover that from Juanty the Amarok 1.4 player is not available as upstream to install (due to the fact that is not developed anymore by Amarok Team); in substitution we get Amarok 2 that have in common with Amarok 1.4 only the name.

How can this happen?

Fortunately a PPA repository is available to install Amarok 1.4 in Jaunty; a big, big thanks to Bogdan Butnaru that make this possible.
[https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)

Amarok and the other one cannot coexist together, so in order to use Amarok we have to remove Amarok 2. Here the steps:

Edit your APT sources:
```
sudo gedit /etc/apt/sources.list
```
Add at the end of the file the following lines and save it:
```
# amarok 1.4
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```
Add the signature for the repository:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AE74AE63
```
Install Amarok:
```
sudo apt-get update
sudo apt-get remove amarok && sudo apt-get install amarok14
```
Done!

Discussions for your convenience:
[http://brainstorm.ubuntu.com/amarok/](http://brainstorm.ubuntu.com/amarok/)
[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)
[http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok)
[http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/](http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/)
[http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569](http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569)

---

### Post by skotos on 2009-05-02
Though I have voted for Amarok 2, it is sad to admit that it lacks many features and that some are broken too (how many might be Jaunty related?). 
Currently I just hope its development/integration goes on quickly and reaches the top quality of version 1.4: incredibly and definitely the best mm player ever.

Some of the new plugins are really nice and I have started enjoying them, but - for sure - the version change makes you expect a miracle since you know the heights reached by the previous one and, instead, you have to face the tough reality that version 2 cannot be considered for production: it is sadly an alpha / pre-release version of what it will be.

Anyway, to me, amarok 2 still is far better than other players which cannot simply be compared to this bugged/broken and still under development version.

---

### Post by Eisenwinter on 2009-05-02
I suggest you switch a distro.

---

### Post by Zoowey on 2009-05-02
I use Amarok 2 but I actually voted for 1.4 simply because I find it to be more stable and 2.0.2 is simply missing some good features that 1.4 had.

---

### Post by collinp on 2009-05-02
They cant change something that major in the repos now, excluding security updates, the repos are frozen.

---

### Post by dox_drum on 2009-05-02
I loved Amarok, until version 2... the deception made me unistall it and stick to rhythmbox.

---

### Post by Zoowey on 2009-05-02
> **Hellow said:**
> They cant change something that major in the repos now, excluding security updates, the repos are frozen.

They can at least keep Amarok 2 as default but still offer 1.4 as a alternative. There are many programs that have their new and older versions in the repository, I don't see why the same can't be said about Amarok.

---

### Post by dentaku65 on 2009-05-03
> **Eisenwinter said:**
> I suggest you switch a distro.

..and why? :confused:
It is much more, let's say, realistic, changing the music player instead...

---

### Post by dentaku65 on 2009-05-03
> **skotos said:**
> Though I have voted for Amarok 2, it is sad to admit that it lacks many features and that some are broken too (how many might be Jaunty related?). 
Currently I just hope its development/integration goes on quickly and reaches the top quality of version 1.4: incredibly and definitely the best mm player ever.

Some of the new plugins are really nice and I have started enjoying them, but - for sure - the version change makes you expect a miracle since you know the heights reached by the previous one and, instead, you have to face the tough reality that version 2 cannot be considered for production: it is sadly an alpha / pre-release version of what it will be.

Anyway, to me, amarok 2 still is far better than other players which cannot simply be compared to this bugged/broken and still under development version.

To me the two amaroks have in common only the name; during the Intrepid time I've used the Neon repository (for Amarok2) in order to use both and they are not comparable, in my opinion first of all is the lack of **u s a b i l i t y**.

I know this petition is silly for the idea to have Amarok back in the upstream, but at least we can post on Amarok forum the result of their users expression; if you lurck in the Amarok forum many critics are addressed as troll opinion and this I really dislike; so that's why the idea of petition.

...and hu, no kebap after 1.00am in Milano, Italy :-)

---

### Post by reyfer on 2009-05-03
I'm not sure what the usability problems are on Ubuntu, but at least for me using Kubuntu, Amarok 2 is still great and still does everything I need it to do

---

### Post by toupeiro on 2009-05-03
I miss all the scripts that 1.4 had.  Outside of this, I could really care less.  Yes it looks different, and yes I did really like 1.4 but IMO its still better than anything else I've used.  Its nowhere near "unusable".  But, I do hope it adopts more scripts than it currently has!

---

### Post by mister_pink on 2009-05-03
I really don't see the big deal. On gnome it doesn't seem to be a massive leap forward or anything, but its certainly not worse. Dare I say it - its hardly that different at all really.

Nothing will get changed though unless you make specific comments. "Its not as good as the old one" doesn't help at all.

---

### Post by LightB on 2009-05-03
Too complicated

---

### Post by LoGinthebest on 2009-05-03
I voted for Amarok 1.4. I think it is better.

---

### Post by dentaku65 on 2009-05-03
> **mister_pink said:**
> I really don't see the big deal. On gnome it doesn't seem to be a massive leap forward or anything, but its certainly not worse. Dare I say it - its hardly that different at all really.

Nothing will get changed though unless you make specific comments. "Its not as good as the old one" doesn't help at all.

Updated 1st post:
**Discussions for your convenience:**
:-)

---

### Post by SomeGuyDude on 2009-05-03
I voted for Amarok 2 because asking the devs to constantly keep old versions of software available upstream is just ridiculous.

I've got a wacky idea: how about instead of complaining and asking for 1.4 back, express your concerns to the Amarok team and see if you can get those features back in the NEXT one.

---

### Post by Guilden_NL on 2009-05-03
2.0 just caused me to upgrade to 1.4 and I am now trying many other apps in case the Amorok team doesn't get a clue about how bad 2.0 is.  I can't think of a worse regression for a previously excellent app in the entire 13 years I have run Linux.  Two thumbs down for Amorok 2.0!

---

### Post by khelben1979 on 2009-05-03
I voted for version 1.4 since it's part of the Debian Lenny release. Works good.

---

### Post by scratman on 2009-05-03
I got 2.0 like everybody else with the 9.04 upgrade/install, and it just does not do the job.  The different UI I can live with, but I personally think that if there's music in the playlist, and I press the play button, I wanna hear noise.

Call me fussy, but a music player that doesn't play music is no use to me.  It wasn't a codec problemn because VLC and Totem could handle the files.  It also felt slower building the library initially, and hung when adding a long list of files to the playlist.

I love 1.4, and I imagine that there are no more than a few bugs in 2.0 that need to be ironed out with the next update, but currently, I do not feel that Amarok 2.0 is fit for purpose, and for that reeason we should be able to install 1.4 from the repos.  If a new user comes from, Windows to 9.04, and thinks that Amarok 2.0 is the only music player available, that Windows disc will be back in the drive by tea time, and I wouldn't blame them.

---

### Post by Guilden_NL on 2009-05-03
> **scratman said:**
> I got 2.0 like everybody else with the 9.04 upgrade/install, and it just does not do the job.  The different UI I can live with, but I personally think that if there's music in the playlist, and I press the play button, I wanna hear noise.

Call me fussy, but a music player that doesn't play music is no use to me.  It wasn't a codec problemn because VLC and Totem could handle the files.  It also felt slower building the library initially, and hung when adding a long list of files to the playlist.

I agree scratman, I had the same problems.  Also no support of devices as 1.4 expertly handled them the first time I plugged one of three that I regularly synched with Amarok.

I think that there are more than a few bugs, from the bug logs, it looks like Amarok has been a complete mess for well over a year in development.  The sad thing is that it's quite well known, so I am scratching my head at the Ubuntu team that added it to the Jaunty distro.  I remember full releases of Firefox and Open Office missing the release candidate and they were well into a very polished release before Ubuntu was.

Someone on the Ubuntu team should reconsider and pull Amarok 2.0 out of the repo and allow everyone to revert back to it, and all those not yet upgraded to Jaunty to have 1.4.

I am going to do some work in the yard and don't have time to mess about with this now.  Will drop back to XP to use Winamp to synch the music I want to listen to **_now_**.

---

### Post by meho_r on 2009-05-03
> **dentaku65 said:**
> To me the two amaroks have in common only the name; during the Intrepid time I've used the Neon repository (for Amarok2) in order to use both and they are not comparable, in my opinion first of all is the lack of **u s a b i l i t y**.


I agree on that. Please, take a look at [amarok usability report]("http://weblog.obso1337.org/2009/amarok-playlist-usability-testing/")

I liked amarok 1.4 much. In fact, after v.2 I switched the player and using Exaile now. Too bad, amarok was the best player ever and was so promising, but in the shape it is now, it's only one of many :(

---

### Post by Roasted on 2009-05-03
Amarok2 looks nice, but the fact they stripped features makes it downright useless. I ditched it in a heartbeat and got a hold of Exaile which I find to be far superior to Amarok2 due to the customizability.

Amarok2 just painted a big black spot over their name. Amarok1 will always be the top dog between the two.

---

### Post by KAMiKAZOW on 2009-05-03
This poll is stupid, because it only talks about "Amarok 2", not "Amarok 2.0" or "Amarok 2.1". Despite being still beta, Amarok 2.1 is a huge improvement over 2.0. Canonical should've included that one, not 2.0.

---

### Post by meho_r on 2009-05-04
> **KAMiKAZOW said:**
> This poll is stupid, because it only talks about "Amarok 2", not "Amarok 2.0" or "Amarok 2.1". Despite being still beta, Amarok 2.1 is a huge improvement over 2.0. Canonical should've included that one, not 2.0.

I would like to share that opinion of yours. Unfortunately, all I noticed is that some plugins don't work anymore (lyricswiki being one of them). But 2.1 is still beta...

---

### Post by canadiandude007 on 2009-05-04
Does this version fix the Wikipedia display bug?

---

### Post by dentaku65 on 2009-05-04
> **canadiandude007 said:**
> Does this version fix the Wikipedia display bug?

Was fixed while ago
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140)
(seek the post of Max libamarok.so.0.0.0)
but at the moment seems that wikipedia change again the headers... someone else can confirm this?

---

### Post by george1984 on 2009-05-04
Hello

I use Amarok1.4 as a library catalog and management system. I can not use Amarok2 effectively for this purpose. This situation is unlikely to change with time as Amarok2 is effectively a new App. with a different philosophy.

Blogdan's ppa enables me to continue running Amarok14, for which I an hugely grateful.

There has been considerable discussion on this subject here ...



[http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

---

### Post by skotos on 2009-05-04
> **dentaku65 said:**
> ...and hu, no kebap after 1.00am in Milano, Italy :-)But a coffee is always hot and ready to go! (American and/or expresso as well!) LOL

---

### Post by hockeyhead019 on 2009-05-04
voted for v2 but i do agree with the previous posts about usability and other reasons... but i think people need to use v2 and help the devs work out the bugs in order to get it back up to the usability... just my opinion

---

### Post by monsterstack on 2009-05-04
> **george1984 said:**
> Hello

I use Amarok1.4 as a library catalog and management system. I can not use Amarok2 effectively for this purpose. This situation is unlikely to change with time as Amarok2 is effectively a new App. with a different philosophy.

Blogdan's ppa enables me to continue running Amarok14, for which I an hugely grateful.

There has been considerable discussion on this subject here ...



[http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

I know exactly what you mean.

Say you have a bunch of songs by a band like *At the Drive-in*. I had a bunch of mp3s with as many different spelling variations as you can think of. I loaded them into the playlist, selected the lot of them, and then right-clicked on the one file that was properly tagged and selected the option to apply that name to all of the songs in the playlist.

And bam. A laborious task in other players, and I did it in just a few clicks. Functionality that bests most specialised music organisation applications in one fell swoop.

It's these kind of usability bits of awesomeness that made me fall in love with Amarok 1.4. The 2.x series so far has left me disappointed.

---

### Post by der_joachim on 2009-05-05
> **dentaku65 said:**
> ..and why? :confused:
It is much more, let's say, realistic, changing the music player instead...

Hear hear! I know plenty of reasons to switch distros, but a mere media player is not one.

---

### Post by davidsmind on 2009-05-05
I just upgraded to Jaunty this morning.

After 2 or 3 hours of trying to load my 50,000+ file collection into Amarok 2.X and failing (by directly loading the material, by loading a list of directories, by trying to import my old amarok settings using the supplied tool)

I finally got my files in the collection pane. Ok, so I've got a collection, now I add some files to the playlist section, awesome.

After listening to the album, I select and right click the songs, I want to add them to my collection...turns out one cannot do this any more. Insane.

Amarok 2.X is, as others have said, a different beast than 1.4.

I'm very happy about amarok14 and look forward to seeing if someone forks amarok 1.4 and compiles it against QT4.

---

### Post by dentaku65 on 2009-05-05
> **der_joachim said:**
> Hear hear! I know plenty of reasons to switch distros, but a mere media player is not one.

Is what I'm saying 

:-)

---

### Post by Bloemetjesgordijn on 2009-05-08
Hi guys

Maybe you can help me

I am using Amarok 1.4 in Januty and now suddenly I have no sound in Amarok 1.4..???

Amarok 1.4 says Xine is busy


Doe you have the same experience???


Cheerz

Bloemetjesgordijn

---

### Post by MikeTheC on 2009-05-08
Well, I can't speak for anyone else, but I'm all for...

[list=1][*] Amarok re-thinking it's user interface
[*] Amarok being more easily configurable for searching
[*] Amarok having better and more extensive iPod support[/list]

---

### Post by lil_rich on 2009-05-08
Just curious, is it possible to have both Amarok versions installed? It would be nice to play with Amarok2, but use Amarok14 if I just want to play something?

---

### Post by Roasted on 2009-05-08
I like how Amarok2 stripped away so many configurable settings. With Amarok1 I was able to listen to YouTube while Amarok was open. I had to switch an audio engine setting to make that happen. In Amarok2, I cannot find it whatsoever.

So now, I use Exaile.

Win.

---

### Post by dentaku65 on 2009-05-08
> **lil_rich said:**
> Just curious, is it possible to have both Amarok versions installed? It would be nice to play with Amarok2, but use Amarok14 if I just want to play something?

I supposed yes through Neon PPA repo
[https://launchpad.net/~project-neon/+archive/ppa](https://launchpad.net/~project-neon/+archive/ppa)
But I don't know what happens if you are running on KDE env; I think it's ok with Gnome.

---

### Post by loneowais on 2009-05-16
I've switched to SONGBIRD.
You should do the same.. It's just awesome

---

### Post by Trail on 2009-05-16
Anyone else seeing the similarities by people not initially liking KDE4.0  and people not initially liking amarok2.0? Inertia.

You don't like it because you're not feeling comfortable after seeing it change so much. That's understandable. But don't say it sucks because you can't right click to add files to your playlist or you don't like big buttons and meaningless crap like that. Amarok2 does have issues, amarok1 also has issues and they always will.

You could whine about it, you can resist upgrading, or you can actually spend 20 minutes with it and see it's not really all that different from 1.4.

Hint hint, the latest 2.1 beta is out.

---

### Post by Paqman on 2009-05-16
If you don't like Amarok2 just switch a different player. The Amarok devs will get the message through the PopCon data.

As for the claim of inertia, that's probably part of it. Speaking for myself though, I admit I disliked Amarok2 from the get-go, but i've been using Amarok for years and wanted to give it a chance. It was only inertia that made it take a couple of months to drop Amarok in favour of Banshee. I'm actually pretty glad I did, btw. Banshee is great.

---

### Post by dentaku65 on 2009-05-16
> **Trail said:**
> Anyone else seeing the similarities by people not initially liking KDE4.0  and people not initially liking amarok2.0? Inertia.

...

I totally agree... in fact I've switched from KDE to Gnome ):P
...but this is another story.

---

### Post by TuxOtaku on 2009-05-16
The biggest thing for me with Amarok 2, is the lack of support for ANY sort of portable media device...honestly...WTF guys?? what happened there? decide to release it before it was FINISHED, just like you did with the rest of KDE 4?

Honestly, someone needs to do one of two things here, fork Amarok 1.4 into a GTK-based project, or get Exaile's mobile device support up to snuff with Amarok 1.4.

At this point I have to say to the KDE devs, I'm very disappointed in you...KDE 3.5 was awesome, and then you had to muck with it and make it into the unusable, clunky, worthless pile of wank and fail that I have ever seen. Big thumbs down again guys...you've dropped the ball so many times, you should just get off the damn court.

And as a result, I'm forced to use sub-par programs to sync my iPod...like rhythmbox and gtkpod...neither of which even tell you how much space is left on the device...fail again.

A HUUUUGE thank you though, to Mr. Bogdan Butnaru for setting up a PPA for Amarok 1.4. You sir, are a prince and a scholar, and I think we are all grateful for your efforts....you're ever in Toronto, look me up, I owe you a beer. ;)

---

### Post by Cyb3rD0n Architectus on 2009-05-25
Thanks dentaku65,

I've tried Amarok 2 for a week now and it sucks bigtime. My entire collection of 15000+ tracks lost all their statistics and ratings because the import function kept crashing Amarok. Although using Gnome, the previous version only crashed once. Now I followed your instructions and went back to Amarok 1.4, with all stats and functions well functioning again (luckily I backup my @home/.kde/share/apps/amarok folder every two days!). Re-installed, copied the backup over it and I only lost two days of listening. Guess what I voted on this one...

Message to the new developers of Amarok: don't mess with my precious rating-stars! ;)

---

### Post by Noah_Kapiolani on 2009-05-25
For me, as a newbie


Amarok 1.4 was an incredible player.  Just Amarok and VLC and you could play about anythng in style.  Now, at least to me, Amarok 2.0 is totally different and basicly not so smooth.  After futzing with it for a short period of time and I'm back to 'ol Rythmbox for the music goodness.  

At this point, I am beginning to realize something.  Several programmers have found it necessary to tell me that Linux is not so hot because we have basicly no standardization.  I replied that freedom of choice is a good thing, and if you want cookie-cutter then MS or Apple is the way to go.  Now, having one of my main programs take a nose dive after going with 9.04 I am wondering if they have a point.

Amarok 1.4 should be a point and click install from the standard repositories

That and have 1.4 work seemlessly with the iPod and iPhone and iTouch and then, ladies and gentlemenm, we would really have a gaint killer

---

### Post by Aerotha on 2009-05-26
> **dentaku65 said:**
> Hi all,
many of us have sadly discover that from Juanty the Amarok 1.4 player is not available as upstream to install (due to the fact that is not developed anymore by Amarok Team); in substitution we get Amarok 2 that have in common with Amarok 1.4 only the name.

How can this happen?

Fortunately a PPA repository is available to install Amarok 1.4 in Jaunty; a big, big thanks to Bogdan Butnaru that make this possible.
[https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)

Amarok and the other one cannot coexist together, so in order to use Amarok we have to remove Amarok 2. Here the steps:

Edit your APT sources:
```
sudo gedit /etc/apt/sources.list
```
Add at the end of the file the following lines and save it:
```
# amarok 1.4
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```
Add the signature for the repository:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AE74AE63
```
Install Amarok:
```
sudo apt-get update
sudo apt-get remove amarok && sudo apt-get install amarok14
```
Done!

Discussions for your convenience:
[http://brainstorm.ubuntu.com/amarok/](http://brainstorm.ubuntu.com/amarok/)
[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)
[http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok)
[http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/](http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/)
[http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569](http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569)

I love you.

---

### Post by arsenic23 on 2009-05-26
I'll still be using hardy for a while on my main PCs, but this thread got me to install jaunty in a virtual computer just to see what was going on.

wow
Someone needs to tell the Amarok2 team, "[COLOR="DarkRed"]If it ain't broke, don't fix it.[/COLOR]"  Amarok seems to have went from, 'The linux music app, so good you'll use it in Gnome.' to 'Another wonky opensource music player.'

Now I don't follow KDE deveolopement (I didn't really like old KDE and new KDE seems way to out there to be usable for me.) but is the switchup with Amarok purely to make it inline with the new KDE setup?

Anyway, assuming they iron out some of the usability bugs in this new version, I seriously hope someone puts in an option to switch over to a more streamlined interface, because the only thing I want to see on a music player is lists of songs.

---

### Post by octavianus on 2009-06-10
> **dentaku65 said:**
> Hi all,
many of us have sadly discover that from Juanty the Amarok 1.4 player is not available as upstream to install (due to the fact that is not developed anymore by Amarok Team); in substitution we get Amarok 2 that have in common with Amarok 1.4 only the name.

How can this happen?

Fortunately a PPA repository is available to install Amarok 1.4 in Jaunty; a big, big thanks to Bogdan Butnaru that make this possible.
[https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)

Amarok and the other one cannot coexist together, so in order to use Amarok we have to remove Amarok 2. Here the steps:

Edit your APT sources:
```
sudo gedit /etc/apt/sources.list
```
Add at the end of the file the following lines and save it:
```
# amarok 1.4
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```
Add the signature for the repository:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AE74AE63
```
Install Amarok:
```
sudo apt-get update
sudo apt-get remove amarok && sudo apt-get install amarok14
```
Done!

Discussions for your convenience:
[http://brainstorm.ubuntu.com/amarok/](http://brainstorm.ubuntu.com/amarok/)
[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)
[http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1051538&highlight=amarok)
[http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/](http://www.reddit.com/r/linux/comments/84zux/who_else_feels_amarok2_is_a_huge_dissapointment/)
[http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569](http://www.lastfm.it/group/Amarok+Users/forum/18538/_/515569)



Please save me :(. I have followed the above mentioned instructions but I could not find that PPA in my synaptic. 

I have also used command line and got the following :
~$ sudo apt-get install amarok14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok14

Amarok 1.4 is the only complete music management solution in this planet that money can not buy you. There is no commercial alternative either. If one has used Amarok 1.4 for at least a year and he has at least 10GB or above of music collections , will understand my point. I don't want revert to older distro.


Can't anyone please create .deb for amarok 1.4 ? I am without music the whole day .

---

### Post by surfed on 2009-06-12
> **octavianus said:**
> Please save me :(. I have followed the above mentioned instructions but I could not find that PPA in my synaptic. 

I have also used command line and got the following :
~$ sudo apt-get install amarok14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok14

Amarok 1.4 is the only complete music management solution in this planet that money can not buy you. There is no commercial alternative either. If one has used Amarok 1.4 for at least a year and he has at least 10GB or above of music collections , will understand my point. I don't want revert to older distro.


Can't anyone please create .deb for amarok 1.4 ? I am without music the whole day .


Try again, there where issues with an update and amarok deb was offline for a bit. Once working backup amarok debs so you are no longer dependent on 3rd party repos.

---

### Post by DeadSuperHero on 2009-06-12
The latest release of Amarok has all the features old Amarok 1.4 had...

---

### Post by surfed on 2009-06-12
> **Mr. Psychopath said:**
> The latest release of Amarok has all the features old Amarok 1.4 had...

What about crossfade?

---

### Post by koleoptero on 2009-06-12
They removed the graphical equalizer. It was the only media player that had a working equalizer (besides xmms and its derivatives). Why oh why did they do that? And what's with linux and equalizers? Oh I could rant all day long... :-#

---

### Post by vgrisham on 2009-06-13
> **Mr. Psychopath said:**
> The latest release of Amarok has all the features old Amarok 1.4 had...

Mass storage device support (sync)?
Sophisticated podcast management?

---

### Post by MasterNetra on 2009-06-13
lol I use Movie Player, ftw, to play my music XD

---

### Post by octavianus on 2009-06-16
> **Mr. Psychopath said:**
> The latest release of Amarok has all the features old Amarok 1.4 had...

MySql/PostgreSQL support is not there which is essential specially for large music collections ( 50GB+ ) . Themes cant be changed like 1.4 . NO Cross fade . Xine-engine works better with Pulse audio than the current Phonon. 1.4 can organise files with little effort which cant be done in Amarok 2.

---

### Post by surfed on 2009-06-16
If I would have the know how, i would fork amarok 1.4 to qt4 in order to have a quality maintained Audio Media Jukebox.

---

### Post by dentaku65 on 2009-06-17
hu... I've seen that Bogdan released the packages of Amarok 1.4 for Karmic... now I can upgrade the distro :-)

---

### Post by gloscherrybomb on 2009-06-17
The biggest issue for me is screen real estate - 2 seems so bloated, only being able to display a small number of songs and every seems to take a click or 2 more than it should.

I messed around with loads of music players before going back to 1.4,and realising once again just how brilliant it is. context menu is brilliant, the playlist is superb (random song loaded whilst allowing easy editing on the fly, e.g. add a song to the playlist, song priorities, refill the playlist if you dont like whats coming up, etc.) and crossfade is so useful.

1.4 is still the best music player linux - they should have stuck with the developing the currently excellent set up instead of trying to reinvent a very good wheel.

---

### Post by octavianus on 2009-06-20
> **gloscherrybomb said:**
> The biggest issue for me is screen real 

1.4 is still the best music player linux - they should have stuck with the developing the currently excellent set up instead of trying to reinvent a very good wheel.


Amarok 1.4 with it's Mysql+xine+pulseaudio support is not only the best music player on Linux platform which has exceeded the perfection limit. It is in fact the best music player in any platform ie Windows and Mac in the history. It is amazing that this very best player is a FOSS project.

Now , I am willing to support any project  that revives Amarok 1.4 from the current orphan state.

---

### Post by cptrohn on 2009-06-21
> **dox_drum said:**
> I loved Amarok, until version 2... the deception made me unistall it and stick to rhythmbox.

I used to like Amarok as well, but I am having trouble with it playing some flac files I have (that were converted from WMA from my windows days)  Rhytmbox plays them perfectly... songbird has no trouble at all playing them either.... I'm sticking with rhythmbox for the time being as it seems to sort the files better, the album art works better, it plays all of my files and seems more solid to me....

I have been toying with songbird and after they add video playback to songbird that might end up being my opensource media player of choice... even though I am experimenting with things like Elisa, mythtv and some other media center types of things from the repo's right now...

As a fairly new linux user, I was really disapointed in Amarok2 after everything I had heard about it.... especially when it seems to have trouble with flac.

---

### Post by Bluztrvler on 2009-07-20
I had to go back to 1.4.  Couldn't get 2.0 to play, and I found the collection list in the left pane to be buggy.

---

### Post by Dimitriid on 2009-07-20
I propose you guys fork it into "Oldmarok" and maintain the old version.

---

### Post by hangfire on 2009-07-24
> **reyfer said:**
> I'm not sure what the usability problems are on Ubuntu, but at least for me using Kubuntu, Amarok 2 is still great and still does everything I need it to do

Usability on my Kubuntu 9.04 is also fine, probably because there are so few features compared to 1.4 that it can't help but be easy to use.

I voted for 1.4. For one thing, I just ripped some of my CD collection, and it cannot sort by Album (it pretends to, but doesn't), in Collection. Since this is my *modus operandi*, I'm rather peeved.

I've never seen a major version upgrade lose so many features. Perhaps the new code base is much easier for the maintainers to program to now, but it offers little to attract a 1.4 user.

-HF

---

### Post by surfed on 2009-07-24
The thing is that Amarok 2 is a complete different application and not an upgrade to 1.4
They should have changed the name or kept 1.4 maintained as it was the best out there and now requires effort to install, soon it will fail to compile as dependencies change.
I am still for starting a fork of amarok 1.4, maybe even with qt4.
just my 2 cents

---

### Post by Mike Brennan on 2009-08-30
I've switched to Exaile -- or at least am giving it a test drive. It's in the Ubuntu repositories and has an interface that will be familiar to any Amarok user. It's not as feature-complete as Amarok 1.4, but then neither is Amarok 2.1.

---

### Post by Exodist on 2009-08-30
1.4 was great.. 2.0 is a disappointment. 2.0 lacks many features that made me love 1.x before.  To me 2.0 is just a KDE Rythmbox. 1.4 was the best music player ever!

---

### Post by maestrobwh1 on 2009-08-30
I voted for 1.4 and the results are telling:

Amarok 1.4 70%

My main reason is that the UI is better for me, and the interaction with my iPod: my playlists can be modified, but perhaps I just have not figure out how to do this in 2.1

I don't dislike Amarok 2, but I just like 1.4 better. It seems more intuituve. 

The 1.4 repo works with Karmic, btw.

AlbumArt will need to be fetched with the script rather than the built in fetcher: Amazon changed its policies.

---

### Post by Cardcaptor Stacey on 2009-08-30
I can't use Amarok 2, it's just too buggy. I just want to listen to some music without the crashes. :(

---

### Post by Crunchy the Headcrab on 2009-08-30
I just like the UI of Amarok 2.1.  I'd prefer to use exaile even under kde.

---

### Post by SuperSonic4 on 2009-08-30
Give amarok 2 a chance, amarok 1.4 didn't appear out of the mist and be perfect

---

### Post by RiceMonster on 2009-08-30
Amarok 2 is good. I don't have any problems with it at all.

---

