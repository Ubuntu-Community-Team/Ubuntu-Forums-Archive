---
title: "modprobe snd-intel8x0 fails"
date: 2009-02-27
forum: Ubuntu Studio
---

### Post by Gorizon on 2009-02-27
Hello, guys!
I've recently upgraded my kernel to experimental [COLOR="DarkGreen"]2.6.29-rc3-wl[/COLOR] one in order to support AP mode for my RaLink card...
Quite expectedly, no sound turned up after kernel compilation
I decided to build ALSA from source (*version 1.0.19 from alsaproject*) with parameters 
```
--with-kernel=<my 2.6.29-rc3-wl kernel source path>
```
and succeeded
However, modprobing the module snd-intel8x0 fails with the following:
```
crystal@Crystal:~$ sudo modprobe snd-intel8x0
FATAL: Error inserting snd (/lib/modules/2.6.29-rc3-wl/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.29-rc3-wl/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.29-rc3-wl/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.29-rc3-wl/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.29-rc3-wl/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.29-rc3-wl/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.29-rc3-wl/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
And dmesg supply me with lots of unknown symbols:
```
crystal@Crystal:~$ dmesg | tail
[ 1028.710744] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[ 1028.710919] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[ 1028.711098] snd_intel8x0: Unknown symbol snd_card_disconnect
[ 1028.711270] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[ 1028.711441] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[ 1028.711772] snd_intel8x0: Unknown symbol snd_pci_quirk_lookup
[ 1028.712030] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[ 1028.712346] snd_intel8x0: Unknown symbol snd_card_create
[ 1028.712516] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[ 1028.712695] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware

```
My hardware: 
```
crystal@Crystal:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

```
Could anyone suppose why does that happen?

---

### Post by thorgal on 2009-02-27
I am not sure, but it looks like not all modules were compiled that are usually loaded with snd-intel8x0. Could be something wrong in the compilation configuration.

---

### Post by Gorizon on 2009-02-27
I went to my previous 2.6.24-23-server kernel and looked what makes up sound there
```
crystal@Crystal:~$ lsmod | grep snd
snd_intel8x0           35356  3
snd_ac97_codec        100772  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42016  0
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35456  0
snd_seq_midi            9248  0
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56868  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm

