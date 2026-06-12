---
title: "Ubuntu makes for a hopeless media centre"
date: 2010-10-12
forum: Testimonials &amp; Experiences
---

### Post by thecapsaicinkid on 2010-10-12
Now rest assured I am a massive Ubuntu fan, I've used it since its inception so it pains me to say this but Ubuntu really is a poor choice to base a media PC on.

I've had an Ubuntu based media pc for quite a few years now with experience of all the big platforms MythTV, XBMC, Boxee etc and I can honestly say it is a *constant* source of frustration. I'd say nearly every movie I have sat down to watch has had the enjoyment spoilt by something not working as intended.

I'll use an example of something I wanted to do on my Ubuntu media pc recently, I wanted to watch a DVD I own (obviously). First thing, my media centre has no dvd drive so I attempt to rip the disc to the file system and transfer it over the network. There are zero open source pieces of software that can do this or should I say do this reliabley for *all* modern dvd releases (especially those with arrcos protection etc.)

The best I have found is using mplayer to dump the output using the dvdnav libraries. Assuming the disc can be read in the first place. dvdread seems to struggle much more so with not-so-perfect discs than the equivalent Windows software.

This brings me on to my next point, dvdnav. Menu support in linux isn't even close to the cheapest, most basic dvd player on the market. More often than not menus don't render properly, highlight fields are missing on language select screens and just generally very flaky to navigate.

Ok so I finally get a working file copied on to my media pc (at a blistering 1MB/s over wifi) I have an external reciever connected via spdif, pulseaudio does not support digital passthrough. This is an absolute show-stopper in its own right for a media machine. Audio has always been a 'challenge' in Ubuntu ever since I first tried it, digital audio especially. Fortunately there are workarounds for this particular issue, it seems if you set pulse's output profile to 'Analog Stereo Output' and then instruct your mediaplayer to route directly to alsa hardware, passthrough works. Obviously you need to keep changing this around every time you want to watch a movie/listen to music and this isn't exactly obvious to the end user.

Up until recently I needed to select 'Analog' in the audio applet to get any sound out of the **digital** out. No idea why.

Ok, movie playing with digital audio. Next problem, no subtitles. Ok, I close gnome-mplayer and start up VLC. Subtitles work. Unfortunately, they work always. There is no support for forced subtitles i.e only shown when someone speaks in a language other than English. Great, I have to keep switching subs off and on throughout the film. Eventually this got tiring and I left them on. Tried the same file on another machine in gnome-mplayer and subs work (if I don't select a default  language 'EN' in the options, I can also add a custom -forcedsubtitles flag to mplayer but most people wouldn't do this. All regular dvd players by default play forced subs afaik)

Film playing, 10 minutes from the end the player quits. As you can imagine by this point I am a little agitated. It seems my file doesn't contain the last 10 minutes, even though mplayer can play the disc itself fully to the end, it can't dump the entire content to disc without screwing it up.

This is only a small list of issues encountered over the years of using a linux box to play my media, juddery video, audio sync issues, endless remote problems and various other niggles are a constant source of annoyance. 

Yes I try and submit bug reports where I can but I've stuck with a linux media pc for several years now (much more than most would!) and it just doesn't seem to improve. The cheapest, most basic dvd player you could buy would outperform an Ubuntu system, I have no doubt. These features really need to work if Ubuntu is going to get taken seriously as a modern OS, most people wouldn't spend a fraction of the time troubleshooting issues like these and would just revert back to Windows. I just feel like they don't really have much priority when they should and I'd love to see it change, but as of now I would never recommend an Ubuntu based media pc.

---

### Post by cchhrriiss121212 on 2010-10-12
I've seen a few posts on here about DVD protection trouble on newer releases. What DVDs from which companies are the difficult ones? Copy protection issues are of course active on all Linux OSs, not just Ubuntu.
I find that older DVDs circa 2001 are the worst for playback with horrific amounts of tearing going on. I use handbrake to rip those, which works fine for me. 

And I don't think I've ever seen a cheap DVD player that can stream content over a network ;)

---

