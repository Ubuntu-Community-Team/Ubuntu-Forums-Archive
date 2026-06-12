---
title: "ipod/tunes headache!"
date: 2006-03-28
forum: The Cafe
---

### Post by nalmeth on 2006-03-28
My head is starting to pound just thinking about all this business.
My friend got an ipod nano as a gift, and said I could look at it and figure it out if I wanted (he still likes his discman, so do I).
So I try using my favorite music app (listen) because I've heard it can sync ipods, and I saw a screenshot of it, so I tried it. The Ipod mounts on my desktop, but listen doesn't recognize it. I restart listen, still nothing. I search and search around, install gtkpod, but it doesn't recognize it either. I then read that I need to format the ipod on a windows computer for it to work in Ubuntu (this is dumb, even if it is correct, which I haven't been convinced of either way yet). I see tons and tons of apps that are supposed to sync ipods, but no far and away winner. I've heard that crossover office can run Itunes, then I've heard it doesn't, then I've heard it will play your music but won't sync your pod. 
:confused:
Can ANYONE answer these simple questions for me, without offering 5 different apps for one function?

1. Do I need to format / write_database with itunes on a windows computer before I can use it in Ubuntu?
2. Will Itunes sync to an Ipod running in Crossover Office?

That's all I want to know

](*,)

---

### Post by mcduck on 2006-03-28
[QUOTE=nalmeth]
1. Do I need to format / write_database with itunes on a windows computer before I can use it in Ubuntu?
2. Will Itunes sync to an Ipod running in Crossover Office?
[/QUOTE]
1. Yes, you need to do that. Thanks Apple :rolleyes: 
2. No idea, but after doing step 1. gtkpod should work. (it works for me at least)

---

### Post by nalmeth on 2006-03-28
thanks mcduck
I expected as much, and I second your :rolleyes:

---

### Post by Jason_25 on 2006-03-28
As he said, once you create the database in gtkpod the ipod sync will work correctly.

---

### Post by joey111 on 2006-03-28
i simply do not understand right now how
i can create the db; do i have to format the ipod in windows itunes and then how would i create/export the itunesdb to ubuntu??

i got a ipod nano 2Gb and gtkpod 0.99.4;
whenever i plug the ipod it says :
[I]You did not import the existing iTunesDB (&#8217;/mnt/ipod/iPod_Control/iTunes/iTunesDB&#8217;). This is most likely incorrect and will result in the loss of the existing database.
 Press &#8216;OK&#8217; if you want to proceed anyhow or &#8216;Cancel&#8217; to skip storing. If you cancel, you can import the existing database before calling this function again.[/I]
or i get the mistake
[I]Could not open &#8220;iTunesDB.ext&#8221; for reading extended info.
 Extended info will not be used.
 iPod Database Import Failed: &#8216;Error reading file &#8216;/mnt/ipod/iPod_Control/iTunes/iTunesDB&#8217;: Is a directory&#8217;.[/I]
when i start gtkpod the read button is monichrome so i cannot use it to read from the ipod ; i guess its related to the nonexisting itunes db, so how i could fix the prob one for alll time??****************
-another thing: how could i prevent the gtkpod program to mess up the titles /photos /playlists ? they are sometimes destroyed, esp.if u use the original itunes program sometimes;

---

### Post by tom-ubuntu on 2006-03-28
Got an Ipod sync question aswell, hope it is alright, if I just jump in.

My whole music collection is stored in FLAC. As far as i know, Ipod is not able to play this format. It also wouldn't make sense for a portable player to use that. Now to my question:

Is there a (easy) way to sync my ipod with the collection but converting the tracks on the fly to mp3?

---

### Post by mrgnash on 2006-03-28
Gotta love Apple's nonexistent support for Linux, and it only gets better once you start to run into all their DRM malarkey. 

Ipods are quite nice, but they'll never get (another) [color=red]red[/color] cent out of me. ](*,)

---

### Post by Jason_25 on 2006-03-28
Under gtkpod, click file > create ipod's directories.  It doesn't seem to destroy or change much of anything on the ipod.  It just makes gtkpod work.

---

### Post by joey111 on 2006-03-28
[QUOTE=Jason_25]Under gtkpod, click file > create ipod's directories.  It doesn't seem to destroy or change much of anything on the ipod.  It just makes gtkpod work.[/QUOTE]
yes, but then it returns that it created alle directories except /mnt/ipod/calendars;
and it has no effect to my prob above, e.g. still the non existing db message appears;

---

### Post by mcduck on 2006-03-28
[QUOTE=joey111]yes, but then it returns that it created alle directories except /mnt/ipod/calendars;
and it has no effect to my prob above, e.g. still the non existing db message appears;[/QUOTE]
Damn. I spoke too soon. I just tried to upload about 4GB of music to my ipod, at some point it just stopped and now i have the same problem with 'non existing db'.. Now my ipod shows that it has no files and gtkpod does nothing but complains about everything.. ](*,) 

