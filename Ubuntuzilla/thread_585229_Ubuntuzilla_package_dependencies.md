---
title: "Ubuntuzilla package dependencies"
date: 2007-10-21
forum: Ubuntuzilla
---

### Post by bbukh on 2007-10-21
I have Kubuntu 6.0.6 (Dapper) which runs Firefox 1.5, and I am happy with both of them... except that now I would like to use a firefox plugin "Zotero" which requires firefox version at least 2.0

I have downloaded the 16kb .deb file for ubuntuzilla. After I ran
"sudo dpkg ubuntuzilla-4.4.3-0ubuntu1-i386.deb"
I was told that ubuntuzilla depends on "gdebi" and "libnotify". Reading about what "gdebi" and "libnotify" do I think they are really unnecessary for the simple task of installing firefox.  

I do not want to run yet another daemon on my system that I have no use for, nor I want to install megabytes upon megabytes of Gnome (recall I run Kubuntu). So, my question is how do I use ubuntuzilla script without all the unnecessary fluff? Or I rather have to go through the manual installation?

Thanks for any help.

Boris

---

### Post by nanotube on 2007-10-22
> **bbukh said:**
> I have Kubuntu 6.0.6 (Dapper) which runs Firefox 1.5, and I am happy with both of them... except that now I would like to use a firefox plugin "Zotero" which requires firefox version at least 2.0

I have downloaded the 16kb .deb file for ubuntuzilla. After I ran
"sudo dpkg ubuntuzilla-4.4.3-0ubuntu1-i386.deb"
I was told that ubuntuzilla depends on "gdebi" and "libnotify". Reading about what "gdebi" and "libnotify" do I think they are really unnecessary for the simple task of installing firefox.  

I do not want to run yet another daemon on my system that I have no use for, nor I want to install megabytes upon megabytes of Gnome (recall I run Kubuntu). So, my question is how do I use ubuntuzilla script without all the unnecessary fluff? Or I rather have to go through the manual installation?

Thanks for any help.

Boris

hey
the solution is simple:
install ubuntuzilla and these dependencies
use ubuntuzilla to install firefox
uninstall ubuntuzilla and these dependencies

:)

---

### Post by bbukh on 2007-10-22
I appreciate your sense of humor, but I prefer manual installation of firefox to installing and uninstalling gnome.

Thinking about it, I think that it would be much funnier to suggest removing kubuntu 6.0.6, and installing ubuntu 7.10 which comes with both gnome and firefox 2.0.0.6

Boris

---

### Post by nanotube on 2007-10-22
> **bbukh said:**
> I appreciate your sense of humor, but I prefer manual installation of firefox to installing and uninstalling gnome.

Thinking about it, I think that it would be much funnier to suggest removing kubuntu 6.0.6, and installing ubuntu 7.10 which comes with both gnome and firefox 2.0.0.6

Boris

are you saying that the entirety of gnome really tries to get installed because of these dependencies? i'm talking just about two very small packages, gdebi, and libnotify...

these two are needed for ubuntuzilla self-updates, and for mozilla update notifications, respectively, by the way.

if it is the case that the whole gnome gets stuffed down the pipe, then you can just extract the .deb as a zip file, and take ubuntuzilla.py from there, and run the script from any location. that way you can bypass the install process, and thus the dependencies.

---

### Post by bbukh on 2007-10-22
Thank for you for a helpful response. I did not know that .deb file is just a .zip file, it helps.

gdebi depends on gksu which depends on bunch of gnome stuff. Whether it is the *whole* gnome or not the *whole* gnome, I know not.

Why not make ubuntuzilla recommend these packages instead of depending on them? They are clearly not central to the function that ubuntuzilla performs. Also, in place of gdebi one can use dpkg or aptitude which are essentially dependency-free package. Or better yet use whatever installed on the system.

Again, thanks for helpful information.

Boris

---

### Post by nanotube on 2007-10-22
> **bbukh said:**
> Thank for you for a helpful response. I did not know that .deb file is just a .zip file, it helps.

