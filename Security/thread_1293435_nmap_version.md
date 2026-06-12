---
title: "nmap version"
date: 2009-10-17
forum: Security
---

### Post by Viking007 on 2009-10-17
Hi everyone,

I have 2 really "not so smart" questions.....

(1) I currently have nmap 4.53 (that's the latest I have on my synaptic list)...and every time I use the nmap command I get an error:  rpcinfo.nse is not a file....aborting script. Is there a reason for that happening as it didn't happen the last time I used it?

(2) Also, I know that the latest version is 5.0....so I'm wondering how do I install a legit updated version of nmap when synaptic or repo list does not show anything other that the 4.53 version I have?


I will really appreciate your help...Thanks

p.s. Ubuntu Rocks:guitar:

---

### Post by __p1n__ on 2009-10-17
1) rpcinfo.nse is one of the default scripts that come with nmap.  It's possible that the file is corrupted or inaccessible. The default location for is in /usr/local/share/nmap/scripts so check there.

2) go to [http://nmap.org/book/inst-source.html](http://nmap.org/book/inst-source.html) and follow the instructions there.  Nmap will work the best if you compile it yourself on your machine and yes, this will give you nmap 5.0.

---

### Post by Viking007 on 2009-10-17
Thanks _P1n_

I checked the folders you mentioned and can't find that file (Duh!).....any reasons for that, cause I'm using the synaptic packet manager to install it so shouldn't that file be already included?

I also appreciate your tip on compiling it myself but is there a link showing how to compile it or if you don't mind telling me how it is done?

Thanks once again!

---

### Post by cariboo on 2009-10-17
You better try again, because the scripts are in /usr/share/nmap/scripts, note the spelling.

---

### Post by Viking007 on 2009-10-17
I've actually looked into the right folder and it seriously does not exist....To be precise I see 41 scripts and rpcinfo.nse is not one of them....is there something I should be worried about?? as nmap 4.53 is installed using the synaptic package manager!

Thanks!

---

### Post by cariboo on 2009-10-18
I'm running Karmic which has nmap v 5.0, that may be why I have the script in /usr/share/namp/scripts.

If you want version 5.0 you can aleays download it from [here]("http://packages.ubuntu.com/search?keywords=nmap&searchon=names&suite=karmic&section=all"). You will also have to download and install the dependencies.

---

### Post by Viking007 on 2009-10-18
Thanks, Cariboo907....will certainly do that!

---

