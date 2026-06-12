---
title: "How to Rip a DTS &quot;5.1 Music Disc&quot; to FLAC and keep the surround sound"
date: 2011-09-24
forum: Tutorials
---

### Post by dearingj on 2011-09-24
This tutorial was written because I recently bought a surround sound copy of The Moody Blues' "Days of Future Passed" in the DTS 5.1 Music Disc format. I spent several hours Googling for Linux-compatible software that would rip this disc with satisfactory results. Everything I found either didn't run under Linux even with Wine, didn't support this disc format, or would just rip it in stereo. Finally I decided to break it up into a bunch of small steps which, according to common Unix philosophy, could all be handled by different programs, each program doing one small thing and doing it very well. This tutorial is the result.

You Will Need (all of these applications are available in Ubuntu's repositories):
--------------
dcadec (part of libdca-utils)
ffmpeg
Sound Juicer or another CD ripping program (must rip to .wav files - no processing or conversion to other formats!)
any terminal program, such as GNOME Terminal or lxterm
EasyTAG
VLC Media Player (Optional)
A few hundred megabytes of free disk space

Steps:
--------------
0) If you don't have these already, download and install all the needed packages:
```
[sudo apt-get install libdca-utils ffmpeg sound-juicer gnome-terminal easytag vlc]("apt://dcadec,ffmpeg,sound-juicer,gnome-terminal,easytag,vlc")
```
[LIST=1]
[*]Insert the disc you wish to rip into your CD drive. Open Sound Juicer. Sound Juicer should detect and identify the disc automatically.
[*]In Sound Juicer, go to Edit->Preferences and click the 'Edit Profiles' button. Create a new profile and name it whatever you wish.
[*]Edit the new profile, and copy & paste the following into "Gstreamer Pipeline":
```
audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc
```
[*]Set the file extension to "wav" (I don't think the extension actually matters, but this is what I used) and check the "Active?" box.
[*]Close the profile and the dialog which lists all the profiles, so that you are back in Sound Juicer's preferences window.
[*]If your new profile does not appear as an option under "Output Format", close and reopen Sound Juicer and reopen Preferences.
[*]Select your new profile, make any changes you wish to the other preferences. You may want to change the 'music folder' to something other than your normal Music folder, so that you don't accidentally get a bunch of temporary .wav files intermixed with whatever else is in there. Now close the Preferences window.
Note: Sound Juicer will usually identify your disc and download any available information such as song titles, artist, genre, etc. If this did not happen, or if the information is incorrect, do not bother correcting it at this stage - all will have to be re-entered later anyway.
[*]Check all the tracks you want to copy, then click Extract.
[*]Open up a terminal and cd to the directory where Sound Juicer put the output files, including the artist and album folders if it was set to create them. (e.g. "cd ~/MusicFolder/The Moody Blues/Days of Future Passed")
[*]To make sure you're in the right folder, enter
```
ls *.wav
```That should list all the files you just created with Sound Juicer and no others.

These wav files are currently encoded using the [DTS Coherent Acoustics]("http://en.wikipedia.org/w/index.php?title=DTS_%28sound_system%29&oldid=450833763#DTS_audio_codec") algorithm, meaning that playing them on a non-DTS capable system will simply sound like noise. Some programs, such as VLC, can play DTS-encoded files without a needing to decode them first.
[*]To decode the files, copy and paste the following into the terminal. It should be all on one line. No typos!:
```
for file in *.wav; do name=$(echo $file | sed "s/\.wav//g"); dcadec -o wavall "$file" > "$name"_decoded.wav; ffmpeg -i "$name"_decoded.wav "$name".flac; rm -f "$file" "$name"_decoded.wav; done
```
[*][Optional] To verify that the newly created flac files are actually in surround sound and are playable on your computer, open one in VLC, then click on Tools->Codec Information. The codec should be listed as FLAC and the channels should be 3F2R/LFE. That's VLC's way of saying it's in 5.1-channel surround sound.

We're almost done. All the files have been created, but they don't have any information within them about what album they're from, who the artist is, or anything. Skip these last two steps if you don't care about that.
[*]Open up EasyTAG and navigate to the folder where all these files are being stored. Click anywhere in the File Name box and press Ctrl+A to select all the files.
[*]Fill in the title, artist, album, etc. fields. For those which should be the same for all files, click the little box next to it. The box's tooltip, when you hover your mouse over it, should read "Tag selected filed with this [field]". Use the arrows in the upper left corner to switch between files. When you're done, click the 'Save File(s)' button.
[/LIST]

----A Breakdown of Step 11
Here's a more detailed explanation of what happens in step 11, for anyone interested:
```
for file in *.wav; do # Loops through every file whose name ends in .wav, one at a time, and stores its name in a variable called file.
    name=$(echo $file | sed "s/\.wav//g"); # Takes the content of the variable file, removes the .wav, and stores the result in a variable called name.
    dcadec -o wavall "$file" > "$name"_decoded.wav; # Starts the dcadec program and tells it to read file (with the .wav at the end), decode it, and give the result as a wav audio file with "all" speaker channels. We then take that result and store it as $name_decoded.wav
    ffmpeg -i "$name"_decoded.wav "$name".flac; # Starts the program ffmpeg and has it read $name_decoded.wav and convert that to a FLAC audio file, $name.flac.
    rm -f "$file" "$name"_decoded.wav; # Removes the original and decoded wav files, leaving only the flac file just created.
done # Goes back to the beginning of the loop to work on the next file.
```

---