gdebi depends on gksu which depends on bunch of gnome stuff. Whether it is the *whole* gnome or not the *whole* gnome, I know not.


ah, i see, i didn't realize there would be so much dependency pull-in for kde users. gnome users already /have/ gdebi by default. it doesn't really matter whether it's the whole gnome or not - you are right that it does seem like too much stuff :)

> 
Why not make ubuntuzilla recommend these packages instead of depending on them? They are clearly not central to the function that ubuntuzilla performs. Also, in place of gdebi one can use dpkg or aptitude which are essentially dependency-free package. Or better yet use whatever installed on the system.

Again, thanks for helpful information.

Boris

i don't think i can just make it a "recommend" package, because gdebi is used for self-updates - so if the user fails to install it, self updates will fail. aptitude cannot install out-of-repo .debs, and dpkg doesn't automatically install dependencies... i'll think about how to play it. is there a kde package installer like gdebi - works for locally downloaded .debs, and automatically pulls dependencies? if there is, i can try using it for kde users...

also, what about libnotify-bin by itself - does that also push too many dependencies on you, or is that one ok?

---

### Post by bbukh on 2007-10-22
> **nanotube said:**
> 
i don't think i can just make it a "recommend" package, because gdebi is used for self-updates...

Are you saying that ubuntuzilla adds a cron job that periodically downloads new versions of ubuntuzilla along with all the dependencies without user's consent?!  That does not sound nice at all.

> **nanotube said:**
> 
also, what about libnotify-bin by itself - does that also push too many dependencies on you, or is that one ok?
Just a  couple of megs in size, it is certainly much less than gnome. However, I very much dislike the idea of running another daemon, which is a potential security risk.

My point is the following: the ubuntuzilla's task is to update firefox. It should not do anything else unless user specifically asks it for doing something else. That means that self-updates, and notifications should be optional features, and not forced upon the user along with megabytes of dependencies. Possibly, during a configuration of .deb package the user should be asked whether he wants these features on or not.

Boris

---

### Post by nanotube on 2007-10-23
> **bbukh said:**
> Are you saying that ubuntuzilla adds a cron job that periodically downloads new versions of ubuntuzilla along with all the dependencies without user's consent?!  That does not sound nice at all.


well, it's not "without the user's consent", since that is a feature explicitly listed in the manual and the website. the reason it's there is as follows. 

one of the key features of ubuntuzilla is automatic notification of new ff/tb/sm updates. this info gets pulled by parsing the mozilla website. if mozilla changes its website layout at any point, this feature will be broken, and so a user relying on it to get timely update notifications will be disappointed. thus, the automatic ubuntuzilla update was born - if mozilla changes website, i push out a new ubuntuzilla version with a fix, which gets updated automatically, and so update checking works again, without the user having to worry about it.

but certainly, there's nothing that prevents a user from disabling the cron job (or even uninstalling ubuntuzilla completely). however, theoretically you are right - the self-updates should be opt-in, rather than opt-out. (see below for more on this)

> My point is the following: the ubuntuzilla's task is to update firefox. It should not do anything else unless user specifically asks it for doing something else. That means that self-updates, and notifications should be optional features, and not forced upon the user along with megabytes of dependencies. Possibly, during a configuration of .deb package the user should be asked whether he wants these features on or not.

notifications are already an optional feature - user has to say "yes" to enable it. you are right, that self-updates should also be user-enabled... but i just don't know how to implement install-time configuration for .debs (i just managed to figure out enough about debs to put together a simple one for ubuntuzilla). would you by any chance be up for helping with this?

thanks a lot for all your feedback! :)

---

### Post by spayneuter on 2007-11-19
I'm obviously less advanced than bbukh because I'd be happy to install the [COLOR="Red"]libnotify-bin[/COLOR] dependency if I had a clue how to do it.

So let me back up, because, silly me, I typed _exactly_ what the instructions...instructed:
[INDENT]sudo dpkg -i /path/to/ubuntuzilla*.deb[/INDENT]
instead of the appropriate path because I can't even figure out how to determine the path and also figured the "*" would be recognized as a wildcard and the appropriate name would be inserted automatically.

