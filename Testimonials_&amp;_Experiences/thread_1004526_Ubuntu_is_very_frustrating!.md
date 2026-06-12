---
title: "Ubuntu is very frustrating!"
date: 2008-12-07
forum: Testimonials &amp; Experiences
---

### Post by aspie on 2008-12-07
I just wanted to let off a little steam, and maybe get some general pointers.  I had tried a good while back to migrate my home recording studio to UbuntuStudio, but the sound card I was using was a real PITA under Linux.  However, I used it for a while until there was a distro upgrade.

So, I upgraded, and I couldn't get my WiFi (Broadcom BCM43XX) up again.  No wired connection was available. So, I finally gave and reluctantly moved back to WinXP.

Anyway, I just got a new sound card that I know works well with UbuntuStudio (a FirePod), so I downloaded UbuntuStudio 8.10 and the WiFi doesn't work!!!

I tried reading through a few threads, and had a go at fixing this but without success.  

So, what do I do now?  Is it time to buy a Mac? 

Maybe an older version of UbuntuStudio will get my WiFi up, but I am rapidly losing interest in this.  I really don't want to spend a few more hours trying 8.04 only to find that it doesn't work either.

---

### Post by aspie on 2008-12-07
Oh, I just thought of another potential solution.  Maybe I should just buy a different WiFi card.  Is this a worthwhile direction to go in?  Maybe some cards just work?

---

### Post by mips on 2008-12-07
My suggestion would be to use what works best for you.

---

### Post by bp1509 on 2008-12-07
d

---

### Post by fjf on 2008-12-07
Yes, it would be nice to know what is the wireless you have problems with.  Also, you may want to look here:  [http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless)
[http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup](http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup)

