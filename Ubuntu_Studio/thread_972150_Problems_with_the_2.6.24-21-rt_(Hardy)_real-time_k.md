---
title: "Problems with the 2.6.24-21-rt (Hardy) real-time kernel"
date: 2008-11-05
forum: Ubuntu Studio
---

### Post by mrhelpman on 2008-11-05
After a number of years of making successful music recordings using a combination of rosegarden and ardour on my Ubuntu Dapper Drake system, and my home grown real-time kernels, I thought it was time to upgrade to Hardy Heron and use the proper real time kernel that the experts had built. What a disappointment!

I have an internal pci sound blaster live card (emu10k1 chip set) and a M-audio audiophile USB sound module.

On my dapper installation, which happened to have 2.6.22.1 real time patched kernel (the default ubuntu kernel was 2.6.15), I could get latencies as low as 1.5ms (32 frames/period) on the sound blaster and 2.7ms ( 64 frames/period) on the USB Audiophile with very few xruns; so few xruns that I used to wonder why people posted to mailing lists/forums about the problem.

With the stock Ubuntu 2.6.24-21rt kernel the sound blaster gives xruns every few seconds with no load (no recording and no playing back) at 23ms latency (512 frames/period) and the Audiophile struggles at 43ms ( 1024 frames/period); I am getting xruns every 10-20 seconds. Infact the rt kernel gives little, if any, improvement over the generic kernel.
Is there something obvious that I am missing.

And now I find that after a recent upgrade to the 2.6.24-21-rt kernel it will no longer run X in the resolution that the generic kernel uses (1650x1050) I guess this is something to do with my Nvidia graphics card (Gforce4 MX420) and the restricted drivers. The generic kernel was updated at the same time but that is not having a problem.

Any help will be really appreciated as I would rather spend my time recording that mucking about building kernels.

John T.

---

### Post by thorgal on 2008-11-05
this is simple: don't fix what's working. As I keep saying to other people, a DAW is a highly customized system. Your home made system based on Dapper Drake seemed to work beautifully. Why change ? 

What you call the "experts" are not necessarily kernel gurus or sound engineers that happen to be highly knowledgeable in the complex technicalities of realtime linux. In my opinion, it's a risky assumption to believe that a prepackaged distro that is audio production oriented will work automagically. How can one expect this to happen ?

---

### Post by babarosa on 2008-11-06
Hi Mr. Helpman!

Even if your customized system works better - 8.10 is to perform better esp. with an audiophile than your experiences show.

If I understand you correctly, you _upgraded_ your system. That causes a lot of problems (it may work for office solutions but certainly not for a DAW): i'd suggest you install 8.10 completely new! An advantage would be that you get more recent programm versions with more features ([www.getdeb.net](www.getdeb.net)).

