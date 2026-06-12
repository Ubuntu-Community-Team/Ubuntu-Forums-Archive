---
title: "How to install Amazon MP3 app on 10.04"
date: 2010-05-09
forum: The Cafe
---

### Post by tvst on 2010-05-09
So, Amazon MP3 app requires libboost 1.34, which is older than the version now included in Ubuntu. The good news is that the old libboost version can coexist with the new one without any problems. So all you have to do is instsall the old version and you're good to go. Here's how.

Copy and paste the following text into a terminal window

```
mkdir old_boost
cd old_boost
wget https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb
sudo dpkg -i *.deb
cd ..
rm -r old_boost

```


Now you can install the Amazon mp3 app normally, following the instructions at:

[http://www.amazon.com/gp/dmusic/help/amd.html/]("http://www.amazon.com/gp/dmusic/help/amd.html/")

---

### Post by greenprell on 2010-05-14
This worked without a hitch! I'm so happy! THANKS for posting this!

---

### Post by miguelastico on 2010-05-15
You are my hero
however, I had to do getlibs /usr/bin/amazonmp3 in order to get it working (getlibs [here]("http://ubuntuforums.org/showthread.php?t=474790"))

---

### Post by Swagman on 2010-05-15
This works on 64 bit ?

---

### Post by highfructose327 on 2010-05-16
Thanks tvst! saved me form digging up all the debs

---

### Post by lenticular on 2010-05-16
Thanks! That is is big help.

---

### Post by pablolie on 2010-05-16
Awesome message, thanks. This post alone earns you forum superstar status as far as I am concerned.

---

### Post by timcredible on 2010-05-17
thanks - this worked for me too

---

### Post by twosox on 2010-05-17
Thanks, this worked.

---

### Post by ubunterooster on 2010-05-17
> **swagman said:**
> this works on 64 bit ?
+1

---

### Post by fluteflute on 2010-05-17
> **Swagman said:**
> This works on 64 bit ?

64-bit method:
[http://ubuntuforums.org/showpost.php?p=9145072&postcount=17](http://ubuntuforums.org/showpost.php?p=9145072&postcount=17)

---

### Post by ubunterooster on 2010-05-17
> **fluteflute said:**
> 64-bit method:
[http://ubuntuforums.org/showpost.php?p=9145072&postcount=17](http://ubuntuforums.org/showpost.php?p=9145072&postcount=17)
Thanks. :)

---

### Post by Swagman on 2010-05-17
> **fluteflute said:**
> 64-bit method:
[http://ubuntuforums.org/showpost.php?p=9145072&postcount=17](http://ubuntuforums.org/showpost.php?p=9145072&postcount=17)

Sorry, I've never had to run a script before.

So, are we supposed to copy & paste that line by line into the cli or something ?

---

### Post by fluteflute on 2010-05-17
> **Swagman said:**
> Sorry, I've never had to run a script before.

So, are we supposed to copy & paste that line by line into the cli or something ?
Yeah that's probably easiest. :)

---

### Post by billfish1881 on 2010-05-17
Thanks! Worked great on my 32bit machine. Thanks for posting that! 
For my 64bit Lucid, this other post did the trick: [http://ubuntuforums.org/showthread.php?p=9145072](http://ubuntuforums.org/showthread.php?p=9145072)
Specifically, the post from [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

---

### Post by Swagman on 2010-05-18
I copied & saved it into gedit and saved it out as amazon.sh. Changed it to executable then double clicked it and ran in terminal.

lots of errors popped up but it went through and installed ok.

Cheers.

---

### Post by Seamyst on 2010-05-29
Oh, that did it!  Thanks so much for this!

---

### Post by comic_rage on 2010-05-30
Thanks for the help. I had to add libglademm as well, but that was no problem. I see that one post directs people to FrozenFox. Who is this, it doesn't look like an official site.

---

### Post by Guitar John on 2010-05-30
Excellent.  Thank you.

---

### Post by QwUo173Hy on 2010-06-05
Works perfectly - thank you so much!

---

### Post by marsrise on 2010-06-05
Well, I must be missing something.  I tried running the script as suggested by TVST and it seemed to go fine.  Then reinstalled the .deb file from Amazon.  When I tried to use the option on the Amazon site however, I was prompted to install the downloader, as if nothing had happened.  I tried the getlibs suggestion, but no dependences seemed to be wanting.  Any ideas anyone?  Thanks in advance.

---

### Post by Seamyst on 2010-06-05
Marsrise, on the Amazon page where it's asking you to download the software again, there should be a link (in a smaller font) near the bottom saying to click here if you've already installed the software.  Click on that and you should be good to go.

---

### Post by marsrise on 2010-06-05
> **Seamyst said:**
> Marsrise, on the Amazon page where it's asking you to download the software again, there should be a link (in a smaller font) near the bottom saying to click here if you've already installed the software.  Click on that and you should be good to go.

Eeesh, Thanks Seamyst, I completely missed that.  Works like a charm now.

---

### Post by Seamyst on 2010-06-05
No problem!  I missed it the first time I installed the downloader, too.

---

### Post by moore.bryan on 2010-06-11
Excellent guide/solution... nice work!

---

### Post by inventory full on 2010-06-13
Thank you so much. I spent a half hour searching out a solution after I downloaded an album from Amazon. I finally got the album I paid for, thanks for posting this.

---

### Post by DonnellyBoy on 2010-06-18
Grazie! Worked a treat and downloading away! Much appreciated!

---

### Post by judiM on 2010-06-25
Fantastic!! 

Losing my Amazon downloader was the only thing I didnt like about upgrading to Lucid - thanks.

---

### Post by Matiancai74 on 2010-06-25
Thanks for this TVST. Solved a headache. :o).

---

### Post by The2DQuartet on 2010-06-26
I've been searching for ages for a way to install this; you can't download whole albums from Amazon without it which is a pain when the album costs a third of what the tracks would cost if bought separately!

I did have one (small) issue though. To get the libboost packages to install I had to force-architecture on them too by changing:

```
sudo dpkg -i *.deb
```

to:

```
sudo dpkg -i --force-architecture *.deb
```

It still warned me that libglademm was not installed but getlibs showed all dependencies to be complete and the application works fine (downloaded 3 albums with it straight away).

Thanks again for your help, I'm very grateful for it.

BTW I'm running Lucid 64-bit on an AMD machine.

---

### Post by gnomeuser on 2010-06-26
Next week Aaron is releasing [Amazon downloader support for Banshee](http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html) which hopefully will also present a nice way to interact with Amazons mp3 store.

---

### Post by hughes532001 on 2010-06-29
Hi, thanks for the instructions. They worked fine for me after I read all the info and then clicked on the link to enable the downloader in the web browser on the Amazon site.
:p

---

### Post by morgandrake on 2010-07-02
Thank you so much! This worked perfectly for me and was really easy for me to do. I really appreciate your taking the time to do this.

---

### Post by fishears on 2010-07-02
Many thanks to the OP for this fix. I'd tried a few others that didn't work but this one does the trick.

---

### Post by spiceminesofkessel on 2010-07-03
Thanks! This worked great! Now my fiance loves me again.

---

### Post by peterinmalaga on 2010-07-24
> **gnomeuser said:**
> Next week Aaron is releasing [Amazon downloader support for Banshee]("http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html") which hopefully will also present a nice way to interact with Amazons mp3 store.
Great but if you live outside the UK Amazon won't let you download anything "for geographic reasons". I live in Spain and thought we were in the European Union, so don't know what the problem is. I've installed  the Amazon MP3 player but can't use it!
It's little wonder that everyone is downloading everything for free illegally!

---

### Post by ksjc on 2010-07-25
Awesome!!!!!:d

---

### Post by gnomeuser on 2010-07-25
> **peterinmalaga said:**
> Great but if you live outside the UK Amazon won't let you download anything "for geographic reasons". I live in Spain and thought we were in the European Union, so don't know what the problem is. I've installed  the Amazon MP3 player but can't use it!
It's little wonder that everyone is downloading everything for free illegally!

Amazon only has mp3 store available in United States, United Kingdom, France, Germany, Austria, Switzerland, and Japan.

Sorry, they simply don't support you (or me) yet.

---

### Post by thirdender on 2010-08-11
Thanks for this! Worked like a charm.

---

### Post by seagullplayer77 on 2010-08-11
Sweet! This did the trick, man. Thanks for posting it!

---

### Post by mikefreeman on 2010-08-16
Tried the 64-bit instructions to the letter (copy/pasted each line into my terminal). Getlibs complained about the following:

No match for libglademm-2.4.so.1
No match for libgtkmm-2.4.so.1
No match for libgiomm-2.4.so.1
No match for libgdkmm-2.4.so.1
No match for libatkmm-1.6.so.1
No match for libpangomm-1.4.so.1
No match for libcairomm-1.0.so.1
No match for libglibmm-2.4.so.1

...and amazonmp3 won't run, giving me this error:

amazonmp3: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory

I'm running Linux Mint 9 (Lucid with a some extras added in). Any ideas? Thanks!

---

### Post by norfair on 2010-08-24
I was so excited to have stumbled upon this thread, but the solution isn't working for me as it has for most others here. I copied and pasted the code into the terminal, and it did a bunch of scary looking things, but the process finished okay. I proceeded to download the Amazon downloader, but upon doing so and running it, I was given this message by the package installer:

[INDENT]**Error: Dependency is not satisfiable: libboost-filesystem1.34.1**[/INDENT]

Does anyone by chance know why this error would occur? Am I doing something wrong, perhaps?

---

### Post by cometabroad on 2010-08-29
Thanks!  This fix worked perfectly.

I'd made the mistake of asking Amazon how to get round this problem, before looking here.

I won't be doing that again in a hurry...

---

### Post by oldos2er on 2010-08-29
> **mikefreeman said:**
> Tried the 64-bit instructions to the letter 

[snip]

I'm running Linux Mint 9 (Lucid with a some extras added in). Any ideas? Thanks!

Try [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by mitchs on 2010-09-01
works for me (10.04)

maybe try this too if it not works:

```
sudo dpkg -i --force-all amazonmp3
```
```
getlibs /usr/bin/amazonmp3 
```
and then like described before.

---

### Post by jofwooster on 2010-09-11
@norfair

I am experiencing the exact same situation: 

"I proceeded to download the Amazon downloader, but upon doing so and running it, I was given this message by the package installer:

Error: Dependency is not satisfiable: libboost-filesystem1.34.1"

@mitchs

I received the following errors consecutively trying your commands:

dpkg: error processing amazonmp3 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 amazonmp3

...and...

getlibs: command not found

Any ideas?

(I want access to all these free songs! : [http://www.amazon.com/Free-Songs-Music/b?ie=UTF8&node=334897011](http://www.amazon.com/Free-Songs-Music/b?ie=UTF8&node=334897011))

---

### Post by pablolie on 2010-09-16
Awesome!

---

### Post by keef123 on 2010-10-16
Works like a charm. Thank you.

---

### Post by Storyman on 2010-10-24
Worked great, thanks.

---

### Post by km10982 on 2010-10-25
> **tvst said:**
> So, Amazon MP3 app requires libboost 1.34, which is older than the version now included in Ubuntu. The good news is that the old libboost version can coexist with the new one without any problems. So all you have to do is instsall the old version and you're good to go. Here's how.

Copy and paste the following text into a terminal window

```
mkdir old_boost
cd old_boost
wget https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb
sudo dpkg -i *.deb
cd ..
rm -r old_boost

```


Now you can install the Amazon mp3 app normally, following the instructions at:

[http://www.amazon.com/gp/dmusic/help/amd.html/]("http://www.amazon.com/gp/dmusic/help/amd.html/")


This worked great for me. Thanks much for the post!

---

### Post by ectospasm on 2010-11-13
This script worked for me(again), thanks so much!

I've been in a dialog with Amazon support over this issue(lack of 64bit .deb for AmazonMP3), and I just got off the phone with an Amazon support representative.  He assured me that the development team is releasing 64bit versions soon, and he expects to have a release in about a week.  Unfortunately he could not point me towards any documentation saying so, but he did add my e-mail address to a list of affected customers.  I will update this thread once I've received word that it has been released.

---

### Post by timmyjoe42 on 2010-11-23
This worked awesome in 10 seconds, after I spent 45 minutes trying to get Pymazon to work.  Thanks a lot.  Why can't Amazon just include this in their process...

---

### Post by dondiego2 on 2010-11-26
Just downloaded the new Weezer album for $1.99 minus the 3.00 promotional gift - so free!  Thanks for the how to.  I was bumming and thought I would have to go back to windows so I was ready to give up because I didn't want to do that.

As a last attempt I did a forum search and found your post.  Worked great and I'm listening to Weezer right now!  Thanks!

---

### Post by daqron on 2010-12-01
> **oldos2er said:**
> Try [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

Clamz is awesome. Works like a charm (or like a clam?) without any errors or dependencies or other nonsense.

---

### Post by ScottyD135 on 2010-12-14
Worked perfectly!  Thanks so much.  I just crossed one more hurdle towards getting my family to use Ubuntu!!
:D

---

### Post by Bryce next on 2010-12-30
Kudos TVST! Your sage, spot-on advice is much appreciated. Worked beautifully.

Thanks.

---

### Post by Kalimol on 2010-12-31
Awesome fix - I've been using Pymazon for a while (and putting up with missing tracks....)

---

### Post by norrie35 on 2011-02-23
Many thanks for the info on installing the AmazonMP3  App. Having persuaded my daughter to move to Mint I was in deep trouble because she could not download MP3 music from Amazon. It :popcorn:Installed perfectly and calm has been restored.

---

### Post by Les_W on 2011-07-05
I've been frustrated by this for ages but this solution has bailed me out - MANY THANKS. It appears that the solution is 32-bit, so tried it on my 11.04 laptop and it worked great. Now to get my 10.04 64-bit desktop working...

(Why can't Amazon sort this out?)

---

### Post by GCLumpkin on 2011-08-07
I started downloading and installing dependencies one at a time as I found out which ones I was missing but thanks to tvst's instructions, the Amazon downloader installed without a hitch.

Thanks!

Greg

---

### Post by voxra on 2011-08-22
> **tvst said:**
> So, Amazon MP3 app requires libboost 1.34, which is older than the version now included in Ubuntu. The good news is that the old libboost version can coexist with the new one without any problems. So all you have to do is instsall the old version and you're good to go. Here's how.

Copy and paste the following text into a terminal window

```
mkdir old_boost
cd old_boost
wget https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb
sudo dpkg -i *.deb
cd ..
rm -r old_boost

```


Now you can install the Amazon mp3 app normally, following the instructions at:

[http://www.amazon.com/gp/dmusic/help/amd.html/]("http://www.amazon.com/gp/dmusic/help/amd.html/")

Cheers, this worked for me (Ubuntu 11.04). Not sure I should support the Amazon MP3 App if these are the hoops we have to jump through to get it to work, but it will do for now.

---

### Post by b1gag3 on 2011-08-28
thanks a lot, worked fo natty :)

---

### Post by coffeecat on 2011-08-28
> **Les_W said:**
> It appears that the solution is 32-bit, so tried it on my 11.04 laptop and it worked great.

> **voxra said:**
> Cheers, this worked for me (Ubuntu 11.04). Not sure I should support the Amazon MP3 App if these are the hoops we have to jump through to get it to work, but it will do for now.

> **b1gag3 said:**
> thanks a lot, worked fo natty :)

Why on Earth are you all installing the Amazon downloader in 11.04/Natty? :confused: The Amazon mp3 store has been nicely integrated into Banshee in Natty and purchasing and downloading Amazon mp3s in Banshee/Natty is so much easier and quicker than using the clunky Amazon downloader.

---

### Post by scaine on 2011-09-07
> **coffeecat said:**
> Why on Earth are you all installing the Amazon downloader in 11.04/Natty? :confused: The Amazon mp3 store has been nicely integrated into Banshee in Natty and purchasing and downloading Amazon mp3s in Banshee/Natty is so much easier and quicker than using the clunky Amazon downloader.

I'll have to check to make sure, but I can think of a few reasons.  One, I don't use a music player on my Ubuntu box - I have a squeezebox to play my music, but occasionally will use Amazon MP3 to download "throw away" tracks.  I've bought previously (via my Android phone, perhaps), then it's nice to be able to download those tunes again on my PC for convenience.  Can't do that without their downloader.

Like I say, I'll check, but I doubt that the store built into Banshee (or Rhythmbox, or whatever) will be intelligent enough to realise that you've previously paid for the music and simply want to download it again without actually paying for it.

[EDIT : Turns out you can't do that... at all!  Like iTunes, Amazon will only allow the re-download of songs exactly ONCE, and it has to be requested via support with a valid argument (like, "my hard disk blew up").  Live and learn.  Guess I'll stick to the CD so I can keep ripping into FLAC for my squeezebox!]

---

### Post by Foxcow on 2011-09-07
> **coffeecat said:**
> Why on Earth are you all installing the Amazon downloader in 11.04/Natty? :confused: The Amazon mp3 store has been nicely integrated into Banshee in Natty and purchasing and downloading Amazon mp3s in Banshee/Natty is so much easier and quicker than using the clunky Amazon downloader.



In my experience (and there are a lot who agree), Banshee is just awful.  I tried to like it but eventually moved back to Rhythmbox.  If there were a plugin for Rhythmbox, I'd be all over it.

---

### Post by Jozza The Wick on 2011-09-27
tvst, thank you. Worked perfectly for me!

---

### Post by virgoboy on 2011-10-17
This worked for me, too, thank you, thank you, thank you!!!  Very easy and painless install! :)

---

### Post by joemcveigh on 2011-11-12
Thank you very much, tvst. I'm on 11.10 and this worked for me.

---

### Post by ectospasm on 2011-11-12
This is still really clunky, and it doesn't work on Debian Squeeze.  However, there's a simple alternative:

[Pymazon]("http://code.google.com/p/pymazon/")

I had given up on being able to download MP3s from Amazon, until I discovered Pymazon.  Leave it to Google to host code which Amazon refuses to fix in their own client.  Time and time again I had called and emailed Amazon about this issue, and they have done NOTHING about it.

---

### Post by zipmon on 2011-11-16
Thank you so much for the workaround tvst! Worked for me on 11.10 and made my day! Amazon should probably update their application one of these days, huh? ;)

---

### Post by ectospasm on 2011-11-17
> **zipmon said:**
> Amazon should probably update their application one of these days, huh? ;)

I've been calling, and complaining, and threatening to cancel my Amazon Prime membership.  They will not be releasing an updated client any time soon.  It's been at least 18 months, with jack all to show for it.  At least Pymazon works for me.

---

### Post by Matt 6:27 on 2011-11-18
+1 on the TVST bandwagon.  Thanks much.

---

### Post by LowSky on 2011-11-18
> **ectospasm said:**
> I've been calling, and complaining, and threatening to cancel my Amazon Prime membership.  They will not be releasing an updated client any time soon.  It's been at least 18 months, with jack all to show for it.  At least Pymazon works for me.

you don't even need banshee or amazon's download app now. Amazon Cloud drive and Cloud player both allow you to download form any normal browser. BOTH FREE.

---

### Post by Quarkrad on 2011-12-09
I have this working on 10.10 thanks to this thread - but I've never used Amazonmp3 before.  I am setting it up for my brother-in-law who I've just converted to Ubuntu. Each time I down load an album or track (I'm using my amazon account and downloading free songs to test) I get prompted to save the *.amz file.  Is this normal?  From what I've read I assumed saving the *.amz file was a one off and subsequent download would be automatic.  So my question is - is it the case that you launch amazonmp3 player, go automatically to the amazon site, pay/download your music and then get prompted to save a *.amz file?  Thanks.

---

### Post by PGScooter on 2011-12-25
+1 the original script worked great for 10.04 for me. I don't know what the rest of the thread said but thank you!

---

### Post by Foster Grant on 2011-12-26
> **Foxcow said:**
> In my experience (and there are a lot who agree), Banshee is just awful.  I tried to like it but eventually moved back to Rhythmbox.  If there were a plugin for Rhythmbox, I'd be all over it.

I second that emotion.

---

### Post by pbidwell on 2012-01-20
Works here too!
Alternatively, if you don't want those weird libraries on your machine and you use Banshee, I found you can just click "I already have the MP3 Downloader" or whatever it is when Amazon complains that you have to install their software.  It will then download the .amz file, and under Banshee you can just Media -> Import Media and choose "Amazon MP3 Purchase".  Then point it to your .amz file and Banshee will take care of downloading your music.

---

### Post by cowb0y on 2012-01-30
clamz is available in the repositories (tried in 11.04 Natty; use the package manager to install it).  It will register the .amz file type, and when you click the appropriate link in Amazon, it should automatically download the album to your Music folder.  See the man page for more details after installation.

---

### Post by stillgale on 2012-01-31
THANK YOU! Fantastic way to answer a potentially complicated issue. Wish Amazon would keep us up-to-date.

---

### Post by Bigjack08 on 2012-05-07
> **tvst said:**
> So, Amazon MP3 app requires libboost 1.34, which is older than the version now included in Ubuntu. The good news is that the old libboost version can coexist with the new one without any problems. So all you have to do is instsall the old version and you're good to go. Here's how.

Copy and paste the following text into a terminal window

```
mkdir old_boost
cd old_boost
wget https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb
sudo dpkg -i *.deb
cd ..
rm -r old_boost

```


Now you can install the Amazon mp3 app normally, following the instructions at:

[http://www.amazon.com/gp/dmusic/help/amd.html/]("http://www.amazon.com/gp/dmusic/help/amd.html/")

Hi I have used the above suggestion and successfully downloaded the Amazon MP3 Downloader.
When I download music and open the downloaded file I do not get the music but a long list of data in Gedit.
As a newbie I am completely lost; before upgrading to the new Ubuntu 04/12 from Ubunto 10/11 there was no problem.
I am using a Samsung R530.

Heeeeeeelp I need my music!!!

---

### Post by coffeecat on 2012-05-07
> **Bigjack08 said:**
> before upgrading to the new Ubuntu 04/12

Do you mean Ubuntu 12.04? In 12.04, simply install Banshee. Banshee comes with an Amazon mp3 store plugin, in which you can browse the Amazon mp3 store, log into your Amazon account and Banshee will download your purchased mp3's automatically to your Music folder.

In fact you could do this in Banshee in 11.10 - you didn't need the Amazon downloader. Things were slightly better in 11.10 because you could use Banshee for both Amazon and the Ubuntu One store. In 12.04, you now have to use the default Rhythmbox for the Ubuntu One store, and Banshee for Amazon.

---

### Post by oldos2er on 2012-05-07
> **Bigjack08 said:**
> Heeeeeeelp I need my music!!!

Besides Banshee, there are a couple other alternatives:

[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by el_oscuro on 2012-05-26
To get it to install in 12.04, I installed the libboost-dev packages:

sudo apt-get install libboost-dev libboost-doc

---

### Post by foxy123 on 2012-07-22
> **el_oscuro said:**
> To get it to install in 12.04, I installed the libboost-dev packages:

sudo apt-get install libboost-dev libboost-doc

On 64bit I've got
```
~/Downloads$ sudo dpkg -i AmazonMP3DownloaderInstall.deb 
Selecting previously unselected package amazonmp3:i386.
(Reading database ... 339087 files and directories currently installed.)
Unpacking amazonmp3:i386 (from AmazonMP3DownloaderInstall.deb) ...
dpkg: dependency problems prevent configuration of amazonmp3:i386:
 amazonmp3:i386 depends on xdg-utils.
dpkg: error processing amazonmp3:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 amazonmp3:i386

```

although I have xdg-utils installed.

---

### Post by trindflo on 2012-09-22
This seems to be the thread talking about getting the Amazon downloader to work, although I have a later linux version.  I just got the Amazon downloader to work for 64-bit 12.04.  The missing piece is supplied by Jeff Wilson:
[http://blog.jeffalwilson.com/](http://blog.jeffalwilson.com/)
as a version of xdg-utils (xdg-utils_1.1.0~rc1-2ubuntu7_i386) with repaired headers so that it works as a "Multi-Arch" solution.  Jeff posted it here:
[https://docs.google.com/open?id=0B8M3gt9MySGrUnVocVpGVnZwM3M](https://docs.google.com/open?id=0B8M3gt9MySGrUnVocVpGVnZwM3M)

Once I installed that version of xdg-utils, the downloader would install and I could download music once again.

---

### Post by hic3456 on 2013-07-05
As far as I can tell, the Amazon MP3 "plugin" in Banshee is little more than a glorified browser to amazon.com and sure as hell doesn't let me to download anything to my system.

Or maybe I'm missing something, in which case it'd be nice, when posting "helpful" suggestions, to actually provide some guidance.

On a related topic, Amazon has now removed the .deb package from their download page: does anyone know how to get ahold of it?

Thanks in advance.

---

