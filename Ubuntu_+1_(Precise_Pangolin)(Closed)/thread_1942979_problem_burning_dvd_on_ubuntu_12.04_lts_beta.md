---
title: "problem burning dvd on ubuntu 12.04 lts beta"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keinnome on 2012-03-18
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///VIDEO_TS
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///VIDEO_TS
BraseroBurnURI Adding directory (null) at /VIDEO_TS/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_3.VOB at /VIDEO_TS/VTS_01_3.VOB
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_0.VOB at /VIDEO_TS/VTS_01_0.VOB
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_1.VOB at /VIDEO_TS/VTS_01_1.VOB
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_0.IFO at /VIDEO_TS/VTS_01_0.IFO
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_2.VOB at /VIDEO_TS/VTS_01_2.VOB
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VTS_01_0.BUP at /VIDEO_TS/VTS_01_0.BUP
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VIDEO_TS.VOB at /VIDEO_TS/VIDEO_TS.VOB
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VIDEO_TS.IFO at /VIDEO_TS/VIDEO_TS.IFO
BraseroBurnURI Added file /home/keinnome/share/convertxtodvd/My DVD/VIDEO_TS/VIDEO_TS.BUP at /VIDEO_TS/VIDEO_TS.BUP
BraseroBurnURI Information retrieval for burn:///AUDIO_TS
BraseroBurnURI Adding directory (null) at /AUDIO_TS/
BraseroBurnURI called brasero_job_get_current_track
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
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_HT59AW.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-dvd-video
	-graft-points
	-path-list
	/tmp/brasero_tmp_Q9PKBW
	-exclude-list
	/tmp/brasero_tmp_58PKBW
	-V
	Jack and Jill
	-A
	Brasero-3.3.91
	-sysid
	LINUX
	-quiet
	-print-size
	-f
	/tmp/brasero_tmp_RLRKBW
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: Warning: Disabling Joliet support for DVD-Video.
BraseroGenisoimage stdout: 1224791
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_session_output_size
BraseroGenisoimage output set (IMAGE) image = /tmp/brasero_tmp_0S8PBW.bin toc = none
BraseroGenisoimage called brasero_job_get_session_output_size
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_image_output
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-dvd-video
	-graft-points
	-path-list
	/tmp/brasero_tmp_4T7PBW
	-exclude-list
	/tmp/brasero_tmp_ES7PBW
	-V
	Jack and Jill
	-A
	Brasero-3.3.91
	-sysid
	LINUX
	-o
	/tmp/brasero_tmp_0S8PBW.bin
	-f
	/tmp/brasero_tmp_NA9PBW
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: Warning: Disabling Joliet support for DVD-Video.
BraseroGenisoimage stderr: Warning: -follow-links does not always work correctly; be careful.
BraseroGenisoimage stderr:   0.41% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   0.82% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   1.22% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   1.63% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   2.04% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   2.45% done, estimate finish Sun Mar 18 16:57:59 2012
BraseroGenisoimage stderr:   2.86% done, estimate finish Sun Mar 18 16:58:33 2012
BraseroGenisoimage stderr:   3.27% done, estimate finish Sun Mar 18 16:58:29 2012
BraseroGenisoimage stderr:   3.67% done, estimate finish Sun Mar 18 16:58:26 2012
BraseroGenisoimage stderr:   4.08% done, estimate finish Sun Mar 18 16:58:23 2012
BraseroGenisoimage stderr:   4.49% done, estimate finish Sun Mar 18 16:58:21 2012
BraseroGenisoimage stderr:   4.90% done, estimate finish Sun Mar 18 16:58:39 2012
BraseroGenisoimage stderr:   5.31% done, estimate finish Sun Mar 18 16:58:55 2012
BraseroGenisoimage stderr:   5.72% done, estimate finish Sun Mar 18 16:59:26 2012
BraseroGenisoimage stderr:   6.12% done, estimate finish Sun Mar 18 16:59:36 2012
BraseroGenisoimage stderr:   6.53% done, estimate finish Sun Mar 18 16:59:46 2012
BraseroGenisoimage stderr:   6.94% done, estimate finish Sun Mar 18 16:59:39 2012
BraseroGenisoimage stderr:   7.35% done, estimate finish Sun Mar 18 17:00:01 2012
BraseroGenisoimage stderr:   7.76% done, estimate finish Sun Mar 18 17:00:07 2012
BraseroGenisoimage stderr:   8.17% done, estimate finish Sun Mar 18 17:00:25 2012
BraseroGenisoimage stderr:   8.57% done, estimate finish Sun Mar 18 17:00:18 2012
BraseroGenisoimage stderr:   8.98% done, estimate finish Sun Mar 18 17:00:23 2012
BraseroGenisoimage stderr:   9.39% done, estimate finish Sun Mar 18 17:00:28 2012
BraseroGenisoimage stderr:   9.80% done, estimate finish Sun Mar 18 17:00:32 2012
BraseroGenisoimage stderr:  10.21% done, estimate finish Sun Mar 18 17:00:35 2012
BraseroGenisoimage stderr:  10.61% done, estimate finish Sun Mar 18 17:00:57 2012
BraseroGenisoimage stderr:  11.02% done, estimate finish Sun Mar 18 17:00:51 2012
BraseroGenisoimage stderr:  11.43% done, estimate finish Sun Mar 18 17:00:53 2012
BraseroGenisoimage stderr:  11.84% done, estimate finish Sun Mar 18 17:00:47 2012
BraseroGenisoimage stderr:  12.25% done, estimate finish Sun Mar 18 17:00:50 2012
BraseroGenisoimage stderr:  12.66% done, estimate finish Sun Mar 18 17:01:00 2012
BraseroGenisoimage stderr:  13.06% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  13.47% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  13.88% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  14.29% done, estimate finish Sun Mar 18 17:01:28 2012
BraseroGenisoimage stderr:  14.70% done, estimate finish Sun Mar 18 17:01:29 2012
BraseroGenisoimage stderr:  15.10% done, estimate finish Sun Mar 18 17:01:24 2012
BraseroGenisoimage stderr:  15.51% done, estimate finish Sun Mar 18 17:01:25 2012
BraseroGenisoimage stderr:  15.92% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  16.33% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  16.74% done, estimate finish Sun Mar 18 17:01:28 2012
BraseroGenisoimage stderr:  17.15% done, estimate finish Sun Mar 18 17:01:28 2012
BraseroGenisoimage stderr:  17.55% done, estimate finish Sun Mar 18 17:01:29 2012
BraseroGenisoimage stderr:  17.96% done, estimate finish Sun Mar 18 17:01:30 2012
BraseroGenisoimage stderr:  18.37% done, estimate finish Sun Mar 18 17:01:25 2012
BraseroGenisoimage stderr:  18.78% done, estimate finish Sun Mar 18 17:01:31 2012
BraseroGenisoimage stderr:  19.19% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  19.60% done, estimate finish Sun Mar 18 17:01:33 2012
BraseroGenisoimage stderr:  20.00% done, estimate finish Sun Mar 18 17:01:33 2012
BraseroGenisoimage stderr:  20.41% done, estimate finish Sun Mar 18 17:01:29 2012
BraseroGenisoimage stderr:  20.82% done, estimate finish Sun Mar 18 17:01:30 2012
BraseroGenisoimage stderr:  21.23% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  21.64% done, estimate finish Sun Mar 18 17:01:31 2012
BraseroGenisoimage stderr:  22.05% done, estimate finish Sun Mar 18 17:01:32 2012
BraseroGenisoimage stderr:  22.45% done, estimate finish Sun Mar 18 17:01:37 2012
BraseroGenisoimage stderr:  22.86% done, estimate finish Sun Mar 18 17:01:37 2012
BraseroGenisoimage stderr:  23.27% done, estimate finish Sun Mar 18 17:01:33 2012
BraseroGenisoimage stderr:  23.68% done, estimate finish Sun Mar 18 17:01:38 2012
BraseroGenisoimage stderr:  24.09% done, estimate finish Sun Mar 18 17:01:34 2012
BraseroGenisoimage stderr:  24.49% done, estimate finish Sun Mar 18 17:01:35 2012
BraseroGenisoimage stderr:  24.90% done, estimate finish Sun Mar 18 17:01:31 2012
BraseroGenisoimage stderr:  25.31% done, estimate finish Sun Mar 18 17:01:32 2012
BraseroGenisoimage stderr:  25.72% done, estimate finish Sun Mar 18 17:01:28 2012
BraseroGenisoimage stderr:  26.13% done, estimate finish Sun Mar 18 17:01:29 2012
BraseroGenisoimage stderr:  26.54% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  26.94% done, estimate finish Sun Mar 18 17:01:34 2012
BraseroGenisoimage stderr:  27.35% done, estimate finish Sun Mar 18 17:01:31 2012
BraseroGenisoimage stderr:  27.76% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  28.17% done, estimate finish Sun Mar 18 17:01:28 2012
BraseroGenisoimage stderr:  28.58% done, estimate finish Sun Mar 18 17:01:25 2012
BraseroGenisoimage stderr:  28.98% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  29.39% done, estimate finish Sun Mar 18 17:01:29 2012
BraseroGenisoimage stderr:  29.80% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  30.21% done, estimate finish Sun Mar 18 17:01:24 2012
BraseroGenisoimage stderr:  30.62% done, estimate finish Sun Mar 18 17:01:21 2012
BraseroGenisoimage stderr:  31.03% done, estimate finish Sun Mar 18 17:01:22 2012
BraseroGenisoimage stderr:  31.43% done, estimate finish Sun Mar 18 17:01:25 2012
BraseroGenisoimage stderr:  31.84% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  32.25% done, estimate finish Sun Mar 18 17:01:26 2012
BraseroGenisoimage stderr:  32.66% done, estimate finish Sun Mar 18 17:01:27 2012
BraseroGenisoimage stderr:  33.07% done, estimate finish Sun Mar 18 17:01:24 2012
BraseroGenisoimage stderr:  33.48% done, estimate finish Sun Mar 18 17:01:22 2012
BraseroGenisoimage stderr:  33.88% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  34.29% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  34.70% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  35.11% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  35.52% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  35.93% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  36.33% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  36.74% done, estimate finish Sun Mar 18 17:01:20 2012
BraseroGenisoimage stderr:  37.15% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  37.56% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  37.97% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  38.37% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  38.78% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  39.19% done, estimate finish Sun Mar 18 17:01:20 2012
BraseroGenisoimage stderr:  39.60% done, estimate finish Sun Mar 18 17:01:21 2012
BraseroGenisoimage stderr:  40.01% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  40.42% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  40.82% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  41.23% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  41.64% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  42.05% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  42.46% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  42.86% done, estimate finish Sun Mar 18 17:01:19 2012
BraseroGenisoimage stderr:  43.27% done, estimate finish Sun Mar 18 17:01:20 2012
BraseroGenisoimage stderr:  43.68% done, estimate finish Sun Mar 18 17:01:18 2012
BraseroGenisoimage stderr:  44.09% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  44.50% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  44.91% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  45.31% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  45.72% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  46.13% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  46.54% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  46.95% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  47.36% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  47.76% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  48.17% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  48.58% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  48.99% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  49.40% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  49.81% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  50.21% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  50.62% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  51.03% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  51.44% done, estimate finish Sun Mar 18 17:01:17 2012
BraseroGenisoimage stderr:  51.85% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  52.25% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  52.66% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  53.07% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  53.48% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  53.89% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  54.30% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  54.70% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  55.11% done, estimate finish Sun Mar 18 17:01:16 2012
BraseroGenisoimage stderr:  55.52% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  55.93% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  56.34% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  56.74% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  57.15% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  57.56% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  57.97% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  58.38% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  58.79% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  59.19% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  59.60% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  60.01% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  60.42% done, estimate finish Sun Mar 18 17:01:14 2012
BraseroGenisoimage stderr:  60.83% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  61.24% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  61.64% done, estimate finish Sun Mar 18 17:01:15 2012
BraseroGenisoimage stderr:  62.05% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  62.46% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  62.87% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  63.28% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  63.69% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  64.09% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  64.50% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  64.91% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  65.32% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  65.73% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  66.13% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  66.54% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  66.95% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  67.36% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  67.77% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  68.17% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  68.58% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  68.99% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  69.40% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  69.81% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  70.22% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  70.62% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  71.03% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  71.44% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  71.85% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  72.26% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  72.67% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  73.07% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  73.48% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  73.89% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  74.30% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  74.71% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  75.12% done, estimate finish Sun Mar 18 17:01:13 2012
BraseroGenisoimage stderr:  75.52% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  75.93% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  76.34% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  76.75% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  77.16% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  77.56% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  77.97% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  78.38% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  78.79% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  79.20% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  79.61% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  80.01% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  80.42% done, estimate finish Sun Mar 18 17:01:12 2012
BraseroGenisoimage stderr:  80.83% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  81.24% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  81.65% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  82.05% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  82.46% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  82.87% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  83.28% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  83.69% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  84.10% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  84.50% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  84.91% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  85.32% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  85.73% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  86.14% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  86.55% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  86.95% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  87.36% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  87.77% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  88.18% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  88.59% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  89.00% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  89.40% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  89.81% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  90.22% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  90.63% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  91.04% done, estimate finish Sun Mar 18 17:01:11 2012
BraseroGenisoimage stderr:  91.44% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  91.85% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  92.26% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  92.67% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  93.08% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  93.49% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  93.89% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  94.30% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  94.71% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  95.12% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  95.53% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  95.93% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  96.34% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  96.75% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  97.16% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  97.57% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  97.98% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  98.38% done, estimate finish Sun Mar 18 17:01:10 2012
BraseroGenisoimage stderr:  98.79% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  99.20% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr:  99.61% done, estimate finish Sun Mar 18 17:01:09 2012
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 1438
BraseroGenisoimage stderr: Total directory bytes: 4096
BraseroGenisoimage stderr: Path table size(bytes): 42
BraseroGenisoimage stderr: Max brk space used 0
BraseroGenisoimage stderr: 1224791 extents written (2392 MB)
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_output_type
BraseroGenisoimage Automatically adding track
BraseroGenisoimage called brasero_job_get_image_output
BraseroGenisoimage called brasero_job_get_session_output_size
BraseroGenisoimage called brasero_job_add_track
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_X355AW.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /tmp/brasero_tmp_0S8PBW.bin (size = 2508371968)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) c39dfa758f2c1bed37983bce03511663 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2856)

```

That's the error report it gave me when it failed. Any help on this would be appreciated. Thank you

---

### Post by gordintoronto on 2012-03-18
There is a specific forum for discussion of problems with the beta release.

I think you will find that Brasero works just fine in the current version of Ubuntu, 11.10.

---

