---
title: "newbie:-  ubuntu 8.04.01 in VBox guest on XP"
date: 2008-10-28
forum: Virtualisation
---

### Post by ulindel on 2008-10-28
Installed Ubuntu 8.04.01 in VBox within XP. 

Tried to import bookmarks frm IE but says cannot find anything. 

The stock em program does not open up. 

Display has only 16 & 800x600. 

Does not import video driver. 

The window does not maximise leaving small space for ubuntu itself. 

Can you help?

---

### Post by bodhi.zazen on 2008-10-28
You need to install the virtualbox additions on the ubuntu guest.

I get the impression you do not understand the implications of virtualization. This of your ubuntu guest as a separate computer. The videocard, network card, CPU, everything are "virtual hardware" but the guest does not directly access your hard drive, or video card, or network card.

---

### Post by ulindel on 2008-10-28
Thanx,

I read the info how to use vb & ubuntu, but found it rather confusing after so long on MSWins.

Just to make sure I explained OK, I run VB within my XP & installed in it Ubuntu 8.

With the pointer in win. I clicked on devises<install guest additions, BUT nothing seems to happen.

---

### Post by bodhi.zazen on 2008-10-28
I understand, virtualization is not easy t first, neither is a new OS.

You can look here : [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

but also to install the additions you can not just click :(

---

### Post by ulindel on 2008-10-28
Thanx again,
just google how to install & found that had to find the iso on my HD put on a CD & then ubuntu accepted it.

Is getting late here, I'll boot up tomorrow & continue.

---

### Post by ulindel on 2008-10-29
Sorry fellows, 

but I read a dozen info on Vbox/ubuntu, on how to install guet additions, typed in hundreds of commands each asked me to, the devices>install guest additions does not work, even tried to install it by burning this "VBoxGuestAdditions.iso" on a CD, install wizard installs it, a directory is made " innotek VirtualBox Guest Additions" BUT nothing is happening.

And to add insalt too, on boot up meriads of text is dished out & then says your grafix are 800x600 & cannot change it or drivers.

VBox seats 6"x6" in the middle of a 20" screen & won't enlarge, grafix are 16, 800x400, nothing inmports etc.

I am in a stand still.

---

### Post by 080729jk on 2008-10-30
&#12288;&#12288; SEO &#26159;&#33521;&#25991;search engine optimization&#30340;&#32553;&#20889;&#65292;&#20854;&#20013;&#25991;&#24847;&#24605;&#26159;&#25628;&#32034;&#24341;&#25806;&#20248;&#21270;&#12290;[**&#21271;&#20140;SEO&#20844;&#21496;**](http://www.jingke.org/seo.htm)&#32780;&#20174;&#20107;&#36825;&#26041;&#38754;&#24037;&#20316;&#30340;&#23601;&#26159;search engine optimizer[**&#21271;&#20140;SEO**](http://www.jingke.org/seo.htm)&#65292;[**&#21271;&#20140;SEO**](http://www.jingke.org/seo.htm)&#25628;&#32034;&#24341;&#25806;&#20248;&#21270;&#24072;&#12290;[**&#21271;&#20140;SEO&#20844;&#21496;**](http://www.jingke.org/seo.htm)&#20182;&#20204;&#21033;&#29992;&#24037;&#20855;&#25110;&#32773;&#20854;&#20182;&#30340;&#21508;&#31181;&#25163;&#27861;&#20351;&#33258;&#24049;&#30340;&#21512;&#25628;&#32034;&#24341;&#25806;&#30340;&#25628;&#32034;&#35268;&#21017;&#20174;&#32780;&#33719;&#24471;&#36739;&#22909;&#30340;&#25490;&#21517;&#65288;&#20063;&#23601;&#26159;&#24120;&#35828;&#30340;&#32593;&#31449;&#20248;&#21270;&#65289;&#12290;[**&#21271;&#20140;SEO**](http://www.jingke.org/seo.htm)&#26080;&#27490;&#22659;&#22320;&#36861;&#27714;&#36739;&#21069;&#25490;&#21517;&#26159;SEO&#20204;&#19968;&#19990;&#30340;&#30446;&#26631;&#12290;

---

### Post by 080801jk on 2008-10-30
&#20135;&#21697;&#21517;&#31216;&#65306; &#23433;&#35834;&#20449;[**&#27004;&#23431;&#23545;&#35762;**](http://www.axjh.com.cn/lydj.htm)&#20027;&#26426; &#20135;&#21697;&#21806;&#20215;&#65306; 0-&#35831;&#30005;&#35810; &#20135;&#21697;&#35268;&#26684;&#65306; ANX-18B3 &#20135;&#21697;&#32534;&#21495;&#65306;  &#20135;&#21697;&#31867;&#21035;&#65306; &#23433;&#35834;&#20449;[**&#27004;&#23431;&#23545;&#35762;**](http://www.axjh.com.cn/lydj.htm) &#8594; &#21035;&#22661;&#31995;&#21015; &#20135;&#21697;&#20449;&#24687;&#65306;       &#20135;&#21697;&#21517;&#31216;&#65306; &#23433;&#35834;&#20449;[**&#27004;&#23431;&#23545;&#35762;**](http://www.axjh.com.cn/lydj.htm)&#20027;&#26426; &#20135;&#21697;&#21806;&#20215;&#65306; 0-&#35831;&#30005;&#35810; &#20135;&#21697;&#35268;&#26684;&#65306; ANX-20B &#20135;&#21697;&#32534;&#21495;&#65306;  &#20135;&#21697;&#31867;&#21035;&#65306; [**&#23433;&#35834;&#20449; **](http://www.axjh.com.cn/lydj.htm)&#27004;&#23431;&#23545;&#35762; &#8594; &#21035;&#22661;&#31995;&#21015; &#20135;&#21697;&#20449;&#24687;&#65306;       &#20135;&#21697;&#21517;&#31216;&#65306; &#27004;&#23431;&#23545;&#35762;&#20027;&#26426; &#20135;&#21697;&#21806;&#20215;&#65306; 0-&#35831;&#30005;&#35810; &#20135;&#21697;&#35268;&#26684;&#65306; AMX-28C &#20135;&#21697;&#32534;&#21495;&#65306;  &#20135;&#21697;&#31867;&#21035;&#65306;[**&#23433;&#35834;&#20449; **](http://www.axjh.com.cn/lydj.htm)&#27004;&#23431;&#23545;&#35762; &#8594; &#31649;&#29702;&#20027;&#26426; &#20135;&#21697;&#20449;&#24687;&#65306;

---

### Post by icodeme on 2008-10-30
Could you please throw a screenshot for people to see :)

---

### Post by ulindel on 2008-10-30
scrnshot of what exactly, these?

[[IMG]http://img221.imageshack.us/img221/2227/fsscr000ea3.th.png[/IMG]](http://img221.imageshack.us/my.php?image=fsscr000ea3.png)[[IMG]http://img221.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img100.imageshack.us/img100/1706/fsscr002mx3.th.png[/IMG]](http://img100.imageshack.us/my.php?image=fsscr002mx3.png)[[IMG]http://img100.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

PS. Say, just noticed my signuture is of the old system, but cannot overwrite it, here is the new:

Asus P5K Premium WiFiiFi Intel ,
AMI Bios 11Oct08  to 0702  update  2008/07/29   Version: 62.92.38.00.05
Intel Core 2 Quad Pro Q6600 95W 2.4GHz, Rev GO, stepping B
OCZ Vendetta Cpu Cooler, 
2x2GB, 240-pin DIMM, DDR2 800 (400mhz) PC2-6400, 
EVGA GeForce 9800 GTX KO 512MB GDDR3 (PCI-E), 
Maxtor sata 160gb, 
OCZ 600W Game XStream Psu, 
X45,XPpro sp2/Ubuntu 8.04.1

---

### Post by Deten on 2008-10-30
do any of these virtual drive programs have video hardware support?  I am on ubuntu and boxing XP

---

