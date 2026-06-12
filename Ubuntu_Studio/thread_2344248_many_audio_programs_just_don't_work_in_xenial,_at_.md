---
title: "many audio programs just don't work in xenial, at least not for me"
date: 2016-11-23
forum: Ubuntu Studio
---

### Post by a-you on 2016-11-23
This is too frustrating! 

At least half of the time I try to start ardour4, whether using jack or directly using alsa, it doesn't work. Starting from terminal it typically reports "core dumped." Meanwhile audacity typically doesn't work most of the time ("core dumped"). Neither muse. And various other programs I've tried, though I haven't kept a list. I know that I've uninstalled several programs just because they weren't working. Cecilia also doesn't work now. It's like I'm limited to using Pd and wonderful though Pd is, it's not enough.  

It's so frustrating because with trusty everything worked wonderfully, now with this xenial install basically hardly any audio programs work at all.  And several other apps are broken too, seemingly because of the "upgrade" from python 2.7 to 3.  I don't know what to say or do, except to wonder whether anybody actually tested what's after all a long term support release before putting it out. Or is it just me that's having these problems??  

Please note that I'm a *huge* ubuntu studio fan, been so since 2010 when I switched from using apple's nonsense and never looked back, as they say. But this is just too frustrating and I'm not sure if I should maybe try another distro? I don't know what to do. Really for me it's not working. Any thoughts??  

PS: why does a post get squeezed into one paragraph now?? There doesn't seem to be a way to stop that from happening!

---

### Post by ajgreeny on 2016-11-23
I have no idea why you can not get paragraphs to stick in your posts (or posts); are you typing into the box with paragraphs as you would normally in a word processor or text editor?
What setting do you have in your forum account general settings for **Message Editor Interface:** where the options are:-
>     Enhanced Interface - Full WYSIWYG Editing
    Basic Editor - A simple text box
    Standard Editor - Extra formatting controls

When posting messages to the forums or other members, there are three interface types available to you. The simplest of these is a simple text box, while the last is a fully-fledged WYSIWYG editor, which allows you to format your text as you want it and see the results immediately.

Occasionally strange things can happen if you have chosen the Enhanced Interface; try Standard Editor as that might help.

As for your sound problems, it is difficult to have any idea what might help as we do not know your hardware; audacity works fine in my Xubuntu-16.04 64bit system, so do all the music players I use, so it is not specifically related only to something in xenial, but maybe your hardware.

---

### Post by CrocoDuck on 2016-11-23
> **ajgreeny said:**
> 
As for your sound problems, it is difficult to have any idea what might help as we do not know your hardware; audacity works fine in my Xubuntu-16.04 64bit system, so do all the music players I use, so it is not specifically related only to something in xenial, but maybe your hardware.

Agree. It is very suspicious that all the audio software is throwing core dumped. It might even be due to faulty ram. Do you experience also other similar crashes?

---

### Post by a-you on 2016-11-23
Hi and thanks for your thoughts. Re the paragraphs: I don't know where to select the different interfaces for the forums editor. That's a minor issue of course. The audio issue is the major problem; very frustrating.  I have run the memory test that one gets as a boot option, running that overnight and it checked out fine. I did that when I upgraded the machine to 8 GB RAM.  Other similar crashes: no I don't think so. Meaning that programs that are for example office apps, those never crash.  As for hardware: the machine is a bit old, a sony viao from 2010, but when I got it it was a high end machine (i7 quad core processor, now has 8 GB RAM) so it seems to me that today it should be more or less an average machine.  I wonder if I should try setting the processor governor to "Performance" instead of leaving it at "Ondemand"?? (Just thought of that; tomorrow I'll try it.)  Any other thoughts on what to try would be very much appreciated! Thanks in advance.

---

### Post by CrocoDuck on 2016-11-23
Uhm... repost here, in code brackets, the whole error message you get from a faulty application.

---

### Post by a-you on 2016-11-25
@crokoDuck here is the output of trying to run audacity, and thank you. By the way I ran memtest overnight again and after 7.5 hours the result was "pass completed no errors."

I wonder if it's possible that a couple of utilities I have might be interfering with these apps?? I have a utility that allows me to keep track of the temps, also one that allows me to change the processor setting (ondemand, performance, etc)?