It worked with no problems for a year. I guess 4GB was just too much. :(

edit: I booted to windows, reset everything, updated ipod software, added some music, booted back to ubuntu and now it works again. At least on some level. Gtkpod doesn't seem to like some of my music, it tells that it writes it to ipod, but freezes when updating the db and then tells that updating db failed..

edit2: and now it did the same thing again.. I guess I'll have to look at the ext driver for windows to move my music to ipod with itunes..

edit3: ok, I installed ext driver for windows and managed to fill my ipod again. But that crappy itunes fails to read v.2.4 ID3-tags, so it shows half of my music colection without tags. :(

I'd just like to know what could be the problem with gtkpod, as it worked just fine the last time I moved songs to my ipod. I suppose it must be something with character sets or something..

---

### Post by Jason_25 on 2006-03-28
That's pretty surprising that it didn't work.  I remember needing to mount and unmount the ipod nano after building the database in gtkpod.  Maybe file a bug if you've exhausted all your options.

---

### Post by Zodiac on 2006-03-28
iPod support is spotty at best...

I even tried Banshee but it used to crash horrible whenever my iPod was plugged into the PC... something about out of date mono packages or some such thing.

Not sure if it is fixed...

---

### Post by nalmeth on 2006-03-28
Can anyone post a screenshot or a quick explanation of what you have to do in itunes to make it work on gtkpod/banshee/amarok/etc?
I don't have windows, so I have to go elsewhere I can find a windows computer. Someone mentioned that gtkpod can make the directories, but I wasn't sure if he meant this was after or before the itunes formatting.
I had itunes going at work last night (windows xp) but itunes made the xp panel disappear, and seemed to be causing other problems aswell.
I hope to go in, format the ipod, and get out before I cause any damage ;)

And no luck with itunes in crossover huh guys?

---

### Post by mcduck on 2006-03-28
[QUOTE=nalmeth]Can anyone post a screenshot or a quick explanation of what you have to do in itunes to make it work on gtkpod/banshee/amarok/etc?
I don't have windows, so I have to go elsewhere I can find a windows computer. Someone mentioned that gtkpod can make the directories, but I wasn't sure if he meant this was after or before the itunes formatting.
I had itunes going at work last night (windows xp) but itunes made the xp panel disappear, and seemed to be causing other problems aswell.
I hope to go in, format the ipod, and get out before I cause any damage ;)

And no luck with itunes in crossover huh guys?[/QUOTE]
all you have to do in itunes is start it, and and perhaps add some music to your iPod. I think you'll get asked some questions when you start iTunes with a new iPod.

What I'm doing now is compiling a new kernel without EFI support, because after whole day of trying everything, and googling around, all I could find was that iPod's report the disk size a bit bigger than what it is, and EFI support in kernel causes some problems. I hardly even know what that is, but since it's the only thing I found I could try I'll do that.. Even if that was supposed to be fixed in 2.6.10 kernel. :rolleyes:

---

### Post by zachtib on 2006-03-28
[QUOTE=nalmeth]
2. Will Itunes sync to an Ipod running in Crossover Office?
[/QUOTE]

not without a really ugly hack.  not worth it IMO.  I would just recomend you use banshee or yamipod.  gtkpod never worked that well for me

---

### Post by joey111 on 2006-03-28
but they dont support playlists and covers right?
well if i dont have that why not use amarok? by far simplest and easiest solution.

---

### Post by zachtib on 2006-03-28
yamipod does playlists, i know, and banshee supports album art in the program, dunno if it syncs it to the ipod

---

### Post by Stormy Eyes on 2006-03-28
[QUOTE=zachtib]yamipod does playlists, i know, and banshee supports album art in the program, dunno if it syncs it to the ipod[/QUOTE]

YamiPod caused my machine to hang so hard that I couldn't even SSH in from my wife's machine. Of course, I was dumb enough to use it on Dapper, so that might be the problem.

---

### Post by endersshadow on 2006-03-28
Time for Uncle Endersshadow to take you on a trip, and what a trip it shall be.

1. Build the latest version of gtkpod.  Here's how:

```
sudo apt-get install libexpat1-dev libglade2-0 libglade2-dev flex libid3tag0 libid3tag0-dev
wget http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz
tar xzf XML-Parser-2.34.tar.gz
perl Makefile.PL
make
sudo checkinstall -D make install
wget http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.3.2.tar.gz
tar xzf libgpod-0.3.2.tar.gz
cd libgpod-0.3.2/
./configure
make
sudo checkinstall -D make install
sudo cp /usr/local/lib/libgpod* /usr/lib
wget http://easynews.dl.sourceforge.net/sourceforge/gtkpod/gtkpod-0.99.4.tar.gz
tar xzf gtkpod-0.99.4.tar.gz
cd gtkpod-0.99.4
./configure
make
sudo checkinstall -D make install
```

