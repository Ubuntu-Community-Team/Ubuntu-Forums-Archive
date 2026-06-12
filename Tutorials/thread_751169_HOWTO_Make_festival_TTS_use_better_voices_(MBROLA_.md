---
title: "HOWTO: Make festival TTS use better voices (MBROLA / CMU / HTS)"
date: 2008-04-10
forum: Tutorials
---

### Post by MonkeeSage on 2008-04-10
**[size="4"][color="#da0000"]Introduction[/color][/size]**

[Festival]("http://www.cstr.ed.ac.uk/projects/festival/") is a Text-To-Speech synthesis system developed at the University of Edinburgh. It can be used with several different voices, which are the models and data it uses to convert typed text into audible speech.

This HOWTO is meant to be a centralized collection of information about how to install the currently available voices for the Festival TTS. While sections of this HOWTO may apply to installing voices for other languages, it is primarily concerned with the English language voices.

The layout of this HOWTO is as follows:

[list]
 [*]Installing the standard Festvox diphone voices
 [*]Installing the enhanced MBROLA voices
 [*]Installing the enhanced CMU Arctic voices
 [*]Installing the enhanced Nitech HTS voices
 [*]Testing voices and choosing a default voice
 [*]Installing Festival 1.96 from source
[/list]

Before we get started, make sure all of the preliminary packages are installed on your system with the following command:

```

sudo apt-get install festival festlex-cmu festlex-poslex festlex-oald libestools1.2 unzip

```


**[size="4"][color="#da0000"]Installing the standard Festvox diphone voices[/color][/size]**

These are the voices that are supplied by the [Festvox project]("http://festvox.org/index.html"), which is run by the Carnegie Mellon University [speech group]("http://www.speech.cs.cmu.edu/"). See the [voice demo page]("http://festvox.org/voicedemos.html") (kal, ked, don and rab are the voices of interest). Of all of the voices we are concerned with, these take up the smallest size on disk, and are the only voices currently in the Ubuntu package tree. All of the other voices have to be installed manually. However, these are also the poorest quality voices and currently, on my computer, they cause festival to segfault (though I have used them successfully with other set-ups in the past). YMMV.

Some of the voices have 8k and 16k versions. This is the output frequency of the audio synthesis. The 16k versions have higher quality output and sound better. The four English voices are:

festvox-don
festvox-rablpc[8|16]k
festvox-kallpc[8|16]k
festvox-kdlpc[8|16]k

**[size="3"][color="#a6926b"]Searching for other voices to install[/color][/size]**

To find all the available festvox voices, execute the following command:

```

apt-cache search festvox-*

```


**[size="3"][color="#a6926b"]Installing the voices[/color][/size]**

Once you've decided on the voices to install, just install them as you would any other apt package. For example, this command will install all of the English voices using the higher quality 16k voices:

```

sudo apt-get install festvox-don festvox-rablpc16k festvox-kallpc16k festvox-kdlpc16k

```


**[size="4"][color="#da0000"]Installing the enhanced MBROLA voices[/color][/size]**

These voices are provided by the [MBROLA project]("http://tcts.fpms.ac.be/synthesis/mbrola.html"), run by the TCTS Lab of the Faculté Polytechnique de Mons in Belgium. They offer several voices, in a variety of languages, which sound much better than the Festvox diphone voices. The database of voices can be viewed at the project's [download page]("http://tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html"). See the [voice demo page]("http://www.cs.cmu.edu/~awb/festival_demos/userin.html") (the us1, us2 and us3 are the voices of interest). To use the MBROLA voices we need three parts: (1.) the mbrola binary program that parses a tokenstream the festival program feeds it and returns audio data back to festival, (2.) the MBROLA voices, and (3.) the Festvox wrappers to let the festival program use the voices. This may sound scary, but it's really very easy to do.

**[size="3"][color="#a6926b"]Downloading the voices, binary and wrappers[/color][/size]**

We will download everything we need for the English voices into a temporary directory (total download size is approximately twenty megs):

```

mkdir mbrola_tmp
cd mbrola_tmp/
wget http://tcts.fpms.ac.be/synthesis/mbrola/bin/pclinux/mbrola3.0.1h_i386.deb
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us1/us1-980512.zip
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us2/us2-980812.zip
wget -c http://tcts.fpms.ac.be/synthesis/mbrola/dba/us3/us3-990208.zip
wget -c http://www.festvox.org/packed/festival/latest/festvox_us1.tar.gz
wget -c http://www.festvox.org/packed/festival/latest/festvox_us2.tar.gz
wget -c http://www.festvox.org/packed/festival/latest/festvox_us3.tar.gz

```


**[size="3"][color="#a6926b"]Installing the binary, unpacking the voices and wrappers[/color][/size]**

Since the MBROLA project has kindly provided us with a binary deb, we can skip the step of building the binary from souce and just use dpkg to install it:

```

sudo dpkg -i mbrola3.0.1h_i386.deb

```


If you're paranoid about installing a deb from a third-party like the MBROLA project, you can grab the binary in a zip file from their [download page]("http://tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html") and install it manually. There doesn't appear to be any source package released to the public, so if you're extremely paranoid, you may just want to avoid using the MBROLA voices altogether. I've personally never had a problem using the binary either from the zip or the deb.

Next we'll unpack the voices and the wrappers:

```

unzip -x us1-980512.zip
unzip -x us2-980812.zip
unzip -x us3-990208.zip
tar xvf festvox_us1.tar.gz
tar xvf festvox_us2.tar.gz
tar xvf festvox_us3.tar.gz

```


**[size="3"][color="#a6926b"]Installing the voices and wrappers[/color][/size]**

First we'll make the directories where the voices will be installed:

```

sudo mkdir -p /usr/share/festival/voices/english/us1_mbrola/
sudo mkdir -p /usr/share/festival/voices/english/us2_mbrola/
sudo mkdir -p /usr/share/festival/voices/english/us3_mbrola/

```


Then we can install the voices and wrappers there:

```

sudo mv us1 /usr/share/festival/voices/english/us1_mbrola/
sudo mv us2 /usr/share/festival/voices/english/us2_mbrola/
sudo mv us3 /usr/share/festival/voices/english/us3_mbrola/
sudo mv festival/lib/voices/english/us1_mbrola/* /usr/share/festival/voices/english/us1_mbrola/
sudo mv festival/lib/voices/english/us2_mbrola/* /usr/share/festival/voices/english/us2_mbrola/
sudo mv festival/lib/voices/english/us3_mbrola/* /usr/share/festival/voices/english/us3_mbrola/

```


**[size="3"][color="#a6926b"]Tidy up[/color][/size]**

Lastly, we can remove the temporary directory:

```

cd ../
rm -rf mbrola_tmp/

```


If all went well, you now have a set of working MBROLA voices installed. See the section below on how to test that the voices are working properly.


**[size="4"][color="#da0000"]Installing the enhanced CMU Arctic voices[/color][/size]**

These voices were developed by the [Language Technologies Institute]("http://www.lti.cs.cmu.edu/") at Carnegie Mellon University. They sound much better than both the diphone and the MBROLA voices. See the [information page]("http://www.festvox.org/cmu_arctic/") and [voice demo page]("http://festvox.org/voicedemos.html") (the *_arctic_cg are the voices of interest). The drawback is that each voice takes over a hundred megs on disk, and with six English voices to choose from, that can take up a lot of bandwidth to download and depending on how much disk space you have to work with, six-hundred plus megs of space might be a bit much for voice data. However, the HTS voices discussed in the next section may in fact provide equal or better quality synthesis, and are only less than %2 of the size.

**[size="3"][color="#a6926b"]Downloading the voices[/color][/size]**

We will download everything we need for the English voices into a temporary directory (total download size is approximately six-hundred megs — you might want to go brew some coffee or something, lots of it...we might be here a while):

```

mkdir cmu_tmp
cd cmu_tmp/
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_awb_arctic-0.90-release.tar.bz2
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_bdl_arctic-0.95-release.tar.bz2
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_clb_arctic-0.95-release.tar.bz2
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_jmk_arctic-0.95-release.tar.bz2
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_rms_arctic-0.95-release.tar.bz2
wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_slt_arctic-0.95-release.tar.bz2

```

*Note: You can add the option "--limit-rate" to wget to set a maximum transfer speed (e.g., "wget -c --limit-rate=60K ..." to limit the download rate to 60KB/s).*

**[size="3"][color="#a6926b"]Unpacking the voices[/color][/size]**

Due to the size of the archives, this will probably take a few minutes as well (Maybe get a slice of cake this time? Also, note than tar is run non-verbosely so we don't have seven-million lines flooding the terminal):

```

for t in `ls cmu_*` ; do tar xf $t ; done
rm *.bz2

```


**[size="3"][color="#a6926b"]Installing the voices[/color][/size]**

Now we can install the voices:

```

sudo mkdir -p /usr/share/festival/voices/english/
sudo mv * /usr/share/festival/voices/english/

```


The voices are now installed, but Festival requires them to have slightly different directory names, so we'll rename the directories as needed.

```

for d in `ls /usr/share/festival/voices/english` ; do
if [[ "$d" =~ "cmu_us_" ]] ; then
sudo mv "/usr/share/festival/voices/english/${d}" "/usr/share/festival/voices/english/${d}_clunits" 
fi ; done

```

*Note: We could just use symlinks, but then the list of installed voices (see section below on testing voices) would show entries for the actual directories and the symlinks, though only the symlinks would work properly.*


**[size="3"][color="#a6926b"]Tidy up[/color][/size]**

Lastly, we can remove the temporary directory:

```

cd ../
rm -rf cmu_tmp/

```


If all went well, you now have a set of working CMU Arctic voices installed. See the section below on how to test that the voices are working properly.


**[size="4"][color="#da0000"]Installing the enhanced Nitech HTS voices[/color][/size]**

*Note: Unfortunately, these voices require at least Festival 1.95, but only 1.4 is available on Ubuntu prior to Hardy (8.04). This means that if you want to use these voices on any prior release (Gutsy, Feisty...), you need to compile Festival from source. This is relatively easy to do, and a section at the bottom of this HOWTO will guide you through the process. Don't waste your time trying to install these voices on Festival versions less that 1.95, they just won't work.*

These voices are produced by the [HTS working group]("http://hts.sp.nitech.ac.jp/?Who%20we%20are") hosted at the [Nagoya Institute of Technology]("http://www.nitech.ac.jp/"). They have produced excellent quality voices which take up very little disk space. In terms of quality and size, probably the best (non-commercial) English voices availible for Festival. See the [voice demo page]("http://festvox.org/voicedemos.html") (the *_arctic_hts are the voices of interest). Highly recommended. The voices are available on their [download page]("http://hts.sp.nitech.ac.jp/?Download").

**[size="3"][color="#a6926b"]Downloading the voices[/color][/size]**

We will download everything we need for the English voices into a temporary directory (total download size is approximately ten megs):

```

mkdir hts_tmp
cd hts_tmp/
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_awb_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_bdl_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_clb_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_rms_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_slt_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_jmk_arctic_hts-2.1.tar.bz2
wget -c http://hts.sp.nitech.ac.jp/archives/1.1.1/cmu_us_kal_com_hts.tar.gz
wget -c http://hts.sp.nitech.ac.jp/archives/1.1.1/cstr_us_ked_timit_hts.tar.gz

```


**[size="3"][color="#a6926b"]Unpacking the voices[/color][/size]**

Next we'll unpack the voices:

```

for t in `ls` ; do tar xvf $t ; done

```


**[size="3"][color="#a6926b"]Installing the voices[/color][/size]**

Now we can install the voices:

```

sudo mkdir -p /usr/share/festival/voices/us
sudo mv lib/voices/us/* /usr/share/festival/voices/us/
sudo mv lib/hts.scm /usr/share/festival/hts.scm

```


**[size="3"][color="#a6926b"]Tidy up[/color][/size]**

Lastly, we can remove the temporary directory:

```

cd ../
rm -rf hts_tmp/

```


If all went well, you now have a set of working Nitech HTS voices installed. See the section below on how to test that the voices are working properly.


**[size="4"][color="#da0000"]Testing voices and choosing a default voice[/color][/size]**

Now that you have some voices to play with, you may want to try out different voices to suite your taste, or just to make sure things are working properly. To get a list of all the voices that are installed, you can simply look at the directories under /usr/share/festival/voices:

```

for d in `ls /usr/share/festival/voices` ; do ls "/usr/share/festival/voices/${d}" ; done

```


Or you can run the fetival program, and, at the prompt, enter (voice.list). The result will look something like this:

```

festival> (voice.list)
(us1_mbrola
 us3_mbrola
 us2_mbrola
 nitech_us_slt_arctic_hts
 nitech_us_jmk_arctic_hts
 nitech_us_clb_arctic_hts
 nitech_us_rms_arctic_hts
 nitech_us_bdl_arctic_hts
 nitech_us_awb_arctic_hts)

```


**[size="3"][color="#a6926b"]Playing with the voices[/color][/size]**

To select a voice, add the prefix "voice_" to the voice name, and surround it by parentheses:

```

festival> (voice_us2_mbrola)

```


Then you can test it using (SayText "The text") to speak a single line of text, or (tts "somefile.txt" nil) to process an entire file. You can also hear a short introduction about Festival with (intro).

```

festival> (SayText "Hello from Ubuntu")
festival> (tts "story.txt" nil)
festival> (intro)

```


**[size="3"][color="#a6926b"]Selecting a default voice[/color][/size]**

You can edit the file /etc/festival.scm to select a default voice. Open the file in your favorite editor (you will need super-user privleges, so run it with sudo or gksu) and add the line:

```

(set! voice_default 'voice_nitech_us_rms_arctic_hts)

```


Simply replace "voice_nitech_us_rms_arctic_hts" with whatever your favorite voice is.

**[size="3"][color="#a6926b"]Making it work with PulseAudio, ESD or ALSA[/color][/size]**

By default, festival tries to synthesize speech to /dev/dsp using OSS. To make it work with ESD, PulseAudio or ALSA you have two options. The first is to use a wrapper to call festival, and the second is to make festival internally try to use one of them output. The advantage to the first method is that you can use the esd, pluseaudio or the alsa wrapper at any time, without having to edit the config file. The advantage of the second method is that you don't have to remember to call the wrapper—directly running festival works.

The available wrappers I know of are: the [font="mono"]aoss[/font] wrapper program from the alsa-oss package, the [font="mono"]padsp[/font] wrapper from pulseaudio-utils, and the [font="mono"]esddsp[/font] wrapper from esound-clients — but *_caveat emptor_* — there is a bug ([#214465]("https://bugs.launchpad.net/ubuntu/+source/esound/+bug/214465")) in the [font="mono"]esddsp[/font] script right now (see [post="4682046"]this post[/post] for a quick-fix).

To use the internal method, see the instructions for editing /etc/festival.scm at the [community docs on TextToSpeech]("https://help.ubuntu.com/community/TextToSpeech").

**[size="3"][color="#a6926b"]An example /etc/festival.scm[/color][/size]**

This is a drop-in /etc/festival.scm file. It covers all of the options mentioned about selecting a default voice and using ESD or ALSA for audio output. The ";;" are comment specifiers, so to use any of the options simply uncomment them by removing the ";;" in from of them and adding it to whatever you want to deactivate. It doesn't matter whether you have two different options uncommented at the same time (e.g., two different default_voice options), Festival will simply use whichever one is defined last in the file, however it may be a little bit slower to start up in such a case and it's better to just uncomment the one you want to use.

```

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; setup audio output
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; defaults to oss output

;;;; use pulseaudio to output sound
;;(Parameter.set 'Audio_Command "paplay $FILE") 
;;(Parameter.set 'Audio_Method 'Audio_Command)
;;(Parameter.set 'Audio_Required_Format 'snd)

;;;; use esd to output sound
;;(Parameter.set 'Audio_Command "esdplay $FILE") 
;;(Parameter.set 'Audio_Method 'Audio_Command)
;;(Parameter.set 'Audio_Required_Format 'snd)

;;;; use alsa to output sound
;;(Parameter.set 'Audio_Command "aplay -D plug:dmix -q -c 1 -t raw -f s16 -r $SR $FILE") 
;;(Parameter.set 'Audio_Method 'Audio_Command)
;;(Parameter.set 'Audio_Required_Format 'snd)


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; setup voices
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; Festvox voices
;;(set! default_voice 'voice_rab_diphone)
;;(set! default_voice 'voice_don_diphone)
;;(set! default_voice 'voice_kal_diphone)
;;(set! default_voice 'voice_ked_diphone)

;;;; MBROLA voices
;;(set! default_voice 'voice_us1_mbrola)
;;(set! default_voice 'voice_us2_mbrola)
;;(set! default_voice 'voice_us3_mbrola)

;;;; CMU Arctic voices
;;(set! voice_default 'voice_cmu_us_rms_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_bdl_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_slt_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_clb_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_awb_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_jmk_arctic_clunits)

;;;; Nitech HTS voices
(set! voice_default 'voice_nitech_us_rms_arctic_hts)
;;(set! voice_default 'voice_nitech_us_bdl_arctic_hts)
;;(set! voice_default 'voice_nitech_us_slt_arctic_hts)
;;(set! voice_default 'voice_nitech_us_clb_arctic_hts)
;;(set! voice_default 'voice_nitech_us_awb_arctic_hts)
;;(set! voice_default 'voice_nitech_us_jmk_arctic_hts)
;;(set! voice_default 'voice_cmu_us_kal_com_hts)
;;(set! voice_default 'voice_cstr_us_ked_timit_hts)


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; Advanced voice configuration
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; Slow the HTS speech down.
;;(set! hts_duration_stretch 0.1)

;;;; Slow the standard voices down
;;(Parameter.set 'Duration_Stretch 2.5)

;;;; Set volume.
;;(set! default_after_synth_hooks
;;    (list (lambda (utt) (utt.wave.rescale utt 2.0 t))))



```

*Note: Advanced voice config based on [this page]("http://gentoo-wiki.com/HOWTO_speechd#Installing_Extra_Voices")*


**[size="4"][color="#da0000"]Installing Festival 1.96 from source[/color][/size]**

*Note: If you have any errors that stop the build process, please report them here so I can update the HOWTO. Even if it's something trivial like a broken path, and you fix it yourself, others may not know how to fix it.*

The HTS voices above require at lest Festival 1.95. Here we will go through the steps necessary to build and install Festival 1.96. This method was tested on the Dapper 6.06.1 VMplayer appliance using VirtualBox, so it should work on all Ubuntu releases. We will build a backport using official Ubuntu sources, so you don't need to remove any existing festival installation — apt will upgrade it for you.

We firstly need some development tools, libraries and headers. Use the following command to install the build requirements:

```

sudo apt-get install autotools-dev debhelper gawk libesd0-dev libncurses5-dev quilt g++ texinfo dpkg-dev devscripts fakeroot

```


Say yes to whatever dependencies are required.

**[size="3"][color="#a6926b"]Downloading the source packages[/color][/size]**

We will download everything we need for building Festival 1.96 into a temporary directory (total download size is approximately five megs):

```

mkdir fest_tmp
cd fest_tmp/
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/speech-tools/speech-tools_1.2.96~beta-2.dsc
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/speech-tools/speech-tools_1.2.96~beta.orig.tar.gz
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/speech-tools/speech-tools_1.2.96~beta-2.diff.gz
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/f/festival/festival_1.96~beta-7ubuntu1.dsc
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/f/festival/festival_1.96~beta.orig.tar.gz
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/f/festival/festival_1.96~beta-7ubuntu1.diff.gz

```


**[size="3"][color="#a6926b"]Unpacking the sources[/color][/size]**

Next we'll unpack the sources and fix some versioning stuff so we can backport:

```

sed -i -e "s/(>= 5)/(>= 4.1.75)/" festival_1.96~beta-7ubuntu1.dsc
sed -i -e "s/(>= 5)/(>= 4)/" speech-tools_1.2.96~beta-2.dsc
dpkg-source -x festival_1.96~beta-7ubuntu1.dsc
dpkg-source -x speech-tools_1.2.96~beta-2.dsc
sed -i -e "s/(>= 5)/(>= 4)/" -e "s/\${binary:Version}/\${Source-Version}/g" speech-tools-1.2.96~beta/debian/control
sed -i -e "s/(>= 5)/(>= 4.1.75)/" -e "s/ (>= 3.105)//" -e "s/ (>= 3.0-10)//" -e "s/ (>= 2.86.ds1)//" -e "s/\${binary:Version}/\${Source-Version}/g" festival-1.96~beta/debian/control

```


**[size="3"][color="#a6926b"]Compiling and installing the sources[/color][/size]**

Now we can compile the sources. Firstly we need to compile the Speech Tools. I'm using debuild because it makes it easier.

```

cd speech-tools-1.2.96~beta/
debuild binary
cd ../

```


This should have created three deb files, which we need to install before we can build and install Festival:

```

sudo dpkg -i libestools1.2_1.2.96~beta-2_i386.deb libestools1.2-dev_1.2.96~beta-2_i386.deb speech-tools_1.2.96~beta-2_i386.deb

```


Now we can build Festival, but first we should add a patch for HTS voices (patch derived from Nitech hts.scm file included in their voices). This step is optional, but recommended, as it can improve the synthesis in some circumstances. Save the following file to *festival-1.96~beta/debian/patches/lib_hts.scm.diff*:

```

--- a/lib/hts.scm
+++ b/lib/hts.scm
@@ -108,7 +108,7 @@
   (format ofd "+%s" (if (string-equal "0" (item.feat s "n.name"))
 			"x" (item.feat s "n.name")))
 ;  nn.name
-  (format ofd "+%s" (if (string-equal "0" (item.feat s "n.n.name"))
+  (format ofd "=%s" (if (string-equal "0" (item.feat s "n.n.name"))
 			"x" (item.feat s "n.n.name")))
 
 ;  position in syllable (segment)
@@ -299,7 +299,7 @@
 	      (item.feat s "R:SylStructure.parent.parent.R:Word.content_words_out")))
 
 ;  distance from content word in phrase
-  (format ofd ";%s" 
+  (format ofd "#%s" 
 	  (if (string-equal "pau" (item.feat s "name"))
 	      "x"
 	      (item.feat s "R:SylStructure.parent.parent.R:Word.lisp_distance_to_p_content")))
@@ -377,7 +377,7 @@
 	      (item.feat s "R:SylStructure.parent.parent.R:Phrase.parent.n.lisp_num_syls_in_phrase")))
 
 ;  length of next phrase (word)
-  (format ofd "=:%s" 
+  (format ofd "=%s" 
 	  (if (string-equal "pau" (item.feat s "name"))
 	      (item.feat s "n.R:SylStructure.parent.parent.R:Phrase.parent.lisp_num_words_in_phrase")
 	      (item.feat s "R:SylStructure.parent.parent.R:Phrase.parent.n.lisp_num_words_in_phrase")))

```

*Note: This file needs to preserve formatting and tab characters! If you get an error about patching failing in the patch command below, try downloading the file [from here]("http://monkeesage.prohosts.org/lib_hts.scm.diff") (right-click save-as) and re-running the patch command. Alternately, you could grab the hts.scm file from a Nitech HTS voice (see section above) and replace the festival-1.96~beta/lib/hts.scm file with it, and skip the patch step.*

Now for the actual build:

```

cd festival-1.96~beta/
patch -p1 -i debian/patches/lib_hts.scm.diff
debuild binary
cd ../

```


And now the install:

```

sudo dpkg -i festival_1.96~beta-7ubuntu1_i386.deb festival-dev_1.96~beta-7ubuntu1_i386.deb
sudo apt-get install festlex-cmu festlex-poslex

```


**[size="3"][color="#a6926b"]Tidy up[/color][/size]**

Lastly, we can remove the temporary directory:

```

cd ../
rm -rf fest_tmp/

```


If all went well, you now have Fastival 1.96 installed.


That's it! Have fun!

---

### Post by datarez on 2008-04-14
Thanks for the post.  Definately made it easy installing the other voices.

Any reason to do your configuration in /etc/festival.scm vs ~/.festivalrc ?
I currently have alsa and my default configured in ~/.festivalrc and was wondering if I'm missing any options that could be set in the other location?

---

### Post by MonkeeSage on 2008-04-14
> **datarez said:**
> Thanks for the post.  Definately made it easy installing the other voices.

Any reason to do your configuration in /etc/festival.scm vs ~/.festivalrc ?
I currently have alsa and my default configured in ~/.festivalrc and was wondering if I'm missing any options that could be set in the other location?

No problem. :)

The possible advantage to having your configuration in /etc/festival.scm versus having it in ~/.festivalrc is that /etc/festival.scm applies to all users, so if you have more than one user account on your computer and festival is used by multiple people, you can prevent duplicating a user config for each user and just put everything in /etc/festival.scm. Or you could put the sound configuration stuff in /etc/festival.scm and let each user select a default voice through ~/.festivalrc.

In terms of being able to set more options and such, I don't think there is any practical difference between using the global or local config files -- they are both loaded in the exact same way at the end of /usr/share/festival/init.scm (lines 138 and 146 respectively).

---

### Post by yosemite610 on 2008-04-14
Rergarding the hts, after installing (a single) one of the voices I receive the following error starting festival:
> SIOD ERROR: module hts_engine required, but not compiled in this installation

---

### Post by Debuggern on 2008-04-14
Kick-*** how to tut. for adding better voices  to festival. Thank you so much MonkeeSage! :)

The only problem I got into was trying to use the Nitech HTS voices.

> SIOD ERROR: module hts_engine required, but not compiled in this installation

---

### Post by MonkeeSage on 2008-04-14
@yosemite610,
@Debuggern

Sounds like the festival version on your box is not recent enough to support the HTS voices. :(

What do you get when run this command:

```

festival --version

```

I'm pretty sure that they work with 1.95, but I haven't verified that. It's been a couple years since I've been running 1.96 (on different boxes). But I thought that 1.95 was recent enough.

---

### Post by MonkeeSage on 2008-04-15
PS. In case anyone is interested, I'm writing a very loose front-end to festival/speech-dispatcher that can load and speak text files. This is VERY, very beta, and it comes with no support or promise that it will work (at all! for any reason!). But, in case you are interested, here you go:

gspeak.py & gspeak.glade

---->%----
```

#!/usr/bin/python
# -*- ts=4:sw=4:noexpandtab -*-

import os
import sys

try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
	import gtk.glade
except:
	print 'This program requires pygtk\n' \
				'http://www.pygtk.org/'
	sys.exit(1)

class SpeechKit:

	def __init__(self):
		self.use_spd = True
		self.active_file = None
		self.pwd = os.path.dirname(sys.argv[0])

		self.glade  = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'main_window')
		self.window = self.glade.get_widget('main_window')
		self.view   = self.glade.get_widget('text')

		self.glade.signal_autoconnect({
			'on_main_quit'   : self.on_main_quit,
			'on_open'        : self.open_file,
			'on_speak'       : self.start_speech,
			'on_stop'        : self.stop_speech,
			'on_choose_fest' : self.on_choose_fest,
			'on_choose_spd'  : self.on_choose_spd,
			'on_about'       : self.show_about
		})

	def run(self):
		gtk.main()

	def open_file(self, widget=None):
		self.glade = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'filechooser_dialog')
		dlg   = self.glade.get_widget('filechooser_dialog')
		dlg.connect('file_activated', self.choose_file)
		dlg.connect('response', self.close_chooser)

	def close_chooser(self, widget, args=None):
		widget.destroy()

	def choose_file(self, widget, args=None):
		name = widget.get_filename()
		fh   = open(name)
		data = fh.read()
		fh.close()
		self.view.get_buffer().set_text(data)
		self.window.set_title(os.path.basename(name))

	def start_speech(self, widget=None):
		buffer = self.view.get_buffer()
		text = buffer.get_text(*buffer.get_bounds())
		if self.use_spd:
			pipe = os.popen('spd-say -e 1 > /dev/null', 'w')
			pipe.write(text)
			pipe.close()
		else:
			fh = open('/tmp/foobarbaz', 'w')
			fh.write(text)
			fh.close()
			os.system(r'echo "(tts \"/tmp/foobarbaz\" nil)" | aoss festival &')

	def stop_speech(self, widget=None):
		if self.use_spd:
			os.system('spd-say -S')
			os.system('spd-say -C')
		else:
			pipe = os.popen('pidof festival', 'r')
			pid = pipe.read().strip()
			while not pid == "":
				os.system('killall -9 festival')
				os.system('killall -9 /usr/lib/festival/audsp')
				pid = pipe.read().strip()
			pipe.close()

	def on_choose_fest(self, widget=None):
		self.use_spd = False

	def on_choose_spd(self, widget=None):
		self.use_spd = True

	def show_about(self, widget=None):
		self.glade = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'about_dialog')
		dlg = self.glade.get_widget('about_dialog')
		dlg.connect('response', self.about_quit)

	def about_quit(self, widget, args=None):
		widget.destroy()

	def on_main_quit(self, widget, args=None):
		self.stop_speech()
		gtk.main_quit()

if __name__ == '__main__':
	sk = SpeechKit()
	if len(sys.argv) > 1:
		if sys.argv[1] == '-s':
		  pass # use default spd-say synthesis
		elif sys.argv[1] == '-f':
			sk.use_spd = False
		for file in sys.argv[2:]:
			sk.active_file = file
			break
	sk.run()

```

---->%----

```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--*- mode: xml -*-->
<glade-interface>
  <widget class="GtkWindow" id="main_window">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Gspeak</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <property name="default_width">640</property>
    <property name="default_height">480</property>
    <property name="icon_name">stock_headphones</property>
    <signal name="delete_event" handler="on_main_quit"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkMenuBar" id="menubar">
            <property name="visible">True</property>
            <child>
              <widget class="GtkMenuItem" id="file_menu">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="file_menu_menu">
                    <child>
                      <widget class="GtkImageMenuItem" id="open">
                        <property name="visible">True</property>
                        <property name="label">gtk-open</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <signal name="activate" handler="on_open"/>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkSeparatorMenuItem" id="separator">
                        <property name="visible">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="quit">
                        <property name="visible">True</property>
                        <property name="label">gtk-quit</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <signal name="activate" handler="on_main_quit"/>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="_Tools">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Tools</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <child>
                      <widget class="GtkMenuItem" id="tool_fest">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Festival</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_choose_fest"/>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkMenuItem" id="tool_spd">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Speechd</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_choose_spd"/>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="help_menu">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="help_menu_menu">
                    <child>
                      <widget class="GtkImageMenuItem" id="about">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">_About</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_about"/>
                        <child internal-child="image">
                          <widget class="GtkImage" id="image4">
                            <property name="visible">True</property>
                            <property name="stock">gtk-about</property>
                            <property name="icon_size">1</property>
                          </widget>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="padding">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkScrolledWindow" id="scrolled">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="vscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="shadow_type">GTK_SHADOW_IN</property>
            <child>
              <widget class="GtkTextView" id="text">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="wrap_mode">GTK_WRAP_WORD</property>
                <property name="left_margin">4</property>
                <property name="right_margin">4</property>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="padding">2</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkButton" id="stop_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_stop"/>
                <child>
                  <widget class="GtkAlignment" id="alignment1">
                    <property name="visible">True</property>
                    <property name="xscale">0</property>
                    <property name="yscale">0</property>
                    <child>
                      <widget class="GtkHBox" id="hbox2">
                        <property name="visible">True</property>
                        <property name="spacing">2</property>
                        <child>
                          <widget class="GtkImage" id="image1">
                            <property name="visible">True</property>
                            <property name="stock">gtk-no</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkLabel" id="label1">
                            <property name="visible">True</property>
                            <property name="label" translatable="yes">Stop</property>
                            <property name="use_underline">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="padding">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="speak_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_speak"/>
                <child>
                  <widget class="GtkAlignment" id="alignment2">
                    <property name="visible">True</property>
                    <property name="xscale">0</property>
                    <property name="yscale">0</property>
                    <child>
                      <widget class="GtkHBox" id="hbox3">
                        <property name="visible">True</property>
                        <property name="spacing">2</property>
                        <child>
                          <widget class="GtkImage" id="image2">
                            <property name="visible">True</property>
                            <property name="stock">gtk-apply</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkLabel" id="label2">
                            <property name="visible">True</property>
                            <property name="label" translatable="yes">Speak</property>
                            <property name="use_underline">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="padding">2</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="padding">2</property>
            <property name="position">2</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkAboutDialog" id="about_dialog">
    <property name="visible">True</property>
    <property name="destroy_with_parent">True</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
    <property name="copyright" translatable="yes">MonkeeSage, 2007</property>
    <property name="comments" translatable="yes">Simple GTK+ frontend to spd-say (part of Speech-Dispatcher).</property>
    <property name="license" translatable="yes">GSpeak 1.0
Copyright (C) 2007 MonkeeSage

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.</property>
    <property name="authors">Jordan Callicoat &lt;MonkeeSage@gmail.com&gt;</property>
    <property name="translator_credits" translatable="yes" comments="TRANSLATORS: Replace this string with your names, one name per line.">translator-credits</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox1">
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area1">
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">GTK_PACK_END</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkFileChooserDialog" id="filechooser_dialog">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Open File....</property>
    <property name="modal">True</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <property name="destroy_with_parent">True</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_DIALOG</property>
    <property name="show_hidden">True</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox1">
        <property name="visible">True</property>
        <property name="spacing">24</property>
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area1">
            <property name="visible">True</property>
            <property name="layout_style">GTK_BUTTONBOX_END</property>
            <child>
              <widget class="GtkButton" id="button1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="label">gtk-cancel</property>
                <property name="use_stock">True</property>
                <property name="response_id">-6</property>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="button2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="label">gtk-open</property>
                <property name="use_stock">True</property>
                <property name="response_id">-5</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">GTK_PACK_END</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by Cyberponcho on 2008-04-15
Thanks for this excellent post, it made my life a hell of a lot easier :-)
Still got some questions, i would like to install a female voice package, i have so far only found male voices... don't they think that there are men who give their workstations female names and would like to give it a female voice?;-) 
Second question is: is there a german voice package as well? i've seen finnish, french, english but no german, i will really appreciate it if you lead me in the right direction.
Thanks a lot again.

---

### Post by Debuggern on 2008-04-15
Yup, MonkeeSage. I had an older version "1.4.2" which I installed from apt-get , from Kubuntu feisty. I have the latest tar.gz packages from festiva'ls website, [http://festvox.org/](http://festvox.org/). I need to compile them. Do you know any good how to compile it, I know the INSTALL documents decribes everything, I have problems compiling the "speech tools".

> gcc -O3 -Wall -o ch_lab ch_lab_main.o -L../lib -lestools -L../lib -lestbase -L../lib -leststring -lcurses -ldl -lncurses -lm -lstdc++ -lgcc
/usr/bin/ld: cannot find -lcurses
collect2: ld returned 1 exit status
make[1]: *** [ch_lab] Error 1

Thanks again for the how to! :)

Cheers!

---

### Post by MonkeeSage on 2008-04-15
> **Cyberponcho said:**
> Thanks for this excellent post, it made my life a hell of a lot easier :-)
Still got some questions, i would like to install a female voice package, i have so far only found male voices... don't they think that there are men who give their workstations female names and would like to give it a female voice?;-) 
Second question is: is there a german voice package as well? i've seen finnish, french, english but no german, i will really appreciate it if you lead me in the right direction.
Thanks a lot again.

Well, it depends on which voices you're using, there are female voices in the CMU and HTS voices (see their information page links in the HOWTO for which voices, I believe that the *_stl_* voice is female and there is another one or maybe two IIRC).

As for German, I believe the MBROLA page has a German voice, see the link from the HOWTO. Installing it should be just like installing the English MBROLA voices. Let me know if you need more help.


> **Debuggern said:**
> Yup, MonkeeSage. I had an older version "1.4.2" which I installed from apt-get , from Kubuntu feisty. I have the latest tar.gz packages from festiva'ls website, [http://festvox.org/](http://festvox.org/). I need to compile them. Do you know any good how to compile it, I know the INSTALL documents decribes everything, I have problems compiling the "speech tools".

[. . .]

Thanks again for the how to! :)

Cheers!

I totally forgot to check what versions shipped with stable Ubuntu! :oops:

There's no backports for festival 1.96. I'll add a section to the HOWTO for compiling from source.

---

### Post by MonkeeSage on 2008-04-16
Alright, the HOWTO is updated. Took me a bit because I had to set up a VM with Dapper on it. The build process should work for all flavors of Ubuntu (tested only on Dapper and Hardy though).

---

### Post by Debuggern on 2008-04-16
Ok, great work, MonkeeSage. I removed all earlier festival packages and installed it from source, this is the problem that came up after I tried to add the nitech voices.

> SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/english/us1_mbrola/festvox/us1_mbrola.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


Cheers, I could run the festival without any prb before I started to add the voices.

You rock! Keep up the work! :)

---

### Post by Debuggern on 2008-04-16
Ok, I solved it, I just downloaded the festlex-cmu package and installed it. Now everything works! :)

This will come handy when I ned to study pdf documents.

Cheers!

---

### Post by MonkeeSage on 2008-04-16
> **Debuggern said:**
> Ok, I solved it, I just downloaded the festlex-cmu package and installed it. Now everything works! :)

This will come handy when I ned to study pdf documents.

Cheers!

Glad you got it sorted! :)

Ps.  festlex-cmu and festlex-poslex are listed in the requirements in the introduction section, but when you removed festival apt probably removed them as well since they depend on it. You can just install them from apt, you don't need to install them from source. 

Pss. Since the HOWTO builds a backport of festival from official Ununtu sources, you don't actually have to remove any previous installations -- apt will upgrade them automatically. I've make a note of that in the HOWTO, and added a line to ensure the festlex-* packages are installed.

Regards,
Jordan

---

### Post by AcuraCoupe on 2008-04-19
Please tell me, how did you remove the earlier festival packages? I just started to use Ubuntu about a month ago. I don't know which command to remove the earlier package. 

After I install the standard Festvox diphone voices and the enhanced MBROLA voices. I get this error when I try to test the voice.

I typed command 'festival' in the Terminal, and it showed this error:

SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/english/ked_diphone/festvox/ked_diphone.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


Please help me! Thanks.


> **Debuggern said:**
> Ok, great work, MonkeeSage. I removed all earlier festival packages and installed it from source, this is the problem that came up after I tried to add the nitech voices.



Cheers, I could run the festival without any prb before I started to add the voices.

You rock! Keep up the work! :)

---

### Post by MonkeeSage on 2008-04-20
> **AcuraCoupe said:**
> Please tell me, how did you remove the earlier festival packages? I just started to use Ubuntu about a month ago. I don't know which command to remove the earlier package. 

After I install the standard Festvox diphone voices and the enhanced MBROLA voices. I get this error when I try to test the voice.

I typed command 'festival' in the Terminal, and it showed this error:

SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/english/ked_diphone/festvox/ked_diphone.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.

Please help me! Thanks.


Hi there. From a terminal window. type this command:

```

sudo apt-get install festlex-poslex festlex-cmu

```


Say yes if it requires some other pckages as well.

Now festival should work for you. :)

---

### Post by AcuraCoupe on 2008-04-20
I typed this command in the Terminal and it displayed:
   festlex-poslex is already the newest version.
   festlex-cmu is already the newest version.

I still have the same error when I typed this command 'festival' in Terminal.
   SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
   closing a file left open: /usr/share/festival/voices/english/ked_diphone/festvox/ked_diphone.scm
   closing a file left open: /usr/share/festival/init.scm
   festival: fatal error exiting.

/usr/share/festival/dicts/  has only 1 folder named 'oald'. I don't see 'cmu' or other folder or file. There are 6 files inside 'oald' folder: all.scm, cuvoald710-0.2.scm, oald-0.4.out, oald_extensions.scm, oaldlex.scm, oald_lts_rules.scm

I have 2 voices folder in /usr/share/festival/voices  : english and us. The 'english' folder have the Festvox diphone voices and MBROLA voices , and the 'us' folder has HTS voices. 

'festival --version' command tell me that I currently have 
   festival: Festival Speech Synthesis System: 1.4.3:release Jan 2003

How can I completely remove the festival 1.4.3 version? So I can install Festival 1.96 from source.

Thank You.

---

### Post by MonkeeSage on 2008-04-20
> **AcuraCoupe said:**
> I typed this command in the Terminal and it displayed:
   festlex-poslex is already the newest version.
   festlex-cmu is already the newest version.

I still have the same error when I typed this command 'festival' in Terminal.

I have 2 voices folder in /usr/share/festival/voices  : english and us. I installed the Festvox diphone voices and MBROLA voices inside the 'english' folder, and HTS voices to 'us' folder. 

'festival --version' command tell me that I currently have 
   festival: Festival Speech Synthesis System: 1.4.3:release Jan 2003

How can I completely remove the festival 1.4.3 version? So I can install Festival 1.96 from source.

Thank You.


Hmm. That's odd. Ok, well, to remove everything, use this command:

```

sudo apt-get pruge festival festival-doc festival-dev festlex-poslex festlex-cmu festvox-don festvox-rablpc16k festvox-rablpc8k festvox-kallpc16k festvox-kallpc8k festvox-kdlpc16k festvox-kdlpc8k libestools1.2 libestools1.2-dev

```


This should remove *eveything* related to festival from your system. After that, try following the HOWTO at every step. If you still have a problem please let me know and I'll try to help you further. Good luck!

---

### Post by AcuraCoupe on 2008-04-20
```
sudo apt-get pruge festival festival-doc festival-dev festlex-poslex festlex-cmu festvox-don festvox-rablpc16k festvox-rablpc8k festvox-kallpc16k festvox-kallpc8k festvox-kdlpc16k festvox-kdlpc8k libestools1.2 libestools1.2-dev
```

It gave me this error:```

E: Invalid operation pruge

```

Help Please! Thanks.

---

### Post by MonkeeSage on 2008-04-21
Hmmmm....that's weird. OK. Try this instead:

```

sudo apt-get remove festival festival-doc festival-dev festlex-poslex festlex-cmu festvox-don festvox-rablpc16k festvox-rablpc8k festvox-kallpc16k festvox-kallpc8k festvox-kdlpc16k festvox-kdlpc8k libestools1.2 libestools1.2-dev

```

Can you tell me the output of this command:

```

lsb_release -drc

```

---

### Post by AcuraCoupe on 2008-04-21
I entered the first command, and it displayed:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package festival-doc is not installed, so not removed
Package festival-dev is not installed, so not removed
Package festvox-rablpc8k is not installed, so not removed
Package festvox-kallpc8k is not installed, so not removed
Package festvox-kdlpc8k is not installed, so not removed
Package libestools1.2-dev is not installed, so not removed
The following packages will be REMOVED:
  festival festlex-cmu festlex-oald festlex-poslex festvox-don
  festvox-kallpc16k festvox-kdlpc16k festvox-rablpc16k libestools1.2
0 upgraded, 0 newly installed, 9 to remove and 5 not upgraded.
Need to get 0B of archives.
After unpacking 48.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 94574 files and directories currently installed.)
Removing festvox-rablpc16k ...
Removing festvox-don ...
Removing festlex-oald ...
Removing festvox-kdlpc16k ...
dpkg - warning: while removing festvox-kdlpc16k, directory `/usr/share/festival/voices/english' not empty so not removed.
Removing festvox-kallpc16k ...
dpkg - warning: while removing festvox-kallpc16k, directory `/usr/share/festival/voices' not empty so not removed.
Removing festlex-poslex ...
Removing festlex-cmu ...
Removing festival ...
Removing libestools1.2 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

Now, the Festival package is completely removed from my Ubuntu right? 

After I entered:```
 lsb_release -drc
```

It showed this
```
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
```



> **MonkeeSage said:**
> Hmmmm....that's weird. OK. Try this instead:

```

sudo apt-get remove festival festival-doc festival-dev festlex-poslex festlex-cmu festvox-don festvox-rablpc16k festvox-rablpc8k festvox-kallpc16k festvox-kallpc8k festvox-kdlpc16k festvox-kdlpc8k libestools1.2 libestools1.2-dev

```

Can you tell me the output of this command:

```

lsb_release -drc

```

---

### Post by AcuraCoupe on 2008-04-21
I checked my File System after I used the 'remove' command above. 

There is a 'festival' folder in my /usr/share/ 
The 'festival' folder (/usr/share/festival) contains a 'voices' folder and 'hts.scm' file. 
The 'voices' folder has 2 other folder: 'english' which contains the MBROLA voices and 'us' which contains the HTS voices.

---

### Post by MonkeeSage on 2008-04-21
> **AcuraCoupe said:**
> I checked my File System after I used the 'remove' command above. 

There is a 'festival' folder in my /usr/share/ 
The 'festival' folder (/usr/share/festival) contains a 'voices' folder and 'hts.scm' file. 
The 'voices' folder has 2 other folder: 'english' which contains the MBROLA voices and 'us' which contains the HTS voices.

Yes, those were manually installed. You can remove them with:

```

sudo rm -rf /usr/share/festival

```

Does the HOWTO work correctly for you now?

---

### Post by AcuraCoupe on 2008-04-21
Should I remove these folder before I start the HOWTO again?


> **AcuraCoupe said:**
> I checked my File System after I used the 'remove' command above. 

There is a 'festival' folder in my /usr/share/ 
The 'festival' folder (/usr/share/festival) contains a 'voices' folder and 'hts.scm' file. 
The 'voices' folder has 2 other folder: 'english' which contains the MBROLA voices and 'us' which contains the HTS voices.

---

### Post by MonkeeSage on 2008-04-21
It shouldn't matter -- but it doesn't hurt to remove them just in case.

---

### Post by AcuraCoupe on 2008-04-21
I removed the festival folder, and started with the HOWTO. However
when I entered this command
```
sudo apt-get intall festvox-don festvox-rablpc16k festvox-kallpc16k festvox-kdlpc16k
```

It gave me this error
```
E: Invalid operation intall
```

When I tried the HOWTO yesterday, it worked when I entered that command. I don't know what wrong now.

---

### Post by AcuraCoupe on 2008-04-21
Nevermind, I found the error now. Because I copy your command and paste to Terminal. And the command line has a mispell of the word 'install'.

Thanks MonkeeSage

> **AcuraCoupe said:**
> I removed the festival folder, and started with the HOWTO. However
when I entered this command
```
sudo apt-get intall festvox-don festvox-rablpc16k festvox-kallpc16k festvox-kdlpc16k
```

It gave me this error
```
E: Invalid operation intall
```

When I tried the HOWTO yesterday, it worked when I entered that command. I don't know what wrong now.

---

### Post by MonkeeSage on 2008-04-21
> **AcuraCoupe said:**
> I removed the festival folder, and started with the HOWTO. However
when I entered this command
```
sudo apt-get intall festvox-don festvox-rablpc16k festvox-kallpc16k festvox-kdlpc16k
```

It gave me this error
```
E: Invalid operation intall
```

When I tried the HOWTO yesterday, it worked when I entered that command. I don't know what wrong now.
Doh! Typo! That should of course be:

```

sudo apt-get install festvox-don festvox-rablpc16k festvox-kallpc16k festvox-kdlpc16k

```

---

### Post by MonkeeSage on 2008-04-21
> **AcuraCoupe said:**
> Nevermind, I found the error now. Because I copy your command and paste to Terminal. And the command line has a mispell of the word 'install'.

Thanks MonkeeSage
 
No problem. Sorry about the misspelling. I've fixed now.

---

### Post by AcuraCoupe on 2008-04-21
I installed the standard Festvox diphone voices.

When I tested the voices, I can only hear the noise. Do I need to install any additional sound software?

This is my testing result:
```
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> (voice.list)
(rab_diphone ked_diphone don_diphone kal_diphone)
festival> (voice_kal_diphone)
kal_diphone
festival> (SayText "Hello from Ubuntu")
#<Utterance 0xb7195b38>
festival> (SayText "Hello from Ubuntu")
#<Utterance 0xb73e45b8>
festival> (SayText "Hello")            
#<Utterance 0xb740f8c8>
```

---

### Post by MonkeeSage on 2008-04-21
> **AcuraCoupe said:**
> I installed the standard Festvox diphone voices.

When I tested the voices, I can only hear the noise. Do I need to install any additional sound software?

This is my testing result:
```
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> (voice.list)
(rab_diphone ked_diphone don_diphone kal_diphone)
festival> (voice_kal_diphone)
kal_diphone
festival> (SayText "Hello from Ubuntu")
#<Utterance 0xb7195b38>
festival> (SayText "Hello from Ubuntu")
#<Utterance 0xb73e45b8>
festival> (SayText "Hello")            
#<Utterance 0xb740f8c8>
```

I'm not quite sure what to make of this, since it appears to work (the utterance appears to be synthesized properly). Maybe try this:

```

sudo apt-get install alsa-oss

```

...then try:

```

echo '(SayText "Hello from Ubuntu")' | aoss festival

```

---

### Post by AcuraCoupe on 2008-04-21
I installed the alsa-oss.

I the command ```
echo '(SayText "Hello from Ubuntu")' | aoss festival
```

but I couldn't hear anything
```
Segmentation fault (core dumped)
```

I use the Virtual Machine VMware to install and run the festival. Is it cause any problems?

Please help! Thanks.

---

### Post by MonkeeSage on 2008-04-23
> **AcuraCoupe said:**
> I installed the alsa-oss.

I the command ```
echo '(SayText "Hello from Ubuntu")' | aoss festival
```

but I couldn't hear anything
```
Segmentation fault (core dumped)
```

What voice were you using? I get segfaults with the Festvox voices. What about the us1 MBROLA voice?

```

echo '(voice_us1_mbrola) (SayText "Hello from Ubuntu")' | aoss festival

```

Next few days I'll try installing the Festvox voices from sources, and if they work that way, I'll add a section for building them from source in the HOWTO.


> **AcuraCoupe said:**
> I use the Virtual Machine VMware to install and run the festival. Is it cause any problems?

No. Well, it shouldn't at least. I tested it with Dapper (6.10) on a VMware Virtual Machine, and I had no problem ( -- other than the Festvox voices don't work that is; but they also don't work on my real desktop which is Hardy (8.04) -- so that's probably nothing to do with VMware).


HTH

---

### Post by MonkeeSage on 2008-04-23
Actually, I just checked, and with festival-1.96~beta-7ubuntu1 (current version in Hardy, and version built from source in HOWTO), the don_diphone voice *does* work for me. However, kal / ked / rab_diphone voices still segfault festival. I'll look into building them from source in a day or two. I the mean time, you can try using the MBROLA or Nitech voices (which sound better anyhow, imo).

---

### Post by AcuraCoupe on 2008-04-24
It works now. The MBROLA voices work with the alsa-oss wrapper.
Thank You for your patient. I appreciate your help.


> **MonkeeSage said:**
> What voice were you using? I get segfaults with the Festvox voices. What about the us1 MBROLA voice?

```

echo '(voice_us1_mbrola) (SayText "Hello from Ubuntu")' | aoss festival

```

Next few days I'll try installing the Festvox voices from sources, and if they work that way, I'll add a section for building them from source in the HOWTO.




No. Well, it shouldn't at least. I tested it with Dapper (6.10) on a VMware Virtual Machine, and I had no problem ( -- other than the Festvox voices don't work that is; but they also don't work on my real desktop which is Hardy (8.04) -- so that's probably nothing to do with VMware).


HTH

---

### Post by monraaf on 2008-04-24
Thanks for the howto.

**Edit: Never mind the quality is probably the same as the CMU ones**

They have also multi-syn voices, the quality is similar or maybe just a little better then the CMU ones They are only in the Scottish and Canadian male voices though.

[http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_cstr_us_awb_arctic_multisyn-1.0.tar.gz]("http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_cstr_us_awb_arctic_multisyn-1.0.tar.gz")
[http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_cstr_us_jmk_arctic_multisyn-1.0.tar.gz]("http://www.cstr.ed.ac.uk/downloads/festival/1.95/festvox_cstr_us_jmk_arctic_multisyn-1.0.tar.gz")

You have to create a directory: **/usr/share/festival/voices-multisyn/english**
and move the **cstr_us_awb_arctic_multisyn** and **cstr_us_jmk_arctic_multisyn** directories from the tarballs over there.

Also the festival that comes with Hardy was missing some multysn *.scm files. I downloaded this tarball:

[http://www.cstr.ed.ac.uk/downloads/festival/1.95/festival-1.95-beta.tar.gz]("http://www.cstr.ed.ac.uk/downloads/festival/1.95/festival-1.95-beta.tar.gz")

and extracted the *.scm files from the multisyn directory to: **/usr/share/festival**

---

### Post by MonkeeSage on 2008-04-24
> **AcuraCoupe said:**
> It works now. The MBROLA voices work with the alsa-oss wrapper.
Thank You for your patient. I appreciate your help.

Great! Glad you got it working! :) You should try the Nitech HTS voices, I personally think they sound the best and they are fairly small to download (see the section in the HOWTO).


> **monraaf said:**
> . . .
They have also multi-syn voices, the quality is similar or maybe just a little better then the CMU ones They are only in the Scottish and Canadian male voices though.
. . .

Ah, I totally forgot about those! Thanks for the reminder. Even if they are of similar quality with the CMU voices, it doesn't hurt to have more options. And given Murphy's Law, somebody, somewhere will want to know how to install them if it's not in the HOWTO. ;) I'll add a section incorporating your instructions later tonight or tomorrow.

---

### Post by MonkeeSage on 2008-05-01
Been busy. I'll update the HOWTO this weekend.

---

### Post by jahala on 2008-05-03
I thought I would post this here because I haven't found this anywhere else.  In order to get festival to work with pulseaudio in Ubuntu 8.04, add the following three lines to your .festivalrc

(Parameter.set 'Audio_Command "paplay $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)
(Parameter.set 'Audio_Required_Format 'snd)

This is similar for making it work with alsa, except you use "paplay" instead of "aplay" in the first line.

---

### Post by MonkeeSage on 2008-05-05
> **jahala said:**
> I thought I would post this here because I haven't found this anywhere else.  In order to get festival to work with pulseaudio in Ubuntu 8.04, add the following three lines to your .festivalrc

(Parameter.set 'Audio_Command "paplay $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)
(Parameter.set 'Audio_Required_Format 'snd)

This is similar for making it work with alsa, except you use "paplay" instead of "aplay" in the first line.

Nice. :)

I understand that you can also use Pulse Audio's wrapper, [font="mono"]padsp[/font], in place of [font="mono"]esddsp[/font] or [font="mono"]aoss[/font].

---

### Post by bixejo on 2008-05-15
Hi, MonkeeSage.

Thank you for your interesting post. It's indeed quite helpful for those (like me) who want to hear their computers speaking.

A simple (and probably stupid) question: do you know anything about some plugin or something like that for Firefox and/or other web browsers? I mean, something that allows you to select some text, right button click and then select the option "Say".

I apologize if this a recurrent question. I've been looking through this (and other) thread and found nothing related.

Regards, and thank you again.

---

### Post by MonkeeSage on 2008-05-16
> **bixejo said:**
> Hi, MonkeeSage.

Thank you for your interesting post. It's indeed quite helpful for those (like me) who want to hear their computers speaking.

A simple (and probably stupid) question: do you know anything about some plugin or something like that for Firefox and/or other web browsers? I mean, something that allows you to select some text, right button click and then select the option "Say".

I apologize if this a recurrent question. I've been looking through this (and other) thread and found nothing related.

Regards, and thank you again.

Hi there,

I also thought of this as a nice feature. But I haven't had the time to code a firefox extension for it. It would be relatively easy to write -- just to get the selected text and pass it to festival via a pipe. But time is money, and I'm poor. ;)

As a partial solution, you might be interested in the gspeak.py code I posted in the first (or maybe second?) page of this thread. Just choose festival from the tools menu, and paste the text into the text box, then press the Speak button. Yeah, it's ghetto, but it works for now. More, better stuffs later (hopefully). :)

---

### Post by cophew on 2008-06-27
Sorry if i sound thick, but is there any way to get the voices on this page 
[http://www.cstr.ed.ac.uk/projects/festival/morevoices.html](http://www.cstr.ed.ac.uk/projects/festival/morevoices.html) 
(Such as Nina, etc) into festival? The voices above are poor at best IMO and often hard to understand (Is it the way im installing it?).

EDIT : Sorry for bumping topic

---

### Post by MonkeeSage on 2008-07-03
> **cophew said:**
> Sorry if i sound thick, but is there any way to get the voices on this page 
[http://www.cstr.ed.ac.uk/projects/festival/morevoices.html](http://www.cstr.ed.ac.uk/projects/festival/morevoices.html) 
(Such as Nina, etc) into festival? The voices above are poor at best IMO and often hard to understand (Is it the way im installing it?).

EDIT : Sorry for bumping topic

No worries, it should be bumped when appropriate. :) I'll be glad to try to figure out how to install those voices, but I'm not sure where to find them (google only seems to find the demo page--where are the actual sources for the voices? Are they commercial, perhaps?).

Ps. Have you tried the Nitech HTS voices from the first post? They sound really good, imo, and they aren't very large to install.

---

### Post by simongales on 2008-07-05
Excellent HOWTO!  Everything working perfectly... but one question.

I built speech-tools 1.2.96 and festival 1.96 from source under Ubuntu gutsy (7.10).  It all lives in a subdirectory under my home directory.

But "make install" seems next to useless.  

How do I get this deployed to /usr/local/share/festival, /usr/local/bin, etc?

TIA,
-Simon

---

### Post by MonkeeSage on 2008-07-06
> **simongales said:**
> Excellent HOWTO!  Everything working perfectly... but one question.

I built speech-tools 1.2.96 and festival 1.96 from source under Ubuntu gutsy (7.10).  It all lives in a subdirectory under my home directory.

But "make install" seems next to useless.  

How do I get this deployed to /usr/local/share/festival, /usr/local/bin, etc?

TIA,
-Simon

NP. :) You have to have super-user permissions to install software into /usr/*.

```
sudo make install
```


However, the preferred method would be to build a gutsy .deb package from the official source packages and install that (see section in howto), so that it can be upgraded / uninstalled automatically by the package manager.

Another alternative is to use checkinstall (get it with sudo apt-get checkinstall, then replace "make install" with "checkinstall" and choose the defaults for everything it asks you), which will build a .deb from your current source tree.

---

### Post by Huss on 2008-07-07
The tute worked for me on Hardy. 

A few notes from a noob:

- My festival.scm was in /usr/share/festival not /ect
- To get the PDF speaking function working I needed to install kttsd from synaptic rather than 'add/remove apps'
- Remember to install festlex-oald, festlex-cmu and festlex-poslex

Thanks for the great tute

---

### Post by simongales on 2008-07-09
> However, the preferred method would be to build a gutsy .deb package from the official source packages and install that (see section in howto), so that it can be upgraded / uninstalled automatically by the package manager.


This worked out well, and I have all my voices working again.

> Another alternative is to use checkinstall (get it with sudo apt-get checkinstall, then replace "make install" with "checkinstall" and choose the defaults for everything it asks you), which will build a .deb from your current source tree.

This didn't seem to work - the deb package only included the docs, no binaries.  

```
root@Mythic:/home/sgales/festival/festival# checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>>  Festival Speech Synthesis System: 1.96:beta July 2004
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@Mythic ]
1 -  Summary: [ Festival Speech Synthesis System: 1.96:beta July 2004 ]
2 -  Name:    [ festival ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ festival ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version:
>> 1.96

This package will be built according to these values:

0 -  Maintainer: [ root@Mythic ]
1 -  Summary: [ Festival Speech Synthesis System: 1.96:beta July 2004 ]
2 -  Name:    [ festival ]
3 -  Version: [ 1.96 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ festival ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making in bin

Remove Links: festival festival_client festival_server festival_server_control text2w                                                                                        ave

Main Links: festival festival_client

Scripts: (sh) (prl) festival_server festival_server_control

======================== Installation successful ==========================

Copying documentation directory...
./
./INSTALL
./COPYING
./doc/
./doc/festival.jpg
./doc/indexHeader.inc
./doc/cstr.gif
./doc/classHeader.inc
./doc/banner.inc
./doc/festival_tiny.jpg
./doc/edcrest.gif
./doc/Makefile
./doc/refcard.tex
./doc/festival_small.jpg
./doc/festival.head
./doc/festival_client.head
./doc/festival_client.1
./doc/est_small.jpg
./doc/est.jpg
./doc/festival.texi
./doc/festival.tail
./doc/festival_client.tail
./doc/festival.1
./doc/hierHeader.inc
./README
./NEWS
cp: cannot stat `//var/tmp/TqALQOBjJDoijMWFImCCj/newfiles.tmp': No such file or direc                                                                                        tory
grep: /var/tmp/TqALQOBjJDoijMWFImCCj/newfile: No such file or directory

Some of the files created by the installation are inside the build
directory: /home/sgales/festival/festival

You probably don't want them to be included in the package,
especially if they are inside your home directory.
Do you want me to list them?  [n]: y
Should I exclude them from the package? (Saying yes is a good idea)  [y]:

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/sgales/festival/festival/festival_1.96-1_amd64.deb

 You can remove it from your system anytime using:

      dpkg -r festival

**********************************************************************


root@Mythic:/home/sgales/festival/festival# dpkg --contents  festival_1.96-1_amd64.deb                                                                               
drwxr-xr-x root/root         0 2008-07-09 09:59 ./
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/share/
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/share/doc/
drwxr-xr-x root/root         0 2008-07-09 09:56 ./usr/share/doc/festival/
-rw-r--r-- root/root     21893 2004-07-01 15:06 ./usr/share/doc/festival/INSTALL
-rw-r--r-- root/root      5038 2004-05-25 08:09 ./usr/share/doc/festival/COPYING
drwxrwxr-x root/root         0 2008-07-04 13:01 ./usr/share/doc/festival/doc/
-rw-r--r-- root/root      9001 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .jpg
-rw-r--r-- root/root       550 2001-04-04 06:55 ./usr/share/doc/festival/doc/indexHea                                                                                        der.inc
-rw-r--r-- root/root       724 2001-04-04 06:55 ./usr/share/doc/festival/doc/cstr.gif
-rw-r--r-- root/root       408 2001-04-04 06:55 ./usr/share/doc/festival/doc/classHea                                                                                        der.inc
-rw-r--r-- root/root       435 2003-02-21 13:10 ./usr/share/doc/festival/doc/banner.i                                                                                        nc
-rw-r--r-- root/root      2223 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _tiny.jpg
-rw-r--r-- root/root      3659 2001-04-04 06:55 ./usr/share/doc/festival/doc/edcrest.                                                                                        gif
-rw-r--r-- root/root      4884 2001-04-04 06:55 ./usr/share/doc/festival/doc/Makefile
-rw-r--r-- root/root     13080 2001-04-04 06:55 ./usr/share/doc/festival/doc/refcard.                                                                                        tex
-rw-r--r-- root/root      3504 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _small.jpg
-rw-r--r-- root/root       722 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .head
-rw-r--r-- root/root       519 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _client.head
-rw-r--r-- root/root      1897 2008-07-04 13:01 ./usr/share/doc/festival/doc/festival                                                                                        _client.1
-rw-r--r-- root/root      1999 2001-04-04 06:55 ./usr/share/doc/festival/doc/est_smal                                                                                        l.jpg
-rw-r--r-- root/root      4398 2001-04-04 06:55 ./usr/share/doc/festival/doc/est.jpg
-rw-r--r-- root/root    357856 2004-05-25 08:10 ./usr/share/doc/festival/doc/festival                                                                                        .texi
-rw-r--r-- root/root       595 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .tail
-rw-r--r-- root/root       364 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _client.tail
-rw-r--r-- root/root      2461 2008-07-04 13:01 ./usr/share/doc/festival/doc/festival                                                                                        .1
-rw-r--r-- root/root       544 2001-04-04 06:55 ./usr/share/doc/festival/doc/hierHead                                                                                        er.inc
-rw-r--r-- root/root      2387 2006-09-25 15:11 ./usr/share/doc/festival/README
-rw-r--r-- root/root      8538 2001-05-27 17:07 ./usr/share/doc/festival/NEWS
root@Mythic:/home/sgales/festival/festival# 
```

Answering "n" to
```
Should I exclude them from the package? (Saying yes is a good idea)  [y]:
```
didn't help at all, the binaries were still left out of the deb.

Thanks for the great HOWTO!

---

### Post by MonkeeSage on 2008-07-10
> **simongales said:**
> This worked out well, and I have all my voices working again.



This didn't seem to work - the deb package only included the docs, no binaries.  

```
root@Mythic:/home/sgales/festival/festival# checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>>  Festival Speech Synthesis System: 1.96:beta July 2004
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@Mythic ]
1 -  Summary: [ Festival Speech Synthesis System: 1.96:beta July 2004 ]
2 -  Name:    [ festival ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ festival ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version:
>> 1.96

This package will be built according to these values:

0 -  Maintainer: [ root@Mythic ]
1 -  Summary: [ Festival Speech Synthesis System: 1.96:beta July 2004 ]
2 -  Name:    [ festival ]
3 -  Version: [ 1.96 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ festival ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making in bin

Remove Links: festival festival_client festival_server festival_server_control text2w                                                                                        ave

Main Links: festival festival_client

Scripts: (sh) (prl) festival_server festival_server_control

======================== Installation successful ==========================

Copying documentation directory...
./
./INSTALL
./COPYING
./doc/
./doc/festival.jpg
./doc/indexHeader.inc
./doc/cstr.gif
./doc/classHeader.inc
./doc/banner.inc
./doc/festival_tiny.jpg
./doc/edcrest.gif
./doc/Makefile
./doc/refcard.tex
./doc/festival_small.jpg
./doc/festival.head
./doc/festival_client.head
./doc/festival_client.1
./doc/est_small.jpg
./doc/est.jpg
./doc/festival.texi
./doc/festival.tail
./doc/festival_client.tail
./doc/festival.1
./doc/hierHeader.inc
./README
./NEWS
cp: cannot stat `//var/tmp/TqALQOBjJDoijMWFImCCj/newfiles.tmp': No such file or direc                                                                                        tory
grep: /var/tmp/TqALQOBjJDoijMWFImCCj/newfile: No such file or directory

Some of the files created by the installation are inside the build
directory: /home/sgales/festival/festival

You probably don't want them to be included in the package,
especially if they are inside your home directory.
Do you want me to list them?  [n]: y
Should I exclude them from the package? (Saying yes is a good idea)  [y]:

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/sgales/festival/festival/festival_1.96-1_amd64.deb

 You can remove it from your system anytime using:

      dpkg -r festival

**********************************************************************


root@Mythic:/home/sgales/festival/festival# dpkg --contents  festival_1.96-1_amd64.deb                                                                               
drwxr-xr-x root/root         0 2008-07-09 09:59 ./
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/share/
drwxr-xr-x root/root         0 2008-07-09 09:57 ./usr/share/doc/
drwxr-xr-x root/root         0 2008-07-09 09:56 ./usr/share/doc/festival/
-rw-r--r-- root/root     21893 2004-07-01 15:06 ./usr/share/doc/festival/INSTALL
-rw-r--r-- root/root      5038 2004-05-25 08:09 ./usr/share/doc/festival/COPYING
drwxrwxr-x root/root         0 2008-07-04 13:01 ./usr/share/doc/festival/doc/
-rw-r--r-- root/root      9001 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .jpg
-rw-r--r-- root/root       550 2001-04-04 06:55 ./usr/share/doc/festival/doc/indexHea                                                                                        der.inc
-rw-r--r-- root/root       724 2001-04-04 06:55 ./usr/share/doc/festival/doc/cstr.gif
-rw-r--r-- root/root       408 2001-04-04 06:55 ./usr/share/doc/festival/doc/classHea                                                                                        der.inc
-rw-r--r-- root/root       435 2003-02-21 13:10 ./usr/share/doc/festival/doc/banner.i                                                                                        nc
-rw-r--r-- root/root      2223 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _tiny.jpg
-rw-r--r-- root/root      3659 2001-04-04 06:55 ./usr/share/doc/festival/doc/edcrest.                                                                                        gif
-rw-r--r-- root/root      4884 2001-04-04 06:55 ./usr/share/doc/festival/doc/Makefile
-rw-r--r-- root/root     13080 2001-04-04 06:55 ./usr/share/doc/festival/doc/refcard.                                                                                        tex
-rw-r--r-- root/root      3504 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _small.jpg
-rw-r--r-- root/root       722 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .head
-rw-r--r-- root/root       519 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _client.head
-rw-r--r-- root/root      1897 2008-07-04 13:01 ./usr/share/doc/festival/doc/festival                                                                                        _client.1
-rw-r--r-- root/root      1999 2001-04-04 06:55 ./usr/share/doc/festival/doc/est_smal                                                                                        l.jpg
-rw-r--r-- root/root      4398 2001-04-04 06:55 ./usr/share/doc/festival/doc/est.jpg
-rw-r--r-- root/root    357856 2004-05-25 08:10 ./usr/share/doc/festival/doc/festival                                                                                        .texi
-rw-r--r-- root/root       595 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        .tail
-rw-r--r-- root/root       364 2001-04-04 06:55 ./usr/share/doc/festival/doc/festival                                                                                        _client.tail
-rw-r--r-- root/root      2461 2008-07-04 13:01 ./usr/share/doc/festival/doc/festival                                                                                        .1
-rw-r--r-- root/root       544 2001-04-04 06:55 ./usr/share/doc/festival/doc/hierHead                                                                                        er.inc
-rw-r--r-- root/root      2387 2006-09-25 15:11 ./usr/share/doc/festival/README
-rw-r--r-- root/root      8538 2001-05-27 17:07 ./usr/share/doc/festival/NEWS
root@Mythic:/home/sgales/festival/festival# 
```

Answering "n" to
```
Should I exclude them from the package? (Saying yes is a good idea)  [y]:
```
didn't help at all, the binaries were still left out of the deb.

Thanks for the great HOWTO!

NP! Glad you got it working. :) I haven't used checkinstall very much, so I'm not sure what it was doing there.

---

### Post by BillaMonster on 2008-08-05
I have cmu_us_rms_arctic_clunits set to the default voice in voice.scm and siteinit.scm, using *(set! voice_default 'voice_cmu_us_rms_arctic_clunits)*

When I use festival via the terminal (e.g. *echo "Test." | festival --tts*) it uses that voice fine.  However, when I use the gnomesword 2.2.3 feature which uses festival to read text aloud, it always uses the robot-sounding kal_diphone voice.

Is there anything else I need to do to ensure cmu_us_rms_arctic_clunits is the default voice?  Or is gnomesword maybe calling festival in some weird way that only uses kal_diphone?

EDIT: It works if I restart my computer, but I can't figure out how to make it work in a more timely manner.

---

### Post by tabarin on 2008-08-31
Thanks for this guide MonkeeSage, I'm not sure I would have been able to get festival up and running so quickly without it.

I have a question about the output quality of the nitech HTS voices, I got and installed the latest 2.1 voices just today but I noticed that they have a very "buzzy" quality when they're output and when I hear them on Edinburgh server they don't have this problem ([http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html](http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html)). Its almost as if the "STRAIGHT vocoder" described in the "An Overview of Nitech HMM-based Speech Synthesis System for Blizzard Challenge 2005" paper is not functioning. Am I missing something or perhaps I should try to build the entire system from scratch using the sources?

Edit: Here are some audio examples so you can hear the problem that I'm talking about.
Using the Nitech SLT voice from the online demo I get:
[http://www.arondennen.com/files/onlineSLT.wav](http://www.arondennen.com/files/onlineSLT.wav)
which is how I would like my system to sound.

However when using the 2.1 version of the Nitech SLT voice on my system I get this buzzy output:
[http://www.arondennen.com/files/problematicSLT.wav](http://www.arondennen.com/files/problematicSLT.wav)

Thanks

---

### Post by 4NERMAN on 2008-09-01
Thank you for the usefull post.

But does any one knows if there is posibility to make festival read romaji

Thanks in Advance

---

### Post by bobonthenet on 2008-09-03
I have gotten everything to work according to the howto but attempting to change the default voice using ```
(set! voice_default 'cmu_us_bdl_arctic_clunits)
``` in /usr/share/festival/festival.scm gives me the following error.
> 
SIOD ERROR: unbound variable : cmu_us_bdl_arctic_clunits
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


Can someone help me with this?

---

### Post by BillaMonster on 2008-09-03
> **bobonthenet said:**
> I have gotten everything to work according to the howto but attempting to change the default voice using ```
(set! voice_default 'cmu_us_bdl_arctic_clunits)
``` in /usr/share/festival/festival.scm gives me the following error.


Can someone help me with this?

Well, mine works if I put the line in *voice.scm* and/or *siteinit.scm*

And mine is called **voice**_cmu_us_rms_arctic_clunits, but I might not have followed the directions exactly...I don't really remember.

---

### Post by bobonthenet on 2008-09-03
> **BillaMonster said:**
> Well, mine works if I put the line in *voice.scm* and/or *siteinit.scm*

And mine is called **voice**_cmu_us_rms_arctic_clunits, but I might not have followed the directions exactly...I don't really remember.

That didn't work but you did steer me in the right direction and I got it working.  There is a line in init.scm that does it.  Its set to voice_default so I changed it to voice_cmu_us_bdl_arctic_clunits and it worked like a charm.  Thanks a ton I don't think I could have figured it out on my own, since I would have had to look at all of the files not knowing what any of them do.

---

### Post by ignoti on 2008-09-13
great thread... i was able to get the voices working and its cool to hear the new voices through icecast (using liquidsoap)

now i should check out your "ghetto" front-end... maybe we could eventually get a few ppl together to set up a more complete front-end.

thanks for the howto

---

### Post by purplemutant on 2008-09-24
Thanks a bunch for this post. I have been playing around with festival for a while. I wasn't all that happy with the default ked voice. These new voices are much better. Everything worked great on my system. Ubuntu Hardy, festival 1.96:beta. :D

I also have a quick question. I have been playing around with python using festival. Right now my programs are issuing console commands to get festival to speak: echo "some text" | festival --tts. Does anyone know how to issue text directly to festival from python rather than issuing console commands?

---

### Post by purplemutant on 2008-09-24
Oh one more thing. When festival is done speaking it iterates a tiny bit of the first word. Any idea what's going on and how I can fix it?

---

### Post by darrelljon on 2008-09-28
I've installed the voices correctly (Mbrola and HTS) yet whenever I select voice I can only get the default voice.```
festival> (set! voice_default 'voice_us3_mbrola)
voice_us3_mbrola
festival> (SayText "Hello")
#<Utterance 0xb696d268>
festival> (set! voice_default 'voice_cmu_us_kal_com_hts)
voice_cmu_us_kal_com_hts
festival> (SayText "Hello")
#<Utterance 0xb69a3d68>
festival> (set! voice_default 'voice_nitech_us_awb_arctic_hts)
voice_nitech_us_awb_arctic_hts
festival> (SayText "Hello")
#<Utterance 0xb69bb0d8>
festival> (voice.list)
(us2_mbrola
 us3_mbrola
 us1_mbrola
 rab_diphone
 cmu_us_kal_com_hts
 nitech_us_rms_arctic_hts
 cstr_us_ked_timit_hts
 nitech_us_bdl_arctic_hts
 nitech_us_awb_arctic_hts
 nitech_us_clb_arctic_hts
 nitech_us_jmk_arctic_hts
 nitech_us_slt_arctic_hts)

```
Am I doing something wrong? Where are the .scm files?

---

### Post by pmuzyk on 2008-10-04
Wow this works great! 

The best is the Nitech 'bdl' voice. It's nice and clear 'tenor' voice.

Thanks for the festival.scm parameters. I wrote a simple bash script that is executed as a cron task and it tells me the time every hour. Good for my time based work that I do.

One thing though, how do you increase the amplitude of the voice when using alsa to output the voice? I have music on sometimes and it's hard to hear the voice over the music. :D

Thanks billions of times!

---

### Post by tagger on 2008-10-23
After using your post to setup and configure all the voices I really appreciate the effort it must have taken to compile it all.  

After using festival for a while I created a shell script (bash) to automatically convert doc, txt, rtf, pdf, ps, chm, html, and even direct URLs into almost any type of audio file (wav/ogg/mp3/etc) using festival with the voice you chose. 

The script is GPL and I posted it along with instructions at my site: [http://taggedzi.com/text2audio.php]("http://taggedzi.com/text2audio.php") 

Hopefully this is the right place to post this, as it ties in and I am not sure if it should be a post of it's own.

Well enjoy and happy text to speeching!

---

### Post by resize on 2008-11-02
After searching for a long time on how to get festivak to work I found this howto :-)

All is working great, but as I want to use the Dutch language I downloaded and installed the Dutch languages.
> wget -c [http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl1/nl1-980609.zip](http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl1/nl1-980609.zip)
wget -c [http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl2/nl2-990507.zip](http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl2/nl2-990507.zip)
wget -c [http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl3/nl3-001013.zip](http://tcts.fpms.ac.be/synthesis/mbrola/dba/nl3/nl3-001013.zip)

unzip -x nl1-980609.zip
unzip -x nl2-990507.zip
unzip -x nl3-001013.zip

sudo mkdir -p /usr/share/festival/voices/dutch/nl1_mbrola/
sudo mkdir -p /usr/share/festival/voices/dutch/nl2_mbrola/
sudo mkdir -p /usr/share/festival/voices/dutch/nl3_mbrola/

sudo mv nl1 /usr/share/festival/voices/dutch/nl1_mbrola/
sudo mv nl2 /usr/share/festival/voices/dutch/nl2_mbrola/
sudo mv nl3 /usr/share/festival/voices/dutch/nl3_mbrola/

Now when I start festival, and try to set the Dutch language I get the following error.
> festival> (voice_nl1_mbrola)
SIOD ERROR: could not open file /usr/share/festival/voices/dutch/nl1_mbrola/festvox/nl1_mbrola.scm
Looking at the /usr/share/festival/voices/dutch/nl1_mbrola directory I can see that festvox is missing. (this is obvious as I did not download it)
So going to the [www.festvox.org](www.festvox.org) site, I do not see the needed files for the Dutch language :(

Anyone here who might know how I can get Dutch to work?

Thank you.

---

### Post by alanbshepard70 on 2008-11-09
To MonkeeSage I just wanted to say thank you for creating one of the best tutorials I've ever needed to use. You're a lifesaver and I for one am extremely thankful for you efforts. Thanks.
come

To tagger your script is the perfect compliment to this guide and I really appreciate what you've done as well. Thanks.

The community needs more contributors like the two of you. Hats off gents, well done ;)

---

### Post by wersdaluv on 2008-11-10
I installed the nitech voices and I am loving them. It's just that, they only work with the use of ktts for me. I am on Intrepid now. For me to let it be used for festival on the command line, I have to run **(voice_nitech_us_awb_arctic_hts)** first. 

Whenever I run festival on the command line, I get ```
festival

WARNING
No default voice found in ("/usr/share/festival/voices/")
either no voices unpacked or voice-path is wrong
Scheme interpreter will work, but there is no voice to speak with.
WARNING

Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'

```

How do I set a default voice? :)

---

### Post by MonkeeSage on 2008-11-19
@resize:

I'm not sure where to get the festvox wrapper for the MBROLA nl1 voice. Google didn't turn up anything helpful either. Sorry. :(


@wersdaluv:

Try adding "(set! default_voice 'voice_nitech_us_awb_arctic_hts)" to /etc/festival.scm.

---

### Post by jivy on 2008-11-19
> **tabarin said:**
> I have a question about the output quality of the nitech HTS voices, I got and installed the latest 2.1 voices just today but I noticed that they have a very "buzzy" quality when they're output and when I hear them on Edinburgh server they don't have this problem ([http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html](http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html)). Its almost as if the "STRAIGHT vocoder" described in the "An Overview of Nitech HMM-based Speech Synthesis System for Blizzard Challenge 2005" paper is not functioning. Am I missing something or perhaps I should try to build the entire system from scratch using the sources?

Edit: Here are some audio examples so you can hear the problem that I'm talking about.
Using the Nitech SLT voice from the online demo I get:
[http://www.arondennen.com/files/onlineSLT.wav](http://www.arondennen.com/files/onlineSLT.wav)
which is how I would like my system to sound.

However when using the 2.1 version of the Nitech SLT voice on my system I get this buzzy output:
[http://www.arondennen.com/files/problematicSLT.wav](http://www.arondennen.com/files/problematicSLT.wav)

I'm also curious about this, as I experience the same problem. Anyone have any ideas?

---

### Post by MonkeeSage on 2008-11-20
> **jivy said:**
> I'm also curious about this, as I experience the same problem. Anyone have any ideas?

I have no idea about the buzzing. You can tweak the speed, frequencies (probably too much low frequency in the output), and other parameters of the voice synthesis; but it's rather convoluted and involved. The defaults should produce a good synthesis though (see the test pages for the voices given in the HOWTO). So I'm not sure what the problem is.

My only guess is to try installing the patch listed in the the "Installing Festival 1.96 from source" section. Save [this file](http://monkeesage.prohosts.org/lib_hts.scm.diff) as /tmp/lib_hts.scm.diff. Then, from a terminal, run:

```

cd /usr/share/festival
sudo patch -p2 -i /tmp/lib_hts.scm.diff

```

---

### Post by Uji-Wu on 2009-01-04
Is this guide leading me to, after all those procedures, have the chance of installing a few french speech bases?

---

### Post by sashko on 2009-01-26
Hi, I'm having festival 1.4.3 on my gutsy gibon and I'm trying to install a cmu voice [http://www.festvox.org/packed/voices/croatian/festvox_cmu_cr_tp_clunits16k.tar.gz](http://www.festvox.org/packed/voices/croatian/festvox_cmu_cr_tp_clunits16k.tar.gz) (luckily I'v found it)
as you said in this tut, I have already upacked, copied and created dir /usr/share/festival/voices/croatian/cmu_cr_tp_clunits, and /etc/festival.scm with line

```
;;(set! voice_default 'voice_cmu_cr_tp_clunits)
```

 When is that line uncomment festival output is :

> sasa@sasa-laptop:~$ festival
SIOD ERROR: could not open file /usr/lib/festival/../src/modules/clunits/acost.scm
closing a file left open: /usr/share/festival/voices/croatian/cmu_cr_tp_clunits/festvox/cmu_cr_tp_clunits.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


Can you suggest me anything what else to do to make this voice usable.
thanks in advance, sasa.



[edit]

same thing with new compiled version

---

### Post by MonkeeSage on 2009-02-07
> **sashko said:**
> Hi, I'm having festival 1.4.3 on my gutsy gibon and I'm trying to install a cmu voice [http://www.festvox.org/packed/voices/croatian/festvox_cmu_cr_tp_clunits16k.tar.gz](http://www.festvox.org/packed/voices/croatian/festvox_cmu_cr_tp_clunits16k.tar.gz) (luckily I'v found it)
as you said in this tut, I have already upacked, copied and created dir /usr/share/festival/voices/croatian/cmu_cr_tp_clunits, and /etc/festival.scm with line

```
;;(set! voice_default 'voice_cmu_cr_tp_clunits)
```

 When is that line uncomment festival output is :



Can you suggest me anything what else to do to make this voice usable.
thanks in advance, sasa.



[edit]

same thing with new compiled version

Sorry for the delay. I'll try to have a look at this over the weekend.

---

### Post by Tycho451 on 2009-02-11
Hi,
first: Thanks for this great Howto!

I have a problem though.
When I try to use the enhanced Nitech HTS voices I get kicked out.
```

$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (voice_nitech_us_slt_arctic_hts)
nitech_us_slt_arctic_hts
festival> (SayText "Incoming message")
Aborted
$

```

I tried to compile from source (although I already had 1.96:beta), but the speech-tools don't compile.
```

g++ -c -g -O3 -fPIC -Wall -Wno-non-template-friend -I../include -DINSTANTIATE_TEMPLATES est_file.cc
../base_class/EST_TNamedEnum.cc: In member function »EST_read_status EST_TNamedEnum<ENUM>::priv_load(EST_String, EST_TNamedEnum<ENUM>*) [with ENUM = EST_EstFileType]«:
est_file.cc:72:   instantiated from here
../base_class/EST_TNamedEnum.cc:215: Fehler: keine passende Funktion für Aufruf von »split(EST_String&, EST_String [12], int, EST_Regex&, char)«
../base_class/EST_TNamedEnum.cc:239: Fehler: keine passende Funktion für Aufruf von »split(EST_String&, EST_String [12], int, EST_Regex&, char&)«
make[2]: *** [est_file.o] Fehler 1
make[1]: *** [utils] Fehler 2
make[1]: Verlasse Verzeichnis '/home/marco/fest_tmp/speech-tools-1.2.96~beta'
make: *** [build-stamp] Fehler 2
debuild: fatal error at line 1311:
couldn't exec fakeroot debian/rules:

```

So I just compiled and installed festival from source. Didn't make a diffrence though.

Has anyone any ideas what might be wrong?

---

### Post by shane2peru on 2009-02-11
Wow, great how too!!!  Excellent!

Shane

---

### Post by Tycho451 on 2009-02-11
I also tried to get german festival voices with this guide:
[http://docs.kde.org/stable/en/kdeaccessibility/kttsd/configuration.html#ims-german-festival](http://docs.kde.org/stable/en/kdeaccessibility/kttsd/configuration.html#ims-german-festival)

I do everything according to the guide, but I can't get it to work (SIOD ERROR: unbound variable : voice_german_de2_os).

---

### Post by shane2peru on 2009-02-11
ok, I'm having real problems with the mbrola side of things.  I have used espeak in the past, and it works well.  I have used it with mbrola as well.  However now whatever I do, mbrola is not working correctly.  I'm working on Ubuntu Intrepid 64 version, all up to date.  MBROLA is not cooperating.  I downloaded and installed the mbrola binary for 64 bit from here:  [http://tcts.fpms.ac.be/synthesis/mbrola.html](http://tcts.fpms.ac.be/synthesis/mbrola.html)   - the last one in the list.  I unzip it, I chomd +x the mbrola file (to make it executable) then copy it to /usr/local/bin.  Then I run the mbrola to make sure it works, and sure enough it gives me the speal, it is installed and running.  When I then run the test according to this page:  [http://tcts.fpms.ac.be/synthesis/mbrola/mbruse.html](http://tcts.fpms.ac.be/synthesis/mbrola/mbruse.html)  and it doesn't work.  Any help that can be provided would greatly be appreciated.  I do have the voices downloaded, and when I run the test line with the appropriate directories, it doesn't seem to work for me.  It is driving me crazy.  Any help would greatly be appreciated.

Shane

PS festival is working, however I want the Spanish voices that come with mbrola, and I didn't see them in any of the others.  I also would just like to have mbrola working correctly.

---

### Post by MonkeeSage on 2009-02-15
> **Tycho451 said:**
> Hi,
first: Thanks for this great Howto!

I have a problem though.
When I try to use the enhanced Nitech HTS voices I get kicked out.

Do any other voices work properly (other Nitech voices, Mbrola voices, &c) or do they all die like that? Did you set up any special output method in the config file?

---

### Post by MonkeeSage on 2009-02-15
> **Tycho451 said:**
> I also tried to get german festival voices with this guide:
[http://docs.kde.org/stable/en/kdeaccessibility/kttsd/configuration.html#ims-german-festival](http://docs.kde.org/stable/en/kdeaccessibility/kttsd/configuration.html#ims-german-festival)

I do everything according to the guide, but I can't get it to work (SIOD ERROR: unbound variable : voice_german_de2_os).

It looks like to use the ims_german_festival requires installing festival / speech tools from vanilla source. I'm not sure how easy it would be to get it working with this guide. Might be pretty complicated. I would suggest following their [README](http://www.ims.uni-stuttgart.de/phonetik/synthesis/festival/README.ims_german_festival) and installing that copy of festival in /usr/local or /opt. Then you can have a German festival install and the English voices from this guide. Good luck!

---

### Post by MonkeeSage on 2009-02-15
> **shane2peru said:**
> ok, I'm having real problems with the mbrola side of things.  I have used espeak in the past, and it works well.  I have used it with mbrola as well.  However now whatever I do, mbrola is not working correctly.  I'm working on Ubuntu Intrepid 64 version, all up to date.  MBROLA is not cooperating.  I downloaded and installed the mbrola binary for 64 bit from here:  [http://tcts.fpms.ac.be/synthesis/mbrola.html](http://tcts.fpms.ac.be/synthesis/mbrola.html)   - the last one in the list.  I unzip it, I chomd +x the mbrola file (to make it executable) then copy it to /usr/local/bin.  Then I run the mbrola to make sure it works, and sure enough it gives me the speal, it is installed and running.  When I then run the test according to this page:  [http://tcts.fpms.ac.be/synthesis/mbrola/mbruse.html](http://tcts.fpms.ac.be/synthesis/mbrola/mbruse.html)  and it doesn't work.  Any help that can be provided would greatly be appreciated.  I do have the voices downloaded, and when I run the test line with the appropriate directories, it doesn't seem to work for me.  It is driving me crazy.  Any help would greatly be appreciated.

Shane

PS festival is working, however I want the Spanish voices that come with mbrola, and I didn't see them in any of the others.  I also would just like to have mbrola working correctly.

Hi Shane,

Works for me...

```

wget http://tcts.fpms.ac.be/synthesis/mbrola/dba/es1/es1-980610.zip
unzip -x es1-980610.zip
mbrola es1/es1 es1/TEST/example1.pho test.wav
play test.wav
rm test.wav

```

What problem are you having with it, exactly?

Jordan

---

### Post by MonkeeSage on 2009-02-16
> **sashko said:**
> Can you suggest me anything what else to do to make this voice usable.
thanks in advance, sasa.

Hi Sasa,

Alright, I finally got some time to play with this. Here's what I found. I got the voice to load by editing /usr/share/festival/voices/croatian/cmu_cr_tp_clunits/festvox/cmu_cr_tp_clunits.scm and changing lines 40-41 from:

```

(if (null (member 'clunits provided))
    (load (path-append libdir "../src/modules/clunits/acost.scm")))

```

to:

```

;;(if (null (member 'clunits provided))
;;    (load (path-append libdir "../src/modules/clunits/acost.scm")))

```

But now when I try to synthesize some text, I get e new error:

```

festival>(voice_cmu_cr_tp_clunits)         
cmu_cr_tp_clunits
festival> (SayText "Lijepa nasa domovino") 
SIOD ERROR: Undefined SynthType Cluster

```

I have no idea how to fix this. :(

I only tried it with 1.96, and this voice is really old (made in 2000 according to the festvox server), so maybe it would work with 1.4. Sorry I can't be more helpful!

---

### Post by shane2peru on 2009-02-16
> **MonkeeSage said:**
> Hi Shane,

Works for me...

```

wget http://tcts.fpms.ac.be/synthesis/mbrola/dba/es1/es1-980610.zip
unzip -x es1-980610.zip
mbrola es1/es1 es1/TEST/example1.pho test.wav
play test.wav
rm test.wav

```

What problem are you having with it, exactly?

Jordan
Ok, I ran all of these, and I don't get any errors.  Except instead of using play I use vlc to play the wav file.  I am using oss instead of alsa, and play doesn't work with oss.  I have tested vlc on other wav files and it works fine.  However when I use vlc test.wav all I get is this horrible sound that someone is running a fan into the microphone.  Very loud and bad.  It doesn't give me any error reports.

Shane

---

### Post by MonkeeSage on 2009-02-17
> **shane2peru said:**
> Ok, I ran all of these, and I don't get any errors.  Except instead of using play I use vlc to play the wav file.  I am using oss instead of alsa, and play doesn't work with oss.  I have tested vlc on other wav files and it works fine.  However when I use vlc test.wav all I get is this horrible sound that someone is running a fan into the microphone.  Very loud and bad.  It doesn't give me any error reports.

Shane

Well, the only difference seems to be our mbrola binaries (I have a 32-bit CPU). Can you run the 32-bit mbrola binary?

---

### Post by shane2peru on 2009-02-18
> **MonkeeSage said:**
> Well, the only difference seems to be our mbrola binaries (I have a 32-bit CPU). Can you run the 32-bit mbrola binary?

I will have to give this a try and will let you know.  Thanks.

Shane

---

### Post by nyiti on 2009-02-24
Hi! Thanks for the great HOWTO.

I'm trying to compile festival with 

**OGIresLPC** - synthesizer C++/Scheme code and a short technical report. 
**OGIlexicon** - Festival-format American English lexicon compiled from Moby and CMU lexicons. This lexicon has recently been resyllabified and cleaned up.
[_http://cslu.cse.ogi.edu/tts/download/_](_http://cslu.cse.ogi.edu/tts/download/_)
The OGIresLPC module installs itself in festival during the compile, that's why I'm frustrating myself with it.

Basically I can't get speech-tools to compile, I tried from the ubuntu sources, debian sources, the originals from festvox.org, etc. No luck, I get the same error each time.

```

# whoami
root
# pwd
.../speech-tools-1.2.96~beta
# make clean
# ./configure
# make
... all goes well, until:
look at library eststring
Making in directory ./utils ...
g++ -c -O3 -fPIC -Wall -I../include cmd_line.cc
cmd_line.cc: In function &#8216;void output_sgml_synopsis(char**, const EST_String&)&#8217;:
cmd_line.cc:463: warning: format not a string literal and no format arguments
g++ -c -O3 -fPIC -Wall -I../include util_io.cc
g++ -c -O3 -fPIC -Wall -I../include filetrans.cc
g++ -c -O3 -fPIC -Wall -I../include cmd_line_aux.cc
g++ -c -O3 -fPIC -Wall -I../include EST_swapping.cc
g++ -c -O3 -fPIC -Wall -I../include EST_Server.cc
EST_Server.cc: In member function &#8216;EST_connect_status EST_Server::disconnect()&#8217;:
EST_Server.cc:385: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
g++ -c -O3 -fPIC -Wall -I../include EST_FringeServer.cc
g++ -c -O3 -fPIC -Wall -I../include -DINSTANTIATE_TEMPLATES est_file.cc
../base_class/EST_TNamedEnum.cc: In member function &#8216;EST_read_status EST_TNamedEnum<ENUM>::priv_load(EST_String, EST_TNamedEnum<ENUM>*) [with ENUM = EST_EstFileType]&#8217;:
est_file.cc:72:   instantiated from here
../base_class/EST_TNamedEnum.cc:215: error: no matching function for call to &#8216;split(EST_String&, EST_String [12], int, EST_Regex&, char)&#8217;
../base_class/EST_TNamedEnum.cc:239: error: no matching function for call to &#8216;split(EST_String&, EST_String [12], int, EST_Regex&, char&)&#8217;
make[1]: *** [est_file.o] Error 1
make: *** [utils] Error 2

```

This seems to be the same problem that Tycho451 reported earlier (comment[_#71_]("http://ubuntuforums.org/showpost.php?p=6716364&postcount=71"))

I'm at my wit's end :( , can you tell what's wrong?

---

### Post by nyiti on 2009-02-24
There is a newer CMU dict file available than the one in the ubuntu festival package, I thought you might want to include it in the HOWTO.

[_cmudict.0.7a_]("https://cmusphinx.svn.sourceforge.net/svnroot/cmusphinx/trunk/cmudict/cmudict.0.7a")

There is a **cmu2ft** script to convert the dict, in the [_festlex_CMU.tar.gz_]("http://www.festvox.org/packed/festival/latest/festlex_CMU.tar.gz") from the [http://www.festvox.org/packed/festival/latest/](http://www.festvox.org/packed/festival/latest/) directory.

How can you install the cmudict.0.7a properly? I guess the Makefile in the festlex_CMU.tar.gz gives the clues, but I don't really get it.

Also, at the festvox latest dir, what are the
**festvox_cstr_us_awb_arctic_multisyn-1.0.tar.gz**
**festvox_cstr_us_jmk_arctic_multisyn-1.0.tar.gz**
files?

Are they voices good enough to include it in the HOWTO?

---

### Post by emnaki on 2009-04-16
This is question is about Carnival, the frontend for festival. Has anyone successfully been able to install it and if possible could you show me how. I tried installing from source but the makefile.unx gives errors. I suspect an old implementation of the wxwidgets API is being used. 

Failing to get Carnival to work, is there any alternatives to Carnival. Perferably I would like to avoid doing my own SSML markups in scheme in the interactive prompt.

---

### Post by kuzniarpawel on 2009-04-19
I also noticed problems with buzzing sound and random jitter. I use festival: Festival Speech Synthesis System: 1.96:beta July 2004
from Ubuntu Jaunty 64 bit.

File attached is a fragment of Wikipedia Article about Gerard K. O'Neill
I used text2audio script from [http://www.taggedzi.com/text2audio.html]("http://www.taggedzi.com/text2audio.html")

Fragment converted from html to txt looks like this.
"to be alive now and not take part in it seemed terribly myopic".^[5] He was put through NASA's rigorous mental and physical examinations. During this time he met Brian O'Leary"

As I said jitter seems to be random and not associated with special characters in text (as in here ^[5]). Generating audio files one more time give different results. 

I use American female - SLT voice
Any ideas why this jitter occurs or why SLT voice is so harsh and buzzing comparing to Festival Text-to-Speech Online Demo - Technical.

---

### Post by MonkeeSage on 2009-04-25
@nyiti:

Sorry I've not had time to properly look at the information you've provided and address your problems. I'll try to get to them this weekend or in the following week.

@emnaki:

Never tried carnival. On my (way too long!) todo list is making a pygtk frontend to Festival--at least for simple TTS. Someday...*sigh*

@kuzniarpawel:

Again, I can't reproduce the problem and have no clue about the cause. Sorry. :(

---

### Post by emnaki on 2009-04-27
MonkeeSage: Cool looking forward to it!

Well after trying the Nitech Voices and CMU Arctic Voices out, I've found them both to be great, but there is one shortcoming to each one of them, the Nitech has nice flowing speech, but the audio quality is a little low. It has this buzzing noise which is annoying. But thats to be expected from something so small. The CMU Arctic on the other hand, has good quality voice, but the words/phonemes don't join very well and so there are clicks here and there. So I'm curious, is it possible to use the Nitech system but with the higher quality CMU unit database?

---

### Post by artir on 2009-05-03
I made a simple GUI to test festival:

[http://launchpad.net/cerva](http://launchpad.net/cerva)

---

### Post by MonkeeSage on 2009-05-10
For posterity, here is a very simple prototype GUI for Festival / SPD-say again:

*gspeak.py*
```
#!/usr/bin/python
# -*- ts=4:sw=4:noexpandtab -*-

import os
import sys

try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
	import gtk.glade
except:
	print 'This program requires pygtk\n' \
				'http://www.pygtk.org/'
	sys.exit(1)

class SpeechKit:

	def __init__(self):
		self.use_spd = True
		self.active_file = None
		self.pwd = os.path.dirname(sys.argv[0])

		self.glade  = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'main_window')
		self.window = self.glade.get_widget('main_window')
		self.view   = self.glade.get_widget('text')

		self.glade.signal_autoconnect({
			'on_main_quit'   : self.on_main_quit,
			'on_open'        : self.open_file,
			'on_speak'       : self.start_speech,
			'on_stop'        : self.stop_speech,
			'on_choose_fest' : self.on_choose_fest,
			'on_choose_spd'  : self.on_choose_spd,
			'on_about'       : self.show_about
		})

	def run(self):
		gtk.main()

	def open_file(self, widget=None):
		self.glade = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'filechooser_dialog')
		dlg   = self.glade.get_widget('filechooser_dialog')
		dlg.connect('file_activated', self.choose_file)
		dlg.connect('response', self.close_chooser)

	def close_chooser(self, widget, args=None):
		widget.destroy()

	def choose_file(self, widget, args=None):
		name = widget.get_filename()
		fh   = open(name)
		data = fh.read()
		fh.close()
		self.view.get_buffer().set_text(data)
		self.window.set_title(os.path.basename(name))

	def start_speech(self, widget=None):
		buffer = self.view.get_buffer()
		text = buffer.get_text(*buffer.get_bounds())
		if self.use_spd:
			pipe = os.popen('spd-say -e 1 > /dev/null', 'w')
			pipe.write(text)
			pipe.close()
		else:
			fh = open('/tmp/foobarbaz', 'w')
			fh.write(text)
			fh.close()
			os.system(r'echo "(tts \"/tmp/foobarbaz\" nil)" | festival &')

	def stop_speech(self, widget=None):
		if self.use_spd:
			os.system('spd-say -S')
			os.system('spd-say -C')
		else:
			pipe = os.popen('pidof festival', 'r')
			pid = pipe.read().strip()
			while not pid == "":
				os.system('killall -9 festival')
				os.system('killall -9 /usr/lib/festival/audsp')
				pid = pipe.read().strip()
			pipe.close()

	def on_choose_fest(self, widget=None):
		self.use_spd = False

	def on_choose_spd(self, widget=None):
		self.use_spd = True

	def show_about(self, widget=None):
		self.glade = gtk.glade.XML('%s/gspeak.glade' % self.pwd, 'about_dialog')
		dlg = self.glade.get_widget('about_dialog')
		dlg.connect('response', self.about_quit)

	def about_quit(self, widget, args=None):
		widget.destroy()

	def on_main_quit(self, widget, args=None):
		self.stop_speech()
		gtk.main_quit()

if __name__ == '__main__':
	sk = SpeechKit()
	if len(sys.argv) > 1:
		if sys.argv[1] == '-s':
		  pass # use default spd-say synthesis
		elif sys.argv[1] == '-f':
			sk.use_spd = False
		for file in sys.argv[2:]:
			sk.active_file = file
			break
	sk.run()



```

*gspeak.glade*
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--*- mode: xml -*-->
<glade-interface>
  <widget class="GtkWindow" id="main_window">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Gspeak</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <property name="default_width">640</property>
    <property name="default_height">480</property>
    <property name="icon_name">stock_headphones</property>
    <signal name="delete_event" handler="on_main_quit"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkMenuBar" id="menubar">
            <property name="visible">True</property>
            <child>
              <widget class="GtkMenuItem" id="file_menu">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="file_menu_menu">
                    <child>
                      <widget class="GtkImageMenuItem" id="open">
                        <property name="visible">True</property>
                        <property name="label">gtk-open</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <signal name="activate" handler="on_open"/>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkSeparatorMenuItem" id="separator">
                        <property name="visible">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="quit">
                        <property name="visible">True</property>
                        <property name="label">gtk-quit</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <signal name="activate" handler="on_main_quit"/>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="_Tools">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Tools</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <child>
                      <widget class="GtkMenuItem" id="tool_fest">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Festival</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_choose_fest"/>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkMenuItem" id="tool_spd">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Speechd</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_choose_spd"/>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="help_menu">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="help_menu_menu">
                    <child>
                      <widget class="GtkImageMenuItem" id="about">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">_About</property>
                        <property name="use_underline">True</property>
                        <signal name="activate" handler="on_about"/>
                        <child internal-child="image">
                          <widget class="GtkImage" id="image4">
                            <property name="visible">True</property>
                            <property name="stock">gtk-about</property>
                            <property name="icon_size">1</property>
                          </widget>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="padding">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkScrolledWindow" id="scrolled">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="vscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="shadow_type">GTK_SHADOW_IN</property>
            <child>
              <widget class="GtkTextView" id="text">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="wrap_mode">GTK_WRAP_WORD</property>
                <property name="left_margin">4</property>
                <property name="right_margin">4</property>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="padding">2</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkButton" id="stop_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_stop"/>
                <child>
                  <widget class="GtkAlignment" id="alignment1">
                    <property name="visible">True</property>
                    <property name="xscale">0</property>
                    <property name="yscale">0</property>
                    <child>
                      <widget class="GtkHBox" id="hbox2">
                        <property name="visible">True</property>
                        <property name="spacing">2</property>
                        <child>
                          <widget class="GtkImage" id="image1">
                            <property name="visible">True</property>
                            <property name="stock">gtk-no</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkLabel" id="label1">
                            <property name="visible">True</property>
                            <property name="label" translatable="yes">Stop</property>
                            <property name="use_underline">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="padding">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="speak_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_speak"/>
                <child>
                  <widget class="GtkAlignment" id="alignment2">
                    <property name="visible">True</property>
                    <property name="xscale">0</property>
                    <property name="yscale">0</property>
                    <child>
                      <widget class="GtkHBox" id="hbox3">
                        <property name="visible">True</property>
                        <property name="spacing">2</property>
                        <child>
                          <widget class="GtkImage" id="image2">
                            <property name="visible">True</property>
                            <property name="stock">gtk-apply</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkLabel" id="label2">
                            <property name="visible">True</property>
                            <property name="label" translatable="yes">Speak</property>
                            <property name="use_underline">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="padding">2</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="padding">2</property>
            <property name="position">2</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkAboutDialog" id="about_dialog">
    <property name="visible">True</property>
    <property name="destroy_with_parent">True</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
    <property name="copyright" translatable="yes">MonkeeSage, 2007</property>
    <property name="comments" translatable="yes">Simple GTK+ frontend to spd-say (part of Speech-Dispatcher).</property>
    <property name="license" translatable="yes">GSpeak 1.0
Copyright (C) 2007 MonkeeSage

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.</property>
    <property name="authors">Jordan Callicoat &lt;MonkeeSage@gmail.com&gt;</property>
    <property name="translator_credits" translatable="yes" comments="TRANSLATORS: Replace this string with your names, one name per line.">translator-credits</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox1">
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area1">
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">GTK_PACK_END</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkFileChooserDialog" id="filechooser_dialog">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Open File....</property>
    <property name="modal">True</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <property name="destroy_with_parent">True</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_DIALOG</property>
    <property name="show_hidden">True</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox1">
        <property name="visible">True</property>
        <property name="spacing">24</property>
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area1">
            <property name="visible">True</property>
            <property name="layout_style">GTK_BUTTONBOX_END</property>
            <child>
              <widget class="GtkButton" id="button1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="label">gtk-cancel</property>
                <property name="use_stock">True</property>
                <property name="response_id">-6</property>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="button2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="label">gtk-open</property>
                <property name="use_stock">True</property>
                <property name="response_id">-5</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">GTK_PACK_END</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by nike984 on 2009-05-16
Can you tell me how to use your python script?
I don't know how to use python script.

---

### Post by MonkeeSage on 2009-05-19
> **nike984 said:**
> Can you tell me how to use your python script?
I don't know how to use python script.

Sure. Save the files (gspeak.py, gspeak.glade) to the same directory. Then just run "python gspeak.py". Don't expect too much though, as this is just a very simple prototype. HTH! :)

---

### Post by mrplow on 2009-05-23
Hi, I can't seem to get any of these voices working, I can get the standard and the mbrola ones working but none of the advanced ones, I'm running jaunty with festival 1.96b from the jaunty repositories

cmu_us_kal_com_hts
nitech_us_bdl_arctic_hts
cstr_us_ked_timit_hts
nitech_us_clb_arctic_hts
nitech_us_rms_arctic_hts
nitech_us_slt_arctic_hts
nitech_us_awb_arctic_hts
nitech_us_jmk_arctic_hts


is there a way to find out what festival is passing on to sox as to why its trying to use -- w with sox

```
myth@myth-desktop:~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (voice_cmu_us_kal_com_hts)   
cmu_us_kal_com_hts
festival> (SayText "Hello from Ubuntu")
Segmentation fault
sox: invalid option -- w
sox: SoX v14.2.0

Failed: invalid option

Usage summary: [gopts] [[fopts] infile]... [fopts] outfile [effect [effopts]]...

SPECIAL FILENAMES (infile, outfile):
-                        Pipe/redirect input/output (stdin/stdout); use with -t
-d, --default-device     Use the default audio device (where available)
-n, --null               Use the `null' file handler; e.g. with synth effect
-p, --sox-pipe           Alias for `-t sox -'

SPECIAL FILENAMES (infile only):
"|program [options] ..." Pipe input from external program (where supported)
http://server/file       Use the given URL as input file (where supported)

GLOBAL OPTIONS (gopts) (can be specified at any point before the first effect):
--buffer BYTES           Set the size of all processing buffers (default 8192)
--combine concatenate    Concatenate multiple input files (default for sox, rec)
--combine sequence       Sequence multiple input files (default for play)
--effects-file FILENAME  File containing effects and options
-h, --help               Display version number and usage information
--help-effect NAME       Show usage of effect NAME, or NAME=all for all
--help-format NAME       Show info on format NAME, or NAME=all for all
--input-buffer BYTES     Override the input buffer size (default: as --buffer)
--interactive            Prompt to overwrite output file
-m, --combine mix        Mix multiple input files (instead of concatenating)
-M, --combine merge      Merge multiple input files (instead of concatenating)
--plot gnuplot|octave    Generate script to plot response of filter effect
-q, --no-show-progress   Run in quiet mode; opposite of -S
--replay-gain track|album|off  Default: off (sox, rec), track (play)
-R                       Use default random numbers (same on each run of SoX)
-S, --show-progress      Display progress while processing audio data
--version                Display version number of SoX and exit
-V[LEVEL]                Increment or set verbosity level (default 2); levels:
                           1: failure messages
                           2: warnings
                           3: details of processing
                           4-6: increasing levels of debug messages
FORMAT OPTIONS (fopts):
Input file format options need only be supplied for files that are headerless.
Output files will have the same format as the input file where possible and not
overriden by any of various means including providing output format options.

-v|--volume FACTOR       Input file volume adjustment factor (real number)
-t|--type FILETYPE       File type of audio
-s/-u/-f/-U/-A/-i/-a/-g  Encoding type=signed-integer/unsigned-integer/floating-
                         point/mu-law/a-law/ima-adpcm/ms-adpcm/gsm-full-rate
-e|--encoding ENCODING   Set encoding (ENCODING in above list)
-b|--bits BITS           Encoded sample size in bits
-1/-2/-3/-4/-8           Encoded sample size in bytes
-N|--reverse-nibbles     Encoded nibble-order
-X|--reverse-bits        Encoded bit-order
--endian little|big|swap Encoded byte-order; swap means opposite to default
-L/-B/-x                 Short options for the above
-c|--channels CHANNELS   Number of channels of audio data; e.g. 2 = stereo
-r|--rate RATE           Sample rate of audio
-C|--compression FACTOR  Compression factor for output format
--add-comment TEXT       Append output file comment
--comment TEXT           Specify comment text for the output file
--comment-file FILENAME  File containing comment text for the output file

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb au avr caf cdda cdr cvs cvsd dat dvms f4 f8 fap flac fssd gsm hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud nist ogg paf prc pvf raw s1 s2 s3 s4 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u2 u3 u4 ub ul uw vms voc vorbis vox w64 wav wavpcm wv wve xa xi
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: alsa

EFFECTS: allpass band bandpass bandreject bass bend chorus compand contrast dcshift deemph delay dither earwax echo echos equalizer fade filter flanger gain highpass ladspa loudness lowpass mcompand mixer noiseprof noisered norm oops pad phaser pitch rate remix repeat reverb reverse riaa silence spectrogram speed splice stat stretch swap synth tempo treble tremolo trim vol

EFFECT OPTIONS (effopts): effect dependent; see --help-effect
Cannot open file /tmp/est_21001_00000/utt.wav as tokenstream
Wave load: can't open file "/tmp/est_21001_00000/utt.wav"
Cannot load wavefile: /tmp/est_21001_00000/utt.wav
#<Utterance 0xb6b1df68>
```

---

### Post by MonkeeSage on 2009-05-28
> **mrplow said:**
> Hi, I can't seem to get any of these voices working, I can get the standard and the mbrola ones working but none of the advanced ones, I'm running jaunty with festival 1.96b from the jaunty repositories

[...]

Cannot open file /tmp/est_21001_00000/utt.wav as tokenstream
Wave load: can't open file "/tmp/est_21001_00000/utt.wav"
Cannot load wavefile: /tmp/est_21001_00000/utt.wav
#<Utterance 0xb6b1df68>

Hmm. Weird. I don't have a box with Ubuntu installed currently, so I can't test this right now. It's my birthday tomorrow (well, today actually--2 am...I should really go to sleep now, heh), and I'll be out of town the next few days. When I get back I'll see about installing jaunty in VirtualBox and trouble-shooting this issue if I can reproduce it. Sorry I can't be of more help at the moment.

---

### Post by mofrikaantje on 2009-05-31
MonkeeSage, thanks a lot for this great Howto, finally got Festival to work with additional voices! One problem though, as already mentioned above: I can't seem to find the Festvox-wrappings for the Dutch voices from Mbrola. They haven't been found, have they?

---

### Post by tjbk_tjb on 2009-05-31
> **mrplow said:**
> is there a way to find out what festival is passing on to sox as to why its trying to use -- w with sox

I found that the -w is a deprecated argument used to indicate that 16 bits or 2 bytes are used per sample. This has been changed to -2 in current versions of sox. The places where this needs to be replaced are in the files:```
/usr/share/festival/voices/us/cmu_us_kal_com_hts/hts/htsvoice.pl
/usr/share/festival/voices/us/cstr_us_ked_timit_hts/hts/htsvoice.pl
```
In both of these files, the line:```

system("sox -r $SAMPRATE -t raw -s -c 1 -w $WORKDIR/tmp.raw $OUTWAVE");
```
needs to be replaced with:```

system("sox -r $SAMPRATE -t raw -s -c 1 -2 $WORKDIR/tmp.raw $OUTWAVE");
```

---

### Post by greywire on 2009-07-02
Is it just me or do these voices still all sound pretty bad?  Only a little better and still quite robotic.

What about the Unit Selection and HMM voices in the demo: [http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html](http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html)?  Now those sound really good!  Where can I get something like that?

---

### Post by Repgahroll on 2009-07-15
> **greywire said:**
> Is it just me or do these voices still all sound pretty bad?  Only a little better and still quite robotic.

What about the Unit Selection and HMM voices in the demo: [http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html](http://www.cstr.ed.ac.uk/projects/festival/onlinedemo.html)?  Now those sound really good!  Where can I get something like that?

Yes man! I installed all the voices (including the ~100MB ones) and there are no voices that sounds like the ones in the demo page.

I want to have that quality shown in the demo page!!!

---

### Post by emnaki on 2009-07-17
From what I understand from the group which makes the voice. They have a venture called Cepstral which has a product that is an improved version of the free voices. Perhaps the demo uses Cepstral voices.

---

### Post by pickarooney on 2009-08-23
> **mofrikaantje said:**
> MonkeeSage, thanks a lot for this great Howto, finally got Festival to work with additional voices! One problem though, as already mentioned above: I can't seem to find the Festvox-wrappings for the Dutch voices from Mbrola. They haven't been found, have they?

I'm having the same problem with the French ones. Has anyone got a link to festvox SCM files for non-English voices?

---

### Post by celtica96 on 2009-08-26
[SIZE=2]@MonkeeSage[/SIZE]
 
[SIZE=2]Thanks for starting this thread.[/SIZE]
 
[SIZE=2]I have gotten Flite to run on two ARM-based MIDs, the SmartQ 7 and SmartQ 5, despite being an Ubuntu/Linux newbie.[/SIZE]
 
[SIZE=2]I thought I would try to get Festival loaded on the Q5 MID so I could move beyond the limitations of Flite (e.g., lack of multiple voices).[/SIZE]
 
[SIZE=2]My Festival install involved using GDebi to open two downloaded packages (libestools1.2_1.2.96~beta-2.arm.deb then festival_1.96~beta-7ubuntu1_arm.deb) from the hasty repository at handhelds.org. (This is similar to how I got Flite to install.)[/SIZE]
 
[SIZE=2]When I enter "festival" at the $ prompt in the evilte terminal program I get errors relating to /lib/libc.s0.6 and the following versions not being found: GLIBC_2.3, GLIBC_2.1, GLIBC_2.1.3, and GLIBC_2.0.[/SIZE]
 
[SIZE=2]Because of the age of Festival, I assume these are older C libraries that have been superseded.[/SIZE]
 
[SIZE=2]All the C libraries seem up to date with the Hasty version of Ubuntu on the Q5 MID. I cannot locate the older GLIBC packages.[/SIZE]
 
[SIZE=2]I thought I would go back to basics when I came across your thread here.[/SIZE]
 
[SIZE=2]When I try your commands in evilte:[/SIZE]
 
[SIZE=2]"sudo apt-get install festival festlex-cmu festlex-poslex festlex-oald libestools1.2 unzip"[/SIZE]
 
[SIZE=2]I get notification that "festival is already the newest version." [/SIZE]
 
[SIZE=2]Also, I get this error message: "Package festlex-cmu is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source." [/SIZE]
 
[SIZE=2]When I modify the evilte commands to try each of the other festlex packages in isolation, I get the same error message indicating that the festlex files are not available.[/SIZE]
 
[SIZE=2]In short, I have gotten Festival to install but it won't run and the other voices don't seem to be available.[/SIZE]
 
[SIZE=2]Can you help with these issues? :confused:[/SIZE]
 
[SIZE=2]Thanks in advance.[/SIZE]

---

### Post by chrost2007 on 2009-08-26
MonkeeSage thanks a mill!
I'm running Intrepid amd64, so I had to download the relevant version

[ftp://ftp.si.debian.org/debian/pool/non-free/m/mbrola/mbrola_3.01h-2_amd64.deb](ftp://ftp.si.debian.org/debian/pool/non-free/m/mbrola/mbrola_3.01h-2_amd64.deb)

installation went smoothly, though I get this error when I try to test voices in festival:

> festival> (voice_us2_mbrola)      
us2_mbrola
festival> (SayText "Good morning")
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:590: audio open error: Device or resource busy
#<Utterance 0x7fb7962f2d50>
festival> 

any ideas?

---

### Post by chrost2007 on 2009-08-26
it was the Firefox that was occupying the sound. closed Firefox and it works.
any ideas how to make it work with Firefox running?

regards,
T

---

### Post by mikeym on 2009-08-29
OK try this on for size! It's my hatchet job to get the functionality I used to get from my Mac where a key combination would speak any text that was highlighted on screen.

First of you need the small command line utility *xsel* and unicode converter *uni2ascii* and command line browser *Lynx*:

```
sudo apt-get install xsel uni2ascii lynx
```

Then copy this script to your computer and save it as *speak*

*speak*
```
#!/bin/bash
# Read highlighted text on screen

# convert text into usable ascii text (if anyone has a better way of 
# doing this which produces text which can be read by festival please let me know)
ascii() 
{
echo "<html><body>" > /tmp/convert.htm
cat | uni2ascii -a Q -a D 2> /dev/null >> /tmp/convert.htm
echo "</html></body>" >> /tmp/convert.htm
cat /tmp/convert.htm | lynx -stdin -dump
rm /tmp/convert.htm
}

#Stop running instance if found then exit

pidfile=/tmp/speak.pid
if [ -e $pidfile ]; then
	pid=`cat $pidfile`
	if kill -0 $pid 2> /dev/null; then
		echo "Already running...Killing process"
		# Ramble on kill
		# kill $pid 2> /dev/null
		# Stop at end of sentence kill
		for i in `ps -ef| awk '$3 == '${pid}' { print $2 }'`; do
			kill $i
		done
		exit 0
	else
		rm $pidfile
	fi
fi
 
# Otherwise speak selected text
xsel -o | ascii | festival --tts 2> /dev/null & pid=$! 
echo $pid > $pidfile
wait $pid 2> /dev/null

rm $pidfile

```

Save the file *speak* then make it executable and copy it to the path.

```

chmod +x speak 
sudo mv speak /usr/local/bin/

```

You can test it from the terminal now by running *speak*. Then setup a keyboard shortcut key to run speak. 

If you're running **Ubuntu _without_ visual effects (no compiz)** run *gconf-editor* and open */apps/metacity/global_keybindings* and set the first available *run_command*, normally *run_command_1* to your shortcut. I use *<Super>F2*. Now set the command under */apps/metacity/keybinding_commands* and which ever command number you used (i.e. *command_1*) and put in the command */usr/local/bin/speak*. 

If you're running **Ubuntu _with_ visual effects (compiz)** run *ccsm* (you may have to install it first). Then under *General>Commands* set *command line 0* (or the 1st available) to */usr/local/bin/speak* and then set your keybinding (I use *<Super>F2*).

The quick kill that I've defaulted to I think leaves some files lying around in the */tmp* directory but I don't think this is too much of a problem as they'll just be wiped the next time you restart and wont take up much space. The other way allows festival to close down its speech process and it just keeps wittering on until it can be arsed to close it down.

---

### Post by Roughnet13888 on 2009-09-29
These codes and tips are useful. TY for them.
[right][[color=#FFFFFF]_Simple interest calculator calculation rates mortgage compound high interest savings account_](http://simpleinterestcalculator.org)[/color][/right]

---

### Post by sainikudu on 2009-12-07
Hey great post. Thanks very much . The post seems to be very much helpful.
 
 
[COLOR=#000000][FONT=arial]__________________
[http://interestratescalculator.net]([URL="http://interestratescalculator.net/")]_Interest Rates Calculator_[/url][/FONT][/COLOR]

---

### Post by davidlarg on 2009-12-07
This post has made Ubuntu an OS that I will use more now.  

The info on getting the highlighted text to be spoken is something that I have been looking for.  Now I will use windows less.

Thank you
:p

---

### Post by XinulTar on 2010-01-05
Nice tutorial. Thanks! :D

I do have a problem though - the CMU arctic voices do play (I'm testing the SLT and CLB voices), but they sound really choppy (not robotic, just *really *choppy). But the demos for those voices from the CSTR website are really smooth.

Does anyone know why this might be a problem?

I've complied it using GCC4 as 64 bit, on Fedora. But I did otherwise follow these instructions.

Thanks

---

### Post by shane2peru on 2010-02-03
Great how to guide!!!  Very informative, well written.  Thanks.

---

### Post by Rodney9 on 2010-03-05
Brilliant, Thank You MonkeeSage.

This should be in Ubuntu ( and all Linux OS ) as default for people with sight problems.

Rodney

---

### Post by go_beep_yourself on 2010-03-18
Does this work with espeak as well or do you know of a similar guide?

---

### Post by durand on 2010-03-22
Thanks, this guide work perfectly on Ubuntu Lucid.

---

### Post by hansum_rahul on 2010-06-14
Thank you!

Just to mention: the /etc/festival.scm did not exist on my system, instead I modified this:

/usr/share/festival/festival.scm

On a Hardy

---

### Post by socratesfoot on 2010-07-05
I could not get the default voice to work in the festival.scm. To set the default voice I edited the init.scm. 
If you're looking to automate the process of setting the default voice. I used the "sed" command.

```


sudo cp /usr/share/festival/init.scm /usr/share/festival/init.scm.backup
sudo sed 's/(eval(list voice_default))/(eval (list voice_nitech_us_slt_arctic_hts))/' init.scm > tmp_file
sudo mv tmp_file init.scm


```

---

### Post by socratesfoot on 2010-07-05
Sorry, to double post but I was thinking about it and it's probably better to just post the whole thing from my history, since the Festival configuration files are in a slightly different location with Ubuntu 10.

*Note, I only wanted the "Female English" voice, so that's all this installed. These voice files are huge and I didn't see any reason to put them all on.*

```

sudo apt-get install festlex-poslex festival festlex-cmu
sudo cd /usr/share/festival/voices/english
sudo mkdir hts_tmp
cd hts_tmp/
sudo wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_slt_arctic_hts-2.1.tar.bz2
sudo wget -c http://hts.sp.nitech.ac.jp/archives/1.1.1/cmu_us_kal_com_hts.tar.gz
sudo wget -c http://hts.sp.nitech.ac.jp/archives/1.1.1/cstr_us_ked_timit_hts.tar.gz
for t in `ls` ; do sudo tar xvf $t ; done
sudo rm festvox_nitech_us_slt_arctic_hts-2.1.tar.bz2 cmu_us_kal_com_hts.tar.gz cstr_us_ked_timit_hts.tar.gz
sudo mkdir -p /usr/share/festival/voices/us
sudo mv lib/voices/us/* /usr/share/festival/voices/us/
sudo mv lib/hts.scm /usr/share/festival/hts.scm
cd ..
sudo rm -rf hts_tmp/
sudo cp /usr/share/festival/init.scm /usr/share/festival/init.scm.backup
sudo sed 's/(eval(list voice_default))/(eval (list voice_nitech_us_slt_arctic_hts))/' init.scm > tmp_file
sudo mv tmp_file init.scm


```

---

### Post by Hendrixski on 2010-07-18
Tried the script... after fixing a few errors (e.g. there is no "sudo cd"... and you have to create tmp_file with adequate permissions before sudo sed can use it)

Whenever I try to play a sound I get this crap:

```

festival> (voice_cstr_us_ked_timit_hts)    
cstr_us_ked_timit_hts
festival> (SayText "hello, this is a test")
Segmentation fault
Cannot open file /tmp/est_18045_00001/utt.wav as tokenstream
Wave load: can't open file "/tmp/est_18045_00001/utt.wav"
Cannot load wavefile: /tmp/est_18045_00001/utt.wav
#<Utterance 0xb6b35868>
festival> 

```

What's wrong?

Is there a PPA for these as a package? (because I haven't done so much work to install something since I used Windows.. .this is NOT the experience I expect from Ubuntu)

---

### Post by VV Cephei on 2010-10-11
Sweet. This is exactly what I was looking for. Thanks!

I am having a weird problem with festival, though. I haven't seen anything on the internet, so I thought I'd start here:

If I feed festival a file, either with 
     cat testfile | esddsp festival --tts
or by first opening festival and using:
     (tts_file "testfile")

It seems to divide the file into a bunch of strings delimited by newlines or punctuation, and then says all the strings _at the same time_. However, if I use:
     (SayText "reset    
> john-laptop pulseaudio: ratelimit.c:  events suppressed
> john-laptop kernel:  lo: Disabled Privacy Extensions
> john-laptop kernel:  lo: Disabled Privacy Extensions
> 08:33:20 AM
> john-laptop pulseaudio: ratelimit.c:  events suppressed
> john-laptop pulseaudio: ratelimit.c:  events suppressed")

then it works just fine. To be clear, the last command works perfectly, but the previous two result in festival saying everything in the file simultaneously. Anyone else have this problem?

---

### Post by jambel on 2010-10-16
Nitech HTS voices doesn't seem to work any more on Ubuntu 10.10 and festival 2.0.95 from ubuntu repos.

After these instructions:

```

mkdir hts_tmp
cd hts_tmp/
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_awb_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_awb_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_bdl_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_bdl_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_clb_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_clb_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_rms_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_rms_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_slt_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_slt_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_jmk_arctic_hts-2.1.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_jmk_arctic_hts-2.1.tar.bz2)
wget -c [http://hts.sp.nitech.ac.jp/archives/1.1.1/cmu_us_kal_com_hts.tar.gz](http://hts.sp.nitech.ac.jp/archives/1.1.1/cmu_us_kal_com_hts.tar.gz)
wget -c [http://hts.sp.nitech.ac.jp/archives/1.1.1/cstr_us_ked_timit_hts.tar.gz](http://hts.sp.nitech.ac.jp/archives/1.1.1/cstr_us_ked_timit_hts.tar.gz)
**[SIZE=3][COLOR=#a6926b]Unpacking the voices[/COLOR][/SIZE]**

Next we'll unpack the voices:


Code:for t in `ls` ; do tar xvf $t ; done
**[SIZE=3][COLOR=#a6926b]Installing the voices[/COLOR][/SIZE]**

Now we can install the voices:

sudo mkdir -p /usr/share/festival/voices/us
sudo mv lib/voices/us/* /usr/share/festival/voices/us/
sudo mv lib/hts.scm /usr/share/festival/hts.scm
```and set this voice [FONT=Courier New](set! voice_default 'voice_nitech_us_slt_arctic_hts)[/FONT] as default on /etc/festival.scm I face that error...

** Error: HTS_Model_load_pdf: Failed to load header of pdfs.**

Any ideas to refresh the instructions of this topic?

Cheers,

John.

---

### Post by digitaltoast on 2010-10-18
> **jambel said:**
> http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_awb_arctic_hts-2.1.tar.bz2

** Error: HTS_Model_load_pdf: Failed to load header of pdfs.**


I had this same problem - until I found a post that suggested that it's because festival 2.095 requires HTS 2.1.1 voices, which can be found here:
[http://hts.sp.nitech.ac.jp/archives/2.1.1/](http://hts.sp.nitech.ac.jp/archives/2.1.1/)

But it's not straightforward! The whole Festival system seems to be designed to be complicated and keep non-geeks out!

Want to try the 2.1.1 voices? You need to do this:

```
* Installation of HTS-demo_CMU-ARCTIC-SLT
==========================================

1. HTS-demo_CMU-ARCTIC-SLT requires Festival, SPTK-3.3, HTS-2.1.1, hts_engine API-1.03, and OpenFst-1.1.
   Please install them before running this demo.
   You can download them from the following websites:

   Festival: http://www.cstr.ed.ac.uk/projects/festival/
   SPTK: http://sp-tk.sourceforge.net/
   HTS: http://hts.sp.nitech.ac.jp/
   hts_engine API: http://hts-engine.sourceforge.net/
   OpenFst: http://www.openfst.org/

   In HTS-demo_CMU-ARCTIC-SLT, a simple F0 extraction script written in Tcl/Tk is included.
   This script calls get_f0 function implemented in the open-source speech toolkit Snack.
   Therefore, HTS-demo_CMU-ARCTIC-SLT also requires Tcl/Tk with Snack.
   ActiveState (http://www.activestate.com/) provides a Tcl/Tk distribution named ActiveTcl
   for many platforms.  You can download it from

   ActiveTcl: http://downloads.activestate.com/ActiveTcl/

   The above distribution includes Snack and it is easy to install and use.
   We recommend you to use this to run this demonstration
   (Of course you can use your own tcl/tk with Snack).
   Note that ActiveTcl 8.5 doesn't include Snack, please use ActiveTcl 8.4.


2. Setup HTS-demo_CMU-ARCTIC-SLT by running configure script:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % ./configure --with-tcl-search-path=/usr/local/ActiveTcl/bin \
                 --with-fest-search-path=/usr/local/festival/examples \
                 --with-sptk-search-path=/usr/local/SPTK-3.3/bin \
                 --with-hts-search-path=/usr/local/HTS-2.1.1_for_HTK-3.4.1/bin \
                 --with-hts-engine-search-path=/usr/local/hts_engine_API-1.03/bin \
                 --with-openfst-search-path=/usr/local/openfst-1.1/bin

   Please adjust the above directories for your environment.
   Note that you should specify festival/examples rather than festival/bin.

   You can change various parameters such as speech analysis conditions and model training conditions
   through ./configure arguments.  For example

   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.0              (24-th order cepstrum)
   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.42             (24-th order Mel-cepstrum)

   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=0    (12-th order LSP,     linear gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=1    (12-th order LSP,     log gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.42 LNGAIN=1    (12-th order Mel-LSP, log gain)
   % ./configure MGCORDER=12 GAMMA=3 FREQWARP=0.42 LNGAIN=1    (12-th order MGC-LSP, log gain)

   % ./configure NSTATE=7 NITER=10 WFLOOR=5   (# of HMM states=7, # of EM iterations=10, mix weight floor=5)

   Please refer to the help message for details:

   % ./configure --help


3. Start running demonstration as follows:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % make

   After composing training data, HMMs are estimated and speech waveforms are synthesized.
   **It takes about 12 to 18 hours :-)**
```

12 to 18 HOURS??? And I don't even know what I'm going to end up with. What does "DEMO" mean? Does it just say something and stop? Also, do I want 
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2)
or
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2)
?

It's not the 492Mb of each file I mind, it's the idea of spending 12-18 hours building one to find I wanted the other one!

The only manual I can find for Festival is here:
[http://www.cstr.ed.ac.uk/projects/festival/manual/](http://www.cstr.ed.ac.uk/projects/festival/manual/)
Dated 1999, for version 1.4

I sometimes feel like I've missed the basics somewhere.
Were it not for threads like [this]("http://ubuntuforums.org/showthread.php?t=677277") I'd be completely lost!

---

### Post by jambel on 2010-10-31
I still haven't make the nitech voices to work but I tried **[those]("http://sourceforge.net/projects/hts-engine/files/")** and worked fine, just their not what I prefer.

try to follow the README file and if you have any issue, nudge me!

> **digitaltoast said:**
> I had this same problem - until I found a post that suggested that it's because festival 2.095 requires HTS 2.1.1 voices, which can be found here:
[http://hts.sp.nitech.ac.jp/archives/2.1.1/](http://hts.sp.nitech.ac.jp/archives/2.1.1/)

But it's not straightforward! The whole Festival system seems to be designed to be complicated and keep non-geeks out!

Want to try the 2.1.1 voices? You need to do this:

```
* Installation of HTS-demo_CMU-ARCTIC-SLT
==========================================

1. HTS-demo_CMU-ARCTIC-SLT requires Festival, SPTK-3.3, HTS-2.1.1, hts_engine API-1.03, and OpenFst-1.1.
   Please install them before running this demo.
   You can download them from the following websites:

   Festival: http://www.cstr.ed.ac.uk/projects/festival/
   SPTK: http://sp-tk.sourceforge.net/
   HTS: http://hts.sp.nitech.ac.jp/
   hts_engine API: http://hts-engine.sourceforge.net/
   OpenFst: http://www.openfst.org/

   In HTS-demo_CMU-ARCTIC-SLT, a simple F0 extraction script written in Tcl/Tk is included.
   This script calls get_f0 function implemented in the open-source speech toolkit Snack.
   Therefore, HTS-demo_CMU-ARCTIC-SLT also requires Tcl/Tk with Snack.
   ActiveState (http://www.activestate.com/) provides a Tcl/Tk distribution named ActiveTcl
   for many platforms.  You can download it from

   ActiveTcl: http://downloads.activestate.com/ActiveTcl/

   The above distribution includes Snack and it is easy to install and use.
   We recommend you to use this to run this demonstration
   (Of course you can use your own tcl/tk with Snack).
   Note that ActiveTcl 8.5 doesn't include Snack, please use ActiveTcl 8.4.


2. Setup HTS-demo_CMU-ARCTIC-SLT by running configure script:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % ./configure --with-tcl-search-path=/usr/local/ActiveTcl/bin \
                 --with-fest-search-path=/usr/local/festival/examples \
                 --with-sptk-search-path=/usr/local/SPTK-3.3/bin \
                 --with-hts-search-path=/usr/local/HTS-2.1.1_for_HTK-3.4.1/bin \
                 --with-hts-engine-search-path=/usr/local/hts_engine_API-1.03/bin \
                 --with-openfst-search-path=/usr/local/openfst-1.1/bin

   Please adjust the above directories for your environment.
   Note that you should specify festival/examples rather than festival/bin.

   You can change various parameters such as speech analysis conditions and model training conditions
   through ./configure arguments.  For example

   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.0              (24-th order cepstrum)
   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.42             (24-th order Mel-cepstrum)

   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=0    (12-th order LSP,     linear gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=1    (12-th order LSP,     log gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.42 LNGAIN=1    (12-th order Mel-LSP, log gain)
   % ./configure MGCORDER=12 GAMMA=3 FREQWARP=0.42 LNGAIN=1    (12-th order MGC-LSP, log gain)

   % ./configure NSTATE=7 NITER=10 WFLOOR=5   (# of HMM states=7, # of EM iterations=10, mix weight floor=5)

   Please refer to the help message for details:

   % ./configure --help


3. Start running demonstration as follows:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % make

   After composing training data, HMMs are estimated and speech waveforms are synthesized.
   **It takes about 12 to 18 hours :-)**
```12 to 18 HOURS??? And I don't even know what I'm going to end up with. What does "DEMO" mean? Does it just say something and stop? Also, do I want 
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2)
or
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2)
?

It's not the 492Mb of each file I mind, it's the idea of spending 12-18 hours building one to find I wanted the other one!

The only manual I can find for Festival is here:
[http://www.cstr.ed.ac.uk/projects/festival/manual/](http://www.cstr.ed.ac.uk/projects/festival/manual/)
Dated 1999, for version 1.4

I sometimes feel like I've missed the basics somewhere.
Were it not for threads like [this]("http://ubuntuforums.org/showthread.php?t=677277") I'd be completely lost!

---

### Post by mrplow on 2010-11-04
you think 12-18 hours is bad, I'm currently compiling HTS-demo_CMU-ARCTIC-ADAPT and it's INSTALL says it should take 2-3 days! I'll let you know how it goes, I'm on 10.10 btw

---

### Post by mrplow on 2010-11-05
hmm well its already done compiling, I'm not sure how to use/install it for use with festival, I don't have time to fool around with it now though

---

### Post by sque on 2010-11-05
> **mrplow said:**
> you think 12-18 hours is bad, I'm currently compiling HTS-demo_CMU-ARCTIC-ADAPT and it's INSTALL says it should take 2-3 days! I'll let you know how it goes, I'm on 10.10 btw

Please tell us your story, after it finishes. For 50 hours of building, even saving one person from doing the same mistake, it will help a lot.

---

### Post by mrplow on 2010-11-05
oops it was still running, I noticed on top my CPU was still running at 90%, I rebooted my comp, then began to rebuild it 8 hours ago, I noticed now it appears done and the last few lines from the terminal are
```
echo "Running a training/synthesis perl script (Training.pl) in background...."
Running a training/synthesis perl script (Training.pl) in background....
/usr/bin/perl scripts/Training.pl scripts/Config.pm > log 2>&1 &
```
and my cpu is still at 90%, I'm not sure how it will notify me when its done since the make command is finished. I guess I'll just watch for my CPU to drop back to normal.

---

### Post by mrplow on 2010-11-06
damn it, computer crashed, stupid flash plugin... starting again, 24 hours cpu time wasted so far :D

---

### Post by mrplow on 2010-11-06
arg, 24 hours in this time and it hard locked. My computer sure doesn't like its cpu taxed %100 for long periods. 48 hours cpu time wasted so far...

---

### Post by mrplow on 2010-11-06
starting again... ](*,)

---

### Post by mrplow on 2010-11-09
arg, 50 hours in and it crashed again... over 100 hours wasted so far lol

---

### Post by digitaltoast on 2010-11-09
> **mrplow said:**
> arg, 50 hours in and it crashed again... over 100 hours wasted so far lol

Before anyone spends any more time on this, I thought I should copy an email I got from the festival mailing list this afternoon - there's a new version! And it mentions these voices. Here it is:

```
message from Alan W Black <HIDDEN@cs.cmu.edu> to festival-talk
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =

       The Festival Speech Synthesis System version 2.1
        and Edinburgh Speech Tools Library version 2.1
                       November 2010

Surprisingly we have a new release.  Please give feedback for
installation issues so they can be fixed in a 2.1 release.

Festival offers a general framework for building speech synthesis
systems as well as including examples of various modules.  As a whole
it offers full text to speech through a number APIs: from shell level,
though a Scheme command interpreter, as a C++ library, from Java, and
an Emacs interface.  Festival is multi-lingual (currently English
(British and American), and Spanish) though English is the most
advanced.  Other groups release new languages for the system.  And
full tools and documentation for build new voices are available
through Carnegie Mellon's FestVox project (http://festvox.org).  This
version also supports voices built with the latest version of Nagoya
Institute of Technologies' HTS system (http://hts.sp.nitech.ac.jp)

The system is written in C++ and uses the Edinburgh Speech Tools
Library for low level architecture and has a Scheme (SIOD) based
command interpreter for control.  Documentation is given in the FSF
texinfo format which can generate, a printed manual, info files and
HTML.

Festival is free software.  Festival and the speech tools are
distributed under an X11-type licence allowing unrestricted commercial
and non-commercial use alike.

This distribution includes:
  * Full English (British and American English) text to speech
  * Full C++ source for modules, SIOD interpreter, and Scheme library
  * Lexicon based on CMULEX and OALD (OALD is restricted to non-commercial
    use only)
  * Edinburgh Speech Tools, low level C++ library
  * rab_diphone: British English Male residual LPC, diphone
  * kal_diphone: American English Male residual LPC diphone
  * cmu_us_slt_arctic_hts: American Female, HTS
  * cmu_us_rms_cg: American Male using  clustergen
  * cmu_us_awb_cg: Scottish English Male (with US frontend) clustergen
  * Full documentation (html, postscript and GNU info format)

Note there are some licence restrictions on the voices themselves.
The US English voices have the same restrictions as Festival.

The UK lexicon (OALD) is restricted to non-commercial use.

Addition voices are also available.

Festival version 2.1 sources, voices

In Europe:
   http://www.cstr.ed.ac.uk/downloads/festival/
In North America:
   http://festvox.org/festival

Requirements

To run Festival you need:
  * A Unix-like environment, e.g Linux, FreeBSD, OSX, cygwin under Windows.
  * A C++ compiler: we have used GCC  versions. 2.x upto 4.5
  * GNU Make any recent version

New in 2.1
  * Support for the new versions of C++ that have been released
  * Integrated and updated support for HTS, Clustergen, Multisyn and Clunits
    voices
  * "Building Voices in Festival" document describing process of building
    new voices in the system
      http://festvox.org/

Alan W Black (CMU)
Rob Clark (Edinburgh)
Junichi Yamagishi (Edinburgh)
Keiichiro Oura (Nagoya)
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
=    University of Edinburgh's Festival Speech Synthesis System       =
= http://festvox.org/festival      Sent Via festival-talk@festvox.org =
=                           To unsubscribe mail majordomo@festvox.org =
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =

```

---

### Post by mrplow on 2010-11-11
well that was fun, I'm not sure how far I made it but I eventually ran into this error 70 hours into compiling
```
====================================================================================
Start synthesizing waveforms (speaker independent) at Thu Nov 11 18:38:44 PST 2010
====================================================================================

Processing directory /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0:
 Synthesizing a speech waveform from cmu_us_arctic_slt_alice01.mgc and cmu_us_arctic_slt_alice01.lf0.../usr/bin/sox: invalid option -- w
/usr/bin/sox FAIL sox: invalid option

/usr/bin/sox: SoX v14.3.1

Usage summary: [gopts] [[fopts] infile]... [fopts] outfile [effect [effopt]]...

SPECIAL FILENAMES (infile, outfile):
-                        Pipe/redirect input/output (stdin/stdout); may need -t
-d, --default-device     Use the default audio device (where available)
-n, --null               Use the `null' file handler; e.g. with synth effect
-p, --sox-pipe           Alias for `-t sox -'

SPECIAL FILENAMES (infile only):
"|program [options] ..." Pipe input from external program (where supported)
http://server/file       Use the given URL as input file (where supported)

GLOBAL OPTIONS (gopts) (can be specified at any point before the first effect):
--buffer BYTES           Set the size of all processing buffers (default 8192)
--clobber                Don't prompt to overwrite output file (default)
--combine concatenate    Concatenate all input files (default for sox, rec)
--combine sequence       Sequence all input files (default for play)
-D, --no-dither          Don't dither automatically
--effects-file FILENAME  File containing effects and options
-G, --guard              Use temporary files to guard against clipping
-h, --help               Display version number and usage information
--help-effect NAME       Show usage of effect NAME, or NAME=all for all
--help-format NAME       Show info on format NAME, or NAME=all for all
--i, --info              Behave as soxi(1)
--input-buffer BYTES     Override the input buffer size (default: as --buffer)
--no-clobber             Prompt to overwrite output file
-m, --combine mix        Mix multiple input files (instead of concatenating)
-M, --combine merge      Merge multiple input files (instead of concatenating)
--magic                  Use `magic' file-type detection
--multi-threaded         Enable parallel effects channels processing (where
                         available)
--norm                   Guard (see --guard) & normalise
--play-rate-arg ARG      Default `rate' argument for auto-resample with `play'
--plot gnuplot|octave    Generate script to plot response of filter effect
-q, --no-show-progress   Run in quiet mode; opposite of -S
--replay-gain track|album|off  Default: off (sox, rec), track (play)
-R                       Use default random numbers (same on each run of SoX)
-S, --show-progress      Display progress while processing audio data
--single-threaded        Disable parallel effects channels processing
--temp DIRECTORY         Specify the directory to use for temporary files
--version                Display version number of SoX and exit
-V[LEVEL]                Increment or set verbosity level (default 2); levels:
                           1: failure messages
                           2: warnings
                           3: details of processing
                           4-6: increasing levels of debug messages
FORMAT OPTIONS (fopts):
Input file format options need only be supplied for files that are headerless.
Output files will have the same format as the input file where possible and not
overriden by any of various means including providing output format options.

-v|--volume FACTOR       Input file volume adjustment factor (real number)
--ignore-length          Ignore input file length given in header; read to EOF
-t|--type FILETYPE       File type of audio
-s/-u/-f/-U/-A/-i/-a/-g  Encoding type=signed-integer/unsigned-integer/floating
                         point/mu-law/a-law/ima-adpcm/ms-adpcm/gsm-full-rate
-e|--encoding ENCODING   Set encoding (ENCODING in above list)
-b|--bits BITS           Encoded sample size in bits
-1/-2/-3/-4/-8           Encoded sample size in bytes
-N|--reverse-nibbles     Encoded nibble-order
-X|--reverse-bits        Encoded bit-order
--endian little|big|swap Encoded byte-order; swap means opposite to default
-L/-B/-x                 Short options for the above
-c|--channels CHANNELS   Number of channels of audio data; e.g. 2 = stereo
-r|--rate RATE           Sample rate of audio
-C|--compression FACTOR  Compression factor for output format
--add-comment TEXT       Append output file comment
--comment TEXT           Specify comment text for the output file
--comment-file FILENAME  File containing comment text for the output file
--no-glob                Don't `glob' wildcard match the following filename

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avr awb caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox w64 wav wavpcm wv wve xa xi
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: alsa

EFFECTS: allpass band bandpass bandreject bass bend biquad chorus channels compand contrast crop+ dcshift deemph delay dither divide+ earwax echo echos equalizer fade filter* fir firfit+ flanger gain highpass input# key* ladspa loudness lowpass mcompand mixer noiseprof noisered norm oops output# overdrive pad pan* phaser pitch polyphase* rabbit* rate remix repeat resample* reverb reverse riaa silence sinc spectrogram speed splice stat stats stretch swap synth tempo treble tremolo trim vad vol
  * Deprecated effect    + Experimental effect    # LibSoX-only effect
EFFECT OPTIONS (effopts): effect dependent; see --help-effect
Error in /usr/local/SPTK/bin/excite -p 80 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.pit | /usr/local/SPTK/bin/mglsadf -m 24 -p 80 -a 0.42 -c 0 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.mgc | /usr/local/SPTK/bin/x2x +fs | /usr/bin/sox -c 1 -s -w -t raw -r 16000 - -c 1 -s -w -t wav -r 16000 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.wav
```

it can probably be fixed by changing scripts/Config.pm line 248
$SOXOPTION = 'w';
but I've spent enough time and I'll wait until someone tries out that new festival and reports back

---

### Post by mrplow on 2010-11-11
oh ya the working directory ended up at 29 gigs and who knows how much further it would have grown, just FYI

---

### Post by meufel on 2011-01-14
We will develop an additional festvox voice. Therefore I had to test the Festival installation process. So far the Nitech voices are the best I came across.
Thanks for your helpful tutorial ):P

> **mrplow said:**
> 
...I've spent enough time and I'll wait until someone tries out that new festival and reports back

hi mrplow. I compiled Festival 2.1. successfully yesterday evening following the detailed instructions of every README and INSTALL text. 

But I had problems getting the Nitech voices to work due to "failed to load header of pdfs". [1] I didn't really understand the proposed solution so I was not able to solve the problem. I completely removed the files today and tried with the old repository version which worked like a charm. 

[1] [http://hts.sp.nitech.ac.jp/hts-users/spool/2010/msg00196.html](http://hts.sp.nitech.ac.jp/hts-users/spool/2010/msg00196.html)

---

### Post by meufel on 2011-01-14
sorry doublepost

---

### Post by kardon33 on 2011-02-08
Does anybody know how to use multiple -eval paramaters in the text2wave program by Festival?

I would like to set (voice_cmu_us_awb_arctic_clunits) as well as (Parameter.set 'Duration_Stretch 1.5) but I cant figure out how?

Any help?

---

### Post by redaxe on 2011-02-28
> **meufel said:**
> We will develop an additional festvox voice. Therefore I had to test the Festival installation process. So far the Nitech voices are the best I came across.
Thanks for your helpful tutorial ):P



hi mrplow. I compiled Festival 2.1. successfully yesterday evening following the detailed instructions of every README and INSTALL text. 

But I had problems getting the Nitech voices to work due to "failed to load header of pdfs". [1] I didn't really understand the proposed solution so I was not able to solve the problem. I completely removed the files today and tried with the old repository version which worked like a charm. 

[1] [http://hts.sp.nitech.ac.jp/hts-users/spool/2010/msg00196.html](http://hts.sp.nitech.ac.jp/hts-users/spool/2010/msg00196.html)

hi Ubuntu/Festival GURUs

I am new to Ubuntu/Linux and new to festival i am trying to setup festival with  Nitech voices but you all already struggled to setup those with latest version of festival 2.1. So I also decided to use festival 1.96.

for this I struggled to use apt-get install to install festival-1.96 but i don't know how to install previous version where as the current version is now 2.0.96~beta, if someone please help me in this considering me a dump on linux.


Anyway I moved to the instruction on [Post#1]("http://ubuntuforums.org/showpost.php?p=4689605&postcount=1") to build festival1.96~beta myself but when i try to debuild it (after performing all the prerequisites) i got following error on terminal.

Please someone help me to get this fixed. Thanks before hand

```
EST_wave_io.cc:74: error: invalid conversion from ‘const char*’ to ‘char*’
EST_wave_io.cc: In function ‘char* nist_get_param_str(const char*, const char*, const char*)’:
EST_wave_io.cc:90: error: invalid conversion from ‘const char*’ to ‘char*’
EST_wave_io.cc: In function ‘EST_read_status load_wave_nist(EST_TokenStream&, short int**, int*, int*, int*, int*, EST_sample_type_t*, int*, int, int)’:
EST_wave_io.cc:222: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
make[2]: *** [EST_wave_io.o] Error 1
make[1]: *** [speech_class] Error 2
make[1]: Leaving directory `/home/mubashar/fest_tmp/speech-tools-1.2.96~beta'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1319:
couldn't exec fakeroot debian/rules: 

```

---

### Post by redaxe on 2011-03-03
I am new to Festival and New to Unix/Linux envoirnment. 

I have Setup Festival 2.1 on Ubuntu 10.10 successfully with instruction given in INSTALL file. 

Then I decided to setup HTS 2.1.1 voices available at [http://hts.sp.nitech.ac.jp/?Download](http://hts.sp.nitech.ac.jp/?Download). 

Downloaded, Configure, make and make install its prerequisites and HTS-demo_CMU-ARCTIC-SLT as per instruction given in INSTALL file and [this post]("http://ubuntuforums.org/showpost.php?p=9992527&postcount=118")  

Everything gone smooth but what to do now, should I copy some files to festival folder, do i need to tell the path of HTS-demo_CMU-ARCTIC-SLT to festival somehow or to add it to Some Environment Variable.  

Please answer me with consideration that I am new to Unix/Linux environment If some one can share the detailed guidelines, I would also like to add other avialble voices in HTS 2.1.1.

---

### Post by LCamel on 2011-03-17
A workaround:

* Install VirtualBox
* Install Ubuntu 8.04.4 LTS
* Follow the instructions in the original post. It works perfectly.

---

### Post by m2xtreme on 2011-03-19
Sounds to me like I'll have to wait for festvox to release the HTS 2.1.1 voices if I want to use festival 2.0.95 beta?  Or I could figure out how to compile the voices myself... Decisions, decisions.  Also, the previous version of festival in Ubuntu's repos (<= Lucid, 1.96 beta) is from 2004 and 2.0.95 beta (>= Maverick's repos) is from 2010.  So should I...

a)  Use an outdated version of festival with better voices
b)  Use a newer version of festival with poorer quality voices
c)  Figure out how to build the voices from source

Sounds like there are enough of interested in it, I'll post back with any progress I make.  Please do the same :D

---

### Post by redaxe on 2011-03-21
> **LCamel said:**
> A workaround:

* Install VirtualBox
* Install Ubuntu 8.04.4 LTS
* Follow the instructions in the original post. It works perfectly.

Thanks for Reply, It really WORKED!!!! :)

Some other voices are not working but nitech voices are working quit fine, anyway I am looking for to control the speed of utterance is there anyway to do it????

---

### Post by dmolina87 on 2011-05-19
Hello, I want to use this scripts for training my own voices, and I have this problem:

Synthesizing a speech waveform from /home/gtc/dmolina/dmolina/hts_pruebas/ar2_michel/data/labels/gen/michelgen1.lab using hts_engine...

Error: HTS_Model_load_pdf: Failed to load header of pdfs

I would like to know how can I solve it, because I need to use this voices

Thanks

---

### Post by Sabinin on 2011-06-24
[B]SIOD ERROR: could not open file /usr/lib/festival/siod.scm
SIOD ERROR: could not open file /usr/lib/festival/siod.scm[/B]

I install festival, speech_tools, festvox (everything i need it) but i  don't know what to do in this case. Someone have any idea about it?

thanks
 		                   		  		  		  		  		  	   	
[URL="http://ubuntuforums.org/editpost.php?do=editpost&p=10972341"]
[/URL]

---

### Post by Rasa1111 on 2011-06-26
Not sure what to do there, sorry mate. 

However, Since using 11.04, i have discovered a program/app called "Gespeaker"
Its got a nice GUI, and you can choose from voices, languages, etc. 
Just type it in, and press play. 

Check out "Gespeaker" in software center.l
Pretty decent!

---

### Post by frytek on 2011-08-03
On this forum there's also a script for converting txt do speech with espeak (+ mbrola)

[http://ubuntuforums.org/showthread.php?t=1721165&highlight=speech+synthesis](http://ubuntuforums.org/showthread.php?t=1721165&highlight=speech+synthesis)

---

### Post by andreasvc on 2011-08-20
I succeeded in getting festival to work with the HTS voices on Ubuntu 11.04. I simply installed the festival package from lucid [1] and followed the procedure for installing the HTS 2.1 voices. You need one additional dependency from lucid, libestools1.2. Simply download these two packages and install the .debs manually with dpkg -i.

[1] [https://launchpad.net/ubuntu/+source/festival/1.96~beta-10ubuntu1/+build/1335123](https://launchpad.net/ubuntu/+source/festival/1.96~beta-10ubuntu1/+build/1335123)

---

### Post by gefthebest on 2011-09-30
> **redaxe said:**
> I am new to Festival and New to Unix/Linux envoirnment. 

I have Setup Festival 2.1 on Ubuntu 10.10 successfully with instruction given in INSTALL file. 



I am also looking for some help using those versions of ubuntu and Festival...

Thanks

---

### Post by Calrama on 2011-10-15
Hi,

I got one of the HTS 2.2 voices compiled, trained (arctic_slt_hts) and then working with festival 2.1. Compilation took about 8 hours, training ~30 hours. From my perspective it was worth it. I did not use Ubuntu for that, but Archlinux - no flame please -, but the produced voice should be usable on Ubuntu as well, just drop the tarball's content in /usr/share/festival/voices/us/ and you should be good to go.

You can get the tarball with the voice here:
[http://dl.dropbox.com/u/1845335/release/cmu_us_slt_arctic_hts.tar.gz](http://dl.dropbox.com/u/1845335/release/cmu_us_slt_arctic_hts.tar.gz)

And if you want to hear the difference first I let the old version (The latest prebuild one from Nitech HTS) and the new version speak the first two paragraphs of this article:
[http://en.wikinews.org/wiki/Eyewitnesses_challenge_Egyptian_state_media_impartiality_in_fatal_protests](http://en.wikinews.org/wiki/Eyewitnesses_challenge_Egyptian_state_media_impartiality_in_fatal_protests)

You can get the two mp3s here:
Old: [http://dl.dropbox.com/u/1845335/release/news_old.mp3](http://dl.dropbox.com/u/1845335/release/news_old.mp3)
New: [http://dl.dropbox.com/u/1845335/release/news_new.mp3](http://dl.dropbox.com/u/1845335/release/news_new.mp3)

Personally I think the new version sounds much smoother (It is compiled & trained with the default options).

Now what this should boil down to is, that you will most likely not need to install festival from source anymore and can just use the normal packages and still have access to the newest Nitech voices (provided you are willing to compile & train them or use the one I posted).

---

### Post by DocFreed0 on 2011-10-24
Hi [Calrama:]("http://ubuntuforums.org/member.php?u=1469971")

Nice  job.

The voice works well on Ubuntu Oneiric 11.10[SIZE=2]

To make this the default voice I did:
$ sudo gedit /usr/share/festival/voices.scm

(defvar default-voice-priority-list 
  '(;nitech_us_slt_arctic_hts    ; [Error: HTS_Model_load_pdf: Failed to load header of pdfs.]
    ;kal_diphone
    ;cmu_us_bdl_arctic_hts
    ;cmu_us_jmk_arctic_hts
    cmu_us_slt_arctic_hts    ; Custom compile 
    ;cmu_us_awb_arctic_hts
;    cstr_rpx_nina_multisyn       ; restricted license (lexicon)
;   ...

Thanks again :popcorn:
[/SIZE]

---

### Post by CHaoSlayeR on 2011-11-24
@Calrama: THX so much for investing the time & resources as well as sharing the voice with all of us! :D

To all of those, who experience the following message:
```
Error: HTS_Model_load_pdf: Failed to load header of pdfs.
```

The Debian guys already have a "fix" for this by including the old HTS engine and publishing it as a module named "hts21compat".

You can find all information in this bug: **[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614)**

So, if no appropriate bug is listed **[here](https://bugs.launchpad.net/ubuntu/+source/festival/+bugs?field.status:list=NEW)**, you probably might want to go ahead and file a bug for including that patch. This way, the available pre-trained HTS-2.1 voices would remain working while the new ones also do with the new hts_engine.

---

### Post by SwedishWings on 2011-12-02
> **CHaoSlayeR said:**
> @Calrama: THX so much for investing the time & resources as well as sharing the voice with all of us! :D

To all of those, who experience the following message:
```
Error: HTS_Model_load_pdf: Failed to load header of pdfs.
```

The Debian guys already have a "fix" for this by including the old HTS engine and publishing it as a module named "hts21compat".

You can find all information in this bug: **[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614)**

So, if no appropriate bug is listed **[here](https://bugs.launchpad.net/ubuntu/+source/festival/+bugs?field.status:list=NEW)**, you probably might want to go ahead and file a bug for including that patch. This way, the available pre-trained HTS-2.1 voices would remain working while the new ones also do with the new hts_engine.

That is good news, thanks for the heads-up.

Has anyone managed to build festival from the Debian patch? If so, a short how-to would be much appreciated! 

Thanks,
Mike

EDIT: I managed to build it myself, it goes something like this:

```
$ mkdir whatever
$ cd whatever
$ git clone git://anonscm.debian.org/tts/festival.git
$ tar cvf festival_2.1~release.orig.tar festival
$ gzip festival_2.1~release.orig.tar
$ cd festival
$ debuild
$ cd ..
$ sudo dpkg --install festival_2.1~release-2.2_i386.deb

```

That's it. You get some errors about signing in the end of the build that can be ignored.

You have to install some dependencies of course, but it was easy.

Read carefully the link above about changing the files
```
/usr/share/festival/voices/us/nitech_us_XXX_arctic_hts/festvox/nitech_us_XXX_arctic_hts.scm
```
to make it work with the backward compatibility module that was added.

Cheers,
Mike

---

### Post by mymiasma on 2012-02-18
I wasn't able to find some of the festvox files at the location in the Howto but was able to find them here:

[http://www.speech.cs.cmu.edu/festival/cstr/festival/1.4.0/](http://www.speech.cs.cmu.edu/festival/cstr/festival/1.4.0/)

Hope this helps someone out. :) Otherwise, despite it's age a very helpful article.

---

### Post by amanisdude on 2012-03-09
Wow. Spent over 40 total hours compiling this (HTS-demo_CMU-ARCTIC-SLT) over and over working out the kinks only to realize that these are **not** the same as the **Nitech voices****. =D>

At any rate, one of the errors I kept getting was the same as [mrplow]("http://ubuntuforums.org/showpost.php?p=10105369&postcount=129") (quoted below). As it turns out, SoX dropped the depreciated '-w' switch in version 14.1.0, resulting in the help text output and overall failure of 'Training.pl'. *(See [http://sox.git.sourceforge.net/git/gitweb.cgi?p=sox/sox;a=blob;f=ChangeLog;hb=6dff9411961cc8686aa75337a78b7df334606820]("http://sox.git.sourceforge.net/git/gitweb.cgi?p=sox/sox;a=blob;f=ChangeLog;hb=6dff9411961cc8686aa75337a78b7df334606820").)*

In essence, **this means that there is one more dependency that is not made known** in the 'INSTALL' ReadMe file: **SoX 14.0.1 or earlier**. (Go figure.) I suppose this could be fixed by editing the 'Config.pl' in the 'scripts' directory to use the newer '-2' switch instead of '-w' [mrplow recommends]("http://ubuntuforums.org/showpost.php?p=10105369&postcount=129"), but this is how I fixed it:
____________

First, download the source for SoX 14.0.1 (the latest version that still supports the '-w' switch):

```
cd ~/Downloads
wget -c http://sourceforge.net/projects/sox/files/sox/14.0.1/sox-14.0.1.tar.gz
```

Then, extract its contents, configure it, make it, and install it:

```
tar xvf sox-14.0.1.tar.gz
cd sox-14.0.1/
./configure
make
sudo make install
```

This should have installed the binaries to '/usr/local/bin', **BUT** SoX will fail to link to its library file 'libsox.so.0' in '/usr/local/lib'! To fix this, run:

```
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
```

(You'll have to do this every time you build the voice.) 

Now you should have the right version of SoX installed. If it still isn't using the right version of SoX, uninstall any other versions of SoX on your system *(sudo apt-get remove sox)* and make sure '/usr/local/bin' is set in the PATH variable. Heck, **I recommend you just uninstall any other versions of SoX before you begin compiling**, just in case. (It's not worth it to build for 20+ hours to run into the same error again.) Besides, you can always re-install the official Ubuntu SoX package when you're done.

You should now be able to compile HTS-demo_CMU-ARCTIC-SLT, though, as I said before, **the CMU Arctic voices are not the same as the Festvox Nitech voices** (which I find to be superior and the ones that I believe *mrplow* was really looking for). As far as I know, **there are no Nitech voices built for Festival 2.X****. *If you want to use the Nitech voices, you should probably just grit your teeth and use an older version of Festival (1.96 or sooner)***. 

Happy compiling!

**EDIT: Gaah! Shame on me for trying to write a forum post at 2 in the morning. **If you want to use the Nitech voices for Festival 2.0.96 or later, see CHaoSlayeR's post above.** (Literally, just scroll up.) You'll need to build a **compatibility patch** into Festival. For information on how to do that, **see SwedishWing's post** right below it. I need some coffee.
____________

> **digitaltoast said:**
> I had this same problem - until I found a post that suggested that it's because festival 2.095 requires HTS 2.1.1 voices, which can be found here:
[http://hts.sp.nitech.ac.jp/archives/2.1.1/](http://hts.sp.nitech.ac.jp/archives/2.1.1/)

But it's not straightforward! The whole Festival system seems to be designed to be complicated and keep non-geeks out!

Want to try the 2.1.1 voices? You need to do this:

```
* Installation of HTS-demo_CMU-ARCTIC-SLT
==========================================

1. HTS-demo_CMU-ARCTIC-SLT requires Festival, SPTK-3.3, HTS-2.1.1, hts_engine API-1.03, and OpenFst-1.1.
   Please install them before running this demo.
   You can download them from the following websites:

   Festival: http://www.cstr.ed.ac.uk/projects/festival/
   SPTK: http://sp-tk.sourceforge.net/
   HTS: http://hts.sp.nitech.ac.jp/
   hts_engine API: http://hts-engine.sourceforge.net/
   OpenFst: http://www.openfst.org/

   In HTS-demo_CMU-ARCTIC-SLT, a simple F0 extraction script written in Tcl/Tk is included.
   This script calls get_f0 function implemented in the open-source speech toolkit Snack.
   Therefore, HTS-demo_CMU-ARCTIC-SLT also requires Tcl/Tk with Snack.
   ActiveState (http://www.activestate.com/) provides a Tcl/Tk distribution named ActiveTcl
   for many platforms.  You can download it from

   ActiveTcl: http://downloads.activestate.com/ActiveTcl/

   The above distribution includes Snack and it is easy to install and use.
   We recommend you to use this to run this demonstration
   (Of course you can use your own tcl/tk with Snack).
   Note that ActiveTcl 8.5 doesn't include Snack, please use ActiveTcl 8.4.


2. Setup HTS-demo_CMU-ARCTIC-SLT by running configure script:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % ./configure --with-tcl-search-path=/usr/local/ActiveTcl/bin \
                 --with-fest-search-path=/usr/local/festival/examples \
                 --with-sptk-search-path=/usr/local/SPTK-3.3/bin \
                 --with-hts-search-path=/usr/local/HTS-2.1.1_for_HTK-3.4.1/bin \
                 --with-hts-engine-search-path=/usr/local/hts_engine_API-1.03/bin \
                 --with-openfst-search-path=/usr/local/openfst-1.1/bin

   Please adjust the above directories for your environment.
   Note that you should specify festival/examples rather than festival/bin.

   You can change various parameters such as speech analysis conditions and model training conditions
   through ./configure arguments.  For example

   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.0              (24-th order cepstrum)
   % ./configure MGCORDER=24 GAMMA=0 FREQWARP=0.42             (24-th order Mel-cepstrum)

   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=0    (12-th order LSP,     linear gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.0  LNGAIN=1    (12-th order LSP,     log gain)
   % ./configure MGCORDER=12 GAMMA=1 FREQWARP=0.42 LNGAIN=1    (12-th order Mel-LSP, log gain)
   % ./configure MGCORDER=12 GAMMA=3 FREQWARP=0.42 LNGAIN=1    (12-th order MGC-LSP, log gain)

   % ./configure NSTATE=7 NITER=10 WFLOOR=5   (# of HMM states=7, # of EM iterations=10, mix weight floor=5)

   Please refer to the help message for details:

   % ./configure --help


3. Start running demonstration as follows:

   % cd HTS-demo_CMU-ARCTIC-SLT
   % make

   After composing training data, HMMs are estimated and speech waveforms are synthesized.
   **It takes about 12 to 18 hours :-)**
```

12 to 18 HOURS??? And I don't even know what I'm going to end up with. What does "DEMO" mean? Does it just say something and stop? Also, do I want 
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT.tar.bz2)
or
[http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2](http://hts.sp.nitech.ac.jp/archives/2.1.1/HTS-demo_CMU-ARCTIC-ADAPT_STRAIGHT.tar.bz2)
?

It's not the 492Mb of each file I mind, it's the idea of spending 12-18 hours building one to find I wanted the other one!

The only manual I can find for Festival is here:
[http://www.cstr.ed.ac.uk/projects/festival/manual/](http://www.cstr.ed.ac.uk/projects/festival/manual/)
Dated 1999, for version 1.4

I sometimes feel like I've missed the basics somewhere.
Were it not for threads like [this]("http://ubuntuforums.org/showthread.php?t=677277") I'd be completely lost!
> **mrplow said:**
> well that was fun, I'm not sure how far I made it but I eventually ran into this error 70 hours into compiling
```
====================================================================================
Start synthesizing waveforms (speaker independent) at Thu Nov 11 18:38:44 PST 2010
====================================================================================

Processing directory /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0:
 Synthesizing a speech waveform from cmu_us_arctic_slt_alice01.mgc and cmu_us_arctic_slt_alice01.lf0.../usr/bin/sox: invalid option -- w
/usr/bin/sox FAIL sox: invalid option

/usr/bin/sox: SoX v14.3.1

Usage summary: [gopts] [[fopts] infile]... [fopts] outfile [effect [effopt]]...

SPECIAL FILENAMES (infile, outfile):
-                        Pipe/redirect input/output (stdin/stdout); may need -t
-d, --default-device     Use the default audio device (where available)
-n, --null               Use the `null' file handler; e.g. with synth effect
-p, --sox-pipe           Alias for `-t sox -'

SPECIAL FILENAMES (infile only):
"|program [options] ..." Pipe input from external program (where supported)
http://server/file       Use the given URL as input file (where supported)

GLOBAL OPTIONS (gopts) (can be specified at any point before the first effect):
--buffer BYTES           Set the size of all processing buffers (default 8192)
--clobber                Don't prompt to overwrite output file (default)
--combine concatenate    Concatenate all input files (default for sox, rec)
--combine sequence       Sequence all input files (default for play)
-D, --no-dither          Don't dither automatically
--effects-file FILENAME  File containing effects and options
-G, --guard              Use temporary files to guard against clipping
-h, --help               Display version number and usage information
--help-effect NAME       Show usage of effect NAME, or NAME=all for all
--help-format NAME       Show info on format NAME, or NAME=all for all
--i, --info              Behave as soxi(1)
--input-buffer BYTES     Override the input buffer size (default: as --buffer)
--no-clobber             Prompt to overwrite output file
-m, --combine mix        Mix multiple input files (instead of concatenating)
-M, --combine merge      Merge multiple input files (instead of concatenating)
--magic                  Use `magic' file-type detection
--multi-threaded         Enable parallel effects channels processing (where
                         available)
--norm                   Guard (see --guard) & normalise
--play-rate-arg ARG      Default `rate' argument for auto-resample with `play'
--plot gnuplot|octave    Generate script to plot response of filter effect
-q, --no-show-progress   Run in quiet mode; opposite of -S
--replay-gain track|album|off  Default: off (sox, rec), track (play)
-R                       Use default random numbers (same on each run of SoX)
-S, --show-progress      Display progress while processing audio data
--single-threaded        Disable parallel effects channels processing
--temp DIRECTORY         Specify the directory to use for temporary files
--version                Display version number of SoX and exit
-V[LEVEL]                Increment or set verbosity level (default 2); levels:
                           1: failure messages
                           2: warnings
                           3: details of processing
                           4-6: increasing levels of debug messages
FORMAT OPTIONS (fopts):
Input file format options need only be supplied for files that are headerless.
Output files will have the same format as the input file where possible and not
overriden by any of various means including providing output format options.

-v|--volume FACTOR       Input file volume adjustment factor (real number)
--ignore-length          Ignore input file length given in header; read to EOF
-t|--type FILETYPE       File type of audio
-s/-u/-f/-U/-A/-i/-a/-g  Encoding type=signed-integer/unsigned-integer/floating
                         point/mu-law/a-law/ima-adpcm/ms-adpcm/gsm-full-rate
-e|--encoding ENCODING   Set encoding (ENCODING in above list)
-b|--bits BITS           Encoded sample size in bits
-1/-2/-3/-4/-8           Encoded sample size in bytes
-N|--reverse-nibbles     Encoded nibble-order
-X|--reverse-bits        Encoded bit-order
--endian little|big|swap Encoded byte-order; swap means opposite to default
-L/-B/-x                 Short options for the above
-c|--channels CHANNELS   Number of channels of audio data; e.g. 2 = stereo
-r|--rate RATE           Sample rate of audio
-C|--compression FACTOR  Compression factor for output format
--add-comment TEXT       Append output file comment
--comment TEXT           Specify comment text for the output file
--comment-file FILENAME  File containing comment text for the output file
--no-glob                Don't `glob' wildcard match the following filename

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avr awb caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox w64 wav wavpcm wv wve xa xi
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: alsa

EFFECTS: allpass band bandpass bandreject bass bend biquad chorus channels compand contrast crop+ dcshift deemph delay dither divide+ earwax echo echos equalizer fade filter* fir firfit+ flanger gain highpass input# key* ladspa loudness lowpass mcompand mixer noiseprof noisered norm oops output# overdrive pad pan* phaser pitch polyphase* rabbit* rate remix repeat resample* reverb reverse riaa silence sinc spectrogram speed splice stat stats stretch swap synth tempo treble tremolo trim vad vol
  * Deprecated effect    + Experimental effect    # LibSoX-only effect
EFFECT OPTIONS (effopts): effect dependent; see --help-effect
Error in /usr/local/SPTK/bin/excite -p 80 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.pit | /usr/local/SPTK/bin/mglsadf -m 24 -p 80 -a 0.42 -c 0 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.mgc | /usr/local/SPTK/bin/x2x +fs | /usr/bin/sox -c 1 -s -w -t raw -r 16000 - -c 1 -s -w -t wav -r 16000 /home/mrplow/Desktop/HTS/HTS-demo_CMU-ARCTIC-ADAPT/HTS-demo_CMU-ARCTIC-ADAPT/gen/qst001/ver1/SI/0/cmu_us_arctic_slt_alice01.wav
```

it can probably be fixed by changing scripts/Config.pm line 248
$SOXOPTION = 'w';
but I've spent enough time and I'll wait until someone tries out that new festival and reports back

---

### Post by N4RPS on 2012-03-12
Is there any way the how-to can be updated to cover how to successfully pull this off in 11.10 Oneric Ocelot?

---

### Post by gefthebest on 2012-04-18
Subscribing too (:

Ubuntu 11.10
Festival 2.1

hts_voice_cmu_us_arctic_slt-1.04

---

### Post by go_beep_yourself on 2012-05-09
Give JSpeak a try. IMHO, it's the best TTS software for Linux =D

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

### Post by stactrac on 2012-07-27
> **andreasvc said:**
> I succeeded in getting festival to work with the HTS voices on Ubuntu 11.04. I simply installed the festival package from lucid [1] and followed the procedure for installing the HTS 2.1 voices. You need one additional dependency from lucid, libestools1.2. Simply download these two packages and install the .debs manually with dpkg -i.

[1] [https://launchpad.net/ubuntu/+source/festival/1.96~beta-10ubuntu1/+build/1335123]("https://launchpad.net/ubuntu/+source/festival/1.96%7Ebeta-10ubuntu1/+build/1335123")


On 12.04 I used the old setup I did with the HTS & then downgraded Festival manually by installing these in this order. Works fine! :)

[libaudiofile0_0.2.6-8ubuntu1_i386.deb]("http://launchpadlibrarian.net/37213711/libaudiofile0_0.2.6-8ubuntu1_i386.deb")                   (80.1 KiB)                                
[festival_1.96~beta-10ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/festival/1.96%7Ebeta-10ubuntu1/+build/1335123/+files/festival_1.96%7Ebeta-10ubuntu1_i386.deb")         (865.1 KiB)

Figured this might help someone.

Stactrac : [http://societystacktrace.com](http://societystacktrace.com)

---

### Post by needhelpwithfestival on 2013-01-12
Hello People!

I have a really urgent question!
But first, the Background of the story.
At the aprenticeship school we have to do IT projects and write adocumentation about what we did.

My Project-Part is Asterisk and it runs very well.
But it looks a little scant in the documentation although I have 26 instead of the requested 15 Pages. 
So I decided to make a TTS with festival.
A script will detect if there is any mail for the "admini" user (Mail Program is Postfix), wich come from the nagios.
So the basic order of events is: 
checkmail.sh -> notification_text.sh    ->  originate.sh
checks mail      makes TTS with text2wave    originates the phonecall
(i know there is a easier way, but i choose this one^^)

It already ran on Tuesday, but unfortunately I decided to change the voice. I installed a voice completly wrong (wrong directory, etc.), but that was not the problem because the TTS still worked with the standard voice.

But then I used a line in the tutorial that sets the installed voice to default voice.. I can't remember the exact line, but it writes the lines into the /etc/festival.scm
(! set somethingsomethingsomething...

Since then not even the default voice worked anymore.

I purged the festival installation and deleted the festival.scm in /etc, restarted the server but nothing worked to get my TTS done.

I reeinstalled it, but still no TTS :(

Could you help me possibly?

Here the codes from the scripts.
I can't access the server on this weekend, 'cause the serve is at school and the IP is not NATed :(


mailcheck.sh
```

echo mail -u admini
if [ "No mail for admini" ]; then
        echo "Alles okay, keine Mails fuer den Admin!" | wall
else
        echo `/etc/asterisk/nagios2voip/notification_text.sh`
fi

```

notification_text.sh
```

echo `mail -u admini < /etc/asterisk/nagios2voip/mailscript | grep -A6 Nagios` | text2wave -scale 50  -o /etc/asterisk/nagios2voip/test.wav
sox test.wav -r 8000 -c 1 test.gsm
mv /etc/asterisk/nagios2voip/test.wav /var/lib/asterisk/sounds/en/test.gsm
/etc/asterisk/nagios2voip/originate.sh

```


originate.sh
```

echo calling 300! | wall
#asterisk -rvx "originate sip/200 extension 103"
asterisk -rvx "originate sip/300 extension 123"

```

I don't think that it's the scripts fault, 'cuz it worked earlier...


Thanks!

---

### Post by ramreddy502 on 2013-02-08
hello,
        i am new to tts. i have the problem with the building of speech tools. unless until festival can not build with out building speech-tools. while building  speech-tools i got the following error

../../include/../base_class/EST_TSimpleMatrix.cc:54:5: error: &#8216;memcpy&#8217; was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
In file included from /usr/include/string.h:642:0,
                 from /usr/include/c++/4.7/cstring:44,
                 from ../../include/EST_String.h:42,
                 from ../../include/EST_error.h:182,
                 from ../../include/../base_class/EST_TMatrix.cc:48,
                 from matrix_i_t.cc:50:
/usr/include/i386-linux-gnu/bits/string3.h:49:1: note: &#8216;void* memcpy(void*, const void*, size_t)&#8217; declared here, later in the translation unit
make[2]: *** [matrix_i_t.o] Error 1
make[1]: *** [inst_tmpl] Error 2
make: *** [base_class] Error 2


please help me how should i solve this problem

thanks in advance

---

### Post by ramreddy502 on 2013-02-13
hi
    i am new to edenburgh festival

i have done the building of festival in ubuntu system. in what way i should check weather it is installed correctly or not.

in the same way is also built festvox  in ubuntu system. but while checking i got 
"oss audio error: failed to open audio device dev/dsp" as an error

 please can anyone help me how to solve this output audio error.

thanks in advance

---

### Post by Ian Clark on 2013-03-02
these instructions are really old. i'm running xubuntu 12.04 and would like to know the simplest way to install these better voices for festival. thanks!

---

### Post by drysdalepete on 2013-03-04
> **ramreddy502 said:**
> hello,
        i am new to tts. i have the problem with the building of speech tools. unless until festival can not build with out building speech-tools. while building  speech-tools i got the following error

../../include/../base_class/EST_TSimpleMatrix.cc:54:5: error: ‘memcpy’ was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
In file included from /usr/include/string.h:642:0,
                 from /usr/include/c++/4.7/cstring:44,
                 from ../../include/EST_String.h:42,
                 from ../../include/EST_error.h:182,
                 from ../../include/../base_class/EST_TMatrix.cc:48,
                 from matrix_i_t.cc:50:
/usr/include/i386-linux-gnu/bits/string3.h:49:1: note: ‘void* memcpy(void*, const void*, size_t)’ declared here, later in the translation unit
make[2]: *** [matrix_i_t.o] Error 1
make[1]: *** [inst_tmpl] Error 2
make: *** [base_class] Error 2


please help me how should i solve this problem

thanks in advance

Dear fellow tts user,
 
Judging from your error message you are compiling speech-tools on >=gcc 4.7
or you are compiling on >=clang 3.0 from upstream rather than the lastest
ubuntu raring patched version.

The upstream (CMU/edinborough) version of festival 2.1 needs to be modified
to compile (it needs stricter c++ compliance).
If you look in the raring code you will see a patch unqualifiedmethods.diff in debian/patches. You will need to apply this to your upstream version to compile with
gcc 4.7 or greater. 

For compiling with clang 3.0, your upstream will need unqualifiedmethods.diff and also need templatefixes.diff applied which can be found in Debian master branch for speech tools
[http://anonscm.debian.org/gitweb/?p=tts/speech-tools.git](http://anonscm.debian.org/gitweb/?p=tts/speech-tools.git).
This patch has not yet been published in Debian or Ubuntu since so few users compile with clang.

best regards
Peter
(a Festival uploader for Debian)

---

### Post by drysdalepete on 2013-03-04
> **ramreddy502 said:**
> hi
    i am new to edenburgh festival

i have done the building of festival in ubuntu system. in what way i should check weather it is installed correctly or not.

in the same way is also built festvox  in ubuntu system. but while checking i got 
"oss audio error: failed to open audio device dev/dsp" as an error

 please can anyone help me how to solve this output audio error.

thanks in advance

Dear fellow tts user,

This also looks like an upstream version of festival. Have a look in 
debian/festival.scm in raring for an example of how sound output is set. Note
we modify the build system to build our sound support in Debian and Ubuntu.

Have you considered building and using the raring version as your starting point.
It removes some of these wrinkles and has hts21 compatibility (if you want
nitech voices which seem surprisingly popular in this forum N.B.- alter the nitech voices as described in the Debian README which comes with the raring version.)

best regards,
Peter
(a Festival uploader for Debian)

---

### Post by nstrikos on 2013-03-24
I have created a simple GUI for the festival and the flite systems.

[http://sourceforge.net/projects/o-milo/](http://sourceforge.net/projects/o-milo/)

You can also use it to install more cmu voices.

---

### Post by totem6678 on 2013-04-22
I am relatively new to linux, and I was trying to use the nitech hts voices with festival 2.1. I read on previous threads that there was a patch out for debian. However, when I am compiling the files, I get an error that the variable **pulse_supported** is not declared in the scope. I was looking over the .diff files, and it is in the file **pulseaudiosupport.diff**. 

(**EDIT**: So i emailed the people who made the patch, and you need to compile speech-tools prior to compiling the festival patch. The git repo is [FONT=arial]git://[/FONT][anonscm.debian.org/tts/speech-tools.git]("http://anonscm.debian.org/tts/speech-tools.git") . They have since updated the festival patch to reflect this dependency.)


**Here are the commands I ran to build:**

```
$ mkdir whatever
$ cd whatever
$ git clone git://[anonscm.debian.org/tts/festival.git]("http://anonscm.debian.org/tts/festival.git")
$ tar cvf festival_2.1~release.orig.tar festival
$ gzip festival_2.1~release.orig.tar
$ cd festival
$ debuild
```



**Here is the error message I am getting:**
```
[FONT=arial]g++ -c   -g -O3 -fPIC  -Wall -Wno-non-template-friend           -I../../../src/include -I/usr/lib/speech_tools/include      -DINSTANTIATE_TEMPLATES -DFTNAME='Festival Speech Synthesis System' -DFTVERSION='2.1' -DFTSTATE='release'  -DFTDATE='November 2010' -DFTOSTYPEC='unknown_DebianGNULinux' festival.cc[/FONT]
[FONT=arial]festival.cc: In function &#8216;void festival_lisp_vars()&#8217;:[/FONT]
[FONT=arial]festival.cc:345:9: error: &#8216;pulse_supported&#8217; was not declared in this scope[/FONT]
[FONT=arial]make[5]: *** [festival.o] Error 1[/FONT]
[FONT=arial]make[4]: *** [festival] Error 2[/FONT]
[FONT=arial]make[3]: *** [arch] Error 2[/FONT]
[FONT=arial]make[2]: *** [src] Error 2[/FONT]
[FONT=arial]make[2]: Leaving directory `/home/pi/festival_tmp2/festival'[/FONT]
[FONT=arial]make[1]: *** [override_dh_auto_build] Error 2[/FONT]
[FONT=arial]make[1]: Leaving directory `/home/pi/festival_tmp2/festival'[/FONT]
[FONT=arial]make: *** [build] Error 2[/FONT]
[FONT=arial]dpkg-buildpackage: error: debian/rules build gave error exit status 2[/FONT]
[FONT=arial]debuild: fatal error at line 1357:[/FONT]
[FONT=arial]dpkg-buildpackage -rfakeroot -D -us -uc failed[/FONT]
```[FONT=arial]


[/FONT]

---

### Post by marsanyi on 2013-09-13
> **Calrama said:**
> Hi,

I got one of the HTS 2.2 voices compiled, trained (arctic_slt_hts) and then working with festival 2.1. Compilation took about 8 hours, training ~30 hours. From my perspective it was worth it. I did not use Ubuntu for that, but Archlinux - no flame please -, but the produced voice should be usable on Ubuntu as well, just drop the tarball's content in /usr/share/festival/voices/us/ and you should be good to go.
...


Works as advertised on 12.04LTS.  Thanks very much for making this available.

---

### Post by marsanyi on 2013-09-13
Used calrama's pre-compiled voice files from post at [http://ubuntuforums.org/showthread.php?t=751169&p=11347639#post11347639;](http://ubuntuforums.org/showthread.php?t=751169&p=11347639#post11347639;) downloaded tarball, un-tar'd, sudo mv'd to /usr/share/festival/voices/us.  Comes right up, sounds good.

---

### Post by West_Slope on 2013-09-25
> **nstrikos said:**
> I have created a simple GUI for the festival and the flite systems.

[http://sourceforge.net/projects/o-milo/](http://sourceforge.net/projects/o-milo/)

You can also use it to install more cmu voices.

Will there be any updates to this? All looks good, but no volume control.
Thanks

---

### Post by fifise on 2013-12-10
> **marsanyi said:**
> Used calrama's pre-compiled voice files from post at [http://ubuntuforums.org/showthread.php?t=751169&p=11347639#post11347639;](http://ubuntuforums.org/showthread.php?t=751169&p=11347639#post11347639;) downloaded tarball, un-tar'd, sudo mv'd to /usr/share/festival/voices/us.  Comes right up, sounds good.

Hello If some are interested, there is a easy way to make the [COLOR=#000000] nitech hts voices with festival 2.1.
 
After some research I found that a patch has been added to the release of festival 2.1 at least in [/COLOR]festival_2.1~release-6 (that the one iam using), but for the [COLOR=#000000] nitech hts voices with festival 2.1[/COLOR]~release-6, you have to modify a fle in each subdirectory of the voice file : for exemple for the voice "nitech_us_awb_arctic_hts" you have to edit the file /usr/share/festival/voices/us/nitech_us_awb_arctic_hts/festvox/nitech_us_awb_arctic_hts.scm (if your voice are in /usr/share/festival/voices/us as describe in a tutorial).

In this file you have to replace :

  the line 
[COLOR=#000000](require 'hts)[/COLOR]

 with:

  (require 'hts21compat)



and the line:

  (Parameter.set 'Synth_Method 'HTS)

must be replaced with:

  (Parameter.set 'Synth_Method 'HTS21)
For more detail look at : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614) message [Message #20]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589614#20")

I work for me on rasbian package, but it should work as well on unbuntu.
Hope this can help someone

---

### Post by billd-p on 2013-12-21
i think this was a great guide and i plan on using it to hopefully read me books

---

### Post by roger35 on 2014-07-03
Hi,

Ubuntu with 'L' plates here.

I've found a voice I like at Festival : [http://www.cstr.ed.ac.uk/projects/festival/morevoices.html](http://www.cstr.ed.ac.uk/projects/festival/morevoices.html)

The voice I am interested in using is the Christine HTS 2011 English RP female.

I cannot figure out which version of Festival I require to use this voice.

Refering to this page, where I am interested in the TTS server :  [https://github.com/InformationIntegrationGroup/festival-text-to-speech-service](https://github.com/InformationIntegrationGroup/festival-text-to-speech-service)

It says that there is only one HTS voice that works with Festival 2.1 - is this still the case ? If so which voice is that please ?

And finally has anyone else got that server I linked to up and running okay ?

Many thanks !

---

### Post by bobmounger on 2014-08-30
I was working through this tutorial & got almost everything working, but  cannot get text2wave working.

$ text2wave -mode singing america1.xml -o america1.wav
SIOD ERROR: wrong type of argument to get_c_val 

This is the festival example file. I did the install exactly as MonkeeSage showed.
Does anyone have an idea what I am doing wrong?

---

### Post by bobmounger on 2014-08-31
workaround:
[http://linuxsagas.digitaleagle.net/2013/09/15/synthesizing-an-accapella-song-with-festival-speech-synthesis/](http://linuxsagas.digitaleagle.net/2013/09/15/synthesizing-an-accapella-song-with-festival-speech-synthesis/)

---

### Post by chovy2 on 2014-12-28
MBROLA instructions don't work anymore

---

### Post by wayward4now on 2015-01-11
> **chovy2 said:**
> MBROLA instructions don't work anymore

I would really like to see a workup fixing that 
"Error: HTS_Model_load_pdf: Failed to load header of pdfs." error resolved. That last thing I want is "man-talk" by my computer! <grins> :) Ric

---

### Post by wayward4now on 2015-01-11
p/s Thanks for sticking with this thread for five years! I'm impressed! :) Ric

---

### Post by wayward4now on 2015-01-11
I'm blubbering a heartfelt THANKS!! It works! She is not the Honey West I had hoped for, but she sounds better than Madonna.

---

### Post by apurva2 on 2015-09-14
hey guyzz plz help me ...in my /usr/share/festival/voices/english....i hv kal_diphone folder which is english male voice bt nw i want to change english male voice to female voice so ..i downloded " cmu_us_clb_arctic-0.95-release.tar.gz ...then followed following step ...
cd /usr/share/festival/voices/english/
sudo tar jxf cmu_us_clb_arctic-0.95-release.tar.bz2 
sudo ln -s cmu_us_clb_arctic cmu_us_clb_arctic_clunits
sudo cp /etc/festival.scm /etc/festival.scm.backup
sudo echo "(set! voice_default 'voice_cmu_us_clb_arctic_clunits)" >> /etc/festival.scm

error is bash : /etc/festival.scm : permission denied...
so i used following cmd = 
gksu gedit /etc/festival.scm

after that /etc/festival.scm file is opened and then at the end of file i typed (set! voice_default 'voice_cmu_us_clb_arctic_clunits) and then i saved it
after that i typed festival on terminal it has given following error :
SIOD ERROR: unbound variable : f2b_f0_lr_start
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


so i again opened /etc/festival.scm and removed that  
(set! voice_default 'voice_cmu_us_clb_arctic_clunits)
and then it strted to work...so plz tell me how to change voice from male to female...

---

### Post by Graham_Toal on 2015-10-11
[COLOR=#111111][FONT=Ubuntu]There's a commented-out line in /usr/share/festival/voices/english/cmu_us_awb_arctic_clunits/festvox/cmu_us_awb_arctic_f0model.scm:[/FONT][/COLOR]
;(require 'f2bf0lr)
[COLOR=#111111][FONT=Ubuntu]just add it back in...[/FONT][/COLOR]

---

### Post by vahnskeyblade on 2015-12-30
Hi there,

I followed your instruction verbatim, and for the most part, they were successful.  Once I get to actually running it, though, and I've set one of the nitech hts voices as my default, this is what I get in response:

```
Warning: HTS_fopen: Cannot open hts/htsvoice.
aplay: main:593: bad speed value 0
aplay: main:593: bad speed value 0
nil

```

So, I don't know what to do from here.  Hopefully, this is not a hard problem to fix.  I am very new to linux and ubuntu, and am teachable as far as the terminal goes, but I don't have a lot of understanding, yet.  Most of my learning has been through Google.

---

### Post by hiddenotebook on 2016-09-11
Lets revive this great post guys I finally can install cmu voices on ubuntu 16.04 check this how to:

Make a directory to do the job:

```
mkdir myvoice  
cd myvoice  
```

Download this great and clear voice:

```
wget http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_slt_arctic-0.95-release.tar.bz2  
```

Extract it:

```
tar xf cmu_us_slt_arctic-0.95-release.tar.bz2 
```

Now move it to festival. Beware, we need to change the name here add _clunits suffix ok:

```
sudo mv cmu_us_slt_arctic /usr/share/festival/voices/english/cmu_us_slt_arctic_clunits  
```

Make it the default voice : edit festival config file add this to a new line (/etc/festival*.scm)

```
(set! voice_default 'voice_cmu_us_slt_arctic_clunits)  
```

Now start festival:

```
festival
```

Test it:

```
(SayText "Hello I am Alice. hot and nice. This is a short introduction test.")
```

Works in Ubuntu 16.04 and raspbian jessie

---

### Post by frytek on 2016-12-11
This post has nothing to do with festival. However, I'm using this thread to ask the following question: is anybody interested in trying out a virtual machine with Lubuntu and a preinstalled speech synthesis system using the Google OpenSAPI engine? If so send me a private message.

---

### Post by adzcsx2 on 2016-12-22
Thank you so much! You have saved me . I am registering for you .

---

### Post by dariodematties on 2017-02-14
Hello,

I have compiled (not installed yet):
```
Festival Speech Synthesis System 2.4:release December 2014
Copyright (C) University of Edinburgh, 1996-2010. All rights reserved.

clunits: Copyright (C) University of Edinburgh and CMU 1997-2010
clustergen_engine: Copyright (C) Carnegie Mellon University 2005-2014
hts_engine: 
The HMM-Based Speech Synthesis Engine "hts_engine API"
hts_engine API version 1.07 (http://hts-engine.sourceforge.net/)
Copyright (C) The HMM-Based Speech Synthesis Engine "hts_engine API"
Version 1.07 (http://hts-engine.sourceforge.net/)
Copyright (C) 2001-2012 Nagoya Institute of Technology
              2001-2008 Tokyo Institute of Technology
All rights reserved.

All rights reserved.
For details type `(festival_warranty)'
festival> 

```

So, I am working in my Download/festival folder on:
```
dario@dario-Lenovo-G460:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
dario@dario-Lenovo-G460:~$
```

Everything seems to be working ok.

I have the following voices available:
```
festival> (voice_
voice_cmu_us_ahw_cg              voice_cmu_us_clb_cg              voice_cmu_us_rms_cg              voice_nitech_us_bdl_arctic_hts
voice_cmu_us_aup_cg              voice_cmu_us_fem_cg              voice_cmu_us_rxr_cg              voice_nitech_us_clb_arctic_hts
voice_cmu_us_awb_arctic_clunits  voice_cmu_us_gka_cg              voice_cmu_us_slt_arctic_clunits  voice_nitech_us_jmk_arctic_hts
voice_cmu_us_awb_cg              voice_cmu_us_jmk_arctic_clunits  voice_cmu_us_slt_arctic_hts      voice_nitech_us_rms_arctic_hts
voice_cmu_us_axb_cg              voice_cmu_us_jmk_cg              voice_cmu_us_slt_cg              voice_nitech_us_slt_arctic_hts
voice_cmu_us_bdl_arctic_clunits  voice_cmu_us_kal_com_hts         voice_cstr_us_ked_timit_hts      voice_rab_diphone
voice_cmu_us_bdl_cg              voice_cmu_us_ksp_cg              voice_kal_diphone                voice_reset
voice_cmu_us_clb_arctic_clunits  voice_cmu_us_rms_arctic_clunits  voice_nitech_us_awb_arctic_hts
festival> (voice_
```

I installed enhanced CMU Arctic voices in ```
~/Download/festival/lib/voices/english/
```
I changed the name with the _clunits sufix as you suggested and they worked well.

Then, I tried to install the enhanced Nitech HTS voices.
In ```
~/Downloads
``` I typed ```
mkdir hts_tmp
``` and ```
cd hts_tmp
```
I extract (tar) the voices there.
I moved the voices ```
mv lib/voices/us/* ../festival/lib/voices/us/
```
And, I typed ```
mv lib/hts.scm ../festival/lib/hts.scm
```

Then from ```
~/Downloads/festival$
```, I lunch festival with ```
bin/festival
```

I test the voice and:

```
festival> (voice_nitech_us_awb_arctic_hts )                                                                                             nitech_us_awb_arctic_hts
festival> (SayText "It is supposed to be a wonderfull voice.")                                                                                       
Warning: HTS_fopen: Cannot open hts/htsvoice.
rateconv: failed to convert from 16000 to 0
#<Utterance 0x7fe14a787c50>
festival> 
```

What could be the problem here?

Thanks in advance

---

