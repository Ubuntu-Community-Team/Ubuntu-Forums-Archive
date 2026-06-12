---
title: "Video Editing Curse?"
date: 2008-11-11
forum: Ubuntu Studio
---

### Post by fINTiP on 2008-11-11
No video editing that I've thus tried has come even close to working. I'm using ubuntu studio 8.4.1.

I don't use DV, so kino is out. Open Movie Editor has too many problems for me to even begin- I can't load a video, I can't play one, etc.

PiTiVi is the closest, but it's just emaciated- I can try and put clips together, and things seem to be ok, but the exported file will only be the first clip, and I can't edit the audio *at all*.

I tried to download Cinelerra 4, and I found that the link on Heroin's website is actually mislinked- the 32 bit link causes you to download an i686 file.

I found [this]("http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071") page, but don't know what to download from the options.

The other thing is the camera I'm using, and the format the videos I'm getting- I get .MOD, and to each MOD there is a corresponding .MOI, and I don't know what that is used for. The camera is the Panasonic SDR-S7. I don't know if that causes any problems, but the editors all seem to accept the file at first, and then deny it.

I know open movie editor won't even allow me to use a basic .mp4 that runs on my ipod just fine...

Kdenlive crashed the first time I started it, sending SIGSEV when trying to load.

Blender, besides looking complicated, has odd issues that aren't even allowing it to display right. :\

Where do I start?

L

---

### Post by sdpiowa on 2008-11-11
I can't really help you with the video editing software, except to say that I successfully downloaded Cinelerra before.

Getting Ubuntu 8.10 fixed the display problem with Blender, but I wouldn't use that for video editing.

I know I probably wasn't much help, but I hope you get it fixed!

---

### Post by warbread on 2008-11-12
I love [Cinelerra.]("http://cinelerra.org/")  Go to the main web page and follow their installation instructions.  I've had it working on 32 and 64 bit systems since early Hardy.

---

### Post by nowardev on 2008-11-12
kdenlive :

 

solution:

1 : sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2: delete configuration files (~/.kde/share/config/kdenliverc)
3: try to disalble compiz (gnome user run this :     metacity --replace  ;  kde user      kwin --replace

if you get crash after this try with 

try open kdenlive like root

kdesudo kdenlive 

or 

gksudo kdenlive

or 

sudo kdenlive


blender you have to select Sequence interface

[[IMG]http://img135.imageshack.us/img135/521/blenderzq4.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=blenderzq4.jpg)[[IMG]http://img135.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by 081104jk on 2008-11-13
&#20844;&#21496;&#25216;&#26415;&#21183;&#21147;&#38596;&#21402;,&#26377;&#19987;&#19994;&#21270;&#38431;&#20237;,&#20855;&#26377;&#20808;&#36827;&#26426;&#26800;&#35774;&#22791;[**&#19978;&#19979;&#27700;&#32500;&#20462;**](http://www.bjjjjgd.cn/sxswx.htm)**,**&#25215;&#25509;&#21508;&#31867;&#39640;&#38590;&#24230;&#31649;&#36947;&#30095;&#36890;.&#26412;&#20844;&#21496;&#25152;&#24314;&#24037;&#31243;**,**[**&#31649;&#36947;&#30095;&#36890;**](http://www.bjjjjgd.cn/gdst.htm) &#22343;&#36127;&#36131;&#32500;&#20462;,&#26412;&#30528;&#19968;&#20999;&#20197;"[**&#39640;&#21387;&#28165;&#27927;**](http://www.bjjjjgd.cn/gyqx.htm)&#23458;&#25143;&#28385;&#24847;&#20026;&#26631;&#20934;&#20197;&#36136;&#37327;&#27714;&#29983;&#23384;,&#31435;&#36275;&#20110;&#35802;&#23454;&#20570;&#20154;&#35802;&#20449;&#26381;&#21153;"[**&#30095;&#36890;&#19979;&#27700;&#36947;**](http://www.bjjjjgd.cn/stxsd.htm)&#20026;&#26381;&#21153;&#30340;&#35268;&#21017;.&#29616;&#24050;&#21457;&#23637;&#25104;&#20026;&#19968;&#23478;&#19987;&#19994;&#25104;&#29087;&#35268;&#33539;,&#35268;&#27169;&#26497;&#22823;&#30340;&#30095;&#36890;&#20844;&#21496;[**&#30095;&#36890;&#19979;&#27700;&#36947;**](http://www.bjjjjgd.cn/stxsd.htm),&#35813;&#20844;&#21496;&#26412;&#30528;&#36208;&#21521;&#22269;&#38469;,&#38754;&#21521;&#20840;&#22269;,&#26381;&#21153;&#21040;&#23478;&#30340;&#21407;&#21017;,&#31283;&#23450;&#23433;&#20840;&#36755;&#36865;&#28192;&#36947;&#30340;&#21407;&#21017;",&#22362;&#25345;&#26381;&#21153;&#21453;&#39304;&#21046;&#24230;,&#23545;&#23458;&#25143;&#30340;&#24847;&#35265;&#21644;&#24314;&#35758;&#36805;&#36895;&#36827;&#34892;&#30563;&#21150;,&#33853;&#23454;,&#20351;&#23458;&#25143;&#30495;&#27491;&#20139;&#21463;&#21040;&#19978;&#24093;&#33324;&#30340;&#26381;&#21153;.

---