```
(Audacity:6202): Gtk-WARNING **: gtk_disable_setlocale() must be called before gtk_init()
no more csLADSPA plugins
lo server running on 14924
*** Error in `audacity': double free or corruption (fasttop): 0x00007f5f400274c0 ***
Warning: failed to load part<>!
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7f5f84a5d7e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x7fe0a)[0x7f5f84a65e0a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7f5f84a6998c]
/usr/lib/dssi/libzynaddsubfx_dssi.so(_ZN4Bank9clearbankEv+0x6e)[0x7f5f456f94fe]
/usr/lib/dssi/libzynaddsubfx_dssi.so(_ZN4Bank8loadbankENSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE+0x47)[0x7f5f456fa3a7]
/usr/lib/dssi/libzynaddsubfx_dssi.so(_ZN15DSSIaudiooutput11mapNextBankEv+0x11d)[0x7f5f456f835d]
/usr/lib/dssi/libzynaddsubfx_dssi.so(_ZN15DSSIaudiooutput10getProgramEm+0x88)[0x7f5f456f8708]
/usr/lib/lv2/naspro-dssi.lv2/dssi.so(+0x270d)[0x7f5f4860470d]
/usr/lib/lv2/naspro-dssi.lv2/dssi.so(+0x213f)[0x7f5f4860413f]
/usr/lib/x86_64-linux-gnu/libnabrit.so.3(nabrit_util_load_all_in_dir+0xb5)[0x7f5f6f84e5a5]
/usr/lib/lv2/naspro-dssi.lv2/dssi.so(+0x207a)[0x7f5f4860407a]
/usr/lib/liblilv-0.so.0(lilv_world_load_bundle+0x3f1)[0x7f5f876b68c1]
/usr/lib/liblilv-0.so.0(+0xebaf)[0x7f5f876b6baf]
/usr/lib/liblilv-0.so.0(+0xd096)[0x7f5f876b5096]
/usr/lib/liblilv-0.so.0(+0xd58b)[0x7f5f876b558b]
/usr/lib/liblilv-0.so.0(lilv_world_load_all+0x137)[0x7f5f876b6db7]
audacity(_ZN16LV2EffectsModule10InitializeEv+0x77f)[0x978c5f]
audacity(_ZN13ModuleManager18InitializeBuiltinsEv+0x96)[0x66b826]
audacity(_ZN13ModuleManager17DiscoverProvidersEv+0x2b)[0x66c4cb]
audacity(_ZN11AudacityApp6OnInitEv+0x895)[0x5aa4f5]
/usr/lib/x86_64-linux-gnu/libwx_baseu-3.0.so.0(_Z7wxEntryRiPPw+0x92)[0x7f5f8aca5f72]
audacity(main+0x12)[0x537a52]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f5f84a06830]
audacity(_start+0x29)[0x55e8a9]
======= Memory map: ========
00400000-00cce000 r-xp 00000000 08:05 928408                             /usr/bin/audacity
00ece000-00ecf000 r--p 008ce000 08:05 928408                             /usr/bin/audacity
00ecf000-00f5c000 rw-p 008cf000 08:05 928408                             /usr/bin/audacity
00f5c000-00f8d000 rw-p 00000000 00:00 0 
022a7000-04613000 rw-p 00000000 00:00 0                                  [heap]
7f5f34000000-7f5f34092000 rw-p 00000000 00:00 0 
7f5f34092000-7f5f38000000 ---p 00000000 00:00 0 
7f5f38000000-7f5f38155000 rw-p 00000000 00:00 0 
7f5f38155000-7f5f3c000000 ---p 00000000 00:00 0 
7f5f3f7ff000-7f5f3f800000 ---p 00000000 00:00 0 
7f5f3f800000-7f5f40000000 rw-p 00000000 00:00 0 
7f5f40000000-7f5f40032000 rw-p 00000000 00:00 0 
7f5f40032000-7f5f44000000 ---p 00000000 00:00 0 
7f5f440af000-7f5f454b1000 rw-p 00000000 00:00 0 
7f5f454b1000-7f5f454bd000 r-xp 00000000 08:05 266986                     /usr/lib/x86_64-linux-gnu/libmxml.so.1.5
7f5f454bd000-7f5f456bc000 ---p 0000c000 08:05 266986                     /usr/lib/x86_64-linux-gnu/libmxml.so.1.5
7f5f456bc000-7f5f456be000 r--p 0000b000 08:05 266986                     /usr/lib/x86_64-linux-gnu/libmxml.so.1.5
7f5f456be000-7f5f456bf000 rw-p 0000d000 08:05 266986                     /usr/lib/x86_64-linux-gnu/libmxml.so.1.5
7f5f456bf000-7f5f457ef000 r-xp 00000000 08:05 271401                     /usr/lib/dssi/libzynaddsubfx_dssi.so
7f5f457ef000-7f5f459ef000 ---p 00130000 08:05 271401                     /usr/lib/dssi/libzynaddsubfx_dssi.so
7f5f459ef000-7f5f459f3000 r--p 00130000 08:05 271401                     /usr/lib/dssi/libzynaddsubfx_dssi.so
7f5f459f3000-7f5f459f4000 rw-p 00134000 08:05 271401                     /usr/lib/dssi/libzynaddsubfx_dssi.so
7f5f459f4000-7f5f459f5000 rw-p 00000000 00:00 0 
7f5f459f5000-7f5f459f8000 r-xp 00000000 08:05 271442                     /usr/lib/dssi/trivial_sampler.so
7f5f459f8000-7f5f45bf7000 ---p 00003000 08:05 271442                     /usr/lib/dssi/trivial_sampler.so
7f5f45bf7000-7f5f45bf8000 r--p 00002000 08:05 271442                     /usr/lib/dssi/trivial_sampler.so
7f5f45bf8000-7f5f45bf9000 rw-p 00003000 08:05 271442                     /usr/lib/dssi/trivial_sampler.so
7f5f45bf9000-7f5f45bfb000 r-xp 00000000 08:05 271443                     /usr/lib/dssi/karplong.so
7f5f45bfb000-7f5f45dfb000 ---p 00002000 08:05 271443                     /usr/lib/dssi/karplong.so
7f5f45dfb000-7f5f45dfc000 r--p 00002000 08:05 271443                     /usr/lib/dssi/karplong.so
7f5f45dfc000-7f5f45dfd000 rw-p 00003000 08:05 271443                     /usr/lib/dssi/karplong.so
7f5f45dfd000-7f5f45e02000 r-xp 00000000 08:05 270969                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f5f45e02000-7f5f46001000 ---p 00005000 08:05 270969                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f5f46001000-7f5f46002000 r--p 00004000 08:05 270969                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f5f46002000-7f5f46003000 rw-p 00005000 08:05 270969                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f5f46003000-7f5f4600b000 r-xp 00000000 08:05 784981                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f5f4600b000-7f5f4620a000 ---p 00008000 08:05 784981                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f5f4620a000-7f5f4620b000 r--p 00007000 08:05 784981                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f5f4620b000-7f5f4620c000 rw-p 00008000 08:05 784981                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f5f4620c000-7f5f4620d000 rw-p 00000000 00:00 0 
7f5f4620d000-7f5f46217000 r-xp 00000000 08:05 785109                     /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f5f46217000-7f5f46416000 ---p 0000a000 08:05 785109                     /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f5f46416000-7f5f46417000 r--p 00009000 08:05 785109                     /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f5f46417000-7f5f46418000 rw-p 0000a000 08:05 785109                     /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f5f46418000-7f5f4643d000 r-xp 00000000 08:05 785137                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f5f4643d000-7f5f4663c000 ---p 00025000 08:05 785137                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f5f4663c000-7f5f46640000 r--p 00024000 08:05 785137                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f5f46640000-7f5f46641000 rw-p 00028000 08:05 785137                     /lib/x86_64-linux-gnu/libtinfo.so.5.9
7f5f46641000-7f5f466bb000 r-xp 00000000 08:05 265014                     /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-8.0.so
7f5f466bb000-7f5f468ba000 ---p 0007a000 08:05 265014                     /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-8.0.so
7f5f468ba000-7f5f468bb000 r--p 00079000 08:05 265014                     /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-8.0.so
7f5f468bb000-7f5f468bc000 rw-p 0007a000 08:05 265014                     /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-8.0.so
7f5f468bc000-7f5f4690a000 r-xp 00000000 08:05 265017                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.19.0
7f5f4690a000-7f5f46b0a000 ---p 0004e000 08:05 265017                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.19.0
7f5f46b0a000-7f5f46b0b000 r--p 0004e000 08:05 265017                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.19.0
7f5f46b0b000-7f5f46b0c000 rw-p 0004f000 08:05 265017                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.19.0
7f5f46b0c000-7f5f46b49000 r-xp 00000000 08:05 785073                     /lib/x86_64-linux-gnu/libreadline.so.6.3
7f5f46b49000-7f5f46d49000 ---p 0003d000 08:05 785073                     /lib/x86_64-linux-gnu/libreadline.so.6.3
7f5f46d49000-7f5f46d4b000 r--p 0003d000 08:05 785073                     /lib/x86_64-linux-gnu/libreadline.so.6.3
7f5f46d4b000-7f5f46d51000 rw-p 0003f000 08:05 785073                     /lib/x86_64-linux-gnu/libreadline.so.6.3
7f5f46d51000-7f5f46d52000 rw-p 00000000 00:00 0 
7f5f46d52000-7f5f46d55000 r-xp 00000000 08:05 265015                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.1.0
7f5f46d55000-7f5f46f55000 ---p 00003000 08:05 265015                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.1.0
7f5f46f55000-7f5f46f56000 r--p 00003000 08:05 265015                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.1.0
7f5f46f56000-7f5f46f57000 rw-p 00004000 08:05 265015                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.1.0
7f5f46f57000-7f5f46fac000 r-xp 00000000 08:05 266026                     /usr/lib/x86_64-linux-gnu/libfluidsynth.so.1.5.2
7f5f46fac000-7f5f471ac000 ---p 00055000 08:05 266026                     /usr/lib/x86_64-linux-gnu/libfluidsynth.so.1.5.2
7f5f471ac000-7f5f471ad000 r--p 00055000 08:05 266026                     /usr/lib/x86_64-linux-gnu/libfluidsynth.so.1.5.2
7f5f471ad000-7f5f471af000 rw-p 00056000 08:05 266026                     /usr/lib/x86_64-linux-gnu/libfluidsynth.so.1.5.2
7f5f471af000-7f5f4721d000 rw-p 00000000 00:00 0 
7f5f4721d000-7f5f47222000 r-xp 00000000 08:05 271440                     /usr/lib/dssi/fluidsynth-dssi.so
7f5f47222000-7f5f47421000 ---p 00005000 08:05 271440                     /usr/lib/dssi/fluidsynth-dssi.so
7f5f47421000-7f5f47422000 r--p 00004000 08:05 271440                     /usr/lib/dssi/fluidsynth-dssi.so
7f5f47422000-7f5f47423000 rw-p 00005000 08:05 271440                     /usr/lib/dssi/fluidsynth-dssi.so
7f5f47423000-7f5f47437000 r-xp 00000000 08:05 271412                     /usr/lib/dssi/xsynth-dssi.so
7f5f47437000-7f5f47637000 ---p 00014000 08:05 271412                     /usr/lib/dssi/xsynth-dssi.so
7f5f47637000-7f5f47638000 r--p 00014000 08:05 271412                     /usr/lib/dssi/xsynth-dssi.so
7f5f47638000-7f5f47649000 rw-p 00015000 08:05 271412                     /usr/lib/dssi/xsynth-dssi.so
7f5f47649000-7f5f4764b000 rw-p 00000000 00:00 0 
7f5f4764b000-7f5f4764c000 ---p 00000000 00:00 0 
7f5f4764c000-7f5f47e4c000 rw-p 00000000 00:00 0 
7f5f47fe0000-7f5f47ff1000 r-xp 00000000 08:05 271409                     /usr/lib/dssi/wsynth-dssi.so
7f5f47ff1000-7f5f481f1000 ---p 00011000 08:05 271409                     /usr/lib/dssi/wsynth-dssi.so
7f5f481f1000-7f5f481f2000 r--p 00011000 08:05 271409                     /usr/lib/dssi/wsynth-dssi.so
7f5f481f2000-7f5f481f3000 rw-p 00012000 08:05 271409                     /usr/lib/dssi/wsynth-dssi.so
7f5f481f3000-7f5f481f6000 rw-p 00000000 00:00 0 
7f5f481f6000-7f5f4823c000 r-xp 00000000 08:05 271399                     /usr/lib/dssi/whysynth.so
7f5f4823c000-7f5f4843b000 ---p 00046000 08:05 271399                     /usr/lib/dssi/whysynth.so
7f5f4843b000-7f5f4843c000 r--p 00045000 08:05 271399                     /usr/lib/dssi/whysynth.so
7f5f4843c000-7f5f48600000 rw-p 00046000 08:05 271399                     /usr/lib/dssi/whysynth.so
7f5f48600000-7f5f48602000 rw-p 00000000 00:00 0 
7f5f48602000-7f5f48606000 r-xp 00000000 08:05 662748                     /usr/lib/lv2/naspro-dssi.lv2/dssi.so
7f5f48606000-7f5f48805000 ---p 00004000 08:05 662748                     /usr/lib/lv2/naspro-dssi.lv2/dssi.so
7f5f48805000-7f5f48806000 r--p 00003000 08:05 662748                     /usr/lib/lv2/naspro-dssi.lv2/dssi.so
7f5f48806000-7f5f48807000 rw-p 00004000 08:05 662748                     /usr/lib/lv2/naspro-dssi.lv2/dssi.so
7f5f48807000-7f5f4880a000 r-xp 00000000 08:05 271601                     /usr/lib/ladspa/quantiser100_2029.so
7f5f4880a000-7f5f48a09000 ---p 00003000 08:05 271601                     /usr/lib/ladspa/quantiser100_2029.so
7f5f48a09000-7f5f48a0a000 r--p 00002000 08:05 271601                     /usr/lib/ladspa/quantiser100_2029.so
7f5f48a0a000-7f5f48a0b000 rw-p 00003000 08:05 271601                     /usr/lib/ladspa/quantiser100_2029.so
7f5f48a0b000-7f5f48a0e000 r-xp 00000000 08:05 271481                     /usr/lib/ladspa/dahdsr_2021.so
7f5f48a0e000-7f5f48c0d000 ---p 00003000 08:05 271481                     /usr/lib/ladspa/dahdsr_2021.so
7f5f48c0d000-7f5f48c0e000 r--p 00002000 08:05 271481                     /usr/lib/ladspa/dahdsr_2021.so
7f5f48c0e000-7f5f48c0f000 rw-p 00003000 08:05 271481                     /usr/lib/ladspa/dahdsr_2021.so
7f5f48c0f000-7f5f48c12000 r-xp 00000000 08:05 271537                     /usr/lib/ladspa/tap_chorusflanger.so
7f5f48c12000-7f5f48e11000 ---p 00003000 08:05 271537                     /usr/lib/ladspa/tap_chorusflanger.so
7f5f48e11000-7f5f48e12000 r--p 00002000 08:05 271537                     /usr/lib/ladspa/tap_chorusflanger.so
7f5f48e12000-7f5f48e13000 rw-p 00003000 08:05 271537                     /usr/lib/ladspa/tap_chorusflanger.so
7f5f48e13000-7f5f48e14000 rw-p 00000000 00:00 0 
7f5f48e14000-7f5f48e19000 r-xp 00000000 08:05 271495                     /usr/lib/ladspa/inv_erreverb.so
7f5f48e19000-7f5f49018000 ---p 00005000 08:05 271495                     /usr/lib/ladspa/inv_erreverb.so
7f5f49018000-7f5f49019000 r--p 00004000 08:05 271495                     /usr/lib/ladspa/inv_erreverb.so
7f5f49019000-7f5f4901a000 rw-p 00005000 08:05 271495                     /usr/lib/ladspa/inv_erreverb.so
7f5f4901a000-7f5f4901e000 r-xp 00000000 08:05 271568                     /usr/lib/ladspa/fm_osc_1415.so
7f5f4901e000-7f5f4921d000 ---p 00004000 08:05 271568                     /usr/lib/ladspa/fm_osc_1415.so
7f5f4921d000-7f5f4921e000 r--p 00003000 08:05 271568                     /usr/lib/ladspa/fm_osc_1415.so
7f5f4921e000-7f5f4921f000 rw-p 00004000 08:05 271568                     /usr/lib/ladspa/fm_osc_1415.so
7f5f4921f000-7f5f49221000 r-xp 00000000 08:05 271501                     /usr/lib/ladspa/decay_1886.so
7f5f49221000-7f5f49420000 ---p 00002000 08:05 271501                     /usr/lib/ladspa/decay_1886.so
7f5f49420000-7f5f49421000 r--p 00001000 08:05 271501                     /usr/lib/ladspa/decay_1886.so
7f5f49421000-7f5f49422000 rw-p 00002000 08:05 271501                     /usr/lib/ladspa/decay_1886.so
7f5f49422000-7f5f49426000 r-xp 00000000 08:05 271522                     /usr/lib/ladspa/triple_para_1204.so
7f5f49426000-7f5f49625000 ---p 00004000 08:05 271522                     /usr/lib/ladspa/triple_para_1204.so
7f5f49625000-7f5f49626000 r--p 00003000 08:05 271522                     /usr/lib/ladspa/triple_para_1204.so
7f5f49626000-7f5f49627000 rw-p 00004000 08:05 271522                     /usr/lib/ladspa/triple_para_1204.so
7f5f49627000-7f5f49629000 r-xp 00000000 08:05 271488                     /usr/lib/ladspa/karaoke_1409.so
7f5f49629000-7f5f49828000 ---p 00002000 08:05 271488                     /usr/lib/ladspa/karaoke_1409.so
7f5f49828000-7f5f49829000 r--p 00001000 08:05 271488                     /usr/lib/ladspa/karaoke_1409.so
7f5f49829000-7f5f4982a000 rw-p 00002000 08:05 271488                     /usr/lib/ladspa/karaoke_1409.so
7f5f4982a000-7f5f4982b000 r-xp 00000000 08:05 271480                     /usr/lib/ladspa/hz_voct_4200.so
7f5f4982b000-7f5f49a2a000 ---p 00001000 08:05 271480                     /usr/lib/ladspa/hz_voct_4200.so
7f5f49a2a000-7f5f49a2b000 r--p 00000000 08:05 271480                     /usr/lib/ladspa/hz_voct_4200.so
7f5f49a2b000-7f5f49a2c000 rw-p 00001000 08:05 271480                     /usr/lib/ladspa/hz_voct_4200.so
7f5f49a2c000-7f5f49a2e000 r-xp 00000000 08:05 271645                     /usr/lib/ladspa/adsr_1653.so
7f5f49a2e000-7f5f49c2d000 ---p 00002000 08:05 271645                     /usr/lib/ladspa/adsr_1653.so
7f5f49c2d000-7f5f49c2e000 r--p 00001000 08:05 271645                     /usr/lib/ladspa/adsr_1653.so
7f5f49c2e000-7f5f49c2f000 rw-p 00002000 08:05 271645                     /usr/lib/ladspa/adsr_1653.so
7f5f49c2f000-7f5f49c31000 r-xp 00000000 08:05 271683                     /usr/lib/ladspa/amp_1181.so
7f5f49c31000-7f5f49e30000 ---p 00002000 08:05 271683                     /usr/lib/ladspa/amp_1181.so
7f5f49e30000-7f5f49e31000 r--p 00001000 08:05 271683                     /usr/lib/ladspa/amp_1181.so
7f5f49e31000-7f5f49e32000 rw-p 00002000 08:05 271683                     /usr/lib/ladspa/amp_1181.so
7f5f49e32000-7f5f49e34000 r-xp 00000000 08:05 271554                     /usr/lib/ladspa/foverdrive_1196.so
7f5f49e34000-7f5f4a033000 ---p 00002000 08:05 271554                     /usr/lib/ladspa/foverdrive_1196.so
7f5f4a033000-7f5f4a034000 r--p 00001000 08:05 271554                     /usr/lib/ladspa/foverdrive_1196.so
7f5f4a034000-7f5f4a035000 rw-p 00002000 08:05 271554                     /usr/lib/ladspa/foverdrive_1196.so
7f5f4a035000-7f5f4a037000 r-xp 00000000 08:05 271597                     /usr/lib/ladspa/tap_pinknoise.so
7f5f4a037000-7f5f4a236000 ---p 00002000 08:05 271597                     /usr/lib/ladspa/tap_pinknoise.so
7f5f4a236000-7f5f4a237000 r--p 00001000 08:05 271597                     /usr/lib/ladspa/tap_pinknoise.so
7f5f4a237000-7f5f4a238000 rw-p 00002000 08:05 271597                     /usr/lib/ladspa/tap_pinknoise.so
7f5f4a238000-7f5f4a239000 r-xp 00000000 08:05 271471                     /usr/lib/ladspa/comb_splitter_1411.so
7f5f4a239000-7f5f4a439000 ---p 00001000 08:05 271471                     /usr/lib/ladspa/comb_splitter_1411.so
7f5f4a439000-7f5f4a43a000 r--p 00001000 08:05 271471                     /usr/lib/ladspa/comb_splitter_1411.so
7f5f4a43a000-7f5f4a43b000 rw-p 00002000 08:05 271471                     /usr/lib/ladspa/comb_splitter_1411.so
7f5f4a43b000-7f5f4a43d000 r-xp 00000000 08:05 271559                     /usr/lib/ladspa/svf_1214.so
7f5f4a43d000-7f5f4a63c000 ---p 00002000 08:05 271559                     /usr/lib/ladspa/svf_1214.so
7f5f4a63c000-7f5f4a63d000 r--p 00001000 08:05 271559                     /usr/lib/ladspa/svf_1214.so
7f5f4a63d000-7f5f4a63e000 rw-p 00002000 08:05 271559                     /usr/lib/ladspa/svf_1214.so
7f5f4a63e000-7f5f4a640000 r-xp 00000000 08:05 271663                     /usr/lib/ladspa/retro_flange_1208.so
7f5f4a640000-7f5f4a840000 ---p 00002000 08:05 271663                     /usr/lib/ladspa/retro_flange_1208.so
7f5f4a840000-7f5f4a841000 r--p 00002000 08:05 271663                     /usr/lib/ladspa/retro_flange_1208.so
7f5f4a841000-7f5f4a842000 rw-p 00003000 08:05 271663                     /usr/lib/ladspa/retro_flange_1208.so
7f5f4a842000-7f5f4a844000 r-xp 00000000 08:05 271482                     /usr/lib/ladspa/matrix_ms_st_1421.so
7f5f4a844000-7f5f4aa43000 ---p 00002000 08:05 271482                     /usr/lib/ladspa/matrix_ms_st_1421.so
7f5f4aa43000-7f5f4aa44000 r--p 00001000 08:05 271482                     /usr/lib/ladspa/matrix_ms_st_1421.so
7f5f4aa44000-7f5f4aa45000 rw-p 00002000 08:05 271482                     /usr/lib/ladspa/matrix_ms_st_1421.so
7f5f4aa45000-7f5f4aa4a000 r-xp 00000000 08:05 271577                     /usr/lib/ladspa/gong_1424.so
7f5f4aa4a000-7f5f4ac49000 ---p 00005000 08:05 271577                     /usr/lib/ladspa/gong_1424.so
7f5f4ac49000-7f5f4ac4a000 r--p 00004000 08:05 271577                     /usr/lib/ladspa/gong_1424.so
7f5f4ac4a000-7f5f4ac4b000 rw-p 00005000 08:05 271577                     /usr/lib/ladspa/gong_1424.so
7f5f4ac4b000-7f5f4ac5b000 r-xp 00000000 08:05 271634                     /usr/lib/ladspa/guitarix_freeverb.so
7f5f4ac5b000-7f5f4ae5a000 ---p 00010000 08:05 271634                     /usr/lib/ladspa/guitarix_freeverb.so
7f5f4ae5a000-7f5f4ae5b000 r--p 0000f000 08:05 271634                     /usr/lib/ladspa/guitarix_freeverb.so
7f5f4ae5b000-7f5f4ae5c000 rw-p 00010000 08:05 271634                     /usr/lib/ladspa/guitarix_freeverb.so
7f5f4ae5c000-7f5f4ae5e000 r-xp 00000000 08:05 271626                     /usr/lib/ladspa/split_1406.so
7f5f4ae5e000-7f5f4b05d000 ---p 00002000 08:05 271626                     /usr/lib/ladspa/split_1406.so
7f5f4b05d000-7f5f4b05e000 r--p 00001000 08:05 271626                     /usr/lib/ladspa/split_1406.so
7f5f4b05e000-7f5f4b05f000 rw-p 00002000 08:05 271626                     /usr/lib/ladspa/split_1406.so
7f5f4b05f000-7f5f4b06f000 r-xp 00000000 08:05 271651                     /usr/lib/ladspa/guitarix_compressor.so
7f5f4b06f000-7f5f4b26f000 ---p 00010000 08:05 271651                     /usr/lib/ladspa/guitarix_compressor.so
7f5f4b26f000-7f5f4b270000 r--p 00010000 08:05 271651                     /usr/lib/ladspa/guitarix_compressor.so
7f5f4b270000-7f5f4b271000 rw-p 00011000 08:05 271651                     /usr/lib/ladspa/guitarix_compressor.so
7f5f4b271000-7f5f4b273000 r-xp 00000000 08:05 271487                     /usr/lib/ladspa/sequencer32_1676.so
7f5f4b273000-7f5f4b472000 ---p 00002000 08:05 271487                     /usr/lib/ladspa/sequencer32_1676.so
7f5f4b472000-7f5f4b473000 r--p 00001000 08:05 271487                     /usr/lib/ladspa/sequencer32_1676.so
7f5f4b473000-7f5f4b474000 rw-p 00002000 08:05 271487                     /usr/lib/ladspa/sequencer32_1676.so
7f5f4b474000-7f5f4b476000 r-xp 00000000 08:05 271490                     /usr/lib/ladspa/sync_square_1678.so
7f5f4b476000-7f5f4b675000 ---p 00002000 08:05 271490                     /usr/lib/ladspa/sync_square_1678.so
7f5f4b675000-7f5f4b676000 r--p 00001000 08:05 271490                     /usr/lib/ladspa/sync_square_1678.so
7f5f4b676000-7f5f4b677000 rw-p 00002000 08:05 271490                     /usr/lib/ladspa/sync_square_1678.so
7f5f4b677000-7f5f4b67b000 r-xp 00000000 08:05 271540                     /usr/lib/ladspa/ambisonic2.so
7f5f4b67b000-7f5f4b87a000 ---p 00004000 08:05 271540                     /usr/lib/ladspa/ambisonic2.so
7f5f4b87a000-7f5f4b87b000 r--p 00003000 08:05 271540                     /usr/lib/ladspa/ambisonic2.so
7f5f4b87b000-7f5f4b87c000 rw-p 00004000 08:05 271540                     /usr/lib/ladspa/ambisonic2.so
7f5f4b87c000-7f5f4b87e000 r-xp 00000000 08:05 271593                     /usr/lib/ladspa/shaper_1187.so
7f5f4b87e000-7f5f4ba7d000 ---p 00002000 08:05 271593                     /usr/lib/ladspa/shaper_1187.so
7f5f4ba7d000-7f5f4ba7e000 r--p 00001000 08:05 271593                     /usr/lib/ladspa/shaper_1187.so
7f5f4ba7e000-7f5f4ba7f000 rw-p 00002000 08:05 271593                     /usr/lib/ladspa/shaper_1187.so
7f5f4ba7f000-7f5f4ba81000 r-xp 00000000 08:05 271476                     /usr/lib/ladspa/pointer_cast_1910.so
7f5f4ba81000-7f5f4bc80000 ---p 00002000 08:05 271476                     /usr/lib/ladspa/pointer_cast_1910.so
7f5f4bc80000-7f5f4bc81000 r--p 00001000 08:05 271476                     /usr/lib/ladspa/pointer_cast_1910.so
7f5f4bc81000-7f5f4bc82000 rw-p 00002000 08:05 271476                     /usr/lib/ladspa/pointer_cast_1910.so
7f5f4bc82000-7f5f4bc86000 r-xp 00000000 08:05 271595                     /usr/lib/ladspa/bandpass_iir_1892.soAborted (core dumped)

