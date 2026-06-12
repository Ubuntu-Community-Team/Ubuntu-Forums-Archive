---
title: "No Sound From M-Audio 24/69 PCI Card"
date: 2009-07-31
forum: Ubuntu Studio
---

### Post by mogui_666 on 2009-07-31
Hi i have just install Ubuntu 9.04 in a new computer. but i can get any sound from my m-audio 24/69 sound card. below is a screen short of the error window.

[IMG]http://img382.imageshack.us/img382/3489/61056408.png[/IMG]

what should i do??

Thanks in advance

---

### Post by martinbaselier on 2009-07-31
You could try to switch to OSSv4. You card is supported by it.

---

### Post by tgalati4 on 2009-07-31
What is the output of:
aplay -l

Install envy24control if you haven't already:
sudo apt-get install envy24control

Run it:

envy24control

---

### Post by mogui_666 on 2009-07-31
> **martinbaselier said:**
> You could try to switch to OSSv4. You card is supported by it.

eh...where do i get this OSSv4??

> **tgalati4 said:**
> What is the output of:
aplay -l

Install envy24control if you haven't already:
sudo apt-get install envy24control

Run it:

envy24control 

here is what i get when i key "aplay -l" in terminal.
> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


i have try to install envy24control. but nothing happen...

---

### Post by igorzwx on 2009-07-31
to install OSS4, follow this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 
 
[B]
[/B]

---

### Post by tgalati4 on 2009-07-31
Well, we know that your m-Audio card is recognized as Card 1.  What happens when you run envy24control in a terminal?

I'm not near my ubuntu machine to test it but also try:

man envy24control

There may be a switch needed to find the second sound card.

---

### Post by sgx on 2009-07-31
> **mogui_666 said:**
> eh...where do i get this OSSv4??



here is what i get when i key "aplay -l" in terminal.


i have try to install envy24control. but nothing happen...
Hi, install envy24control with synaptic, then when you run it, the analog outputs will be off-screen, so use the slider widget at the bottom of the interface. Disable the other nvidia hda soundchip in the bios, reboot, and run the command

sudo alsaconf

Follow the prompts, it will configure things, and raise the volume on the soundcard for you. Run the command

envy24control     or start it from a menu item, find the analog outputs, adjust as desired. Read up on using the software. It's an excellent card, but keep in mind newer ones are reportedly not working in linux, while ones several years old do quite well.

Cheers

---

### Post by mogui_666 on 2009-08-01
hi guy, thanks for the time and the advice....but i am just a new starter in ubuntu...so please be patience with me. Sometime i can ask really stupid questions.thanks again=)

> ...run the command

sudo alsaconf



ok i think i got envy24control install in my computer. but where do i run this command?? In terminal??:confused:

---

### Post by igorzwx on 2009-08-01
Do not worry!
It is not difficult.
Perhaps, you should start here:
[https://help.ubuntu.com/9.04/advanced-topics/C/index.html](https://help.ubuntu.com/9.04/advanced-topics/C/index.html)

[Using the Command Line 		]("https://help.ubuntu.com/9.04/basic-commands/C/")

---

### Post by igorzwx on 2009-08-01
or here:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

**Using the Terminal**

Contents

[LIST=1]
[*][Why?]("https://help.ubuntu.com/community/UsingTheTerminal#Why?")
[*][Using this page]("https://help.ubuntu.com/community/UsingTheTerminal#Using%20this%20page")
[*][Starting a Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal")
[LIST=1]
[*][In Gnome (Ubuntu)]("https://help.ubuntu.com/community/UsingTheTerminal#In%20Gnome%20%28Ubuntu%29")
[*][In Xfce (Xubuntu)]("https://help.ubuntu.com/community/UsingTheTerminal#In%20Xfce%20%28Xubuntu%29")
[*][In KDE (Kubuntu)]("https://help.ubuntu.com/community/UsingTheTerminal#In%20KDE%20%28Kubuntu%29")
[/LIST]
[*][Commands]("https://help.ubuntu.com/community/UsingTheTerminal#Commands")
[LIST=1]
[*][sudo: Executing Commands with Elevated Privileges]("https://help.ubuntu.com/community/UsingTheTerminal#sudo:%20Executing%20Commands%20with%20Elevated%20Privileges")
[*][File & Directory Commands]("https://help.ubuntu.com/community/UsingTheTerminal#File%20&%20Directory%20Commands")
[*][System Information Commands]("https://help.ubuntu.com/community/UsingTheTerminal#System%20Information%20Commands")
[*][Adding A New User]("https://help.ubuntu.com/community/UsingTheTerminal#Adding%20A%20New%20User")
[/LIST]
[*][Options]("https://help.ubuntu.com/community/UsingTheTerminal#Options")
[*]["Man" and getting help]("https://help.ubuntu.com/community/UsingTheTerminal#%22Man%22%20and%20getting%20help")
[LIST=1]
[*][Searching for man files]("https://help.ubuntu.com/community/UsingTheTerminal#Searching%20for%20man%20files")
[/LIST]
[*][Other Useful Things]("https://help.ubuntu.com/community/UsingTheTerminal#Other%20Useful%20Things")
[LIST=1]
[*][Prettier Manual Pages]("https://help.ubuntu.com/community/UsingTheTerminal#Prettier%20Manual%20Pages")
[*][Pasting in commands]("https://help.ubuntu.com/community/UsingTheTerminal#Pasting%20in%20commands")
[*][Save on typing]("https://help.ubuntu.com/community/UsingTheTerminal#Save%20on%20typing")
[*][Change the text]("https://help.ubuntu.com/community/UsingTheTerminal#Change%20the%20text")
[/LIST]
[*][More ways to run a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#More%20ways%20to%20run%20a%20terminal")
[*][More Information]("https://help.ubuntu.com/community/UsingTheTerminal#More%20Information")
[/LIST]

---

### Post by sgx on 2009-08-01
> **mogui_666 said:**
> hi guy, thanks for the time and the advice....but i am just a new starter in ubuntu...so please be patience with me. Sometime i can ask really stupid questions.thanks again=)



ok i think i got envy24control install in my computer. but where do i run this command?? In terminal??:confused:
Hi, alsaconf is run from a terminal as root user  

mogui$sudo alsaconf

sudo alsaconf
envy24control can be started as a command by normal user

mogui$envy24control

or look in the Ubuntu audio menus, and choose it there.
Its just a nice mixer, and audio preferences gui for m-audio
or similar envy24 soundchip based soundcards.

Cheers

---

