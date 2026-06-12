---
title: "iSky installs iTunes, Internet Explorer and Skype - and they run perfectly"
date: 2009-08-23
forum: Wine
---

### Post by Random Squires on 2009-08-23
[CENTER][FONT=Times New Roman][SIZE=3][U][B]iTUNES, INTERNET EXPLORER and SKYPE INSTALL EASILY AND WORK SATISFACTORILY*
[/B][/U] [/SIZE][/FONT][/CENTER]

[RIGHT]                                                [SIZE=1]*Skype works perfectly, IE works fine, iTunes works well but not with iPhone or iTouch.
[/SIZE][/RIGHT]
 
Hello all,
I'd like to announce a script I wrote called iSky. It is an interactive terminal-based installer for Skype, iTunes and Internet Explorer for users running Ubuntu / Kubuntu 9.04 Jaunty Jackalope. It is designed for users with minimal expertise in Linux and Wine.

Put simply: By selecting "Install Dependencies", iSky automatically adds the WineHQ repos to the user's sources list.
                 Then, iSky installs the latest versions of wine and cabextract.

Users can then choose to install Skype, iTunes, or Internet Explorer. 

The Skype option is merely a useful script which fetches and installs the package from the website, and saves the user from having to use nasty non-free repos, many of which hold out of date versions anyway.

The iTunes option fetches and installs iTunes 8.0 (under Wine). I have tested this, and it works like a charm. N.B: I do not own an ipod, but iTunes installs and runs perfectly.

The Internet Explorer option fetches the latest release of [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), extracts the tarball and runs the installer that is a part of that project.



iSky is simply a shell script, so all that is needed is to download it from the site: [https://sourceforge.net/projects/isky/](https://sourceforge.net/projects/isky/)
Copy it into the /usr/bin directory and then make it executable and run it. Contact me if you need baby-steps instructions as to how you do this.

So, please download it, let me know if you find it useful.
Contact me with questions, suggestions, thanks, rants etc etc
oh and yes I know Internet Explorer is a piece of sh1t, but some people are forced to use it for online banking etc, and if you ignore them they will go straight back to windows.

Thanks
Eddie

---

### Post by SuperSonic4 on 2009-08-23
iTunes is more a piece of sh1t than IE but your point is valid

---

### Post by hikaricore on 2009-08-23
I don't see the point in this.
You can install these in WINE easily and there are already other tools for this as well.

---

### Post by Random Squires on 2009-08-23
> **hikaricore said:**
> I don't see the point in this.
You can install these in WINE easily and there are already other tools for this as well.
Perhaps I didn't make it clear: this is intended (eventually - it's by no means a finished product) to be for  people with little or no experience of Linux or Wine.

For instance, to install iTunes, the user would have to first try and find out if the official Ubuntu Wine repo version could do the job. Then they would have to trawl through hundreds of contradictory and misleading webpages and forums in order to find out a) if it is even possible, and b) which version of itunes they should download (The lates version from Apple DOES NOT work, and is not used here). Then they'd have to find that version to download somewhere. And if something did go wrong, they wouldn't have the expertise or the patience to fix it. They'd just go back to windows.

As for internet explorer, I have been using Linux for a while now, and it was a long time before I found out about the ies4linux project (which is separate from wine.) Heaven knows how likely it is that a newbie could find it.

Hope that clears things up if there was a misunderstanding - if I've failed to grasp your point then I'd be interested to hear more.

---

### Post by Random Squires on 2009-08-28
iSky is now at version 1.50, which solved a number of issues; the "Install Dependencies" option to install Wine has now been removed and incorporated into the script so that this is done automatically before the installation of either IE or iTunes. The Kubuntu version is now on a par with the standard version.

---

### Post by aysiu on 2009-08-28
iTunes doesn't "run perfectly" until it can sync with an iPod Touch or iPhone.

Almost all of the other functions of iTunes can be done in a native Linux program.

---

### Post by aysiu on 2009-08-28
iTunes doesn't "run perfectly" until it can sync with an iPod Touch or iPhone.

Almost all of the other functions of iTunes can be done in a native Linux program.

---

### Post by howefield on 2009-08-28
Wouldn't your script download the "wrong" version of skype for many people ?

---

### Post by Random Squires on 2009-08-28
_**To aysiu:**_ okay I admit it might have been a little misleading. What I meant was that with my script iTunes is downloaded, installed and runs satisfactorily - as opposed to the average experience of a new user where iTunes crashes either on install or startup due to a wrong version of WINE or of iTunes. If you're concerned I encourage people to bypass native linux apps, then I have a suggestion: as you may have noticed, the script currently provides an option "no thanks". When you select this, you are given info as to why the software concerned is "bad" and which linux apps fulfil the same purpose. Do you think I should print this on screen before the user has the choice to install anything?