If you still face a lot of x-runs, try to use these settings: [http://ubuntuforums.org/showthread.php?t=965611&highlight=babarosa](http://ubuntuforums.org/showthread.php?t=965611&highlight=babarosa)

Good luck,
Michael

---

### Post by mrhelpman on 2008-11-06
> **babarosa said:**
> Hi Mr. Helpman!

Even if your customized system works better - 8.10 is to perform better esp. with an audiophile than your experiences show.

If I understand you correctly, you _upgraded_ your system.
No, I did a complete re-install from a new iso download.

> That causes a lot of problems (it may work for office solutions but certainly not for a DAW): i'd suggest you install 8.10 completely new! An advantage would be that you get more recent programm versions with more features ([www.getdeb.net](www.getdeb.net)).


I have considered this, but 8.10 will not support my graphics card - it is in the release notes. I don't particularly want to shell out on a new graphics card. 

My plan at the moment is to re-install 6.04 (dapper) and get  my home grown kernel packages from backup.

Thanks for taking the time to reply - it is very much  appreciated.

JT

---

### Post by babarosa on 2008-11-07
Sorry that it did not help.

Do you know that you can save a lot of effort backing up your completely setup system with remastersys ([http://www.remastersys.klikit-linux.com/)?](http://www.remastersys.klikit-linux.com/)?)

It only takes appr. 20 minutes to re-install your system with all personal settings.

Regards,
Michael

---

### Post by mrhelpman on 2008-11-09
> **babarosa said:**
> Sorry that it did not help.

Do you know that you can save a lot of effort backing up your completely setup system with remastersys ([http://www.remastersys.klikit-linux.com/)?](http://www.remastersys.klikit-linux.com/)?)

It only takes appr. 20 minutes to re-install your system with all personal settings.

Regards,
Michael

Thanks very much, I will have a look at that. It took me most of yesterday to get back to the lower latencies of my old system with a re-install of Dapper, but I did take the opportunity to do a little bit of tweaking - chaning partitions - that sort of thing. I have still got a build of ardour to do - but rosegarden appears to be running fine.

Perhaps we should keep the discussion about how to get the best performance from the rt kernels going. I am aware of this other thread:
[http://ubuntuforums.org/showthread.php?t=975713](http://ubuntuforums.org/showthread.php?t=975713)

John T.

---

### Post by mrhelpman on 2008-11-09
> **Stochastic said:**
> Sorry to hear you had trouble with the Hardy kernel though, it worked great for me.

Could you let me know what sort of system you are using - No. CPUs, CPU clock speed, memory and sound card types and the latency you get ( from jackd)?

Mine is a single 2.3GHz pentium, 1GB ram, SB live and Audiophine USB sound.

I am interested in finding out why my system performed so poorly under Hardy. At the moment I am not kean on installing Intrepid as it specifically does not support my old nvidia graphics card in 3d mode; I do run some graphic intensive progs when not recording audio.

John T.

---

### Post by 081103jk on 2008-11-10
&#21360;&#21047;&#30340;&#25253;&#20215;&#26159;&#22914;&#20309;&#24418;&#25104;&#30340;&#65311; &#24425;&#33394;&#21360;&#21047;&#26159;&#23545;&#20154;&#31867;&#34892;&#20026;&#21644;&#20135;&#21697;&#26381;&#21153;&#26368;&#31934;&#30830;&#30340;&#25551;&#36848;&#25163;&#27573;&#12290;[**&#20809;&#30424;&#21051;&#24405;**](http://www.itd9.com/gpkl.asp)&#23427;&#32473;&#20154;&#31867;&#24102;&#26469;&#28145;&#21051;&#30340;&#38590;&#20197;&#30952;&#28781;&#30340;&#31532;&#19968;&#21360;&#35937;&#21644;&#24863;&#21463;&#65292;[**&#20809;&#30424;&#25171;&#21360;**](http://www.itd9.com/gpdy.asp)&#23427;&#31934;&#30830;&#30340;&#34920;&#36848;&#21487;&#20197;&#31215;&#26497;&#22320;&#23545;&#20154;&#31867;&#24773;&#24863;&#21644;&#20915;&#31574;&#26045;&#21152;&#26368;&#22823;&#30340;&#24433;&#21709;&#65292;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#29305;&#21035;&#26159;&#36141;&#20080;&#20915;&#31574;&#21644;&#23458;&#25143;&#33719;&#24471;&#26381;&#21153;&#21518;&#30340;&#28385;&#36275;&#24863;&#12290;&#24425;&#33394;&#21360;&#21047;&#21697;&#36890;&#24120;&#20316;&#20026;&#20135;&#21697;&#20419;&#38144;&#30340;&#37325;&#35201;&#19968;&#29615;&#65292;&#26159;&#20851;&#31995;&#21040;&#20225;&#19994;&#25104;&#36133;&#30340;&#20851;&#38190;&#29615;&#33410;&#19982;&#21161;&#25163;&#12290; &#23458;&#25143;&#21046;&#20316;&#20135;&#21697;&#25512;&#24191;&#38144;&#21806;&#39044;&#31639;&#26102;&#65292;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#20250;&#24613;&#20110;&#24471;&#30693;&#21360;&#21047;&#21697;&#30340;&#25104;&#26412;&#26159;&#22810;&#23569;&#65292;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#21482;&#35201;&#24744;&#22635;&#23436;&#25972;&#25105;&#20204;&#30340;&#25253;&#20215;&#21333;&#65292;&#25105;&#20204;&#30340;&#23458;&#26381;&#20154;&#21592;&#21363;&#20250;&#20026;&#20320;&#22238;&#22797;&#25253;&#20215;

---

