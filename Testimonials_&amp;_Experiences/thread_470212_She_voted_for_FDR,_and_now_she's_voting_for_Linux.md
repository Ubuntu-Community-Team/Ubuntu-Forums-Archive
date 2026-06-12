---
title: "She voted for FDR, and now she's voting for Linux"
date: 2007-06-10
forum: Testimonials &amp; Experiences
---

### Post by MattDTownsend on 2007-06-10
I've been using Linux for years, and when my 82-year-old grandmother complained that Outlook wasn't downloading her e-mails anymore (sockets weren't opening, period), I decided it was time to wipe Windows 98 off of the clunker and try installing xubuntu.

With a 400 mhz celeron and 64 mb of ram, I found it necessary to put her hard drive into my tower to perform the actual install, and I crossed my fingers that, when replaced, her dinosaur would be able to run XFCE smoothly.  Well, it sure isn't sexy, and it sure isn't fast, but it runs.  Sort of like my grandmother.

She has no trouble accessing her e-mail through Evolution and finds the program easier to manage than Outlook, especially with attachments.  At her age, my grandmother's vision is pretty much in the crapper, but this was no problem with XFCE, since I could make panel icons enormously large, remove desktop icons to discard clutter, use high-contrast themes with brightly-coloured window buttons, etc.  She has four items on the panel:  the Evolution icon, the Firefox icon, a gigantic digital clock, and the halt button.  Which, to her amazement, actually shuts down the system every time.

Just shows you that, were it pre-installed, even the least computer-savvy users would have no problem with Linux -- which is far fewer problems than they oft have with Windows.

---

### Post by Geekkit on 2007-06-10
Hah, that's great to hear, glad she's finding it easier. :p

---

### Post by brownknight on 2007-06-10
Hah! That made me smile. Nice to hear :)

---

### Post by octathlon on 2007-06-10
Great job.  Out of curiosity, is she on dial-up?  

I ask because I set up my mom (72) with MEPIS, and did the whole thing like you did with big icons and fonts, but I didn't know how to make the modem automatically dial whenever she starts the browser or email.  Her Win98 would do that and also ask if she wanted to hang up when she closed the browser.  Were you able to set that up for your grandmother?  Anyway, my mom has no problems either and she's glad she didn't have to buy a new computer. :)

---

### Post by MattDTownsend on 2007-06-10
She lives with my parents, and they recently switched to broadband.  So, that problem is solved.

So far as your concern, you might try a bash script.

#!/bin/bash
# Paste this into a file, like /usr/local/bin/momnet as root/with sudo
# Save it, and then run sudo chmod +x /usr/local/bin/momnet

gnome-ppp &
# Gnome-PPP is launched, and the "&" allows the script to continue.

sleep 45
# We wait for 45 seconds for the connection to happen.  You can tweak this.

firefox
# Firefox is launched, but because there is no "&", the script holds until
# firefox is quit.  You should install the firefox quit button extension
# so she can easily quit the program.

killall -1 gnome-ppp
# killall -1 tells Gnome-PPP to quit, rather than killing it by force.
# It reports "Hangup" to stdout when this is run, which is what you want.

# End of file

---

### Post by octathlon on 2007-06-10
Wow, very interesting, I thought there might be a way to make a script for it.  Of course, she now has the procedure down pat, but it would be a good learning experience for me to play with it, maybe have it ask first before disconnecting and so forth.  I haven't heard of the quit button extension either.

Thanks! :)

---

### Post by djchandler on 2007-06-10
Hey, MattDTownsend, great thread. I'd like to get my Mom and Dad set up with a computer, but they resist, and they are about the same age. It sounds like your grandmother is a very interesting person. It's great you were able to get her set up with a working system. 

Linux would be a great way to get some of our parents and grandparents involved with email and forums, and give them something else interesting to do besides sitting around waiting for the grim reaper. We have a local source of re-cycled computer parts here in the Kansas City area, and I've been able to pick up bits and pieces to build computers to donate, and your post has just given me another idea to put into action here in my area. I bet that old box of your grandmother's could be upgraded to a PIII and you could extend its life even more than you already have.

This could be a great way for some of us to spread Linux around more. Glad you could help your grandmother out, and you posted the experience here. :D

