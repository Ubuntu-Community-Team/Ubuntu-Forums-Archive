---
title: "Input methods (or the lack of such) for Asian languages"
date: 2005-10-13
forum: The Cafe
---

### Post by Rounin on 2005-10-13
Continuing the discussion from the Development Forum, I think it's a shame that Breezy currently only has one available solution for multilingual input, that is, UIM, or Universal Input Method.

While UIM is a good solution for languages like Japanese and Korean, it's sometimes difficult to use when one needs to switch between several input methods, and it's not very innovative when it comes to inputting Chinese.

The two other solutions that I know of are SCIM (Smart Common Input Method) and IIIMF - SCIM's currently included in Ubuntu, but has a bug that causes it to segfault under Breezy, even when compiled from source. This might be solved by upgrading the package to a newer version. IIIMF is also included, but the actual input methods for IIIMF as a rule aren't. The input methods that ARE included don't seem to do anything when one starts them up, either, though I'm aware that at least one of them requires the user to start up an additional server, which as far as I'm concerned makes it useless for anyone but experts.

I have to add that I think UIM is already a very good solution for multilingual input which should suit a lot of users, but it's not so good that it's a good idea to drop all the other available solutions. There are billions of people living in Asia, and if we want them to be able to use Ubuntu (not to mention if we want *me* to be able to use it), there has to be some no-config, no-hassle methods available for inputting Asian languages.

---

### Post by kairu0 on 2005-10-14
I agree completely. I have been toying with the idea of Kubuntu for a while, but the fact is that with a broken SCIM it would be very hard. I already have UIM working beautifully in Xubuntu, but I've never been able to use UIM in KDE.

So, my options are a segfaulting SCIM and UIM (and maybe IIIMF, but I can't find any documentation for Ubuntu about it.

The SCIM seg fault has been occuring since at least Colony 3 for me.

Anyone know how to use UIM in KDE? Last time I tried it only worked in GTK applications.

---

### Post by Marc Higgins on 2005-11-15
We live & work in Seoul Korea so Korean input is fairly important for us.

In terms of input methods alternatives we have tried are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.

imhangul (0.9.11-1)
language-pack-gnome-ko (20051011)
language-pack-gnome-ko-base (20051011)
language-pack-ko (20051011)
language-pack-ko-base (20051011)
language-support-ko (20051010)
libnspr4 (2:1.7.12-1ubuntu1)
mozilla-browser (2:1.7.12-1ubuntu1)
mozilla-firefox-locale-ko (1.0-1ubuntu1)
mozilla-locale-ko (1.7-1)
nabi (0.15-1)
openoffice.org2-help-ko (1.9.129-0.1ubuntu5)
openoffice.org2-l10n-ko (1.9.129-0.1ubuntu3)
ttf-alee (4.7ubuntu1)
ttf-unfonts (1.0.1-2ubuntu1)
xfonts-baekmuk (2.2-1ubuntu1)


Then I have  

#sudo dpkg-reconfigure locales

decided i didn't really need 50 differnet kinds of english but i did need Korean, so  i selected the following; 

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

the quick way to achivev the same this is sudo nano /etc/locale.gen  edit it to look like this & save it

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

then run 

 sudo locale-gen

But when i run nabi for the term i see;

Nabi: Can't load config file
Nabi: xim server started

It starts but there are no fonts

---

