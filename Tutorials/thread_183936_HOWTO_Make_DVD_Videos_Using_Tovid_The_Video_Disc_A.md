---
title: "HOWTO: Make DVD Videos Using Tovid: The Video Disc Authoring Suite"
date: 2006-05-29
forum: Tutorials
---

### Post by user1397 on 2006-05-29
So here are the steps to take if you want to have a dvd movie, that's playable in a home dvd player, and created from a video file on your computer.

Tovid should work on any architecture (x86, x86_64, PPC, etc.) and any desktop environment (Gnome, KDE, Xfce, etc.). This guide assumes that you already have a video file saved on your computer, that you own a dvd burner, and that you have a blank dvd.

Tovid will accept many different types of video formats for your initial video.  In fact, whatever formats the programs mplayer and ffmpeg support, tovid supports.  There are very few formats it doesn't support, but you'll probably have one of the more common ones, so there's nothing to worry.

Also, please know that for tovid to work optimally, it's *recommended* to have at least 20GB of free space, so that it can author and encode the video smoothly.

- - - - - 

**Installation**

To install tovid, just search for it in the Software Center, or else type this in a terminal:```
sudo apt-get install tovid
```If that doesn't work, [install from source]("http://tovid.wikia.com/wiki/Installing_tovid").

If you don't see any tovid menu entries under Applications > Sound & Video, refresh the gnome panels: ```
killall gnome-panel
```- - - - - 

**Using the GUI:**

Go to Applications > Sound & Video > tovid.  If for some reason it doesn't start up correctly, run the command in a terminal to diagnose the cause of the issue: ```
todiscgui
```**_OR_**

**Using the CLI:**

You have an avi file named 'foo' in your home directory, and you live in the Eastern Hemisphere (not Japan, they use NTSC), and you have a widescreen TV.  You would simply type in a terminal: 
```
tovid -wide -pal -in foo.avi -out foo_encoded
``` The -wide command tells tovid to make it widescreen, the -pal command tells tovid to make it PAL format, the -in file is the original, and the -out is the final product.  Simple huh?

Consider the more complicated scenario: You have 3 videos, File1.mpg, File2.mpg, and File3.mpg.  You want the menu to have titles Episode 1, Episode 2, and Episode 3.  You want the dvd to be called Season_One.  Your command would be:
```
todisc -files File1.mpg File2.mpg File3.mpg \
 -titles "Episode 1" "Episode 2" "Episode 3" \
-out Season_One
```
- - - - - 

Once it is finished encoding, you could try to burn the video to a dvd using the burn tab in the GUI, but sometimes it doesn't work, so just minimize tovid (you dont want to close it, just in case if the encoding output is needed for support.)  Then open a terminal and paste (this is just an example; replace the italic words accordingly):   
```
makexml -menu *Menu*.mpg \*foo1*.mpg *foo2*.mpg *foo3*.mpg \
 -out *MyDisc*
```That created an xml file, which in this case would be called: *MyDisc*.xml
Now, you have to burn to a dvd, using this command (again, replacing the italic word with your actual file name): ```
makedvd -burn *MyDisc*.xml
```  When it's finished, you'll have a dvd that's playable on your computer and on all (or most) dvd players!

If you wish to make more dvd's using this guide, you'll have to delete the dvd folder that was created, and move any completed files to your completed folder, or delete it if you wish.  These should be moved from the encoding directory so that tovid can encode anew with a fresh place, no left-over trash, so that it doesn't run into space problems or errors.

Official tovid website (installation/info/guides): _**[here]("http://tovid.wikia.com/wiki/Main_Page")**_.

Official tovid forums (bug reports and general info/help): **_[here]("http://www.createphpbb.com/tovid/")_**.

Disclaimer:  I'm not responsible for anything related to this howto. Be aware of the laws in your country.

---

### Post by boywondr16 on 2006-05-30
Erik,

Following your HOWTO to the letter, but I'm getting this when I type the command make:

make: command not found

Paging back up, here's the output I got from ./configure:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
configure: Checking for required core dependencies...
checking for grep... ok
checking for sed... ok
checking for md5sum... ok
checking for mplayer... ok
checking for mencoder... ok
checking for mplex... ok
checking for mpeg2enc... ok
checking for yuvfps... ok
checking for yuvdenoise... ok
checking for ppmtoy4m... ok
checking for mp2enc... ok
checking for ffmpeg... ok
checking for sox... ok
configure: Checking for optional dependencies...
configure: Checking for ImageMagick...
checking for composite... ok
checking for convert... ok
configure: Checking for dvd tools...
checking for spumux... ok
checking for dvdauthor... ok
checking for growisofs... ok
checking for mkisofs... ok
configure: Checking for vcd tools...
checking for vcdxbuild... ok
checking for cdrdao... ok
configure: Checking for transcode...
checking for tcprobe... ok
checking for tcrequant... ok
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/tovid-init.sh
config.status: creating setuplib.py
configure:

From there it gives me the list of dependencies met, etc.  Why is the make file not being created?  Do I need to run as superuser?

---

### Post by user1397 on 2006-05-30
boywondr16, did you install the packages build-essential and checkinstall?

oops! forgot to add that in my howto! i'll edit my howto right now.  Pay close attention to step 1

---

### Post by boywondr16 on 2006-05-31
[QUOTE=erik1397]boywondr16, did you install the packages build-essential and checkinstall?[/QUOTE]

<slaps forehead>

Thanks.  :oops:

---

### Post by justinflavin on 2006-05-31
excellent guide -  i was always wondering how i could do this, but i got lost in page after page of tovid technical and dvd authoring information.

---

### Post by user1397 on 2006-05-31
[quote=boywondr16]<slaps forehead>

Thanks.  :oops:[/quote]
Your're welcome! ;)

---

### Post by user1397 on 2006-05-31
[quote=justinflavin]excellent guide -  i was always wondering how i could do this, but i got lost in page after page of tovid technical and dvd authoring information.[/quote] Why thank you! :p

---

### Post by squidward_tentacles on 2006-06-01
Hello, first off great tutorial...really straightforward and easy to follow. However when I attempted to run: tovidgui I recieved the following output:

Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 33, in ?
    from libtovid import TDL,Parse, Project
ImportError: No module named libtovid

As I am really new at this, I have no idea what went wrong, I tried removing the parse argument, and still recieved the exact same error message, thinking this was not the problem , I gedited it back in.....I have no idea how to proceed, any help would be greatly appreciated, Thanks:D

---

### Post by squidward_tentacles on 2006-06-01
PS I did make sure all the dependancies were installed before begining, and it DOES seem to work w/out the GUI, aka if I enter just "tovid", however as a recent convert from windows, I am a bit bewildered as how to run programs entirely from the command prompt, a GUI interface is highly desired. Well thanks in advance for your help:)

---

### Post by QUASAR_FREAK on 2006-06-01
[QUOTE=squidward_tentacles]Hello, first off great tutorial...really straightforward and easy to follow. However when I attempted to run: tovidgui I recieved the following output:

Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 33, in ?
    from libtovid import TDL,Parse, Project
ImportError: No module named libtovid

As I am really new at this, I have no idea what went wrong, I tried removing the parse argument, and still recieved the exact same error message, thinking this was not the problem , I gedited it back in.....I have no idea how to proceed, any help would be greatly appreciated, Thanks:D[/QUOTE]

Same problem here =/

---

### Post by user1397 on 2006-06-01
[quote=squidward_tentacles]PS I did make sure all the dependancies were installed before begining, and it DOES seem to work w/out the GUI, aka if I enter just "tovid", however as a recent convert from windows, I am a bit bewildered as how to run programs entirely from the command prompt, a GUI interface is highly desired. Well thanks in advance for your help:)[/quote] 
[quote=QUASAR_FREAK]Same problem here =/[/quote] 
Well to answer both of your questions :p, here's the solution:  Instead of just taking out the "Parser" part, delete this entire line from the file "tovidgui":
# Import other tovid modules
from libtovid import TDL, Parser, Project

---

### Post by squidward_tentacles on 2006-06-01
OK, removing the entire line DID fix the GUI interface =). While waiting for a reply to the last post, I went ahead and ran tovid from the command line, and took the new dvd.mpeg file and sent it through the mkiso process, I have my movie! <yay!> now to write it to disk! /home/DVD...ok, theres 2 files here Audio_TS, and Video_TS, Ill make the assumption that Video_TS is the one we want here, wait..theres also a new entry in the home folder, but not in the DVD folder, that boldy proclaims itself as simply "dvd.iso" properties = raw CD image, 3.1gbs that wasnt mentioned in the tutorial, so ill steer clear of that right now...hmmmm, THAT isnt the one im supossed to write, is it? Staying with my interpertation of the tutorial, Applications, Sound & Video, k3b......new error msg about configuring k3b as root...hmmm, "sudo k3b" <being the gullible Linux newbie that I am> well, "something" happened all right lol, then I recieved the k3b error msg you documented at in the link posted at the very start of this thread, the one about "file size bigger than 2gb", the one where the given solution was to try a different program...again, lol. 
Well, ok, theres more than one way to write an .iso in Linux right? Next stop Gnomebaker, result "file too large". OK then, Graveman. Wow, its finally writing!! The end result was a movie of wildly varying video qualities, with an audio track that fades out to silence with loud "pops" at regular intervals and will only play on one of my two DVD players.
um...amy suggestions as to what may have gone wrong/ how I can improve quality, as to make a watchable movie? Please forgive me if I seem a bit frustrated here, during the course of trying to post this reply, Firefox has unexpectadly crashed once, and when I tried to post this a minute ago, I was told I was no longer signed in...start over. Anyway, thanks in advance for your help =) I DO like Ubuntu, I think I may just be having "one of those days" heh, I think ill hold off on the "How to install HP printers" till tommorow, one thing at a time right? ;)

---

### Post by user1397 on 2006-06-01
[quote=squidward_tentacles]OK, removing the entire line DID fix the GUI interface =). While waiting for a reply to the last post, I went ahead and ran tovid from the command line, and took the new dvd.mpeg file and sent it through the mkiso process, I have my movie! <yay!> now to write it to disk! /home/DVD...ok, theres 2 files here Audio_TS, and Video_TS, Ill make the assumption that Video_TS is the one we want here, wait..theres also a new entry in the home folder, but not in the DVD folder, that boldy proclaims itself as simply "dvd.iso" properties = raw CD image, 3.1gbs that wasnt mentioned in the tutorial, so ill steer clear of that right now...hmmmm, THAT isnt the one im supossed to write, is it? Staying with my interpertation of the tutorial, Applications, Sound & Video, k3b......new error msg about configuring k3b as root...hmmm, "sudo k3b" <being the gullible Linux newbie that I am> well, "something" happened all right lol, then I recieved the k3b error msg you documented at in the link posted at the very start of this thread, the one about "file size bigger than 2gb", the one where the given solution was to try a different program...again, lol. 
Well, ok, theres more than one way to write an .iso in Linux right? Next stop Gnomebaker, result "file too large". OK then, Graveman. Wow, its finally writing!! The end result was a movie of wildly varying video qualities, with an audio track that fades out to silence with loud "pops" at regular intervals and will only play on one of my two DVD players.
um...amy suggestions as to what may have gone wrong/ how I can improve quality, as to make a watchable movie? Please forgive me if I seem a bit frustrated here, during the course of trying to post this reply, Firefox has unexpectadly crashed once, and when I tried to post this a minute ago, I was told I was no longer signed in...start over. Anyway, thanks in advance for your help =) I DO like Ubuntu, I think I may just be having "one of those days" heh, I think ill hold off on the "How to install HP printers" till tommorow, one thing at a time right? ;)[/quote] actually, you're supposed to burn the "dvd.iso" file! Srry if i wasn't clear enough on that!  you can actually delete that "dvd" folder, but don't delete the "dvd.iso" file, until you've actually burned it!

---

### Post by user1397 on 2006-06-01
i've made the instructions a little clearer for step 7; now i don't say anything about the dvd folder, i only talk about the iso file, because that's the only one that matters.

---

### Post by user1397 on 2006-06-01
Please post anyone if this method has worked for you, and list any/all issues you may have encountered while taking this tutuorial.  Thank you.

---

### Post by squidward_tentacles on 2006-06-01
Awesome! Thanks for the clarification. :) I installed k3b as per the instrucions given, I dont know why its not working. In the end, all I did to write the image to disk <as graveman wouldnt accept the dvd.iso> was right click on it and choose write to disk, and a short time later I have a high quality movie, that is instantly recognized as DVD-VIDEO by either one of my DVD players. Thanks again! Superb job. Cheers!

---

### Post by user1397 on 2006-06-01
[quote=squidward_tentacles]Awesome! Thanks for the clarification. :) I installed k3b as per the instrucions given, I dont know why its not working. In the end, all I did to write the image to disk <as graveman wouldnt accept the dvd.iso> was right click on it and choose write to disk, and a short time later I have a high quality movie, that is instantly recognized as DVD-VIDEO by either one of my DVD players. Thanks again! Superb job. Cheers![/quote] Look on post below.

---

### Post by user1397 on 2006-06-02
*Edited the howto. Now I chose not to add instructions on installing and using k3b, since I deem it actually unneccessary (even though I didn't feel like that before.)  Instead I chose to use nautilu's cd/dvd creator, a much simpler application, and plus k3b needs lots of dependencies, and that's no good for a slower system.  (Plus, who likes KDE apps on GNOME anyway??? :p)

---

### Post by user1397 on 2006-06-03
*Edit: Added ending credits ;)

---

### Post by yabbadabbadont on 2006-06-03
I don't know of the berlios page is just a mirror, or the new home, or an old page, or ...  but this ( [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page) ) seems to be the page with the most current version of tovid.  (0.27)

I'm going to (mostly) follow your instructions, but with the newer version.  Perhaps the problem with the module import has been corrected in tovidgui in the new version.

Thanks for posting these instructions.  I doubt that I would have found this program otherwise.  (and I've been wanting to create some DVDs from assorted funny videos I have collected)

---

### Post by yabbadabbadont on 2006-06-03
After reading the tovid forums, it looks to me like the library module issue might be that Ubuntu doesn't include /usr/local/lib in the python library module path.  (or whatever it is called)  I configured tovid to use /usr instead of /usr/local and didn't have the issue.  I did find a bug in the 0.27 version of tovidgui.  When it calls makexml, it doesn't include "-out" before the output file name.  The developer has already answered my bug report in the tovid forums with a simple edit to fix the problem.  (I didn't try to track it down myself last night.  I was too sleepy.)  There is also a bug in the tovid shell script in which the WORKING_DIR variable is not properly quoted in two places.  Again, someone in the tovid forums posted a simple fix.

I thank you again for pointing out this software.  It was exactly what I was looking for.

---

### Post by TriggerHappyChewie on 2006-06-04
Ok, well based on your script, you can only make one mpeg file into the iso, right?  Is there a way to make an iso with multiple video files with your script?

---

### Post by ahaslam on 2006-06-04
Hi,
Tovid is great, I'd never heard of it before I read this. Thanks for the info.
I followed your how to up to & including step number 4.
This took a couple of hours to convert the .avi to .mpeg.
From there I went ahead and clicked the burn tab, where it converted it into its separate video & sound folders, created a disc .iso & finally burnt the disc.
The burn process was slow @ 1 x, but it completed successfully & the disc works perfectly. The whole process took somewhere between 5&6 hours. I thought was a little excessive, but the finial product is great quality.
[ATTACH]10597[/ATTACH]
:D 
Thanks again,
Tony.

---

### Post by TriggerHappyChewie on 2006-06-04
The burn tab really isn't working for me...

When I select Author Disc Structure and Create Disc image, it starts the process.

However, it then puts this out:
```
It looks like some files already exist with prefix
Removing existing files...
```

And it deletes the file it already encoded, the mpg, then encodes it again!

---

### Post by ahaslam on 2006-06-04
[QUOTE=erik1397]this just never worked for me, so it'll probably never work for you[/QUOTE]
[QUOTE=TriggerHappyChewie]And it deletes the file it already encoded, the mpg, then encodes it again![/QUOTE]
I must've been very lucky. I don't usually deviate from the instructions, I just had a good feeling about it.

[QUOTE=TriggerHappyChewie]It looks like some files already exist with prefix
Removing existing files...[/QUOTE]
I've no idea what that means, but Tovid renamed my video during this last stage, as the original was to long. I wonder if that's what made the difference?

PS. I've seen that Tovid .27 is now availabe, see their wiki - anyone tried it?

Tony.

---

### Post by TriggerHappyChewie on 2006-06-04
You must have been lucky :-).

I'm going to try .27 today and see what happens.

---

### Post by ahaslam on 2006-06-04
[QUOTE=TriggerHappyChewie]I'm going to try .27 today and see what happens.[/QUOTE]
Let us know how you get on ;) 

Cheers,
Tony.

---

### Post by yabbadabbadont on 2006-06-04
Read my post at the top of this page...  it is about a couple of bugs in the 0.27 version of tovid.  Both have quick fixes.  I think I found another problem with how tovidgui handles files that contain underscores in the filenames though.  It (tovidgui) also seems to randomly skip videos when it starts the encoding process.  I'll have to do some more testing to be sure though.  So far however, the console apps in 0.27 seem to all work correctly.

---

### Post by TriggerHappyChewie on 2006-06-04
Well, I installed .27, but I don't have the time to encode anything tonight.

Thanks for the heads-up on the bug yabbadabbadont.

---

### Post by jon_gunnar on 2006-06-05
[QUOTE=yabbadabbadont]After reading the tovid forums, it looks to me like the library module issue might be that Ubuntu doesn't include /usr/local/lib in the python library module path.  (or whatever it is called)  I configured tovid to use /usr instead of /usr/local and didn't have the issue.  I did find a bug in the 0.27 version of tovidgui.  When it calls makexml, it doesn't include "-out" before the output file name.  The developer has already answered my bug report in the tovid forums with a simple edit to fix the problem.  (I didn't try to track it down myself last night.  I was too sleepy.)  There is also a bug in the tovid shell script in which the WORKING_DIR variable is not properly quoted in two places.  Again, someone in the tovid forums posted a simple fix.
.[/QUOTE]
Thanks for this.The 0.27 worls quite nice here.
For info,direct link to the mentioned bugs:

[http://www.createphpbb.com/tovid/viewtopic.php?p=1967&mforum=tovid#1967](http://www.createphpbb.com/tovid/viewtopic.php?p=1967&mforum=tovid#1967)
[http://www.createphpbb.com/phpbb/viewtopic.php?t=410&highlight=workingdir&mforum=tovid](http://www.createphpbb.com/phpbb/viewtopic.php?t=410&highlight=workingdir&mforum=tovid)

---

### Post by user1397 on 2006-06-10
Thank you guys for all of the suggestions and comments they have really helped.  Don't worry, I'll do a major overhaul of the whole guide, I was just having fun at the beach that's all! :D

---

### Post by user1397 on 2006-06-10
[quote=TriggerHappyChewie]Ok, well based on your script, you can only make one mpeg file into the iso, right?  Is there a way to make an iso with multiple video files with your script?[/quote] well using my script, i guess you could just experiment and do this: ```
mkiso /directory_of_first_file /directory_of_second_file
``` etc., where the space between the two paths tells the script to do it for two different files.  I'm not saying this will work, but in theory it could.

---

### Post by PapaWiskas on 2006-06-13
[QUOTE=erik1397]well using my script, i guess you could just experiment and do this: ```
mkiso /directory_of_first_file /directory_of_second_file
``` etc., where the space between the two paths tells the script to do it for all of the ones you type.  I'm not saying this will work, but in theory it could.[/QUOTE]


Can anyone confirm that this works for two files to be placed on the DVD, so that you can watch both episodes on the home DVD player.

The reason why I ask is because when I used to do this in Windows, I could get two TV episodes on a DVD disc.

Because I am wondering if doing it this way will make an two individual ISO's or will it actually make one ISO that you can put on a DVD, hence two episodes per disc.

---

### Post by lime4x4 on 2006-06-13
i'm having a hard time finding the following packages
transcode and lsdvd

I tired a google search but i never find any files to download

---

### Post by user1397 on 2006-06-14
[quote=lime4x4]i'm having a hard time finding the following packages
transcode and lsdvd

I tired a google search but i never find any files to download[/quote]do you have the multiverse repositories enabled?  Try this: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by lime4x4 on 2006-06-14
yes i do i was able to find lsdvd but i'm having no luck with the transcode.. I keep getting transcode for fonts..Also i tried transcode.org and all there links are dead

---

### Post by user1397 on 2006-06-14
[quote=lime4x4]yes i do i was able to find lsdvd but i'm having no luck with the transcode.. I keep getting transcode for fonts..Also i tried transcode.org and all there links are dead[/quote]thats really weird. As you can see, it should be in synaptic after enabling multiverse.  Look at the attachment below for proof.  Did you ever try the reload button in synaptic before looking for it?  maybe that's all u have to do.

---

### Post by lime4x4 on 2006-06-14
i will try that i've done sudo apt-get update

---

### Post by lime4x4 on 2006-06-14
well when i click on the reload button all i get is errors for some odd reason

[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

This has been going for over a week now..I've tried different sources and they all error like that

---

### Post by PapaWiskas on 2006-06-14
[http://ubuntuforums.org/showthread.php?t=176894&highlight=Sub-process+gzip](http://ubuntuforums.org/showthread.php?t=176894&highlight=Sub-process+gzip)

should help you guys out.

---

### Post by lime4x4 on 2006-06-14
thanks i tried all those suggestions before still no go

---

### Post by user1397 on 2006-06-17
*EDIT: okay i just did the major overhaul of the guide, now with the new version of tovid, 0.27

---

### Post by buildid on 2006-06-18
if you have already mpg files , i create them with avidemux2 then there is a really nice script into tovid that creates also a dvd from several mpg files :
 i  use this command :


buildid@Breezy:~$ todisc -text-mist -menu-fade -files File 1.mpg file 2.mpg File 3.mpg File 4.mpg  -titles "Deel 19" "Deel 20" "Deel 21" "Deel 22"  -out videocollectionDVD

with this i get misty text , a menu that comes op slowly, and the dvd is build into the videocollection directory.

using latest stable version of Tovid.



This script can also produce dvd from avi including hardcoded subs .

---

### Post by user1397 on 2006-06-18
[quote=buildid]if you have already mpg files , i create them with avidemux2 then there is a really nice script into tovid that creates also a dvd from several mpg files :
 i  use this command :


buildid@Breezy:~$ todisc -text-mist -menu-fade -files File 1.mpg file 2.mpg File 3.mpg File 4.mpg  -titles "Deel 19" "Deel 20" "Deel 21" "Deel 22"  -out videocollectionDVD

with this i get misty text , a menu that comes op slowly, and the dvd is build into the videocollection directory.

using latest stable version of Tovid.



This script can also produce dvd from avi including hardcoded subs .[/quote]and what is this script you're talking about?

---

### Post by buildid on 2006-06-18
todisc is the name.

[http://tovid.wikia.com/wiki/Todisc]("http://tovid.wikia.com/wiki/Todisc")

it is included into the latest version

---

### Post by user1397 on 2006-06-18
well i guess that answers your question, PapaWiskas.

---

### Post by oyvindaa on 2006-06-19
[QUOTE=buildid]if you have already mpg files , i create them with avidemux2 then there is a really nice script into tovid that creates also a dvd from several mpg files :
 i  use this command :


buildid@Breezy:~$ todisc -text-mist -menu-fade -files File 1.mpg file 2.mpg File 3.mpg File 4.mpg  -titles "Deel 19" "Deel 20" "Deel 21" "Deel 22"  -out videocollectionDVD

with this i get misty text , a menu that comes op slowly, and the dvd is build into the videocollection directory.

using latest stable version of Tovid.



This script can also produce dvd from avi including hardcoded subs .[/QUOTE]

I've got 12 .avi files, each about 350mb. I've also got subtitles (.srt) for each and everyone of these .avi files. Can I put all these and their subtitles on one dvd?

---

### Post by user1397 on 2006-06-19
[quote=oyvindaa]I've got 12 .avi files, each about 350mb. I've also got subtitles (.srt) for each and everyone of these .avi files. Can I put all these and their subtitles on one dvd?[/quote]i would try the tovid forums or the tovid wiki for that: [http://tovid.wikia.com/wiki/Help:Contents](http://tovid.wikia.com/wiki/Help:Contents)

---

### Post by oyvindaa on 2006-06-19
[QUOTE=erik1397]i would try the tovid forums or the tovid wiki for that: [http://tovid.wikia.com/wiki/Help:Contents](http://tovid.wikia.com/wiki/Help:Contents)[/QUOTE]

Ok mate, will do. Thanks.

---

### Post by user1397 on 2006-06-19
[quote=oyvindaa]Ok mate, will do. Thanks.[/quote]you're very welcome, mate (I didn't know they used mate in Norway, unless you're in fact australian :p)

---

### Post by zenwhen on 2006-06-19
Thanks to this guide, the last thing that I did in Windows two years ago that I havent done as much in linux can be done easily. I've been using this method for about a week to make dvd's of some .avi files, and it has worked flawlessly with about ten files.

---

### Post by oyvindaa on 2006-06-19
[QUOTE=erik1397]you're very welcome, mate (I didn't know they used mate in Norway, unless you're in fact australian :p)[/QUOTE]

Well, they don't but I do when I type english :-)

---

### Post by user1397 on 2006-06-19
[quote=zenwhen]Thanks to this guide, the last thing that I did in Windows two years ago that I havent done as much in linux can be done easily. I've been using this method for about a week to make dvd's of some .avi files, and it has worked flawlessly with about ten files.[/quote]well, you are ever-so welcome! (trying to pull a cartman on you ;))

---

### Post by user1397 on 2006-06-19
[quote=oyvindaa]Well, they don't but I do when I type english :-)[/quote]ah! I see...

---

### Post by oyvindaa on 2006-06-19
From the tovid wiki:

"Future plans

A number of additional features are planned for the tovid GUI. Among the things I have in mind (more or less in order of priority):

[...]

    *  Capability to add subtitles (as a subtitle stream) to videos. This would also require a tovid 

implementation first."

[...]

I guess it's not possible yet then.

Did anyone else manage to add subtitles?

---

### Post by user1397 on 2006-06-19
[quote=oyvindaa]From the tovid wiki:

"Future plans

A number of additional features are planned for the tovid GUI. Among the things I have in mind (more or less in order of priority):

[...]

    *  Capability to add subtitles (as a subtitle stream) to videos. This would also require a tovid 

implementation first."

[...]

I guess it's not possible yet then.

Did anyone else manage to add subtitles?[/quote]i have not done anything with subtitles, to answer your question, but notice that it only talks about the tovid gui.  maybe the command-line version works with subtitles.  just keep on reading and you might find the answer!!! :D

---

### Post by oyvindaa on 2006-06-19
Yeah it's possible alright. Just had a look at the manual pages for tovid.

"-subtitles FILE
              Get subtitles from FILE and encode them into the  video.   WARN&#8208;
              ING:  This hard-codes the subtitles into the video, and you can&#8208;
              not turn them off while viewing the video. By default, no subti&#8208;
              tles  are  loaded.  If  your video is already compliant with the
              chosen output format, it will be re-encoded to include the  sub&#8208;
              titles."

---

### Post by user1397 on 2006-06-19
[quote=oyvindaa]Yeah it's possible alright. Just had a look at the manual pages for tovid.

"-subtitles FILE
              Get subtitles from FILE and encode them into the  video.   WARN&#8208;
              ING:  This hard-codes the subtitles into the video, and you can&#8208;
              not turn them off while viewing the video. By default, no subti&#8208;
              tles  are  loaded.  If  your video is already compliant with the
              chosen output format, it will be re-encoded to include the  sub&#8208;
              titles."[/quote]awesome! well i gess that answers your question!

---

### Post by oyvindaa on 2006-06-20
With the following command I succeeded including subtitles:

```

tovid -pal -dvd -subtitles filename.srt -in filename.avi -out filename_encoded

```

Doing this with 11 other video files is gonna take a while though! :)

Using todisc I can add the .mpg files to the DVD like this:

```

todisc -files File1.mpg File2.mpg File3.mpg \
     -titles "Episode 1" "Episode 2" "Episode 3" \
     -out Season_one

```

My question is - will the method above generate an identical result (in terms of size and quality) to the method posted by you, Erik? (the one about making an .iso).

---

### Post by user1397 on 2006-06-20
[quote=oyvindaa] My question is - will the method above generate an identical result (in terms of size and quality) to the method posted by you, Erik? (the one about making an .iso).[/quote] i gotta tell you, I really am not sure! they should be the same size and quality, as the .iso file is always the same size as the .mpg file, so it really should be all the same!  (best way to know, is to try it! :p)

---

### Post by oyvindaa on 2006-06-20
[QUOTE=erik1397]in i gotta tell you, I really am not sure! they should be the same size and quality, as the .iso file is always the same size as the .mpg file, so it really should be all the same!  (best way to know, is to try it! :p)[/QUOTE]

Alright, I'll test this tomorrow when I've encoded the last .avi

This sure is an interesting topic, I've been wanting to do this for a while and tovid seems like a great program for it.

I'll post back when everything's done.

---

### Post by lime4x4 on 2006-06-20
it just stops working

||  Encoding audio to ac3: 103 MB written to         
    ---  Encoding audio to ac3: 105 MB written to         
    |||  Encoding audio to ac3: 108 MB written to         
    ---  Encoding audio to ac3: 110 MB written to 

That is what is displayed and it will sit there for over 4 hours and not move..I've tried 7 avi's and they all stop around that point

---

### Post by oyvindaa on 2006-06-21
Successfully burned a DVD this morning.

```

makedvd -burn /path/to/Season_one

```

The subtitles ended up a bit large, but not too large. Picture and sound quality was good, not excellent, but good. That's good enough for me. 

See, I didn't need the gui :D

---

### Post by user1397 on 2006-06-21
[quote=oyvindaa]Successfully burned a DVD this morning.

```

makedvd -burn /path/to/Season_one

