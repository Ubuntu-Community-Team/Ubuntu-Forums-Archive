---
title: "Wild Dog NRFPT"
date: 2009-01-30
forum: System76 Support
---

### Post by jbelmonte on 2009-01-30
I received my son's birthday Wild Dog earlier this week and we just set it up. We are having some issues with the initial set-up and I sent a couple of  messages to support-at-system76-dot-com. I just want to make sure they were received.

---

### Post by jbelmonte on 2009-01-31
I haven't heard from System76 yet, so maybe the community can help me.

This is the configuration of the Wild Dog Performance I bought my son for his 21st birthday.
Options
*Graphics : 1 GB ATI Radeon 4850 PCI-Express x16 GDDR3 (2 x DVI, S-Video, DVI to HDMI, DVI to VGA)
*Hard Drive : 1 TB SATA II 300Mbps - 7200 rpm 32 MB Buffer
*LCD Monitor : 26” KDS Widescreen LCD (1920 x 1200)
*Memory : 8 GB - 4 x 2 GB - DDR 2 - 800 MHz
*Operating System : Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
*Optical Drive : CD-RW / DVD-RW
*Processor : Quad Core Q9550 2.83 GHz FSB 1333 MHz L2 12 MB
*Speakers : 2.1 - Logitech X-230 - 2 Satellites, 1 Subwoofer
*Wireless : 802.11 bg

On initial boot up, we saw the splash screen with the option to press F2 to enter BIOS. We then saw GRUB. We then entered the Initial Ubuntu setup where my son was able to select his language and create a login. Then the Ubuntu logo was displayed with the orange progress bar. When that completed, rather than showing the login prompts, the screen went wacky and showed blocks of different colors in a patchwork.

We powered off and restarted the computer. We saw the splash screen with the option to press F2 to enter BIOS. We then saw GRUB at which point we hit esc and chose the recovery mode option. The only option that seemed to offer a quick solution was the xfix option. We tried that and on restart we get to the Ubuntu logo with the orange progress bar again. Once that finished, the screen goes completely white rather than showing the patchwork of colors.

I tried using a Live CD, but the same thing happens. As soon as the orange progress bar under the Ubuntu logo finishes, the screen goes white and nothing else happens.

Is there some command line work I can do to try and get the system to make it past the progress bars?

TIA for any assistance.

---

### Post by Lee_Machine on 2009-01-31
I've seen this sort of thing before. The issue was the video card had become loose,this happens sometimes during shipping. I dont know your computer exp, but i would open up the case and reseat the card. 


does this help?

I would also reseat the RAM.

Using the Live-Cd 99% of the time rules out software issues, and I haven't read about any s76ers getting DOA hardware.

---

### Post by jbelmonte on 2009-01-31
> **Lee_Machine said:**
> I've seen this sort of thing before. The issue was the video card had become loose,this happens sometimes during shipping. I dont know your computer exp, but i would open up the case and reseat the card. 


does this help?

I would also reseat the RAM.

Using the Live-Cd 99% of the time rules out software issues, and I haven't read about any s76ers getting DOA hardware.

Good thought on the loose video card. Thanks. If I won't void my warranty, I have no problem opening it up and reseating the card. I'll wait for Tom to give me the OK to do this.

I don't think I need to reseat the RAM as a full MemTest came up clean.

I'm not saying my issue is DOA hardware, but DOA hardware happens to every manufacturer. It's how they handle it that counts. I'm confident that System76 will get my issues resolved. I just wish the issues didn't happen on a Friday night.

---

### Post by jdb on 2009-01-31
> **jbelmonte said:**
> Good thought on the loose video card. Thanks. If I won't void my warranty, I have no problem opening it up and reseating the card. I'll wait for Tom to give me the OK to do this.

I don't think I need to reseat the RAM as a full MemTest came up clean.

I'm not saying my issue is DOA hardware, but DOA hardware happens to every manufacturer. It's how they handle it that counts. I'm confident that System76 will get my issues resolved. I just wish the issues didn't happen on a Friday night.

Check out this thread & thomasaaron's reply.
System76 is good on their warranty & opening the machine won't void it.

[http://ubuntuforums.org/showthread.php?t=1001312&highlight=loose](http://ubuntuforums.org/showthread.php?t=1001312&highlight=loose)


I'm sure Tom will reply first thing Monday, but it's hard to wait that long ;)

