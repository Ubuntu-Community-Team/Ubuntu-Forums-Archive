---
title: "Project: MOTHER."
date: 2005-01-31
forum: The Cafe
---

### Post by senectus on 2005-01-31
**_*[COLOR=Red]The project has been resurrected! Both myself and the MOTHER In question are tired of all the on going problems with MS Windows and I'm now documenting the project [HERE]("http://www.modmeup.net/?page_id=2") [/COLOR]*_**


[COLOR=Red]***Update 10:15 pm 3rd of Feb 2005***[/COLOR]

I got sick of rebuilding my mothers PC every 6 months because she is way to trusting and like the funny things her friends send her.
Every 6 months her machine becomes so loaded with adware/spyware/malware that it has a hard time booting.

So after my many successes with this very new distro I told her I'm not going to put up with her pain any more and I'm rebuilding her machine one. last. time.

So she's been migrated to Ubuntu.
I plan on documenting the entire process here.. partially for fun, partially for my education and partially because I want others to learn from my mistakes.
Also feel free to point out better ways to do the things I'm doing, and ask questions.

I'm going to try and keep it in this one post so I'll just re-edit it as time progresses, I'll put the last edited date at the top manually (as the forum likes to put that at the bottom )

Here goes...

Her PC is an old Dell Optiplex I picked up cheap from an auction.
PIII 700mhz
320mb ram 

I started by driving to her place burning a CD of her music, a cd of her photo's and a cd of random files and email/favourites.
I made an extra copy of the e-mail stuff because I had been told on the ubuntu mail list that Outlook Express (OE) mail boxes were directly importable into evolution, so I'd take that back with me.

Pickup PC then drive home.
I didn't even boot into windows, I just plugged it in and booted straight into a warty CD and started the install process.
I'll put most of the process into the code box, as there are addresses that might be useful to some people.

```

Build from Warty CD
After default build I logged in and :
sudo passwd root
I do this for various reasons.. mostly because I'm lazy 
	**Up to this point took about 30-45 mins! A winXP build with the same level of applications and security setup would have taken me at least half a day. Fantastic!

apt-get install rssh
     Because I will need to remotely support her.
apt-get install linux-686
      Might as well squeeze the last bit of juice out of it. 

The Ubuntu Philosophy is to be 100% free, and although I support and applaud this stance Its way to restrictive for reality everyday usage so time to add the unofficial repositories :

add sources to /etc/apt/sources.list
	deb http://ubuntu-bp.sourceforge.net/ubuntu warty-backports main universe
	deb http://archive.ubuntu.com/ubuntu/ warty multiverse

	deb http://ubuntu.tower-net.de/ubuntu/ warty java

	deb ftp://ftp.nerim.net/debian-marillat/ stable main
	deb ftp://ftp.nerim.net/debian-marillat/ unstable main
	deb ftp://ftp.nerim.net/debian-marillat/ testing main

apt-get update
apt-get upgrade
apt-get dist-upgrade

Time to add java support :
http://www.ubuntulinux.org/wiki/AddingJavaSupport/view?searchterm=java

wget jre-1_5_0_01-linux-i586.bin
sh jre-1_5_0_01-linux-i586.bin
mkdir /usr/java
mv jre1.5.0_01/ /usr/java/
chown -R root:root /usr/java/jre1.5.0_01/
ln -s /usr/java/jre1.5.0_01/bin/java /usr/bin/java
ln -s /usr/java/jre1.5.0_01/bin/java_vm /usr/bin/java_vm
vi /etc/bash.bashrc
	JAVA_HOME=/usr/java/jre1.5.0_01
	export JAVA_HOME
	PATH=$PATH:$JAVA_HOME/bin
	export PATH

Java Plugins for the browser:
cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

Music and stuff:
apt-get install xmms
apt-get install build-essential

I found IPv6 really hampered my internet speeds so lets kill it:
vi /etc/modutils/aliases
	de-hash the line:
	alias net-pf-10 off
update-modules

```

