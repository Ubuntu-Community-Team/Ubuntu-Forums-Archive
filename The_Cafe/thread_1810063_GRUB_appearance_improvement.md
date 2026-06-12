---
title: "GRUB appearance improvement?"
date: 2011-07-22
forum: The Cafe
---

### Post by MG&amp;TL on 2011-07-22
Recently, at my school, I used an Apple Mac that had been dual-booted with Windows so it could use the standard school network and applications/limitations. Anyway, I noticed that the mac version of grub looked considerably better than the current 'purple text' version we have with ubuntu.

As the main message of ubuntu is 'user-friendly', perhaps we could put some thought into redesigning the graphical aspect of GRUB, particularly as most Windows transitionees, myself included, have dual-booted at some point. The grub screen can be intimidating, and looks especially bad on boot. 

I am happy to donate photographs and/or artwork to help, if this is possible?

---

### Post by fjgaude on 2011-07-22
Good thought... likely this will come about in fullness of time. Right now the guys are hard at it getting 11.10 up fully.

Backgrounds are usually never an issue, photos galore!

---

### Post by MG&amp;TL on 2011-07-22
Yes, of course...is 11.10 likely to be a 'significant' release (by this I mean like 11.04 had Unity, and 12.04 will be a LTS) , or are they just ironing out the bugs in Unity?

Is there somewhere I can get the source code for GRUB (if there is any?), that way I can experiment and see what happens.

Good luck with 11.10 guys!

---

### Post by MG&amp;TL on 2011-07-22
Or there again, just downloaded the source and read the license, and apparently distributing unedited copies is allowed, but not editing it in any way. Bang goes the theory. :D

---

### Post by PhantmKllr on 2011-07-22
> **MG&TL said:**
> Yes, of course...is 11.10 likely to be a 'significant' release (by this I mean like 11.04 had Unity, and 12.04 will be a LTS) , or are they just ironing out the bugs in Unity?

Is there somewhere I can get the source code for GRUB (if there is any?), that way I can experiment and see what happens.

Good luck with 11.10 guys!
11.10 is a somewhat "significant" release, considering the switch from the GNOME 2 (GTK 2) stack to the GNOME 3 (GTK 3) stack, but I don't think that work is being done to improve GRUB's apperaance.

Perhaps you should voice your idea at the Ubuntu Brainstorm.

[http://brainstorm.ubuntu.com]("http://brainstorm.ubuntu.com")

---

### Post by godhika on 2011-07-22
> **MG&TL said:**
> Yes, of course...is 11.10 likely to be a 'significant' release (by this I mean like 11.04 had Unity, and 12.04 will be a LTS) , or are they just ironing out the bugs in Unity?


Well 11.10 sees the change to Gnome3 and also Gtk3 which means big changes behind the scene

---

### Post by hugmenot on 2011-07-22
> **MG&TL said:**
> Or there again, just downloaded the source and read the license, and apparently distributing unedited copies is allowed, but not editing it in any way. Bang goes the theory. :D

Read again. It&#8217;s not so simple. There might be simple explanations of the GPL on the web selsewhere too.

---

### Post by fjgaude on 2011-07-22
> **MG&TL said:**
> Or there again, just downloaded the source and read the license, and apparently distributing unedited copies is allowed, but not editing it in any way. Bang goes the theory. :D

It's open source as far as I know. Here's their homepage:

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by MG&amp;TL on 2011-07-22
Oops, I was reading the licence for the licensing document...:oops:

It is indeed open-source. I shall get to work understanding how it works...please tell me it's written in C++...please...[-o<

---

### Post by edujose on 2011-07-22
Could it be possible that your school uses BURG instead of GRUB?

BURG is derived from GRUB 2 and allows for fancier backgrounds, icons instead of text and other graphical goodness.

I haven't used it myself, but saw other people installing and customizing it for dual boot between windows and ubuntu.

You can see some some BURG screenshots [in its site]("http://code.google.com/p/burg/wiki/Screenshots").

---

### Post by cariboo on 2011-07-22
Burg isn't being maintained any more, so that may not be a good choice,

---

### Post by MG&amp;TL on 2011-07-22
Nope, not burg, I think it's definitely the Mac OSX one.  It looks like this:

EDIT: Okay, copying and pasting images don't work. I'll reupload normally.



Or similiar. I think it looked a little better than this at school.

---

### Post by MG&amp;TL on 2011-07-22
Nope, I'lll have to upload.[IMG]http://www.google.com/imgres?imgurl=http://www.hal-pc.org/journal/2006/06_may/trumors_image010.jpg&imgrefurl=http://forum.voodooprojects.org/index.php%3Ftopic%3D1771.0&usg=__s2Q4dZ-JOPsxUiV8ByL_56Ldtvs=&h=275&w=400&sz=11&hl=en&start=0&zoom=1&tbnid=ThKhzawCZlckiM:&tbnh=164&tbnw=209&ei=948pTuyYKIrOswa2mtGADA&prev=/search%3Fq%3Dmac%2Bbootloader%26um%3D1%26hl%3Den%26client%3Dubuntu%26sa%3DN%26channel%3Dfs%26gl%3Duk%26biw%3D1303%26bih%3D649%26tbm%3Disch&um=1&itbs=1&iact=rc&dur=316&page=1&ndsp=16&ved=1t:429,r:2,s:0&tx=107&ty=88[/IMG]

Try 'insert image' this time...I know you can upload things from your computer via the attachments, but I want to see what else works.

---

### Post by MG&amp;TL on 2011-07-22
Last try...I'm uploading the idea to brainstorm as we speak.

---

### Post by MG&amp;TL on 2011-07-22
[http://brainstorm.ubuntu.com/idea/28306/](http://brainstorm.ubuntu.com/idea/28306/) Thanks for pointing me to Brainstorm! :)

---

### Post by edujose on 2011-07-22
Hmm, didn't know BURG is unmaintained. Sorry for the suggestion.

Also found that another reason not to use BURG is that it seems to conflict with Plymouth.

So better stay with GRUB 2, though no icons and fancy graphics for us :-)

---

### Post by MG&amp;TL on 2011-07-22
Although something like BURG would be a great alternative, Ubuntu seems to be interwoven with GRUB, so a new bootloader would require a serious rethink of the whole OS. I thought we could perhaps modify the bootloader slightly so that it's graphical. I don't know precisely how much work that it would entail-for me, give me six months and access to the web and I could probably do it, for a GRUB expert/author, a day or two at most.

---

### Post by MG&amp;TL on 2011-07-22
Hypothetically, should I modify something in grub and wish to test it without installing it on my machine, how would I go about doing this?

---

### Post by seeker5528 on 2011-07-22
> **MG&TL said:**
> Last try...I'm uploading the idea to brainstorm as we speak.

[img]http://ubuntuforums.org/attachment.php?attachmentid=198101&stc=1&thumb=1&d=1311372257[/img]

Looks like the normal OS X bootloader to me, and I can't find any indication that OS X uses grub. :confused::confused:

Later, Seeker

---

### Post by MG&amp;TL on 2011-07-22
I was using it as an example that we could do better, as our current one, compared to all our compiz-fusion finery, is alittle lacking.

---

### Post by cecilpierce on 2011-07-22
> **MG&TL said:**
> Hypothetically, should I modify something in grub and wish to test it without installing it on my machine, how would I go about doing this?

I use BURG and I put it on a flash drive just in case something goes wrong with the 2 HD's here, someone started theming GRUB awhile back but it never really worked to good, its still around some where.>

[http://www.google.com/search?q=grub+themes&hl=en&biw=1280&bih=933&prmd=ivnsfd&tbm=isch&tbo=u&source=univ&sa=X&ei=kAwqTuRxjYK2B43NhdgC&sqi=2&ved=0CDEQsAQ](http://www.google.com/search?q=grub+themes&hl=en&biw=1280&bih=933&prmd=ivnsfd&tbm=isch&tbo=u&source=univ&sa=X&ei=kAwqTuRxjYK2B43NhdgC&sqi=2&ved=0CDEQsAQ)

Good luck, hope to see some thing new with GRUB

---

### Post by seeker5528 on 2011-07-22
> **MG&TL said:**
> I was using it as an example that we could do better, as our current one, compared to all our compiz-fusion finery, is alittle lacking.

I thought something like that might be the case, but was unsure since you referred to it as grub. 

Hack on. ;)

Later, Seeker

---

### Post by MG&amp;TL on 2011-07-22
You'll be lucky cecil! :) Ok, will look into usb drives to see whether I can do that, as I don't really want to muck up system.

Do I have any (preferably experienced) helpers on my quest? :P

---

### Post by cecilpierce on 2011-07-22
I wish I had the experience I would have done it long ago :lolflag:
All I know is trial and error editing, mostly errors, but its fun  and You learn from mistakes.
I was always interested in programing but never had the time, now I am retarded, I mean retired and to old to start stuff that I cant remember or even sometimes cant read all my notes !!!
Theres some real good people on the IRC channel #grub if you want to get on there and ask, they have been a lot of help to me.
Well I hope you can get it going, let me know, 
Cecil

---

### Post by MG&amp;TL on 2011-07-23
Ok... setting up a dual-boot ubuntu on Vbox. Will set grub up there. 

Hack on! :lolflag:

---

### Post by gooeykablooey on 2011-07-23
Check out GRUB themes. I was looking into this a while ago, and there are some pretty cool things you can do. I don't think you need to do any modifications of the GRUB source, you just need to play around with the grub.conf file or something like that. I had a Wiki stored in my bookmarks, but the link no longer works, though a quick search on google should get you started.

---

### Post by buzzmandt on 2011-07-23
this looks really good, a little dated now but still looks good:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

i changed my background in grub2 with this
[http://ubuntuguide.net/an-easy-way-to-addchange-grub2-background-image-in-ubuntu-11-04](http://ubuntuguide.net/an-easy-way-to-addchange-grub2-background-image-in-ubuntu-11-04)

---

### Post by larn on 2011-07-23
I'm using the plain Grub in Puppy Linux (think variation of Ubuntu), Grub2 might be more user friendly.  There is not a lot of options in basic Grub but you can install a minimum color splash image and change text in Grub.  It works if you can get the file size below 350 kb or so.  Grub installs a menu.1st file in folders /boot/grub/ and changing code is like html web page code from a text editor is all I'm using in Puppy, backup safeguard is to make a back up copy of file, and,  boot off CD if need to access and make changes to the file.  I used Gimp to adapt an image to 640x480 size and 14 colors, save as background image and zip the file, am novice too but learned by searching with questions, lot of fun in that.

---

### Post by larn on 2011-07-23
After studying how to work with Grub menu.1st, I have found that the text and border gets in the way of the image.  I think I have found a solution in this blog to add a line for hidden menu, got this idea which I haven't tried yet.  That border looks the size of when it asked in the install of Grub, what size resolution do you want (in effect) and I chose the default of 640x480, thinking that border crossing over the fullsize image is size 640x480.  Would try bigger resolution next time.  Here is link to hide text, middle of page somewhere:

  	 	 	 	 	 	  [http://ubuntuforums.org/showthread.php?t=757623&highlight=grub+text](http://ubuntuforums.org/showthread.php?t=757623&highlight=grub+text)

---

### Post by drs305 on 2011-07-23
Adding a Grub background is very easy in Grub 1.99 (Natty). You can just drop an approriate image in the /boot/grub folder and run "sudo update-grub". For the details, here is a thread:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

If you want complete theming (buttons, images, etc), here is a really compreshensive guide:
[http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html]("http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html")

---

### Post by MG&amp;TL on 2011-07-23
Thanks for all the help guys...if it's this easy then why haven't canonical adopted it? It's not like an image and a GUI is going to take up that much more space, and they must have taken up a huge amount more disk space when they got Unity as well as GNOME.

And here's me about to try and reprogram the thing entirely, and will undoubtedly fail...;)

Never mind, will follow the links and see how much more space the updated grub takes up. I shall see if I can follow the default Ubuntu theme and background.

If I get it working, I shall post screenshots.

Thanks once again people. :)

---

### Post by MG&amp;TL on 2011-07-23
Have downloaded the tarball from drs's second link...:D great reading, thanks drs, and the other people that have given me links. 

It feels good to be making/programming something that is actually useful. The closest I've ever come to useful was a brute force prime-generator that worked, and then, myteriously, didn't.

Thanks for all the help, people and I will keep you posted.

My brain's fried from the guide though, so I shall call it a night.

---

### Post by drs305 on 2011-07-24
> **MG&TL said:**
> My brain's fried from the guide though, so I shall call it a night.

I don't think I've still made it through the entire guide...

Let us know how it works.

;-)

---

### Post by MG&amp;TL on 2011-07-24
It's going good so far, just got to the 'basic' theme, shall get all the ubuntu fonts and graphics-y things so that it matches, should anyone want to have an ubuntu grub.  I shall have to see how to distribute it...nah, you won't want my rubbishy one.

---

### Post by cecilpierce on 2011-07-24
> **MG&TL said:**
> It's going good so far, just got to the 'basic' theme, shall get all the ubuntu fonts and graphics-y things so that it matches, should anyone want to have an ubuntu grub.  I shall have to see how to distribute it...nah, you won't want my rubbishy one.

I'll take it, anything is better then plain ole grub blah :P

Thats why I use outdated burg loader, easy to fiddle with :D

Good luck, 
Cec

---

### Post by MG&amp;TL on 2011-07-24
Thanks Cecil-this is great! My software fiddles are appreciated. Maybe I should get into fiddling rather than programming...:)

Yep, Ubuntu forums allow me to upload tarballs, so I shall do that once I'm done. I expect this to be about Wednesday. :)

---

### Post by MG&amp;TL on 2011-07-24
DRS- I run update-grub (as root, don't worry about that): 

-without a space in between "GRUB_THEME=" and the path to the theme text file, it finds the theme, and then displays a black version of the normal theme on GRUB on reboot. 

-with a space, it says that I do not have permission to the text file. Any ideas? I'm sure I'll crack it eventually, but if you have any tips, it would help. Thanks!

---

### Post by drs305 on 2011-07-24
> **MG&TL said:**
> -without a space in between "GRUB_THEME=" and the path to the theme text file, it finds the theme, and then displays a black version of the normal theme on GRUB on reboot. 

-with a space, it says that I do not have permission to the text file. Any ideas? I'm sure I'll crack it eventually, but if you have any tips, it would help. Thanks!

There shouldn't be a space, and you should probably put the entire entry after the **=** in quotes. If you attach what you are using I might be able to see what's happening. Note: I haven't played with themes - just backgrounds and font colors so my 'expertise' in this area is only that I know how the devs have written other Grub 2 sections.

You could try the theme in pieces - such as first trying your background image separately to make sure it works correctly (without including it in a theme).

---

### Post by MG&amp;TL on 2011-07-24
Done the background image. Here's the attachments. Thanks DRS. Theme.txt is attached, grub wouldn't attach for some reason, so here it is:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_THEME=/boot/grub/themes/ubuntu/theme.txt
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by drs305 on 2011-07-24
After spending a few minutes reviewing things I can tell troubleshooting this will take more time than I have to spend on it at the moment.

A couple of things I would investigate:

1. Is the theme reference incorporated into the grub.cfg file (is your theme.txt) referenced therein? I checked to ensure the "GRUB_THEME" entry is an acceptable entry in /etc/default/grub (it is) but when I just add that to /etc/default/grub it is not automatically incorporated into grub.cfg. 

I saw in the attachments to the Grub theming manual that he includes a 08_ script which may add some things missing in the default 05_debian_theme script.

2. I noticed you have a "+ boot_menu" line in your theme.txt  
It looks like an unusual entry to me to have it start with the **+** symbol. But I'm not speaking from any depth of knowledge here.  ;-)

---

### Post by MG&amp;TL on 2011-07-24
I wasn't asking you to do it for me! :P

Yep, I'll have a look at that, and the script, too. And I forgot to take the line-numbering out of his source code...:oops:

---

### Post by drs305 on 2011-07-24
> **MG&TL said:**
> I wasn't asking you to do it for me! :P

I know. 

I just like trying to solve Grub 2 puzzles, as I'm always learning from the questions asked about G2. Fortunately now, as opposed to when G2 first came out, I can usually tell if a question is within my capability of researching/solving or not. It sometimes takes me a few minutes to come to this conclusion, but there was a time I'd spend an hour or more before realizing I had no clue and wasn't likely to get one ...  :-)

---

### Post by MG&amp;TL on 2011-07-24
I know the feeling...:D Sorting out my mum's (crashing badly) laptop at the moment, catch up with things in a while.

---

### Post by MG&amp;TL on 2011-07-24
Thanks, DSR. Tried from the bottom up approach and it's working, although because I've only got a title at present, I just have to wait for the timeout. Great stuff.

The rest is just creative, now. :D

---

### Post by MG&amp;TL on 2011-07-24
Version 0 out now! (now includes Ubuntu default background, and...wait for it... Ubuntu default title!)

Screenshots will arrive as soon as I work out how to put this in Virtualbox. :)

