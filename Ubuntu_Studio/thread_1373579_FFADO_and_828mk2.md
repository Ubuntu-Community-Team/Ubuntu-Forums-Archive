---
title: "FFADO and 828mk2"
date: 2010-01-05
forum: Ubuntu Studio
---

### Post by thediggler on 2010-01-05
Hello,
I'm trying to use my motu 828mk2 with ubuntu 9.10 which i believe has ffado installed by default. From what i've read on the net the 828 should work but i cant get anything on my asus laptop it doesnt seem to see it at all.

When i run "sudo ffado-test Discover" i get 
"Could not initialize device manager
14319340125: Fatal (devicemanager.cpp)[ 165] initialize: No firewire adapters (ports) found." which makes me think its not even seeing the ports which is strange because my external hhd works fine in the same ports.

I'm using a pci express card fw adapter with a Texas instruments chipset on an Asus F3j laptop ive tried the built in 4 pin port its exactly the same.

Really want to get this working been trying to get away from windows for years and this is my last real hurdle, don't really want to change sound cards as this one covers all my needs very well and has been reliable under heavy loads. Plus I'm sick of paying for cubase updates when even old issues are often ignored in favour of new features.
Any help would be really appreciated

---

### Post by gordintoronto on 2010-01-06
If you run Accesories/Terminal and enter the command:
lspci
any Firewire ports should show up.  That will at least confirm that Ubuntu sees the ports.  I'm sorry, I don't know what to do from there, other than trying Google, finding stuff like this: [http://osdir.com/ml/linux.drivers.freebob.devel/2007-06/msg00018.html](http://osdir.com/ml/linux.drivers.freebob.devel/2007-06/msg00018.html)

You might get a laugh from this: I was confused by your post, because in Ubuntuland a "motu" (Master Of The Universe) is a person who packages software to go into the repositories.  I had no idea it was a company name until I Googled "828mk2".  The device looks really cool.

---

### Post by thediggler on 2010-01-06
Thanks for the reply checked that link but I think hes using the older freebob driver and also it seems to relate to installing it, I think ffado is already part of ubuntu 9.10 having said that i'm not really an expert and could be totally wrong.
lspci gives me these references to iee1394:

04:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
05:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller

so its seeing the ports thats a start, don't know were to go from here been searching the net but can't find the same problem.
Any ideas?

---

### Post by AutoStatic on 2010-01-06
Hello thediggler, did you walk through this howto: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?

---

### Post by thediggler on 2010-01-06
Autostatic your a genius Thankyou, I now have a fully functional on screen mixer and after 5 minutes of tinkering i was able to play back a stereo track in Ardour. 

I'm getting heaps of x runs and the jack connection did terminate after maybe 5 minutes but I'm nearly there. Do I need to install the rt kernel for more stable performance? Not really that concerned about latency so long as its within reason, stability is my biggest issue.

Thanks so much really excited now I'd just about given up on the 828 ever working at all with linux hopefully just a matter of getting this jack setup right and i can delete windows.

---

### Post by thediggler on 2010-01-06
Just had another look at that walk though looks like i might need to install the rt kernel can I do this in ubuntu with out installing ubuntu studio?

---

### Post by trulan on 2010-01-06
You certainly can.  You can install it with synaptic, or apt-get, or whatever you prefer.  You will be able to choose which kernel you want to boot in your grub menu.

You will get better performance with the rt kernel and ffado, but it is not strictly necessary.  If you set your buffering high enough it should run OK.  But I'd install the rt kernel, I don't think you'll regret it.

---

### Post by thediggler on 2010-01-06
Thanks Trulan just installed the kernel and the ubuntustudio audio package with synaptic, ardour works great no xruns with 11 msecs latency. Tried running Hydrogen and jack crashes not sure whats happening there must be some setting not quite right any ideas?
Thanks again

---

### Post by AutoStatic on 2010-01-07
What are your current JACK settings? Could you post the content of your *.jackdrc* file? It's in your home directory (*/home/youraccount/.jackdrc*). It's a hidden file (prepended by a dot) so in Nautilus you might have to hit ctrl+h when you browse to your home directory so you can see it.
And I would really try installing the realtime kernel, it wil improve stability and enable you to lower the latency in JACK.

---

### Post by dawiba on 2010-01-07
> **thediggler said:**
> Tried running Hydrogen and jack crashes not sure whats happening there must be some setting not quite right any ideas?
Thanks again

I had a similar problem and this worked for me. In Hydrogen go to preferences, uncheck 'Connect to Default Output Pair' under the Audio System tab. Restart Jack. Make your own Hydrogen connections in Jack again and with any luck, you should be good to go.

Hope this helps.

---

### Post by thediggler on 2010-01-10
Thanks for the responses been away from my pc for a few days, 
dawiba thanks for the suggestion got hydrogen working hadn't realized you have to physically connect things in jack found that a bit confusing at first but its a cool idea very flexible.

Autostatic thanks, tried looking for my .jackdrc file strangely i cant find it, the closest i've got is .jamin don't know whats happening there?
I've installed the realtime kernel and your right its improved things heaps, Ardour and hydrogen seem stable havent tested many others yet.

Are there any good native sampler instrument plugins, have vsampler in windows wonder if there's an equivalent linux plugin.
cheers

---

### Post by AutoStatic on 2010-01-10
> **thediggler said:**
> Autostatic thanks, tried looking for my .jackdrc file strangely i cant find it, the closest i've got is .jamin don't know whats happening there?No idea, it should be there. It doesn't show up when you do a **ls -al $HOME | grep jack** ?

> **thediggler said:**
> Are there any good native sampler instrument plugins, have vsampler in windows wonder if there's an equivalent linux plugin.You could try Qsynth or LinuxSampler. With Qsynth you can use SoundFonts and for GigaStudio files you can use LinuxSampler. All the other fileformats mentioned on the vsampler site are unsupported (except for WAF and AIFF files). Qsynth can be installed with Synaptic. LinuxSampler is a bit more difficult, it's not in Synaptic because of it's license. But there are howto's around.

---

### Post by dawiba on 2010-01-10
This should make it easy to install Linuxsampler if you want to try it.

From the Linuxsampler site
> 
You should compile and install at least libgig and linuxsampler. As a beginner you should definitely as well compile and install a convenient GUI frontend like either qsampler or jsampler, whatever you prefer. qsampler depends on liblscp, so you have to compile and install liblscp before starting to build qsampler. Also if you like to be able to edit instruments, you should compile and install gigedit as well. The recommended order to compile and install is:

1. libgig
2. linuxsampler
3. gigedit
4. liblscp
5. qsampler


This is the [page to go to for downloads]("http://download.linuxsampler.org/packages/ubuntu/"). These are all .debs, so installation is really easy.

---

### Post by thediggler on 2010-01-10
Thanks for all the help guys, tried 
**ls -al $HOME | grep jack** and got this output
-rw-r--r--  1 derek derek       62 2010-01-10 21:21 .jackdrc
so its there but i still can't find it?
Will try linux sampler and qsynth I think qsynth might be good as vsampler can save in soundfont format.

---

### Post by thediggler on 2010-01-10
Sorry just found my .jackdrc file right in front of me i was looking for a folder don't know why. Anyway heres its contents:
**/usr/bin/jackd -p 128 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0 **

---

### Post by thediggler on 2010-01-10
Sorry again here it is after booting jack:
**/usr/bin/jackd -R -P70 -m -dfirewire -dhw:0 -r44100 -p256 -n2**

---

### Post by AutoStatic on 2010-01-11
Looks good to me.

@dawiba, the debs are for 8.04 32bit. Do they also work for 9.10? And you probably don't need Qsampler, Fantasia probably works better.

---

### Post by dawiba on 2010-01-11
[QUOTE="Autostatic"]@dawiba, the debs are for 8.04 32bit. Do they also work for 9.10? And you probably don't need Qsampler, Fantasia probably works better.[/QUOTE]

Works fine for me on this computer. I just assumed backwards compatibility. Qsampler is working just fine as a front end for me too :)

---