Also, for broadcom cards:  [http://ubuntuforums.org/showthread.php?t=201902&highlight=wireless](http://ubuntuforums.org/showthread.php?t=201902&highlight=wireless)

---

### Post by Paqman on 2008-12-07
Best thing to do with hardware is a quick bit of research. Before you buy anything, search these forums and/or Google Linux for the exact model number. If tons of stuff comes up, don't buy!

Buying Linux-friendly hardware is a good way to help Linux as a whole, as you're supporting manufacturers who've put time and money into Linux support.

---

### Post by phrostbyte on 2008-12-07
Please paste the results of the "lspci" command in here if you can.

---

### Post by fatality_uk on 2008-12-07
> **phrostbyte said:**
> Please paste the results of the "lspci" command in here if you can.

Ideally post your output into a support forum. The Cafe isn't really the place for support.

---

### Post by init1 on 2008-12-07
Yeah, I've had a lot of trouble with my Broadcom card. Works fine in Hardy and Intrepid, but not in any older distro.

---

### Post by Jdm111 on 2008-12-07
> **aspie said:**
> Oh, I just thought of another potential solution.  Maybe I should just buy a different WiFi card.  Is this a worthwhile direction to go in?  Maybe some cards just work?

Edimax Cards work great with Ubuntu

---

### Post by Bölvaður on 2008-12-07
[QUOTE=aspie;6325036 However, I used it for a while until there was a distro upgrade.[/QUOTE]

IMO there should be a warning sign on that upgrade button saying "warning, switching to new distro might break your system, and the kernel in the release you are going to install does not support your wireless card"


To the OP:
Staying in 8.04 will work if it worked before, it is because of kernel update.

---

### Post by igknighted on 2008-12-07
You just need to download firmware that Ubuntu cannot ship (legal issues).  You can do this under XP and then transfer the files over.  There are lots of instructions available on the forum.  If you could plug in to a wired connection it could do this automatically, but since that isn't an option, download them on XP.

---

### Post by gn2 on 2008-12-07
> **aspie said:**
> Oh, I just thought of another potential solution.  Maybe I should just buy a different WiFi card.  Is this a worthwhile direction to go in?  Maybe some cards just work?

That's an excellent idea if you have no success with [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by aspie on 2008-12-08
Thanks for all the replies.  I'll give it another go now, and if all fails, I will try 8.04 before buying a new card.

BTW, there is no Network Manager installed on my 8.10 system!  I guess that's part of the problem :)

---

### Post by halovivek on 2008-12-08
i am also getting frustrated for one thing. i got sound in system speakers but i could not hear in the head phone.:confused:

---

### Post by glotz on 2008-12-08
halovivek, there's a separate volume slider for headphones. Check it's not muted and not at zero volume.

---

### Post by halovivek on 2008-12-08
> **glotz said:**
> halovivek, there's a separate volume slider for headphones. Check it's not muted and not at zero volume.

thanks i will check and i will post the reply):P

---

### Post by stalkingwolf on 2008-12-08
First are you working wit a desk top or laptop?  
I am seeing that the broadcom 43xx is like the unichrome pro.  There
are several revisions.  8.04.1 worked OOTB with the broadcom 43xx
in an everex stepnote I gave to a friend.  That was the first time
I had gotten it to work with any distro.

If you are working with a laptop I have had great success with the DLink dwl g650 aircard.  For either I use a Netgear wg111 USB adapter or one of its clones.

Up to the release of 8.04 I never paid much attention to the on board wireless. When I installed 8.04 on my hP laptop I was WOWed when I found
that I had not only my Dlink wireless connection but also the onboard "just worked" and better than the DLINK.  The same is true of my EEE 701.  I had read the "horror stories" of the EEE not being able to connect fron 10 feet
away, Yet mine loaded with EEE8.04.1 can connect to a connection 1/2 mile
away.

I guess it all boils down to  YMMV.

---

### Post by aspie on 2008-12-08
Hey thanks for that, I will cut my losses & try 8.04 next then.  Oh, and it's a desktop (with PCI WiFi card).

---

### Post by stalkingwolf on 2008-12-09
What brand of card is it?  It seems that people have the best luck
with DLink or Netgear.  I have only used one and I dont remember what brand it was.

When I want to do the wireless thing on a desktop I usually just plug in one of my USB adapters.

---

### Post by aspie on 2008-12-09
It's an early Belkin 54G card.  

I installed 8.04.1 last night and it looks a lot more promising, I have Network Manager now. So, that's progress.

Later, I will see if I can get this working, I'm a lot more confident that I have Network Manager, at least it now looks right.

---

### Post by cardinals_fan on 2008-12-10
I have a Belkin F5D7050.  It works out-of-the-box on most Linux and BSD systems now, but getting it working when I first started (2+ years ago w/Ubuntu 6.06) was an extremely unpleasant process.  What's your adapter's model number?

---

### Post by cmay on 2008-12-10
[http://64studio.com/screenshots](http://64studio.com/screenshots)

try this. i left windows xp with cubase and roladn cakewalk for it. with out a doubt an good alternative. for my computer wiht my emu 1212m and a harddisk recorder it just works when installed. i can plug in my usb keyboards and drum machines and its just setup an working by it self. most instruments are. ohterwise use jack and jack control to connect it and record. i am more productive this way than on windows where if i unplugged the wrong usb cable had to find my driver cd and install the drum machine drivers again. (i have only five usb plugged in at one time since there is not more on the compy but i have most of my things usb and i switch a lot) 

check the link  out there is  a live cd as well which i also reccomenend trying out first.

---

### Post by cardinals_fan on 2008-12-10
@cmay: wrong thread?

---

### Post by aspie on 2008-12-10
> **cardinals_fan said:**
> What's your adapter's model number?

I'd have to break out a screwdriver to be sure, but I seem to remember that it is a F5D7000

---

### Post by cardinals_fan on 2008-12-10
> **aspie said:**
> I'd have to break out a screwdriver to be sure, but I seem to remember that it is a F5D7000
That should work with ndiswrapper, if all else fails.

---

### Post by cmay on 2008-12-10
> **cardinals_fan said:**
> @cmay: wrong thread?
ehh......could be. nevermind the post.

---

### Post by badpyhedy on 2008-12-10
&#12288;&#31532;&#19968;&#20135;&#19994; 1958&#24180;&#20840;&#38215;&#31918;&#39135;&#24179;&#22343;&#20137;&#20135;130&#20844;&#26020;&#65292;&#24635;&#20135;630&#19975;&#20844;&#26020;&#65307;1978&#24180;&#24179;&#22343;&#20137;&#20135;2 64&#20844;&#26020;&#65292;&#24635;&#20135;1233&#19975;&#20844;&#26020;&#12290;[&#21378;&#25151;&#31199;&#36161;](http://www.eurekacitypark.com/)&#20013;&#20849;&#21313;&#19968;&#23626;&#19977;&#20013;&#20840;&#20250;&#21518;&#65292;&#20840;&#34903;&#36947;&#23454;&#34892;&#23478;&#24237;&#32852;&#20135;&#25215;&#21253;&#36131;&#20219;&#21046;&#65292;&#35843;&#21160;&#20102;&#20892;&#27665;&#29983;&#20135;&#31215;&#26497;&#24615;&#65292;&#21516;&#26102;&#65292;&#25552;&#20513;&#31185;&#23398;&#31181;&#30000;&#65292;&#22823;&#24133;&#24230;&#25552;&#39640;&#20102;&#31918;&#39135;&#20316;&#29289;&#30340;&#21333;&#20135;&#37327;&#12290;&#20826;&#30340;&#25913;&#38761;&#24320;&#25918;&#25919;&#31574;&#65292;&#20351;&#20013;&#38889;&#34903;&#36947;&#21150;&#20107;&#22788;&#32463;&#27982;&#39134;&#36895;&#21457;&#23637;&#65292;&#32463;&#27982;&#25910;&#20837;&#26377;&#20102;&#36739;&#22823;&#25552;&#39640;&#65292;&#20892;&#26449;&#32463;&#27982;&#23454;&#21147;&#26126;&#26174;&#25552;&#39640;&#12290;&#19968;&#26159;&#21152;&#24555;&#20102;&#20892;&#19994;&#32467;&#26500;&#35843;&#25972;&#65292;&#22823;&#21147;&#21457;&#23637;&#37117;&#24066;&#20892;&#19994;&#65292;&#23454;&#26045;&#20892;&#19994;&#31934;&#21697;&#24037;&#31243;&#12290; &#30707;&#32769;&#20154;&#26053;&#28216;&#35266;&#20809;&#22253;&#20316;&#20026;&#38738;&#23707;&#24066;9&#22823;&#20892;&#19994;&#31934;&#21697;&#31034;&#33539;&#24037;&#31243;&#24050;&#21021;&#20855;&#35268;&#27169;&#65292;&#24102;&#21160;&#20102;&#21608;&#36793;&#26449;&#26053;&#28216;&#35266;&#20809;&#20892;&#19994;&#30340;&#21457;&#23637;&#12290;&#35813;&#39033;&#30446;&#24050;&#34987;&#21015;&#20837;&#22269;&#23478;&#20892;&#19994;&#24320;&#21457;&#39033;&#30446;&#12290;&#26543;&#26691;&#33457;&#21321;&#22522;&#22320;&#24314;&#35774;&#24050;&#21021;&#20855;&#38607;&#24418;&#65292;&#24102;&#21160;&#20102;&#35813;&#34903;&#36947;&#33457;&#21321;&#20135;&#19994;&#19978;&#35268;&#27169;&#12289;&#19978;&#26723;&#27425;&#65307;&#20108;&#26159;&#31361;&#20986;&#21457;&#23637;&#20102;&#28023;&#29645;&#21697;&#12289;&#27973;&#28023;&#12289;&#34299;&#31867;&#21644;&#36125;&#31867;&#20859;&#27542;&#19994;&#65292;&#30830;&#23450;&#20102;&#27700;&#20135;&#19994;&#22312;&#22823;&#20892;&#19994;&#20013;&#30340;&#25903;&#26609;&#20135;&#19994;&#22320;&#20301;&#65292;&#20351;&#27700;&#20135;&#19994;&#21457;&#23637;&#19978;&#20102;&#26032;&#21488;&#38454;&#12290;2000&#24180;&#20840;&#34903;&#36947;&#31918;&#39135;&#24179;&#22343;&#20137;&#20135;478&#20844;&#26020;&#65292;&#24635;&#20135;78.6&#19975;&#20844;&#26020;&#12290;1978&#24180;&#20840;&#38215;&#20892;&#19994;&#24635;&#20135;&#20540;&#20026;517&#19975;&#20803;&#65292;2000&#24180;&#20026;1.9413&#20159;&#20803;&#12290;&#31181;&#26893;&#19994;&#24635;&#20135;&#20540;4382&#19975;&#20803;&#65292;&#27700;&#20135;&#21697;&#20859;&#27542;&#38754;&#31215;&#36798;&#21040;324&#20844;&#39031;&#65292;&#28180;&#19994;&#24635;&#20135;&#20540;1.4115&#20159;&#20803;&#12290;&#32789;&#22320;&#38754;&#31215;460&#20844;&#39031;&#65292;&#20892;&#20316;&#29289;&#38754;&#31215;319&#20844;&#39031;&#65292;&#20854;&#20013;&#31918;&#39135;&#20316;&#29289;&#25773;&#31181;&#38754;&#31215;110&#20844;&#39031;&#65292;&#32463;&#27982;&#20316;&#29289;20&#20844;&#39031;&#12290;&#31918;&#12289;&#32463;&#20316;&#29289;&#20135;&#20540;&#27604;&#20026;1:9&#12290;&#12288;&#12288;&#31532;&#20108;&#20135;&#19994; [&#21378;&#25151;&#31199;&#36161;](http://www.eurekacitypark.com/plane_kj.htm)&#24314;&#22269;&#21069;&#65292;&#20013;&#38889;&#20154;&#27665;&#20197;&#20892;&#19994;&#20026;&#20027;&#12290;&#22320;&#21306;&#20869;&#26377;&#37247;&#37202;&#19994;&#12289;&#27048;&#27833;&#19994;&#12289;&#30742;&#29926;&#19994;&#31561;&#65292;&#20174;&#19994;&#20154;&#21592;&#22810;&#19981;&#19987;&#32844;&#65292;&#19982;&#20892;&#19994;&#21171;&#21160;&#32039;&#23494;&#32852;&#31995;&#65292;&#32844;&#19994;&#20998;&#24037;&#19981;&#26126;&#26174;&#12290;&#24314;&#22269;&#21518;&#65292;&#24037;&#19994;&#21644;&#20854;&#20182;&#34892;&#19994;&#36805;&#36895;&#21457;&#23637;&#65292;&#22823;&#25209;&#20154;&#21592;&#20174;&#20892;&#19994;&#20013;&#20998;&#31163;&#20986;&#26469;&#65292;&#32844;&#19994;&#20998;&#24037;&#24840;&#26469;&#24840;&#26126;&#26174;&#12290;1958&#24180;&#25104;&#31435;&#20154;&#27665;&#20844;&#31038;&#65292;&#24320;&#22987;&#21457;&#23637;&#31038;&#38431;&#24037;&#19994;&#65292;&#20808;&#21518;&#24314;&#36215;&#20102;&#38754;&#31881;&#21378;&#12289;&#26426;&#26800;&#21378;&#12289;&#30742;&#21378;&#31561;&#23567;&#22411;&#20225;&#19994;&#12290;1978&#24180;&#31532;&#20108;&#20135;&#19994;&#20174;&#19994;&#20154;&#21592;1130&#20154;&#65292; &#23454;&#29616;&#20135;&#20540;713&#19975;&#20803;&#12290;&#36827;&#20837;90&#24180;&#20195;&#65292;&#20197;&#25552;&#39640;&#32463;&#27982;&#25928;&#30410;&#20026;&#20013;&#24515;&#65292;&#21152;&#24555;&#24037;&#19994;&#32467;&#26500;&#35843;&#25972;&#65292;&#31215;&#26497;&#24320;&#21457;&#39640;&#26032;&#25216;&#26415;&#20135;&#21697;&#65292;&#20225;&#19994;&#23454;&#34892;&#36328;&#22320;&#21306;&#12289;&#36328;&#34892;&#19994;&#12289;&#36328;&#25152;&#26377;&#21046;&#30340;&#22810;&#20803;&#21270;&#21457;&#23637;&#26684;&#23616;&#65292;&#37325;&#26032;&#25226;&#25307;&#21830;&#24341;&#36164;&#24037;&#20316;&#23450;&#20301;&#20026;&#65306;&#20381;&#38752;&#39640;&#31185;&#22253;&#65292;&#31361;&#20986;&#39640;&#31185;&#22253;&#65292;&#20869;&#36164;&#22806;&#36164;&#24182;&#37325;&#65292;&#22823;&#23567;&#39033;&#30446;&#24182;&#20030;&#12290;&#39033;&#30446;&#25307;&#21830;&#36880;&#27493;&#24418;&#25104;&#8220;&#20197;&#22806;&#20026;&#20027;&#65292;&#20869;&#22806;&#24182;&#37325;&#65307;&#20197;&#22806;&#24341;&#22806;&#65292;&#20197;&#20869;&#24341;&#22806;&#8221;&#30340;&#29305;&#28857;&#12290;[&#21378;&#25151;&#31199;&#36161;](http://www.eurekacitypark.com/news_detail3.htm)&#20225;&#19994;&#31283;&#27493;&#21457;&#23637;&#65292;&#25216;&#26415;&#27700;&#24179;&#21644;&#20135;&#21697;&#36136;&#37327;&#19981;&#26029;&#25552;&#39640;&#12290;&#38738;&#23707;&#38754;&#31881;&#26426;&#26800;&#21378;&#29983;&#20135;&#30340;&#8220;&#21452;&#31119;&#8221;&#29260;&#38754;&#31881;&#21152;&#24037;&#25104;&#22871;&#35774;&#22791;&#65292;&#22810;&#24180;&#30021;&#38144;&#22269;&#20869;&#22806;&#65307;&#21335;&#24352;&#26131;&#36890;&#20844;&#21496;&#30340;&#21355;&#26143;&#23548;&#33322;&#20202;&#12289;&#33394;&#35889;&#20202;&#12289;&#22823;&#27668;&#37319;&#26679;&#22120;&#33719;&#22269;&#20248;&#31216;&#21495;&#65307;&#35199;&#38889;&#39044;&#21046;&#26500;&#20214;&#21378;&#30340;&#39044;&#21046;&#26495;&#26448;&#36890;&#36807;&#30465;&#32423;&#37492;&#23450;&#65292;&#23646;&#30465;&#20813;&#26816;&#20135;&#21697;&#65307;&#22823;&#40614;&#23707;&#38081;&#36335;&#26426;&#36710;&#26426;&#26800;&#20135;&#21697;&#36136;&#37327;&#36807;&#30828;&#65292;&#20139;&#35465;&#38738;&#23707;&#65292;&#30446;&#21069;&#65292;&#20854;&#20225;&#19994;&#20135;&#21697;&#26377;3&#20010;&#33719;&#22269;&#23478;&#19987;&#21033;&#65292;7&#20010;&#33719;&#30465;&#20248;&#12290;2000&#24180;&#20840;&#38215;&#31532;&#20108;&#20135;&#19994;&#20174;&#19994;&#20154;&#21592;15226&#20154;&#65292;&#23454;&#29616;&#20135;&#20540;36.903&#20159;&#20803;&#12290;&#12288;&#12288;&#31532;&#19977;&#20135;&#19994; 1978&#24180;&#65292; &#20840;&#38215;&#31532;&#19977;&#20135;&#19994;&#24180;&#21019;&#20135;&#20540;273&#19975;&#20803;&#65292;2000&#24180;&#20840;&#38215;&#20849;&#26377;&#21830;&#19994;&#12289;&#39278;&#39135;&#19994;&#12289;&#26381;&#21153;&#19994;&#31561;&#21508;&#31867;&#26381;&#21153;&#32593;&#28857;1200&#25143;&#65292;&#20174;&#19994;&#20154;&#21592;4148&#20154;&#65292;&#24180;&#21019;&#20135;&#20540;3.4871&#20159;&#20803;&#65292;&#23454;&#29616;&#21033;&#31246;1427&#19975;&#20803;&#12290;&#12288;&#12288;&#20154;&#27665;&#29983;&#27963; [&#21378;&#25151;&#31199;&#36161;](http://www.eurekacitypark.com/quality_pp.htm)&#24314;&#22269;&#21069;&#20154;&#22343;&#32789;&#22320;&#19981;&#36275;&#21322;&#20137;&#65292;&#32431;&#25910;&#20837;&#19981;&#36807;10&#20803;&#24038;&#21491;&#65292;&#19981;&#36275;&#20197;&#33258;&#32473;&#12290;1978&#24180;&#20154;&#22343;&#32431;&#25910;&#20837;135&#20803;&#65292;&#24180;&#20154;&#22343;&#31918;&#39135;417&#20844;&#26020;&#12290;2000&#24180;&#20154;&#22343;&#32431;&#25910;&#20837;4567&#20803;&#12290;

---

