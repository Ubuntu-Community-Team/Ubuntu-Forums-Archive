---
title: "HOWTO:  Install Rubyripper on Ubuntu"
date: 2008-05-19
forum: Tutorials
---

### Post by ghindo on 2008-05-19
[center]**[SIZE="5"][COLOR="Red"]HOWTO:  Install Rubyripper on Ubuntu[/COLOR][/SIZE]**[/center]

[SIZE="1"]*Note:  These instructions are aimed at Ubuntu 10.04 and above.  Results on other Ubuntu releases may vary.*[/SIZE]

**[SIZE="3"]What is Rubyripper?[/SIZE]**
From the _[HydrogenAudio wiki](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)_:
> Rubyripper is a digital audio extraction algorithm that uses cdparanoia in a sophisticated way to make sure that a CD rip is done successfully and accurately.

**[SIZE="3"]How is Rubyripper different from other CD rippers?[/SIZE]**
Rubyripper differs from programs like K3b and Sound Juicer because it is **much** more thorough.  Rubyripper rips each audio track at least twice, then compares each rip for differences and attempts to make the most accurate compilation of rips it possibly can.  The result?  Higher quality, *accurate* CD rips.

**[SIZE="3"]Installation[/SIZE]**
Unfortunately, Rubyripper isn't yet available in the official Ubuntu repositories.  Fortunately, there's a personal package archive (PPA) available which makes installation easy!  No more compiling from source! :)

[LIST=1]
[*]First, open up the terminal.  You can do this by looking in the Applications menu, under Accessories.
[*]Next, copy the following text into the terminal and hit enter:```
sudo add-apt-repository ppa:aheck/ppa
```This should prompt you for your password.
[*]Then, run the following command:```
sudo apt-get update
```
[*]Finally, enter```
sudo apt-get install rubyripper-gtk
```
[/LIST]

And that's it!  Rubyripper should now be in the applications Applications menu under Sound & Video. :)

**[SIZE="3"]Uninstallation[/SIZE]**
If you find you are unhappy with Rubyripper, for whatever reason, uninstalling is a snap.
[LIST=1]
[*]Simply open up the Ubuntu Software Center under the Applications menu.
[*]Search for "rubyripper" and press the "remove" button next to the search results.  Rubyripper will then uninstall.
[/LIST]

**[SIZE="3"]Further Resources[/SIZE]**
For more information, check out the _[Rubyripper home page](http://code.google.com/p/rubyripper/)_ or _[HydrogenAudio wiki](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)_.

---

### Post by ghindo on 2008-05-19
Please feel free to leave comments and criticism so I can improve this tutorial :)

---

### Post by SenatorKane on 2008-05-22
Hello,
I followed the howto step by step and everything works fine until the "make install"

The ouput basicly consists of bunch of line like the one below
> 
/usr/lib/ruby/1.8/gettext/parser/ruby.rb:36: command not found: msgmerge ./locale/po/rr_cli.pot tmp.pot
Failed to merge with ./locale/po/rr_cli.pot - skipping!
Please check new .pot in tmp.pot~
the last ones look like this
> 
install -D rr_lib.rb /usr/lib/site_ruby/1.8/rr_lib.rb
install: Entfernen von „/usr/lib/site_ruby/1.8/rr_lib.rb“ nicht möglich: Permission denied
make: *** [install] Fehler 1


strangely enough starting ruby from applications -> sound&video works, but the buttons are all grey and don't react. Starting ruby from console doesn't work at all.
I'd be gratful for any help you can offer, but please keep it simple ;-)

regards

alex

---

### Post by ghindo on 2008-05-22
Did you run "make install" with sudo?  The last lines make me think that you don't have sudo permissions...

If you *did* run```
sudo make install
```then I would recommend uninstalling Rubyripper and starting over.

---

### Post by pulsewidth on 2008-05-27
This is the second time I've seen someone do a post about Rubyripper in either this forum or a blog, so I thought I'd pass along my experience with this program as well. I've been using it since version 0.4.2 and quite like it, and I seem to recall version 0.5.0 working in 7.10. 

I get this when I try to run Rubyripper:
```
[ernst::interzone::~/build/rubyripper-0.5.0]:-./rubyripper_gtk2.rb 
/home/ernst/build/rubyripper-0.5.0/rr_lib.rb:413:in `open': Not a directory - /home/ernst/.cddb/d90a4011 (Errno::ENOTDIR)
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:413:in `foreach'
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:413:in `searchLocal'
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:411:in `foreach'
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:411:in `searchLocal'
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:396:in `get_disc_info'
    from /home/ernst/build/rubyripper-0.5.0/rr_lib.rb:378:in `freedb'
    from ./rubyripper_gtk2.rb:176:in `scan_drive'
    from ./rubyripper_gtk2.rb:165:in `initialize'
    from ./rubyripper_gtk2.rb:165:in `new'
    from ./rubyripper_gtk2.rb:165:in `scan_drive'
    from ./rubyripper_gtk2.rb:67:in `initialize'
    from ./rubyripper_gtk2.rb:1082:in `new'
    from ./rubyripper_gtk2.rb:1082
```and Rubyripper crashes. There was a patch available at the Rubyripper Google Code site, but it esseitially broke the Freedb search, necessitating manual title entry.

Version 0.4.4 of Rubyripper works just fine in 8.04. Hopefully the developer, or someone who knows Ruby, sorts this out.

---

### Post by ghindo on 2008-05-27
Weird.  I wish I could help you out, but I can't decipher any of that.  :(  At least 0.4.4 works.  Hopefully the next version will work for you.

---

### Post by ghindo on 2008-07-11
Minor update:  Changed from Rubyripper version 0.5.0 to 0.5.1.

Fixes included in Rubyripper 0.5.1:> ---------0.5.1 RELEASE------

* important fix that prevents creating corrupted wav files
* move over to one single language file
* make ruby-gettext optionally
* single file ripping supported
* cuesheet support
* some small fixes all over the placeCuesheets are finally supported :)  Have fun, kids!

---

### Post by ghindo on 2008-07-18
Minor update: Changed from Rubyripper version 0.5.1 to 0.5.2.

Fixes included in Rubyripper 0.5.2:> ---------0.5.2 RELEASE------
* add a check for permission while reading the cdrom drive
* fix the configure script to obey the not needing ruby-gettext dependency
* fix the terrible state of the command-line client

---

### Post by Mediapirate on 2008-07-25
Brilliant tutorial dude.

I don't think I would have managed to get it installed without your help.

I used it before but can't remember where I got the details to install it from.

Keep updating it also and i'll keep it bookmarked.

:-D

---

### Post by ghindo on 2008-07-26
> **Mediapirate said:**
> Brilliant tutorial dude.

I don't think I would have managed to get it installed without your help.

I used it before but can't remember where I got the details to install it from.

Keep updating it also and i'll keep it bookmarked.

:-DNo problem, glad it helped you out!  I'll do my best to keep it updated.

---

### Post by rainwalker on 2008-08-02
I'm only on the first step and I'm already worried...
> riley@riley-laptop:~$ sudo aptitude install cd-discid cdparanoia ruby ruby-pkg-tools libgettext-ruby1.8 libgtk2-ruby
[sudo] password for riley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  jackd libevolution3.0-cil libgnome-keyring1.0-cil libgnomedesktop2.20-cil 
  libsox-fmt-all libsox-fmt-alsa libsox-fmt-ao libsox-fmt-base 
  libsox-fmt-ffmpeg libsox-fmt-flac libsox-fmt-gsm libsox-fmt-mp3 
  libsox-fmt-ogg libsox-fmt-oss libsox-fmt-sndfile libsox0 mjpegtools 
  mkvtoolnix ogmtools sox 
The following NEW packages will be automatically installed:
  debhelper devscripts fakeroot html2text intltool-debian irb1.8 
  libatk1-ruby1.8 libcairo-ruby1.8 libcompress-raw-zlib-perl 
  libcompress-zlib-perl libdigest-hmac-perl libdigest-sha1-perl 
  libfile-remove-perl libgdk-pixbuf2-ruby1.8 libgettext-ruby-util 
  libglib2-ruby1.8 libgtk2-ruby1.8 libio-compress-base-perl 
  libio-compress-zlib-perl libio-stringy-perl libmail-box-perl 
  libmail-sendmail-perl libmailtools-perl libmime-types-perl 
  libobject-realize-later-perl libpango1-ruby1.8 libreadline-ruby1.8 
  libsvn-perl libuser-identity-perl po-debconf rdoc rdoc1.8 
  svn-buildpackage unp 
The following NEW packages will be installed:
  cd-discid debhelper devscripts fakeroot html2text intltool-debian irb1.8 
  libatk1-ruby1.8 libcairo-ruby1.8 libcompress-raw-zlib-perl 
  libcompress-zlib-perl libdigest-hmac-perl libdigest-sha1-perl 
  libfile-remove-perl libgdk-pixbuf2-ruby1.8 libgettext-ruby-util 
  libgettext-ruby1.8 libglib2-ruby1.8 libgtk2-ruby libgtk2-ruby1.8 
  libio-compress-base-perl libio-compress-zlib-perl libio-stringy-perl 
  libmail-box-perl libmail-sendmail-perl libmailtools-perl 
  libmime-types-perl libobject-realize-later-perl libpango1-ruby1.8 
  libreadline-ruby1.8 libsvn-perl libuser-identity-perl po-debconf rdoc 
  rdoc1.8 ruby-pkg-tools svn-buildpackage unp 
0 packages upgraded, 38 newly installed, 20 to remove and 0 not upgraded.
Need to get 5510kB of archives. After unpacking 15.1MB will be used.
Do you want to continue? [Y/n/?] 

That's A LOT of stuff to install/uninstall, is this normal?

---

### Post by ghindo on 2008-08-03
> **rainwalker said:**
> I'm only on the first step and I'm already worried...


That's A LOT of stuff to install/uninstall, is this normal?That doesn't seem normal to me.  Could aptitude just be taking care of dependencies for other programs?

---

### Post by rainwalker on 2008-08-03
I guess so...I'll go ahead and try it tomorrow and let you know what happens

---

### Post by ghindo on 2008-08-04
> **rainwalker said:**
> I guess so...I'll go ahead and try it tomorrow and let you know what happensDefinitely.  Let me know how it goes and I'm sorry I couldn't be of more help :(

---

### Post by Circus-Killer on 2008-08-05
awsome tutorial, but i've got one problem.

everything installed okay. but when i start rubyripper, in the main window it sais "Cdrom drive scd0 does not exist on your system! Please first configure your cdrom drive first."

strange thing is that the cdrom works fine in everything else. it picks up in gnome in general, sound juicer and rhythmbox both pick em up. and when i tell rubyripper to open the cd drive, it does. but when i close the cd drive, rubyripper wont read the cd, just gives me back the same message.

any ideas?

---

### Post by Circus-Killer on 2008-08-05
> **Circus-Killer said:**
> awsome tutorial, but i've got one problem.

everything installed okay. but when i start rubyripper, in the main window it sais "Cdrom drive scd0 does not exist on your system! Please first configure your cdrom drive first."

strange thing is that the cdrom works fine in everything else. it picks up in gnome in general, sound juicer and rhythmbox both pick em up. and when i tell rubyripper to open the cd drive, it does. but when i close the cd drive, rubyripper wont read the cd, just gives me back the same message.

any ideas?

okay, found this solution in another thread.
i ran the command: ls -l /dev/cdrom*
which gave me the following results:
```
lrwxrwxrwx 1 root root 4 2008-08-05 19:23 /dev/cdrom -> scd0
```
with this, a user suggested that i go into rubyripper preferences, and change the cdrom field from **/dev/cdrom** to **/dev/scd0**

it worked for me, so just thought i would post it here in case someone runs into the same problem.

---

### Post by logos34 on 2008-08-05
> **Circus-Killer said:**
> a user suggested that i go into rubyripper preferences, and change the cdrom field from /dev/cdrom to /dev/scd0

it worked for me, so just thought i would post it here in case someone runs into the same problem.

Wish I had your luck.  That's the first thing I tried...no go.  And I already have the symlinks in /dev pointing to scd0

This problem has plagued me since I first tried to run Ruburipper a long time ago.  Nothing seems to change.  I get that 'does not exist!' runaround no matter if I set it to cdrom, scd0, hdc or whatnot--and this despite the fact that the 'open/close tray' button works!  Go figure...

---

### Post by rainwalker on 2008-08-07
Awesome, everything worked for me :)
Had to change the path to my CD drive to /dev/scd0 but that's it, thanks!

---

### Post by ghindo on 2008-08-10
> **Circus-Killer said:**
> a user suggested that i go into rubyripper preferences, and change the cdrom field from **/dev/cdrom** to **/dev/scd0**

it worked for me, so just thought i would post it here in case someone runs into the same problem.I was having that problem as well, and your solution worked for me!  Thanks :)  I'll edit the OP in case anybody else is having difficulties, and maybe file a bug report.

---

### Post by logos34 on 2008-08-10
> **ghindo said:**
> I was having that problem as well, and your solution worked for me!  Thanks :)  I'll edit the OP in case anybody else is having difficulties, and maybe file a bug report.

everyone has success except me.:(

---

### Post by thomman on 2008-08-18
Thanks for the install directions. I managed to install it. But Now when I try to rip it says LAME not found on system. Ihave already enabled LAME I think by installing Ubuntu restricted extras. What else could be wrong?

---

### Post by Circus-Killer on 2008-08-19
> **thomman said:**
> Thanks for the install directions. I managed to install it. But Now when I try to rip it says LAME not found on system. Ihave already enabled LAME I think by installing Ubuntu restricted extras. What else could be wrong?

no, ubuntu-restricted-extras does not install lame. to install lame, go to the terminal and enter: ```
sudo aptitude install lame
```

---

### Post by VCSkier on 2008-08-21
This is a great program.  Thanks for the tutorial ghindo.  I'm wondering if if something is wrong with my setup though.  I launched Rubyripper from terminal via "./rubyripper_gtk2.rb", and my drive has been whirring away for almost a half hour already.  In the Rubyripper window, both of the progress percentages ("ripping progress" and "not yet started") have stayed at 0%, and the progress meter in the terminal is probably at about 30%.  So going by the terminal's progress meter, the whole rip should take about an hour and a half.  That just doesn't seem right.

The cd wasn't terribly scratched...  Here's my log so far:

```
This log is created by Rubyripper, version 0.5.2
Website: http://code.google.com/p/rubyripper

Cdrom player used to rip:
HL-DT-ST RW/DVD GCC-4243N 1.01
Cdrom offset used: 102

Ripper used: cdparanoia -Z
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-flac 	-> --best (flac 1.2.1)

CDDB INFO

Artist	= RUN KID RUN
Album	= LOVE AT THE CORE
Year	= 2008
Genre	= Punk
Tracks	= 10

01 - Rescue Me
02 - CAPTIVES COME HOME
03 - Fall into the Light
04 - One In A Million
05 - LOVE AT THE CORE
06 - Sure Shot
07 - My Sweet Escape
08 - The Emergency
09 - SET THE DIAL
10 - Freedom

STATUS

Starting to rip CD image, trial #1}
```

Is this normal?

If it's relevant, I'm ripping to a single file image, and encoding to flac.

---

### Post by ghindo on 2008-08-23
> **VCSkier said:**
> This is a great program.  Thanks for the tutorial ghindo.  I'm wondering if if something is wrong with my setup though.  I launched Rubyripper from terminal via "./rubyripper_gtk2.rb", and my drive has been whirring away for almost a half hour already.  In the Rubyripper window, both of the progress percentages ("ripping progress" and "not yet started") have stayed at 0%, and the progress meter in the terminal is probably at about 30%.  So going by the terminal's progress meter, the whole rip should take about an hour and a half.  That just doesn't seem right.

The cd wasn't terribly scratched...  Here's my log so far:

```
This log is created by Rubyripper, version 0.5.2
Website: http://code.google.com/p/rubyripper

Cdrom player used to rip:
HL-DT-ST RW/DVD GCC-4243N 1.01
Cdrom offset used: 102

Ripper used: cdparanoia -Z
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-flac 	-> --best (flac 1.2.1)

CDDB INFO

Artist	= RUN KID RUN
Album	= LOVE AT THE CORE
Year	= 2008
Genre	= Punk
Tracks	= 10

01 - Rescue Me
02 - CAPTIVES COME HOME
03 - Fall into the Light
04 - One In A Million
05 - LOVE AT THE CORE
06 - Sure Shot
07 - My Sweet Escape
08 - The Emergency
09 - SET THE DIAL
10 - Freedom

STATUS

Starting to rip CD image, trial #1}
```

Is this normal?

If it's relevant, I'm ripping to a single file image, and encoding to flac.I'm not entirely sure if this is normal, but if you're ripping an entire CD to one image, it may be.  I would let it go for a bit longer, and if nothing changes then I would start getting worried.

---

### Post by thomman on 2008-08-24
> **Circus-Killer said:**
> no, ubuntu-restricted-extras does not install lame. to install lame, go to the terminal and enter: ```
sudo aptitude install lame
```

Thanks I think Iv got it working now.

---

### Post by Despot Despondency on 2008-08-26
Great tutorial, bookmarked it for future reference. Seem to have a problem though, when I press the 'rip cd now' button rubyripper just closes and nothing happens. Has anyone else had this problem. Any ideas on how to solve it?

---

### Post by Despot Despondency on 2008-08-26
OK, so I ran rubyripper in the terminal and I got the following message

```

Use config file ~/.rubyripper/settings
Audio-disc found, number of tracks : 10, total playlength : 68:38
Fetching freedb info...

FREEDB INFO
Artist : Du Pré, Baker, Barbirolli (LSO)
Album : Elgar: Cello Concerto Sea Pictures
Genre : Classical
Year : 2004

Track 1 : Cockaigne (In London Town) Op.40
Track 2 : Moderato
Track 3 : 2.Lento
Track 4 : 3.Adagio
Track 5 : 4.Allegro
Track 6 : 1.Sea Slumber song
Track 7 : 2.In Heaven (Capri)
Track 8 : 3.Sabbath Morning at Sea
Track 9 : 4.Where Corals Lie
Track 10 : 5.The Swimming


Should all tracks be ripped ? (y/n)  [y] y
Tracks to rip are 1 2 3 4 5 6 7 8 9 10
Now here, class = Rubyripper
/usr/local/lib/site_ruby/1.8/rr_lib.rb:113:in `get_filename': undefined method `varArtists' for #<Disc:0xb7bbc580> (NoMethodError)
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:1343:in `prepare_dirs'
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:1341:in `each'
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:1341:in `prepare_dirs'
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:1274:in `settings_ok'
	from /usr/local/bin/rrip_cli:280:in `freedb_finished'
	from /usr/local/bin/rrip_cli:359:in `update'
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:577:in `searchMetadata'
	from /usr/local/lib/site_ruby/1.8/rr_lib.rb:557:in `freedb'
	from /usr/local/bin/rrip_cli:265:in `get_cd_info'
	from /usr/local/bin/rrip_cli:48:in `initialize'
	from /usr/local/bin/rrip_cli:402:in `new'
	from /usr/local/bin/rrip_cli:402

```

I have also noticed that in the gui this cd has two sections for artist, even though one section is actually part of the title (see screenshot).I think this is causing the problem, since I managed to rip a different cd fine, but that one only had one artist field at the top of the screen. Still don't know what to do?

---

### Post by Despot Despondency on 2008-08-28
Turns out I was being extremely stupid. All I had to was uncheck the multiple artist box and it ripped fine. Can't believe it, didn't even notice that box until just now. doh..

---

### Post by ghindo on 2008-09-03
Minor update: Changed from Rubyripper version 0.5.2 to 0.5.3.

Fixes included in Rubyripper 0.5.3:> ---------0.5.3 RELEASE------

* fix detection of some devices
* update Hungarian / German translation
* fix permissions on install + other small config fixes
* add totaltracks tag
* add albumartist tag
* add support for lame 3.98: all genre tags now allowed
* mention the artist / album in the summary page
* add accelerator keys
* encoding errors are now always reported
* support weird characters in tags, while disabling in the filename
* small fixes here and there

---

### Post by NWAdawg on 2008-09-05
I followed the install directions. Got Rubyripper up and running, no problems. It is a very nice mp3 ripper, far better than the other ones I've used. Thank you for this HowTo thread.

---

### Post by Crafty Kisses on 2008-09-05
Thanks, nicely written. :)

---

### Post by oliwally on 2008-09-09
Great stuff ghindo. Worked well!