I got lazy here, and started installing bulk software without writing down what I did.. so here is a summery from memory:
gmplayer
xine
realplayer
w32codecs
plugins for firefox
dvd codecs
supertux
liquidwars
pornview (boy did I have a red face when explaining this little gem to my mother  [-X  but it really is one of the best image viewers in my opinion.)


So now its ready to take back.
Drive back there and plug in and turn on.
Boots up fine.. the first thing I wanted was net connectivity, she runs dial up at the moment so 
Copmuter > System Configuration > Networking.
Add new connection, choose Modem(ppp), and setup as per the requirements.
Attempt to connect.. and the modem dials (external generic 56k modem), talks for a bit then drops off.

 :-# 

tail /var/log/messages
and I'm seeing "authentication failure"
 
Double check the username and password.. try again, and it fails again and again and again.
Ring tech support:
ME "Hey can I check a username and password for my mothers account?"
HelpDesk "yeah no problem, whats the username"
ME "Senectus_mum"
HelpDesk "ahh yeah found it, whats the password?"
ME "Cats_Name" (*sigh*  I can't believe we're related)
HelpDesk "*quiet pause and I swear I heard him chuckle* yeah you have it right"
ME " hmmm  :???: what have I done wrong"
HelpDesk "What Os are you using?"
ME "ahh I know you guys don't support it, but its Linux..."
HelpDesk "heh, thats ok.. *utter amazment at my end of the phone* what distro?"
ME "Ubuntu.. its debian based"
HelpDesk "ahh yeah, I've heard of that.. cool, um what Authentication are you using?"
ME " ahhh.. good question... I may have to get back to you"
HelpDesk " yeah no problem, you might want to check that modem works under windows on a different machine if you have one"
ME " yeah I have a dual boot laptop.. I'll do that thanks"
HelpDesk " No problem"

At this point in time I'd like to place a small plug here:
Westnet ([www.westnet.com.au](www.westnet.com.au)) are THE BEST ISP in Australia, They just don't give up until you problem is solved.

Next small point I need to make  the gui method I used to create the dial up does not allow you to change or even find out what authentication your using.. something that needs to be fixed??

So I pulled my lappy out and hooked up the old modem and made a perfect connection.
so username and password are fine.
While I'm hooked up I poke around the wiki to see if there is anything on dial up..
sure enough.. I found this:
[http://www.ubuntulinux.org/wiki/DialupModemHowto/view?searchterm=dialup](http://www.ubuntulinux.org/wiki/DialupModemHowto/view?searchterm=dialup)

and it worked almost perfectly.. I had to set it to use CHAP authentication and bingo.. happy as larry!

Great.. so next I crank up the email and get that downloading..
After the emails are all downloaded I try importing the inbox.mbx file..
hmmm I don't think it worked, but I got no error.
Next try the other e-mail files.. ( I forget what the extentions are but they're folders from OE ), and it appears they won't import either.. Evolution doesn't know what they are..
Same deal for address book (.WAB), no ability to import it.
Bugger, not all is rosey so far.

Mother see's the frown om my forehead and tells me it doesn't really matter.
I refuse to give in and tell her I will work it out later and bring them back when I do
"no worries" she says "no hurry" 

Not please.. but eager to get the rest working I then head for the favourites.
Fire-fox wont import them either.  It appears the IE 6 likes to store favourites as ".url" files..
damnitdamnitdamnit should have researched more.

once again mother saves my ego and tells me I can fix that later too.
Not impressed with myself at this stage.

Next is the digital camera.
*sigh*
Kodak DC200, its old, its clunky and its not detected by Ubuntu.
You guessed it...
"You can take that back home with you and figure it out"
  ](*,) 

feeling tired and worn out by now.. I just wanted to clear out and go home.

Stuff around fixing internet banking pop-up problem I knew was there, show various games (which makes me feel better because she likes them) and show her how to use the basics..
Leave her with the instructions that she may play with it as much as she likes, as she isn't going to break it *PROVIDED* that if anything that pops up asking her for a password, she be vary carefull with.. as generally anything that wants a password, wants it for a reason..

I asked her to make a list of questions and anything she doesn't like.

Since this happened I've posted a few Q's on the mail list about e-mail importing and other stuff.. you can find them and the replies here:
[http://www.ubuntuforums.org/showthread.php?t=13277](http://www.ubuntuforums.org/showthread.php?t=13277)
and
[http://www.ubuntuforums.org/showthread.php?t=12640](http://www.ubuntuforums.org/showthread.php?t=12640)

I haven't progressed much at all since then.. but I intend to tomorrow night..

**Things I/MOTHER thinks Ubuntu needs to fix:**
CDROM ejecting from the button on the front of the drive. (currently not supported)
The ppp modem setup gui is a little too "dumbed down" (example: how do you setup CHAP authentication?)
Some sort of applet that shows you currently have an active dialup running.


**Things that hindered the migration:**
Mail from OE to evolution conversion, no simple and easy method of doing this and to actually do it you need windows and other MS software. 
I had tried to soften the blow by setting up thunder bird and fire fox in windows some months before the migration.
She dropped thunder bird because she couldn't use the cute stationary and other such "gump" that her friends use.
Fire fox she dropped because tech support asked her too, they don't support FF only IE and if she wants her problems looked at then please uninstall FF.
This I feel, displays some _major_ flaws in the "gradual migration" methods. If we're going to get serious about the "taking on" of our competitors market, we need some more and _much_ better migration tools, ones that don't requires the "other" OS to be running preferably. 
Also I'm not aware of any "Migration guide" out there (for Ubuntu or other).
It seems logical to me that there must be one, as others have been doing this before me.. so I'll put this down to a temp gap in my learning.


Important milestone. *FEEDBACK*
I recieved a message from my mother, this is important as I've not been in contact with her since my semi completed migration ending 4 days ago.

Here it is:
> Hi Senectus and Mrs_Senectus,
                  I am still getting used to the computer and not real
sure if I like it.  Yahoo is just so different and I can't do a lot of
things that I used to do which  makes me more visible to others  which I
don't like.    I have issues with some of the sounds..... I know I
will get used to them but some still baffle me, I can  be doing
something and it makes a funny noise...... it can mean anything from
mail arriving to  someone  coming or going  on yahoo...  I really need
my addresses from  outlook, but  its not an issue, people are slowly
sending me mail so I can reply  and add them. There is  one or two  like
XXX XXXXXX that I really  would  love to have.  I tried to copy  some
music  from my cd's to the computer  but I have no idea how to  do this,
I tried  for  quite a while and thought I had been successful because it
looked like it was saving but then I couldn't find where it was. Sorry if
I sound like I'm whining  coz I'm really not, I am getting used to  the
change and am very grateful.   
I have two people who are interested in a  copy of unix ..... will they
need  someone savy like you to install it? both these people are dummies
like me when it comes to puters.
Thanks love
Mum XOXOXOOX


Now I'm in a bit of trouble here.. because I have one really crap and very full week, I just haven't had *time* to fix the things I left hanging.. so important note to those of you thinking of doing this.
Leave plenty of time for the unexpected.. be prepared for the worse to happen..
One thing I should have done that I am kicking myself about now.. is the planning phase.
I had a manager once that was _right in_ to "self development" and one thing he taught me that I found rather cool was a particular method of planning that helps to iron out bugs and issue's.. apparently it was used in the planning of our first trip to the moon..
The way it works is you think in reverse.
So for that would be.. 
my mother having a fully functioning Linux PC with her mail and address book and Internet connection and camera connectivity plus the ability to  rip music at will.

Then you take the next step back from that..
What happened before that:
I pulled some images from her camera
Before that? :
The OS detected and installed the drivers
Before that? : 
I checked the model of the camera and downloaded the right drivers
Before that? :

and so on and so on..
Doing this way really opens up your planning method and helps to stop you taking short cuts that are inherit in normal "planning".

I vow to make myself use this method more in future..

---

### Post by Rancoras on 2005-01-31
Great post, I've been thinking about doing this for my mother for a while now.  I just haven't worked up the courage yet, hehe.

One thing I want to know, though.  Who is Larry and why is he so happy? ;)

---

### Post by CowPie on 2005-01-31
I love it!!!  Great writing and good luck

---

### Post by poofyhairguy on 2005-01-31
Tips for the camera:

[http://www.sleeper.apana.org.au/kodak.html](http://www.sleeper.apana.org.au/kodak.html)

Your good writing has proven to me what I already knew- Linux is best suited for a broadband environment.

Whenever I do my daily upgrade of Hoary, it averages 80 megs. Even warty needs 40+ megs of updates after and install. I would prefer hours of watching figure skating (*me shudders at thought*) rather than trying to get that on dial-up.

Linux will grow as broadband does I believe.

(no offense to people who like figure skating. Because somebody does or it wouldn't be on TV.)

---

### Post by rudi on 2005-01-31
[QUOTE=Rancoras]One thing I want to know, though.  Who is Larry and why is he so happy? ;)[/QUOTE]
 He could be referring to Leisure Suit Larry....... then you'll know why he is happy ;-)
 
 Back on-topic, like the post! I wouldn't have the guts to get my mum to Linux [img]http://www.ubuntuforums.org/images/smilies/icon_mrgreen.gif[/img]

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=rudi] 
 Back on-topic, like the post! I wouldn't have the guts to get my mum to Linux [/QUOTE]

Me neither.

Its easier to talk her into a sleek minimac. Let her be apple's problem!

---

### Post by senectus on 2005-01-31
wow.. thanks for the replies :-)

I think now you've said that I'll do another for :
Project: Girlfriend

:-) I converted her some time ago... and its a substantially different story.

---

### Post by TravisNewman on 2005-01-31
I like the idea of Project: MOTHER as a repository with a metapackage called "Mother" with all the dependencies of said metapackage. Basically it would set up all the stuff that you need to do to make your mother happy with Linux.

---

### Post by senectus on 2005-02-01
neat idea.. 

How hard is this to setup.. ?
Actually a repository howto would be handy too..

---

### Post by nocturn on 2005-02-01
Just two quick reactions to your update.

Migrating your mail from Outlook to something else is difficult due to the reason that Outlook stores its mail in a proprietary file format.  Something to which other devs have no access and that can even be legally fishy to reverse engineer.  
This is part of the Microsoft lock-in tactic (make it as difficult as possible to migrate).

On the techsupport requiring IE, we cannot fix that.  Only when FireFox gains a significant market share for them to *have* to support it, this will get better.
The sad thing is that if IE followed standards even a little, most things would just work on any other browser too.

---

### Post by adbak on 2005-02-01
Congrats!
For this story has made it to the front page of LXer.com!!

It's under the name 'Ubuntu for mama'.

---

### Post by GreyBeard on 2005-02-01
Kmail will import Outlook Express folders.  Perhaps you could install it from debian and then remove it once you have brought your email across.  I find I need the kde and qt libs anyways for quanta, rosegarden, noteedit and scribus.

GreyBeard

---

### Post by senectus on 2005-02-01
[QUOTE=adbak]Congrats!
For this story has made it to the front page of LXer.com!!

It's under the name 'Ubuntu for mama'.[/QUOTE]


 8-[ 
Two things I'm grateful for...
1) I try to never use my real name on the net... 
2) My Mother isn't a geek so there is little chance of her reading it...   8-[ 

