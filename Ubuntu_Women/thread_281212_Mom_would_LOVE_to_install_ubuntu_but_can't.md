---
title: "Mom would LOVE to install ubuntu but can't"
date: 2006-10-20
forum: Ubuntu Women
---

### Post by M8M on 2006-10-20
I am SO determined to make Ubuntu work for me, but I'm getting really discouraged. I followed all the steps properly, but some how a "wacom" module didn't install and now it won't load unbuntu. The first problems I encountered were answered at [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

I can get all the way to 3/4 down the page where it says to press cntrl-alt-F7, then cntrl-alt-backspace for the configuration to take effect. The problem seems to be that it can't find a "wacom" module and therefore the configuration can't take place and the follwing error occurs:
"The x server is now disabled. Restart GDM when it is configured correctly."
I have reconfigured at least six times, but unsuccesfully since it stops working at the contrl-alt-backspace. 

I don't know how to find and install a "wacom" module especially since I can't even get ubuntu to load so I can attempt going online with it.

I thought of deleting everything and just trying right from the beginning again, but I have NO CLUE how to "undo" the partitioning etc that has already been done.

Please help this determined woman to get this up and running. I just want to see if I can love Ubuntu as much as others! I've never even seen any other OS in action other than windows and I can't make myself like windows any longer....

---

### Post by Old Pink on 2006-10-20
"wacom" are the drivers used in Ubuntu as a replacement for "SiS" or "Silicon Intergrated Systems" 

Looks like you need a graphics card driver, and then to reconfigure and restart the GUI. :)

---

### Post by M8M on 2006-10-20
Ok, this is going to make me sound stupid, but how does one do that? I'm not the techie type person b/c of lack of experience (I am capable of learning it, just haven't had the opportunity yet.)

Could it be that I didn't configure it right? (I had to tell it which monitor, keyboard, etc I had and some of it I just went with default b/c I didn't know.) I chose all "safe" options but had no clue what I was saying when I gave info such as 24bit screen setting or something like that. I just tried to use my best jugdement plus memory of some past experience, but can't say they were educated choices.

Thank you for your help. I will continue to rack my brain here and see if I can make sense or learn some more here.

---

### Post by jinx099 on 2006-10-20
Try "sudo apt-get install wacom"

I've never had a "wacom" card, so I'm guessing.

---

### Post by Aranel on 2006-10-20
Well...

I'm actually not even an Ubuntu user (against my own will - I'll try to install it again when Edgy is released in about a week), but I use Debian, which is similar. When I first set it up, it had set me up with an incorrect graphics driver; whenever I tried to start X, it would blink three times and give me some cryptic error message. I entered dpkg-reconfigure xserver-xfree86 (in Ubuntu's case, this would be sudo dpkg-reconfigure xserver-xorg) and selected drivers until it finally worked. It took me three or four tries.

So... do you know what kind of graphics card you have? You could try experimenting with the different graphics cards listed there and seeing whether each of them work. I know it's tedious, but...

If none of them work, it's looking to me like, as the previous poster said, you're gonna need to install a graphics driver that's not already there. Try entering sudo aptitude from the command prompt, selecting "Not Installed Packages" and hitting Enter, pressing the "/" key, and searching for "wacom." Then install that package and see if this "wacom" driver does the trick.

Again, I'm in no way experienced in this area... I've just had a similar ordeal before. Good luck, at any rate. :)

---

### Post by M8M on 2006-10-20
I'm think I'm learning as I go...bear with me....

The previous poster said:  'Try entering sudo aptitude from the command prompt, selecting "Not Installed Packages" and hitting Enter, "

Is this all a one line command? ex. sudo aptitude not installed packages <enter> or do I just do sudo aptitude <enter> then select "not installed packages".

Thank you for your patience and help,
M8M

---

### Post by Aranel on 2006-10-20
> **M8M said:**
> I'm think I'm learning as I go...bear with me....

The previous poster said:  'Try entering sudo aptitude from the command prompt, selecting "Not Installed Packages" and hitting Enter, "

Is this all a one line command? ex. sudo aptitude not installed packages <enter> or do I just do sudo aptitude <enter> then select "not installed packages".