---

### Post by MG&amp;TL on 2011-07-24
Progress is swift, and I think I will call it a night. However, I have got an improved background (comped in GIMP), and menu entries.

---

### Post by towheedm on 2011-07-24
The provided 08_gfxmenu_theme script file is only required for GRUB2 versions prior to 1.98+20100804.  Please keep in mind that ANY errors whatsoever in your theme.txt file WILL cause the theme not to display.  Instead GRUB falls back to plain text mode.

I get it that you're testing this on a MAC.  I did not have access to a MAC to test.  I would appreciate if you PM me with any problems you may encounter using it with the MAC.  I will probably wait for a possible 2.0 release before releasing another edition as most of time is now spent in learning to build the kernel.

Looking at your theme.txt, the color values should not be enclosed in parenthesis ie:"255.255.255" and not "(255,255,255)".

Thanks
Towheed Mohammed

---

### Post by cecilpierce on 2011-07-24
Since your trying grub I thought I would look at it again to see what gives,
so I put 'GRUB_THEME=/boot/grub/themes/ubuntu2/theme.txt' in /etc/default/grub, then did update and installed grub on my second drive (sdb).
Reboot gave me nice background but the menu list was in the upper left hand corner, bummer :(
Well getting late for you I guess, I will look at it some more tomorrow maybe have better luck :P

---

### Post by towheedm on 2011-07-24
That's because your screen resolution does not correspond to the resolution that the theme was designed for.  Try different resolutions to see the effect of this.  If you have downloaded my grub guide, see the section on making your theme resolution independent on Pg 29.

---

### Post by cecilpierce on 2011-07-24
> **towheedm said:**
> That's because your screen resolution does not correspond to the resolution that the theme was designed for.  Try different resolutions to see the effect of this.  If you have downloaded my grub guide, see the section on making your theme resolution independent on Pg 29.


Thanks Towheed, I will try that later, I've been on this thing all day and getting sleepy,
Cecil

---

### Post by Paddy Landau on 2011-07-25
> **MG&TL said:**
> [http://brainstorm.ubuntu.com/idea/28306/](http://brainstorm.ubuntu.com/idea/28306/) Thanks for pointing me to Brainstorm! :)
This idea was already in Brainstorm (24 May):
[http://brainstorm.ubuntu.com/idea/27987/](http://brainstorm.ubuntu.com/idea/27987/)
Go there and add your votes.

---

### Post by MG&amp;TL on 2011-07-25
Three things:

1) I'm NOT on a Mac, that's just where I got the idea from.

2) @Paddy, Sorry, I know that now, but I did look in the duplicates list it gave me when I was posting, and it wasn't in there.

3) Have fixed the bug with the resolutions now, following the guide, so it should now work on any resolution (within reason) It also has a new background, with an Ubuntu plymouth logo comped in.

Text is now centred. After this, I shall move on to icons and other such delicacies. Theme.txt is attached. :D Feel free to try, although I don't guarantee it will work, therefore I recommend Virtualbox or similiar. :)

---

### Post by MG&amp;TL on 2011-07-25
And while I remember, here's the Desktop image. Put it in the same folder as theme.txt.

You'll have to create the fonts yourself, as Ubuntu forums doesn't support fonts.

---

### Post by Starks on 2011-07-25
> **PhantmKllr said:**
> 11.10 is a somewhat "significant" release, considering the switch from the GNOME 2 (GTK 2) stack to the GNOME 3 (GTK 3) stack, but I don't think that work is being done to improve GRUB's apperaance.

Perhaps you should voice your idea at the Ubuntu Brainstorm.

