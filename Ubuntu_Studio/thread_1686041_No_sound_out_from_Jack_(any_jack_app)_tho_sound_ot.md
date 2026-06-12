---
title: "No sound out from Jack (any jack app) tho sound otherwise works; plz help"
date: 2011-02-11
forum: Ubuntu Studio
---

### Post by youWho on 2011-02-11
Can somebody please help??!

I am using Ubuntu Studio Lucid. I'm  new to Ubuntu and I've been  installing and trying various apps, including quite an assortment of  simple audio file players; that might be relevant (don't know). Audio  output in general works fine. That is, I can play files with sweep for  example and basically any other app I've tried.

The problem is that although Jack runs, as far as I know just fine,  there's no audio output. If for example I play something in Ardour I can  see activity on the meters, but no matter what I try I get no sound.

To be  honest, I'm a little embarrassed to say that I don't actually  remember for sure whether Ardour (via Jack) was running before, but *do*  actually think so. If it stopped working then it must be due to a  software update perhaps???

But Linux audio is to me confusing and I don't know where to  start---could anybody help (I'd appreciate it)?? Thanks!  (Switched from  OS X.)

If I can post anything that would be a helpful place to start please let me know and I'll gladly do so.

---

### Post by Pablo_F on 2011-02-11
Hi, 

Make sure that jack is using the right interface (setup window of qjackctl, aka Jack Control). 

Make sure that your audio player is jack-aware (either by means of a jack output plugin or by default. For example, Aqualung just works when jack is up and running). 

Check the connections. For jack, "System" is the generic name of the audio card. You want, for example, aqualung's outputs connected to system: playbacks, normally 1 and 2.  

Last but not least, make sure that the hardware mixer of your card is OK (PCM, Master, maybe Front levels...). You can access it by means of a tool called "Alsa mixer". There is the CLI alsamixer, and also some graphic alsa mixers, for example gamix (software center).  

If you still have problems, please run the alsa-info script and show the message window of qjackctl. For the former, run this command from a terminal:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

upload and give the URL. 

Cheers, Pablo

---

### Post by youWho on 2011-02-12
Hi Pablo,

First, thanks for your kind help. I'm a little embarrassed that my post sounded so... desperate. It wasn't meant like that ;-). But it is true that I don't yet know my way around linux audio at all, and am feeling a bit overwhelmed trying to figure this out. So I appreciate your kindness.

Now, the odd thing is that I only now(!!) realize that the problem is more general than I had thought---the nutty thing is that I thought when I posted that request that audio in general was working---and literally a week ago I was using GWC to de-noise some files, which I was also playing with other apps too like I think sweep. But at the moment actually I get *no* sound out at all, contrary to my post. I've tried Audacity, Aqualung and Audacious, on the idea that they (I think) all use different audio output routing(?), and I get no sound from any of them. Also I only now realized that I get no "system alert" sounds (I hadn't realized that before because I often keep that muted).

In my limited (trying to learn fast :-) ) understanding, ALSA includes the basic driver that runs the hardware; if that's so then I should say that that should be fine---it was definitely working up until a short while ago. Beyond that I lose a sense of what goes on: I guess audio servers like Jack, PulseAudio or ESD handle the interface between the audio apps and ALSA, but I'm not sure if I'm understanding that correctly.

I rebooted and checked with the gui "GNOME ALSA Mixer" and all the faders are up and none of the channels are muted.

I could upload the output of alsa-info.sh to [www.alsa-project.org]("http://www.alsa-project.org") but I don't know how to do that. Should I run the script again with the --upload option??? Perhaps simpler would  be if I just post here relevant parts of that output if you wouldn't mind telling telling me what I should post.

Again thanks so much for your kindness.

Best,
Sam

---

### Post by youWho on 2011-02-12
An update:

I noticed that in the gui "Sound Preferences" dialog under the "Output" tab there was only 1 item: "High Definition Audio ... (HDMI)" though I thought there should be 2, one for the analog in/out there as well.

Also a few days ago I uninstalled Cinelerra (not because I didn't want it; only because the ppa had become non-functional and the newer installation hadn't worked; this is not relevant; just by way of explanation) ... it had been difficult to uninstall and perhaps that had taken something with it, I wonder.

Anyway so using Synaptic I reinstalled alsa-base; also I uninstalled alsa-oss, which is something I had installed a few days ago thinking it might be somehow useful. Now there are 2 items under the "Output" tab, and when I select "Internal Audio Analog Stereo" I again have "system alert" sounds, and Audacity and Audacious both play files, but still no sound from Jack applications via Jack.

I'll try some other things... any tips would be appreciated.

---

### Post by youWho on 2011-02-12
Huh. So it would seem that I've solved this. Thanks(!) to Pablo_F for kindly offering his expert advice, and so immediately too that I was amazed. Anyway  in the end the solution(s) seemed to be first the things I mentioned trying just above (reinstalling alsa-base, probably, and uninstalling alsa-oss possibly), then just now while futzing around with every little thing I could think of I happened to try simply connecting in the "Connect" window of JACK Control, the signal I'm trying to hear to the outputs "playback_3" and "playback_4", instead of 1 and 2, and it works!!

Who knew. I wouldn't have expected that to be the oh so simple solution,  but I'm glad it's solved.

Perhaps this helps some other folks?

---

### Post by Pablo_F on 2011-02-12
Cool. 

Please, what is the colour of the (hardware) minijack socket and can you give the output of the following command?

lspci |grep -i audio

?

