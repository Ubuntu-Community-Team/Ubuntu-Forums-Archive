---
title: "Burning Disks ALWAYS fails"
date: 2008-12-31
forum: Ubuntu Studio
---

### Post by Charbs on 2008-12-31
Ive tried everything and have wasted too many cd's and dvd's trying to get any type of burning working.

No matter what program I try, or what type of disk, they all refuse to burn. It looks like the burn is gonna start, but then 10 sec later it fails and ruins the disk. Opening the program as SUDO doesnt help either.

Im not sure if this has anything to do with it. But when I installed Ubuntu, I had to add the "all_generic_ide" line or the live cd wouldnt boot at all.

---

### Post by J03y on 2008-12-31
Well you could try to install it from a usb drive. Thats how i installed. I would link you a guide but this computer doesn't have a bookmarked guide on how to do it.

---

### Post by Charbs on 2008-12-31
Thanks but no can do. My bios doesnt allow boot from usb :(

This is what it says right after I start the burn.

"There was an error writing to the disc:
Error while writing to disc.  Try a lower speed."

Im going as slow as my drive will let me. 4.7x or 2x

As soon as the burn starts, it says finishing or finalizing disk.

---

### Post by J03y on 2008-12-31
> **Charbs said:**
> Thanks but no can do. My bios doesnt allow boot from usb :(

This is what it says right after I start the burn.

"There was an error writing to the disc:
Error while writing to disc.  Try a lower speed."

Im going as slow as my drive will let me. 4.7x or 2x

As soon as the burn starts, it says finishing or finalizing disk.Then you should try burning at a slower speed. Every time I tried burning Ubuntu into a cd I was never successful. I even burned Ubuntu at 1x which is the most recommended(I think I had a dirty burner or something) but no luck.

---

### Post by Charbs on 2008-12-31
Im not trying to burn the Ubuntu.iso

I already have ubuntu installed. Now i want to burn some audio cd's or video dvd's and it never works. Fails every time. And im pretty sure it has to do with installing Ubuntu with "all_generic_ide" mode. Cuz both desktops that ive had to use that mode with give the same results when burning.

---

### Post by albinootje on 2008-12-31
> **Charbs said:**
> Im not trying to burn the Ubuntu.iso

I already have ubuntu installed. Now i want to burn some audio cd's or video dvd's and it never works. Fails every time. And im pretty sure it has to do with installing Ubuntu with "all_generic_ide" mode. Cuz both desktops that ive had to use that mode with give the same results when burning.

You're using Ubuntu HH / 8.04.x ?
On my machine I had to boot with the all_generic_ide options to prevent coasters being burned. That was an annoying problem.
Some more people had the same problem, and I wonder whether that is fixed in 8.04.1 or at least mentioned somewhere.

Are you booting with or without those options right now ?

---

### Post by Charbs on 2008-12-31
Im booting WITH all_generic_ide. Otherwise ubuntu will not work on my 6 year old pc.

If i try to boot the live cd without changing anything, it just fails to boot with the BusyBox error.

---

### Post by Charbs on 2009-01-04
Here is a log of Brasero, even tho i was able to re-install Ubuntu from a USB stick and NOT use the "all_generic_ide" i still cant burn.

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_action
BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_C3MDNU.cdr
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Creating new pipeline
BraseroNormalize called brasero_job_set_current_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.006570)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.017022)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.027993)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.038921)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.049860)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.060852)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.071802)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.082667)
BraseroNormalize Setting track peak (0.537857) and gain (-1.300000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.091773)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.101133)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.110393)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.119707)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.129049)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.138417)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.147695)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.157046)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.166595)
BraseroNormalize Setting track peak (0.603896) and gain (-2.350000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.174889)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.183474)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.192067)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.200701)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.209236)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.217862)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.226398)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.234917)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.243015)
BraseroNormalize Setting track peak (0.729397) and gain (-1.320000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.251788)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.263511)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.275066)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.286688)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.298243)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.309720)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.321365)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.333099)
BraseroNormalize Setting track peak (0.654327) and gain (-2.140000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.344580)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.356383)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.368316)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.380191)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.391994)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.403844)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.415979)
BraseroNormalize Setting track peak (1.000000) and gain (-6.310000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.426285)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.436645)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.447160)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.457582)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.467952)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.478343)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.488734)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.499186)
BraseroNormalize Setting track peak (1.000000) and gain (-5.800000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.511186)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.524079)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.536882)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.549556)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.562359)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.575123)
BraseroNormalize Setting track peak (0.842495) and gain (-5.390000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.585964)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.594560)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.603148)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.611711)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.620137)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.628641)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.637169)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.645596)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.654099)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.662636)
BraseroNormalize Setting track peak (1.000000) and gain (-5.970000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.670714)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.679025)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.687384)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.695751)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.704014)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.712357)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.720684)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.728955)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.737314)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.745681)
BraseroNormalize Setting track peak (0.751015) and gain (-2.200000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.754202)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.763163)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.772133)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.781006)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.789773)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.798690)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.807580)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.816427)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.825273)
BraseroNormalize Setting track peak (1.000000) and gain (-6.190000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.833880)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.844786)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.855567)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.866505)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.877422)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.888192)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.899109)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.910026)
BraseroNormalize Setting track peak (0.602354) and gain (-1.960000)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.920447)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.930753)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.940929)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.951044)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.961038)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.971173)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.981248)
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Called brasero_job_set_progress (0.991222)
BraseroNormalize Setting track peak (1.000000) and gain (-6.730000)
BraseroNormalize Setting album peak (1.000000) and gain (-4.570000)
BraseroNormalize called brasero_job_tag_add
BraseroNormalize called brasero_job_tag_add
BraseroNormalize finished successfully session
BraseroNormalize stopping
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_7CUBNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 205740408163 / bytes = 0 36292608
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -1.300000 0.537857
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 01 - Jingle Bells.mp3 to /tmp/brasero_tmp_7CUBNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 36292608 bytes (= 36292608 ns)
=> padding 1104 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 80 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_QESCNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 241397551020 / bytes = 0 42582528
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -2.350000 0.603896
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 02 - Let It Snow.mp3 to /tmp/brasero_tmp_QESCNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 42582528 bytes (= 42582528 ns)
=> padding 432 bytes
BraseroTranscode written 432 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_005BNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 263941224489 / bytes = 0 46559232
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -1.320000 0.729397
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 03 - Christmas Song.mp3 to /tmp/brasero_tmp_005BNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 46559232 bytes (= 46559232 ns)
=> padding 960 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 448 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_LJ1KNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 194768979591 / bytes = 0 34357248
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -2.140000 0.654327
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 04 - Winter Wonderland.mp3 to /tmp/brasero_tmp_LJ1KNU.cdr
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 34357248 bytes (= 34357248 ns)
=> padding 768 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 256 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_KEYENU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 183666938775 / bytes = 0 32398848
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -6.310000 1.000000
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 05 - I'll Be Home For Christmas.mp3 to /tmp/brasero_tmp_KEYENU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 32398848 bytes (= 32398848 ns)
=> padding 2304 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 256 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_H3TPNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 211356734693 / bytes = 0 37283328
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -5.800000 1.000000
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 06 - Christmas Time Is Here.mp3 to /tmp/brasero_tmp_H3TPNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 37283328 bytes (= 37283328 ns)
=> padding 576 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 64 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_RPHBNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 169665306122 / bytes = 0 29928960
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -5.390000 0.842495
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 07 - Santa Claus Is Coming To Town.mp3 to /tmp/brasero_tmp_RPHBNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 29928960 bytes (= 29928960 ns)
=> padding 240 bytes
BraseroTranscode written 240 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_766HNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 256496326530 / bytes = 0 45245952
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -5.970000 1.000000
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 08 - Have Yourself A Merry Little Christmas.mp3 to /tmp/brasero_tmp_766HNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 45245952 bytes (= 45245952 ns)
=> padding 1824 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 288 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_BOJQNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 272117551020 / bytes = 0 48001536
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -2.200000 0.751015
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 09 - White Christmas.mp3 to /tmp/brasero_tmp_BOJQNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 48001536 bytes (= 48001536 ns)
=> padding 432 bytes
BraseroTranscode written 432 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_BXNJNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 246543673469 / bytes = 0 43490304
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -6.190000 1.000000
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 10 - What Are You Doing New Years Eve.mp3 to /tmp/brasero_tmp_BXNJNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 43490304 bytes (= 43490304 ns)
=> padding 528 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 16 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_3P4NNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 207151020408 / bytes = 0 36541440
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -1.960000 0.602354
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 11 - Sleigh Ride.mp3 to /tmp/brasero_tmp_3P4NNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 36541440 bytes (= 36541440 ns)
=> padding 1584 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 48 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_1IJNNU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 216476734693 / bytes = 0 38186496
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set -6.730000 1.000000
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/norm/Music/Diana Krall - Christmas Songs/Diana Krall - Christmas Songs - 12 - Count Your Blessings Instead Of Sheep.mp3 to /tmp/brasero_tmp_1IJNNU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 38186496 bytes (= 38186496 ns)
=> padding 576 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 64 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim stopping
Session error : Insufficient space on media (0 available for 200204) (brasero_burn_record burn.c:2524)

