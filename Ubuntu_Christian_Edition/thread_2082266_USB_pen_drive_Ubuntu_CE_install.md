---
title: "USB pen drive Ubuntu CE install"
date: 2012-11-08
forum: Ubuntu Christian Edition
---

### Post by prism01 on 2012-11-08
USB pen drive UbuntuCE install.

Tags,  USB, pen drive, flash drive, install.

Hi

This post is about installing UbuntuCE on a 16 gigabyte Sandisk Cruzer.

This post is intended for the person who is absolutely new to Linux.

Ergo, **if the gentle reader is an experienced Linux person**, he or she need not read this post in terms of anything new.  And for the experienced Linux person, one can cut to the chase and merely mention that the install went as normal for a usb pen drive.

The drive originally had another Linux distro on it formatted to Ext 4..

1) Why do it?
a) Very simply it is convenient.
b) the resulting install is very fast.
c) it is tres kewl to brag that one did it! :)

2) Why not?
a) One will not have a lot of "drive space" upon which to dump files at will so that one will need an other, external storage drive.   However, that is a good thing.  One should try to not mix data and an OS on one drive.
b) One will have to go to the trouble to actually make sure that one does not install to the Windows drive if one does not want to do a "dual boot".


3) **THIS SECTION OF THE POST IS A RUNNING NARRATIVE OF THE INSTALL**
a) The install can be made as a "clean install" or as a "dual boot".
b) If one is not completely at ease with doing an install in terms of "possibly installing on my Windows hard drive", then this author would recommend either unplugging the existing Windows hard drive manually or taking it to a friend or small business to have it unplugged.  And having the person show how to plug it back in.  If one is going to go to a business, one will have to pay, probably, for a "bench fee", but one would then be able to do it onesself so the cost can be amortized over many installs of  free (no cost) distros.
c) Physically unplugging the hard drive while the computer is turned off will in no way create a situation in which the Windows hard drive will "know" that it was removed and then "complain" after replugging it and starting Windows.
d) HOWEVER, if one is willing to actually read the installer, and to do a "custom" install, then one will be shown that there is a hard drive and a usb drive, and one would install to the usb drive.
e) the installer will NOT make a mistake but the person making the decision might.  
f) If one is not familiar with the terminology, one can default to look at the SIZE of the drives shown in the installer, by and large the smaller "drive" will be the USB drive.

4) An unusual thing about this particular install.

A rather amazing thing occurred in the install.  The latest Ubu, apparently, does, indeed, get rid of Sandisk's very small file that it reserves to itself.

5) If the computer will not SEE THE INSTALL, after it is made, one will have to get into the "BIOS" and change the "boot order".

This particular install required changing both "the boot order" and also "selecting"  "DOD recognize USB" in another part of the BIOS.

Since different manufacturers can arrange this information in different ways in the BIOS screen, one will have to manually hunt around for where to make the changes.   Please remember that if one gets scared in the middle of this then just "save without changes".

6) The install.

a) It is recommended, by this author, to not install, "directly" from the live cd.

Run the live cd and make sure that the wireless is working so that one can have extra stuff installed during the initial process.

b) One needs at least 4.4 gig of space for the install.  So, a 16 gig drive is large enough if one does not load it up with other applications.
c) The install went as is usual for a modern Ubuntu install.
d) It checked for the minimal drive space, 4.4 gig, and for an internet connection.
e) It asked whether to install 3rd party software, etc.
d)_It asked whether to erase the previous install or to do a custom install.  The custom install would mean keeping the original OS and one has to make some decisions(these are not discussed in this post).
e) The author chose "erase" and it installed to the full 16 gig and erased the SanDisk partition.
f) It installed with Ext.4 file system.
g) It automagically found the correct time zone and the language(English in this case).
h) Since it was installing over a previous install it searched for original files that would be applicable to the new install and this reduces install time.
i) The install was 12.04 LTS.
j) An ODDMENT during the install was in the little textual notes there was a sentence that said something really odd about asking questions at the forums:

"You'll be sorted in no time at all".

Possibly a developer might comment upon this.  However, it is irrelevant to the actual install process.

