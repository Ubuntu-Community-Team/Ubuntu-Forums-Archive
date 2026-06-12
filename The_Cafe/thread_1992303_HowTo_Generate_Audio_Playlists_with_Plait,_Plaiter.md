---
title: "HowTo: Generate Audio Playlists with Plait, Plaiter, Gjay, fapg - And Listen to Them"
date: 2012-05-31
forum: The Cafe
---

### Post by ohnonot on 2012-05-31
Every now and then I try to find better ways of listening to my music collection.
One tends to listen to the same stuff again and again and some good music never gets listened too - or one just totally randomly listenes to everything.
I admit, my songs are very poorly tagged, i don't like ratings or genres or playcounts very much so i'm looking for a different approach.

While I was searching for a new audio player (I love gmusicbrowser, but it has difficulties with my old ntfs usb harddrive with bad sectors, buggy music files and whatnot; if someone has some advice to that, let's hear it!) i came across a few playlist generating tools.

I like the idea behind [_**gjay**_]("http://gjay.sourceforge.net/") a lot - it analyses all songs frequencies and bpm, plus you can set rating and color/mood, from which it generates a database (takes days) from which you can then generate custom playlists (takes seconds). 
i was intrigued by the idea of an objective analysis that comes close to something resembling a mood, plus once you have the database it doesn't consume your cpu. also you can set a song as starting point.
unfortunately i couldn't get it to work properly - i suspect my hard drive / buggy files again.
but i could get it to generate a few playlists (which is possible before completing the database). interesting.

then there is [_**fapg**_]("http://royale.zerezo.com/fapg/"), a commandline utility that uses id3 genres to put together lists - or just from a directory. so it reads tags, but it's still quite fast. example:```
fapg -r -g 26 -o list.m3u /path/to/music
```creates a list of all tracks tagged ambient in your music directory recursively. 26 stands for ambient. [_(list)_]("http://www.id3.org/id3v2.3.0#head-129376727ebe5309c1de1888987d070288d7c7e7")

but my favorite is [_**plait**_]("http://stephenjungels.com/jungels.net/projects/plait/"). 
it allows you to play songs from your collection based on file names, but very intuitively, e.g.```
plait jazz not dizzie
plait doors 196
```the first works in my music collection because i put all jazz in a folder named jazz, but i don't want dizzie gillespie in the mix cause it's corny.
the latter would ideally play the doors from the 1960ies.

it requires a minimum of setting up. you have to create the ~/.plait directory, then it asks you where your music directory is. then i manually edited  the config file to this:```
MUSICDIR="/path/to/music"
PLATFORM=linux-plaiter
TYPES=".mp3 .wav .aif .ogg .flac .m4a .mpc .wma .mpeg3 .MP3"
```there's also a daemon called plaiter which is supposed to take care of feeding the playlists to an audio player, but i could not get it to work. i almost gave up on it but then i made alittle shell script that takes arguments in the above way, and gives the playlist to an audio player of your choice. like this:```
#!/bin/sh

plait $2 $3 $4 $5 $6 $7 $8 $9 $10 $11 $12 $13 $14 $15 $16 --list > mutmp.m3u 
$1 mutmp.m3u
rm -f mutmp.m3u
```i saved it to ~/bin as mu (make it executable).
then i can use it thus:```
mu deadbeef jazz not dizzie -r
```i have another version that uses deadbeef (audio player) by default:```
mus jazz not dizzie -r
```and another one that has also the --random option hardcoded```
mur jazz not dizzie
```this works with most players. some require a different syntax.

this obviously requires that your music collection is sorted in a recognizable file structure and that you more or less know what you have. so if you downloaded an album with files named 8743508702.mp3 and put it in New Folder (23), it won't work. but if you suddenly remember that you ripped queens of the stone age half a year ago, just type mus queens stone age - voilá!

similar scripts could be made for fapg - an extra challenge to use words instead of numeric values for genres - preferably with flexible syntax.
gjay should do that from a gui - if it works. did someone get it to work fully?

PS: all 3 utilities are in the repositories.

PPS: to include more audio filetypes it isn't enough to edit the config file - you have to edit the actual script.```
sudo gedit /usr/bin/plait
```- edit lines 617-620 to include more filetypes.

---