```

---

### Post by a-you on 2016-11-25
I'm thinking that these crashes might be due to old, bad plugins. I saw one post that said that the old calf plugins cause crashes like this. Seems like I should try uninstalling those and see what happens.

---

### Post by CrocoDuck on 2016-11-25
I am not too accustomed to read these particular error logs, but seems indeed a plugin related issue. Perhaps, spanned by this:

```

7f5f4bc82000-7f5f4bc86000 r-xp 00000000 08:05 271595                     /usr/lib/ladspa/bandpass_iir_1892.soAborted (core dumped

```

That plugin should be part of [swh-plugins]("https://apps.ubuntu.com/cat/applications/swh-plugins/"), so maybe try uninstall that package and see if you can make it any further.

---

### Post by a-you on 2016-11-25
@CrokoDuck thanks again for your help. I just tried removing that package but it didn't solve it. I also tried removing some other packages that seemed to be potentially problematic, but that didn't solve it either. Not sure what to try next...

Updating this comment: I tried uninstalling all ladspa plugins and it still didn't solve this, so I reinstalled them. Any ideas from out there would be appreciated, thanks in advance.

---

### Post by CrocoDuck on 2016-11-25
Uhm... I feel like there is some problem in memory allocation. At least, that is the impression I got by [Ducking the error message]("https://duckduckgo.com/?q=***+Error+in+%60audacity%27%3A+double+free+or+corruption+(fasttop)%3A+0x00007f5f400274c0+***+Warning%3A+failed+to+load+part%3C%3E!&atb=v38-2&ia=qa"). Give us the output of groups:

```

groups

```

Also, does the problem happen only if JACK is running? If you use qjackctl, give us the output of

```

cat .jackdrc

```

memtest is saying that your memory is ok. Good, but perhaps we should also run an userspace test and make sure programs can allocate memory. [This]("https://www.techwalla.com/articles/how-to-test-the-ram-on-linux") will tell you how.

---

### Post by a-you on 2016-11-27
Thanks again @CrocoDuck. No the problem doesn't only happen when jack is running.   Ardour4 now can run with jack or without, and the problem is there either way. And I was starting audacity without jack and got the above error messages.  Output of groups: myusername adm dialout fax cdrom floppy tape sudo audio dip video plugdev netdev lpadmin scanner sambashare  That last makes no sense as I don't use samba. But it's there anyway.  Output of cat .jackdrc:  /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2  Sorry it's getting scrunched again into 1 paragraph. Don't know how to stop that.  I ran the memtester and after a short while it prints "killed" then I check the exit status and it was 137. Hard to tell what that means.

---

### Post by CrocoDuck on 2016-11-27
You are in the audio group, which is OK. Nothing weird on JACK side either. I am puzzled by memtester. If memtester does not return 0 then your memory has a problem, but I am not sure why we have 137. Did you run it as:

```

sudo memtester size_of_RAM_in_MB number_of_tests

```

Let's also have a look at your /etc/security folder:

```

ls -la /etc/security/

```

Let us know more about how did you upgrade the RAM. Are all the RAM sticks of the same kind? What vendor are they? Are you sure they are OK for your motherboard? Did you install a fresh system on the upgraded RAM?

It is weird that only audio programs are having this problem. Or there is something specific in how they allocate memory or there is some configuration thing that snapped and prevents them from allocating correctly. You might try an [AVLinux]("http://www.bandshed.net/avlinux/") live and see whether the programs launch correctly on that.

EDIT:
I looked around and when a process exits with 137 it means [it was terminated by being sent a SIGKILL signal]("http://www.unix.com/302925510-post4.html?"). memtester never went around testing ram correctly. This makes sense considering the error message you got. Make sure you run it as above.

Let's get more info about your RAM:
```

cat /proc/meminfo 

```

---

### Post by a-you on 2016-11-28
Thanks again @CrocoDuck

I did run memtester that way, being careful to specify the amount of RAM that my system has. I bought 2 of the same RAM cards and according to the person at the store they were compatible with my machine. As I was mentioning before I did run the boot memory test option twice: back when I upgraded and just a few days ago, both times for several hours. Both times it reported no problems.

Contents of /etc/security (I deleted this just because I worry a bit about exposing my security configuration to the whole world; I can send it of course)

Re your question about a fresh system: I was running trusty until xenial came out. Then I installed that from scratch, so it's basically fresh. I didn't do an upgrade from trusty.

By the way I haven't disabled swap but I have it set lower than the amount of RAM I have. It's generally hardly touched.

cat /proc/meminfo:

```

MemTotal:        8156596 kB
MemFree:         3515724 kB
MemAvailable:    6077436 kB
Buffers:          246896 kB
Cached:          2314304 kB
SwapCached:            0 kB
Active:          2321184 kB
Inactive:        1753216 kB
Active(anon):    1514956 kB
Inactive(anon):    45012 kB
Active(file):     806228 kB
Inactive(file):  1708204 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:       4095484 kB
SwapFree:        4095484 kB
Dirty:               244 kB
Writeback:             0 kB
AnonPages:       1513312 kB
Mapped:           268284 kB
Shmem:             46772 kB
Slab:             448304 kB
SReclaimable:     352236 kB
SUnreclaim:        96068 kB
KernelStack:        9616 kB
PageTables:        40544 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8173780 kB
Committed_AS:    4482336 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:    727040 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      164308 kB
DirectMap2M:     8206336 kB

```

---

### Post by CrocoDuck on 2016-11-28
OK, seems like your system sees the RAM correctly. Let's have a look at limits.conf:

```

cat /etc/security/limits.conf

```

and at the contents of limits.d:
```

ls -la /etc/security/limits.d

```

Sorry about the fact that I am proceeding by baby steps, but I am not very sure about Ubuntu conf files directories as I switched to Arch Linux few years ago...

---

### Post by a-you on 2016-11-30
Thanks again @CrocoDuck. A quick question: is it dangerous that these security items are being revealed to the whole world?? Because if so maybe we could communicate by PM or in some way that doesn't expose security aspects of my system to everybody.

I'll be glad to post the contents of /etc/security/limits.conf and the contents of that folder if it's not potentially compromising my system; please tell me what you think.

I worry a bit that I'm showing the world security configuration items here. If that's problematic please let's continue in some less public way. Thanks again for all your help!

Hopefully I'm not offending you by asking. Basically what I would appreciate knowing is what connection do you see between the security configuration of my system and the fact that audio apps crash?? If I understood your thinking it would help a lot, thanks!

---

### Post by CrocoDuck on 2016-11-30
Ho there! /etc/security contains files that set the limits for the resources the programs can ask for. That is the reason why we are looking at it: to see if there is some rule that makes memory allocation hard for audio software. Most of the files there are supplied by PAM. Given that you have systemd (I think) we will probably need to look at /etc/security/limits.d/99-audio.conf, which is a file installed by JACK containing, in particular, the amount of RAM that can be allocated by JACK.

Here few links:
[http://superuser.com/questions/962683/in-linux-what-is-etc-security](http://superuser.com/questions/962683/in-linux-what-is-etc-security)
[https://linux.die.net/man/5/limits.conf](https://linux.die.net/man/5/limits.conf)
[https://wiki.archlinux.org/index.php/PAM](https://wiki.archlinux.org/index.php/PAM)
[https://wiki.archlinux.org/index.php/Professional_audio#System_Configuration](https://wiki.archlinux.org/index.php/Professional_audio#System_Configuration)

So, the files we are looking at are limited to resource allocation. So, there shouldn't be any sensible information in there (no passwords, no stuff like that), just system confs. Of course, read the links (and/or other material) and decide for yourself whether you want to share it or not. This is always a good rule to go by, I always think twice before posting online.

I am not too sure we will find something here tho, especially given that you run into this problem not only when running on JACK.

If you prefer, try an AVLinux live pendrive first, look if audio software runs ok there. If so, it really means there is something wrong configuration-wise on your installation. The easiest path might actually be to just make a new fresh installation.

OH WAIT.

How did you install your new Ubuntu? There was another Ubuntu installed on the same drive, wasn't it?

---

### Post by a-you on 2016-11-30
Hi and thanks again @CrocoDuck.  Re /etc/security thanks for explaining that. I'd like to read those links you provided, then I'll get back to you.  Re your question about my installation: no, I installed xenial from scratch so there was no other installation on the same drive. I should add though that I have a separate home partition and with each new system the home partition has in the past stayed the same. Meaning that any configuration files in there remained as they were. BUT this time with xenial I decided that I wanted to try to clean my home, so I went through and trashed files and folders there that related to apps that I don't use. Also I *think* that this time I deleted some of the files/folders relating to apps that I do use, so that they'd be regenerated as well. So it's basically as fresh an install as possible under the circumstances.  Yes, it seems like a good idea to try AVlinux.  "The easiest path might actually be to just make a new fresh installation." it might be. When I have a chance to I'll try AVlinux first though because that should be pretty revealing. Uh, sorry that it's squashing this into 1 paragraph again.

---

### Post by CrocoDuck on 2016-11-30
> **a-you said:**
> Re your question about my installation: no, I installed xenial from scratch so there was no other installation on the same drive. I should add though that I have a separate home partition and with each new system the home partition has in the past stayed the same. Meaning that any configuration files in there remained as they were. BUT this time with xenial I decided that I wanted to try to clean my home, so I went through and trashed files and folders there that related to apps that I don't use. Also I *think* that this time I deleted some of the files/folders relating to apps that I do use, so that they'd be regenerated as well. 

OK. I asked cause in my experience, few releases ago (2010 - 2012 era), I had the following problem: when installing Ubuntu on a hard drive where there was another Ubuntu, even if formatting the hard drive with the installer, it often resulted in a corrupted installation. That is why I ended up doing this:

Download an Ubuntu image and checksum it.
Boot with [SystemRescueCD]("http://www.system-rescue-cd.org/SystemRescueCd_Homepage") and -erase- the hard drive.
Boot the Ubuntu image and install it on the erased hard drive.

I hope the installer improved in the meanwhile.

Deleting conf files in home shouldn't be too much of an issue in general, as these usually have counter parts in /etc where the applications fall back if no user configuration is found. However, it might be as well that some program is looking for user configuration, it is not founding it, and it has not the privileges to access system wise conf files for some reason. Which is why conf files should never be handled manually, but by l[etting the package manager to do the job]("http://askubuntu.com/questions/231562/what-is-the-difference-between-apt-get-purge-and-apt-get-remove#231568"). I wonder whether something like this happened.

Do you have an Intel CPU? Maybe worth installing [microcode ]("https://wiki.archlinux.org/index.php/Microcode")(another long shot, it does not explain why only audio is affected). [This]("https://launchpad.net/ubuntu/+source/intel-microcode") should be the Ubuntu package, you should be able to apt-get it without problems. Check whether there is something in particular to do to install microcode under Ubuntu.

---

### Post by a-you on 2016-11-30
Thanks @CrocoDuck again. Your idea about the conf files is a good point. To be honest I'm not sure if I deleted any of the ones that related to programs I actually use. I may not have. I just now don't exactly recall now for sure. I actually think that I didn't, now, looking back.  Yes I have an intel CPU and I did install the microcode. I wonder if I should try uninstalling that??? I installed it through the "Settings" menu item, which allows one to access "drivers" and the microcode came up under drivers.

---

### Post by CrocoDuck on 2016-11-30
uhm... I think it is good you have microcode actually. I have seen a post somewhere (I lost the link) where a similar problem was solved by installing micro-code. So I guess we are good on that side. Let's try AVLinux first and see how it goes.

---

### Post by a-you on 2016-12-09
I just now tried AVLinux by downloading the iso, burning that not to a DVD but to a USB stick with startup disk creator but when I tried booting it up to test drive it it asked me for a password. Unbelievable. So there was no way to test that.  Sorry to have been out of touch. Just had a lot of work.

---

### Post by coffeecat on 2016-12-09
> **a-you said:**
> Unbelievable.

Not if you read the user manual for AVLinux, or even the home page for the AV Linux website:

[http://www.bandshed.net/avlinux/](http://www.bandshed.net/avlinux/)

User names and passwords for their live session are clearly explained.

It always helps if you read the documentation for any distro you want to try. I find it helps avoid aggravation and frustration.

Anyway - AV Linux is not an Ubuntu flavour. Indeed, it is not even based on Ubuntu, so if you want help with AV Linux, please either post in the appropriate sub-forum in [this section](https://ubuntuforums.org/forumdisplay.php?f=446), or wherever AV Linux offers support. If indeed it does, but I'll leave you to find that if you need it.

---

### Post by a-you on 2016-12-09
Thanks @coffeecat for that. Guess I didn't read that part. And I didn't realize that it's not based on ubuntu. But I'll still check  it out because I want to see if it solves the other issues with  programs crashing on start. If so then hmm, maybe time to try another  distro. Too bad because I like ubuntu, so if the programs work in  AVLinux then perhaps there's another solution. One based at least on  debian if not ubuntu, though I would prefer an ubuntu based system if at  all possible.

---

### Post by a-you on 2016-12-09
@CrocoDuck if you're still paying attention to this thread... Sorry, I had a lot of work for a few days, but I did try AVLinux. Starting audacity from a terminal in that showed a lot of errors. I didn't carefully check whether they were exactly the same errors as I get with ubuntu studio, but the list was about as long and I would guess that they were much the same.

I didn't realize that AVLinux is not based on ubuntu. It seems to be based on arch though I'm not sure. But anyway it looks like there's an issue no matter which distro I try.

---

### Post by CrocoDuck on 2016-12-09
> **coffeecat said:**
> 
Anyway - AV Linux is not an Ubuntu flavour. Indeed, it is not even based on Ubuntu, so if you want help with AV Linux, please either post in the appropriate sub-forum in [this section]("https://ubuntuforums.org/forumdisplay.php?f=446"), or wherever AV Linux offers support. If indeed it does, but I'll leave you to find that if you need it.

I suggested to a-you to try an AVLinux live image just to help troubleshooting his currently malfunctioning Ubuntu Studio install. In fact, I am not entirely sure he is not having an hardware problem. If AVLinux was working correctly we would have found that Ubuntu was most likely having a configuration issue. Unfortunately, both Ubuntu and AVLinux work in a weird way. I am really starting thinking there is something wrong with a-you's RAM.

Please, if you can, return:


[LIST]
[*]Your complete motherboard model 
[*]Each of your RAM sticks vendors 
[*]Each of your RAM sticks size 
[*]Each of your RAM sticks type 
[*](It would help to have the complete model name of the RAM sticks) 
[/LIST]
 
I am not sure I can guide you through RAM troubleshooting, as I am not very expert on these sort of things, but we can try. Alternatively, if we find something that smells bad, you could open a new thread in the hardware forum.

> **a-you said:**
> 
I didn't realize that AVLinux is not based on ubuntu. It seems to be  based on arch though I'm not sure. But anyway it looks like there's an  issue no matter which distro I try.

AVLinux is Debian image tuned for pro-audio.

---

### Post by a-you on 2016-12-11
Thanks @CrocoDuck. I'll collect that info and post it.

---

### Post by a-you on 2016-12-13
In the meantime I just realized there's another symptom: if one user is logged in and starts the jack server other users that log in have no audio via pulse!! That seems totally screwy to me!

---

### Post by a-you on 2016-12-20
Hi @CrocoDuck if you're still following this thread.

> **CrocoDuck said:**
> 

Please, if you can, return:          
[LIST]
[*]Your complete motherboard model 
[*]Each of your RAM sticks vendors 
[*]Each of your RAM sticks size 
[*]Each of your RAM sticks type 
[*](It would help to have the complete model name of the RAM sticks) 
[/LIST]
       

As for the motherboard it's difficult to get info on that because this is a laptop. I'd pretty much have to take the computer apart to get at it, and even then I don't know for sure that there'd be anything printed on it. And at the moment it's not practical to take it apart since I have to use it for work every day.  But it would seem that the motherboard was manufactured by Sony since this is a viao VPCF116FX.

lshw seems to confirm this. That is, it doesn't report any other vendor for the motherboard specifically, so I would assume it means that it's from Sony.

Now as for the RAM I'll have to take the sticks out to read the model and vendor but for now I do have this info:

* Memory Device
      Error Information Handle: Not Provided
      Total Width: 64 bits
      Data Width: 64 bits
      Size: 4096 MB
      Form Factor: SODIMM
      Set: None
      Locator: SODIMM1
      Bank Locator: Bank 0
      Type: DDR3
      Type Detail: Unknown
* Memory Device
      Error Information Handle: Not Provided
      Total Width: 64 bits
      Data Width: 64 bits
      Size: 4096 MB
      Form Factor: SODIMM
      Set: None
      Locator: SODIMM2
      Bank Locator: Bank 1
      Type: DDR3
      Type Detail: Unknown

When I upgraded the RAM from 4GB to 8GB the salesperson said (I asked) that the RAM was appropriate for my computer. It's possible that he was wrong of course, but I did run memtest overnight twice and no errors were reported. If you think the RAM is at fault though I can try putting the original sticks back in and checking if that makes any difference.

So it would appear that in order to stop the forum software from putting everything into a single paragraph one has to have javascript enabled!!!

---

### Post by CrocoDuck on 2016-12-21
I think it might be worth for you to post the whole output of lshw at this point. Memtester might not be telling us the whole story and we have been unable to test the ram from user space, which might be hiding some detail. I will search for hardware info about your laptop model online. We should find everything this way, so do not take your computer apart.

> **a-you said:**
> In the meantime I just realized there's another  symptom: if one user is logged in and starts the jack server other users  that log in have no audio via pulse!! That seems totally screwy to  me!
This might actually be normal. By default when JACK is running all other sound servers are "silenced". Pretty much, JACK monopolizes communication with the hardware drivers. In fact, if you want to use PulseAudio and JACK together, you need to arrange for PulseAudio to talk with JACK. This is done automatically in UStudio for your user, but I don't think it is done across different users. Actually, I don't know if it is even possible to have a PuseAudio instance by an user providing a JACK socket for a JACK instance of another user...

---

### Post by CrocoDuck on 2016-12-21
From what I gather by having a look online I would think that perhaps your ram is fine, but better to see lshw first. Not really sure about what to think now really, a part for checking for memory limits in /etc/security. Actually, we don't need you to post back the content if you don't feel comfortable in doing so. Have a look at /etc/security/limits.conf. This should not be needed anymore, so perhaps all the items are commented (have an # in front). Check that this is the case. In my system the limits to how much ram audio programs can allocate is set by /etc/security/limits.d/99-audio.conf:

```

@audio 	- rtprio 	99
@audio 	- memlock 	unlimited
```

As you can see this file contains only system audio settings and not any sensible information whatsoever. Notice that the memlock is unlimited: my audio programs can ask how much ram as they want to the operating system. You might want to check that this is also the case for you.

---

### Post by a-you on 2016-12-21
Hi and thanks again @CrocoDuck.

I'm slightly nervous about posting the raw output of lshw, only because I don't know what that might reveal to the whole world. Sorry if I'm being unnecessarily nervous. It's only that I don't really know enough about what the ramifications of that could be if the whole world sees exactly what my hardware contains. Mind you, it would be the same for any Sony Vaio VPCF116FX.

As you predicted, every line in /etc/security/limits.conf is commented out. I assume that's normal for ubuntu studio because I haven't changed it, so it must have been set that way by the developers of ubuntu studio, or by Canonical.

In /etc/security/limits.d/audio.conf the limits are like yours except that mine has rtprio set to 95. But the memlock line says "unlimited."

And btw yes I read that audio is blocked for other users when they are all in the audio group. Actually that was listed as a bug if I recall correctly. And it seems to be one to me, since I would think that ideally each logged in user should have their own audio. It's not really an issue, so no biggie. As a test I have removed the second user from the audio group to see what happens.

---

### Post by CrocoDuck on 2016-12-21
Looking at lshw would give info about both the hardware and how your system recognizes it, which is probably the most important part. I don't think it can expose you to any danger, but only share what you are comfortable with sharing ;). I am afraid I really have no ammo left on this... A part maybe this:

> **a-you said:**
> 
It's so frustrating because with trusty everything worked wonderfully

You might try a trusty live, just like we did with AVLinux. We know that it was working, so if it doesn't now it would reinforce the hardware malfunction theory. If it works, you might just reinstall it to be honest. It is an LTS that is still going to have support for some time, so I think it might be worth it. Apparently support for the standard Ubuntu Desktop will last 5 years (so until 2019). This should mean that you could install Ubuntu Desktop and then just add the Ubuntu Studio packages.

---

### Post by a-you on 2016-12-22
Thanks @CrocoDuck that's a good idea to try a trusty live and see if it works. It would be a shame to have to go back to using trusty since several programs are updated (Ardour for example, and now MusE actually works on my system; it didn't until about a week ago when I ran the software updater). I have to admit that I'm also wondering about other audio/video distros, like possibly mint (I like nemo) or debian with audio and video stuff installed. I'm also now reading through every audio troubleshooting guide I can get ahold of very thoroughly (again). Thanks for all your help!! I really appreciate it!

---

### Post by CrocoDuck on 2016-12-22
Sorry we couldn't really fix this. About other distros, you could check [this post]("https://thecrocoduckspond.wordpress.com/2015/10/22/pro-audio-linux-distributions/") in my blog. I think you might like KXStudio. Cool thing is that KXStudio has repositories you can add on top of any Debian-Ubuntu distro. [Have a look]("https://linuxmusicians.com/viewtopic.php?f=19&t=9666"). It works also on Mint and there is indeed a [ready to use image]("http://mayastudio.tumblr.com/64bit") for LTS Mint releases.

---

### Post by a-you on 2016-12-26
Thanks @CrocoDuck really a lot for all your help. I have started a question via launchpad. Hopefully some of the alsa developers might see that. I imagine that if anybody might know the answer it would be them.

Also thanks for the link to KXStudio. I'd like to try that. If that solves it then it'd be wonderful. I just looked at your page and that's a nice list of multimedia distros :-)

---

