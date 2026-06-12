---
title: "What is the real reason that Google Earth won't install in Ubuntu 13.10 anyway?"
date: 2013-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Jim_Granite on 2013-12-28
Why would Canonical kill Google Earth on purpose? It makes no sense.

I had a devil of a time installing Google Earth when I first installed it into Ubuntu 13.10 (64 bit); and now, a few months later, it just crashes upon execution (and I can't re-install it properly).
Googling, I find this is a well known long-standing problem, e.g., this thread shows the same symptoms that I have:
- [Google Earth won't start - 13.10 edition         ]("http://ubuntuforums.org/showthread.php?t=2187353")

Worse, I find a systemic problem listed in this Softpedia article:
- [Say Goodbye to Google Earth on Ubuntu 13.10]("http://news.softpedia.com/news/Say-Goodbye-to-Google-Earth-on-Ubuntu-13-10-396451.shtml")

That article says the problem is Canonical purposefully deprecated a certain library (ia32-libs) which Google Earth needs in order to run.
But, why would Canonical essentially disable Google Earth, on purpose?

It wouldn't right? So there must be a reason that the ia32-libs are deprecated. Right?
So, I'm confused. What's going on, in plain words anyway? 
Is this a lesser-of-two-evils problems, or a competitive attack, or just a mistake, or what?

---

### Post by Bucky Ball on 2013-12-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by SuperFreak on 2013-12-28
I cannot help you with your installation problems other than to say I am running 13.10 64 bit on my laptop and was able to install Google Earth with instructions I found online. I just used it half an hour ago to view a street address at street level

edit: This might p;oint you in the right direction[http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438]("http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438")

---

### Post by Jim_Granite on 2013-12-28
> **SuperFreak said:**
>  This might p;oint you in the right direction[http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438](http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438)

I've been trying web-solutions for an hour (including trying the 32-bit Google-Earth Deb file); and all are failing miserably. 
There is not a single howto on the net that actually works. You have to know something that is not in the instructions to make it work.

This sequence of cryptic steps came the closest to working, but still failed miserably:
[http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/](http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/)

Here's a history log of the commands that I ran, but, there were far too many dependencies for me to resolve:
$ wget [https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb](https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb)
$ sudo dpkg -i googleearth-package_1.1.0_all.deb 
$ sudo apt-get install -f
$ make-googleearth-package
$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb 
$ sudo apt-get install libfreeimage3 lsb-core libcurl3 libsm6 libfontconfig1 libxt6 libxrender1 libxext6 libgl1-mesa-glx libgl1-mesa-dri
(this fails, due to numerous dependencies)
$ sudo apt-get install -f
$ which google-earth
=> ./google-earth
$ google-earth
=> ./googleearth-bin: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

---

### Post by monkeybrain20122 on 2013-12-28
It is not that Canonical tries to kill ge, but bad packaging on goolge's part. The rpm doesn't install on Fedora either but for a different reason. The work around is to take the deb (or rpm) file apart and rebuild it.

Down load the ge 64 bit deb, say you put it on the Desktop. Then right click > extract here and it will create a folder called google-earth-stable_current_amd64,
then delete the original .deb. Now open the extracted folder, navigate to the sub-folder "DEBIAN", open the control file, remove the dependency ia32-lib and save the change (you may also want to delete the hidden file ~control)

Now rebuild the .deb with the command (assuming your google-earth folder is on your Desktop)
```
dpkg -b Desktop/google-earth-stable_current_amd64

```

Then it will produce a new .deb and you can just right click to install it with gdebi or Software Centre.

To run ge you need additional dependencies
```

sudo apt-get install libc6:i386 lsb-core

```

---

### Post by SuperFreak on 2013-12-28
> **Jim_Granite said:**
> I've been trying web-solutions for an hour (including trying the 32-bit Google-Earth Deb file); and all are failing miserably. 
There is not a single howto on the net that actually works. You have to know something that is not in the instructions to make it work.

This sequence of cryptic steps came the closest to working, but still failed miserably:
[http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/](http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/)

Here's a history log of the commands that I ran, but, there were far too many dependencies for me to resolve:
$ wget [https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb](https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb)
$ sudo dpkg -i googleearth-package_1.1.0_all.deb 
$ sudo apt-get install -f
$ make-googleearth-package
$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb 
$ sudo apt-get install libfreeimage3 lsb-core libcurl3 libsm6 libfontconfig1 libxt6 libxrender1 libxext6 libgl1-mesa-glx libgl1-mesa-dri
(this fails, due to numerous dependencies)
$ sudo apt-get install -f
$ which google-earth
=> ./google-earth
$ google-earth
=> ./googleearth-bin: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

There is a comment in that link that should help you(bottom of article). Quoting it says:
> 
noop says:	
November 27, 2013 at 4:55 am	

It works perfect,after a slight change. THX Geekster!
This is how I did it:
1: $ wget https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.de^C
2: $ sudo dpkg -i googleearth-package_1.1.0_all.deb
3: $ sudo apt-get install -f
4: $ make-googleearth-package
!!so far so good, but then…
5: $ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb
then again like above…
6: $ sudo apt-get install -f
Reply	


---

### Post by pqwoerituytrueiwoq on 2013-12-28
google earth 7 wont run on 12.10 even with the 32bit libaries
and google earth 6 has a broken search feature (obsolete search url)
i don't have any 32bit installs, i dont use anything 32bit, if i cant get 64bit versions don't use it, nothing should be 32bit anymore, we have had 64bit cpus for a decade or so now

---

### Post by monkeybrain20122 on 2013-12-29
GE 7 64-bit works on 13.10, just follow my instructions above.

---

### Post by Newbunto on 2013-12-29
> **monkeybrain20122 said:**
> GE 7 64-bit works on 13.10, just follow my instructions above.

And yet it doesn't.

I've hacked the deb file to get it even to install. Successfully installed it.

When I run Google Earth it just bombs (with the same messages that everyone who has a problem gets, if run from shell). Get splash screen, get main window (including showing my placemarks) and then bomb.

If anything Google Earth has got worse. When I first upgraded to Ubuntu 13.10 Google Earth would bomb most of the time on startup but given some patience (i.e. just keep starting it) it could usually be made to start and then once started it would be usable and stay up. However a few updates after that, I now can't start it at all. Even with 20 attempts to run it, it will just bomb on startup 20 times i.e. completely unusable, completely broken.

Google Earth version appears to be 7.1.2.2041-r0 (That's from dpkg-query as obviously I can't ask Google Earth itself.)

---

### Post by monkeybrain20122 on 2013-12-29
Not sure why it doesn't work for you. You said you upgraded to 13.10, any possibility of corrupt configurations? (hidden file .google-earth in home)

---

### Post by Newbunto on 2013-12-29
> **monkeybrain20122 said:**
> any possibility of corrupt configurations? (hidden file .google-earth in home)

Doesn't look like it.

I moved .googleearth away to a different name and ran google-earth and it automatically created .googleearth again but still bombed. Strangely though I ran google-earth a few more times (with the brand new config) and after a few more bombs, one of the runs didn't bomb. That was not reproducible though. Went back to bombing after that. But ever since Ubuntu 13.10 it has been hit and miss (mostly miss!) running google-earth.

What exact version of google-earth do you have?

---

### Post by monkeybrain20122 on 2013-12-29
Ge version 7.1.1.1888

---

### Post by monkeybrain20122 on 2013-12-29
Ok, just downloaded and installed the latest version 7.1.2.2041, still works. No crashes.

---

### Post by alphacrucis2 on 2013-12-30
> **monkeybrain20122 said:**
> Ok, just downloaded and installed the latest version 7.1.2.2041, still works. No crashes.

May depend on which graphics driver you are using. I get the same symptoms as the other poster where it works about one time in ten but otherwise crashes shortly after starting. I'm using nvidia blob

---

### Post by monkeybrain20122 on 2013-12-30
> **alphacrucis2 said:**
> May depend on which graphics driver you are using. I get the same symptoms as the other poster where it works about one time in ten but otherwise crashes shortly after starting. I'm using nvidia blob

I suspect it is a graphic card or driver issue.

I have two 13.10 installations, one uses the Nvidia blob (331.20) the other uses noveau (on an external hd), ge works fine on both, it never crashes. (Ok, with the blob need to uncheck "compress" in 3d view or get black street view, it is a Nvidia bug that affects Windows as well) The same ge version on both, 7.1.2.2041.

---

### Post by Newbunto on 2013-12-30
Hardware is nVidia GeForce GTX 560M. Driver package is nvidia-319. In case it helped, I just now let it pick up updates so is now nvidia-319-updates. (Went from nvidia 319.32 to 319.60, I think.) Needless to say, Google Earth is still bombing.

I was already using nvidia-319 on Ubuntu 12.04 LTS i.e. before the upgrade to Ubuntu 13.10 - although I couldn't swear that Google Earth was working as I don't use it "every day". Shortly before upgrading Ubuntu I had upgraded the nvidia driver from nvidia-304, trying to fix other issues. But there was a time before I upgraded to Ubuntu 13.10 when some combination of software allowed Google Earth to work reliably.

---

### Post by monkeybrain20122 on 2013-12-30
Upgrade or fresh install? Could be bad upgrade. You can upgrade your driver without upgrading the system. use x-swat or xorg-edger ppa.

---

### Post by Newbunto on 2013-12-30
Upgrade. In individual steps. 12.04 -> 12.10 -> 13.04 -> 13.10. A fresh install was too painful to contemplate at the time.

---

### Post by Bucky Ball on 2013-12-31
> **Newbunto said:**
> 12.04 -> 12.10 -> 13.04 -> 13.10. 

Not unexpectedly problematic (not to mention time consuming). Did you try each upgrade before heading onto the next??? You might check to see you ONLY have the 13.10 repositories enabled in Software Sources.

I think I would have waited or installed 13.10 on another partition as LTS upgrades directly to the next LTS, leapfrogging the interim releases in between. In your case, that would have been 12.04 LTS>14.04 LTS when it is released next April. ;)

Bit off topic but thought I'd mention FYI ...

---

### Post by monkeybrain20122 on 2013-12-31
Well other than graphic driver your problem may be the result of bad upgrade (I always do clean install) You can install Ubuntu 13.10 on a small test partition and see if you still get the same problem with google earth. I have a suspicion that many strange problems people have about 13.10 (or any release for that matter) are due to bad upgrades (so you hear claims like installing *buntu or Mint every problem goes away, because then it would be a fresh install)

---

### Post by Newbunto on 2013-12-31
> **Bucky Ball said:**
> (not to mention time consuming)

A fresh install was going to be time consuming too, more so than doing the sequence of upgrades.

> Did you try each upgrade before heading onto the next?

What does "try" mean?

Try Google Earth? No. I didn't know that Google Earth was going to break on 13.10 so it wasn't something that I was testing. So Google Earth may actually have broken in one of the intervening releases.

Try a few basic things like booting up and logging in and accessing files and accessing the web? Yes.

> You might check to see you ONLY have the 13.10 repositories enabled in Software Sources.

If I should be looking at [FONT=courier new]/etc/apt/sources.list[/FONT] then it seems to be clean. No occurrences of precise, quantal or raring.

> In your case, that would have been 12.04 LTS>14.04 LTS when it is released next April.

Wasn't an option. I was having a significant issue with 12.04 (at bootup graphics often but fortunately not always fail to initialise leaving me with console only). The upgrade does seem to have resolved that.

I will certainly upgrade when 14.04 comes out.

---

### Post by Bucky Ball on 2013-12-31
> **Newbunto said:**
> A fresh install was going to be time consuming too, more so than doing the sequence of upgrades.

You are kidding, right? It takes about half an hour to an hour to do a clean install. Backing up your personal data may have taken some time, but that should always be done before doing an upgrade anyhow as they can be problematic (sometimes extremely). 

> **Newbunto said:**
> What does "try" mean?

Try each upgrade to see if the actual upgrade to the next release worked. Nothing to do with Google Earth.

> **Newbunto said:**
> Try a few basic things like booting up and logging in and accessing files and accessing the web? Yes.

Yes, that. 12.04 worked fine before the next upgrade to 12.10, then?

So, 13.10 is working but Google Earth still isn't.

---

### Post by Newbunto on 2013-12-31
> Yes, that. 12.04 worked fine before the next upgrade to 12.10, then?

Well, 12.04 was not exactly working fine - repeated problem initialising the graphics. But 12.10, 13.04 and 13.10 all had no obvious or major flaws. 12.10 and 13.04 were good enough to upgrade to the next release but didn't receive extensive testing by me.

> **Bucky Ball said:**
> You are kidding, right? It takes about half an hour to an hour to do a clean install. Backing up your personal data may have taken some time, but that should always be done before doing an upgrade anyhow as they can be problematic (sometimes extremely).

Actually backing up doesn't take much time (maybe 20 minutes to image the entire drive). Restoring stuff is slower.

Also, installing and configuring other software that will have been wiped out by a fresh install.

> So, 13.10 is working but Google Earth still isn't.

13.10 seems to have a few rough edges. Google Earth is a high profile one. I've also had issues with PuTTY (q.v.) and LibreOffice.

---

### Post by ubunt72 on 2014-01-05
I have a problem with GE not working either.   Not sure why.   I carried out all the steps.   I agree with the other poster who said all the 'how-to's' out there are just outdated or awfully written.   If you get it to work, present EXACTLY WHAT YOU DID.

There are many posters saying they did A, B and C and it worked for them.   But, there is crucial info being left out.

I have the error message (when I try to run it from the command line):
./googleearth-bin: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory


When I start 'the globe', the screen just goes back to my windows that are open (i.e. nothing seems to happen).   I am currently using 14.04 and ver. 7.1 of GE is installed (the default download as of today).

---

### Post by Bucky Ball on 2014-01-05
> **ubunt72 said:**
>    I am currently using 14.04 ...

Then your post does not belong here and is not related to this thread. 14.04 LTS is testing, not released until April, and all support posts/threads should be posted in the ***Ubuntu +1*** sub-forum. Thanks.

This is a non-support discussion thread in a non-support sub-forum. ;)

