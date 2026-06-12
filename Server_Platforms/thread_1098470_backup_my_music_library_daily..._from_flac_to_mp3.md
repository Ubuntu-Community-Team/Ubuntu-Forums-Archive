---
title: "backup my music library daily... from flac to mp3"
date: 2009-03-17
forum: Server Platforms
---

### Post by TheKnudson on 2009-03-17
Hi Everybody,

I want to backup my lossless (FLAC) music library to a lossles format - say mp3 - daily. I've already found a suitable conversion script. Now I need to find a smart backup script that only add's new tracks to the backup folder. I would like to keep the file/folder structure in the backup folder.

Do any of you people know what package/script can do this for me?

I'm running ubuntu server 7.10

Thanks in advance

---

### Post by hyper_ch on 2009-03-17
mp3 is not lossless

---

### Post by Bengaul on 2009-03-17
You could simply use cp -u to move the files once you have invoked the conversion script. Write a shell script that calls the conversion script, and copies to a folder, then cp -u *.*, then rm *.* to get rid of the temporary files. Put this in cron to run each day. 

Would that work?

---

### Post by TheKnudson on 2009-03-18
First of all, thanks for the replies.

hyper_ch, im aware that mp3 is a lossy format, I need to compress my files to MP3 to be able to stream them over the internet. Transcoding is not an option because of the limited processor capacity of my NAS. I'll keep the original lossless files for home network listening goodness.

Bengaul, I'm not certain this solution would work. This would mean I need to convert my entire library every night, and then copy only the new files. Or do I mis the point?

---

### Post by netztier on 2009-03-18
> **TheKnudson said:**
> Hi Everybody,

I want to backup my lossless (FLAC) music library to a lossles format - say mp3 - daily. I've already found a suitable conversion script. Now I need to find a smart backup script that only add's new tracks to the backup folder. I would like to keep the file/folder structure in the backup folder.


Erm.. just as hyper_ch pointed out - MP3 is not lossless. You seem to be aware of this, but then calling your goal *backup* misses the point entirely.

The point of backups is to have the ability to *restore* to a state that the data had before - which can't be done from an MP3 format; data is lost while converting to MP3.

So what you need is an automated intelligent conversion of your FLAC based collection to MP3 format - not a backup solution ;-)

I for one wouldn't know about such a script, though. MIght be possible with something like.. hmm.. 

- only looking at filenames (not filename extensions), copy all new files from the FLAC repository to the MP3 repository. Maybe **rsync** can be configured to look only at filenames (and ignore different file sizes, different filename extensions and different hash values of their binary content).
- launch the conversion tool to run across the entire MP3 repository and grab any *.flac file and convert it to MP3 and rename it .mp3

Like this, your systems wouldn't do any unneeded copying and no unneeded conversion operations.


regards

Marc

---

### Post by issih on 2009-03-18
you should be able to use find and a few command line things to get something knocked together.

e.g.:

something like

```
find directoryToSearch -name *.flac -mtime 1
```

That should list any flac files that have been modified in the last day in the directory you care about.
you could append an exec to copy them somewhere else, e.g.:

```
find directoryToSearch -name *.flac -mtime 1  -exec cp {} directoryToCopyTo \;
```

you could then use something akin to what is in here to do the conversion:

[http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3](http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3)

i.e. something like:

```
for file in directoryFilesCopiedTo/*.flac; do $(flac -cd "$file" | lame -h - "${file%.flac}.mp3"); done
```
(assuming you have flac and lame installed

A simple solution would be to use the exec after find to copy to the directory you keep all your backups in, then run the conversion line, then do a:

```
rm -f *.flac
```

in the mp3 store directory to clean up.

A simple script doing these 3 in sequence could be thrown together and dropped into cron.

Hope that helps

---

### Post by hyper_ch on 2009-03-19
you need now backup or conversation?

---

