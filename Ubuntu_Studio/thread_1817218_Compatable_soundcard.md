---
title: "Compatable soundcard"
date: 2011-08-03
forum: Ubuntu Studio
---

### Post by marcsolo on 2011-08-03
Hi there, pretty new to this platform, thought I'd like to experiment around with a Linux based system for multi track recording. I have installed Ubuntu 11.4 and are currently looking around for a suitable sound card that will not take too much to setup on the system. Have read some of the posts around the net and it seems that m audio sound card -audiophile 24/96 pci card would be the safer bet. Wondering if I'm on the right track, and would be grateful for anyones input :(

---

### Post by Sylos on 2011-08-03
Hello and welcome to the party.

M-audio do some very nice cards that take minimal setting up (you will need a bit of fiddling - particularly if you want to keep the pulseaudio sound server running for other apps). I have a Delta series card and really like it.

You should be carefull if you are multi tracking that you factor into the equation that you will need some form of pre amp as well if you plan on using a mic and recording live instruments.

Happy hunting.

---

### Post by marcsolo on 2011-08-03
Thanks for that, I bought my son a delta series, which is being used on xp they are very good, i am also coming frm years of windows, so this is a learning curve. sounds like sound on Linux is slightly more tricky to set up. Once i have set up a card is there any sequence these apps need to be installed in, or is it install and hope for the best....

---

### Post by Sylos on 2011-08-03
It is a bit of a learning curve but once you get used to it its not really difficult. I came from Mac to linux as far as sound recording is concerned so Im not sure what the windows set up is like (when I looked into it years ago windows audio was hopelessly glitchy and unstable so I didnt bother).

Anyhow, as far as installation is concerned it shouldnt be difficult. The easiest way is to just install the ubuntu studio packages over the top of your current installation (use the Software Centre). The core of the studio set up is just vanilla ubuntu - all the audio specific stuff are basically modules that can be bolted on. This should bring in all the necessary drivers and basic apps. I think once you do that you will need to add your user to the audio group and give it real time permissions (there is plenty of instructions on how to do this). Then use the Envy24 Control app to set up the M-audio card and you should be in business.

If you hit trouble just do a google search and if that fails hit the forum and someone will help out.

All the best.

---

### Post by sgx on 2011-08-03
Hi, run the command lsmod, and look for   snd_ice1712
this is your maudio card kernel module.

Now start qjackctl, go to the setup page, on the right you see

Input device  >
Output device  >

click the >  widgets, and your card should appear, so select it
for input and output.

Here is an overview/screenshots of the qjackctl gui

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Cheers

---

### Post by marcsolo on 2011-08-03
Thanks to both of the above tips..will now purchase this soundcard as it appears by all of your comments with some work I will be in business. No doubt  I'll have a few more issues as time goes on. Yes Windows Ha ..there used to be a saying on the old 520 ste..Atari if I wanted windows I'll put a whole in the wall!  Things have moved on since them dayz though,
cheers Guys, am looking forward to getting up and running

---

### Post by sgx on 2011-08-04
I have a revision 2 pci 24/96, its a few years old. Used ones go for
$40-50 dollars, I have not seen verified that new ones work, they did
a chip-reduction re-issue. Try and get a returns policy on a new purchase, to be safe. Quite a few Delta 1010s of recent purchase are in linux use, just thought you should know.
Cheers

---

### Post by trungvkvk on 2011-08-04
sorry. I am a newbie to use ubuntu.
 hopefully I'll get experience from people.
 What people experience when using ubuntu addiction please share.
 thanks.

---

### Post by marcsolo on 2011-08-16
Thanks again for the help, managed to get the above mentioned card, unfortunately my 98 system i use just for headphone monitoring (soundblaster live card) packed up so the m audio card has taken its place, so SGX funny you mentioned the Delta 1010 system as I have just been given the input rack to this system so you've answered my next question if they were compatable. Just have to source the pci card and connecting lead and will be back here to try and get it installed. This is why I'm eager to get going on this system, its a never ending battle with windows.
Thanks again.:)

---

### Post by marcsolo on 2012-10-27
Been a long time away, have still been battling with windows, am wondering if a presonus 44vsl usb card is workable on this platform. thanks:confused:

---

