---
title: "Veoh peercasting network needs volunteer help with GUI for Linux client"
date: 2006-06-09
forum: The Cafe
---

### Post by jbus on 2006-06-09
Those of you that are not familiar with Veoh should check it out (veoh.com). Think YouTube, but with peercasting and hi-res video in its native format. You can preview low-res video on the website just like youtube, but you need the client to view hi-res video. They currently only offer Windows and Mac clients.

I emailed Veoh about releasing a Linux client...
> Please release a Veoh client for Linux. There are more Linux users in the world than there are Mac users. Veoh could gain a larger share of users by reaching out to Linux users that are often ignored. 

and this is the response I got:

> Most of our code already runs on Linux.  The GUI part doesn't. Unfortunately, we can't afford to support the development effort of the
GUI on Linux.

We would, however, like to support a volunteer effort.

Do you know any coders who would like to work on this?

Ted Dunning
Veoh Networks

I'm not a dev or I'd help, but maybe some of the talented devs out there can help get us a nice Veoh client on ubuntu, that would be awesome.

If anyone is interested in helping let me know and I'll PM you with Ted Dunnings email or you can contact him through the Veoh contact page [http://www.veoh.com/contact.html](http://www.veoh.com/contact.html)

---

### Post by AndrewGene on 2007-06-26
Bump, I'd really like to see this too.

---

### Post by DoctorMO on 2007-06-26
It depends on their licensing; very few developers will merrily work on software for free under a proprietary license. Now we see an excellent reverse to the old FSF vs OSS, technically OSS people should be happy to work on it, but I doubt it because your results are not open to even the most modest peer review.

Please get in touch with them and ask them what the plan was, then post it in a development community (ubuntu forums is a user community and only a few devs frequent this place (lack of respect from users mostly))

---

### Post by H.E. Pennypacker on 2007-07-14
I'd like to see this happening, but I guarantee you that the Linux client's GUI won't even compare to its counterparts in design.  The sleek dark look of online player looks superb, but I am certain it won't be accomplished on a Linux system.  Things just don't look as nicely here (Linux).

---

### Post by PriceChild on 2007-07-14
What amused me most a few weeks ago, was that I could download veoh videos using their player... and watch them fine in it.

However if I tried to use windows media player to view them it would be upside down and back to front. So I copied the file from the virtual machine to the host ubuntu install and played the video.... perfect!

I wonder what they would want from the app... just something to be able to authenticate, then manage downloads? Everything else could be done by the standard video players we already have.

---

