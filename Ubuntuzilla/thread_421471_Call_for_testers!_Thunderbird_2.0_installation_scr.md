---
title: "Call for testers! Thunderbird 2.0 installation script revision"
date: 2007-04-23
forum: Ubuntuzilla
---

### Post by nanotube on 2007-04-23
*** EDIT: this is no longer the "current" version. please get your script straight from the ubuntuzilla project site, here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
new versions will be posted for testing in separate threads, to keep things sane.
***

ok, new version to test. :)
please try the following combinations:
a profile in ~/.mozilla-thunderbird
a profile in ~/.thunderbird
a profile in both of those
a profile in neither of those
a profile in ~/.mozilla-thunderbird, and a link to it from ~/.thunderbird

the script should now be able to handle all of these possibilities.
new version of script is attached.

---

### Post by aysiu on 2007-04-24
I still haven't gotten around to testing this. I'll post back when I do.

Anyone else who can help test?

I can test the above situations in Feisty, but I can't account for every possible situation (older installations, scenarios we haven't foreseen).

---

### Post by nanotube on 2007-04-24
Note: I have amended the script to refer to our new website and forums for help. Check also if you like the wording, etc.

---

### Post by aysiu on 2007-04-24
All right, I tested the script, and found a glitch. If I have only a ~/.mozilla-thunderbird, I get this message: ```
A Thunderbird profile has been found at ~/.mozilla-thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.mozilla-thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: y

Backing up old thunderbird preferences

You seem to have two Thunderbird profiles, one in ~/.thunderbird and one in ~/.mozilla-thunderbird. Please choose among the following options. ( If you need more information, please see our FAQ on this issue here: http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Help_on_multiple_profiles_.5BThunderbird.5D ).
1. use ~/.thunderbird directory as your profile for the new installation.
2. use ~/.mozilla-thunderbird directory as your profile for the new installation (~/.thunderbird is moved out of the way, and a link to ~/.mozilla-thunderbird is created)
3. exit the script now, take your time and figure out which profile you want to use, and then try running this script again later when you are ready.
Enter the number for your choice [1/2/3] 
``` It looks as if the script made a link between ~/.mozilla-thunderbird and ~/.thunderbird and the detected a ~/.thunderbird and thought there were two profiles.

---

### Post by nanotube on 2007-04-24
ah, heh, sorry, my bad. i didn't realize that the directory check by default dereferences symlinks. fixed it up, attached is the new version.

---

### Post by aysiu on 2007-04-25
Okay. It works for ~/.mozilla-thunderbird alone.

When I run it again with a ~/.thunderbird symlinked to ~/.mozilla-thunderbird, it does exactly the same thing (act as if I had only a ~/.mozilla-thunderbird profile)... is that what it's supposed to do?

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> Okay. It works for ~/.mozilla-thunderbird alone.

When I run it again with a ~/.thunderbird symlinked to ~/.mozilla-thunderbird, it does exactly the same thing (act as if I had only a ~/.mozilla-thunderbird profile)... is that what it's supposed to do?

yes, because it knows that ~/.thunderbird is just a symlink, not a real directory.

---

### Post by aysiu on 2007-04-25
> **nanotube said:**
> yes, because it knows that ~/.thunderbird is just a symlink, not a real directory.
Cool. I'll test some of the other scenarios, then.

Or should I wait until you add in the install/remove ability?

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> Cool. I'll test some of the other scenarios, then.

Or should I wait until you add in the install/remove ability?

well, testing the profile scenarios is really separate from install/remove (since that part will not be modified). so might as well just go ahead and test those now, and then test install/remove later (because i'm going to sleep for the night :) ).

---

### Post by nanotube on 2007-04-25
ok, here's the latest version of the thunderbird script (with -remove and -install features). 
i have also changed localization fetching to use w3m rather than wget, since wget produced inconsistent results for some users, which ended up not giving them a list (just got help from a guy tracking this down over email). 

So, go ahead, give it some testing, and if it holds up, i will upload it over to the live site. :)

---

### Post by Mitlik on 2007-04-25
When I ran this script it fizzled on the gpg key the first time, and I ran again, because my system seems to fizzle on the first attempt with a new gpg key, then it worked fine. I believe I have two profiles(.thunderbird and .mozilla-thunderbird), but I don't know how to tell if one is "symlinked" (heck I had to go to your wiki to get how to run this to give you an idea of how little I know) I like it though, it beats having to fiddle around with a bunch of settings myself. I hope the feedback is useful 'cause I like this script.