---

### Post by MattDTownsend on 2007-06-10
A bit of a Mickey Mouse job, but this seems to work:

#!/bin/bash
# Paste this into a file, like /usr/local/bin/momnet as root/with sudo
# Save it, and then run sude chmod +x /usr/local/bin/momnet

gnome-ppp &
# Gnome-PPP is launched, and the "&" allows the script to continue.

sleep 45
# We wait for 45 seconds for the connection to happen.  You can tweak this.

firefox
# Firefox is launched, but because there is no "&", the script stops until
# firefox is quit.  You should install the firefox quit button extension
# so she can easily quit the program.

# prompt is below
xmessage -buttons Disconnect:0,Remain:1 "Disconnect or remain online?" -center 
if [ "$PIPESTATUS" == "0" ]; then
echo Disconnecting.
killall -1 gnome-ppp
else
echo Remaining online.
fi

exit

# End of file

---

### Post by MattDTownsend on 2007-06-10
Firefox has extensions now that can wipe your butt for you, if you like.  The quit button is one of the nicer ones.

djchandler:  There's something nice about seeing Linux work for the very young and very old.  Not to mention the very poor and the very distant.  Ubuntu is a great OS for those who are forgotten because, ultimately, they're as much a part of the computing community as anyone else.

As I was working on her install, I kept thinking about what could be done to make Linux easier for the elderly.  That is, make it easier for people like us to set it up for the elderly and leave them alone with it.  My grandmother was concerned about not being able to use her computer with linux because she'd have to learn things -- interestingly enough, she was reading and replying to e-mails in Evolution before I had a chance to sit down and discuss it with her, telling her sister how she "still has to learn the new computer system."

Mission accomplished.

I imagine after a week or two, she'll realize there was never anything to learn.  After all, it is hard to miss the enormous e-mail button on the XFCE bar, or the equally large shutdown button.  I can't imagine what this woman would do with Vista.  She'd give up on e-mail, all together, because Vista would be way too complicated to even look at.  It's too complicated for me, and I've been running *nix since RH5.  Vista makes FreeBSD look friendly.

Maybe we should try to put together a guide and start increasing interest in this.  There must be many other people out there, like us, who are sick of keeping elderly parents'/grandparents' machines running operating systems from 1998.  Maybe something on the wiki?  There needs to be some kind of effort to consolidate software, accessibility options, and even arguments for converting them. 

You know, if Ubuntu could put together a nice package that, with one apt-get command, would make the desktop elderly-friendly, those Dell machines could get AARP support.

---

### Post by weblordpepe on 2007-06-11
Oh yeah totally. Being able to have huge configuration packages which instantly turn Ubuntu into a targeted system would RULE.

Eg: Being able to turn Ubuntu into Ubuntu studio. Or being able to turn Ubuntu into Eubuntu.

Anyway back on topic: Thats a great story. Its one worth bookmarking. 
I have set up many computers for people, with icons etc. I am yet to do it with Linux. My main fear is applications. But things are changing, now.

---

### Post by MattDTownsend on 2007-06-11
I could be wrong, but can't you just type

sudo apt-get install edubuntu-desktop

for that?

I've never tried it, since I'm not interested in frakking my system. . .but it may be worth trying to see.

So, what we'd really need is just an Ubuntu BlueHair Edition. . .errr, Silver Edition, or somesuch.  Probably built on xubuntu, since they oft use slower computers/don't want lots of widgets.

---

### Post by Al Fairclough on 2007-06-11
Actually, Matt, that is a really great idea, IMO.

---

### Post by octathlon on 2007-06-11
Matt,
I think that's a good idea and maybe it woud fall under the Accessibility category.  But wouldn't a theme pretty much do it?  Large fonts, large icons, large cursors, large window buttons/scrollbars, good contrasting colors.

Learning about creating themes is on my to-do-one-of-these-days list.  One of the first things I always did in Windows was go into Desktop properties and increase the width of the scrollbar and size of the window close buttons, to make them easier to click on, less precision needed.  I finally found how to increase scrollbar width (a little bit only) in KDE, but there seems to be no way to do it in Gnome.

---

