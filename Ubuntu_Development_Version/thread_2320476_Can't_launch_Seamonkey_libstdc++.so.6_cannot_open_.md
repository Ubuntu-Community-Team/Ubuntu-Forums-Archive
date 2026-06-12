---
title: "Can't launch Seamonkey: libstdc++.so.6: cannot open shared object file"
date: 2016-04-14
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2016-04-14
Hi all,

16.04 LTS and trying to run Seamonkey 2.40 following the [instructions here]("http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux"). 

I open a terminal, cd to the correct directory and try to launch Seamonkey as per the info given on that link:

```
./seamonkey
```

... and I get this:
```

bucky@Studio:~/Downloads/seamonkey2/seamonkey$ ./seamonkey
./seamonkey: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

Any clues or 16.04 and Seamonkey are simply not happy together yet?

PS: I've never used Seamonkey so this wasn't working previously and now isn't. Just downloaded and can't launch.

---

### Post by QDR06VV9 on 2016-04-14
Runs Great on xenial here.
This has always worked for me....and I get updates as they come in(current)  [http://linuxpitstop.com/install-seamonkey-on-ubuntu/](http://linuxpitstop.com/install-seamonkey-on-ubuntu/)
Kind regards

---

### Post by sudodus on 2016-04-14
Maybe this link helps,

[Installing the light-weight web browser seamonkey](http://ubuntuforums.org/showthread.php?t=2281120)

---

### Post by Bucky Ball on 2016-04-14
> **runrickus said:**
> Runs Great on xenial here.
This has always worked for me....and I get updates as they come in(current)  [http://linuxpitstop.com/install-seamonkey-on-ubuntu/](http://linuxpitstop.com/install-seamonkey-on-ubuntu/)
Kind regards

This worked for me and thanks anyway sudodus. I needed to install genometools and that was it. (Forgot to mention previously, oversight on my part sorry, I'm using Xubuntu-core 16.04 so not everything installed that normally would be in a default Ubuntu). 

@sudodus: Are there any major differences between these two methods that make one better, or more advantageous, than the other? I am still going to be getting the updates? runrickus' link has slapped 'Mozilla Build of Seamonkey' in my apps menu and seem to be running fine.

PS: Was looking for something similar to Kompozer and couldn't get that to install. Seamonkey's 'Composer' is eerily similar and looks like it's going to work a treat for the simple stuff I need to do this year. :D

Tnx for the help.

---

### Post by sudodus on 2016-04-15
I don't remember the details. It's a long time since I did the testing and wrote that tutorial. If you are happy with your installation, fine :-)

Maybe, if I remember correctly, one method is installing for only one user, yourself, and the other installation is for all users. If you have only one user in your system, it would make no difference. I don't remember if there are differences concerning automatic upgrades.

---

### Post by vasa1 on 2016-04-15
> **Bucky Ball said:**
> This worked for me and thanks anyway sudodus. I needed to install genometools and that was it. ...
32-bit or 64-bit? IIRC, 64-bit is only a "contributed" build.

genometools? So you're into genome analysis? I've done my share of sequencing in the hazy past.

---

### Post by Bucky Ball on 2016-04-15
> **vasa1 said:**
> 32-bit or 64-bit? IIRC, 64-bit is only a "contributed" build.

genometools? So you're into genome analysis?

No. It was telling me I needed 'gt' when it wouldn't install. Told me to install the package 'genometools' so I did. Then it installed! 

I'm looking into doing the HTML pages with Libreoffice at the moment. Although Seamonkey is working for what I'm needing it to do, I get this error whenever I update:

```
W: http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/InRelease: Signature by key FBC0FA27F5D79B1F60A77837CCC158AFC1289A29 uses weak digest algorithm (SHA1)
```

Maybe I forgot to insert a key somewhere along the way or there is something wrong with key that is being used. Any thoughts? ... :-k

PS: I just ran the commands from the original link again, and this is and was the error I was getting from this first command:

```
bucky@Studio:~$ sudo echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list &gt; /dev/null
[3] 2861
gt: error: neither tool nor script specified; option -help lists possible tools