To improve this how to - perhaps include 'lame' in step one. And secondly, a quick user guide to explain how to adjust the compression settings. How, for example, do I tell Rubyripper to compress to Mp3 at 128 mps constant bitrate?

I just wish someone would make a linux ripper with a gui that has simple options to click/tick to allow users to choose compression rate and the file naming scheme. Get away from all the codes that one has to look up... how would I know what "-V 3" means for the lame codec. I'm not interested in finding out - just give me a button with easy to understand options!

---

### Post by keyshawn on 2008-09-27
Thanks for your tutorial. Following it, I had no problems installing rubyripper. However, I am unable to rip any mp3s. 

After configuring it, rubyripper spits out this message when I am extracting a cd: 

```
WARNING: ENCODING ERRORS WERE DETECTED
``` and didn't create the mp3 file for me. 

After looking on the rubyripper website, I found someone with the same error message and the developer advised them to upgrade lame to 3.98 (hardy only has 3.97...boo). 

Has anyone else had problems as well ? Are you able to use lame 3.97 with rubyripper (I'm using version 0.5.3) ?

Edit: I got to work by using the following parameters for my flac and mp3 files: 
flac: -v -8 
lame/mp3: -v0 --vbr-new

Tagging is already taken care of too !

---

### Post by tog1947 on 2008-10-23
Hi,

Changed from Windows to Ubuntu about a month ago.

Have been using RubyRipper and neroAacEnc to rip my CD's with this command line:

/home/ian/NeroCodecs/neroAacEnc -br 256000 -if %i -of "%o.m4a"

This works fine but it doesn't tag the output files as NeroAacEnc doesn't support tagging.

Now Nero have produced neroAacTag for linux and I have put this in the same folder as neroAacEnc with the same permissions  - but I can't figure out the syntax to get this program to tag the output files from the same command line in RubyRipper "other" codecs.

I've tried appending this:

&& /home/ian/NeroCodecs/neroAacTag %a %t %b %n  
 
(and many variations specifying input and output files) but nothing works.

Can anybody help?

---

### Post by mc4man on 2008-10-23
I use this as a command line for neroAacEnc in rr, though am using -q instead of -br. ( a -q of 0.37 is about 128k, a -q of 0.75 is around 320k though maybe not necessary. Personally I prefer using -q to a set br

```
neroAacEnc -q 0.65  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a
```

Couple of ways to have rr auto rip upon cd insertion
[http://ubuntuforums.org/showthread.php?p=5708646#post5708646](http://ubuntuforums.org/showthread.php?p=5708646#post5708646)

---

### Post by tog1947 on 2008-10-23
Thanks for the quick reply.

Copied your string verbatim and it produced an untagged file.

So thought it must be something in rr. I didn't have anything in the "Pass CD Paranoia Options" box. Should I have a string in there too?

Will think later about "q" and not letting Rhythmbox open every time I put a CD in - but for now trying to resolve this.

---

### Post by mc4man on 2008-10-23
> it produced an untagged file.
I'm sorry, I've never paid much attention to tagging because I never use the gui of any player for playback so naming is more important here. Just assumed it was tagging due to the line in mediainfo I'd see when checking files occasionally. (screen
Have do do some experimenting with neroAactag.

> I didn't have anything in the "Pass CD Paranoia Options" box
I don't either but I don't believe that has anything to do with tagging. The default of rr is -Z which 'disables all paranoia checking'. I removed it because I know my drive has no issues there and don't mind the extra time to rip.

---

### Post by tog1947 on 2008-10-24
You may find that everything in your ripping string after *"%o.m4a"* is redundant and that the result will be the same even if you remove everything after that - that's how mine seems to work.

I think I need to invoke neroAacTag at that point and then execute the tagging commands but I can't figure out how to do that.

Will let you know if I figure anything out.

I stopped Rhythmbox opening automatically - thanks for the hint. 

The "q" settings I'll pass on as 256 is more than adequate and I did that for consistency with the vast amount of music I had previously encoded in iTunes.

---

### Post by tog1947 on 2008-10-24
I upgraded to 0.5.3 today but ripping log files created by rr still say created with 0.5.2 - although the executables have definitely been updated.

Can't find a version number in the GUI.

---

### Post by mc4man on 2008-10-24
> You may find that everything in your ripping string after "%o.m4a" is redundant
Your correct there - didn't realize 'other' used the preset naming.
Spent a few min. with neroAacTag, you can run it 'after the fact' and it works well to some extent. This works on a folder for all tracks
> 
doug@doug-desktop:~/other/The Jimi Hendrix Experience (1968) Electric Ladyland$ neroAacTag  *.m4a -meta:artist="Jimi Hendrix" -meta:album="Electric Ladyland" -meta:genre=rock -meta:year=1968 -meta:totaltracks=16


If I used something like this it accepted but reports info as %[COLOR="Red"]x[/COLOR]
>  neroAacTag  *.m4a -meta:artist="%a" -meta:title="%t" -meta:album="%b" -meta:track="%n" -meta:genre=rock

Track specific seemed to have to be done individually (-meta:track=[COLOR="Red"]x[/COLOR],  ect.


I'm sure you can figure this out better than me
What i found info wise
> 
Usage:
neroAacTag <file.mp4> <command> [<command> [<command> ...]]
Available commands:
-list-meta                    : Lists existing metadata entries.
-meta:<name>=<value>          : Sets specified metadata field to specified
                                value. Eg. -meta:artist="Pink Floyd"
-meta-user:<name>=<value>     : Sets specified metadata field to specified
                                value. Allows non-standard metadata fields
                                to be added.
                                WARNING: fields added using -meta-user are
                                not guaranteed to be read back on all
                                Nero Digital compliant software/hardware.
-list-standard-meta           : Displays a list of field names usable with
                                -meta command.
-list-covers                  : Lists cover art entries.
-add-cover:<type>:<jpegfile>  : Creates a cover art entry from specified 
                                JPEG file.
                                <type> specifies type of cover art entry and
                                can be "front" or "back".
                                If specified cover art entry already exists,
                                its contents are overwritten.
                                Eg. -add-cover:back:hello.jpg
-dump-cover:<type>:<jpegfile> : Dumps specified cover art entry contents to 
                                a JPEG file.
-remove-cover:<type>          : Removes specified cover art entry.
-remove-cover:all             : Removes all cover art entries.
-list-chapters                : Lists chapters present in the file.
-chapter:<number>             : Sets chapter index metadata edits apply to.
                                Value of 0 (default state) applies edits to
                                all present chapters.
                                Also affects -list-meta output.
-chapters-to-tracknumbers     : Generates track number metadata according to
                                the chapter list

> List of standard Nero Digital metadata field names:
  title
  artist
  year
  album
  genre
  track
  totaltracks
  disc
  totaldiscs
  url
  copyright
  comment
  lyrics
  credits
  rating
  label
  composer
  isrc
  mood
  tempo
End of metadata field name list.
The above field names can be used with -meta command. To bypass the field name list restriction, use -meta-user command instead of -meta. Fields not present in the above list are not guaranteed to be read by Nero Digital compliant software/hardware.


---

### Post by tog1947 on 2008-10-24
Thanks for your help mc4man but I think I'll stay with EasyTag for now - it's very simple to use and gets the job done in a few minutes per album.

---

### Post by mc4man on 2008-10-24
I saw what I think was your post on an other forum so checked out easytag earlier - does seem a lot more straightforward.

---

### Post by tog1947 on 2008-10-26
I've been researching for the last couple of days and come up with some enhancements - thanks to Junon and others on the HydrogenAudio forum.

Firstly install AtomicParsley (Command Line Tagger) from Synaptic.

Then put something like this in your command line for "Other" codecs:

neroAacEnc -br 256000 -if %i -of "%o.m4a" && mkdir -p "/home/YOURNAME/Desktop/NewRips/%a/ %b" && AtomicParsley "%o.m4a" -o "/home/YOURNAME/Desktop/NewRips/%a/ %b/%n. %t.m4a" --artist "%a" --album "%b" --tracknum "%n" --title "%t" && rm "%o.m4a"

Substitute your username for YOURNAME as appropriate.

You can adjust -br to your preference or substitue appropriate -q value.

This will create a structured NewRips/Artist/Album folder on your desktop with tagged .m4a files inside - you can also add genre and year tags through the command line, if you prefer. Once you have reviewed the files you can drag and drop them into the appropriate location in your music folder.

It will also remove the untagged .m4a file from wherever you previously set in RubyRipper.

[FONT="Comic Sans MS"]***If you change the "Base Directory" setting in RubyRipper/Preferences/Other to:

/home/YOURNAME/Music/RippingLogs

it will leave behind a stuctured folder of all your ripping logs inside your Music folder.***

***Only carry out this instruction if you are ONLY ripping to AAC.***[/FONT]

If you don't change it your ripping logs will still be left behind wherever your privious settings indicated.

I tried this substituting "neroAacTag" for "AtomicParsley" in the string but it didn't work - maybe somebody else would like to take that up.

---

### Post by Fraoch on 2008-11-02
Installed Intrepid yesterday and decided to update Rubyripper to 0.5.4.

Unfortunately I can't get it installed:

```
mark@Sauron:~/Desktop/rubyripper-0.5.4$ sudo ./configure --enable-lang-all --enable-gtk2 --enable-cli
./rr_lib.rb:19: undefined method `+' for nil:NilClass (NoMethodError)
	from ./configure:37:in `require'
	from ./configure:37
mark@Sauron:~/Desktop/rubyripper-0.5.4$
```

make install obviously doesn't work after this.

All dependencies are satisfied, I have an older version of Rubyripper installed and running fine.

Any ideas?

---

### Post by PeeZz on 2008-11-12
I've just installed Rubyripper 0.5,4 and everything works just fine.

You can use the same instructions to install it.

---

### Post by Fraoch on 2008-11-13
> **PeeZz said:**
> You can use the same instructions to install it.

Which instructions?  I've tried the ones at the start of this thread and the ones in the README (all it adds is a '--prefix=/usr') and I get the same error.:(

---

### Post by ghindo on 2008-11-21
Minor update: Changed from Rubyripper version 0.5.3 to 0.5.4.

Fixes included in Rubyripper 0.5.4:> ---------0.5.4 RELEASE------

* disable threaded encoding, because since the ruby-gtk2 0.17
release forking a process within a thread results in a freeze.
Hopefully a more elegant solution will follow.
* add French translation
* add proxy support

---

### Post by curts on 2008-11-23
Upgraded to Ubuntu 8.10 today, and then discovered that Rubyripper 0.5.3 had stopped working properly.  Upgraded to 0.5.4 and all is well.

Curt

---

### Post by Fraoch on 2008-11-27
Well, I seemed to be the only one having problems installing, so I took the easy way out - the 64-bit Intrepid build at Getdeb as suggested on another forum.

[http://www.getdeb.net/app/Rubyripper](http://www.getdeb.net/app/Rubyripper)

0.5.4 install worked like a charm...even kept my old settings.

---

### Post by ghindo on 2008-11-27
> **Fraoch said:**
> Well, I seemed to be the only one having problems installing, so I took the easy way out - the 64-bit Intrepid build at Getdeb as suggested on another forum.

[http://www.getdeb.net/app/Rubyripper](http://www.getdeb.net/app/Rubyripper)

0.5.4 install worked like a charm...even kept my old settings.Huh, I didn't even know that there was a .deb for Rubyripper.  Kinda makes my tutorial feel obsolete :(

Glad you found it and go everything working, though!

---

### Post by Fraoch on 2008-11-27
Perhaps it had something to do with 64-bit - your instructions were straightforward and there wasn't really a way for me to get it wrong aside from a typo...(which didn't happen as I copied and pasted and checked spelling when it didn't work).

---

### Post by BigAl-SA on 2008-12-25
Just got onto this ripper from [another page](http://ubuntuforums.org/showthread.php?t=300635) which pointed to 0.5.3. I installed using the recipe with no problems. When I ran it though (Intrepid), it went into a loop hogging one core to 100%. I saw there was a newer version out so uninstalled via the recipe. Got this error:

```
ruby configure --update-lib                                                                               
./rr_lib.rb:19: undefined method `+' for nil:NilClass (NoMethodError)                                     
        from configure:37:in `require'                                                                    
        from configure:37                                                                                 
make: *** [clean] Error 1 
```

Installed 0.5.4, and it now works ok. Looks good too, especially with all the hassles I had with another GUI ripper yesterday.

---

### Post by Capt_Zaphod on 2008-12-28
The tutorial worked perfectly, the first try.

Thank you!

---

### Post by Fraoch on 2009-01-05
> **BigAl-SA said:**
> Just got onto this ripper from [another page](http://ubuntuforums.org/showthread.php?t=300635) which pointed to 0.5.3. I installed using the recipe with no problems. When I ran it though (Intrepid), it went into a loop hogging one core to 100%. I saw there was a newer version out so uninstalled via the recipe. Got this error:

```
ruby configure --update-lib                                                                               
./rr_lib.rb:19: undefined method `+' for nil:NilClass (NoMethodError)                                     
        from configure:37:in `require'                                                                    
        from configure:37                                                                                 
make: *** [clean] Error 1 
```

Installed 0.5.4, and it now works ok. Looks good too, especially with all the hassles I had with another GUI ripper yesterday.

Gee, looks awfully familiar. ;)  See my previous posts in this thread.  We've both solved our problems, but out of interest, are you running 64 bit?

---

### Post by tubegeek on 2009-01-12
Thanks to all of you who recommended getdeb - I was stumped with the exact same problem in compiling as above (on 32-bit, FYI) and getdeb method solved my woes.

THANKS!!

---

### Post by lingenfr on 2009-01-19
I installed gettext and libgettext-ruby1.8 and the configure and make worked fine.

---

### Post by Joe on 2009-01-21
Anyone else have a problem with the most recent version (0.5.4) stopping before ripping the last track of the cd?

---

### Post by herefornow on 2009-01-25
Thanks for the instructions. They worked fine for me on ubuntu 8.1 using ruby 0.5.4

---

### Post by VCSkier on 2009-02-03
0.5.5 appears to be out now.  I haven't tried it yet, but I hope to soon.

On another note, how could one go about requesting that rubyripper be added to the universe repository?  I wouldn't think it would be hard.  Who would we need to ask?

---

### Post by ghindo on 2009-02-17
Sorry that I haven't been updating this thread all that much - school has started and I am now using Arch Linux.> **VCSkier said:**
> 0.5.5 appears to be out now.  I haven't tried it yet, but I hope to soon.

On another note, how could one go about requesting that rubyripper be added to the universe repository?  I wouldn't think it would be hard.  Who would we need to ask?Yes, Rubyripper 0.5.5 is out!  I haven't updated the guide yet, as I no longer have an Ubuntu system.  But if somebody wants to build it on an Ubuntu system and let us know how it works, please do so!

As for adding Rubyripper to the Ubuntu repositories, I [filed a bug report a while ago]("https://bugs.launchpad.net/debian/+bug/234228"), but I'm not sure if there's anything else we can really do, other than either wait for the developers or package Rubyripper ourselves (which I don't know how to do, and don't really have the time/motivation to learn).

---

### Post by dkelley on 2009-03-17
I installed the prereq stuff (cd-discid, cdparanoia, flac, lame, mp3gain, normalize-audio, ruby-gnome2, ruby, vorbisgain) and all the other garbage it neeeds via SPM.  I then installed rubyripper 0.5.5.1 via debian package install (downloaded the .deb from getdeb) and it installed ok.  The app even shows up in the Applications menu.  Something is not quite right though because when I start it, it scans the CD drive but then it can't find the freedb server (not sure why, I'm online).  Then when I click Rip CD Now, it just exits.  Also when I press Preferences -> Disc Info just exits.

Suggestions??

Thanks in advance.
Dan ...

---

### Post by ghindo on 2009-03-18
> **dkelley said:**
> I installed the prereq stuff (cd-discid, cdparanoia, flac, lame, mp3gain, normalize-audio, ruby-gnome2, ruby, vorbisgain) and all the other garbage it neeeds via SPM.  I then installed rubyripper 0.5.5.1 via debian package install (downloaded the .deb from getdeb) and it installed ok.  The app even shows up in the Applications menu.  Something is not quite right though because when I start it, it scans the CD drive but then it can't find the freedb server (not sure why, I'm online).  Then when I click Rip CD Now, it just exits.  Also when I press Preferences -> Disc Info just exits.

Suggestions??

Thanks in advance.
Dan ...Hm, I'm not sure.  Have you tried launching Rubyripper from the command line?  Have you tried building it from source?

---

### Post by Ticketoride on 2009-04-20
Installed without a Hitch, runs flawlessly, and no Crashes under U-9.04

Thx for the Tutorial.

Cheers

---

### Post by anlayne on 2009-05-25
Running a new install of Rubyripper as per this thread with a cd in the drive, I get this:

```
adam@adam-desktop:~$ rrip_cli
Use config file ~/.rubyripper/settings
Audio-disc found, number of tracks : 4, total playlength : 39:41
Fetching freedb info...
/usr/local/local/lib/site_ruby/1.8/rr_lib.rb:840:in `checkVarArtist': undefined method `include?' for nil:NilClass (NoMethodError)
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:839:in `times'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:839:in `checkVarArtist'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:837:in `each'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:837:in `checkVarArtist'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:825:in `handleResponse'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:653:in `searchMetadata'
	from /usr/local/local/lib/site_ruby/1.8/rr_lib.rb:634:in `freedb'
	from /usr/local/bin/rrip_cli:265:in `get_cd_info'
	from /usr/local/bin/rrip_cli:49:in `initialize'
	from /usr/local/bin/rrip_cli:480:in `new'
	from /usr/local/bin/rrip_cli:480
```

and then it quits. Disabling freedb lookup allows the cd to rip, but that's not really an acceptable solution. I know other people have had this problem, but I never found a suitable solution. Thanks in advance.

---

### Post by Fraoch on 2009-05-26
Looks sort of like freedb has changed the way they send back data and RubyRipper can't handle it?

---

### Post by VCSkier on 2009-06-09
Does anyone here rip their CD's to single file FLAC images, with cuesheets?  I like to for a variety of reasons, but K3B is the only application that I know of that can burn them back to a blank CD.  Does anyone know of any other applications that can do this?  I don't like having all the excess KDE packages for one simple task.  Thanks!

---

### Post by howwhi on 2009-07-01
Just followed the instructions (that you repeated from the wiki) with rubyripper 0.5.5 

./configure fails with the message

/usr/lib/ruby/1.8/gtk2.rb:12:in `init': Cannot open display:   (RuntimeError)

make install fails for lack of rule to make target

How to fix??   Going to try 0.5.4

---

### Post by mc4man on 2009-07-02
> How to fix??
Read the 'readme' in RR source folder

I'd install libgtk2-ruby1.8

> Suggested:
* ruby-gettext (for translations)
* [COLOR="Blue"]ruby-gtk2 [/COLOR](for gtk2 gui)
* cd-discid or discid (for proper freedb support)
* eject or diskutil for MacOS (for eject support)
* flac, oggenc, lame (if the codec is wanted)
* wavgain, vorbisgain, mp3gain (for replaygain support)
* normalize (for normalize support)


---

### Post by ghindo on 2009-07-11
Rubyripper 0.5.6 is out:```
---------0.5.6 RELEASE------
* fix a problem with cdparanoia and last track on some drives
* implement "abort" button while ripping
* add Bulgarian translation
* support for multiple-disc albums
* some ruby-1.9 syntax fixes
* fix various artist field for other codec
* don't convert to ISO-8859-1 for lame if the character isn't supported
* add an option to replace spaces with underscores
* add an option to lowercase all filenames.
* remove the hardcoded --id3v2only tag
```

---

### Post by ghindo on 2009-07-11
By the way, is there any way for me to change the title of this thread?  It still shows up as "HOWTO:  Install Rubyripper 0.5.0 on Ubuntu 8.04" even though I've tried to change it :/

---

### Post by ghindo on 2009-07-13
Rubyripper 0.5.7 is out:> ---------0.5.7 RELEASE------
* a fix for discs that start with a data track
* a fix for checking the available space for some languages
* a few fixes for the OpenBSD platform
* fix a typo in the logfile when errors were corrected
* don't replace bracquets in filenames -> []
* fix a typo which resulted in a directory not containing the album name
* allow multiple encoding threads once again :)

---

### Post by ghindo on 2009-07-15
Looks like [there's been some progress upstream in packaging Rubyripper]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463584#20").  With any luck, before too long I'll be leaving this guide by the wayside and authoring a new one - HOWTO:  Configure and Use Rubyripper :)

---

### Post by meocuchad on 2009-07-15
I really appreciate you making this install guide, ghindo. You made it painless as could be for a Linux newbie like me. Thanks a million!

---

### Post by ghindo on 2009-07-16
> **meocuchad said:**
> I really appreciate you making this install guide, ghindo. You made it painless as could be for a Linux newbie like me. Thanks a million!No problem!  Glad it helped you out :)

---

### Post by warpasylum on 2009-07-21
Thanks man. Worked fine for me on Jaunty 64-bit.:)

---

### Post by Artemis3 on 2009-07-23
This ripper looks promising, one of the few that won't destroy japanese characters in tags, cues or filenames.

Bugs with the 0.5.7 version:

You can't use the "RIP CD to single file" preference, so no single flac+cue (cdparanoia seems to hang).

Using 2 encoder threads should stick to encoding, not ripping. I don't think its healthy for the drive to spawn 2 cdparanoia processes which are twice reading each track...

Grip was smarter in this regard, you could have it rip tracks and start encoding the tracks already ripped in parallel.

Will be very nice when the AccurateRip feature is added.

---

### Post by ghindo on 2009-07-26
> **Artemis3 said:**
> This ripper looks promising, one of the few that won't destroy japanese characters in tags, cues or filenames.

Bugs with the 0.5.7 version:

You can't use the "RIP CD to single file" preference, so no single flac+cue (cdparanoia seems to hang).

Using 2 encoder threads should stick to encoding, not ripping. I don't think its healthy for the drive to spawn 2 cdparanoia processes which are twice reading each track...

Grip was smarter in this regard, you could have it rip tracks and start encoding the tracks already ripped in parallel.

Will be very nice when the AccurateRip feature is added.Be sure to file those bugs with Rubyripper so these bugs get fixed!

---

### Post by yahoo on 2009-07-27
Thanks ghindo, easy install on jaunty 9.04. Rips just as I like.
Cheers
yahoo

---

### Post by sjalloq on 2009-07-27
Hi there,

I haven't been able to find any official support forums for rubyripper so decided to post on this thread.  Please let me know if I should move it somewhere more appropriate.

I have just installed the 0.5.7 CLI on my Ubuntu Server 9.04.  I'm running 32-bit on an old AMD Sempron.

As soon as rubyripper starts to rip it exits.  Are there any known bugs?  Is there a way of getting more verbose debug output?

Thanks.

```
STATUS

Ripping progress (0 %)
Ripping track 1
Expected filesize for track 1 is 44753900 bytes.
ubuntu-server:~>

```

---

### Post by codedash on 2009-08-09
> **ghindo said:**
> Looks like [there's been some progress upstream in packaging Rubyripper]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463584#20").  With any luck, before too long I'll be leaving this guide by the wayside and authoring a new one - HOWTO:  Configure and Use Rubyripper :)

Is it that difficult for ubuntu developers to make the first move and add some new packages in the repos? Why debian must always include the packages first so we can benefit? I dont like this.

---

### Post by ghindo on 2009-09-07
Exciting news for us:  not only has mc4man been so kind as to [package Rubyripper for us]("http://ubuntuforums.org/showpost.php?p=7909514&postcount=17"), but there has been progress on [the bug I filed over a year ago]("https://bugs.launchpad.net/ubuntu/+bug/234228").  It has now gone from "Confirmed" to "In Progress," and has had a developer sign on.

Exciting! :)

---

### Post by ghindo on 2009-09-08
Today, Andreas Heck created a PPA for Rubyripper, rendering most of my tutorial obsolete.  Check it out [here]("https://launchpad.net/~aheck/+archive/ppa"). :popcorn:

---

### Post by duralex69 on 2009-09-20
Hi,

I've just installed Rubyripper with Ubuntu 9.04 (because I couldn't handle with parametering bitrate in Sound Juicer).