### Post by danieldarmstrong on 2007-09-17
I am currently working with Veoh to provide a native Linux client. I flew to San Diego and met and worked along side them for a few days and I am proud to say that they are very interested in an open source Veoh effort. I have been developing a Veoh client for Linux for the last month or so and I do have a working command line download manager available. You can find more information on my effort at [http://ichthudion.wordpress.com](http://ichthudion.wordpress.com) I am still heavily improving my framework and I have recently started designing the GUI but it is still a bit away. For those who do not think Linux can meet the beauty of the Windows client. You have not seen Linux at it's true potential. Ubuntu is not a beautified distribution and tends to rape Linux of the potential it possesses. My first GUI will not match that of the Windows client but you can expect it to get there soon enough as I'm just putting a concept together to provide a quick Veoh solution. If you are only interested in downloading from Veoh then I recommend that you take a look at the openVeoh command line client that I have prepared. If you need any specific help in building and using the software please do not hesitate to contact me via skype at daniel.d.armstrong or via email at [email]daniel.d.armstrong@gmail.com[/email].

---

### Post by SunnyRabbiera on 2007-09-17
> **DoctorMO said:**
> It depends on their licensing; very few developers will merrily work on software for free under a proprietary license. Now we see an excellent reverse to the old FSF vs OSS, technically OSS people should be happy to work on it, but I doubt it because your results are not open to even the most modest peer review.

Please get in touch with them and ask them what the plan was, then post it in a development community (ubuntu forums is a user community and only a few devs frequent this place (lack of respect from users mostly))

well even if the app is propriety as long as they allow even a few people look at their code and let those people development without those developers facing a patent issue or some crap its good...
but pay em!
Maybe if we convince them perhaps Veoh might allow GPL to be used

---

### Post by crypto178 on 2007-09-17
> **danieldarmstrong said:**
> I am currently working with Veoh to provide a native Linux client. I flew to San Diego and met and worked along side them for a few days and I am proud to say that they are very interested in an open source Veoh effort. I have been developing a Veoh client for Linux for the last month or so and I do have a working command line download manager available. You can find more information on my effort at [http://ichthudion.wordpress.com](http://ichthudion.wordpress.com) I am still heavily improving my framework and I have recently started designing the GUI but it is still a bit away. For those who do not think Linux can meet the beauty of the Windows client. You have not seen Linux at it's true potential. Ubuntu is not a beautified distribution and tends to rape Linux of the potential it possesses. My first GUI will not match that of the Windows client but you can expect it to get there soon enough as I'm just putting a concept together to provide a quick Veoh solution. If you are only interested in downloading from Veoh then I recommend that you take a look at the openVeoh command line client that I have prepared. If you need any specific help in building and using the software please do not hesitate to contact me via skype at daniel.d.armstrong or via email at [email]daniel.d.armstrong@gmail.com[/email].

It's a great project.

I'm trying to build vget right now, but it complains about a missing "veohsystem.h" file. I don't have much experience at compiling software.
If anyone else wants to try, here is what I did so far on feisty:
Install the build-essential, libssl-dev, and subversion packages (if missing).

Then, open a terminal somewhere in your home directory:
svn co [https://veohlin.svn.sourceforge.net/svnroot/veohlin](https://veohlin.svn.sourceforge.net/svnroot/veohlin) openveoh
cd openveoh/src/sockets-cpp
make
sudo make install
cd ../tools/vget
./build

Here I get the error about the missing veohsystem.h

---

### Post by danieldarmstrong on 2007-09-17
I am terribly sorry about the missing files. I forgot to add it to my repository, will fix that right now. There we go, it is fixed. Also to those who are mentioning that it needs to be GPL... Please notice the name of the software is "open"Veoh. It is GPL and Veoh stands behind me all the way. Their source code is useless to us as it is almost entirely written in Win32 API using embedded IE to operate. I have also started adding the ability to pull current logins from Firefox. On my machine it is added and works great but I will have to rewrite a lot of the library to add it in. In order to keep you guys with a working application I will not be updating the repository with this yet. Anyways, I love the feedback guys.

Regards,
Daniel
openVeoh
[http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

---

### Post by danieldarmstrong on 2007-09-17
> **crypto178 said:**
> It's a great project.

If anyone else wants to try, here is what I did so far on feisty:
Install the build-essential, libssl-dev, and subversion packages (if missing).



Also make sure you have SQLite installed along with dev packages. I will install Ubuntu in VMware later on tonight and try to get a precise set of instructions for Ubuntu gathered up.

Regards,
Daniel
openVeoh
[http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

---

### Post by DoctorMO on 2007-09-17
Let me know when you want to start packaging, I can give you some advice in that area.

---

### Post by crypto178 on 2007-09-18
> **danieldarmstrong said:**
> Also make sure you have SQLite installed along with dev packages. I will install Ubuntu in VMware later on tonight and try to get a precise set of instructions for Ubuntu gathered up.

Regards,
Daniel
openVeoh
[http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

Thanks! It works now.
To wrap up:

Dependencies (on ubuntu feisty 7.04):
```
build-essential
libssl-dev
subversion
libsqlite3-dev
```

And to build it:
```
svn co [https://veohlin.svn.sourceforge.net/svnroot/veohlin](https://veohlin.svn.sourceforge.net/svnroot/veohlin) openveoh
cd openveoh/src/sockets-cpp
make
sudo make install
cd ../tools/vget
./build
```

Now onto testing!

---

### Post by danieldarmstrong on 2007-09-18
When you want to update to the latest version you do not need to do an "svn co <url> <dir>" you only need to do "svn update" from the top level of the openveoh sources.

Regards,
Daniel
openVeoh
[http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

P.S. If anyone has any web development experience and would like to create a site for openVeoh then please contact me. We have webspace on Sourceforge. Just no time to do a site.

---

### Post by aeto on 2007-09-24
For those of you facing problems..just know the following:

When running **make install**, everything is installed in */usr/local* as dictated by the *Makefile* (only *PREFIX* understood by default, no *DESTDIR*).

You can change that by running **make PREFIX="$" install** where **$** is your preferred starting directory. For example, you may prefer installed apps to be in */opt* or */usr*, so it would look like **make PREFIX="/opt/openveoh" install** and **make PREFIX="/usr" install** respectively.

The source file *$openveoh/src/tools/vget/build* looks in the new paths created by **make instal**l, including */usr/local/include/Sockets* which contains all the **.h* files. The paths can be changed in *$build* to reflect your choice or the distro's packaging system.

So in short, if you successfully finished with **make && make install**, the only cause for a failed **./build** is wrong path references. So make ammendments where necessary :) Ahh yes and in my case the main binary **vget** wasn't part of the installation so you can just copy it over to the binary path, though I don't know if that's all since it works here anyway.

Btw, great work on this. Thanks! :mrgreen:

---

### Post by danieldarmstrong on 2007-09-27
My sources are now in a new repository and you will need to delete the current ones and grab a fresh copy like so:

rm -rf openveoh
svn co [https://openveoh.svn.sourceforge.net/svnroot/openveoh](https://openveoh.svn.sourceforge.net/svnroot/openveoh) openveoh

I have created a true build and install system for the project which you can find the instructions for on my blog at: [http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

For those who are impatient and want the instructions now:

Navigate to the openveoh directory and run:

make sockets
make
make install

This will build and install vget, the Firefox plugin and the protocol handlers for Firefox. This is everything you need to start clicking the "Download Video" links on veoh.com

I hope you guys enjoy!

Regards,
Daniel
openVeoh
[http://ichthudion.wordpress.com](http://ichthudion.wordpress.com)

---

### Post by daxumaming on 2007-10-04
i gave up on Veoh when they started cutting down videos to 5mins. I emailed them and got a reply that I should check out danieldarmstrong's blog. I didn't know that there's a post on this forum regarding openVeoh. Anyway, good work with your project. Just need to finish a few stuff of my own, then I'll start helping out.

---

### Post by daxumaming on 2007-10-04
Hmmm, I seem to be having some problems with the videos I downloaded. Konqi tells me that the video I have is 45+mins.. problem is, I can only play up to five mins. I tried xine, vlc, kaffeine, real player, and mplayer, but still no luck. i must be doing something wrong.

---

