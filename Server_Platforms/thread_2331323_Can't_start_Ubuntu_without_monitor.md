---
title: "Can't start Ubuntu without monitor"
date: 2016-07-20
forum: Server Platforms
---

### Post by dragen2 on 2016-07-20
Hello.

I've been trying to set up a headless server for a week now. But no matter what I do, Ubuntu refuses to start without a monitor connected. It just reboots the computer.
I've tried using a vesa xorg.conf, I've tried disabling some Intel driver. It's not the BIOS, as I've disabled halt on errors.

Starts fine with monitor connected. Using 16.04 (ubuntu-16.04-server-amd64.iso).

Any help?

I'll also mention that I have no GUI installed. It's a purely cmd line install, as the computer is supposed to be in a closet.

---

### Post by howefield on 2016-07-21
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by MAFoElffen on 2016-07-21
> **dragen2 said:**
> I've been trying to set up a headless server for a week now. But no matter what I do, Ubuntu refuses to start without a monitor connected. It just reboots the computer.
That is strange.  
> **dragen2 said:**
> I've tried using a vesa xorg.conf, I've tried disabling some Intel driver. It's not the BIOS, as I've disabled halt on errors.
With no installation of xserver, an xorg.conf file is not going to do anything... You said you tried to disable an intel driver? With xserver not installed, how did you try to disable an Intel driver?
> **dragen2 said:**
> I'll also mention that I have no GUI installed. It's a purely cmd line install, as the computer is supposed to be in a closet.
Here is the deal with Ubuntu Server Graphics. It is thought of as being text, but is basically vga graphics to do the colors and fonts used for the virtual consoles of your tty sessions. In that respect, there is also a facility to change the VGA pallet for you console. You can also force the console to be text only, but I like having the color contrast. So video/graphics drivers are not used. Technically, the only graphics drivers are low-level frame-buffer drivers. 

I have 14 servers in a server rack. All are administered remotely from my Remote Admin Console... but they are also connected locally to a series of KVM switches to a rack-mount HP TFT5600 RKM. As how KVM switches work, only one is active at a time, but is not connected if the cover is down and pushed into the rack... So all 14 are headless.

This is what I do. I set the video settings in grub, vai kernel boot options.

Open /etc/default/grub
```

sudo vim /etc/default/grub

```
Press <Insert> then go to the GRUB_CMDLINE_LINUX_DEFAULT line. Change it to
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset video=uvesafb:mode_options=1024x768-16@60,mtrr=0,scroll=ywrap,noedid"

```
What that says is turn off kms mode switching in the kernel; Use the uvesafb frame buffer; Set it to a resolution of 1024x768, with a depth of 16 at 60 mHz sync rate; Disable the memory type range registers for the framebuffer; Enable display panning in a wrap-around mode, using VESA protected mode; Do not probe the display to check for edid data. When you switch over to it or connect it to a monitor, then it should be set to that mode (already).

The last part makes that all work while being disconnected. It's sort of like UTP... in that it sets it all up as if something is there (in this case manually), but doesn't care that it is not connected.

Then do 
```

sudo update-grub

```
To pick up the changes. Shutdown/Reboot with your monitor disconnected to test.

If that does not work. then take that back out, and change to 
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset text"

```
That will force the console to text mode

Then uncomment this line:
```

#GRUB_TERMINAL=console

```
Which will force the Grub Menu from graphics mode to text mode.

Remember to do an update-grub to pick up the changes before rebooting.

Tell me how it goes.

EDIT-- If all that fails... then tell me what your hardware is: Brand, model, video GPU... so I can look to see if there might be a BIOS or other quirk that might cause that...

---

### Post by Elizine on 2016-07-21
Install dummy monitor
```
sudo apt-get install xserver-xorg-video-dummy
```
Backup xorg.conf
```
sudo  mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Create a new xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

with


```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1152x864"
    EndSubSection
