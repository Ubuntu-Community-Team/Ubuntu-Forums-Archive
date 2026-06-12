---
title: "Installed Studio and now No sound, No wifi"
date: 2009-09-30
forum: Ubuntu Studio
---

### Post by tinawina on 2009-09-30
I was running Ubuntu 9.04 and all was just great. I had no troubles ever with sound, display, wifi, etc. No tweaking required. Today I installed Ubuntu Studio (latest version) and decided to install using my entire HDD since I couldn't see a need to keep Ubuntu as it would just duplicate Studio.

During the installation, wireless could not be configured. Something about my wireless adapter (an SMC wifi USB dongle wh was plugged into the system, green light "on") not being configured to use DHCP (wh is not true). After many attempts to make this work, I decided to skip this step during install thinking I could get wifi up and running later. 

Well, Studio is installed and now I have no WiFi and no sound. I had both without a hitch with Ubuntu. 

Admittedly, I have a steep learning curve to figure out all the ins/outs (literally) of JACK, Hydrogen, Ardour, etc. However, when I installed and tried Hydrogen and JACK on my old Ubuntu I had sound and everything worked great.

I am considering overwriting Studio with Ubuntu 9.04 and then just adding the audio programs I want/need once I'm back to good with sound and wifi. Studio sure is pretty though.... Any insight, advice, instructions are really appreciated. Thanks!

---

### Post by jmfal on 2009-09-30
Hi, welcome to ubuntu.
 I`ve had problems with downloads from ub studio, long downloads, m5sdm not right, etc..etc..etc
 If you want to start over, you can re-install jaunty, then "convert" to 
studio using synaptics>meta,. IF you don`t have any meta packages, go to software sources and check all the boxes except sources and cd-rom, when you close it will say not up to date ,let it update.
 Go back to software sources> third party> put a check in all the boxes,close , let it update, install your studio packages, good to go!!
    You don`t need to install studio- desktop if you don`t want to, when you install the audio packages it will install the rt-kernal.
  I hope this helps..,enjoy

---

### Post by c00kie55 on 2009-09-30
well i have been down that road and cut not figure it out so did a little  google and came up with this 
[http://ubuntuforums.org/showthread.php?t=1138557](http://ubuntuforums.org/showthread.php?t=1138557)  remember to update before installing studio 
or else i coudent find all packaes

there still seams to be some small errors like after installing and updating to newst kernel i have to do a manually fsck  and last i tryed i had problems building nividia kernel (gave up migth be better now)

but all in all i like it 

by the way i dont seam to be able to chance login screens look (it allways ther first thing i do i like simpel with face then i chance background to plain black)

there also seam to be some probs with locking memmeory and you have to edit limits.config manually 
to get realtime 

updating from old ubuntu was a headegg for me gave up no wireless whatever you do god luck

---

### Post by tinawina on 2009-09-30
hey jmfal and cookie55 - 

thanks for the info. 

i was reading that wifi screws up audio latency and that's why u-studio doesn't do well with it.

regardless, i want to play around with hydrogen and sooperlooper asap! wh means i need sound up and running. and i also need wifi since this is my home computing set-up. for me the least path of resistance is to install ubuntu 9.04 and then install audio software packages. i'll give your tips a whirl jmfal.

studio is a nice looking interface. maybe i can grab the studio skin? way cooler than anything i've seen in windows, mac, or ubuntu. but - function over form!

thanks for your help!

---

### Post by c00kie55 on 2009-09-30
i use this guide all the time [http://www.unix-tutorials.com/go.php?id=826](http://www.unix-tutorials.com/go.php?id=826)
it will give you wireless

also if you install as in my above post you will end up with ubuntustudio 9.10 alpha 6 with working wireless 
and jack realtime kernel if you just install the ubuntu desktop i think you will be missing realtime

if you fallow this guide remember not to reboot before your are all done (or else lan will be broken grr)
folow guide from this part (above dont seam to be needed in studio)
sudo apt-get install network-manager-gnome network-manager


and dont do this 

sudo /etc/init.d/dbus restart (reboot insted)

---

### Post by c00kie55 on 2009-09-30
ahh  i forgot that by deafult ubuntustudio 9.10 sound i on mute so you have to go to soundsettings and unmute then turn up volume but guess you already have tryed that

---