``` 
The subtitles ended up a bit large, but not too large. Picture and sound quality was good, not excellent, but good. That's good enough for me. 

See, I didn't need the gui :D[/quote]good for you!  maybe you can share your tovid command-line knowledge here, so there's an option for people that don't like the gui!

---

### Post by user1397 on 2006-06-21
[quote=lime4x4]it just stops working

||  Encoding audio to ac3: 103 MB written to         
    ---  Encoding audio to ac3: 105 MB written to         
    |||  Encoding audio to ac3: 108 MB written to         
    ---  Encoding audio to ac3: 110 MB written to 

That is what is displayed and it will sit there for over 4 hours and not move..I've tried 7 avi's and they all stop around that point[/quote]did you ever get all of the dependencies for it?  i remember that you couldn't get some dependencies.

---

### Post by oyvindaa on 2006-06-21
[QUOTE=erik1397]maybe you can share your tovid command-line knowledge here, so there's an option for people that don't like the gui![/QUOTE]

I'll be doing that, don't worry. I won't make a HOWTO though, because I aint good enough yet. I'll be posting little snippets as I go along :)

---

### Post by tuxcantfly on 2006-06-25
[http://tovid.sourceforge.net/download/kubuntu/](http://tovid.sourceforge.net/download/kubuntu/)

has deb packages

---

### Post by user1397 on 2006-06-25
[quote=tuxcantfly][http://tovid.sourceforge.net/download/kubuntu/]("http://tovid.sourceforge.net/download/kubuntu/")

has deb packages[/quote]thanks for that! I have just updated the guide with the deb package, which makes things much easier.

---

### Post by user1397 on 2006-06-26
yes, the tovid developers have made it more simple than anything for ubuntu people! check this out: [http://tovid.wikia.com/wiki/Tovid_packages]("http://tovid.wikia.com/wiki/Tovid_packages") See the ubuntu/kubuntu .deb?!!!  Now i have included this package in my guide, so no more installing from source!

---

### Post by oyvindaa on 2006-06-26
Great news :)

---

### Post by user1397 on 2006-06-26
If you haven't noticed, I have also taken out any quotation marks from the guide, because this confuses some people into thinking if they have to type the quotation marks or not.  instead, I made those words bold (a little tip I picked up from aysiu, thanks again aysiu!)

---

### Post by BluDragon on 2006-06-26
Does anybody have a copy of the icon? It doesn't seem to exist on my system (Dapper Drake).

---

### Post by user1397 on 2006-06-26
[quote=BluDragon]Does anybody have a copy of the icon? It doesn't seem to exist on my system (Dapper Drake).[/quote]I'll upload the icon and put it at the bottom of the guide for convinience.

---

### Post by BluDragon on 2006-06-28
[QUOTE=erik1397]I'll upload the icon and put it at the bottom of the guide for convinience.[/QUOTE]

Much thanks!

---

### Post by user1397 on 2006-06-28
[quote=BluDragon]Much thanks![/quote]no prob.

---

### Post by user1397 on 2006-06-28
*EDIT: I updated the tovid icon to the most current one :p

---

### Post by justinflavin on 2006-06-29
i get an error when the last command in Tovid is executed (this is after it has encoded my avi to mpg)

makexml -dvd -overwrite -menu "/home/justin/tovid/Untitled_menu_1.mpg" "/home/justin/tovid/menorca-june2006 007.avi.tovid_encoded.mpg" "/home/justin/tovid/Untitled_disc"

the error in the tovid log is :
The file /home/justin/tovid/Untitled_disc was not found


Any clues anyone?

---

### Post by justinflavin on 2006-06-29
[http://tovid.wikia.com/wiki/Tovid_changelog#makexml](http://tovid.wikia.com/wiki/Tovid_changelog#makexml)

says that -out is now a required option for makexml.  but the tovidgui script doesnt have that option.

the makexml statement above *should* look something like this:
makexml -dvd -overwrite -menu "/home/justin/tovid/Untitled_menu_1.mpg" "/home/justin/tovid/menorca-june2006 007.avi.tovid_encoded.mpg" -out "/home/justin/tovid/Untitled_disc"

note the -out before the "Untitled_disc" bit at the end.

any clues were i can change this within the tovid python scripts? this is obviously some sort of bug thats crept into the tovid .deb package.

---

### Post by justinflavin on 2006-06-29
ok - i got it working.

bit of an ugly hack this , as it involves altering a Tovid python script (ideally , this hack should be incorporated as a bugfix in Tovid itself)


cd to 

/usr/local/lib/python2.4/site-packages/libtovid/gui

sudo pico options.py

CTRL+w (for find) - type  Use output directory

change this line (line 84):
strCommand += " \"%s/%s\"" % (curConfig.strOutputDirectory, self.outPrefix)

to

strCommand += "**-out** \"%s/%s\"" % (curConfig.strOutputDirectory, self.outPrefix)

CTRL+O to save

restart Tovid

I'm on Ubuntu Dapper - so obviously makexml has been updated since this guide was originally written, and it now requires the -out option.  This change hasnt been incorporated in the .deb Tovid package (or maybe the .deb package is just out of date).

the hack above will add the -out requirement to the final makexml command as issued by the tovidgui.

---

### Post by justinflavin on 2006-06-29
there's a bug in the latest tovid that causes problems if you have spaces in your avi filename

[http://www.createphpbb.com/tovid/viewtopic.php?t=414&mforum=tovid](http://www.createphpbb.com/tovid/viewtopic.php?t=414&mforum=tovid)


just make sure you rename the avi (removing spaces) before encoding.

---

### Post by user1397 on 2006-06-29
[quote=justinflavin]there's a bug in the latest tovid that causes problems if you have spaces in your avi filename

[http://www.createphpbb.com/tovid/viewtopic.php?t=414&mforum=tovid]("http://www.createphpbb.com/tovid/viewtopic.php?t=414&mforum=tovid")


just make sure you rename the avi (removing spaces) before encoding.[/quote]thank you so much justin, as you can see I have already made a link to all of these issues/bugs at the bottom of my guide.

---

### Post by user1397 on 2006-07-03
okay i'm thinking about taking out the mkiso part of the guide, as this makes a duplicate file of the original that is very large in size, and some people can't afford to have that big of hard drive space, plus it's sort of unneeded.  i'm deciding on what is the best option, and i will revise the guide soon.

---

### Post by oyvindaa on 2006-07-05
[QUOTE=erik1397]okay i'm thinking about taking out the mkiso part of the guide, as this makes a duplicate file of the original that is very large in size, and some people can't afford to have that big of hard drive space, plus it's sort of unneeded.  i'm deciding on what iis the best option, and i will revise the guide soon.[/QUOTE]

That's great mate, keep up the good work :)

---

### Post by lime4x4 on 2006-07-05
okay finally got it working correctly..Only one problem remains when using the next chapter button on my dvd it dumps me back to the beginning of the dvd anyway to fix this?

---

### Post by user1397 on 2006-07-06
[quote=lime4x4]okay finally got it working correctly..Only one problem remains when using the next chapter button on my dvd it dumps me back to the beginning of the dvd anyway to fix this?[/quote]does that only happen with one video or all the videos or some?

---

### Post by lime4x4 on 2006-07-06
all videos

---

### Post by user1397 on 2006-07-06
[quote=lime4x4]all videos[/quote]then im guessing it must have something to do w/  the dvd player itself.  i guess you'll just have to ignore it. you could ask on the tovid forums about it.  its just as easy to register there as it is here: [tovid forum]("http://www.createphpbb.com/tovid/")

---

### Post by k420 on 2006-07-15
When i run tovidgui i get this > Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 22, in ?
    import wxversion
ImportError: No module named wxversion
There was an error importing the 'wx' libraries. The above
output should help you find what went wrong. Re-installing
wxPython 2.6 (or upgrading from wxPython 2.4 to 2.6) may
help. Consult the tovid homepage (tovid.org) for further
assistance.
Sorry, 'tovidgui' will not work.


---

### Post by user1397 on 2006-07-15
> **k420 said:**
> When i run tovidgui i get thistry reinstalling or removing/installing python-2.6 in synaptic (system > administration > synaptic package manager)

---

### Post by PapaWiskas on 2006-07-15
I am a very avid tovid user, the gui is in dire need of repairs, and it is way out of date.  The command line is VERY easy to use, not hard at all.  Heck if I can do it anyone can do it, trust me, I am serious.

The gui does not work well at all, since I switched to command line only, I have done over 30 DVDs without ANY issues at all.

---

### Post by user1397 on 2006-07-16
> **PapaWiskas said:**
> I am a very avid tovid user, the gui is in dire need of repairs, and it is way out of date.  The command line is VERY easy to use, not hard at all.  Heck if I can do it anyone can do it, trust me, I am serious.

The gui does not work well at all, since I switched to command line only, I have done over 30 DVDs without ANY issues at all.yes i know that the gui is way behind, but it is still beginner-oriented, and many people are afraid to use the command line.  as i get more proficient with the command line, i will post more and more terminal sections, or if you would like to post some easy terminal steps, go ahead.  the gui will improve however, as the tovid project is an ever-changing one.

---

### Post by daFoos on 2006-07-16
any advice on how to install that file on a 64-bit system?

oh and how do you write an image in K3b?  It says it only wants to write the dvd.iso to a CD and I have to force it to write to a DVD+R (which didn't work).

---

### Post by daFoos on 2006-07-17
k I think I figured everything out

---

### Post by user1397 on 2006-07-17
> **daFoos said:**
> k I think I figured everything outsorry for the late reply, and it seems you've got it figured out, but just to explain, in k3b you would have to go to tools > burn dvd image.  for .iso files, you always have to burn the **image**, not burn the file as a data file.

---

### Post by thunderduck3141 on 2006-07-18
great tutorial
and btw, compiling from source for tovid is fast and easy, plus program is faster afterwards
peace out

---

### Post by NinjitsuStylee on 2006-07-18
> **erik1397 said:**
>    When that's done, you'll have a file named **dvd.iso** in /home. Now, put your blank dvd in the corresponding drive, right-click on the **dvd.iso** file, and click **Write to Disc**.


Maybe you already mentioned this somewhere else in this [growing] thread, but is there a way to modify that script so it doesn't put dvd.iso in /home and puts it in another directory that we can specify?  I have lots of space on my fat partition and even more on another hard drive but not that much left in /home :(

---

### Post by user1397 on 2006-07-19
> **NinjitsuStylee said:**
> Maybe you already mentioned this somewhere else in this [growing] thread, but is there a way to modify that script so it doesn't put dvd.iso in /home and puts it in another directory that we can specify?  I have lots of space on my fat partition and even more on another hard drive but not that much left in /home :(well looking at the script itself, it seems that it doesn't specify any directory within itself, so i guess it just matters where yourt current directory is and then run the script.  in other words, do this:
```
cd <where_your_fat_partition_is>
```then do the mkiso command.  see if that works.

---

### Post by lifeform23 on 2006-07-25
whenever i trying use tovid for encoding i get this error
91 audio & 204 video codecs

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/lifeform23/fiona elizabeth nixon.avi.
AVI file format detected.
AVI: ODML: Building odml index (1 superindexchunks)
AVI_NI: No video stream found.


BENCHMARKs: VC:   0.000s VO:   0.000s A:   0.000s Sys:-1323.374s = -1323.374s

Exiting... (End of file)
[tovid]: Encode stopped, killing all sub processes
[tovid]: tovid encountered an error during encoding:
[tovid]:     Couldn't create file: "/tmp/fiona elizabeth nixon.avi.tovid_encoded.m2v"


I'm quite sure that all dependencies are installed....

---

### Post by dimatrod on 2006-07-26
> **lifeform23 said:**
> whenever i trying use tovid for encoding i get this error
91 audio & 204 video codecs

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/lifeform23/fiona elizabeth nixon.avi.
AVI file format detected.
AVI: ODML: Building odml index (1 superindexchunks)
AVI_NI: No video stream found.


BENCHMARKs: VC:   0.000s VO:   0.000s A:   0.000s Sys:-1323.374s = -1323.374s

Exiting... (End of file)
[tovid]: Encode stopped, killing all sub processes
[tovid]: tovid encountered an error during encoding:
[tovid]:     Couldn't create file: "/tmp/fiona elizabeth nixon.avi.tovid_encoded.m2v"


I'm quite sure that all dependencies are installed....

Are you sure you've got Mplayer installed?  Also try changing the filename from fiona elixabeth nixon to fiona_elizabeth_nixon, and see if that works

---

### Post by Bosonator on 2006-07-28
The tovid dependencies list you give says that it is necessary to have wxPython installed. Even after updating my repositories as you recommend ([http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php).) and doing an apt-get update, I can't seem to find any package called wxPython (though others refer to it). Should I be looking for another package name?

---

### Post by tassoman on 2006-07-31
Hi to all,
 I've tried to make a DVD from a long AVI file. (gone with the wind)
Tovid GUI has created two mpg files chunked at 4.2 GB. And one Mpg for the menu.

I wonder i must burn 2 DVDs one with each mpg.

But when I convert shorten AVI files, how can i get the iso with the menu and he movie?

if I run the standalone script to make iso from mpg, it does with only 1 video for each iso. So I can't insert the menu also.

How to embed menus into dvd image?

---

### Post by user1397 on 2006-07-31
sorry guys but i've been extremely busy these past 2 months, i can't help out much.  

i have updated the tovid download to version 0.28

---

### Post by starscalling on 2006-08-01
heh
ive been looking for a simple guide like this for friggan forever!
this is teh awesomeness
thanx trying it now :)

---

### Post by doomsday on 2006-08-01
that's right, give more of these sticky fingered freaks reasons to go to best buy and act like idiots.

---

### Post by starscalling on 2006-08-01
> **doomsday said:**
> that's right, give more of these sticky fingered freaks reasons to go to best buy and act like idiots.

excuse me sir
i buy my dvd's by the box of 600
dont confuse my enthusiasm with blatant theft
bish

---

### Post by user1397 on 2006-08-04
> **Bosonator said:**
> The tovid dependencies list you give says that it is necessary to have wxPython installed. Even after updating my repositories as you recommend ([http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php).) and doing an apt-get update, I can't seem to find any package called wxPython (though others refer to it). Should I be looking for another package name?after looking in the ubuntu package database, i would think that wxPython would be one of these package names in ubuntu: [SIZE=2]python-wxversion, python-wxgtk2.6, or python-wxtools.  So try installing one at a time, or maybe one depends on the other, so maybe you need to install them all![/SIZE]

---

### Post by starscalling on 2006-08-06
i tried a 2 hr long avi to convert... lets call it fd3
so when it was done converting or whatever
i had the movie file which was 2 gigs and 2 menu files
wth ??
how do i mkiso with 3 files like that ~_~
or how do i combine them or something ??
or do i mkiso themovie and toss the other isos in somewhere??



mmm 
still curious about that..
but i got the burn function to work from tovid!
burned in about 20 minutes
1. what about error verification?
2. what about keeping the aspect ratio the same as the input file... just draw blanks around the extra area?

sigh... someone post so i dont have to keep editing ~_~
[i hate double posters so typically unless its an uuuuuuuuuuuuuuuber long post i dont do so myself ~_^]
ok i found by clicking on the file itself i can choose some aspect ratios
adding my log from tovid... and before anyone gets all pissy i own this movie already ~_~
anyway so yeh what can i do with that dir with the stuff in it?
the ones with the vobs
i wanna burn with k3b so i can use error checking!
though at least with tovid im getting2-4x speeds i think...

---

### Post by user1397 on 2006-08-07
> **starscalling said:**
> i tried a 2 hr long avi to convert... lets call it fd3
so when it was done converting or whatever
i had the movie file which was 2 gigs and 2 menu files
wth ??
how do i mkiso with 3 files like that ~_~
or how do i combine them or something ??
or do i mkiso themovie and toss the other isos in somewhere??



mmm 
still curious about that..
but i got the burn function to work from tovid!
burned in about 20 minutes
1. what about error verification?
2. what about keeping the aspect ratio the same as the input file... just draw blanks around the extra area?

sigh... someone post so i dont have to keep editing ~_~
[i hate double posters so typically unless its an uuuuuuuuuuuuuuuber long post i dont do so myself ~_^]
ok i found by clicking on the file itself i can choose some aspect ratios
adding my log from tovid... and before anyone gets all pissy i own this movie already ~_~
anyway so yeh what can i do with that dir with the stuff in it?
the ones with the vobs
i wanna burn with k3b so i can use error checking!
though at least with tovid im getting2-4x speeds i think...sorry about the late reply, just real busy here.

so you want to burn with k3b i see...well i believe when you first open it up you can select out of the possible projects:  "DVD video" or something like that.  You might want to look in tools> or new>.  sorry but im not on ubuntu rite now so i dont know the exact location but i know k3b has an option to create dvd movies.  it might work, and then again, it might not.

i do know for sure though, that in k3b you can go to tools > burn dvd iso, and you can browse for your movie iso and error check it at the end.  

Though i doubt all of that is necessary if you say tovid burns at 2-4x!!!

---

### Post by starscalling on 2006-08-08
very nessisary
as i want data verification
and i can burn much faster with k3b


also how about getting a slideshow to work? 
the menu option is there but greyed out !_!

---

### Post by user1397 on 2006-08-08
> **starscalling said:**
> very nessisary
as i want data verification
and i can burn much faster with k3bthe faster you burn the dvd, the less probable that it will turn out without errors, so i would recommend using speeds of 4-8x max.


> **starscalling said:**
>  also how about getting a slideshow to work? 
the menu option is there but greyed out !_!i am not sure about that.  all i know is that the gui is far less advanced than the command line interface of tovid, so sometimees the gui doesn't cut it!  And i'm not really proficient with the command line of tovid, so im afraid i can't help you...sorry!

---

### Post by starscalling on 2006-08-08
nekostar@dapper:~$ ls Desktop/tovid/
10-12.mpg
1-3.mpg
4-6.mpg
7-9.mpg
Main_menu.mpg
po_po_tan.xml
[triad] popotan - 01.avi.tovid_encoded.mpg
[triad] popotan - 02.avi.tovid_encoded.mpg
[triad] popotan - 03.avi.tovid_encoded.mpg
[triad] popotan - 04.avi.tovid_encoded.mpg
[triad] popotan - 05.avi.tovid_encoded.mpg
[triad] popotan - 06.avi.tovid_encoded.mpg
[triad] popotan - 07.avi.tovid_encoded.mpg
[Triad] Popotan - 08.avi.tovid_encoded.mpg
[Triad] Popotan - 09.avi.tovid_encoded.mpg
[Triad] Popotan - 10.avi.tovid_encoded.mpg
[Triad] Popotan - 11.avi.tovid_encoded.mpg
[Triad] Popotan - 12.avi.tovid_encoded.mpg

ok so thats my tovid output folder !_!
mind looking in k3b and double checking what i should use?
i wanna make sure my menu works and all too
or how do i use the mkiso bit on that ?
ive no problem using commandline to do something i just need to know what im looking for


Done. The resulting XML was written to /home/nekostar/Desktop/tovid/po_po_tan.xml.
You can now author, image and/or burn the disc by running:
    makedvd /home/nekostar/Desktop/tovid/po_po_tan.xml
Thanks for using makexml!

is how it says to do it.. which im gonna give a try,,,,,

#!/bin/bash
#Make iso from MPG's
dvdauthor -o dvd -t $1 &&
dvdauthor -o dvd -T &&
mkisofs -dvd-video -o dvd.iso dvd/ &&
exit

that being the tovid mkiso script....
seems that from commandline i could just tell it to work off of something... !_! sorry but that bit at the begining for me wasnt that clear

now the basic set of commands that tovid runs at this point is

The following commands will be run:
=========================================
makedvd -device /dev/dvdrw -author  /home/nekostar/Desktop/tovid/po_po_tan.xml
------------------------
Running command: makemenu -ntsc -dvd -align northwest -background "/home/nekostar/duals/nice/Planet_Nova_by_mrastro316.jpg" -audio "/media/hdb1/music/B_SOUL_DARKSIDE_SOLDIERS_MIX_24_04_2006.mp3" -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "1-3" "4-6" "7-9" "10-12" -out "/tmp/Main_menu"
--------------------------------
makemenu
A script to generate DVD/(S)VCD menus
Part of the tovid suite, version 0.28
with: core magick dvd vcd transcode 
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Adding title 1-3
Adding title 4-6
Adding title 7-9
Adding title 10-12
=========================================================
Font: "Default" does not appear to be available in ImageMagick.
A similarly-named font was not found. Sorry!
The font "Helvetica" will be used instead.
=========================================================
Adding 4 titles to the menu:
1-3
4-6
7-9
10-12
Creating the background canvas with the following command:
convert "/home/nekostar/duals/nice/Planet_Nova_by_mrastro316.jpg" -resize 720x -resize "x480<" -gravity center         -crop 720x480+0+0 -matte makemenu.bg_canvas.12319.png
Converting "/media/hdb1/music/B_SOUL_DARKSIDE_SOLDIERS_MIX_24_04_2006.mp3" to ac3 with the following command:
ffmpeg -i "/media/hdb1/music/B_SOUL_DARKSIDE_SOLDIERS_MIX_24_04_2006.mp3" -ac 2 -ar 48000 -ab 224 -acodec ac3 -y "/tmp/Main_menu.ac3"

---

### Post by HAARP on 2006-08-09
I haven't read the thread, but I made a better package some time ago. It's converted from the Fedora Core RPM, but it has all the dependencies so you don't need to fiddle with them manually. It also creates menu items automagically.

I'd be glad if you could add this to the start post.

---

### Post by starscalling on 2006-08-09
seems that one makes me try to isntall mencoder
though its already a part of my mplayer package whereas the one in the thing in front doesnt........

---

### Post by loadeddreams on 2006-08-28
My only question. I used Windows a lot at home, and used to use my laptop to burn DVDs.. I recently installed Ubuntu and found this guide.

I used to use Nero which automatically created Chapters for the avi file. Is there a way to do this in Ubuntu? I'm clueless as I've never transcoded AVI's to DVD using any Linux distro..

I haven't finished with this DVD yet, but thus far tovid seems to be working well.
And I'm loving Ubuntu so far.. I like it more than I did fedora, but I'm still a Slackware lover :)

---

### Post by user1397 on 2006-08-28
> **loadeddreams said:**
> My only question. I used Windows a lot at home, and used to use my laptop to burn DVDs.. I recently installed Ubuntu and found this guide.

I used to use Nero which automatically created Chapters for the avi file. Is there a way to do this in Ubuntu? I'm clueless as I've never transcoded AVI's to DVD using any Linux distro..

I haven't finished with this DVD yet, but thus far tovid seems to be working well.
And I'm loving Ubuntu so far.. I like it more than I did fedora, but I'm still a Slackware lover :)yes there is a way to create chapters and lots more with tovid, but my knowledge does not extend that far with it.  you might have luck in the tovid forums or the tovid wiki, people are really helpful there.  (both of those links are at the bottom of my guide)

---

### Post by user1397 on 2006-08-28
ANNOUNCEMENT TO PEOPLE WHO ARE UBER-KIND!!!:

If someone would take the time to make a tovid package with all dependencies preinstalled, and preferably made into an ubuntu compatible .deb package, would help solve many problems that people have with tovid.

So if anyone is interseted in this, please tell me so that I can praise you! :p

(Sorry but I don't want any tovid packages converted from RPM or something else, only .deb's please)

---

### Post by PapaWiskas on 2006-08-28
The DVDs I make in Tovid automatically have 5 minutes chapters built in.
Meaning when I push forward on the chapters button it skips ahead in 5 minute increments.
Hope this helps.

---

### Post by user1397 on 2006-08-29
> **PapaWiskas said:**
> The DVDs I make in Tovid automatically have 5 minutes chapters built in.
Meaning when I push forward on the chapters button it skips ahead in 5 minute increments.
Hope this helps.hmmm, sounds like a bug to me....i'll report it on the tovid forums and see what they say.

---

### Post by user1397 on 2006-08-29
hey papawiskas, i started a thread in the bugs section of the tovid forums about your bug, but i'm pretty sure they'll need some of your own input, so if you really want to fix it, i suggest you make an account in the tovid forums.  Here is the actual thread: [http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid](http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid)

---

### Post by PapaWiskas on 2006-08-29
> **erik1397 said:**
> yes there is a way to create chapters and lots more with tovid, but my knowledge does not extend that far with it.  you might have luck in the tovid forums or the tovid wiki, people are really helpful there.  (both of those links are at the bottom of my guide)

Hello erik,

I wasnt reporting a bug per say, but rather trying to answer the question on the Ubuntu forum about chapter creation.

What I was trying to say is that whenever I transcode Tovid using the terminal/command line, meaning from .avi to dvd compatible .mpg.  After the Tovid program is done, I then use "makemenu" then I use "makexml" then I use "makedvd", now somewhere in there it makes 5 minute chapters by default and if I am not mistaken it is the "makexml" process that actually does this because the resulting .xml file has the chapter breakdown listed in it with each .mpg associated with it.

So actually I guess I am wrong in saying tovid creates the chapters when actually it is the makexml process that does this.  Tovid just transcodes the .avi to .mpg.

Not sure if any of this makes any sense as I have had a few beers, and some Captain Morgan....but I follow what I am saying nonetheless.... :D

---

### Post by loadeddreams on 2006-08-30
> **PapaWiskas said:**
> Hello erik,

I wasnt reporting a bug per say, but rather trying to answer the question on the Ubuntu forum about chapter creation.

What I was trying to say is that whenever I transcode Tovid using the terminal/command line, meaning from .avi to dvd compatible .mpg.  After the Tovid program is done, I then use "makemenu" then I use "makexml" then I use "makedvd", now somewhere in there it makes 5 minute chapters by default and if I am not mistaken it is the "makexml" process that actually does this because the resulting .xml file has the chapter breakdown listed in it with each .mpg associated with it.

So actually I guess I am wrong in saying tovid creates the chapters when actually it is the makexml process that does this.  Tovid just transcodes the .avi to .mpg.

Not sure if any of this makes any sense as I have had a few beers, and some Captain Morgan....but I follow what I am saying nonetheless.... :D

lol.. well I follow you too ;)
there is a -chapters INTERVAL option with makexml, which I didn't see prior to this. I'm currently burning a disc but when that finishes I'll look at tovid and flip through the options.

The -chapters option is good, but what I meant was nero looks for blackspace and creates a chapter at that point. Which makes sense, a new chapter during scene changes, and there were always 18 chapters (DVD default I believe?) Either way, I can definitely settle with a new chapter every few minutes. Thanks! :)
edit: this thing really needs a spellcheck.. lol

---

### Post by user1397 on 2006-08-30
> **PapaWiskas said:**
> Hello erik,

I wasnt reporting a bug per say, but rather trying to answer the question on the Ubuntu forum about chapter creation.

What I was trying to say is that whenever I transcode Tovid using the terminal/command line, meaning from .avi to dvd compatible .mpg.  After the Tovid program is done, I then use "makemenu" then I use "makexml" then I use "makedvd", now somewhere in there it makes 5 minute chapters by default and if I am not mistaken it is the "makexml" process that actually does this because the resulting .xml file has the chapter breakdown listed in it with each .mpg associated with it.

So actually I guess I am wrong in saying tovid creates the chapters when actually it is the makexml process that does this.  Tovid just transcodes the .avi to .mpg.

Not sure if any of this makes any sense as I have had a few beers, and some Captain Morgan....but I follow what I am saying nonetheless.... :Dwell ok then :p
wapcaplet did return the needed answer anyway

---

### Post by loadeddreams on 2006-08-30
> **erik1397 said:**
> well ok then :p
wapcaplet did return the needed answer anyway

what answer was that? I read through the thread and didn't see that username :( well.. I didn't read through all the thread, but y'know.
anyways, I looked to see if there was a makexml config file but there is no such thing.. and I can't find a way to edit the command being run in tovid. I don't think I could, anyways.. I'm at a friends on a windows machine now so I can't check, but I think I tried a few times.

---

### Post by PapaWiskas on 2006-08-31
> **loadeddreams said:**
> what answer was that? I read through the thread and didn't see that username :( well.. I didn't read through all the thread, but y'know.
anyways, I looked to see if there was a makexml config file but there is no such thing.. and I can't find a way to edit the command being run in tovid. I don't think I could, anyways.. I'm at a friends on a windows machine now so I can't check, but I think I tried a few times.


Hello loadeddreams,

I think he (erik) was referring to the post he made on the Tovid forum, which is where I responded also.  Anywhoo....here is the link.
Drink up me hearty!:-P 
[http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid](http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid)

---

### Post by user1397 on 2006-08-31
> **PapaWiskas said:**
> Hello loadeddreams,

I think he (erik) was referring to the post he made on the Tovid forum, which is where I responded also.  Anywhoo....here is the link.
Drink up me hearty!:-P 
[http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid](http://www.createphpbb.com/tovid/viewtopic.php?t=482&mforum=tovid)yep, that's what i meant.  

[quote=wapcaplet]Yes indeed, it is makexml that creates 5-minute chapters by default. The **-chapters** option lets you specify a different interval, but there's presently no way to do arbitrary chapter points (i.e., a list of explicit time indexes) with makexml. You can always edit the .xml file prior to authoring, to get desired chapter points (or none at all).[/quote]

---

### Post by greenwom on 2006-08-31
I've got the gui running and I make a three menu selection with backgrounds and music.  After the long encode I was left with a mpg that was only 89MB.  I ran it in totem and vlc and I saw my menu but no action on the video selections (I have two / teo hour movies.)

I also was going to let it install in /tmp but that didn't work it said my 23gigs wasn't enough space?

What I take is that it didn't covert the avi's at all.  I'm trying the gui again, letting it write to /tmp (do I need to start the gui as sudo?)

---

### Post by PapaWiskas on 2006-08-31
to be honest I think the GUI to be buggy...I run tovid from the command line only.

Just use terminal, change to the directory that the avi are in and type tovid...this will bring up a sort of help text for you that shows you the options...

For example I would type this in terminal...

tovid -dvd -ntsc -in nameofavifile.avi -out newnameofmpg

This command would effectively convert the .avi file into a dvd compatible .mpg file in the same directory as the avi file.

After that is done you can do the makemenu, then makexml, then makedvd to finally author and burn it.
However I did notice that in the .xml file you do need to edit it in order for widescreen to work on 4:3 TVs...just do this edit...
  after <titles> put the following...
<video aspect="16:9" widescreen="nopanscan" />
save and you are done...this will make a widescreen movie NOT be cut off on the sides.

---

### Post by user1397 on 2006-08-31
> **greenwom said:**
> I've got the gui running and I make a three menu selection with backgrounds and music.  After the long encode I was left with a mpg that was only 89MB.  I ran it in totem and vlc and I saw my menu but no action on the video selections (I have two / teo hour movies.)

I also was going to let it install in /tmp but that didn't work it said my 23gigs wasn't enough space?

What I take is that it didn't covert the avi's at all.  I'm trying the gui again, letting it write to /tmp (do I need to start the gui as sudo?)hmmm the 23 Gigs is plenty of space, and no you're not supposed to run it as root.  as has been mentioned, however, the tovid gui is somewhat buggy, so you could try the tovid forums on that one. :???:

---

### Post by user1397 on 2006-08-31
> **PapaWiskas said:**
> to be honest I think the GUI to be buggy...I run tovid from the command line only.

Just use terminal, change to the directory that the avi are in and type tovid...this will bring up a sort of help text for you that shows you the options...

For example I would type this in terminal...

tovid -dvd -ntsc -in nameofavifile.avi -out newnameofmpg.mpg

This command would effectively convert the .avi file into a dvd compatible .mpg file in the same directory as the avi file.

After that is done you can do the makemenu, then makexml, then makedvd to finally author and burn it.
However I did notice that in the .xml file you do need to edit it in order for widescreen to work on 4:3 TVs...just do this edit...
  after <titles> put the following...
<video aspect="16:9" widescreen="nopanscan" />
save and you are done...this will make a widescreen movie NOT be cut off on the sides.thanks for the help, i will add these simple instructions as an alternative to the gui soon.

---

### Post by PapaWiskas on 2006-08-31
I made a mistake so I changed my post...

the mistake was newnameofmpg.mpg

It should read

-out newnameofmpg

it automatically puts the .mpg at the end on its own, it doesnt need to be declared.

---

### Post by PapaWiskas on 2006-08-31
> **erik1397 said:**
> thanks for the help, i will add these simple instructions as an alternative to the gui soon.

Let me know if you want some help on it....I used to be GUI dependent, but have found the command line is just as easy and way more stable....

Anyway, I write instruction manuals for work, they tell me I am good at making things understandable...LMAO....meaning they aren't technically gifted....

---

### Post by user1397 on 2006-08-31
> **PapaWiskas said:**
> Let me know if you want some help on it....I used to be GUI dependent, but have found the command line is just as easy and way more stable....

Anyway, I write instruction manuals for work, they tell me I am good at making things understandable...LMAO....meaning they aren't technically gifted....okay, i  appreciate it, i'll ask for help if need be

---

### Post by Mtnear on 2006-09-08
> **k420 said:**
> When i run tovidgui i get this...

Installing the python-wxgtk2.6 pkg in synaptic took care of this for me.

---

### Post by jocheem67 on 2006-09-10
How long is a conversion supposed to take?
About 5 hours for a 3 hour xvid avi?
Pretty long....

And I used this command:

jochem@jochem-desktop:~/movie$ tovid -pal -full -subtitles movie.srt -in movie.avi -out movie_encoded.

Encoding is underway, but I'm afraid that I should have used the 'dvd'option instead of the ' full' option?

Anyone knows?

---

### Post by PapaWiskas on 2006-09-10
you might as well cancel it...but by the time you read this it will probably be too late.

You should have used the -dvd option not -full....

---

### Post by darrenm on 2006-09-12
Anyone on Edgy getting this message:
```
Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 39, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: No module named libtovid.gui.frames
```
should download the source from sourceforge and run it with ```
./configure --prefix=/usr
```
Something about python2.4 not being in the search path. May be an Edgy bug but I may be just running a dodgy system.

EDIT: Just saw this same thing fixed on page 3. Doh!

---

### Post by Anonii on 2006-09-18
Greetings, since the converted avi will take 2.2GB~ we can fit another movie in there, right? :/
If yes, how can we do that?


Thanks.

---

### Post by user1397 on 2006-09-18
> **Anonii said:**
> Greetings, since the converted avi will take 2.2GB~ we can fit another movie in there, right? :/
If yes, how can we do that?


Thanks.i don't really know the intricacies of tovid man, sorry.  i put this guide here as a way for "noobs" that are coming into the forums, can see that this is easy to do in linux as it is in windows. if you have more complex questions, like the one you mentioned, you'll have better luck asking in the tovid forums (i provide a link to it at the end of the guide.)

---

### Post by Anonii on 2006-09-19
> **erik1397 said:**
> i don't really know the intricacies of tovid man, sorry.  i put this guide herer as a way for "noobs" coming into the forums can see that this is easy to do in linux as it is in windows. if you have more complex questions, like the one you mentioned, you'll have better luck asking in the tovid forums (i provide a link to it at the end of the guide.)
Ok thanks! Another question:

I got this error at step11:

> $ mkiso -input-charset utf-8 Requiem.png
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Using GIBVI000.MPG;1 for  /gibvideo3.mpg (gibvideo2.mpg)
Using GIBVI001.MPG;1 for  /gibvideo2.mpg (gibvideo1.mpg)
Using MINBT000.PNG;1 for  /minbtsize3.png (minbtsize2.png)
Using MINBT001.PNG;1 for  /minbtsize2.png (minbtsize1.png)
Using MINBT002.PNG;1 for  /minbtsize1.png (minbtsize0.png)
mkisofs: Unable to make a DVD-Video image.

Tried with:

> $ mkiso -input-charset UTF-8 Requiem.png
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Using GIBVI000.MPG;1 for  /gibvideo3.mpg (gibvideo2.mpg)
Using GIBVI001.MPG;1 for  /gibvideo2.mpg (gibvideo1.mpg)
Using MINBT000.PNG;1 for  /minbtsize3.png (minbtsize2.png)
Using MINBT001.PNG;1 for  /minbtsize2.png (minbtsize1.png)
Using MINBT002.PNG;1 for  /minbtsize1.png (minbtsize0.png)
mkisofs: Unable to make a DVD-Video image.


but still no changes :/

---

### Post by user1397 on 2006-09-19
> **Anonii said:**
> Ok thanks! Another question:

I got this error at step11:



Tried with:



but still no changes :/hmmm are you typing the mkiso command with all of those extra commands after it?  or is that just part of the mkiso process?

---

### Post by Anonii on 2006-09-19
Well, screwed up the mkiso script, made it all in one line (-_-) . Fixed it now ^_^

Thanks for the help!

---

### Post by user1397 on 2006-09-19
> **Anonii said:**
> Well, screwed up the mkiso script, made it all in one line (-_-) . Fixed it now ^_^

Thanks for the help!no prob
thanks for using this guide

---

### Post by fabertawe on 2006-09-20
> **Anonii said:**
> Greetings, since the converted avi will take 2.2GB~ we can fit another movie in there, right? :/
If yes, how can we do that?


Thanks.

Have you tried [ManDVD]("http://www.kde-apps.org/content/show.php?content=38347&vote=good&tan=73191165&PHPSESSID=b0fc4ec8303fb395575ca2deffdf9558")? It even works here on AMD64 (Dapper 6.06) prefixed by 'linux32'. It reminds me of the DVD authoring part of the Nero suite on Windows (I forget the name).

I created a quick ISO containing two AVIs with a menu and it played perfectly in my DVD player.

Paul

---

### Post by yeehawjared on 2006-09-23
ManDVD has a slick interface GUI, but you can only use mpeg2 :(

---

### Post by binks on 2006-10-01
ok just a quickie you can use todisc to create a dvd with more than one title 

Usage
          todisc [OPTIONS] \
             -files <file list> -titles <title list>
             -out OUT_PREFIX

       For example:

          $ todisc -files File1.mpg File2.mpg File3.mpg \
               -titles "Episode 1" "Episode 2" "Episode 3" \
               -out Season_one
binks :)
edit this is an exstract from man todisc
todisc is installed when you install tovid ;)

---

### Post by Valavien on 2006-10-10
Hi all,

Just created an mpg file and went to use the script to create an iso and copied the text in exaclty but I get this error?  Any ideas.

mkisofs: No such file or directory. Invalid node - dvd/

---

### Post by user1397 on 2006-10-10
> **Valavien said:**
> Hi all,

Just created an mpg file and went to use the script to create an iso and copied the text in exaclty but I get this error?  Any ideas.

mkisofs: No such file or directory. Invalid node - dvd/did you miss this part of my guide: "Make sure that it looks **exactly** like that, or else it won't work."   meaning, that when you copy and paste the script, it'll appear all in one line, but you have to make it so that it appears exactly how it is in the howto.  your script is probably one long line.

oh, and it's not "mkisofs"  its just "**mkiso**"

---

### Post by Valavien on 2006-10-10
Ah, I did read that and what popped in my head was, "hmm, it will be ok I will just copy and paste it"...  Clearly doing this stuff at midnight wasn't a good idea after all.  But it has now worked, now I just have to move a few things around so / isn't at 100% *sigh*  ](*,) 

Thanks

---

### Post by user1397 on 2006-10-10
***EDIT:  Made the dependency installation  as easy as copy/paste.  no more fussing about with synaptic!

---

### Post by user1397 on 2006-10-10
***ANOTHER EDIT:  Made the mkiso script easily pastable, stupid me.  no more messing with one long line of code.  Please tell me if this works anybody.

---

### Post by mssever on 2006-10-10
I've found DVDStyler to be more functional than Tovid, especially when it comes to creating menus. And, you don't have to touch the command line if you don't want to.

The process is:[LIST=1]
[*]Create MPEG file(s)
[*]Open up DVDStyler
[*]Create menu(s)
[*]Drag and drop MPEGs to form titles
[*]Configure buttons
[*]Use the (poorly-named) Burn command to automatily build everything. Check the review box if you hve xine installed to avoid wasting DVDs. Tell DVDStyler to create an ISO
[*]Burn the ISO to disc using your favorite burning software.[/LIST]

---

### Post by maddbaron on 2006-10-11
HELP!

I tried to add the how to from 1st page on konsole when it asked me did i want to stop kdm daemon I canceled and it started removing kubuntu!

it(konsole text) said removing... and it removed a lot of base kubuntu programs like klipper, kubuntu help and stuff like that. I closed konsole before it could finish and I didnt reboot yet. the stuff looks like it is still there but if I reboot will it be gone?

how can I check?

please!?

---

### Post by maddbaron on 2006-10-11
yes i looked in my menu a lot of my programs are now gone kwireless, adept, ksnapshot, kopete gone a lot of utilities gone also omg omg omg....all i have left is stuff from gnome but nothing "k"....how do I get them back???  anyone....

---

### Post by mssever on 2006-10-11
[quote=maddbaron]yes i looked in my menu a lot of my programs are now gone kwireless, adept, ksnapshot, kopete gone a lot of utilities gone also omg omg omg....all i have left is stuff from gnome but nothing "k"....how do I get them back??? anyone....[/quote]

(re)install kubuntu-desktop.
```
sudo apt-get install kubuntu-desktop
```

---

### Post by user1397 on 2006-10-11
> **mssever said:**
> (re)install kubuntu-desktop.
```
sudo apt-get install kubuntu-desktop
```thats's if he wanted to keep it forever.  the wiser method would be to use ```
sudo aptitude update&&sudo aptitude install kubuntu-desktop
```it is easier to remove kubuntu-desktop with aptitude, if you decide that you dont like it, but with apt-get it might/might not work.

---

### Post by mssever on 2006-10-11
> **erik1397 said:**
> thats's if he wanted to keep it forever.  the wiser method would be to use ```
sudo aptitude update&&sudo aptitude install kubuntu-desktop
```it is easier to remove kubuntu-desktop with aptitude, if you decide that you dont like it, but with apt-get it might/might not work.

My guess is that the whole reason that he lost KDE stuff is because of using aptitude. I lost Xubuntu once after installing something with aptitude. Aptitude thought that xubuntu-desktop and all dependencies were unused and removed them (I didn't notice until too late). Aptitude also tries to label stuff on my system as broken (which is bogus) and has tried many times to remove gqphoto. I have none of these problems with apt-get or Synaptic. So, that's why I suggested apt-get. Aptitude would be a great idea if it worked consistantly for me.

---

### Post by user1397 on 2006-10-11
> **mssever said:**
> My guess is that the whole reason that he lost KDE stuff is because of using aptitude. I lost Xubuntu once after installing something with aptitude. Aptitude thought that xubuntu-desktop and all dependencies were unused and removed them (I didn't notice until too late). Aptitude also tries to label stuff on my system as broken (which is bogus) and has tried many times to remove gqphoto. I have none of these problems with apt-get or Synaptic. So, that's why I suggested apt-get. Aptitude would be a great idea if it worked consistantly for me.well then, you must be a rare case.  aptitude has always worked for me, and for lots of people too.  the reason why your xubuntu was removed was probably caused by not updating, which you should do everytime before using aptitude.

---

### Post by user1397 on 2006-10-11
i'm thinking of making an executable script for this guide, a first for me.  it would download and install all dependencies, download and install tovid, download the icon and put it in /usr/share/icons, and download the mkiso script and put it in /usr/bin.  

What do you guys think?

all you would have to do to start the script would be something like:
```
chmod +x installtovid.sh
./installtovid.sh
```

---

### Post by tmcahow on 2006-10-12
I hope someone is still reading this thread...i am having no luck in burning the files to my dvd...i follow the instructions and when i type the mkiso command i get the following error:

ERR: Error opening dvd/VIDEO_TS/VTS_01_1.vob:  No such file or directory

I also tried strictly using makedvd...however, i get the following error when trying to use the -burn option:

Cannot continue!  DVD image (3725MB) exceeds the DVD's capacity 0MB)

Can anyone help?

---

### Post by user1397 on 2006-10-12
> **tmcahow said:**
> I hope someone is still reading this thread...i am having no luck in burning the files to my dvd...i follow the instructions and when i type the mkiso command i get the following error:

ERR: Error opening dvd/VIDEO_TS/VTS_01_1.vob:  No such file or directory

I also tried strictly using makedvd...however, i get the following error when trying to use the -burn option:

Cannot continue!  DVD image (3725MB) exceeds the DVD's capacity 0MB)

Can anyone help?is this the first time you've used this guide?  i mean, have you made the mkiso script in the past 2 days, or did you made it a long time ago?

---

### Post by tmcahow on 2006-10-13
Thank you for the reply...and first off let me say i think your idea is great about make the tovid script file...the process of finding all the dependencies was painful (of course i did all that before i found this thread)...

I have never successfully used the script...I created the script maybe 2 days ago...and then received the errors noted previously...

Tad

---

### Post by tmcahow on 2006-10-13
Update:

I am using Kubuntu and KDE 3+...and no matter what i do i can not get any program to write the mpg file to the dvd writer...K3b recognizes the dvd blank disc...but i can not get the darn encoded file to the dvd...sorry, a little frustrated...

as i am on the other side of the planet (japan), please tell me what information you need from me to help me resolve this problem...

Tad

---

### Post by user1397 on 2006-10-13
> **tmcahow said:**
> Update:

I am using Kubuntu and KDE 3+...and no matter what i do i can not get any program to write the mpg file to the dvd writer...K3b recognizes the dvd blank disc...but i can not get the darn encoded file to the dvd...sorry, a little frustrated...

as i am on the other side of the planet (japan), please tell me what information you need from me to help me resolve this problem...

Tad
EDIT:  arrrrgh, just forget what I wrote before in this post, it made no sense.  The script is fine, it should work, I have learned that the way it's organized does not matter to much, except the code can't all be in one line.  before i make the huge, all-powerful script, I have simplified the mkiso process.  i now provide a downloadable mkiso script, just follow the new directions to get it working.  remove your old mkiso script and start anew.  here's how to remove the old one: 
```
sudo rm /usr/bin/mkiso
```the script should work for you.  EDIT:  wow im an idiot today, giving you directions on nautilus when you have kde! *slaps his face with a great intensity*  okay, in k3b, you should go to tools > burn DVD IMAGE, or DVD ISO (something like that).  that's the only way to do it.

---

### Post by user1397 on 2006-10-13
***EDIT:  Okay, I finally made the script, check it out at the top of the first page.

PLEASE ALL VOLUNTEERS, HEP TEST MY SCRIPT!!!

---

### Post by tmcahow on 2006-10-14
Ok...everything worked...one note...the dvd.iso file remains in the /tmp directory...

Thank you very much...you are a credit to the linux community...all members of this community should take note of your willingness to help increase users abilities to employee linux products...often i have found the community to be information keepers instead of information sharers...you are a refreshing change...

again thanks from the other side of the planet...

one last thing, can you help the bears remain undefeated for the entire season?

Tad

---

### Post by user1397 on 2006-10-14
> **tmcahow said:**
> Ok...everything worked...one note...the dvd.iso file remains in the /tmp directory...hmm that's weird.  did you change the output directory while in tovid?

> **tmcahow said:**
>  Thank you very much...you are a credit to the linux community...all members of this community should take note of your willingness to help increase users abilities to employee linux products...often i have found the community to be information keepers instead of information sharers...you are a refreshing change...

again thanks from the other side of the planet...thanks, no problem man, just trying to give back what i can

> **tmcahow said:**
>  one last thing, can you help the bears remain undefeated for the entire season?

Tadhmmm, i'm not sure if that power is under my jurisdiction:D

---

### Post by nalmeth on 2006-10-14
Hey, erik, not that you are a tovid ambassador or anything, but in your travels have you ever heard of tovid crashing Ubuntu (as in immediate shutdown) while encoding files?

I would first think this has to do with kernel related services, but everytime I try to encode one specific video file my PC outright powers out, no notice of anything.

I've looked on the tovid forums and elsewhere, but can't reproduce anything.

I'll keep looking for an explanation, but just thought I'd ask

---

### Post by user1397 on 2006-10-14
> **nalmeth said:**
> Hey, erik, not that you are a tovid ambassador or anything, but in your travels have you ever heard of tovid crashing Ubuntu (as in immediate shutdown) while encoding files?

I would first think this has to do with kernel related services, but everytime I try to encode one specific video file my PC outright powers out, no notice of anything.

I've looked on the tovid forums and elsewhere, but can't reproduce anything.

I'll keep looking for an explanation, but just thought I'd asknope, i've never heard of any such bug.  very weird though.  sorry i cant help you out.

---

### Post by nalmeth on 2006-10-14
> nope, i've never heard of any such bug.  very weird though.  sorry i cant help you out.
OK, thanks anyway!

---

### Post by user1397 on 2006-10-14
sooo....anybody test out my script yet???:(

---

### Post by BatteryCell on 2006-10-15
Hm I didnt get any audio after creating the disk (none in the original mpg either :-/)  Any ideas as to why the .avi has audio but not the mpg.  I mean tovid goes through the whole 
```