I need more basic instruction than even the sourceforge is giving, apparently.  I did see that I have the appropriate package installer, and the error stating that I didn't have the necessary libnotify-bin dependency stopped me cold.

Help this humble non-tech simpleton?:confused:

---

### Post by nanotube on 2007-11-20
> **spayneuter said:**
> I'm obviously less advanced than bbukh because I'd be happy to install the [COLOR="Red"]libnotify-bin[/COLOR] dependency if I had a clue how to do it.


ok, there are two ways. you could either do
```
sudo gdebi /path/to/ubuntuzilla.deb
```

or

```
sudo dpkg -i /path/to/ubuntuzilla*.deb
sudo apt-get install -f
```
(note that this is two commands - first run dpkg (as you have), then run aptgetinstall -f (which will fix dependencies for you). 

let me know how it goes. :)

---

### Post by spayneuter on 2007-11-20
Thank you.  

Last night I explored your website (listed on your profile) and googled "libnotify-bin".  Eventually I found a download, which I tried to download and install (which did nothing).  Unfortunately, I'm incredibly sleep-deprived and forgot what I did and to document what I did, so all I know is that I'm still stuck.

I tried in the order you listed, then backward (since only the last command worked).  Here's the cut-n-paste of that:

[INDENT]spayneuter@spayneuter-desktop:~$ sudo gdebi /path/to/ubuntuzilla.deb
Password:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /path/to/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$ sudo dpkg -i /path/to/ubuntuzilla*.deb
dpkg: error processing /path/to/ubuntuzilla*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/ubuntuzilla*.deb
spayneuter@spayneuter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spayneuter@spayneuter-desktop:~$ sudo dpkg -i /path/to/ubuntuzilla*.deb
dpkg: error processing /path/to/ubuntuzilla*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/ubuntuzilla*.deb
spayneuter@spayneuter-desktop:~$ sudo gdebi /path/to/ubuntuzilla.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /path/to/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$
[/INDENT]

Ugh!

I figure you probably intended /path/to to indicate where I should fill in the appropriate path to(?); however, I really am that new at this that I can't figure it out.  I'm tempted to type usr/desktop/ubuntuzilla*.deb because it is saved to the desktop and it seems all is under usr/

I'm not hopeless; just a sincere novice.

---

### Post by spayneuter on 2007-11-20
So I did try replacing path/to with usr/desktop and got the same error:

[INDENT]spayneuter@spayneuter-desktop:~$ sudo gdebi usr/desktop/ubuntuzilla
Password:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: usr/desktop/ubuntuzilla
[/INDENT]

How do I find the path/to?  I can't seem to locate any type of directory that shows the path in this format.

I will continue to surf and read about the terminal/comand line (after I get some sleep).  Meanwhile, hopefully you can see where I'm tripping up and point me in the right direction (assuming the problem is with my inexperience and not with the actual software or configuration...

[IMG]http://i133.photobucket.com/albums/q45/SpayNeuter/melting.png[/IMG]

---

### Post by nanotube on 2007-11-21
ah, sorry i didn't realize that it was the "path/to" that was giving you trouble. well, the /path/to means the path to where you downloaded the ubuntuzilla.deb.

if it is e.g., your desktop, then it would be
/home/yourusername/Desktop/ubuntuzilla*.deb

you might have an easier time just finding ubuntuzilla in your gui file browser, and doubleclicking on the .deb - this will start the graphical installer.

also, libnotify-bin is is the official repositories, no need to scour the web for it - open up the synaptic package manager (system -> administration -> synaptic package manager), and search for "libnotify" and it will pop up in the search results. 

let me know if you succeed ! :)

---

### Post by spayneuter on 2007-11-22
YOU RULE!

Success!

After I installed with your last set of instructions, I was able to go back to your original ubuntuzilla project to "Where did it go?" and follow along from there.

I'm writing this using the newest version of Firefox...WooHoo!!!

Thank you!

---

