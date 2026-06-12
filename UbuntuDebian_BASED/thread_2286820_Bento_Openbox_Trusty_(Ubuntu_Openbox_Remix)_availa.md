---
title: "Bento Openbox Trusty (Ubuntu Openbox Remix) available for test"
date: 2015-07-14
forum: Ubuntu/Debian BASED
---

### Post by Melodie on 2015-07-14
Hello,
This edition is the second since the 12.04 and has had many versions out previously, with tiny details improvements. What is it? I'll let you discover it here. Just let me tell you it's the work of many people, although led quietly without much advertising. The main goal is to have a almost "only Openbox" made easy to use and easy to customize.

Any questions? A wish, after testing? Just ask!
[http://linuxvillage.org/en/2015/07/bento-openbox-trusty-soon-final/](http://linuxvillage.org/en/2015/07/bento-openbox-trusty-soon-final/)

[IMG]http://linuxvillage.org/wp-content/uploads/2015/05/bento-vivid-rc4-640x478.png[/IMG]

---

### Post by sudodus on 2015-07-16
I'm testing **bento-trusty-rc2-i386.iso** live now (flashed with mkusb to a USB drive). It works very well so far, but I must admit that I liked your old wallpaper better ;-)

---

### Post by sudodus on 2015-07-16
Is there some particular program or task, that you want us to test?

---

### Post by Melodie on 2015-07-17
> **sudodus said:**
> Is there some particular program or task, that you want us to test?

Hi sudodus,

Yes please, if lightdm-gtk-greeter-settings could be tested extensively*, and also to be checked, if zram-config works right. (I has to produce one block device per cpu, you can check the output of "cat /proc/cpuinfo"). And the usual other things, connection Ethernet, wifi, sound... loud speakers...

Thanks. :)

PS: * just because in my install this bug reappeared after I tried to change a detail:
[https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/1460303](https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/1460303)

---

### Post by anakai on 2015-07-23
There is also:
[https://unit193.net/icebox/](https://unit193.net/icebox/)
Wich I think is one of the developer of xubuntu, he has one openbox iso on his site made from ubuntu base. I think it is nice, but I don't like openbox.

---

### Post by Portaro on 2015-07-23
Nice I follow this distro and I comment on a posts but never receive a answer to my comments.

Have a nice look and this is a good distro for old pcs or pcs with poor resources.

Thanks for share.

---

### Post by Melodie on 2015-07-26
> **anakai said:**
> There is also:
[https://unit193.net/icebox/](https://unit193.net/icebox/)
Wich I think is one of the developer of xubuntu, he has one openbox iso on his site made from ubuntu base. I think it is nice, but I don't like openbox.

Hello, 

I know it. I have tried and tested it, especially since Unit193 provided very interesting tech information to me which I intend to use in the Bento Openbox project. He is a very good dev indeed.

While Bento Openbox is dedicated to truly end users, with many details added along the years while presenting it to very end users IRL (the project was started in another GNU/Linux community) and will continue to be developed with the needs of the end users in mind, Icebox (Openbox Desktop by Unit193) is much more geeky. 

I have also listed all kinds of distributions coming with Openbox very lately, tested a few, among which an Italian version coming with GUI tools of their own, and I have created a page of wiki describing them all on the linuxvillage.org wiki (interacting too with the ubuntu-fr.org wiki). I plan to translate it, or have it translated to English at some point in the future. You can have a look and either use translate.google and or click to the links on that page:
[http://wiki.linuxvillage.org/doku.php?id=fr:configuration:gestionnaire_de_fenetres](http://wiki.linuxvillage.org/doku.php?id=fr:configuration:gestionnaire_de_fenetres)

If you know other ones which aren't listed there, we can add them.

Meanwhile, please consider testing Bento Openbox and bring feedback. :)

---

### Post by Melodie on 2015-07-26
> **Portaro said:**
> Nice I follow this distro and I comment on a posts but never receive a answer to my comments. Have a nice look and this is a good distro for old pcs or pcs with poor resources.

Thanks for share.


Hello,

Where do you follow it and where have you posted? I usually never miss a reply and sooner or later I answer everyone. 

This distro has limits in matter of low resources : I consider it should not be installed to a machine with less than 756MB, and at least 1GB for a good experience. A processor with at least 1Mhz and a FSB not too low (to be tested on a per case basis). For machines with less resource there are other distributions which can allow using them (antiX, DSL, Slitaz, Puppy… )

Best regards,
Mélodie

---

### Post by Melodie on 2015-07-31
Hello,

Bento Openbox Trusty remix final will be out in a few hours! Both 32 and 64bits as live desktop are ready for all!

---