Waiting 30 seconds for output file "audio.ac3" to appear...
Waiting 29 seconds for output file "audio.ac3" to appear...
Waiting 28 seconds for output file "audio.ac3" to appear...
Processing started. Please wait...                                               
    ---  Copying compliant audio stream: 21 MB written to audio.ac3        
    |||  Copying compliant audio stream: 45 MB written to audio.ac3        
    ---  Copying compliant audio stream: 68 MB written to audio.ac3        
    |||  Copying compliant audio stream: 93 MB written to audio.ac3        
    ---  Copying compliant audio stream: 117 MB written to audio.ac3        
    |||  Copying compliant audio stream: 143 MB written to audio.ac3        
    ---  Copying compliant audio stream: 164 MB written to audio.ac3        
    |||  Copying compliant audio stream: 182 MB written to audio.ac3        


```
thing but Im all the more confused,

It does say :
```

Found compliant audio and dumping the stream.
This sometimes causes errors when multiplexing; add '-force' to the tovid 
command line to re-encode if multiplexing fails.
Copying the existing audio stream with the following command:
nice -n 0 mplayer  "/data1/Shared/Band of Brothers 01 - Currahee.avi" -dumpaudio -dumpfile "/root/Band of Brothers 01 - Currahee.avi.tovid_encoded.CyxGUl/audio.ac3"

```
Before that copying thing...but no errors so once again Im confused.

Any help would be great because I've got all 10 band of brothers on my disk (about 8 gigs) and really need them off.

---

### Post by user1397 on 2006-10-15
> **BatteryCell said:**
> Hm I didnt get any audio after creating the disk (none in the original mpg either :-/)  Any ideas as to why the .avi has audio but not the mpg.  I mean tovid goes through the whole 
```

Waiting 30 seconds for output file "audio.ac3" to appear...
Waiting 29 seconds for output file "audio.ac3" to appear...
Waiting 28 seconds for output file "audio.ac3" to appear...
Processing started. Please wait...                                               
    ---  Copying compliant audio stream: 21 MB written to audio.ac3        
    |||  Copying compliant audio stream: 45 MB written to audio.ac3        
    ---  Copying compliant audio stream: 68 MB written to audio.ac3        
    |||  Copying compliant audio stream: 93 MB written to audio.ac3        
    ---  Copying compliant audio stream: 117 MB written to audio.ac3        
    |||  Copying compliant audio stream: 143 MB written to audio.ac3        
    ---  Copying compliant audio stream: 164 MB written to audio.ac3        
    |||  Copying compliant audio stream: 182 MB written to audio.ac3        


```thing but Im all the more confused,

It does say :
```

Found compliant audio and dumping the stream.
This sometimes causes errors when multiplexing; add '-force' to the tovid 
command line to re-encode if multiplexing fails.
Copying the existing audio stream with the following command:
nice -n 0 mplayer  "/data1/Shared/Band of Brothers 01 - Currahee.avi" -dumpaudio -dumpfile "/root/Band of Brothers 01 - Currahee.avi.tovid_encoded.CyxGUl/audio.ac3"

```Before that copying thing...but no errors so once again Im confused.

Any help would be great because I've got all 10 band of brothers on my disk (about 8 gigs) and really need them off.this one is stumping me...have you installed all proprietary codecs?

---

### Post by BatteryCell on 2006-10-15
Yup...right now Im trying it with avidemux and seing if I cant get it work.

---

### Post by user1397 on 2006-10-15
okay, as impatient as i am, i have tested my script , and it worked, for me at least.  so please feel free to use it and report if any errors occur.

---

### Post by BatteryCell on 2006-10-15
Yea I already had tovid installed, but i just did the script anyways, and so far it looks good :-).

---

### Post by user1397 on 2006-10-15
> **BatteryCell said:**
> Yea I already had tovid installed, but i just did the script anyways, and so far it looks good :-).yay!  my first feedback!  and a positive report too! hope its not the only one...:-k

---

### Post by aysiu on 2006-10-16
> **erik1397 said:**
> has the menu entry ever worked for anybody automatically?   cause on my tovid script, it didn't work for me.
I took a look at your .desktop file for Tovid, and it doesn't appear to have a classification: ```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Tovid
Type=Application
Terminal=false
Name[en_US]=Tovid
Exec=tovidgui
Icon[en_US]=/usr/share/icons/Tovid_icon.png
Icon=/usr/share/icons/Tovid_icon.png
GenericName[en_US]=
``` It specifies and icon and the executable, but it doesn't say what category the application belongs to.

---

### Post by user1397 on 2006-10-16
> **aysiu said:**
> I took a look at your .desktop file for Tovid, and it doesn't appear to have a classification: ```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Tovid
Type=Application
Terminal=false
Name[en_US]=Tovid
Exec=tovidgui
Icon[en_US]=/usr/share/icons/Tovid_icon.png
Icon=/usr/share/icons/Tovid_icon.png
GenericName[en_US]=
``` It specifies and icon and the executable, but it doesn't say what category the application belongs to.ah ok, i got it now.  thanks to your songbird.desktop file actually!  sorry about the copycat-ness:D

---

### Post by user1397 on 2006-10-16
***EDIT: Okay, I have edited the script so that the tovid executable will actually go to applications > sound & video.  i have also finally included the x86_64 or amd64 version for tovid in the conventional guide, i don't know why i delayed it this long.  i will add the amd64 version to the script soon, as soon as i learn how.

---

### Post by Big Fish on 2006-10-17
I ran your script and when I try to run the program, nothing happens. :( 

Applications > Sound & Video > Tovid = nothing

---

### Post by user1397 on 2006-10-18
> **Big Fish said:**
> I ran your script and when I try to run the program, nothing happens. :( 

Applications > Sound & Video > Tovid = nothinghmm very strange.  do you have the command line output of my script in action?  if not, what happens when you type **tovidgui** in a terminal?

---

### Post by Big Fish on 2006-10-18
> **erik1397 said:**
> hmm very strange.  do you have the command line output of my script in action?  if not, what happens when you type **tovidgui** in a terminal?

Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 22, in ?
    import wxversion
ImportError: No module named wxversion
There was an error importing the 'wx' libraries. The above
output should help you find what went wrong. Re-installing
wxPython 2.6 (or upgrading from wxPython 2.4 to 2.6) may
help. Consult the tovid homepage (tovid.org) for further
assistance.
Sorry, 'tovidgui' will not work.

---

### Post by user1397 on 2006-10-18
> **Big Fish said:**
> Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 22, in ?
    import wxversion
ImportError: No module named wxversion
There was an error importing the 'wx' libraries. The above
output should help you find what went wrong. Re-installing
wxPython 2.6 (or upgrading from wxPython 2.4 to 2.6) may
help. Consult the tovid homepage (tovid.org) for further
assistance.
Sorry, 'tovidgui' will not work.ok, paste this into a terminal: ```
sudo apt-get update && sudo apt-get install python python-wxgtk2.6
```and then try **tovidgui** in the terminal.

---

### Post by Big Fish on 2006-10-18
> **erik1397 said:**
> ok, paste this into a terminal: ```
sudo apt-get update && sudo apt-get install python python-wxgtk2.6
```and then try **tovidgui** in the terminal.

It said this: "sh: convert: command not found" and then it opened. :)

---

### Post by Big Fish on 2006-10-18
> **Big Fish said:**
> It said this: "sh: convert: command not found" and then it opened. :)

It works in the Applications menu too. :)

---

### Post by user1397 on 2006-10-18
> **Big Fish said:**
> It works in the Applications menu too. :)okay good, it's still weird though....i dont get why my script didn't install wxPython for you.  does it always say the **sh: convert** error when you try opening it?

---

### Post by Big Fish on 2006-10-18
> **erik1397 said:**
> okay good, it's still weird though....i dont get why my script didn't install wxPython for you.  does it always say the **sh: convert** error when you try opening it?

When I type "tovidgui" into the console, I get that. When I use the menu, it opens fine.

---

### Post by user1397 on 2006-10-18
> **Big Fish said:**
> When I type "tovidgui" into the console, I get that. When I use the menu, it opens fine.that still sounds strange though, but it appears to be a minor bug, since tovid still opens.  i would report the bug in the tovid forums if i were you, the link is at the bottom of my guide.

EDIT:  btw, did you install the right version of tovid?  i mean, for your architecture? (x86 or x86_64?)

---

### Post by user1397 on 2006-10-18
*****EDIT: **okay i updated my script once again, now there's a maor change...you can choose to install the 386 version or the amd64 version of tovid.  I need as much testing as possible with this script please, so that i can get rid of the conventional guide and simplify this whole guide.

edit: Okay I just tried the new script on my x86 machine, and it works perfectly, so now i know that it at least works on i386 PC's.  please all amd64 people, test this out!

---

### Post by user1397 on 2006-10-18
*****EDIT:  **Also, I've just made a tovid removal script, in case you want to remove everything it downloaded.  Please report if this works.

---

### Post by Big Fish on 2006-10-19
When I actually try to encode an avi file, my machine locks up at various points of the process. :(

---

### Post by mssever on 2006-10-19
> **Big Fish said:**
> When I actually try to encode an avi file, my machine locks up at various points of the process. :(

The fact that you're getting random lockups is a sure sign of bad hardware--probably bad memory or processor.

To test memory, choose the memtest86 option from the Grub menu (when you first boot). Let it run for at least several hours and see if it reports any errors.

I don't know how to test the processor.

---

### Post by user1397 on 2006-10-19
> **Big Fish said:**
> When I actually try to encode an avi file, my machine locks up at various points of the process. :(yep, just like mssever said, sometimes hardware is just incompatible.   maybe u'r just out of luck this time...but maybe not, who knows?:-k

---

### Post by Big Fish on 2006-10-20
I have 4 sticks of 256Mb. When I ran the test the first time I got three errors in about three hours. I removed the two newest sticks and ran the test again and didn't get any errors.

Here are the results from the original test that I did: [View Image]("http://www.lasikforbill.com/memory.jpg")

I tried to encode a video again and it seemed to go all the way but it said there was an error. I'll try it again and post the error message.

---

### Post by Big Fish on 2006-10-20
I give up. It locked up at the "probing" part again, with the good memory. :(

---

### Post by user1397 on 2006-10-23
> **Big Fish said:**
> I give up. It locked up at the "probing" part again, with the good memory. :(it just sounds like you are one of the very few unlucky people with your hardware.  sorry man, i wish i could help you out here.   :(

---

### Post by user1397 on 2006-10-23
***EDIT: Alrite, i have finally updated the guide, now it only has the "new" guide, not the old conventional guide, because i feel that my script is quite stable.  But of course, if there are any errors, please feel free to ask me here on this thread, or u can PM me, or you can ask the tovid forums people (the link is on the guide itself, at the bottom).

---

### Post by mssever on 2006-10-23
> **erik1397 said:**
> 
```
chmod +x installtovid.sh
./installtovid.sh
```<snip>```
chmod +x removetovid.sh
./removetovid.sh
```
For a more foolproof command, try this: ```
chmod +x installtovid.sh && ./installtovid.sh
``` and ```
chmod +x removetovid.sh && ./removetovid.sh
```> ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------These separators cause a lot of horizontal scrolling on my 1024x768 screen. This makes it really annoying to try to read the howto. Please use shorter lines, or do something like ```
- - - - - - - -
``` (note the spaces), or better yet, remove them entirely and use headings in a large font instead. (BTW, the majority of computer users use 1024x768 and most inexpensive LCD displays--including laptops--are only designed to run at 1024x768.)

---

### Post by wolf202 on 2006-10-24
works great but a 700 xvid file comes out to 4.8 gigs is there an option to compress?

---

### Post by biff on 2006-10-24
Has anyone experienced ac3 2 channel output on all avi conversions?  I've been using the tovid cli with -pal -wide -ffmpeg (and without ffmpeg) and every time I get ac3 2 channel with no option to select 5.1 on the dvd player.

Am I missing something here?

---

### Post by user1397 on 2006-10-24
> **mssever said:**
> For a more foolproof command, try this: ```
chmod +x installtovid.sh && ./installtovid.sh
``` and ```
chmod +x removetovid.sh && ./removetovid.sh
```These separators cause a lot of horizontal scrolling on my 1024x768 screen. This makes it really annoying to try to read the howto. Please use shorter lines, or do something like ```
- - - - - - - -
``` (note the spaces), or better yet, remove them entirely and use headings in a large font instead. (BTW, the majority of computer users use 1024x768 and most inexpensive LCD displays--including laptops--are only designed to run at 1024x768.)hmm, your suggestions look pretty good, i forgot about resolution problems.  i'll edit the howto in a bit

---

### Post by user1397 on 2006-10-24
> **wolf202 said:**
> works great but a 700 xvid file comes out to 4.8 gigs is there an option to compress?
did you delete previous encoded video folders and files, before you began to encode the new one?  you have to erase everything in the directory where you encode stuff, or else, videos build up on each other, and you'll get bigger files.

---

### Post by TooRight on 2006-10-24
Greattt tutorial!! I tested it last night on converting an avi... was a lil freaked out by the file size increase, but i can deal with that. I didn't burn it however because the conversion changed the resolution and made the movie look like you were viewing it from some crazed "looking down on everything" angle. It seemed to squish everything up from side to side, making everything seem extremely tall and skinny. Is there anything I can edit that will keep my wide screen movies wide screen?

---

### Post by user1397 on 2006-10-24
> **TooRight said:**
> Greattt tutorial!! I tested it last night on converting an avi... was a lil freaked out by the file size increase, but i can deal with that. I didn't burn it however because the conversion changed the resolution and made the movie look like you were viewing it from some crazed "looking down on everything" angle. It seemed to squish everything up from side to side, making everything seem extremely tall and skinny. Is there anything I can edit that will keep my wide screen movies wide screen?when you were choosing the options for the video, did you choose widescreen?  (default is 4:3 ratio)

---

### Post by PapaWiskas on 2006-10-24
> **TooRight said:**
> Greattt tutorial!! I tested it last night on converting an avi... was a lil freaked out by the file size increase, but i can deal with that. I didn't burn it however because the conversion changed the resolution and made the movie look like you were viewing it from some crazed "looking down on everything" angle. It seemed to squish everything up from side to side, making everything seem extremely tall and skinny. Is there anything I can edit that will keep my wide screen movies wide screen?

Go into the whatevernameyouchose.xml file created for dvdauthor and I added the line after <titles>:
<video aspect="16:9" widescreen="nopanscan" /> 

I am not reading through this whole thread to tell if you are using GUI, which I dont use...or command line, which I do use.

The above edit will make sure your widescreen aspect ratio will hold true on widescreen tvs, and on standard tvs you will have the black bars above and below.

---

### Post by user1397 on 2006-10-24
> **PapaWiskas said:**
> Go into the whatevernameyouchose.xml file created for dvdauthor and I added the line after <titles>:
<video aspect="16:9" widescreen="nopanscan" /> 

I am not reading through this whole thread to tell if you are using GUI, which I dont use...or command line, which I do use.

The above edit will make sure your widescreen aspect ratio will hold true on widescreen tvs, and on standard tvs you will have the black bars above and below.ah, i didn't know the fix was that simple.  thanks man, now i know that for the future.

---

### Post by PapaWiskas on 2006-10-24
> **erik1397 said:**
> ah, i didn't know the fix was that simple.  thanks man, now i know that for the future.

No problem erikdude...glad to help.:mrgreen:

---

### Post by user1397 on 2006-10-27
***EDIT: updated the guide again, this time i made a zip file containg the install and removal scripts.  i thought it was easier, plus, to gt it you have to become a member!  (it's an attachment)

---

### Post by user1397 on 2006-10-28
***EDIT AGAIN: modified the script; now i finally included the source tarball of tovid, instead of deb packages, it's just cleaner (and a lot easier to write in my script:))

---

### Post by nightjar on 2006-10-28
Excellent !!!
In other way: do you know how how to add/ paste subtitles at this DVD format?

---

### Post by nightjar on 2006-10-28
Excellent !!!
In other way: do you know how to add/ paste subtitles at this DVD format?

---

### Post by tzulberti on 2006-10-28
I am getting the following message when trying to open tovid:
/usr/local/bin/tovid-init: 299: Syntax error: Bad substitution

---

### Post by user1397 on 2006-10-28
> **nightjar said:**
> Excellent !!!
In other way: do you know how to add/ paste subtitles at this DVD format?nope, i don't know how to do that, sorry!

---

### Post by user1397 on 2006-10-28
> **tzulberti said:**
> I am getting the following message when trying to open tovid:
/usr/local/bin/tovid-init: 299: Syntax error: Bad substitutioni know the exact fix for this.  actually, this is a little "bug" of tovid-0.28, only happens in edgy, and it only affects the command line version of tovid.  when i log into ubuntu (im on windows now) i'll tell you how to fix this.

EDIT: okay im logged into ubuntu now.  what you have to do is, type in a terminal: ```
gksudo gedit /usr/local/bin/tovid
``` now, do you see the first line?  it starts with **#!/bin/sh** right?  change that first line to **#!/usr/bin/env bash** , save it and close gedit,  and it should work.

also, if you would like to use the other command line scripts that came with tovid, do the same thing as with the tovid script above, but just change the name accordingly.  All of the scripts are: idvid, makedvd, makemenu, makeslides, makexml, postproc, todisc, and tovid. All of these scripts are located in /usr/local/bin.  So for example you would type: ```
gksudo gedit /usr/local/bin/makemenu
```and edit the first line exactly how I explained for tovid.

this little "bug" is already on the tovid website: [http://tovid.wikia.com/wiki/Common_t...h_.28Ubuntu.29]("http://tovid.wikia.com/wiki/Common_tovid_problems#.2Fbin.2Fsh_link_doesn.27t_point_to_bash_.28Ubuntu.29")

---

### Post by tzulberti on 2006-10-30
Thanks a lot, that solved my problem..
:D :D

---

### Post by johnward on 2006-11-02
hi erik1397,
Downloaded your scripts - thanks a lot.

There is a minor error in your script. You need to cd .. before the line

'Moving the tovid icon to the correct folder.'

The icon, desktop, and mkiso script files are in the parent directory and script is running inside tovid-0.28 directory at that point.

John

---

### Post by user1397 on 2006-11-02
> **johnward said:**
> hi erik1397,
Downloaded your scripts - thanks a lot.

There is a minor error in your script. You need to cd .. before the line

'Moving the tovid icon to the correct folder.'

The icon, desktop, and mkiso script files are in the parent directory and script is running inside tovid-0.28 directory at that point.

John
i'll get on this ASAP, not ubuntu right now, but i will be later.  thanks for pointing this out.

---

### Post by lime4x4 on 2006-11-03
fresh install of edgy.The script seems to have worked.Well it did install tovid but when i try to make a dvd from a movie i get an error about an error has occured while encoding here is the log. But i don't c any errors

The following commands will be run:
=========================================
makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "super.mpg" -out "/tmp/Untitled_menu_1"
------------------------
tovid -overwrite -ntsc -dvd -full -in "/home/john/Desktop/movie/super.mpg" -out "/tmp/super.mpg.tovid_encoded"
------------------------
makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/super.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "super.mpg" -out "/tmp/Untitled_menu_1"
Running command: tovid -overwrite -ntsc -dvd -full -in "/home/john/Desktop/movie/super.mpg" -out "/tmp/super.mpg.tovid_encoded"
Running command: makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/super.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"

I also get this error when starting tovidgui from the command line

john@john-edgy:~$ tovidgui

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by user1397 on 2006-11-03
> **lime4x4 said:**
> fresh install of edgy.The script seems to have worked.Well it did install tovid but when i try to make a dvd from a movie i get an error about an error has occured while encoding here is the log. But i don't c any errors

The following commands will be run:
=========================================
makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "super.mpg" -out "/tmp/Untitled_menu_1"
------------------------
tovid -overwrite -ntsc -dvd -full -in "/home/john/Desktop/movie/super.mpg" -out "/tmp/super.mpg.tovid_encoded"
------------------------
makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/super.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "super.mpg" -out "/tmp/Untitled_menu_1"
Running command: tovid -overwrite -ntsc -dvd -full -in "/home/john/Desktop/movie/super.mpg" -out "/tmp/super.mpg.tovid_encoded"
Running command: makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/super.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"

I also get this error when starting tovidgui from the command line

john@john-edgy:~$ tovidgui

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(python:6926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",so what happens afer those commands are run?  like what happens next?  or does it just hang?

and when you open tovidgui from the terminal, does it still open ok and look ok?

---

### Post by user1397 on 2006-11-03
> **nightjar said:**
> Excellent !!!
In other way: do you know how to add/ paste subtitles at this DVD format?
the instructions for this are here: [http://tovid.sourceforge.net/manpages/tovid.html#toc9](http://tovid.sourceforge.net/manpages/tovid.html#toc9)

meaning, you have to run tovid from the command line.  if you live in the us, and if you have a widescreen tv, then you would probably just do ```
tovid -wide -subtitle FILE -in movie.avi -out movie_encoded
```where FILE is your subtitle file, and movie is your original avi file.  you have to have a subtitle file for this to work, and you can't turn them off when you're watching the movie.

---

### Post by lime4x4 on 2006-11-03
yes it opens and looks ok
when i hit the start encode button it pops about it incountered an error while encoding but i can't find an error log anywhere

---

### Post by lime4x4 on 2006-11-03
ok i think i found the probelm.For some reason removetovid.sh,mkiso,installtovid.sh are installed on my desktop
Which folders do they belong in?

---

### Post by skydivingbiker on 2006-11-03
Im no Linux master but... have you searched for libtovid in any of the package installers? (Synaptic)

IM new to Ubuntu, but most of my errors are caused because I need special do-hickeys installed.

---

### Post by user1397 on 2006-11-03
> **skydivingbiker said:**
> Im no Linux master but... have you searched for libtovid in any of the package installers? (Synaptic)

IM new to Ubuntu, but most of my errors are caused because I need special do-hickeys installed.libtovid does not exist in the ubuntu repositories.  what little do-hickeys do you need?  what problems have made you install more dependencies, and which dependencies?

i need more info!

---

### Post by fatboysmith on 2006-11-04
> **erik1397 said:**
> i know the exact fix for this.  actually, this is a little bug of the 0.28 version, only happens in edgy i think, and it only affects the command line version of tovid.  when i log into ubuntu (im on windows now) i'll tell you how to fix this.

EDIT: okay im logged into ubuntu now.  what you have to do is, type in a terminal: ```
gksudo gedit /usr/local/bin/tovid
``` now, do you see the first line?  it starts with like **#!/bin/sh** or something?  change that first line to **#!/usr/bin/env bash** , save it and close gedit,  and it should work.

Dude!  That is great.  You should send this to the ToVid folk(s) and ask them to add it to the installation portion of the website.
Thanks

Dennis

---

### Post by user1397 on 2006-11-05
> **fatboysmith said:**
> Dude!  That is great.  You should send this to the ToVid folk(s) and ask them to add it to the installation portion of the website.
Thanks

Dennisedit:  this already exists: [http://tovid.wikia.com/wiki/Common_tovid_problems#.2Fbin.2Fsh_link_doesn.27t_point_to_bash_.28Ubuntu.29](http://tovid.wikia.com/wiki/Common_tovid_problems#.2Fbin.2Fsh_link_doesn.27t_point_to_bash_.28Ubuntu.29)

---

### Post by rado_london on 2006-11-05
I have a problem. When I click "Start encoding" I get the following message:

```
Error(s) occurred during encoding. If you want to
help improve this software, please file a bug report
containing a copy of the output log. Unfortunately,
this also means you won't be able to continue with
creating your disc. Sorry for the inconvenience!
```

I also attach a screenshot.

Help me please.

---

### Post by user1397 on 2006-11-05
> **rado_london said:**
> I have a problem. When I click "Start encoding" I get the following message:

```
Error(s) occurred during encoding. If you want to
help improve this software, please file a bug report
containing a copy of the output log. Unfortunately,
this also means you won't be able to continue with
creating your disc. Sorry for the inconvenience!
```I also attach a screenshot.

Help me please.this might just be one of the times when the tovid gui is too buggy.  you can try the command line if you wish,  i can guide you.  first i need some info so that you can make the correct type of dvd.

first of all, what continent do you live on? (this will determine wheher you need NTSC or PAL format)

do you have a regular tv (4:3 ratio) or a widescreen tv (16:9)?

how big (in GB) is your original avi file?

---

### Post by rado_london on 2006-11-05
> **erik1397 said:**
> this might just be one of the times when the tovid gi is too buggy.  you can try the command line if you wish,  i can guide you.  first i need some info so that you can make the correct type of dvd.

first of all, what continent do you live on? (this will determine wheher you need NTSC or PAL format)

do you have a regular tv (4:3 ratio) or a widescreen tv (16:9)?

how big (in GB) is your original avi file?

I live in UK and AFAIK the format should be PAL. I would like to watch it on widescreen TV. The original size of the AVI file is 1.2GB. I would also like to add a wallpaper to the menu. The wallpaper is located in /home/rado/Desktop/Godfather.jpg. I would also like to add a background sound for the menu which is in /home/rado/godfather-theme.mp3. I also have subtitles in SUB format but I am not sure if I can add them. If I can it would be great. Thank you very much indeed.

---

### Post by user1397 on 2006-11-05
> **rado_london said:**
> I live in UK and AFAIK the format should be PAL. I would like to watch it on widescreen TV. The original size of the AVI file is 1.2GB. I would also like to add a wallpaper to the menu. The wallpaper is located in /home/rado/Desktop/Godfather.jpg. I would also like to add a background sound for the menu which is in /home/rado/godfather-theme.mp3. I also have subtitles in SUB format but I am not sure if I can add them. If I can it would be great. Thank you very much indeed.im guessing this is the command you want for your video:
```
tovid -pal -wide -quality 7 -discsize 4380 -subtitles *FILE* -in YourVideo.avi -out YourVideo_encoded
```  (replace *FILE*, and both "YourVideo" )

for your menu, try:
```
makemenu -pal -background *IMAGE* -audio *FILE* "Title" -out MainMenu
``` (replacing *IMAGE, FILE, *and the Title to whatever you want, respectively.)

---

### Post by user1397 on 2006-11-06
> **lime4x4 said:**
> ok i think i found the probelm.For some reason removetovid.sh,mkiso,installtovid.sh are installed on my desktop
Which folders do they belong in?they dont belong in any folder.  mkiso should be in /usr/bin (if its not, use this command to get it there--```
cd ~/Desktop
sudo mv mkiso /usr/bin/
```
installtovid.sh and removetovid.sh can be anywhere.

---

### Post by rado_london on 2006-11-06
> **erik1397 said:**
> im guessing this is the command you want for your video:
```
tovid -pal -wide -quality 7 -discsize 4380 -subtitles *FILE* -in YourVideo.avi -out YourVideo_encoded
```  (replace *FILE*, and both "YourVideo" )

for your menu, try:
```
makemenu -pal -background *IMAGE* -audio *FILE* "Title" -out MainMenu
``` (replacing *IMAGE, FILE, *and the Title to whatever you want, respectively.)

Great I just finished watching The Godfather on my tv. Thanks again.

---

### Post by user1397 on 2006-11-06
> **rado_london said:**
> Great I just finished watching The Godfather on my tv. Thanks again.wait, so all my commands worked out for you???

---

### Post by user1397 on 2006-11-06
***New Tovid version out - - - 0.29
Will update this guide soon.

---

### Post by rado_london on 2006-11-06
> **erik1397 said:**
> wait, so all my commands worked out for you???

The menu one didnt work as I got the line 299 error. I changed the tovid-init file (edited the first line), but I still had that error. Then I realised I dont need the menu and skiped it. And it worked beautifully:-D 

Also to make mkiso worked I used:
```
sudo ./mkiso and the other commands
```

---

### Post by user1397 on 2006-11-06
> **rado_london said:**
> The menu one didnt work as I got the line 299 error. I changed the tovid-init file (edited the first line), but I still had that error. Then I realised I dont need the menu and skiped it. And it worked beautifully:-D 

Also to make mkiso worked I used:
```
sudo ./mkiso and the other commands
```awesome.  i just learned how to handle the tovid command line recently, glad i could help someone with it.  weird command you used - - ./mkiso :-k o well, if it worked, then what the hell...

btw, to make makemenu work, you should do the same thing to it as i suggested for the tovid script - - change that first line.

actually, i'll edit that post so that it makes more sense.

---

### Post by user1397 on 2006-11-07
***Updated the script.  New tovid version included, and fixd a tiny bug involving cd'ing before moving the extra items.  thanks johnward!

---

### Post by user1397 on 2006-11-09
***I updated the guide yesterday.  I decided that that whole zip file thingie didn't really work too well, so I decided to go back to the old way of doing things.  Now you just have to download the script, give it exec permissions, and run it.  no more messing with little zip files.

---

### Post by user1397 on 2006-11-10
***Updated the guide again, was a little confusing and wordy.

---

### Post by user1397 on 2006-11-11
***Yet another update.  This time, I updated the scripts, because it was basically useless and did not work.  Now it should work pretty well.  The only note to take here is that i'm using checkinstall to make a deb package from the tarball, so you have to just go with the defaults during the checkinstall installation.  as soon as the 0.29 ubuntu deb gets put up on the tovid site, i'll switch to that instead.

---

### Post by user1397 on 2006-11-14
***Update, though kinda minor, it is easier.  I had the main tovid guy upload my checkinstall-made tovid deb package to the main tovid site, so the script now just downloads a deb package, and hence is easier to install.

---

### Post by user1397 on 2006-11-14
alright i realize that the tovid GUI isn't working for u all, its just that the new tovid version (0.29) needs one more dependency, so I will add that when I can.

---

### Post by user1397 on 2006-11-16
***got it fixed. script should work now.  btw, there's also a new gui called the todisc gui, which can create a DVD with animated menus.  it is not supposed to replace the tovid gui, its complimentary to it.

the command for it is: [B]todiscgui

EDIT[/B]: actually, i just found out that the todiscgui is not quite functional yet....but they're working hard on it.

---

### Post by tzulberti on 2006-11-16
I reccomend a program called DeVeDe (apt-get install DeVeDe vcdimage)

---

### Post by user1397 on 2006-11-16
> **tzulberti said:**
> I reccomend a program called DeVeDe (apt-get install DeVeDe vcdimage)actually, i've tried devede, and though it might work for some people, it did not work for me at all.  plus, tovid's capabilities are nearly limitless compared with devede.

---

### Post by breakerfall on 2006-11-20
hiya,

is there any way to easily change the directory that tovid is using as a temp?  it seems to want to create a working directory in my homedir, where i dont have a huge amount of space.  i have changed the dir for the output file, but i dont see an option to change the working dir...

any ideas?

---

### Post by user1397 on 2006-11-20
> **breakerfall said:**
> hiya,

is there any way to easily change the directory that tovid is using as a temp?  it seems to want to create a working directory in my homedir, where i dont have a huge amount of space.  i have changed the dir for the output file, but i dont see an option to change the working dir...

any ideas?you're using the gui or the command line?  (and also, what directory are you proposing for your working dir? )

---

### Post by PapaWiskas on 2006-11-20
> **breakerfall said:**
> hiya,

is there any way to easily change the directory that tovid is using as a temp?  it seems to want to create a working directory in my homedir, where i dont have a huge amount of space.  i have changed the dir for the output file, but i dont see an option to change the working dir...

any ideas?

using nautilus or thunar or whatever your file manager is, go into your hidden directory named .tovid

inside there is a preferences file...open with a text editor....there you will see what you need to edit for working directory and output directory etc....

the example looks as follows...

# tovid preferences
# Configures working/output directories for tovid
#WORKING_DIR=/tmp
#OUTPUT_DIR=/video/outfiles

get rid of the # and set your directories.

Good luck.

---

### Post by breakerfall on 2006-11-21
> **PapaWiskas said:**
> using nautilus or thunar or whatever your file manager is, go into your hidden directory named .tovid

inside there is a preferences file...open with a text editor....there you will see what you need to edit for working directory and output directory etc....

the example looks as follows...

# tovid preferences
# Configures working/output directories for tovid
#WORKING_DIR=/tmp
#OUTPUT_DIR=/video/outfiles

get rid of the # and set your directories.

Good luck.

awesome, that worked...

thanks!

---

### Post by PapaWiskas on 2006-11-21
> **breakerfall said:**
> awesome, that worked...

thanks!


Glad to have helped.:-D

---

### Post by user1397 on 2006-11-21
> **PapaWiskas said:**
> Glad to have helped.:-Ddidn't think about the tovid.preferences folder, do u know if that applies to the gui and the command line?

---

### Post by breakerfall on 2006-11-21
> **erik1397 said:**
> didn't think about the tovid.preferences folder, do u know if that applies to the gui and the command line?

well, I'm using the GUI, and while i do still have to set the 'output' directory in the gui, the resulting process seems to obey the paths i set in the prefs file.

---

### Post by PapaWiskas on 2006-11-22
The last time I used the GUI it way to many issues and it frustrated me.  I never looked back once I switched to the command line, to me its just easier.

I would think the GUI should reference the preferences though, so my stated method should work.  However if memory serves me correctly I think you are forced to give a output directory when using the GUI aren't you?  I cant remember...LOL....anyway, glad it worked out for you.  ;)

---

### Post by user1397 on 2006-11-22
> **PapaWiskas said:**
> The last time I used the GUI it way to many issues and it frustrated me.  I never looked back once I switched to the command line, to me its just easier.

I would think the GUI should reference the preferences though, so my stated method should work.  However if memory serves me correctly I think you are forced to give a output directory when using the GUI aren't you?  I cant remember...LOL....anyway, glad it worked out for you.  ;)yea i think it probably references to the tovid.preferences file.  you aren't forced to give an output directory, it's just optional (it defaults it to /tmp)

and yea i like the command line so much better, once i got the hang of it. when i learn python, i'll be sure to help out the tovid project as much as possible.

---

### Post by j3cakes on 2006-11-23
I've just read most of this thread and my brain's about to explode.

What do I need to do to get this working - is the guide at the start still accurate and the link to the script(s) still the one I need to follow? The thread references three versions of tovid since the guide was first posted.

I also need to change the working directory to not be my home dir due to space restrictions so can I still use the script?

---

### Post by user1397 on 2006-11-23
> **j3cakes said:**
> I've just read most of this thread and my brain's about to explode.

What do I need to do to get this working - is the guide at the start still accurate and the link to the script(s) still the one I need to follow? The thread references three versions of tovid since the guide was first posted.

I also need to change the working directory to not be my home dir due to space restrictions so can I still use the script?sorry about any confusion you may have, but the first post in this thread is always the most up-to-date post here.  that is where the guide is found.  to change the working dir, just follow papawiskas instructions here: [http://ubuntuforums.org/showthread.php?p=1785834#post1785834](http://ubuntuforums.org/showthread.php?p=1785834#post1785834)

---

### Post by user1397 on 2006-11-24
***small update: finally, i was able to put all of my script stuff into the official tovid ubuntu site: [http://tovid.sourceforge.net/download/ubuntu](http://tovid.sourceforge.net/download/ubuntu)

so all downloads are from there, officially. (not a big change, but cool nonetheless)

also, if i have not already mentioned this, jdong, one of the forum members here, made an architecture-independent tovid package, meaning that it doesn't matter if you have an x86 (i386) PC, or an x86_64 (amd64) PC, it works on everything (well except PowerPC)

and i have already included that package in the install script, so it's all good.

---

### Post by j3cakes on 2006-11-25
maybe I'm just doing it wrong....

I did what you said in the first post - downloaded the script and pasted that command in but I've tried it twice now and I keep getting:

> 
Installing tovid.

Selecting previously deselected package tovid.
(Reading database ... 78451 files and directories currently installed.)
Unpacking tovid (from tovid_0.29-0jdong1_all.deb) ...
dpkg: dependency problems prevent configuration of tovid:
 tovid depends on mplayer; however:
  Package mplayer is not installed.
 tovid depends on mencoder; however:
  Package mencoder is not installed.
 tovid depends on mjpegtools; however:
  Package mjpegtools is not installed.
 tovid depends on transcode; however:
  Package transcode is not installed.
dpkg: error processing tovid (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tovid


I can install all that stuff manually but I thought the script would do it for me... or am I just being thick? :)

if I do "apt-get install -f" it fixes it all up (ie removes tovid) but I'd like to have this in and working.

Should I just install the programs listed above manually?

---

### Post by user1397 on 2006-11-25
> **j3cakes said:**
> maybe I'm just doing it wrong....

I did what you said in the first post - downloaded the script and pasted that command in but I've tried it twice now and I keep getting:



I can install all that stuff manually but I thought the script would do it for me... or am I just being thick? :)

if I do "apt-get install -f" it fixes it all up (ie removes tovid) but I'd like to have this in and working.

Should I just install the programs listed above manually?give me the full ouput of the script when you run it.

---

### Post by j3cakes on 2006-11-25
do you want me to post all of it here?

---

### Post by user1397 on 2006-11-25
> **j3cakes said:**
> do you want me to post all of it here?yep!

---

### Post by j3cakes on 2006-11-26
ok, here goes. This is after I ran automatix to install mplayer and its dependencies. 

This is the error dialogue box I get:

> 
Error(s) occurred during encoding. If you want to help improve this software, please file a bug report containing a copy of the output log. Unfortunately, this also means you won't be able to continue with creating your disc. Sorry for the inconvenience!


This is the log from my attempts at getting it to convert an avi

> 
The following commands will be run:
=========================================
makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "whatever.avi" -out "/tmp/Untitled_menu_1"
------------------------
tovid -overwrite -ntsc -dvd -full -in "/media/Maxtor 300Gb/Storage/My Videos/Movies and TV/Movies/whatever.avi" -out "/tmp/whatever.avi.tovid_encoded"
------------------------
makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/whatever.avi.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "whatever.avi" -out "/tmp/Untitled_menu_1"
You are missing tovid CORE dependencies!

  mplayer       MISSING: mplayer_msg
  mencoder      MISSING: mencoder_msg
  mplex         MISSING: mplex_msg
  mpeg2enc      MISSING: mpeg2enc_msg
  yuvfps        MISSING: yuvfps_msg
  yuvdenoise    MISSING: yuvdenoise_msg
  ppmtoy4m      MISSING: ppmtoy4m_msg
  mp2enc        MISSING: mp2enc_msg
  jpeg2yuv      MISSING: jpeg2yuv_msg

Please install the above MISSING dependencies, run 'tovid -refresh-deps', and try again.
Running command: tovid -overwrite -ntsc -dvd -full -in "/media/Maxtor 300Gb/Storage/My Videos/Movies and TV/Movies/whatever.avi" -out "/tmp/whatever.avi.tovid_encoded"
You are missing tovid CORE dependencies!

  mplayer       MISSING: mplayer_msg
  mencoder      MISSING: mencoder_msg
  mplex         MISSING: mplex_msg
  mpeg2enc      MISSING: mpeg2enc_msg
  yuvfps        MISSING: yuvfps_msg
  yuvdenoise    MISSING: yuvdenoise_msg
  ppmtoy4m      MISSING: ppmtoy4m_msg
  mp2enc        MISSING: mp2enc_msg
  jpeg2yuv      MISSING: jpeg2yuv_msg

Please install the above MISSING dependencies, run 'tovid -refresh-deps', and 
try again.
Running command: makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/whatever.avi.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
You are missing tovid CORE dependencies!

  mplayer       MISSING: mplayer_msg
  mencoder      MISSING: mencoder_msg
  mplex         MISSING: mplex_msg
  mpeg2enc      MISSING: mpeg2enc_msg
  yuvfps        MISSING: yuvfps_msg
  yuvdenoise    MISSING: yuvdenoise_msg
  ppmtoy4m      MISSING: ppmtoy4m_msg
  mp2enc        MISSING: mp2enc_msg
  jpeg2yuv      MISSING: jpeg2yuv_msg

Please install the above MISSING dependencies, run 'tovid -refresh-deps', and 
try again.


and this is the output from running the script:

> 
jason@jason-desktop:~/Downloads$ chmod +x installtovid.sh && ./installtovid.sh

Downloading and installing all dependencies for tovid.

Get: 1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get: 2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 8B in 60s (0B/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving ‘gb.archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Temporary failure resolving ‘archive.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
mplayer is already the newest version.
mencoder is already the newest version.
mjpegtools is already the newest version.
ffmpeg is already the newest version.
python is already the newest version.
python-wxgtk2.6 is already the newest version.
python-imaging is already the newest version.
imagemagick is already the newest version.
dvdauthor is already the newest version.
dvd+rw-tools is already the newest version.
vcdimager is already the newest version.
sox is already the newest version.
normalize-audio is already the newest version.
txt2tags is already the newest version.
The following extra packages will be installed:
  gawk libavifile-0.7c2 libfame-0.9 libpvm3 python2.4-dev
Suggested packages:
  avifile-player avifile-utils avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin
  avifile-divx-plugin libc6-dev libc-dev libdvdcss xvid4conf
Recommended packages:
  pvm toolame transcode-doc
The following NEW packages will be installed
  gawk libavifile-0.7c2 libfame-0.9 libpvm3 lsdvd python-cairo python-dev python2.4-dev transcode
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7MB of archives.
After unpacking 55.6MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main gawk 1:3.1.5-2build1 [833kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main python2.4-dev 2.4.3-0ubuntu6 [1464kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse libfame-0.9 0.9.0-0.1 [77.7kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse lsdvd 0.15-5 [14.3kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse transcode 2:1.0.2-0.0ubuntu2 [14.5MB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe libavifile-0.7c2 1:0.7.44.20051021-1ubuntu2 [1746kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main python-cairo 1.0.2-1ubuntu1 [30.3kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main python-dev 2.4.2-0ubuntu3 [7274B]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe libpvm3 3.4.5-6 [82.5kB]
Fetched 18.7MB in 5m11s (60.1kB/s)
Selecting previously deselected package gawk.
(Reading database ... 81610 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.5-2build1_i386.deb) ...
Selecting previously deselected package libavifile-0.7c2.
Unpacking libavifile-0.7c2 (from .../libavifile-0.7c2_1%3a0.7.44.20051021-1ubuntu2_i386.deb) ...
Selecting previously deselected package libfame-0.9.
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.0-0.1_i386.deb) ...
Selecting previously deselected package lsdvd.
Unpacking lsdvd (from .../archives/lsdvd_0.15-5_i386.deb) ...
Selecting previously deselected package python-cairo.
Unpacking python-cairo (from .../python-cairo_1.0.2-1ubuntu1_all.deb) ...
Selecting previously deselected package python2.4-dev.
Unpacking python2.4-dev (from .../python2.4-dev_2.4.3-0ubuntu6_i386.deb) ...
Selecting previously deselected package python-dev.
Unpacking python-dev (from .../python-dev_2.4.2-0ubuntu3_all.deb) ...
Selecting previously deselected package libpvm3.
Unpacking libpvm3 (from .../libpvm3_3.4.5-6_i386.deb) ...
Selecting previously deselected package transcode.
Unpacking transcode (from .../transcode_2%3a1.0.2-0.0ubuntu2_i386.deb) ...
Setting up gawk (3.1.5-2build1) ...

Setting up libavifile-0.7c2 (0.7.44.20051021-1ubuntu2) ...

Setting up libfame-0.9 (0.9.0-0.1) ...

Setting up lsdvd (0.15-5) ...
Setting up python-cairo (1.0.2-1ubuntu1) ...
Setting up python2.4-dev (2.4.3-0ubuntu6) ...

Setting up python-dev (2.4.2-0ubuntu3) ...
Setting up libpvm3 (3.4.5-6) ...

Setting up transcode (1.0.2-0.0ubuntu2) ...

Downloading tovid.

--21:20:10--  [http://tovid.sourceforge.net/download/ubuntu/tovid_0.29-0jdong1_all.deb](http://tovid.sourceforge.net/download/ubuntu/tovid_0.29-0jdong1_all.deb)
           => `tovid_0.29-0jdong1_all.deb'