If you want explanation, go [here](http://ubuntuforums.org/showthread.php?t=114946).

2. Open gtkpod up.

3. Use it.

If you've got songs on your iPod, use the read button, as pictured:

[IMG]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-read.gif[/IMG]

If you haven't got songs on your iPod and would like to make them work with Linux, use the Create iPod Directories option in the menu:

[IMG]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-create.gif[/IMG]

Once you have that, add your songs by using the add button, which will pop up a file chooser:

[IMG]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-add.gif[/IMG]

Once you're happy with the stuff on your iPod, Sync it:

[IMG]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-sync.gif[/IMG]

Voila. You've got your iPod support on Ubuntu Linux :-D

---

### Post by nalmeth on 2006-03-28
Wow, good shit! 
Screenshots and everything. 
Thank you kindly, I will post how it works out. 
First though I have to sanitize my computer desk, my roomate has tonsilitis and who knows what else. He's left all kinds of diseased articles all over the desk. I'm using my laptop right now, but have no music on it. I've got something to do now!
Thanks again man

---

### Post by endersshadow on 2006-03-28
[QUOTE=nalmeth]Wow, good shit! 
Screenshots and everything. 
Thank you kindly, I will post how it works out. 
First though I have to sanitize my computer desk, my roomate has tonsilitis and who knows what else. He's left all kinds of diseased articles all over the desk. I'm using my laptop right now, but have no music on it. I've got something to do now!
Thanks again man[/QUOTE]

You're welcome.  I remember when I got my iPod over Christmas...nobody could tell me what the hell to do...so, I started playing around, and figured it out...took me forever though... :-D

---

### Post by joey111 on 2006-03-28
thanks so much;
actually i had everyhing ( maybe apart from libexpat1-dev), but if i want to make sure and have a proper clean install, how would i remove gtkpod?
sudo apt-get remove gtkpod says: it wasnt recently installed, 0 files removed.

---

### Post by endersshadow on 2006-03-28
[QUOTE=joey111]thanks so much;
actually i had everyhing ( maybe apart from libexpat1-dev), but if i want to make sure and have a proper clean install, how would i remove gtkpod?
sudo apt-get remove gtkpod says: it wasnt recently installed, 0 files removed.[/QUOTE]

Is this an old version of gtkpod?

Edit: gtkpod is not in the repositories, so you probably installed it from source...

---

### Post by joey111 on 2006-03-28
99.4 ( the newest); in synaptic there appears the older version only, thats why i cannot make it be removed trough synaptic.

---

### Post by endersshadow on 2006-03-28
[QUOTE=joey111]99.4 ( the newest); in synaptic there appears the older version only, thats why i cannot make it be removed trough synaptic.[/QUOTE]

Did you use checkinstall to install it, or did you do a straight make install?

Edit: If you did a checkinstall, you probably didn't change the package name, so do:

```
sudo dpkg -r gtkpod-0.99.4
```

If you did a straight make install, go to the source folder and do a sudo make uninstall.

Should be all set...

Another edit: If you've installed gtkpod from source, you have a clean install--it will automatically write over older versions.

---

### Post by joey111 on 2006-03-28
i used make install (couldnt use check install for some reason);
anyway i built it from source and would now need to overwrite it with the same version (0.99.4) so if i understood u correct i dont need to remove? it is overwritten automatically?

---

### Post by endersshadow on 2006-03-28
[QUOTE=joey111]i used make install (couldnt use check install for some reason);
anyway i built it from source and would now need to overwrite it with the same version (0.99.4) so if i understood u correct i dont need to remove? it is overwritten automatically?[/QUOTE]

Overwritten automatically...just make install it :-D

---

### Post by nalmeth on 2006-03-29
endersshadow, you are officially 'the man'
Following your directions, I now have a functional ipod program.
I must say this gtkpod isn't the nicest looking program in the world, and a little confusing at first, but I'm just glad it's working.
You should really make this into a howto, or even a script, some kind of 3rd party app or something. No newb could pick this up and get it working. So many people have ipods too, that it would be widely used I would think.
If you make a howto, only corrections are to add checkinstall to apt-get install list, and add cd XML-Parser-2.34 before perl Makefil.PL. Otherwise, flawless.
A couple question though if you don't mind, or anyone else who could answer them.
Do you have to create a new playlist before dragging the tracks over to the ipod? Or do you only make one at the beginning, or when you clear the current one?
Can you have mulitple playlists to pick from on the pod?
What about images? Would I just drag them over, and would they be put in the right "images" folder? Do I have to create this?
I want gtkpod to open automatically when the ipod is plugged in. In 'Removable Drives and Media Preferences', in order to make an app open, I have to enable "Sync Music Files when Connected".
What does this mean? Can you stop nautilus from opening when plugging it in? And can you use nautilus to add files to the pod?
Lots of questions I know.
Thanks again, big time man

BTW whose the player in your avatar? U of Mass I'm guessing?

---

### Post by endersshadow on 2006-03-29
[QUOTE=nalmeth]endersshadow, you are officially 'the man'
Following your directions, I now have a functional ipod program.
I must say this gtkpod isn't the nicest looking program in the world, and a little confusing at first, but I'm just glad it's working.

1. You should really make this into a howto, or even a script, some kind of 3rd party app or something. No newb could pick this up and get it working. So many people have ipods too, that it would be widely used I would think.
If you make a howto, only corrections are to add checkinstall to apt-get install list, and add cd XML-Parser-2.34 before perl Makefil.PL. Otherwise, flawless.

A couple question though if you don't mind, or anyone else who could answer them.

2.Do you have to create a new playlist before dragging the tracks over to the ipod? Or do you only make one at the beginning, or when you clear the current one?

3.Can you have mulitple playlists to pick from on the pod?

4. What about images? Would I just drag them over, and would they be put in the right "images" folder? Do I have to create this?

5. I want gtkpod to open automatically when the ipod is plugged in. In 'Removable Drives and Media Preferences', in order to make an app open, I have to enable "Sync Music Files when Connected".
What does this mean? Can you stop nautilus from opening when plugging it in? And can you use nautilus to add files to the pod?
Lots of questions I know.
Thanks again, big time man

6. BTW whose the player in your avatar? U of Mass I'm guessing?[/QUOTE]

Okay, I just had to deal with a kid having a seizure (I'm an RA, woohoo), so my answers may or may not be coherent...50/50 shot right now :-D

1. I just may write a HowTo...my current project is [Vive](http://vive.sourceforge.net), which blossomed out of my problem that I wanted to use my iPod on Ubuntu and I wanted to copy my DVDs onto said iPod.  Luckily for me, I figured it out, and I've just made it look pretty and handed it out under the GPL...but a gtkpod tutorial may be useful...and mayhaps I'll send it to Jorg so he can throw it up on the gtkpod site.  Who knows when I'll have time though...

2. You can do whatever your heart desires.  I've found that creating playlists helps me sort out my songs, but you can do just one if your heart so desires.

3. Absolutely!  I currently have 3 audio playlists (All My Rock, Dane Cook, Best Rock), and 1 video playlist (Movies) on mine...makes life simple for me.

4. Yes, add images like you would add a song.  It will automatically put them into the "Photos" section...the Firmware is good like that.  Just in case I misunderstood your question, here's how to set cover art (if you hadn't had it set already).  Right click on a song (on the iPod) and click Edit Details, as pictured:

[img]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-editdetails.gif[/img]

Then, click the Set Cover Art button in the ensuing window to choose a picture from your computer (NOT your iPod):

[img]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-coverart.gif[/img]

Sync it, and you're all set.

5. I've managed to stop Nautilus from opening, but I don't remember how...I searched for it quickly and didn't figure it out...if I remember how, I'll post it.

6. Lord help me if it were UMass.  No, it's Stephen Gionta of Boston College (the school I attend).  It's actually a crop of a picture I took...original picture (it's a big file, so here's a link, dialupers beware!): [Gionta1](http://www.politicalcrossfire.com/temp/TPCohasset/gionta1.jpg)

Edit: If you get a 500 error, go to politicalcrossfire.com first, and then try the link again.  Sorry about that...

That's him against John Curry of BU.  They play April 6th at 3pm EST against the University of North Dakota Fighting Sioux in Milwaukee, Wisconsin on ESPN2.  If they win, they go on to face the winner of Maine v. Wisconsin for the NCAA Men's Ice Hockey Championship Game on April 8th at 8PM EST on ESPN.  I'm a little excited.  I actually grew up in Ithaca, though, so I've always been a Cornell fan (but came to BC for the better business school), and I was heartbroken when they lost in triple overtime to Wisconsin on Sunday night.  Okay, you got me talking hockey.  I better shut up now or I'll never stop :lol:

---

### Post by nalmeth on 2006-03-29
Awesome thanks for clearing all that up. I like how the firmware deals with all that automatically, there's no way to know what its going to do at first sight.
Sorry to blaspheme, I know how hardcore people can get about their teams.
Is Stephen Gionta by chance related to Brian Gionta for the Devils?
You're heartbroken huh? I'm a Flames fan, and still devastated after all this time. I know college hockey is huge down south, and it's a different game, but hockey fans are hockey fans.
BTW Hope you're not a Bruin's fan this year. WOW
Anyways, like you said, hockey discussion will go on forever. 
Thanks for your time and help

---

### Post by mcduck on 2006-03-29
I solved my problems with iPod. I had to compile my own kernel disabling EFI Partition support (it has been enabled since 2.6.15-8.10 kernel: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/26186]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/26186")). 

After that, my iPod mini works perfectly again. :D 

So, if you have problems with your iPod not mounting, or mounting but failing to work when you try to read or write to it, this is worth a try.

While searching for possible solutions to my problems with iPod I found many pages mentioning kernel a kernel patch that allows both iPod and EFI support at the same time. I suppose people responsible for Ubuntu kernel either forgot that patch or don't even know about it :rolleyes:

I'll file a bug report about this in lauchpad, and hopefully iPods will work again in the final Dapper release :)

---

### Post by endersshadow on 2006-03-29
[QUOTE=nalmeth]Awesome thanks for clearing all that up. I like how the firmware deals with all that automatically, there's no way to know what its going to do at first sight.
Sorry to blaspheme, I know how hardcore people can get about their teams.
Is Stephen Gionta by chance related to Brian Gionta for the Devils?
You're heartbroken huh? I'm a Flames fan, and still devastated after all this time. I know college hockey is huge down south, and it's a different game, but hockey fans are hockey fans.
BTW Hope you're not a Bruin's fan this year. WOW
Anyways, like you said, hockey discussion will go on forever. 
Thanks for your time and help[/QUOTE]

Stephen is Brian's younger brother.  Brian graduated from BC last year.  Stephen's a bit smaller, but he's got a better shot and he's much quicker.  Kind of scary, if you think about it.

And yes, I am a Bruins fan.  I will leave it at that, and you can draw your own conclusions about my mental state.

[quote=mcduck] 	I solved my problems with iPod. I had to compile my own kernel disabling EFI Partition support (it has been enabled since 2.6.15-8.10 kernel:  [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/26186)](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/26186)).

After that, my iPod mini works perfectly again.

So, if you have problems with your iPod not mounting, or mounting but failing to work when you try to read or write to it, this is worth a try.

While searching for possible solutions to my problems with iPod I found many pages mentioning kernel a kernel patch that allows both iPod and EFI support at the same time. I suppose people responsible for Ubuntu kernel either forgot that patch or don't even know about it

I'll file a bug report about this in lauchpad, and hopefully iPods will work again in the final Dapper release.[/quote]

It appears that there's a fix in the repositories for it, now, so we shouldn't have to worry about the format of the iPod.    I suppose I was lucky enough to not have to deal with this, as my compy is the only one my iPod has ever touched.  It worked as soon as I plugged it in (brand new) to it...so woohoo!

---

### Post by mcduck on 2006-03-29
[QUOTE=endersshadow]
It appears that there's a fix in the repositories for it, now, so we shouldn't have to worry about the format of the iPod.    I suppose I was lucky enough to not have to deal with this, as my compy is the only one my iPod has ever touched.  It worked as soon as I plugged it in (brand new) to it...so woohoo![/QUOTE]
Fix for what? Dapper's Kernel? Updates to gtkpod won't fix my problem.

My iPod Mini mounted perfectly, and unmounted perfectly, and everything worked just fine as long as I didn't try to actually read or write to it.. That caused it to lock and corrupted all data on the iPod.

That's because iPods (at least some versions) report their size to be a bit bigger than what it really is (thanks Apple, great job), and that was not a problem until EFI support was enabled in Ubuntu kernels. And so my iPod worked with no problems in Hoary and Breezy. But now the kernel tries to check the last sectors of the iPod to see if it's a EFI partition, only that those sectors don't even exist :rolleyes: And that's when all the I/O errors start..

take a look at this: [http://www.linuxquestions.org/questions/showthread.php?p=1197015#post1197015]("http://www.linuxquestions.org/questions/showthread.php?p=1197015#post1197015")

---

### Post by endersshadow on 2006-03-29
[QUOTE=mcduck]Fix for what? Dapper's Kernel? Updates to gtkpod won't fix my problem.

My iPod Mini mounted perfectly, and unmounted perfectly, and everything worked just fine as long as I didn't try to actually read or write to it.. That caused it to lock and corrupted all data on the iPod.

That's because iPods (at least some versions) report their size to be a bit bigger than what it really is (thanks Apple, great job), and that was not a problem until EFI support was enabled in Ubuntu kernels. And so my iPod worked with no problems in Hoary and Breezy. But now the kernel tries to check the last sectors of the iPod to see if it's a EFI partition, only that those sectors don't even exist :rolleyes: And that's when all the I/O errors start..

take a look at this: [http://www.linuxquestions.org/questions/showthread.php?p=1197015#post1197015]("http://www.linuxquestions.org/questions/showthread.php?p=1197015#post1197015")[/QUOTE]

Oh, okay, I misunderstood your problem.  I see that now...wow...that's, um, wow.  Way to go, Apple!

---

### Post by endersshadow on 2006-03-29
I've managed to figure out how to change it so gtkpod opens up when you plug in the iPod.  In the Removable Storage and Media settings (in System>Preferences), go to the multimedia tab, check the Sync files and then in the command line, put gtkpod, so it looks like this:

[IMG]http://i31.photobucket.com/albums/c390/endersshadow7/gtkpod-autoload.png[/IMG]

Also, to make it mount correctly each and every time, do this (w/o iPod connected):

```
sudo mkdir /media/ipod
sudo gedit /etc/fstab
```

Then, add this line at the bottom:

```
/dev/sdc2	/media/ipod	vfat	defaults	0	0
```

Save it and then you're all set to go :-D

---

### Post by joey111 on 2006-03-29
which menu would i have to choose in kde?
i checked the systems etc. but ipod as option doesn't seem to appear there..
-well one has to figure out (right?) which device, for me eg.. it is /dev/sda2, if sth else is plugged /dev/sdb2 etc.
as i also have linux on the ipod nano (for the films) it opens /dev/sda2 and /dev/sda3 (linux partition 32 MB) the latter can be ignored i think.

---

### Post by joey111 on 2006-03-30
i did a complete new install following the instructions above and still the first thing it says is: did not import the existing db..
first i thought its because maybe the gtkpod (and its automatic umount/mount mechanism is not in the sudoers list- how could i add it there?)
but it also appears when I do that manually- the mounting.
I am exhausted.. its never gonna work i guess..I cannot read from the Ipod once i plug it.The button stays monochrome and the error message appears
 But when i do *Check ipod's Files * it imports the files (corrupting all playlist and covers, and it last everytime 5 mins).
The error message I would have to ignore in this case is:
You did not import the existing iTunesDB. This is most likely incorrect and will result in the loss of the existing database.
[I]
Press 'OK' if you want to proceed anyhow or 'Cancel' to abort. If you cancel, you can import the existing database before calling this function again.[/I]
please any idea?
thank you

---

### Post by joey111 on 2006-04-01
ok, it finally worked to import the db, but now (after evrything did the job a couple of times ) this appears all of a sudden again and again:this happened after i had done a new playlist and wanted to synchronize it.[I]
Error opening '/media/ipod/iPod_Control/Music/F00/gtkpod080108.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F01/gtkpod252050.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F02/gtkpod314130.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F03/gtkpod706685.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F04/gtkpod251717.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F05/gtkpod685194.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F06/gtkpod165112.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F07/gtkpod678599.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F08/gtkpod179751.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F09/gtkpod688355.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F10/gtkpod631517.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F11/gtkpod010070.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F12/gtkpod422221.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F13/gtkpod045819.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F14/gtkpod581230.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F15/gtkpod400031.mp3' for writing (Permission denied).

Error opening '/media/ipod/iPod_Control/Music/F16/gtkpod010002.mp3' for writing (Permission denied).

[/I]
if i want to quit then it says:Data has been changed and not been saved.
OK to exit gtkpod?
and on the ipod the files don't appear. 
well it seems that it has something to do with the rights,
i have to use the  *sudo*command,
if i dont then e.g. the message above appears, but if I use *su*
then it cannot open the display:
[I]usr@fluffy:~$ su
Password:
root@fluffy:/home/usr# gtkpod &
[1] 17662
root@fluffy:/home/usr# Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gtkpod:17662): Gtk-WARNING **: cannot open display:
[/I]

another thing i mentioned:
in gnome u can just do "umount the ipod" on the desktop, while in kde u need to do "eject /dev/sda2".

how could i manage it that gtkpod automatically starts with sudo rights?
e.g. i cannot use katapult i always have to open a terminal to start gtkpod:
thx

---

### Post by joey111 on 2006-04-04
in the edit/preferences what do u specify as path to notes/calendar/contacts if u want to synchronize between kontact and the ipod through gtkpod?
e.g. for notes i tried
- knotes & 
- /home/usr/.kde/share/apps/knotes/notes 
- /usr/bin/knotes
; 
what should i specify there, doesn't work..

---

### Post by jbmalone on 2006-04-04
I know that this is really late but this is how I got my iPod working when it was messing up.

1. Go to a Windows computer and install the iPod software off of the packaged cdrom.

2. Plug your iPod into the computer and open the iPod software.  In the software, choose reset.  It will warn you that you are getting ready to clear your iPod, choose OK.  Afterwards, you need to plug the iPod back into the wall on the charger and let it rebuild the firmware.  

3. Plug the iPod back in the Windows computer and open iTunes.  In iTunes load a random track/album/whatever.

4. Install gtkpod on your Ubuntu machine, and plug the iPod in.  Make sure you click "Read" before you start adding/deleting/editing tracks.  Everything should work out fine.

_____________________

Possible errors:

Before I went through these steps I constantly had problems with the DB, but these steps solved all of it.  The ONLY other error I have encountered was a Playback Count error.  This error prevents you from adding and deleting tracks.  The fix is to eject your iPod and use it.  Let it run for ten or so tracks, then try again.  This resets that file and gets it to work normally.  Sometimes, you will also encounter an error syncing files saying blah.mp3 could not be added.  Ignore this message.  The track was added and will play.

I hope this helped someone.

---

### Post by kassetra on 2006-04-05
[quote=nalmeth]
Can ANYONE answer these simple questions for me, without offering 5 different apps for one function?

1. Do I need to format / write_database with itunes on a windows computer before I can use it in Ubuntu?
2. Will Itunes sync to an Ipod running in Crossover Office?[/quote] 
1. Not necessarily. Your iPod came pre-formatted in HFS+ format, which as of Hoary (that I can say with certainty), is supported in the Kernel. Your iPod never has to touch a windows computer or a mac if you do not use iTunes. If you need to use iTunes with your iPod and all you have available to you is the Windows version, then Yes, you have to first sync your iPod to iTunes in Windows - so that it converts the format to FAT32 instead of HFS+ (of course, this also removes the journaling capabilities of the hfs filesystem.)

2. I have been able to sync iPods to iTunes running in VMWare, but I am not 100% sure that the driver support you would need in order to do this is available in XOver.

--

If you don't need to use iTunes, or have used iTunes on your Windows box to burn cds that you have then moved to your Ubuntu computer, then you do not need to format your iPod with Windows iTunes - and can use gnupod instead (or any of a number of other linux ipod tools.)

That's what I do, for both of my iPods.

---

### Post by x5452 on 2006-04-05
I just today got ubuntu up and running, Im installing it on a friends computer cause we cant afford to buy a new windows for a damn reg key! but whatever, he has an ipod and i have his itunes cd here, is there a wiki somewhere, or HOWTO so i can put itunes in ubuntu so he can sync with his ipod and have songs there?  I dont have an ipod or know anything about how itunes works.  If there is a howto please direct me, thank you much!  
On the other hand, if its not possible please tell me that too  ](*,)

---

### Post by nalmeth on 2006-04-05
Check out post #19 in this thread. Endersshadow gives a good walkthru, you'll see it worked for me. Screenshots and everything.
[http://ubuntuforums.org/showpost.php?p=870912&postcount=19]("http://ubuntuforums.org/showpost.php?p=870912&postcount=19")

---

### Post by JungleBeast on 2006-04-08
I'm afraid to say I need assistance with this. I've followed Endersshadow's amazing instructions, which were really excellent. I've briefly run my ipod on windows and so got the database up and running, and whacked a couple songs on there. I run gtkpod and it can't read the iTunesDB. I get:
[HTML]'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.[/HTML]

I've fiddled around with Edit Preferences in gtkpod and tried various iPod mount points some wrong intentionally, and I still get the same error message. 

There is nothing in my /media/ipod  file, and yet "sudo eject /media/ipod" ejects the pod fine (as does "sudo eject /dev/sde2")

](*,) :confused:    Any ideas?    

Thanks!

---

### Post by endersshadow on 2006-04-08
[QUOTE=JungleBeast]I'm afraid to say I need assistance with this. I've followed Endersshadow's amazing instructions, which were really excellent. I've briefly run my ipod on windows and so got the database up and running, and whacked a couple songs on there. I run gtkpod and it can't read the iTunesDB. I get:
[HTML]'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.[/HTML]

I've fiddled around with Edit Preferences in gtkpod and tried various iPod mount points some wrong intentionally, and I still get the same error message. 

There is nothing in my /media/ipod  file, and yet "sudo eject /media/ipod" ejects the pod fine (as does "sudo eject /dev/sde2")

](*,) :confused:    Any ideas?    

Thanks![/QUOTE]

In gtkpod, go to File>Create iPod's Directories

---

### Post by JungleBeast on 2006-04-08
Thanks for geting back to me so fast! 

I do that, and get: 
```

OK to create the following directories?

/media/ipod/Calendars
/media/ipod/Contacts
/media/ipod/iPod_Control
/media/ipod/iPod_Control/Music
/media/ipod/iPod_Control/iTunes
/media/ipod/iPod_Control/Music/F00
...
/media/ipod/iPod_Control/Music/F19

```

and click "OK" but nothing more happens..

edit: (and there's still nothing under /media/ipod)

---

### Post by endersshadow on 2006-04-08
Then click Read.  Add the files you want, then Sync it.  You're all set to go :-D

---

### Post by JungleBeast on 2006-04-08
If only it was that easy. Read is still grayed out. As is Read iTunesDB in the file menu.
And on reopenning, I still get the same error message.

---

### Post by jbmalone on 2006-04-08
Go to the previous page and look at my post.  I had that problem and tried EVERYTHING possible through Linux, and that was the only way I could ammend the problem.

---

### Post by joey111 on 2006-04-09
@junglebeast; i had exactly the same problem, for my worked that- no windows needed:
1.)go to your /etc/fstab and 
change your /media/ipod or /mnt/ipod mount pointline to that
[B][I]/dev/sda2       /media/ipod     vfat    user,sync,rw,noauto,umask=000 0 0
[/B][/I]
with _sudo kate /etc/fstab_
2.) set in the preferences of gtkpod mountpoint /media/ipod
3.)uncheck handle mounting and importing db automatically (u can change later)
4.)log out, log in, plug ipod (dont know if necessary)
5.)mount the ipod device (e.g. here it is /dev/sda2) with _sudo mount /dev/sda2 /media/ipod_, wait until it has mounted.if it appears later one time to be e.g. to be /dev/sdb2 u can  also mount it manually to /dev/sdb2 /media/ipod, even though sdb2 its not in the fstab file.
6.)open gtkpod from terminal with _sudo gtkpod & _ ( if u start it as root it meant say: cannot open gtk display..). (if it works u can start it however u want later)
7.)u should now be able to do the read thing and create the directories.
tell me if it worked;i am not sure but i think this missing db thing is related to permissions one specified in the fstab.
-can someone tell me what i have to set as path to application if i want the ipod to synchronize to /knotes/korganizer/kaddressbook
-does anyone know how i would exchange the gtkpod icons with those? 
[http://www.kde-look.org/content/show.php?content=36687](http://www.kde-look.org/content/show.php?content=36687)

---

### Post by JungleBeast on 2006-04-09
Cheers guys!  :-D  I changed the end bit of the mount in /etc/fstab   i'm not sure if that was what did it. But just opening it as super user seemed to do it. I had to do it quite a few times, and then after a few more, it just started working fine automatically. :KS 
 So it was definitely a permissions thing, although maybe related to the mount too, it mounts as apple ipod (2)  , and apple ipod just sits there, same as before. But that's fine with me!  
Excellent!  I'm really pleased it's working :-D     I can now enjoy my spanking new ipod and then when i'm ready for more, i'll try and get Vive working. (I had a few issues installing that before, i was just doing the whole lot in one go hoping it would work first time. Hopefully the issues are sorted now gtkpod is properly working..)

---

### Post by sinaen on 2006-04-10
Yay. it seems like you need more help than i :)