Thanks!
Ben

---

### Post by nanotube on 2007-04-25
hey ben/mitlik :)
thanks for your feedback!

to figure out what you have in your profiles, please post the output of the following command (run from your home dir):
```
ls -ald .*thunderbird
```

if something is a link, it will start with "lrwxrwxrwx", and show where it links to with an arrow "->"

symlink = symbolic link, which is basically like a shortcut. see
```
man ln
```
for [a lot] more detail. ;)

but, if the script told you that you have two profiles, then neither is a link to the other one (because the script checks for that). you did not find this section of the wiki helpful in resolving your multiple profile issue?:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Help_on_multiple_profiles_.5BThunderbird.5D](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Help_on_multiple_profiles_.5BThunderbird.5D)

---

### Post by aysiu on 2007-04-25
nanotube, I'm going to do some extensive testing now.

Do you think, though, that we could change *aptitude* to *apt-get*? I recently remove *ubuntu-desktop*, and *aptitude* wants to uninstall (without confirmation) *xorg* and about fifteen other packages.

I'll post back the results on all the profile situations.

---

### Post by aysiu on 2007-04-25
> **nanotube said:**
> ok, here's the latest version of the thunderbird script (with -remove and -install features). 
i have also changed localization fetching to use w3m rather than wget, since wget produced inconsistent results for some users, which ended up not giving them a list (just got help from a guy tracking this down over email). 

So, go ahead, give it some testing, and if it holds up, i will upload it over to the live site. :)
Okay, I tested install and remove for these scenarios:

~/.mozilla-thunderbird
~/.thunderbird
~/.mozilla-thunderbird with symlink from ~/.thunderbird
Profiles in both ~/.mozilla-thunderbird and ~/.thunderbird
No profile whatsoever

Everything worked just fine (and I had replaced *aptitude* with *apt-get*).

I say take this version live.

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> nanotube, I'm going to do some extensive testing now.


excellent. :)


> Do you think, though, that we could change *aptitude* to *apt-get*? I recently remove *ubuntu-desktop*, and *aptitude* wants to uninstall (without confirmation) *xorg* and about fifteen other packages.


i'm sure that could be arranged. for the purposes of just making sure two packages are installed, there is really no reason to prefer one over the other - so if aptitude gets ornery, might as well apt-get.

> I'll post back the results on all the profile situations.

cool. looking forward to that.

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> Okay, I tested install and remove for these scenarios:

~/.mozilla-thunderbird
~/.thunderbird
~/.mozilla-thunderbird with symlink from ~/.thunderbird
Profiles in both ~/.mozilla-thunderbird and ~/.thunderbird
No profile whatsoever

Everything worked just fine (and I had replaced *aptitude* with *apt-get*).

I say take this version live.

cool. i will s/aptitude/apt-get/, and post it live.

---

### Post by Mitlik on 2007-04-26
Yeah, mine is symlinked, but Aysiu got back quicker than I did. Sorry for being slow.
Thanks again for the script.

Ben

---

### Post by nanotube on 2007-04-26
> **Mitlik said:**
> Yeah, mine is symlinked, but Aysiu got back quicker than I did. Sorry for being slow.
Thanks again for the script.

Ben

you're welcome, thanks for testing. :)

---

### Post by fwojciec on 2007-04-27
Thanks for the script nanotube - it worked perfectly on my computer (profile in ~/.mozilla-thunderbird).

---

### Post by shane2peru on 2007-04-27
> **nanotube said:**
> ok, new version to test. :)
please try the following combinations:
a profile in ~/.mozilla-thunderbird
a profile in ~/.thunderbird
a profile in both of those
a profile in neither of those
a profile in ~/.mozilla-thunderbird, and a link to it from ~/.thunderbird

the script should now be able to handle all of these possibilities.
new version of script is attached.

Is this the same script that is on the PyKeylogger page?  Is so I'm running it now.  And it seems to have hung at 78% download.  Don't know why, my internet is working fine.  Maybe server overload from the download place?  Not sure.  Here is my terminal output: ```
Downloading Thunderbird archive from the Mozilla site

--15:03:51--  http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz
           => `thunderbird-2.0.0.0.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz [following]