Resolving tovid.sourceforge.net... 66.35.250.209
Connecting to tovid.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 495,872 (484K) [text/plain]

100%[======================================================================================================>] 495,872       47.47K/s    ETA 00:00

21:20:25 (39.61 KB/s) - `tovid_0.29-0jdong1_all.deb' saved [495872/495872]


Installing tovid.

Selecting previously deselected package tovid.
(Reading database ... 82226 files and directories currently installed.)
Unpacking tovid (from tovid_0.29-0jdong1_all.deb) ...
Setting up tovid (0.29-0jdong1) ...

Downloading the tovid icon, the mkiso script, and the tovid menu entry.

--21:20:25--  [http://images.wikia.com/tovid/images/2/2c/Tovid_icon.png](http://images.wikia.com/tovid/images/2/2c/Tovid_icon.png)
           => `Tovid_icon.png'
Resolving images.wikia.com... 216.224.121.136
Connecting to images.wikia.com|216.224.121.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,968 (20K) [image/png]

100%[======================================================================================================>] 19,968         2.37K/s    ETA 00:00

21:20:41 (2.37 KB/s) - `Tovid_icon.png' saved [19968/19968]

--21:20:41--  [http://tovid.sourceforge.net/download/ubuntu/install_script/mkiso](http://tovid.sourceforge.net/download/ubuntu/install_script/mkiso)
           => `mkiso'
Resolving tovid.sourceforge.net... 66.35.250.209
Connecting to tovid.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129 [text/plain]

100%[======================================================================================================>] 129           --.--K/s

21:20:43 (12.30 MB/s) - `mkiso' saved [129/129]

--21:20:43--  [http://tovid.sourceforge.net/download/ubuntu/install_script/tovid.desktop](http://tovid.sourceforge.net/download/ubuntu/install_script/tovid.desktop)
           => `tovid.desktop'
Resolving tovid.sourceforge.net... 66.35.250.209
Connecting to tovid.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 343 [text/plain]

100%[======================================================================================================>] 343           --.--K/s

21:20:49 (32.71 MB/s) - `tovid.desktop' saved [343/343]

Moving the tovid icon to the correct folder.

Moving the menu entry to the correct folder.

Giving the mkiso script executable permissions.

Moving the mkiso script to the correct folder.

Removing debian package (not needed anymore).
You have successfully installed tovid.  If it is not in the menus, the command for the tovid GUI is: tovidgui


I noticed that there are a couple of 'failure to resolve' errors but it looks like it eventually found the targets.

Any ideas?

I haven't tried running the 'tovid -refresh-deps' because the programs should already be installed.

---

### Post by user1397 on 2006-11-26
> **j3cakes said:**
> ok, here goes. This is after I ran automatix to install mplayer and its dependencies. 

This is the error dialogue box I get:



This is the log from my attempts at getting it to convert an avi



and this is the output from running the script:



I noticed that there are a couple of 'failure to resolve' errors but it looks like it eventually found the targets.

Any ideas?

I haven't tried running the 'tovid -refresh-deps' because the programs should already be installed.seems like you have the gpg error in your repos...let's see...
try these commands in a a terminal:
[FONT=monospace]
[/FONT]```
wget http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg -O- | sudo apt-key add -
``````
wget http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg -O- | sudo apt-key add -
``````
wget http://archive.ubuntu.com/dapper-backports/Release.gpg -O- | sudo apt-key add -
``````
wget http://gb.archive.ubuntu.com/dapper/Release.gpg-O- | sudo apt-key add -
```and then try: ```
sudo aptitude update
```
then try running the tovid script again, and then try running: ```
tovid -refresh-deps
```

---

### Post by j3cakes on 2006-11-27
ok. thanks erik, I'll give it a go when I get home from work tonight.

---

### Post by j3cakes on 2006-11-27
I got the following error:

> 
jason@jason-desktop:~$ wget [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg) -O- | sudo apt-key add -
--18:26:31--  [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
           => `-'
Resolving gb.archive.ubuntu.com... 195.248.90.35, 195.248.90.38
Connecting to gb.archive.ubuntu.com|195.248.90.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 189 [text/plain]

100%[====================================>] 189           --.--K/s

