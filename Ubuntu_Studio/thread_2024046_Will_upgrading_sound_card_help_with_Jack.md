---
title: "Will upgrading sound card help with Jack?"
date: 2012-07-13
forum: Ubuntu Studio
---

### Post by Hoff123 on 2012-07-13
Hi! I was using Arch Linux and was trying to setup Jack. But, no matter what I could not do it. I asked about it here a while ago: [http://www.linuxquestions.org/questions/linux-software-2/jack-jackd-doesnt-work-have-tried-everything-935321/](http://www.linuxquestions.org/questions/linux-software-2/jack-jackd-doesnt-work-have-tried-everything-935321/)

Anyway, now I am dual booting Arch and Ubuntu Studio, and at least Jack works now, but I still have some problems. First of all if I run Jack any lower than 1024 Frames/Period I immediately get a lot of Xruns and after a while I have A LOT of them. If I run higher than 1024(eg. 2048) Frames/Period Jack doesn't even start. So now I run at 1024 and I have no Xruns when I start Jack but the more programs I run and the longer I run Jack, the more Xruns starts to appear. Also some programs doesn't seem to work very well together. For example I was running Hydrogen and Qtractor at the same time and for some weird reason the stop button in Hydrogen didn't work AND I could not change the BPM. But as soon as I closed Qtractor everything worked again. Maybe that has do to with something else, but I don't know.

OK, at the "Jack FAQ" it says that Jack supports ALL ALSA cards and I can KIND OF run Jack, but with a lot of problems and only in Ubuntu Studio. Right now I am using an intergrated card(som kind of HDA ATI sound card or something) and I suppose that buying a REAL card would help. What do you think? Would it help?

PS: Yes I know about Jack and PulseAudio not working very well together, but if I got another card, couldn't I use the integrated for PulseAudio and the new one for Jack?

---

### Post by Sylos on 2012-07-13
Hello there.

Could you clarify a few things.

1. Are you now dual booting properly or is Ubuntu Sudio still in Virtualbox?
2. What specs is the PC (ram cpu etc).
3. What kernal are you using?
4. Are you using realtime?
5. Are the Xruns audible?

On a general note, having a better soundcard will give you performance benefits. But I dont see why you should be having such problems just doing basic stuff with an onboard card. It should work without Xruns when your only handling a few tracks (non-intensive stuff). Maybe check your interrupts to see if its getting a low IRQ number:

```
cat /proc/interrupts
```

Also try switching off your wireless (if you have it) as wireless polling can cause Xruns I believe.

Cheers

---

### Post by Hoff123 on 2012-07-13
OK, so first of all I use a desktop pc with NO wireless(using a cable that runs all around the house...lol).

And no, I'm not using Virtualbox. it is normal dual booting(well 2 Linux distros and no Windows, but whatever). 

Partitions:
* One primary for Arch root(ext4)
* One primary for Arch home(ext4)
* One primary for Arch boot(ext2)
* Extended partition 
       * One logical for Ubuntu Studio 12.04(ext4)
       * One logical for swap

Using Grub2 in both Ubuntu Studio and Arch(it uses Arch's grub, but it's the same)


Specs:
Motherboard: ASUS M4A78LTM_LE [http://www.asus.se/Motherboards/AMD_AM3/M4A78LTM_LE](http://www.asus.se/Motherboards/AMD_AM3/M4A78LTM_LE)
Processor: AMD Athlon II X2 250
RAM: 4(2X2)GB DDR3 1333 RAM
Graphics Card: AMD Radeon HD 5450


Kernel? Always newest possible(that is not "testing", beta or something else).
At least version 3. I update both Arch and Ubuntu Studio very often and I have had this problem for ever basically(but I am kind of new to making music and such, so a few months).


Realtime? Yeah. Well in Ubuntu Studio at least. And doesn't 12.04 come with a realtime kernel?


Audible? Well you mean if I get problems that are actually noticable. Well...OK, I am kind of a noob at this stuff, but I can see the QJackCtl icon getting red and getting more and more Xruns, all the time(but it depends on the programs I use). So, no. Not at the moment, I don't think I have noticed something.


And this is what I get when I run "cat /proc/interrupts"
```
         CPU0       CPU1       
  0:         47          0   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          1          4   IO-APIC-edge      i8042
 14:         93      18797   IO-APIC-edge      pata_atiixp
 15:        171      38434   IO-APIC-edge      pata_atiixp
 16:        381     113051   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb3, snd_hda_intel
 17:          0          3   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          0          3   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb5, ohci_hcd:usb6
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb7
 22:          0          0   IO-APIC-fasteoi   ahci
 42:          0         60   PCI-MSI-edge      snd_hda_intel
 43:        508      82252   PCI-MSI-edge      eth0
 44:       1775     720883   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
NMI:         54         56   Non-maskable interrupts
LOC:    1006392     978097   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:         54         56   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RTR:          0          0   APIC ICR read retries
RES:    2003571    1858876   Rescheduling interrupts
CAL:       1468       2181   Function call interrupts
TLB:      48046      30645   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         33         33   Machine check polls
ERR:          1
MIS:          0
```But right now I am using Arch Linux, so some things may be different In Ubuntu Studio...I'll come back.


EDIT Here it is in Ubuntu Studio but it looks about the same:
           ```
CPU0       CPU1       
  0:        122          1   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          1          4   IO-APIC-edge      i8042
 14:         48        199   IO-APIC-edge      pata_atiixp
 15:          7       5717   IO-APIC-edge      pata_atiixp
 16:        904       1281   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, snd_hda_intel
 17:          0          3   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          0          3   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 22:          0          0   IO-APIC-fasteoi   ahci
 42:          0         59   PCI-MSI-edge      snd_hda_intel
 43:        470         74   PCI-MSI-edge      eth0
 44:          6       7312   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
NMI:          0          0   Non-maskable interrupts
LOC:      48681      48510   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:      21083      15955   Rescheduling interrupts
CAL:        808        273   Function call interrupts
TLB:        407        391   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0
```

---

### Post by Sylos on 2012-07-14
Hello there.

Thanks for the additional info.

The first thing to note from your /interrupts output is this line:

```
 42:          0         59   PCI-MSI-edge      snd_hda_intel
```

This is your soundcard it would appear. As far as I know the first number is its interrupt (IRQ) number. High value = bad  - Low value = good. Sadly its difficult to change. If I remember correctly - only IRQs 1 to 15 are actually hard wired from CPU (Have independent lanes) anything above 15 is virtual which means it has to fight with other devices/controllers to talk to your CPU. This delay can cause your Xruns.

That being said - your card is being run on MSI (message signalled interrupts) which is supposed to help alleviate the problem. 

As far as Xruns go - heres a basic idea. They can be caused by a number of things but they are only a problem when they cause real world issues - like your apps disconnect from the sound server or you hear audible pops, clicks, scratches etc. If you dont get these real world issues then Xruns arent a problem. I get at least one when I start any additional sound app. As long as Im not recording at the time it isnt a problem. 

So - recomendations - I would say go into your BIOS and turn off everything you can whilst still leaving a bootable system. That means USB and USB 3 Controllers etc and see if it improves. I would try turning off your ethernet for testing purposes as well (its also on MSI so could possibly be interfering). If you find that turning one thing off makes a big difference then you can possibly find a way around it. If your ethernet card is the problem then buying a PCI ethernet card is way cheaper than buying a decent sound card.

Sorry I cant give a more techy solution but Im hardly a wizard and most of the time these things are trial and error. Just in case though - could you post a screenshot of your Jack Settings window to see if there are any issues there.


Cheers

---

### Post by Hoff123 on 2012-07-14
So first of all I disabled everything in BIOS and it seemed Jack worked better(both in Arch and Ubuntu Studio). Then I reverted all settings to the default settings(there was an option in BIOS to do that). Everything still seemed to work OK. And then I remembered that I had enabled "hardware virtualization" a while ago because I wanted to be able to use 64 bit in Virtualbox and default it was disabled. And then I did some testing and on that, and yeah, it seems that that was the problem. Jack seems to hate hardware virtualization.

But of course this is Arch Linux we are talking about here and it ain't Arch if everything is working perfectly lol. OK, that was a bit harsh on Arch Linux, but since you configure EVERYTHING yourself it is easy to mess things up. I have had A LOT of weird problems with Arch in the past :). So after a while Arch didn't want to run Jack anymore(for some VERY F*CKING WEIRD REASON), but it doesn't really matter because everything works great in Ubuntu Studio.


To summarise:

[B]Ubuntu Studio
[/B]Everything works perfectly. I can run Jack with A LOT of programs(EVEN FREAKING LMMS that hates Jack) WITHOUT ONE SINGLE XRUN!!! Now that is with 1024 Frames/Period. With 512 Frames/Period it is about the same as 1024 used to be. That is, maybe 5 Xruns after a while. But I'll just run at 1024 because it works great and I am not recording live or anything.

[B]Arch Linux
[/B]Lol... OK, it does not work in KDE at all(it did for a while, but whatever...) because of problems with Phonon(GStreamer) and PulseAudio it seems. In Gnome 3 it works somewhat(Gnome doesn't use Phonon), but I get quite a lot of Xruns(at least if I run a lot of different programs).


So basically...I will absolutely use Ubuntu Studio to make music :). Ubuntu Studio is made for audio(and Jack) and uses a realtime kernel(I think 12.04 does?) and uses XFCE so no weird Phonon problems or something. Also I don't get weird PulseAudio Problems. Now, flash(and youtube) sound doesn't work when running Jack, but whatever...


Thank you for all your help!


[B]UPDATE

[/B]After having used Jack for real and working with some programs to make some music I started seeing a few Xruns after a while. but at least it wasn't that many.

---

### Post by Sylos on 2012-07-15
Glad to hear you are getting better results now!

There is a way of getting web browser sound into jack (I think) by setting up the pulseaudio to jack connection stuff. Personally I never bother because my Ubuntu Studio install is solely for music production. You could also install flash replacer in Firefox and use VLC - then install the jack VLC plugin - but thats a long winded and likely not very well supported solution. I just close all my sound apps and stop jack if I want to hear something from a browser.

I assume your Xruns are probably arising when you start/stop applications. If it starts to become a problem then return to the forum here and somebody can hopefully help.

And if you want to check whether you are using the real time kernel just give;

```
uname -r
```

and the result should have -rt at the end.

Happy music making.

---

### Post by Hoff123 on 2012-07-16
Want to hear something funny? Changing the sample rate to 96000 helped A LOT. NO F*UCKING XRUNS AT ALL!!! And of course the audio quality got better :).

EDIT It also seems that changing "Periods/Buffer" to 3(instead of 2) helped a lot. Now I can run at 256 "Frames/Period" without any problems(barely any Xruns at all).
Anyway this thread is solved now, good bye.

---

### Post by RaumTrug on 2012-07-17
Also, try using the free radeon graphics driver instead of the fglrx when doing music stuff. You might want to consider a seperate installation for that. With the free driver things are _much_ better for me than with fglrx...

---

### Post by Hoff123 on 2012-07-17
OK, thank you for the tip, but after doing some figuration both in BIOS and QJackCtl it seems to work very well now. If somehow things gets worse again I'll probably do that. I don't care about graphics in Ubuntu Studio(I use it only for music), but in Arch I definitely need fglrx. Thanks for the tips anyway.

EDIT I removed fglrx and now use the open source drivers again(I think at least...lol) and it works even better now. Thanks.

---