---

### Post by ubunt72 on 2014-01-05
My point is it doesn't matter if it's 13.10 or 14.04, most write-ups for Google Earth are now outdated.   There is too much confusion and mention of ia32-libs which is outdated info.   Okay?

---

### Post by oldos2er on 2014-01-05
I had GE 7.1.1.1888 running on 14.04 (64-bit), but it had the [bug of not showing Panoramio images]("http://productforums.google.com/forum/#!msg/earth/_h4t6SpY_II/jM5-GACFL8IJ"). I managed to install the newest stable version (as of today) of GE, with the bug fix. Here's how (NOTE: This assumes a 64-bit system, and that you have some familiarity with working in terminal. I'm not responsible if you mess up your system):

Download 64-bit deb of GoogleEarth stable from  [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) and [URL="https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit?usp=sharing"]ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.txz
[/URL]

Open a terminal, run ```
sudo dpkg -i google-earth-stable_current_amd64.deb
``` Next we need to remove ia32-libs dependency, so ```
cd /var/lib/dpkg

sudo cp status status.backup

sudo nano status
``` You don't need to use nano if you prefer a different editor; whatever you use needs root privilege to edit the status file. Search for google-earth-stable, remove ia32-libs from the *Depends* line, save and exit the file. Run ```
sudo apt-get install -f
``` to complete the installation.

Now we need to extract the tar file contents to a new folder (I'm assuming you downloaded it to ~/Downloads/): ```
cd /opt/google/earth