She doesn't appreciate some of my dryer sarcasm...  :mrgreen:

---

### Post by Lovechild on 2005-02-01
I found the GNOME and KDE game packages invaluable tools in converting mothers. For me PySol and Freeciv2 has also worked nicely in convincing the gf that Linux isn't all evil and breakage (as she experiences it watching me.. giving my nack for tinkering I break Linux all the time)

As for the eject button, that's a HAL issue, we can support it but because of shabby hardware specifications not all drives support the needed call, thus leading to two different experiences for users (supported or unsupported) which isn't good for usability - thus for now we are forced to do the umount thing. I know David who works fulltime on HAL and related matters for RedHat is giving this some thought, but it seems that hardware is setting the limitor on this for now.

---

### Post by machiner on 2005-02-01
Hey Senectus - Your post was very, very good. I have saved it and will refer to it when I set up similar machines.

Thank you for your work and diligence...esp your references.

I hope you work out the little ditties that are making your mom-box appear less than perfect.

rock on.

---

### Post by Marquis_de_Carabas on 2005-02-01
[QUOTE=senectus]Some sort of applet that shows you currently have an active dialup running.[/QUOTE]

Have you tried Modem Lights? I'm on broadband so I've never used it, but it's in the gnome applets package and it *appears* to be what you're looking for.