Shame that this only describes to make gtkpod work
I dont have the repositories to get to compile the newest gtkpod from source. have any of you any tip. which repositories you use.

and to get this straigt. 
Yamipod - is very good. you can sync/build a list with many folders that sync to your ipod. but you cannot create the directorys needed if you erase them. to do that youll need
gtkpod - that is very nice. but that i find very messy. hard to get to work and yeah. hard to figure out

AmaroK - is to be said to automaticly sync coverart. that have i never experienced. and i dont know how to install the latest version from source either. cause i dont have the f***** repositories :C
and it gets me mad

 youve already cleared out that itunes via crossoveroffice doesnt work with ipod in linux. why i dont know. but id like to figure out.

and the first thing i needed to do was to format it in windows. then it worked in linux and windows. before that nothing happend

now. im not a linux newbie. but i think ipod should be much much much easier in linux. and i do really want to have an ipod-program that doesn't chew up my cpu, when i use it

Feel free to pm me if you have any tip on how to get gtkpod to work properly and the rest of the programs. right now i like yamipod best it supports a lot of file synching. but sometimes "drop" files :/

and yeah gtkpod should be alot easier and simpler. imho

---

### Post by Wallakoala on 2006-04-10
Just to put this out there, the music player banshee is a very good music player and its ipod-syncing is way better than any program I have used.

