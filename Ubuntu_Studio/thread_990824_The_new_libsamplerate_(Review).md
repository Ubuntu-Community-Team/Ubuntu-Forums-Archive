---
title: "The new libsamplerate (Review)"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by clubsoda on 2008-11-23
[size=3]**Introduction**[/size]
If your soundcard operates at 48kHz (most) and you like playing CDs or music streamed at 44.1kHz (most) then somewhere in your computer there's a sample rate conversion taking place.  In Ubuntu this is handled in the background by the libsamplerate library.  Converting between sample rates involves a compromise between accuracy and computation time.

Back in March, "[Secret Rabbit Code](http://www.mega-nerd.com/SRC/)" guru Erik de Castro Lopo released an updated version of libsamplerate, promising "huge quality improvements to two best SINC based converters".  This new version has arrived with Intrepid but can also be dropped directly into earlier versions of Ubuntu  because its only dependency is libc6.

I thought it would be interesting to see how libsamplerate measures up.

[SIZE="3"]**Conversion from 44.1kHz to 48kHz**[/SIZE]
The delta Dirac function is a single non-zero pulse.  Running it through a digital filter allows us to see the profile of the filter and hints at the complexity of the internal calculation.
<IMAGE 1> [img]http://ubuntuforums.org/attachment.php?attachmentid=93806&stc=1&d=1227432029[/img] (log in if not visible)
Evidently the Medium and Best Sinc converters are slightly more complex in v0.1.3 than previously.  Audacity looks disappointing, with its "Best" setting coming up short of the Fast converter in libsamplerate.  I suspect this is due to Audacity being a cross-platform editor which contains an outdated snapshot of the libsamplerate code.  

Next let's have a look at the CPU requirements for real-time conversion (500MHz Pentium III baseline :-$, [nbench](http://www.tux.org/~mayer/linux/bmark.html) floating point index: 4.238 8-[).
<IMAGE 2> [img]http://ubuntuforums.org/attachment.php?attachmentid=93807&stc=1&d=1227432029[/img] (log in if not visible)
The good news is that Fast Sinc (the default converter) is more efficient than before, producing identical output in less time.  On the baseline machine, Fast Sinc will occupy 23% CPU.  Medium Sinc is doing more work in about the same time as before but Best Sinc's demands have increased significantly, chewing up over 1GHz of CPU.  

How clean are these conversions?  Convert a 32-bit floating point sine wave and look for spurious signals.
<IMAGE 3> [img]http://ubuntuforums.org/attachment.php?attachmentid=93808&stc=1&d=1227432029[/img] (log in if not visible)
Since 48kHz is not an exact multiple of 44.1kHz, the Zero Order Hold algorithm adds a lot of distortion.  It gives music a metallic ringing.
Linear interpolation is surprisingly good.  It makes music sound a bit fuzzy, that's all.
Fast Sinc exceeds the 96dB dynamic range of 16-bit sound.  This is the default SRC (sample rate converter) in Ubuntu.
For 24-bit work, Medium or Best Sinc may be preferable and the improvements in the newer version can be seen in the above numbers.


[SIZE="3"]**Conversion from 96kHz to 44.1kHz**[/SIZE]
Recent model audio recorders and interfaces offer 96kHz as a standard sampling rate but this will usually have to be down-converted to 44.1kHz for delivery on CD.
<IMAGE 4> [img]http://ubuntuforums.org/attachment.php?attachmentid=93809&stc=1&d=1227432029[/img] (log in if not visible)
The Hardy version performed poorly in this test with Fast Sinc actually measuring better than the (supposedly superior) Medium and Best Sinc converters.  It's good to see this is now fixed.

<IMAGE 5> [img]http://ubuntuforums.org/attachment.php?attachmentid=93810&stc=1&d=1227432029[/img] (log in if not visible)
However, Best Sinc in Intrepid is a CPU hog!  With Medium Sinc so close to achieving the theoretical 24-bit dynamic range of 144dB, it doesn't seem worthwhile to throw five times as much computing power at the problem for such a minor improvement.

[SIZE="3"]**Conclusion**[/SIZE]
Winner!  Version 0.1.3 of libsamplerate is a substantial upgrade over its predecessor.  In default Fast Sinc mode it is 8% more efficient, which means more CPU left over for everything else.
For purists with 24-bit soundcards, Medium Sinc is the obvious choice, the new library producing cleaner output for only a tiny increase in CPU demand.
As mentioned earlier, it is not necessary to upgrade to Intrepid to take advantage of [the new libsamplerate](http://packages.ubuntu.com/intrepid/libsamplerate0).

========================================

[SIZE="3"]**Resources**[/SIZE]
The above tests were done with a handy utility called **sndfile-resample** which is part of the *samplerate-programs* package, plus the **time** command for calculating CPU demand.  Note that these artefact tests are only indicative because the test signal is a single frequency sine wave.  Some more extensive test results can be seen at [http://src.infinitewave.ca/](http://src.infinitewave.ca/), with frequency sweeps through the audible spectrum and beyond, plus impulse response and filter response graphs.  

[SIZE="3"]**Improvements**[/SIZE]
Could libsamplerate be improved further?  Arguably there is little to be gained in chasing even higher signal-to-noise ratios unless the computational load can be held in check.  It would be interesting to benchmark outright conversion speed against some of the commercial packages.  
About the only feature missing is something found in very few applications (such as Sony Vegas, r8Brain Pro or iZotope RX), a tailored impulse response with a very short attack time.  This is said to eliminate so-called "pre-ring" but its main benefit is very low latency.  As it is, the latency of the Medium Sinc converter is under 1ms so this isn't really an issue.
According to the Infinitewave tests, libsamplerate's Best Sinc filter is linear-phase with negligible aliasing, so it's clearly in the professional league.

---

### Post by Stochastic on 2008-11-23
I find quality is more important than number of CPU cycles taken - and in this category, 1.3 is a clear winner.  Here are some more thorough and descriptive tests.  Libsamplerate is also known as Secret Rabbit Code (which is what it's called in these tests): [http://src.infinitewave.ca/](http://src.infinitewave.ca/)

Secret Rabbit Code 1.3 stacks up quite well against the major audio softwares, but still doesn't surpass Sox - another free alternative.

There's actually a new version out that didn't make it into Intrepid 1.4, but supposedly it's just a bug-fix release.

---

