---
title: "music manipulation software."
date: 2010-05-23
forum: Ubuntu Studio
---

### Post by BorgCymru on 2010-05-23
While Ubuntu installs on my new laptop I thoughtb I would ask a few questions before I download all the wrong stuff :)

I'm looking for software to manipulate sounds.

I've seen Antraes Auto-Tune on youtube do some of the things I want. Auto correct and pitch correction.

I would like this to be used on recorded tracks and with live input to live output.

What should I look at downloading?

Thanks

---

### Post by linuxman94 on 2010-05-23
You might want to have a look at audacity.  It can do that and a whole much more.  Simply install it through Ubuntu Software Center in the applications menu.

---

### Post by sgx on 2010-05-23
> **BorgCymru said:**
> While Ubuntu installs on my new laptop I thoughtb I would ask a few questions before I download all the wrong stuff :)

I'm looking for software to manipulate sounds.

I've seen Antraes Auto-Tune on youtube do some of the things I want. Auto correct and pitch correction.

I would like this to be used on recorded tracks and with live input to live output.

What should I look at downloading?

Thanks

I use audacity daily, for several important functions, but not for what the you requested. Its speed and pitch shifting are primitive and unreliable. Tested just a few days ago. This is one area still requiring professional quality software. 

Someone may know a different linux alternative that works?

Whether the windows software in question will currently work in
wine/wineasio, I do not know. It is easy enough to try. Here is
a step-by-step that will yield the ability to use lots of windows
tools, and demo potential purchases. You will ne limited, but enjoy great functionality within those limits :)

---------------------------------------------------------------------------

Install wine and wineasio from synaptic, to
use Reaper, the daw that by far, works best with vsts in linux.
then run these commands from a terminal, after installing wine and wineasio. 

Open a terminal. $ is the user prompt, # is the root user prompt) 

wineprefixcreate    (this makes your windows file structure similar to this: /home/user/.wine/drive_c/Program Files  )

regsvr32 wineasio.dll   (this gets you an asio driver) 

The 'change directory' command is cd, so

cd /home/user/.wine/drive_c/Program*Files  (Note the * must fill all spaces in windows paths/titles that you use in commands. 

Now that you are at $Program Files, use mkdir to create these folders

mkdir Steinberg  then

cd Steinberg    then

mkdir VstPlugins

Now download and install Reaper to your
/home/user folder. 

[http://www.reaper.fm/download.php](http://www.reaper.fm/download.php) 

This is done by the simple command    wine name-of-installer

Now, install your vst collection, use installer defaults, .dll and .fxb files you can just copy to VstPlugins. I have installed a few NI demos, the service center works as it should, only Pace or ilok or dongleware plugins usually fail.

to start reaper, from a new terminal, first start jackd

jackd -d alsa -r 44100     then
 
wine reaper/reaper.exe

Now go to reaper prefs and configure as desired

wineasio will appear in its vst prefs Device page, and then you show reaper what folders to scan for plugins.

Then the typical daw learning-re-learning curve begins. In Reaper, right and left and middle click all widgets and empty spaces to reveal their popup dialogues, and of course the menu nests

Cheers

Linux apps,
 
qjackctl to connect the following:

zynaddsubfx and phasex synths
hydrogen drum machine/sample sequencer
rakarrack multi-fx, amazing+ used on the above 3 instruments
Timemachine for recording
Audacity to convert timemachine w64 to mp3, .wav etc

the rest can wait :) don't get bogged down, get recording!

---

### Post by BorgCymru on 2010-05-23
Bloody hell :?) that should fill the week up just doing all that :)

Thanks

PS: qjackctl   whats that mean ?

---

### Post by Bucky Ball on 2010-05-23
If you install the ubuntu studio audio you will get a whole lot of software to play with for sound.

Go to Synaptics Package Manager and search for ubuntu studio. Just install the audio and audio-plugins.

---

### Post by sgx on 2010-05-23
> **BorgCymru said:**
> Bloody hell :?) that should fill the week up just doing all that :)

Thanks

PS: qjackctl   whats that mean ?
Hi, its a nifty gui to configure and start jackd,
then connect your hardware and software together