---

### Post by x5452 on 2006-04-13
anyone figure out the auto unmounting thing?  I did as ender said with setting it up so when i plug the ipod in it mounts, (shows icon on desktop) and opens up gtkpod.  but when im done, i click file>quit in gtkpod, and it just says unmounting of /dev/sda2 unsuccesful, then it closes, and the ipod icon on desktop goes away.  ipod still says do not disconnect, but after 15 minutes i did anyway, the 9 large video files i transferred were all good so nothing got jacked up, but im curious about the error

---

### Post by endersshadow on 2006-04-13
Well, first of all, you don't have to worry about the DO NOT DISCONNECT.  You will *not* harm your iPod.  It's simply a warning that you may leave some junk behind on your OS.  This is especially valid in both Windows and OS X, but since you've unmounted it, you're fine.

What you can do is take it out of your fstab, and when you want to unmount it, simply do a fdisk -l and then find out the sd*2 where it's mounted, and run this command:

```
sudo eject -sv /dev/sdx2
```

Where x is the letter of the sd it's mounted at.

---

### Post by Old Jimma on 2006-10-01
Y'all:

There are my 9 i-opinions:

1st: I hope that Linux users who want to buy a "mp3" player will learn before making their purchase that Linux creates all sorts of nice music file types that are not proprietary, like OGG and FLAC files. However, Apple stuff will not read those OGG and FLAC files. Don't make OGG or FLAC files on your linux machine if you want your iPod to play them.

