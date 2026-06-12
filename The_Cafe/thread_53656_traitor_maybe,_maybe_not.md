---
title: "traitor? maybe, maybe not"
date: 2005-08-01
forum: The Cafe
---

### Post by brickbat on 2005-08-01
Hi,

For some reason my Ubuntu stopped being able to burn to cd/dvd.  I got very frustrated and installed Fedora Core 4.  It rocks! If you are between Ubuntu releases like me, I recommend it.  It feels quite a bit faster and more responsive. On a 500mhz machine any performance spurts you can get are valuable.

When Breezy comes out properly I will probably install it over my sick Hoary.  I miss apt-get and synaptic but fc4 rpms are everywhere and there is yum

The sad thing is that I moved to linux so I wouldnt have to install windows every 3 months.  At least now I am getting new features every time I do it! Thats life.

On a day to day basis they are functionally the same. gnome, firefox,thunderbird,openoffice,audacity,etc.

The strange thing is that the only app I installed before my cd/dvd burning died was opera 8.  I don't get it.

ciao
bb

---

### Post by aysiu on 2005-08-01
Sounds as if you could use a separate /home partition... if you don't already have one. Then, you can install and reinstall to your heart's content.

---

### Post by davidgypsy on 2005-08-01
[QUOTE=brickbat]Hi,

For some reason my Ubuntu stopped being able to burn to cd/dvd.  I got very frustrated and installed Fedora Core 4.  It rocks!
bb[/QUOTE]

How could you be a traitor if you still use Linux? Under the skin they are still essentially the same. I am dual booting Debian and Ubuntu to decide which to use full time. ;-)

---

### Post by darkoptix on 2005-08-01
I found Fedora slower personally...

---

### Post by kanem on 2005-08-01
[QUOTE=brickbat]For some reason my Ubuntu stopped being able to burn to cd/dvd.[/QUOTE]This has happened to me and a few other Ubuntu users. There is maybe one thread about it, but it was hard to find.

Anyway, I figured out what happend (in my case at least) after many frustrating hours.

HAL has to be a member of some groups for all the automounting and burning goodness to work. When adding a new user using the System->Administration->Users & Groups GUI it sometimes (sometimes, arrggh, this was why it was so hard to pin down). It sometimes removed hal from those groups in /etc/group and so no more cd burning.

Edit: Dammit!!! As I was checking exactly which file it was that was the problem I see that my /etc/group doesn't have hal anywhere in it. Hmm, maybe it was a different file? Nope. I Check to see if I can burn cds and get nothing but the evil burn to file image option. Oh well, at least I know how to fix it now. But I haven't added any other users recently so something else caused it this time.

---

### Post by sapo on 2005-08-01
Deserter!  We are gonna kill you... but before it we are gonna make a torture session heheh  :-P 

Btw.. i m in love with ubuntu.. even if people say that is there another stuff better out there... i cant change to another OS... i m in love with this comunity...

Never met people like there are here in the ubuntu comunity, people that doesnt hate windows users nor newbies, and when you ask a freaking dumb question.. the answer it without saying "go away noob".

Thats why i love ubuntu  :grin: 

And of course.. is a god damn f***** good OS  :grin:

---

### Post by davidgypsy on 2005-08-01
[QUOTE=sapo] 
Btw.. i m in love with ubuntu.. even if people say that is there another stuff better out there... i cant change to another OS... i m in love with this comunity...

Never met people like there are here in the ubuntu comunity, people that doesnt hate windows users nor newbies, and when you ask a freaking dumb question.. the answer it without saying "go away noob".

Thats why i love ubuntu  :grin: 
[/QUOTE]

I concur. Best community there is by far!!!

---

### Post by Juergen on 2005-08-01
Bah: go away noob 
:-)

I think many of those changing to Linux just ignore(d) their problems with windows and never tried to ask a question in a windows-newsgroup/-forum.
They aren't friendlier there as in Linux forums AFAIK, especially the international groups.

As a Windows-Developer (only at work, don't blame me! ;-)) I read some of the german NGs, and they are a bit more tolerant.
Nothing comes near to the Ubuntu-community, of course ;-)

BTW: the term 'zealot' I had to look up in WikiPedia. It seems not to be in my 'normal' dictionaries.

---

### Post by brickbat on 2005-08-02
[QUOTE=Juergen]Bah: go away noob 
:-)

BTW: the term 'zealot' I had to look up in WikiPedia. It seems not to be in my 'normal' dictionaries.[/QUOTE]

try "define: zealot" in google

---

### Post by npaladin2000 on 2005-08-02
I had more trouble with Fedora, actually.  But that's because their PalmPilot support is broken, and not looking like it's gonna get fixed soon.   But the theme is great, and it's ALMOST as good as Ubuntu....except yum is kind of a wannabe APT.  And the Yumex GUI frontend is UTTERLY inferior to Synaptic. 

This is easy to fix in FC4 though.. Make sure the extras yum repository is enabled, and then type "yum install synaptic."  That's right, Synaptic and apt-rpm are right in Fedora's own repositories....I do NOT get why they're bothering with yum...just include APT!

---

### Post by brickbat on 2005-08-05
Synaptic.......yum.

I just installed it. Thanks.

---

### Post by Lovechild on 2005-08-05
I welcome yet another user to a distro that actually works, there's absolutely no shame in using Fedora Core it's an excellent distro - I personally stick to the development branch since I like partaking in the discovery of bugs.

---