18:26:31 (18.02 MB/s) - `-' saved [189/189]

gpg: no valid OpenPGP data found.


I tried it a couple of times but got the same result.

---

### Post by user1397 on 2006-11-27
> **j3cakes said:**
> I got the following error:



I tried it a couple of times but got the same result.damn...i really don't know what to tell you, I'm not very experienced with the whole apt repo thingie...if i were you, i would try starting a thread on the gpg errors you're getting, because that not only affects your installation of tovid, but potentially many other programs as well.

---

### Post by j3cakes on 2006-11-27
I am having other problems with this install so there's a good chance I've done something completely wrong. It's a fresh install anyway so I might just do a rebuild and see how I go.

I have a windows program from sourceforge that does something similar, I was hoping that ubuntu would free up some system resources to make it go a bit faster (it takes 3-4 hours in windows.)

thanks for your help anyway erik.

---

### Post by user1397 on 2006-11-27
> **j3cakes said:**
> I am having other problems with this install so there's a good chance I've done something completely wrong. It's a fresh install anyway so I might just do a rebuild and see how I go.

I have a windows program from sourceforge that does something similar, I was hoping that ubuntu would free up some system resources to make it go a bit faster (it takes 3-4 hours in windows.)

thanks for your help anyway erik.if you have any other questions, just ask.  i think i know what program you're talking about - dvdshrink, right?  i have it installed on my windows partition, but i've never used it!

and, as i've warned on the first page, you must have at least 20GB free space for the encoding process of tovid to go smoothly.

---

### Post by user1397 on 2006-11-27
I requested a thread title change, and it was granted.  It now more accurately represents what the guide is about.  It used to be: "Howto: Make Dvd Videos from Avi Files" but that is not entirely correct, as tovid not only supports avi files, but many other formats as well.

---

### Post by j3cakes on 2006-11-28
> **erik1397 said:**
> if you have any other questions, just ask.  i think i know what program you're talking about - dvdshrink, right?  i have it installed on my windows partition, but i've never used it!
and, as i've warned on the first page, you must have at least 20GB free space for the encoding process of tovid to go smoothly.

disk space isn't really a problem (200GB free), neither is memory (2Gb) or processor power (3.0Ghz) but it still takes well over three hours. I just figured it was windows being inefficient but that's always just been a guess.

the program, incidentally, is called DVD Flick.

---

### Post by user1397 on 2006-11-28
> **j3cakes said:**
> disk space isn't really a problem (200GB free), neither is memory (2Gb) or processor power (3.0Ghz) but it still takes well over three hours. I just figured it was windows being inefficient but that's always just been a guess.

the program, incidentally, is called DVD Flick.i think its just the buggy tovid gui acting up again, at least for you (dont know why, but it works better for some people, and worse for others...)

if you want to, i could give you specific details on using the command line, which will probably work.

all i need to know is the continent you live on, the aspect ratio of ur tv, and the location (directory) and size of your movie file.  also, where in your hard drive do u have the most free space?

---

### Post by j3cakes on 2006-11-28
> **erik1397 said:**
> 
if you want to, i could give you specific details on using the command line, which will probably work.

that'd be great. see if it works this way.

> all i need to know is the continent you live on, the aspect ratio of ur tv, and the location (directory) and size of your movie file.  also, where in your hard drive do u have the most free space?

- Europe (UK - PAL)
- 16:9
- can you use <locn> and <size> for those two parameters? That way, if I need to, I can apply it to other avi files.
- biggest directory: /storage/video 

another quick question, if I use dvd flick and put the output on a samba share, can I use the tovid CLI commands to make/burn the iso to DVD?

---

### Post by user1397 on 2006-11-28
> **j3cakes said:**
> that'd be great. see if it works this way.



- Europe (UK - PAL)
- 16:9
- can you use <locn> and <size> for those two parameters? That way, if I need to, I can apply it to other avi files.
- biggest directory: /storage/video 

another quick question, if I use dvd flick and put the output on a samba share, can I use the tovid CLI commands to make/burn the iso to DVD?do you mean use the <locn> and <size> in the ~/.tovid/tovid.preferences file?

put your movie file in /storage/video:
```
sudo mv /path/to/file /storage/video
```then cd to the encoding dir:
```
cd /storage/video
```and finally, the tovid command (this is assuming your original video is in avi format, and that you dont want a menu) :
```
tovid -pal -wide -discsize 4380 -in movie_name.avi -out desired_movie_name
```and about the dvd flicker samba thing: its theoretically feasible, but i'm not entirely sure it'll work.  is the file created by dvd flicker an mpeg video?

---

### Post by j3cakes on 2006-11-29
> **erik1397 said:**
> do you mean use the <locn> and <size> in the ~/.tovid/tovid.preferences file?
no, I just meant use the monikers 'locn' and 'size' to show these parameters. 

the file path is /storage/video/movies
the size of the files vary but usually around 700MB.

> 
and about the dvd flicker samba thing: its theoretically feasible, but i'm not entirely sure it'll work.  is the file created by dvd flicker an mpeg video?

no, it creates two directories: AUDIO_TS and VIDEO_TS which, I thought, was the same as tovid.

---

### Post by user1397 on 2006-11-29
> **j3cakes said:**
> no, I just meant use the monikers 'locn' and 'size' to show these parameters. 

the file path is /storage/video/movies
the size of the files vary but usually around 700MB.nope, these don't work as parameters.  to see all possible parameters in tovid, you can use **man tovid** in your terminal, or you can check out the man pages online: [http://tovid.sourceforge.net/manpages/](http://tovid.sourceforge.net/manpages/)

to set the default working dir and output dir for tovid, go to your /home/username/.tovid/tovid.preferences .tovid is a hidden folder---press ctrl+H to view hiddden files and folders in nautilus)

then you should see something like:>  # tovid preferences
# Configures working/output directories for tovid
#WORKING_DIR=/tmp
#OUTPUT_DIR=/video/outfilesfor your case, i would make it look like this:
> # tovid preferences
 # Configures working/output directories for tovid
 WORKING_DIR=/storage/video/
 OUTPUT_DIR=/storage/video/movies/
# Continent-specific format
-pal
# Aspect ratio
-widethen all you would have to do every time u used tovid from the command line, would be ```
tovid -in *Video -out New_Name_of_Video*
```
[quote=j3cakes]no, it creates two directories: AUDIO_TS and VIDEO_TS which, I thought, was the same as tovid.[/quote]actually, the script "tovid" itself does not create those folders...but the script "makexml" (part of the tovid package) does.  you don't have to do the whole makexml part, you could just use the mkiso script to burn the ouput file created by tovid, directly to a dvd.

---

### Post by Robert.Zapata on 2006-12-01
> **erik1397 said:**
> Please post anyone if this method has worked for you, and list any/all issues you may have encountered while taking this tutuorial.  Thank you.

Hello Team and Happy Holidays..!!

**Eric:** Excellent How-to/Guide and Tutorial..!! Thank you very much for your patience and your hard work putting all this together.

Just for curiosity I installed **tovid** in my Lenovo machine following your instructions in the first post, everything went flawless..!!

Just for kicks and grins I give it a try with an AVI file and everything worked great. !! I did not "burn" the DVD because this machine *(Thinkpad)* is not intended for video processing. I will re-install tovid in my Toshiba notebook at home and will complete the whole process to the end *(playable DVD)*

*(I'm at work right now..so not much time to continue testing tovid, but so far, so good)*

Just as a reference, here's my tovid log file *(edited to make it shorter and highlite times in bold)*

In summary it took two hours to encode a 1:50 video.

KUDOS TO YOU AND KEEP DOING A GREAT JOB..!!! *(sorry for the yelling)*


> 
The following commands will be run:
=========================================
makemenu -ntsc -dvd -align northwest -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "Revolver[2005]DvDrip[Eng]-aXXo.avi" -out "/home/rob/tovid/encoding/Untitled_menu_1"
------------------------
tovid -overwrite -ntsc -dvd -wide -in "/home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi" -out "/home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded"
------------------------
makexml -dvd -overwrite -menu "/home/rob/tovid/encoding/Untitled_menu_1.mpg" "/home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.mpg" -out "/home/rob/tovid/encoding/Untitled_disc"
--------------------------------
tovid 
DVD and (S)VCD video conversion script
Version 0.29
with: core magick dvd vcd transcode 
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
tovid command-line used:
-overwrite -ntsc -dvd -wide -in /home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi -out /home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded
Using config file /home/rob/.tovid/tovid.config, containing the following options:
(none)
Changing to working directory: /home/rob

=========================================================

Converting /home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi to compliant NTSC DVD format
Saving to /home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.mpg
Storing log and temporary files in /home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0
Run 'tail -f /home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/tovid.log' in another terminal to monitor the log

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 4622 MB of disk space.
You currently have 43554 MB available in this directory.
Analysis of file /home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi:
  552 x 226 pixels, 25.000 fps
  **Duration (best guess): 01:50:03 (HH:MM:SS)**
  DX50 video with ffmp3 audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  7840 kbits/sec video, 224 kbits/sec audio
Using explicitly provided aspect ratio of 16:9
No letterboxing necessary
Input is not 29.970 fps. Framerate will be adjusted.
Scaling picture to 720 x 480
=========================================================
=========================================================
Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i /home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi -vn -ab 224 -ar 48000 -ac 2 -acodec ac3 -y /home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/audio.ac3
Waiting 30 seconds for output file "audio.ac3" to appear...
Processing started. Please wait...          
Audio encoding finished successfully.
=========================================================
Encoding video stream with the following commands:
nice -n 0 mplayer -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/video.yuv" -vf scale=720:480 "/home/rob/MyDocs/DVD/Revolver[2005]DvDrip[Eng]-aXXo.avi"
cat "/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/video.yuv" | yuvfps -r 30000:1001 -v 0 | nice -n 0 mpeg2enc --sequence-length 4300 --nonvideo-bitrate 304 --aspect 3 -f 8 -b 7840 -g 4 -G 11 -D 10 -K hi-res --frame-rate 4 -v 0 --video-norm n --reduction-4x4 2 --reduction-2x2 1 -q 5 -o "/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/video.m2v"

Processing started. Please wait...                                               
Waiting 30 seconds for output file "video.m2v" to appear...
Processing started. Please wait... 
=========================================================

Multiplexing audio and video together with the following command:
Multiplexing finished successfully
Output files:
/home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.mpg
    /home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.mpg (2.2G)

=========================================================

    ----------------------------------------
    **Final statistics**
    ----------------
    tovid 0.29
    File: /home/rob/tovid/encoding/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.mpg, 6603 secs DVD NTSC
    Final size:      2306300 kilobytes
    Target bitrate:  7840 kbits/sec
    Average bitrate: 2534 kbits/sec
    Peak bitrate:    8196 kbits/sec
    **Took 02:00:11 to encode on  Intel(R) Celeron(R) M CPU        420  @ 1.60GHz 1596.049 mhz**
    -----------------------------------------
Statistics written to /home/rob/.tovid/stats.tovid
Cleaning up...
removed `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/video.yuv'
Removing temporary files...
removed `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/tovid.log'
removed `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/tovid.scratch'
removed `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/audio.ac3'
removed `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0/video.m2v'
removed directory: `/home/rob/Revolver[2005]DvDrip[Eng]-aXXo.avi.tovid_encoded.0'

=========================================================

Done!

=========================================================


---

### Post by user1397 on 2006-12-01
> **Robert.Zapata said:**
> Hello Team and Happy Holidays..!!

**Eric:** Excellent How-to/Guide and Tutorial..!! Thank you very much for your patience and your hard work putting all this together.

Just for curiosity I installed **tovid** in my Lenovo machine following your instructions in the first post, everything went flawless..!!

Just for kicks and grins I give it a try with an AVI file and everything worked great. !! I did not "burn" the DVD because this machine *(Thinkpad)* is not intended for video processing. I will re-install tovid in my Toshiba notebook at home and will complete the whole process to the end *(playable DVD)*

*(I'm at work right now..so not much time to continue testing tovid, but so far, so good)*

Just as a reference, here's my tovid log file *(edited to make it shorter and highlite times in bold)*

In summary it took two hours to encode a 1:50 video.

KUDOS TO YOU AND KEEP DOING A GREAT JOB..!!! *(sorry for the yelling)*No problem, just my way of giving back to the community.  Thanks for using this guide.   And damn, that is actually quite impressive...the video took only like 10 more minutes than the actual length of the video...don't see that too often.

---

### Post by Robert.Zapata on 2006-12-01
Argh......

I'm having trouble with the **mkiso** script...!!!

This's what I get:

> 
rob@rob-laptop:~/tovid/encoding$ mkiso Revolver.mpg
**bash: /usr/bin/mkiso: /bin/bash^M: bad interpreter: No such file or directory**
rob@rob-laptop:~/tovid/encoding$


The script exist at the **usr/bin/** location.

What I'm doing wrong..??

I run the **installtovid.sh** in my Toshiba box under 6.06LTS

---

### Post by user1397 on 2006-12-02
> **Robert.Zapata said:**
> Argh......

I'm having trouble with the **mkiso** script...!!!

This's what I get:



The script exist at the **usr/bin/** location.

What I'm doing wrong..??

I run the **installtovid.sh** in my Toshiba box under 6.06LTSi know the exact problem. notice that "^M" in the error message?  as far as i know, that happens when you transfer a file from windows to linux (it could be more general than that, as in from one OS to another, but i dunno)

did you just use my script to install the mkiso script?  u didn't transfer anything from windows right?  

if the answer to the former is yes and the answer of the latter is no, then i have done something unspeakable...

---

### Post by Robert.Zapata on 2006-12-02
> **erik1397 said:**
> i know the exact problem. notice that "^M" in the error message?  as far as i know, that happens when you transfer a file from windows to linux (it could be more general than that, as in from one OS to another, but i dunno)

did you just use my script to install the mkiso script?  u didn't transfer anything from windows right?  

if the answer to the former is yes and the answer of the latter is no, then i have done something unspeakable...

Eric:

1 - Yes. I use the script and folow all the instructions in your first post of the thread.

2 - The original avi file was created in co-worker Windoze machine *(do not know the OS ver.)*

3 - I connected to my co-worker machine using: Places -> Connect to Server ->  Windows Share and copy the file to my Lenovo Notebook *(Ubuntu 6.10)*

4 - Went to home and transfer the MPG file to my external HD and then re-attach external HD to my Toshiba notebook *(Ubuntu 6.10)*.

Note: I also rename the file to make it shorter (Revolver.mpg)

So...What's going on...?? How did you found our that Windoze was involved...??

---

### Post by user1397 on 2006-12-02
> **Robert.Zapata said:**
> Eric:

1 - Yes. I use the script and folow all the instructions in your first post of the thread.

2 - The original avi file was created in co-worker Windoze machine *(do not know the OS ver.)*

3 - I connected to my co-worker machine using: Places -> Connect to Server ->  Windows Share and copy the file to my Lenovo Notebook *(Ubuntu 6.10)*

4 - Went to home and transfer the MPG file to my external HD and then re-attach external HD to my Toshiba notebook *(Ubuntu 6.10)*.

Note: I also rename the file to make it shorter (Revolver.mpg)

So...What's going on...?? How did you found our that Windoze was involved...??I didn't find out - I just had a similar problem before, and that was what a forum member told me.

I don't think transferring the avi file from windows should do anything, but maybe it does.  Nevertheless, paste this (in a terminal):
```
sudo rm /usr/bin/mkiso
```
then open gedit, and paste this into it:
> 
#!/bin/bash
#Make iso from MPG's
dvdauthor -o dvd -t $1 &&[FONT=monospace]
[/FONT]dvdauthor -o dvd -T &&[FONT=monospace]
[/FONT]mkisofs -dvd-video -o dvd.iso dvd/ &&[FONT=monospace]
[/FONT]exit save it as **mkiso** to your **desktop**, and close gedit.

Now, open a terminal, and paste the following commands:
```
cd ~/Desktop
sudo mv mkiso /usr/bin/
``` and then try running the mkiso command again with your video.

---

### Post by Robert.Zapata on 2006-12-03
Hey...!!! Now is working..!!!!


I finally got a playable DVD...!!!! Thank you very much.

---

### Post by user1397 on 2006-12-03
> **Robert.Zapata said:**
> Hey...!!! Now is working..!!!!


I finally got a playable DVD...!!!! Thank you very much.wait, so my solution worked for you? or it all of a sudden worked (with the mkiso from the script)

o and, np

---

### Post by Robert.Zapata on 2006-12-03
Sorry for not properly clarify.

I follow your instructions regarding deleting and creating a new **mkiso** script and that did the trick, but can not see any difference between the old  mkiso and the new one...:confused: 

I'll stop using my co-worker sources regarding movies.

---

### Post by user1397 on 2006-12-03
> **Robert.Zapata said:**
> Sorry for not properly clarify.

I follow your instructions regarding deleting and creating a new **mkiso** script and that did the trick, but can not see any difference between the old  mkiso and the new one...:confused: 

I'll stop using my co-worker sources regarding movies.no, you can still use your co-worker's resources...it is my fault that the mkiso script does not work.  Apparently, i must have created it while in windows, and that's why that happens.  I'll fix my script with the mkiso script later.

---

### Post by user1397 on 2006-12-05
*fixed the mkiso script.  should work now.

---

### Post by sumithar on 2006-12-11
Hi,
I used your script and installed tovid.  But when I tried to convert a .avi to dvd I ran into some problems.  When I posted the problems on the tovid groups they recommended I upgrade to version 0.29

Could you tell me how I should upgrade- should I modify the script and run again?

Thanks

---

### Post by user1397 on 2006-12-11
> **sumithar said:**
> Hi,
I used your script and installed tovid.  But when I tried to convert a .avi to dvd I ran into some problems.  When I posted the problems on the tovid groups they recommended I upgrade to version 0.29

Could you tell me how I should upgrade- should I modify the script and run again?

Thanksman that's really strange...my script should install the 0.29 version.  can you post your problems here, and maybe see if I can help?

---

### Post by sumithar on 2006-12-11
Thanks.
Turned out that I had an older version of tovid that I had forgotten about.  This was installed in /usr/local/bin directory which was ahead in the PATH concatenation than /usr/bin which is where the later version (yours) was installed.
I proceeded to delete everything in /usr/local/bin and then ran your remove script and then your install script again.

But I guess I mucked up something since now when I click on the menu item under Applications-Sound&Video-Tovid nothing happens
And when I run tovidgui on the command line I get the message
auser1@Wintergreen:~$ tovidgui
Traceback (most recent call last):
  File "/usr/bin/tovidgui", line 39, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: cannot import name TovidFrame

---

### Post by user1397 on 2006-12-11
> **sumithar said:**
> Thanks.
Turned out that I had an older version of tovid that I had forgotten about.  This was installed in /usr/local/bin directory which was ahead in the PATH concatenation than /usr/bin which is where the later version (yours) was installed.
I proceeded to delete everything in /usr/local/bin and then ran your remove script and then your install script again.

But I guess I mucked up something since now when I click on the menu item under Applications-Sound&Video-Tovid nothing happens
And when I run tovidgui on the command line I get the message
auser1@Wintergreen:~$ tovidgui
Traceback (most recent call last):
  File "/usr/bin/tovidgui", line 39, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: cannot import name TovidFramehmm, it shouldn't be in /usr/bin at all, it should be in /usr/local/bin.  maybe since you had 2 different versions installed, it installed one in /usr/bin and one in /usr/local/bin.  try deleting only the tovid stuff from /usr/bin and /usr/local/bin, then run the removal and the install script again.

WARNING: BE CAREFUL!!!!! only delete stuff from /usr/bin that is tovid-related!!! many important system executables are in that directory!!!  sorry for screaming at you!!!

---

### Post by kirini on 2006-12-12
Hi all
I had that problem with edgy
(#!/bin/sh right? => #!/usr/bin/env bash)

It fixed tovid and makemenu commands, but it did not work for makexml. 

it still gives me that error. 

I am using windows at moment so cannot post that error message. 

another thing, tovid is slow.
I used tovid for 25 avi file each about 25min long so used bitrate limit 889 to make it fit in 4300mb.
But it is odd that in windows side similar job took lot less time with ConvertXtoDVD(also creates menu, and creates single DVD from several avi). I used GUI to create commands but copied those command to terminal and executed them there. don't remember how long it took, but closer to 10h, when in Windows it took 6h or less. Any way to speed tovid? Does tovid use ffmpeg or something else?

---

### Post by binks on 2006-12-12
yes add the option **-ffmpeg** ffmpeg is faster at encodeing 
binks

---

### Post by user1397 on 2006-12-12
tovid uses mplayer by default to encode, but like binks said, you can use ffmpeg to speed up the process, though i think ffmpeg is not as clean (no?)

edit: i found out that the only badside to ffmpeg, is if you use a lower quality option (default -quality is 8, so if you put it at less than 8, ffmpeg will produce more low-quality video than mplayer.)

---

### Post by sumithar on 2006-12-14
> **erik1397 said:**
> hmm, it shouldn't be in /usr/bin at all, it should be in /usr/local/bin.  maybe since you had 2 different versions installed, it installed one in /usr/bin and one in /usr/local/bin.  try deleting only the tovid stuff from /usr/bin and /usr/local/bin, then run the removal and the install script again.

WARNING: BE CAREFUL!!!!! only delete stuff from /usr/bin that is tovid-related!!! many important system executables are in that directory!!!  sorry for screaming at you!!!

Thanks.  That worked.  Now I was able to do everything up to creating the AUDIO_TS and VIDEO_TS folder.  When I run mkiso I get the message.  Vidheyan is the name of the video and inside this directory are the AUDIO_TS and VIDEO_TS folder.

/mnt/hdd1/tovidwork$ mkiso Vidheyan
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing Vidheyan...
STAT: VOBU 0 at 0MB, 1 PGCS
/usr/bin/mkiso: line 6: 27916 Segmentation fault      dvdauthor -o dvd -t $1


Any ideas?

Thanks

---

### Post by user1397 on 2006-12-14
> **sumithar said:**
> Thanks.  That worked.  Now I was able to do everything up to creating the AUDIO_TS and VIDEO_TS folder.  When I run mkiso I get the message.  Vidheyan is the name of the video and inside this directory are the AUDIO_TS and VIDEO_TS folder.

/mnt/hdd1/tovidwork$ mkiso Vidheyan
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing Vidheyan...
STAT: VOBU 0 at 0MB, 1 PGCS
/usr/bin/mkiso: line 6: 27916 Segmentation fault      dvdauthor -o dvd -t $1


Any ideas?

Thankshmm strage... 
try this in a terminal:
```
sudo rm /usr/bin/mkiso
touch mkiso
```in the gedit file that opens, paste:
> [FONT=monospace][/FONT]
#!/bin/bash[FONT=monospace]
[/FONT]#Make iso from MPG's[FONT=monospace]
[/FONT]dvdauthor -o dvd -t $1 &&[FONT=monospace]
[/FONT]dvdauthor -o dvd -T &&[FONT=monospace]
[/FONT]mkisofs -dvd-video -o dvd.iso dvd/ &&[FONT=monospace]
[/FONT]exit then save, and close gedit.
again in the terminal, paste this: ```
sudo mv mkiso /usr/bin/
```and retry the mkiso script

---

### Post by kirini on 2006-12-15
I tested to convert same file with different ways, i used episode of naruto
I used 
Tovid
tovid (using ffmpeg codec)
fmpeg
avidemux

278233088 2006-12-14 22:59 naruto_76_avidemux_lavc_anim_type.mpg
278233088 2006-12-14 22:44 naruto_76_avidemux_lavc_notype.mpg
278233088 2006-12-14 23:16 naruto_76_avidemux_lavc_tmpeg_type.mpg
244068352 2006-12-15 00:01 naruto_76_ffmpeg_default.mpg
186720256 2006-12-13 23:20 naruto_76_tovid_default_codec_anim_type.mpg.mpg
184496128 2006-12-13 22:47 naruto_76_tovid_default_codec_notype.mpg.mpg
324032512 2006-12-14 00:03 naruto_76_tovid_ffmpeg_codec_anim_type.mpg.mpg
324032512 2006-12-13 23:45 naruto_76_tovid_ffmpeg_codec_notype.mpg.mpg

avidemux and tovid using ffmpeg codec had good picture guality. 
tovid using default codec had bad picture quality and no difference with animation setting.

any other codec to create mpeg?

---

### Post by user1397 on 2006-12-15
> **kirini said:**
> I tested to convert same file with different ways, i used episode of naruto
I used 
Tovid
tovid (using ffmpeg codec)
fmpeg
avidemux

278233088 2006-12-14 22:59 naruto_76_avidemux_lavc_anim_type.mpg
278233088 2006-12-14 22:44 naruto_76_avidemux_lavc_notype.mpg
278233088 2006-12-14 23:16 naruto_76_avidemux_lavc_tmpeg_type.mpg
244068352 2006-12-15 00:01 naruto_76_ffmpeg_default.mpg
186720256 2006-12-13 23:20 naruto_76_tovid_default_codec_anim_type.mpg.mpg
184496128 2006-12-13 22:47 naruto_76_tovid_default_codec_notype.mpg.mpg
324032512 2006-12-14 00:03 naruto_76_tovid_ffmpeg_codec_anim_type.mpg.mpg
324032512 2006-12-13 23:45 naruto_76_tovid_ffmpeg_codec_notype.mpg.mpg

avidemux and tovid using ffmpeg codec had good picture guality. 
tovid using default codec had bad picture quality and no difference with animation setting.

any other codec to create mpeg?hmm I don't know of any other programs or codecs that do this task, but I know that tovid only has those two options available.

---

### Post by sumithar on 2006-12-16
> **erik1397 said:**
> hmm strage... 
try this in a terminal:
```
sudo rm /usr/bin/mkiso
touch mkiso
```in the gedit file that opens, paste:
then save, and close gedit.
again in the terminal, paste this: ```
sudo mv mkiso /usr/bin/
```and retry the mkiso script

Thanks again.  I followed your steps and that gave me the same error.  So I looked at your shell script and just typed in the command
 mkisofs -dvd-video -o Vidheyan.iso Vidheyan/ on the command line.

That seemed to work.  It created an ISO image that I burnt to DVD like you said(right click and choose Write option).  I am half way thru watching it on my DVD player.

Thanx a ton.

---

### Post by user1397 on 2006-12-16
> **sumithar said:**
> Thanks again.  I followed your steps and that gave me the same error.  So I looked at your shell script and just typed in the command
 mkisofs -dvd-video -o Vidheyan.iso Vidheyan/ on the command line.

That seemed to work.  It created an ISO image that I burnt to DVD like you said(right click and choose Write option).  I am half way thru watching it on my DVD player.

Thanx a ton.ah I see..yea I don't know what's up with the mkiso script, I think I might just scratch it out...and then I could just put the recommended tovid way of doing things...

---

### Post by wilberfan on 2006-12-16
Holy crap, it actually *worked!!*

Start to finish, no errors...even burned properly.   And it's playing in my extremely fussy DVD player!  :mrgreen: 

Just one thing I notice:   The video seems a triffle 'jerky' (ie, not smooooooooth).   It's especially noticable in scenes with a lot of camera movement...   Could this be addressed by the other NTSC "film rate" option??  (I processed this one with the first, "NTSC" option...)   The audio is beautiful...

If not, what IS that option intended for?

---

### Post by user1397 on 2006-12-16
> **wilberfan said:**
> Holy crap, it actually *worked!!*

Start to finish, no errors...even burned properly.   And it's playing in my extremely fussy DVD player!  :mrgreen: 

Just one thing I notice:   The video seems a triffle 'jerky' (ie, not smooooooooth).   It's especially noticable in scenes with a lot of camera movement...   Could this be addressed by the other NTSC "film rate" option??  (I processed this one with the first, "NTSC" option...)   The audio is beautiful...

If not, what IS that option intended for?glad it worked for you.  the reason why its choppy might be cause of the -quality setting.  (you did this with the command line right?)  the default quality is -quality 8, but you could put it at -quality 9 if you felt like it, and it would look better, but the file size would be larger.

I'm not sure what you mean by the other NTSC option.

---

### Post by wilberfan on 2006-12-16
I didn't use the command line...it was all done from the gui.  

There are two "NTSC" options:   The first one says, "NTSC: Used in the Americas and East Asia"
The second one says, "NTSC Film: Same as NTSC, with a film frame rate"

The third option is for PAL.

I don't see that there are any "quality" settings in the gui--other than what I just mentioned..

:-k

---

### Post by yabbadabbadont on 2006-12-16
> **wilberfan said:**
> I didn't use the command line...it was all done from the gui.  

There are two "NTSC" options:   The first one says, "NTSC: Used in the Americas and East Asia"
The second one says, "NTSC Film: Same as NTSC, with a film frame rate"

The third option is for PAL.

I don't see that there are any "quality" settings in the gui--other than what I just mentioned..

:-k

Just a heads up.  If you are going to use the gui, then you should be sure to use the svn version of tovid.  The gui was severely neglected in the past, but there is a new maintainer who is adding/fixing things in it every day now.

---

### Post by wilberfan on 2006-12-16
> **yabbadabbadont said:**
> Just a heads up.  If you are going to use the gui, then you should be sure to use the svn version of tovid.  The gui was severely neglected in the past, but there is a new maintainer who is adding/fixing things in it every day now.

That must be binks ["tovidwiz"?]("http://www.ubuntuforums.org/showthread.php?t=311936")   

I did notice that the 'standard" tovid has an "8" as a default quality setting...

---

### Post by yabbadabbadont on 2006-12-16
> **wilberfan said:**
> That must be binks ["tovidwiz"?]("http://www.ubuntuforums.org/showthread.php?t=311936")   

I did notice that the 'standard" tovid has an "8" as a default quality setting...

tovidwiz is something different.  I'm talking about tovidgui.

If you use tovid very often, then you should probably follow the tovid forums too:

[http://www.createphpbb.com/tovid/](http://www.createphpbb.com/tovid/)

There is some pretty good information there.

---

### Post by wilberfan on 2006-12-16
I guess I don't know what the "svn" version is.  (It was mentioned on that tovidwiz thread, so I thought they were the same thing...)

How do I know which version of tovid I'm using??    My "about" box says, [I]"You are using the tovid GUI, version 0.28,
part of the tovid video disc authoring suite.[/I]

Thanks for the heads up on the tovid forum...

---

### Post by yabbadabbadont on 2006-12-16
> **wilberfan said:**
> I guess I don't know what the "svn" version is.  (It was mentioned on that tovidwiz thread, so I thought they were the same thing...)

How do I know which version of tovid I'm using??    My "about" box says, [I]"You are using the tovid GUI, version 0.28,
part of the tovid video disc authoring suite.[/I]

Thanks for the heads up on the tovid forum...

[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

In the "Installing tovid" section, there is information about the svn version.  Basically svn (subversion), is version control software.  When you run the "svn" version, you are pulling the latest version of every file directly out of their version control software.

---

### Post by wilberfan on 2006-12-16
[Edit] Seconds too late!

I found some good stuff on the tovid wiki (duh!) [here]("http://tovid.wikia.com/wiki/Main_Page").  

   I'll have to investigate!

---

### Post by binks on 2006-12-18
just to add to svn is the latest version of the **testing** this means the files are updated as we add new features ie if your using the svn you can use the testing version of the gui by running **tktodisc ** from a shell 

and the diff between ntsc and ntscfilm are the framerate ie 
as taken from [www.dvdrhelp.com](www.dvdrhelp.com) 

PAL 

Video:
Up to 9.8 Mbps* (9800 kbps*) MPEG2 video
Up to 1.856 Mbps (1856 kbps) MPEG1 video
720 x 576 pixels MPEG2 (Called Full-D1)
704 x 576 pixels MPEG2
352 x 576 pixels MPEG2 (Called Half-D1, same as the CVD Standard)
352 x 288 pixels MPEG2
352 x 288 pixels MPEG1 (Same as the VCD Standard)
25 fps*
16:9 Anamorphic (only supported by 720x576)

Audio:
48000 Hz
32 - 1536 kbps
Up to 8 audio tracks containing Dolby Digital, DTS, PCM(uncompressed audio), MPEG-1 Layer2. One audio track must have MPEG-1, DD or PCM Audio.

Extras: 
Motion menus, still pictures, up to 32 selectable subtitles, seamless branching for multiple storylines, 9 camera angles. And also additional DVD-ROM / data files that only can be read by computer DVD drives. 

Total:
Total bitrate including video, audio and subs can be max 10.08 Mbps (10080 kbps) 


* Mbps = million bits per second
* kbps = thousand bits per second 
* fps = frames per second 

For more technical DVD-Video details read the DVDDemystified DVD FAQ section 3.4 or the mpeg.org DVD Technical Notes.

 
NTSC (NTSC Film)



Video:
Up to 9.8 Mbps* (9800 kbps*) MPEG2 video 
Up to 1.856 Mbps (1856 kbps) MPEG1 video
720 x 480 pixels MPEG2 (Called Full-D1)
704 x 480 pixels MPEG2
352 x 480 pixels MPEG2 (Called Half-D1, same as the CVD Standard) 
352 x 240 pixels MPEG2
352 x 240 pixels MPEG1 (Same as the VCD Standard) 
29,97 fps*
23,976 fps with 3:2 pulldown = 29,97 playback fps (NTSC Film, this is only supported by MPEG2 video)
16:9 Anamorphic (only supported by 720x480) 


Audio:
48000 Hz
32 - 1536 kbps 
Up to 8 audio tracks containing DD (Dolby Digital/AC3), DTS, PCM(uncompressed audio), MPEG-1 Layer2. One audio track must have DD or PCM Audio.

Extras: 
Motion menus, still pictures, up to 32 selectable subtitles, seamless branching for multiple storylines, 9 camera angles. And also additional DVD-ROM / data files that only can be read by computer DVD drives. 

Total:
Total bitrate including video, audio and subs can be max 10.08 Mbps (10080 kbps) 


* Mbps = million bits per second
* kbps = thousand bits per second 
* fps = frames per second 

For more technical DVD-Video details read the DVDDemystified DVD FAQ section 3.4 or the mpeg.org DVD Technical Notes.

**Also see** [http://www.videohelp.com/tmpgencexplained.htm](http://www.videohelp.com/tmpgencexplained.htm)
 


cheers binks

---

### Post by RBH on 2006-12-22
had everything up and running in no time. encoded my first dvd from an avi and had no errors. it played fine in my dvd player but the quality just doesn't seem to be the best. it has a camcorder feel to it when watching the movie. maybe i have something setup wrong and will play around with it. an excellent project though and look forward to its further development.

---

### Post by user1397 on 2006-12-23
> **RBH said:**
> had everything up and running in no time. encoded my first dvd from an avi and had no errors. it played fine in my dvd player but the quality just doesn't seem to be the best. it has a camcorder feel to it when watching the movie. maybe i have something setup wrong and will play around with it. an excellent project though and look forward to its further development.yea videos you make always seem to be of a lower quality, I think it's because of the default quality setting imposed in tovid (they put it at less than the max or best quality possible, so people don't run into space issues)  

if you want to try making a dvd with the command line, where you can change the settings like the quality setting, let me know.

---

### Post by user1397 on 2006-12-23
> **wilberfan said:**
> I guess I don't know what the "svn" version is.  (It was mentioned on that tovidwiz thread, so I thought they were the same thing...)

How do I know which version of tovid I'm using??    My "about" box says, [I]"You are using the tovid GUI, version 0.28,
part of the tovid video disc authoring suite.[/I]

Thanks for the heads up on the tovid forum...Just to clear things up (this might be a little confusing)

tovid is the big umbrella name of the entire tovid project, sometimes also known as "tovid: the video disc authoring suite"

actually, tovid is just a collection of scripts that work together, and each script has its own name.  there's the makemenu, makedvd, postproc, and todisc scripts for example, and there is even a single script named tovid, which is the 'main' script, or the script that started it all.


the svn version of tovid is always the latest possible build of the whole tovid suite, but is is the development branch, and hence, is supposedly 'unstable'

as far as i understand it, both version 0.28 and 0.29 of the tovidgui both display "version 0.28" in their help > about tabs.

apart from the tovidgui, ther's the tktodisc gui, and then there's bink's tovidwiz gui.  all of these are GUI's, (graphical user interfaces) of tovid, but they use different scripts of tovid to work.

apart from that, you can use each individual script of the tovid suite in the terminal, or command line interface (CLI) 

that's about it

---

### Post by Mushie on 2006-12-28
This is a really long thread and I'm happy to have found it. I only have one problem. I try to see the output after i tell it to creat the audio and video ts files. Well, there's nothing in the audio part ? I'm not sure what went wrong, but I get the the encoded mpg and then try to turn that into a dvd file. I've burnt a copy and it doesn't recogize the disc since there's nothing in the audio ts folder. Any help ?

---

### Post by dannyboy79 on 2006-12-28
I can honestly tell you that there is never anything in the audio folder. AH, take a look at any dvd from you living room and open it up, you'll see what I am talking about. it's not working due to something else. try it again.

---

### Post by user1397 on 2006-12-28
> **Mushie said:**
> This is a really long thread and I'm happy to have found it. I only have one problem. I try to see the output after i tell it to create the audio and video ts files. Well, there's nothing in the audio part ? I'm not sure what went wrong, but I get the the encoded mpg and then try to turn that into a dvd file. I've burnt a copy and it doesn't recognize the disc since there's nothing in the audio ts folder. Any help ?dannyboy said t, it's not something to do with the audio file.  Is there some weird output from the mkiso script?  or what method did you use to burn the movie to a dvd?

---

### Post by bionnaki on 2007-01-17
the install script does not seem to work with kubuntu. says package transcode cannot be found. tovid does not start.

any ideas?

edit: nevermind. figured it out.

---

### Post by dannyboy79 on 2007-01-18
> **bionnaki said:**
> the install script does not seem to work with kubuntu. says package transcode cannot be found. tovid does not start.

any ideas?

edit: nevermind. figured it out.

for the benefit of the forum and all users after you please never put, "nevermind. figured it out". Always make sure you post how you solved your issue so others can solve their issue as well. This way you'll save time from people pm'ing you asking you how you solved your issue.

---

### Post by hammmy on 2007-01-20
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg                                                              
  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Fetched 56.3kB in 4m0s (234B/s)                          
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Just tried to use the script and I ran into this.  The install moved past this after a bit and tovid installs and starts up.

---

### Post by user1397 on 2007-01-22
> **hammmy said:**
> Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg                                                              
  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Fetched 56.3kB in 4m0s (234B/s)                          
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Just tried to use the script and I ran into this.  The install moved past this after a bit and tovid installs and starts up.that just means the servers were down for a bit.  just try the script again

---

### Post by mthaddon on 2007-02-02
> **erik1397 said:**
> yea videos you make always seem to be of a lower quality, I think it's because of the default quality setting imposed in tovid (they put it at less than the max or best quality possible, so people don't run into space issues)  

if you want to try making a dvd with the command line, where you can change the settings like the quality setting, let me know.

Yeah, I'd like to take you up on that one. I tried tovid and same issue - the DVD seems to skip on my quite a lot. Also, it isn't recognised as a DVD by my computer (mounts it as a CD-ROM), but it does at least play on a regular DVD player (although as I say, it's a little choppy).

Thanks, Tom

---

### Post by user1397 on 2007-02-03
> **mthaddon said:**
> Yeah, I'd like to take you up on that one. I tried tovid and same issue - the DVD seems to skip on my quite a lot. Also, it isn't recognised as a DVD by my computer (mounts it as a CD-ROM), but it does at least play on a regular DVD player (although as I say, it's a little choppy).

Thanks, Tomalright, tell me a few things first:

PAL or NTSC?  (americas or eurasia/africa?)
do you just want the video and a simple menu or more complicated menus?

---

### Post by mthaddon on 2007-02-04
> **erik1397 said:**
> alright, tell me a few things first:

PAL or NTSC?  (americas or eurasia/africa?)
do you just want the video and a simple menu or more complicated menus?

It would be for both (let's start with PAL, UK). Just simple video would be fine.

Thanks, Tom

---

### Post by user1397 on 2007-02-06
> **mthaddon said:**
> It would be for both (let's start with PAL, UK). Just simple video would be fine.

Thanks, Tomtom try this for a pal dvd (I'm replacing your actual video file name with the bold word "**foo**"):
```
tovid -pal -discsize 4380 -quality 10 -in **foo** -out **foo**_encoded
```also if you want a widescreen aspect ratio, add "-wide" after "-pal"

For ntsc, do the same command but without "-pal"

---

### Post by user1397 on 2007-02-07
btw, i've updated the guide and the scripts so that mkiso is no longer existent.  the conventional tovid method will be used instead from now on.

---

### Post by mthaddon on 2007-02-07
> **erik1397 said:**
> tom try this for a pal dvd (I'm replacing your actual video file name with the bold word "**foo**"):
```
tovid -pal -discsize 4380 -quality 10 -in **foo** -out **foo**_encoded
```also if you want a widescreen aspect ratio, add "-wide" after "-pal"

For ntsc, do the same command but without "-pal"

Thanks, I'll give that a try.

Tom

---

### Post by gbajosh on 2007-02-08
Any time I try to do any apt command or any install command for anything this happens

chmod +x installtovid.sh && ./installtovid.sh

0% [Connecting to 69.117.223.248 (69.117.223.248)] [Connecting to 69.117.223.24


It stays at 0% for unlimited amount of time.  My internet works fine as I am online, but the installing does not.

---

### Post by user1397 on 2007-02-09
> **gbajosh said:**
> Any time I try to do any apt command or any install command for anything this happens

chmod +x installtovid.sh && ./installtovid.sh

0% [Connecting to 69.117.223.248 (69.117.223.248)] [Connecting to 69.117.223.24


It stays at 0% for unlimited amount of time.  My internet works fine as I am online, but the installing does not.so did this happen like one time (like in one day) or several days in a row?  cause if it was just like one day or a couple of days, it couldve just been the tovid server is down.

---

### Post by user1397 on 2007-02-11
Big News: tovid release .30 is out, I'll update the script pretty soon, like tomorrow.  Pretty big changes actually, read about it here: [http://tovid.wikia.com/wiki/Tovid_changelog](http://tovid.wikia.com/wiki/Tovid_changelog)

edit: updated the scripts

---

### Post by Robert.Zapata on 2007-02-13
Sweet..!!!

Thanks for your hard work and infinite patience...!!!.

---

### Post by Robert.Zapata on 2007-02-15
Arghhhh...!!!!! I select the built-in "burn" option in the tovid GUI and did not work for me..!! I did not got any errors per the log file attached below.

When I put the DVD in the DVD-Player the movie does not play..!! Just a blue screen with the  name it parsed from the menu options.

Then I tried using K3b with the option "New DVD-Video Project" using the files created in the VIDEO_TS folder but no luck.

Lastly I select the manual option as mentioned in the first post and got a different error refering to: "**Cannot continue! DVD image (7152MB) exceeds the DVD's capacity (4482MB).**"

Here's the tovid LOG file


> 
The following commands will be run:
=========================================
makedvd -quiet -author -burn -device /dev/dvdrw /home/rob/tovid/encoding/Untitled_disc.xml
------------------------
Running command: makedvd -quiet -author -burn -device /dev/dvdrw /home/rob/tovid/encoding/Untitled_disc.xml
--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.30
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Authoring disc from file: /home/rob/tovid/encoding/Untitled_disc.xml
=========================================================
Creating disc structure with the following command:
dvdauthor -x "/home/rob/tovid/encoding/Untitled_disc.xml"
=========================================================
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /home/rob/tovid/encoding/Untitled_menu_1.mpg...

INFO: Video pts = 0.178 .. 0.211
INFO: Audio[0] pts = 0.178 .. 4.178
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 1 at 0MB, 1 PGCS

INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: Processing /home/rob/tovid/encoding/Borat.R5.LINE.PROPER.REPACK.XViD-PUKKA.avi.tovid_encoded.mpg...
STAT: VOBU 16 at 1MB, 1 PGCS
STAT: VOBU 32 at 5MB, 1 PGCS
STAT: VOBU 48 at 8MB, 1 PGCS
.
.
.
STAT: VOBU 13088 at 2375MB, 1 PGCS
STAT: VOBU 13104 at 2376MB, 1 PGCS
STAT: VOBU 13120 at 2379MB, 1 PGCS

INFO: Video pts = 0.178 .. 4820.226
INFO: Audio[0] pts = 0.178 .. 4820.146
STAT: VOBU 13133 at 2381MB, 1 PGCS

INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixed 1 VOBUS                         
STAT: fixing VOBU at 1MB (17/13133, 0%)
STAT: fixing VOBU at 5MB (33/13133, 0%)
STAT: fixing VOBU at 8MB (49/13133, 0%)
.
.
.
STAT: fixing VOBU at 2375MB (13089/13133, 99%)
STAT: fixing VOBU at 2376MB (13105/13133, 99%)
STAT: fixing VOBU at 2379MB (13121/13133, 99%)
STAT: fixed 13133 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /home/rob/tovid/encoding/Untitled_disc/VIDEO_TS/VTS_01_0.IFO
=========================================================
Authoring completed.
=========================================================
Found blank DVD+R.
=========================================================
Burning with growisofs 5.21 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/dvdrw -dvd-video -V "UNTITLED_DISC" "/home/rob/tovid/encoding/Untitled_disc"
=========================================================
Executing 'mkisofs -dvd-video -V UNTITLED_DISC /home/rob/tovid/encoding/Untitled_disc | builtin_dd of=/dev/dvdrw obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
/dev/dvdrw: "Current Write Speed" is 2.5x1385KBps.
:-? the LUN appears to be stuck writing LBA=300h, retry in 231ms
  0.41% done, estimate finish Wed Feb 14 22:48:49 2007
  0.82% done, estimate finish Wed Feb 14 21:31:59 2007
  1.23% done, estimate finish Wed Feb 14 21:06:14 2007
.
.
.  
 98.38% done, estimate finish Wed Feb 14 20:16:38 2007
 98.79% done, estimate finish Wed Feb 14 20:16:38 2007
 99.20% done, estimate finish Wed Feb 14 20:16:37 2007
 99.61% done, estimate finish Wed Feb 14 20:16:38 2007
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 21000
1219722 extents written (2382 MB)
/dev/dvdrw: flushing cache
/dev/dvdrw: closing track
/dev/dvdrw: closing disc
/dev/dvdrw: reloading tray
=========================================================
Done.


---

### Post by user1397 on 2007-02-19
updated the guide, more fluid

---

### Post by user1397 on 2007-02-24
could someone using edgy please test out my installation script?

---

### Post by user1397 on 2007-02-24
Please read the message at the top of the first post in this thread.  Thank you.

---

### Post by PapaWiskas on 2007-02-24
I recently installed Uberyl uses Edgy as you know.  Your installation script worked flawlessly by the way.....awesome work.  Not sure if I will use the GUI or not but wanted to use it to install Tovid.  

And I have a problem that is really confusing me.  I had been using tovid via command line for so long without issues, but now I am lost.

I get to the makedvd part and it says it cant find my dvdr?  And to specify it using the -device command or whatever.

I have done everything I can think of and I can not get it to see my DVD+R disc. 

I dont know what to do, my gut thinks it has something to do with my fstab, but I dont know.

Any help would be appreciated.

First I type this...
> $ makedvd -burn -speed 4 -label TENACIOUS shrunk

Which then gets me this error...

> Please insert a blank DVD+/-R(W) disc into your DVD-recorder
(/dev/dvdrw) if you have not already done so.
Couldn't find /dev/dvdrw! Are you sure your burner is /dev/dvdrw? Specify your 
burner with '-device /path/to/burner'.
Stopping here.

---

### Post by user1397 on 2007-02-24
> **PapaWiskas said:**
> I recently installed Ubery[FONT=Verdana]l[/FONT] uses Edgy as you know.  Your installation script worked flawlessly by the way.....awesome work.  Not sure if I will use the GUI or not but wanted to use it to install Tovid.  

And I have a problem that is really confusing me.  I had been using tovid via command line for so long without issues, but now I am lost.

I get to the makedvd part and it says it cant find my dvdr?  And to specify it using the -device command or whatever.

I have done everything I can think of and I can not get it to see my DVD+R disc. 

I dont know what to do, my gut thinks it has something to do with my fstab, but I dont know.

Any help would be appreciated.

First I type this...


Which then gets me this error...thanks for trying it out.  please tell me if both the tovidgui and the todiscgui show up in the menus, and if they startup correctly.

as for your issue, try -device /dev/hdc (its worked for me before)

---

### Post by PapaWiskas on 2007-02-24
Yes they both showed up in the menu and both activated just fine.

I tried -device /dev/hdc and it did not work, I did find out by using gnomebaker that my drive is actually /dev/sr0

So then I tried that, but after 3 lines of percentages using makedvd it errored out.
I dont have the errors at the moment, and I am tired of trying to figure it out right now.

I will get back to you tomorrow on it....

---

### Post by dannyboy79 on 2007-02-24
i am not sure exactly what you are trying to do but DeVeDe is really awesome and it worked when I needed to create a dvd from an avi file. you can download the tar, extract it, then simply run the ./install.py and you'reod to go. I would think you need python insalled to run it though.

---

### Post by user1397 on 2007-02-25
> **dannyboy79 said:**
> i am not sure exactly what you are trying to do but DeVeDe is really awesome and it worked when I needed to create a dvd from an avi file. you can download the tar, extract it, then simply run the ./install.py and you'reod to go. I would think you need python insalled to run it though.Yes, you're not the first to mention devede in this thread, and I do agree that it is a good program, but it is not the *only* program that can do what it can do.

tovid happens to be an alternative, and is a much more powerful tool than devede, but it is still in its alpha stages, and more progress will be made.

i just wrote this guide to show people one way, you or anyone who wants to can write another guide if you/they wish to.

---

### Post by user1397 on 2007-02-25
> **PapaWiskas said:**
> Yes they both showed up in the menu and both activated just fine.

I tried -device /dev/hdc and it did not work, I did find out by using gnomebaker that my drive is actually /dev/sr0

So then I tried that, but after 3 lines of percentages using makedvd it errored out.
I dont have the errors at the moment, and I am tired of trying to figure it out right now.

I will get back to you tomorrow on it....okie-doke.

---

### Post by user1397 on 2007-02-25
by the way, i rendered my 0.30 deb package kinda unstable, so i decided to go with the tarball again, for now

---

### Post by PapaWiskas on 2007-02-26
Ok, so now I know my DVD drive is /dev/sr0, I can read CDs, I can play DVDs that ARENT encrypted, but it gives me an error when I play commercial DVDs, even though I got all the codecs installed via AUTOMATIX.

But my combo drive will not burn CDs or DVDs for some reason.  MakeDVD gives that error and K3B does as well.

I never had this problem in Dapper....any ideas of where to start?

---

### Post by user1397 on 2007-02-26
> **PapaWiskas said:**
> Ok, so now I know my DVD drive is /dev/sr0, I can read CDs, I can play DVDs that ARENT encrypted, but it gives me an error when I play commercial DVDs, even though I got all the codecs installed via AUTOMATIX.

But my combo drive will not burn CDs or DVDs for some reason.  MakeDVD gives that error and K3B does as well.

I never had this problem in Dapper....any ideas of where to start?hmm...upgrade to feisty?  (joking, but seriously if its not your production machine, you really should try feisty.  i have it installed right now, its really great.)

other than that, i dont know what else to tell ya.

---

### Post by PapaWiskas on 2007-02-26
But I just got Uberyl to the point where I like it....after blowing away my just fine Dapper....which I upgraded from my just fine Breezy....it just never ends does it?

Do you recommend a clean install of feisty or upgrade?

Is it one of those Herd Cds I read about....tell you what....can you just point me in the right direction (download page), I am starting to get cranky....LMAO.....

---

### Post by user1397 on 2007-02-26
> **PapaWiskas said:**
> But I just got Uberyl to the point where I like it....after blowing away my just fine Dapper....which I upgraded from my just fine Breezy....it just never ends does it?

Do you recommend a clean install of feisty or upgrade?

Is it one of those Herd Cds I read about....tell you what....can you just point me in the right direction (download page), I am starting to get cranky....LMAO.....heh, well you dont have to upgrade if you dont want to, if you just got beryl configured correctly, then whatever.  i do recommend you at least try the live cd: [http://distrowatch.com/?newsid=04042](http://distrowatch.com/?newsid=04042)

---

### Post by PapaWiskas on 2007-02-27
Ok...found it here.
[http://cdimage.ubuntu.com/releases/feisty/herd-4/](http://cdimage.ubuntu.com/releases/feisty/herd-4/)

I also have a different thread in the beginner section trying to get some help with my burning error.  Seems like I am not the only one.

Hopefully Feisty will fix the problem.  But I wish I knew enough on how to fix the problem without having to do that.

---

### Post by spockrock on 2007-02-27
ok I just tried the script, and it more or less dies, tovidgui and todiscgui are not there...and tovid it self did not install I am on edgy.

ok so I just went to the tovid site, grabbed the tar.gz ran configure, and then sudo checkinstall, and poof its working....

---

### Post by user1397 on 2007-02-27
> **spockrock said:**
> ok I just tried the script, and it more or less dies, tovidgui and todiscgui are not there...and tovid it self did not install I am on edgy.

ok so I just went to the tovid site, grabbed the tar.gz ran configure, and then sudo checkinstall, and poof its working....ARGHHH! 

* bangs his head on the wall a few times, and then a few more times

okay, i'll work on it

edit: hmm, im actually contemplating on whether the script is necessary at all, maybe i should just point to the tovid website...i dont know!


EDIT: okay, i finally went for it...no more installation scripts!

---

### Post by Dubbayoo on 2007-02-27
The thing I don't like about tovidgui is that:

-  you can't make a disc without a menu even if there is just one video on the disc
- you don't have enough control over the size of the video. You can select QUALITY but you can't see how much of the disc that will fill beforehand.
- for whatever reason devede is like 2-3X faster anyway. 

If you're putting one video on a disc use devede.

---

### Post by yabbadabbadont on 2007-02-28
> **spockrock said:**
> ok I just tried the script, and it more or less dies, tovidgui and todiscgui are not there...and tovid it self did not install I am on edgy.

ok so I just went to the tovid site, grabbed the tar.gz ran configure, and then sudo checkinstall, and poof its working....

Don't get too attached to todiscgui, it is most likely going away soon.

[http://www.createphpbb.com/tovid/viewtopic.php?p=2953&mforum=tovid#2953](http://www.createphpbb.com/tovid/viewtopic.php?p=2953&mforum=tovid#2953)

---

### Post by user1397 on 2007-02-28
> **Dubbayoo said:**
> The thing I don't like about tovidgui is that:

-  you can't make a disc without a menu even if there is just one video on the disc
- you don't have enough control over the size of the video. You can select QUALITY but you can't see how much of the disc that will fill beforehand.
- for whatever reason devede is like 2-3X faster anyway. 

If you're putting one video on a disc use devede.well just so you know, it's a work-in-progress, and is in its very early alpha stages.  the tovidgui is not the main part of the project, the main part is the command line, and that works beautifully.

by the way, a dvd can fit about 4300 MB, or 4380 max i think.  when the tovidgui is done, you could go to the location of your encoded video, and right click > properties to see if it can fit on a dvd.

the reason devede is faster is because it uses ffmpeg to author, instead of mplayer/mencoder.  you can use ffmpeg with the tovid command line if you want to, you just have to add the -ffmpeg option to it.

mplayer/mencoder is used for better quality i think, or is less error prone maybe, i dont know.

but whatever, suit yourself.

---

### Post by azray on 2007-03-18
having a problem with tovid. When I envoke the gui program it begins then goes away without completing.??

---

### Post by user1397 on 2007-03-18
> **azray said:**
> having a problem with tovid. When I envoke the gui program it begins then goes away without completing.??please open a _[terminal]("http://psychocats.net/ubuntu/terminal")_ and type **tovidgui**.  Please post here the result.

---

### Post by casfindad on 2007-03-19
> **ubuntuman001 said:**
> please open a _[terminal]("http://psychocats.net/ubuntu/terminal")_ and type **tovidgui**.  Please post here the result.

Here's what I get after installing tovid 0.30-1 and typing "tovidgui" in Konsole:

```
Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 43, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: No module named libtovid.gui.frames