[http://brainstorm.ubuntu.com]("http://brainstorm.ubuntu.com")

Developers don't care about Brainstorm.

If you don't file or add to a bug on launchpad against grub, your concerns or desires don't exist.

---

### Post by Paddy Landau on 2011-07-25
> **Starks said:**
> Developers don't care about Brainstorm.
What is it there for, then? Have I been wasting my time on there? I know it's moderated well, so *someone* is looking at it. I had hoped that it was someone with the authority to do something.

---

### Post by MG&amp;TL on 2011-07-25
I thought it was just something where people voice their thoughts myself...like the community cafe here. Anyway, shall continue to work on GRUB, and shall work on having an install script, and .deb package so that it is distributable, if only for Cecil. :D

---

### Post by cariboo on 2011-07-25
There is a member of the Community relations team that looks at Brainstorm, just before UDS, they create a digest of the ideas, and submit it to the developers. Whether they get acted on, I'm not sure.

---

### Post by dino99 on 2011-07-25
> **cariboo907 said:**
> There is a member of the Community relations team that looks at Brainstorm, just before UDS, they create a digest of the ideas, and submit it to the developers. Whether they get acted on, I'm not sure.

yes thats it, some ideas picked for UDS.
so reporting bugs is the way to get things done quicker if devs dont declare them as "low" or as "wish", meaning "if we have time and dont know what to do, maybe we glance at it, but not sure"

---

### Post by Paddy Landau on 2011-07-25
> **MG&TL said:**
> Anyway, shall continue to work on GRUB...
Are you working on Grub or Grub2? If your changes are good enough, I guess that you could submit it to Canonical for official inclusion; but I'm guessing that the company would require Grub2.

---

### Post by Starks on 2011-07-25
> **Paddy Landau said:**
> What is it there for, then? Have I been wasting my time on there? I know it's moderated well, so *someone* is looking at it. I had hoped that it was someone with the authority to do something.

No. It's just a useless feel-good tool with zero commitment or accountability.

It's like the Simple English version of Wikipedia.

---

### Post by MG&amp;TL on 2011-07-25
It's in GRUB2. Wow, I didn't know that Canonical takes all comers, I assumed you had to be signed on as a developer. My laptop has crashed at the moment, so when I've sorted that out, work will continue.

---

### Post by cecilpierce on 2011-07-25
> **MG&TL said:**
> I thought it was just something where people voice their thoughts myself...like the community cafe here. Anyway, shall continue to work on GRUB, and shall work on having an install script, and .deb package so that it is distributable, if only for Cecil. :D

WOW ! thats great but then I wont have nuttin to fiddle with   :(

---

### Post by MG&amp;TL on 2011-07-25
Or there again not...you could always fiddle after you've installed it. Just change a few lines here or there. Or just not bother, I have a feeling this will get postponed, as my laptop is running off cd at the moment,  and I'm busy from wedensday onwards :(

Maybe in a couple of weeks...:(

---

### Post by cecilpierce on 2011-07-25
Oh no !

What are you using over there, a Commodore 64 ?
I have old clunkers here and a lot of spare parts but no lap tops, there too hard to work on and expensive  :P 

Well, good luck with that gizzmo, (maybe a hammer will fix it!)

Later, Cecil

---

### Post by MG&amp;TL on 2011-07-26
I didn't choose a laptop; you can get easier, more compatible spec with a desktop. Might be back on the grub thing, I have a windows recovery disk now. It's a sony VAIO, and I accidentally deleted one of the grub partitions. :(

spare parts a-plenty here too...none of them compatible with laptops...sigh.:)

---

### Post by meborc on 2011-07-26
> **MG&TL said:**
> I didn't choose a laptop; you can get easier, more compatible spec with a desktop. Might be back on the grub thing, I have a windows recovery disk now. It's a sony VAIO, and I accidentally deleted one of the grub partitions. :(

spare parts a-plenty here too...none of them compatible with laptops...sigh.:)

Hope you have luck in restoring your grub. Check Ubuntu wiki for instructions

---

### Post by MG&amp;TL on 2011-07-26
Started a thread for them. :D

---

### Post by cecilpierce on 2011-07-26
@MG&TL

Maybe ya need a good boot loader ! hehehe :P

[http://www.addictivetips.com/ubuntu-linux-tips/manage-plymouth-burg-grub-with-super-boot-manager/](http://www.addictivetips.com/ubuntu-linux-tips/manage-plymouth-burg-grub-with-super-boot-manager/)

---

### Post by MG&amp;TL on 2011-07-26
Maybe I do....bwahahaha...8-[

---

### Post by cecilpierce on 2011-07-26
> **MG&TL said:**
> Maybe I do....bwahahaha...8-[

I'm still waiting to "fiddle" with this all new and improved grub gadget :P

What are you gona call it, grubby ???
:P :P :P

---

### Post by MG&amp;TL on 2011-07-26
If you take it from drs's post, you can get instructions.

---

### Post by cecilpierce on 2011-07-26
> **MG&TL said:**
> If you take it from drs's post, you can get instructions.

Having any luck with your flap-top ?

---

### Post by MG&amp;TL on 2011-07-26
Yup, cecil, flap-top has stopped flapping now, but only because I used a windows recovery cd. :(

Ubuntu is still dead. <sniff, sniff>

I shall make windows the whole partition, and use vbox to develop my GRUB spinoff/whatever you call an edited grub.cfg file. Project should be back online by tomorrow, and hopefully complete in six weeks or so, or possibly six days, you can never tell how much trouble something is going to cause you.

Thanks for all the concern and morale-boosting cecil, and drs for the link :D

Apologies for delay. ;)

---

### Post by MG&amp;TL on 2011-07-27
Laptop stopped flapping now, so am Installing Vbox as of now. Just thought I'd keep you posted. This a record thread for me in terms of views. :D

---

### Post by Paddy Landau on 2011-07-27
> **MG&TL said:**
> This a record thread for me in terms of views. :D
Even though a good-looking Grub is a "nice-to-have" rather than a productivity booster, the fact that it provides a first impression of Linux for most people (usually Windows users) makes it important.

Are you installing the latest version of Virtual Box (version 4.1.0)?

---

### Post by MG&amp;TL on 2011-07-27
I'm literally just installing it from the site, so it probably will be the latest stable release. Let you know how I get on. 

I very much agree about grub, that was the reason I volunteered.

---

### Post by cecilpierce on 2011-07-27
> **MG&TL said:**
> Laptop stopped flapping now, so am Installing Vbox as of now. Just thought I'd keep you posted. This a record thread for me in terms of views. :D

Good afternoon (morning here) MG&TL, dont know which one is you,ha
glad you have your puter working again.

I guess this thread is popular because a lot of people would like to see something that just works :P

I had one of three O.O. installs crash yesterday and cant get it right, I think its the nVidia crap, its always giving people problems.

Well carry on, just thought I'd say HI!

Good luck.
:KS

---

### Post by MG&amp;TL on 2011-07-28
Update: GRUBby has got to the point he was before laptop crashed. Screenshot attached. Criticism please! :)

I will continue to develop, but obviously I need to know how people would like to see it go; some things are possible and some are not; but I will do my best! [SIZE="1"]<what am I letting myself in for?> :confused:[/SIZE]

---

### Post by cecilpierce on 2011-07-28
> **MG&TL said:**
> Update: GRUBby has got to the point he was before laptop crashed. Screenshot attached. Criticism please! :)

I will continue to develop, but obviously I need to know how people would like to see it go; some things are possible and some are not; but I will do my best! [SIZE="1"]<what am I letting myself in for?> :confused:[/SIZE]

ALOT of time !!! but you got it going, nice background but im half blind and cant see the text to good.

Can you make it look something close to this:

---

### Post by MG&amp;TL on 2011-07-28
Sure can. I am gratified to see my thread in the background of that image ;)

Sorry, it won't go any bigger unless I install it for real; and i won't be able to take screenshot then. You could try blowing it up; press the control and '+' button on your machine. In fact, actually, there's a magnifier in orca, isn't there?

In fact, the tutorial I'm following gives a result very close to that; I'm just trying to deliver an Ubuntu theme so that the devs take note. :D

Right, back to work then!

---

### Post by drs305 on 2011-07-28
I spent a couple of hours yesterday working my way through forum member *towheedm's* Theming guide. 

All in all I came up with fairly good results. A couple of items still need work on my system. I didn't find any errors in the guide and the few items I didn't get working may be attributed to changes in the Grub 1.99 version of Grub.

I'll be looking forward to the results of your efforts!

---

### Post by cecilpierce on 2011-07-28
@MG&TL

I can see it ok its the dark on dark, I make one a light color, kinda sets it off better for me any how.
Have some fun as the S.u.S.E. people say.

Here is another ubuntu shot:

---

### Post by MG&amp;TL on 2011-07-28
Thanks guys-cecil; are these your own efforts? They're really good!

Things like rotary timeouts, a decent terminal window, and compatibility/install scripts coming soon-I will have laptop for next ~two weeks, but no internet, so I WILL be working on it, but no feedback I'm afraid. :(

Ta-ra for now, see you in two weeks, hopefully with re-designed grub, MG&TL.

---

### Post by MG&amp;TL on 2011-08-07
$%^& Those icons! :evil:

The icons just refuse to appear, but never mind, I shall cut the icons for now and see if I can get the other stuff to work. Sorry folks, have spent two weeks trying to get <icons> of all things to work. Everything else works fine though.

Oh, btw, a call for graphics artists, any works you could donate would be fantastic, as every time I need something new I have to design and edit it (slowly!) in Vbox, as for some reason the provided software does not seem to work. :(

A background is the most pressing thing at the moment. Something cool, like cecil's screenshots, but DON'T put anything like text or the loading circle on  there, I will program that in 'on top'. Thank you!

---

### Post by MG&amp;TL on 2011-08-07
@cecil:

TL is me, MG is my brother, only one e-mail account and he wanted a UF to start with.

---

### Post by cecilpierce on 2011-08-07
I couldn't get the icons to appear in grub either, thats one reason I switched over to burg,
good to see ya back from your vacation :P

---

### Post by MG&amp;TL on 2011-08-07
Hmmm...Suspect it may be the version of grub...the guide I'm mostly following is technically for GRUB 1.98xxxxxxxx, whereas Ubuntu uses 1.99. Hence inconsistencies in the instructions, so I usually have to search for something if I can't find it immediately.

Thanks...back to work on Ubuntu! Wasn't much of a holiday, tbf. Anyways...

Maybe I'll drop a line to the GNU people and see whether they have any advice-they must do, they wrote the thing! Will update on progress later tonight-am aiming for working features rather than aesthetics at the moment. Oh, and if anyone wants to donate graphics (please!-it's taking me half an hour per graphic at this rate (I hate Vbox!) only for me to find it doesn't look right anyway. I shall have an install script soon, once I've learned to bash script. That'll be the easy bit :))

Currently I'm using the graphics that came with the guide, which are frankly hideous. Hence hideous screenshots. :(

---

### Post by MG&amp;TL on 2011-08-07
Updated to include highlighted menu entries, support for small resolutions (in that the text doesn't fall off the edge any more) and a separate menu area. Not big advances, but an improvement, I feel. Will work on graphics and readability as soon as it works. :D

Screenshot attached. Sorry about abysmal resolution, but it's a virtual machine and I haven't got it to go any bigger yet.

Will now work on an install script. (I've got a little bored with grub for the minute) 'proper' grub coming your way. 

V.1.0.0 (development release!) ;)

---

### Post by cecilpierce on 2011-08-07
Looks good !
You should use your avatar for a background
:P

---

### Post by Blasphemist on 2011-08-07
MG&TL- Have you looked at the resulting entries that come from using a custom script that uses labels and symlinks? I'm just thinking that not only resolves multi boot issues in it's own right but it also produces clean, clear consistent output for your display. 

I like what you are doing and look forward to using it. This will spur me to finish getting symlinks and my custom script finished to work right with non-ubuntu distros. I have some work to do with Fedora and openSUSE to finish that and I'll try to do it monday. If you don't have that already, I'll be glad to pass it on to you with whatever documentation is needed (mostly for the non-ubuntu distros).

I also offer this site for graphics you might want to think of using if they'll work. Just click the galleries and you'll see lots of interesting distro neutral tux graphics. [http://www.nd.edu/~ljordan/linux/contents.html](http://www.nd.edu/~ljordan/linux/contents.html)

---

### Post by MG&amp;TL on 2011-08-08
Thanks a lot blaspemist...did have a look at symlinks and shorter name tags, (in fact 'Gentoo' on that list is a fake, will just loop back to GRUB...), but couldn't work out how to remove the originals, and if I tried to edit the original's string value (somewhere in /etc/grub.d/ btw.) it would crash (go back to default grub) or not show any change. Any ideas?

Will have a look at the graphics :) Although if this ever makes it into the repositories (although I doubt it!), I'm sure the Ubuntu quality control people will have lots of official graphics to stick in there.

@cecil, yeah, I love my avatar, have you seen the films? :)

---

### Post by TheNosh on 2011-08-08
> **MG&TL said:**
> Although something like BURG would be a great alternative, Ubuntu seems to be interwoven with GRUB, so a new bootloader would require a serious rethink of the whole OS.

No, sir. You can use GRUB, GRUB 2, BURG, LILO, EFI, or even the Windows bootloader with Ubuntu. 

Probably others as well, but I haven't checked.

---

### Post by MG&amp;TL on 2011-08-08
OK...will BURG or LILO recognize other OS partitions? I understand they were discontinued for a reason? Thanks for the info though.

In the process of writing shell script now, so I should have something for you soon. Sorry to use this site as file hosting, but I'm guessing that's why you are given five upload options at a time.

---

### Post by TheNosh on 2011-08-08
> **MG&TL said:**
> OK...will BURG or LILO recognize other OS partitions? I understand they were discontinued for a reason? Thanks for the info though.

In the process of writing shell script now, so I should have something for you soon. Sorry to use this site as file hosting, but I'm guessing that's why you are given five upload options at a time.

BURG was based on GRUB 2, so there's no reason it shouldn't still work. To put that in perspective, the original GRUB was discontinued when GRUB 2 came out, and it still works fine.

LILO is still maintained.

In other words, both will recognise other OS partitions without problem.

---

### Post by MG&amp;TL on 2011-08-08
Ok...well, I suppose I've put a lot into this project now, so I shall continue to post things for GRUB2, but I will look into alternatives.Feel free to use the thread to post alternatives and theme installers.:D

Install script in next post, along with 'dependencies'-images and fonts.

---

### Post by MG&amp;TL on 2011-08-08
Ignore all of these, sorry, I made a mistake. Find my last post, detar the attachment to your desktop, call it 'installer' if it isn't already, then run 'install.sh' PLEASE, PLEASE be careful. Run it in Vbox if you're not sure.

---

### Post by MG&amp;TL on 2011-08-08
Place images directly into the 'Installer' folder on your desktop. (oh, btw, this should be able to be removed after use.)

---

### Post by MG&amp;TL on 2011-08-08
More images.

---

### Post by MG&amp;TL on 2011-08-08
And again...

---

### Post by MG&amp;TL on 2011-08-08
Only a few more....

---

### Post by MG&amp;TL on 2011-08-08
Sigh...seven more images left

---

### Post by MG&amp;TL on 2011-08-08
More of them...:( Please tell me that's all of them :lolflag:

Hopefully, they'll come with names like 'terminal_sw.png' If not, tell me and I'll tell you how to manually rename. Sigh. On to text and admin.

---

### Post by MG&amp;TL on 2011-08-08
Ahhhhh....just realised something-this forum supports tarballs, so I shall just tar it and post that. Detar it to your desktop. Then run 'installgrubby.sh' as root. :)

Much simpler.

[SIZE=3]PLEASE BE VERY CAREFUL, run it in Vbox or similiar if unsure. Still what I would term an 'alpha'[/SIZE]

---

### Post by jerrylamos on 2011-08-08
Mac's easy to use??   Only if what you want to do is exactly what Apple wanted you to do.  My wife and I have been on pc's since 1982 using Microsoft and in my case various linux.

Our son and one daughter use Mac's.  When we try their pc's it's a fight to do the things "ordinary users" do.  Tiny little pictures squirreling around.  Hieroglyphics belong on Egyptian pyramids.  We can actually read text so long as it has good contrast and isn't buried in artsy craftsy colors and embedded in pictures.

We can zip down a sorted list so much faster than wandering around the screen full of pictures that don't mean anything to us.

Ever notice a whole lot of information in a page of text vs. the Ubuntu "apps" display which is mostly space and unknown symbols?

Now I do play around with a tablet which uses symbols and tiny text.  The reason for the big symbols is the severe limitations of precision with a big finger on a tiny touch screen.  O.K. if you are only doing a few limited things.  I've one 7" tablet with a keyboard to match.  A bit slow to write an email because of the size but much faster than hunt and peck on a screen keyboard.

So you have choices.  You want a screen with some pictures spaced around it, or a screen with lots of easy to read information on it?

I've got Meerkat here, and Narwhal and Oneiric.  I use unity because that's what we're supposed to be testing.  In my book Unity-2D beats Unity-3D because it doesn't have the Compiz overhead and I like nice clear crisp edges on my pictures not fuzzy stuff and transparent images which are very hard for me to read with any rapidity.

Actually Unity doesn't bug me that much since here I sit with full screen applications, text, videos, etc.

Jerry

---

### Post by MG&amp;TL on 2011-08-08
Did I ever say MAC was 'easy to use' ? <shudder> Definitely not! The bootloader, maybe. And 'easy-to-use' doesn't necessarily mean newbie-friendly...

I suggest running it in virtual box and seeing if you like it...although I suspect not :)

It's not for everybody. Maybe as an option, enabled by default that you could uninstall later. 
I suppose, given time and encouragement, it wouldn't be too difficult to write an editor (like ccsm) for the bootloader. Problem that I forsee is merging c++ and FLTK (my preferred language/library for GUI) and Bash script, which is what linux seems to talk in. Hmmmm. Research time, methinks.

 I do agree with you about Unity 2d. The only thing that does bug me is the lack of windows that snap when you drag them to top or sides. I usually make a point of having both, then using 3d if I'm in the mood, and 2d for serious work or programming.

Anyways. Sorry about the mess I left over the last burst of posts, didn't realise about tarballs. :mad:

---

### Post by cecilpierce on 2011-08-08
Hay TL,
Had a little trouble with the installer but sorted it out, looks good, a little slow acting on the moving buttons gizmo's, its coming out pretty good though.
Keep fiddling  :P

sorry abt the pics, cell phones fault !

---

### Post by cecilpierce on 2011-08-08
> **MG&TL said:**
> Did I ever say MAC was 'easy to use' ? <shudder> Definitely not! The bootloader, maybe. And 'easy-to-use' doesn't necessarily mean newbie-friendly...

I suggest running it in virtual box and seeing if you like it...although I suspect not :)

It's not for everybody. Maybe as an option, enabled by default that you could uninstall later. 
I suppose, given time and encouragement, it wouldn't be too difficult to write an editor (like ccsm) for the bootloader. Problem that I forsee is merging c++ and FLTK (my preferred language/library for GUI) and Bash script, which is what linux seems to talk in. Hmmmm. Research time, methinks.

 I do agree with you about Unity 2d. The only thing that does bug me is the lack of windows that snap when you drag them to top or sides. I usually make a point of having both, then using 3d if I'm in the mood, and 2d for serious work or programming.

Anyways. Sorry about the mess I left over the last burst of posts, didn't realise about tarballs. :mad:

[http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/](http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/)

Check that out, maybe get some new and better ideas.

---

### Post by Paddy Landau on 2011-08-08
> **MG&TL said:**
> I suppose, given time and encouragement, it wouldn't be too difficult to write an editor (like ccsm) for the bootloader.
For Grub, there used to be [startupmanager]("apt:startupmanager") (still available in the repositories) to allow you to make changes easily.

It would be wonderful if we could have something like that again.

EDIT: @cecilpierce: I just missed your post!

---

### Post by MG&amp;TL on 2011-08-08
@cecil-Wow, that's great, you got it working! Pictures aren't that bad...working on scrollbar and circular progress bar now. Did you feel that the progress updates were excessive or did you like them? I did wonder about putting them in.

You mean that there's already something to do this? :mad:

I shall have to install it and then see if it has all the features you want. I shall defer until I have completed this though. :D

Over 100 posts and 2400 views now. Didn't realise such an obscure topic would be so popular...:D

---

### Post by MG&amp;TL on 2011-08-08
Looked more carefully at super boot loader-great ideas, I'll see whether I can get the source and build on top of that. If I could just add an 'appearance' tab...

Is a ppa like apt-get, in that you can get the source via 'apt-get source <package>?

---

### Post by Paddy Landau on 2011-08-08
> **MG&TL said:**
> Didn't realise such an obscure topic would be so popular...:D
It's the first thing a person sees when dual-booting. It's important, silly as it might seem.

> **MG&TL said:**
> Is a ppa like apt-get, in that you can get the source via 'apt-get source <package>?
Yes, exactly. All the repositories are on PPAs.

---

### Post by MG&amp;TL on 2011-08-08
Grubby V.1.1.0 Same process as before...Now includes circular progress bar.

Terminal graphics are being updated soon. I hate that terminal with a passion.

---

### Post by cecilpierce on 2011-08-08
I guess you guys on the other side of the pond went out to eat or a nap!
Just got back from the beach, bike ride, kinda hot then rain and cool down on the way back to the house.

@TL (whats tt stand for, Tough Love?)

Cant wait to try Grubby V.1.1.0.

@Paddy

I forgot about that "startupmanager" it was good but nobody went with it.
I like BURG but its author has quit to, at least for now :(

---

### Post by Paddy Landau on 2011-08-08
> **cecilpierce said:**
> I forgot about that "startupmanager" it was good but nobody went with it.
I like BURG but its author has quit to, at least for now :(
Yes, we have to go with what is being supported, otherwise whatever you do will become obsolete fast. It's good that someone (you) has decided to run with this.

Once you're done, you'll have to find out how to get your work back into the mainstream.

---

### Post by TheNosh on 2011-08-08
> **Paddy Landau said:**
> Yes, we have to go with what is being supported, otherwise whatever you do will become obsolete fast. 

That's not entirely true, especially with bootloaders. There's optimisation that get's done, but very little will actually stop working. You can get an absolutely ancient version of GRUB to work fine still.

---

### Post by cecilpierce on 2011-08-08
@Paddy
You said it, "The first impression of linux is GRUB",to me is a + and so many people have fiddled with it and we still have grub 1.99? When will grub2 get here, I hope its in my life time! 

I use a 40_custom file that hardly needs editing so I really don't update anymore,

---

### Post by MG&amp;TL on 2011-08-08
TL-"TuxLove" :roll:#-o:oops::shock: - I didn't make the account, although I'm the sole user now. :(

Just how complicated is BURG's source code? I could switch the aim of the project to updating BURG? It really depends on what people want-I've certainly learned a lot and I'm happy to carry on learning as long as there is demand.

@cecil-you're right, we on the other side of the pond took a nap...:)

---

### Post by cecilpierce on 2011-08-08
> **MG&TL said:**
> TL-"TuxLove" :roll:#-o:oops::shock: - I didn't make the account, although I'm the sole user now. :(

Just how complicated is BURG's source code? I could switch the aim of the project to updating BURG? It really depends on what people want-I've certainly learned a lot and I'm happy to carry on learning as long as there is demand.

@cecil-you're right, we on the other side of the pond took a nap...:)

Well to me its quite complicated because I'm not a coder, just a fiddler :P
I just DL it from here:
[http://code.google.com/p/burg/downloads/detail?name=burg-bzr-1832.zip&can=2&q=](http://code.google.com/p/burg/downloads/detail?name=burg-bzr-1832.zip&can=2&q=)
just to see what was in there. It looks like grub, almost the same I guess?
Theres a lot of grub and burg info out there if any body is ambitious enough.
I wish I could but too old to start now!
Now that you had that nap you can stay up all night messing with this stuff
:popcorn:

---

### Post by Blasphemist on 2011-08-08
Just adding my two cents worth while you're discussing advancement. 

My opinion is that for users that only have two OS's, be that windows and a linux distro or 2 distros, grub works fine but by default looks less than modern. This effort addresses the looks and for an unknown percentage of users (unknown as far as I know) the looks should be a priority of someone.

By default there is a design flaw in Grub of any flavor for those of us with 3 or more OSs. The limitation of what seems to be commonly referred to as being forced to have a dominant or controlling Grub and having to use a custom script. Kernel updates to an OS that isn't the dominant Grub partition show the design flaw. I work around this with a custom script like Cecil mentioned and use symlinks in it. The way things are right now I think most people only become aware of this when they have problems and even then documentation on doing this workaround is lacking. Using the custom script that doesn't show or point to specific kernel versions, and disabling certain default scripts seems less than ideal to me.

I haven't developed or written any design spec for a boot loader that overcomes this design flaw, if it can be called that. It is my opinion that many of us do use more than 2 OS implementations. Addressing the look and interaction with the boot loader is definitely an improvement if it makes a better impression on users but this other issue seems important to me to.

---

### Post by drs305 on 2011-08-08
@ MG&TL,

I've not kept up with this thread, but I know you were having problems with getting icons to appear. I'm using G 1.99 and found the icon part fairly trouble-free. 

I used .png images, placed them in /boot/grub/themes/ubuntu/icons, with my theme of /boot/grub/themes/ubuntu/mytheme.txt

I made a 'class' entry  in the menuentry title ( --class pingname ) and they appeared. The 'pingname' is the name of the icon you want to use without the extension (i.e. myping.png would be: --class myping) which was stored in /boot/grub/themes/ubuntu/icons

BTW, Grub legacy never got past version 0.97 and it was around for many years. If you don't see Grub 2.00 any time soon don't be surprised.  ;-)

---

### Post by MG&amp;TL on 2011-08-08
Nope, sorry drs-tried all of that. I guess icons aren't essential...

@Blasphemist-I know what you are saying-If we do end up editing source code for BURG or GRUB, or writing a program to theme them, that, I think, should be one of the priorities-or else back to LILO :)

I think (good start, that!) that a themed grub is going to be a temporary solution, what people really want is a GUI that can theme grub from within Ubuntu, thereby becoming more user-friendly and appealing, like the infinitude of other options you can edit safely, without worrying about your computer going "ker-phutt".

@cecil Yep, doing it now. Oh, hell, BURG's source code is in C. I hate C. Somewhat weirdly written C too. Anyways. I shall have a go at understanding it, but no promises (I can do C++ well, and some other obscure languages, but nothing else.)

Maybe now is the time to pool developing skills? I appreciate that some people will not want to actually write code, but that's not the point-using a debugger and reporting errors is as useful as correcting the damn insects. Or just make constructive criticism. Or learn how to make .deb packages (still haven't worked them out.)

Me:

C++ experience (understand use of standard library, written a few basic programs, GUI with FLTK)
bash shell writing (very basic)
Patience.
4 month's linux experience. 

Not a great start, but hey.

What are your ideas on a project to create our own (or a modded someone else's) bootloader theme-er? Tell me if I'm barking up the wrong tree.

---

### Post by Paddy Landau on 2011-08-09
> **MG&TL said:**
> I could switch the aim of the project to updating BURG?
I wouldn't. Stick with what is being supported; that way, you continue to get support. The ultimate aim, I would hope, would be to get Canonical to accept your changes and incorporate them permanently.

> **MG&TL said:**
> I think (good start, that!) that a themed grub is going to be a temporary solution, what people really want is a GUI that can theme grub from within Ubuntu, thereby becoming more user-friendly and appealing, like the infinitude of other options you can edit safely, without worrying about your computer going "ker-phutt".
Absolutely. This is the holy grail. Maybe -- this is just a suggestion -- once you have fiddled with Grub2 to find out what needs doing, you can revert to the default Grub2 and develop a GUI program (using your knowledge) to automatically modify Grub2? That would be awesome, but it most certainly would be hard!

---

### Post by MG&amp;TL on 2011-08-09
Probably not that hard...what I did with the installer was to have files in the Installer directory and then simply remove the originals, then copy the others in. Rather than appending anything to any files, which I guess IS probably VERY hard in BASH. :confused:

What I really need to know before I do things like that is: (sorry, Google's not my friend today)

-what library does Ubuntu use for its GUI as standard-I don't want to write a humungous program only for Canonical to say "sorry, this doesn't conform"?

-how I run BASH programs from another programming language? In C++, it's system("<systemcommand>"); but I don't know how to pass variables or anything like that without writing to gEdit and leaving notepad(s) all over he desktop...

-what languages do you people use? Obviously we'll go with the majority, that way I get supporters! :D

---

### Post by Paddy Landau on 2011-08-09
> **MG&TL said:**
> -how I run BASH programs from another programming language? In C++, it's system("<systemcommand>"); but I don't know how to pass variables or anything like that without writing to gEdit and leaving notepad(s) all over he desktop...
I don't know how to set environment variables from other languages, but I do know that if you need to use a small, temporary file, you can create one in RAM. Use the RAM disk /dev/shm, which Ubuntu creates by default. I use the command
```
mktemp --tmpdir=/dev/shm somename-XXXXXXXXXX
```Remember to delete the file when finished with it.

> **MG&TL said:**
>  -what languages do you people use? Obviously we'll go with the majority, that way I get supporters! :D
Sorry; I know PHP -- not useful to you -- and bash (both only up to a point). I can help with bash tips and tricks, but not with full-scale programming. I would imagine that Perl or Python are the way to go; as I understand they are easy yet flexible.

---

### Post by MG&amp;TL on 2011-08-09
Hmmm...python is superficially similiar to C++...that RAM command of yours; that's BASH, right?

I'm guessing we're going to have to use BASH eventually-I don't think anything else provides the functionality.

Do you know any good python tutorials-I looked on the web and it seems to be very popular in Linux-maybe I'll have to try it.

Unfortunately not got a 'live' partition, only Vbox, so testing is err...slow. But never mind, it's the holidays.

---

### Post by Paddy Landau on 2011-08-09
> **MG&TL said:**
> Hmmm...python is superficially similiar to C++
Sorry, I can't comment on Python or C++.

> **MG&TL said:**
> ...that RAM command of yours; that's BASH, right?
Yes, it is. Here's what I do when needing small temporary files:
```
TMPFILE=$( mktemp --tmpdir=/dev/shm nicename-XXXXXXXXXX )
*[commands that use ${TMPFILE}]*
rm -f ${TMPFILE}
```> **MG&TL said:**
> I'm guessing we're going to have to use BASH eventually-I don't think anything else provides the functionality.
Unfortunately, bash is rubbish at providing a GUI. The best that I have found, and it's really for the most basic tasks, is [yad]("http://code.google.com/p/yad/") (a fork of Zenity).

> **MG&TL said:**
> Do you know any good python tutorials
Full Circle Magazine has been running a tutorial for some time.
Start with its [special Python archives]("http://fullcirclemagazine.org/2011/05/04/surprise-python-special-edition-02/"), and thereafter download (in order) editions 17 and onwards from the [main archives]("http://fullcirclemagazine.org/downloads/").

> **MG&TL said:**
>  Unfortunately not got a 'live' partition, only Vbox, so testing is err...slow.
Slow... Indeed! Still, it allows you to test safely, and that's the main thing.

---

### Post by MG&amp;TL on 2011-08-09
Thanks for links, paddy.

True-having a virtual test has my tail on numerous occasions-also given me an intimate knowledge of the workings of the Ubuntu error console.

I do recommend C++-there's lots of resources, and it's a relatively easy language to learn. Just a suggestion.

Yup, I agree, BASH is rubbish at GUI-but then it is designed as a terminal. I did have a look at yad, but it was still 'best of the bad'

Thanks for temp-file command- I'd never have found that on my own.

---

### Post by MG&amp;TL on 2011-08-09
Err...do you mean 27? that's where python seems to start? Might be mistaken, but...

---

### Post by cecilpierce on 2011-08-09
Too much talk and not enough action !
:P :P :P

---

### Post by MG&amp;TL on 2011-08-09
We were you sort of waiting for direction from you or drs :p

Would you like us to continue theming GRUB, or would it be better to start off a GUI for theming it?

And hey, come on, I learnt basic python this morning, found a floppy disk and spent two hours formatting it, but still didn't work, and 'pinged' my network (mostly because I could)

;) Votes and programming pooling please!

---

### Post by MG&amp;TL on 2011-08-09
Oh yeah, and did you manage to get the second GRUB theme I sent out? I'm curious to see if it works-I get weird fonts on mine if I do it-fine otherwise...:confused:

---

### Post by cecilpierce on 2011-08-09
Yea, I got it and it works but up and down arrow moves the choices real slow and if ya hit "E" to look or edit it takes awhile to appear,
Whats new? gota grub editor yet?   :P

---

### Post by MG&amp;TL on 2011-08-09
Yeah, I was confused about the slowness-presumably it takes up processing power.

Just starting one, jeez :P

---

### Post by MG&amp;TL on 2011-08-09
Running terminal commands is considerably easier in python than in C++, so I'll use python for now. See here for instructions:

[Thread about python in bash]("http://ubuntuforums.org/showthread.php?t=729192")

---

### Post by Basher101 on 2011-08-09
Nice to see that Grub could look smokin'. Im really looking forward to it. A really cool looking bootloader, a virus free operating system with free software and almost no limitations to customizability, really cool compiz effects (like the cube and others) and this thread[http://ubuntuforums.org/showthread.php?t=58862]("http://ubuntuforums.org/showthread.php?t=58862"). I will use those to convert people in my school to linux (i am currently the only one using linux - and that for a month and i am blown away by it). Ive seen many netbooks of them getting unusable cuz their windows XP got crawled with viruses.

---

### Post by Paddy Landau on 2011-08-09
> **MG&TL said:**
> I do recommend C++-there's lots of resources, and it's a relatively easy language to learn.
Thanks for the idea. If -- and that's an enormous 'if' -- I get the time to learn a new language, I shall have a look.

> **MG&TL said:**
> I agree, BASH is rubbish at GUI-but then it is designed as a terminal. I did have a look at yad, but it was still 'best of the bad'
I agree.

> **MG&TL said:**
> Thanks for temp-file command- I'd never have found that on my own.
Also have a look at coproc ([FONT=Courier New]man bash[/FONT] and search for *Coprocesses*). Useful, especially when using yad with a progress bar.

> **MG&TL said:**
> Err...do you mean 27? that's where python seems to start? Might be mistaken, but...
Sorry. I simply took the comment from the special edition, "This special edition is a reprint of the Python articles from FCM#09 – #16", and extrapolated from there. I'm obviously wrong; I don't follow the tutorials as I know nothing about Python (other than that it's a popular programming language).

> **MG&TL said:**
> Would you like us to continue theming GRUB, or would it be better to start off a GUI for theming it?
I would suggest you theme away in order to learn how it's done. Then, when you program a GUI for changing themes, you will know and understand what needs doing.

> **MG&TL said:**
> ... found a floppy disk and spent two hours formatting it...
Cool, a floppy disk! I didn't realise they still existed!

> **MG&TL said:**
> ... programming pooling please!
Is there an official Grub forum where you could request help?

---

### Post by MG&amp;TL on 2011-08-09
I'm happy to go it alone, but I would appreciate help-as far as I know, GNU seem not to be interested-at least by the looks of their previous efforts, they do not do GUIs.

Yep, I've pretty much finished about learning grub, tbh. The only things I haven't done are pointless things like scrollbars (without a mouse?) and I know how to do those anyways.If you like, I can spend a while longer on the graphics, but there's two problems with that:

[I]1) for some reason, theming grub makes it much slower, something attested by cecil. IDK why, my pc should be more than capable of loading the pretty simple 'pseudo GUI'

2) I'm not a graphic artist.
[/I]


I've finished 'basic training' in Python, now moving on to Tkinter. I shall report back as soon as I have a GUI. Once I have a GUI, I shall make the commands do something. I still have a problem with the slowdown issue, though. Any ideas? It doesn't come up in Google.

---

### Post by cecilpierce on 2011-08-09
@TL
Awhile back when I was testing GRUB GFX Theming I noticed it was slow and jumpy and when Bean overhauled grub and called it burg it seemed to work real good from the beginning so thats what I have been using and waiting for GRUB to come out with something Great.
You might, if you haven't already take a look at the burg code and see how he did it.
I have looked at the files and they seem to be about the same, but I don't understand a lot of it.

Well carry on and good luck, cant wait  :D

link to burg .deb junk, looks like grub with a little added
[http://www.megaupload.com/?d=NHN6MI64](http://www.megaupload.com/?d=NHN6MI64)

---

### Post by MG&amp;TL on 2011-08-10
I'll see if I can find out how burg do it. I do understand it, it's just the shear volume of code that needs to be looked at. I don't suppose there's an official maintainer I can pester?

---

### Post by MG&amp;TL on 2011-08-10
Have sent an e-mail to the maintainer. If, indeed he is the maintainer. 

Tkinter moves on apace, however everytime I try to add a colour or another option to the basic defaults, I get a run-time error.Is it something to do with the Python versions, as I am following old guides, as there does not seem to be a modern one.

---

### Post by lucazade on 2011-08-10
My grub is set to last 3 seconds and I've fixed purple background to black.
I would not bother too much for a colorful one, prefer a sober startup, the same applies to plymouth.

---

### Post by cecilpierce on 2011-08-10
@TL

Hows it going?
Do you have IRC, like Chatzilla in Firefox?
There is a grub channel on there that can probable help, I ask about the maintainer awhile back and (someone) said he kinda vanished. He had or has a forum but it hasn't had much activity lately.
 I'm sure you can get some help there, they helped me in the past.

---

### Post by MG&amp;TL on 2011-08-10
Yeah, Xchat comes pre-installed with Xubuntu.

Wonder where he went?

is it just #grub?

Yup, Tkinter's coming good, but source code for grub is still unintelligible. And Tkinter's still producing interesting errors. Even when copying and pasting. So no GUI yet.

@lucazade -apreciated, one could uninstall the programs after the newbie stage, or design a neutral theme. It's not for everyone.

---

### Post by MG&amp;TL on 2011-08-10
Or there again, maybe not, it seems to be more of a support chatroom, and they don't seem to welcome newbies. :( I don't know what I did, but apparently something that I've personally had and found a solution to is 'I don't know what I'm talking about' Anyways...

---

### Post by MG&amp;TL on 2011-08-10
Ahhh...got Tkinter working now. It seems only basic Tkinter works in windows. Just tried it on Xubuntu, and it works fine.

I suppose I should **Tkinter** account that Python's for Linux (I think). :D

---

### Post by cecilpierce on 2011-08-10
Yea I noticed the attitude on there was sometimes off ! I think 'phcoder' was the most helpful but people come and go on channels. 
I was on there for awhile. guess you got on after I left, I was on compiz and ubuntu+1.
Did you look on the forum ?

---

### Post by MG&amp;TL on 2011-08-10
What forums? These ones?

Yeah, I guess some people get hot under the collar on chatrooms.

compiz, ah compiz. Will not  work on my machine, but I loved it when I had it. How is Oneiric going? I got the .isos, but they would never work. Tkinter test windows up and running now :D

---

### Post by cecilpierce on 2011-08-10
> **MG&TL said:**
> What forums? These ones?

Yeah, I guess some people get hot under the collar on chatrooms.

compiz, ah compiz. Will not  work on my machine, but I loved it when I had it. How is Oneiric going? I got the .isos, but they would never work. Tkinter test windows up and running now :D

Hasn't been anyone on in 3 months though:
[http://www.burgloader.com/bbs/index.php](http://www.burgloader.com/bbs/index.php)

Got any screen shots of Tkinter ?
Oneiric is more like Ornery  :P

---

### Post by MG&amp;TL on 2011-08-10
Tkinter screenshot. Obviously, I'm working on something bigger and better. :p

---

### Post by MG&amp;TL on 2011-08-10
> **cecilpierce said:**
> 
oneiric is more like ornery  :p

:d

---

### Post by cecilpierce on 2011-08-10
> **MG&TL said:**
> Tkinter screenshot. Obviously, I'm working on something bigger and better. :p

Well.... thats a start
:P
You should have it done it a bit, huh ?

---

### Post by MG&amp;TL on 2011-08-10
Yep, been developing it on my old pc (pure Xubuntu). Just realised I should probably have some clue of what I'm doing before I do a GUI. 

Oh well. I know how to do Tkinter now. Mr. Bean (!) hasn't got back to me yet, so I'm guessing BURG is pretty much dead, particularly as the forums haven't been answered since May, and that was a bump.
#grub don't seem interested, more a support chatroom.

Go to programming sub-forum and enlist the help of programming specialist?

---

### Post by cecilpierce on 2011-08-10
Sorry you had so much bad luck, I wish I could do something to help because grub really need a face-lift.
I sent him (bean) a few msgs awhile back and never heard from him, he does a good job and then vanishes, anyway thats what I was told on the irc.
Well burg is still out there for dl and it works for me until I see grub get better, when you look at both side by side, not much diff.

Guess its late for you so tata for now.

---

### Post by MG&amp;TL on 2011-08-10
If you're not busy, that's fine. I'm not sleepy! :shock:

What would you like to see out of GRUB in terms of graphics? Heavy graphics, extensively customisable, basic graphics, slight facelift?

Have started a thread in the Programming sub-forum, asking for help. Programming guys aren't the quickest to respond, but if you do manage to hook one, they generally follow until you are completely satisfied.

---

### Post by cecilpierce on 2011-08-10
Well maybe ask or start a new thread on what people would like to see, like a gui to change default, timeout, background, fonts, font colors, maybe gfx themes would be nice and all the things you have to know about editing all those files scattered around.
I guess just start out simple GUI and keep adding as people have ideas.

---

### Post by MG&amp;TL on 2011-08-10
Yup. I probably won't start a new thread for ideas yet, as project is still quite small and people drop in and out.

I can easily do a GUI for the gfxmenu themes, I could do it tonight, but my computer that I develop on's chewing on something. And being a Pentium4, chewing on something means 'locked up' Not to mention the fact that my mum doesn't like me crashing around in the loft...:(

But we do have a slight problem with that, with the slowdown. I'll research that, if we can find a cure, it would make things far easier. :)

---

### Post by cecilpierce on 2011-08-10
I remember something about that slow action of grub in a old, old thread.
Seems like they almost had it fix the last time I used it but then burg came along and it worked so much better and I lost my HD with everything. Got a new one and started all over and never fiddled with grub for awhile and when I did who ever was doing grub theming kinda gave up on it, but that link might help.
I have two HD's one with grub and one with burg, incase one takes a dive again.
Ill look around and see if I can find something.

---

### Post by cecilpierce on 2011-08-10
Been digging for an hour, and I saw the other thread abt .pup, I think your right!
Seems like ubuntu, mint and debian are about the only distro's using grub2.
Suse, fedora, arch, pclinux, mandriva and others are still using grub .97 and all of those Ive tried have gfxboot and work ok.... so
back to your re-thinking   :P

---

### Post by MG&amp;TL on 2011-08-11
Humph. Here's me thinking I could just rip off the arch code.:D

Oh well, back to the drawing board....

---

### Post by Paddy Landau on 2011-08-11
> **MG&TL said:**
> What would you like to see out of GRUB in terms of graphics? Heavy graphics, extensively customisable, basic graphics, slight facelift?
Start with the simple. A professional look will impress newcomers much better than "fancy" graphics. A blue background, black writing on a white background, and clear icons in full colour, I would imagine. Maybe something red.

There was a Brainstorm entry where people showed some excellent samples, but I cannot find it. The search facility in Brainstorm isn't exactly comprehensive.

---

### Post by cecilpierce on 2011-08-11
@Paddy

That sounds like the best idea, simple and to the point.
:P
Some images>
 
[http://www.google.com/search?q=gfxboot+themes&hl=en&biw=1280&bih=932&prmd=ivns&source=lnms&tbm=isch&ei=SbhDTrycB47UgAeP45D-AQ&sa=X&oi=mode_link&ct=mode&cd=2&sqi=2&ved=0CAwQ_AUoAQ](http://www.google.com/search?q=gfxboot+themes&hl=en&biw=1280&bih=932&prmd=ivns&source=lnms&tbm=isch&ei=SbhDTrycB47UgAeP45D-AQ&sa=X&oi=mode_link&ct=mode&cd=2&sqi=2&ved=0CAwQ_AUoAQ)

@TL

Arch would be a good start, and the others I mentioned all look nice but....grub .97, maybe I should go back to it (downgrade) haha!

p.s. I like the third one on the second row!!!

---

### Post by MG&amp;TL on 2011-08-11
Agreed about the search facility. :mad:

Just tried ArchLinux (for the bootloader) :shock: I know Ubuntu's for human beings, but they take it to the opposite end. Doing anything was an effort. Don't get me wrong, loved the idea, just definitely not a newbie's distro, an intermediate distro, or even' a non-developer distro. Oh well, will try installing grub legacy instead or something.

@cecil. <rolls eyes> There's probably a 'Ubuntu XXX' distribution for that you know...

---

### Post by MG&amp;TL on 2011-08-11
Although they've stopped developing, it seems they've beaten us to it:

[https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

Oh well, not developed, and a little limited, I feel. :D Potential for us!

---

### Post by Paddy Landau on 2011-08-11
> **cecilpierce said:**
> Some images ... I like the third one on the second row!That depends on how wide your screen is.

As a default look, I would go with a simple blue background.

By default, show only the icons (with text) for the different operating systems, so the typical installation would have one icon for Windows and one icon for Ubuntu.

Provide an option near the bottom of the screen to show boot options (help, edit boot line, etc.) and all other boot choices (recovery mode, previous kernels, etc.).

> **MG&TL said:**
> Although they've stopped developing, it seems they've beaten us to it:
[https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)
Is that not the original startup manager that worked with legacy Grub?

---

### Post by MG&amp;TL on 2011-08-11
It might have been. Still in the repos though, so I thought it must be GRUB 2. Yeah, I agree, it depends on how big your screen is. You must have a huge screen

---

### Post by MG&amp;TL on 2011-08-11
<sigh>

I think we have reached a fork in the road here. BURG isn't maintained, GRUB2 slows it down horrifically, GRUB legacy will never be accepted by the ubuntu devs at it is a step backwards, LILO is just strange and out of date (and see Grubleg.)

I think we can discount LILO.

GRUB legacy equally (if we want it to actually be used in its lifetime)

So three options: (none particularly attractive)

-translate the C source code for BURG into Python. Or become its maintainers. C-> Python is not an easy conversion. C is a lower level language, and many language features are downright incompatible. 'Maintaining something that's 'dead' is probably not a good idea, additionally if Mr. Bean ever does come back, he's not going to be a happy bunny if we're running 'his' show. I know it's free software, but I can see why he would get annoyed.

-Find the problem with GRUB2/the gfxmenu themer. This could take days of effort only to find that the error doesn't exist and it is simply the way it is written. Additionally, grub updates will not be possible directly if we have modded the source code.

-Write our own, completely new bootloader. <run screaming> This could easily swallow a year or so. Enough said. But probably the option that will produce the best results.

:confused::confused::confused::confused::confused::confused::confused::confused:

Consensus of opinion please.

---

### Post by MG&amp;TL on 2011-08-11
My somber mood has been caused by trying to use a Debian command-line install without apt-get, as the internet did not support USB routers. Then it decided that a USB was not a supported filesystem and wiped it. Don't even ask.

Anyway, normal service will resume shortly.

---

### Post by cecilpierce on 2011-08-11
Sounds like your in a mell of a hess !
Why not copy and rename burg to TgrubLe since hes not going to reappear.
looks like he copied most of it from grub if you look at all the files he just changed the name and he did a lot of improvements.

I screwed up my grub today and been fiddling with it all day trying to get a good 40_custom file, some boot and some say "you must load kernel first, Dah!
Checked over and over till I went blind, It works in burg but not grub, so I had to rewrite the whole thing, wish I knew what I was doing :P

---

### Post by MG&amp;TL on 2011-08-11
To be fair BASH script is not one of the easier things to read. Don't put yourself down, basic coding can be picked up in an afternoon (I know, I did it) :D I expect you to be bash-literate next tiime you post....;)

Oh, why can't stuff just work. ](*,)

I wonder how hard a new bootloader would be? Calling drs!
Yep, could do that, but hey, everyone's put work in to this, it should be named as a conglomerate of all the people who've contributed to the thread. What spec is the machine you ran my theme on? Because I've just realise I only assigned 256 mb of RAM to my virtual machine.

---

### Post by cecilpierce on 2011-08-11
One gig ram, but I think there is a big dif in the two loaders, even when grub gfx themeing was working it was complained by people that it was jerky and I have never seen burg do that, I dont know what bean did but he got it right in a short time, he spent alot of time on that forum going back and forth from english to chineese, maybe it drove him away or nuts :P

he had other people that helped him maybe you can find one of them.

---

### Post by MG&amp;TL on 2011-08-11
I can imagine it would. (at one point in my schooling, I was being taught four different languages simultaneously (not by choice), and random words from other languages popped up in place of the one I wanted. I'm pleased I stopped down to three now...)

I shall have to have further look at source. Tommorow's project, methinks.

Generally, do you lot have Xchat? I was just thinking we could hijack the err...*charming* #grub (irc.freenode.net) channel and talk there, ideas exchanged faster. Or maybe not, just an idea

---

### Post by cecilpierce on 2011-08-11
Thats a funny crew there, not much goes on unless they feel like it, we could try but might get kicked off
:P
Or we can start a new one and leave it on all day or night and see if any one spots us !!!

---

### Post by MG&amp;TL on 2011-08-11
I agree, saying anything on there gets you frosty looks and abuse.

Can you make a new channel?

---

### Post by cecilpierce on 2011-08-11
Yea I just made one #grub2

---

### Post by MG&amp;TL on 2011-08-11
Very succesful. Next 'conference' is at 4:00 GMT tommorow. topics for discussion?

---

### Post by Paddy Landau on 2011-08-12
@TL: Sorry to hear of the problems. Wish I had the knowledge to help.

> **MG&TL said:**
> Consensus of opinion please.
Finding the problem with the Grub2 & gfxmenu themer would be the best solution by far. But it sounds as though you need some help.

> **MG&TL said:**
> To be fair BASH script is not one of the easier things to read. Don't put yourself down, basic coding can be picked up in an afternoon (I know, I did it)
It helps tremendously to learn how to use the function command, if you haven't already.

> **MG&TL said:**
> Oh, why can't stuff just work. ](*,)
Uh, isn't that the strategy of MS and (in older days) of IBM... so that you need large teams of maintainers? [sarcastic]

> **MG&TL said:**
> Because I've just realise I only assigned 256 mb of RAM to my virtual machine.
Grub2 needs to be able to work in a small amount of RAM, so it can be used (for example) with Lubuntu and Puppy.

> **cecilpierce said:**
> Yea I just made one #grub2
Can you give me a pointer as to how to join such a discussion? In such matters, I'm a 100% newbie and wouldn't have the faintest idea where to start! A link to a tutorial would be useful.

---

### Post by MG&amp;TL on 2011-08-12
Yeah, sorry, I just meant that slightly more user-friendly would be an advantage. 

Get a client like Xchat. 

Launch Xchat, then follow the prompts. You should be prompted to join a  channel. Type the name of the channel you want to join. In this case, #grub2, but this won't be open all the time, only when cecil opens it.

Who wrote the theming engine? We could make a 'lite' and a heavy version-like Xu nd Ku-buntu.

---

### Post by Paddy Landau on 2011-08-12
Thanks for the answers.

> **MG&TL said:**
> Who wrote the theming engine?
Sorry, I don't know.

> **MG&TL said:**
> We could make a 'lite' and a heavy version-like Xu nd Ku-buntu.
That would make it a lot more effort. Perhaps stick to a single, simple version, and let it grow over time (as programs do)?

Once you get something very basic working (e.g. choosing the order of the boot options, which one is default, the time-out, and automatically hiding the boot options and extra boot options with an option to reveal them), then you know you have a working start. Thereafter, "grow" the options, one at a time, adding (say) a background choice; different icons; and so on.

Any other way will make it exceedingly hard, don't you think?

---

### Post by MG&amp;TL on 2011-08-12
Yeah. to all of that. ;)

---

### Post by MG&amp;TL on 2011-08-12
I'm looking at the source code on launchpad and to be honest, it's looking pretty slimmed down already, perhaps a few extreaneous variables, but nothing that would cause slowdown on that scale.

---

### Post by cecilpierce on 2011-08-12
Hi Paddy,
TL is using XCHAT which you can get from synaptic, it comes with a help file and you can search for what your interested in and then just connect to it.
I use "Chatzilla" which runs inside of FireFox, its an Add-on in the 'Tools' menu or if its not there you can DL it from 'Mozilla'.
When it opens you have to connect to a node, I use 'freenode' and to start you can get a list which is large of chat channels or if you know the one you want type '/join #name' and your there.
They all have help files, five minutes and your a pro !
Ten minutes and your bored :P

---

### Post by cecilpierce on 2011-08-12
You guys type faster then me!
I got distracted by my grandson in the middle of the last msg and when I sent it 3 earlier one were there, geeez!   :p

---

### Post by MG&amp;TL on 2011-08-12
Yeah, sorry internet generation I'm afraid, you oldies are just gonna have to catch up! :P

Nah, you knew how to use Xchat better than I did!

---

### Post by cecilpierce on 2011-08-12
Im having a bad day, gota go buy a basketball for my grandson and take him for breakfast.
So Ill yak at ya later on after while sooner or later, get off the Internet and do some grubin !!!
:popcorn:

---

### Post by MG&amp;TL on 2011-08-12
Grubbin' now!

---

### Post by Paddy Landau on 2011-08-12
> **MG&TL said:**
> Next 'conference' is at 4:00 GMT tommorow.
Can I confirm that this means Saturday 13th at 16:00 UK time? Or did you mean 4:00 a.m.?

[http://www.timeanddate.com/](http://www.timeanddate.com/)

Also, thanks all for the IRC details. I discovered that I had experimented with IRC a long time ago, but I had forgotten about it. Luckily, I had saved my password!

Anyway, I tried Pidgin, gnome-xchat, xchat and ChatZilla. The last one is the "prettiest", but I struggled to find out how to join a server (the first three have a menu option to do it). Pidgin had the best defaults (it remembers your password and which server you had last signed in to).

Anyway, I know how to use it now. Thanks.

I'm following #ubuntu -- how do people know what's going on? There are several conversations all happening at the same time!

---

### Post by MG&amp;TL on 2011-08-12
I guess you just 'tune in' to the one you want...- I'm writing a GUI tonight to edit the gfxmenu themes. It may be slow, but at least i'll have something to show whille we work out what's causing the slowdown. I'll post developments here. Tarball format and .sh installers OK for everyone?

I've switched from Tkinter to PyGtk, as this seems to be what all the Gnome apps are written in (i.e. gEdit, gNotes, that kind of style). It's also much easier, although I would have said less configurable from a first glance.

---

### Post by MG&amp;TL on 2011-08-13
Really sorry guys, haven't made any progress at all since I last posted, Internet has been down. :(

Grubby continuing apace now.

---

### Post by MG&amp;TL on 2011-08-14
Making a launchpad thingummy now-the files are too big for Ubuntu forums.

[https://launchpad.net/grubby]("https://launchpad.net/grubby")

Source code will be arriving soon, and I'm looking in to how I allow you guys to contribute.

---

### Post by cecilpierce on 2011-08-14
What am I suppose to do with that rdf thing ?
:confused:

---

### Post by Paddy Landau on 2011-08-14
> **cecilpierce said:**
> What am I suppose to do with that rdf thing?
You're not supposed to do anything with it. It's the description of the Launchpad project itself.

---

### Post by cecilpierce on 2011-08-14
> **Paddy Landau said:**
> You're not supposed to do anything with it. It's the description of the Launchpad project itself.

OH! I thought he said there were files in launchpad, I'm not so bright about this rig-a-ma-roe ! :confused:

---

### Post by Paddy Landau on 2011-08-14
> **cecilpierce said:**
> ... I thought he said there were files in launchpad...

Not yet:> **MG&TL said:**
> Source code will be arriving soon...

I'm sure TL will tell us when he's uploaded something.

---

### Post by MG&amp;TL on 2011-08-14
Nothing's up there yet. Launchpad is hell to use...I'm posting a thread on here now asking how to use it.

---

### Post by MG&amp;TL on 2011-08-16
Right, have two themes and an installer so you can choose between them. 

Launchpad is being horrifically slow in emailing my pgp key, so if anyone wants it, PM me with your email and I will 'post' it. :)

---

### Post by MG&amp;TL on 2011-08-16
More themes are coming, btw. If anyone wants to contribute, I need: a font or two (any format you like, preferably .ttf or pf2) a backdrop, and a colour palette of some sort, prefereably in hex code, but if not RGB or 'light blue' format.

I already have Ubuntu and a default theme, but don't let that stop anybody. The themes run (with no noticeable lag) on a Pentium 4 with 256 Mb RAM, so it should work on your PCs. I intend to produce 'lite' and 'heavy' themes for those with different hardware levels.

Lite is what I'm producing currently, includes title, backdrop, and coloured text. 

Heavy could include circular timers, selection highlighters, etc. The world is your oyster, providing it's in gfxmenu. If you want to make a 'heavy' theme for your supercomputer, PM me. All themes will be attributed to those who made them. :)

---

### Post by cecilpierce on 2011-08-16
@TL

Well I got one of my Ornerys to work after fiddeling for 2 days, now to see whats wrong with the other one.
I sent you a pm, you had a few msgs on your home page !!!

Well carry on 

:popcorn:

---

### Post by MG&amp;TL on 2011-08-16
My first (naive) volunteer! Heh, Heh. Thanks cecil!

---

### Post by MG&amp;TL on 2011-08-16
Arrgh. Debian packaging is a nightmare. I don't suppose there's any veterans out there who have done it before? A lot to ask, I know (it would be my lucky day!) 

GUI coming soon. How's it going cecil? I'm getting a bit worried since I haven't heard back, I'm hoping my software hasn't killed anything? :o

---

### Post by cecilpierce on 2011-08-16
Sorry TL, I had a small crash Saturday, rolled the air-boat over and im kinda soar and cut up from saw-grass, took a nap after I tried Grubby, it works real good, I tried to take a pic of it but my old cell phone got wet Saturday so the new one wont let me get the pic out of it. but it looks nice.
I put grub on sdb and burg on sda.
Can you put a solid background on the selected text? I guess you can Im going to look at it and see what the files look like.
Well its 8:30 here so I guess your 6+ ahead of me and asleep so yak at you later, 
Thanks, Cecil

---

### Post by MG&amp;TL on 2011-08-17
Cecil! A boat crash! :shock: Poor you.

When you say a solid background, you mean a little box around the text (like in the original), right? Yeah, sure I can do that, or you can, it's up to you. Make sure that the credits are updated to include what you did if you do it yourself. Don't want to put anybody down.

Launchpad has finally emailed back with the encryption, so away I go. Ubuntu code of conduct now. ;) As if I would misbehave...

---

### Post by cecilpierce on 2011-08-17
Congratulations :)

Yea, the box, it makes it stand out for us old pharts to see better !!!

Whats next on the agenda ?

---

### Post by MG&amp;TL on 2011-08-17
Well, A GUI, when:

a) I can get it to work, and

b) I've found a way of packaging it so that you don't have to install the GUI libraries manually.

In the meantime, any other suggestions? Yours is down cecil, I've got MG working on it now. :)

Yes, and a .deb so that non-devs can install it- :P. I've found a guide for a basic .deb (that's readable) , but I have a feeling that if said .deb wants to go anywhere or do anything complicated, it's not going to be good enough.

Any suggestions are most welcome, as I don't have a clue about either of these, and my head's hurting.

Thank you very much cecil. I don't need to be congratulated, it's you guys with the suggestions and inspirations. :D

Oh, and a useful thing I found, if you put any executable in /usr/bin, you can type its name in a terminal, and it runs the app. :)

---

### Post by MG&amp;TL on 2011-08-17
Just a quick test: Can you run this executable once decompressed? It opens a test window. Double-clickable. Cheers guys! :D

---

### Post by Paddy Landau on 2011-08-17
> **MG&TL said:**
> ... when: b) I've found a way of packaging it so that you don't have to install the GUI libraries manually.
Try these three links:

[LIST]
[*][Personal Repositories]("https://help.ubuntu.com/community/Repositories/Personal")
[*][Debian New Maintainer's Guide]("http://www.debian.org/doc/manuals/maint-guide/")
[*][Create Debian Linux Packages]("http://www.ibm.com/developerworks/linux/library/l-debpkg/")
[/LIST]
I've never done it myself, so I hope those help.
 
> **MG&TL said:**
> I don't need to be congratulated
Very modest of you, TL, but when all's said and done, you're the one doing the work. I second cecilpierce: Congratulations!

> **MG&TL said:**
> ... if you put any executable in /usr/bin, you can type its name in a terminal, and it runs the app.
In a terminal, type [FONT=Courier New]echo ${PATH}[/FONT] to show you all the executable paths.

> **MG&TL said:**
> Just a quick test: Can you run this executable once decompressed? It opens a test window. Double-clickable. Cheers guys! :D
I would -- if I knew where the executable was!

---

### Post by MG&amp;TL on 2011-08-17
> **Paddy Landau said:**
> 


I would -- if I knew where the executable was!

Err...it should be there. Damn, just checked my linux pc, it didn't upload. Damn Internet dropped out. I shall upload in an hour or so when dinner's over. I'm only on here because I'm laying the table...:D Thanks for the gotcha, paddy.

Thanks for the links as well.

---

### Post by MG&amp;TL on 2011-08-17
Got away!

---

### Post by Paddy Landau on 2011-08-17
My result:
```
./Test: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
```I have checked Synaptic, and I have libgtkmm-2.4-1c2a installed.

---

### Post by MG&amp;TL on 2011-08-17
Thanks for testing it, paddy! A brave soul downloads executables from the web...

If you wouldn't mind, would you try:

```
sudo apt-get install libgtkmm-2.4-dev
```

Thank you! (it should work after that)

---

### Post by cecilpierce on 2011-08-18
Hay, just got back from working on the boat, tired ! 
I don't know whats going on but I tried your test tar thingy

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> A brave soul downloads executables from the web...
Or foolhardy!

> **MG&TL said:**
> sudo apt-get install libgtkmm-2.4-dev
Done, but the same error:
```
./Test: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
```It worked for cecilpierce, so what's the difference? I'm running 64-bit Lucid. cecilpierce, what are you running?

TL, do you want to list all dependencies (if you know what they are), so that I can see what I may be missing?

---

### Post by MG&amp;TL on 2011-08-18
Thank you cecil, and you too paddy. In theory, the only thing my executable needs is to be able to use the gtkmm libraries, and since gtk is the standard GNOME format, everyone should be able to. I just installed the libgtkmm-2.4-dev package so I can develop it, I thought.

It's a very simple 'hello world' program, but I wanted to test whether a GUI would run 'out of the box' without installing anything. I don't suppose you would have removed anything, paddy? 

I think I'll just put the package in 'depends' Your error is interesting. I just didn't want to write something that nobody could use without a load of dev libraries. I'll run a USB, and see if I can run it. I hate bugs....:mad: Sorry to trouble you, paddy. If I can find out what's causing it, I'll fix it.  

Version 1.1 should have a GUI. :)

Thanks for the test, cecil, that's exactly how it should have worked. Have you installed anything along the gtkmm line? btw, how's the boat doing?

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> I don't suppose you would have removed anything, paddy?
Not to my knowledge, I haven't. Perhaps raise a new thread in the programming forum to ask what the problem could be. Post the thread link here so that I can follow it and help out with testing.

> **MG&TL said:**
> Sorry to trouble you, paddy.
No problem, TL! This is my way of contributing.

---

### Post by MG&amp;TL on 2011-08-18
Thread here:

[http://ubuntuforums.org/showthread.php?t=1827595]("http://ubuntuforums.org/showthread.php?t=1827595")

Humph. Well, in the meantime, I shall try and get a GUI working.

---

### Post by MG&amp;TL on 2011-08-18
According to the guy who answered, your libraries are out-of-date. So, I think:

```
sudo apt-get update && sudo apt-get upgrade
```

should work, although I'm waiting for confirmation. Hope this sorts the problem. .deb. package might be incoming tonight, I vaguely understand it now.

---

### Post by cecilpierce on 2011-08-18
@Paddy 
I'm using 32-bit Oneiric Ocelot.
Lucid might not have all the newer lib's maybe ?

---

### Post by MG&amp;TL on 2011-08-18
I'm using Lucid. 32-bit. I think the best solution is for me to build a .deb package and see if that works, rather than firing stand-alone executables cross the web. If I get the oppurtunity, that should be on launchpad tonight. (GMT). If there's no bugs. :) I'm afraid there's still no GUI, but at least there's a .deb. Purge any previous installs you may have had before you install the .deb :D

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> According to the guy who answered, your libraries are out-of-date.
I've posted [my reply]("http://ubuntuforums.org/showthread.php?p=11163522#post11163522") on your thread, TL.

---

### Post by MG&amp;TL on 2011-08-18
Instructions for paddy, who's volunteered to compile 64-bit code for me. :D

make sure you have g++.

```
sudo apt-get install g++
```

That is all you need.

Extract tarball to home folder, call it 'Grubby' if it doesn't already. (Home folder, not desktop or anything!) (There will be 'system' locations next release, i.e. not cluttering up your stuff)


Then compile:
```
cd ~/Grubby/src

g++ -o Grubby Grubby.cxx

```

And if all goes well, (no errors, returns to prompt after a pause), cut and paste the executable from ~/Grubby/src up one, to just ~/Grubby. Run it if you want (please don't if you value your stuff/don't know how to fix if all goes wrong), then recompress the folder, calling it 'Grubby64.tar.gz' or whatever.

Any errors or problems, PM, email, or post here. Cheers! :D

---

### Post by Paddy Landau on 2011-08-18
I compiled without error.

I ran it, thinking that this was going to be your little test GUI :redface:

Luckily, I didn't run it with sudo, so no harm done!

I will email the compiled code to you.

Would you like me to create a VB and test it?

---

### Post by MG&amp;TL on 2011-08-18
Sorry, should have made that clear. Phew. It won't actually do anything until you select an option, but that was close. :o

Please do-but only if you want to-VERY experimental at this stage (but that's what a VM is for, I guess). Got the executable, the terminal's building the .deb as we speak. Thanks a lot-are you willing to do this for future releases? It was a great help, if only for this release. :D

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> are you willing to do this for future releases?
Yes, of course! Just ask.

---

### Post by MG&amp;TL on 2011-08-18
Thank you Paddy! .deb is being attached. :D :D

Cecil, do you want a .deb as well? (if so, email me, tell me your architecture)

Instructions: Remove any folders in your home folder labelled GRUBBY (if you have any)

Extract .tar.gz to wherever you like. Double-click on the .deb, and away you go. All done. Type 'Grubby' in a terminal to run. PPA coming soon. :D

Send any bug reports to me, and they will get fixed. (I am sure there will be plenty, as I am even less confident about the .deb than the source! For pity's sake run it in a VM if you value your machine's general wellbeing...)

EDIT: no tarballs, you can't compress .debs. Noob error, sorry.

---

### Post by Paddy Landau on 2011-08-18
I'm building a virtual machine now.

I'll get back to you tomorrow; it's getting late and I need to get the kids (and me!) to bed.

---

### Post by MG&amp;TL on 2011-08-18
OK...night, paddy kids! Sleep well.

---

### Post by cecilpierce on 2011-08-18
@TL
email me the deb I will get it a try, 32-bit

---

### Post by MG&amp;TL on 2011-08-18
Sending now. I must sync this with Ubuntu One or something so that you can all get it. Launchpad is a project for tommorow. :D

---

### Post by cecilpierce on 2011-08-18
Thanks TL, 
I just put it in a new install of O.O.
Had some dependency probs but fixed that, libmm.dev or something like that.
It still jerks a little with the ubuntu theme and if you hold the down arrow key to long it keeps on jerking, but it did that with the old grub gfx theming to but not with burg, wonder how he fixed that ???   :confused:

---

### Post by cecilpierce on 2011-08-18
The air boat is patched up for now, still have a voltage drain on the battery but cant find it so I just disconnect it when not in use, went for a test ride and a good thing, there was a man and his grandson broke down, oil plug came out !
Took them back in to get more oil and a plug, bummer....!

---

### Post by MG&amp;TL on 2011-08-19
IDK, that's why I was trying to get hold of him. It only lags a little on 256 Mb RAM, maybe it's your VM (I think, what's O.O?) 

Good to hear about the boat. It's not like a little more oil's going to be a problem in your part of the world.. :P

libgtkmm-2.4-dev? That's a dependency, but I don't know why it didn't just install that...:confused:

---

### Post by Paddy Landau on 2011-08-19
TL, I have received your 64-bit deb, and created a VM to test it.

But, oh, the irony!

VirtualBox cannot [support 64-bit virtualisation]("http://www.virtualbox.org/manual/ch03.html#intro-64bitguests") unless the CPU supports hardware virtualisation.

Guess what my CPU does not support... So, sorry, I can't test for you. :(

Here's how to check whether or not you can run a 64-bit virtualisation on your machine, *even if you have a 32-bit host OS*.

```
grep -qF lm /proc/cpuinfo && grep -cE 'svm|vmx' /proc/cpuinfo
```
[LIST]
[*]If this returns 0 or nothing, you cannot run 64-bit virtualisation on your machine.
[*]If it returns 1 or greater, you can run a 64-bit virtualisation, even if you have a 32-bit OS.
[/LIST]
 
If you can support 64-bit virtualisation, you can create a VM with a 64-bit Ubuntu guest (even on a 32-bit Ubuntu host) and do everything you need there.

BTW, I recommend [Lubuntu]("http://lubuntu.net/") instead of Ubuntu, as it optimised for slower hardware. Lubuntu is extremely fast and has much lower RAM requirements (just 256Mb to install and 128Mb to run; you can set the RAM to 256Mb, install, then lower the RAM to 128Mb). You can get its 64-bit version from its [download page]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#11.04"). Be sure to read the section labelled [About 64 Bit]("https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD#11.04%2064%20bit%20Community%20Edition") to check the download's integrity before installing.

---

### Post by Paddy Landau on 2011-08-19
> **cecilpierce said:**
> ... but not with burg, wonder how he fixed that?> **MG&TL said:**
> IDK, that's why I was trying to get hold of him.
What about asking on the [Programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39")?

---

### Post by MG&amp;TL on 2011-08-19
Sorry, hardware returns 0. It WAS made when 64-bit was only used in supercomputers...I shall have to find a different way to test. 

I see no reason why code compiled on a 64-bit machine should not run on your machine, so I think what we will do in the meantime is continue to build the project (32-bit versions), and send you 'dud' 64-bit executables that don't do anything, but do run. Is that agreeable to everyone? Would I be right in thinking that 32-bit applications run on 64-bit, just not as efficiently as they could? When the project releases a stable release, I suggest that we recompile, and see if it works then. (If you're willing, I don't expect you to be)

AFAIK, you can simply re-install GRUB from a live cd, so testing isn't as dangerous as I thought. :D

PPA is going badly, why can't it just take .debs, it would be much simpler. And if I don't know how to get the 'orig.tar.gz' in the first place, how am I going to upload it? Once I've got this sorted out, I'll have to find out how to write a 'how-to' on the topic for any other launchpad newbs.

---

### Post by cecilpierce on 2011-08-19
@TL
O.O. is Ubuntu Oneiric Ocelot 11.10
I have 3 installed and that one was all messed up, so I dumped it :D for a new and improved one.

---

### Post by MG&amp;TL on 2011-08-19
@cecil. Ahhh...

I think we've been spammed. :( I'll report it.

---

### Post by MG&amp;TL on 2011-08-19
Done the thread, will keep you posted on any developments. 

Heading for my first 'coffe cup rank' :popcorn:

---

### Post by Paddy Landau on 2011-08-19
> **MG&TL said:**
> Sorry, hardware returns 0. It WAS made when 64-bit was only used in supercomputers...
:lol:

> **MG&TL said:**
> Would I be right in thinking that 32-bit applications run on 64-bit, just not as efficiently as they could?
I believe that you need to install something-or-other to be able to do that. Remember the problem we got with [the "Test"]("http://ubuntuforums.org/showthread.php?p=11161014#post11161014") that you did previously.

Please try that Test again: send me the source code along with the instructions on how to compile it. I'll compile it, run it, and let you know the results.

> **MG&TL said:**
> When the project releases a stable release, I suggest that we recompile, and see if it works then. (If you're willing, I don't expect you to be)

AFAIK, you can simply re-install GRUB from a live cd, so testing isn't as dangerous as I thought.
Good points, TL. When you get a stable (or at least a beta) release, I'll try. But I'd like to do the Test first as proof-of-concept.

> **MG&TL said:**
> Once I've got this sorted out, I'll have to find out how to write a 'how-to' on the topic for any other launchpad newbs.
Surely there's one already? Did you see the [official help]("https://help.launchpad.net/Packaging")?

---

### Post by MG&amp;TL on 2011-08-19
The test prog I sent was just a GUI; it didn't actually DO anything.

Sorry about this mess; I'd forgotten about 64-bit. ;) This is why I work as a team...

Yep, I can send the prog again if you wish. Sending it now.

Yeah, I did see the official help-I'm afraid it's in code. :D Typically, I find that if you are completely new to launchpad (and I was) you can get through about three steps, then something fails because you haven't organised it correctly. I'll search for a how-to, but I didn't see one on my Internet searches.

---

### Post by Paddy Landau on 2011-08-20
Hi TL, thanks for your Test code.

I compiled and ran it successfully, without any problem. I had a blank window that I could minimise, restore, maximise and close.

If you need me to compile code for you, send it along and I'll be happy to do so. But I won't test on my live machine until you have at least a beta version and I know how to restore Grub on failure (and I will back up my data first!).

---

### Post by MG&amp;TL on 2011-08-20
No, no really, I don't want anyone to muck up their pcs with any of my (dubious) code. :D I'll email when I believe I have a beta...

Really pleased that the GUI works, a PPA should be up there soon. (I have done it, but it ran into an error, so I'll have to do it again.

---

### Post by cecilpierce on 2011-08-20
Good Morning Grubers :)

Can't you test or install grubby on a flash drive (sdb or sdc) and choose it from the bios when you start the PC ?
That way you don't mess with the original grub on sda in case something, heaven forbid, goes wacky :P

If you had a 4 gig flash you could run off it entirely!

---

### Post by lucazade on 2011-08-20
I'm still wondering what is about this thread after 25 pages :D
Is it a tool to customize grub? A work in progress? something?!

---

### Post by MG&amp;TL on 2011-08-20
Grubby, as it currently stands, is a command-line tool to apply pre-made themes to the Grub2 bootloader. It is still in progress, and any installs should be made with caution. In the future, two important devlopments need to be made:

-a GUI

-Make it so you can make your own themes too.

There is only two themes available currently, (Ubuntu and Default), but more are coming shortly.

There is a PPA on launchpad, but it's not working as yet. Thanks for the interest, btw. I'm not entirely certain how it ran to 25 pages and 5,000 views, but there you go.

The flash idea's a good'un, cecil, I hadn't thought of that. PPA might (hopefully) be up by this evening, barring any bugs. (Is it still running, grubby, cecil?)

How's the boat and Ornerys going?

---

### Post by lucazade on 2011-08-20
ah ok.. tnx for clarification and good work!

---

### Post by MG&amp;TL on 2011-08-20
No problem, it's my first project, hence why everything's a 'work in progress' and 'not working'!

Thanks really go to the co-pilots, here, mainly Cecil and Paddy at the mo, but there have been others. Any help, btw, is very welcome, as is the spirit of open-source. :D

---

### Post by MG&amp;TL on 2011-08-21
Just an update, guys. Launchpad is still not being very helpful, I have posted on their 'answers' forums about the issue. :D

Grubby has had it's first revision! (1.0.1)

-Fixed bug in 'Default.sh'

-Modular code.

-Rewritten GRUB theme installation process to be less system-intensive. Still a bit of lag on the actual bootloader though, although if you have on OK computer, you should have no problem whatsoever.  :(

Sorry I haven't posted for a while, I've been at a '1940s weekend'. GUI by this evening is my target. <facepalm>

Bit of a problem with your highlighters, cecil, should be fixed by next release.

---

### Post by cecilpierce on 2011-08-21
@TL

1940's huh ?
Were there any old English Fords there ?
First car I drove, was my uncles, back then they only had one color, Black!

---

### Post by MG&amp;TL on 2011-08-21
Yup, lots of Fords (guess what? all in black) Early Mk Jags too. =P~ :-({|=

No, I had to dress up. :( :oops: It was awful, and it wasn't exactly my choice, so I rebelled and stayed at home today. :D

---

### Post by RJ12 on 2011-08-21
Just a tip on publishing, you could also probably use GitHub too so you can commit, push, and others can pull the code easily while Launchpad isn't working.

---

### Post by MG&amp;TL on 2011-08-21
No, launchpad's fine, I just gotta learn how to use  it. ;) The documentation isn't what I would have called clear. They're also really slow at sending e-mail to yahoo! I did file a bug report to Yahoo! but got a bot. :(

Will have to have a look at GitHub.

---

### Post by Paddy Landau on 2011-08-22
> **cecilpierce said:**
> Can't you test or install grubby on a flash drive (sdb or sdc) and choose it from the bios when you start the PC ?
For some reason, I haven't been getting the emails telling me of new posts. I just discovered these new posts by accident -- I was wondering why there was no news!

You're right, I could try a flash or even a partition on an external hard drive. That's a clever idea -- as long as it doesn't mess with the internal hard drive.

---

### Post by MG&amp;TL on 2011-08-22
Nope. At least it doesn't on my laptop. :D

---

### Post by MG&amp;TL on 2011-08-22
PPA coming soonly, btw, just gotta learn to write makefiles and such...:(

I've begun to hate everything about launchpad, btw. Don't mention it in my hearing :P

---

### Post by SevenMachines on 2011-08-22
Launchpad will feel a lot better for you given time... probably :) It can do a lot of good things like automatically generating debian packages from bzr repository and flash things like that. But, getting started can be a bit of a pain, failing to upload a package with no helpful message or clue to why can be very frustrating. Setting up a bzr repository from your launchpad page should be fairly straightforward though no?

---

### Post by MG&amp;TL on 2011-08-22
Nope, already tried bzr and that was even worse...finally got a PPA up, it's just 'waiting to be built' :D IDK whether it'll actually work or not, but it's up.

Yeah, I agree, 7machines, once it's up there, it must be the easiest thing in the net to update. But to get it up there. If I get a spare moment, I'll write a how-to. ;)

Accidentally wrote a virus today. :shock: Not so much a virus, but it fills up your hard drive at a rate of 1Mb every 15 secs...:) Oops.

---

### Post by MG&amp;TL on 2011-08-23
Two things...

-Launchpad will be delayed as I forgot to write a makefile, and therefore a bunch of source code gets dumped to the cache on my pc, instead of installing the program.

-further developing will be delayed, as in an effort to provide a more up-to-date package, I upgraded to 11.04. -installed driver so I could run unity, doesn't work, try one of the suggested bug fixes, kills pc. No resolution. Reinstalling it now. (good thing my files are backed up to the cloud.)

[SIZE="3"]<RAGE>[/SIZE]

anyways...how were your days? Back to school in a fortnight...:( Will still develop grubby at the same rate, as I do not have to do anything on school nights as such. (only homework, and that doesn't take very long) I've fixed the problem with your boxes, cecil, so those should be in next release (when I've fixed my hardware)

---

### Post by MG&amp;TL on 2011-08-23
Phew...managed to recover it, and I've started to write a makefile. :D

I've started to write a makefile now, sorry I was grumpy earlier :(

---

### Post by cecilpierce on 2011-08-23
Were you grumpy or grubby ?
Back to school for the two grandsons, First grade and sixth grade, the both did real good, hope it stays like that :P
The oldest is starting to like linux, I showed him some neat tricks in a terminal and hes liking it more.

---

### Post by MG&amp;TL on 2011-08-23
mistyped on a keyboard once, typed 

```
apt-get moo
```

which was ummm...weird. Try it. <moo> ;)

Grubby obviously :D (although I'm very OCD, so grubby=grumpy-when I was a kid, eating a KitKat (chocolate bar), I used to have to have my hand washed after the first half so I could eat the second half, otherwise I had a tantrum :) I still get annoyed about grub on my hands)

The 'compiling' bit of the makefile is a go-go, just need to write the copying bit now.

Mucking around with windows...telnetted to my brother's laptop and a left a readme on his desktop :D Such fun.

---

### Post by cecilpierce on 2011-08-23
(__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...

Thats neat, how did you figure that out?
I have seen that on Mint Linux term window....I must wash my hands 50 times a day, its hell on the water bill :biggrin:

---

### Post by MG&amp;TL on 2011-08-23
Mint window's quotes and ASCII graphics are very cool. Like Mint itself, really, until it gets annoyingly green.

Next door's cat sat on me :( Still finding cat hairs all over the place, they got in my computer once and caused it to fail. Love cats, though.

Got to the point where the detergent was giving me ezcema, so I was forced to quit with the excessive hand-washing. :D
 Night, all.

---

### Post by cecilpierce on 2011-08-23
Later Gator

---

### Post by Paddy Landau on 2011-08-24
> **MG&TL said:**
> ... which was ummm...weird. Try it. <moo>
There are several Easter eggs in Linux.

Search the forums and Google for them.

Try this one. Press Alt-F2 and enter [FONT=Courier New]gegls from outer space[/FONT].

---

### Post by MG&amp;TL on 2011-08-24
Really sorry to have to say this guys, particularly after 2 month's development, blood, sweat and brain juice, I'm probably not going to be able to continue with the project. I am really sorry, (not my fault as such, MAJOR bust up with family member.) particularly after what you guys went through to get me here.

Would you know of anyone that might be able to continue the project? I have my project on the Ubuntu 1 cloud.

It's been great knowing you guys, as friends and co-developers.

later gator,

TL.

---

### Post by Paddy Landau on 2011-08-24
Hey, TL, really sorry to hear that.

I personally don't know anyone, but it was great while it lasted ;)

The thread will still be here should you change your mind later.

Good luck with whatever is happening.

---

### Post by MG&amp;TL on 2011-08-24
Sorry for alarm guys, it should be OK now. Said family member has calmed down a bit (but is still ranting and raving) , although I have one non-booting pc to fix :(

Project back on. I think. God, being a teenager is restricting. If I was an adult, I would have free speech, and free actions. <sigh>

See you in the morning guys, I have pieces (literal and emotional) to pick up here...

---

### Post by cecilpierce on 2011-08-24
@TL

Sorry,
I know what your going through, a FM just went to prison for two yrs and the mess here cant be fixed, it will get better I hope  
:(

ps now we have a hundred + mile storm coming, geez!!!

---

### Post by MG&amp;TL on 2011-08-24
Buckle up, cecil! Don't want 32-bit tester getting blown over here, convenient as it might be...we never get any decent wind, although we do get 'fen blows' where dry soil gets lifted off the fens and into the air, entire sky goes brown/purple. :D

---

### Post by Paddy Landau on 2011-08-25
> **MG&TL said:**
> God, being a teenager is restricting. If I was an adult, I would have free speech, and free actions. <sigh>
But on the other hand, with adulthood comes experience and responsibility. Things to look forward to. ;)

Teenagehood is a notoriously difficult time. I don't miss it. It'll get better.

---

### Post by MG&amp;TL on 2011-08-25
Yeah, I don't really want to be an adult I suppose, but I _really_ don't want to be a teenager.

PC has decided to make a system beep and an alarm noise now, so the motherboard's OK. I think it might be the RAM sticks or something. How's your storm going cecil? Try as I might, I couldn't find a florida weather forecast.

---

### Post by cecilpierce on 2011-08-25
@ToughLad

Well it looks like the storm is going North, its oved over to the East a little bit so all we will get is some rain and wind gusts.
Im going to the Everglades to work on the boat and there is a meeting tonight, dues are due $$$ I don't have :(

I noticed GFX Theming stuff in Synaptic but no gui, info or how to ?

Well you will probably be asleep when I get back so take care.

---

### Post by MG&amp;TL on 2011-08-25
Well, I probably won't be, I'm almost never asleep. Good to hear that you're being missed by it, although I hope you find the $ for your boat, I love boats. What sort is it?

Tough Lad- :lolflag:

Yeah, right, I still have teddy. :oops: . You want a tough lad, go ask the agricultural types around here. :D. Almost everyone's a farmer around here...depressing. Most of them talk about crop circles or harvesting celery...as you can imagine, my talents (such as they are) are not appreciated.

'puter's finally booted now, RAM stick was bent, although amazingly it still works. Phew. Makefile for the PPA should be up by tonight, so you lot can have a PPA. I think this release should be stable. :D Still no GUI, but should be in the release after this one. It's my next project as soon as I've got lauchpad working. 

Got some of my GCSEs back today, 1 A*, 3As and a B. I guess you lot in America have err...finals? IDK, I had a friend on one of the USAF air bases around here, he said he'd do his 'finals' in America, but what he meant by that I don't know. He said he was going back a year by going to america. Apparently you start a year later. :confused:

---

### Post by philinux on 2011-08-25
Thread moved to Community Cafe.

---

### Post by MG&amp;TL on 2011-08-25
OK, thanks phil. Probably needed doing as the thread as drifted somewhat from my original post.

---

### Post by sanderd17 on 2011-08-25
> **cecilpierce said:**
> (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...

Thats neat, how did you figure that out?
I have seen that on Mint Linux term window....I must wash my hands 50 times a day, its hell on the water bill :biggrin:

or try
```

aptitude moo
aptitude -v moo
aptitude -vv moo
...

```

or with the old gnome2, you could also do an ALT+F2 and execute "free the fish". Too bad it's gone in G3.

Oh, and for asciiart, there is a command called "cowsay".


```

[sander@arch ~]$ cowsay "we are cows"
 _____________ 
< we are cows >
 ------------- 
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
[sander@arch ~]$ cowsay -d "I should stop drinking"
 ________________________ 
< I should stop drinking >
 ------------------------ 
        \   ^__^
         \  (xx)\_______
            (__)\       )\/\
             U  ||----w |
                ||     ||


```

---

### Post by Linuxratty on 2011-08-25
> **MG&TL said:**
> Recently, at my school, I used an Apple Mac that had been dual-booted with Windows so it could use the standard school network and applications/limitations. Anyway, I noticed that the mac version of grub looked considerably better than the current 'purple text' version we have with ubuntu.
. 

I am happy to donate photographs and/or artwork to help, if this is possible?

I like this idea.

---

### Post by sanderd17 on 2011-08-25
> **Linuxratty said:**
> I like this idea.

Yes, back on topic, maybe the best.


MG&TL, how far did you get? I didn't read the whole thread, but are you working on GRUB or BURG now, because it seems that BURG has great appearance, but also less powerfull settings

[http://blog.smronju.com/decorate-grub-2-boot-loader-using-burg/](http://blog.smronju.com/decorate-grub-2-boot-loader-using-burg/)

---

### Post by MG&amp;TL on 2011-08-25
Right...an update to save you two working through this somewhat enormous thread. I have written a program (with Grub2) to provide easy access to pre-installed grub themes.

I am still working on it, and it is pretty much infinitely extensible. It is nowhere near the standard of work produced by BURG and the like, but BURG is dead, and something like that on grub 2 produces serious lag.

It currently has two themes, and a PPA is being readied to provide it to the masses. Currently, once you have installed it, you run 'Grubby' in a terminal, and choose one of two themes:

Ubuntu-well, it's brown, human-theme like, Ubuntu.

Default-simple black and white text laid out in a more pleasing fashion with a title.


Many more themes are possible, I'm currently just concentrating on getting a PPA and making it stable. And we (me, cecil, and paddy) would love a GUI. It's been a little slow of late, as my computer keeps crashing, and because of family circumstances. So phil moving it to here is probably a good thing. And I have an Ubuntu laptop now, so production will increase. :)

Contribution is very welcome; especially in two areas. 

1) a PPA. I hate launchpad, and it's taken me 15 tries to get it so far, and it still isn't working. I daresay I'll get there eventually, but someone who's done it before would be very welcome.

2) Themes. The >two< I have currently are rubbish, and we need more. I need a background image, a colour palette, and some grub fonts (.pf2, use grub-mkfont. google it, that will explain better than me) And if you want fancy things like circular timers in your theme (any themes WILL be included), PM me.

---

### Post by Paddy Landau on 2011-08-25
Hey, TL, it's probably not a good idea to publish your email address here. The spammers will have a whale of a time with it. Rather let people PM you, and you can send your email to them like that.

Regarding themes, may I make a suggestion?

Rather than bundle pre-made themes with your program, what about this...

I think the ideal would be to concentrate on making a GUI package that does the following:

[LIST=1]
[*]Let people choose their own background, icons, text, timeout, etc. That is, let them design their own theme via the GUI.
[*]When a theme has been created, provide an option to "export" the theme from the GUI.
[*]Likewise, have an option to "import" a theme using the GUI.
[/LIST]

Then, let it loose!

People will create their own themes (just as they already do with the desktop). Encourage people to share their themes, perhaps in a new thread.

In other words, don't try to provide ready-made themes. Instead, provide the *mechanism* to create, export and import themes. People will provide themes.

(Of course, you can pick the ones you like the best and "bundle" them with your package. But the ability to export and import themes takes the pressure off *you* to create those themes.)

This would be ideal, because it provides maximum flexibility with maximum ease-of-use.

I hope that makes sense?

---

### Post by sanderd17 on 2011-08-25
I don't believe a GUI for theme making would give you a lot of benefit. I don't know what format is used now to write the themes, but if it is anything familiar (some kind of XML structure, or a bit CSS like) than the themes will come.

But getting your efford on OMGubuntu, Web Upd8 or similar sites will get some theme makers interested.

---

### Post by MG&amp;TL on 2011-08-25
Yeah, that was one of the eventual aims. No, it's not written in XML or CSS or anything like that, plain, honest-to-goodness shell script.

Yes, I agree with both of you. I disagree that I don't need more themes, not everyone will want to make a theme, but I agree that a theme framework is a Very Good Idea.

PPA should be up by this evening. If you're lucky.

BTW, if anyone wants a pre-release source .tar.gz to 'make' , feel free to PM me. oops about the email, slipped up. If only people didn't hack stuff. :(

---

### Post by Paddy Landau on 2011-08-26
> **sanderd17 said:**
> I don't believe a GUI for theme making would give you a lot of benefit.
I disagree. Look at how popular startup-manager was for Grub 1. Many people are like me in that they don't like the command line.

> **sanderd17 said:**
> But getting your efford on OMGubuntu, Web Upd8 or similar sites will get some theme makers interested.
Excellent idea!

> **MG&TL said:**
> oops about the email, slipped up. If only people didn't hack stuff. :(
You can go back and edit your post to remove the email address.

---

### Post by MG&amp;TL on 2011-08-30
Righty ho,

Back on task now. Two things have delayed progress:

1. Unexpected holiday.

2. Vicious bug that causes, among other things, non-booting, infinite loop of restart/crash/restart, bad resolution, basically anything that can go wrong, will go wrong. Fixed now though. :D

Have deleted email. oops.

---

### Post by Paddy Landau on 2011-08-30
Good to see you back, TL.

Have you had any thoughts about what direction you'll choose while you've been away?

---

### Post by MG&amp;TL on 2011-08-30
Yup, we'll take both, if that's ok with everyone.

I'm working on something that creates a theme, and I hope that anyone who likes this can put something on something like? Gnome-art or web-upd8 if this takes off.





Arrrgggh. Piping/redirection in Bash is horrible if you try and call it via C++.

I don't suppose anyone has a clue how you would import a launchpad key onto another pc. My laptop doesn't have my computer's PGP key, and I've had to do a reinstall of my OS on my pc. :confused: No problem, I can always just re-import a key, but it takes AGES. :(

---

### Post by cecilpierce on 2011-08-30
I wish someone would warn me about moving threads, geeeeeeeeeez
:confused:

---

### Post by MG&amp;TL on 2011-08-30
Ahhh...I wondered where you'd gone. I assumed I'd p****d you off in some way :( Apologies.

Sorry, I forget, because 'find all my threads' tells me where it is...know exactly what you mean though. When I was VERY much a newb, I posted a message in 'absolute beginner talk' saying that I'd found a bug in their forum, as my thread had disappeared. I was NOT popular for a bit...

---

### Post by Paddy Landau on 2011-08-30
> **cecilpierce said:**
> I wish someone would warn me about moving threads, geeeeeeeeeez
:confused:Strange. I got the usual email telling me about a new post, and it took me to the new (changed) thread.

> **MG&TL said:**
> When I was VERY much a newb, I posted a message in 'absolute beginner talk' saying that I'd found a bug in their forum, as my thread had disappeared. I was NOT popular for a bit...
LOL

---

### Post by MG&amp;TL on 2011-08-30
Grubby has failed to build twice and is being built now on launchpad...

<prayers>

---

### Post by MG&amp;TL on 2011-08-30
...and has now failed to build AGAIN.

I shall post for support, as it complains that it doesn't have permission, then if I include 'sudo' or 'su' in the makefile, it says that it can't find the commands...:confused:

---

### Post by Paddy Landau on 2011-08-30
> **MG&TL said:**
> ...and has now failed to build AGAIN.

I shall post for support, as it complains that it doesn't have permission, then if I include 'sudo' or 'su' in the makefile, it says that it can't find the commands...:confused:
Sorry I can't help with that. The only thing I can ask is: are you sure that you own all the files and that none of them is read-only?

---

### Post by cecilpierce on 2011-08-31
Whats up doc.

---

### Post by MG&amp;TL on 2011-08-31
Oh, it's cool, me being an idiot. Never done this before, so everything goes wrong.

"Grubbymake" as I've dubbed it, is coming along nicely. Over 200 lines of code already...<gulp>

It would seem you can't pass values to BASH, you have to write a shell script from C++, then execute in BASH automatically from the program. Hence I've had to use the temp directory. Ugly workaround, but it works.

---

### Post by MG&amp;TL on 2011-08-31
It builds on my own machine, it's just launchpad's build farm it doesn't like. Never mind, all fixed now, just gotta re-write makefile.

---

### Post by Paddy Landau on 2011-08-31
> **MG&TL said:**
> Hence I've had to use the temp directory.
If you need a short-term storage to pass values, and the file is small, use a RAM disk instead.

Linux has a built-in RAM disk -- which has recently been moved. The new RAM disk is supported in Ubuntu from version 11.10 onwards.

The old RAM disk (version 11.04 and prior) was [FONT=Courier New]/dev/shm[/FONT], and the new one is [FONT=Courier New]/run/shm[/FONT]. The good news is that for the foreseeable future, [FONT=Courier New]/dev/shm[/FONT] will be linked to [FONT=Courier New]/run/shm[/FONT]. So, for now, you can use [FONT=Courier New]/dev/shm[/FONT] in all versions. When version 11.04 and prior are no longer supported, you can change it permanently to [FONT=Courier New]/run/shm[/FONT].

In Bash, you can make a temporary file with the [FONT=Courier New]mktemp[/FONT] command:
```
TMPFILE=$( mktemp --tmpdir=/dev/shm filename-XXXXXXXX )
```This will create a file named [FONT=Courier New]/dev/shm/filename-XXXXXXXXXX[/FONT], where the "X" will be replaced with a random letter or digit. [FONT=Courier New]${TMPFILE}[/FONT] will contain the full path of the file. Do remember to delete the temporary file after you have finished with it.

Example:
```
GRUBBYTMPFILE=$( mktemp --tmpdir=/dev/shm grubby-XXXXXXXXXX )
echo ${GRUBBYTMPFILE}
[COLOR=DarkSlateGray]/dev/shm/grubby-IPfnx7YhJ5[/COLOR]
    :    :
    :    :
 rm ${GRUBBYTMPFILE}
```

---

### Post by MG&amp;TL on 2011-08-31
Yeah, could do that, does it work with directories? I'm not sure if launchpad likes that though, I'm trying to setup chroot and failing...maybe I'll just try uploading.

[http://ubuntuforums.org/showthread.php?t=1836028]("http://ubuntuforums.org/showthread.php?t=1836028")

Is the thread I asked for support on.

---

### Post by Paddy Landau on 2011-08-31
> **MG&TL said:**
> Yeah, could do that, does it work with directories?
Ah, sorry, I thought this was about your program rather than putting onto Launchpad. I've never used Launchpad, so I cannot help there.

I do notice that you are loading to /tmp -- isn't that shared by everyone? There would be a risk of you overwriting someone else's files, or vice-versa. I would imagine you need to create a directory within /tmp and use that? (Sorry if I'm talking nonsense; I don't know Launchpad.)

You can use mktemp with a directory, as:
```
TMPDIR=$( mktemp **--directory** --tmpdir=/dev/shm grubby-XXXXXXXXXX )
```(Or you could use [FONT=Courier New]--tmpdir=/tmp[/FONT] if you wanted the hard disk.)

---

### Post by MG&amp;TL on 2011-08-31
Nah, it's OK, it's "debian/tmp". Debian is the file in a debian package that tells everything where to go, what to do, and how to decode it.

I'll use mktemp in Grubbymake, when I can get it to compile.

---

### Post by MG&amp;TL on 2011-08-31
Progress IS being made with the packaging, it's just slow. And TEDIOUS. :( 

Luckily UF has sprung to the rescue again.

---

### Post by MG&amp;TL on 2011-08-31
YES! PPA is up and built. :D :D :D

Go to here:

[https://launchpad.net/~michaelrawson76/+archive/grubby]("https://launchpad.net/~michaelrawson76/+archive/grubby")

And add to your software sources or whatever.

I have a feeling that I might have to build different packages for different releases...but I'll do that tomorrow, I have a headache...:(

Thanks for being patient, guys. If one of you would care to test it for me? You SHOULD be able to get it from the software centre...please be careful, though. Don't break anything important for me.

---

### Post by MG&amp;TL on 2011-09-01
...or there again not. Be fixed in a couple of hours, I think.

---

### Post by Paddy Landau on 2011-09-01
I've just spotted a [Grub Customizer how-to]("http://ubuntuforums.org/showthread.php?t=1664134"). Would it help you at all?

---

### Post by MG&amp;TL on 2011-09-01
It would seem we have been superseded somewhat...move on to something else, or keep at it?

---

### Post by Paddy Landau on 2011-09-01
> **MG&TL said:**
> It would seem we have been superseded somewhat...move on to something else, or keep at it?
Oh heck, I hadn't looked at the post properly. I thought it was about *manually* changing Grub.

I will reserve some time this afternoon to look at it properly, and get back to you.

---

### Post by MG&amp;TL on 2011-09-01
Thanks paddy.

---

### Post by MG&amp;TL on 2011-09-01
Don't get me wrong, I love Grubby and the work that's gone into it, it's just that I don't want to develop something that's already there. On the other hand, there must be some use for 24 source code files...:confused:

---

### Post by Paddy Landau on 2011-09-01
Well, I've been wanting to test, but every time I try to install Lubuntu in a VM, it hangs.

I may try a minimal installation. I'll let you know if I manage to test.

---

### Post by Paddy Landau on 2011-09-01
> **MG&TL said:**
> ... I don't want to develop something that's already there.
I've managed to get it working. I don't know what was wrong, but it's fixed.

Um... Grub Customizer is nice. But it doesn't do all of the nice things that you were looking at, does it? Such as icons instead of text, and hiding the recovery options.

Let's see...

What Grub 2 does:

[LIST]
[*]Hides kernels other than the most recent in a sub-menu
[/LIST]
What Grub Customizer does:

[LIST]
[*]Change the background
[*]Decide which kernels to display
[*]Decide whether or not to display the menu by default
[*]Set the menu time-out if displayed
[*]Change the default boot item
[*]Change the background and text colours
[*]Change the screen resolution
[*]... and some other features
[/LIST]
What Grubby could do extra:

[LIST]
[*]Move the recovery option into the sub-menu (or can Grub Customizer do this already?)
[*]Show icons with brief text (e.g. "Windows XP", "Ubuntu 10.10", "Mac OS") instead of plain text
[/LIST]
If you could do even those last two items, that would make Grubby valuable.

Once you have succeeded, you could suggest to Daniel Richter that your code be incorporated into Grub Customizer (it may have to be rewritten, but that should be easy once you have done it the first time). I'm sure Daniel would give his blessing.

---

### Post by Nyromith on 2011-09-01
Whatever appearance improvements you make up, don't forget to include an option to turn them off.

---

### Post by MG&amp;TL on 2011-09-01
Thats's fairly easy, Nyromith. You just replace /etc/default/grub with the default, and all is back to normal...

Paddy-

1) What's the sub-menu?

2) I never got the GRUB icons to work...drs has no clue, and it's a registered bug in Bennet's code. Which is no longer maintained. :confused:

BUT-does Grub Customizer support timers and other such eyecandy?

Happy to know I still have a project. I'll 'apt-get source' his project, and see what I can mod. I'll then email him and see if he's willing.

---

### Post by MG&amp;TL on 2011-09-01
Recovery options can be turned off. Very easily. But not put into the sub-menu. :confused:

EDIT: actually, Grub customizer does this. Preferences>Advanced>Kernel parameters>Generate recovery mode entries

---

### Post by MG&amp;TL on 2011-09-01
apt-get source don't work. I shall have to email for it. Assuming that the guy has made it open-source...

---

### Post by MG&amp;TL on 2011-09-01
Hi everybody. I have contacted the developer and he says he is happy to merge my project and his IF I can get it to work. So this project now consists of me trying to get my 'plugin' to work on his project. Is this a direction that people agree with?

Lovely bunch of people on UF. Hope it continues for many years. <sniff, dist-patriotic sigh> ;)

---

### Post by cecilpierce on 2011-09-01
Good going there old man!
 make it better then BURG 
:lolflag:

---

### Post by MG&amp;TL on 2011-09-01
Cecil! Where did you get to?

old man? Who are you calling old!? :P

How's it going with the boat and kid's school? Gotta go in 4 days myself...

If you're happy with it, yeah, good going! ...'course it's going to be better than BURG, I don't abandon my projects, and my name's not bean. :)

---

### Post by cecilpierce on 2011-09-01
@MG&TL (More Grub To Love)

Ive been going crazy trying to get Arch installed ! What a pain in the ars.
 :P

---

### Post by MG&amp;TL on 2011-09-01
I did quiz the guy who made the acccount, he says 'Maths Geekyness and Tux Love' Um...right.

Can't agree with you more about Arch. On the other hand, while it's not Linux, and practically nothing works, Haiku OS (an open-source remake of BeOS) is worth a look; the API is fantastic, it comes with a bare minimum of tools, and it's compatible with Grub2. Unless you have ancient Wifi, wireless internet won't work. Dial-up is apparently 'dodgy'. Can't fault them for simplicity, though.

And it comes with a rather cool 3d tester. You know glxgears, from mesa-utils (you must know glxgears, the red/green/blue cogs), you get a spinning OpenGL teapot instead.

Anyways. another couple of lines of code added. Had trouble with the compile stage, apparently three #includes (include directives, sort of like a 'go here' statement in programming) away, there was an error, and it only just got reported. Sigh. Anyway, fixed now.

---

### Post by Paddy Landau on 2011-09-02
> **MG&TL said:**
> 1) What's the sub-menu?
I read about it in the [Grub Customizer how-to]("http://ubuntuforums.org/showthread.php?t=1664134"):> Grub Customizer has yet to deal with the new *submenu* feature introduced in Grub 1.99 and Natty. Grub 1.99 places all but the newest kernel in a submenu..
> **MG&TL said:**
> does Grub Customizer support timers and other such eyecandy?
Yes. See the first post in the above-mentioned thread for screen-shots and a description.

> **MG&TL said:**
> I have contacted the developer and he says he is happy to merge my project and his IF I can get it to work. So this project now consists of me trying to get my 'plugin' to work on his project. Is this a direction that people agree with?Excellent! Yes, I think this would be great. Grub Customizer does all the important bits; the final step of great eye-candy is what is missing. Specifically, using lovely icons with brief text for the primary boot options, and putting all other items into the submenu. You won't be able to use lovely icons with the submenu, though, although you may be able to use small icons.

> **MG&TL said:**
> Lovely bunch of people on UF. Hope it continues for many years. <sniff, dist-patriotic sigh> ;)Oh yes, this is one of the friendliest and helpful forums I've come across.

> **cecilpierce said:**
> Ive been going crazy trying to get Arch installed !I was reading last night about Arch. Bearing in mind that Linux's [kernel.org]("http://kernel.org/") was [recently hacked]("http://ubuntuforums.org/showthread.php?t=1837305"), and that Arch does not sign its packages, it may not be the best distro to go for from a security point of view.

---

### Post by MG&amp;TL on 2011-09-02
Whoah. Surely they could make more money (and have more fun) hacking something like a shop website, not the kernel.org page? It's obscure enough...

Yup, I'm having a look at the gfxmenu source code to find out why the icons don't work.

---

### Post by sanderd17 on 2011-09-02
For those icons, maybe a dirty hack, but can you change the background image while GRUB is loaded?

If you can, you could make different background images (with a glow on different places, an icon on different places) and when the user hits one of the arrows, the background image gets changed.

making such different backgrounds should happen when grub is updated via a script.

OT:
> **Paddy Landau said:**
> 
I was reading last night about Arch. Bearing in mind that Linux's [kernel.org]("http://kernel.org/") was [recently hacked]("http://ubuntuforums.org/showthread.php?t=1837305"), and that Arch does not sign its packages, it may not be the best distro to go for from a security point of view.

No Arch is not secure, nobody uses rolling releases for stability, safety or security. Btw, the maintainers of the Arch repositories are called "trusted users". Anyone can become a trusted user if you prove you have some knowledge.

But Arch is wickedly fast, has cutting edge software and is completely configurable.

---

### Post by MG&amp;TL on 2011-09-02
Well, you could...

I see no reason why this would not work, but on my 'slow' test machine (minimal install Vbox with 64Mb RAM, and Naff-all CPU), there is a slight blink when re-drawing GRUB. Reloading an image would cause a bigger blink? I don't know how far up the system scale this would go, but I guess that it could cause major blinkage up to around 512Mb/Pentium 4...

I shall have to look, but if I can find a way around the bug, I will. Welcome to the n00b project, btw. (as in made by one, not supported/used by them)

---

### Post by Paddy Landau on 2011-09-02
> **MG&TL said:**
> Surely they could make more money (and have more fun) hacking something like a shop website, not the kernel.org page?
That depends why they hack. Illegal hackers cause huge problems; it's as bad as robbing someone on the street, though they seem to think it's funny.

> **sanderd17 said:**
> ... you could make different background images (with a glow on different places, an icon on different places) and when the user hits one of the arrows, the background image gets changed.
Smashing idea!

> **MG&TL said:**
> I see no reason why this would not work, but on my 'slow' test machine (minimal install Vbox with 64Mb RAM, and Naff-all CPU), there is a slight blink when re-drawing GRUB. Reloading an image would cause a bigger blink? I don't know how far up the system scale this would go, but I guess that it could cause major blinkage up to around 512Mb/Pentium 4...
As my VM is working, I'd be happy to test it for you on a faster machine.

---

### Post by MG&amp;TL on 2011-09-02
Hmmm...well, the icons are meant to be only a couple of lines in the theme.txt, so I'll see if there's a fix for the icons first, as writing a script for that will take a while...actually, Is it necessary to draw the icons separately onto the image, or could we just have a pre-made image that draws the icons listed in grub customiser?

I have to go away for three days without internet, but I should be devloping through then...see you tuesday. Sorry about my unreliability, that should calm down as soon as term starts...

I CAN have a faster VM, it's just that I wanted to make sure it ran on everyone's machine first. If you're willing, though Paddy, that's great.

Does anyone knowhow to draw/redraw image in BASH?

---

### Post by Paddy Landau on 2011-09-02
> **MG&TL said:**
> Is it necessary to draw the icons separately onto the image, or could we just have a pre-made image that draws the icons listed in grub customiser?
I'm not entirely sure what you mean by that.

> **MG&TL said:**
> I CAN have a faster VM, it's just that I wanted to make sure it ran on everyone's machine first. If you're willing, though Paddy, that's great.
Yes, I'm willing. It's my way of helping.

> **MG&TL said:**
> Does anyone knowhow to draw/redraw image in BASH?
Do you mean how to draw an image on the screen? AFAIK, there is no built-in command. I imagine this would have to be the application that draws Grub. How does Burg do it?

If you are asking how to modify an image, use [FONT=Courier New]convert[/FONT]; part of the [ImageMagick]("apt:imagemagick") suite. Use [FONT=Courier New]man imagemagick[/FONT] and [FONT=Courier New]man convert[/FONT] to discover more. There is also [FONT=Courier New]mogrify[/FONT], which is identical to [FONT=Courier New]convert[/FONT] except that it overwrites the original.

---

### Post by MG&amp;TL on 2011-09-06
Well, I got talking to the grub customizer chap, and he says that's fine. (YAY!) So now I just gotta work out where everything goes...:confused:

I email-ed the guy for help.

---

### Post by cecilpierce on 2011-09-06
What are your plans for the GC ?

---

### Post by MG&amp;TL on 2011-09-06
Simply a tick box that says 'use theme' under the appearance tab, then a dialog to choose a theme, or make a new one, eventually. If people want it, I can still produce a stand-alone executable, but I'll concentrate on GC for now. Is this okay?

---

### Post by cecilpierce on 2011-09-06
Fine with me, have fun  :p

---

### Post by MG&amp;TL on 2011-09-06
Yeah, yeah, whatever. ;) 

Well, it didn't go where I thought it would go, but oh well. This ain't bad.

---

### Post by MG&amp;TL on 2011-09-07
Maintainer says that I should concentrate on producing source code, and he'll do the porting to his code. :D

Version 3.0 of grub customizer should include it.

Fixed the blink, btw, I set a custom resolution through GC and it works now :confused:

---