### Post by lexdave on 2007-06-12
sudo apt-get install kubuntu-desktop is a valid command and it does download the kubuntu (KDE) desktop, but it also downloads everything the makes kubuntu different from Ubuntu: all of the KDE files and programs that come default with kubuntu (took me a solid 90 minutes to download at work - I work for an ISP with an 3.5 Gig pipe - that was a big file).

I believe you can download just KDE or xforce separate and have them replace gnome if you wanted to.  Much easily and faster IMO.

Good work on setting up your grandmothers computer, I'm getting ready to face the same choice on moving my grandparents over as well but I need to see their setup first and see what will and wont work.

---

### Post by MattDTownsend on 2007-06-12
> **octathlon said:**
> Matt,
I finally found how to increase scrollbar width (a little bit only) in KDE, but there seems to be no way to do it in Gnome.

Thanks for reminding me to look into this -- my grandmother has a tremor, and she has a hell of a time clicking those little 10 point bars!

In GTK, scrollbar size is theme-controlled (actually, good for our goals if we want to make a theme).  I chose Crux for her, since it has a coloured scroll slider. . .easier to see.  So, the following -definitely- applies to the Crux theme.

Open the gtkrc in the theme file.  For crux, 
*sudo gedit /usr/share/themes/Crux/gtk-2.0/gtkrc*

Find this section:
[I]
GtkRange::slider_width = 13
  GtkRange::stepper_size = 13
  GtkRange::trough_border = 1

  GtkScale::slider_width = 12
  GtkScale::stepper_size = 12
  GtkScale::trough_border = 0[/I]

and change it to something like this:

[I]GtkRange::slider_width = 24
  GtkRange::stepper_size = 24
  GtkRange::trough_border = 1

  GtkScale::slider_width = 24
  GtkScale::stepper_size = 24
  GtkScale::trough_border = 0[/I]

Save, close, and reload the theme in the manager.

At 1024x768, 24 sliders are hard to miss.

---

### Post by MattDTownsend on 2007-06-12
It's a good point that a nice theme is an important part of accessibility, but I think it's important to remember that we're using Microsoft's definition of accessible, here.  That is, when we speak of accessibility and computers, we're probably talking about that stupid Windows 95 control panel with four or five tabs for oversized fonts, special beeps and sticky keys.  Oooh.  Ahhhh.

In other words, accessibility should imply accessible -- that is, possible to access.  Small screen resolution is not the only trouble the elderly have with accessing computers.  I grew up in Florida, so I've dealt with older computer users a lot. . .they need simple software, scripted events, etc. . .basically, the computing experience needs to be as basic as possible.  The more menus and programs installed, the more daunting the process seems. . .since most want only basic web and e-mail access.  I think they can be introduced to more, like the relationship between computers and audio, but this needs to be done with applications like Striim rather than RhythmBox.  Simple, one or two buttons, no digging through directories, etc.  Skype is another nice program for an older person, once all of the extra tools/options are removed from the screen.  Thunderbird is a great application, but in the hands of an elderly computer user, it's a nightmare of options and submenus -- e-mail, GIMP-style.  Certain views can't be changed, panels can't easily be removed, and attachments are just kind of barfed out at the end of the message.  Evolution's simpler approach both to reading and composition makes it a better choice.

