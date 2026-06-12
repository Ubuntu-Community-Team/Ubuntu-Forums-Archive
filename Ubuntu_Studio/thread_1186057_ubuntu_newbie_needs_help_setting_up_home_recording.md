---
title: "ubuntu newbie needs help setting up home recording studio"
date: 2009-06-13
forum: Ubuntu Studio
---

### Post by extendedping on 2009-06-13
well I am making the switch away from windows (and fedora too buggy) and downloaded ubuntu studio last week. did not like it (apps minimized just disappeared I fixed it but it left a bad taste) so tried regular ubuntu and am amazed how sleek and easy it is. the only thing I now don't have that I had on windows is my cubase which I had version sl3. I was just learning it but when my computer bugged and I am not gong back to windows...so...here is what I am trying to do and here is what I have.

trying to:
record rock songs in a home studio. just me putting guitar, bass vocals and some sort of drum one piece at a time. 

have: cubase which I know I can't use
      presonus firepod which interfaced with my xp through firewire
      old (like 3 years) bfd drumming software
      dr rhythm 880 drum machine
      xoom effects pedal that connected to the firepod for guitar sounds.

so I want to duplicate the way I was doing thing before on cubase xp but now on ubuntu. what I was doing was multitrack recording using my zoop pedal into the firepod (and into the computer via firewire) for guitar/bass effects and just dragging in short drum loops from bfd then copying them  (cubase calls it duplicating)throughout the track and then adding drums fills cowbells (gotta have those) etc with the dr rhythm 880. the bfd shows up as something called a vst instrument in cubase.

so I need to know a bunch of things
1) what in plain terms is this "jack" audio and how can I make sure it starts (or is already started) when I start the recording app
2) if I am using the firepod as an external sound card (I read somewhere it works with linux unofficially) do I need kind of extensions to the kernel for recording due to latency issues? I read the ubuntu studio has a special kernel. I do need to have kvm working for virtual machines so anything that would mess that up would not be an option
3) to best replicate the way I was recording before would the adour or the rosegarden software be better? or if both are equally capable which do you like and why?
4)if bfd is not supported what drum software could be used? I read there is something called hydrogen anyone have experience with it?

thanks so much for reading this mouthful. though I had cubase for several years it was sitting there unused for almost all the time thus I only have a few weeks (or weekends I should say) experience recording so I am not exactly a whiz kid with the technology. 

again thanks for reading. this ubuntu is the real deal :)

---

### Post by trulan on 2009-06-13
Well, I'm a newbie as well.  First off, the firepod works with linux.  It's more work to get it set up properly, but it's way better once you do.  I'm not sure exactly what version of Ubuntu you are using, but here is basically what you should need:
 - A real time kernel (comes with Ubuntu Studio, can be installed in any Ubuntu)
 - FFADO drivers
 - JACK
 - Ardour (instead of Cubase - I haven't tried Rosegarden but I'm really liking Ardour)
 - a drum machine (which I know nothing about - I hear a lot of good stuff about Hydrogen)

Here's a pretty good general how-to for setting things up.  This should answer your questions about latency and such:
[https://help.ubuntu.com/community/UbuntuStudioPreparation?highlight=(\bCategoryAudio\b]("https://help.ubuntu.com/community/UbuntuStudioPreparation?highlight=%28%5CbCategoryAudio%5Cb"))
Some of it is over my head, but the firewire section, and the real-time sections are pretty understandable.

Here's another page with a lot of info:
[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Be aware, when reading stuff on the web, that most of the info out there is at least a little bit out of date.  (both the links I gave are out of date too in some ways)

I haven't gotten much beyond Ardour yet, as far as software goes.  But Ardour is great, you should be fine with it if you're used to cubase.

---

### Post by extendedping on 2009-06-13
thanks for the links, i took the 2 ubuntu studio packages from the second link as suggested (just for audio) and installed the real time kernel. now my only issue is I can't use my kvm machines...always something right?

---

### Post by trulan on 2009-06-13
So you're saying you can't run a virtual machine with the real time kernel?  I was intending to mess around with that when I get the time, but I was searching just now and didn't come up with much.  You would think there would have to be a way...

---

### Post by extendedping on 2009-06-14
I am certainly no expert but it did not work for me. I also posted on the studio 64 forum to see if they knew since that is a dedicated platform but nobody answered back. so since I need the virtual machine more then the music I am sticking to to regular kernel and seeing if I can get my firepod working and how slow it is. too bad, if the kernal ran the vm's I would really be able to make a total break from windows. :(

---

### Post by kayosiii on 2009-06-15
Well you can choose to run a regular kernel or the realtime one at startup. So as long as you don't need the VM and audio as the same time you should be ok.

The non Realtime Kernel for Jaunty is working fine for me here... You just won't be getting as good latencies. I am using an FP10 here. Earlier non RT kernels weren't so good for me.

---

