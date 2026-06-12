---
title: "New machine build, quote, teaching qualification"
date: 2012-09-26
forum: Ubuntu Studio
---

### Post by darkvoid86 on 2012-09-26
Hey there guys, I am about to start my post grad to become a teacher and have been using ubuntu for the last three years to much success.  I am currently filling in my career development loan forms and I wanted to include getting a new pc as an expense.  This computer is to be used for:

1.  Producing music 
2.  Gaming
3.  General use

My budget is £2,000 and I know that things aren't cheap over here in the UK.  My questions/need for help is:

1.  What is the divide between the best of audio production software between Ubuntu and Windows?  (I haven't had a go with it so far simply because my computer just is that old and not built for such tasks.  My Uni also uses Apple exclusively and that is my only experience, I just happen to loath Apple and the best I am willing to compromise is Windows, which I would have to for the sake of modern gaming any ways.....)

2.  Is it best to get an external sound card or internal?

3.  I am confident with building the computer because I used to help my dad with such things growing up (it has been a reeeeally long time though).  Can anyone help me out with some specs and save me trawling through reading tons of articles on what is going in/out/value for money etc?  Compatibility issues with Ubuntu are something that worry me, especially considering the high demands I want to put on the machine.

Any help, advice, information etc. would be extremely useful.

---

### Post by fedexnman on 2012-09-26
Well you can dual-boot Windows7 ( OEM VERSION IS $99 )and UbuntuStudio on the same machine whether it be  PC or Mac , thats what I do on my PC.   The best of both worlds free and un free . I have a firewire sound card, but I  recommend going with a PCI or PCI-e sound card . RME makes the good " PRO " Quality and M-audio are good and known to work well for on a budget .  Google ALSA for compatible stuff .   Google ubuntustudio prep  , and learn about Jackd and qjackctrl .  :guitar:

---

### Post by jejeman on 2012-09-26
If you want to play computer games than you will need windows. And also because of that you will need more stronger graphic card. I always go for Nvidia because of Ubuntu, and at the moment I have GTX560-Ti which is working all right. This card is strong enough for modern games and it is middle range priced. If you can afford go for stronger.

For the rest of the PC I don't know 2000£ is a lot in my country, and for that I could buy all the latest hardware.(Which is, of course, not good for Ubuntu ;))
I would go for:
Intel CPU - i3 and above
Intel chipset on the highend motherboard from 2011.
At least 4GB of RAM DDR3 1600

Just make shure not to buy hardware from 2012, or you can, but then you'll need to use Ubuntu 12.10 or 13.04.
>  2. Is it best to get an external sound card or internal?Not a crucial differance. Crucial is - is it supported.
I have Edirol FA66 and it's working good. But card it self is not all, you need also good Monitor Speakers, good room to work in etc.

Software

If you are not willing or don't have time to learn go for windows and Entry level audio software. Or something speciffic depending on the music you make.
For Audio production in Ubuntu Studio you will need couple of months of hard work to learn and get things going.

Personally, now after couple of years, I don't see any problem in doing Audio production with FLOSS or to be inferior to comercial software.
The main difference is that professional softwer can be more efficiant, and supports more hardware, doesn't require much knowledge of audio production -> preset ready. ;)
I'm speaking, of course, from perspective of the small studio/home producer.

Good luck.

---

### Post by Lars Noodén on 2012-09-26
Have you looked at [Ardour](http://ardour.org/) yet?  I think that may be your main choice on the good side of things.  That's the one I've read most about.  The list seems to have grown of late and include Rosegarden and Qtractor.  All three are in the repositories, so it will be easy to try them out on the equipment you currently have.

---

### Post by CrocoDuck on 2012-09-26
Hi. _In my opinion_ the main difference between commercial and open source software is that any open source program is born to solve a precise task. Those programs are not written with the main goal to being sold in mind, that implies that they are scientifical and maybe less user friendly, but very powerful and accurate. I like them so much because I don't have to dial with "advertising presets" (the way I call preset and programs that wants to impose to me a commercially-blended tone): open source lets me to be crative. When I have a sound in mind I can bring it to life without being distracted. It also make me learning a lot of informatics, electronics, music and acoustic well together. Of course, audio commercial software for linux actually exists and it could be cool for you. _In my opinion_, al last: everything you can do with commercial software you can do with open source too. Things that you can immagine and do with open source sometimes are hard to do with commercial. I recommend to have a try with dual boot, so you will notice the difference and will be able to choose the software that really fits your needs.

Probably a PCI card is better, but if you mount a silent power supply into your computer: an internal soundcard will catch the electromagnetic noise produced by computer components, mostly the noise from power supply (I cleary hear the difference, as I have both internal and external soundcards). Remember to check the compatibility for all the hardware. ALSA and FFADO are the reference projects for audio devices.

I'm sorry for my bad english, but I'm not a native speaker...

P.S.: If you want to run video games for windows, dual boot is the best choice.

---

### Post by darkvoid86 on 2012-09-27
Hey there guys, thanks for all the helpful advice.

I am currently now looking at external sound cards from RME.  From what research I did a couple of years ago, they seem like a company that offers super high end quality before you get that massive hike in price for not much more performance (I was previously looking at getting a fireface800).  People often talk about USB vs firewire and we know the obvious choice in that realm, however PCI is surely the best and runs at easily the lowest latency?

I have come across the RME Multiface II, anyone have any thoughts or experiences? (this so far seems to be the logical option over the fireface 800)  However I went to the following link after a couple of people's suggestions:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-RME](http://www.alsa-project.org/main/index.php/Matrix:Vendor-RME)

Does this mean that the multi-face II isn't supported? :(

As for monitors I believe that I previously researched the Adam a7x as a good option for money as it also had the sub woofer (among other things I like metal and low end is an important frequency for me).  Still a good option?

Can I get away with 4gb of RAM for the moment or is it not worth really hanging around and just going straight up to say 16gb?

Checking out Nvidia graphics cards, good ideas so far and definitely the top choice for compatibility.

As for mother boards I am reading that ASUS doesn't seem to be liking Linux these days.  From what reading I have done so far, are Intel motherboards the way to go?

For a case, I found an article that endorses this fractal audio case, thoughts?

[http://www.amazon.co.uk/Silverstone-SST-PS06B-A-USB-3-0-Precision/dp/B005XM0QWW/ref=sr_1_1?s=computers&ie=UTF8&qid=1348747562&sr=1-1](http://www.amazon.co.uk/Silverstone-SST-PS06B-A-USB-3-0-Precision/dp/B005XM0QWW/ref=sr_1_1?s=computers&ie=UTF8&qid=1348747562&sr=1-1)

---

### Post by Sylos on 2012-09-27
A little cautionary warning for you on the PCI card front:

Some (I dont think all) of the intel chipset mobos that take the i series chips dont provide a proper PCI controller - its bridged onto the pci-e with some special chip. The upshot is that people have reproted that the throughput is not as high as it should be. Ok for people fiddling with consumer level cards but for anything approaching the professional level it can be a problem. You can see some chatter about it on the RME forums.

I have had problems with an i5 running on a Gigabyte GA-z68APd3 board. Took ages to figure out that I can only register my soundcard when I have both PCI slots filled (I installed an old soundblaster alongside my Maudio Delta 66 that I use) and even then I have to blacklist the soundblaster kernel module because if I dont the two cards are given the same HW ID number.

I never figure out why this happens (only that it didnt happen on a friends higher end z68 mobo).

So, my advice: Dont buy the same mobo as me. And be careful with pro cards on the i series mobos - cos that problem affects windows and linux.

Cheers

---

### Post by fedexnman on 2012-09-27
+1 on gigabyte mobo  -  make sure you get one with firewire (ieee 1394 ) if you decide to go that route later.

1. memory  is dirt cheap 4gb is fine but 8gb ram is not gonna cost much more these days .
 
+1 on RME make sure you follow that ALSA page and do your research, google !! 

+1 on Nvidia graphics cards , get a decent one if $100 -$200 if your gonna game .

2. Things you dont need but are nice are some extra hardrives . - I have 3 . I use  1- 60 gb SSD for my Windows7 OS  , I have a 2 HDD 7200rpm,  1 for samples 1 for music projects . one of the HDDs has my linux partition  for Ubuntu on it .   SSD are not really needed , but are nice to have for Windows7 .  You still would be fine with 1 HDD too .

 3. Im fine using a firewire audio interface , but I have to use LXDE ,  XFCE , or the Enlightenment desktop environments  . If I use gnome3 or Unity my system locks up and I get xruns with Qjackctrl or jackd .  I have an Echo audiofire4  . Google FFADO for compatible stuff.  Its works great but Id love to have something PCI or PCI-e by RME ,  I've heard nothing but good things about RME .

4. You don't need the latest and greatest most expensive CPU or mobo with a lot of bells and whistles to run Linux on it . So don't break the bank  .

5. Its gonna take a little more homework than windows or mac , to get it up, but it works and is free .   Ardour is a great audio multi-tracker DAW , Hydrogen is great for drum samples  you can make realistic acoustic kits with it and record it with Ardour  to the grid or manually with a midi controller . Specimen is a cool sampler /synth that you can use one WAV sample or loop and make a synth out of . You can record it with Ardour , you have to hook it all together with QJackctrl ( jack )  and its patchbay . Thats the Linux way in a nut shell , you will be wiring apps together , kinda like rewire on mac and windows .  

6. You record metal , if you dont have a drummer you can make a great Hydrogen kit with these samples .  [http://rekkerd.org/nsa-custom-series-drumkit-free-acoustic-drumkit-samples-by-dean-aka-nekro/](http://rekkerd.org/nsa-custom-series-drumkit-free-acoustic-drumkit-samples-by-dean-aka-nekro/)    FREE !  alls you need is a cheap midi keyboard an do some time and research .

---

### Post by CrocoDuck on 2012-09-27
If my memory serves me, at T-Rex studios an RME Multiface II is used with Ubuntu Studio... but their website ([http://trexstudio.com/](http://trexstudio.com/)) is changed and I can't find the page where it was written... I'm sorry if I stress on this point, but buy a soundcard only if you have a precise idea on how to make it working (even if is just plug 'n' play). Sometimes devices that not figures in the ALSA matrix actually works. So google around and take note of issues, pros, cons and other people experience. If you can, find someone with that hardware and test it with a live iso (sometimes I act like this at shops... using a bootable media like a shuriken:p).

Talking about monitors: they have to be as linear as possible. In fact, most of monitors are produced with a frequency response that emphasises some bands and frequencies, in order to give to the sound a tone that is characteristic of the brand. Brands are usually put their tone into electronics and acoustic of the monitors. This happens with guitar amplifiers too: a mesa boogie is different from fender, that is different from peavy etc...etc... But this isn't good for recording, mixing and mastering: you have to hear the sound without any band boosted. You have to hear exactly what you have recorded, in order to improve bass if they aren't enough or bring down treeble if they are too much. Mixing and mastering with a monitor that has too much response on bass frequencies implies that when you'll listen your record in a stereo with a moderate response it will be like all the bass frequencies were cut off! If a song sound good with linear monitors, then will sound good with all kind of monitors. Vice versa is mostly false. Important is also the room where you are going to use your monitors. In fact reflections of the waves on the walls and resonances are usually modify the spectrum you hear. The frequencies that are emphasized or extincted depend on the shape of the room.  Of course, the perfect building of a room is for professionals only. But for us (hobbist or semi-porfessional) a compromise actually exists:

Try to get monitors with a good linear response. You have to find graphs that shows amplitude vs frequency: db has to vary as little as possible in the spectrum (+/- 1 db from 20 Hz to 20 Khz is very good). Phase response is also very important, as it implies the detail of the stereo image. Another important parameter: THD (total harmonic distortion). THD has to be less (I suggest very less) than 1% .

The best shape for a mixing-mastering room is rectangular, avoid 2x1 proportions.

Here some reading and tools you could find very useful:

[http://mastering-media.blogspot.it/2008/05/diy-mastering-part-3-mastering-speakers.html](http://mastering-media.blogspot.it/2008/05/diy-mastering-part-3-mastering-speakers.html)

[http://mastering-media.blogspot.it/2008/04/diy-mastering-part-3-room-acoustics.html](http://mastering-media.blogspot.it/2008/04/diy-mastering-part-3-room-acoustics.html)

[http://www.hometracked.com/2008/01/25/quick-home-studio-monitor-tests/](http://www.hometracked.com/2008/01/25/quick-home-studio-monitor-tests/)

---

### Post by sgx on 2012-09-27
> **darkvoid86 said:**
> Hey there guys, I am about to start 


1.  Producing music 
2.  Gaming
3.  General use

Any help, advice, information etc. would be extremely useful.
Reaper is the daw that runs in linux, mac and win,
so that might simplify your interactions at school, and using it in
linux with wine and wineasio, allows a world of vst plugins within linux.

Ardour is mac and linux, and has a windows alpha release.
It is designed for the highest signal quality, and to be used safely
in complex or massive scenarios, which doesn't lesson it's value
to mere mortals. I use an maudio 24/96 pci and nvidia video card for many moons,
with only an occasional problem, almost always self inflicted ;)
Reaper outputs in qjackctl, can be directed to any
linux software with available inputs.

Test your mixes on a car stereo, portable mp3 player with
average earbuds, and a typical home theater setup.

The U-he synth collection, and most of the
Native Instruments Komplete package, works well in Reaper wineasio,
and are considered world class in quality, and are native in both
windows and Mac. There a dozen great linux instruments and fx,
that make a great sonic foundation, so softwsare synth purchases
may be for fun, instead of necessity.

links 4 and 8 at this wiki, will help to set up and configure
jackd and qjackctl, lots of youtube vids as well.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)
Cheers

---