It has Settings and Connect buttons to open its main pages.
The Connect page has 3 tabs, ignore the middle one.
Sound in the left tab, midi in the right tab.
Each tab has input on one side, output on the other.
click items you want to connect, then press the connect button
in this page, not the main page.

so a midi keyboard connects to your alsa midi-in
a software synth, connects to both your midi keyboard, and
your System audio-out.


The soft-synth output can first go to a multi-fx input if desired,
then that multifx output then goes to your System audio-out.
The end of the chain, or the various parts, can also go to
Timemachine recorder. 

zyn to rakarrack to System and Timemachine 
Hydrogen to System and Timemachine
Press timemachine record button (its the big one in the middle :)

youtube  has vids of ardour, hydrogen, zynaddsubfx, rakarrack,
and many cover qjackctl, because its the first step.

As for the how-2, its takes about 30 minutes, including download time.
Memorization is not required :) 
I tried to put it in a sensible order.
Cheers

---

### Post by BorgCymru on 2010-05-24
Sweet thanks.

I was also going to try auto-tune in wine, but its been a long time since I last used wine.

---

### Post by BorgCymru on 2010-05-24
Couldn't find wineasio in SPM, will apt-get get it ?

---

### Post by BorgCymru on 2010-05-24
> **Bucky Ball said:**
> If you install the ubuntu studio audio you will get a whole lot of software to play with for sound.

Go to Synaptics Package Manager and search for ubuntu studio. Just install the audio and audio-plugins.

OK did this, then looks in the sound menu. mmmm theres way to many things in there for me :) 

Is there any specific to the two things I'm looking for

Pitch control or what is now being called that T-Pain affect, although its been used long before him, and auto tune correction on voice ?

Thanks

---

### Post by KoRnholio on 2010-05-25
> **BorgCymru said:**
> OK did this, then looks in the sound menu. mmmm theres way to many things in there for me :) 

Is there any specific to the two things I'm looking for

Pitch control or what is now being called that T-Pain affect, although its been used long before him, and auto tune correction on voice ?

Thanks

The T-Pain effect is a vocoder, and there's a good page about free vocoder software here - [http://hubpages.com/hub/free-vocoder-software-download](http://hubpages.com/hub/free-vocoder-software-download)

All the ones it links to are VSTs, so you'll need the version of Ardour built with VST support, or just use LMMS (Linux MultiMedia Studio). LMMS is available from the Ubuntu repos, and is very easy to use. Ardour-VST might require adding a PPA or compiling it yourself, and its a bit more complicated and powerful than LMMS. I'd recommend trying LMMS first, and seeing how that goes.

Others will mention Reaper with Wine for VSTs, but I think that's silly when LMMS and Ardour-VST can use them just fine.

---

### Post by sgx on 2010-05-25
LMMS is very unstable compared to Reaper. VST support in linux programs
is very limited. I have never heard of anyone using ardour or anything else with 5 or 6 vsts, plus a few fx vsts in one instance of the linux app. The author of Ardour has made it clear that midi and vst support, is not the priority, excellent audio processing is. I'll be happy if any linux softwares can better the functions, speed, ease of use, and diminutive size of Reaper.
It is maintained by a small highly efficient commercial team of coders with a huge headstart.
 The linux coder has potential users in dozens of distros, many needing multiple window managers, with apps using various gui toolkits, different packaging formats, new kernels and patches, and a frothing cauldron of dependencies competing for inclusion in the big-name disrtibutions.
How do the coders keep sanity? Truly, an app like Rakarrack or Hydrogen is amazing both for excellence, and mere existance. :) 

Whats silly is to lead people down a garden path to problematic and inferior solutions, ones not even intended by their creators, to service the desires of the original poster. But it clearly is the purpose of the wine team to enable use of some windows software, and the purpose of the
reaper team to enable solid, affordable audio, midi, and vst plugin support in one package. But I doubt Antares Autotune will work in a current linux wine based Reaper. Probably 2 years away, based on the pace wine is moving at, which is actually quite rapid.
Cheers

---

