---
title: "I dont understand why..."
date: 2005-08-03
forum: The Cafe
---

### Post by KezzerDrix on 2005-08-03
I dont understand why I dont have any luck getting the multimedia capabilities of Ubuntu to work properly.  I added the needed repositories and followed the unofficial guide, but all I recieved was one error after another.  I then went to the  wiki and followed it everything installed error free but when I clicked on a movie to play it I would recieve gstreamer failures.
What am I doing wrong?   I like totem but it doesn't seem to work.  Should I install "xine"?  or Mplayer?  I wish Ubuntu would preinstall  these things, other distros do so  it must be possible.    
I like the look and feel of ubuntu, the huge repositories, and the community.  I want to use it but cant seem to  get this problem resolved.  Please give me some suggestions.

---

### Post by pmj on 2005-08-03
I followed the instructions on ubuntuguide.org and everything I've tried so far has worked.

Tried vlan?

---

### Post by KezzerDrix on 2005-08-03
No, I keep digging through the forums and found one suggestion to try totem-xine.

Anyone know if this helps.

---

### Post by TravisNewman on 2005-08-03
if you're trying to use totem, then yes, totem-xine is the best bet. You can also install gxine or mplayer.

---

### Post by ubuntu_demon on 2005-08-03
I prefer xine-ui
to install xine-ui (without $)
$sudo apt-get install xine-ui

---

### Post by poofyhairguy on 2005-08-03
Try this command and then try again:

> sudo apt-get update

You need that command.

The reason Ubuntu does not include that stuff out of the box is because its illegal to do so....Ubuntu does not want to break the laws of the major nations its users are in.

The distro MEPIS comes like that by default.

---

### Post by KezzerDrix on 2005-08-03
i appreciate your help, I was getting very frustrated last night, the only thing I could get to play are mpegs.  Linux will play all formats wont it, ie shockwave, flash, quicktime/mov, wmv, avi etc, etc?

If I install totem-xine will it work automatically? say click a link and video downloads and plays?  Will I have to alter config files?  

Same question, only put xine in place of totem?

---

### Post by TravisNewman on 2005-08-03
Shockwave won't work, but flash will.

---

### Post by KezzerDrix on 2005-08-03
what about this part...

If I install totem-xine will it work automatically? say click a link and video downloads and plays? Will I have to alter config files? 

Same question, only put xine in place of totem?

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=KezzerDrix]what about this part...

If I install totem-xine will it work automatically? say click a link and video downloads and plays? [/QUOTE]

Are you talking about movies in the browser? you need this:

[http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger](http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger)

---

### Post by ubuntu_demon on 2005-08-04
xine-ui (named xine in the menu) can't play in the browser as far as I know
totem-xine can and yeah you need mozplugger (see poofyhairguy's link)

---

### Post by KezzerDrix on 2005-08-05
Okay,

I had limited time and wanted to install Linux on a friends computer.  I new that Mepis and PCLinuxOS would install everything I needed but for whatever reason neither would boot to this pc.  It is a 1600+ amd with a nf2 chipset, 512 of ddr and a geforce3 graphics card.  The only Linux I could get to work is Ubuntu's text installer.  To be honest, I have not had good luck with Ubuntu in the past but decided to give it another try.  Everything went fine, I even worked through the partioning part and within a few minutes Ubuntu was up and running.  In my opinion Ubuntu is the best laid out desktop.  Well like I was saying, everything went fine intill the multimedia capabilities came around.  After an hour or so I came here for help, I recieved some advice and tried again.  After several more hours I managed to get mpeg to work.  I then came here and asked for more help, which I recieved and after a few minutes (installed totem-xine, and mozplugger) I could watch almost any type of video, but could not stream content.  I then installed mplayer, which looked promising but would lock up as it was buffering and kill firefox altogether.  As I stated I had limited time and had to give the computer back in this somewhat broken state to a person who never has used Linux before, I am sure it will give her a bad impression of Linux.  

I thought it might just be me, but the forum is full of these type of questions, and I am no slouch, I have been working on computers for better than 15 years.  

I respect Ubuntu's decision to leave out the necessary files due to legal restrictions.  I just wish someone could come up with a better solution.  As powerful and functional as Ubuntu is I am suprised no one has rolled up an "all in one media package" and put it in the universe or multiverse.  

As much as I personally like Ubuntu and plan on installing it ("again") on my own computer, where maybe I can figure out the multimedia problems over tiime.  I can not feel comfortable suggesting it to friends or my customers.

---

### Post by man.life on 2005-08-05
Did you use the sources.list in Ubuntu Guide?

Check that you have the same file.

sudo apt-get install flashplayer-mozilla (Flash)
sudo apt-get install w32codecs (Windows codecs)
sudo apt-get install totem totem-xine (Upgrade Totem and install Xine backend)

Now you have swf, mov, wmv, avi support and you can play movies in Firefox.

---

### Post by Wolki on 2005-08-05
[QUOTE=KezzerDrix]I then installed mplayer, which looked promising but would lock up as it was buffering and kill firefox altogether.[/QUOTE]

maybe this has to do with mplayer and esd? It needs to have Audio Output set to esd in the preferences before playing a file, that's a problem many people encounter.

Anyway, i've hat the best experiences just starting a media player for streams instead of using a browser plugin. I think there's even a firefox extension that helps with that.

w

---

### Post by KezzerDrix on 2005-08-05
Yes, I used the sources and everything downloaded and installed via synaptic with no errors, at that point.  

I will try the esd thing and see if it makes a difference.

thanks for the help.

kezz

---

