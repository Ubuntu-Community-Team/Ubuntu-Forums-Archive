---
title: "How to get Hugin to work"
date: 2008-09-04
forum: Ubuntu Studio
---

### Post by paltwo on 2008-09-04
I have Ubuntu 8.04 installed. I installed Hugin with Synaptic. When I have completed a panorama with some photos and wants to save it, Hugin crasches. I started Hugin from a shell and it says "Could not load pano13". With Hugin libpano12 is installed. I can't install libpano13 with the packet installer (downloaded a .deb). I get the error "Error: Dependency is not satisfiable: libpano13-0".

How do I get Hugin to work?

Peter

---

### Post by cotcot on 2008-09-05
Could not reproduce your problem. I have hugin 0.7 beta4 fully normal from the repos and libpano12. I started hugin from terminal and made a panorama. No error, no crash, no question for libpano13. 

Have you tried [[COLOR="Blue"]fotoxx[/COLOR]]("http://kornelix.squarespace.com/downloads/") ? It works fine.

---

### Post by paltwo on 2008-09-08
> **cotcot said:**
> Could not reproduce your problem. I have hugin 0.7 beta4 fully normal from the repos and libpano12. I started hugin from terminal and made a panorama. No error, no crash, no question for libpano13. 

Have you tried [[COLOR="Blue"]fotoxx[/COLOR]]("http://kornelix.squarespace.com/downloads/") ? It works fine.

What version of Ubuntu do you use?? I have 8.04 LTS.

I have re-installed Hugin and the same happends every time.

I can't install fotoxx. I get tons of errors starting with something that seems like I haven't got "gtk+-2.0" .

Im really frustrated now with this Hugin. Somewhere in the OS there must be something that tells Hugin it shall use libpano13. Where can I find that?

Im close to giving up on this one.

Peter P.

---

### Post by 080711jk on 2008-09-10
&#20140;&#25644;&#23478;&#20844;&#21496;-&#21271;&#20140;&#25644;&#23478;-&#25644;&#23478;-&#25644;&#23478;&#20844;&#21496;-&#21271;&#20140;&#24425;&#34425;&#25644;&#23478;&#26377;&#38480;&#20844;&#21496;010-65487131.&#21271;&#20140;&#25644;&#23478;&#20844;&#21496;&#25104;&#31435;&#20110;1995&#24180;&#12290;&#32463;&#36807;&#20960;&#24180;&#30340;&#19981;&#25032;&#21162;&#21147;&#65292;[**&#21271;&#20140;&#25644;&#23478;**](http://www.bjbanjiags.com.cn/)&#24320;&#25299;&#21457;&#23637;&#65292;&#29616;&#24050;&#25104;&#20026;&#21271;&#20140;&#35268;&#27169;&#26368;&#22823;&#30340;&#19987;&#19994;&#25644;&#23478;&#65288;&#29289;&#27969;&#65289;&#20844;&#21496;&#12290;[&#21271;**&#20140;&#25644;&#23478;&#20844;&#21496;**](http://www.bjbanjiags.com.cn/)&#29616;&#25317;&#26377;&#21508;&#31867;&#36816;&#36755;&#36710;&#36742;&#12289;&#26426;&#26800;&#35774;&#22791;270&#22810;&#21488;&#22871;&#12290;&#20844;&#21496;&#20197;&#23621;&#27665;&#12289;[**&#25644;&#23478;&#20844;&#21496;**](http://www.bjbanjiags.com.cn/)&#20225;&#20107;&#19994;&#25644;&#22330;&#20026;&#22522;&#30784;&#65292;&#24314;&#31435;&#36215;&#24066;&#20869;&#29289;&#27969;&#12289;&#24037;&#19994;&#25644;&#22330;&#12289;[**&#21271;&#20140;&#25644;&#23478;&#20844;&#21496;**](http://www.bjbanjiags.com.cn/)&#23567;&#20214;&#24555;&#36816;&#12289;&#38598;&#35013;&#31665;&#36816;&#36755;&#12289;[**&#21271;&#20140;&#25644;&#23478;&#20844;&#21496;**](http://www.bjbanjiags.com.cn/)&#24066;&#20869;&#37197;&#36865;&#20026;&#20027;&#30340;&#36816;&#36755;&#20307;&#31995;&#65292;&#22521;&#32946;&#20986;&#19968;&#25209;&#32463;&#39564;&#20016;&#23500;&#30340;&#19987;&#19994;&#38431;&#20237;&#65292;&#23545;&#25152;&#26377;&#39640;&#26723;&#23478;&#20855;&#65292;&#38050;&#29748;&#12289;&#31354;&#35843;&#12289;&#22823;&#22411;&#26426;&#22120;&#31561;&#20855;&#26377;&#25216;&#26415;&#31934;&#36890;&#19987;&#19994;&#20154;&#21592;&#25286;&#35013;&#21450;&#25644;&#21160;&#65292;&#19968;&#26465;&#40857;&#26381;&#21153;&#12290;&#25552;&#20379;&#38271;&#12289;&#30701;&#36816;&#36755;

---

### Post by kornelix on 2008-09-10
fotoxx - looks like you need to install the gtk2-dev package, as shown on the download page for fotoxx.

---

### Post by cotcot on 2008-09-10
I am using 8.04 LTS (64 bit) and I have libgtk2.0-dev installed.
libpano13 seems to be available [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/en/intrepid/libpano13-0")

---

### Post by Fnx on 2008-09-10
I am using (K)ubuntu 8.04.1 (AMD 32bits) and I cannot reproduce your error.
Hugin 0.7beta4 works.

---

### Post by paltwo on 2008-09-11
One step on the road....

Now I managed to install libpano-13 and when I run Hugin I don't get any messages about that. Still when I hit the save-button to save my panorama as a *.tif file I get a segmentation fault.

The last one says (from the syslog):

Sep 11 20:45:07 Castor kernel: [  176.287937] hugin[5988]: segfault at 00000000 eip b6d26283 esp bf8bca1c error 4

Something in the back of my head says that seg fault is a memory fault, right? I remember something about getting this when running 64-bit applications with large memory demand on 32-bit stations. Can someone understand what the error message means?

My computer is an old Dell Dimension 4600 with 1,5Gb of RAM.

The good thing is that I am learning a lot. I really hope its worth the frustration because Hugin seems really fun and I got some perfect set of photos I wanna try it with.

Peter P.

---

### Post by paltwo on 2008-09-11
OK, the problem seems to be solved. I got an idea that perhaps Hugin didn't like either the use of a Swedish letter in the name of the directory I was working in (umlaut-o 'ö') or a space I had in the directory name. For some reason I also wanted to try if the length of the path was to long. It seems like the length was the key. When I moved up a bit in the file system tree it started to work.......

This is a problem I thought only appeared in DOS!!

*sigh* But now it works and I have created a really nice panorama of 3 photos over a lake in the Swedish mountains. WAS worth it!

Thanks everyone who took their time.
Peter P.

---