2nd: There is nice software that will convert those nice Linux music file formats to mp3: I use Sound Converter, but there are many others that might suit your needs better. CHECK THIS SOFTWARE OUT BEFORE BUYING AN IPOD, IF YOU MUST BY AN IPOD. If you are a musician, see my 8th comment, below.

3rd: Apple stuff (iTunes, iPod and Nano) creates files that are "m4a" file format types, If you download songs from the Apple store you will get an m4a file type. Although some destop music players can be confgured to play them, you will have to work at making them do it! 

4th: I know of no software that coverts m4a files to any other file types that Linux and your car CD player prefer. That software might exist, but you will have to look hard to find it. As a Linux user and commuter, you will wish you had it.

5th: If you are a dedicated Linux user and are thinking about purchasing a "iPod clone," READ THE FEATURES OF THE PLAYER CAREFULLY BEFORE MAKING YOUR PURCHASE TO MAKE SURE IT READS THE FILE TYPES THAT YOU WILL CREATE ON YOUR LINUX MACHINE.

6th: If you want to burn your linux music files to  CDs that will be played in your car, then find out what file formats your car's CD player will read. Choose an "iPod clone" that can read the same formats that your car's CD player will read. You will think you are a genious if you do this!

7th: Stick to the music file type that your "iPod clone," car CD player, and Linux music player can use. THIS WILL ENHANCE YOUR MUSIC ENJOYMENT. Otherwise, you will spend hundreds of hours converting files to filetypes to satisfy the requirements of the hardware gadgets that you have purchased. 