EndSection
```

---

### Post by MAFoElffen on 2016-07-21
@OP- Do not Install the package the last poster recommended.

@Ellizine
Sorry, but installing xserver-xorg-video-dummy would only work if the OP was using XServer, which is not even installed. He is not using, nor will he be using a local, nor any remote XSession. (Note- "No GUI")

In fact, using apt-get to install of that single package would cause the complete Xorg Server to be installed ... Which would kick-off a landslide of extra packages to be installed on his text-console server, which he would not use, and would have no affect on what is happening. He stressed the point that he is not using, nor has X11 installed. 

Please *carefully* read the OP's original post, and my response again. This has nothing to do with X11. (not installed)

---

### Post by dragen2 on 2016-07-21
> **MAFoElffen said:**
> 
Tell me how it goes.

EDIT-- If all that fails... then tell me what your hardware is: Brand, model, video GPU... so I can look to see if there might be a BIOS or other quirk that might cause that...

Neither of those worked.

The hardware is a Gigabyte GA-Z68p-DS3 rev.1 with an i5 2300. Not using a dedicated GPU, as I don't see the point.

Did a reinstall of the OS, so I could be sure I didn't forget to rollback any changes before trying yours. Only packages other than default is SAMBA and OpenSSH.

---

### Post by dragen2 on 2016-07-21
Also, sorry for the delay. Had to deal with *people*&#8203; all day.

---

### Post by mastablasta on 2016-07-22
disable the GPU in BIOS!? It's porbabyl a desktop motherboard so it expects monitor. similar issue with some ubuntu/Linux sticks.

---

### Post by MAFoElffen on 2016-07-22
I'm looking at the spec's on that board now. Yes, a gaming board that is wrapped around the support of fast graphics, Which is going to show a video error in BIOS as a Video failure. Looking through the BIOS options to see if there is a way to disable video in BIOS... Went through the board manual. It switches internally looking for video or you can set to a source manually. No option to have none.

Mastablasta was right, it is a desktop board, that thinks that no video is an error. No way to disable that *feature* in that board. My apologies, in that, I deal mostly with server hardware, for headless. Sometimes I forget, that other eople use 'other' hardware. But luckily, I have a lot of legacy and 'other' experience...

^ *** There is a somewhat inexpensive workaround for you. Get an [ATI Rage]("http://www.newegg.com/Product/Product.aspx?Item=9SIA4UB1T25480") Pro or XL (Radeon) video card. That GPU chip is basic GPU graphics that has been a standard for onboard server graphics for years. It is also "dirt cheap." Is has a standard 15-pin Analog VGA port (Your board has only digital video ports.) Then buy a 75 ohm VGA dummy termination plug ([like this one]("https://www.conferenceroomav.com/RapcoHorizon-/VGA-TM.cfm?gclid=CjwKEAjwiMe8BRD0ts3Vtv-ohWgSJAAZurk1kms4cu0obrs-v8RzITmsoDYv2FbBw2Nj8wO71lEtEBoCgAzw_wcB")). Then in the OneTouch BIOS > Advanced BIOS Settings > Init Display First, set it to "PCI". That way the first display it looks for is that PCI Video, instead of onboard. With the dummy plug attached to it's port, it carries the signal across the pins, thinking it has an attached monitor... 

That is the best commercial recommendation I see for you. (For your work.) I could explain or point you to how to make a VGA dummy plug, but for commercial, you want someone to blame, liabilities and guarantees... right? Besides, with your first one, learning to pin it out, the cost of the kit, resistors, your boss paying your labor... It's cheaper to just buy one.

---

### Post by dragen2 on 2016-07-22
Really? It'll halt even when I've told it to not halt on error?

---

### Post by MAFoElffen on 2016-07-22
It doesn't halt. It reboots. Right? Just after the BIOS? Before loading the grub menu?

If the above is true and you set it "not to halt on any errors," then:
- If rebooting before it gets to the Grub Boot Menu (But boots fine with an attached monitor), then it is most likely a hardware issue.
- It has internal GPU, so it always has video, but does it when no monitor. Since the internal is digital output...
- If it had no video at all (no GPU) it would be a Northbridge error and beep. But it does, see above.

With some (rare) desktop motherboards, if you had no monitor, then it will not boot. I've seen starting around 2004, thorugh last year, that reacted that way, all desktops. Most server boards, they plan that they are going to be headless. 

On those that did not boot without an attached monitor, those same did boot if they had an attached monitor. The monitor did not have to be turned on, just had to be attached. 

An old trick use 3 75 ohm resisters between pins was to supply a load between vga pins 1-6, 2-7, and 3-8... They sell dummy/terminators that are already pre-made for that. Problem is, that your board has digital video, so would need a basic anolog card with a VGA port to do that.

So the "tell" is if the conditions at the start of this post are true, then your hardware falls into that category.

---

### Post by dragen2 on 2016-07-26
So I asked Gigabyte.
And they claim the F9 BIOS can boot headless. Too bad F9 makes the motherboard useless.

---

### Post by Vegan on 2016-07-26
Given you have Sandy Bridge, I am aware that the BIOS for a lot of machines leaves something to be desired

you should check to be sure you have the latest version installed. I have a similar rig with an i3 which also is a nuisance with Linux, could be that intel does not want desktop boards being used as servers etc?

---

### Post by dragen2 on 2016-07-31
Well, the reason for it not running the latest BIOS, is that I did actually update it to the latest version but it decided it wasn't going to behave with that. It kept bluescreening and reboot on its own. So I bought a new computer, and decided to roll back to F5 which worked.

I've now installed F9 (latest BIOS), and I'll see if it likes it this time.

I do have another box running with Windows, also headless. It's maybe a year older than the ubuntubox. Works like a charm with stock BIOS and i3.

---

### Post by MAFoElffen on 2016-08-01
Still following this, and following your results. 

You read my recommends... You are on the right track for other alternatives. I know the vendor said it should work and that you should try "due deligence" in following their instructions for their board. (That good faith effort) I feel for you.

---

### Post by dragen2 on 2016-08-01
Had it running with a head for 24 hours to see if F9 was still borked. Turns out my first update to F9 was faulty. No reboot or crash during the 24 hours. 

So I tested running it headless, and it works.

---

### Post by MAFoElffen on 2016-08-03
Great!!! So the BIOS update has fixed it then?

If so, then please reviist this thread to mark it as solved = Link at upper right of page "Thread Tools" > Select "Mark Thread as Solved". This helps others (laters) when they search for answers to their similar problems.

---

### Post by dragen2 on 2017-01-09
Yes. The BIOS update fixed it. Protip: Don't use Gigabytes Windows tool.

---

