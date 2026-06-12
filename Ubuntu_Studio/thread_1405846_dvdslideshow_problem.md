---
title: "dvdslideshow problem"
date: 2010-02-13
forum: Ubuntu Studio
---

### Post by ashishvalsad on 2010-02-13
Hi, 

I am trying to make a simple picture DVD slide show, without any music.
I am getting an error when dvdslideshow tries make a silent audio file
as you can see below:





[dir2slideshow] dir2slideshow version 0.8.2
[dir2slideshow] Input directory = my_pictures
[dir2slideshow] Slideshow name = Complete_example
[dir2slideshow] Output file = output/Complete_example.txt
[dir2slideshow] subtitle=
[dir2slideshow] subtitle2=
[dir2slideshow] background=
[dir2slideshow] title_background=
[dir2slideshow] title=1
[dir2slideshow] kenburns=0
[dir2slideshow] pal=0
[dir2slideshow] output_dir=output
[dir2slideshow] slide_duration=5
[dir2slideshow] sortmethod=name
[dir2slideshow] crossfade=0
[dir2slideshow] wipe=0
[dir2slideshow] title_type=title
[dir2slideshow] themefile=
[dir2slideshow] audio_list=
[dir2slideshow] Total pictures found = 4
[dir2slideshow] Total audio files found = 0
[dir2slideshow] Sorting pictures...
#########################################
background:0::black
background:1
fadein:1
title:5:Complete example
background:0::black
fadeout:1
background:2
fadein:1
/home/virtuall/public_html/dev/newvs/dvd/my_pictures/640x480_grid.jpg:5
/home/virtuall/public_html/dev/newvs/dvd/my_pictures/pano.jpg:5
/home/virtuall/public_html/dev/newvs/dvd/my_pictures/picture1.jpg:5
/home/virtuall/public_html/dev/newvs/dvd/my_pictures/picture2.jpg:5
fadeout:1
background:2
#########################################
[dir2slideshow] Done!
[dir2slideshow] Output file is output/Complete_example.txt

[dvd-slideshow]            dvd-slideshow 0.8.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2007 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] Parsing input file output/Complete_example.txt
[dvd-slideshow] ###########################################################
[dvd-slideshow] Found 4 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 3 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 4 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192k
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/default/Type1/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/default/Type1/n019004l.pfb
[dvd-slideshow] Running initial error check...
[dvd-slideshow] #######################################################
[dvd-slideshow] Total audio length = 
[dvd-slideshow] Total video length = 0:0:30.000
[dvd-slideshow] Temp dir is output/dvd-slideshow_temp_13895
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow]###########################################################
[dvd-slideshow] Title 0:0:5.000
[dvd-slideshow]         Title=Complete example
[dvd-slideshow]############################################################
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]###########################################################
[dvd-slideshow] background 0:0:2.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow]###########################################################
[dvd-slideshow] 1/4 ...v/newvs/dvd/my_pictures/640x480_grid.jpg 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] 2/4 ..._html/dev/newvs/dvd/my_pictures/pano.jpg 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] 3/4 ...l/dev/newvs/dvd/my_pictures/picture1.jpg 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] 4/4 ...l/dev/newvs/dvd/my_pictures/picture2.jpg 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]###########################################################
[dvd-slideshow] background 0:0:2.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:30.000 silence.
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:30.000
sox: invalid option -- 2
sox: invalid option -- 2
sox: bad input format for file /dev/zero: data size was not specified
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:30.000
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio...
cat: output/dvd-slideshow_temp_13895/audio1_????.raw: No such file or directory
[dvd-slideshow] ERROR during sox execution!
[dvd-slideshow] see output/test_complete.log for details
[dvd-slideshow] cleanup...



can you please guide how to solve this problem.

Thanks

---

### Post by ron999 on 2010-02-13
Hi
dvd-slideshow seems to be working OK for me.
I can make a 30 second silent slideshow from an image.
[U]Have you got **sox** installed on your computer?
[/U]
> ron@ubuntu:~$ dvd-slideshow silent.txt
[dvd-slideshow]            dvd-slideshow 0.8.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2007 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] Using default slideshow name: silent
[dvd-slideshow] Output directory not specified.
[dvd-slideshow] Using /home/ron
[dvd-slideshow] Parsing input file silent.txt
[dvd-slideshow] ##############################
[dvd-slideshow] Found 1 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 0 title slides.
[dvd-slideshow] Found 0 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192k
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Running initial error check...
[dvd-slideshow] #
[dvd-slideshow] Total audio length = 
[dvd-slideshow] Total video length = 0:0:30.000
[dvd-slideshow] Temp dir is /home/ron/dvd-slideshow_temp_3142
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] 1/1 image.jpg 0:0:30.000
[dvd-slideshow]############################################################
[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:30.000 silence.
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:30.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:30.000
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow]############################################################
[dvd-slideshow] Multiplexing audio and video...
[dvd-slideshow]############################################################
[dvd-slideshow] total chapters=1
[dvd-slideshow]############################################################
[dvd-slideshow] cleanup...




---

### Post by ashishvalsad on 2010-02-15
thank you ron999

for the kind help,

i think sox is installed,

because previously the error was "no sox found"

and now 
"ERROR during sox execution!"

so this can be other thing,

i am very much confuse what this can be?

Thanks,
Ashish.

---

### Post by ron999 on 2010-02-15
Hi
I don't know the answer Ashish.
To check whether sox is installed look in
System > Administration > Synaptic Package Manager.

---

### Post by Eric Fortuna on 2010-02-15
I'm sorry if I cannot help you with your problem. I, like you, am having some problem on my DeVeDe software. I used to create DVD movies/video through this DeVeDe sotfware but recently the program always failed with following message:

.....................................................................................................................................
You have just inserted a Video DVD. Choose what application to 
                             ERROR!!!
                     Conversion failed.
               It seems a bug of SPUMUX.
....................................................................................................................................
Please help!!! Anyone?!

---

### Post by ron999 on 2010-02-15
@ Eric Fortuna
Off topic, start your own thread.

---

