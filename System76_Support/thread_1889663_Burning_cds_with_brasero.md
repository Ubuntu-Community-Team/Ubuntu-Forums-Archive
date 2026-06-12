---
title: "Burning cds with brasero"
date: 2011-12-01
forum: System76 Support
---

### Post by solotwit on 2011-12-01
When I burn a cd or dvd using brasero it cannot be read properly by my friends windows computers. It shows as blank, doesnt play as a music cd, or video cd. Basically doesn't work at all except on my computer. Any idea why? What am I doing wrong?

---

### Post by isantop on 2011-12-02
Are you burning it as an audio or video CD, and if so, what program are you using to try and open it on Windows?

If not, make sure the disk is unreadable from Windows Explorer.

---

### Post by ussndmac on 2011-12-02
I got tired of Brasero making coasters a couple years back...loaded Gnomebaker: no more coasters.:popcorn:

---

### Post by solotwit on 2011-12-04
I just clicked on the dvd/r image and used cd/dvd creator, nothing happened. I opened brasero and selected video project, it requested dvdauthor to be installed, I said ok. Now i got this error



Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_1JI05V.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_WAI05V.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_action
BraseroVob deactivating
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_session_output_size
BraseroVob Output set (AUDIO) image = /tmp/brasero_tmp_81H05V.cdr
BraseroVob called brasero_job_get_session_output_size
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_output_type
BraseroVob Got output type (is DVD 1, is SVCD 0)
BraseroVob Creating new pipeline
BraseroVob called brasero_job_get_current_track
BraseroVob called brasero_job_get_audio_output
BraseroVob called brasero_job_tag_lookup
BraseroVob called brasero_job_tag_lookup
BraseroVob Setting ratio 4:3
BraseroVob Linked video bin to muxer == 0
BraseroVob called brasero_job_tag_lookup
BraseroVob Adding AC3 audio stream
BraseroVob Setting AC3 rate to 48000
BraseroVob Setting AC3 bitrate to 448000
BraseroVob Error while linking pads
BraseroVob can't create object : Impossible to link plugin pads 

BraseroVob stopping
Session error : Impossible to link plugin pads (brasero_burn_record brasero-burn.c:2856)

---

### Post by solotwit on 2011-12-04
So now I'm making an ISO file with devede and burning it with k3d. What is going on, it's 2011?

---

### Post by bluexrider on 2011-12-04
Yeah! me too, also used K3b because of Brasero issues

> **ussndmac said:**
> I got tired of Brasero making coasters a couple years back...loaded Gnomebaker: no more coasters.:popcorn:

---

### Post by solotwit on 2011-12-04
So I made an iso file with devede, then i burned it with k3b. Twice. Once again with brasero. (Same disc) Signs seem to indicate burning is taking place and successful but the disc is blank according to my computer. What gives?

---

### Post by BBQdave on 2011-12-05
> **solotwit said:**
> When I burn a cd or dvd using brasero it cannot be read properly by my friends windows computers. It shows as blank, doesnt play as a music cd, or video cd. Basically doesn't work at all except on my computer. Any idea why? What am I doing wrong?

As Isantop asked: What format are you burning the data in?

Short answer: Use universal file format that works on most systems.

It may be that you need to burn music in Mp3 format for Window's system to play.  Or add VLC player to Window's system to play audio format you burned with Brasero.

I have had no issue burning data cd's with Brasero, and the cd's are read by GNU/Linux, Mac and Window's machine.  And my music is Mp3's, playable on GNU/Linux, Mac and Window"s machines.

---

### Post by solotwit on 2011-12-06
I think I'm just gonna be done with discs. If they want it they can come and get it with a thumb drive or something. Thanks!

---

### Post by sfmadmax on 2011-12-07
> **solotwit said:**
> I think I'm just gonna be done with discs. If they want it they can come and get it with a thumb drive or something. Thanks!

Good Call, USB Stick == much faster :P  plus most of the modern HW support boot from USB

---

### Post by halw on 2011-12-10
I tried burning an ISO this morning with Brasero and no matter what I did I couldn't get the burn speed to 4x.Furthermore, the cd wouldn't auto-eject. Got some sort of error and had to manually eject.

What other programs are there that might work in Ubuntu Oneiric?

---

### Post by isantop on 2011-12-12
Your burner probably doesn't support burning at 4x; many of the burners we sell in systems can only go down to 8x. As for the Auto-eject issue, we are aware of it, and while the error dialog is obnoxious, it should cause any problems with the disk itself.

---

### Post by BBQdave on 2011-12-14
> **halw said:**
> I tried burning an ISO this morning with Brasero and no matter what I did I couldn't get the burn speed to 4x.Furthermore, the cd wouldn't auto-eject. Got some sort of error and had to manually eject.

What other programs are there that might work in Ubuntu Oneiric?

I have a dell inspiron 1100 (celeron 2.0GHz with 1 gig or ram).  Running **Debian6** :)  The built in cd burner is touch and go, inconsistent burns.  And I would get that annoying *eject failure message*, and have to eject disc manually.  Note that this machine is pushing a decade of use :o

I got a **Light-On** usb cd/dvd burner.  It works great.  Burns CD's and DVD's without issue and auto ejects when disc is burnt.  Not sure why this usb burner works so well, but it does.  So maybe not the ideal fix, but an inexpensive one that you can use with other machines (with usb ports) :D

---

### Post by bluesloth on 2011-12-17
> **halw said:**
> What other programs are there that might work in Ubuntu Oneiric?
Xfburn.  It's an Xfce program, but you don't need to run Xfce to use it.

I used Brasero once, but not anymore.  I already have enough coasters.

---

### Post by isantop on 2011-12-19
The success rate for a burn (in my experience), seems to have more to do with the brand of disk you use rather than the software. I've never had a failed burn in Brasero, for example, even after over a year of solid use.

---

### Post by bluesloth on 2011-12-20
> **isantop said:**
> The success rate for a burn (in my experience), seems to have more to do with the brand of disk you use rather than the software. I've never had a failed burn in Brasero, for example, even after over a year of solid use.
Ahh, ok.. that's bigger than my sample size.  Maybe I got unlucky, or got a buggy version.

---

### Post by crazy bird on 2011-12-20
To adjust the burning speed in Brasero, click on the *Properties* next to the selected drive under *Select a disc to write to*. There you can adjust the burning speed.
 
But then again which has been said here too: Breasero is prone to create unreadable disc. It's still not stable enough to compete with burning tools like Xfburn and K3B. Best is to de-install Brasero and choose a package like Xfburn or K3B. 
 
K3B is, compared to Xfburn, a burning tool with more powerful options. It can be compared with Nero burningtool.

---

### Post by BBQdave on 2011-12-20
+1  Xfburn :)

Thought I would play around with Xfburn, and it works great on my old hardware.  I have to join others in recommended Xfburn over brasero.

---

### Post by RedRat on 2011-12-26
I have had nothing but problems with Brasero. Having read threads both here and on usenet, many others have problems too. I would suggest either k3b or GnomeBaker. I have not had any problems with GnomeBaker and use it frequently. This is both on my 8.04 and 10.04 machines.

Judging from the responses and threads, it would appear that Brasero seems to be a very, very touchy program for burning CDs and DVDs. I too have made many coasters with Brasero.

---

