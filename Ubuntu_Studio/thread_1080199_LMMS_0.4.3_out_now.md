---
title: "LMMS 0.4.3 out now"
date: 2009-02-25
forum: Ubuntu Studio
---

### Post by simtaalo on 2009-02-25
copied from email sent out on mailing list

[quote=toby@lmms]
Hi folks,
 
We're glad to announce the availability of LMMS 0.4.3. This version is a 
maintainance release of the 0.4.x series. It fixes most of the bugs found in 
version 0.4.2 and brings in improvements on performance and stability. Thanks 
to all who helped making up this release (especially those who kept up testing 
and reporting bugs)!
 
 
Detailed changes: 
================= 
 
Core: 
* fixed various bugs regarding MIDI recording and record accompany 
* do not lockup when freezing pattern 
* sampleBuffer: fixed small bug in usage of libsamplerate API which caused 
lots of zero samples at the end of various samples (e.g. in 
AudioFileProcessor) 
* sampleBuffer: do not load samples bigger than 100 MB 
* integrated latest libsamplerate which is both faster and more reliable 
* various fixes to allow compilation with upcoming GCC 4.4 
* simplified formulas for calculating envelope and LFO data resulting in about 
3x performance when changing envelope or LFO parameters frequently (e.g. by 
automation) 
* audio mixer: heavily improved organization of worker-threads resulting in 
much better performance and stability (especially with Hyperthreading-enabled 
CPUs) 
 
GUI: 
* update patternView after freezing 
* fixed painting of frozen patterns 
* make space always play song when in Song-Editor regardless of last button 
pressed 
* rewrote timing of fading animation for not postponing updates of hidden 
fadeButton until it becomes visible 
* disable output monitor per default and show a hint on how to enable 
* small cosmetic improvements 
* Piano-Roll: fixed bug that alloed to move notes past the beginning via 
shift+left 
* fixed unquantized BB-objects dragging in Song-Editor, use Alt modified 
instead Ctrl 
* fixed cloning of Beat/Bassline track 
* fixed infinite recursion in mouse-event-handling of knob on Mac OSX 
 
Plugins: 
* Sf2Player: update patch after loading settings (i.e. project or preset) 
* FLP import: properly initialize isMuted member - fixes muted FX channels 
when importing older FL files 
 
Win32 build: 
* used latest snapshot of GCC 4.3.x series for compiling 
* integrated latest snapshots of Qt 4.4.x 
* upgraded libsndfile from 1.0.17 to 1.0.18 
 
 
 
The download is available at  
 
[http://sourceforge.net/project/showfiles.php?group_id=105168](http://sourceforge.net/project/showfiles.php?group_id=105168)
 
Ubuntu packages of lmms and lmms-extras for Intrepid and Hardy (NEW) can be 
found at
 
[https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa)
 
 
More information is available at the project-homepage  
 
[http://lmms.sourceforge.net](http://lmms.sourceforge.net)  
 
and the Wiki  
 
[http://lmms.sourceforge.net/wiki](http://lmms.sourceforge.net/wiki)  
 
Please also notice the LMMS Sharing Platform (LSP):  
 
[http://lmms.sourceforge.net/lsp.php](http://lmms.sourceforge.net/lsp.php)
 
 
Toby
in the name of the LMMS developer team[/quote]

any lmms users out there old or new, come join us in the irc channel on freenode ##lmms

---