--15:03:53--  http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz
           => `thunderbird-2.0.0.0.tar.gz'
Resolving releases.mozilla.org... 130.239.18.158, 130.239.18.159, 64.50.236.214
Connecting to releases.mozilla.org|130.239.18.158|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,428,569 (11M) [application/x-gzip]

78% [=================================================>              ] 8,972,897     --.--K/s    ETA 04:41
```  It just stayed at 78% for about 3 minutes and I killed it.  Re running it now to see how it goes on try two.

Shane


**EDIT:**  Ok, after 4 minutes of waiting on attempt 2, it is still hung on 78%.  It started right at 78%, and stayed there for the 4 minutes.  I'm going to assume this is a server problem, I'm 100% sure it is not my internet problem since I have access to the web and am downloading via d4x.  (I set it to the lowest setting so it isn't the cause of the problem either, it isn't eating my bandwidth.)  :)  I will give it some time and give it a whirl again.  

Shane

**Edit2**  Ok, I ran it again, and figured I would just let it set there and think for a while.  However before running it, there were some new updates (from the update that it does) and so I installed them, in all honesty I ran them while the last one was just setting there doing nothing.  Running it again the 3rd time, it picked right up and started again.  Don't know for what reason.  Seems to be running fine.  Ok, hung up on the key thing, after the 5th run, worked fine.  I think there may need to be a little fine tuning that needs to be done.  Seems to work fine other than you have to run it 4 times to get it to work.  I can't attribute all of the problems to the script, but somehow I think it didn't allow for the update.  Thanks for the script though!  

Shane

---

### Post by nanotube on 2007-04-27
> **fwojciec said:**
> Thanks for the script nanotube - it worked perfectly on my computer (profile in ~/.mozilla-thunderbird).

great, thanks for your feedback. :)

---

### Post by nanotube on 2007-04-27
> **shane2peru said:**
> Is this the same script that is on the PyKeylogger page?  Is so I'm running it now.  And it seems to have hung at 78% download.  Don't know why, my internet is working fine.  Maybe server overload from the download place?  Not sure.  Here is my terminal output: ```
Downloading Thunderbird archive from the Mozilla site

--15:03:51--  http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz
           => `thunderbird-2.0.0.0.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz [following]
--15:03:53--  http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz
           => `thunderbird-2.0.0.0.tar.gz'
Resolving releases.mozilla.org... 130.239.18.158, 130.239.18.159, 64.50.236.214
Connecting to releases.mozilla.org|130.239.18.158|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,428,569 (11M) [application/x-gzip]

78% [=================================================>              ] 8,972,897     --.--K/s    ETA 04:41
```  It just stayed at 78% for about 3 minutes and I killed it.  Re running it now to see how it goes on try two.

Shane


**EDIT:**  Ok, after 4 minutes of waiting on attempt 2, it is still hung on 78%.  It started right at 78%, and stayed there for the 4 minutes.  I'm going to assume this is a server problem, I'm 100% sure it is not my internet problem since I have access to the web and am downloading via d4x.  (I set it to the lowest setting so it isn't the cause of the problem either, it isn't eating my bandwidth.)  :)  I will give it some time and give it a whirl again.  

Shane

**Edit2**  Ok, I ran it again, and figured I would just let it set there and think for a while.  However before running it, there were some new updates (from the update that it does) and so I installed them, in all honesty I ran them while the last one was just setting there doing nothing.  Running it again the 3rd time, it picked right up and started again.  Don't know for what reason.  Seems to be running fine.  Ok, hung up on the key thing, after the 5th run, worked fine.  I think there may need to be a little fine tuning that needs to be done.  Seems to work fine other than you have to run it 4 times to get it to work.  I can't attribute all of the problems to the script, but somehow I think it didn't allow for the update.  Thanks for the script though!  

Shane

thanks for your testing and feedback.
it looks like the default timeout for wget is 15 minutes, which is probably a bit too long. in the next version of the script i will set the timeout to 1 minute, after which time it will automatically retry.

i am also working on a more robust gpg key retrieval, so that should hopefully reduce gpg key verification problems.