8th: There are some very good reasons why musicians might want an iPod. If you play professionally or solo, you can connct an iPod to a PA system and use it very effectively to play high-quality music thru the PA system to be your back-up band. If you are not a musician, then you might have more options.

9th: With all of this said, I think you will wind up creating mp3 files if you want to use music files between a car, your "iPod clone," and your Linux machine.

Sorry to express this opinion that runs against our efforts to create open source products. I'm in favor of open source stuff. However, as the household Linux system administrator and father of 2 sons who have iPods and drive my car, these are the opinions I've settled on at this point in time. 

I hope that you find hardware in your car, linux machine, and "iPod clone" that simplifies your life and enhances your ability to enjoy music. Please let me know if there is something I've overlooked or am not aware of.

Sincerely,
Phil Smith
DULUTH, GA

---

### Post by endersshadow on 2006-10-01
Phil,

As for #3 and #4, you can use [ffmpeg](http://ffmpeg.mplayerhq.hu/) to convert the music files from m4a to mp3, ogg, or whatever you feel like doing.  Thought you should know to make your life easier :)

---

### Post by Old Jimma on 2006-10-07
Endershaddow is correct.

Also, if you'd like to rip your CD's directly to MP3s using Sound Juicer, see 
[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

All the best,
Phil Smith
Duluth, GA

---

### Post by 3rdalbum on 2006-10-08
> now. im not a linux newbie. but i think ipod should be much much much easier in linux.

I'm a Windows newbie but I've been using Linux since the beginning of the year, and Mac OS for over a decade. I agree that iPod-loading programs on Linux suck, but iTunes sucks almost as much. My mother has a Shuffle, and quickly gets tired of all the songs on it; so she asks me to completely change the list.

If I try to delete the songs off the iPod in iTunes, it doesn't actually delete them. I always have to "Restore" the iPod first. I've twice installed the iPod software updater, both times the installer crashed TWICE. The first time I tried to load music onto the pod, iTunes didn't update the database and GTKpod did.

Why don't people complain about crap software on Windows?

---

### Post by Polygon on 2006-10-08
there is an option in itunes for the shuffle that makes it so it creates a random playlist out of the songs in the main library and then syncs them to the ipod. 

itunes is actually a pretty spiffy music player, there are plugins to make it play .ogg files. My only complaint is that the ipod doesnt play ogg files or else i would be very happy getting an ipod.

---