[3]+  Stopped                 sudo echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list
bash: /dev/null: Permission denied
```

I went ahead and ran the rest and it gave me Seamonkey anyhow, but probably the above error is behind the update error. (I ran this command without 'sudo' to start, but tried 'sudo' when I saw the 'Permission denied' message. Same error either way.)

PPS: Tnx for that sudodus. Looks like the PPA is attempting to update but getting the above error.

---

### Post by vasa1 on 2016-04-15
So have you the 32-bit or 64-bit version? I've only managed to install 64-bit Seamonkey on Lubuntu.

---

### Post by Bucky Ball on 2016-04-15
Whatever is installed by [this link]("http://linuxpitstop.com/install-seamonkey-on-ubuntu/") provided by runrickus in an earlier post. When I open Seamonkey and Help> About, I get this:

> You are currently on the release update channel.
See a list of contributors to the Mozilla Project.
Read the licensing information for this product.
Read the release notes for this version.
See the build configuration used for this version.
**User agent: Mozilla/5.0 (X11; Linux x86_64; rv:43.0) Gecko/20100101 Firefox/43.0 SeaMonkey/2.40**
Build identifier: 20160118183220

By the looks of the line in bold, it is the 64bit version, but frankly, no idea. It is Seamonkey 2.40.

---

### Post by QDR06VV9 on 2016-04-15
> **Bucky Ball said:**
> No. It was telling me I needed 'gt' when it wouldn't install. Told me to install the package 'genometools' so I did. Then it installed! 

I'm looking into doing the HTML pages with Libreoffice at the moment. Although Seamonkey is working for what I'm needing it to do, I get this error whenever I update:

```
W: http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/InRelease: Signature by key FBC0FA27F5D79B1F60A77837CCC158AFC1289A29 uses weak digest algorithm (SHA1)
```

Maybe I forgot to insert a key somewhere along the way or there is something wrong with key that is being used. Any thoughts? ... :-k

PS: I just ran the commands from the original link again, and this is and was the error I was getting from this first command:

```
bucky@Studio:~$ sudo echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list &gt; /dev/null
[3] 2861
gt: error: neither tool nor script specified; option -help lists possible tools

[3]+  Stopped                 sudo echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list
bash: /dev/null: Permission denied
```

I went ahead and ran the rest and it gave me Seamonkey anyhow, but probably the above error is behind the update error. (I ran this command without 'sudo' to start, but tried 'sudo' when I saw the 'Permission denied' message. Same error either way.)

PPS: Tnx for that sudodus. Looks like the PPA is attempting to update but getting the above error.

I have never used 'sudo' when using the echo command..
My method has been just this
```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list &gt; /dev/null
 
```
And then
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

```
Then "update" and install
```
sudo apt-get install seamonkey-mozilla-build

```
And yes the weak digest error is still there...I have seen they are working on that now.
Kind Regards

---

### Post by Bucky Ball on 2016-04-15
Ok, sorry to waste people's time but a future traveler may gain something from our discussion. Now it really is solved, in a round about way, by using Libreoffice for what I'm wanting to do.

Working on a uni submission due at the end of the year. I'm going to include audio/video linked directly from the text-based digital document. Uni requires a hard copy of text-based submission with any digital media on a disk (no USBs) as well as a digital version of the text-based submission as a PDF. So I was going to request permission to submit a self-contained html (can't be online) which links to video clips (which are essential to the research). 

Turns out if I put hyperlinks into the Libreoffice document and export as a PDF, the links work perfectly in the PDF also. This includes links to local video files. The link automatically opens them in VLC, and I'm presuming the same would happen with the default media player on a Windows or Mac machine. Yes, I'll have to be careful with the link details, but do-able once I get my head around it.

Thanks for the input. :)

---

### Post by vasa1 on 2016-04-15
Another way to check is to enter *about:buildconfig* in the address bar and then press *enter*. I see ```
about:buildconfig
Source

Built from http://hg.mozilla.org/releases/mozilla-release/rev/e8bb3550be0f344804a13cc7aa268b91a9154e93
Build platform
target
**x86_64**-unknown-linux-gnu
Build tools
Compiler 	Version 	Compiler flags
/usr/bin/ccache /builds/slave/rel-c-rel-**lnx64**-bld/build/gcc/bin/gcc 	4.7.3 	-Wall -Wempty-body -Wpointer-to-int-cast -Wsign-compare -Wtype-limits -Wno-unused -Wcast-align -std=gnu99 -fgnu89-inline -fno-strict-aliasing -ffunction-sections -fdata-sections -fno-math-errno -pthread -pipe
/usr/bin/ccache /builds/slave/rel-c-rel-**lnx64**-bld/build/gcc/bin/g++ 	4.7.3 	-Wall -Wempty-body -Woverloaded-virtual -Wsign-compare -Wwrite-strings -Wno-invalid-offsetof -Wcast-align -fno-exceptions -fno-strict-aliasing -fno-rtti -ffunction-sections -fdata-sections -fno-exceptions -fno-math-errno -std=gnu++0x -pthread -D_GLIBCXX_USE_CXX11_ABI=0 -pipe -DNDEBUG -DTRIMMED -g -freorder-blocks -Os -fomit-frame-pointer
Configure arguments

--enable-crashreporter --enable-release --enable-elf-hack --enable-stdcxx-compat --enable-default-toolkit=cairo-gtk2 --enable-application=suite --enable-optimize --enable-update-channel=release --enable-update-packaging --disable-debug --enable-tests --with-ccache=/usr/bin/ccache --with-external-source-dir=/builds/slave/rel-c-rel-**lnx64**-bld/build
```
I used [https://archive.mozilla.org/pub/mozilla.org/seamonkey/releases/2.40/contrib/seamonkey-2.40.en-US.linux-x86_64.tar.bz2](https://archive.mozilla.org/pub/mozilla.org/seamonkey/releases/2.40/contrib/seamonkey-2.40.en-US.linux-x86_64.tar.bz2) as the source and installed it locally.

---

### Post by Bucky Ball on 2016-04-15
Yep. Identical. ;)

---

