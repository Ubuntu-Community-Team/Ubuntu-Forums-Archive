---
title: "Anyone using LinuxSampler here ?"
date: 2011-07-31
forum: Ubuntu Studio
---

### Post by fedexnman on 2011-07-31
I was kinda interested about LinuxSampler and came across this website . [http://wootangent.net/](http://wootangent.net/)            There is some cool stuff in there about synths , samplers , linux , ardour3, and lv2 plugins . And i can tell he uses Ubuntu .  Im really kind of interested in LinuxSampler and trying it out . I use Hydrogen for drum/sampler stuff and Ardour for tracking, but Im really curious about a synth or a more of a keyboard laid out type sampler, like the ones you'd find in popular Windows or Mac host . ex. Cubase's Halion sampler or Logics esx24 sampler  or even NI Kontackt .  What do you guys use for a sampler for linux ??

---

### Post by mwinthrop on 2011-07-31
I, too, am interested in using LinuxSampler.  My interest is because I would like to try the Sonatina Symphonic Orchestra or SSO ([http://sso.mattiaswestlund.net/](http://sso.mattiaswestlund.net/)), which is available now.  I am pretty new to Linux and Ubuntu Studio and I have been trying to figure out how to run LinuxSampler.  I have reviewed the web site you showed and several others in the Ubuntu Forum and come to the following conclusions:

1) There is a licensing concern that prevents the Ubuntu Studio folks from providing this program as part of the available Ubuntu Studio packages.
2) Compiling the program(s) from source or loading them from someone's PPA seems to require running Jack1 versus using Jack2.  Removing Jack 2 from Ubuntu Studio results in  other audio programs being deleted due to dependency issues.  I discovered this by trial and several errors.  After a while, I managed to recover to the original Ubuntu Studio setup (I think) - at least everything seems to be working again.
3) LinuxSampler seems to be the only piece of software that allows use of the SFZ format.

I did find an SF2 version of SSO and can load it in QSynth (a nice soundfont player that comes in the Ubuntu Studio setup), but there seemed to be soundfonts that produced sounds different from what I expected.  Not sure why that is.

Anyway, to summarize, I would like to try LinuxSampler, but I don't know how to do it without disrupting my current setup.  Hope I did not mess up the original question in this thread . . .

---

### Post by fedexnman on 2011-07-31
found another sampler but its linux vst  " discodsp's highlife " .  im interested in a sampler where you can open a wav file or loop wav in it and it maps it out all over the keyboard .  so each note youll hit on your midi keyboard will effect the speed and pitch that the wav or loop wav is played back at . i tried out  a linux app  called " specimen " today but  only got it to play one note on the midi keyboard . im scratchin my head on this one , but i know theres gotta be a sampler that does this ?

---

### Post by sgx on 2011-07-31
> **mwinthrop said:**
> I, too, am interested in using LinuxSampler.  My interest is because I would like to try the Sonatina Symphonic Orchestra or SSO 

Anyway, to summarize, I would like to try LinuxSampler, but I don't know how to do it without disrupting my current setup.  Hope I did not mess up the original question in this thread . . .

I would install a linux on a usbstick or external drive for general testing. And you'll want a separate drive for any serious sampler work anyway. You can go barebones, and add a few apps from debian testing/unstable, or install the ready-to-run distros that people usually recommend.
Cheers

---

### Post by Pablo_F on 2011-07-31
> i tried out a linux app called " specimen " today but only got it to play one note on the midi keyboard .

You have to select the pitch range to both sides of the central note, Click on the strip above the virtual piano keyboard. Depending on what side you are, you have to use button1 or button2. With button3 you select the central note.
> 
 im scratchin my head on this one , but i know theres gotta be a sampler that does this ? 
petri-foo is another one, based on specimen. I think that a recent version of hydrogen (with a piano roll) is also able to do this.

> there seemed to be soundfonts that produced sounds different from what I expected. Not sure why that is.
Just in case it has something to do: Make sure qsynth and jack sample rate is the same. 

> Compiling the program(s) from source... seems to require running Jack1 versus using Jack2
I am not so sure of this (did you try installing libjack-jackd2-dev as a linuxsampler build dependency, instead of libjack-dev?) In any case, jack1 works very well in US 11.04. 

Cheers, Pablo

---

### Post by fedexnman on 2011-07-31
Thanks ! gonna give " speciman " another go , and then check out petri-foo , thx for answering my post .

thx todd

---

### Post by mwinthrop on 2011-07-31
> I would install a linux on a usbstick or external drive for general testing.

Agreed - I purchased a usbstick and will work on putting Ubuntu Studio on it soon.

> Just in case it has something to do: Make sure qsynth and jack sample rate is the same. 

Thanks for the suggestion.  Tried your idea, but that was not the answer.  I should have been clearer on my statement (my fault for being vague!).  I downloaded SSO from [http://www.newgrounds.com/bbs/topic/1262167](http://www.newgrounds.com/bbs/topic/1262167).  I loaded the soundfonts one at a time into QSynth and used virtual keyboard to hear how they sound.  Some of them sounded O.K., but some like "Strings - 1st Violins Pizzicato" only play 3 notes a half step apart no matter where I played on the keyboard.  At first I wondered if there was something going on with QSynth or Virtual keyboard.  I also was wondering if there was something strange about the soundfont creating this.  Thinking about it some more and having run a test using my keyboard this time, I am guessing it has to do with the soundfont, but have not been able to check more yet because Swami SoundFont editor has a bug.  I also suspect that the SFZ format might play the sounds correctly, but have not been able to verify that.  Oh well, I will keep working on it.

> I am not so sure of this (did you try installing libjack-jackd2-dev as a  linuxsampler build dependency, instead of libjack-dev?) In any case,  jack1 works very well in US 11.04. 


I've seen information that says I need Jack1 (i.e. [http://ubuntuforums.org/archive/index.php/t-1634289.html](http://ubuntuforums.org/archive/index.php/t-1634289.html)).  I have not tried to compile LinuxSampler yet, but did try installing it from a PPA, once, resulting in the problems I had.  I purchased a memory stick and am going to try to make that boot Ubuntu Studio.  Then, I am going to try different ways to get LinuxSampler running, without goofing up my main system.  When I am more confident I understand the impacts, then I may try to put it on my main system, though it depends on what I learn in this process.

---

### Post by Pablo_F on 2011-08-01
> I've seen information that says I need Jack1 (i.e. [http://ubuntuforums.org/archive/inde...t-1634289.html](http://ubuntuforums.org/archive/inde...t-1634289.html)). I have not tried to compile LinuxSampler yet, but did try installing it from a PPA, once, resulting in the problems I had. I purchased a memory stick and am going to try to make that boot Ubuntu Studio. Then, I am going to try different ways to get LinuxSampler running, without goofing up my main system. When I am more confident I understand the impacts, then I may try to put it on my main system, though it depends on what I learn in this process. 

Thanks for the link and sorry if my words could have confused you. Well done and I hope the tests go fine!

By the way; 

[http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2](http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2)

---

### Post by mwinthrop on 2011-08-01
> Thanks for the link and sorry if my words could have confused you.No worries - I did not get confused.  I was hoping there was another way to make this work using Jack2 directly, but there does not seem to be one.  Thanks for the link on differences between Jack1 and Jack2.  It is helpful.

---

