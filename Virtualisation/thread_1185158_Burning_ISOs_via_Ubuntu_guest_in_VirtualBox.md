---
title: "Burning ISOs via Ubuntu guest in VirtualBox"
date: 2009-06-11
forum: Virtualisation
---

### Post by tomcat2007 on 2009-06-11
Hello, I am trying to burn an ISO from within a VirtualBox 2.2.2 Ubuntu Jaunty guest running on an XP SP2 host and running into errors.  It is my understanding that while burning audio is not yet supported, burning a bootable image from an ISO is.  Passthrough is enabled, Jaunty sees the drive as does Brasero, Brasero acts as though it will burn the image but after it finishes creating the cue sheet it errors out.

Installing a third party burner on the laptop is not an option & the built in burning support does not create images from ISOs.

Attached is a log from one such experience... is there anything helpful within this to determine what the problem may be?  Any assistance is appreciated :-)

BraseroWodim stdout: Track 01:    0 of  277 MB written.
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 02 0F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 06 00 00 00 00 0A 00 00 00 00 29 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x6 Unit Attention, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x29 Qual 0x00 (power on, reset, or bus device reset occurred) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 37.563s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of  277 MB written (fifo  99%) [buf  97%]   0.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1079296 bytes
BraseroWodim stdout: Writing  time:   71.898s
BraseroWodim stdout: Average write speed  36.8x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.077s
BraseroWodim stderr: wodim: fifo had 272 puts and 18 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: wodim: fifo was 0 times empty and 3 times full, min fill was 96%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