---

### Post by albinootje on 2009-01-04
> **Charbs said:**
> Here is a log of Brasero, even tho i was able to re-install Ubuntu from a USB stick and NOT use the "all_generic_ide" i still cant burn.

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
-- cut --
Session error : Insufficient space on media (0 available for 200204) (brasero_burn_record burn.c:2524)

In Hardy/8.04 I've found out that for my dvd-drive I really needed the all_generic_ide kernel boot parameter, otherwise I would end up having coasters all the time.

In Intrepid/8.10 I didn't need that parameter to burn successfully.

I use k3b exclusively, but that shouldn't matter here I think.

---

### Post by Charbs on 2009-01-04
Ya im pretty sure its not the applications fault. Brassero and Serpentine both fail.

Heres the output from K3b:

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4040B A104 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 1440
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-4040B'
Revision       : 'A104'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1204224 = 1176 KB
Drive DMA Speed: 11499 kB/s 65x CD 8x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 4234 KB/s
pregap1: -1
Track 01: audio   34 MB (03:25.80) no preemp swab copy
Track 02: audio   40 MB (04:01.45) no preemp swab copy
Track 03: audio   44 MB (04:24.00) no preemp swab copy
Track 04: audio   32 MB (03:14.82) no preemp swab copy
Track 05: audio   30 MB (03:03.72) no preemp swab copy
Track 06: audio   35 MB (03:31.41) no preemp swab copy
Track 07: audio   28 MB (02:49.72) no preemp swab copy
Track 08: audio   43 MB (04:16.56) no preemp swab copy
Track 09: audio   45 MB (04:32.17) no preemp swab copy
Track 10: audio   41 MB (04:06.60) no preemp swab copy
Track 11: audio   34 MB (03:27.21) no preemp swab copy
Track 12: audio   36 MB (03:36.53) no preemp swab copy
Total size:      449 MB (44:30.01) = 200251 sectors
Lout start:      449 MB (44:32/01) = 200251 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 159594
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
SAO startsec: -12508
Writing lead-in...
Lead-in write time:   21.536s
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   34 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 01 0E 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 635040 bytes
Writing  time:   35.086s
Average write speed 197.0x.
Fixating...
Fixating time:    0.007s
/usr/bin/wodim: fifo had 202 puts and 11 gets.
/usr/bin/wodim: fifo was 0 times empty and 10 times full, min fill was 99%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree textfile=/tmp/k3bzpzlQa.dat -eject -useinfo -audio /tmp/kde-norm/k3b_audio_0_01.inf /tmp/kde-norm/k3b_audio_0_02.inf /tmp/kde-norm/k3b_audio_0_03.inf /tmp/kde-norm/k3b_audio_0_04.inf /tmp/kde-norm/k3b_audio_0_05.inf /tmp/kde-norm/k3b_audio_0_06.inf /tmp/kde-norm/k3b_audio_0_07.inf /tmp/kde-norm/k3b_audio_0_08.inf /tmp/kde-norm/k3b_audio_0_09.inf /tmp/kde-norm/k3b_audio_0_10.inf /tmp/kde-norm/k3b_audio_0_11.inf /tmp/kde-norm/k3b_audio_0_12.inf