In my experience, many older users, if they are capable of starting the computer up and reading/sending e-mail, are terrified of "breaking their computer."  This concern often doesn't go away, as it has been reinforced by years of Micro$oft applications breaking on their own.   So far, the best way of abating this fear, that I've found, is simply stripping everything down to the most basic, simple interface.  (It's hard to "break" something with three buttons.)  Which, coincidentally, makes it all easier to see, anyway.

---

### Post by skirkpatrick on 2007-06-12
I don't know if there is an easy package in the repos to do dial-on-demand but a quick Google brought up this website: [http://nleaudio.com/bnotes/dialondemand.htm](http://nleaudio.com/bnotes/dialondemand.htm)

---

### Post by octathlon on 2007-06-12
> Save, close, and reload the theme in the manager.

Uh, gee ... *That *didn't work out too well.  Coming to you from Windows XP now, because I can't even start my Gnome session, not even Failsafe Gnome!

What I did was I edited the Clearlooks file rather than Crux.  I just changed a couple of things from 15 to 22 and saved the file.  Then I opened the Theme manager and clicked on Clearlooks, that's when everything started crashing, such as all my panel apps.  Then I ctrl-alt-backspace and tried to log in again, Gnome started but Trash can, mixer, etc. wouldn't start. I used Theme manager to switch to a completely different theme, I logged out and back in, this time Gnome would not even start. I restarted the computer and tried to log in-- nothing but blank blinking panels, then tried Gnome Failsafe and that would not start either.

Just checked and I am able to log into a KDE session, but I'm not sure how to fix Gnome configuration.  One false move and the whole thing is hosed, unbelievable. Do you know of a log file I can look at to figure what what is causing the problem or anything?

:'(

---

### Post by MattDTownsend on 2007-06-12
Hey, I said Crux, mate.  :-p

Seriously though, I'd try, first, an apt-get remove gnome-themes and then an apt-get install gnome-themes . . . see if that might cover it.  Otherwise, I'd try moving the Clearlooks directory to a backup location (as opposed to deleting it, so if things get worse you can fix it).  I suspect if you remove/move the theme, gnome should default over to something else and the problem will be solved.  Clearlooks is pretty well pixmapped. . .that might be the problem.

And, of course, if you can't do shite in X and need a terminal, hit Ctrl+Alt+F1 (and Ctrl+Alt+F7 to go back to X).

MT

---

### Post by octathlon on 2007-06-12
Looking at the file from Konqueror, it thinks it is a Java Source File instead of a Plain Text file, which is how it sees the other themes' gtkrc.

That's weird.  I don't know how it decides what file type it is when there is no extension and it just contains text.  I tried various things, making a new plain text and pasting the text in, but once I paste in the text it reverts to thinking it is a Java Source file.  

I also get a bunch of cryptic errors when trying to edit the file, so something is screwy; it's not just a case of editing a normal text config file.  hmmm  I'll be back later ...

---

### Post by octathlon on 2007-06-12
hmmm, when I tell it to remove gnome-themes it says " the following will be removed - gnome-themes, ubuntu-desktop"
!!!! I don't want to remove ubuntu-desktop 

arrgg, maybe I'll have to.

 moving the Clearlooks directory did not have any effect, BTW.  Gnome still doesn't start and just has a blank desktop with blinking blank panels.

---

### Post by MattDTownsend on 2007-06-12
The package "ubuntu-desktop" is only a placeholder of sorts. . .it just means that you have everything installed that qualifies as "ubuntu-desktop" as opposed to "kubuntu-desktop" or "edubuntu-desktop."  I'm guessing it's a 0k package, or close to it.  So, you can safely remove it, and then reinstall it to feel at ease.

You know, here we are talking about the elderly having problems with computers. . .and, well.  

Oops. :p

---

### Post by octathlon on 2007-06-12
Well, I think it's **ridiculous **that editing and/or corrupting a THEME config file would completely take down my Gnome Desktop!  Let's see, how did that question go again, something like "is Linux ready for the desktop?" or something like that.... I mean, how could that have even happened? 

As for ubuntu-desktop being a placeholder --- I don't know, all I know is when I said install kbuntu-desktop, it installed everything for Kubuntu desktop, so ... hmmm, I guess I'll back up all my gnome config files in my home directory and give it a shot... 
heh

---

### Post by MattDTownsend on 2007-06-12
It really depends upon how you edited the file.  When I looked at the gtkrc for Clearlooks, I didn't see any pre-existing lines for slider size.  So, I'm not sure what you edited.

And I agree -- it shouldn't take down the system.  Maybe we've discovered a new bug, or a place where gnome could improve?  Personally, I can't stand gnome, but it's not nearly as bloated as KDE and I don't feel like using fluxbox, again.  Honestly, I miss Enlightenment DR15.  Those were the days.  Maybe this makes Linux less ready for the desktop, but keep in mind that it's not particularly easy to edit windows themes.  If you can.  Which I doubt.

If you tell it to install ubuntu-desktop and you already have all but one program in ubuntu-desktop, it won't have much to install.  And if it says it wants to install 500 packages, hit the N key.

You might get the theme file from gnome-look or freshmeat and replace it.  Maybe that'll help.  Again, do backups, and extract everything in your home directory first.  I don't really know your proficiency with linux or the terminal, but if you get tired of sudo'ing, type sudo xterm.  Just don't "break your computer," as it were.

I'm not sure why gnome wouldn't default to something else, unless it's holding a bad copy of the rc file in your home directory.  Poke around in ~/.config

Edit: dumb question
Have you tried calling gnome-theme-manager from KDE?  :-)

