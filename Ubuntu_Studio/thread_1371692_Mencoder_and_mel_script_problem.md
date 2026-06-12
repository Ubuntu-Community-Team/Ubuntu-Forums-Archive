---
title: "Mencoder and mel script problem"
date: 2010-01-03
forum: Ubuntu Studio
---

### Post by FrostBlue on 2010-01-03
Hi everybody I have been using this mel script[http://www.creativecrash.com/maya/downloads/scripts-plugins/animation/c/linux-blast?os=linux](http://www.creativecrash.com/maya/downloads/scripts-plugins/animation/c/linux-blast?os=linux) for maya to make preview animations for some time now. I have recently upgraded to karmic and this script doesnt work any more.

If I disable the remove temp files options in the script the mel gives me a file sequence and a audio file.But it doesnt encode those into a complete movie.Can someone with the knowledge of mencoder please have a look at the script and lemme know if something has changed in the latest mencoder that comes with karmic.

The script isnt that long, especially the mencoder options.

Thankyou very much.

---

### Post by Jose Catre-Vandis on 2010-01-03
Post or upload mencoder section - website you link to requires membership to download :(

---

### Post by FrostBlue on 2010-01-04
Sorry for that ,didnt realise it.

Heres the mencoder section,its from different parts of the script but I think it covers all the variables (I have also uploaded the whole script here [http://rapidshare.com/files/330142434/linux_blast-v1.3-.mel.html](http://rapidshare.com/files/330142434/linux_blast-v1.3-.mel.html))

	//mencoder flags - adjust video codec, etc
	string $encoder_flags = ("-ovc lavc -lavcopts vcodec=mpeg4:vbitrate=" + $video_bitrate);

	// viewer command run on the output file
	//for me, mplayer seemed to sync up the sound a bit better though i normally use xine

	string $viewer_command;
	if ($player == 1)
		$viewer_command = "kmplayer";
	else
		$viewer_command = "xine --no-splash --fullscreen --loop=repeat ";

	// ---------------------------------------------------------------------



	// set specific file locations
	string $movie_name = ( $temp_file_location + "last_linux_playblast.avi");
	string $audio_trim_file = ( $temp_file_location + "ecf_audio_trim.wav");
	string $audio_trim_raw_file = ( $temp_file_location + "ecf_audio_raw_1.raw");
	string $audio_trim_raw_file_2 = ( $temp_file_location + "ecf_audio_raw_2.raw");
	string $audio_trim_raw_file_3 = ( $temp_file_location + "ecf_audio_raw_3.raw");

//see what fps to play at
	$time_unit = `currentUnit -query -time`;
	int $playback_fps = 30;
	if ($time_unit == "game"){
		$playback_fps = 15;
	}
	else if ($time_unit == "film"){
		$playback_fps = 24;
	}
	else if ($time_unit == "pal"){
		$playback_fps = 25;
	}
	else if ($time_unit == "ntsc"){
		$playback_fps = 30;
	}
	else if ($time_unit == "show"){
		$playback_fps = 48;
	}
	else if ($time_unit == "palf"){
		$playback_fps = 50;
	}
	else if ($time_unit == "ntscf"){
		$playback_fps = 60;
	}


// playblast starts after the start of our audio - crop off the beginning
		else{
			$command_string = ("sox \"" + $displayed_sound_file + "\" \"" + $audio_trim_file + "\" trim "
									 + $start_minutes + ":" + $start_seconds + " " + $duration_minutes + ":" + $duration_seconds);
			if ($verbose) print ($command_string + "\n");
			$command_result = `system($command_string)`;
			if ($verbose) print ($command_result + "\n");

			$audio_source = $audio_trim_file;
		}


		$sound_args = "-oac copy -audiofile \"" + $audio_source + "\"";
	}


	//encode
	$command_string = ("mencoder -mf fps="
							 + $playback_fps + " "
							 + $sound_args + " "
							 + $encoder_flags + " -o \""
							 + $movie_name + "\" mf://\"" + $filename + "\"");
	if ($verbose) print ($command_string + "\n");
	$command_result = `system($command_string)`;
	if ($verbose) print ($command_result + "\n");



Thankyou verymuch for the reply

---

### Post by Jose Catre-Vandis on 2010-01-05
I can't see anything I recognise as being a problem :(

If worst comes to worst, I can always help with a simple mencoder script that will put your video and audio files together for you

---

### Post by Doctor Drive on 2010-01-05
I'm trying to change sound in flv file form mp3 64 stereo to aac 48 mono like this
```

mencoder Funny\ Metal.flv -o encoded.avi -oac faac -faacopts br=48:mpeg=4:object=2 -channels 1 -ovc copy

```

but what I get is the same video encoded
Audio stream: 63.658 kbit/s (7957 B/s) size: 1341406 bytes 168.577 secs
just like it was... 64kbps.. stereo...

any suggestions?

---

### Post by Doctor Drive on 2010-01-05
Found my solution here
[http://ubuntuforums.org/showthread.php?t=1117283&highlight=Audio+LAVC%2C+couldn%27t+find+encoder+for+codec+libfaac](http://ubuntuforums.org/showthread.php?t=1117283&highlight=Audio+LAVC%2C+couldn%27t+find+encoder+for+codec+libfaac)

```

mencoder Funny\ Metal.flv -o encoded.avi -ovc copy -oac lavc -lavcopts acodec=libfaac:abitrate=32

```

Now bitrate converts... but how to make mono?

hlp plz

---

### Post by FrostBlue on 2010-01-05
Thankyou very much Jose Catre-Vandis. The script would be great, only thing is I am looking to put together an audio file with a sequence of images in .sgi format.Thats what the mel script gives me.

Again thankyou.

FrostBlue

---

### Post by Jose Catre-Vandis on 2010-01-06
This page looks like it should give you everything you need?

[http://personal.cscs.ch/~mvalle/mencoder/mencoder.html](http://personal.cscs.ch/~mvalle/mencoder/mencoder.html)

---

### Post by FrostBlue on 2010-01-06
Thankyou, I will make this work.

FrostBlue

---