### Post by Stigmata13 on 2010-10-12
Google a program called Handbrake. It's not in the official repository but you should be able to install it by adding a private repository. Assuming you have libdvdcss installed from the Medibuntu repository, it should be able to rip/encode straight from the DVD to your hard drive.
It worked with my copy of Avatar and I'm assuming that had copy protection.

---

### Post by dmizer on 2010-10-12
Since this is not a request for help, I've moved this to the Testimonials section.

Thank you.

---

### Post by laceration on 2010-10-12
I agree, but I am glad of that fact that "Ubuntu makes for a hopeless media centre", because I think the concept of the media center itself is the hopeless part.

Consider:
Organizing a computer as a "media center" is Microsoft invented consumerist model and Linux attempts to mimic this an is odd fit.  I have messed around with Myth, xmbc and the worth of these projects escapes me, even if they did work well. 

For me the organizing model of the computer is the operating system!  Playing media is just another thing it does.  I have a hidef 42" monitor with remote control and get free hdtv with a dvb card and get other media via the web and bittorrent.  I too have audio via spdif to a nice sound system, but do not have issues w/ it, like you do.

For people who want to buy into(literally and figuratively) the conglomerate produced media product, Microsoft media center, other window programs or probably some kind of pricey Apple product is the way to go.  Then you can be assured of locking down the content every step of the way and support proprietary models!  Why people are into this mind-numbing pablum is another thing that escapes me.

To achieve what I did, I had to write my own software, so I agree with you there is not a good solution in Ubuntu, but my suggestion is to try to find your solution outside of the media center model.

My program, OSTV, needs updating, I hope I get some time to do it soon.

---