k) The total install took about 50 minutes.
l) The initial splash screen has "Christian Edition" in small, neat, letters over the word Ubuntu.  The usual dots cycling through colours indicates that the OS is being activated.
m) Immediately upon the first boot up one sees a "script" running in a white terminal.  This script says that it wants to do a "distribution upgrade" which actually just is a flash plugin installer, gstreamer, etc. for media codecs etc and Skype and DropBox.  This takes quite a while to run.  Dropbox complains that it is running "from an unsupported location" and wants to install from the website, but will not do so.  The interactive boxes that deal with the DropBox install are somewhat confusing. 
n) At first blush this author thought that going to a website and downloading a .deb file and letting the installer install it would be a salutary lesson for the absolutely new user but....when it did not install...well that is a bad thing. :)
o) However, again, upon reconsideration, it was a good thing anyway because the absolutely new user from Windows is exposed to the absolutely gorgeous screen for Ubuntu Software store.  The inclusion of a pretty game advert at the top is especially nice.

7) ** THIS SECTION OF THE POST DISCUSSES WHAT ONE HAS AS A RESULT OF THE INSTALL. **

a) One sees the Unity interface with three customized icons in the left panel, in addition to the usual suspects, for Xiphos, Bible Time and Bible Memorizer.

b) One gets an obligatory Ubuntu coloured wallpaper that is actually very nice and Christian.  This author personally prefers ANY colour other than the obligatory Ubuntu "brown".   To ameliorate this the developers have provided a very large selection of Christian themed wallpapers that are of a variety of styles and colours so the situation was easily remedied.

** DISCUSSION OF THE BIBLE SOFTWARE**
c) The author decided to install a Bible through Bible Time and was initially confused by the app.
i) When one opens the installer, and selects "bookshelf" there is a LONG wait.  The window "goes transparent black". And then one waits.
After up to a minute, the database is populated.
This time delay occurs each and every time that the application is NEWLY opened, but if one wants to install multiple items in one session then one can do it quickly, just one at a time.
After the database is populated, all of the boxes are ticked for install.  But, as previously stated, one cannot install more than one item at a time.
One should go to the very top of the list and untick the top "box" and all will be unticked.
One can then tick a certain Bible or book and it will download and install in a relatively short while.
The popup installer window will stay open and one needs to close it manually.  The best way to determine when the Bible/book is onboard seems, to this author, to be to move the popup to one side so that one can see that the box ticks as to being installed.
The Bibles and books are installed through Crosswire and there seems to be no way to change the source.  If anyone would care to comment on this please do so.
ii) The only way to add another item that is not in Crosswire is to download it manually.  The files have an extension which is ".bblx".  This file can be copied to the hidden folder: .sword.
However, it seems, that one cannot just install "a file" for a Bible.   There are associated files to the actual "Bible" file itself;  so one really should just go to a source and download "all of the stuff" in one file.
iii) A NOTE, however, about going to a "source" site.  One cannot actually download an external file without "joining" the site.  One will then get, possibly,  unwanted "donation nags" from the site.
iv) This author chose to not do so and will be content with the materials from Crosswire for the time being.
v) This author downloaded the Tyndall Bible and is having a pleasant time reading it.

d) Subsequent to downloading the Tyndall Bible,; BibleMemorizer  fully accepted the Bible and provided an easy way to work with memorizing stuff.

e) Xiphos also accepted the Bible and the author was able to interact with the Bible through Xiphos.

** THIS SECTION OF THE POST DISCUSSES OTHER, BUT NOT ALL, SOFTWARE IN THE DISTRO **

f) The other default software of UbuntuCE are the usual suspects; but some pieces are worthy of note.

** E- mail client **
g) The author was surprised to see the default e-mail client was not an integrated one, and that "contacts" is some kind of generic nameless app which is not connected to the e-mail client.  But, after perusing the forum the author was able to determine why the decision was made.

At least the "atheist detractors" of UCE do not have any justification in the aspersions from several years ago that the developers have not gone to a lot of trouble to actually produce a "different" distro.  :)  I have seldom seen an application which does not have a "help" file or other attribution.

** Rhythmbox **
h) The default Rhythmbox has been "customized" by providing a very short list of "radio stations" that seem to be oriented toward Christian music.
This is a good thing in that people who may not have heard different Christian music than the "mainstream" will be exposed to some creative stuff.
One cannot play a ".pls" stream from a site such as Shoutcast.
Rhythmbox found a music cd automagically, offered Musicbrainz to supply track information and played a music cd.