It looks like good but I would have three more questions :
1) how do you parameter the bitrate for MP3 (the test with VLC I did renders me a file at 128 kb/s and in Nautilus it's 51 kbps !!!) Personnaly, I would like to rip at 160 kbps.
2) what is "cuesheet" and is it important ?
3) is it important to parameter "Cdrom offset" because I didn't find how to.

I'm very sorry for my poor english I hope you can manage with it (you know I'm french !!!).

Thanks for your answers...

Best Regards

Alex

---

### Post by Trent T on 2009-09-23
Thanks, ghindo!
I was able to follow your instructions the 2nd time I tried--
My first go did not work, but the 2nd time I used the CLI(terminal) command to 'extract here.'  For some reason, it worked where the GUI command did not.

As a side benefit, I finally found out that, while Control C copies in the GUI environment, I need to use [Shift][Insert] to paste text into the terminal command line.  

Good work, and thanks again!

---

### Post by mvsjes2 on 2009-11-01
Is there a way to have RubyRipper rip a CD as soon as you put it in the drive?

---

### Post by mc4man on 2009-11-01
> Is there a way to have RubyRipper rip a CD as soon as you put it in the drive? 

Pretty simple, a couple of ways.

You can have it run silently in the background or in a visible terminal
I prefer in the background but there are some limitations there.