### Post by Bucky Ball on 2010-05-25
> **sgx said:**
> LMMS is very unstable compared to Reaper. VST support in linux programs
is very limited. I have never heard of anyone using ardour or anything else with 5 or 6 vsts, plus a few fx vsts in one instance of the linux app. The author of Ardour has made it clear that midi and vst support, is not the priority, excellent audio processing is. I'll be happy if any linux softwares can better the functions, speed, ease of use, and diminutive size of Reaper.
It is maintained by a small highly efficient commercial team of coders with a huge headstart.
 The linux coder has potential users in dozens of distros, many needing multiple window managers, with apps using various gui toolkits, different packaging formats, new kernels and patches, and a frothing cauldron of dependencies competing for inclusion in the big-name disrtibutions.
How do the coders keep sanity? Truly, an app like Rakarrack or Hydrogen is amazing both for excellence, and mere existance. :) 

Whats silly is to lead people down a garden path to problematic and inferior solutions, ones not even intended by their creators, to service the desires of the original poster. But it clearly is the purpose of the wine team to enable use of some windows software, and the purpose of the
reaper team to enable solid, affordable audio, midi, and vst plugin support in one package. But I doubt Antares Autotune will work in a current linux wine based Reaper. Probably 2 years away, based on the pace wine is moving at, which is actually quite rapid.
Cheers

+1 Wise words. A dual boot cos nothing beats Pro-Tools, Sibelius, Reason, Ableton and a million other things pro-audio. Don't get me wrong. My Windows boot runs only this stuff. Everything else is done in Ubuntu which I love. Over christmas I will probably start experimenting with Windows as a VM in Ubuntu. That way, no having to boot into the other OS to use the best A/V software. I wish it wasn't like that but it is. Blame proprietory software, money market, Apple, whatever. Unfortunately it just is. Linux visual stuff is probably a leap ahead from Linux audio right now ... let's see what happens.

---

### Post by mango42 on 2010-05-25
[QUOTE="sgx"]...the purpose of the reaper team [is] to enable solid, affordable audio, midi, and vst plugin support in one package.[/QUOTE]

So, considering their incredibly fair trading policy, I don't understand why they don't offer a native Linux version, perhaps with DSSI & LV2 support instead of VST?

