---
title: "Win 7 RC through VirtualBox 3 -- works great!"
date: 2009-08-20
forum: System76 Support
---

### Post by samalex on 2009-08-20
Hey Guys ...

There's been several folks comment on installing Windows through VirtualBox, but I wanted to throw this out incase someone wanted to try Windows 7.  Microsoft is offering Win 7 RC free to download from this site:
[http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx](http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx)

I downloaded the 32-bit version last night (2.5 Gigs) and it installed perfectly using VirtualBox 3.0.4 on my PanP5 system.  The audio driver wasn't picked up at first, even after installing the VirtualBox Guest software, but a Windows update downloaded the driver from Microsoft's site and all is golden now.  

This version is Win 7 Ultimate and it expires on March 1, 2010.  I'll use it until then and if I get any benefit out of it I may look at getting it and moving away from Win XP, which is installed on a separate VirtualBox system.

Anyway, just an FYI. Oh, and today is the last day Microsoft is letting people download this.  It won't be available tomorrow.

Sam

---

### Post by miniyak on 2009-08-20
thanks for the tip, though i hate windows, i'll  pick up the rc for support sake. do you think it matters if its the 64bit or the 32bit version? I not sure this matters to virtual box, i think ill go with the 32 by gut feeling...

---

### Post by samalex on 2009-08-20
[QUOTE="miniyak"]thanks for the tip, though i hate windows, i'll pick up the rc for support sake. do you think it matters if its the 64bit or the 32bit version? I not sure this matters to virtual box, i think ill go with the 32 by gut feeling...[/QUOTE]

I'm there with ya, but I foresee us moving to Windows 7 at work eventually, so I figure I'd better brush-up on it to some degree.  Plus I keep hearing promising things about it, so figured if it's free I'll try it out.

I already have an instance of XP going via VirtualBox which has everything I need, so I'm sure after March 1st when the Win 7 RC expires I'll drop it in the trash and move on.  Maybe eventually if I can find Win 7 dirt cheap I _may_ invest in it, but no time soon as it'll never be my primary operating system outside of work.

Sam

---

### Post by texla on 2009-08-20
> **samalex said:**
> Hey Guys ...

  Oh, and today is the last day Microsoft is letting people download this.  It won't be available tomorrow.

Sam

Dead now - Signed up and it says: 

"We're sorry, but downloads are no longer available."

:confused:

---

### Post by Hogosha on 2009-08-20
yeah, yesterday was the last day to get the iso and a valid key. That could have been one of the biggest selling points of Windows 7 if they kept it up. The RC is good for nearly a year so they should have just let people keep trying it. But i have not done several millions in market research so what do i know

---

### Post by samalex on 2009-08-20
> Dead now - Signed up and it says:

"We're sorry, but downloads are no longer available."

It was working just a few hours ago... I thought it ended on the 20th so I assumed it would work all day.  Looks like you can still get the key but not the download itself.  Bummer.

I'd put the ISO out there for anyone to grab, but my upstream at home is WAY too slow to pull a file that large over in any reasonable amount of time.

Sorry for the confusion then...  :???:

Sam

---

### Post by miniyak on 2009-08-20
the sign up ordeal with ms was kind of annoying but i guess you have to put some deterrents in place when your hosting a 2.5 GB file on a MS server... lol. Kind of confused about the windows live id sign up, was it suppose to set a new email or just verify who you are?  ....would it expire like hotmail accounts do? 

btw, did you have any luck seting up usb in vbox?

---

### Post by miniyak on 2009-08-20
> yeah, yesterday was the last day to get the iso and a valid key. That could have been one of the biggest selling points of Windows 7 if they kept it up. The RC is good for nearly a year so they should have just let people keep trying it. But i have not done several millions in market research so what do i know

huh? mine is downloading right now...

---

### Post by Copernicus1234 on 2009-08-20
Its so typically Microsoft I couldnt help myself laughing out loud when trying this.

You have no other option than to use a download manager that is built as a ActiveX control, therefore only works on Windows, in Internet Exploder, to download this file. :lolflag:

I will get it from a torrent then. I got a key anyway, thats all I need.

Just doing this for 5 minutes reminds me strongly about all the things I hate with Microsoft.

---

### Post by miniyak on 2009-08-20
> You have no other option than to use a download manager that is built as a ActiveX control, therefore only works on Windows, in Internet Exploder, to download this file.

I just finished downloading it with firefox on ubuntu...

---

### Post by samalex on 2009-08-20
> **miniyak said:**
> I just finished downloading it with firefox on ubuntu...

They must've disabled it not long after you fired off your download because it was working just before I made my initial post.  

Weird --

Update: I just ran across this on PC World:
[http://www.pcworld.com/article/170512/windows_7_want_the_release_candidate_youre_too_late.html](http://www.pcworld.com/article/170512/windows_7_want_the_release_candidate_youre_too_late.html)

Sam

---

### Post by samalex on 2009-08-20
> **Copernicus1234 said:**
> Its so typically Microsoft I couldnt help myself laughing out loud when trying this.

You have no other option than to use a download manager that is built as a ActiveX control, therefore only works on Windows, in Internet Exploder, to download this file. :lolflag:

I will get it from a torrent then. I got a key anyway, thats all I need.

Just doing this for 5 minutes reminds me strongly about all the things I hate with Microsoft.

Actually I downloaded the ISO using Firefox on Ubuntu.  It used a JRE downloader that worked okay.  I also use dreamspark.com which is a MS site to download software for students, and it has the same download manager which also works on Firefox on Linux.  I've downloaded Visual Studio and SQL 2008 through it.

At any rate I'm not a fan of downloaders that 'help' you out.  Just give me the file...

Sam

---

### Post by miniyak on 2009-08-20
> At any rate I'm not a fan of downloaders that 'help' you out. Just give me the file...

For sure. Same goes for uploaders (im looking at you facebook!)

Its really not all that much of a complicated process to begin with

---

### Post by miniyak on 2009-08-25
hey sam, im still having a problem with audio through win7, could you detail what you did to get it to work? thanx in advance

---

### Post by miniyak on 2009-08-25
never mind i spoke too soon, Figured the initial updates in win7 would have taken care of it, but it turns out that there are other optional updates one can find in the windows update section of the control panel. The sound is kind of choppy though, oh well... good enough for me!

---

### Post by samalex on 2009-08-26
[QUOTE="miniyak"]never mind i spoke too soon, Figured the initial updates in win7 would have taken care of it, but it turns out that there are other optional updates one can find in the windows update section of the control panel. The sound is kind of choppy though, oh well... good enough for me![/QUOTE]

Other then installing Win 7 I haven't worked much with it since.  Most of the apps I use in Windows are setup under my Win XP image, and with Win 7 expiring in 6 or 7 months I don't want to invest too much time into it other then to play and see if I like it.

But yeah, sound was I think on the second or third round of updates :)  Silly Microsoft and it's need to reboot.  I figured they'd have fixed that by now.

Sam

---

### Post by Jose Catre-Vandis on 2009-08-26
Once you get to the "key" page (after you have entered your live id) if you backspace or press the back button, the page will reload and give you another key :)

---

### Post by samalex on 2009-08-26
[QUOTE="Jose Catre-Vandis"]Once you get to the "key" page (after you have entered your live id) if you backspace or press the back button, the page will reload and give you another key [/QUOTE]

Sounds like a bug, but I personally only need one key :)

Sam

---

