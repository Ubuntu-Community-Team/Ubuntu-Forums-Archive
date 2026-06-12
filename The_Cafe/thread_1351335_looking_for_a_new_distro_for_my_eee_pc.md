---
title: "looking for a new distro for my eee pc"
date: 2009-12-10
forum: The Cafe
---

### Post by markp1989 on 2009-12-10
I have used arch on this for a while, after the last update ended up breaking my system (my fault, ran out of space part way through the update)

i want somthing like arch, bare minimal , with editable init scripts (BSD-style like arch, so i can remove bits that arent needed or customize the script like i did with arch), but without the rolling release?

is there a distro like this?

thanks Markp1989

---

### Post by snowpine on 2009-12-10
SliTaz is a fun little EEE distro. It's quite minimalistic (you can even do a CLI-only install, if 30mb is too big for you) and has the Arch-like init scripts you're looking for. You have your choice of rolling (cooking) or once-a-year stable releases. It also has the TazUSB installer, fantastic if you want to test drive from a thumb drive or SD card.

---

### Post by markp1989 on 2009-12-10
> **snowpine said:**
> SliTaz is a fun little EEE distro. It's quite minimalistic (you can even do a CLI-only install, if 30mb is too big for you) and has the Arch-like init scripts you're looking for. You have your choice of rolling (cooking) or once-a-year stable releases. It also has the TazUSB installer, fantastic if you want to test drive from a thumb drive or SD card.

That sounds perfect, il give it a go, and report back :D 

thankyou :D

---

### Post by snowpine on 2009-12-10
You might have to configure wireless drivers, correct xorg settings, etc. yourself. But I'm sure you can handle that since you are familiar with Arch. Drop by the SliTaz forums while you're at it; there used to be a mega-thread with EEE tips and tricks (and maybe even an EEE-specific remix if I remember correctly).

I'd help you myself, but I recently hopped back to Arch on my netbook. :)

EDIT: Here's the eee remix: [http://download.tuxfamily.org/slitaz/iso/cooking/flavors/](http://download.tuxfamily.org/slitaz/iso/cooking/flavors/)

---

### Post by ajgreeny on 2009-12-10
Seeing as this is a ubuntu forum, have you considered using the minimal install CD and adding just what you want from the repos, eg lxde, xorg and xdm for a very light desktop, firefox and thunderbird for internet, and maybe gnumeric and abiword for office alternatives.  I'm not sure about the wireless situation with lxde.

I used this, just to try it out on a very small partition on my desktop machine about a year ago, and was impressed.  I think it could be made to work very well on a netbook machine.  I realise you have no CD on a netbook, but there are ways around that as you must know.

---

### Post by starcannon on 2009-12-10
I have 2 Asus Eee 4g's(701) and 1 Asus Eee 8g(702) and I simply put a 16gb SDHC card in the card reader slot, and put on a regular install of Ubuntu and then switched to the Array.org kernel. It runs great, plenty of space for what I do, and with the Array kernel it suspends/resumes/hibernates/wakes up just fine, and with a script I even have cpu throttling and clocking to the full 900mhz capability.

GL and HF
[http://array.org/ubuntu/](http://array.org/ubuntu/)

[16gb SDHC cards]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170068%201053325334&bop=And&ActiveSearchResult=True&Order=PRICE") I use the AData one.

[32gb SDHC cards]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170068%201053325335&name=32GB") NOT the CF card, you want the SDHC cards.

---

### Post by Wiebelhaus on 2009-12-10
Build your own from [scratch]("http://www.linuxfromscratch.org/").

---

### Post by markp1989 on 2009-12-10
> **snowpine said:**
> You might have to configure wireless drivers, correct xorg settings, etc. yourself. But I'm sure you can handle that since you are familiar with Arch. Drop by the SliTaz forums while you're at it; there used to be a mega-thread with EEE tips and tricks (and maybe even an EEE-specific remix if I remember correctly).

I'd help you myself, but I recently hopped back to Arch on my netbook. :)

EDIT: Here's the eee remix: [http://download.tuxfamily.org/slitaz/iso/cooking/flavors/](http://download.tuxfamily.org/slitaz/iso/cooking/flavors/)

hey, thanks :d im useing the eee remix of slitaz (posting form it now) 

@ajgreeny - i used to use ubuntu minimal on my eee, but i found no matter how light i got the DE/WM the ubuntu base still took too long to boot for me (its a netbook so i dont leave it on, and standby is rubbish on here, still uses up alot of battery power when in standby) 

slitaz isnt booting as fast as i had my arch install going, but give me a few days ,, and i will see what i can do to speed it up .

thanks to all who replied here :D

---