---

### Post by senectus on 2005-02-01
:-) cool
I'm very happy that it's helped someone :-)
I promise to keep it uptodate as I can.. with at least a change a week..  for the next feew weeks.. 
I _will_ make it right.

make sure you drop in again ;-)

---

### Post by penguinwarrior on 2005-02-01
With my daughter, her choices were using Windoze on my wifes computer or Linux on mine.  She chose windoze (it was what she grew up with) even though that computer was slower (pentium plus adware/spyware/windoze-stupidity/reboot/reboot/reboot)... that was until she got tired of rebooting every time she was downloading songs or instant messaging and she got sooo tired of the computer getting slower and slower and then rebooting itself! 
( =D>   yay Microsoft... they got something right....sometimes it could reboot itself and actually not crash while rebooting    =D> ).

She finally saw that i could download songs (limewire, just like on windoze) and instant message (GAIM with MSN, almost like on windoze) and i had no problems with having to reboot, no slowdowns, nothing. 

My wifes computer is now almost crippled (she can no longer open her word-perfect documents and she is running spybot almost daily) but she "doesn't want to learn something new... windoze is just easier to use than Linux  (I am so embarassed for her  :oops:   :D   but i understand she doesn't have time.... she's too busy running spybot or rebooting  =D>  8-)     sorry dear.   I still love you  :!: 

but my daughter is now almost fully into Linux  (GNU/ Linux!).  pysol is mandatory and now so is Tetravex, as well as Gaim and Limewire.