```

Selecting tovid GUI or todisc GUI in Kmenu>Graphics gives me a bouncing icon, but the program does not start.

---

### Post by user1397 on 2007-03-19
> **azray said:**
> having a problem with tovid. When I envoke the gui program it begins then goes away without completing.??

> **casfindad said:**
> Here's what I get after installing tovid 0.30-1 and typing "tovidgui" in Konsole:

```
Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 43, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: No module named libtovid.gui.frames

```Selecting tovid GUI or todisc GUI in Kmenu>Graphics gives me a bouncing icon, but the program does not start.okay i think that the problem lies with the deb package.  Please try installing from source, as described _[here]("http://tovid.wikia.com/wiki/Installing_tovid")_

---

### Post by Bill Statler on 2007-03-26
> **ubuntuman001 said:**
> okay i think that the problem lies with the deb package.  Please try installing from source, as described _[here]("http://tovid.wikia.com/wiki/Installing_tovid")_

I was just fighting this same problem today.  I installed tovid_0.30-1_i386.deb on my Ubuntu 6.06 Dapper system.

Seems the problem is that the .deb installs a bunch of stuff in a python2.5 subdirectory where python 2.4 doesn't look for it.  My kludge fix was to move the entire [COLOR="DarkRed"]libtovid[/COLOR] directory from [COLOR="DarkRed"]/usr/local/lib/python2.5/site-packages[/COLOR] to [COLOR="DarkRed"]/usr/local/lib/python2.4/site-packages[/COLOR].

So far, it seems to be working.

---

### Post by garlicsalt2 on 2007-03-27
Okay, I normally read entire topics to search for answers. This is the first topic I've come across that has 36 pages...

I'll just skip to the end and ask. I hope no one is too upset if this question has been answered. If they are/it has, just point me to the page, and I'll take it from there.

Situation: I have several .3gp files and some .jpg files, plus one animated .gif (four-frame, repeating). I am trying to get these files onto a DVD - and have done so already. The problem? The DVD comes out full-screen. This wouldn't be a problem normally, except that the images were designed for a 3"-4" screen. When viewed on a 13" television or a 15" Monitor, one can't tell what one is seeing. It's too "blotchy". Does anyone know how to tell tovid or equivalent to resize to about 3-4x of the original, and **not **take up the whole screen. Centering the images on the display would be a nice touch too...

For the Jpegs, I would like them to be like a slideshow-type of deal. I had done this before, but the images seem to "hiccup" every second or so. It is as though some one was video-taping a still photo, while in a car on a bumpy road. The image is there, but seems like it is being "jostled" about once every second. I had used a combination of "transcode", "ffmpeg" and "mencoder", as well as "tovid" to do the various conversions.

I wouldn't mind putting some small text into the bottom of the videos and jpegs to denote which segment is which source file.

The last problem is with the .gif file. It's only about 4-frames long!!! When viewed in a web browser, it repeats forever. If I convert it to a video file, it lasts about 1/8th of a second. How would I convert this to, say an mpeg file that repeats a fixed number of times, like, say 20?

Thanks in advance!
--Aaron

---

### Post by user1397 on 2007-03-27
> **Bill Statler said:**
> I was just fighting this same problem today.  I installed tovid_0.30-1_i386.deb on my Ubuntu 6.06 Dapper system.

Seems the problem is that the .deb installs a bunch of stuff in a python2.5 subdirectory where python 2.4 doesn't look for it.  My kludge fix was to move the entire [COLOR=DarkRed]libtovid[/COLOR] directory from [COLOR=DarkRed]/usr/local/lib/python2.5/site-packages[/COLOR] to [COLOR=DarkRed]/usr/local/lib/python2.4/site-packages[/COLOR].

So far, it seems to be working.I'll notify the tovid devs about this.

---

### Post by user1397 on 2007-03-27
> **garlicsalt2 said:**
> Okay, I normally read entire topics to search for answers. This is the first topic I've come across that has 36 pages...

I'll just skip to the end and ask. I hope no one is too upset if this question has been answered. If they are/it has, just point me to the page, and I'll take it from there.

Situation: I have several .3gp files and some .jpg files, plus one animated .gif (four-frame, repeating). I am trying to get these files onto a DVD - and have done so already. The problem? The DVD comes out full-screen. This wouldn't be a problem normally, except that the images were designed for a 3"-4" screen. When viewed on a 13" television or a 15" Monitor, one can't tell what one is seeing. It's too "blotchy". Does anyone know how to tell tovid or equivalent to resize to about 3-4x of the original, and **not **take up the whole screen. Centering the images on the display would be a nice touch too...

For the Jpegs, I would like them to be like a slideshow-type of deal. I had done this before, but the images seem to "hiccup" every second or so. It is as though some one was video-taping a still photo, while in a car on a bumpy road. The image is there, but seems like it is being "jostled" about once every second. I had used a combination of "transcode", "ffmpeg" and "mencoder", as well as "tovid" to do the various conversions.

I wouldn't mind putting some small text into the bottom of the videos and jpegs to denote which segment is which source file.

The last problem is with the .gif file. It's only about 4-frames long!!! When viewed in a web browser, it repeats forever. If I convert it to a video file, it lasts about 1/8th of a second. How would I convert this to, say an mpeg file that repeats a fixed number of times, like, say 20?

Thanks in advance!
--Aarontry this page (it describes tovid CLI commands): _[http://tovid.sourceforge.net/manpages/tovid.html](http://tovid.sourceforge.net/manpages/tovid.html)_, especially the advanced options section.  (mess around with the aspect ratios)
[]("http://tovid.sourceforge.net/manpages/tovid.html")

---

### Post by lgmdaniel on 2007-04-04
> **Bill Statler said:**
> I was just fighting this same problem today.  I installed tovid_0.30-1_i386.deb on my Ubuntu 6.06 Dapper system.

Seems the problem is that the .deb installs a bunch of stuff in a python2.5 subdirectory where python 2.4 doesn't look for it.  My kludge fix was to move the entire [COLOR="DarkRed"]libtovid[/COLOR] directory from [COLOR="DarkRed"]/usr/local/lib/python2.5/site-packages[/COLOR] to [COLOR="DarkRed"]/usr/local/lib/python2.4/site-packages[/COLOR].

So far, it seems to be working.

Ta, this worked for me.

---

### Post by user1397 on 2007-04-19
Please try the tovid .30 ubuntu deb now, all you recent feisty fawn users.  It should install with no problems.

---

### Post by fatalbert on 2007-04-29
Would anyone know if this application can help me out? My situation is that I already have NTSC files that I downloaded from Bittorrnt and so I have a buch of file like this :

VIDEO_TS.BUP  VTS_01_0.BUP  VTS_01_1.VOB  VTS_01_3.VOB
VIDEO_TS.IFO  VTS_01_0.IFO  VTS_01_2.VOB

in a folder called VIEDO_TS and are ready to be ripped to DVD, but I don't know how to do this in Linux.

Thanks

---

### Post by yabbadabbadont on 2007-04-29
You could use tovid, but it isn't necessary since the files are already in the proper DVD format.  Install k3b through synaptic (or apt-get or aptitude or adept, whichever you prefer) and then create a DVD-Video project (it might be called Video-DVD, I'm not sure).  Add the VIDEO_TS directory to the project.  Then burn the DVD.  If you can, use a re-writable DVD first so that if it doesn't work right away, you can reuse the disc.

---

### Post by fatalbert on 2007-04-30
I'm running Gnome and I think k3b is for KDE only. Is that correct? If so, do you know of an app for Gnome?

Thanks for your time and info.

---

### Post by viciouslime on 2007-04-30
> **fatalbert said:**
> I'm running Gnome and I think k3b is for KDE only. Is that correct? If so, do you know of an app for Gnome?

Thanks for your time and info.

No, KDE apps work fine in gnome, it will look a bit odd as it uses the QT toolkit instead of GTK, but it will function just fine.

Edit: Likewise, gnome apps work fine in KDE too!

---

### Post by fatalbert on 2007-04-30
Cool! I will try this when I get home tonight!

---

### Post by fatalbert on 2007-04-30
It worked!

---

### Post by goodtimetribe on 2007-05-19
> **ubuntuman001 said:**
> This guide is based on **_[this]("http://www.ubuntuforums.org/showthread.php?t=169825")_** thread, but it is clearer and more-beginner oriented.


This guide took me two attempts. The CLI has always worked, but after the first install tovidgui would disappear after launching. It now works after removing and reinstalling.

Having practiced with the command line, I think I like it better anyway.

---

### Post by jet2230 on 2007-05-29
thanks dude, someone asked me earlier on today to make them a DVD of a movie they saw on my laptop. i didn't know how, but i knew it was possible thru ubuntu - then i did a quick google search ´ubuntu avi to dvd´ which bought me to this thread, and my questions have been answered.

currently encoding a full DVD from 2 split avi files with covers + menus using the tovidgui... spent maximum 5mins reading your guide to accomplish this. i am so impressed. thank you for sharing this wonderful knowledge.

---

### Post by user1397 on 2007-05-29
> **jet2230 said:**
> thanks dude, someone asked me earlier on today to make them a DVD of a movie they saw on my laptop. i didn't know how, but i knew it was possible thru ubuntu - then i did a quick google search ´ubuntu avi to dvd´ which bought me to this thread, and my questions have been answered.

currently encoding a full DVD from 2 split avi files with covers + menus using the tovidgui... spent maximum 5mins reading your guide to accomplish this. i am so impressed. thank you for sharing this wonderful knowledge.this kind of feedback makes my day...:)

you're welcome

---

### Post by dannyboy79 on 2007-05-30
well this didn't work for me. it appeared as though it was but when it got to the point to record the menu.xml and hte 2 mpg files, it says it couldn't find the files despite them being there. I have attached the log file if anyone can help.
i posted it here, 

[http://www.mediafire.com/?9cbi0sp3l1j]("http://www.mediafire.com/?9cbi0sp3l1j")

---

### Post by yabbadabbadont on 2007-05-30
> **dannyboy79 said:**
> well this didn't work for me. it appeared as though it was but when it got to the point to record the menu.xml and hte 2 mpg files, it says it couldn't find the files despite them being there. I have attached the log file if anyone can help.
i posted it here, 

[http://www.mediafire.com/?9cbi0sp3l1j]("http://www.mediafire.com/?9cbi0sp3l1j")

Try putting the log somewhere that doesn't require cookies to be enabled in order to see it....  :roll:

---

### Post by dannyboy79 on 2007-05-31
well I don't know of any places where I can put files for free and I had trouble finding that one. BUT I figured it out on my own. Theres 1 bug, 1 aspect that I don't understand that I think they should allow control on and then there's a weird occurance. I'll explain all 3 issues.

There's a patch here for the xml file fix and the -noask error just prior to burning.
 [http://tovid.wikia.com/wiki/Known_bugs](http://tovid.wikia.com/wiki/Known_bugs)
[http://www.createphpbb.com/tovid/viewtopic.php?p=3209&mforum=tovid#3209](http://www.createphpbb.com/tovid/viewtopic.php?p=3209&mforum=tovid#3209)

but to be honest i have never patched anything before so I am not sure if I have to UNINSTALL tovid suite first OR if I apply the patch and then redo the       ./configure   sudo -c 'make install'
commands will it just overwrite the existing files that don't have the patch?

So i was able to just edit the .xml on my own like the link says and it made the dvd structure so I could burn it . THere was another issue however but I am not sure if it was because I had problems originally due to my ~/ having only 2.4gb of space when tovid said it needed way more. So i ended up going back and forth between encode and  the first screen so maybe that's why it appended a "1" onto the file names of the end .mpg files? 

So here's my grip and would like to be able to control where it puts temp files. I don't get that, why would tovid use a location other then the output directory for temp files? so, I was able to move some stuff around since I wasn't able to find a way to have it put all it's temp files in the output directory. 
Then the other issue was that the names of the .mpg files was this
mvs-potc3a.avi.tovid_encoded.1.mpg
mvs-potc3b.avi.tovid_encoded.1.mpg
BUT tovid was looking for 
mvs-potc3a.avi.tovid_encoded.mpg
mvs-potc3b.avi.tovid_encoded.mpg
so I just simply renamed them before issuing 
the makedvd command from this manual fix
So, before I say that the tovid has a bug about naming, I'll try again and this time make sure that I have enough room so maybe it won't happen again. BUT I would like to know from anyone if they know how to make tovid use the same directory for temp files as the output directory.

MY last question, it has create 2 .mpg files that are 4.1 gb each, is there any way you can tell it to make them a certain size so that it'll fit onto a dvd5 instead of a dvd9? I think I will just create 2 dvd's for this one but my menu will only be on the first disc and who likes to have to pull out the dvd and put in the next one?

Why I like Winbloz for this task is because I use Winavi and it just does everything for me and create the Video and Audio folders and they are never this large and I can just burn it with Nero BUT I am sure I'll figure this out soon and not have to count on winbloz much longer.

---

### Post by yabbadabbadont on 2007-05-31
[http://pastebin.ca/](http://pastebin.ca/)  is a good place to dump log files.

Not to be mean or anything, but you really should read the manpages for tovid and the documentation provided at their wiki.  :D
```

/home/daffy/.tovid $ cat preferences 
# tovid preferences
# Configures working/output directories for tovid
WORKING_DIR=/home/daffy/temp
#OUTPUT_DIR=/video/outfiles