i) ** VLC media player **

1) Did play a .pls stream, by selecting VLC from the "open with" when the file was right clicked.

2)  VLC offered to play a DVD but failed.  An attempt was made using Movie Player with the same results.  After the below mentioned update the video still did not play.  There are "codecs" which are available that will play an encrypted DVD but they are not legal in some countries and, evidently, the developers opted on the side of legal caution.

j) Curiously, synaptic was also included, but that may have been because it is provided by Ubuntu.  Since the Ubu installer is locked into the left panel, one might assume that it was "left" there so that people could move beyond the Ubu installer.

k ) The updater provided 235 updates.

** Winetricks **

l) WineTricks is provided, I assume for people that want to use the Win version of Esword.

** WHY PEOPLE MIGHT NOT WANT TO USE WINE TRICKS AND JUST USE THE PROVIDED LINUX SOFTWARE **
A NOTE to new users of "Linux" from Windows.  
a) If one does not actually NEED to interact with MS products then one does not...need....a MS program in Wine. 

Apple people have spent a long time not using MS products.

In other words, if one is going to do e-mail, produce self-made "word" documents, etc. then Linux can do all of that stuff, so there is no actual need to run a MS product in Linux, except for that of "familiarity".

b) If one has not actually used Photoshop then learning G.I.M.P. does not have a very much longer learning cycle than Photoshop.  G.I.M.P. has a "skin" that emulates that of Photoshop for those who have used Photoshop.

vi) ** HARDWARE observations **

a) An old HP printer, parallel, was found and added by going to "printing" and "add".
b) a wide screen LCD screen was found automatically.
c) a set of external speakers were found automatically, including the Bass.
d) an Nvidia 5200 video card was found and configured automatically.
e) usb mouse and keyboard were found and configured automatically.

**SUMMARY:**

a) The install was a normal Ubuntu install, almost effortless, except for the "script" which did it's work with some small fiddling.
b) the install to a USB stick worked as if installing to a "hard drive" with the addition of having to enable in BIOS "DOS USB".   This would probably not be a problem with most folks.
c) the default "Bible" apps work as expected.
d) Some customization has been done for the icons on the left panel, the wallpapers, of which there are many provided, and the "radio" section of Rhythmbox.
d) What was not addressed by this author was installing in the presence of UEFI(secure boot).
e) Thumbs up to the developers.  :)

prism01

---

### Post by prism01 on 2012-11-09
Hello.
Please take this post as:
a) an attempt to inform parents about the positive domain blocking capabilities of Google Chrome.
b) what to "tell the kids" so as to not have them complaining about "losing their music(in terms of the radio stations)".
c) a reassurance that Rhythmbox will do the necessary things.

This author spends considerable time listening to streaming music on the net and is familiar with all of the genres and most of the things that are needed to get something to "play".

** DOMAIN BLOCKING **
a) In terms of "domain blocking" Google chrome does a fine job of this.  If the author attempts to listen to a music stream from "the net" in a "popup" player (as it were) a semitransparent mask appears that says something to the effect of: "oops, this domain has been blocked".

This occurs for a "Christian stream" as well as any other stream, so the parent should be able to rest assured that, given that the child does not try to do a work around, that the developers have done their job, as best they can, to filter/block unwanted content.

** APPROPRIATE RADIO STREAMS AS DEFAULT BY THE DEVELOPERS **
b 1 ) Since this author spends considerable time on the computer and listens to streaming music; a cursory listening to the provided radio stations indicates to this author that the developers have gone to some trouble to include some acceptable stations for at least "most" parents, (given that the player is to be used at all and not removed by the parent).

IF the parent wants to REMOVE the streams before use by the child a simple right click and remove of each stream will so do.

HOWEVER there is a concern, if the parent plans to allow the child to listen to the internet stations.

Because of the blocking capabilities of other parts of the system, one cannot "just add" a station, to Rhythmbox.

So....if the child accidentally REMOVES a station, it is pretty nigh not doable to add another one back in.

So, it is the opinion of this author that the parent might want to warn the child not to remove a station unless it is to be a permanent removal.

However, as stated in the OP.  An external stream can be added in VLC, so if the parent does not ever want the situation of adding a station to occur then VLC will have to be removed, but then some dvds might not be able to be played.