sudo cp -a free free.newlibs

cd free.newlibs

sudo cp ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz .

sudo tar xvf ~/Download/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
``` Update links: ```
sudo mv /usr/bin/google-earth /usr/bin/google-earth.old

sudo ln -s /opt/google/earth/free.newlibs/googleearth /usr/bin/google-earth
``` Now ```
google-earth
``` should work.

This is not my work, but amirpli's. See this [README]("https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit?usp=sharing") for more info. 

Hope this helps those who're having problems.

---

### Post by monkeybrain20122 on 2014-01-05
> **oldos2er said:**
> I had GE 7.1.1.1888 running on 14.04 (64-bit), but it had the [bug of not showing Panoramio images]("http://productforums.google.com/forum/#!msg/earth/_h4t6SpY_II/jM5-GACFL8IJ"). I managed to install the newest stable version (as of today) of GE, with the bug fix. Here's how (NOTE: This assumes a 64-bit system, and that you have some familiarity with working in terminal. I'm not responsible if you mess up your system):

..


Hi, just fixed the Panoramio images. Thanks a lot!

The instructions can be simplified a bit. Basically just untar the new qt libs into free and that's it. No need to create a dublicate and then change the simlink. (Don't really need to back up those files for reference, if something goes wrong just reinstall ge)

so  install google-earth either following this guide or by rebuilding the .deb to remove ia32-lib dependency like in post #5

```
sudo apt-get install libfreeimage3
```

```
cd /opt/google/earth/free
sudo tar xvf ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
```

that's it.

---

### Post by oldos2er on 2014-01-05
I prefer not to overwrite, so I don't. Plus [the instructions I was working from]("https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit?usp=sharing") recommended doing that way, so I did. 

Re: ia32-libs, I think it's easier to edit the status file than to rebuild the deb, but again, that's just me. It all comes down to personal preference.

Thanks for your feedback, glad it worked for you.

---

### Post by help_me2 on 2014-01-06
Google earth is just google maps made into its own app. They pretty much do the same things. (street view, terrain, etc.) I don't even bother with GE any more.

---

### Post by monkeybrain20122 on 2014-01-06
> **help_me2 said:**
> Google earth is just google maps made into its own app. They pretty much do the same things. (street view, terrain, etc.) I don't even bother with GE any more.

Yeah except google map uses flash which is slow and buggy on many machines.

---

### Post by Newbunto on 2014-01-06
Google Maps doesn't appear to have tools like "Ruler", which I use frequently.

---

### Post by oldos2er on 2014-01-07
> **Newbunto said:**
> Google Maps doesn't appear to have tools like "Ruler", which I use frequently.

Nor does it have Mars or the moon.

---

### Post by beesthorpe on 2014-01-07
Google Maps does have a ruler if you click the "Maps Labs" link at the bottom of the left hand side bar you can initialise it.  I think you might need to be signed into a Google account to do this however, and I wouldn't argue if you said it was not exactly intuitive...

---

### Post by Newbunto on 2014-01-07
> **beesthorpe said:**
> Google Maps does have a ruler if you click the "Maps Labs" link at the bottom of the left hand side bar you can initialise it.  I think you might need to be signed into a Google account to do this however, and I wouldn't argue if you said it was not exactly intuitive...

Thanks very much. Seeing as I am stuck with Google Maps for the moment )-:, that is very useful to know.

(It doesn't look as if you need a Google account in order to use the ruler. I think I do have a Google account but I am reasonably sure that I am not signed in. For example, clicking on "My Places" tells me that I am not signed in and invites me to do so.)

---

### Post by Smask on 2014-02-15
Never mind, my solution borks searches completely.

---

### Post by Idiens on 2014-10-31
Sigh! After following all this good advice, GE works when started in the terminal and shows panoramio pictures. But when started from the icon in Unity, it either crashes or if it works, pictures are blank again. In the terminal there are lots of:
[1031/153023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
statements.

---

### Post by Bucky Ball on 2014-10-31
*Thread closed*.

This thread hasn't seen any action for nine months or so and you don't have much chance of support buried in this graveyard.

Improve your chances by posting a support thread in the appropriate forum section and with a descriptive title. All the best.

PS: If you're still using 13.10, which is what this thread deals with, then you should consider upgrading to a supported release as it is no longer supported by Canonical or these forums.[ Please see here]("https://help.ubuntu.com/community/EOLUpgrades").

---