```

There is a new option "-fit" in the SVN version of tovid that allows you to specify the final size of the video.  Otherwise you have to mess with the "-quality" setting to roughly adjust the size.

---

### Post by dannyboy79 on 2007-05-31
thanks for the info. You're absolutely correct, I always tell people to read the man pages and for some reason it didn't even cross my mind as some packages that I install from source don't have man pages. None-the-less, I should have tried, man tovid. 

I also always tell people to  look thru gogle before posting and I did look thru gogle and couldn't come up with a good way to phrase the questoion (temp files location for tovid) and kept getting crap results. As far as the wiki, that's how I solved the -noask issue so I did read it, just not in regards to the working directory issue.

As for my question about applying the patch and reinstalling, will that work if I DON'T uninstall it first and just hope that the patched files overwrite the other ones. Also, now that you say the SVN version has a way to spcifiy the final video size, will I have to uninstall the current version before installing the SVN? also, do you know if the patch for the -noask error is applied within the SVN source?

Thanks again for your help!

---

### Post by yabbadabbadont on 2007-05-31
Just to be safe, you should probably uninstall the old version before installing a new one (patched or otherwise).  Your ~/.tovid config directory will not be touched.  If you install the SVN version, you will need to uninstall the previous one first.  Yes, the SVN code has been patched.  It is always the most current development version.

---

### Post by dannyboy79 on 2007-05-31
my movie is finally created, I had to use quality 5 for 2 avi's files that were 700mb in size, it ends up being around 3.5gb dvd movie. the menu appeared to have worked (meaning there is a menu.mpg which has my chosen music and pic and it located within the working dir) but isn't loading when I chose to play the dvd thru mplayer, the movie just starts right away? and since I chose to enable the working directory to be the same as the temp dir per the ~/.tovid/preferences file I can't seem to find any log file anymore? i've done a find for it using *tovid and it only found these files:
sudo find / -name *tovid
/usr/local/lib/python2.5/site-packages/libtovid
/usr/local/bin/tovid
/usr/local/bin/pytovid
/home/daniel/.tovid
/home/daniel/.tovid/stats.tovid
/media/500gb/downloaded/linux-programs/tovid-0.30/src/pytovid
/media/500gb/downloaded/linux-programs/tovid-0.30/src/tovid
/media/500gb/downloaded/linux-programs/tovid-0.30/libtovid

i know when I had the working dir still what it was as the default, it put them in ~/.tovid but now that has only stats files, preferences, and tovid.config. Any help from yaba................. would be apprecaited and yes, I did google this and I did read the man pages.

---

### Post by yabbadabbadont on 2007-05-31
Sorry, no clue on this.  Try posting your issue on the tovid forums.  Just FYI, there is a special thread there for you to use so that you have five posts.  The forum software there won't let you post anything that looks like it might be a URL until your user has five posts.

---

### Post by dannyboy79 on 2007-05-31
ok, very quick response, now that's the best support I have ever had and I didn't even have to pay for it. thanks for the reponse despite not being able to specifically help (don't get me wrong, i didn't think without the log file, you'd be able to tell me why the menu isn't showing up) I don't want a menu so it's actually ok,. but I spent all this time resizing the image I downloaded from the net with gimp and chosing a song to play for 90 seconds and what not so I was kind of like, WOW, this is gonna be cool but now that it doesn't work it's not a big deal as I am used to watching discs with no menu (avi files)
And the log file issue is very weird I might add.

---

### Post by unabatedshagie on 2007-06-05
Apologies for bumping this thread but I'm having a small problem when I try to encode any videos.

The process seems to be successful but when I burn it to disk or try and view the .mpg file the audio is out of sync with the video.

I have tried various combinations of settings with no luck.

Anyone have any suggestions as to how I could solve the problem?

---

### Post by dannyboy79 on 2007-06-07
> **unabatedshagie said:**
> Apologies for bumping this thread but I'm having a small problem when I try to encode any videos.

The process seems to be successful but when I burn it to disk or try and view the .mpg file the audio is out of sync with the video.

I have tried various combinations of settings with no luck.

Anyone have any suggestions as to how I could solve the problem?

check the tovid forums as I can almost guarantee there are instructions about how to fix this. I am lucky and the 3 I have done so far have been in sync but I am sure that sooner or later I'll have to read it. If you find out the answer be sure to post back here what ya did. Which encoder are you using? I left it the way it was and like I said, I don't have any issues. Are your .avi files in sync before you encode them?

---

### Post by unabatedshagie on 2007-06-07
I have tried every combination of settings.

The two NTSC one's and PAL, with both mpeg2enc & ffmpeg.

Whatever settings I seem to choose the audio is off by the same amount everytime.

The avi file plays perfectly with no problems with the sound.

---

### Post by dannyboy79 on 2007-06-07
what kind of hardware do you have? are you performing other cpu intensive stuff while encoding? I would try to encode it when you're not doing anything at all and see if that helps. if it does, than that's your problem possibly. Also, I have read that avidemux can resync audio but I think it's for avi files but I am not sure as I haven't tried it yet since I haven't had the need. You know, when you this happens to me in Winbloz like on Winavi or AutoGK, I never knew how to fix it in winbloz either, so hopefully there is a fix for this in linux!!

---

### Post by unabatedshagie on 2007-06-07
I have a dual core 64 bit processor (5200+) with 2 gig ram.

I usually start the file encoding before I go to bed and leave it running overnight.

There are no significant programs running, I sometimes have transmission downloading in the background.

---

### Post by dannyboy79 on 2007-06-07
well then your hardware certainly isn't the problem! you have plenty of power there. not sure then, sorry.

---

### Post by morequende on 2007-06-14
Hey to all! So i followed the guide, and though it says that Tovid is for AMD64 i'm getting the following when i try ro install it

morequende@ubuntu:~/Desktop$ sudo dpkg -i tovid_0.27_0.27_1_i386.deb
dpkg: error processing tovid_0.27_0.27_1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 tovid_0.27_0.27_1_i386.deb

does anybody have any idea?

thanks in advance :D

---

### Post by sagarhshah on 2007-06-14
> **morequende said:**
> Hey to all! So i followed the guide, and though it says that Tovid is for AMD64 i'm getting the following when i try ro install it

morequende@ubuntu:~/Desktop$ sudo dpkg -i tovid_0.27_0.27_1_i386.deb
dpkg: error processing tovid_0.27_0.27_1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 tovid_0.27_0.27_1_i386.deb


dude the one your trying to install is for x86 and not amd64 notice the i386.deb at the end of the file? the i386 means its for those with x86 versions of ubuntu.

you need to get the one made for amd64

---

### Post by user1397 on 2007-06-14
> **morequende said:**
> Hey to all! So i followed the guide, and though it says that Tovid is for AMD64 i'm getting the following when i try ro install it

morequende@ubuntu:~/Desktop$ sudo dpkg -i tovid_0.27_0.27_1_i386.deb
dpkg: error processing tovid_0.27_0.27_1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 tovid_0.27_0.27_1_i386.deb

does anybody have any idea?

thanks in advance :DI have no idea why you're trying to install tovid version 0.27, the latest version is 0.30 [http://tovid.org](http://tovid.org)

edit: as dannyboy states below, just install from source using the instructions on the main tovid site, because then you don't have to worry about architecture.

---

### Post by dannyboy79 on 2007-06-14
> **morequende said:**
> Hey to all! So i followed the guide, and though it says that Tovid is for AMD64 i'm getting the following when i try ro install it

morequende@ubuntu:~/Desktop$ sudo dpkg -i tovid_0.27_0.27_1_i386.deb
dpkg: error processing tovid_0.27_0.27_1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 tovid_0.27_0.27_1_i386.deb

does anybody have any idea?

thanks in advance :D

not to mention, he states in his guide that the .deb doesn't even work for Ubuntu so use the source, it's all scripts so Platform doesn't matter.

---

### Post by morequende on 2007-06-15
Ok thanks... it's just that i'm new to Linux and i'm still learning... anyway, thanks:p

---

### Post by Beastofomous on 2007-07-05
hey everyone I managed to use todisc to make a menu on a dvd successfully before, actually using the same .avi file im about to show you an error report from, but now i changed a couple settings that i didnt want and it wont work... heres the log file if, if anyone can help me out it would be greatly appreciated.

[todisc]: 
[todisc]: Creating a title image
Running convert -size 620x100 xc:none -font Helvetica -pointsize 30 -fill black 
-stroke black -gravity center -annotate +0+0 Die Hard With a Vengeance -fill 
#CDC0B0 -stroke gray -strokewidth 1 -annotate +1+1 Die Hard With a Vengeance 
miff:- |
convert - -trim +repage -blur 0x0.4 /tmp/todisc-work1/title_txt.png

Running: ffmpeg -i /home/craig/myDocuments/iso_movie/diehard3.mpg -an -ss 2 
-vframes 1 -s 320x240 /tmp/todisc-work1/pics/0/%06d.jpg

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, mpeg, from '/home/craig/myDocuments/iso_movie/diehard3.mpg':
  Duration: 00:59:46.9, start: 0.178022, bitrate: 6263 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 9800 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 224 kb/s
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, image2, to '/tmp/todisc-work1/pics/0/%06d.jpg':
  Stream #0.0: Video: mjpeg, yuvj420p, 320x240, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    1 q=1.6 Lsize=       0kB time=0.0 bitrate=   0.0kbits/s    

video:2kB audio:0kB global headers:0kB muxing overhead -100.000000%
[todisc]:
[todisc]: =========================================================
[todisc]:
[todisc]: Preview OK, continuing.
[todisc]:
[todisc]: =========================================================
[todisc]:
[todisc]: Checking /home/craig/myDocuments/iso_movie/diehard3.mpg for 
compliance...
[todisc]: Running nice
tcdemux -f
29.970 -W
-i /home/craig/myDocuments/iso_movie/diehard3.mpg > /tmp/todisc-work1/nav0_log
[todisc]:
[todisc]: =========================================================
[todisc]:
 video codec:    MPEG2 
 video bitrate:  1813.307 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   3586.95  seconds
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[todisc]: todisc encountered an error:
[todisc]: Problem creating images from the video.
tc_memcpy: using sse for memcpy
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_jpg.so] v0.2.1 (2003-08-06) (video) *
[demuxer.c] (pid=15880) processing PU [0], on at PTS=2.0132 sec
[demuxer.c] (pid=15880) AV sync established for PU [0] at PTS=2.0020 (-0.0112)
[demuxer.c] (pid=15873) processing PU [0], on at PTS=2.0132 sec
[demuxer.c] (pid=15873) AV sync established for PU [0] at PTS=2.0020 (-0.0112)
tc_memcpy: using sse for memcpy
tc_memcpy: using sse for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: 3dnow
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /home/craig/myDocuments/iso_movie/diehard3.mpg (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 16:9
[transcode] V: zoom             | 320x240  1.33:1 (Lanczos3)
[transcode] V: bits/pixel       | 0.782
[transcode] V: decoding fps,frc | 29.970,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  224 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse 3dnowext 3dnow mmxext mmx asm C)
[transcode] V: video buffer     | 10 @ 720x480
[import_vob.so] tccat -i "/home/craig/myDocuments/iso_movie/diehard3.mpg" -t vob -d 1 -S 60 | tcdemux -a 0 -x ac3 -S 0 -M 1 -d 1 | tcextract -t vob -a 0 -x ac3 -d 1 | tcdecode -x ac3 -d 1 -s 1.000000,1.000000,1.000000 -A 0
[import_vob.so] tccat -i "/home/craig/myDocuments/iso_movie/diehard3.mpg" -t vob -d 1 -S 60 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 1 | tcextract -t vob -a 0 -x mpeg2 -d 1 | tcdecode -x mpeg2 -d 1 -y yv12

encoding frame [10],  11.20 fps,  1.0%, ETA: 0:00:52, ( 7| 1| 0)  
encoding frame [20],  13.82 fps,  2.7%, ETA: 0:00:42, ( 6| 1| 1)  
encoding frame [30],  14.96 fps,  4.3%, ETA: 0:00:38, ( 6| 1| 0)  
encoding frame [40],  14.39 fps,  6.0%, ETA: 0:00:39, ( 4| 1| 2)  
encoding frame [50],  15.04 fps,  7.7%, ETA: 0:00:36, ( 2| 1| 0)  
encoding frame [60],  14.73 fps,  9.4%, ETA: 0:00:36, ( 5| 1| 2)  
encoding frame [70],  15.11 fps, 11.0%, ETA: 0:00:35, ( 6| 1| 1)  
encoding frame [80],  14.80 fps, 12.7%, ETA: 0:00:35, ( 6| 1| 2)  
encoding frame [90],  15.13 fps, 14.4%, ETA: 0:00:33, ( 6| 1| 1)  
encoding frame [100],  15.05 fps, 16.1%, ETA: 0:00:33, ( 8| 1| 0)  
encoding frame [110],  14.86 fps, 17.7%, ETA: 0:00:33, ( 6| 1| 1)  
encoding frame [120],  15.30 fps, 19.4%, ETA: 0:00:31, ( 6| 1| 0)  
encoding frame [130],  15.09 fps, 21.1%, ETA: 0:00:31, ( 6| 1| 2)  
encoding frame [140],  15.01 fps, 22.7%, ETA: 0:00:30, ( 7| 1| 1)  
encoding frame [150],  15.05 fps, 24.4%, ETA: 0:00:30, ( 6| 1| 2)  
encoding frame [160],  15.17 fps, 26.1%, ETA: 0:00:29, ( 7| 1| 0)  
encoding frame [170],  14.99 fps, 27.8%, ETA: 0:00:28, ( 6| 1| 2)  
encoding frame [180],  15.08 fps, 29.4%, ETA: 0:00:27, ( 7| 1| 0)  
encoding frame [190],  14.89 fps, 31.1%, ETA: 0:00:27, ( 7| 1| 1)  
encoding frame [200],  14.92 fps, 32.8%, ETA: 0:00:26, ( 6| 1| 1)  
encoding frame [210],  14.85 fps, 34.4%, ETA: 0:00:26, ( 5| 1| 3)  
encoding frame [220],  14.94 fps, 36.1%, ETA: 0:00:25, ( 5| 1| 1)  
encoding frame [230],  14.86 fps, 37.8%, ETA: 0:00:25, ( 6| 1| 0)  
encoding frame [240],  14.80 fps, 39.5%, ETA: 0:00:24, ( 6| 1| 1)  
encoding frame [250],  14.99 fps, 41.1%, ETA: 0:00:23, ( 6| 1| 0)  
encoding frame [260],  14.90 fps, 42.8%, ETA: 0:00:22, ( 6| 1| 1)  
encoding frame [270],  14.98 fps, 44.5%, ETA: 0:00:22, ( 6| 1| 0)  
encoding frame [280],  14.91 fps, 46.2%, ETA: 0:00:21, ( 7| 1| 1)  
encoding frame [290],  14.97 fps, 47.8%, ETA: 0:00:20, ( 4| 1| 1)  
encoding frame [300],  14.92 fps, 49.5%, ETA: 0:00:20, ( 5| 1| 2)  
encoding frame [310],  14.88 fps, 51.2%, ETA: 0:00:19, ( 7| 1| 1)  
encoding frame [320],  14.91 fps, 52.8%, ETA: 0:00:18, ( 5| 1| 3)  
encoding frame [330],  14.98 fps, 54.5%, ETA: 0:00:18, ( 6| 1| 1)  
encoding frame [340],  14.95 fps, 56.2%, ETA: 0:00:17, ( 8| 1| 0)  
encoding frame [350],  14.98 fps, 57.9%, ETA: 0:00:16, ( 8| 1| 0)  
encoding frame [360],  15.03 fps, 59.5%, ETA: 0:00:16, ( 5| 1| 1)  
encoding frame [370],  14.99 fps, 61.2%, ETA: 0:00:15, ( 6| 1| 2)  
encoding frame [380],  15.02 fps, 62.9%, ETA: 0:00:14, ( 6| 1| 0)  
encoding frame [390],  14.98 fps, 64.5%, ETA: 0:00:14, ( 7| 1| 1)  
encoding frame [400],  15.02 fps, 66.2%, ETA: 0:00:13, ( 6| 1| 0)  
encoding frame [410],  14.96 fps, 67.9%, ETA: 0:00:12, ( 6| 1| 2)  
encoding frame [420],  14.94 fps, 69.6%, ETA: 0:00:12, ( 7| 1| 1)  
encoding frame [430],  14.99 fps, 71.2%, ETA: 0:00:11, ( 6| 1| 0)  
encoding frame [440],  15.00 fps, 72.9%, ETA: 0:00:10, ( 7| 1| 1)  
encoding frame [450],  14.99 fps, 74.6%, ETA: 0:00:10, ( 8| 1| 0)  
encoding frame [460],  15.00 fps, 76.3%, ETA: 0:00:09, ( 6| 1| 2)  
encoding frame [470],  15.00 fps, 77.9%, ETA: 0:00:08, ( 6| 1| 1)  
encoding frame [480],  14.98 fps, 79.6%, ETA: 0:00:08, ( 6| 1| 2)  
encoding frame [490],  15.02 fps, 81.3%, ETA: 0:00:07, ( 7| 1| 0)  
encoding frame [500],  14.99 fps, 82.9%, ETA: 0:00:06, ( 6| 1| 2)  
encoding frame [510],  14.97 fps, 84.6%, ETA: 0:00:06, ( 7| 1| 1)  
encoding frame [520],  15.01 fps, 86.3%, ETA: 0:00:05, ( 8| 1| 0)  
encoding frame [530],  15.03 fps, 88.0%, ETA: 0:00:04, ( 6| 1| 1)  
encoding frame [540],  15.06 fps, 89.6%, ETA: 0:00:04, ( 6| 1| 0)  
encoding frame [550],  15.03 fps, 91.3%, ETA: 0:00:03, ( 6| 1| 2)  
encoding frame [560],  15.03 fps, 93.0%, ETA: 0:00:02, ( 6| 1| 0)  
encoding frame [570],  15.00 fps, 94.6%, ETA: 0:00:02, ( 6| 1| 2)  
encoding frame [580],  15.09 fps, 96.3%, ETA: 0:00:01, ( 7| 1| 0)  
encoding frame [590],  15.06 fps, 98.0%, ETA: 0:00:00, ( 6| 1| 2)  
encoding frame [600],  15.09 fps, 99.7%, ETA: 0:00:00, ( 7| 1| 0)  
failed to write Y plane of frame(demuxer.c) write program stream packet: Broken pipe
(decode_ac3.c) write failed

---

### Post by yabbadabbadont on 2007-07-10
@Beastofomous: If you haven't already, start a thread on the tovid forums and post your log.  The forum software there won't let you post the log until you have made at least five posts.  There is a thread there specifically for making five junk posts, so that you can then post your log.

[http://www.createphpbb.com/tovid/](http://www.createphpbb.com/tovid/)

---

### Post by robertmf on 2007-07-20
***Thank You ***for figuring out the Ubuntu tovid install and posting this HOW-TO. :)

---

### Post by user1397 on 2007-07-20
> **robertmf said:**
> ***Thank You ***for figuring out the Ubuntu tovid install and posting this HOW-TO. :)you're welcome!  though I have had much help from many people on this, so don't give all the credit to me!

---

### Post by user1397 on 2007-08-05
In recent tovid news, the devs have patched up version 0.30 to 0.30.2, which is now downloadable at [_[U]here_[/U]]("http://tovid.sourceforge.net/download/ubuntu/tovid_0.30.2-1_i386.deb").

Also, they have moved their program's site from sourceforge.net to google code: [http://code.google.com/p/tovid/](http://code.google.com/p/tovid/)

---

### Post by user1397 on 2007-08-06
Okay I have uploaded tovid's first true deb package to the main site (thanks Frak!)

It is still the same link as the one I posted several hours ago: [_[U]here_[/U]]("http://tovid.sourceforge.net/download/ubuntu/tovid_0.30.2-1_i386.deb")

This time, however, it auto installs all dependencies for you.

---

### Post by robertmf on 2007-08-06
FEISTY - tovidgui generates makexml -noask  illegal parameter   

(FEISTY - mencoder is broken)

---

### Post by user1397 on 2007-08-07
> **robertmf said:**
> FEISTY - tovidgui generates makexml -noask  illegal parameter   

(FEISTY - mencoder is broken)Please report this in the tovid IRC chatroom: irc.freenode.net/tovid

or post a bug report on the tovid forums (link is on the first page of this thread)

---

### Post by VON_CAPO on 2007-08-10
I installed the package "  tovid_0.30.2-1_i386.deb  " and I created a new entry in Applications/Sound & Video/tovidgui to launch the GUI.

I used 2 MPG files (they were already encoded from AVI to MPG using DeVeDe),
and I burnt a DVD... ---> SUCCESS!!! 

Also I included a very crude menu, and all the process took some 10 minutes.

Very neat software indeed.

Thank you for let us know this jewel. :popcorn:

EDIT: I am attaching the log file

---

### Post by dannyboy79 on 2007-08-10
> **ubuntuman001 said:**
> Please report this in the tovid IRC chatroom: irc.freenode.net/tovid

or post a bug report on the tovid forums (link is on the first page of this thread)

it's already been reported, there's a solution on the website

---

### Post by BGreet on 2007-08-18
After installing the .deb I get a weird error:

Found 2 installations of tovid on your system!
I won't run until there is only one of me :)
Installed versions:
   /usr/bin/tovid
   /usr/bin/X11/tovid
Exiting...

I tried removing tovid from one or the other directories and it then tells me that there are no copies of tovid available.  Not sure what to do, any help appreciated.  Thanks!

---

### Post by dannyboy79 on 2007-08-20
well you should never just remove a file and think that's the whole program. sometimes it is but not always. you should use a package manager to remove it. if you downloaded the .deb for debian than that was a mistake as it's not working I read somewhere. you need to go to tovid website and read a little. So to remove it you can use this command:
sudo dpkg -r package_name
then just to double check, do a search for tovid again.
sudo find / -name *tovid*
and see if there's anything left around. if so, then you can remove it
Then you'll want to download the source and configure, make, make install. there's great info in the faq on the tovid website, also read teh know common problems and the install page.

---

### Post by dannyboy79 on 2007-08-20
does anyone know how to keep .avi resolutions the same? for example I have a file that per MediaInfo is:

Width                : 640 pixels
Height               : 272 pixels
Aspect ratio         : 2.35
Frame rate           : 23.976 fps


and when I run it through tovid (option for full dvd), it stretchs it to the standard dvd width and height (720x480, I think?), anyway, everything is stretched vertically very noticeably. the movie is watchable but it's just not right! can anyone suggeest anything to how I can fix this? thank you

---

### Post by user1397 on 2007-08-24
> **dannyboy79 said:**
> does anyone know how to keep .avi resolutions the same? for example I have a file that per MediaInfo is:

Width                : 640 pixels
Height               : 272 pixels
Aspect ratio         : 2.35
Frame rate           : 23.976 fps


and when I run it through tovid (option for full dvd), it stretchs it to the standard dvd width and height (720x480, I think?), anyway, everything is stretched vertically very noticeably. the movie is watchable but it's just not right! can anyone suggeest anything to how I can fix this? thank youdo u have a widescreen tv?

---

### Post by user1397 on 2007-08-24
by the way, tovid 0.31 came out

an ubuntu deb will prolly soon be made.

---

### Post by dannyboy79 on 2007-08-25
> **ubuntuman001 said:**
> do u have a widescreen tv?

i don't see what the point of that question is? I do but that shouldn't matter. what's happening is that the video is being stretched vertically to be 720 x 480 I think and since the video is only 2 hundred something tall, it's making the poeple and everything look stretched vertically. anyone have a suggestion?

---

### Post by user1397 on 2007-08-26
> **dannyboy79 said:**
> i don't see what the point of that question is? I do but that shouldn't matter. what's happening is that the video is being stretched vertically to be 720 x 480 I think and since the video is only 2 hundred something tall, it's making the poeple and everything look stretched vertically. anyone have a suggestion?well i just thought maybe the tv's aspect ratio might stretch it out in weird ways, since every time I've made a video with tovid, resolutions always work out so that the movie looks fine to me on my tv

as to your particular problem, I have no idea, try the tovid forums or the irc channel #tovid on freenode

---

### Post by ephman on 2007-08-26
> **BGreet said:**
> After installing the .deb I get a weird error:

Found 2 installations of tovid on your system!
I won't run until there is only one of me :)
Installed versions:
   /usr/bin/tovid
   /usr/bin/X11/tovid
Exiting...

I tried removing tovid from one or the other directories and it then tells me that there are no copies of tovid available.  Not sure what to do, any help appreciated.  Thanks!

i go the same error installing the .deb, and i know 100% i didn't have it already installed.  when i installed by svn it was totally fine.  try installing that way.

thanks for the bandwidth,

ephman

---

### Post by user1397 on 2007-08-27
> **ephman said:**
> i go the same error installing the .deb, and i know 100% i didn't have it already installed.  when i installed by svn it was totally fine.  try installing that way.

thanks for the bandwidth,

ephman
really? are you talking about the 0.30-2 ubuntu deb?

---

### Post by dannyboy79 on 2007-08-28
that deb is broken and it specifically stated that on their website I believe. just build from latest source which is 0.31, it doesn't have the error's anymore and it works straight away! I just need to figure out how to get the video to encode it the same as it's source instead of stretching it verically.

---

### Post by JungleJoker on 2007-08-29
Hi, I've got a stupid question: I succeeded in installing tovid 0.31 and am trying it out right now, the only problem I have is that the GUI interface is to big for my screen. So I can't see the buttons on the buttom which would help me configuring the dvd-buttons etc. Anyone know how to fix this? (simpy resising the window doesn't help, off course)

---

### Post by dannyboy79 on 2007-08-29
i suggest asking on the tovid forum. not sure sorry.

---

### Post by user1397 on 2007-08-29
> **JungleJoker said:**
> Hi, I've got a stupid question: I succeeded in installing tovid 0.31 and am trying it out right now, the only problem I have is that the GUI interface is to big for my screen. So I can't see the buttons on the buttom which would help me configuring the dvd-buttons etc. Anyone know how to fix this? (simpy resising the window doesn't help, off course)this actually has happened to me too, but I haven't researched about it yet.  If anything comes up, I'll let you know.

---

### Post by dannyboy79 on 2007-08-30
> **ubuntuman001 said:**
> this actually has happened to me too, but I haven't researched about it yet.  If anything comes up, I'll let you know.

i looked into it, if you didn't get any suggestions from the tovid forums, check out devilspie. [http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

---

### Post by grepster on 2007-09-01
> Hi, I've got a stupid question: I succeeded in installing tovid 0.31 and am trying it out right now, the only problem I have is that the GUI interface is to big for my screen. So I can't see the buttons on the buttom which would help me configuring the dvd-buttons etc. Anyone know how to fix this? (simpy resising the window doesn't help, off course)

This appears to be a bug in todiscgui.  I've posted an link to a temporary patch below that should serve until we can think about a better solution..
Using the smallest font size in the File-> config option may help a bit, but probably won't solve it without the patch if your screen res is not large enough.

As a side note, I recommend trying 1152x864 in your xorg.conf for screen resoltuion, once you get the fonts tweaked how you like you might not want to go back !

[http://tovid.sourceforge.net/download/tovid-0.31.patch](http://tovid.sourceforge.net/download/tovid-0.31.patch)

Use by cd'ing into the top level directory of 0.31.
```
cd tovid-0.31/
```
Then issuing ( lets say you downloaded the patch to /tmp):
```
patch -p1 < /tmp/tovid-0.31.patch
```

HTH,

grepper

---

### Post by yabbadabbadont on 2007-09-01
> **grepster said:**
> As a side note, I recommend trying 1152x864 in your xorg.conf for screen resoltuion, once you get the fonts tweaked how you like you might not want to go back !

Assuming, of course, that your monitor will **go** that high...  (mine won't :(  then again, I only use the command line tools ;))

---

### Post by crouzilles on 2007-09-29
I have a bit of a problem.
I have installed everything success fully, but when I want to run tovid i get the following error:
tovidgui requires wxPython 2.6; please install or upgrade wxPython.

The last thing I installed was wxPython so i tried to do an install again and here is what I get:
python-wxgtk2.8 is already the newest version.

Does anybody know what's wrong?

Thank you

---

### Post by user1397 on 2007-09-29
> **crouzilles said:**
> I have a bit of a problem.
I have installed everything success fully, but when I want to run tovid i get the following error:
tovidgui requires wxPython 2.6; please install or upgrade wxPython.

The last thing I installed was wxPython so i tried to do an install again and here is what I get:
python-wxgtk2.8 is already the newest version.

Does anybody know what's wrong?

Thank youfor some reason the latest version of wxPython returns this error, I believe if you install the 2.6 version it'll work

---

### Post by herbster on 2007-10-04
Okay, I've gotten it up and running, was going through the motions with random videos to test the program and no matter the video I choose, the Preview Video button opens up Mplayer which gives me this error everytime:

[IMG]http://www.bobgill.net/mplayerrorr.png[/IMG]

:confused: And I cannot watch anything with it. I've never used mplayer and after going through the Preferences I can't find anything that would fix this. Any help appreciated, TIA.

---

### Post by user1397 on 2007-10-04
> **herbster said:**
> Okay, I've gotten it up and running, was going through the motions with random videos to test the program and no matter the video I choose, the Preview Video button opens up Mplayer which gives me this error everytime:

[IMG]http://www.bobgill.net/mplayerrorr.png[/IMG]

:confused: And I cannot watch anything with it. I've never used mplayer and after going through the Preferences I can't find anything that would fix this. Any help appreciated, TIA.do you have the necessary codecs for the specific video you're watching? install the ubuntu-restricted-extras package, and that covers most codecs.  also, you can always try another media player, such as totem, xine, kaffeine, etc.

---

### Post by herbster on 2007-10-04
> **ubuntuman001 said:**
> do you have the necessary codecs for the specific video you're watching? install the ubuntu-restricted-extras package, and that covers most codecs.  also, you can always try another media player, such as totem, xine, kaffeine, etc.

Yup, every video format works just fine with VLC and Xine, but how do I tell the tovidgui program to use one of those players instead of mplayer when I click the Preview button ???

EDIT: Wait a sec, I just realized that Preview is only playing the video as it currently is, I was under the impression it was playing the video or a clip of it as a preview of how it will look *after* being encoded. Woops :)

---

### Post by kr0n1x on 2007-10-15
why i haven't "python2.6" in Synaptic? :( i've this error when i try to start tovidgui:

> pasquale@pasquale-desktop:~/Discarica/tovid$ tovidgui -s
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running command:
makemenugui
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Traceback (most recent call last):
  File "/usr/local/bin/makemenugui", line 26, in <module>
    import wxversion
ImportError: No module named wxversion
There was an error importing the 'wx' libraries. The above
output should help you find what went wrong. Re-installing
wxPython 2.6 (or upgrading from wxPython 2.4 to 2.6) may
help. Consult the tovid homepage (tovid.org) for further
assistance.
Sorry, 'tovidgui' will not work.
pasquale@pasquale-desktop:~/Discarica/tovid$ 


i've python2.4 and python2.5...you?

---

### Post by yabbadabbadont on 2007-10-15
> **kr0n1x said:**
> why i haven't "python2.6" in Synaptic? :( i've this error when i try to start tovidgui:

i've python2.4 and python2.5...you?

Try installing python-wxversion.
```
/home/daffy $ aptitude show python-wxversion 
Package: python-wxversion
State: installed
Automatically installed: no
Version: 2.6.3.2.1.5ubuntu6
Priority: optional
Section: universe/python
Maintainer: Ubuntu MOTU developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 90.1k
Depends: python-central (>= 0.5.8), python (>= 2.5), python (< 2.6)
Conflicts: wxpython2.6-0
Replaces: wxpython2.6-0
Description: wxWidgets Cross-platform C++ GUI toolkit (wxPython version selector)
 wxWidgets (formerly known as wxWindows) is a class library for C++ providing GUI components and other facilities on several
 popular platforms (and some unpopular ones as well).  For more information see http://wxwidgets.org 
 
 This package provides the wxPython version selector.

```

---

### Post by kr0n1x on 2007-10-16
ok...did..but:
```
pasquale@pasquale-desktop:~$ tovidgui -s
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running command:
makemenugui
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
tovidgui requires wxPython 2.6 or 2.8.
Please install or upgrade wxPython.
pasquale@pasquale-desktop:~$ 