Quoting from one of their websites ( [http://reaper.fm/](http://reaper.fm/) )

> REAPER's 4MB download is smaller than some web pages. It contains no multi-gigabyte library of someone else's music, no crippled evaluation versions of a bunch of software somebody paid us to package, no arbitrary hardware or software restrictions and absolutely no invasive copy protection system.

Hear, hear and Amen for good luck.

On a side note, I have just 'discovered' FLAC ( [http://flac.sourceforge.net/index.html](http://flac.sourceforge.net/index.html) ) - all I can say is 'Wow - impressive! Why is this not a universal standard?'

---

### Post by Bucky Ball on 2010-05-25
Agreed. FLAC rocks. Like being in the orchestra pit!

---

### Post by BorgCymru on 2010-05-25
So back to windows it is then :(

Think I'll build a dedicated box for the sound programs and leave Ubuntu on the lappy as a lappy :)

Thanks

---

### Post by BorgCymru on 2010-05-25
Having a play with LMMS but when I hover my mouse pointer over the buttons the name takes pop out info boxes are empty.

---

### Post by sgx on 2010-05-25
> **BorgCymru said:**
> So back to windows it is then :(

Think I'll build a dedicated box for the sound programs and leave Ubuntu on the lappy as a lappy :)

Thanks
Hi, you can have both and more, on each computer if desired, traditional dual booting, a wubi install where ubuntu is installed like a windows app inside a windows partition, virtual machines, and bootable usbsticks for
various niche sysytems. So very few arbitrary limits remain! :) I agree that having a powerful desktop computer is welcome and sometimes necessary relief from the constraints of laptop technology.
Cheers

---

### Post by rlameiro on 2010-05-25
You have a kind of autotune plugin, its called autotalent.

[http://web.mit.edu/tbaran/www/autotalent.html](http://web.mit.edu/tbaran/www/autotalent.html)

there is also versions in VST and AU.

Sometimes, people just need to digg a little bit deeper :D

---

### Post by Bucky Ball on 2010-05-26
> **BorgCymru said:**
> So back to windows it is then :(

Think I'll build a dedicated box for the sound programs and leave Ubuntu on the lappy as a lappy :)

Thanks

That would be the go. Or at least a dedicated boot on the same machine rather than buying another box, unless you have one lurking about doing not much with specs that will make a DAW (digital audio workstation). Good luck.

---

### Post by mango42 on 2010-05-27
> **Bucky Ball said:**
> Agreed. FLAC rocks. Like being in the orchestra pit!

Almost - I reserve the virtual orchestra pit to good vinyl on an excellent player like the kit at [www.recordplayer.com](www.recordplayer.com)

---

### Post by Bucky Ball on 2010-05-27
Mango, you are missing something, because FLAC will pretty much reproduce vinyl at the correct compression, as in virtually none. This is the file type used by audiophiles everywhere to transfer their precious vinyl to digits.

---

### Post by KoRnholio on 2010-05-27
> **sgx said:**
>  I have never heard of anyone using ardour or anything else with 5 or 6 vsts, plus a few fx vsts in one instance of the linux app. 

From the original post, it just looks like he needs one vst plugin. Where are you getting 5-6 plus plugins?

I've personally had great results with VST instruments in Festige, and getting fed midi input from MuseScore or Rosegarden.  The vocoder VSTs should be plugins, not instruments, which should be even easier.

I'm all about using the right tool for the job. If I was trying to create a VST orchestra with effects, I might have to use Windows tools. But saying that he should use a Windows program to use one VST plugin is just ignoring the advances that have been made in Linux audio.

---

### Post by sgx on 2010-05-28
5 or 6 plugins plus some fx. is very common for small audio projects. People often go one of two ways, either lots of free and affordable favorite plugins, or a small number of expensive powerhouse name-brand instruments. You can use what you like, but ardour, rosegarden and dependencies are going to use minimum four times the diskspace compared
to Reaper, and bring in the considerable complexities inherent with needing multiple interfaces, while offering less efficiency. For someone new to the minefields of linux audio production, complexity is the last thing needed. 
 
Indeed, the Antares collection is high-end, but uses pace copy protection.
That may never work in linux, since pace has to stay ahead of pirates,
its probably too fast of a moving target. The various demos installed, but
refused to function in wine, as expected. The windows versions have a ten day free trial, and the various Autotune features were fun when used with
a couple choir sounds. 

I'm not into either/or campsites, preferring 'both, and more'. Arbitrary limits don't help musicians. One of my favorite instruments is zynaddsubfx, a world-class multi-timbral synth, with a powerful computer,
a lot can be done with just one instance, no vsts required at all :)
Cheers

---

### Post by Bucky Ball on 2010-05-28
> **sgx said:**
> 5 or 6 plugins plus some fx. is very common for small audio projects. People often go one of two ways, either lots of free and affordable favorite plugins, or a small number of expensive powerhouse name-brand instruments. You can use what you like, but ardour, rosegarden and dependencies are going to use minimum four times the diskspace compared
to Reaper, and bring in the considerable complexities inherent with needing multiple interfaces, while offering less efficiency. For someone new to the minefields of linux audio production, complexity is the last thing needed. 
 
Indeed, the Antares collection is high-end, but uses pace copy protection.
That may never work in linux, since pace has to stay ahead of pirates,
its probably too fast of a moving target. The various demos installed, but
refused to function in wine, as expected. The windows versions have a ten day free trial, and the various Autotune features were fun when used with
a couple choir sounds. 

I'm not into either/or campsites, preferring 'both, and more'. Arbitrary limits don't help musicians. One of my favorite instruments is zynaddsubfx, a world-class multi-timbral synth, with a powerful computer,
a lot can be done with just one instance, no vsts required at all :)
Cheers

+1 All good stuff. 5 or 6 vst plugins and effects I would consider normal. You can get there without really trying. As a musician, I would not want to have to stop and think about it too much. It's called creativity. Unfortunately, the way things are right not in the world of Linux audio, it's a maze and you're lucky if you can get anything working.

Not saying it's the developers fault, it has to do with money, not unlike a lot of the issues we wade through in a contemporary world.

---

### Post by thorgal on 2010-05-28
I can also guess that creativity could be boosted by technical constraints sometimes :)

---

### Post by cchhrriiss121212 on 2010-05-28
> **thorgal said:**
> I can also guess that creativity could be boosted by technical constraints sometimes :)
I agree, creativity is about making the most from what you have, as opposed to relying on vsts and plugins to bolster weak compositions.

> Unfortunately, the way things are right not in the world of Linux audio, it's a maze and you're lucky if you can get anything working.
If you are referring to unsupported hardware then I would agree, but if you research what cards are supported before you buy then it can be less painful. I don't think pulse helps much in this regard.

---

### Post by sgx on 2010-05-28
> **cchhrriiss121212 said:**
> I agree, creativity is about making the most from what you have, as opposed to relying on vsts and plugins to bolster weak compositions.


If you are referring to unsupported hardware then I would agree, but if you research what cards are supported before you buy then it can be less painful. I don't think pulse helps much in this regard. 

Mozart was recently quoted saying,
"weak composition transcends all technology".

One might follow your observation about creativity, and assume you ride to work on horseback, since bicycles and cars are newer. Or that
orchestras should utilize only primitive drums, instead of relying on violins and flutes to bolster weak rythym sections.
Cheers :)

---

### Post by thorgal on 2010-05-29
try not to confuse creativity and originality ;)

---

### Post by Bucky Ball on 2010-05-29
> **sgx said:**
> Mozart was recently ...

Recently? Which Mozart because the composer has been dead for quite some time now ... ;)