Thank you for your patience and help,
M8M

When you enter "sudo aptitude," a text-based program will come up with a menu. From that menu, select "Not Installed Packages" using the arrow keys and press Enter. Once you're done, just hit "q" to quit.

---

### Post by Aranel on 2006-10-20
Come to think of it, though, you'll need to set up the repositories first. Before you do any of the stuff mentioned previously, enter "sudo nano /etc/apt/sources.list" (which will open a text-based text editor) and remove the "#" in front of all the lines that begin with "deb." Hit Ctrl+x to save and exit when that's done. Then enter "sudo aptitude update" and *then* do the whole aptitude thing mentioned earlier.

---

### Post by M8M on 2006-10-20
Ok, after waiting for my hubby too fool around with windows, I tried the above instructions and this is the result:

It found the wacom package in the not installed packages and when I told it to install it posted:

No packages, removed or upgraded. Some packages could be upgraded, but you have not chosen to upgrade them. Type "U" to prepare an upgrade.

I don't fully recall "holding back" any packages as it lists, but I do remember way at the beginning it saying that some file was corrupted and it could continue to install and I could make manual changes later. Basically I just went with the flow. I don't know how to "undo" the withholding. I tried typing the capital U and the small u but neither worked b/c when I came back it still showed the same.

I feel that we're "on to" something and we may have found the problem (I sure hope so!) but I just don't know how to correct it.

Thank you.

---

### Post by Aranel on 2006-10-20
> **M8M said:**
> Ok, after waiting for my hubby too fool around with windows, I tried the above instructions and this is the result:

It found the wacom package in the not installed packages and when I told it to install it posted:

No packages, removed or upgraded. Some packages could be upgraded, but you have not chosen to upgrade them. Type "U" to prepare an upgrade.

I don't fully recall "holding back" any packages as it lists, but I do remember way at the beginning it saying that some file was corrupted and it could continue to install and I could make manual changes later. Basically I just went with the flow. I don't know how to "undo" the withholding. I tried typing the capital U and the small u but neither worked b/c when I came back it still showed the same.

I feel that we're "on to" something and we may have found the problem (I sure hope so!) but I just don't know how to correct it.

Thank you.

Hmm, that's pretty odd. Try writing down the exact name of the package containing the name "wacom" and entering "sudo aptitude install [package's-name]" (replacing [package's-name] with... umm... its name). Again, I'm not sure exactly what it's called because I... don't have Ubuntu. If that works, try doing the whole "sudo dpkg-reconfigure xserver-xorg" thing again, and congratulations if it works.

...Now, wait, you *are* connected to the Internet, right? Does the output of "sudo ifconfig" return anything similar to "lo" and "eth0"? If so, good; if not, enter "sudo ifconfig eth0 up" followed by "sudo ifup eth0" (assuming you're not using dialup or a wireless card or something).

Sorry you're having to go through all this. :???:

---

### Post by M8M on 2006-10-20
> **Aranel said:**
> Hmm, that's pretty odd. Try writing down the exact name of the package containing the name "wacom" and entering "sudo aptitude install [package's-name]" (replacing [package's-name] with... umm... its name). Again, I'm not sure exactly what it's called because I... don't have Ubuntu. If that works, try doing the whole "sudo dpkg-reconfigure xserver-xorg" thing again, and congratulations if it works.

[COLOR="DarkGreen"]That did work and I redid the reconfiguring but it still stopped at: Starting GNOME display manager...[ok] then the next line is username@ubuntu: ~$ 
I don't know what to do next.[/COLOR]