```

---

### Post by kr0n1x on 2007-10-16
my dvds born correcly.
i born 1 dvd yesterday, and another one today (not the same film/file), and i had 2 times the same error:

```
 99.69% done, estimate finish Tue Oct 16 17:05:57 2007
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 0
827575 extents written (1616 MB)
builtin_dd: 827584*2KB out @ average 7.8x1352KBps
/dev/dvdrw: flushing cache
/dev/dvdrw: reloading tray
:-( unable to reload tray: Input/output error
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not burn the disc to /dev/dvdrw
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
pasquale@pasquale-desktop:~/dlcompleti$ 

```

unable to reload tray...why?

but the dvds work correctly

---

### Post by user1397 on 2007-10-17
> **kr0n1x said:**
> my dvds born correcly.
i born 1 dvd yesterday, and another one today (not the same film/file), and i had 2 times the same error:

```
 99.69% done, estimate finish Tue Oct 16 17:05:57 2007
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 0
827575 extents written (1616 MB)
builtin_dd: 827584*2KB out @ average 7.8x1352KBps
/dev/dvdrw: flushing cache
/dev/dvdrw: reloading tray
:-( unable to reload tray: Input/output error
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not burn the disc to /dev/dvdrw
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
pasquale@pasquale-desktop:~/dlcompleti$ 

```unable to reload tray...why?

but the dvds work correctlywell tovid is at an alpha version stage, so it won't always be perfect.  The good thing is that your dvd worked after all; as for the error message, try looking for it in the tovid wiki ([http://tovid.org/](http://tovid.org/)
or look for it in the tovid forums (a link is in the wiki)

---

### Post by user1397 on 2007-10-29
i have finally made a deb (well with checkinstall, but it actually download all dependencies for you) and posted it on the tovid site.

so please try it and see if it works: [http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu](http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu)

I will make this type of deb from now on.

---

### Post by lukon on 2007-12-05
Error as a result of double clicking the tovid_0.31.all.deb:

Dialog box reports:

"Error: Dependency is not satisfyable: python2.5"

This is a Dapper 6.06 system.

Any suggestions?

---

### Post by mssever on 2007-12-05
> **lukon said:**
> Error as a result of double clicking the tovid_0.31.all.deb:

Dialog box reports:

"Error: Dependency is not satisfyable: python2.5"

This is a Dapper 6.06 system.

Any suggestions?

The easiest thing is to upgrade to a more recent version of Ubuntu. There was a major change in Python between Dapper and Edgy. Alternatively, if you know what you're doing, you might be able to backport either Tovid or Python 2.5. But that probably wouldn't be a simple process.

---

### Post by user1397 on 2007-12-05
> **lukon said:**
> Error as a result of double clicking the tovid_0.31.all.deb:

Dialog box reports:

"Error: Dependency is not satisfyable: python2.5"

This is a Dapper 6.06 system.

Any suggestions?yep, as mssever said, dapper used python2.4 while edgy and onward uses python2.5
the 2.5 version is not in the repositories of 6.06, so unless you upgrade to a newer release, then there's not much you can do.

---

### Post by yabbadabbadont on 2007-12-05
> **lukon said:**
> Error as a result of double clicking the tovid_0.31.all.deb:

Dialog box reports:

"Error: Dependency is not satisfyable: python2.5"

This is a Dapper 6.06 system.

Any suggestions?

Try manually installing tovid using the instructions on the tovid wiki.  As long as Dapper has wxPython 2.6 (or newer) it will probably work.  There is no version requirement listed on the wiki for python itself.

[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

---

### Post by lukon on 2007-12-05
Thanks for the explanation and suggestion.

So I am to understand that the tovid installer simply won't work with Dapper, but there is a way to install a less functional version of tovid on Dapper by doing some complicated things specified on the wiki.

So here's my suggestion. Let's have the wiki clearly state these facts. Also, perhaps the person who designed the tovid installer might also make another tovid installer just for Dapper, one that will install the appropriate, although less functional, version of tovid. This can be a big help to linux novices like myself.

Oh, and, if tovid isn't for me: where can I get a DVD authoring program that both runs on Dapper AND is usable by someone who has never authored a DVD before (such as myself)?

---

### Post by yabbadabbadont on 2007-12-05
> **lukon said:**
> Thanks for the explanation and suggestion.

So I am to understand that the tovid installer simply won't work with Dapper, but there is a way to install a less functional version of tovid on Dapper by doing some complicated things specified on the wiki.

So here's my suggestion. Let's have the wiki clearly state these facts. Also, perhaps the person who designed the tovid installer might also make another tovid installer just for Dapper, one that will install the appropriate, although less functional, version of tovid. This can be a big help to linux novices like myself.

Oh, and, if tovid isn't for me: where can I get a DVD authoring program that both runs on Dapper AND is usable by someone who has never authored a DVD before (such as myself)?
The tovid authors do not provide (to the best of my knowledge) native packages, just the standard "./configure ; make ; make install" of linux source packages.  The deb package you are trying to install was created by an Ubuntu *user*, not a tovid developer.  The tovid wiki provides generic instructions that should work on *any* linux distribution, not just Ubuntu.  Just FYI.  If you have trouble following the wiki's instructions, then I suggest that you follow the links provided there to the tovid community pages.  One is to a forum that is not that active these days, but still contains a lot of information.  The other is to the tovid group on google.  For that matter, if you post your questions about the wiki instructions in this thread, I'm sure that someone will be able to help you.

---

### Post by user1397 on 2007-12-05
> **lukon said:**
> Thanks for the explanation and suggestion.

So I am to understand that the tovid installer simply won't work with Dapper, but there is a way to install a less functional version of tovid on Dapper by doing some complicated things specified on the wiki.

So here's my suggestion. Let's have the wiki clearly state these facts. Also, perhaps the person who designed the tovid installer might also make another tovid installer just for Dapper, one that will install the appropriate, although less functional, version of tovid. This can be a big help to linux novices like myself.

Oh, and, if tovid isn't for me: where can I get a DVD authoring program that both runs on Dapper AND is usable by someone who has never authored a DVD before (such as myself)?FYI, I made the latest deb package, and I edited the ubuntu installation instrucitons on the tovid wiki.  the reason I didn't include dapper debs was because
a) dapper is a relatively old release and not tat many people use it
b) the new LTS version will come out in the spring
c) I erased the GUI from my ubuntu pc, cause I turned it into a server, i.e. I can't test debs anymore (though I can still make them and you can test them if you want)

---

### Post by lukon on 2007-12-05
FYI: someone should fix this wiki page here:

[http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu](http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu)

because the following statement on that wiki page has been proven false:

> If you're using Ubuntu dapper 6.06 or newer, just double click the package to open gdebi and install it.

Dapper 6.06 should not be included among the operating systems for which the installer works.

So now I’m curious about something.

I’m told by implication (by yabbadabbadont) that Tovid can be installed on basically any distribution so long as you follow a given generic and complicated procedure. This means that Tovid can indeed work on Dapper 6.06. And it means that Tovid presents NO necessary dependency conflict with whatever version of Python I happen to have.

yabbadabbadont: > The Tovid wiki provides generic instructions that should work on any linux distribution, not just Ubuntu.

But then I am also told by implication (by ubuntuman001) that the Python version DOES matter. 

ubuntuman001: > …Dapper used Python2.4 while Edgy and onward uses Python2.5. The 2.5 version is not in the repositories of 6.06, so unless you upgrade to a newer release, then there's not much you can do.

Something is wrong here. 

Perhaps it is the code of the installer itself that needs a specific version of Python. Is this the case?

Otherwise, either Tovid does care about my Python version (and won’t run on my system) or, the installer is needlessly specific about Python’s version. Which is it?

---

### Post by yabbadabbadont on 2007-12-05
I ran tovid on Dapper.  Nuf said.  ;)

I'm also running it on my current Gentoo system:
```
/home/daffy $ equery l tovid
[ Searching for package 'tovid' in all categories among: ]
 * installed packages
[I--] [ ~] media-video/tovid-0.31 (0)
/home/daffy $ equery l python
[ Searching for package 'python' in all categories among: ]
 * installed packages
[I--] [  ] app-admin/python-updater-0.2 (0)
[I--] [  ] dev-lang/python-2.4.4-r6 (2.4)
[I--] [  ] dev-python/notify-python-0.1.1 (0)
[I--] [  ] dev-python/python-fchksum-1.7.1 (0)
[I--] [  ] dev-python/python-xlib-0.12-r3 (0)
[I--] [  ] dev-python/wxpython-2.6.4.0 (2.6)

```

Notice that I am using python 2.4.

---

### Post by user1397 on 2007-12-06
Here's the deal:
I didn't want to complicate things too much, so I just told you (lukon) that there wasn't much you can do.

But really, tovid is just as compatible with dapper as with any other ubuntu release.  It's just that I made the latest tovid deb package depend on python 2.5, since that was the lastest version used in the last few releases of ubuntu.  So it's not tovid, it's the required dependency list that I made for that package.

You could install it from source code (instructions are on the wiki), but I think I'll make a dapper deb just for you and everyone else who uses dapper, just because I'm that nice :)

I also edited the wiki page, you were right, the information there was wrong.

lukon, please download [_this deb_]("http://tovid.sourceforge.net/download/ubuntu/tovid_0.31_dapper_all.deb") and see if it works.  I made its dependency python 2.4, so it should work (as tovid is compatible with python 2.4 and newer.)

just curious: has anyone gotten tovid to work for PPC architecture comps?

---

### Post by r9mcgon on 2008-01-30
I had used tovid before, but it stopped working for some reason, so I tried to uninstall it. I couldn't figure out how do this (no make uninstall?), so I reinstalled a new version (deb package). Now it tells me it won't run because 2 versions are installed. Can anyone help me get rid of tovid/todisc completely so I can start again?

---

### Post by dannyboy79 on 2008-01-30
> **r9mcgon said:**
> I had used tovid before, but it stopped working for some reason, so I tried to uninstall it. I couldn't figure out how do this (no make uninstall?), so I reinstalled a new version (deb package). Now it tells me it won't run because 2 versions are installed. Can anyone help me get rid of tovid/todisc completely so I can start again?

according to the tovid wiki, you just cd to the location you compiled it in (where ever the Makefile is), then just run
sudo make uninstall

---

### Post by user1397 on 2008-01-30
> **r9mcgon said:**
> I had used tovid before, but it stopped working for some reason, so I tried to uninstall it. I couldn't figure out how do this (no make uninstall?), so I reinstalled a new version (deb package). Now it tells me it won't run because 2 versions are installed. Can anyone help me get rid of tovid/todisc completely so I can start again?do what dannyboy said, try to find the original tovid driectory where the makefile was (it should be in /home or some folder therein, maybe try ```
 locate tovid
```in a terminal to search for it, or you can use the graphical file search too.

also, uninstall the deb version, and don't reinstall it until you're removed both versions.

---

### Post by r9mcgon on 2008-01-31
Thanks for the fast response guys. I'm still not having any luck with this;

Edited results of 'locate tovid' (leaving out the man, share, doc, icon, python directories)
/usr/share
/usr/share/applications
/usr/local/share/applications/tovidgui.desktop
/usr/local/bin
/usr/bin
/home/rob/.tovid
/var/lib/dpkg/info/tovid.list
/var/lib/dpkg/info/tovid.conffiles

What I tried:

rob@Beag-laptop:~$ cd .tovid
[email]rob@Beag-laptop:~/.tovi[/email]d$ sudo make uninstall
[sudo] password for rob:
make: *** No rule to make target `uninstall'.  Stop.
[email]rob@Beag-laptop:~/.tovi[/email]d$ cd /usr/bin
rob@Beag-laptop:/usr/bin$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
rob@Beag-laptop:/usr/bin$ cd /usr/local/bin
rob@Beag-laptop:/usr/local/bin$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
rob@Beag-laptop:/usr/local/bin$ cd /usr/share/applications
rob@Beag-laptop:/usr/share/applications$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.

---

### Post by r9mcgon on 2008-01-31
Forgot to mention, I was able to uninstall the deb version ok.

---

### Post by user1397 on 2008-01-31
> **r9mcgon said:**
> Thanks for the fast response guys. I'm still not having any luck with this;

Edited results of 'locate tovid' (leaving out the man, share, doc, icon, python directories)
/usr/share
/usr/share/applications
/usr/local/share/applications/tovidgui.desktop
/usr/local/bin
/usr/bin
/home/rob/.tovid
/var/lib/dpkg/info/tovid.list
/var/lib/dpkg/info/tovid.conffiles

What I tried:

rob@Beag-laptop:~$ cd .tovid
[EMAIL="rob@Beag-laptop:%7E/.tovi"]rob@Beag-laptop:~/.tovi[/EMAIL]d$ sudo make uninstall
[sudo] password for rob:
make: *** No rule to make target `uninstall'.  Stop.
[EMAIL="rob@Beag-laptop:%7E/.tovi"]rob@Beag-laptop:~/.tovi[/EMAIL]d$ cd /usr/bin
rob@Beag-laptop:/usr/bin$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
rob@Beag-laptop:/usr/bin$ cd /usr/local/bin
rob@Beag-laptop:/usr/local/bin$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
rob@Beag-laptop:/usr/local/bin$ cd /usr/share/applications
rob@Beag-laptop:/usr/share/applications$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.the problem is you seem to have deleted the original source code file you downloaded form the tovid site.  remember the one you had to unpack, and then it became a folder called 'tovid-0.31' ?

that has the makefile and everything...you probably deleted it accidentally as it doesn't show up with the locate command.

anybody else know what to do...I'm stumped (I almost never install through source code.)

---

### Post by yabbadabbadont on 2008-01-31
Download the source again.  Then reinstall it from source.  This will overwrite the existing orphaned install.  Now "make uninstall".  It will clean it up for you.  Finally, install the deb.  :D

---

### Post by user1397 on 2008-01-31
> **yabbadabbadont said:**
> Download the source again.  Then reinstall it from source.  This will overwrite the existing orphaned install.  Now "make uninstall".  It will clean it up for you.  Finally, install the deb.  :Done more thing learned from you, yabbadabbadont :)

---

### Post by yabbadabbadont on 2008-01-31
> **ubuntuman001 said:**
> one more thing learned from you, yabbadabbadont :)

And this time, it isn't just bad habits....   :lol:

---

### Post by r9mcgon on 2008-02-02
Thanks guys. That worked perfectly and tovid is working again. I appreciate the help.

---

### Post by bayvista on 2008-02-23
Don't think anyone has looked at this recently. When I tried to install on Feisty following the Wiki, i get a message that there are several missing modules. I have enabled all the repositories as instructed, so where to next?

---

### Post by schmolch on 2008-02-23
I stopped reading where it said you have 3 options if you want to use a GUI.

---

### Post by user1397 on 2008-02-27
> **bayvista said:**
> Don't think anyone has looked at this recently. When I tried to install on Feisty following the Wiki, i get a message that there are several missing modules. I have enabled all the repositories as instructed, so where to next?Please give me more info; what modules were missing?  Did you install using the ubuntu instructions or from source?

---

### Post by user1397 on 2008-02-27
> **schmolch said:**
> I stopped reading where it said you have 3 options if you want to use a GUI.yep, I realize that this guide is a little confusing;  I find it pretty difficult to make a guide because so many faqs/guides/howtos/tutorials are already on the wiki, so it seems like a contradiction that I write things in here when there are already guides out there.

However, I will revise this sometime soon.

---

### Post by robertmf on 2008-04-08
At the next release - tovid-0.32 - ttovid.org intends to incorporate todisc into the tovid package.

---

### Post by user1397 on 2008-04-08
> **robertmf said:**
> At the next release - tovid-0.32 - ttovid.org intends to incorporate todisc into the tovid package.Hmm, then I'll definitely need to revise this guide...:guitar:

---

### Post by buried on 2008-04-11
Thanks, just what I was looking for.

---

### Post by lukon on 2008-04-11
Hey ubuntuman001,

I just finally returned to this forum to see that you had made an instal file for Dapper.

I used it. It seems to work.

So thank you for making it. Yes. Very nice of you.

---

### Post by user1397 on 2008-04-23
> **buried said:**
> Thanks, just what I was looking for.no problem!

> **lukon said:**
> Hey ubuntuman001,

I just finally returned to this forum to see that you had made an instal file for Dapper.

I used it. It seems to work.

So thank you for making it. Yes. Very nice of you.no problem!

---

### Post by santaslittlehelper on 2008-05-09
I can't get thumbnail menus to work.

```
todisc -pal -aspect 16:9 -widescreen -videos-are-chapters -button-style text-rect -menu-length 120 -menu-title "foo" -menu-fontsize 22 -bgaudio foo.wav -menu-audio-length 48 \
-files foo1.mpg foo2.mpg \
-titles "foo 1" "foo 2" \
-out foo
```

That creates a AUDIO_TS and VIDEO_TS folder.
Then I make it in to a iso. 
The menu will show and play fine in both vlc, mplayer. Totem wont see it at all. 
It seems like all dvd functions are missing, episodes, can't make use of chapters etc...

If I need to do the xml thing how would I do that when it has already created a dvd structure and leaves me with no main_menu.mpg

ps
works fine with makemenu and makexml just can't figure out how to do the thumbnail menus.

_edid_

[SIZE="3"]**Oh...My...God**[/SIZE]

So it's working, for some reason neither vlc, mplayer or totem can handle the menus? Uhm ok, thinking that something on my end. 
But they do work fine in a dvd player or on windows with vlc.

---

### Post by user1397 on 2008-05-11
> **santaslittlehelper said:**
> I can't get thumbnail menus to work.

```
todisc -pal -aspect 16:9 -widescreen -videos-are-chapters -button-style text-rect -menu-length 120 -menu-title "foo" -menu-fontsize 22 -bgaudio foo.wav -menu-audio-length 48 \
-files foo1.mpg foo2.mpg \
-titles "foo 1" "foo 2" \
-out foo
```That creates a AUDIO_TS and VIDEO_TS folder.
Then I make it in to a iso. 
The menu will show and play fine in both vlc, mplayer. Totem wont see it at all. 
It seems like all dvd functions are missing, episodes, can't make use of chapters etc...

If I need to do the xml thing how would I do that when it has already created a dvd structure and leaves me with no main_menu.mpg

ps
works fine with makemenu and makexml just can't figure out how to do the thumbnail menus.

_edid_

[SIZE=3]**Oh...My...God**[/SIZE]

So it's working, for some reason neither vlc, mplayer or totem can handle the menus? Uhm ok, thinking that something on my end. 
But they do work fine in a dvd player or on windows with vlc.Hmm, that is strange that it doesn't work properly under ubuntu, probably has something to do with the codecs you have.  Did you install all of the restricted codec packages?  (in add/remove programs)

---

### Post by santaslittlehelper on 2008-05-11
> **ubuntuman001 said:**
> Hmm, that is strange that it doesn't work properly under ubuntu, probably has something to do with the codecs you have.  Did you install all of the restricted codec packages?  (in add/remove programs)

I had totem with gstreamer backend changed to totem-xine with xine-lib backend as I understand it, that got the menus working in totem(well-xine).

What I was doing with vlc was "right click menu" open iso with vlc, no menu, nothing. 
If I go "Open Disc > costumize "path to iso" menu works with vlc too! If I cd to directory and do "vlc iso, menu works. 
Can't figure howcome.

So it's all good except it took me way to long to figure that it might be the players and not me screwing up with todisc. 8-[

ps
I am not on ubuntu right now so might make the difference.

---

### Post by nova on fire on 2008-05-13
Awesome How-To! I have a problem with playing the new DVD on my TV DVD player. I'm using NTSC and I burned it with the tovid GUI. Is it a problem with finalizing? Sorry but I'm a new ubuntu user trying to learn!:)
Thanks,
[INDENT][/INDENT]Nova

---

### Post by user1397 on 2008-05-15
> **nova on fire said:**
> Awesome How-To! I have a problem with playing the new DVD on my TV DVD player. I'm using NTSC and I burned it with the tovid GUI. Is it a problem with finalizing? Sorry but I'm a new ubuntu user trying to learn!:)
Thanks,NovaWell, I can't really help you much with that little info! Did you save a copy of the output of the tovid GUI? (i.e. all the text that was showing while it was running)

Perhaps you can redo it, and see if something went wrong, or if you can't see anything obvious, you can post it here.

---

### Post by nova on fire on 2008-05-16
Okay I actually tried making the disk multiple times already. I don't really know much about what the output says but some of it is pretty self explanatory to me. Could you look and see if anything is wrong? Here is the output:

The following commands will be run:
=========================================
makemenu -noask -quiet -overwrite -ntsc -dvd -align northwest -menu-title "Thanksgiving Movie" -menu-title-fontsize 32 -background "/home/nc/Pictures/NC Pics/Misc/3765220_011f29b9c6_o.png" -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "thanks.mpg" -out "/tmp/Untitled_menu_1"
------------------------
tovid -quiet -overwrite -ntsc -dvd -full -quality 8 -in "/home/nc/Videos/ThanksgivingMovie/thanks.mpg" -out "/tmp/thanks.mpg.tovid_encoded" -from-gui -noask
------------------------
makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/thanks.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -noask -quiet -overwrite -ntsc -dvd -align northwest -menu-title "Thanksgiving Movie" -menu-title-fontsize 32 -background "/home/nc/Pictures/NC Pics/Misc/3765220_011f29b9c6_o.png" -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "thanks.mpg" -out "/tmp/Untitled_menu_1"
--------------------------------
makemenu
A script to generate DVD/(S)VCD menus
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
=========================================================
Font: "Helvetica" does not appear to be either a font file or registered with ImageMagick.
A similarly-named font was not found. Sorry!
The font "Helvetica" will be used instead.
=========================================================
=========================================================
Button: "Helvetica" does not appear to be either a font file or registered with ImageMagick.
A similarly-named font was not found. Sorry!
The font "Helvetica" will be used instead.
=========================================================
Adding 1 titles to the menu:
    1: thanks.mpg
Making the DVD buttons...   
Creating the text menu...   
Creating the DVD button overlays...   
Adding the menu title...
Placing text menu in the safe area...   
Placing DVD buttons in the safe area...   
Working on the background...   
Centering the safe area over the background...   
Positioning the DVD button overlays on the background...   
Creating 4-second silent ac3 audio...   
Converting menu image to video. This may take a while...   
Multiplexing video and audio streams...   
Adding the DVD buttons to menu...   
Cleaning up...   
=========================================================
Done!
Running command: tovid -quiet -overwrite -ntsc -dvd -full -quality 8 -in "/home/nc/Videos/ThanksgivingMovie/thanks.mpg" -out "/tmp/thanks.mpg.tovid_encoded" -from-gui -noask
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Using config file /home/nc/.tovid/tovid.config, containing the following options:
(none)
Converting /home/nc/Videos/ThanksgivingMovie/thanks.mpg to NTSC DVD format
Encoding quality is 8 of 10 (use -quality to change)
Saving to /tmp/thanks.mpg.tovid_encoded.mpg
Storing log and temporary files in /home/nc/thanks.mpg.tovid_encoded.0
Run 'tail -f "/home/nc/thanks.mpg.tovid_encoded.0/tovid.log"' in another terminal to monitor the log

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 1029 MB of disk space.
You currently have 7802 MB available in this directory.
Analysis of file /home/nc/Videos/ThanksgivingMovie/thanks.mpg:
  720 x 480 pixels, 29.970 fps
  Duration (best guess): 00:24:31 (HH:MM:SS)
  MPEG2 video with ac3 audio

=========================================================

Audio and video streams appear to already be compliant with the
selected output format. If you want to force encoding (for instance,
to change the bitrate or take advantage of denoising), run tovid
again with the '-force' option. A symbolic link has been created
in place of the output file:
    /tmp/thanks.mpg.tovid_encoded.mpg --> /home/nc/Videos/ThanksgivingMovie/thanks.mpg

=========================================================

Done!
Cleaning up...
Removing temporary files...
removed `/home/nc/thanks.mpg.tovid_encoded.0/tovid.log'
removed directory: `/home/nc/thanks.mpg.tovid_encoded.0'
Running command: makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/thanks.mpg.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
--------------------------------
makexml
A script to generate XML for authoring a VCD, SVCD, or DVD.
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Adding a titleset-level menu using file: /tmp/Untitled_menu_1.mpg
Adding title: /tmp/thanks.mpg.tovid_encoded.mpg as title number 1 of titleset 1
    Calculating the duration of the video with:
        idvid -terse "/tmp/thanks.mpg.tovid_encoded.mpg"
    This may take a few minutes, so please be patient...
    The duration of the video is 00:24:31
Closing titleset 1 with 1 title(s).
Done. The resulting XML was written to /tmp/Untitled_disc.xml.

Also, this is only what it says for the encoding process. Not the burning. Does this help? Thanks, Nova

---

### Post by user1397 on 2008-06-07
> **nova on fire said:**
> Okay I actually tried making the disk multiple times already. I don't really know much about what the output says but some of it is pretty self explanatory to me. Could you look and see if anything is wrong? Here is the output:

Also, this is only what it says for the encoding process. Not the burning. Does this help? Thanks, NovaHmm It all seems ok.  Can you provide the output for the burning process?  Or maybe try in another dvd player (does it work on your computer dvd player?)

---

### Post by reiki on 2008-06-09
> **ubuntuman001 said:**
> Hmm It all seems ok.  Can you provide the output for the burning process?  Or maybe try in another dvd player (does it work on your computer dvd player?)

Doesn't matter if it plays in VLC on the computer that created it. I'm not sure what's broken in Hardy, but I had the same problem. Every DVD... no matter what I used to AUTHOR them... resulted in "unsupported" on any other player in the house. I used the exact same tools to burn it when booted to Gutsy and it came out beautifully.

HOWEVER... I can make a complete DVD copy using GnomeBaker in Hardy and create an iso... and then burn that iso and it plays on all machines in my house. *SOMETHING* is borked in Hardy and it has to do SPECIFICALLY with the burning. 

In Hardy I used Tovid and Todisc to do all preparation. Running makedvd -burn resulted in a coaster. Rebooted to Gutsy, ran makedvd -burn and it worked flawlessly.

---

### Post by user1397 on 2008-06-09
> **reiki said:**
> Doesn't matter if it plays in VLC on the computer that created it. I'm not sure what's broken in Hardy, but I had the same problem. Every DVD... no matter what I used to AUTHOR them... resulted in "unsupported" on any other player in the house. I used the exact same tools to burn it when booted to Gutsy and it came out beautifully.

HOWEVER... I can make a complete DVD copy using GnomeBaker in Hardy and create an iso... and then burn that iso and it plays on all machines in my house. *SOMETHING* is borked in Hardy and it has to do SPECIFICALLY with the burning. 

In Hardy I used Tovid and Todisc to do all preparation. Running makedvd -burn resulted in a coaster. Rebooted to Gutsy, ran makedvd -burn and it worked flawlessly.that's weird...I'm thinking it could be the new python version installed in hardy; I know for sure some people had problems installing a python2.5-dependent version of tovid on a python2.4 ubuntu install.  But hardy seems to have python 2.5.2, so it really shouldn't be a problem :confused:

I don't have an answer for ya man, I'll have to look more into it.

---

### Post by reiki on 2008-06-09
> **ubuntuman001 said:**
> that's weird...I'm thinkinh it could be the new python version installed in hardy; I know for sure some people had problems installing a python2.5-dependent version of tovid on a python2.4 ubuntu install.  But hardy seems to have python 2.5.2, so it really shouldn't be a problem :confused:

I don't have an answer for ya man, I'll have to look more into it.

And I, for one, appreciate anything you can do to figure this out. I might just be lucky that I kept my Gutsy installation around. I was going to wipe it because Hardy was doing everything fine. Until a friend asked me to author some DVDs for her from bits and pieces of other DVDs and video tape. I made about 5 or 6 coasters trying various programs to create the structure and burn a DVD with a menu. 

For some reason after I had created the structure for about the billionth time I thought..."I wonder if Gutsy can do this"... reboot... run makedvd -burn ... and voila!  done deal. So all of the preparation done by tovid and todisk in Hardy work fine. Because I USED the structure created in Hardy using those tools. It was only when it came time to put that all onto a DVD that the process failed to produce a proper DVD. I could play it in VLC on the machine that created it, but no other DVD player could read it properly. 

Now I'm not smart enough to figure out WHY it is that I can burn an iso that GnomeBaker made.... in Hardy... and it works fine. But it DOES have me wondering what's different about burning the structure created by todisk as opposed to an iso. 

Does GnomeBaker not have to use makedvd because I'm burning an iso instead of having to interpret the file structure and burn that?  

Regardless.... thank you for looking into this. At age 56 there are some things I've learned to leave to others to resolve. :)

---

### Post by user1397 on 2008-06-26
> **reiki said:**
> And I, for one, appreciate anything you can do to figure this out. I might just be lucky that I kept my Gutsy installation around. I was going to wipe it because Hardy was doing everything fine. Until a friend asked me to author some DVDs for her from bits and pieces of other DVDs and video tape. I made about 5 or 6 coasters trying various programs to create the structure and burn a DVD with a menu. 

For some reason after I had created the structure for about the billionth time I thought..."I wonder if Gutsy can do this"... reboot... run makedvd -burn ... and voila!  done deal. So all of the preparation done by tovid and todisk in Hardy work fine. Because I USED the structure created in Hardy using those tools. It was only when it came time to put that all onto a DVD that the process failed to produce a proper DVD. I could play it in VLC on the machine that created it, but no other DVD player could read it properly. 

Now I'm not smart enough to figure out WHY it is that I can burn an iso that GnomeBaker made.... in Hardy... and it works fine. But it DOES have me wondering what's different about burning the structure created by todisk as opposed to an iso. 

Does GnomeBaker not have to use makedvd because I'm burning an iso instead of having to interpret the file structure and burn that?  

Regardless.... thank you for looking into this. At age 56 there are some things I've learned to leave to others to resolve. :)Well to tell you the truth, I'm quite stumped on this one...I really have no idea.  If I were you and gnomebaker works fine, then I would just use that for now, and if you're really interested in the reason why, I would ask in the tovid forums or IRC channel.

---

### Post by user1397 on 2008-06-26
In other news, tovid is officially in the ubuntu repositories now! (hardy only)

all you need do now is a simple ```
sudo apt-get install tovid
```

---

### Post by gaspard.leon on 2008-07-16
Fixing missing fonts if you follow instructions at the tovid site and it still doesn't show any fonts:

In the tovid scripts, replace [FONT="Courier New"]convert -list type[/FONT] with [FONT="Courier New"]convert -list font[/FONT]

if your version of ImageMagick has updated that feature as mine had...
(run those 2 commands in a shell to test)

i found that the following files had to change:
```
/usr/share/tovid/makemenu
/usr/share/python-support/tovid/libtovid/gui/configs.py
```

And another bug I found was the menu titles appeared right next to the menu items (no space)... this was a bug referenced on this page: [http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=10367](http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=10367)

I used the -flip -flip work-around:
In [FONT="Courier New"]/usr/share/tovid/makemenu[/FONT]
change this line:
```
    convert "$MENU_TITLE_TEXT" -background none -splice 0x$TILE_HEIGHT "$MENU_TITLE_TEXT"
```
to this line:
```
    convert "$MENU_TITLE_TEXT" -flip -background none -splice 0x$TILE_HEIGHT -flip "$MENU_TITLE_TEXT"
```

It worked!! :guitar:

I have fonts in the list in the gui and working in makemenu and I have a nice space in-between the title and the items.

---

### Post by EnigMattic on 2008-07-21
Or you could just use [ManDVD]("http://www.getdeb.net/app/ManDVD") :)

---

### Post by SchindlerShadow on 2008-08-11
ok help needed here XD i try to encode it and i get an error!

Error(s) occurred during encoding. If you want to
help improve this software, please file a bug report
containing a copy of the output log. Unfortunately,
this also means you won't be able to continue to
burning your disc. Sorry for the inconvenience!

=========================================
makemenu -noask -quiet -overwrite -ntsc -dvd -align northwest -menu-title "Rush Hr. 2" -menu-title-fontsize 32 -background "/home/youssef/Pictures/eternalubuntu.png" -audio "/home/youssef/Music/3 Days Grace - Home.mp3" -length 450 -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "Rush Hour 2.mp4" -out "/tmp/rush_hr_2"
------------------------
tovid -quiet -overwrite -ntsc -dvd -full -quality 8 -in "/home/youssef/my ex hdd/Downloads/Rush Hour 2.mp4" -out "/tmp/Rush Hour 2.mp4.tovid_encoded" -from-gui -noask
------------------------
makexml -quiet -overwrite -dvd -menu "/tmp/rush_hr_2.mpg" "/tmp/Rush Hour 2.mp4.tovid_encoded.mpg" -out "/tmp/Rush_hr_2"
------------------------
Running command: makemenu -noask -quiet -overwrite -ntsc -dvd -align northwest -menu-title "Rush Hr. 2" -menu-title-fontsize 32 -background "/home/youssef/Pictures/eternalubuntu.png" -audio "/home/youssef/Music/3 Days Grace - Home.mp3" -length 450 -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "Rush Hour 2.mp4" -out "/tmp/rush_hr_2"
--------------------------------
makemenu
A script to generate DVD/(S)VCD menus
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
=========================================================
  composite   MISSING!
=========================================================
  convert     MISSING!

You are missing dependencies required for making menus! Please install the 
above MISSING dependencies and try again. See 
tovid.wikia.com/wiki/Tovid_dependencies or tovid.org for help.
=========================================================
Running command: tovid -quiet -overwrite -ntsc -dvd -full -quality 8 -in "/home/youssef/my ex hdd/Downloads/Rush Hour 2.mp4" -out "/tmp/Rush Hour 2.mp4.tovid_encoded" -from-gui -noask
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Using config file /home/youssef/.tovid/tovid.config, containing the following options:
(none)
Converting /home/youssef/my ex hdd/Downloads/Rush Hour 2.mp4 to NTSC DVD format
Encoding quality is 8 of 10 (use -quality to change)
Saving to /tmp/Rush Hour 2.mp4.tovid_encoded.mpg
Storing log and temporary files in /home/youssef/Rush Hour 2.mp4.tovid_encoded.2
Run 'tail -f "/home/youssef/Rush Hour 2.mp4.tovid_encoded.2/tovid.log"' in another terminal to monitor the log

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 3782 MB of disk space.
You currently have 12839 MB available in this directory.
Analysis of file /home/youssef/my ex hdd/Downloads/Rush Hour 2.mp4:
  480 x 224 pixels, 29.970 fps
  Duration (best guess): 01:30:03 (HH:MM:SS)
  avc1 video with faad audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  7200 kbits/sec video, 224 kbits/sec audio

=========================================================

Using explicitly provided aspect ratio 4:3
Overriding auto-detected aspect ratio 133:100
No letterboxing necessary
Input is already 29.970 fps. Framerate will not be altered.
Scaling picture to 720 x 480

=========================================================

Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i /home/youssef/my ex hdd/Downloads/Rush Hour 2.mp4 -vn -ab 224k -ar 48000 -ac 2 -acodec ac3 -y /home/youssef/Rush Hour 2.mp4.tovid_encoded.2/audio.ac3

Waiting 30 seconds for output file "audio.ac3" to appear...
Processing started. Please wait...                                               


Encode stopped, killing all sub processes
Keeping temporary files used during encoding in /home/youssef/Rush Hour 2.mp4.tovid_encoded.2
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
tovid encountered an error during encoding:
    There was a problem with encoding the audio to ac3 format.
Check the contents of /home/youssef/Rush Hour 2.mp4.tovid_encoded.2/tovid.log to see what went wrong.
 
See the tovid help page for what to do next:
  [http://tovid.wikia.com/wiki/Help:Contents](http://tovid.wikia.com/wiki/Help:Contents)
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Running command: makexml -quiet -overwrite -dvd -menu "/tmp/rush_hr_2.mpg" "/tmp/Rush Hour 2.mp4.tovid_encoded.mpg" -out "/tmp/Rush_hr_2"
--------------------------------
makexml
A script to generate XML for authoring a VCD, SVCD, or DVD.
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
The file /tmp/rush_hr_2.mpg was not found.  Exiting.




and the vid is an mp4! :confused::confused:

---

### Post by yabbadabbadont on 2008-08-11
> **SchindlerShadow said:**
> ok help needed here XD i try to encode it and i get an error!

=========================================================
  composite   MISSING!
=========================================================
  convert     MISSING!

You are missing dependencies required for making menus! Please install the 
above MISSING dependencies and try again. See 
tovid.wikia.com/wiki/Tovid_dependencies or tovid.org for help.


Make sure that you have imagemagick installed.

---

### Post by robertmf on 2008-09-19
> **squidward_tentacles said:**
> PS I did make sure all the dependancies were installed before begining, and it DOES seem to work w/out the GUI, aka if I enter just "tovid", however as a recent convert from windows, I am a bit bewildered as how to run programs entirely from the command prompt, a GUI interface is highly desired. Well thanks in advance for your help:)

[COLOR="DarkRed"]Try using "tovid-interactive [filename]" from the cli.[/COLOR]

---

### Post by wetinwales on 2008-09-19
Hi All
Using Ubuntu 8.04. Installed (I hope) ALL the dependencies listed in the tovid WIKI. Re-installed tovid.
It will not Encode (from a .vob file)

The log gives:-

The following commands will be run:
=========================================
makemenu -noask -quiet -overwrite -pal -dvd -align northwest -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "VTS 01 1.VOB" -out "/tmp/Untitled_menu_1"
------------------------
tovid -quiet -overwrite -pal -dvd -full -quality 8 -in "/media/disk/Fallout Decrypt/VTS_01_1.VOB" -out "/tmp/VTS 01 1.VOB.tovid_encoded" -from-gui -noask
------------------------
makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/VTS 01 1.VOB.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -noask -quiet -overwrite -pal -dvd -align northwest -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "VTS 01 1.VOB" -out "/tmp/Untitled_menu_1"
=========================================================
  mencoder    MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING 
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or 
tovid.org for help.
=========================================================
Running command: tovid -quiet -overwrite -pal -dvd -full -quality 8 -in "/media/disk/Fallout Decrypt/VTS_01_1.VOB" -out "/tmp/VTS 01 1.VOB.tovid_encoded" -from-gui -noask
=========================================================
  mencoder    MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING 
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or 
tovid.org for help.
=========================================================
Running command: makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/VTS 01 1.VOB.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
=========================================================
  mencoder    MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING 
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or 
tovid.org for help.
=========================================================
 Can anyone shed light on it for me ???
Daf

---

### Post by yabbadabbadont on 2008-09-19
Even though installing tovid through synaptic or apt should have pulled it in automagically, make sure that the mencoder package is actually installed.

If you open a terminal window and type mencoder and hit enter.  If it is installed, and in your PATH, then it should spit out it's version information and an error message about "no file given".

Edit: I saw your message on the tovid mailing list.  I'm sure that you'll get the same answer there as I have just given you.  :D

---

### Post by wetinwales on 2008-09-20
Hi Thanks for that. In terminal typing mencoder gives me:-

*******@*******:~$ mencoder
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(TM) XP 2100+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)

Don't quite understand that lot yet..!

Thanks
Daf

---

### Post by yabbadabbadont on 2008-09-20
I saw your messages on the tovid mailing list, but I wasn't sure about what was going on there.  Have you gotten past the mencoder error and are now getting a dvdauthor error?

---

### Post by RavUn on 2008-09-21
Is tovid better than ManDVD?  I tried using ManDVD on my other computer and something always seemed to screw up... the menu items wouldn't highlight so I could never tell which video I'm selecting and sometimes only half of the videos would actually play.  

Can you burn multiple videos on a dvd with Tovid?

---

### Post by Rocko262c on 2008-09-30
Did you ever find a solution to your problem?
Thanks,
Rocko

---

### Post by jake3988 on 2008-10-03
> **RavUn said:**
> Is tovid better than ManDVD?  I tried using ManDVD on my other computer and something always seemed to screw up... the menu items wouldn't highlight so I could never tell which video I'm selecting and sometimes only half of the videos would actually play.  

Can you burn multiple videos on a dvd with Tovid?


Yes.  Simply create a menu and create an entry for each movie.  Then click on the movie you want to play. 

Remember that converting the movies to mpg will DRAMATICALLY increase the size of the movie to that of a real dvd.  If they're motion pictures unless short (~100 minutes or less each) you probably will not be able to fit two on one dvd. But you're certainly welcome to try.

---

### Post by sofasurfer on 2009-01-25
I tried the tovid gui. I performed 'layout' and 'encode'. But when I did 'burn' I got the message that it could not open /dev/dvdrw. So I tried getting it to use /dev/dvd3, /dvdrw3, /media/cdrom and /media/cdrom0. Kept getting the same message. 

What should I do?

---

### Post by labinnsw on 2009-02-25
Here is something I have found at [http://ubuntuforums.org/showthread.php?p=6795022#post6795022]("http://ubuntuforums.org/showthread.php?p=6795022#post6795022").

How to install tovid DVD creator on Ubuntu 8.04

1.Install the following from Synaptic
tovid
tovidgui
tcl8.4 
tcl8.4-dev 
tcl8.4-doc 
mencoder 
dvdauthor 
qdvdauthor

Optional:
You can also install the following if you wish to have an alternate GUI.
todiscgui

2.Run the following commands in a terminal
cd /usr/share/tovid 
sudo ln makemenu makexml /usr/bin 
which makemenu 
which makexml

---

### Post by dannyboy79 on 2009-02-25
> **jake3988 said:**
> Yes.  Simply create a menu and create an entry for each movie.  Then click on the movie you want to play. 

Remember that converting the movies to mpg will DRAMATICALLY increase the size of the movie to that of a real dvd.  If they're motion pictures unless short (~100 minutes or less each) you probably will not be able to fit two on one dvd. But you're certainly welcome to try.
I regularly will convert 700mb avi movies downloaded from internet using tovidgui, using quality 7 and can fit 2 movies on 1 dvd disc. the source movies normally have an aspect ratio of 16:9 or sometimes even worse, where the width is more than twice the height. ANyway, that's just my experience. I love tovidgui though. Oh, I am still using Feisty if that matters to anyone.

---

### Post by dannyboy79 on 2009-02-25
> **sofasurfer said:**
> I tried the tovid gui. I performed 'layout' and 'encode'. But when I did 'burn' I got the message that it could not open /dev/dvdrw. So I tried getting it to use /dev/dvd3, /dvdrw3, /media/cdrom and /media/cdrom0. Kept getting the same message. 

What should I do?
this is listed as a common problem on the tovid.org website. here is the solution:
[http://tovid.wikia.com/wiki/Common_tovid_problems#unable_to_open64.28.22.2Fdev.2Fdvd.22.2CO_RDONLY.29:_Permission_denied](http://tovid.wikia.com/wiki/Common_tovid_problems#unable_to_open64.28.22.2Fdev.2Fdvd.22.2CO_RDONLY.29:_Permission_denied)
this solution is only for after the .xml file has been created by tovid and it's stored in the /tmp directory or whatever directory you chose to have temp files stored. the way to permanently solve this issue to make sure that you as a user can write to /dev/dvd0 or whatever your dvd writer is.
what does this command return for ya?
```
ls -la | grep dvd
```

---

### Post by trksh22 on 2009-02-26
How does this compare to using Handbrake to rip two DVD's and using DeVeDe to combine them into one? It's a lengthy process.... but it works. I just can't shake the feeling that there might be something easier out there.... like this Tovoid. *installing it now*

---

### Post by user1397 on 2009-03-01
> **trksh22 said:**
> How does this compare to using Handbrake to rip two DVD's and using DeVeDe to combine them into one? It's a lengthy process.... but it works. I just can't shake the feeling that there might be something easier out there.... like this Tovoid. *installing it now*
well yes, ripping DVDs and using DeVeDe can do the job for that basic process, but tovid has a plethora of options to customize your project in whatever way you want it, *a lot* more than DeVeDe does

---

### Post by user1397 on 2010-02-02
I've edited the guide yet again (after not doing so for a long time) this time making it far simpler, less wordy, and cleaner in general.  Enjoy ;)

---

### Post by stoppage on 2010-05-11
> **gaspard.leon said:**
> Fixing missing fonts if you follow instructions at the tovid site and it still doesn't show any fonts:

In the tovid scripts, replace [FONT="Courier New"]convert -list type[/FONT] with [FONT="Courier New"]convert -list font[/FONT]

if your version of ImageMagick has updated that feature as mine had...
(run those 2 commands in a shell to test)

i found that the following files had to change:
```
/usr/share/tovid/makemenu
/usr/share/python-support/tovid/libtovid/gui/configs.py
```

And another bug I found was the menu titles appeared right next to the menu items (no space)... this was a bug referenced on this page: [http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=10367](http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=10367)

I used the -flip -flip work-around:
In [FONT="Courier New"]/usr/share/tovid/makemenu[/FONT]
change this line:
```
    convert "$MENU_TITLE_TEXT" -background none -splice 0x$TILE_HEIGHT "$MENU_TITLE_TEXT"
```
to this line:
```
    convert "$MENU_TITLE_TEXT" -flip -background none -splice 0x$TILE_HEIGHT -flip "$MENU_TITLE_TEXT"
```

It worked!! :guitar:

I have fonts in the list in the gui and working in makemenu and I have a nice space in-between the title and the items.

I spent sooo long looking for a solution to my fonts being "stuck" at Defect....but are there still only four choices for buttons? 
Much obliged for this

---

### Post by rey1321 on 2010-06-04
Why you guys have to go thru all this
headache using command lines?

There's a nice application called
DeVeDe that make everything for you.

you just add the video files and relax!
it will convert them to dvd files, and playable 
in any commercial dvd player. period:guitar:

---

### Post by user1397 on 2010-06-05
> **rey1321 said:**
> Why you guys have to go thru all this
headache using command lines?

There's a nice application called
DeVeDe that make everything for you.

you just add the video files and relax!
it will convert them to dvd files, and playable 
in any commercial dvd player. period:guitar:
yea you're probably like the 1000th person to post about how awesome devede is in this thread.

and for the 1000th time, I'm gonna say that they are two different programs with different capabilities.  tovid is much more customizable, as you can add a customized menu complete with pictures and sounds,can even add subtitles and a whole range of things.

and it is not just command-line, there is a GUI.

---

### Post by rey1321 on 2010-06-06
ManDVD
does everything you just said

---

### Post by ron999 on 2010-06-06
> **rey1321 said:**
> ManDVD
does everything you just said

So maybe you should start your own thread:-
**HOWTO: Make DVD Videos Using ManDVD**

---

### Post by travellinghunter on 2010-06-07
as of 2010 the tovid and tovidgui can be installed through the ubuntu package manager and work very easily. 
I found an article in a book called  [I]"Ubuntu Hacks: Tips & Tools for Exploring, Using, and Tuning Linux" which shows how to use this very good program and other things. Similar to the original posters directions here. 
Btw the original poster motivated me to look more in to tovid and hence the discovery of this book about this program. 
Good luck.
[/I]

---

### Post by Sempfinger on 2010-10-01
I have the following problem:

I am using the gui v. 0.31. After choosing the menu for the dvd - basic stuff with image and sound - I click on "Start Encoding". Now the script runs and sets things up. 

But it gets stuck at: 
```
Probing video for information. This may take several minutes...
```

This runs for 45 minutes now, which seems odd. I checked the running processes and it appears tovid started the following mplayer process:
```
mplayer -vo null -ao null -frames 90 -channels 6 -identify
```

which is running at 2% CPU usage and is running and running...

tovid runs as:
```
bash /usr/bin/tovid -quiet -overwrite -pal -dvd -full -quality 8 -in <inputfile>
```

and
```

bash /usr/bin/idvid -terse <inputfile>
```

<inputfile> is of course the path to my mpeg video which I converted to mpeg via ffmpeg...

Any ideas / hints would be greatly appreciated

cheers

edit: Ok, after some testing it seems that mplayer does not work as expected. As I understood it, tovid probes for Information and tells mplayer to play the file, but only the first 90 frames and then to stop. When I try the above command that tovid uses, i.e.:
```
mplayer -vo null -ao null -frames 90 -channels 6 -identify -aid 128 <inputfile>
```

mplayer does not stop! It continues to play the first few frames in a loop... tovid is presumably waiting for mplayer to return which never happens...

Any Ideas on that one?

---

### Post by Sempfinger on 2010-10-01
Just for reference, there was the option 
```
loop=0
```

in the .mplayer file, which caused the looping

In my opinion it would be better for tovid to use a call to mplayer which ignores the users customizations in .mplayer to make the probing more robust...

---

### Post by yabbadabbadont on 2010-10-01
I would try using the current release, 0.33.  (or better yet, the svn version)  You should probably also read through the tovid-users google group.  [http://groups.google.com/group/tovid-users/](http://groups.google.com/group/tovid-users/)

Tovid had pretty much died for a long while, but it seems to be showing signs of life recently.  [http://groups.google.com/group/tovid-svn](http://groups.google.com/group/tovid-svn)

---

### Post by mrady on 2011-10-28
> **ubuntuman001 said:**
> So here are the steps to take if you want to have a dvd movie, that's playable in a home dvd player, and created from a video file on your computer.

Tovid should work on any architecture (x86, x86_64, PPC, etc.) and any desktop environment (Gnome, KDE, Xfce, etc.). This guide assumes that you already have a video file saved on your computer, that you own a dvd burner, and that you have a blank dvd.

Tovid will accept many different types of video formats for your initial video.  In fact, whatever formats the programs mplayer and ffmpeg support, tovid supports.  There are very few formats it doesn't support, but you'll probably have one of the more common ones, so there's nothing to worry.

Also, please know that for tovid to work optimally, it's *recommended* to have at least 20GB of free space, so that it can author and encode the video smoothly.

- - - - - 

**Installation**

To install tovid, just search for it in the Software Center, or else type this in a terminal:```
sudo apt-get install tovid
```If that doesn't work, [install from source]("http://tovid.wikia.com/wiki/Installing_tovid").

If you don't see any tovid menu entries under Applications > Sound & Video, refresh the gnome panels: ```
killall gnome-panel
```- - - - - 

**Using the GUI:**

Go to Applications > Sound & Video > tovid.  If for some reason it doesn't start up correctly, run the command in a terminal to diagnose the cause of the issue: ```
todiscgui
```**_OR_**

**Using the CLI:**

You have an avi file named 'foo' in your home directory, and you live in the Eastern Hemisphere (not Japan, they use NTSC), and you have a widescreen TV.  You would simply type in a terminal: 
```
tovid -wide -pal -in foo.avi -out foo_encoded
``` The -wide command tells tovid to make it widescreen, the -pal command tells tovid to make it PAL format, the -in file is the original, and the -out is the final product.  Simple huh?

Consider the more complicated scenario: You have 3 videos, File1.mpg, File2.mpg, and File3.mpg.  You want the menu to have titles Episode 1, Episode 2, and Episode 3.  You want the dvd to be called Season_One.  Your command would be:
```
todisc -files File1.mpg File2.mpg File3.mpg \
 -titles "Episode 1" "Episode 2" "Episode 3" \
-out Season_One
```- - - - - 

Once it is finished encoding, you could try to burn the video to a dvd using the burn tab in the GUI, but sometimes it doesn't work, so just minimize tovid (you dont want to close it, just in case if the encoding output is needed for support.)  Then open a terminal and paste (this is just an example; replace the italic words accordingly):   
```
makexml -menu *Menu*.mpg \*foo1*.mpg *foo2*.mpg *foo3*.mpg \
 -out *MyDisc*
```That created an xml file, which in this case would be called: *MyDisc*.xml
Now, you have to burn to a dvd, using this command (again, replacing the italic word with your actual file name): ```
makedvd -burn *MyDisc*.xml
```  When it's finished, you'll have a dvd that's playable on your computer and on all (or most) dvd players!

If you wish to make more dvd's using this guide, you'll have to delete the dvd folder that was created, and move any completed files to your completed folder, or delete it if you wish.  These should be moved from the encoding directory so that tovid can encode anew with a fresh place, no left-over trash, so that it doesn't run into space problems or errors.

Official tovid website (installation/info/guides): _**[here]("http://tovid.wikia.com/wiki/Main_Page")**_.

Official tovid forums (bug reports and general info/help): **_[here]("http://www.createphpbb.com/tovid/")_**.

Disclaimer:  I'm not responsible for anything related to this howto. Be aware of the laws in your country.


good one will give it a go

---

### Post by George Heine on 2012-04-09
Does anyone still read this thread?  My question is below.  I tried to post to the tovid forums and got a mysterious message about "Registered member must have at least 5 postings to post any URL/Website" 


Am using tovid 0.34 on Ubuntu 11.04.  The tovid man page contains the following

```
Command:chapters
       tovid  chapters will start a GUI using mplayer to set chapter points in
       a video.  Its only (mandatory) option is the path to a video file.
```However, entering "tovid chapters" at the command line gives me the following message:

```
Traceback (most recent call last):
  File "/usr/local/bin/tovid", line 208, in <module>
    tovid = Frontend(sys.argv)
  File "/usr/local/bin/tovid", line 74, in __init__
    self.run_command(args)
  File "/usr/local/bin/tovid", line 147, in run_command
    proc = subprocess.Popen([script] + ini_args + args)
  File "/usr/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1213, in _execute_child
    raise child_exception
OSError: [Errno 13] Permission denied
```Any ideas?  Note that the tovid gui -does- run on my system.  

Also, any comments on the usefulness of this routine?  I have successfully used "mplayer -ss" to find logical chapter breaks in the video file , then manually edit the DVDauthor xml file to create the chapters.  But it is a lot of work.  Is "tovid chapters" any easier, or just the same process

---