_**To howefield:**_ Currently the download page informs people that the script is for Ubuntu / Kubuntu Jaunty 9.04. This is because the WINE repos added for IE and iTunes would DEFINITELY be wrong for other Ubuntu releases. However, I should think most users wouldn't have a problem with skype. In actual fact, there has never been a Skype package for Jaunty, the script downloads the Intrepid version and this works fine. It might be that this package will not install on Hardy, but I really don't know; sometimes Intrepid packages seem to work alright on fully updated Hardy. In any case, versions for previous Ubuntu releases are in the works, primarily because the WINE repos that are added would need to be changed. I know Skype provide a package for Hardy, so this would be included then.

---

### Post by aysiu on 2009-08-28
> **Random Squires said:**
> _**To aysiu:**_ okay I admit it might have been a little misleading. What I meant was that with my script iTunes is downloaded, installed and runs satisfactorily - as opposed to the average experience of a new user where iTunes crashes either on install or startup due to a wrong version of WINE or of iTunes. If you're concerned I encourage people to bypass native linux apps, then I have a suggestion: as you may have noticed, the script currently provides an option "no thanks". When you select this, you are given info as to why the software concerned is "bad" and which linux apps fulfil the same purpose. Do you think I should print this on screen before the user has the choice to install anything? Thanks for your reply.

No, I wasn't concerned about bypassing native Linux apps.

My concern is unrealistic expectations.

It certainly is nice, for those who have realistic expectations of what iTunes in Wine can and cannot do, to have iTunes seamlessly install in Wine without erroring out.

But the term *run[s] perfectly* can be misleading, as it sounds as if all the functionality in iTunes will be there if you install it in Wine using this script.

And without all the functionality of iTunes (particularly compatibility with iPods and iPhones above what native Linux apps can already achieve), I'm not sure what the worth of it is.

---

### Post by Random Squires on 2009-08-28
Okay thanks, I edited the post; if there's any way to edit the thread title in a similar way, that would be useful....and yes, users might get unrealistic expectations, I can see that....it's just an issue that many users would be very resistant even to using an alternative ipod/media library programme on windows. So to have a host of complete unknowns on Linux is in practice too confusing....

---

### Post by howefield on 2009-08-28
> **Random Squires said:**
> ..Currently the download page informs people that the script is for Ubuntu / Kubuntu Jaunty 9.04.... (snippety snip the rest)

I'm referring to whether or not your script detects what the the host system is running (32 or 64 bit).

---

### Post by Random Squires on 2009-08-28
Ah, my mistake :redface: umm, no it will not detect it automatically, so yes I suppose for 64-bit users the current script would install the 'wrong' package, although this would be easy to correct, just a matter of changing a url......my understanding of 64-bit computing is almost non-existent, can they not run 32-bit programmes as well?

---

### Post by Random Squires on 2009-08-28
I just added 64-bit versions, should work.

---

### Post by howefield on 2009-08-28
> **Random Squires said:**
> ...can they not run 32-bit programmes as well?

Yes, 32 bit programmes will most likely run well enough.

I am really saying that someone running a 64 bit operating system would most likely want 64 bit applications, where possible.

Or at the least, be clear on what they are installing.

---

### Post by Random Squires on 2009-08-28
Ah okay then, yeah you're right, if I ran 64-bit I'd first) want to understand what it was :) 
and second) know what I'm installing, 
So yeah it was just a case of altering it to fetch the 64-bit version from the website, which I've done, so now anyone wanting a 64-bit version can just go to [https://sourceforge.net/projects/isky/](https://sourceforge.net/projects/isky/), click "show all files, go to "64-bit" and download from there.

---

### Post by seamles on 2009-09-17
How does this work with IE? I have to watch videos online through school and the only way to double speed it is through IE. What version of IE does it install? Is it compatible as a windows with all the sites?

---

### Post by seamles on 2009-09-17
I need baby steps to install...

---

### Post by Chronon on 2009-09-17
> **Random Squires said:**
> if there's any way to edit the thread title in a similar way, that would be useful..

You can edit the topic title if you use use the advanced editing options.

---

### Post by mrebanza on 2009-11-30
since apple is now unix based wouldn't an apple version of the program be easily ported????


:popcorn:

---

### Post by Papajerry on 2009-11-30
> **seamles said:**
> I need baby steps to install...

Me Too !!!

---

### Post by eamonhonda on 2010-02-01
any update on how to install this

---

### Post by jfa2214 on 2010-03-13
ISky does not appear to work with ubuntu iso 64 9.10. I ran it from usr/bin and it ran to the question Y/n. I type capital Y and nothing occured. I ran iSky again and tried the lower case y still nothing occurred. Sounds like an interesting package. Sure would like to be able to get on line with the itunes store.

---