---

### Post by cchhrriiss121212 on 2010-05-29
I think I could have explained myself a bit better up there. I don't mean to say that vsts should not be used, or that new technology should be shunned. My comment on weak composition is referring to the dominant aspects of modern popular music, where the production techniques often outshine the music, which is not to my liking.

I think most of us would agree that the creativity depends upon the mind of the producer and not the tools he has become accustomed to.

---

### Post by sgx on 2010-05-29
> **thorgal said:**
> try not to confuse creativity and originality ;)
Ingenuity is the word that comes to mind when I think of
dealing with limitations and strengths of tools. Creativity is more to do with the limitations and strengths within our selves. Originality would
be the perceived results of our ingenuity and creativity. 

The aura of linux being a toolbox without locks, and the realities of
needing to piece things together that may be prepackaged in other
operating systems, (and often at a significant price), has great benefits. When others have thrown in the towel, and head for
Guitar Center, a linux user is likely to be putting on a fresh pot of coffee, and headed for the search engines.
Cheers

---

### Post by sgx on 2010-05-29
> **Bucky Ball said:**
> Recently? Which Mozart because the composer has been dead for quite some time now ... ;)
No, he heard some of my tunes, and began rolling over in his grave,
and then thought, f-this grave stuff, I've gotta go back and drive
a stake through the heart of Autotune, before its too late :twisted:
:guitar::guitar:

---

### Post by sgx on 2010-05-29
> **cchhrriiss121212 said:**
> I think I could have explained myself a bit better up there. I don't mean to say that vsts should not be used, or that new technology should be shunned. My comment on weak composition is referring to the dominant aspects of modern popular music, where the production techniques often outshine the music, which is not to my liking.

I think most of us would agree that the creativity depends upon the mind of the producer and not the tools he has become accustomed to.
Dude! You made Britney cry! :(  I think she needs a hug now. ;)

---

### Post by zettberlin on 2010-05-29
Back on topic people!

Why fumble around with autotune if you can get autotalent?

[http://web.mit.edu/tbaran/www/autotalent.html](http://web.mit.edu/tbaran/www/autotalent.html)

fine-tuned using the automation ardour offers it can do quite a useful job on bad intonation.
Yet as always not as good a job as only the one powertool to adress intonation-issues can do: the mighty "get some training and re-record." -method. ;-)


btw: For those of us really in love with higher maths: autotalent has parameters, that can be set to -0 Minus Zero, welcome to the 21st century!

---

### Post by sgx on 2010-05-29
This could be very useful as a ladspa effect in audacity. Using part of a sampled sax solo, perhaps one could feed it the 'wrong' data, to get some of the tonal imperfections/nuances back? Thanks for the link! :)

---