A funny aside (funny to geeks like us... my wife just thinks i'm compulsive) the other day i was in McToilets with my wife and son (diagnosed mildly autistic.. surprise surprise) and i took him downstairs to the 'playroom' which is just video games and pay per use air hockey.  His favourite game is this touch-screen matching game.

the game was unplugged, so i plugged it in.  of course, i was watching to see what it booted up under and was happy to see LILO, then  BOOTING LINUX!

Next will be Project: WIFE (or : how to get the my angel out of Hell and into Heaven  or : Don't even try mister... just keep your hands off my computer).

---

### Post by jdodson on 2005-02-01
smile you have been linked from [http://osdir.com/](http://osdir.com/) :)

[http://www.osdir.com/Article3917.phtml](http://www.osdir.com/Article3917.phtml) to be a bit more specific.

---

### Post by Typhoon on 2005-02-01
If you start with someone who has had no Windows experience, the process is much easier. My neighbour is a 95 yo woman who fell a couple of years ago and was housebound. I set up an old box with Red Hat and she uses it every day to surf the net and send/receive email.

If I were doing it today, I would definitely use Ubuntu.

Nice article!

Typhoon

---

### Post by senectus on 2005-02-03
Thanks for the replies everyone..
I'm setting some time aside to fix my stuff-ups using your suggestions this Saturday.. I hope she can wait that long...

hmm if my original post gets much longer I'm going to have to move it somewhere else I think... I don't want to be breaking forum rules by making ridiculous sized posts..

---

### Post by stilus on 2005-02-19
Great post, enjoyed it very much and found it very familiar!

I finally managed to get both my girlfriend and my mom over to linux. My mother was actually the easiest to convert. She was using her computer for both work and ehr... cardgames... but got sick enough from viri and other pesky things to try something new. 

I don't remember any problems with Outlook, as she had been using Suse (and Kmail, see GreyBeard's post) shortly before switching to Ubuntu. One advise I would give to all the "resident geeks" that end up doing these installs (that's what family is for, isn't it?  :wink: ). It fits in perfectly with the "trip-to-the-moon technique" (I'm gonna remember that one): what would you do before installing ubuntu? Try to find out if the hardware will work. And what would you do before that? Go with mom/ anyone important to the store when they buy hardware, so you know it will work with linux (In case they want to switch someday  :grin: ). Or at least advise them. 

Do take senectus' advise and take your time for an install though, nastyness is always around the corner. It was for me: I was all bouncy and happy with Ubuntu and getting her all enthousiastic. She was looking right over my shoulder and.... then the CDROM wouldn't boot...  :shock: The [smart boot loader](http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/) provided the answer to that problem. That brings me to my second advise: always keep an internet-savvy computer (laptop?) handy in case you have to find out things (or make a floppy) along the way!

Anyway, things have gotten a lot quieter on the help-mom-desk and ssh (and a phonecall) does the rest ("what!? Are you on my computer...**now?!**..."). She's pretty happy with her machine and so am I! 
Good luck to all of you (and especially senectus) installing Ubuntu everywhere!

---

### Post by senectus on 2005-03-07
Thanks for the input guys.. but I'm sad to announce that Project : MOTHER has been closed and in my mind classed as a partial failure.

The test subject has nearly finished recovering from some surgery and is now attending classes to learn office skills. 
To be able to practice she needs Office and will not accept that Open Office is a good substitute.
So I've rebuilt her machine with XP ( ](*,) ) and Bought Office 2000 to put on her machine.

On the upside she did say that the only thing she didn't like about linux was the fact that we hadn't figured out how to log onto GAIM (Yahoo) in invisible mode. 
Having to choose invisible mode _after_ logging in isn't good enough.

She says that she _really_ is going to miss the card games it came with and she's stoked that I can make supertux run under windows.. 

:-( 

oh well..

---

### Post by landotter on 2005-03-07
[QUOTE=Marquis_de_Carabas]Have you tried Modem Lights? I'm on broadband so I've never used it, but it's in the gnome applets package and it *appears* to be what you're looking for.[/QUOTE]
 modem lights rock!

The gui ppp dial up tools in gnome indeed are lousy, but running "pppconfig" in a terminal will guide you through a painless modem connection (if you have a supported modem)

after setup, configure modem lights to "pon providername" and "poff providername".

BTW, my momma uses Ubuntu and loves it. Mind you this is a woman that browses the web, does email, and prints a bit--that's it. She insisted on the Mozilla suite, as that's what she's been using with windows--and that Realplayer be installed for Swedish National radio and BBC.

She plugs in her camera, and gThumb imports the photos for her, there's a desktop icon called "my pictures" which is really just a stealth link to gThumb.

The woman has a hard time understanding what a directory is for crying out loud--but she uses Ubuntu very productively because it simply doesn't "bother her" like XP did. No prompts for constant updates, no known virii, few if any popups, buy a new mouse at Costco--plug it in and it usually works...all in all a 100% success. 

:D

---

### Post by carpman on 2005-03-08
Know it is bit late but i wouold have installed firefox and thunderbird on win machine and imported fav and emails, would then have backed up firefox and thunderbird data dir and just copied these to new ubuntu install.

---

### Post by Slapdash on 2005-03-08
Great POST 

Yeah I have the same thing but mine wil be 

Project: Soon to be Father-in-Law so I'll have to learn everything before attemptng this LOL ;)

---

### Post by senectus on 2005-03-08
[QUOTE=carpman]Know it is bit late but i wouold have installed firefox and thunderbird on win machine and imported fav and emails, would then have backed up firefox and thunderbird data dir and just copied these to new ubuntu install.[/QUOTE]

Mein Gott! You have 20/20 vision  :roll: 

Yeah.. I know.. Maybe I'll get another change one day later.

---

### Post by bodyhead on 2005-04-07
Great article.  I'm sorry to see this failed for you.  I am doing the same thing for several people close to me.  I would suggust buying a copy of crossover office if windows support is a must.  If functions rather well and it will give your family those apps they 'must' have.  Personally I would also recommend a transgaming cedega account but that's simply because I need those games.

---

### Post by Brunellus on 2005-04-07
Ugh.  I hate to see the whole project fail just because she needed to learn MS Office!

It's things like this that make me look at mass migration to Linux as a chicken/egg problem:  how do you convince people to migrate to Linux when the larger marketplace still demands Windows skills (ie. interface familiarity, really) ?

Technically-minded people--geeks, academics, tinkerers, compulsive readers, curious people like me etc--deal better with abstract concepts.  These are relatively portable ideas, so we transfer them to whichever computing environment we're sitting in front of.  

Most of the population is not like this, I guess.  They need to be taught in a very specific manner--this sequence of gestures accomplishes this task, etc.  The concepts behind each step are utterly irrelevant:  they don' thave time to learn, and besides the result is important.  

My father is one of the former;  if necessary, he'll learn new things, and he'll try to carry over as much of his conceptual understanding to each new thing that he can.  When I'm talking about computer stuff, he usually asks me very broad questions about how stuff works....and while I'd struggle to give a complete explanation of, say, how our LAN works, I can give him the broad concepts.

My mother, on the other hand, requires specific, step-by-step instructions.  Explanations of *how* things work are wasted on her.  

My dad's pretty committed to Windows, since he gets his computers issued to him by his employer--but I suspect that he wouldn't be too fussed by a transition to Linux.  My mother hated my original attempt to migrate the house to Linux (SuSE 9.1 with KDE 3.2), probably because she had to ask me how to do *everything* step-by-step.    I suspect that now that I'm a little better at system administration, I'll repeat the experiment with Kubuntu and see how it goes.

---

### Post by poofyhairguy on 2005-04-07
[QUOTE=Brunellus]Ugh.  I hate to see the whole project fail just because she needed to learn MS Office!

It's things like this that make me look at mass migration to Linux as a chicken/egg problem:  how do you convince people to migrate to Linux when the larger marketplace still demands Windows skills (ie. interface familiarity, really) ?
[/QUOTE]

simple. 

First step: Download and run spybot (or adaware, or Microsoft's if you want to look official)

Step two: Show them all of the malware running on their computer. (if there is none, the person is competent in Windows and only needs a linux live CD without rhetoric).

Step Three: tell them about how bad malware is, what it does, and how it gets on their computer. Be sure to bring up ways that will make the person feel hopeless "its comes onto your computer when you use Internet Explorer" "EVEN YOUR (insert name of app you see on taskbar that you KNOW uses spyware for finacial support) HAS IT!!!!" Scare the crap out of them.

Step Four: the proceed to either sell them on a Mac (like for my mom- she doesn't trust Linux cause its free) or whip out the Ubuntu install CD and GET TO WORK! They won't usually object as long as you set up everything nice for them and give them access to their old ntfs files.

---

### Post by Brunellus on 2005-04-07
[QUOTE=poofyhairguy]simple. 

First step: Download and run spybot (or adaware, or Microsoft's if you want to look official)

Step two: Show them all of the malware running on their computer. (if there is none, the person is competent in Windows and only needs a linux live CD without rhetoric).

Step Three: tell them about how bad malware is, what it does, and how it gets on their computer (be sure to bring up ways that will make the eprson feel hopeless "its comes onto your computer when you use Internet Explorer" "EVEN YOUR (insert name of app you see on taskbar that you KNOW uses spyware for fincial support) HAS IT!!!!") Scare the crap out of them.

Step Four: the proceed to either sell them on a Mac (like for my mom- she doesn't trust Linux) or whip out the Ubuntu install CD and GET TO WORK! They won't usually object as long as you set up everything nice for them and give them access to their old ntfs files.[/QUOTE]

I hate fighting FUD with FUD, though.  Generally, I pitch it as a stabler, more efficient OS, with excellent software that's just up to the tasks most people need it for.

Their inevitable question is "if it's so good, why hasn't everybody else gone for it yet?" which is a much better question than it seems on the surface.

As to buying a Mac, well, that's a non-starter.  Macs are expensive--always have been, and still are.  My mother's a hard-bargaining type, and even if she doesn't fully understand what all the numbers on a spec sheet mean, she wants the biggest spec numbers for the smallest price.  Apple doesn't do that for you--they have successfully become a 'premium' platform--something that people are willing to pay extra for....and my folks aren't extra-paying sorts. 

So they're intrigued by free (gratis y libre) software, but somewhat overwhelmed by FUD.

---

### Post by wondering_jew on 2005-04-11
I try to convince my mother to at least try out linux from time to time and it inevitably turns into a discussion of politics. She seems to think that the idea of open source software etc stinks of communism and that windows is therefore obviously better (her logic on this one escapes me completely). Further discussion tends to reveal (much to my surprise) that I am a godless commie as well. Maybe she'd be more comfortable if I tried to convince her to pay $60 for the redhat distro i see at the book store so at least somebody was making some money....

---

### Post by kleeman on 2005-04-11
Godless communism in Wyoming  :smile:  :smile: I'm shocked! What would Dick Chaney say?  :smile: BTW keep up the good work (this from a NE Liberal :smile: )

---

### Post by connellr on 2005-04-11
[QUOTE=senectus]Thanks for the input guys.. but I'm sad to announce that Project : MOTHER has been closed and in my mind classed as a partial failure.

The test subject has nearly finished recovering from some surgery and is now attending classes to learn office skills. 
To be able to practice she needs Office and will not accept that Open Office is a good substitute.
So I've rebuilt her machine with XP ( ](*,) ) and Bought Office 2000 to put on her machine.

On the upside she did say that the only thing she didn't like about linux was the fact that we hadn't figured out how to log onto GAIM (Yahoo) in invisible mode. 
Having to choose invisible mode _after_ logging in isn't good enough.

She says that she _really_ is going to miss the card games it came with and she's stoked that I can make supertux run under windows.. 
[/QUOTE]

Oh, you were so close ... it pains me to see you give up! ... If you happen to get a 2nd chance at it  [-o<  here is a tip that I think you'll find makes the transition MUCH easier!  

Look into purchasing [Crossover Office](http://www.codeweavers.com/) This is a commercial linux program that sells for $35 (for the personal edition), and it allows you to run Microsoft Office, and many other windows applications natively in linux.  The installation is very easy and Office programs run flawlessly in it.  Other programs such as Quicken, QuickTime, Dreamweaver, Photoshop, Internet Explorer, etc all work well too.

Even with your mother taking classes for MS Office products she would still be able to use linux.

---

### Post by senectus on 2005-04-12
[QUOTE=connellr]Oh, you were so close ... it pains me to see you give up! ... If you happen to get a 2nd chance at it  [-o<  here is a tip that I think you'll find makes the transition MUCH easier!  

Look into purchasing [Crossover Office](http://www.codeweavers.com/) This is a commercial linux program that sells for $35 (for the personal edition), and it allows you to run Microsoft Office, and many other windows applications natively in linux.  The installation is very easy and Office programs run flawlessly in it.  Other programs such as Quicken, QuickTime, Dreamweaver, Photoshop, Internet Explorer, etc all work well too.

Even with your mother taking classes for MS Office products she would still be able to use linux.[/QUOTE]

I wasn't aware it was that cheap.. hmmm if/when she gets a new machine I may very well do that..

---

### Post by Zhukov on 2005-07-14
Well after a month of my own "MOTHER-like project" i have no trouble at all :D
All's fine, except some fuss with the .doc files, because Oo saves them as sxw. Is there anyway to make the .doc default?

And yes, the click-the-button and cd-will-eject would be a nice feature... :P

As well as an easy way to erase RWs.

Dont give up :) If i've managed it, everyone can :D

---

### Post by kleeman on 2005-07-14
Check out the Granny kde freak:
[http://reallylinux.com/docs/gran4.shtml](http://reallylinux.com/docs/gran4.shtml)

It's hilarious! I like the BS Dee crack

---

### Post by aysiu on 2005-07-14
[QUOTE=Zhukov]Well after a month of my own "MOTHER-like project" i have no trouble at all :D
All's fine, except some fuss with the .doc files, because Oo saves them as sxw. Is there anyway to make the .doc default?[/QUOTE] Yes, in options or preferences, under Save, you can change the default save type for "text" to be Word 97/2000/XP.

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=wondering_jew] Further discussion tends to reveal (much to my surprise) that I am a godless commie as well. [/QUOTE]

No offense, but this person is the target market for Windows....

---

### Post by senectus on 2005-11-20
stay tuned guys and girls.. this little project may be making a comeback *with a twist* (stupid reality TV style ;-) )

---

### Post by Brunellus on 2005-11-20
oh don't be coy.  what *twist*?

---

### Post by senectus on 2005-12-05
Project resurrected!

Now being documented [HERE]("http://www.modmeup.net/?page_id=2")

Wish me luck :-D

---

### Post by senectus on 2005-12-18
Project is nearing the end.
[http://www.modmeup.net/?page_id=2]("http://www.modmeup.net/?page_id=2")

It's been converted and handed back.
I'll log any new calls I get and call back in a week or so to find out how she's finding it :D

---

### Post by M3ta7h3ad on 2005-12-18
lol! being the devils advocate here.

I'd have just left windows on it, cleaned out the spyware, installed anti-virus and anti-spyware programs that I trust (not listed here... people always have different preferences when it comes down to it), and kept her machine clear of the gumpf.

I'd of also have done the customary defrag with a promise to come around and clean up the computer once a month when I go around for me cup of tea and biccie on the weekends. (Its a case of running defrag, and setting a full system scan going on all the tools... 3 hours later i've had my biccies and tea and we've caught up with whats going on, and I can leave.) 

I even set the computer to shutdown on its own accord in 3.5hours time, and have written a short batchfile to do this automatically in case of my absence I tell her to leave it on overnight if there is a problem with it, and at 2am everything kicks in thanks to scheduled tasks.

In 3 years I havent had a single major problem with her computer (in my experience im talking about me nan that lives up the road... but insert mother in its place for your purposes), she browses the net, does a bit of online card games (made a bit of money on that! aye), and sends emails.

I left her with the instructions of "If your unsure about anything just hit cancel, or no." She runs IE, and OE. Neither are infected with spyware, or have ever been. Would I try getting her to run linux? Based on your encounters with it, Windows seems the easier and more user-friendly choice for her. So I would have to say no.

So yeah.. several weeks tinkering to get it working in linux, or a day spent cleaning out junk from a pc to get windows up and running nicely. I know what I prefer.

Edit: just thought I'd say that since SP2, the monthly batchfile runs have never picked up on anything untoward. Before SP2 then yes... there were invariably one or two moderate threats that it found, from her ramblings around casino websites. (These are the worst culprits for it I think.. far worse than the dialers you get from 16yr olds viewing porn on their dad's pc.)

---

### Post by senectus on 2005-12-18
I've rebuilt her PC a total of 4 times (WinXP sp2 each time) in the last 2 years.
Each time was because she had installed crap software with hidden spyware then used the antispyware software to remove it, or had a virus EVEN THOUGH she is virus protected and my constant warnings and lessons on her PC activities.

The last time was mostly because Windows had done something bad to the modem driver and she was dropping offline constantly and connecting at ultra slow speeds.

The reason it took me weeks is not because it was a hard machine to build, I just didn't have the time to dedicate to it. (and _my_ PC shagged itself :-| ).

If I had had 3-4 hours to sit down and dedicate to it, that's all it would have taken.

---

### Post by M3ta7h3ad on 2005-12-19
lol :) you didnt say that it was your mum's ability to ignore advice :) I too have parents that do exactly the same, they learn soon enough when I explain that if they keep doing this they'll lose files and so forth.

I've now used local policies in xp to lock the system down for my sister and mum, my dad is sensible thank goodness. Will only install stuff after asking me, or if its on a CD and he knows it... my sister likes ringtones (stupid damn ringtone spyware websites), and my mum clicks yes on everything. :D Now 5 mins work in gpedit.msc and they cant do anything other than surf safe sites, and use the programs I allow them to use. If they need anything my dad can install it, or I can do it :)

---

### Post by senectus on 2005-12-19
[QUOTE=M3ta7h3ad]lol :) you didnt say that it was your mum's ability to ignore advice :) [/QUOTE]

Sorry, I kinda thought that was a given :???: 

I really, _really_ don't want to be on the speed dial for tech support, hence the Linux thing.
In theory I shouldn't get nearly any contact from her concerning this machine now.

---

### Post by ubuntu_demon on 2005-12-19
[QUOTE=M3ta7h3ad]lol :) you didnt say that it was your mum's ability to ignore advice :) I too have parents that do exactly the same, they learn soon enough when I explain that if they keep doing this they'll lose files and so forth.

I've now used local policies in xp to lock the system down for my sister and mum, my dad is sensible thank goodness. Will only install stuff after asking me, or if its on a CD and he knows it... my sister likes ringtones (stupid damn ringtone spyware websites), and my mum clicks yes on everything. :D Now 5 mins work in gpedit.msc and they cant do anything other than surf safe sites, and use the programs I allow them to use. If they need anything my dad can install it, or I can do it :)[/QUOTE]

isn't that roughly the same as a normal (non-admin) account (talking about XP ofcourse) ?

---

