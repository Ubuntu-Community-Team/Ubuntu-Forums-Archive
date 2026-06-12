---
title: "Ubuntu 9.10 won't install..."
date: 2009-11-04
forum: Server Platforms
---

### Post by ZALinuxDude on 2009-11-04
Hi Guys got a pretty strange problem(first time its happened to me - first time i'm trying server edition out), its freaking me out any help would be appreciated

Let me explain my problem...

I am not new to the Ubuntu range but am not what you would call an expert, any way i managed to acquire a pretty neat little (and old) little server setup which i want to use as a File sharing and web server in a home network, the specs are as follows 

GigaByte GA-6BXDU Dual processor (2 x PIII processors)
512Mb Ram (4 x 128Mb modules)
40Gb OS hard drive 
160Gb Media drive (not installed as yet waiting untill server up and running)

I downloaded the ISO for 9.10 server (32bit) and copied it to cd
when i put the disc in the machine boots up no problems no errors runs through mem check fine etc etc. the disk boots up into Ubuntu language i choose English then come to the ubuntu splash screen and main menu i select "install ubuntu" and then... nothing i get a black screen with flashing (horizontal) cursor in top left corner of screen and that's how its stays, the cd rom stops functioning (light stops flickering and slows down along with internal fan noises as well), am i using the wrong version (is 9.10 too advanced), should i try an older version for my hardware, (i don't understand why it should be a problem as i checked the minimum requirements and i'm "safe" all of them are good) can someone please shed some light on this issue 

Oh yes before i forget the "clients" will be running Windows XP pro SP3 and Windows 7 Ultimate and i require VPN access, I really hope that i can get this sorted, my alternative is Windows 2K advanced server and lets face it, its not linux... nuff said

---

### Post by dvandok on 2009-11-04
I assume you checked the CD for errors.

Your description suggests that the video mode chosen by the installer is incompatible with your graphics hardware.

Is there an option (like, under f6) to choose a text-based installation?

Not wanting to play down Ubuntu here but you may consider Debian as an alternative, if this is just going to be a server.

---

### Post by ZALinuxDude on 2009-11-05
Well actually I did check it for errors but its not just this OS its having a problem with, I tried Debian 5.0.3 last night and Windows XP pro and both just stop, and seeing as all of these OS's are fairly recent releases i figured its them thats causing the problem, are they a little too advanced for the hardware i'm using?

I remember that one of the HDD's i used for the server had W2K on it and this worked which only confirms that its the OS that is causing the problem, should i not maybe try Ubuntu server 8.0.4 LTS?

---

### Post by cariboo on 2009-11-05
THe server install is text based, but try pressing F4 and selecting safe graphics mode, then press enter, then select install and press enter. If you having problems with difference distributions, than it's a common problem.

---

### Post by ZALinuxDude on 2009-11-05
> **cariboo907 said:**
> THe server install is text based, but try pressing F4 and selecting safe graphics mode, then press enter, then select install and press enter. If you having problems with difference distributions, than it's a common problem.

Do you think the graphics problem is impeding the installation process for all the OS though, as i said i'm stumped with this as i have never had this problem before now... any way thanks to EVERY ONE for your help I will give this way a try tonight and let you know but just incase downloading the 8.0.4 LTS ISO as well maybe i can give that a try just in case...:D

---

### Post by jongudm on 2009-11-05
I don't know if this is relevant to your situation but I had a very similar looking problem installing 9.10 server 32 bit except the installation didn't always stop in the same place.  Sometimes it would crash during the installation itself (after partitioning and formatting the HDD) and at least once it stopped the way you describe here.  This however just turned out to be my very old cd drive that simply stopped accessing the disc seemingly at random.  When I plugged in a different one everything worked.

---

### Post by ZALinuxDude on 2009-11-06
Thanks for the help guys tried all of your suggestions nothing helped, then i tried the 8.04 LTS version and it generated an error:

"ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI."

Which i'm assuming means i need to update my bios which i am willing to do but how do i do that without a DOS disk or OS already on th HDD, the bios version i already have doesn't have 
"@BIOS" or that other little app in order for me to do this can any one help, may i make a suggestion at the same time here... would it be possible for someone to embed these bios updating tools into the distro's install menu that way we can select that option first if we need to update the bios first before the install will run without a problem, I would do it but my skill level is not yet at that level

Otherwise i'm gonna have to use W2K which i know previously worked then update bios and then reformat HDD when i load Ubuntu, hopefully that will sort my predicament, unless of course there is another solution, or is there an ubuntu server adition available that is compatible with bios versions older then 1999?

The other issue is when i try running "rescue damaged system" (or something like that) it gives me a logfile readout and about half way through the screen scrambles and then goes blank would that also be a symptom of the bios problem?

Again any help or suggestions would be appreciated

---

### Post by ZALinuxDude on 2009-11-09
Hi guys it would seem that my problem runs deeper and could also be a hardware problem more specifically i assume its a faulty motherboard i have since sourced another candidate and will attemp another installation and startup tonight and will fill you all in tomorrow

---

### Post by ZALinuxDude on 2009-11-10
Just a quick update guys finally got my server installed and booted up now its just a case of setting it up properly

---

### Post by cariboo on 2009-11-10
Could you please let us know what you had to do in order to do the installation, others may benefit from your experience.

---

### Post by ZALinuxDude on 2009-11-10
Sure no problem, like i said it turned out to be a hardware problem...faulty mobo i think, so sourced a neat little P4 2.5 put about 750mb ram in it (sorry i completely frankensteined the poor thing but its working better then i expected) any way with this new little machine just stuck the ISO cd of 9.10 in and it loaded straight away no problems didn't even have "file corrupted" issues the only thing now is i'm trying to set everything up to what i want, but may have inadvertantly run into other problems, such as i would like to load a gui, so that my wife can see whats going on if i'm not there (she doesn't know commandline at all) the problem is i can't get my 3G modem to work so i don't have internet, so now i am trying to find out how i can install either from the ISO that i used or download individual install files or update packages and then use Flash drive maybe you can help me with this...? I mean i have done searches and come up with hits but none that are both relevant to this version of ubuntu or clear and precise enough for me to understand and carry out commands, i really hope you can help

---

