---
title: "HOW I Installed Lexmark X1270 on Lucid"
date: 2010-06-12
forum: Tutorials
---

### Post by tiggsy on 2010-06-12
I had such a lot of trouble getting this to work, I thought once I had finally managed it, this might be useful for other people. It worked for my X1270, and will most likely work on a lot of other varieties of Lexmark, specifially the X1100 and X1200 series pretty much for certain, but others too, I guess.

**This is the latest version of how to do it, as things have changed since I first set this up**
(I've left my original instructions in the next post, in case you need them for some reason).

**Works on**

Following the reports of several users in this thread, this procedure is valid for:

**Ubuntu 10.04 Lucid Lynx**
+ Lexmark X1170 printer (see fagulhaspt post #7)
+ Lexmark X1185 printer (see Travis13 post #14)
+ Lexmark X1270 printer (see tiggsy post #2)
+ Lexmark Z517 printer (see divali post #4)

**Kubuntu 10.04 Lucid Lynx**
+ Lexmark X1170 printer (see fagulhaspt post #7)

**Xubuntu 10.04 Lucid Lynx**
+ Lexmark Z705 (see InkyDinky post #8 )

**Ubuntu 10.10 Maverick Meerkat**
+ Lexmark X1270 printer (see inearlygaveup post #15 and moody_mark post #16)

**Unspecified**
+ Aspire 5100
+ Lexmark X1150 (see begsfg post #29)
**_Please report in your success/failures so we keep this list "fresh" _**

###
### HOW TO Install Lexmark printer in (K/L/X)ubuntu 
###
### As updated by fagulhaspt (see page 2 of this thread)

In the terminal, do this:

```
cd ~
mkdir lexmark
cd lexmark
```

**Either** download the drivers from [http://www.easy-share.com/1908438339/Z617.tar.gz]("http://www.easy-share.com/1908438339/Z617.tar.gz") (You will need to manually download the file in your browser, and wait a minute for the download button to appear. Save it in your lexmark folder.)

**Or** use this command in the terminal:

```
wget http://ompldr.org/vNjQ5ag/Z617.tar.gz
```

Extract the contents of the downloaded file Z617.tar.gz - it will create a directory "Z617" with 4 "deb" files - use this command in the terminal:

```
tar -zxvf Z617.tar.gz
```

To install each of the 4 "deb" files, enter these commands into the terminal in the following order (the order is important):

```
sudo dpkg -i Z617/libcupsys2_1.3.9-17ubuntu3.1_all.deb
sudo dpkg -i Z617/libstdc++5_3.3.6-17ubuntu1_i386.deb
sudo dpkg -i Z617/z600cups_1.0-2_i386.deb
sudo dpkg -i Z617/z600llpddk_2.0-2_i386.deb
```

Uncompress the file:

```
sudo gunzip /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
```

Now the drivers are installed, but we need to tell cups to use them for your Lexmark printer. Start up your printer and connect it to the computer.

Go to System-> Administration-> Printing and click Add.

Wait while the computer automatically searches for drivers. In the list there should appear a Lexmark option - select it and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen.

If the drivers were not automatically found, as happened to fagulhaspt in (K)ubuntu 10.04, then it will ask you to "Choose the Drivers" -> click "Provide PPD file", and select the file "/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd" (in the lexmark folder). Then click "Forward" and "Apply" on the next screen

Turn your printer off, wait a few seconds and turn it back on again (this is just to make sure there's nothing in the buffer to cause problems). 

Select the printer, right-click -> "Properties" -> "Printer options", and configure the "Media size" (to A4 in my case), the "Media Type" (to Plain Paper=normal paper, in my case) and any other option you see fit. Configure at least the "Media size" or the printing may be distorted.

And it should be all done and working now!

Try to print a test-page in the CUPS options, or open OpenOffice Writer to write something on a blank sheet and click "Print" :)

From now on, you only need to plug the printer to the computer, and you can "Print" normally to it :)

NOTES:
If you get an error message saying that the "printer could not execute a filter" then execute:

```
sudo chown -hR root:root /usr/lib/cups/filter
sudo chown -hR root:root /usr/lib/cups/backend
```

---

### Post by tiggsy on 2010-06-12
**I've left this here, even though the current revised version is shown above. Use that one, please.**

I originally tried the HOW TO I found [here]("http://ubuntuforums.org/showthread.php?t=49714"), which used to work in previous Ubuntu versions, but it didn't this time.

Even after trying to get round the "printer could not execute a filter" problem with:
```
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
```

I got just part of a page and then the printer stopped with a flashing light, which could not be cleared even by switching it off and on again.

I found these [instructions for Z605]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605") and am reproducing it here with extra notes for newbies.

Start by installing alien and libstdc++5. Open a terminal and type (or copy and paste) each of the following lines in turn:

```
sudo apt-get install alien
cd ~/Downloads
mkdir lexmark
cd lexmark
wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/
cd /usr/lib
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```

Download the drivers from [http://www.easy-share.com/1908438339/Z617.tar.gz]("http://www.easy-share.com/1908438339/Z617.tar.gz"). You will need to wait for a minute for the download button to appear. Save it in your lexmark folder.

Extract the 4 files to your lexmark folder, then doubleclick on each and select Install, in the following order:

libcupsys2_1.3.9-17ubuntu3.1_all.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
z600cups_1.0-2_i386.deb
z600llpddk_2.0-2_i386.deb

Then open a terminal and type/copy the following lines in turn: 

```
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```

Close the terminal. 

Go to System-> Administration-> Printing and click Add. Select your printer and click Forward. Once it has found the drivers, they will appear. Select Lexmark and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen. 

Turn your printer off, wait a few seconds and turn it back on again (this is just to make sure there's nothing in the buffer to cause problems). Then print a test page. 

Hope this helps.

PS. if you get an error message saying that the "printer could not execute a filter" then go up to the top of this post and execute the commands mentioned there.

---

### Post by K.Mandla on 2010-06-13
Similar threads merged.

---

### Post by divali on 2010-09-02
This worked for me using **Lucid** with my **Lexmark Z517** but, I used the **cups local web admin interface**, once I had installed all the drivers, at [http://localhost:631](http://localhost:631). When it asked me for a driver I gave it the PPD file which should be located in /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz once you have the above deb's installed.

So thanks, it has taken me ages to find the correct drivers after I upgraded to Lucid.

---

### Post by tiggsy on 2010-09-02
Exactly my experience. The old "how to" stopped working when I upgraded to Lucid, but after a lot of mucking about, I found the way through, and then I put it on here to help others, and in case I crashed and had to reinstall again - which happened a few days ago when my old Alienware died. :(

---

### Post by I, the Deceiver on 2010-11-07
I love you.
\\:D/

---

### Post by fagulhaspt on 2010-11-10
Thank you for your sharing tiggsy!! 

This made my Lexmark X1170 printer work with ubuntu 10.04 and kubuntu 10.04 after 2 years of disbelief!

---

### Post by InkyDinky on 2010-11-22
I'm guessing the initial statements "Install libstdc++.so.5
" are for amd x64 processors. My old 32bit laptop got the drivers working on Xubuntu 10.04 without those additional commands. I started with downloading and extracting the driver package. I got the Z705 to work but not the Z1300 :(

---

### Post by inearlygaveup on 2010-11-24
> **tiggsy said:**
> I originally tried the HOW TO I found [here]("http://ubuntuforums.org/showthread.php?t=49714"), which used to work in previous Ubuntu versions, but it didn't this time.


I found these [instructions for Z605]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605") and am reproducing it here with extra notes for newbies.

Start by installing alien and libstdc++5. Open a terminal and type (or copy and paste) each of the following lines in turn:

```
sudo apt-get install alien
cd ~/Downloads
mkdir lexmark
cd lexmark
wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/
cd /usr/lib
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```

Download the drivers from [http://www.easy-share.com/1908438339/Z617.tar.gz]("http://www.easy-share.com/1908438339/Z617.tar.gz"). You will need to wait for a minute for the download button to appear. Save it in your lexmark folder.

Extract the 4 files to your lexmark folder, then doubleclick on each and select Install, in the following order:

libcupsys2_1.3.9-17ubuntu3.1_all.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
z600cups_1.0-2_i386.deb
z600llpddk_2.0-2_i386.deb

Then open a terminal and type/copy the following lines in turn: 

```
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```

Close the terminal. 

Go to System-> Administration-> Printing and click Add. Select your printer and click Forward. Once it has found the drivers, they will appear. Select Lexmark and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen. 

Turn your printer off, wait a few seconds and turn it back on again (this is just to make sure there's nothing in the buffer to cause problems). Then print a test page. 

Hope this helps.

PS. if you get an error message saying that the "printer could not execute a filter" then go up to the top of this post and execute the commands mentioned there.

**Anyone know if this works with  Ubuntu 10.10 - the Maverick Meerkat**

---

### Post by fagulhaspt on 2010-11-30
> **InkyDinky said:**
> I'm guessing the initial statements "Install libstdc++.so.5
" are for amd x64 processors. My old 32bit laptop got the drivers working on Xubuntu 10.04 without those additional commands. I started with downloading and extracting the driver package. I got the Z705 to work but not the Z1300 :(

Hi InkyDinky, clarifying your thoughts - these instruction are for **32 bits** systems, not for 64bits.

I'll comment a little the "Install libstdc++.so.5" section:


```
#--- Install libstdc++.so.5
cd ~/Downloads
mkdir lexmark
cd lexmark
wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb
```
The above lines will download a 64bits .deb file.
This _64bits deb file will never be installed_, as we only need to copy some 32bits files from within it, not install it. 
Continue reading, I'll explain it further...

```
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
```
The above line, _will not install_ the deb file, it will extract the contents of the .deb file into directory "ia32-libs" (see "man dpkg" the "-x" option)
 
```
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/
```
The above line, will copy one file from the ia31-libs directory extracted into /usr/lib 
The file is a 32bits library "libstdc++.so.5.0.7", which is needed for the driver to work. NOTE: It *must* be this exact version of this library, because the drivers will only work with it. That's why we need to extract this file from a .deb package, simply because in this .deb package the "libstdc++.so.5.0.7" has the pretended version to work with the printer driver

```
sudo ln -s /usr/lib/libstdc++.so.5.0.7 /usr/lib/libstdc++.so.5
```
The above line makes an alias with another name to the same file.
It creates a symbolic link  pointing to the library file, but gives the link another name



Now to the second part:

> **InkyDinky said:**
> My old 32bit laptop got the drivers working on Xubuntu 10.04 without those additional commands. I started with downloading and extracting the driver package. I got the Z705 to work but not the Z1300

If more people can confirm that it works without executing the "#--- Install libstdc++.so.5" section, than we can change the resume

Cheers

[COLOR="SeaGreen"]UPDATE 2011/08/31: It seems that there is no need to "install alien" nor to "install libstdc++.so.5" as was once described, so that was removed from the instructions.
Also in the past I made a cleanup/resume of the original instructions of tigsy. But it happens that tiggsy and I agreed that it was better that those instructions to be left in the head of this thread, mantained by tiggsy. So I removed the previous resume instructions, and we now have a single source of information about how to install the drivers, and that is the post #1 mantained by tiggsy
All this to say that: 
  - *this* post is already outdated as the libstdc++.so.5 is not installed as was discussed in this post, and so you should make no case of this post
  - only follow the install instructions provided be tigssy in the post [#1]("http://ubuntuforums.org/showpost.php?p=9450026&postcount=1") of this thread. Those will be updated as needed with new info :)
[/COLOR]
Cheers

---

### Post by inearlygaveup on 2010-12-21
Thanks tiggsy & fagulhaspt worked like a charm on my Aspire 5100

---

### Post by fagulhaspt on 2011-01-06
Happy to help :)

---

### Post by tiggsy on 2011-02-21
Just checking in to say, I had to move computer yet again and these instructions still work. But with lucid. I don't have maverick.

Someone tell us if they get it to work with maverick, Please!

---

### Post by Travis13 on 2011-02-22
> **tiggsy said:**
> I originally tried the HOW TO I found [here]("http://ubuntuforums.org/showthread.php?t=49714"), which used to work in previous Ubuntu versions, but it didn't this time.

Even after trying to get round the "printer could not execute a filter" problem with:
```
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
```

I got just part of a page and then the printer stopped with a flashing light, which could not be cleared even by switching it off and on again.

I found these [instructions for Z605]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605") and am reproducing it here with extra notes for newbies.

Start by installing alien and libstdc++5. Open a terminal and type (or copy and paste) each of the following lines in turn:

```
sudo apt-get install alien
cd ~/Downloads
mkdir lexmark
cd lexmark
wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/
cd /usr/lib
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```

Download the drivers from [http://www.easy-share.com/1908438339/Z617.tar.gz]("http://www.easy-share.com/1908438339/Z617.tar.gz"). You will need to wait for a minute for the download button to appear. Save it in your lexmark folder.

Extract the 4 files to your lexmark folder, then doubleclick on each and select Install, in the following order:

libcupsys2_1.3.9-17ubuntu3.1_all.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
z600cups_1.0-2_i386.deb
z600llpddk_2.0-2_i386.deb

Then open a terminal and type/copy the following lines in turn: 

```
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```

Close the terminal. 

Go to System-> Administration-> Printing and click Add. Select your printer and click Forward. Once it has found the drivers, they will appear. Select Lexmark and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen. 

Turn your printer off, wait a few seconds and turn it back on again (this is just to make sure there's nothing in the buffer to cause problems). Then print a test page. 

Hope this helps.

PS. if you get an error message saying that the "printer could not execute a filter" then go up to the top of this post and execute the commands mentioned there.
This is what worked for me while trying to install my Lexmark X1185!! Thanks for the help!

---

### Post by inearlygaveup on 2011-02-26
> **tiggsy said:**
> I originally tried the HOW TO I found [here]("http://ubuntuforums.org/showthread.php?t=49714"), which used to work in previous Ubuntu versions, but it didn't this time.

Even after trying to get round the "printer could not execute a filter" problem with:
```
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
```

I got just part of a page and then the printer stopped with a flashing light, which could not be cleared even by switching it off and on again.

I found these [instructions for Z605]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605") and am reproducing it here with extra notes for newbies.

Start by installing alien and libstdc++5. Open a terminal and type (or copy and paste) each of the following lines in turn:

```
sudo apt-get install alien
cd ~/Downloads
mkdir lexmark
cd lexmark
wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/
cd /usr/lib
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```

Download the drivers from [http://www.easy-share.com/1908438339/Z617.tar.gz]("http://www.easy-share.com/1908438339/Z617.tar.gz"). You will need to wait for a minute for the download button to appear. Save it in your lexmark folder.

Extract the 4 files to your lexmark folder, then doubleclick on each and select Install, in the following order:

libcupsys2_1.3.9-17ubuntu3.1_all.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
z600cups_1.0-2_i386.deb
z600llpddk_2.0-2_i386.deb

Then open a terminal and type/copy the following lines in turn: 

```
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```

Close the terminal. 

Go to System-> Administration-> Printing and click Add. Select your printer and click Forward. Once it has found the drivers, they will appear. Select Lexmark and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen. 

Turn your printer off, wait a few seconds and turn it back on again (this is just to make sure there's nothing in the buffer to cause problems). Then print a test page. 

Hope this helps.

PS. if you get an error message saying that the "printer could not execute a filter" then go up to the top of this post and execute the commands mentioned there.

[B][SIZE="2"]Just to let everyone know that this guide worked on my 10.10 Maverick.
Except that the download would not work from easy-share.com 
so I got it from [http://ompldr.org/vNjQ5ag/Z617.tar.gz](http://ompldr.org/vNjQ5ag/Z617.tar.gz)

thanks again
:p[/SIZE][/B]

---

### Post by moody_mark on 2011-04-04
Hi folks

Working on a 10.10 system just fine thank you very much folks. We should add this to the help wiki pages I think as it probably works for many other lexmarks too? (possibly)

Note. I didnt install alien and used the wget link to download the drivers

```

wget http://ompldr.org/vNjQ5ag/Z617.tar.gz
```

THANKS UBUNTU FORUMS!

---

### Post by aadgj on 2011-07-09
No luck for me.  File ia32-libs_2.7ubuntu6.1_amd64.deb doesn't seem to be located at [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs) any more.  I tried the latest package there, but it didn't contain the libstdc++.so.5.0.7 file.  Which package should I wget?

---

### Post by LiM3 on 2011-08-07
> **aadgj said:**
> No luck for me.  File ia32-libs_2.7ubuntu6.1_amd64.deb doesn't seem to be located at [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs) any more.  I tried the latest package there, but it didn't contain the libstdc++.so.5.0.7 file.  Which package should I wget?

I'm having problems with this too.

---

### Post by tiggsy on 2011-08-07
I did a google search for libstdc++.so.5.0.7 and it directed me to:

[http://packages.debian.org/cgi-bin/search_contents.pl?word=libstdc%2B%2B.so&searchmode=searchfiles&case=insensitive&version=stable&arch=i386&prmdo=1]("http://packages.debian.org/cgi-bin/search_contents.pl?word=libstdc%2B%2B.so&searchmode=searchfiles&case=insensitive&version=stable&arch=i386&prmdo=1")

amongst other places. Looks as if it may be useful.

---

### Post by fagulhaspt on 2011-08-31
I've just updated the install-instructions, removing what I believe to be unnecessary sections ("alien install" and "libstdc++5" sections). 

With these changes, there is no more need to use the file "http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb" which is now in an invalid url

I've tested them myself, but would be nice if someone else reports back confirming that the instructions are complete and clear.

Those instructions are being mantained by tiggsy in the [#1 post]("http://ubuntuforums.org/showpost.php?p=9450026&postcount=1") of this thread

Hope it helps :)
And thanks again tiggsy - you putted the ball rolling :)

---

### Post by fagulhaspt on 2011-08-31
.

---

### Post by fagulhaspt on 2011-08-31
> **aadgj said:**
> No luck for me.  File ia32-libs_2.7ubuntu6.1_amd64.deb doesn't seem to be located at [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs) any more.  I tried the latest package there, but it didn't contain the libstdc++.so.5.0.7 file.  Which package should I wget?

> **LiM3 said:**
> I'm having problems with this too.

@aadgj and @LiM3: I've updated the install instructions, because it may be possible to install the driver without needing that missing file.

The instructions are published by tiggsy in the [#1 post]("http://ubuntuforums.org/showpost.php?p=9450026&postcount=1") 

Try again now and report back your success/failures - that way we can all learn together.

Cheers

---

### Post by tiggsy on 2011-08-31
Thanks fagulhaspt. You'll see I've posted the revised version (based on yours, with some extra explanations for newbies) at the head of this thread.

---

### Post by fagulhaspt on 2011-08-31
> **tiggsy said:**
> Thanks fagulhaspt. You'll see I've posted the revised version (based on yours, with some extra explanations for newbies) at the head of this thread.

Good - this way the thread gets clearer and more direct.
I've deleted from my posts the older-instructions-resumes, so that nobody gets confused.


tiggsy - [COLOR="Silver"][s][SIZE="1"]it would be nice if you also putted in that first post the ubuntu versions/printer models that were reported to work. I gathered some in my post [#7]("http://ubuntuforums.org/showpost.php?p=10099408&postcount=7") (when you do it, tell me and I'll remove them from my post to avoid duplicates)[/SIZE][/s][/COLOR] Ok, I think that we now got this much more organized for everyone :)

Well done :)


[SIZE="3"][COLOR="Blue"][B]Now all that anyone needs to do, is:
  - follow the instructions in the [#1 post]("http://ubuntuforums.org/showpost.php?p=9450026&postcount=1") of the thread.
  - report your success/failure indicating your ubuntu-version/printer-model[/B][/COLOR]
[/SIZE]

[SIZE="1"]Well, this looks ugly, but draws the attention :)[/SIZE]

---

### Post by tiggsy on 2011-08-31
@fagulhaspt

OK. I've added all the printers/os versions to the first post.

Would anyone who gets it working on another version of Ubuntu/another type of printer please gi'us chapter and verse. Ta.

---

### Post by aadgj on 2011-09-04
I just tried the new directions.  The printer seemed to install properly.  When I tried to print a test page the sheet slowly moved through the machine, but nothing printed.  It's probably just a toner issue.  No one's used this thing in a long time.

---

### Post by tiggsy on 2011-09-05
Most likely. Toner dries up just like cartridges. Or maybe it loses its charge or something (not sure how it works, but I seem to recall it's not the same as ink).

I put a brand new ink cartridge in my printer 2 days ago, printed 5 pages, and the next day it decided it had run out!

btw, can you tell us which printer this was? and confirm if you do manage to get a printout with new toner, please.

---

### Post by fagulhaspt on 2011-09-08
> **aadgj said:**
>  No one's used this thing in a long time.

I've used this method myself last week, in ubuntu 10.04 LTS, but more confirmations would reassure us.

aadgj, please tell us when you have your printer working, indicating the ubuntu version and printer model, and tiggsy will update the #1 post with that info, so other can benefit from it.

---

### Post by begsfg on 2011-09-15
Just installed for a Lexmark X1150, it worked like a charm. Thank you for the information and help.

---

### Post by fagulhaspt on 2011-10-09
@begsfg: So that we can keep track of the success/failure experiences, tell us what's your ubuntu version - ? ubuntu 11.04 ?

---

### Post by minotavrs on 2011-12-24
Thanks for the help... after ur instructions at the 1st post Lexmark x1150 works great at ubuntu 11.10 but there is a problem .. 

**NO ubuntu update at all **after installation of z600cups file!! 

The message i get is something like this [B]fix z600cups broken package update 
[/B]
and the only fix for get updates back is to run :
$ sudo apt-get install -f

after this unfortunately ubuntu 11.10 updates works again but **NOT the printer ....**
Do u have any solution for that?

thanks again

---

### Post by madman22 on 2012-01-12
Do I have to have the Lexmark X1170 be connected to computer when installing drivers?

When I go to Administrator > Printing and select Add > should I see Lexmark somewhere?

---

### Post by fagulhaspt on 2012-01-18
> **madman22 said:**
> Do I have to have the Lexmark X1170 be connected to computer when installing drivers?
No, you connect the printer after the drivers are installed
> **tiggsy said:**
> Now the drivers are installed, but we need to tell cups to use them for your Lexmark printer. Start up your printer and connect it to the computer.



> **madman22 said:**
> When I go to Administrator > Printing and select Add > should I see Lexmark somewhere?
Yes - read again the indications left in the first post
> **tiggsy said:**
> Go to System-> Administration-> Printing and click Add.

Wait while the computer automatically searches for drivers. In the list there should appear a Lexmark option - select it and click Forward, then Z600 (at the end), Forward. Then click Apply on the next screen.

---

### Post by fagulhaspt on 2012-01-18
> **minotavrs said:**
> Thanks for the help... after ur instructions at the 1st post Lexmark x1150 works great at ubuntu 11.10 but there is a problem .. 

**NO ubuntu update at all **after installation of z600cups file!! 

The message i get is something like this [B]fix z600cups broken package update 
[/B]
and the only fix for get updates back is to run :
$ sudo apt-get install -f

after this unfortunately ubuntu 11.10 updates works again but **NOT the printer ....**
Do u have any solution for that?

thanks again


To be honest, no, I did not had that error

If someone with some expertise around **apt** could throw some light on it, would be just great...

---

### Post by fagulhaspt on 2012-07-30
***Update for ubuntu 11.10*** (and possibly 12.xx, ...)

The existing procedure does not work for Ubuntu 11.10 Oneiric - it fails on the installation of libcupsys2_1.3.9-17ubuntu3.1_all.deb and libstdc++5_3.3.6-17ubuntu1_i386.deb, for what seems a conflict of version between the libcupsys2 that it tried to install, and an already existing "libcups2" package. 

```


paulo@lnxp:~$ mkdir lexmark
paulo@lnxp:~$ cd lexmark/


paulo@lnxp:~/lexmark$ wget http://ompldr.org/vNjQ5ag/Z617.tar.gz
--2012-07-30 14:56:48--  http://ompldr.org/vNjQ5ag/Z617.tar.gz
Resolving ompldr.org... 178.63.66.150
Connecting to ompldr.org|178.63.66.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4174049 (4.0M) [application/x-gzip]
Saving to: `Z617.tar.gz'

100%[======================================>] 4,174,049    613K/s   in 6.8s

2012-07-30 14:56:55 (601 KB/s) - `Z617.tar.gz' saved [4174049/4174049]



paulo@lnxp:~/lexmark$ tar -zxvf Z617.tar.gz
Z617/
Z617/z600llpddk_2.0-2_i386.deb
Z617/z600cups_1.0-2_i386.deb
Z617/libcupsys2_1.3.9-17ubuntu3.1_all.deb
Z617/libstdc++5_3.3.6-17ubuntu1_i386.deb



paulo@lnxp:~/lexmark$ sudo dpkg -i Z617/[COLOR="Red"]libcupsys2_1.3.9-17ubuntu3.1_all.deb[/COLOR]
[sudo] password for paulo:
Selecting previously deselected package libcupsys2.
dpkg: regarding .../libcupsys2_1.3.9-17ubuntu3.1_all.deb containing libcupsys2:
 [COLOR="red"]libcups2 conflicts with libcupsys2[/COLOR]
  libcupsys2 (version 1.3.9-17ubuntu3.1) is to be installed.
dpkg: error processing Z617/libcupsys2_1.3.9-17ubuntu3.1_all.deb (--install):
 conflicting packages - not installing libcupsys2
Errors were encountered while processing:
 Z617/libcupsys2_1.3.9-17ubuntu3.1_all.deb



paulo@lnxp:~/lexmark$ sudo dpkg -i Z617/[COLOR="Lime"]libstdc++5_3.3.6-17ubuntu1_i386.deb[/COLOR]
Selecting previously deselected package libstdc++5.
(Reading database ... 442872 files and directories currently installed.)
Unpacking libstdc++5 (from .../libstdc++5_3.3.6-17ubuntu1_i386.deb) ...
Setting up libstdc++5 (1:3.3.6-17ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



paulo@lnxp:~/lexmark$ sudo dpkg -i Z617/[COLOR="Red"]z600cups_1.0-2_i386.deb[/COLOR]
Selecting previously deselected package z600cups.
(Reading database ... 442879 files and directories currently installed.)
Unpacking z600cups (from Z617/z600cups_1.0-2_i386.deb) ...
dpkg: dependency problems prevent configuration of z600cups:
 z600cups depends on libcupsys2 (>= 1.2.7); however:
  [COLOR="red"]Package libcupsys2 is not installed.[/COLOR]
dpkg: error processing z600cups (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 z600cups


paulo@lnxp:~/lexmark$


```


I didnt want to break anything, so I left "libcups2" package unchanged (came by default with ubuntu), and googled for a more updated method of installing the Lexmark printer in ubuntu 11.10


I found [this resumed explanation]("http://angel-de-vicente.blogspot.com.es/2012/07/lexmark-x1190-with-ubuntu-1110-64-bits.html") (which is based from [this other info]("http://blog.rachaelbond.com/lexmark/")) and so got my printer Lexmark X1170 working in Ubuntu 11.10 :)


After trying-and-failing the above procedure for ubuntu 10.xx, I had to "undo" the errors from the failed attempt, and from then on, I just followed the instructions from the site above indicated, which I leave here for convenience and giving all the credit to the blog's author :)

The following commands, are the continuation after the previous failed attempt, which "undos" the failed install of z600cups and continues with the install
```


# => this is to undo of the previous failed attempt
sudo apt-get remove z600cups


# From now on, is just following the procedure from the refered blog
sudo apt-get install rpm

# No need to install sdtlibc++5 because I've already done it during the failed attempt
# However, it should be something like: 
#
# sudo apt-get install libstdc++5

cd ~
mkdir -p lexmark
cd lexmark
wget http://software.rachaelbond.com/CJLZ600LE-CUPS-1.0-1.TAR.gz
tar xzvf CJLZ600LE-CUPS-1.0-1.TAR.gz
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar xzvf install.tar.gz
sudo rpm --force-debian -ivh z600cups-1.0-1.i386.rpm z600llpddk-2.0-1.i386.rpm --nodeps
sudo service cups restart

```



Now connect your printer and turn it on, and open the printer configuration program:
NOTE: this program does not show up inside the applications menu (which should), so you have to launch it manually by typing the program name in a console:
```

system-config-printer

```

Now will open the program window for you to configure your printer:
[INDENT]  Main window:
    .Click Add button
    .see [img](http://postimage.org/image/s7vx4sofl/)

  Select Device:
    .Select Lexmark X1100
    .Forward
    .see [img](http://postimage.org/image/vsrso0sz5/)

  Choose Driver:
    .select "Select printed from database"
    .select "Lexmark"
    .Forward
    .see [img](http://postimage.org/image/v4iy52u9d/)

  Choose Driver:
    .Models select "Z600 v1.0-1" (my printer is a Lexmark X1170, but the driver name is "Z600 v1.0-1")
    .Forward
    .see [img](http://postimage.org/image/t18ixeugh/)

  Describe Printer:
    .This is not important - name your printer as you wish (office, or livingroom, or kids), or leave it as it is (as me)
    .Apply
    .see [img](http://postimage.org/image/bpcrppqcx/)
  
  Would you like to print a test page?
    .Click "Print Test Page"
    .your printer should start printing a colorfull test page. If not, then something is wrong, most probably the problem comes from the drivers installation in the console - check that to see if you can find any errors which might lead to your specific problem/solution (google it like "ubuntu lexmark printer <myerror>")
    .see [img](http://postimage.org/image/vl8r597e9/)

  Post-install - put your own settings:
    .Select the printer, right-click -> "Properties" -> "Printer options", and configure the "Media size" (to A4 in my case), the "Media Type" (to Plain Paper=normal paper, in my case) and any other option you see fit. Configure at least the "Media size" or the printing may be distorted.
    .OK
    .see [img](http://postimage.org/image/3z5zkko1d/)
    .see [img](http://postimage.org/image/9om84vu7l/)


And from now on, your printer should be working - urray :) !
If not, then something went not quite well as expected... google for the error/solution



Take a moment to think about this - this is linux, where the colaboration of motivated people over more than 20 years created a free and opensource operating system equal-or-better than commercial ones. It has its advantages and problems as any other, but excels with a vibrant community made of people who volunteer to support opensource culture and are willing to share/help as they can. Please share your own success or failures, so that others also learn from your own experience :)
This is what I hope it will happen with this post - help others in same situation :)


Also, if you are new to linux and a bit frustrated, don't dispair: you will notice that over time, the number of linux-problems is lesser and lesser, as more and more efforth is made from more people to make it easy to use, which reduces this kind of problems, and makes linux more "user-friendly" and less "hacker-only" :)


Cheers

---

### Post by fagulhaspt on 2012-08-09
In the [blog I mentioned in my previous post]("http://angel-de-vicente.blogspot.com.es/2012/07/lexmark-x1190-with-ubuntu-1110-64-bits.html"), it is also explained how to make the scanner work for Ubuntu 11.10, which made it work on my Lexmark X1170.


For convenience, I leave it here all resumed below, and in [this gist]("https://gist.github.com/3304160")

[B]Ubuntu 11.10, Lexmark X1170 scanner:
[/B]
```


# The fix is based on installing an older version of libsane and libsane-extras
# For more info, see [1] and [2]
#   [1] http://angel-de-vicente.blogspot.com.es/2012/07/lexmark-x1190-with-ubuntu-1110-64-bits.html
#   [2] https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475
#   [3] http://ubuntuforums.org/showpost.php?p=12159929&postcount=36
#
# To apply the fix, copy/paste the following in a terminal:

#   . Uninstall libsane + libsane-extras
sudo apt-get remove libsane libsane-extras

#   . Manually download and install the older version 1.0.21-9 of libsane and libsane-extras
cd
mkdir -p lexmark
cd lexmark
wget http://ftp.us.debian.org/debian/pool/main/s/sane-backends/libsane_1.0.21-9_i386.deb
wget http://ftp.us.debian.org/debian/pool/main/s/sane-backends-extras/libsane-extras_1.0.21.2_i386.deb
sudo dpkg -i libsane-extras_1.0.21.2_i386.deb
sudo dpkg -i libsane_1.0.21-9_i386.deb

#   . Tell APT to *pin* the libsane and libsane-extras to the 1.0.21-9 version, so that they do not get updated and stay fixed with this specific version
cat <<EOT | sudo tee -a /etc/apt/preferences.d/libsane
Package: libsane
Pin: version 1.0.21-9
Pin-Priority: 900
EOT

#   . Reinstall simple-scan (not in the blog, but I had to do it)
sudo apt-get install -y simple-scan

#   . Test and enjoy your scanner :)
simple-scan
#     NOTE: I had to go to Documents/Preferences 
#            Scan Source = LexmarkX110/rev.2C
#            Close
#
#     NOTE2: It takes a while to start scanning - just be patient and wait, or if so, close-and-reopen the program
#
#     NOTE3: You can launch the simple-scan from the menu/Graphics/Simple-scan

```


After rebooting (?why?) the scanner worked better :)


Share your success/failure

---