### Post by ubunterooster on 2010-10-12
Ubuntu is not meant for being a media player; for that try MythBuntu: [http://distrowatch.com/?newsid=06311](http://distrowatch.com/?newsid=06311)

---

### Post by thecapsaicinkid on 2010-10-12
> **laceration said:**
> I agree, but I am glad of that fact that "Ubuntu makes for a hopeless media centre", because I think the concept of the media center itself is the hopeless part.

Consider:
Organizing a computer as a "media center" is Microsoft invented consumerist model and Linux attempts to mimic this an is odd fit.  I have messed around with Myth, xmbc and the worth of these projects escapes me, even if they did work well. 

For me the organizing model of the computer is the operating system!  Playing media is just another thing it does.  I have a hidef 42" monitor with remote control and get free hdtv with a dvb card and get other media via the web and bittorrent.  I too have audio via spdif to a nice sound system, but do not have issues w/ it, like you do.

For people who want to buy into(literally and figuratively) the conglomerate produced media product, Microsoft media center, other window programs or probably some kind of pricey Apple product is the way to go.  Then you can be assured of locking down the content every step of the way and support proprietary models!  Why people are into this mind-numbing pablum is another thing that escapes me.

To achieve what I did, I had to write my own software, so I agree with you there is not a good solution in Ubuntu, but my suggestion is to try to find your solution outside of the media center model.

My program, OSTV, needs updating, I hope I get some time to do it soon.
It's interesting you say this because I have just done away with the Boxees/XBMCs etc. as I too found little use for them. In my experience all they do is wrap everything in a remote control friendly interface. Web content is better in a browser with a mouse, music is better in a music player etc. etc.

Currently on the big screen I have 3 workspaces, first with a fullscreen browser and 'permatabs' for each site I regularly visit (kinda like channels) There is a MythTV backend running and currently I view recordings via the web interface in the browser along with all the other pages. 2nd workspace has Spotify fullscreen and the third just has an instance  of gnome-mplayer for dvd/file playback. Pushing the mouse to the edge of the screen slides between each workspace ('brightside') and double tapping against the right edge brings the mouse back to my laptop situated near my seat. I use 'readitlater' Firefox extension to add videos I find on the laptop/at work to a queue which I can view on the big screen later. I can for example listen to music with spotify and watch a fullscreen HD video muted from YouTube or an internet stream etc.

You can then see my issues are with the fundamentals, the libdvdread/dvdnav/mplayer/pulseaudio/flash (do't get me started on Flash) and not a particular 'frontend' piece of software like Boxee. 

I still need to rely on DVD playback as my main source of film content (I'd be happy to do away with physical discs but we're not quite there yet) and in Ubuntu, dvd playback is quite frankly, rubbish. On a positive, I seem to get less programs blocking the sound completely now, that was a nightmare on a media pc running more than one program that wanted to play sound.

I'm definitely getting closer to my ideal media machine but it seems a never ending battle. I'd be curious to hear how you've configured Ubuntu to play both regular audio and passthrough via a digital connection btw (this used to be possible before recent updates)

---

### Post by cariboo on 2010-10-12
I on the other just love XBMC, I have a custom built system dedicated to it, all the system is for is playing media. If you need the system for other things, them maybe a media center is not for you.

I've ripped my dvd collection using vobcopy, so now it's just a matter of looking at a menu, instead of digging through several shelves of dvds. I have a large collection of recorded tv shows, using XBMC they are all in one place. If I feel like watching all the episodes of a certain show, it's just a matter of turning the system on and selecting what I want to watch.

The same with listening to music. I generally prefer to listen to music randomly, so I just click on a directory full of music and let it play.

The system is connected to a 32" Samsung LCD TV via VGA and a Technics receiver with 5.1 surround sound connected to custom built speakers.

---

### Post by ventrical on 2010-10-12
I also   share that the DVD part of Ubuntu is a total non- starter. I even tried the VLC app and it will read everything except play the video. My videos are not pirated at all. All of Ubuntus media/movie players that I have installed keep asking for codecs .. etc... and I do a google search and download the  pkgs - whatever .. and the DVDs will just not play.  I'm not asking for help . Just pointing out the  probs that did also the OP.

  I had a guest over on the long Canadian  Thanksgiving weekend and was hoping to play a DVD using a dual monitor on a Sony Vaio and it was a complete failure. Luckily I had an old Dell with XP (VLC) but could't get it to recognize the other monitor... 

 Anyways .. I pulled it off with XP home .. but it was still very frustrating and aggravating - and - also perhaps I more than likely should have done some more investigation on my own.  I'm not saying Ubuntu's media capabilites were flimsy and buggy, just very difficult to navigate through , considering the expectations due to the rave reviews that apparently are out there in the ether. ie; "Perfect 10" I think not.

  I still think Linux distros are better structured and will keep immersing myself with the OS.

 Thanks.

---

### Post by cariboo on 2010-10-12
I've never had a problem playing DVDs on my computer running Ubuntu, do you guys that are having problems have libdvdcss2 installed?

You can install it enabling the medibuntu repositories, or running the script in /usr/share/doc/libdvdread4.

Ubuntu is just like any other operating system, you have to install extra software in order to play DVDs.

---

### Post by laceration on 2010-10-12
> Web content is better in a browser with a mouse, music is better in a music player etc. etc.
Exactly.  In every case these media center type apps try to do too many things and do them poorly.  I remember when I was checking out Myth and saw that they had a RSS reader plugin.  It was then obvious that they had jumped the shark.  

I use the spdif for all my sound, except for a skype phone device.  I have to reconfigure at each boot to get the skype thing setup.  The jumbled ubuntu sound stack is not good at complications.  Why don't you just do all sound through the spdif?

---

### Post by ubunterooster on 2010-10-12
> **laceration said:**
> Exactly.  In every case these media center type apps try to do too many things and do them poorly.  I remember when I was checking out Myth and saw that they had a RSS reader plugin.  It was then obvious that they had jumped the shark.  

I use the spdif for all my sound, except for a skype phone device.  I have to reconfigure at each boot to get the skype thing setup.  The jumbled ubuntu sound stack is not good at complications.  Why don't you just do all sound through the spdif?
Agreed. That's what I like about Fluendo. What does it do? Play movies.

What else does it do? Nothing! I like it!

---

### Post by johntaylor1887 on 2010-10-13
I love Ubuntu as a media center OS. I play and rip DVD's, music CD's, watch and record TV, all without any issues. It's as good as windows was for me without any of the extra baggage. Well done Ubuntu team!

---

### Post by 23dornot23d on 2010-10-13
I have never really tried to put a DVD onto here ......

But will try now ....... what are the first steps .... Other than getting one of my DVD's and
sticking it in the drive .....

What program is the best to use I want it all as one file though not in two separate directories ..... as the DVDs often have .....

_____________________________________________________

1 ......... ok first thing DVD is in and mounted ..... now what .....  ?

[COLOR=Red]ok bizarre .... VLC and Movie Player ..... on two separate DVD players cannot read from Device ............[/COLOR]

ok another DVD to try !!!!

Ok exactly the same again ..... obviously ... me never using the computer for movies ..... nothing seems set up ..........

[B]Lets see what errors and problems pop up ...... and then try to resolve them .....

A file there Video_TS ...... 25 items .... so it reads the disc ok .....

2 separate DVD drives .... will not play ..... either disc ..... Hellboy and Collateral Damage ..... maybe my choice of movies 
that it does not like .........

[/B]I remember a long time ago having problems with region information and things like that .... but this is something different .........
will try it on another OS ..... Linux Mint is pretty good with most things ........

Was using the latest version of Maverick by the way .... for this test ..... no alterations yet ..... a clean install ...... and it plays other things
ok I download the TED videos off the net and they work great ......

keith2@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
keith2@keith-laptop:~$

---

### Post by Perfect Storm on 2010-10-13
Never had trouble playing DVDs on Ubuntu (I got a ~500 DVD collection :popcorn:).

As for mediacenter I use XBMC, for normal multimediaplayer I use Gnome mplayer.

Things I make sure is installed:
libdvdcss2 (medibuntu)
ubuntu-restricted-extras
non-free-codecs (medibuntu)

---

### Post by mastablasta on 2010-10-13
> **laceration said:**
>  
For me the organizing model of the computer is the operating system! 
 
what is for you the organising model of phone? since they stick so many things on it these days.... :)
 
 
btw i too have a mess with movies on hard disk.... so many of them, no picture and way to find them but to search the movei by title through total commander (in XP).

---

### Post by thecapsaicinkid on 2010-10-13
> **laceration said:**
> The jumbled ubuntu sound stack is not good at complications.  Why don't you just do all sound through the spdif?
All sound does go through spdif, there are no analog speakers attached to the machine. The problem is pulseaudio doesn't support passthrough (Alsa does) and while it is configured to use spdif (i.e for all regular audio, music etc.) Alsa cannot access it. Hence why I need to switch the sound profile to Analog (which stops pulse blocking it). 

[http://www.pulseaudio.org/ticket/167](http://www.pulseaudio.org/ticket/167)

---

### Post by 23dornot23d on 2010-10-13
Interesting ..... Linux Mint plays the DVD's ok in VLC ..... 

but it still it struggles in Movie Player plays a few frames and falls over.

Ok next step how to copy it to the USB hard disk .... do I want it full size ... is there a compressed format ?

Guess MP4 is it .... what program to use ?

---

### Post by SeijiSensei on 2010-10-13
Please don't blame Ubuntu for having to comply with the copyright restrictions and digital rights management systems that rights-holders require.  Software like libdvdcss violates the "no-circumvention" provisions of the US Digital Millenium Copyright Act.  Yes, it's more difficult to play or rip a DVD on Linux because totally-free distributions like Ubuntu can't legally distribute the software to do so in some countries, particularly the US.  Instead they leave the decision whether to obtain this software up to the user via the restricted-extras repository.  

Windows machines usually include licensed software to handle these tasks.  Most buyers don't know this and assume it's just part of Windows.  The same holds true for the H.264 video codec.  Microsoft pays a licensing fee to the MPEG-LA for each copy of Windows so that the codec can be bundled with Windows Media Player.  Ubuntu users have paid none of these licensing fees unless they've chosen to use [Fluendo]("http://www.fluendo.com/").  People migrating from Windows to Linux thus expect that Linux will provide the same level of support for things like DVDs and are often surprised to find that support missing.

These legal issues largely pertain only to the US and a few other countries.  Nevertheless to avoid having to make separate distributions for different jurisdictions, free distributions like Ubuntu and Fedora must put the software that violates laws like the DMCA in a separate location.

---

### Post by 23dornot23d on 2010-10-13
Ok ..... not blaming it .... am finding a routine that people can follow if they desire to get the best results .... no harm in that.

I need to know how though .... !!

We buy the DVD's .... the greedy man got our money ..... but to watch them ..... the greedy man wants more money for the codec .... does not seem right to me

One Solutiion we stop buying DVD's and Codecs ...... and only watch the free broadcasts on the web then they will improve as demand does.

**It does not sort out the fact I have a load of DVD's that I bought and my only means to watch them is the computer .... so they are worthless .... seems bizarre to me.**

---

### Post by mastablasta on 2010-10-13
or get windows and pay for them...
 
or use another linux distro that is not USA based and to which these laws do not apply.

---

### Post by thecapsaicinkid on 2010-10-13
Just tested and the forced subtitle option (i.e show subtitles for just the non English bits) does not work in the current mplayer and isn't supported at all in VLC. How exactly are people watching dvds then or am I the only non multi-lingual person? Wished I'd paid more attention in French and German at school now :(

---

### Post by thecapsaicinkid on 2010-10-13
> **SeijiSensei said:**
> Please don't blame Ubuntu for having to comply with the copyright restrictions and digital rights management systems that rights-holders require.  Software like libdvdcss violates the "no-circumvention" provisions of the US Digital Millenium Copyright Act.  Yes, it's more difficult to play or rip a DVD on Linux because totally-free distributions like Ubuntu can't legally distribute the software to do so in some countries, particularly the US.  Instead they leave the decision whether to obtain this software up to the user via the restricted-extras repository.  

Windows machines usually include licensed software to handle these tasks.  Most buyers don't know this and assume it's just part of Windows.  The same holds true for the H.264 video codec.  Microsoft pays a licensing fee to the MPEG-LA for each copy of Windows so that the codec can be bundled with Windows Media Player.  Ubuntu users have paid none of these licensing fees unless they've chosen to use [Fluendo]("http://www.fluendo.com/").  People migrating from Windows to Linux thus expect that Linux will provide the same level of support for things like DVDs and are often surprised to find that support missing.

These legal issues largely pertain only to the US and a few other countries.  Nevertheless to avoid having to make separate distributions for different jurisdictions, free distributions like Ubuntu and Fedora must put the software that violates laws like the DMCA in a separate location.
Windows doesn't come with a dvd codec, at least XP didn't the last time I tried it. Also, bypassing copyright i.e CSS is never a problem, libdvdcss works great so I would say DRM issues etc. aren't the cause.

My main issues were with pulseaudio, libdvdnav, subtitle handling etc. etc.

No digital audio passthrough support and no forced subtitles both kill dvd playback dead imo. Both would be a bare minimum requirement for your basic standalone dvd player.

I'm not blaming Ubuntu as such, it's my not-inexperienced opinion of media playback in Ubuntu as it currently stands. Like I say, I really want to stick with Ubuntu for my media box but I absolutely would not recommend any built themselves a media pc based on it.

---

### Post by mastablasta on 2010-10-13
> **thecapsaicinkid said:**
> Windows doesn't come with a dvd codec, at least XP didn't the last time I tried it. Also, bypassing copyright i.e CSS is never a problem, libdvdcss works great so I would say DRM issues etc. aren't the cause.
 

 
also ultimate/media whatever editions?

---

### Post by ventrical on 2010-10-13
> **cariboo907 said:**
> I've never had a problem playing DVDs on my computer running Ubuntu, do you guys that are having problems have libdvdcss2 installed?

You can install it enabling the medibuntu repositories, or running the script in /usr/share/doc/libdvdread4.

Ubuntu is just like any other operating system, you have to install extra software in order to play DVDs.


  I did everything  "t"  a tee and still get .. over and over ..

---

### Post by ventrical on 2010-10-13
> **thecapsaicinkid said:**
> 

I'm not blaming Ubuntu as such, it's my not-inexperienced opinion of media playback in Ubuntu as it currently stands. Like I say, I really want to stick with Ubuntu for my media box but I absolutely would not recommend any built themselves a media pc based on it.

  I'm not complaining either. Actually they call it a 'distraction'. (DVD players) but it's nice when they are working if we need them. Overall, Ubuntu/Kubuntu are still tops.

  I'm thinking of writing my own OS called  Nanubuntu -- a simpler, more educational based OS for younger people so they are not playing so many video games.!!

ehehe:)

---

### Post by ubunterooster on 2010-10-13
> **ventrical said:**
> I'm not complaining either. Actually they call it a 'distraction'. (DVD players) but it's nice when they are working if we need them. Overall, Ubuntu/Kubuntu are still tops.

  I'm thinking of writing my own OS called  Nanubuntu -- a simpler, more educational based OS for younger people so they are not palying so many video games.!!

ehehe:)
Why? :(

We can just add games; trust me when there's a will, there's a game

---

### Post by ventrical on 2010-10-13
> **ubunterooster said:**
> Why? :(

We can just add games; trust me when there's a will, there's a game


 I think what I meant to say is that, yes , KDE and GNOME offer some really good games but, for the most part, those games are educationally based.  (I would rather see a kid play ExtremeTuxRacer than Call to Duty on XBox or Ps2(3).

Watching the more graphical and violent games gets kids out of sync with an exercise regime.IMO.

  I am a certified video game  repairman , although that was from a long time past (space invaders/pac-man) and so I guess I just had my fill of the supergraphic aspect of PCing. However, my point again is that it would be nice , err, if not convenient to have a working DVD player while running an Ubuntu platform.

 VLC works fine on Win XP Home and Pro... just download and stick in the DVD. On the Sony Vaio a DVD player comes with the OEM.. so there is no codecs worry there.. etc..

---

### Post by Perfect Storm on 2010-10-13
> **ventrical said:**
> I did everything  "t"  a tee and still get .. over and over ..

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ventrical on 2010-10-13
> **Artificial Intelligence said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 But Great Unholy Puppet Master.. that is exactly where I went and I followed that script to a "t" and it installed everything (even the libdvdcss2 file) and nothing. But rest assured, Great Hammer Master, that I mean no complaints.

  Guess the best I can do is read  it over again or take it to mean that Ubuntu project  does not include codecs .. and I am at peace with that.

  I am going to try an experiment. I am going to download VLC  on to my XP which I have set up as a virtual machine on my Dell . I'll get back.

 Thank you  Great Mojo Master.

---

### Post by ubunterooster on 2010-10-13
"Puppet Master", "Hammer Master", "no complaints" "Mojo Master" Oookay then I think it is safest I move along.

BTW, I find that Fluendo works fine even though I had many problems with other players

---

### Post by Perfect Storm on 2010-10-13
> **ventrical said:**
> But Great Unholy Puppet Master.. that is exactly where I went and I followed that script to a "t" and it installed everything (even the libdvdcss2 file) and nothing. But rest assured, Great Hammer Master, that I mean no complaints.

  Guess the best I can do is read  it over again or take it to mean that Ubuntu project  does not include codecs .. and I am at peace with that.

  I am going to try an experiment. I am going to download VLC  on to my XP which I have set up as a virtual machine on my Dell . I'll get back.

 Thank you  Great Mojo Master.

Can you start a new thread in our support section. Then I and others can take a closer look at it.

---

### Post by ventrical on 2010-10-13
> **Artificial Intelligence said:**
> Can you start a new thread in our support section. Then I and others can take a closer look at it.

Done . Thanks.

---

### Post by ventrical on 2010-10-13
> **ubunterooster said:**
> "Puppet Master", "Hammer Master", "no complaints" "Mojo Master" Oookay then I think it is safest I move along.

BTW, I find that Fluendo works fine even though I had many problems with other players

I'll give that a try .

Thanks

---

### Post by ubunterooster on 2010-10-13
> **ventrical said:**
> I'll give that a try .

Thanks
$25 might be bit steep for the price though

---

### Post by ventrical on 2010-10-13
My aplogies.

Actually I re-installed VLC and it works just beautiful. The graphical image is just lucid !! So, Ubuntu makes for a good entertainment center.
 Thanks everyone.

---

### Post by SonicSteve on 2010-10-13
> **ventrical said:**
> I did everything  "t"  a tee and still get .. over and over ..


I've seen this message on a toshiba laptop. It turned out that the DVD player itself was the issue. Using a different DVD drive solved the problem. I never figured out why the drive kept giving this message but it did.

---

