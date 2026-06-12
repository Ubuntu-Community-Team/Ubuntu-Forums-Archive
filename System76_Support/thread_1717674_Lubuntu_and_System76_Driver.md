---
title: "Lubuntu and System76 Driver"
date: 2011-03-30
forum: System76 Support
---

### Post by vttay03 on 2011-03-30
--I currently have Ubuntu 10.04 installed on my star1.  While everything works wonderfully, it is a little sluggish (I was never a fan of the UNR and have always just kept the desktop version of Ubuntu installed).  So last night I downloaded Lubuntu and made a bootable USB in order to try it out.  I was extremely impressed, everything was quite a bit snappier as expected.  So I'm interested in installing this on my Starling, will I have any issues in getting the System76 driver installed?  Of course it's a must for the wireless issues...otherwise the netbook is basically useless.  I know the System76 driver is truly only guaranteed to work with the Ubuntu, but wanted to know if there were any obvious reasons why it wouldn't work with Lubuntu.  Any help/insight is appreciated.

---

### Post by jml on 2011-03-30
I'm not a programmer, but I recall reading here that the driver package is basically a Perl script that "reads" what version of ubuntu you have installed and then installs the correct binary bits to make the wireless usable, along with other tweaks I assume.  hopefully, a S76 rep will chime in and answer with more specific details.  specifically will it recognize Lubuntu and will the driver work.  Good luck.

Joe

---

### Post by isantop on 2011-03-30
You shouldn't have any trouble as long as Lubuntu reports itself as Ubuntu. Then, it's just like Kubuntu or Xubuntu, etc.

That said, we seem to have a bug floating around that breaks wireless on 10.04 with the latest System76 Driver. We haven't confirmed this, but we are looking into it.

---

### Post by vttay03 on 2011-03-30
Ahhh so that may explain my wireless issues as of late...if I just rollback the driver version, I should be back up and running, right?

---

### Post by isantop on 2011-03-31
In theory, and it's definitely worth a try.

---

### Post by dct35115 on 2011-05-01
I have a panp5, circa Summer 2009.  I'm going to give Unity a try on LiveCD or in VirtualBox.  But I'm trying to do some leg work ahead of time on other options if I don't like Unity.  I did a LiveCD of Mint 10 and wireless worked no problem.  I did not try the webcam yet.  I also downloaded Xubuntu 11.04 and tried it on LiveCD and wireless worked [but did not try the webcam].

So a couple of questions: 
1] Besides wireless and the webcam, what else does the System76 driver likely provide for a panp5 for August 2009?

2] A comment in this tread intimated that Xubuntu will "identify itself" as Ubuntu and the inference is that the System76 driver will work no problem for Xubuntu.  Did I understand that correctly?  If I do a fresh install of Xubuntu 11.04 can I download and install the System76 driver?

3] Forgive my ignorance but did wireless work on the Mint 10 LiveCD test because of the System76 driver that is present in the Ubuntu 10.04 install OR did I just get luck that Mint 10 recognized the wireless card?  Might I also get so lucky with the webcam? :)

Thanks!

---

### Post by jdb on 2011-05-02
> **dct35115 said:**
> 
2] A comment in this tread intimated that Xubuntu will "identify itself" as Ubuntu and the inference is that the System76 driver will work no problem for Xubuntu.  Did I understand that correctly?  If I do a fresh install of Xubuntu 11.04 can I download and install the System76 driver?

The System76 drivers work fine with Xubuntu

jdb

---

### Post by samalex on 2011-05-02
> **jdb said:**
> The System76 drivers work fine with Xubuntu

jdb

Awesome!  I was just coming in here to ask this exact question since I hope to move from Ubuntu 10.04 to Xubuntu 11.04 on my PanP5.  Also just curious what Network Manager comes with Xubuntu?  I like the one that Gnome uses, which I think is just called NetworkManager, but i wasn't sure if Xubuntu used something else.

Thanks :)

Sam

---

### Post by jdb on 2011-05-02
> **samalex said:**
> Awesome!  I was just coming in here to ask this exact question since I hope to move from Ubuntu 10.04 to Xubuntu 11.04 on my PanP5.  Also just curious what Network Manager comes with Xubuntu?  I like the one that Gnome uses, which I think is just called NetworkManager, but i wasn't sure if Xubuntu used something else.

Thanks :)

Sam

It comes with network-manager.

jdb

---