...Now, wait, you *are* connected to the Internet, right? Does the output of "sudo ifconfig" return anything similar to "lo" and "eth0"? If so, good; if not, enter "sudo ifconfig eth0 up" followed by "sudo ifup eth0" (assuming you're not using dialup or a wireless card or something).

[COLOR="darkgreen"]Yes, both "lo" and "eth0" showed up.[/COLOR]

Sorry you're having to go through all this. :???:

[COLOR="darkgreen"]Thank you for all the help and sympathy! I really should be in bed, but I'm just want to get a rush of experiencing Ubuntu and know that I DID IT, (well with your help). My hubby already told me I'm on my own! LOL [/COLOR]

---

### Post by M8M on 2006-10-21
I have manually installed every package I could listed in the "not installed packages" and that helped me get into ubuntu.
However I now get a power management error after logging in and it freezes up about 1 min later. I can use it quite well for that quick minute, so I can access the terminal, etc.

There is also another error about not being able to load HAL!
I'm not sure what that means or what to do about it.

ANy suggestions?

---

### Post by Aranel on 2006-10-21
Yay!

So you can get the graphical stuff to work, right? Well, that's definitely making progress. As for this whole power management thing, I think that's beyond my narrow scope of experience... I'm using the stable branch of Debian, which uses hopelessly obsolete software - to the point that it doesn't even *have* any power management options. I really wish I could help, but I don't think I can in this aspect. Sorry. :(

---

### Post by M8M on 2006-10-21
Yes, I'm excited and discouraged at the same time. LOL

My main obsticle right now is that I think I need to install one more GNOME file, but when I try to install something through the terminal it starts installing then comes to a point where it says to put the CD in the cdrom and press enter. I do that but then the cd rom can't communicate with the terminal b/c nothing happens (no lights go on or sound) and it immediately aborts. So any fixes that I find in my searches can't be performed b/c the cdrom paralizes at that point. I can boot or use the cdrom any other time, but then.

---

### Post by M8M on 2006-10-22
:KS Celebrate with me! I reinstalled Ubuntu and now it's working PERFECTLY!

YAY!

---

### Post by Aranel on 2006-10-22
> **M8M said:**
> :KS Celebrate with me! I reinstalled Ubuntu and now it's working PERFECTLY!

YAY!

Yay! I trust you've found it to your liking? :)

---

### Post by M8M on 2006-10-22
Oh, most definitely! Thank you so much for all your help!

Where do I find the cool desktop backgrounds and all the other applications to add on?

---

### Post by aeon on 2006-10-22
double post sorry

---

### Post by aeon on 2006-10-22
It hurts finding this thread so late, but I think I know what the problem is, or atleast I know of a solution Incase anyone else encounters it.

The problem for me was in my xorg.conf

what i did was open a terminal, then:
```
sudo nano /etc/X11/xorg.conf
```
then scroll down and look for the "wacom" entry and comment those lines out with a #

after this just ctrl-x to save the document and then ctrl-alt-backspace to restart the x-server

I remember someone telling me this about a year back, don't know if it's because of buggy drivers or of another nature, but it works unless you don't have a wacom tablet or a tabletPC which need the driver..

glad you got it working though!! =D>

-aeon

---

### Post by Aranel on 2006-10-23
> **M8M said:**
> Oh, most definitely! Thank you so much for all your help!

Where do I find the cool desktop backgrounds and all the other applications to add on?

[Here's an automatic repository generator.](http://www.ubuntulinux.nl/source-o-matic) Under one of the menus, there's a "Run Application..." item; enter "gksudo gedit /etc/apt/sources.list" into that dialog, and the sources.list file you edited before will come up in a text editor. Once you're finished there, replace the file's contents with what that site gives you and save it.

Once you've done that, you can easily install... well, pretty much anything. Just open Synaptic Package Manager (should be in the menu somewhere). As for desktop backgrounds and stuff, I'm not sure if there's a software package that provides any, but you can certainly Google around for some. :mrgreen:

---

### Post by seshomaru samma on 2006-10-23
> **M8M said:**
> Oh, most definitely! Thank you so much for all your help!

Where do I find the cool desktop backgrounds and all the other applications to add on?
[this website]("http://www.gnome-look.org/") has everything concerning eye-candy : backgrounds, themes ,icons...
for installing software there many ways :
[this website]("http://monkeyblog.org/ubuntu/installing/") explains it better

have fun!

---

### Post by M8M on 2006-10-25
Thank you! These link are VERY helpful!

I'm trying to install my samsung printer driver, but can't seem to find the answers I need. I will continue to look at the second link you gave me and see if I can find the answer....

I'm thinking I will need to install a wine thingy anyway, for my business software, so that may be the way to go for this printer too....

I could be totally off too, but I haven't finished readin the link yet....

---

