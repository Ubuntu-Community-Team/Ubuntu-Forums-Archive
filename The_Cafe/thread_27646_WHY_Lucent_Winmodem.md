---
title: "WHY? Lucent Winmodem"
date: 2005-04-17
forum: The Cafe
---

### Post by Insane on 2005-04-17
Well, I am going to ask this now, and please note I do not even want the WORD terminal or anything mentioned. Just PLEASE give me EXACT instructions on how to make my Lucent WInmodem work with Ubuntu Hoary.

PLEASE! Exact. Like in Click there, type that, and voilla!

I hope you understand. I NEED it to work, and very quickly, at that.

Thank you! O:)

---

### Post by KiwiNZ on 2005-04-17
[http://www.linmodems.org/](http://www.linmodems.org/)  This is your best bet

---

### Post by Insane on 2005-04-17
[QUOTE=KiwiNZ][http://www.linmodems.org/](http://www.linmodems.org/)  This is your best bet[/QUOTE]
 You do not know how many times I have been sent to that site. I cannot take it anymore. It doesn;t help me because they give instructions as if you should know everything already.

I am a newby, in fact, there isn;t even a word to describe my newby-ness.

---

### Post by Insane on 2005-04-17
IE they give things like this:

> After decompression (command gunzip scanModem.gz ), do not forget to make it executable with chmod +x scanmodem or trigger it with source scanmodem .

I have absolutly NO IDEA what that means. :'(

---

### Post by KiwiNZ on 2005-04-17
add one of the following two lines to your  /etc/apt/sources.list and let apt-get do the rest for you:   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


 To add the repositories sudo gedit , open the /etc/apt/sources.list  . Add those lines and save .

---

### Post by CRCampbell on 2005-04-17
[QUOTE=KiwiNZ]add one of the following two lines to your  /etc/apt/sources.list and let apt-get do the rest for you:   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


 To add the repositories sudo gedit , open the /etc/apt/sources.list  . Add those lines and save .[/QUOTE]


If he can't get his winmodem to work under linux, how do you expect him to apt-get anything?

About winmodems:  they are a pain.  I never could get mine to work.  Your best bet is the go out and buy a external serial modem.  

If you're that much of a newbie, I'd suggest reading some basics about linux before adventuring on.  If you aren't willing to command line anything, linux isn't the OS for you.

---

### Post by KiwiNZ on 2005-04-17
Doh! :-#](*,) My bad

I just  saw what I wrote , damm , well it was at  the end of a long hard day demolishing an old barn like garage.

Anyway a PC with Internet is available . Down load the files , burn to CD , add the Cd to the repositories and again let apt do its thing .

But to be honest , Winmodems are a pain , designed to work on a flakey system(windows) and as such are flakey beasts.

If your budget can handle it , it would be better if you can get yourself a new "hardware " modem.

---

### Post by Brunellus on 2005-04-17
[QUOTE=Insane]

PLEASE! Exact. Like in Click there, type that, and voilla!

[/QUOTE]

I hate to be the one to tell you this, but there is no 'click here, type that' way to get a lucent winmodem up and running  under Linux...

---

### Post by az on 2005-04-17
You will need the terminal, but it is not that difficult.  Read here.  Ask questions if you need info for a particular step.


[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)


"About winmodems: they are a pain. I never could get mine to work. Your best bet is the go out and buy a external serial modem."

I would say that more than 50 per cent of winmodems have linux support today.


"If you're that much of a newbie, I'd suggest reading some basics about linux before adventuring on. If you aren't willing to command line anything, linux isn't the OS for you."

Actually, this is the kind of thing that will make you realise the power of the command line.  I would never have learned some things if I was never faced with _Having_ to do it.  I think this applies to the desktop user, too.

---

### Post by az on 2005-04-17
[QUOTE=Brunellus]I hate to be the one to tell you this, but there is no 'click here, type that' way to get a lucent winmodem up and running  under Linux...[/QUOTE]


Heheheh!  The lt-modem modules are in linux-restricted-modules and are available through synaptic on your cd!

To be fair, you will have to do some command line things to load the modules.

sudo modprobe lt_serial 
sudo modprobe lt_modem

To edit files as is described, do 
sudo gedit
as for step 3,  just use /dev/ttLTM0.

The rest of the dialup configuration can be done with the networking thing.

---

