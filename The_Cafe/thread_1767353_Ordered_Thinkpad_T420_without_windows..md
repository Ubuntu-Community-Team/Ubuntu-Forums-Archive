---
title: "Ordered Thinkpad T420 without windows."
date: 2011-05-25
forum: The Cafe
---

### Post by donniezazen on 2011-05-25
Just ordered Lenovo Thinkpad T420 without Windows. While the difference was worth stones but it just feels good to go completely Ubuntu.

This collegehumor line cracks me every time i think about it.
***
> Neo says,"Ubuntu, I am going to learn Ubuntu."
***

---

### Post by sanderd17 on 2011-05-25
I also searched a while to get a computer without Windows, and I finally got an Ahtec ( [http://www.ahtec.nl/](http://www.ahtec.nl/) , site is half dutch-half english). They don't ship to a lot of countries, but I felt great to be able to buy a computer without OS.

I later noticed that it are in fact debranded Qforce computers. Compare the two:

[http://www.ahtec.nl/product/espec/index.jsp?id=531](http://www.ahtec.nl/product/espec/index.jsp?id=531)
[http://q-force.be/dura-7520.htm](http://q-force.be/dura-7520.htm)

---

### Post by bjordan1979 on 2011-05-26
How in the world did you  pull that off? I've decided to get a Thinkpad T420 and I'd love to save cost and get it without an OS if possible but I haven't found an OS'less option yet.

---

### Post by donniezazen on 2011-05-26
> **bjordan1979 said:**
> How in the world did you  pull that off? I've decided to get a Thinkpad T420 and I'd love to save cost and get it without an OS if possible but I haven't found an OS'less option yet.

They were actually very polite about it. I called the sales department and asked if they could ship it with DOS. He waived off 35-40 bucks which not a lot compared to an i7 Thinkpad's price but i have a couple of Windows licenses that i get from my school. So, why pay for it and an OEM install comes with 100s of bloatware to slow it down.

---

### Post by NET WT on 2011-05-26
I thought Windows came free with new computers. Would there even be a discount?

---

### Post by angryfirelord on 2011-05-26
> **NET WT said:**
> I thought Windows came free with new computers. Would there even be a discount?
There's some, but generally the cost of Windows to OEMs isn't that big. It's not anywhere near the cost of a retail box of Windows. It's usually done more on a basis of principle than on cost savings.

---

### Post by abiswas on 2011-05-26
> **bjordan1979 said:**
> How in the world did you pull that off? I've decided to get a Thinkpad T420 and I'd love to save cost and get it without an OS if possible but I haven't found an OS'less option yet.
 
 
I got a thinkpad T420 just 2 days back in Switzerland. We can order it without windows and its 120 franks cheaper. Just loving it !!!

---

### Post by jhonan on 2011-05-26
> **soham_1207 said:**
> They were actually very polite about it. I called the sales department and asked if they could ship it with DOS.
DOS? As in DOS5.5 (or whatever it was) ? - I could just imagine them searching the storeroom for the DOS boot diskettes...

---

### Post by matthewbpt on 2011-05-26
> **soham_1207 said:**
> They were actually very polite about it. I called the sales department and asked if they could ship it with DOS. He waived off 35-40 bucks which not a lot compared to an i7 Thinkpad's price but i have a couple of Windows licenses that i get from my school. So, why pay for it and an OEM install comes with 100s of bloatware to slow it down.

Damn I should've thought of doing that! I bought a Thinkpad Edge 11, arrived last week and I'm loving it. Came with Win 7, but I also have free licenses available from my school, and I hardly use it anyway, just been using Ubuntu.

---

### Post by fetbec on 2011-06-02
> **matthewbpt said:**
> Damn I should've thought of doing that! I bought a Thinkpad Edge 11, arrived last week and I'm loving it. Came with Win 7, but I also have free licenses available from my school, and I hardly use it anyway, just been using Ubuntu.
Hi,
I bought a Thinkpad T420, arrived last week and Came with Win 7, so can somebody send me link to download Ubuntu certified for this model ?

---

### Post by sanderd17 on 2011-06-02
> **fetbec said:**
> Hi,
I bought a Thinkpad T420, arrived last week and Came with Win 7, so can somebody send me link to download Ubuntu certified for this model ?

All installations of Ubuntu use the same installation disk, it's found on the main page of the main Ubuntu site.

There is nothing as a "certified Ubuntu" for a computer. Just burn the iso, run the CD and see if it works. If it works, you can install it.

---

### Post by mejo on 2011-06-02
> **sanderd17 said:**
> All installations of Ubuntu use the same installation disk, it's found on the main page of the main Ubuntu site.

There is nothing as a "certified Ubuntu" for a computer. Just burn the iso, run the CD and see if it works. If it works, you can install it.

I assume your claims are right, but the page about ThinkPad T420[1] in 'Certified hardware' section of Ubuntu.com gives the impression, that such a certified Ubuntu does exist:

> Ubuntu releases:
     10.10 (Pre-installed only, with notes)and:

> **The [B]       Lenovo       Thinkpad T420     **     laptop     has been awarded the status of     **Certified**     on Ubuntu     PC (x86).[/B]

         **[B]Please note that for pre-installed systems:**[/B]

   1) _A special image of Ubuntu is available via the computer  manufacturer designed for this specific computer._ It takes advantage of  hardware features for these systems and may include proprietary software  and codecs. Please contact the computer manufacturer for access to that  specific Ubuntu operating system version.


   2) Standard images of Ubuntu may not work at all on this system or  may not work well. Canonical and computer manufacturers try to certify  all OEM systems with standard releases of Ubuntu, although we are not  yet there in 100% of cases.[1] [http://www.ubuntu.com/certification/hardware/201102-7230:201102-7315](http://www.ubuntu.com/certification/hardware/201102-7230:201102-7315)

---

### Post by Canime on 2011-06-02
UBUNTU UBUNTU UBUNTU! Clearly the best choice!

---

### Post by donniezazen on 2011-06-02
It would be interesting to see what works out of box. I hated Ubuntu when i need to install wireless driver for my old dell E1505 using ethernet. And latest driver doesn't work at all which forced me to use maverick version.

---

### Post by mejo on 2011-06-06
> **soham_1207 said:**
> It would be interesting to see what works out of box. I hated Ubuntu when i need to install wireless driver for my old dell E1505 using ethernet. And latest driver doesn't work at all which forced me to use maverick version.

for me, nearly everything worked out of the box with natty narwhal on my t420. here's a list (from memory) of issues i remember:

- need to disable nvidia optimus in BIOS. either choose internal intel graphics (saves power, satisfying for me) or discrete nvidia graphics. work is in progress though, to support optimus for linux. see [1].

- the fan runs all the time. you need to install thinkfan and manually add newer temperature sensors to its config file in order to make it work on the t420. See [2] (german) for further information

- battery lifetime was very short without tweaks. with integrated intel graphics, thinkfan running, and tlp installed and configured, i get up to 7,5 hours now.

- the microphone mute button doesn't work. didn't find a solution for that one yet. [3] [4]

- both speakers mute button and wireless hotbutton behave in an unexpected way. for the wireless hotbutton that seems to be a feature (see [5]), for the speakers mute button I hope a fix is found soon.

- issues with external monitor. regardless whether I use the docking station or directly plot my monitor into the vga connector, the screen is somehow broken and cluttered. hope this will be fixed with kernel & video driver update soon.

all in all I have to say that I'm pretty satisfied with ubuntu 11.04 on my t420, given that it's pretty new hardware.

also see the following thread: [http://ubuntuforums.org/showthread.php?p=10886666](http://ubuntuforums.org/showthread.php?p=10886666)

greetings,
 jonas

[1] [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
[2] [http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)
[3] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751471](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751471)
[4] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903)
[5] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773558)

---

### Post by donniezazen on 2011-06-06
> **mejo said:**
> for me, nearly everything worked out of the box with natty narwhal on my t420. here's a list (from memory) of issues i remember:

- need to disable nvidia optimus in BIOS. either choose internal intel graphics (saves power, satisfying for me) or discrete nvidia graphics. work is in progress though, to support optimus for linux. see [1].

- the fan runs all the time. you need to install thinkfan and manually add newer temperature sensors to its config file in order to make it work on the t420. See [2] (german) for further information

- battery lifetime was very short without tweaks. with integrated intel graphics, thinkfan running, and tlp installed and configured, i get up to 7,5 hours now.

- the microphone mute button doesn't work. didn't find a solution for that one yet. [3] [4]

- both speakers mute button and wireless hotbutton behave in an unexpected way. for the wireless hotbutton that seems to be a feature (see [5]), for the speakers mute button I hope a fix is found soon.

- issues with external monitor. regardless whether I use the docking station or directly plot my monitor into the vga connector, the screen is somehow broken and cluttered. hope this will be fixed with kernel & video driver update soon.

all in all I have to say that I'm pretty satisfied with ubuntu 11.04 on my t420, given that it's pretty new hardware.

also see the following thread: [http://ubuntuforums.org/showthread.php?p=10886666](http://ubuntuforums.org/showthread.php?p=10886666)

greetings,
 jonas

[1] [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
[2] [http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)
[3] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751471](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751471)
[4] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903)
[5] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773558)

Thanks,

The biggest up side was that wifi driver worked on its own which was a big trouble on Dell i had as bcmwl 100.x.x.x doesn't work at all. Yeah i had trouble with NVIDIA card but i figured out that optimus needed to be disabled. Nvidia doesn't play nice with brightness but their is a hack to enable it. Pretty much everything works.

I noticed this morning that it is an i7 DUAL-CORE machine not a quad-core. I don't know if it matters for my work. I am no video editor but will be encoding video and play latest games. I guess it should be fine.

---

### Post by boriolis on 2011-07-07
> **angryfirelord said:**
> There's some, but generally the cost of Windows to OEMs isn't that big. It's not anywhere near the cost of a retail box of Windows. It's usually done more on a basis of principle than on cost savings.



Here in India the difference is huge. The price difference of Thinkpad E420 with and without Windows 7 here is US $135 (on converting to US currency).

---

### Post by shobon on 2011-07-07
Ooo is this a Thinkpad thread? I think so.

I'm ordering a T60 later this week just for GNU/Linux. It'll be used so I don't think requesting it without Windows is worth anything, seeing as how I plan to format it the minute I open it.

---

### Post by Dustin2128 on 2011-07-07
> **jhonan said:**
> DOS? As in DOS5.5 (or whatever it was) ? - I could just imagine them searching the storeroom for the DOS boot diskettes...
It's usually FreeDOS, GPL'd drop in MS-DOS replacement. Don't see the point myself, on such powerful hardware.

---

### Post by donniezazen on 2011-07-07
Forty or Fifty bucks is not a huge difference so i would just but it with Win 7. Natty's performance is awful on this machine. I had to spend a whole day setting it up as i already had a licensed copy but drivers are a big mess. Then i found the Thinkpad Software updater which automatically downloads everything needed.

---

### Post by rewyllys on 2011-08-28
> **donniezazen said:**
> Forty or Fifty bucks is not a huge difference so i would just but it with Win 7. Natty's performance is awful on this machine. I had to spend a whole day setting it up as i already had a licensed copy but drivers are a big mess. Then i found the Thinkpad Software updater which automatically downloads everything needed.
What and where is this "Thinkpad Software updater"?  

Could you please provide a URL for it?  

Thanks.

---

### Post by donniezazen on 2011-08-28
> **rewyllys said:**
> What and where is this "Thinkpad Software updater"?  

Could you please provide a URL for it?  

Thanks.

[http://support.lenovo.com/en_CA/downloads/detail.page?LegacyDocID=TVSU-UPDATE](http://support.lenovo.com/en_CA/downloads/detail.page?LegacyDocID=TVSU-UPDATE)

---

### Post by keithpeter on 2011-08-28
> **shobon said:**
> I'm ordering a T60 later this week just for GNU/Linux. It'll be used so I don't think requesting it without Windows is worth anything, seeing as how I plan to format it the minute I open it.

If its like my T60 type 1952 you might need to research the 'thinkfan' fan control package. I had it working ok with 10.04 using these instructions...

[http://ubuntuforums.org/showthread.php?t=1586094](http://ubuntuforums.org/showthread.php?t=1586094)

but hopefully the thinkfan package has been updated since. in my case, the fan was coming on all the time (noisy but the safer option!)

Apart from that it was nice and fast.

Cheers

---

### Post by rewyllys on 2011-08-28
> **donniezazen said:**
> [http://support.lenovo.com/en_CA/downloads/detail.page?LegacyDocID=TVSU-UPDATE](http://support.lenovo.com/en_CA/downloads/detail.page?LegacyDocID=TVSU-UPDATE)

Donniezazen,

Many thanks for the URL.:popcorn:

It's encouraging to learn that Lenovo has such support for Linux.

---

### Post by donniezazen on 2011-08-28
> **rewyllys said:**
> Donniezazen,

Many thanks for the URL.:popcorn:

It's encouraging to learn that Lenovo has such support for Linux.

I am sorry. This is not for Linux but Windows 7. Most of the drivers for Linux come pre-installed. The only tweaks i had to do were get [thinkfan]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38") working, [TLP]("http://thinkpad-wiki.org/TLP_-_Stromspareinstellungen_fuer_Ubuntu") and patch boot line for [kernel power regression issues]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html#more").

---

### Post by rewyllys on 2011-08-29
> **donniezazen said:**
> I am sorry. This is not for Linux but Windows 7. Most of the drivers for Linux come pre-installed. The only tweaks i had to do were get [thinkfan]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38") working, [TLP]("http://thinkpad-wiki.org/TLP_-_Stromspareinstellungen_fuer_Ubuntu") and patch boot line for [kernel power regression issues]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html#more").
Thanks for the clarification.

---

### Post by Ferralll on 2012-07-08
I tried several times to call Lenovo and see if they would sell a T420 with just DOS, Ubuntu or even with out an OS.  

Each time, they clearly said no, and would not offer any extra incentive to buy (except a 10% discount that it seems they give to pretty much any one who asks) 

It is a shame.  I guess I will continue my search.  I just do not feel like forking over ~$80 for an OS that I will erase the day I get the computer.

---

### Post by angryfirelord on 2012-07-09
> **Ferralll said:**
> I tried several times to call Lenovo and see if they would sell a T420 with just DOS, Ubuntu or even with out an OS.  

Each time, they clearly said no, and would not offer any extra incentive to buy (except a 10% discount that it seems they give to pretty much any one who asks) 

It is a shame.  I guess I will continue my search.  I just do not feel like forking over ~$80 for an OS that I will erase the day I get the computer.
Well, you are and you aren't. One of the things computer manufacturers do to get prices lower is by bundling all that "junk" that you won't use. They also can get Windows at a lower rate than what the OEM disk sells for since they're selling a lot of it. If they took off Windows, it might actually be more expensive for them to manufacturer it.

---