but, actually, regarding your very first question - i think the script posted here may be a couple of minor revisions behind the script posted on pykeylogger at this point. so, i will edit the first post to make it clear that that is no longer the "current" version to test. :)

thanks again for your persistence and reporting your results!

---

### Post by shane2peru on 2007-04-27
> **nanotube said:**
> thanks for your testing and feedback.
it looks like the default timeout for wget is 15 minutes, which is probably a bit too long. in the next version of the script i will set the timeout to 1 minute, after which time it will automatically retry.

i am also working on a more robust gpg key retrieval, so that should hopefully reduce gpg key verification problems.

but, actually, regarding your very first question - i think the script posted here may be a couple of minor revisions behind the script posted on pykeylogger at this point. so, i will edit the first post to make it clear that that is no longer the "current" version to test. :)

thanks again for your persistence and reporting your results!

Glad to be of help.  To make it clear, I did get the script from the pykeylogger page, and not this forum.  You may want to replace your link with a link directly to the same one as on the pykeylogger page.  Just a thought, that way you don't have to upkeep two links.  :)    Thanks again for the script, I'm going back to Thunderbird after using Evolution for several months.  T-Bird, is just way better of an email client.  Lacking on PIM qualities but and awesome email client.  

Shane

---

### Post by Jaymac on 2007-04-28
Could someone tell me how to reverse the the installation and go back to TB 1.5?  What should I change the symlinks to?

It's a shame, but Thunderbird 2 freezes for me any time I receive a new email, and it also likes to download the same email 5 or 6 times off the server, so it isn't much use to me.

---

### Post by Soarer on 2007-04-28
Hi,

I just downloaded the script from the main site and, with the help of the excellent explanations, ran it. It worked perfectly first time, keys & all.

Well done & thanks very much.

---

### Post by Mitlik on 2007-04-28
> **Jaymac said:**
> Could someone tell me how to reverse the the installation and go back to TB 1.5?

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) has the instructions, I believe it says just to run the script with -remove.

@nanotube did you want people to test the remove portion as well?

---

### Post by Jaymac on 2007-04-28
> **Mitlik said:**
> [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) has the instructions, I believe it says just to run the script with -remove.

@nanotube did you want people to test the remove portion as well?

That does nothing.  It ignores the remove flag...

[edit] I moved it to the Desktop and it worked.  weird....

---

### Post by shane2peru on 2007-04-28
> **Jaymac said:**
> That does nothing.  It ignores the remove flag...

[edit] I moved it to the Desktop and it worked.  weird....

That is a good point, because when I ran mine, I didn't run it from the desktop either.  (for the install).  I ran it from another folder.  I don't really do work on my desktop.  :)

Shane

---

### Post by nanotube on 2007-04-28
> **Mitlik said:**
> [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) has the instructions, I believe it says just to run the script with -remove.

@nanotube did you want people to test the remove portion as well?

well, yea, all functionality should be tested. :) aysiu did report than -remove worked, but if more people test, there's more chance that bugs will be caught.

---

### Post by nanotube on 2007-04-28
> **Jaymac said:**
> That does nothing.  It ignores the remove flag...

[edit] I moved it to the Desktop and it worked.  weird....

maybe you mistyped the command when you tried it the first time? the script doesn't really do any sort of checking to see if it's on the desktop or not, so there's no way that should matter...

---

### Post by nanotube on 2007-04-28
> **shane2peru said:**
> That is a good point, because when I ran mine, I didn't run it from the desktop either.  (for the install).  I ran it from another folder.  I don't really do work on my desktop.  :)

Shane

well, i just have the instructions say to put it on the desktop because i have to have some consistent place where people can put it and find it later. if you are comfortable running shell scripts, then you don't have to care where you put it. but for people who are going to be copy-pasting the command from the ubuntuzilla website, it comes in handy. :)

---

### Post by shane2peru on 2007-04-30
> **nanotube said:**
> well, i just have the instructions say to put it on the desktop because i have to have some consistent place where people can put it and find it later. if you are comfortable running shell scripts, then you don't have to care where you put it. but for people who are going to be copy-pasting the command from the ubuntuzilla website, it comes in handy. :)

Right, understood, sometimes the script may or could I guess in a remote case be location specific.  I figured it was just for the easiness of running the commands at a copy paste level.  Thanks again.

Shane

---

