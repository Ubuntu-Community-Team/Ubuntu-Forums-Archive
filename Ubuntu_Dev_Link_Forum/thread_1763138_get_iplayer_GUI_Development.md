---
title: "get_iplayer GUI Development?"
date: 2011-05-20
forum: Ubuntu Dev Link Forum
---

### Post by darren123web on 2011-05-20
Hello All,

Just started the process of converting from Windows Vista to Ubuntu 11.04 on my lappy.

Pretty impressed with Ubuntu so far I must say.

One thing I'm wondering is how to contact the Developers of the get_iplayer GUI (if indeed it is currently under development)

(no luck with many attempts downloading / installing iPlayer from BBC etc)

Selfish reasons really I suppose - I'd like a decent GUI and think I may be able to contribute at least on the graphical layout side of things.

But - I do think this would be a great feature for Ubuntu that would make it easier for even more Windows users to convert to Ubuntu.  

Any pointers gratefully received.

---

### Post by johnaaronrose on 2011-08-10
I've written a GUI for get_iplayer in Gambas. It allows selection of a program followed by downloading it. It calls get_iplayer  with a --raw parameter since it doesn't work without it. Its .deb  package (which includes Gambas runtime) is  downloadable from:
[http://dl.dropbox.com/u/3928731/irec...0.39-1_all.deb]("http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb")

Selecting Default mode results in a TV programmes being recorded as a  .flv  file. Use Mobile Media Converter / HandBrake / VLC / WinFF if you  wish  to convert to another format (e.g. to play on the iphone). 

I'd be grateful if people who try iRecorder would let me know their  experiences with it, particularly if they wish to suggest enhancements. 

I'd be happy to write similar functionality incorporated into iRecorder  of the code used in get_iplayer if anyone could document the Perl code  used by iRecorder  (i.e usage of the search and get options.  Alternatively, documentation  of the requests & responses from the  iPlayer archives. Similarly,  for Channel 4 IOD.

---

### Post by johnaaronrose on 2011-08-10
I've made an error in my last message:
The .deb file is Canonical's attempt at  packaging get)iplayer 2.79 which is actually 2.78! To get get_iplayer  2.79, either run following in terminal:
sudo apt-get install git-core && \
cd ~/ && \
git clone git://git.infradead.org/get_iplayer.git && \

sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer(which will put  the source etc into a new directory called get_iplayer, which you can  delete afterwards, as the Perl script is installed into /usr/bin)

or get the Perl script from:
[http://dl.dropbox.com/u/3928731/get_iplayer](http://dl.dropbox.com/u/3928731/get_iplayer)
and install it by:
sudo mv /home/user/Downloads/get_iplayer /usr/bin/
(assuming that user is your login id & that you have configured  Firefox to download to Downloads directory, otherwise adjust  appropriately) .

---

### Post by conal on 2011-10-09
Hi johnaaronrose, pleased to see you are working on this project! Just to let you know I got this message every time I started your application up:

> This application has raided an unexpected error and must abort

[6] Type Mismatch:wanted Void, got integer instead.
Fmain.?.0

So then I realised I needed to update get_iplayer as descibed in your second post - I used your second suggestion. then I tried launching your gui. It no longer crashes after launching. I search for programs on your GUI but no matter what I put in, even if I know it exists - it returns no results. Then I tried clicking the Hints button and it crashed with another > This application has raided an unexpected error and must abort
 message. 


I'm probably doing something silly here. For now I have reverted to the 2.78 version of iplayer in the ubuntu 10.10 repos. This works fine from the command line, so I'm not too bothered - just wanted to give you feedback, as requested!

Thanks 

Conal

---

### Post by johnaaronrose on 2011-10-10
Conal,

Thanks for your feedback. I've just run the app on an Acer Aspire One using 10.04 Netbook Edition and it was OK. When the app starts, it tries to download details of all TV programmes. It states on the bottom that they are being retrieved. When it's assembled all the details, the app states that all details are retrieved. Did that happen with your test?

At the point when all details are retrieved the normal user action is to select a Title or key in part of a Title and click the Search button. I haven't been able to repeat any of the behaviour that you found. Did you run iRecorder from the Other menu in the Applications drop down list?

Very occasionally I've found the app crashes due to the BBC's servers changing the feed list of programmes. I've also found that the app crashes when rtmpdump is installed or when flvstreamer is not installed.

As I previously stated/hinted, I don't understand get_iplayer's code. I'll have a look at iRecorder's code.

---

### Post by conal on 2011-10-10
I'm pretty sure after I updated to the newer get_iplayer it updated the feeds. I think I followed the normal user action you described. I should also meantion that I could not run the newer version from the command line as it said I did not have permission to access the application, but aptitude recognised it as the newest version of get_iplayer so I'm pretty sure it had installed ok. I'm using a powerPC - maybe that could be the reason - someone else posted a different GUI for get_iplayer that worked fine on my x86 laptop, but would not run on the PowerPc. I definately have flvstreamer installed, not sure about rtmpdump (I'm not on that computer just now) - I rtemeber getting tied in knots with these when trying to install get_iplayer on an older version of Debian. 

Anyway - like I said I'm not too bothered as long as I can use it from the command line. As I currently only have PowerPCs it is the only way I can watch iPlayer. Thanks for the quick reply. I'll give iRecorder another shot in the future.

Best

COnal

---

### Post by johnaaronrose on 2011-10-11
New version of iRecorder is at:
[http://dl.dropbox.com/u/3928731/irecorder_0.0.41-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0.41-1_all.deb)

(PS inserting hyperlink did not work properly so you'll have to copy the above URL into your browser's URL box)

Fixes bug of allowing user to e.g. click Record button before a title is selected which caused crash.

---

### Post by johnaaronrose on 2012-07-09
Latest version of iRecorder is at:
[http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb)

You need to use Gambas 3 ppa by kendek, due to Benoit now having a check
that Gambas version dev = (though might be <=) Gambas version run on. It downloads from:
[https://launchpad.net/~nemh/+archive/gambas3](https://launchpad.net/~nemh/+archive/gambas3)

No need to download anything explicitly from the ppa site: after adding the repository, just do sudo apt-get update & sudo apt-get upgrade. Running the above .deb should cause gdebi to install the appropriate Gambas3 modules.

---

### Post by ReetP on 2012-12-19
FYI your dropbox links are either wrong or dead.

B. Rgds
John

---

### Post by howefield on 2012-12-19
Old thread closed.

---

