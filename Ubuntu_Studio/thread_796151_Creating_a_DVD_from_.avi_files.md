---
title: "Creating a DVD from .avi files"
date: 2008-05-16
forum: Ubuntu Studio
---

### Post by jarica on 2008-05-16
Right I am new to Ubuntu and currently have 8.04 installed.

I am looking for a programme that will allow me to take a few .avi files and create a DVD with menus that will play like a normal Movie DVD.

I Used to use Nero 8 Video to do this and it worked perfectly but I have not been able to find anyhting for Linux, I have been looking honest.  I downloaded NeroLinux but that only included the Nero Burning ROM.

I do not want anything that involves using the Terminal I just want a GUI that lets you add a .avi create a menu and then click a button and it does it all for you (I am lazy I know).

Does anyone know of anything like this?

---

### Post by vanadium on 2008-05-16
DeVeDe is targeted for exactly what you want to do.

---

### Post by Hey Gary on 2008-05-16
Using Hardy Heron, I used DeVeDe to make a DVD movie from my avi file.
In DeVeDe I:
- first selected Video DVD.
- defined my title
- added my .avi file (and set my output to NTSC (US)
- fixed my menu
- ran a preview (for me the video did not work, but I don't think that mattered)
- clicked Forward

The Forward dialog asked for the directory and name of a "file", that file will be created as an ISO image.  When it was done, I double-clicked on the .iso file.  That opened the burn dialog and I then burned the iso to disk.

I popped that DVD into my DVD player and it works beautifully.

---

### Post by jarica on 2008-05-19
Thanks for your help I will install that and give it a go.

---

### Post by raynedanser on 2008-05-19
> **Hey Gary said:**
> 
The Forward dialog asked for the directory and name of a "file", that file will be created as an ISO image.  When it was done, I double-clicked on the .iso file.  That opened the burn dialog and I then burned the iso to disk.

I popped that DVD into my DVD player and it works beautifully.

I either just have a really shitty DVD player (which has played homemade DVDs in the past) or am missing something somewhere. I burn the ISO file and get a disc error. Did I not go forward enough times?

---

### Post by timseal on 2008-05-30
Happens to me too.

---

### Post by thanhquanky on 2008-05-30
While i preview, it was happened error when i added a Vietnamese subtitle:
> [size=5][color=blue]Conversion failed
It seems a bug of SPUMUX[/color][/size]

---

### Post by tunespoon on 2008-08-19
I used to have the same problem with converting avi files together with subtitles: "Conversion failed It seems a bug of SPUMUX"

i don't know exactly what solved it eventually but i did the following:

1. installed qdvdauthor (which i don't like but i thought it might come with codecs or whatever), my installed players are now: vlc, movie player, and mplayer movie player (with a few additional codec packs "gstreamer" something i think).

2. i copied the avi file to my harddrive (from external fat32 drive)

3. set up devede to burn a dvd from it with menu and subtitles. tried the prieview, which worked perfectly (it didn't in previous attemps and gave me the mentioned error message). 

4. burned the iso image with brasero and it worked fine on my dvd player!

hope i could help somebody. sorry for such a shallow post.


EDIT: actually i think it's about the subtitles format!! use .srt files, they will work in devede. sub and idx won't.

---

### Post by imagecko on 2008-08-19
I use mandvd to make dvd's from my avi's.
I think its perfect for the job.

You can get it at getdeb.net

---

### Post by Vietman on 2008-10-19
I found that you can't use the "&" symbol in the title for the menus or else it messes things up...perhaps special characters should not be used.

---

### Post by keither on 2009-05-04
> **thanhquanky said:**
> While i preview, it was happened error when i added a Vietnamese subtitle:

hey, i got the same error with my dvd creation.
I read the posts and thought i would mention this, as it worked for me.

1. Always check the previews. Seems it's an actual sample encoded by DeVeDe so if that doesn't work, you can expect a similar error after a few hours of waiting :)

2. Rename your files. The movie names of mine were fine like "Name of movie.avi" but the .srt files i got were insane: "Name.of.movie..(downloaded.from.full.url.of.website).2.CD.english.srt
it may have been the two periods side by side that upset DeVeDe, i'm no expert. 
i renamed them to cd1.srt and cd2.srt. Both the preview and DVD work fine now...


hope this helps.

---

### Post by kayosiii on 2009-05-07
Sounds like it might be using html or xml formating for the subtitles... See what happens if you replace & with &amp; (if so that might make for some interesting formating capabilities)

---

### Post by TVMA on 2009-05-10
I've successfully made DVD movies using DeVeDe using the initial steps, although I used K3B (in the repos) to burn the DVD iso image. Popped it in a normal DVD player and voila.. worked like a charm..

Hope that helps..

---

### Post by apparle on 2009-05-11
try [http://www.videohelp.com](http://www.videohelp.com)

---

### Post by physwizz on 2009-05-18
I've been trying to burn video dvds with braserio bet there is a bug which leaves the burn button greyed out. I tried to follow some of the hi tech stuff at [Bug #270976 in brasero (Ubuntu): “[SRU] gst-plugins-bad0.10 needs rebuilding with mjpegtools to enable burning video with Brasero”]("https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/270976") but to no avail.

Is there a dummies version?

---

### Post by chmacka on 2009-08-05
I get the SPUMUX error only when I set subtitles encoding to any of the CP----.

I need to change it to Windows-1250 / CP1250 so I could see &#268;&#262;&#381;&#352;&#272; characters.

---

### Post by emperillado on 2010-06-26
Here is a little manual for DVDs creation from .avi and other formats that I wrote for you guys:

First than all I expended many days trying to figure out how to create movies out of any format, not only .avi but all the formats you get them from Internet and found that DeVeDe is a great tool to do it. It works fine with all the formats I have tried until now.

I'm using Ubuntu 10.04 LTS, but this should work just fine for every version.

This is what you have to do in order to make it work, and I'm going to start from scratch because I want this guide to be useful even for the 1st time users::p

 1 Make sure that you already have installed DeVeDe. To do that just go to Applications>Sound & Video and look for DeVeDe DVD/CD Video Creator. If you don't have it then this is what you have to do in order to install it:[INDENT]  1.1 Go to Applications>Ubuntu Software Center
 1.2 Type “devede” without the quotation marks on the search field at the top-right corner where the binoculars are and press Enter.
 1.3 You should get at least one item in the results list which is DeVeDe and it has a “Install” button so click it and wait for the program to be installed. And that's it, you already have DeVeDe on your ubuntu.
[/INDENT]2 Go to Applications>Sound & Video>DeVeDe DVD/CD Video Creator. This opens DeVeDe.[INDENT]  2.1 Here you are going to get a simple menu called “Disk type selection”, choose the first option “Video DVD”.
 2.2 Now you get the “Unsaved disc structure – DeVeDe” window, it is divided in several sections: Titles, Files, File info, Disk usage, Default format, and Menus. Now under Titles click “Properties” and change “Title 1” for the name of your movie, also choose “Play the first title” and hit OK.
 2.3 Under “Files” click “Add” button. You will get the “File properties” window:[INDENT]  2.3.1 Under “File” click the little folder icon on the right.
 2.3.2 Browse to the folder your movie is and select it. If the format is supported it is going to show the file on the list. Click “Open”
 2.3.3 You are back to the “File properties” window.
 2.3.4 Under “Video format” choose “PAL/SECAM” if you are in Europe or “NTSC” for USA.
 2.3.5 Now under “Subtitles” click “Add”. You are going to get the “devede” window:[INDENT]  2.3.5.1 Hit the little folder icon at the right of the “File” field and browse for your subtitle file.[INDENT]  2.3.5.1.1 WARNING: Over here is where everybody gets stuck:[INDENT]  2.3.5.1.1.1 First than anything, the fact that DeVeDe is showing a file doesn't mean that it is a subtitle file!!! Choose carefully. DeVeDe supports .sub, .srt, .ssa, .smi, .txt, .aqt, .jss and .***, but you can trick the program choosing for example a .txt with no subtitles at all, the program takes it but you are going to get the “Conversion failed it seems a bug of SPUMUX”. It also happened to me with a .nfo and a .sfv files that I selected by error.
 2.3.5.1.1.2 DeVeDe tries to detect if the file is pure ASCII, UTF-8 or UTF-16; in case it's unable to do so, it will set the last format selected, so if the detection doesn't work and you don't choose the proper format for the codepage you are going to get an error. I always try to use .srt and .sub and never have problems with them.
[/INDENT][/INDENT]2.3.5.2 Once you have chosen you subtitle file you must choose the language too. This allows the DVD player to show the language code when you enable the subtitles.
 2.3.5.3 Hit OK.
[/INDENT]2.3.6 Now click on “Preview”. This is really important because if you get any errors over here it means that you are not going to be able to create the .iso file at all.[INDENT]  2.3.6.1 If you get errors in the preview phase, try removing the subtitle files one by one until you don't get errors. If you are using only one subtitle file and you are sure that this file is not corrupted then try changing the encoding, but, the list is really big. I would rather download a new subtitles file from internet.
 2.3.6.2 Now, if you were able to preview the title and only in that case, click OK.
[/INDENT][/INDENT]2.4 You are back to the “Unsaved disc structure” window:[INDENT]  2.4.1 Under “Disc usage” click “Adjust disc usage”. Clicking on it will adjust the video rate in each video in order to use the 100% of the disk. To do so, DeVeDe takes in account the final resolution and the length, giving more bits per second to the videos with a higher resolution, but always in a proportional way. Remember that you should always click again the Adjust disk usage button after changing the final resolution, adding or removing subtitles, adding or removing titles, or, in general, before creating your disk, in order to assign a good video bit rate to each film. Remember that changing the soundtrack used in the menus will change the disk usage too. (Taken from DeVeDe help pages).
 2.4.2 Under “Default format” make sure that you have chosen the right format for your country.
 2.4.3 Under “Menus” make sure that “Create a menu with the titles” is checked.
 2.4.4 You don't really need to mess up with the “Advanced options”, they are nice but the default values work just fine.
 2.4.5 Click “Forward”.
 2.4.6 You get a little window that allows you to name the .iso file to be created, it is advisable to change the word “movie” for the name of the movie. I also prefer to change the folder because by default it drops the .iso files on a folder on the “Home” folder and it rapidly becomes too crowded. 
 2.4.7 Now click OK. The program starts the creation of the .iso file. It takes a long time to do it, just like any other similar program, it depends on your computer speed obviously, but any ways it is going to take some time. When it finishes you are going to end up with a .iso file ready to burn a DVD.
[/INDENT][/INDENT]3 Now go to the folder where the .iso file was created. It is going to be either “Home/movie” or the one that you chosen on step 2.4.6.[INDENT]  3.1 Right-click the .iso file that DeVeDe just created.
 3.2 Click “Write to Disc...”. You get the “Write to Disk” window:[INDENT]  3.2.1 Under “Select a disc to write to” make sure that you it shows your DVD writer and don't pay to much attention to the size of the file.
 3.2.2 Click on “Properties”[INDENT]  3.2.2.1 Under “Burning speed” choose the lowest possible value, normally it is 4x. This makes the DVD a lot more compatible with old DVD players.
 3.2.2.2 Click “Close”
[/INDENT]3.2.3 Click either “Burn Several Copies” or “Burn” depending on your own needs.
[/INDENT]3.3 Now you are going to create a DVD. The creation is a very fast process even at the lowest speed. It should be something around 5 minutes.
[/INDENT]4 Enjoy it!

---

### Post by d3v1150m471c on 2010-06-26
you may be able to use strong quotes and get away with it: '&'

---

### Post by rocksockdoc on 2012-01-15
The explanation above made sense for the error I just received today in this thread:
- [ubuntu] [DeVeDe & DVDAuthor "Error: Conversion failed. It seems a bug of SPUMUX" (sic)]("http://ubuntuforums.org/showthread.php?t=1909478")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210906&stc=1&d=1326644975[/IMG]

---

### Post by howefield on 2012-01-15
Old thread closed.

---

