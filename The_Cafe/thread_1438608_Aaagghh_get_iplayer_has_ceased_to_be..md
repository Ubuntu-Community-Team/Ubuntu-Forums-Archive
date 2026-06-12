---
title: "Aaagghh get_iplayer has ceased to be."
date: 2010-03-25
forum: The Cafe
---

### Post by nothingspecial on 2010-03-25
[http://linuxcentre.net/get_iplayer-dropped-in-response-to-bbcs-lack-of-support-for-open-source#comments](http://linuxcentre.net/get_iplayer-dropped-in-response-to-bbcs-lack-of-support-for-open-source#comments)

No fair. After deciding to drop 6music and now this, my tv is going on the skip and they can shove the license fee you know where.

---

### Post by Philip Farrugia on 2010-03-25
Just found out myself and rather disappointed.

Where can I get an up to date .deb? The download seems to have gone.
Installed Lucid today and found an older version in the package manager but having trouble with HD video downloads.

This has been a god send as I never find time to watch tv or listen to radio until its gone passed its sell by date on the official BBC version.

Hoping someone with the know how takes up the gauntlet and runs with it...

---

### Post by heyup on 2010-03-26
This is very disappointing. Those in the BBC (British Broadcasting Corporation) responsible for this should hold their head in shame.

get_iplayer was a great programme that did no harm to the BBC, and was convenient to users.

Now we are forced to use Adobe Flash. A retrograde step.

---

### Post by clanky on 2010-03-26
google search for iplayer downloader.

You have to install ruby and ruby gems and then do a gem install of iplayer-dl

---

### Post by clanky on 2010-03-26
[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

---

### Post by nothingspecial on 2010-03-26
> **clanky said:**
> google search for iplayer downloader.

You have to install ruby and ruby gems and then do a gem install of iplayer-dl

An alternative, and thanks for posting, but get_iplayer it is not.

I can understand the problem the bbc has.

I (amongst many other things) download the Radio one Punk show to listen to at the gym (you know your going to get a good bpm).

If I wanted to, I could use audcaity (or something else) to extract the songs I like and save them.

I don`t.

I just don`t like being penalized because I could.

If people want the content, they can get it through other means.

Personally, I delete the last one once the new one has downloaded. 

If I like a song I hear, I buy the album.

The fact that that show airs at 2am means I`m not going to hear it anymore and therefore will not be buying music from the artists it introduces me too.

Another example of the music industry shooting itself in the foot.

---

### Post by ajgreeny on 2010-03-26
I am disgusted at the BBC for forcing us into this situation, which I have only just found out about as I tried to update my version of get_iplayer from v2.66.

Thank goodness it still works, and I still, at least have that .deb install package, and I will make sure I hang on to it for as long as I can continue to use it, but it seems to me that if the BBC really does not want us to use this software to download anything, they will soon change things their end and make it impossible to use it any more in the future.

What a disgrace!!  And I thought we, the British public, owned the BBC; it is supposed to be a public service broadcaster, after all.  That we could download non DRM progs, is no different to the way a DVD recorder can record programs to keep for ever, or mplayer can dump web streams to files on your hard disk, so the BBC is not stopping any major pirating possibilities, as far as I can see, merely alienating some of their customers.

Does anyone have a copy of the most recent get_iplayer deb file to replace my 2.66 version?

---

### Post by nothingspecial on 2010-03-26
I have 2.41-1 on karmic and 2.66.1 on lucid so I can`t help.

Really annoyed about this.

---

### Post by MentalNotes on 2010-03-26
get_iplayer has been forked and is available at [http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer)

---

### Post by nothingspecial on 2010-03-26
> **MentalNotes said:**
> get_iplayer has been forked and is available at [http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer)

Thank god.

I hope this guy is as good as Phil.

---

### Post by ajgreeny on 2010-03-27
Yes, thank goodness for that!

I have just downloaded the package and then began to wonder how the heck to use it. 

I simply extracted the tarball and copied the **get_iplayer** perl script to /usr/bin to overwrite the previous version (2.66, renamed, just in case), and all works well.  There is no .deb package, unfortunately, so some may find this a bit of a challenge in comparison, but it certainly still works very well, or at least as well as the get_iplayer ever did.

PS:  At the moment, at least, the script is still exactly that of Phil, ie no changes as far as I can make out and even still has Phil's copyright on it.

---

### Post by heyup on 2010-03-27
> **ajgreeny said:**
> 
I simply extracted the tarball and copied the **get_iplayer** perl script to /usr/bin to overwrite the previous version (2.66, renamed, just in case), and all works well.

I tried this (renamed previous version as get_iplayer_1.19) but I get this error message when I tried to run:

bash: ./get_iplayer: No such file or directory

How do I get bash to find the path to get_iplayer?

---

### Post by ajgreeny on 2010-03-27
The file was already executable in my archive so would only need the command ```
get_iplayer
``` if you put then file in /usr/bin.  This assumes that you tried to run it with the command ```
./get_iplayer
```Try removing the ./ from the command you used and it should run without problem.

---

### Post by heyup on 2010-03-27
Doh.... Of course. Found path with 

```
get_iplayer
```

But then I get this:
> get_iplayer v2.76, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

WARNING: Running the updater again to obtain plugins.
INFO: Current version is 2.76
INFO: Checking for latest version from linuxcentre.net
ERROR: Failed to connect to update site - Update aborted

So it doesn't seem to work for me, or have I done something wrong?

---

### Post by ajgreeny on 2010-03-27
What happens if you try again in the same terminal?  The update is only usually after using the -u option after the command, but then tells you:-
```
INFO: Please run the following commands to update get_iplayer using apt-get
  wget http://linuxcentre.net/get_iplayer/packages/get-iplayer-current.deb
  sudo dpkg -i get-iplayer-current.deb
  sudo apt-get -f install
```
so I don't know what is going on in your case, unless your much older original version than mine lacked some dependencies for the 2.76 that you now have, which my original 2.66 already had.

---

### Post by scouser73 on 2010-03-28
Yeah, it's a shame that the BBC have forced get_iplayer out of action, I've found the latest (I think) version of get_iplayer here: [[COLOR="Red"]**Get iPlayer**[/COLOR]]("http://packages.debian.org/testing/video/get-iplayer")

---

### Post by CarlWalters on 2010-03-28
> **scouser73 said:**
> I've found the latest (I think) version of get_iplayer here: [[COLOR="Red"]**Get iPlayer**[/COLOR]]("http://packages.debian.org/testing/video/get-iplayer")

Thank you! I've been looking for this for a while after removing my version by accident

---

### Post by ajgreeny on 2010-03-28
It's not quite the most recent, but almost.

I am now running the 2.76 version, which came from [http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer), but this is not a .deb, as I said above, and needs the get_iplayer script to be manually copied into /usr/bin to replace any older version you may already have.

---

### Post by heyup on 2010-03-28
I can reinstall 1.19 using
```
sudo dpkg -i get-iplayer-current.deb
sudo apt-get -f install

```
If I try to install 2.68-1 from [http://packages.debian.org/testing/video/get-iplayer](http://packages.debian.org/testing/video/get-iplayer) using
```
sudo dpkg -i get-iplayer_2.68-1_all.deb

```
I get this error message, and install fails
> (Reading database ... 209706 files and directories currently installed.)
Unpacking get-iplayer (from get-iplayer_2.68-1_all.deb) ...
dpkg: error processing get-iplayer_2.68-1_all.deb (--install):
 trying to overwrite `/usr/bin/get_iplayer', which is also in package get_iplayer
Errors were encountered while processing:
 get-iplayer_2.68-1_all.deb

If I install 2.76 (as per post #11) I get error (as per post #14).

I'm stuck. Might have to remove 1.19 and then install 2.68-1 to overcome this problem. Any ideas?

---

### Post by Xbehave on 2010-03-28
meh, the BBC put some damn good content out and some damn good software (Schroedinger/Dirac anyone?). In order to stop us having to pay more for the license fee, they have to negotiate with content producers and have drm* on their videos, the limited content the BBC actually produces also needs to be protected so that it can be resold to recoup some of the money spent on it. 

This has nothing to do with open source software and everything to do with drm and piracy, stop hiding behind the FOSS flag when all you really want to do is pirate the videos.

*I don't think anybody sensible is flat out against drm, mearly the selling of products with drm so users aren't aware they don't actually own what they paid for. As the bbc never even hint at the content you watch on iplayer being yours to keep, drm is not really a problem.

As for your radio six comment, I'm amazed how many people listen to it, but fail to show up in the listening figures.

---

### Post by heyup on 2010-03-28
> **heyup said:**
> Might have to remove 1.19 and then install 2.68-1 to overcome this problem.

That sorted the problem. Installed 2.68. Haven't tried 2.76 yet.

2.68 works for radio. Not blocked at present. I'm downloading a Radio 4 programme at the moment.

I use get_iplayer to download radio programmes to listen to them when I want to and where I want to, not to pirate tv programmes.

---

### Post by nothingspecial on 2010-03-28
> **Xbehave said:**
> 

As for your radio six comment, I'm amazed how many people listen to it, but fail to show up in the listening figures.

If they get rid of 6 music then the bbc remit has failed.

---

### Post by Xbehave on 2010-03-28
> **nothingspecial said:**
> If they get rid of 6 music then the bbc remit has failed.
How so? 6 music is a niche channel, if this huge number of supposed listeners care so much about it why don't you fund it yourselves instead of scrounging of the rest of us? Infact if there is such a demand for a radio station to push out the same music that is available on last.fm/spotify/etc, but without interactivity and with DJs then why is there no commercial radio station jumping to fill the niche. Radio6 was good when it started but it's reached a dead end now, it's not providing anything that can't be found elsewhere but it's listners (and [everybody else who jumped on the bandwagon]("http://www.guardian.co.uk/media/2010/mar/01/ed-vaizey-bbc-6-music")) are kicking up a fuss demanding that tax pays duplicate this service at our expense, not theirs.

---

### Post by nothingspecial on 2010-03-28
> **Xbehave said:**
> How so? 6 music is a niche channel, if this huge number of supposed listeners care so much about it why don't you fund it yourselves instead of scrounging of the rest of us? Infact if there is such a demand for a radio station to push out the same music that is available on last.fm/spotify/etc, but without interactivity and with DJs then why is there no commercial radio station jumping to fill the niche. Radio6 was good when it started but it's reached a dead end now, it's not providing anything that can't be found elsewhere 

That`s cool. I`ll fund 6 music, (a few programs) on radio 4 and the Late Junction on Radio 3.

Why does everybody else scrounge off me for BBC1, 2, 3 ,4 Parliment CBeebies etc etc etc.  I don`t watch them. I`d love a BBC pay per veiw/listen.

Listen by content would surely save me a fortune. I`m all for it.

Whilst I must fund Shaz and Tracey`s addiction to life in the square, I`d rather have a radio station that plays stuff I`m not going to hear any where else, to sweeten the pill, thankyou.

That`s why.

---

### Post by ajgreeny on 2010-03-28
> **Xbehave said:**
> meh, the BBC put some damn good content out and some damn good software (Schroedinger/Dirac anyone?). In order to stop us having to pay more for the license fee, they have to negotiate with content producers and have drm* on their videos, the limited content the BBC actually produces also needs to be protected so that it can be resold to recoup some of the money spent on it. 

This has nothing to do with open source software and everything to do with drm and piracy, stop hiding behind the FOSS flag when all you really want to do is pirate the videos.

*I don't think anybody sensible is flat out against drm, mearly the selling of products with drm so users aren't aware they don't actually own what they paid for. As the bbc never even hint at the content you watch on iplayer being yours to keep, drm is not really a problem.

As for your radio six comment, I'm amazed how many people listen to it, but fail to show up in the listening figures.
I assume from this post that you believe that we get_iplayer users are all pirating BBC programs to sell on, or something similar.  Well, I can assure you that is not the case, for me, at least.

I am unlucky enough to live in an area where freeview TV is not yet available, and will not be until 2012, so the only way I can see or record programs from, for example, BBC3, BBC4, and other digital non-BBC stations, is to use my computer.  The flash iplayer on the BBC web site, is frankly, not good enough to watch streamed content for any more than a few minutes, and tends to be pretty flaky at times, with constant jerks and stops at the times that I'm likely to be around and wanting to watch.  Therefore I download and watch in good quality when I wish to; for me, it's the only practical way.

Pirating the programs?  No thanks, I can't be bothered.  But I do want to watch some programs.

---

### Post by Xbehave on 2010-03-28
> **nothingspecial said:**
> That`s cool. I`ll fund 6 music, (a few programs) on radio 4 and the Late Junction on Radio 3.

Why does everybody else scrounge off me for BBC1, 2, 3 ,4 Parliment CBeebies etc etc etc.  I don`t watch them. I`d love a BBC pay per veiw/listen.
But that's not how the BBC license fee works and the fact is the cuts have to come somewhere and 6 music is quite expensive per listener hour for a non-ethnic diversity channel.

> I`d rather have a radio station that plays stuff I`m not going to hear any where else,Nowhere else other than spotify, last.fm, your own music collection. This is another problem with 6 music, it not only isn't popular, it also isn't unique, there are a billion places to get inde music online, why should the BBC provide yet another.

In the examples you give:
BBC1/BBC2 popular
BBC3 is a testbed for comedy/action so isn't actually expensive as anything good gets moved to BBC1/2
BBC4 is a testbed for documentaries/drama and produces a lot of qulity programming not found elsewhere
Parliament/ceebebies are both niche channels

so all of them can be justified but
6 music is not popular, 
6 music doesn't fund the production of new music
6 music doesn't fill a niche

So while you might like 6 music (hell you might have even listened to it before it was cool), saying that the BBC remit has failed is ridiculous.

> Well, I can assure you that is not the case, for me, at least.
It sucks that there were legitimate users of the software who simply used it as an alternative to the real iplayer, but I doubt you constitute the majority of get_iplayer users (much like legit torrents), right from the start get_iplayer has been exploiting weaknesses in the BBCs system so I think it always drew pirates more often than legit users (especially since the move to air for the download system)

> The flash iplayer on the BBC web site, is frankly, not good enough to watch streamed content for any more than a few minutes, and tends to be pretty flaky at times, with constant jerks and stops at the times that I'm likely to be around and wanting to watch. Therefore I download and watch in good quality when I wish to; for me, it's the only practical way.
When's the last time you tried it, I used have similar problems but recently it has been much more reliable. 
p.s Have you tried the air player, it does pretty much what you want but while protecting the BBC's content.

---

### Post by nothingspecial on 2010-03-29
> **Xbehave said:**
> 
Nowhere else other than spotify, last.fm, your own music collection. This is another problem with 6 music, it not only isn't popular, it also isn't unique, there are a billion places to get inde music online, why should the BBC provide yet another.

The enormous BBC sessions archive which 6music dips into every day. You cannot hear that anywhere else.

---

### Post by tghe-retford on 2010-03-29
> **Xbehave said:**
> But that's not how the BBC license fee works and the fact is the cuts have to come somewhere and 6 music is quite expensive per listener hour for a non-ethnic diversity channel.
BBC Radio 6Music is exactly the sort of channel that a public service broadcaster (PSB) funded by the public should be providing. The point of the BBC is to provide content which the commercial sector will not provide. Under your argument, we could axe BBC Radio 3 - probably one of the most diverse and culturally benefitting channels in the world. If Radio 3 were to be axed, the BBC is dead as a PSB. The last thing the BBC should be doing is removing minority and niche programming and pandering to the commercial sector. That would make it far easier for the likes of Rupert and James Murdoch, Global Radio and other commercial broadcasters to argue for the end of the licence fee and even the BBC itself.

---

### Post by nothingspecial on 2010-03-29
> **nothingspecial said:**
> The enormous BBC sessions archive which 6music dips into every day. You cannot hear that anywhere else.

Example, copied just now from 6music`s lastfm page
```

racks
	To Rococo Rot &#8211; Away 			Just listened
	
	Echo & The Bunnymen &#8211; With A Hip 			8 minutes ago
	
	Fairfield Parlour &#8211; Free 			12 minutes ago
	
	The Wave Pictures &#8211; Kittens 			23 minutes ago
	
	[COLOR="Red"]Au Pairs &#8211; Love Song - BBC Session 28/05/1980 [/COLOR]			26 minutes ago
	
Play
	Port O'Brien &#8211; Leap Year full track 			43 minutes ago
	
	Belle and Sebastian &#8211; Photo Jenny 1999 			46 minutes ago
	
	Wah! Heat &#8211; 7 Minutes To Midnight 			3 hours ago
	
	Steve Mason &#8211; Lost and Found 			3 hours ago
	
	Vampire Weekend &#8211; Giving Up the Gun
```

Tell me where on spotify, and my music collection I`m going to hear that, and don`t say Lastfm because if 6music goes that option won`t be there.

Or on commercial radio.

Infact there`s a few tunes there you wouldn`t hear on commercial radio.

I don`t think you`ve listened to 6music properly.

And to imply I`m a music pirate?????

---

### Post by auberginepop on 2010-06-06
I went to [http://git.infradead.org/get_iplayer.git](http://git.infradead.org/get_iplayer.git) 

Select the most recent snapshot which will download a tar file.

In there is a version of get_iplayer. I just replaced the file in /usr/bin with this one and everything worked again.

From the site it looks like the code is now maintained by David Woodhouse. If this is the case then thank you David!!

---

### Post by scouser73 on 2010-06-06
Thank you for this, I have missed using get_iplayer.

---