---

### Post by octathlon on 2007-06-12
Well, I did the remove and install of gnome-themes.  But it made no difference, Gnome will not start.  I have no idea what happened.  I swear, all I did was edit that file.

I guess I really will need to remove and reinstall the complete gnome desktop at this point, somehow.

---

### Post by octathlon on 2007-06-12
Funny, Clearlooks is back, but the gtk-2.0 subdirectory is not there.  I think something else got messed up somewhere when everything went crazy after I opened the Theme manager and tried to select Clearlooks.

I'm not sure how to tell it to totally remove gnome-desktop since removing "ubuntu-desktop" didn't actually remove anything, as you predicted.  

KDE appears to be working fine, at least.  I switch between them every so often because there are things I like and dislike about each.  Right now I really really dislike Gnome, heh.

---

### Post by MattDTownsend on 2007-06-12
Exactly.  Removing ubuntu-desktop does nothing.  It's just a placeholder, as I said, like a 0kb package.

To remove gnome, you'd use apt-get remove gnome, I believe.  HOWEVER, if your problem is NOT the theme file, this will do next to nothing.  As I said, it could be a setting that's been held-over in your home dir.  To rule this out, you should try creating a new user (easy enough) and log in with gnome.  If you have problems with that new user, then you know it's a problem outside of /home/ and may be worthy of a complete gnome removal.  Don't go pulling teeth if you only need to fill a cavity.

---

### Post by octathlon on 2007-06-12
Yes, you're right!  I logged in as a different user and it was fine.  Good point, I was getting frustrated and not thinking clearly.

---

### Post by MattDTownsend on 2007-06-12
Well, just as the elder computer users think they break their computer by adjusting the volume control, sometimes, it's easy to get upset when you're encountering new things.  Just keep in mind that it's nearly impossible to destroy Linux or Gnome without sweeping uses of sudo.  On things other than theme files.

It may take you a spot of time to find where that rotten file is located in your ~ dir, but I'm sure you will.

My motherboard kicked the bucket last night, so I can't do much right now for theme creation.  However, I think once I drop the new one in, I'll put together a nice, accessible theme based upon whatever theme doesn't make Gnome crap itself.  Crux could work.

---

### Post by octathlon on 2007-06-12
Sorry to hear about your motherboard!  I just ordered a laptop from System76 so I'm awaiting that with anticipation.  

In spite of this event, or maybe moreso because of it, haha, I'm still interested in learning about themes and I think the idea of a "senior theme" is a good one, definitely needed.  Keep us posted on what you come up with. 

 Thanks for the help. :)

---

### Post by dschaller on 2007-06-13
> **MattDTownsend said:**
> Exactly.  Removing ubuntu-desktop does nothing.  It's just a placeholder, as I said, like a 0kb package.

It's not exactly a 0kb package, but it does not contain any installable programs. It is a dependency package. When it is installed, it makes sure that all the Ubuntu components are on your machine that are supposed to be there with a regular install. So it doesn't really wipe out anything to remove it. Mine gets removed all the time because of various "unofficial" packages I add or take away from my system. Not a big deal.

It is, however, a good idea to make sure it is installed if you are going to do an upgrade from one version of Ubuntu to another. That way you have a clean upgrade path and less chance of programs breaking because of the upgrade.

---

### Post by octathlon on 2007-06-14
@dschaller:  Thanks for the info about ubuntu-desktop. :)

@Matt:  FYI, I managed to get my gnome desktop back by luckily guessing right which file was the problem by looking at the date modified and so forth, then deleting it as it didn't seem to be required. Phew!

---

### Post by StooJ on 2008-04-24
How are things progressing on your theme?

My Gran's eyesight is getting worse & worse, so I am hoping to migrate her to Xubuntu as soon as possible, trimmed down to simplicity & with large fonts & icons.

I'll need to buy her a new scanner, but that's OK. Her current scanner refuses to work with linux.

---

