---
title: "avidemux can't open files from dvd unknown riff file"
date: 2010-01-20
forum: Ubuntu Studio
---

### Post by anco on 2010-01-20
I have been searching but have not found. A friend made a dvd with windows moviemaker, I try to open the .DAT files from the DVD to also cut a few small mpeg parts to be sent by email.

I wanted to use Avidemux as I don't have windows... but it doesn't read the files, while mplayer has no problem showing these files. Anybody an idea?

[I]anco@edubuntu:~/Bureau$ avidemux Keep\ On\ Your\ Light.dat 
*************************
  Avidemux v2.5.1
*************************
 [http://www.avidemux.org](http://www.avidemux.org)
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , [email]nestordi@augcyl.org[/email]
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, [email]amistry@am-productions.biz[/email]
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.4.1
Build Target: Linux (x86-64)
User Interface: GTK+ (2.18.3)

Large file available: 1 offset

Initialising prefs
Directory /home/anco/.avidemux exists.Good.
Using /home/anco/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
		MMX detected 
		3DNOW detected 
		MMXEXT detected 
		SSE detected 
		SSE2 detected 
		SSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

 Registering Encoders
*********************
MJPEG encoder registered
FFmpeg encoder registered

2 encoder(s) registered

[SDL] Version: 1.2.13
[SDL] Initialisation succeeded
[SDL] Video Driver: x11


[Locale] setlocale fr_FR.UTF-8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _Fichier

Initializing Dithering tables
[COREUI] Compiled with 01.00.01
[COREUI] Linked with   01.00.01
[CoreUI] Compiled with patch version 1, using 1
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Internal Filters
******************************

[ADM_ad_plugin] Scanning directory /usr/lib/ADM_plugins/audioDecoder/
[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_a52.so, desc: LibAC3 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_vorbis.so, desc: libVorbis decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_Mad.so, desc: LibMad decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_faad.so, desc: Faad2 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Scanning done, found 4 codec
[ADM_vf_plugin] Scanning directory /usr/lib/ADM_plugins/videoFilter/
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendDgBob.so as  DG Bob
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaU.so as  Chroma U
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_gtk.so as  MPlayer resize
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mcdeint.so as  mcDeinterlace
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Deinterlace.so as  Deinterlace
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartPalShift.so as  PAL smart
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_addborders.so as  Add black borders
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_gtk.so as  asharp
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapuv.so as  Swap U and V
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Denoise.so as  Denoise
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_gtk.so as  MPlayer hue
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_dropOut.so as  Drop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaV.so as  Chroma V
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_palShift.so as  PAL field shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutiongauss.so as  Gauss smooth
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blackenBorders.so as  Blacken borders
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lavDeinterlace.so as  libavcodec deinterlacer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_gtk.so as  Chroma shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_reverse.so as  Reverse
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_gtk.so as  Luma equalizer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_tdeint.so as  TDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Whirl.so as  Whirl
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapField.so as  Swap fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_gtk.so as  MPlayer eq2
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fade.so as  Fade
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Mosaic.so as  mosaic
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionsharpen.so as  Sharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mergeField.so as  Merge fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_gtk.so as  Cnr2
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Pulldown.so as  Pulldown
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmean.so as  Mean
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3d.so as  MPlayer denoise3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSmooth.so as  MSmooth by Donald Graft
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_stackField.so as  Stack fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Tisophote.so as  TIsophote
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vlad.so as  Temporal Cleaner
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendRemoval.so as  Blend Removal
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_soften.so as  Soften
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_qt4.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_kernelDeint.so as  KernelDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_unstackField.so as  Unstack fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_gtk.so as  MPlayer delogo
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_gtk.so as  Avisynth ColorYUV
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vflip.so as  Vertical flip
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_separateField.so as  Fade
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmedian.so as  Median
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_qt4.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepEvenField.so as  Keep even fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartSwapField.so as  Smart swap fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_telecide.so as  Decomb Telecide
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hzStackField.so as  separatefields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3dhq.so as  MPlayer hqdn3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_resampleFps.so as  Resample fps
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_gtk.so as  Subtitler
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_FluxSmooth.so as  FluxSmooth
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lumaonly.so as  Luma only
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Delta.so as  Luma delta
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Crop_gtk.so as  Crop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_gtk.so as  Resize
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_crop_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_crop_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSharpen.so as  MSharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_rotate.so as  Rotate
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_largemedian.so as  Median (5x5)
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_yadif.so as  yadif
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_gtk.so as  Contrast
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_qt4.so]: libADM_UIQT4.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_forcedPP.so as  Forced postprocessing
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_decimate.so as  Decomb Decimate
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_ssa.so as  ***
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepOddField.so as  Keep odd fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Stabilize.so as  Light denoiser.
[ADM_vf_plugin] Scanning done
[ADM_av_plugin] Scanning directory /usr/lib/ADM_plugins/audioDevices/
Name :Oss ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_oss.so as  Oss audio device (c) mean
Name :PulseAudioS ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_pulseAudioSimple.so as  PulseAudioSimple audio device (c) mean
Name :Sdl ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_sdl.so as  Sdl audio device (c) mean
Name :Alsa ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_alsa.so as  Alsa audio device (c) mean
Symbol loading failed for /usr/lib/ADM_plugins/audioDevices//libADM_av_jack.so
/usr/lib/ADM_plugins/audioDevices//libADM_av_jack.so:CannotLoad
[ADM_av_plugin] Scanning done
[ADM_ae_plugin] Scanning directory /usr/lib/ADM_plugins/audioEncoders/
[AudioEncoder] Loaded TwoLame version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so as  TwoLame MP2 encoder plugin Mean 2008
[AudioEncoder] Loaded PCM version 01.00.00 wavTag :0x1
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_pcm.so as  PCM encoder plugin Mean 2008
[AudioEncoder] Loaded Faac version 01.00.00 wavTag :0xff
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_faac.so as  Faac AAC encoder plugin Mean 2008
[AudioEncoder] Loaded LavAC3 version 01.00.00 wavTag :0x2000
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_ac3.so as  AC3 LavEncoder encoder plugin Mean 2008
[AudioEncoder] Loaded Lame version 01.00.00 wavTag :0x55
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lame.so as  Lame MP3 encoder plugin Mean 2008
[AudioEncoder] Loaded Vorbis version 01.00.00 wavTag :0x676f
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_vorbis.so as  Vorbis encoder plugin Mean 2008
[AudioEncoder] Loaded LavMP2 version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_mp2.so as  MP2 LavCodec encoder plugin Mean 2008
[ADM_ae_plugin] Scanning done
[ADM_ad_plugin] Scanning directory /home/anco/.avidemux/plugins/audioDecoder/
[ADM_ad_plugin] Cannot parse plugin
[ADM_vf_plugin] Scanning directory /home/anco/.avidemux/plugins/videoFilter/
[ADM_vf_plugin] Cannot parse plugin
[ADM_vidEnc_plugin] Scanning directory /usr/lib/ADM_plugins/videoEncoder/
ignored: xvid
ignored: avcodec
ignored: x264
[Xvid] Initialising Xvid
[Xvid] Build: xvid-1.1.2
[Xvid] SIMD supported: (cf)
		MMX
		MMXEXT
		SSE
		SSE2
		ALTIVEC
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_x264.so, desc: x264 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: DV video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFV1 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFVHuff video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: Huffyuv video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Scanning done, found 6 codec
Found 19 video encoder
Found 8 audio encoder
Found 0 Copy audio encoder
Found 1 MP2 (Twolame) audio encoder
Found 2 PCM audio encoder
Found 3 AAC (Faac) audio encoder
Found 4 AC3 (lav) audio encoder
Found 5 MP3 (lame) audio encoder
Found 6 Vorbis audio encoder
Found 7 MP2 (lav) audio encoder
[AudioEncoder] Selected copy for index 0, tag 0x2ad0f530 
Found 13 Format 
Directory /home/anco/.avidemux/custom/ exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
The screen seems to be 1024 x 768 px
/dev/input/event0: Permission non accordée
/dev/input/event1: Permission non accordée
/dev/input/event2: Permission non accordée
/dev/input/event3: Permission non accordée
/dev/input/event4: Permission non accordée
No physical Jog/Shuttle device found.
Spidermonkey initialized.
No crash file (/home/anco/.avidemux/crash.js)

 *** Automated : 52 entries*************
46464952 -> 46464952
 
 Riff file detected... 
 Unknown Riff...
 ********** Automation ended***********
Deleting post proc
[GTK] Changing size to 0 0
Cleaning up
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
[SDL] Quitting...
End of cleanup

Images stat:
___________
Max memory consumed (MB)     : 0
Current memory consumed (MB) : 0
Max image used               : 0
Cur image used               : 0
Global mem stat
______________
	Memory consumed: 0 (MB)

Goodbye...
[/I]


Start from the commandline shows me an error on unknown RIFF file, but I have not found the right information yet.

Thanks

---