---

### Post by albinootje on 2009-01-04
> **Charbs said:**
> Ya im pretty sure its not the applications fault. Brassero and Serpentine both fail.

If you're using Hardy Heron, please try with the all_generic_ide boot option.
That has helped for me in the past, and I've decided to use it everywhere where I've installed HH/8.04.

---

### Post by Charbs on 2009-01-04
Im using 8.10 Intrepid :(

Im worried that im gonna have to go back to Windows XP if i cant figure this burning out. What good is a computer if you cant get anything off it.

---

### Post by albinootje on 2009-01-04
> **Charbs said:**
> Im using 8.10 Intrepid :(

Im worried that im gonna have to go back to Windows XP if i cant figure this burning out. What good is a computer if you cant get anything off it.

Instead of giving up on Ubuntu, and use XP, you can do the following :
1) boot with the before mentioned generic ide all parameter.
2) file a bug-report

With the 2nd option you are making the first step to make things possibly easier for people who are you using the same machine or cdrw- or dvd-drive as you.

If this is a bug, it's not likely to be fixed if noone talks about it.

Some time ago I wanted to install Ubuntu on some brand new Dell computer. 
Installation failed..
After searching I found out that the BIOS needed an upgrade before the installation cdrom would boot properly.
Without the spread knowledge from other users I could not have found that out myself, and could not have done that installation.

---

### Post by Charbs on 2009-01-04
Ya i really dont want to go back to windows either.

The all_generic_ide installation that i had previous to this usb installation gave me the same results. So it probably has nothing to do with that. Its something else that no one seems to be able to figure out.

all_generic_ide or not, burning will always fail fail fail.

---

### Post by albinootje on 2009-01-04
> **Charbs said:**
> Ya i really dont want to go back to windows either.

The all_generic_ide installation that i had previous to this usb installation gave me the same results. So it probably has nothing to do with that. Its something else that no one seems to be able to figure out.

all_generic_ide or not, burning will always fail fail fail.

Then please file a bug report at [http://launchpad.net](http://launchpad.net)

---