jdb

---

### Post by jbelmonte on 2009-01-31
> **jdb said:**
> Check out this thread & thomasaaron's reply.
System76 is good on their warranty & opening the machine won't void it.

[http://ubuntuforums.org/showthread.php?t=1001312&highlight=loose](http://ubuntuforums.org/showthread.php?t=1001312&highlight=loose)


I'm sure Tom will reply first thing Monday, but it's hard to wait that long ;)

jdb

Thanks jdb. It looks like I can just open it up and make sure everything is well seated without voiding the running into a warrany issue. So I will give it a try.

---

### Post by jbelmonte on 2009-01-31
I opened it up and everything looked okay. I reseated the video card and made use everything else was securly seated or connected. No luck. Just a whie screen after the Ubuntu logo and progress bar. Pushing the power button shows the Ubuntu logo and progress bar during shut down.

---

### Post by jdb on 2009-01-31
> **jbelmonte said:**
> I opened it up and everything looked okay. I reseated the video card and made use everything else was securly seated or connected. No luck. Just a whie screen after the Ubuntu logo and progress bar. Pushing the power button shows the Ubuntu logo and progress bar during shut down.

Bummer.

I'm sure Tom will take care of you Monday.
It's probably best not to try too much else because any configuration changes will just make it harder for Tom to troubleshoot.

I hate it when things happen on a Friday night that can't be taken care of until Monday :(
It was really frustrating back when all the stores were closed on Sundays, that's inevitably when I needed a part of some weekend honeydo.

jdb

---

### Post by jbelmonte on 2009-01-31
Carl took care of me today. The Wild Dog is up and running and my son is a very happy camper.

The DVI to DVI connection was the initial problem. Carl thinks it may have something to do with DRM. The quick fix was to use DVI to HDMI. I complicated my problem by running xfix from recovery mode when it first happened. This reset the xorg.conf file and lost the required driver information. I was fighting a losing battle after that. However, Carl talked me through using nano to edit the xorg.conf file from the command line. Now it's all good and the Wild Dog is RFPT (Ready For Party Time).

FYI, the build on the Wild Dog is excellent. Great case, great components, and well put together.  The description and pictures on the System76 web site do not do it justice. After my son has worked with it for a while, I'll get him to write a review.

Thank you Carl. Thank you System76. I will spread the word about your great service and wonderful Ubuntu computers.

---

### Post by wabre on 2009-04-11
are you planning on getting jaunty 9.04 running on the machine? would be interesting to know how it performs

---

### Post by jbelmonte on 2009-04-11
> **wabre said:**
> are you planning on getting jaunty 9.04 running on the machine? would be interesting to know how it performs


I'm sure that my son will upgrade to Jaunty after his semester is over in Mid-May. No sense in taking a chance with a hosed upgrade during finals. And Intrepid is working just fine for him. I'm sure he will write a review during break, but the only thing he mentioned when I asked him about performance issues had nothing to do with the Wild Dog itself. He works with very large spreadsheets and Open Office Calc only uses one core, which makes it less fast than everything else. Overall he seems really happy with the Wild Dog.

---

### Post by SysKoll on 2009-05-06
jbelmonte,

Thank you for sharing your favorable experience.

I am also interested in getting a System76 Wild Dog. One small worry: the noise level. Is the fan noise OK? I had a machine in a big case, with powerful fans that were so noisy it was actually tiring. Any problem with fan noise?

---

### Post by jbelmonte on 2009-05-08
> **SysKoll said:**
> jbelmonte,

Thank you for sharing your favorable experience.

I am also interested in getting a System76 Wild Dog. One small worry: the noise level. Is the fan noise OK? I had a machine in a big case, with powerful fans that were so noisy it was actually tiring. Any problem with fan noise?

Sorry for the delay in response. I didn't remember any noise issue with my son's Dog, but I wanted to wait until he came home from college to fire it up and listen for myself. His  Dog is on the desk right next to the monitor, so it is as close to the ears as possible. It was pretty quite. You know that it is on, but it is "whisper" quiet and well below any "tiring" threshold. My son doesn't use the DVD drive often, and I didn't think to ask him to use the drive last night. I will ask him to test it today so I can hear the DVD drive in action.

---