Normally, the system: playbacks 1 and 2 correspond to the frontal stereo output. But each soundcard is different and it is hard to guess without info. 

As for the alsa-info script, don't worry, it is simpler than you thought. Just answer "y" to the question if you want to upload the results. Then a URL will be shown where your basic hardware-software audio configuration info is available to the world, yourself and possible helpers included. But, as the problem is solved, just leave it alone.

Note that Sound Preferences is a frontend gui for pulseaudio, which as you know is the default sound server in ubuntu. Jack doesn't care about settings in Sound Preferences but it does about the alsa mixer. 

Uninstalling alsa-base was not a good idea...

I am glad you solved it :)

Cheers, Pablo

---

### Post by youWho on 2011-02-13
Hi Pablo,

The minijack on the computer is black, and it has a little picture of headphones next to it. This is a Sony Vaio VPCF116FX by the way, if it's useful for you to know.

The output of "lspci |grep -i audio" is:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

By the way, when I got the computer there were some difficulties getting sound out working. Sorting that out I came across posts saying that this machine has a newer chip than the one that the ALSA driver was meant for. I think one of the issues was that this chip has 2 input pins and the previous one had 1, and that that's why nobody with this chip has both the internal mic and the external input. By defaut I think the external input works, the internal mic not---I say "I think" because actually I've never tested the external input (don't know whether it's line level or mic, I guess line level), but I can confirm that the internal mic has never worked. By the way that's basically  the only hardware that I've had a way to test that doesn't work on the machine, a testament to the wonderful work of the gnu/linux people I think. Anyway I do believe that the driver is due to be updated to accomodate this chip at version something like 2.6.36 of the kernal (I don't remember where I read that). You probably know all about this though, but in case not there's some info if it's useful to know. (Or are you one of the ALSA developers???) All by way of saying that perhaps this has bearing too on the fact that the outputs I should have been using were 3 and 4.

By the way I never intentionally uninstalled alsa-base. I meant to say this: I had to uninstall Cinelerra temporarily, or rather, I ended up doing that. I actually like Cinelerra a lot, but the ppa had stopped working, and so every time I did a software update there'd be this delay and then an error message to that effect, so I disabled that ppa, put a newer one in as per advice from the community version of Cinelerra's web site. But then Cinelerra wouldn't install properly, and since I figured I wouldn't need for a little while I'd just wait until perhaps that got sorted out, then try iinstalling it again later. Well, unfortunately neither Synaptic nor apt-get could uninstall Cinelerra, for reasons not clear to me, which was solved by deleting from /var/lib/dpkg/info these: "cinelerra.list", "cinelerra.postinst" and "cinelerra.postrm", after which it was possible to uninstall Cinelerra with Synaptic.

Then while pondering the audio problem it finally occurred to me that that elaborate process might have unwittingly damaged the audio, though it seems like it shouldn't have. As I mentioned, the other possibility I thought of was that it might have been the fact that I had installed alsa-oss; I did uninstall that, and that might actually be what fixed things. Hmm, I guess I could go install that again and see if it breaks again---do you want me to try that just to test???

Thanks for explaining that the "Sound Preferences" are actually only for PulseAudio. I don't know what to make of that. Perhaps then I actually *did* have JACK all along, and that only PulseAudio output had been broken, and just didn't know it because I never thought to try the other outputs in JACK.

Anyway thanks again, and sorry for the long post; only that if it's useful to you somehow---or helpful to others perhaps---you know.

Best,
Sam

---

### Post by Pablo_F on 2011-02-13
Hi, 

The black minijack socket corresponds normally to the rear stereo output in surround audio systems. You normally connect the speakers in the front output, which is usually the green one.

Jack sees the rear stereo as the third and fourth "system: playback" ports and the front stereo (green) as the first and second ones. 

Also, as you seem to have two audio interfaces, it is for your best that you tell jack to use the device named by name, not by number, as numbers sometimes get mixed up when you reboot the computer, resulting  in jack using the wrong audio interface and you don't knowing the reason why it worked and now it doesn't. This is frustrating for many jack beginners.

So, in Jack Control setup, interface field, write down (you won't see the option):

hw:Name

where Name is the name of the card you can see between square brackets in the terminal output of 

cat /proc/asound/cards

This could be hw:Intel or similar. Check your case and choose the right one. 

Yes, alsa developers are doing an incredible work supporting a huge number of different audio cards. And no, I am not one of them. I just like to read and experiment and offer help to beginners. Developers don't usually follow distro specific forums. There is an alsa user mailing list which they do read.

Cheers! Pablo

---

### Post by youWho on 2011-02-13
Hi 'gain,

Actually I don't have a green minijack at all, only a black one for output and a red input. But that's interesting to know.

Thanks for the tip re using a name instead of a number; I'll try that. By the way in my case the output was:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe8e00000 irq 36
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xe3080000 irq 16

(I tried to edit the title of this thread to better reflect what had happened in case anybody's searching and it might be useful; but it doesn't change the main title, only here... never mind. But this is still [SOLVED])

---

### Post by youWho on 2011-02-18
Just a short update to say that I reinstalled alsa-oss and everything is still working, so seemingly somehow my install of alsa-base had gotten corrupted. I don't know how. It *might* have had to do with the unusual steps I went through when trying to temporarily uninstall Cinelerra, though who knows. In case it helps anybody.

I'll definitely be re-installing Cinelerra soon; it's a nice video editor indeed. Installing it the first time there were no problems at all, by the way.

---

