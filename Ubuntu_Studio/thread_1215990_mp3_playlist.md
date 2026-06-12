---
title: "mp3 playlist"
date: 2009-07-17
forum: Ubuntu Studio
---

### Post by th1bill on 2009-07-17
[COLOR="DarkRed"]... I have downloaded the WEB Bible in mp3 format and want to burn them to two CDs.  Without buying some windoze software I cannot find anything that will write the playlist order desired and I have just spent the dy searching for the method, title, form and extension and I felt much better about it before I began than I do now.
... I'm going to burn with k3b and all I need to learn how to create a playlist to put the thing into order.  Thank-you.[/COLOR]

---

### Post by kilowattradio on 2009-07-17
> **th1bill said:**
> [COLOR="DarkRed"]... I have downloaded the WEB Bible in mp3 format and want to burn them to two CDs.  Without buying some windoze software I cannot find anything that will write the playlist order desired and I have just spent the dy searching for the method, title, form and extension and I felt much better about it before I began than I do now.
... I'm going to burn with k3b and all I need to learn how to create a playlist to put the thing into order.  Thank-you.[/COLOR]

 You can use a text editor to view a playlist and edit it the way you like. Many text editors also support sorting lines of text. You will have to learn regular expressions however to get a list of lines sorted the way you like.

---

### Post by th1bill on 2009-07-17
Thanks for the reply but what I need is what do I name the playlist and with what extension.  And an example line would be perfect to illustrate the form of it.  I am into computers since the seventies but have no experience with mp3 format disks.

---

### Post by kostkon on 2009-07-17
If it is a large mp3 file that you want to split in pieces then [*mp3splt*]("http://mp3splt.sourceforge.net/mp3splt_page/home.php") will be useful. Then you can make a [*M3U*]("http://en.wikipedia.org/wiki/M3U") playist out of them by for example loading them in *Rhythmbox* and saving them as a playlist or in any other media application that can create and save playlists.

---

### Post by optimix on 2009-07-30
mp3splt has a **-m** option for creating a .m3u file containing the split files: [mp3splt manual]("http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html")

---

### Post by CDrewing on 2009-09-16
I remember this setting, but mp3splt doesn't:

> [FONT="Fixedsys"]cdrewing@ubuntu-desktop:~$ mp3splt -f -m CD1.m3u -c 101-va_-_masterpiece_\(created_by_francois_k\)_cd_1_\(napoli\).cue 101-va_-_masterpiece_\(created_by_francois_k\)_cd_1_\(napoli\).mp3
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
mp3splt: invalid option -- 'm'
Error: Run without arguments for HELP. Read man page for complete documentation[/FONT]

What did I do wrong?

Best regards
Christian

---

### Post by CDrewing on 2009-09-16
Ah got it. The Jaunty repo only has v2.1 with itself and option -m will be available from V2.2.

---