That, of course, is a decision for the parent to make since it seems to this author that the developers have gone to great lengths to accommodate a "range" of Christian outlooks.

** DISCUSSION OF HOW SOME RHYTHMBOX FUNCTIONALITY IS REDUCED BY NOT HAVING OTHER SOFTWARE AVAILABLE.**

b 2 ) Rhythmbox developers have made great strides in the development of the app but if certain "affiliated" items are not included then certain things are not functional, and this is true of ALL applications.

The problem with "stuff" waaaayyy down in the basic parts of any operating system is that the inclusion/exclusion of stuff affects other parts of the system.

This author has not been able to get things like "stars" or "latest played" etc. to work for Rhythmbox and this is because of the lack of a certain "script".

One would assume that if the developers wanted to include the "script" that they would have done so but have not done so for "blocking/privacy" reasons.

** SUMMARY STATEMENT: PARENTS CAN BE RELATIVELY ASSURED THAT THE DEVELOPERS HAVE DONE WHAT THEY CAN TO PROVIDE PARENTAL CONTROLS **
c)The parent can be relatively assured, in the opinion of this author, that: given that the parent wants the child to listen to streaming music at all:
i) the streaming music stations seem to be acceptable to, for this author, the "average Christian parent".
ii) Rhythmbox will play cds.

And, if one thinks about it, that is all that is really "necessary", the rest of it is "enhancements".

If there are questions please ask. :)

prism01

---

### Post by Megaptera on 2012-11-09
Very useful info in both those threads, I hope you'll be open to what I offer as constructive feedback?
The posts are very lengthy. Any chance you could break down the info in to 'bite size' chunks perhaps in different sections? Could you consider clerarer bullet points to seperate the salient points?
Maybe use heading such as:
- Intro to UCE
- Benefits of UCE for concerned families
- How to install to pen drive
etc etc.

Hope you're OK with these suggestions?

---

### Post by prism01 on 2012-11-09
good suggestions, I'll reformat them.  :)

prism01

---

### Post by prism01 on 2012-11-09
Hi Megaptera.

Done as done! lol

Since you are more "in tune" with the needs of readers of this forum, please feel free to make any other suggestions as you, or anyone else, see(s) fit.

prism01

---

### Post by prism01 on 2012-11-09
** THIS POST IS ABOUT THE FUNCTIONALITY OF DROPBOX **

** THE INITIAL CONDITION **

Dropbox, upon a first run, for this author, presented an error message to the effect that it was working from a location that was not operational.

The author, at first, as noted above, attempted a re-install with no result.

After the multitudinous updates another re-install was attempted with no results.

** THE RESULTS OF ATTEMPTING TO OPERATE DROPBOX AFTER THE ERROR MESSAGE **

The situation may, or may not, have been a problem with the actual install of dropbox.

The author attempted to open a pre-existing account and was informed that the password for Dropbox had expired.

The author only uses Dropbox occasionally, and only the free amount at that. 

** NOTE: DROPBOX OFFERS 250 MB FREE**

After a new password had been enabled, Dropbox does, indeed, work.

So the whole problem with Dropbox, as noted above, may have merely been one of ....

POOR WORDING OF AN ERROR MESSAGE by the developers of Dropbox.  Or not! :)

If anyone has questions about Dropbox, feel free to ask but a new thread might garner a more rapid response.

prism01

---

### Post by Megaptera on 2012-11-10
:) Thanks!! Those really are much easier to navigate :)

---

### Post by prism01 on 2012-11-10
my pleasure.

prism01

---

### Post by prism01 on 2012-11-19
Well, 
This author is considering that the intent of this thread is probably relatively complete.

After more than a week, the distro runs fine on a usb pen drive, and it should continue to so do.

A lot of distros run nicely on a pen drive, but not all ...not all by any means.

So for the developers to have included DansGuardian, firewalls etc, can do funny things to how an OS interacts with the web, and all the Christian stuff... and it work so well...

that kind of says something about the care and attention to detail exhibited by the devs.

If something appears that is worthy of note about the "install per-se" then the author will post it, but probably will not do much more in this tread.

If anyone needs some kind of help please so post and this author will undertake to help, but probably someone more experienced would pop in to do it right! lol

prism01

---

### Post by TRPrecht on 2013-01-03
thanks for the write ups.

---

