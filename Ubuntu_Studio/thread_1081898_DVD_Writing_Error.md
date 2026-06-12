---
title: "DVD Writing Error"
date: 2009-02-27
forum: Ubuntu Studio
---

### Post by swapnilnarendra on 2009-02-27
Hi,
I tried to burn a DVD with Brasero and got an error in the end when it tried to burn)it checked the checksums with no issues).
This is the error log i copied.

I would appreciate any help.
Thanks in advanced.



Checking session consistency (brasero_burn_check_session_consistency burn.c:1956)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI burn:// URI found burn:///Dominion%20Prequel%20To%20The%20Exorcist.avi
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /media/Swapnil/Movies/Dominion Prequel To The Exorcist.avi at /Dominion Prequel To The Exorcist.avi
BraseroBurnURI Added file /media/Swapnil/Movies/The Exorcist - Begining.avi at /The Exorcist - Begining.avi
BraseroBurnURI Added file /media/Swapnil/Movies/The Exorcist.avi at /The Exorcist.avi
BraseroBurnURI Added file /media/Swapnil/Movies/The Exorcist II - The Heretic.avi at /The Exorcist II - The Heretic.avi
BraseroBurnURI Added file /media/Swapnil/Movies/The Exorcist III.avi at /The Exorcist III.avi
BraseroBurnURI no burn:// URI found
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_2P8XPU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=3
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_EQZ6PU
	-exclude-list
	/tmp/brasero_tmp_CUE7PU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_EQZ6PU -exclude-list /tmp/brasero_tmp_CUE7PU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Using THE_E000.AVI;1 for  /The Exorcist III.avi (The Exorcist II - The Heretic.avi)
BraseroGrowisofs stderr: Using THE_E001.AVI;1 for  /The Exorcist II - The Heretic.avi (The Exorcist - Begining.avi)
BraseroGrowisofs stderr: Using THE_E002.AVI;1 for  /The Exorcist - Begining.avi (The Exorcist.avi)
BraseroGrowisofs stderr: Total extents scheduled to be written = 1792963
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=3
	-use-the-force-luke=tracksize:1792963
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_7LM8PU
	-exclude-list
	/tmp/brasero_tmp_FKM8PU
	-V
	Data disc (27 Feb 09)
	-A
	Brasero-0.9.1
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_7LM8PU -exclude-list /tmp/brasero_tmp_FKM8PU -V Data disc (27 Feb 09) -A Brasero-0.9.1 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Using THE_E000.AVI;1 for  /The Exorcist III.avi (The Exorcist II - The Heretic.avi)
BraseroGrowisofs stderr: Using THE_E001.AVI;1 for  /The Exorcist II - The Heretic.avi (The Exorcist - Begining.avi)
BraseroGrowisofs stderr: Using THE_E002.AVI;1 for  /The Exorcist - Begining.avi (The Exorcist.avi)
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 17
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 18
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 19
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 23
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 24
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 24
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 25
BraseroGrowisofs stderr:   0.28% done, estimate finish Fri Feb 27 12:48:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.56% done, estimate finish Fri Feb 27 12:48:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.84% done, estimate finish Fri Feb 27 12:48:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 2.5x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=300h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: closing track
BraseroGrowisofs stderr: :-[ CLOSE TRACK failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: closing disc
BraseroGrowisofs stderr: :-[ CLOSE DISC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2653)

---