### Post by nanotube on 2007-11-22
> **spayneuter said:**
> 
I'm writing this using the newest version of Firefox...WooHoo!!!

Thank you!

great! enjoy :)

---

### Post by spayneuter on 2007-12-25
Long story skipped, we've had to install ubuntu from scratch about 4 times now (fiddling with Windows, crashing, losing everything, starting over).  Each time, I've had to return to this forum and go through our conversation to get the ubuntuzilla to work.  Each time, I've had a different problem using it; however, I've been able to figure it out.

This time, I'm completely stuck.  Here's what I get in terminal:

[COLOR="DarkRed"]spayneuter@spayneuter-desktop:~$ sudo dpkg -i /home/spayneuter/desktop/ubuntuzilla*.deb
dpkg: error processing /home/spayneuter/desktop/ubuntuzilla*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/spayneuter/desktop/ubuntuzilla*.deb
spayneuter@spayneuter-desktop:~$ sudo gdebi /home/spayneuter/desktop/ubuntuzilla.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /home/spayneuter/desktop/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spayneuter@spayneuter-desktop:~$ sudo dpkg -i /home/spayneuter/desktop/ubuntuzilla.deb
dpkg: error processing /home/spayneuter/desktop/ubuntuzilla.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/spayneuter/desktop/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spayneuter@spayneuter-desktop:~$ sudo dpkg sudo dpkg -i /home/spayneuter/desktop/ubuntuzilla*.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
spayneuter@spayneuter-desktop:~$ sudo gdebi /home/spayneuter/desktop/ubuntuzilla.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /home/spayneuter/desktop/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$[/COLOR]



I've spent hours and hours getting to this point.  Before I understood that the ...-f fixes the library dependencies, I did try to download library parts which the warnings said were needed.  I'm thinking that may be the problem; however, I can't even figure out how to find those and remove them, as going to the downloads and choosing to "remove" them doesn't.

?

---

### Post by spayneuter on 2007-12-26
After getting some sleep, I tried again.  I got a message basically that it wanted to uninstall ubuntizilla and asked if I wanted to proceed, and I said Y.  It said it uninstalled ubuntuzilla, but it was still on the desktop and when I double-clicked on it, got the same (needs libnotify-bin) message.

I've tried again and have a different problem.  It seems when I use terminal, it doesn't recognize the path to ubuntuzilla.deb, saying it isn't there.  When I double-click on it on the desktop (because it is there), it says it needs libnotify-bin.  I even went to Synaptic Package Manager in search of libnotify and found libnotify1 and libnotify-dev.  I marked and applied to reinstall libnotify1 and marked and applied to install libnotify-deb.  I've done everything a dozen times with similar results.


> spayneuter@spayneuter-desktop:~$ sudo gdebi /home/spayneuter/desktop/ubuntuzilla.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /home/spayneuter/desktop/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$ sudo gdebi /home/spayneuter/desktop/ubuntuzilla.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: /home/spayneuter/desktop/ubuntuzilla.deb
spayneuter@spayneuter-desktop:~$ sudo dpkg -i /home/spayneuter/desktop/ubuntuzilla*.deb
dpkg: error processing /home/spayneuter/desktop/ubuntuzilla*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/spayneuter/desktop/ubuntuzilla*.deb
spayneuter@spayneuter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by spayneuter on 2007-12-26
Another long story short, I apparently somehow had managed to screw up my libnotify-bin.  I found a Linux apps link where I was able to download a working version and install it, then I was able to follow your instructions again and get ubuntuzilla installed.  Once I did that, all I needed to do (though it took me a while to figure it out) was go back to the original ubuntuzilla instructions and proceed with the next step after installation.

I'm really not thick; I'm just not familiar enough with ubuntu/Linux/etc. to be fluent or comfortable, so everything seems much harder and more confusing than it should.

I'm on the updated Firefox version again.

---

### Post by nanotube on 2008-01-08
hey, i'm glad you solved the problem :)
i was out of the country for a couple of weeks, so i'm sorry i couldn't help you troubleshoot. good work :)

---