Versions 0.5.6 and 0.5.7 have a bug that makes it not possible due to having the -a command not work as intended, this has been fixed in the git and should be in the next release. (0.5.5 works fine with -a


The other limitation is if the same output folder exists, that usually requires user interaction which causes the silent to fail.

Ex.
> ...........
Tracks to rip are 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
/home/doug/flac/Funk_Brothers_(2004)_Standing_In_The_Shadows_Of_Motown_(Soundtrack)
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

Please enter the number of your choice:  [1]  

( possibly there is a command line option for options 1 or 2, documentation is hard to find on rrip_cli  (anyone ..?

Basically set your preferences as desired in the gui and then use a small script as a auto run choice or default for audio cd's.



Anyway
For silent

```
#!/bin/bash
rrip_cli -a
```

Edit: this may be a better command depending on rr version (the very latest uses -d, .deb below uses the -a
rrip_cli -d

for visible (again the deb below uses -a, latest git uses -d 

```
#!/bin/bash
gnome-terminal -e "rrip_cli -a" 
```

I use a ~/bin so put script in there, the home folder would do. Then just put in an audio cd, hold down the shift button and in the pop up dropdown choose 'open with other application' and browse to your script ( on hardy you need another method to add to default /autorun choices

It's possible that you could enter the command directly, I prefer to use and point to a script


Edit:
here's a 0.6 beta that would be suitable for silent/background auto rips
This is a beta but should be fine
(r, click save link as is best way to dl

The gtk gui is currently broken in lucid, works fine from cli ( you can set it up in the gui, then use the cli to rip & encode

Edit: the gui now works in lucid though it does seem to take  much longer to create the md5 and start next trackthan in karmic and earlier - from the cli no such delay

Note that if you happened to want to use  this beta version and had previously installed from the above ppa - **remove the ppa's rubyripper-gtk package first**. The ppa split the cli (rubyripper) and gui (rubyripper-gtk) into 2 separate .deb's. The below beta includes both

---

### Post by nomnex on 2009-11-22
This is about set-up. Need help.


Cdrom device

```
/dev/cdrom
```That's the default CD tray of the notebook. However I am using an external CD-DVD connected to a USB. Rubyripper does not detect it and I don't know how to enter it manually. Ubuntu auto-mounts the drive but whatever I enter in the rubyripper options, that does not work.

A little help welcome

---

### Post by mc4man on 2009-11-22
> I don't know how to enter it manually
It may be /dev/cdrom1 or /dev/cdrom2, ect.

with the usb drive connected run this and find out or just trial & error

```
sudo lshw -C disk
```

---

### Post by nomnex on 2009-11-23
did not work, the only thing that did was

```
/dev/sr1
```

BTW, I have installed the PPA link above and I don't have an icon in the applications nor a GUI (ALT + F2 rubyripper), only the cli (rrip_cli) how do you get the full GUI?

---

### Post by Gorf on 2009-11-23
Rubyripper installed great for me, however it seems to be unable to process foreign language characters.  Specifically I am ripping some of my Russian CD's and the information looks like this:

Artist	= Áàñòà
Album	= Áàñòà 1
Year	= 2006
Genre	= Hip-Hop
Tracks	= 19

01 - Ðàç è íàâñåãäà
02 - Òàê ïëà÷åò âåñíà

Is that a known issue, or should I open a bug on it?  The info in the CDDB database is correct.  Looks like Rubyripper has problems with the text returned.

---

### Post by mc4man on 2009-11-23
> should I open a bug on it? 
RR isn't an ubuntu package, issues should be posted here

[http://code.google.com/p/rubyripper/issues/list](http://code.google.com/p/rubyripper/issues/list)

Did you build or install from a package?

RR can be built with multiple locales (translations), whether that would have any effect on your issue don't really know, though I see a ru folder in the build I did. ( have no idea what it's for..?

/usr/share/locale/ru/LC_MESSAGES/rubyripper.mo

---

### Post by nomnex on 2009-11-24
I have installed the lib and the .deb from the ubuntu help doc CDripping. Work fine now, great app!

BTW do you use the preset -Z or keep the field empty (Pass cdparanoia options), Rubyripper v 5.7.1?

---

### Post by mc4man on 2009-11-24
> BTW do you use the preset -Z or keep the field empty (Pass cdparanoia options), Rubyripper v 5.7.1?

Myself, atm am now using abcde, though still have RR and use occasionally for non aac rip & encodes ( while both RR and abcde can use neroAacEnc and AtomicParsley it goes a bit easier in abcde

Anyway as far as -Z, sometimes I leave it out and sometimes add ( results in a faster rip

You have to see what suits you and your cd's better.

A small note on that ppa linked previously

It appears he's broken RR into 2 packages rubyripper (cli) and rubyripper-gtk (gui

While I guess you could make a small case for that, mself don't see the point.

Also cd-discid is just a recommend, if it's not  installed it should be if you wish cddb info

---

### Post by nomnex on 2009-12-03
> **mc4man said:**
> Anyway as far as -Z, sometimes I leave it out and sometimes add (results in a faster rip) You have to see what suits you and your cd's better.

Also cd-discid is just a recommend, if it's not  installed it should be if you wish cddb info

cd-discid is already installed thanks for the tip

what the purpose of the -Z preset? My CDs are in excellent condition (no scratch) and my drive does not need correction.

---

### Post by mc4man on 2009-12-03
> what the purpose of the -Z preset?

from the man
 > -Z --disable-paranoia           : disable all paranoia checking
 -Y --disable-extra-paranoia     : only do cdda2wav-style overlap checking

Will make the rip faster, tend to use here on most discs, i know my drive is a good ripper and I'm not generally over concerned about such things for ripping for use on pc ( though did set drive offset

---

### Post by nomnex on 2009-12-03
> **mc4man said:**
> from the man
 Will make the rip faster, tend to use here on most discs, i know my drive is a good ripper and I'm not generally over concerned about such things for ripping for use on pc ( though did set drive offset

I am pushing my questions. Rubyripper already reads the CD twice. Is it in addition of cdparanoia or that is cdparanoia - I am bit confuse.

If that's the first case. What's the point to have 2x reading + cdparanoia (noob question what is the diff. between the Rubuyripper check and and cdparanoia?)

thanks

---

### Post by mc4man on 2009-12-03
It is fairly simple to find any info about cdparanoia to whatever extent you wish.

Maybe start here
[http://www.xiph.org/paranoia/faq.html](http://www.xiph.org/paranoia/faq.html)

> How can I tell if my drive would be OK with regular cdda2wav?
Easy. Run cdparanoia; if the progress meter never shows any characters but the little arrow going across the screen, the CDROM drive is probably one of the (currently) few drives that can read a pristine stream of data off an audio disc regardless of circumstances. This drive will work quite well with cdda2wav (or cdparanoia using the '-Z' option)

A drive that results in a bargraph of all hyphens would *likely* work OK with cdda2wav, but it's less certain. 

Run cdparanoia or RR from cli and check out your drive's performance and symbols

---

### Post by nomnex on 2009-12-03
mc4man, can you explain me in simple terms the difference between cdparanoia and cdda2wav in rubyripper (or other ripping software).

**Do I assume correctly that:**

[I]1. cdda2wav is the software that does the actual rip (CD -> WAV) some accuracy checks.
2. cdparanoia is  a another software above or next to cdda2wav that also does the actual rip (CD -> WAV) with some accuracy checks.[/I]

sorry about it but I am all to confuse. Does rubyripper (or other players) use 2 methodes  to rip 1 cd? is it like using 2 spell checkers (same function, but different brands) on a same sentence? Is there not a ripping software that does both in one time (if the preceding was correct)?

Thanks to clarify

**from the net**

> [FONT=Verdana, Arial, Helvetica][SIZE=3][COLOR=Black]cdparanoia began life as a set of patches to Heiko Eissfeldt's '[cdda2wav]("ftp://ftp.gwdg.de/pub/linux/misc/cdda2wav/")' application in late 1994.  Cdparanoia gained its own life as a rewrite of cdda2wav in January of 1998 as "Paranoia III". Paranoia has had no real relation to cdda2wav since then.[/COLOR][/SIZE][/FONT]

---

### Post by codedash on 2009-12-08
Since you created a package, consider create a ppa so more people can use rr, test it and help with development. Either way many thanks to everyone involved in this project.

---

### Post by Gryphen on 2009-12-09
Is there a way to reset the settings back to default(like deleting the config)?

---

### Post by mc4man on 2009-12-09
Delete ~/.rubyripper/settings
(home folder -> edit -> show hidden files if you don't see the .rubyripper folder

---

### Post by ryrules1 on 2009-12-09
For some reason I get this (see below) when I run "make install" any ideas? I have installed all the required and suggested dependants from the Readme. and followed the ./configure steps. 

```
Install GNU Gettext then set PATH or MSGMERGE_PATH correctly.
	from /usr/lib/ruby/1.8/gettext/utils.rb:94:in `msgmerge_all'
	from /usr/lib/ruby/1.8/gettext/utils.rb:147:in `update_pofiles'
	from configure:84:in `update_lang'
	from configure:169
	from configure:147:in `each'
	from configure:147
make: *** [all] Error 1

```

---

### Post by ryrules1 on 2009-12-12
anyone?

---

### Post by mc4man on 2009-12-12
> anyone? 
Well something's not right. Maybe post your configure or compare to this one I just did with 0.5.7
( encoders aren't required to install

> doug@doug-desktop:~/Desktop/rubyripper-0.5.7$ ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr
Checking the NEEDED dependencies....
cdparanoia found...

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
ruby-gtk2 bindings found

Testing support for freedb metadata fetching...
cd-discid or discid found...

Testing support for ejecting the disk tray...
eject or disktutil found...

Testing support for different codecs on your system...
flac found...
oggenc (vorbis) found...
lame (mp3) found...

Testing support for replaygain...
wavegain NOT found.
vorbisgain found...
mp3gain found...

Testing support for normalize...
normalize NOT found
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/bin
* Localization files: /usr/share/locale
* Icon file: /usr/share/icons/hicolor/128x128/apps
* Desktop file: /usr/share/applications
* Ruby library: /usr/local/lib/site_ruby/1.8

Gtk2 frontend will be installed
Cli frontend will be installed
Languages to be installed: nl, de, fr, hu, ru, es, se, bg

You can now run make install
Make sure you've got the writing privileges

doug@doug-desktop:~/Desktop/rubyripper-0.5.7$ 

Otherwise I've posted a 0.6 beta deb in post 86, it's good for any ubuntu release 8.04 thru 10.04

 ( doesn't install encoders, if used install them yourself, after install you can search rubyripper in synaptic, right click on the package and the  install recommends and suggests will show you what's installed (greyed out) and what's not

---

### Post by ljrmorgan on 2009-12-19
> **duralex69 said:**
> Hi,

I've just installed Rubyripper with Ubuntu 9.04 (because I couldn't handle with parametering bitrate in Sound Juicer).

It looks like good but I would have three more questions :
1) how do you parameter the bitrate for MP3 (the test with VLC I did renders me a file at 128 kb/s and in Nautilus it's 51 kbps !!!) Personnaly, I would like to rip at 160 kbps.
2) what is "cuesheet" and is it important ?
3) is it important to parameter "Cdrom offset" because I didn't find how to.

I'm very sorry for my poor english I hope you can manage with it (you know I'm french !!!).

Thanks for your answers...

Best Regards

Alex

Not sure about 2 & 3, but I think I've managed 1!

OK, so, by default LAME encodes at a constant bitrate, but rubyripper passes in the '-V 3' parameter, which sets it to a variable bitrate (the '3' is to do with the quality). If you delete the '-V 3' part and replace it with '-b 160' then that will encode at a constant bitrate of 160kbps. Try typing 'man lame' into a terminal, that'll give you all the options you can pass in.

That seems to work for me :-)

---

### Post by nomnex on 2009-12-19
@[duralex69]("http://ubuntuforums.org/member.php?u=448229") (Post #83)

command

```
man lame
```or here [URL="http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE"]http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE
[/URL] 
Personal note: I would rather chose 192 VBR than 160 CBR. File sizes will be quite similar but the former will give a better sound quality.

You can rip track by track - 1 track = 1 file, or as a single file + CUE sheet (text file with the album, track, track duration, etc. information)

Single file + CUE is the best audiophile format for archiving music collection. beware Linux players do not (some exceptions) handle CUE sheet yet, at least on GNOME. There is no point ripping with a lossy codec on a single file, but this is me.

The" audiophile" way is: copying the album with a lossless codec (WavPack, Flac, etc) as a single file/CUE - that's the source. Then split the album or songs you like and encode them with lossy codec (.ogg, .mp3, etc) according to need (portable player, car player, etc.).

Here for CDrom-offset
[http://www.exactaudiocopy.de/en/index.php/support/faq/offset-questions/](http://www.exactaudiocopy.de/en/index.php/support/faq/offset-questions/)

There is a link to click on the Rubyripper to click. That brings you here: [http://www.accuraterip.com/driveoffsets.htm](http://www.accuraterip.com/driveoffsets.htm). Just check your cdrom, see the offset setting (+n) and report it in the Rubyripper setting field. If you don't find your CDrom, either the model has not been reported yet, either you don't need to set anything.

---

### Post by booksnmore4you on 2009-12-23
I can't get RubyRipper to read from CDDB, and can't get Juicer to accept MP3 as a profile.  So it's either no MP3 or no CDDB for me.

**Can't anyone make an audio extraction program that just freakin' works?!?!**

---

### Post by mc4man on 2009-12-23
> Can't anyone make an audio extraction program that just freakin' works?!?!

Obviously people have had very little trouble in those regards, - 
for gstreamer mp3 encoding either install the fluendo gstreamer plugin (search gstreamer in synaptic) or 
```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

You haven't said how you got, installed, RR, whether from building, ppa or otherwise. For cddb you need 
```
sudo apt-get install cd-discid
```

---

### Post by booksnmore4you on 2009-12-27
I got juicer working great, and it is amazingly fast, too. Regrettably, RubyRipper still fails to query CDDB, and I had the dependency you mentioned installed all along.  I've installed it from PPA. A plain and current step-by-step to get it going in Karmic would be a nice find!

---

### Post by mc4man on 2009-12-27
> RubyRipper still fails to query CDDB
I've never had an issue there, it you wish maybe try the RR beta I attached to post 86 ( could use updating

If so make sure you remove the ppa package**s** first

Edit:
also maybe delete or rename the config folder in your home dir. 
~/.rubyripper

---

### Post by ucraymond on 2010-01-11
Just a note from an Ubuntu moron...I had trouble getting Rubyripper to rip mp3s.
After following the nice instructions at the HydrogenAudio wiki, I got an error like this

WARNING: Encoding to mp3 exited with an error with track 1!

WARNING: ENCODING ERRORS WERE DETECTED

and no mp3 files were created.

I was running rubyripper 0.5.7 (also tried 0.5.0) with lame 3.9.7 on Ubuntu Hardy Heron.
Part of my trouble was that I was expecting more output in the logfile when I hit the
debug flag in the preferences.  Didn't even realize that what the Rubyripper manual
calls "the console window" I call "the terminal"...

Anyway, once that was sorted I found  I just needed to comment out the following line
in rr_lib.rb:

```
tags += "--tv DISCID=\"#{@settings['cd'].discId}\" "
```and then after reinstalling it worked.  That option doesn't exist in my version of lame.

Maybe this will help someone who is as confused as I was, if any such beings exist.

---

### Post by JSeymour on 2010-01-16
> **mc4man said:**
> Myself, atm am now using abcde, ...I'm currently in the process of choosing ripping and burning applications for creating compilations.  Mind if I ask why you switched to abcde?

Thanks,
Jim

---

### Post by mc4man on 2010-01-16
> Mind if I ask why you switched to abcde?

 Based on that  for various reasons lately I'm encoding to aac using neroAacEnc and atomicparsley for tags.

abcde does a slightly better job (and I mean slightly), more related to how and where the files  are saved than the quality of the encodes/ tagging which  is about the same.

---

### Post by JSeymour on 2010-01-16
> **mc4man said:**
> Based on that  for various reasons lately I'm encoding to aac using neroAacEnc and atomicparsley for tags.I want to rip to .wav and create CD compilations from those .wav files, so I guess this doesn't apply to my needs?

> **mc4man said:**
> abcde does a slightly better job (and I mean slightly), more related to how and where the files  are saved than the quality of the encodes/ tagging which  is about the same.RR's big claim to fame appears to be its "secure ripping," which most seem to agree RR does better (read: More thoroughly) than any of the others?

Thanks,
Jim

---

### Post by ace214 on 2010-02-05
For some reason, I can't get Andreas Heck's package to work if the CD is not in the FreeDb. It asks me if I want to change the settings and then the program simply exits. Am I doing something stupid?

:~$ rrip_cli -v
Verbose output specified.
Use config file ~/.rubyripper/settings
Audio-disc found, number of tracks : 17, total playlength : 77:30
Fetching freedb info...
No match in Freedb database. Default values are used.
Do you want to change your settings? (y/n) :  [y] n
:~$

I'm using Lucid. Also, the GUI never successfully detects the CD, even though CLI version does.

ADD: I think my problem is this: [http://code.google.com/p/rubyripper/issues/detail?id=357](http://code.google.com/p/rubyripper/issues/detail?id=357)

Guess I'll go back to EAC...

---

### Post by brewmeister on 2010-02-24
Followed instructions, installed (older version) and it don't work. 

The frustrating part is it used to work.

Scans drive, reads cd all with no problem.

When I click rip cd now button, nothing happens. absolutely nothing. 

As I said it used to work. probably about 5 or 6 ubuntu upgrades ago. I haven't ripped a cd for a couple of months and made recommended upgrades. This includes 0.5.7.

When I wanted to rip a cd, the above happened. I uninstalled 5.7 went down to 5.5 still no luck 

I am using 9.10.

I'm fairly new to the ubuntu/linux world. When rubyripper worked it was great, just finished uninstalling the program. 

I do have wine installed, and will probably go with EAC as I that works. 

Any suggestions as to why the program will not rip my cds?? 

Thanks

---

### Post by mc4man on 2010-02-24
@ brewmeister
not sure what you're issue is, rr works fine here on karmic - just installed on a test 64 bit install. (is currently not working as a gui in lucid.

Maybe go into you're home folder and delete the .rubyripper folder (hidden.

If you wish I have a 0.6b all deb on page 9 # 86 (just used it here on the 64 bit tester

If so make sure you fully remove your existing one first (and the .rubyripper folder
Best way is to right click on the attachment -> 'save link as'

> ...to work if the CD is not in the FreeDb

No problem here with that (on karmic
using a test disk with no cddb info possible, see screen

---

### Post by mahavishnu on 2010-03-08
> **ucraymond said:**
> Just a note from an Ubuntu moron...I had trouble getting Rubyripper to rip mp3s.
After following the nice instructions at the HydrogenAudio wiki, I got an error like this

WARNING: Encoding to mp3 exited with an error with track 1!

WARNING: ENCODING ERRORS WERE DETECTED

and no mp3 files were created.

I was running rubyripper 0.5.7 (also tried 0.5.0) with lame 3.9.7 on Ubuntu Hardy Heron.
Part of my trouble was that I was expecting more output in the logfile when I hit the
debug flag in the preferences.  Didn't even realize that what the Rubyripper manual
calls "the console window" I call "the terminal"...

Anyway, once that was sorted I found  I just needed to comment out the following line
in rr_lib.rb:

```
tags += "--tv DISCID=\"#{@settings['cd'].discId}\" "
```and then after reinstalling it worked.  That option doesn't exist in my version of lame.

Maybe this will help someone who is as confused as I was, if any such beings exist.

Many, many thanks dude !!
works like a charm here.;)

---

### Post by mc4man on 2010-03-10
Just to note that RR is now working fine in lucid (using the 0.6b I posted in post 86
Too bad they don't allow .debs to be attached any more or I'd update it..

Edit:
well the gui now works, settings can be made, tracks are ripped but no encoding from gui.
The cli works fine, and if desired using the -a from cli will use the setting made in gui.
(so almost fully functional

---

### Post by mahavishnu on 2010-03-13
> **Joe said:**
> Anyone else have a problem with the most recent version (0.5.4) stopping before ripping the last track of the cd?

Here using Rubyripper 0.5.7 with Hardy and with a driver offset of +667 I **can't rip and encode the last track** of any CD. 

Maybe it's a cdparanoia bug.

Googled and can't find any help for this. :confused:

If I set the driver offset to **0** the last track is ripped ok, but I think it's quite nonsense using Rubyripper with no driver offset correction.

---

### Post by mc4man on 2010-03-13
> I can't rip and encode the last track of any CD. 

While i'm on karmic atm, haven't had any issues with last track and cdrom offset
Assuming you've set the offset to the proper confirmed one for your drive maybe try an 0.6X version.

I have a 0.6b deb attached in post 86 (p. 9), it's about a month old (debs are no longer allowed so won't update), it will install on hardy thru lucid, if so, please read edit

Or if more suitable just grab the latest git 
```
git clone git://github.com/rubyripperdev/rubyripper.git
```

While I haven't used in months maybe I'll try on my hardy install later...

---

### Post by mahavishnu on 2010-03-14
**mc4man**, could install version 0.6 with Hardy.

But now I couldn't encode any track.
All I get is the message: 

[B]
"WARNING: Encoding to mp3 exited with an error with track 1!"[/B]

and so on with every track till the end of a CD...

I revised the Lame parameters, clean up my home directory, changed the Number of extra encoding threads from 0 to 4... nothing worked here..

---

### Post by mc4man on 2010-03-14
> But now I couldn't encode any track.
Just booted to a stock hardy and it appears RR doesn't like the version of lame hardy has. (could be the parameters

Anyway no reason not to use a more current version which will work fine. 
Go here and get the .deb for your install (i386 or amd_64

[http://packages.ubuntu.com/karmic/lame](http://packages.ubuntu.com/karmic/lame)

Just click thru and let gdebi install

Then RR will work fine (make sure id3v2 is installed for tags) see screen

(if you installed from the .deb, then search in synaptic, highlight rubyripper, right click will expose suggested and recommended you may also want if not already

---

### Post by mc4man on 2010-03-14
It also seems that RR doesn't get a menu icon in hardy ( at least from the 0.6 deb.

If not and wanted quite simple
From terminal
```
alacarte
```

Go down to Sound & Video and then on r. side right click on rubyripper -> properties.

Click on the icon box -> then hit 'browse' button

Navigate to /usr/share/icons/hicolor/128x128/apps
The box will stay empty, just hit the 'open' button and you'll be returned to orig. screen where the icon will be seen to choose.

A few screens show what I mean

---

### Post by mahavishnu on 2010-03-14
> **mc4man said:**
> Just booted to a stock hardy and it appears RR doesn't like the version of lame hardy has. (could be the parameters

Anyway no reason not to use a more current version which will work fine. 
Go here and get the .deb for your install (i386 or amd_64

[http://packages.ubuntu.com/karmic/lame](http://packages.ubuntu.com/karmic/lame)

Just click thru and let gdebi install

Then RR will work fine (make sure id3v2 is installed for tags) see screen

(if you installed from the .deb, then search in synaptic, highlight rubyripper, right click will expose suggested and recommended you may also want if not already

Can't manage to satisfy all the libraries Lame 3.98 need in Hardy.

Keep with 3.97 and once again managed to solve my problem editing *rr_lib.rb* and comenting *tags += "--tv DISCID=\"#{@settings['cd'].discId}\" "*

Now I can use 0.6b with Hardy and offset parameter wwhat rips and encode all the tracks.

The icon is set with restarting the system.

Thanks for all your help and sorry about my bad english.

---

### Post by mc4man on 2010-03-14
> Can't manage to satisfy all the libraries Lame 3.98 need in Hardy.

sorry about that - I used to have 2 hardy installs, one heavily modded and one I remembered as being stock. I've replaced my main one with lucid and it turns out the 'stock' one isn't exactly so.

Taking a look in synaptic it turns out I created 'dummy' liblame0 and -dev packages, then installed the newer libmp3lame ones ( both liblame0 and libmp3lame0 provide the same thing - libmp3lame - hardy got stuck behind a name change...
glad you got it sorted.

---

### Post by ron999 on 2010-04-22
Hi
Can somebody help me to use neroAacEnc with RubyRipper.

I know that RubyRipper works OK when ripping to WAV, FLAC and mp3.
And I know that neroAacEnc works OK from the command line.
But I can't figure out how to work them together.

I've looked back through this thread, and several others.
Just now I've got this entered in my 'Other' window:-
**neroAacEnc -q 0.65  -if %i -of "%o.m4a"**
And I've got the 'Other' box ticked.

When I run the rip it does the trial #1 and trial #2 then it analyzes then it crashes. The GUI just disappears.
I've noticed that it has created a 'other' folder which contains a wav file and a 'ripping.log file'.
I've attached a copy of my 'settings' file and the 'ripping.log'.

So, is there something else I need to do?

I have
Ubuntu 9.10 32 bit Karmic
rubyripper 0.5.7-1 from getdeb
neroAacEnc v1.5.4.0

---

### Post by mc4man on 2010-04-22
Hey ron - Do you want tagging or just plain rip and encode with neroAacEnc

(for tagging a little bit of explanation - otherwise try this

Make sure neroAacEnc is in /usr/bin and executable 

Removing the tagging stuff from my line it looks like this

```
neroAacEnc -q 0.65 -if %i -of "%o".m4a 
```

abcde also works well if set up to use neroAacEnc and the tagging is a hair easier...

---

### Post by ron999 on 2010-04-22
Hi mc4man
I'm glad you replied.
neroAacEnc is in usr/bin folder and it is executable.
I've changed the settings to 
neroAacEnc -q 0.65 -if %i -of "%o".m4a
But it's crashed again.
I've attached the very latest settings and ripping log files.

---

### Post by mc4man on 2010-04-22
Don't see any issue w/ your logs - does rr crash when doing a different codec?

(actually the nero command is the same in both your posted logs ("%o"

reset my pref.'s to match your's (for the most part), and have no trouble
> preEmphasis=cue
req_matches_all=2
minLengthHiddenTrack=2
naming_various=%f/%a (%y) %b/%n - %va - %t
vorbissettings=-q 4
flacsettings=--best -V
cd=#<Disc:0xb759a850>
freedb=true
naming_normal=%f/%a (%y) %b/%n - %t
max_tries=5
wav=false
tracksToRip=2
pregaps=prepend
gain=album
req_matches_errors=2
noCapitals=false
editor=gedit
username=anonymous
verbose=false
noSpaces=false
maxThreads=0
mp3=false
gainTagsOnly=false
normalize=replaygain
first_hit=true
cdrom=/dev/cdrom
create_cue=false
site=http://freedb2.org:80/~cddb/cddb.cgi
playlist=true
other=true
no_log=false
filemanager=nautilus --no-desktop
hostname=my_secret.com
ripHiddenAudio=false
eject=true
debug=true
naming_image=%f/%a (%y) %b/%a - %b (%y)
basedir=~/
othersettings=neroAacEnc -q 0.65 -if %i -of "%o".m4a 
mp3settings= --id3v2-only
image=false
rippersettings=
offset=6
vorbis=false
flac=false

Things I'd try
delete .rubyripper and re-setup
use the other box for something you know should work (put a flac or mp3 command in it) just to eliminate that - saving to other.

If you wish on page 9 (post 86) I attached a more recent rr - if so remove current one and the .rubyripper folder, then install - it's an all.deb

---

### Post by ron999 on 2010-04-22
Hi mc4man
I changed the 'other' command to **lame i% o%.mp3** - AND IT CRASHED!:):)

So I've uninstalled it and installed your deb.
This time it's working fine with command **neroAacEnc -q 0.65 -if %i -of "%o".m4a**
:guitar::guitar:

There must be something wrong with the v0.5.7-1 that I downloaded from getdeb.
But the fault won't show unless people use a 'other' codec.

I've changed the command now to yours from post #35.
```
neroAacEnc -q 0.65  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a

```
But MediaInfo shows no tags. Should I use a different command instead?

> General
Complete name                    : /home/ron/other/Various (1995) Usa Music Tour/10 - Patsy Kline - Crazy.m4a
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 4.64 MiB
Duration                         : 2mn 43s
Overall bit rate                 : 238 Kbps
Encoded date                     : UTC 2010-04-22 23:26:55
Tagged date                      : UTC 2010-04-22 23:27:15
Writing application              : Nero AAC codec / 1.5.4.0
cdec                             : ndaudio 1.5.4.0 / -q 0.65

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 2mn 43s
Bit rate mode                    : Variable
Bit rate                         : 236 Kbps
Maximum bit rate                 : 270 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 4.61 MiB (99%)
Encoded date                     : UTC 2010-04-22 23:26:55
Tagged date                      : UTC 2010-04-22 23:27:15






---

### Post by mc4man on 2010-04-22
The tagging is a little bit of an issue with rr, works perfectly with a patched abcde.

(I'll have to go read post 35 - the command is shy.

Anyway for tagging I use atomicparsley

The problem that has come up in rr /atomicparsley is it will not write a .m4a ext.
( it will write to any other ext., I'm sure there is a solution but haven't bothered since abcde works with nero/atomicparsley just fine.

So 2 things come up - 
first the tracks are tagged and written to ~/tmp/m4a/<whatever>, you need to move back to ~/other/<whatever>

second I've told ap to output as .aac, the tracks aren't .aac so I do a batch rename to .m4a
(many players care less about the .aac ext., some do (vlc

I really think these things can be worked out

Side note - atomicparsley will not write genre tags properly in either rr or abcde - it's  either they need to be input as a binary and aren't or they are and ap doesn't recognize a binary for genre..?

(i guess one could always tag later - for myself ap does fine

So here is the nero encoding line for rr (quite long

```
neroAacEnc -q 0.65 -if %i -of "%o".m4a && mkdir -p /home/doug/tmp/m4a/%a\ \(%y\)\ %b && AtomicParsley "%o".m4a -o /home/doug/tmp/m4a/%a\ \(%y\)\ %b/%n\ -\ %t.aac --artist "%a" --album "%b" --tracknum "%n" --year "%y" --title "%t"  --genre "%g" && rm "%o".m4a
```

Obviously change /home/doug/ to you (2 places) - the .aac in question  is here (should be .m4a

> -o /home/doug/tmp/m4a/%a\ \(%y\)\ %b/%n\ -\ %t.aac


Edit: if you use rr/ap, and want to rename the ext ( unless you can figure this out) a batch comm. - cd to dir. with tracks

```
for f in *.aac; do mv "$f" "${f%.aac}.m4a"; done;
```

*regarding #35 - maybe I got tagging, more likely I posted in a command from a file where I was working on the nero part. - 18 months seems like forever at this point as far as remembering what I was doing

---

### Post by ron999 on 2010-04-22
Hi mc4man

I tried your command. The tags are OK.:)

As you said, the ripped tracks now have an aac suffix and they are in a tmp folder.:confused:

Thanks for your effort, but I'm going back to the original command without tags.8-)

The main problem was getting the 'other' codec command to work, and now that's fine with v0.6b.2.

Consider it [SIZE="5"]**[SOLVED]**[/SIZE]

> General
Complete name                    : /home/ron/tmp/m4a/Various (1995) Usa Music Tour/03 - Love Is A Battlefield.aac
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 7.32 MiB
Duration                         : 4mn 6s
Overall bit rate                 : 249 Kbps
Album                            : Usa Music Tour
Track name                       : Love Is A Battlefield
Track name/Position              : 3
Track name/Total                 : 0
Performer                        : Various
Genre                            : Rock/Pop
Encoded date                     : 1995
Tagged date                      : UTC 2010-04-23 00:04:43
Writing application              : Nero AAC codec / 1.5.4.0
cdec                             : ndaudio 1.5.4.0 / -q 0.65

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 4mn 6s
Bit rate mode                    : Variable
Bit rate                         : 247 Kbps
Maximum bit rate                 : 274 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 7.27 MiB (99%)
Encoded date                     : UTC 2010-04-23 00:03:29
Tagged date                      : UTC 2010-04-23 00:04:43



---

### Post by mc4man on 2010-04-22
Glad you got it squared away
Interesting you did get genre ok, will have to ck. that, am on lucid now

( the having to move the files back was 1 reason I went to abcde, though there probably is a solution.

If you ever want to try abcde w/nero & ap let me know

I made it into an all.deb - I always use a local repo in my installs so having stuff I do or redo as .debs (debian) makes it quite easy for re-installs and new installs

unfortunately I can no longer attach .debs here, though for abcde I could attach the patched abcde script and sample config

---

### Post by ghindo on 2010-04-23
Is Abcde still being actively developed?  I checked the website and it seems like there haven't been any updates in a while.  Although, I suppose it's been close to a year since Rubyripper has been updated :/

Anyway, I've updated the OP with simpler install instructions using aheck's PPA.  I've been meaning to write up a how-to on how to actually *use* Rubyripper as well, but I haven't gotten around to it yet.

---

### Post by mc4man on 2010-04-25
> Is Abcde still being actively developed?
Well that would depend on definition of 'actively'

There have been some updates this year and probably will be some from time to time -- version is now 2.4.2 (r 290

(the only real advantage I realize with abcde is if ripping/encoding w/ nero and tags as mentioned 

As far as RR I see some advantages to using the 0.6 version as noted in post 86

---

### Post by fatboab on 2010-05-05
I tried installing this from the ppa and while it appeared to work, I couldn't find the app to run it, I'm on Kubuntu if that makes any difference. I had ruby 1.8 installed, but it took a ridiculous amount of time to rip a cd, then I found there might be an issue with this version of ruby. So I installed ruby1.9.1, and running the cli script it doesn't rip anything, it just creates the folder, .cue  and .m3u files and then exits. This is the log:

```
This log is created by Rubyripper, version 0.5.7
Website: http://code.google.com/p/rubyripper

Cdrom player used to rip:
HL-DT-ST DVDRAM GSA-4083N 1.08
Cdrom offset used: 0

Ripper used: cdparanoia --never-skip=40
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-flac     -> -5 -V (flac 1.2.1)

CDDB INFO

Artist    = Balance
Album    = 016 - Agoria (Disk 1)
Year    = 2010
Genre    = Tech House, Minimal
Tracks    = 25

01 - Gregg Kowalsky - Ashes From Evermore
02 - Alva Noto - Xerrox Monophaser 2 / DJ Koze - Lords Of Panama
03 - Mark Pitchard - ?
04 - Manvoy de Saint Sadrill - Soeheniona
05 - Tisca - Joe Si Ha
06 - Emiliana Torrini - Gun
07 - Agoria - Parasite 2
08 - Arandel - In D#5
09 - Messina - Columpnam
10 - 19.454.18.5.25.5.18 - When I Think Of
11 - Pom Pom - IO
12 - Agoria - Altre Voci
13 - Glimpse - Train In Austria Part 2
14 - The Field  - Over The Ice (Live Mix)
15 - Olibusta - La Pazz
16 - Cubenx - Mis Dias Y Tus Noches
17 - Felix Laband - Whistling In Tongues (Todd Terje Remix)
18 - Jozif - Back 2 My Roots (Jozif's 5 O'Clock Fabric Shadow Edit)
19 - Bibio - Jealous of roses
20 - LCD Soundsystem  - 45:33 (Trus'me Remix)
21 - Bozoo Bajou feat Rumer - Same Sun (Prins Thomas Diskomiks) / Oxia - Less Time
22 - Hatikvah - Synchronicty (Block Barley & Engin Ozturk Holmby Hills Remix)
23 - Rio en Medio - The Last Child's Tear
24 - Tipper - Just As The Sun Went Down
25 - Gregg Kowlasky - Ashes From Evermore / Alva Noto - Xerrox Monophaser 2

STATUS


```It looks like others have it running under ruby1.9.1, what am I missing...?

Cheers,

---

### Post by Captain_Falafel on 2010-05-08
> **fatboab said:**
> I tried installing this from the ppa and while it appeared to work, I couldn't find the app to run it, I'm on Kubuntu if that makes any difference. I had ruby 1.8 installed, but it took a ridiculous amount of time to rip a cd, then I found there might be an issue with this version of ruby. So I installed ruby1.9.1, and running the cli script it doesn't rip anything, it just creates the folder, .cue  and .m3u files and then exits. This is the log:
It looks like others have it running under ruby1.9.1, what am I missing...?

Cheers,

I did the same thing, and I can't find the application anywhere :S

---

### Post by mc4man on 2010-05-08
I guess a few points may be useful

First rr isn't 'built', it's just some ruby scripts so a .deb package just installs it, creates a menu item for the gui (if installed), and depending on the deb may install some dependencies if missing.

You can actually just run it from the downloaded dir.

As far as the ppa mentioned - the ppa has split rr into 2 packages - the cli version (rubyripper) and the gui (rubyripper-gtk)
To 'see' rr you need to install rubyripper-gtk.

The gui works fine in any ubuntu release prior to lucid, in lucid it will hang for quite awhile between tracks, running rr from the cli in lucid works fine.

I see no advantage to using ruby1.9.1 for rr in lucid - it is no faster that the default 1.8 (at least here.

The gui is only available with libgtk2-ruby installed

The gui can be put to use in lucid, you can set up rr's config, encoding parameters, encoders to use, ect. 
Then just rip from cli, either manually or as an 'autorip' function

This post describes setting up 'autorip' and has a 0.6 beta attached, if trying please read note (deb includes both the cli and gui versions (#86

[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

---

### Post by Captain_Falafel on 2010-05-09
> **mc4man said:**
> I guess a few points may be useful

First rr isn't 'built', it's just some ruby scripts so a .deb package just installs it, creates a menu item for the gui (if installed), and depending on the deb may install some dependencies if missing.

You can actually just run it from the downloaded dir.

As far as the ppa mentioned - the ppa has split rr into 2 packages - the cli version (rubyripper) and the gui (rubyripper-gtk)
To 'see' rr you need to install rubyripper-gtk.

The gui works fine in any ubuntu release prior to lucid, in lucid it will hang for quite awhile between tracks, running rr from the cli in lucid works fine.

I see no advantage to using ruby1.9.1 for rr in lucid - it is no faster that the default 1.8 (at least here.

The gui is only available with libgtk2-ruby installed

The gui can be put to use in lucid, you can set up rr's config, encoding parameters, encoders to use, ect. 
Then just rip from cli, either manually or as an 'autorip' function

This post describes setting up 'autorip' and has a 0.6 beta attached, if trying please read note (deb includes both the cli and gui versions (#86

[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

Thank you! I installed libgtk2-ruby and the gtk version of rr came up, but like you said, it was very slow. So I'll just use the cli version while having the configuration set up in rr gtk

---

### Post by schily on 2010-05-16
Let me give some information on cdparanoia vs. cdda2wav.
Cdparanoia started as a patch on an old version of 
cdda2wav but never updated the version of cdda2wav.

As a result, cdparanoia does not include the new and much
better extraction techniques used by recent cdda2wav 
versions. Development of cdparanoia stopped in 2001
and after that, cdda2wav added the relevant paranioa
code that was developed by Monty as a real benefit.

The big other advantage of the code (including the 
paranoia code) in cdda2wav is that it is portable 
while cdparanoia is still Linux only.

A recent cdda2wav gives you the advantaged from cdparanoia
and the advantages of recent development in cdda2wav, so
cdda2wav is currently the best solution foe CD ripping.

[ftp://ftp.berlios.de/oub/cdrecord/alpha/](ftp://ftp.berlios.de/oub/cdrecord/alpha/)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)

---

### Post by ghindo on 2010-05-17
> **schily said:**
> Let me give some information on cdparanoia vs. cdda2wav.
Cdparanoia started as a patch on an old version of 
cdda2wav but never updated the version of cdda2wav.

As a result, cdparanoia does not include the new and much
better extraction techniques used by recent cdda2wav 
versions. Development of cdparanoia stopped in 2001
and after that, cdda2wav added the relevant paranioa
code that was developed by Monty as a real benefit.

The big other advantage of the code (including the 
paranoia code) in cdda2wav is that it is portable 
while cdparanoia is still Linux only.

A recent cdda2wav gives you the advantaged from cdparanoia
and the advantages of recent development in cdda2wav, so
cdda2wav is currently the best solution foe CD ripping.

[ftp://ftp.berlios.de/oub/cdrecord/alpha/](ftp://ftp.berlios.de/oub/cdrecord/alpha/)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)I'm not sure all the information you gave is entirely accurate.  According to the [cdparanoia page]("http://www.xiph.org/paranoia/"), its latest release was in 2008, not 2001.  And I'm not sure why you say it's Linux-only software; because it's open source, it can be ([and has been]("http://wiki.hydrogenaudio.org/index.php?title=Cdparanoia")) ported to other platforms.

What specific advantages does cdda2wav offer over cdparanoia?  Your post was a bit vague.

---

### Post by ghindo on 2010-05-25
[Rubyripper developer expects 0.6 release in June]("http://groups.google.com/group/rubyripper-release/msg/947ef8f267aa61a7"):> Dear all, 
It has been a while. Between the jobs I've fixed most of the known 
bugs that were opened and closed some feature requests as well. Since 
the previous release is about 1 year ago, it seems like a new release 
is most welcome. This comes with ruby-1.9 support as well. 
Dear translators, please update your language files. As tradition 
tells, I've opened up an issue for this. In this issue you'll find an 
archive of today's git version: 
[http://code.google.com/p/rubyripper/issues/detail?id=420](http://code.google.com/p/rubyripper/issues/detail?id=420) 
Dear testers and package maintainers, please stress test the upcoming 
release a bit, so ugly surprises won't be part of the future ;) If 
needed you can use the archive for the translators. 
A release is expected in june. If all goes well, early june. 
With most kind regards, 
Bouke Woudstra 
Rubyripper developer

---

### Post by freddybob on 2010-05-25
I installed Rubyripper last year following the Hydrogen Audio instructions ([http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu)).

How do I uninstall?  It does not show up in Synaptic or Ubuntu Software Centre.

---

### Post by ghindo on 2010-05-25
> **freddybob said:**
> I installed Rubyripper last year following the Hydrogen Audio instructions ([http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu)).

How do I uninstall?  It does not show up in Synapticor Ubuntu Software Centre.The instructions on the Hydrogen Audio wiki show you how to compile from source.  To uninstall, you have to download a Rubyripper tarball, extract it, and run ```
sudo make uninstall
```

---

### Post by freddybob on 2010-05-25
> **ghindo said:**
> The instructions on the Hydrogen Audio wiki show you how to compile from source.  To uninstall, you have to download a Rubyripper tarball, extract it, and run ```
sudo make uninstall
```

That was easy.  :)  Thanks.

---

### Post by braddjwinter on 2010-05-28
Has the repository moved?

I followed these instructions, but "locate rubyripper" returns nothing.

When I try installing again, I get this:

brad@brad-desktop:~$ sudo apt-get install rubyripper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rubyripper is already the newest version.


Using Ubuntu 9.10

---

### Post by mc4man on 2010-05-28
> ..................
Reading state information... Done
rubyripper is already the newest version.


If you are using the ppa then rr is 2 separate packages

rubyripper = cli version, command of rrip_cli (or add. cli options

rubyripper-gtk = gui, should be in your applicationns menu or launch command of rrip_gui

so search in synaptic for rubyripper and install the gtk  package (or maybe sudo apt-get install rubyripper-gtk (never have used ppa

---

### Post by braddjwinter on 2010-05-28
> **mc4man said:**
>  maybe sudo apt-get install rubyripper-gtk 

it worked. Thanks :)

---

### Post by schily on 2010-05-29
> **ghindo said:**
> I'm not sure all the information you gave is entirely accurate.  According to the [cdparanoia page]("http://www.xiph.org/paranoia/"), its latest release was in 2008, not 2001.  And I'm not sure why you say it's Linux-only software; because it's open source, it can be ([and has been]("http://wiki.hydrogenaudio.org/index.php?title=Cdparanoia")) ported to other platforms.

What specific advantages does cdda2wav offer over cdparanoia?  Your post was a bit vague.

Well, my information of course is correct. There was no new code or features added to cdparanoia recently. Monty of course added a lot of comment to the code as an ovious result to the fact hat he now seems to have problems to understand his old code.

Cdparanoia fails entirely with many recent media because it is based on an extremely old version of cdda2wav. Cdda2wav has no problems with these media and cdda2wav is able to extract all meta data that is completely ignored by cdparanoia. If you like to create a 1:1 copy from a music CD, cdrecord needs this meta data.

In any case, the wonderful code that made cdparanoia unique survives in cdda2wav which is an actively maintained project that published 80 new releases since September 2004.

---

### Post by jeggerleg on 2010-06-11
[QUOTE=ghindo;4993055][center]**[SIZE="5"][COLOR="Red"]HOWTO:  Install Rubyripper on Ubuntu[/COLOR][/SIZE]**[/center]

[SIZE="1"]*Note:  These instructions are aimed at Ubuntu 10.04 and above.  Results on other Ubuntu releases may vary.*[/SIZE]

**[SIZE="3"]What is Rubyripper?[/SIZE]**
From the _[HydrogenAudio wiki](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)_:


**[SIZE="3"]How is Rubyripper different from other CD rippers?[/SIZE]**
Rubyripper differs from programs like K3b and Sound Juicer because it is **much** more thorough.  Rubyripper rips each audio track at least twice, then compares each rip for differences and attempts to make the most accurate compilation of rips it possibly can.  The result?  Higher quality, *accurate* CD rips.

**[SIZE="3"]Installation[/SIZE]**
Unfortunately, Rubyripper isn't yet available in the official Ubuntu repositories.  Fortunately, there's a personal package archive (PPA) available which makes installation easy!  No more compiling from source! :)

[LIST=1]
[*]First, open up the terminal.  You can do this by looking in the Applications menu, under Accessories.
[*]Next, copy the following text into the terminal and hit enter:```
sudo add-apt-repository ppa:aheck/ppa
```This should prompt you for your password.
[*]Then, run the following command:```
sudo apt-get update
```
[*]Finally, enter```
sudo apt-get install rubyripper
```
[/LIST]

And that's it!  Rubyripper should now be in the applications Applications menu under Sound & Video. :)

Done all that:

"couldn't find package rubyripper"

---

### Post by mc4man on 2010-06-11
see post 148 or to get to the point 
```
sudo apt-get install rubyripper-gtk
```

(starting in lucid there are 'time' issues with the gui - can be resolved by a couple of methods - none ideal

---

### Post by Rodney9 on 2010-06-12
Thank You.

---

### Post by sarvodaya on 2010-06-18
Thank you!

I've finally just dumped windoze xp from my dual boot, and was looking  for an eac replacement. Once I'd discovered RubyRipper it only took a  couple of seconds to find this guide. Good job, it's very simple and  really n00b-friendly. PPA's a nice touch.

Keep up the good work!

---

### Post by ghindo on 2010-06-18
> **Rodney9 said:**
> Thank You.
> **sarvodaya said:**
> Thank you!

I've finally just dumped windoze xp from my dual boot, and was looking  for an eac replacement. Once I'd discovered RubyRipper it only took a  couple of seconds to find this guide. Good job, it's very simple and  really n00b-friendly. PPA's a nice touch.

Keep up the good work!Hey, no problem!  Glad y'all found it helpful! :)

---

### Post by HotshotGG on 2010-06-20
Hello. Ghindo I just wanted to thank you for this invaluable thread you have here. I am a long time Hydrogenaudio member and the person who edited and cowrote the wiki page for Rubyripper with the leader developer Mr. Woudstra. I figured it could be a collaborative effort if you wanted me to include anything in the wiki page that you feel is missing or that members are having problems with!. I have done my best to incorporate everything about the software when I first helped write the page. I also know how to code a little a few language (Ruby is not one of them, but I would be willing to learn!). I just started using Lucid Lynx about a month ago. Great Operating System. I look forward to being a big contributer to the Ubuntu forums in the future and figured I would start here. Look forward to helping out new Ubuntu users get acquainted with the software. Take care! ):P

> (starting in lucid there are 'time' issues with the gui - can be  resolved by a couple of methods - none ideal  

I noticed that as well.  It takes a much longer time to generate an MD5 hash as well.

---

### Post by ghindo on 2010-06-25
Hey, thanks HotShot!  Your wiki page has always been a great resource, hope you like it here around the forums :)

By the by, Rubyripper 0.6.0 has been released!  Here's the changelog:```
---------0.6.0 RELEASE------
* many ruby-1.9 fixes
* get advanced toc scanning with help of cdrdao
* support for hidden tracks before track 1
* optionally set how many seconds a hidden track at least must be
* optionally not rip sectors before track 1 (prevent crashes for some drives)
* option to either append / prepend pregaps
* option for pre-emphasis handling
* fix rips with discs that start with a data track once again
* all new options result in a correct cuesheet (like EAC)
* fix the --all CLI option and rename it to --defaults
* improved aborting a rip
* better show intention of "overwrite" dir by renaming it
* better detection of various artist discs
* cooldown the drive for two minutes after 30 minutes non-stop ripping
* better handling of incomplete rips of last track due to offsets
* added detection of free disk space
* force a unique output directory in the gtk2 gui
* fix some exotic lame tags
* poll for the drive for some seconds to detect a disc
* more easy visual sign when some erors were not recovered
* move to freedesktop.org standard directories to store files (auto migration)
* automatically filter out illegal FAT32 characters in filenames
* better implementation of encoding threads, fixes multiple encodings
* show the amount of seconds for each trial to rip
* new Italian translation
* update of many translations
* and many other small fixes
```

---

### Post by spiral the dog on 2010-07-21
Hi try to install rubyripper followed the code but after first line it comes up with
add-apt-repository: command not found
then if i put in the next line its says

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

what should i do next 

when i put the last line it says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rubyripper-gtk

should i run sudo apt-cdrom then what?

help!  
oh running on 9.04

---

### Post by HotshotGG on 2010-08-05
> help!  
oh running on 9.04  

Having installed Rubyripper you might be hard pressed to upgrade your distro! Rubyripper has a lot of dependencies on newer packages that are needed in order to use the program correctly and they need to be installed (with exception of FLAC 1.2.1). Make sure you have ruby-gnome2 installed. That's the frontend library for Rubyripper GUI. That presents folks with a lot of problems!. I recommend you check out the community wiki page. I tested the instructions out before on 9.04 and got the program to run, but that was, because I built it from the source! You might want to consider that as well. 

[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu)

---

### Post by mc4man on 2010-08-05
> Having installed Rubyripper you might be hard pressed to upgrade your distro! 
Not at all - any rubyripper 'build' or .deb will work just fine on hardy thru maverick.

(for instance this .deb I attached quite some time ago [in post # 86 ]("http://ubuntuforums.org/showthread.php?t=799621&page=9")works on any ubuntu release hardy thru maverick

As far as a .deb I'd suggest  the [debian-multimedia all deb]("http://www.debian-multimedia.org/pool/main/r/rubyripper/rubyripper.php") is the most up to date and well constructed.
*it doesn't have cd-discid as a depend - only a suggested, most all users will want to have that installed.

Actually on hardy thru karmic the gui will work fine, on lucid and maverick one has to workaround the poor libruby1.8 version being used.

Dependencies of the debian-multimedia all .deb, note there is nothing version specific (or arch

> Package: rubyripper
Version: 0.6.0-0.0
Architecture: all
Bugs: mailto:marillat@debian.org
Maintainer: Christian Marillat <marillat@debian.org>
Installed-Size: 624
Depends: ruby, cdparanoia, libgtk2-ruby, eject, libgettext-ruby-util
Recommends: normalize-audio, vorbisgain, mp3gain, flac, vorbis-tools
Suggests: lame, cd-discid

---

### Post by Flandry on 2010-10-01
> **mc4man said:**
> Not at all - any rubyripper 'build' or .deb will work just fine on hardy thru maverick.

(for instance this .deb I attached quite some time ago [in post # 86 ]("http://ubuntuforums.org/showthread.php?t=799621&page=9")works on any ubuntu release hardy thru maverick

As far as a .deb I'd suggest  the [debian-multimedia all deb]("http://www.debian-multimedia.org/pool/main/r/rubyripper/rubyripper.php") is the most up to date and well constructed.
*it doesn't have cd-discid as a depend - only a suggested, most all users will want to have that installed.

Actually on hardy thru karmic the gui will work fine, on lucid and maverick one has to workaround the poor libruby1.8 version being used.

Dependencies of the debian-multimedia all .deb, note there is nothing version specific (or arch

Thanks. I just installed the Kubuntu 10.10 release candidate and there's not yet a version in the PPA for it, so i clicked your link and used the deb installer to install RR from the debian-multimedia all deb.

For those who might follow suite, you'll need discid as he mentions:
sudo apt-get install cd-discid

I looked up my CD drive offset (6) by getting the ID from cdparanoia
cdparanoia -vQ
and looking it up in the [accurate rip db](http://www.accuraterip.com/driveoffsets.htm) and added that in the settings, changed the settings to use the musicbrainz cddb, ([http://freedb.musicbrainz.org:80/~cddb/cddb.cgi](http://freedb.musicbrainz.org:80/~cddb/cddb.cgi)) as per [the manual](http://code.google.com/p/rubyripper/wiki/Manual), made a few cosmetic tweaks to the output file naming scheme and enabled replaygain on a per-album basis (which [will add both per-track and per-album normalization metadata](http://code.google.com/p/rubyripper/issues/detail?id=276), a nice touch), and tried to rip.

I also needed to install oggenc and flac to output to those two formats:
sudo apt-get install vorbis-tools
sudo apt-get install flac

At that point, i let it rip... RR is a fantastic little program. It's great to see real native linux options to best-of-breed apps previously found only in Windows.

Unfortunately Ubuntu's slow action to move to Ruby 1.9 means that there's still the long delay between each track, but [this post](http://www.humbug.in/2010/ppa-updates-for-ruby-1-9-1-and-ruby-1-9-2-handling-ruby-versions-using-the-update-alternatives-system/) has me hoping that a 1.9 alternative will be available for 10.10 soon.

---

### Post by mc4man on 2010-10-01
> has me hoping that a 1.9 alternative will be available for 10.10 soon.
That ppa looks interesting though note that there is no updated ruby-gtk2 package which is an absolute must for RR.
( though the maintainer appears to be very approachable - he may provide one if requested.

On my lucid (abandoned) and maverick I've gone ahead and switched the default ruby to 1.9.2 using the maverick repo packages and provided an updated ruby-gtk2 so RR now works from the gui.

Due to the way ubuntu provides ruby ect. (thru dependency packages, ie. ruby-defaults), it's not exactly straightforward, so for the moment the method of using the gui for setup and cli to rip may be the best for most.

---

### Post by fr33think3r on 2010-10-18
> **Flandry said:**
>  has me hoping that a 1.9 alternative will be available for 10.10 soon.

I just updated my ppa with ruby1.9.2 packages for maverick.

Read about it [here]("http://www.humbug.in/2010/ruby-1-9-2-final-build-for-ubuntu-kubuntu-maverick-10-10-uploaded-to-launchpad-ppa/").

I am a KDE user, hence have no need for ruby-gtk. Also ruby-gtk is part of the ruby-gnome package which is a huge package to maintain.

---

### Post by Bazirker on 2010-10-26
Just wanted to drop a quick thanks to the OP!  These directions worked perfectly for me and I'm now ripping away  :)

---

### Post by mc4man on 2010-10-27
> I just updated my ppa with ruby1.9.2 packages for maverick

Works well, very convenient having ruby in update-alternatives

from the gnome side a newer ruby-gtk2 is still needed for the gui, pretty simple to build
(only ruby-gtk2 needs to be built - suggest the 0.19.4 source  - ruby-gtk2-0.19.4.tar.gz  - instead of the newest. - 0.90.4

---

### Post by lingenfr on 2010-12-23
When I update, it tells me iot can't find maverick files in the aheck ppa and then of course it can't find the package to install. Are there instructions for 10.10?

---

### Post by mc4man on 2010-12-24
> **lingenfr said:**
> When I update, it tells me iot can't find maverick files in the aheck ppa and then of course it can't find the package to install. Are there instructions for 10.10?
If you want to use that ppa's packages then open Software Sources - Other, find your entry for it and click edit.
Change the name in the Distribution box to lucid, then click close and reload.
If you wish a newer version then just scroll up to top of this page, post 161, and read carefully, 2 options, pretty straightforward (use the package I posted or the latest from debian multimedia.

( you may also want to note the current issue with running the rip from the gui, better to setup in the gui and then run RR from a terminal when actually ripping.
The solution to returning speed to the gui requires a little work that you may not be interested in atm, though not that hard.

---

### Post by lingenfr on 2010-12-24
> **mc4man said:**
> If you want to use that ppa's packages then open Software Sources - Other, find your entry for it and click edit.
Change the name in the Distribution box to lucid, then click close and reload.
If you wish a newer version then just scroll up to top of this page, post 161, and read carefully, 2 options, pretty straightforward (use the package I posted or the latest from debian multimedia.

( you may also want to note the current issue with running the rip from the gui, better to setup in the gui and then run RR from a terminal when actually ripping.
The solution to returning speed to the gui requires a little work that you may not be interested in atm, though not that hard.

I gave up on the ppa and used the getdeb package. It works, but as you mention, it is 'ridiculously' slow. If it is a matter of configuration to get it speeded up, I am willing. I don't want to compile/replace libraries, etc that are dependencies to other applications. I have never used the command line before. I will take a look into that as well. It is disappointing that RR hasn't been adopted as the ubuntu standard. It is by far the best.

---

### Post by mc4man on 2010-12-24
> but as you mention, it is 'ridiculously' slow.

It does involve installing ruby 1.9.1 or 1.9.2 libraires, changing the default 'ruby' to use them and building/installing a newer version of ruby-gtk.
(the ppa mentioned above takes care of the first part very easily, ruby-gtk has to be done oneself.

What you can do is open the gui, set up your rip, then open a terminal to actually run it. 
I'm not familiar w/ the getdeb build so you'd need to try. The easiest command would be one of these 2 depending on the version of RR
```
rrip_cli -a
```
or
```
rrip_cli -d
```

When started from cli there is no slowdown between tracks

Edit: note the above commands are meant for a full disk rip, what you're doing in the gui is setting encoder(s), and any other 'global' settings.
For a partial rip from cli you'd just run 
rrip_cli 
and follow prompts.

---

### Post by pickarooney on 2011-01-09
I still can't figure out how to run this on Maverick. I've installed all the dependencies and also the DEB from above but the menu entry does nothing and I can't find any binary called rubyripper, ruby-ripper or anything remotely related. How am I supposed to run it exactly?

rrip_gui tells me "The ruby-gtk2 library could not be found" but I've installed libgtk2-ruby which is the only related package available in either the repositories or PPA.

---

### Post by lingenfr on 2011-01-09
I would suggest that you uninstall everything you have installed (rubyripper related) and install JUST rubyripper from getdeb:

[http://www.getdeb.net/updates/Ubuntu/10.10/?q=rubyripper](http://www.getdeb.net/updates/Ubuntu/10.10/?q=rubyripper)

It will take care of any dependencies. On my 32-bit machine it works fine.

Also in the previous post where it references the command line, rrip_cli -a is correct. rrip_cli -d returns an error. I see that additional instructions have been posted, but still looks a bit painful. If this isn't sorted out soon, I suppose I will switch to running EAC under wine and get off the rubyripper merry-go-round. It is unfortunate that rubyripper can't be kept stable and adopted into the mainstream.

---

### Post by NertSkull on 2011-01-24
> **pickarooney said:**
> I still can't figure out how to run this on Maverick. I've installed all the dependencies and also the DEB from above but the menu entry does nothing and I can't find any binary called rubyripper, ruby-ripper or anything remotely related. How am I supposed to run it exactly?

rrip_gui tells me "The ruby-gtk2 library could not be found" but I've installed libgtk2-ruby which is the only related package available in either the repositories or PPA.


I was having the same problem, but now I've "fixed" it.  I've gotten it to open, and even rip songs, but it is EXTREMELY slow.  Because I've never used rubyrip before, I don't know if its always this slow (I've heard cdparanoia slows things down) or if its slow because of something I've done.

This is what I did.  

1) I downloaded the source code from [here]("http://code.google.com/p/rubyripper/downloads/list").  I downloaded the most recent 0.6.0 version.

2) I unzipped the file I downloaded.  I downloaded it into my downloads folder.  Then right clicked on it, extracted here.

3) I opened a terminal and navigated to the folder I just unzipped.  So for me it was ```
cd ~/Downloads/rubyripper-0.6.0
```

4) Just because I'm paranoid and wanted to make sure I'm in the right place.  I listed the files to make sure I saw the "configure" file

```
ls
```

5) Now I made sure I had stuff installed like ruby, and flac so I could rip to flac and ogg (i haven't ripped to mp3 yet)

```
sudo apt-get install libglade2-ruby cd-discid cdparanoia flac lame mp3gain normalize-audio ruby-gnome2 ruby vorbisgain
```

6) Then I configured to file enabling the gui.

```
./configure --enable-lang-all --enable-gtk2 --enable-cli
```

7) Then I ran make

```
make
```

8.) Then I installed by  ------[<--- haha, I had to put a dot after the 8 or it gave me a smiley 8)]

```
sudo make install
```

9) Success.  At this point I had it in the menu.  Or I could run ```
rrip_gui
``` from the command line and it would bring up the program.

NOTES:  

Its really slow for me.  I read in a post above to set the settings in the gui, then run rrip_cli -d and that seems to speed things up a LITTLE.  

But when I run it, it will take 8-10 minutes to do the "Advanced TOC Analysis" and then another 30-40+ minutes to actually rip the disc.  

I haven't played with some of the settings yet though other than to change to Flac as my output.  It appears to make to read each track twice, save it as a wav.  Then combine?? them together or check them against each other?? to make the FLAC file.

I feel like its doing a great job though, and I've compared to other rippers and the audio sounds great.  So all in all I'm happy with it.

Last, I have **[COLOR="Red"]NO IDEA[/COLOR]** if what I did was right, or if it will work for others.  But its working for me, so I hope it will for others.

I'm running ubuntu 10.10 64-bit (I think the 64-bit is what caused some things to not work with other install methods)

---

### Post by Erulisseuiin on 2011-01-28
This is really bumming me out, Maverick has been out for close to 4 months and there is still no consistent way to install and get rubyripper running.  How do we compile the ruby 1.9.2 gnome package (to get the rubyripper gui working smoothly) More importantly where is the package located? 
The hydrogen audio wiki seems to have no information on this. 
Where are our devs? :( We want to use this awesome piece of code! Bring back (easy) Secure Ripping to linux! 

Ok, now that I have that off my chest :P . Honestly Does anyone know how to get ruby ripper **fully** working on Ubuntu 10.10?

---

### Post by mc4man on 2011-01-29
> how to get ruby ripper fully working on Ubuntu 10.10? 
Pretty simple, just set up a new maverick, took about 5 min.'s or so.
Basic method - not a how to though I'll lay it out.

While several ways to provide the proper ruby and ruby-gtk this is  one easy way, - will use a ppa to provide ruby1.9.2  as an alternative and you need to build the gtk lib's
On a fresh install didn't have to remove anything - [COLOR="Blue"]in existing remove existing rubyripper and ruby1.8-dev, libgtk2-ruby1.8,  if installed.
[/COLOR]
Quote boxes below should match up.

Then add this ppa to software sources and update
[COLOR="Blue"]Edit: for natty  - before running update open software sources, click on the 2 ppa entries in Other.., and edit the "Distribution" line to  -  
maverick[/COLOR]
```
sudo add-apt-repository ppa:pratikmsinha/ruby192+bindings 
sudo apt-get update

```
[COLOR="Blue"]
Edit: for 10.04 change git to git-core in below command[/COLOR]
```
sudo apt-get install libruby libruby1.8 \
libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
build-essential checkinstall libgtk2.0-dev git
```

You should see an alternative set at end of install - like this
> ..........
Setting up ruby1.9.2 (1.9.2.z1-1ppa1~maverick) ...
update-alternatives: using /usr/bin/ruby1.9.2 to provide /usr/bin/ruby (ruby) in auto mode.
Setting up ruby1.9.2-dev (1.9.2.z1-1ppa1~maverick) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Then go here and dl ruby-gtk2-0.19.4.tar.gz (last one listed
[http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/](http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/)

create a build folder (I used rubyr) and extract the above to it, then cd to ruby-gtk2-0.19.4
This at the prompt 
```
ruby extconf.rb
```
Should not error, will start out like this
> doug@doug-alienware:~/rubyr$ cd ruby-gtk2-0.19.4
doug@doug-alienware:~/rubyr/ruby-gtk2-0.19.4$ ruby extconf.rb
extconf.rb: Entering directory `glib'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
........
and end like this, check
> extconf.rb: Leaving directory 'gtk'

-----
Target libraries: glib, gdkpixbuf, pango, atk, gtk
-----
Done.
When finished
```
make
```
make should end as such
> SUCCEEDED:  glib gdkpixbuf pango atk gtk
FAILED: NONE
if good then
```
sudo checkinstall --fstrans=no --default --deldoc  && sudo ldconfig
```
After ruby-gtk2 is installed from same prompt

```
cd .. && git clone git://github.com/rubyripperdev/rubyripper.git
```
```
cd rubyripper
```
```
sudo apt-get install cdparanoia eject cd-discid libgettext-ruby-util \
lame flac vorbis-tools [COLOR="Blue"]mp3gain vorbisgain normalize-audio[/COLOR]

```
Blue are quite optional - **if** normalize-audio is installed then run this or rubyripper will not find
```

sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

Then configure and install rubyripper - note that translations will not work w/ the 1.9.2 ruby libs so hopefully english will do

In same terminal at rubyripper prompt
```
./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local

```
If configure looks good then this (Adding a + date, adjust or remove as desired

```
sudo checkinstall --fstrans=no --default --deldoc  --pkgversion 0.6+0129 
```

Ex. configure - red must be same, if not then some persistence will fix
> 
doug@doug-alienware:~/rubyr/rubyripper$ ./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local
ruby-gettext is not found. Translations are disabled!
Checking the NEEDED dependencies....
cdparanoia found...

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
[COLOR="Red"]ruby-gtk2 bindings found[/COLOR]

Testing support for freedb metadata fetching...
cd-discid or discid found...

Testing support for ejecting the disk tray...
eject or disktutil found...

Testing support for different codecs on your system...
flac found...
oggenc (vorbis) found...
lame (mp3) found...

Testing support for replaygain...
wavegain NOT found.
vorbisgain found...
mp3gain found...

Testing support for normalize...
normalize found...
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/local/bin
* Localization files: /usr/local/share/locale
* Icon file: /usr/local/share/icons/hicolor/128x128/apps
* Desktop file: /usr/local/share/applications
* Ruby library: [COLOR="Red"]/usr/local/local/lib/site_ruby/1.9.2[/COLOR]

[COLOR="Red"]Gtk2 frontend will be installed[/COLOR]
Cli frontend will be installed

Note on the ruby alternative - if needing to switch temporarily for something run this, self explanatory

```
sudo update-alternatives --config ruby
```

Edit: it'll most likely take a logout/in to get rr to show up in Applications menu

---

### Post by Erulisseuiin on 2011-01-29
Works like a gem :D I laud your excellence!

---

### Post by meocuchad on 2011-04-05
Can't thank you enough, mc4man! Fired right up and has been ripping like a charm since.

---

### Post by maembe on 2011-04-06
I'm using kubuntu 10.10 and when I try do apt-get update I'm getting a couple error messages among all of the other text.

W:  failed to fetch [http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz) 404 Not Found
W:  failed to fetch [http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz) 404 Not Found
E:  Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

---

### Post by iconoclast hero on 2011-04-18
mc4man, thanks.  that is quite impressive and i'm sure much better than my sloppy hacking around...but here is what i did.  your list looks awfully scary.  the one thing that i really needed was the line about  ln normalize-audio to normalize.
I was able to get away with installing asunder and LAME, installing ruby-gnome2, and everything that was dependent on them.  That took care of almost all the dependences I needed.    Then I saw something that suggested there might be something I didn't have to compile (the first post in this thread) so I wouldn't have to screw with ruby but I got this error...
```
@ruthpc:/# sudo add-apt-repository ppa:aheck/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 3FD5CB5A8A30FE066AF99C96F6FECFF1A5CCD09F
gpg: requesting key A5CCD09F from hkp server keyserver.ubuntu.com
gpg: key A5CCD09F: "Launchpad PPA for Andreas Heck" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```**[Can anyone explain this to me?]**

So when I couldn't get that I went back to ruby reluctantly (i was hoping ruby-gnome2 was like some graphical interface).  From this [very good guide]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Manual_Installation_on_Ubuntu") I realized it might just be that simple.  After running ./configure I picked which options I wanted so
```
./configure --enable-gtk2 --enable-cli
``` and from the output I needed to add ```
sudo apt-get install mp3gain normalize-audio cd-discid
``` for the options I wanted.  (Turns out apt-get couldn't find discid.)  Then I found your tutorial after normalize wasn't found and apt-get couldn't find "normalize".  After looking at what you had there, I might have just said the hell with it this is too complicated for right now!

(Now I need to learn what ln does and why one uses it.  I am guessing it is what people call a symlink but I didn't get too much further than ln --help.) 

When the ./configure looked like everything was fine and it wasn't in the applications > sound and video I was crestfallen.  I was very glad to see your edit about needing a reboot so I found and launched it in /usr/local/bin# rrip_gui and it appears to be ripping right now.  All this came from not having CDex anymore and procrastinating turbotax.

---

### Post by iconoclast hero on 2011-04-18
> **maembe said:**
> I'm using kubuntu 10.10 and when I try do apt-get update I'm getting a couple error messages among all of the other text.

W:  failed to fetch [http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz) 404 Not Found
W:  failed to fetch [http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.lauchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz) 404 Not Found
E:  Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

Same thing happened to me:
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

My previous post showed what I did.  A few posts up is about the same method but done the right way.

---

### Post by iconoclast hero on 2011-04-18
Wait, I think I had a eureka moment:

I looked over the instructions and I think you just want to try it out and you already have a program like asunder, all you need to do is:
1) sudo apt-get install ruby ruby-gtk2 cdparanoia
2) download the source code from [here]("http://code.google.com/p/rubyripper/downloads/detail?name=rubyripper-0.6.0.tar.bz2&can=2&q=") open with the archive manager
3) move the folder to the desktop and open it
4) click on either of two rubyripper_*.rb scripts in the rubyripper folder.

If you hate it, you can stop there, if you love it, you can try and finish the job.  Is that really all there is to it?

---

### Post by Trompette83 on 2011-05-23
Hi,

I spend a lot of time trying to install a good working Rubyripper.
I run Ubuntu 10.04 LTS.

Is there someone who could tell me how to install any version of Rubyripper but working at a good speed (seems ruby1.8 faulty)?
May be I didn't get the good post in the thread with the good process, please let me know.
If there is not an easy way to do, I am open to go to 11.04, only if I can get it working well.

Thank you for your time

---

### Post by iconoclast hero on 2011-05-24
Start with #174 on [http://ubuntuforums.org/showthread.php?t=799621&page=18](http://ubuntuforums.org/showthread.php?t=799621&page=18).  Looking back on them, my posts are probably more confusing than helpful.  

Now are you saying that you have it installed but it is ripping very slowly?  That might be something for the rubyripper developers...I think it might be related to the fact that it uses cd paranoia and scans every track twice.  Personally, I think it is just slow.  It took me a little over 10 minutes to scan 2 tracks with a total of 28 minutes total. 

 I really do miss CDex.  It is probably the only reason I can think of to install wine.

I'm running 10.10.

> **Trompette83 said:**
> Hi,

I spend a lot of time trying to install a good working Rubyripper.
I run Ubuntu 10.04 LTS.

Is there someone who could tell me how to install any version of Rubyripper but working at a good speed (seems ruby1.8 faulty)?
May be I didn't get the good post in the thread with the good process, please let me know.
If there is not an easy way to do, I am open to go to 11.04, only if I can get it working well.

Thank you for your time

---

### Post by Trompette83 on 2011-05-24
Thank hero for reading my post.

As I had previously installed ruby1.9.2 so I get this message: 

$ sudo apt-get install libruby libruby1.8 libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev build-essential checkinstall git libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package git has no installation candidate

git is installed in fact
$ git --version
git version 1.7.5.2

If I continue with
$ ruby extconf.rb

I get
-----
Ignored libraries: glib, gdkpixbuf, pango, atk, gtk
-----

I am not good with Ubuntu could you let me know how to fix that?

THX

---

### Post by Trompette83 on 2011-05-24
I tried to install libgtk2.0-dev

$ sudo apt-get install libgtk2.0-dev

.......
0 upgraded, 39 newly installed, 0 to remove and 77 not upgraded.
Need to get 3,652kB/14.8MB of archives.
After this operation, 49.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) lucid/main x11proto-fixes-dev 1:4.1.1-2
  404  Not Found
Err [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) lucid/main libxcomposite-dev 1:0.4.1-1
  404  Not Found
Err [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) lucid/main gettext 0.17-8ubuntu3
  404  Not Found

...........

I got a lot of errors

Any idea?

---

### Post by Trompette83 on 2011-05-24
Same with Synaptic

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

No

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_4.1.1-2_all.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_4.1.1-2_all.deb)
  404  Not Found


W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.1-1_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.1-1_i386.deb)
  404  Not Found

and more
Why?

---

### Post by Trompette83 on 2011-05-24
I changed the archive ubuntu server and succeed to install libgtk2.0-dev.

But I still have the same error:
-----
Target libraries: glib, gdkpixbuf, pango, atk, gtk
-----

What now?

---

### Post by Trompette83 on 2011-05-24
OK, my mistake. The last message was not an error.

I continued and have another error here

./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
ruby-gtk2 is not found. The graphical frontend won't work!

gtk2 is still not installed!!!

Painfull...

---

### Post by iconoclast hero on 2011-05-24
> **Trompette83 said:**
> OK, my mistake. The last message was not an error.

I continued and have another error here

./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
ruby-gtk2 is not found. The graphical frontend won't work!

gtk2 is still not installed!!!

Painfull...

ok, well, first of all, do you want those language packs?  I left that out since it defaults to english.  I did not need to use the --prefix=/usr/local when i installed it yesterday.

but it is telling you what it needs...  did you try 
sudo apt-get install ruby-gtk2?

I don't know if it is that easy or if you have to go through the following from #174:

>  then go here and dl ruby-gtk2-0.19.4.tar.gz (last one listed
[http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/](http://sourceforge.net/projects/ruby-gnome2/files/ruby-gnome2/ruby-gnome2-0.19.4/)

create a build folder (I used rubyr) and extract the above to it, then cd to ruby-gtk2-0.19.4
This at the prompt 
```
ruby extconf.rb
```Should not error, will start out like this

and end like this, check

When finished
```
make
```make should end as such

if good then
```
sudo checkinstall --fstrans=no --default --deldoc  && sudo ldconfig
```

This didn't transfer properly, but try the apt-get install ruby-gtk2 and then try compiling.   If that doesn't work go back to #174 and follow the steps I couldn't copy and paste fully.

---

### Post by Trompette83 on 2011-05-24
I started again #174 from the beginning.

$ sudo apt-get install libruby libruby1.8 \
> libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
> build-essential checkinstall git libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
...
build-essential is already the newest version.
checkinstall is already the newest version.
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package git has no installation candidate

Why this first error?
$ git --version
git version 1.7.5.2
git is installed

I continued and for some reason I succeeded to install.
I don't understand at all.

I tried to rip one CD:
Drive spins, some head activity but for 20 mn still:
Starting to rip track 1, trial #1
Ripping progress 0%, Not yet started(0%)

I am back to the same issue.
I read ruby1.8 is faulty. 
What version do you use?

---

### Post by iconoclast hero on 2011-05-24
> **Trompette83 said:**
> I started again #174 from the beginning.

$ sudo apt-get install libruby libruby1.8 \
> libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
> build-essential checkinstall git libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
...
build-essential is already the newest version.
checkinstall is already the newest version.
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package git has no installation candidate

Why this first error?
$ git --version
git version 1.7.5.2
git is installed

I continued and for some reason I succeeded to install.
I don't understand at all.

I tried to rip one CD:
Drive spins, some head activity but for 20 mn still:
Starting to rip track 1, trial #1
Ripping progress 0%, Not yet started(0%)

I am back to the same issue.
I read ruby1.8 is faulty. 
What version do you use?

Ok, well mine is not *that* slow.  I really can't help you any further once you've gotten it compiled.  I considered that a major success once I got to that point.  To answer your question about what version of ruby, I don't know which it was compiled with, here is 
```

$ /usr/bin/ll
lrwxrwxrwx  1 root   root         22 2011-05-23 14:09 ruby -> /etc/alternatives/ruby*
-rwxr-xr-x  1 root   root       5448 2010-07-31 10:43 ruby1.8*
-rwxr-xr-x  1 root   root       5460 2010-10-18 02:59 ruby1.9.2*

```One thing to try might be able to try to see if it is rubyripper or if it is just the GUI...  try /usr/local/bin/rrip_cli if you can figure out how to get it to work.  You might want to see if the developers of rubyripper can give you any ideas.

---

### Post by mc4man on 2011-05-24
> Why this first error?
$ git --version
git version 1.7.5.2
git is installed
Because you are on lucid - if you read at the top of my post it said - 
> Quote:
how to get ruby ripper fully working on Ubuntu 10.10? 
That method would work just fine on lucid - the package is named git-core on lucid
Also works fine on natty, just did, though the ppa entries for ruby need to be edited after adding (no natty packages, edited to maverick

As far as what else you've done hard to tell, maybe you got it right, **but**

> I tried to rip one CD:
Drive spins, some head activity but for 20 mn still:
Starting to rip track 1, trial #1
Ripping progress 0%, Not yet started(0%)

That is not the issue with RR and the current ruby-gtk2, the pause comes **between** tracks, -  not with ripping a track itself

you seem to have an overall drive issue or at least with that cd

---

### Post by Trompette83 on 2011-05-25
Many thanks mc4man, my CD is faulty. No scratch, good looking but never start to rip.
Murphy's law !

You are right again, between every track there is a "coffee break" for 10 mn at least.

I would prefer to use the GUI, so could you show me a link where I could get the howto to:
"To fix the gui on lucid and or maverick requires switching default 'ruby' to the 1.9.X version and supplying a new ruby-gtk2 built off of ruby 1.9.X" as you said in the thread Re: rubyripper problems - lucid ruby 1.8 / 1.9 / libgtk2-ruby.

Thanks again.

---

### Post by mc4man on 2011-05-25
> **Trompette83 said:**
> 
I would prefer to use the GUI,.
Maybe we can square you up, - need to know something first, did you add the ppa as I suggested (ppa:pratikmsinha/ruby192+bindings) and did you install RR with checkinstall?

---

### Post by Trompette83 on 2011-05-26
OK, thanks for your time,

I am back on a previous install of my Ubuntu 10.04.
I stated your post #174 from the beginning.
sudo add-apt-repository ppa:pratikmsinha/ruby192+bindings 
sudo apt-get update
=> OK
sudo apt-get install libruby libruby1.8 libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev build-essential checkinstall git libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libruby is already the newest version.
libruby set to manually installed.
libruby1.8 is already the newest version.
libruby1.8 set to manually installed.
**E: Couldn't find package libruby1.9.2**

I found this to fix
cd /etc/apt/sources.list.d/
mv pratikmsinha-ruby192+bindings-lucid.list pratikmsinha-ruby192bindings-lucid.list

Now
ruby -v
ruby 1.9.2dev (2010-07-02) [i486-linux]

Which version I need to install?
ruby-gnome2-all-0.19.4.tar.gz 
ruby-gnome2-all-0.90.8.tar.gz

ruby-gtk2-0.19.4.tar.gz
ruby-gtk2-0.90.8.tar.gz

Do I need to install ruby-gnome AND ruby-gtk2 or only one, Which one?

---

### Post by mc4man on 2011-05-26
> Which version I need to install?
I marked a line in red - that's the one - ruby-gtk2-0.19.4.tar.gz

Make a directory in your home folder - name it something simple - rubyr would be fine.
Download the archive I said, put it in the 'rubyr' folder, r. click on it - "extract here"
Once extracted then open a terminal and cd to the extracted ruby-gtk2-0.19.4 folder so your terminal prompt looks like this - 
> :~/rubyr/ruby-gtk2-0.19.4$ 
Then just follow all the commands, starting right under "This at the prompt"  , the quote boxes should match up at each point.

**Do note** - at the top I marked something in blue - please take care of first
(remove rubyripper, ruby1.8-dev, libgtk2-ruby1.8 if installed - search and remove if need be in synaptic **before** doing anything

---

### Post by Trompette83 on 2011-05-27
Goooood, it's working well and quick,

I followed thoroughly what you wrote but for some raison the command
sudo apt-get install libruby libruby1.8 libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev build-essential checkinstall git libgtk2.0-dev
didn't install all the packages. With Synaptic I could see them but not installed, so I did with Synaptic.

Last question. I don't understand what you do mean with this:
> Note on the ruby alternative - if needing to switch temporarily for something run this, self explanatory
sudo update-alternatives --config ruby

Sorry I am a newbie in Linux.

Anyway thank you for your time and your patience.

---

### Post by mc4man on 2011-05-28
> **Trompette83 said:**
> Goooood, 

Last question. I don't understand what you do mean with this:

The package "ruby" is a dependency package - it includes some files that link to what is set as the default, one ex. is /usr/bin/ruby

Atm we've changed the 'default ruby' to the 1.9.2 version, if for some reason you needed the default 'ruby' to be 1.8 then you'd use update-alternatives to switch. It most likely you won't need to do this - anyway to show  - 

```
doug@doug-XPS-M1330:~$ sudo update-alternatives --config ruby
There are 2 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/ruby1.9.2   400       auto mode
  1            /usr/bin/ruby1.8     200       manual mode
  2            /usr/bin/ruby1.9.2   400       manual mode

Press enter to keep the current choice[*], or type selection number: 


```

If I needed to temp switch back to ruby1.8 I'd select 1

Edit: - just to note - the issue here with RR was not with the version of ruby, it's with the version of ruby-gtk that ubuntu/debian are using and have been for some time (actually it's not even the ver.  - 1.8 , it's the particular revision in use.
This obviously has affected RR and some other apps - there has been no movement to replace, therefore the need to workaround the stagnation, this was one way

---

### Post by Trompette83 on 2011-05-29
I understand now.

I really do appreciate your patience and I can see in your posts all the passion for teaching you have. Hope you will write in this forum for long time.

Many thanks again.

Take care

---

### Post by kakaw on 2011-06-11
I ran into the same error as Trompette83:
> **E: Couldn't find package libruby1.9.2**Tried the recommended fix, which was:
```
cd /etc/apt/sources.list.d/
mv pratikmsinha-ruby192+bindings-lucid.list pratikmsinha-ruby192bindings-lucid.list
```Then I went back to mc4man's instructions in #174 and tried this again:
```
sudo apt-get install libruby libruby1.8 \
libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
build-essential checkinstall libgtk2.0-dev git
```But I still get the same error.  What am I doing wrong?

---

### Post by mc4man on 2011-06-11
The ppa is for lucid and maverick - not sure what Trompette83 issue was.
For _**natty and oneiric**_ you add the ppa and then _edit the sources as shown in software-sources screens_, very simple

ppa is here - can be added manually or see cli below
[https://launchpad.net/~pratikmsinha/+archive/ruby192+bindings](https://launchpad.net/~pratikmsinha/+archive/ruby192+bindings)
 
first ck. software-sources as in screen 1, if there then edit to match what ubuntu release you have, -  if no listings for the ppa then in terminal

```
sudo add-apt-repository ppa:pratikmsinha/ruby192+bindings
```

Then in software-sources open each of the 2 listings and edit - if using natty they'll show natty instead of oneiric, edit to maverick
screen 2  - before editing the binary entry, screen 3 after.
screen 4 before editing source entry, screen 5 after.

then close, reload, and for good measure run 
sudo apt-get update


Ex.  - just did on 11.10 - 
> 
doug@doug-alienware:~$ sudo apt-get install libruby libruby1.8 \
> libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev \
> build-essential checkinstall libgtk2.0-dev git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
git is already the newest version.
libgtk2.0-dev is already the newest version.
checkinstall is already the newest version.
The following extra packages will be installed:
  libreadline5
Suggested packages:
  ri ruby-dev ruby1.8-examples ri1.8 ruby1.9.2-examples rdoc1.9.2 ri1.9.2 rubygems1.9.2
The following NEW packages will be installed:
  libreadline5 libruby libruby1.8 libruby1.9.2 ruby ruby1.8 ruby1.9.2 ruby1.9.2-dev
0 upgraded, 8 newly installed, 0 to remove and 49 not upgraded.
Need to get 6,377 kB of archives.
After this operation, 22.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libreadline5 i386 5.2-8 [123 kB]
Get:2 [http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/](http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/) maverick/main libruby1.9.2 i386 1.9.2.z1-1ppa1~maverick [3,316 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libruby1.8 i386 1.8.7.334-5 [1,780 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libruby all 4.8 [4,766 B] 
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main ruby1.8 i386 1.8.7.334-5 [35.8 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main ruby all 4.8 [5,054 B]
Get:7 [http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/](http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/) maverick/main ruby1.9.2 i386 1.9.2.z1-1ppa1~maverick [27.9 kB]
Get:8 [http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/](http://ppa.launchpad.net/pratikmsinha/ruby192+bindings/ubuntu/) maverick/main ruby1.9.2-dev i386 1.9.2.z1-1ppa1~maverick [1,084 kB]
Fetched 6,377 kB in 5s (1,245 kB/s)      
Selecting previously deselected package libreadline5.
(Reading database ... 198378 files and directories currently installed.)
Unpacking libreadline5 (from .../libreadline5_5.2-8_i386.deb) ...
Selecting previously deselected package libruby1.8.
Unpacking libruby1.8 (from .../libruby1.8_1.8.7.334-5_i386.deb) ...
Selecting previously deselected package libruby.
Unpacking libruby (from .../archives/libruby_4.8_all.deb) ...
Selecting previously deselected package libruby1.9.2.
Unpacking libruby1.9.2 (from .../libruby1.9.2_1.9.2.z1-1ppa1~maverick_i386.deb) ...
Selecting previously deselected package ruby1.8.
Unpacking ruby1.8 (from .../ruby1.8_1.8.7.334-5_i386.deb) ...
Selecting previously deselected package ruby.
Unpacking ruby (from .../apt/archives/ruby_4.8_all.deb) ...
Selecting previously deselected package ruby1.9.2.
Unpacking ruby1.9.2 (from .../ruby1.9.2_1.9.2.z1-1ppa1~maverick_i386.deb) ...
Selecting previously deselected package ruby1.9.2-dev.
Unpacking ruby1.9.2-dev (from .../ruby1.9.2-dev_1.9.2.z1-1ppa1~maverick_i386.deb) ...
Processing triggers for man-db ...
Setting up libreadline5 (5.2-8) ...
Setting up libruby1.8 (1.8.7.334-5) ...
Setting up libruby (4.8) ...
Setting up libruby1.9.2 (1.9.2.z1-1ppa1~maverick) ...
Setting up ruby1.8 (1.8.7.334-5) ...
update-alternatives: using /usr/bin/ruby1.8 to provide /usr/bin/ruby (ruby) in auto mode.
Setting up ruby (4.8) ...
Setting up ruby1.9.2 (1.9.2.z1-1ppa1~maverick) ...
update-alternatives: using /usr/bin/ruby1.9.2 to provide /usr/bin/ruby (ruby) in auto mode.
Setting up ruby1.9.2-dev (1.9.2.z1-1ppa1~maverick) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by kakaw on 2011-06-12
Thanks very much, mc4man!  I'm actually running 10.04, so I'm not sure why it wasn't working yesterday, but when I returned to your original instructions again today, they worked beautifully.  I came to this thread via a link you gave me on another thread about Banshee.  I am VERY grateful for your willingness to provide support for this!

---

### Post by mc4man on 2011-06-12
> **kakaw said:**
> , but when I returned to your original instructions again today, they worked beautifully. 
Glad you got it - that post was orig. just a response to someone using 10.10, and though the method would be valid for 10.04 > 11.10, there are some very small diff's

Just to note them
For 10.04 the only difference is the git package is named  git-core, otherwise the same.

For 11.04 & 11.10 the ppa I'm suggesting hasn't built 11.04 & 11.10 packages, though the 10.10 ones will work fine . So one just needs to edit the ppa source entries to maverick 

(maybe he'll add 11.04 and or 11.10 packages, maybe not
Better yet maybe some day debian/ubunu will move to he 1.9.X ruby as default which will then provide a proper working ruby-gtk

!ATm this is good on 11.10 though that is subject to change! 
And the use of the ppa was for convenience, not the only way by any means, the key source is ruby-gtk which is being built locally

---

### Post by iconoclast hero on 2011-06-15
> **mc4man said:**
> 
When finished
```
make
```make should end as such

if good then
```
sudo checkinstall --fstrans=no --default --deldoc  && sudo ldconfig
```After ruby-gtk2 is installed from same prompt

```
cd .. && git clone git://github.com/rubyripperdev/rubyripper.git
``````
cd rubyripper
``````
sudo apt-get install cdparanoia eject cd-discid libgettext-ruby-util \
lame flac vorbis-tools [COLOR=Blue]mp3gain vorbisgain normalize-audio[/COLOR]

```Blue are quite optional - **if** normalize-audio is installed then run this or rubyripper will not find
```

sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
``` 

mc4man, I am trying to follow your installation directions on a fresh 10.10 install *so I understand what is going on* (I have been able to follow your instructions several times successfully and I'm sure it will be the same this time as well.).  I think I get it... first install ruby and then onto ruby ripper...  I'm curious though as to where this line comes from:  ```
cd .. && git clone git://github.com/rubyripperdev/rubyripper.git
```.  I mean how would I know to use this particular command (the git command) rather than downloading it from code.google.com?

thanks

---

### Post by mc4man on 2011-06-15
> I mean how would I know to use this particular command (the git command) rather than downloading it from code.google.com?

You could do either way, easier for me to post a command than a link to site, download this ect.

The git command also gets the latest vs. from the site's download page which has the latest release (06/10 in this case
To know the git command one would go here instead of RR downloads page
[http://code.google.com/p/rubyripper/wiki/Git?tm=4](http://code.google.com/p/rubyripper/wiki/Git?tm=4)

(the cd .. part was to move your prompt from the ruby-gtk folder back to the build folder (rubyr or whatever you were using), note that on page they say "cd $HOME", we aren't building in home folder but in a folder for both RR and ruby-gtk

Edit  - in this case there hasn't been that much changed since the 0.6 release on 06/09 - see here 
[https://github.com/rubyripperdev/rubyripper/commits/master](https://github.com/rubyripperdev/rubyripper/commits/master)

---

### Post by iconoclast hero on 2011-06-15
> **mc4man said:**
> You could do either way, easier for me to post a command than a link to site, download this ect.

The git command also gets the latest vs. from the site's download page which has the latest release (06/10 in this case
To know the git command one would go here instead of RR downloads page
[http://code.google.com/p/rubyripper/wiki/Git?tm=4](http://code.google.com/p/rubyripper/wiki/Git?tm=4)

(the cd .. part was to move your prompt from the ruby-gtk folder back to the build folder (rubyr or whatever you were using), note that on page they say "cd $HOME", we aren't building in home folder but in a folder for both RR and ruby-gtk

Edit  - in this case there hasn't been that much changed since the 0.6 release on 06/09 - see here 
[https://github.com/rubyripperdev/rubyripper/commits/master](https://github.com/rubyripperdev/rubyripper/commits/master)

I know I'm going off topic here, but how do apt-get and git differ?  PM if you prefer.

---

### Post by amitaru on 2011-06-16
I just installed rubyripper (I assume it was 1.8) and it is ridiculously slow, 100 minutes to rip and 50 minutes CD. Based on forum posts it seems that it is a version issue, but I would like to hear how fast it is when it is working properly, how fast it is expected to rip a 50 minutes CD ?
Also, any hopes for a "simple" installation of the latest version ? I just don't have the balls to go through the sequence described in post #174. I'm on Ubuntu 10.10 and currently using Asunder and that is amazingly  fast, 2 to 3 minutes for a 50 minutes CD, but being an obsessive audiophile I'd like to try rubyripper that supposedly does a "better" ripping.

Thank you, Alex

---

### Post by mc4man on 2011-06-16
> **amitaru said:**
> I just installed rubyripper (I assume it was 1.8) and it is ridiculously slow, 100 minutes to rip and 50 minutes CD. Based on forum posts it seems that it is a version issue, but I would like to hear how fast it is when it is working properly, how fast it is expected to rip a 50 minutes CD ?
Also, any hopes for a "simple" installation of the latest version ? I just don't have the balls to go through the sequence described in post #174. I'm on Ubuntu 10.10 and currently using Asunder and that is amazingly  fast, 2 to 3 minutes for a 50 minutes CD, but being an obsessive audiophile I'd like to try rubyripper that supposedly does a "better" ripping.

Thank you, Alex
ripping speeds will be hardware dependant, normally RR is fairly quick (does a 2 pass min as default

There is no solution for the gui until debian/ubuntu upgrades ruby-gtk other than as I described or similar methods

However the cli RR is unaffected, you can setup RR in the gui as far as options, parameters, ect. ect, then do your rips from cli, either interactively or as an auto rip

abcde is also a good ripper - cli only, needs setting up the .conf
abcde has extensive options, can use cdda2wav (the real one, not icedax), instead of cdparanoia and can also be done interactively or auto

---

### Post by iconoclast hero on 2011-06-16
> **mc4man said:**
> ripping speeds will be hardware dependant, normally RR is fairly quick (does a 2 pass min as default

There is no solution for the gui until debian/ubuntu upgrades ruby-gtk other than as I described or similar methods

However the cli RR is unaffected, you can setup RR in the gui as far as options, parameters, ect. ect, then do your rips from cli, either interactively or as an auto rip

abcde is also a good ripper - cli only, needs setting up the .conf
abcde has extensive options, can use cdda2wav (the real one, not icedax), instead of cdparanoia and can also be done interactively or auto

I'm personally not a huge fan of the cdparanoia, but meh, whatever.  I'm really not ripping that many music CDs...  My main problem is audio books and unless I can find something that approaches the Fraunhoffer IIS codec I've been using for low quality, small size disc-at-once rips, I'm going to have to go back to windows to rip.

At any rate, this took 18 minutes with two passes (you'll have to check, but I count ca. 53 minutes):
Artist : Jimi Hendrix
Album: Band of Gypsys Live at the Fillmore East (Disc 2)

RIPPING SUMMARY

All chunks were tried to match at least 2 times.
None of the tracks gave any problems

---

### Post by ron999 on 2011-07-12
@mc4man
Hi
I followed the how-to in post # 174
Spot-on instructions.:KS
RubyRipper's up and running.:guitar:
(Lucid 10.04)

Thanks.

PS
On the humbug/pratikmsinha website, he's added another instruction.

> Because of a bug in aptitude/python-software-properties, another small change will be required. Executed the following commands...

Here:- [http://www.humbug.in/2010/launchpad-ppa-for-ruby-1-9-2-and-some-ruby-bindings/]("http://www.humbug.in/2010/launchpad-ppa-for-ruby-1-9-2-and-some-ruby-bindings/")

---

### Post by mc4man on 2011-07-16
> **ron999 said:**
> 
RubyRipper's up and running.:guitar:
(Lucid 10.04)

Thanks.

I just did it on 11.10, still a decent way, You'd think one of these days they'll update ruby, ruby-gtk, they haven't been since 10.04

I guess you moved to 10.04?
(I know of a very interesting ppa for lucid if you want to take a glance sometime - sorta a quasi- rolling though I think dev on it has slowed down a lot - could have some value as a 'pick and choose', then disable

---

### Post by ron999 on 2011-07-16
> **mc4man said:**
> 
I guess you moved to 10.04?
(I know of a very interesting ppa for lucid... 

Yes, I went from Karmic to Natty to Lucid.:)
Can I have information about that Lucid ppa please.

---

### Post by mc4man on 2011-07-16
> Can I have information about that Lucid ppa please. 

[https://launchpad.net/~guido-iodice/+archive/guiodiclucid](https://launchpad.net/~guido-iodice/+archive/guiodiclucid)

It now says unmaintained - not really
Plus if you look at the list of  contributors some very talented people (read - trustworthy
Last week I had a lucid install to test something (the _very poor_ decision to SRU a nautilus patch meant only for Mav and Natty
Went ahead and used the ppa - no issue

Another interesting thing for lucid - I have a semi-hidden how-to build/install totem-xine on karmic > natty
It's a bit scattered, used more as a crib sheet for myself, let me know..

Edit: if curious about what I believe was an improper patch see here - 
I spent 7+ months getting Mav and Natty fixed, don't intend to pursue this any further than..
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805753](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805753)

---

### Post by ron999 on 2011-08-07
Hi mc4man
I've just followed your #174 tutorial with Natty.

As you said... "Also works fine on natty, just did, though the ppa entries for ruby need to be edited after adding (no natty packages, edited to maverick".
This is easy to understand.

Then everything else went according to plan...
Until I installed rubyripper with checkinstall.
It gave error:-

ruby configure --update-lang #update the locale files
ruby-gettext is not found. Translations are disabled!
install -D -m 644 rr_lib.rb /usr/local/local/lib/site_ruby/1.9.2/rr_lib.rb
install: [COLOR="Red"]cannot create directory /usr/local/local/lib/site_ruby/1.9.2: No such file or directory[/COLOR]
make: *** [install] Error 1

So I had to create manually the folders **local/lib/site_ruby/1.9.2**
Then rr_lib.rb got installed in folder 1.9.2 OK.
:)

EDIT
I think this is because of a change in GIT today.

> diff --git a/rubyripper_cli.rb b/rubyripper_cli.rb
index 4540bde..315eb80 100755
@@ -15,7 +15,7 @@
 #    You should have received a copy of the GNU General Public License
 #    along with this program.  If not, see <http://www.gnu.org/licenses/>
 
-RUBYDIR=[ENV['PWD'], File.dirname(__FILE__), "/usr/local/lib/ruby/site_ruby/1.8"]
[COLOR="YellowGreen"]+RUBYDIR=[ENV['PWD'], File.dirname(__FILE__), "/usr/local/local/lib/site_ruby/1.9.2"][/COLOR]
 
 found_rrlib = false
 RUBYDIR.each do |dir|
diff --git a/rubyripper_gtk2.rb b/rubyripper_gtk2.rb
index 97604d5..0c84f23 100755
@@ -16,7 +16,7 @@
 #    along with this program.  If not, see <http://www.gnu.org/licenses/>
 
 ICONDIR=[ENV['PWD'], "/usr/local/share/icons/hicolor/128x128/apps"]
-RUBYDIR=[ENV['PWD'], File.dirname(__FILE__), "/usr/local/lib/ruby/site_ruby/1.8"]
[COLOR="YellowGreen"]+RUBYDIR=[ENV['PWD'], File.dirname(__FILE__), "/usr/local/local/lib/site_ruby/1.9.2"][/COLOR]
 
 found_rrlib = false
 RUBYDIR.each do |dir|


---

### Post by mc4man on 2011-08-07
ron - just did on a natty install, worked fine using previous method of installing to the default of /usr/local and also tried changing to install to /usr ( for default I don't specify prefix=, though no different if you do

Where you install to determines where the /bin and /share libraries go, the rr_lib.rb file seems goes to go  to  - see below edit

So if RR is installed to /usr you get this - 
> 
[QUOTE]========================= Installation results ===========================
ruby configure --update-lang #update the locale files
ruby-gettext is not found. Translations are disabled!
install -D -m 644 rr_lib.rb /usr/local/lib/site_ruby/1.9.2/rr_lib.rb
install -D -m 755 rubyripper_gtk2.rb /usr/bin/rrip_gui
install -D -m 644 rubyripper.png /usr/share/icons/hicolor/128x128/apps/rubyripper.png
install -D -m 644 rubyripper.desktop /usr/share/applications/rubyripper.desktop
install -D -m 755 -D rubyripper_cli.rb /usr/bin/rrip_cli


Which installs rr_lib.rb to the existing /usr/local/lib/site_ruby dir. created when installing ruby-gtk2 

The default of installing to /usr/local would do this - 
> ========================= Installation results ===========================
ruby configure --update-lang #update the locale files
ruby-gettext is not found. Translations are disabled!
install -D -m 644 rr_lib.rb /usr/local/local/lib/site_ruby/1.9.2/rr_lib.rb
install -D -m 755 rubyripper_gtk2.rb /usr/local/bin/rrip_gui
install -D -m 644 rubyripper.png /usr/local/share/icons/hicolor/128x128/apps/rubyripper.png
install -D -m 644 rubyripper.desktop /usr/local/share/applications/rubyripper.desktop
install -D -m 755 -D rubyripper_cli.rb /usr/local/bin/rrip_cli


Where RR creates a new dir, /usr/local/local/... 
In either case RR installed fine here, in the latter /usr/local/local/  didn't exist and was created during install.

Always thought that was odd (/usr/local/local) but never paid much mind because there was no issues seen here.

It would seem that unless told differently RR installs rr_lib.rb to prefix+location of ruby_site


Not sure why checkinstall failed to create /usr/local/ [COLOR="Blue"]local/lib/site_ruby/1.9.2[/COLOR] for you, does so here, using 
```
sudo checkinstall --fstrans=no --default --deldoc  --pkgversion 0.6+0607

```
Edit: the makefile shows the install paths, the configure file determines them, seems the location of the site_ruby plays a part.

---

### Post by mc4man on 2011-09-07
11.10 just got a new ruby-gtk2 (1.0.0-1) upgrade that will work well with rubyripper.
So RR can be configured against it and ruby1.9.1 (1.9.2.290-2) and should perform well 
The only thing to do is before configuring and installing RR is to run 
sudo update-alternatives --config ruby
and set to /usr/bin/ruby1.9.1
Otherwise it will use ruby1.8 and continue to hang as before

Ex,
```
$ sudo update-alternatives --config ruby
There are 3 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /usr/bin/ruby1.9.2   400       auto mode
  1            /usr/bin/ruby1.8     50        manual mode
[COLOR="Blue"]* 2            /usr/bin/ruby1.9.1   10        manual mode[/COLOR]
  3            /usr/bin/ruby1.9.2   400       manual mode
```

Or you may just see this when running update-alternatives which is fine
> $ sudo update-alternatives --config ruby
There is only one alternative in link group ruby: /usr/bin/ruby1.9.1


---

### Post by mc4man on 2011-09-16
Simplified method for install on **11.10**
11.10 has a new ruby-gtk so very easy to install a RR with no gui hang

 ```
sudo apt-get install ruby-gtk2 ruby1.9.1 \
checkinstall libgettext-ruby1.9.1 git
```

Edit : till -.7 releases I would not get the git, go to download page linked below, dl 0.6.2, extract & proceed
```
mkdir rubyr; cd rubyr; \
git clone https://code.google.com/p/rubyripper/ && \
cd rubyripper
```

Edit:^  another way to get the source & possibly a better option option for some would be to grab a  release version. Download, extract into a build folder, cd to it & proceed the same.
[http://code.google.com/p/rubyripper/downloads/list](http://code.google.com/p/rubyripper/downloads/list)


The blue are optional, remove as desired
```
sudo apt-get install cdparanoia eject cd-discid  \
lame flac vorbis-tools [COLOR="Blue"]mp3gain vorbisgain normalize-audio[/COLOR]
```

If normalize-audio is wanted then run this or RR will not find
```
sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

Should not be needed but run to double ck. anyway, if it happens to show ruby1.8 as the default then switch to ruby1.9.1 
(if at any time RR gets the gui hang re-run this & ck.
```
sudo update-alternatives --config ruby
```

configure RR 

```
./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr/local
```
Should show similar to this - important in red

> Checking the NEEDED dependencies....
[COLOR="Red"]cdparanoia found[/COLOR]...

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...

[COLOR="Red"]ruby-gtk2 bindings found[/COLOR]

Testing support for freedb metadata fetching...
[COLOR="Red"]cd-discid or discid found.[/COLOR]..

Testing support for ejecting the disk tray...
eject or disktutil found...

Testing support for different codecs on your system...
flac found...
oggenc (vorbis) found...
lame (mp3) found...

Testing support for replaygain...
wavegain NOT found.
vorbisgain found...
mp3gain found...

Testing support for normalize...
normalize found...
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/local/bin
* Localization files: /usr/local/share/locale
* Icon file: /usr/local/share/icons/hicolor/128x128/apps
* Desktop file: /usr/local/share/applications
* Ruby library: /usr/local/local/lib/site_ruby/[COLOR="Red"]1.9.1[/COLOR]

[COLOR="Red"]Gtk2 frontend will be installed
Cli frontend will be installed[/COLOR]
Languages to be installed: de, hu

You can now run make install


finish up with 
```
sudo checkinstall --fstrans=no --default --deldoc  --pkgversion 0.6.2
```

---

### Post by mc4man on 2011-10-06
A follow up on previous post or maybe using the current git in general - note: have no issues with english

this will now be reported when installed,
> Unfortunately ruby-gettext crashed at updating the po file.
This is a known issue with ruby-1.9 and ruby-gettext.
See also issue 400 at [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper).
For official releases the po files are already updated.

Otherwise 11.10 is good to go & certainly fine w/ english

---

### Post by georgelappies on 2011-10-09
> **jeggerleg said:**
> [QUOTE=ghindo;4993055][center]**[SIZE="5"][COLOR="Red"]HOWTO:  Install Rubyripper on Ubuntu[/COLOR][/SIZE]**[/center]

[SIZE="1"]*Note:  These instructions are aimed at Ubuntu 10.04 and above.  Results on other Ubuntu releases may vary.*[/SIZE]

**[SIZE="3"]What is Rubyripper?[/SIZE]**
From the _[HydrogenAudio wiki](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)_:


**[SIZE="3"]How is Rubyripper different from other CD rippers?[/SIZE]**
Rubyripper differs from programs like K3b and Sound Juicer because it is **much** more thorough.  Rubyripper rips each audio track at least twice, then compares each rip for differences and attempts to make the most accurate compilation of rips it possibly can.  The result?  Higher quality, *accurate* CD rips.

**[SIZE="3"]Installation[/SIZE]**
Unfortunately, Rubyripper isn't yet available in the official Ubuntu repositories.  Fortunately, there's a personal package archive (PPA) available which makes installation easy!  No more compiling from source! :)

[LIST=1]
[*]First, open up the terminal.  You can do this by looking in the Applications menu, under Accessories.
[*]Next, copy the following text into the terminal and hit enter:```
sudo add-apt-repository ppa:aheck/ppa
```This should prompt you for your password.
[*]Then, run the following command:```
sudo apt-get update
```
[*]Finally, enter```
sudo apt-get install rubyripper
```
[/LIST]

And that's it!  Rubyripper should now be in the applications Applications menu under Sound & Video. :)

Done all that:

"couldn't find package rubyripper"

Yeah, this is not working in 11.04...

---

### Post by tcarney57 on 2011-10-19
I've just installed 0.6.0 on my Kubuntu 10.10 system. I'm using the  command-line version, and so far I'm ripping to ogg. But I seem not to  understand how the "base directory" and file-naming settings work. I'll  try to explain:

1. I have my base directory set to ~/Music.

2. I have my standard naming scheme set to %a (%g) %t (my various artists scheme is similar).

3. When I select "Rip cd now," I get the following message:

[INDENT]The directory ~/Music already exist. What do you want rubyripper to do?
[/INDENT]
I  can cancel the rip, overwrite the directory, or auto-rename the  directory, none of which sounds like what I want. "Overwrite" sounds  scary. When I try "auto-rename," RR creates a new directory called  "Music#1" off my home directory. I assume it would continue doing that  (sermons#2, etc.) on future runs.

4. I use Amarok to organize my  music, so I'd just as soon dump all my music files into ~/Music and let  Amarok scan and refresh its database. I also prefer to use internal tags  for metadata and I don't feel I need a file structure (ex.:  /genre/artist/album/) to keep my stuff in order. That's Amarok's job.

So,  what am I getting wrong, and how do you think I can solve this issue.  I'm holding off ripping because I don't want to make a big mess.:confused:

Many thanks!

Todd

---

### Post by mc4man on 2011-10-20
> **tcarney57 said:**
> I've just installed 0.6.0 on my Kubuntu 10.10 system. I'm using the  command-line version, and so far I'm ripping to ogg. But I seem not to  understand how the "base directory" and file-naming settings work. I'll  try to explain:

1. I have my base directory set to ~/Music.

2. I have my standard naming scheme set to %a (%g) %t (my various artists scheme is similar).

I believe RR need to save in a directory(new), not loose in an existing dir.

You should use the gui to set this up - look at the "Example filename" to see, it changes as you adjust
(if you set it to something unacceptable it will be changed, after setting click on "Disc Info", then click on "Preferences" again to see if altered

the basename should end in a / like
~/Music/[/QUOTE]
your standard should include at least 1  / , i'm sure you'll figure it out 
Ex.  of a minimal standard
%b/%n-%t

---

### Post by manney on 2011-11-02
When I use Rubyripper's custom settings for mp3 conversion 
-V 3 --id3v2-only    Rubyripper will rip an mp3, but its a low quality rip.  When I use a high quality setting, -v 0 --vbr-new ,  Rubyripper comes back with this error:  1WARNING: Encoding to mp3 exited with an error with track 1!   In previous installs of Rubyripper I have never had a problem with this code.  Any ideas?  I'm using Ubuntu 10.04 64bit.

---

### Post by mc4man on 2011-11-02
Just change the -V 3 to -V 0 in RR's settings
The  --vbr-new  is not needed - it is a default

Ex. the "-V 0 --id3v2-only"  uses these parameters - 
> -m j -V 0 -q 0 -lowpass 19.5 --vbr-new -b 32

---

### Post by manney on 2011-11-04
Thank you mc4man.  I ripped a cd with your settings and it sounds great.  I think the problem I had with the default settings was when I viewed  the properties of the ripped mp3, under the audio tab, the default settings bitrate was only 88 kbps.  Using your settings the bitrate moved to 96 kbps, but it sounds amazing so either my OS isn't registering the proper bitrate or bitrate no longer matters?  Anyway thanks again for your help.

---

### Post by mc4man on 2011-11-04
> **manney said:**
> Thank you mc4man.  I ripped a cd with your settings and it sounds great.  I think the problem I had with the default settings was when I viewed  the properties of the ripped mp3, under the audio tab, the default settings bitrate was only 88 kbps.  Using your settings the bitrate moved to 96 kbps, but it sounds amazing so either my OS isn't registering the proper bitrate or bitrate no longer matters?  Anyway thanks again for your help.

I'm not up that much on mp3, use flac & aac generally

As far as what the r. click properties shows, never quite trusted that, sometimes correct, sometimes not, sometimes shows nothing

Prefer mediainfo - generally start in the default "easy" view, then switch to "HTML" for more extensive or "Text" for copying
(I normally start mediainfo, then drop file onto - can also be used from r. click context

Can be gotten from this ppa
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

Best way to add - 
 
```
sudo add-apt-repository ppa:shiki/mediainfo
```

Then 
```
sudo apt-get update; sudo apt-get install mediainfo-gui
```

There is also the command line package - mediainfo

( the default for RR in vbr is -b 32 which I believe means the min. br allowed when doing a vbr is 32, I guess that could be raised though I don't think it matters much, the algorithm tends to pick what's best while encoding 
(again mp3's aren't something I've used much

---

### Post by jymbob on 2011-11-20
> **georgelappies said:**
> [QUOTE=jeggerleg;9445077]

Yeah, this is not working in 11.04...

The problem is that the repository hasn't been updated to know about Maverick, Natty or Oneiric. Here's what I did:

```
sudo add-apt-repository ppa:aheck/ppa
```
Then change the file to point to the Lucid repository:
```
sudo nano /etc/apt/sources.list.d/aheck-ppa-oneiric.list
```
Make it look like this:
```
deb http://ppa.launchpad.net/aheck/ppa/ubuntu [COLOR="Red"]lucid[/COLOR] main
deb-src http://ppa.launchpad.net/aheck/ppa/ubuntu [COLOR="red"]lucid[/COLOR] main

```
After which you should be able to run
```
sudo apt-get update
```
without errors.

Finally, the rubyripper package doesn't install the front end by default, so you should probably do:
```
sudo apt-get install rubyripper-gtk
```

---

### Post by manney on 2011-11-29
Has anyone else encountered the problem where new  cd's ripped with the current version of RR will keep playing the same track and won't advance to the next track unless I press the forward button on my Philips Go Gear Vibe 8GB mp3 player?  The cd's that were already on my mp3 player which were ripped with RR 0.5.7 all advance on there own.  I've tried disabling repeat mode and selecting play all under settings and nothing seems to work.  I would appreciate any advice before I try re-ripping these troublesome cds.  On a side note I had to enter the track info in manually but I don't see how that would affect the tracks from advancing.

---

### Post by mc4man on 2011-11-29
> **manney said:**
> Has anyone else encountered the problem where new  cd's ripped with the current version of RR will keep playing the same track and won't advance to the next track unless I press the forward button on my Philips Go Gear Vibe 8GB mp3 player?  The cd's that were already on my mp3 player which were ripped with RR 0.5.7 all advance on there own.  I've tried disabling repeat mode and selecting play all under settings and nothing seems to work.  I would appreciate any advice before I try re-ripping these troublesome cds.  On a side note I had to enter the track info in manually but I don't see how that would affect the tracks from advancing.

Don't have a mp3 player (had an ipod but it was totally bricked during 11.10 dev testing), if you are using a git version of RR then maybe remove and try a release,  0.6 or 0.6.1 - you'd install as before,ect.
[http://code.google.com/p/rubyripper/downloads/list](http://code.google.com/p/rubyripper/downloads/list)

RR issues if you're inclined 
[http://code.google.com/p/rubyripper/issues/list](http://code.google.com/p/rubyripper/issues/list)

---

### Post by cornelis spronk on 2011-11-29
I managed to install Rubyripper into Maveric 10.10 following the steps outlined in post 225. However, I had to stumble through several steps, as there is some information missing.  In the end I could not explain to an Ubuntu newbie what I did to get each step to work, which frustrates me.

If someone would be so kind as to give a more complete explanation of each step, it would be helpful to someone less experienced with Ubuntu than I am.

---

### Post by Edoardo_P on 2012-03-20
Hi guys, I need a little help with this.

I'm using RubyRipper 0.6.2

when I import the folder in any Music Player (e.g. Rhythmbox, GMPC), everything is unknown but the name of the track which begins with the track number.

e.g.
---
Track: [Blank space]
Title: "01 - Yesterday"
Artist: "unknown"
Album: "unknown"
Genre: "unknown"
---

So... How to set the preferences?

---

### Post by mc4man on 2012-03-21
> **Edoardo_P said:**
> Hi guys, I need a little help with this.

I'm using RubyRipper 0.6.2

when I import the folder in any Music Player (e.g. Rhythmbox, GMPC), everything is unknown but the name of the track which begins with the track number.

e.g.
---
Track: [Blank space]
Title: "01 - Yesterday"
Artist: "unknown"
Album: "unknown"
Genre: "unknown"
---

So... How to set the preferences?Rubyripper doesn't tag Wav

---

### Post by smgendler on 2012-03-24
I used the built-in Ubuntu Software Center to get RR, and that installed version 0.5.7.  RR has been extremely slow on 10.04 LTS for me.  I uninstalled via the Software Center and downloaded the latest version, 0.6.2, using the instructions from the RR wiki.  RR is still slow, but I see a huge improvement in performance in going to the latest version.  I recommend it.  Secure ripping is worth the wait.

---

### Post by faucon50 on 2012-06-03
Hi, 

By opening RR I get this in the terminal:

rrip_gui
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': iconv will be deprecated in the future, use String#encode instead.
/usr/lib/ruby/1.9.1/gettext/runtime/locale_path.rb:20: Use RbConfig instead of obsolete and deprecated Config.
NOTE: Gem.all_load_paths is deprecated with no replacement. It will be removed on or after 2011-10-01.
Gem.all_load_paths called from /usr/lib/ruby/1.9.1/gettext/runtime/locale_path.rb:56.
NOTE: Gem.all_partials is deprecated with no replacement. It will be removed on or after 2011-10-01.
Gem.all_partials called from /usr/lib/ruby/1.9.1/rubygems.rb:258.
NOTE: Gem.all_partials is deprecated with no replacement. It will be removed on or after 2011-10-01.
Gem.all_partials called from /usr/lib/ruby/1.9.1/rubygems.rb:258.

RR works but I just wanted to know if anybody got the same "errors"? It looks like a bug in gettext, for more informations:

[http://code.google.com/p/rubyripper/issues/detail?id=503](http://code.google.com/p/rubyripper/issues/detail?id=503)

I'm on ubuntu 12.04 LTS server base + Xfce 4.10 PPA, Ruby 1.9.3.0-1ubuntu1, Gettext 0.18.1.1-5ubuntu3 and RR 0.6.2

Thanks

---

### Post by Rulius on 2012-12-30
I don't understand why installing rubyripper has to be so complicated.

Getdeb isn't working for me: I go to [http://linuxappfinder.com/package/rubyripper](http://linuxappfinder.com/package/rubyripper) click on "0.6.2-1~getdeb1" for precise and get "unable to connect" error.

It seems to me that rubyripper is not properly supported.

---