```
Then tried to compare [COLOR="DarkOrange"]/lib/modules/2.6.29-rc3-wl/kernel/sound [/COLOR]and [COLOR="#ff8c00"]/lib/modules/2.6.24-23-server/kernel/sound[/COLOR]. Not a big difference, really. At least first three exist in both cases

---

### Post by lyjx0228 on 2009-02-28
&#12288;[**&#38024;&#28792;&#20943;&#32933;**](http://www.zdfjf.com/jjjf.html)&#30340;&#20248;&#21183;&#26377;&#24456;&#22810;&#65292;[**&#20013;&#21307;&#20943;&#32933;**](http://www.zdfjf.com/zyjf.html)&#26080;&#30171;&#24863;&#65292;&#30103;&#25928;&#26174;&#33879;&#21448;&#26080;&#39035;&#39281;&#23581;&#20854;&#20182;&#20943;&#32933;&#26041;&#24335;&#21487;&#33021;&#24102;&#26469;&#30340;&#30171;&#33510;&#12290;&#26377;&#20123;&#22899;&#23401;&#36861;&#27714;&#24555;&#36895;&#20943;&#32933;&#65292;&#32780;&#19981;&#24796;&#26426;&#20307;&#21463;&#21040;&#25439;&#20260;&#65292;&#37319;&#29992;&#21507;&#20943;&#32933;&#33647;&#12289;&#36807;&#24230;&#33410;&#39135;&#12289;&#36807;&#24378;&#30340;&#20307;&#32946;&#36816;&#21160;&#65292;&#25511;&#21046;&#27599;&#26085;&#30340;&#39278;&#27700;&#37327;&#31561;&#38169;&#35823;&#30340;&#20570;&#27861;&#26469;&#36827;&#34892;&#20943;&#32933;&#65292;&#35753;&#25105;&#20204;&#26469;&#30475;&#30475;&#36825;&#20123;&#20943;&#32933;&#26041;&#27861;&#21040;&#24213;&#26377;&#21738;&#20123;&#24330;&#31471;&#65306;&#12288;&#12288;A.&#21507;&#20943;&#32933;&#33647;&#12288;&#12288;&#33145;&#27899;&#21033;&#23615;&#34429;&#28982;&#20943;&#36731;&#20307;&#37325;&#36739;&#24555;&#65292;&#20294;&#20943;&#21435;&#30340;&#37117;&#26159;&#27700;&#20998;&#65292;&#38543;&#30528;&#27700;&#20998;&#30340;&#20002;&#22833;&#65292;&#20307;&#20869;&#30005;&#35299;&#36136;&#20063;&#38543;&#20043;&#36896;&#25104;&#32010;&#20081;&#65292;&#36824;&#26131;&#24182;&#21457;&#20195;&#35874;&#24615;&#37240;&#20013;&#27602;&#65292;&#23545;&#20943;&#32933;&#32773;&#26469;&#35762;&#65292;&#21487;&#20197;&#35828;&#26159;&#26377;&#30334;&#23475;&#32780;&#26080;&#19968;&#21033;&#65307;&#12288;&#12288;B.&#36807;&#24230;&#33410;&#39135;&#12288;&#12288;&#33410;&#39135;&#19981;&#20294;&#19981;&#33021;&#25345;&#20037;&#65292;&#32780;&#19988;&#26131;&#20986;&#29616;&#37230;&#30151;&#37240;&#20013;&#27602;&#65292;&#20986;&#29616;&#30130;&#20047;&#26080;&#21147;&#65292;&#24694;&#24515;&#21589;&#21520;&#31561;&#30151;&#29366;&#65307;&#12288;&#12288;C.&#36807;&#24378;&#30340;&#36816;&#21160;&#12288;&#12288;&#26131;&#28040;&#32791;&#33889;&#33796;&#31958;&#65292;&#19981;&#21033;&#20110;&#33026;&#32938;&#20195;&#35874;&#65292;&#23545;&#20943;&#32933;&#24466;&#21171;&#26080;&#30410;&#65307;&#12288;&#12288;D.&#25511;&#21046;&#39278;&#27700;&#37327;&#12288;&#12288;&#36896;&#25104;&#26426;&#20307;&#33073;&#27700;&#65292;&#19981;&#20294;&#23545;&#33026;&#32938;&#20195;&#35874;&#19981;&#21033;&#65292;&#36824;&#22686;&#21152;&#20102;&#32925;&#32958;&#36127;&#25285;&#65292;&#20351;&#20195;&#35874;&#36807;&#31243;&#20013;&#30340;&#24223;&#29289;&#19981;&#33021;&#21450;&#26102;&#25490;&#20986;&#20307;&#22806;&#65292;&#24341;&#36215;&#26426;&#20307;&#33258;&#36523;&#30340;&#20013;&#27602;&#21453;&#24212;&#12290;&#12288;&#12288;&#32780;&#38024;&#28792;&#20943;&#32933;&#23601;&#19981;&#23384;&#22312;&#20197;&#19978;&#36825;&#20123;&#38382;&#39064;&#65292;&#25152;&#20197;&#36825;&#20123;[**&#24555;&#36895;&#20943;&#32933;**](http://www.zdfjf.com/)&#26041;&#27861;&#37117;&#26159;&#19981;&#21487;&#21462;&#30340;&#12290;&#25105;&#20204;&#25552;&#20513;&#31283;&#36895;&#30340;&#20581;&#24247;[**&#20013;&#21307;&#20943;&#32933;**](http://www.zdfjf.com/zyjf.html)&#20943;&#32933;&#12290;[**&#38024;&#28792;&#20943;&#32933;**](http://www.zdfjf.com/jjjf.html)&#26356;&#23433;&#20840;&#12289;&#21487;&#38752;&#65292;&#23545;&#20154;&#20307;&#26080;&#20219;&#20309;&#25439;&#23475;&#65292;&#26159;&#19968;&#31181;&#23433;&#20840;&#30340;&#20943;&#32933;&#26041;&#24335;&#12290;

---

### Post by Gorizon on 2009-02-28
Well, I don't speak whatever this oriental language is, sorry

---

