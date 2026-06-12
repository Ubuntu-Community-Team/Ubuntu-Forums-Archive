---
title: "Amazon MP3 Downloader Released For Linux"
date: 2008-02-29
forum: The Cafe
---

### Post by Het Irv on 2008-02-29
It's here... I am about to switch to Linux to see how well it works.
Edit: They have support for mulitiple versions of Linux, including Gutsy Gibbon.   And it works without a hitch

Can someone try it with Hardy Heron to see if their are any issues?

---

### Post by fs3rp4 on 2008-02-29
> **Het Irv said:**
> It's here... I am about to switch to Linux to see how well it works.
Edit: They have support for mulitiple versions of Linux, including Gutsy Gibbon.   And it works without a hitch

Can someone try it with Hardy Heron to see if their are any issues?

Great! Big step.

Now they must open buy for other than USA...

---

### Post by Het Irv on 2008-02-29
Its US only?  oh.. well.. that sucks..

I hope they expand as well, I think no DRM and Native Linux Client are great selling points.

---

### Post by jcconnor on 2008-02-29
Don't know about Hardy compatibility but it works great with Feisty.  I was a beta tester for them on it and it was great.  i was impressed that they listened to folks that complained (me!!) and got something out that worked well.

The installation is a deb you can adjust where it saves files.  My only minor complaint is that while the ID3 tags contain the album art I wish they downloaded that into the folder with the tracks as well so other applications (and my player) had them automajically.  

Other than that it's great to see them supporting Linux.  Just one more way to differentiate themselves from iTunes.

John

---

### Post by derekr44 on 2008-02-29
This is cool.  Amazon has become my friend.

---

### Post by bash on 2008-02-29
Can you post some screens of it? Currently don't have a linux machine near :(

---

### Post by Het Irv on 2008-02-29
I just bought 4 albums with no problems, Firefox didn't mess with anything, I told it to open ".amz" with the program and it did so.  Amazon is getting alot of my money because of this, yay no DRM.
Here are some screenies

---

### Post by Sunflower1970 on 2008-02-29
I just tried this out. Works great. This will be how I buy some albums from now on. WTG Amazon! Thinking of us Linux Folks :)

---

### Post by firenurse4 on 2008-02-29
Too bad it doesn't support 64 bit. :(

---

### Post by dasunst3r on 2008-02-29
All right!  I'm going to buy an album now just to say "I agree with what you're doing -- keep up the good work!"  Also, time to uninstall iTunes from my Windows installation (dang piece of bloat!)

Here's to having a 64-bit version for those of you waiting.

---

### Post by igknighted on 2008-02-29
just use "dpkg -i --force-all package.deb" and try it.  If it still fails, use getlibs to finish getting any missing dependant libraries.

EDIT: Hmm, this could be a tough one to get all the 32bit libs for...

---

### Post by slightcrazed on 2008-03-01
Wow.....and, the thing...with the thing....Wow. 

I logged on this morning, took a look at my music collection and realized that it had some gaping holes, and decided on a quick google to see if I could find them anywhere. First hit, amazon. OK, I haven't shopped on Amazon for some time, but I load it up and sure enough, they sell MP3s. DRM FREE MP3s at that. Plus 1 for Amazon. But I knew, I mean I just knew, that as soon as I try to buy a song I'll be hit with the big 'you must be running windows XP' page. 

So I find the song I want, click on the 'buy' button, and I am presented with a page that says 'please choose which version of linux you want to download the amazon song download software for'.

That's when I fell out of my chair. Totally didn't see this coming. I was stunned..... I sat there for a minute, and waited for the page to flip over to a big ol' JUST KIDDING page or something. But it didn't. I installed the software, purchased the song (after I got back into my chair of course), and it's playing right now. And then I went back and bought like twenty more songs. 

Way to go Amazon. 

Wow.... :):):)

---

### Post by jaybstn on 2008-03-01
I hope the answer wont be obvious, so I wont feel foolish. I cant get the downloader program to work for me.  I downloaded and installed the 7.10 Ubuntu version and everything seemed to install ok (meaning no error messages). I downloaded the free song as instructed form the setup page (it downloads as a .amz file). The downloader program pops-up, and sits there, nothing happens, no mp3 downloads, and no error message pops-up either. I have tried this with a different free song from their site, and have the same problem. I have uninstalled it, trashed the .amazon file from my home folder and re installed it with the same results.  Am I missing a step? If anyone has any thoughts I'd greatly appreciate the help. 

Thanx

---

### Post by AusIV4 on 2008-03-01
I just got it installed on 64 bit Ubuntu. I used getlibs to install the missing libraries. I haven't tried it out, but it seems to be running fine.

[Edit]
I just tried it with a single song and it seems to work fine. Still can't speak for albums.

---

### Post by _avatar on 2008-03-01
> I hope the answer wont be obvious, so I wont feel foolish. I cant get the downloader program to work for me. I downloaded and installed the 7.10 Ubuntu version and everything seemed to install ok (meaning no error messages). I downloaded the free song as instructed form the setup page (it downloads as a .amz file). The downloader program pops-up, and sits there, nothing happens, no mp3 downloads, and no error message pops-up either. I have tried this with a different free song from their site, and have the same problem. I have uninstalled it, trashed the .amazon file from my home folder and re installed it with the same results. Am I missing a step? If anyone has any thoughts I'd greatly appreciate the help.


There appears to be a bug where the downloader can't open .amz that are marked with read-only permission. I just read a report that someone else experienced this same problem. Navigate to your /tmp directory, the .amz file should be there. Copy it to your home directory, and enable write permission. You can do this various ways, but with gnome right click the file -> Properties -> Permissions -> Owner Access -> Read and Write. You can also "chmod u+w file.amz" from the command line. Now try to open the file in the downloader again.

Out of curiosity, what web browser are you using?

---

### Post by jaybstn on 2008-03-01
Whoo hoo thanx :), that was the trick, however the free songs are no longer available. The important par was the track appeared in the program. Though I did have to manually open the file using the right click and' open with other application..' and a custom command of amazonmp3. Im using Swiftfox did that make the difference you think?

---

### Post by geoff123 on 2008-03-02
Thanks for the tip on changing the .amz file to read-write.

I found another way that worked for me which elimates the permission changing step. 
After hitting "continue' on the amazon website, the firefox box will open and chose 'save as' (which for me is my desktop).  Then manually load the files into amazonmp3 downloader.  

I've already downloaded one album and a few of the free songs.  Works great.

---

### Post by blueorder on 2008-03-03
Quick question, how did you guys install on Feisty? I only see a download for Gutsy.

Thanks in advanced...

---

### Post by Het Irv on 2008-03-04
I believe you can use the same files, try that and see, if it doesn't work, tell us.

---

### Post by blueorder on 2008-03-04
> **Het Irv said:**
> I believe you can use the same files, try that and see, if it doesn't work, tell us.

I tried it but it came back with dependency issues with libboost-*1.34.1

All the latest libraries in that family installed are version 1.33.1 in Feisty.

---

### Post by cooney on 2008-03-04
> **blueorder said:**
> I tried it but it came back with dependency issues with libboost-*1.34.1

All the latest libraries in that family installed are version 1.33.1 in Feisty.


I downloaded the debian (etchy?) .deb and it installed & worked GREAT with Feisty!

---

### Post by blueorder on 2008-03-06
> **cooney said:**
> I downloaded the debian (etchy?) .deb and it installed & worked GREAT with Feisty!

Thanks for the info. The Debian Etch file worked like a charm.

---

### Post by Het Irv on 2008-03-06
Good information to know.

---

### Post by chudder on 2008-05-07
> **jcconnor said:**
> Don't know about Hardy compatibility but it works great with Feisty.  I was a beta tester for them on it and it was great.  i was impressed that they listened to folks that complained (me!!) and got something out that worked well.

The installation is a deb you can adjust where it saves files.  My only minor complaint is that while the ID3 tags contain the album art I wish they downloaded that into the folder with the tracks as well so other applications (and my player) had them automajically.  

Other than that it's great to see them supporting Linux.  Just one more way to differentiate themselves from iTunes.

John

You got it to work on Feisty?  How so?  I tried installing it but it gave this message in the installation window:
"Error: Dependency not satisfiable: libboost-1.34.1" and the "Install" button is not able to be selected.
I looked in synaptic for that component but the version that's given is 1.33, what should I do?  

Thanx!

---

### Post by chudder on 2008-05-07
> **chudder said:**
> You got it to work on Feisty?  How so?  I tried installing it but it gave this message in the installation window:
"Error: Dependency not satisfiable: libboost-1.34.1" and the "Install" button is not able to be selected.
I looked in synaptic for that component but the version that's given is 1.33, what should I do?  

Thanx!

Oops, found the solution just above my post, I'll try that out and let you know if it did or didn't work.

---

### Post by chudder on 2008-05-07
I got it installed successfully after using the Etch package.  Thanx everyone!  I'll have to try it later to see if it actually works.

---

### Post by CRCarl on 2008-05-08
I was wowed by the pick your version of Linux down loader. Worked great in 7.10, Amazon gets 100% of my MP3 business from now on!

---

### Post by lespaul_rentals on 2008-05-08
DRM free, Linux client, cheaper than iTunes...Amazon rocks!

---

### Post by maniacmusician on 2008-05-08
> **jcconnor said:**
> 
The installation is a deb you can adjust where it saves files.  My only minor complaint is that while the ID3 tags contain the album art I wish they downloaded that into the folder with the tracks as well so other applications (and my player) had them automajically.  


If you have easytag installed, you can open it to the directory of the album, switch to the Pictures tab on the far right, and click the save button. That will export the image out of the tag and you can save it wherever you want.

It's a hassle and an extra step, and you might as well use google images, but it is what it is.

But this is definitely a great step.

---

### Post by taylonr on 2008-07-03
To get it up and running on hardy, I had to go to: [https://launchpad.net/ubuntu/hardy](https://launchpad.net/ubuntu/hardy)

I then downloaded libboost dev, thread, signals, date-time, and iostreams for version 1.34.  After I installed this, I did 'sudo dpkg -i --force-all' for the the amazon package.  It worked and I'm downloading an album right now.

Might be easier ways, but this one worked for me.

---

### Post by jesusprice on 2008-07-03
tried it and the amazon downloader installs and works perfectly

---

### Post by Languid Heap on 2008-10-04
I'm using Hardy Heron and have the Amazon MP3 Downloader working fine. I merely downloaded the "Ubuntu 7.10 Gutsy" package, opened it in Gdebi (which found 4 dependencies), and installed. No muss, no fuss -- and best of all, no DRM!

---

### Post by SuperSonic4 on 2008-10-04
> **fs3rp4 said:**
> Great! Big step.

Now they must open buy for other than USA...

Seconded, I'd buy music from Amazon UK if they sold it for download like the US version

---

### Post by doorknob60 on 2008-10-04
Hmm...no generic binary (Arch? Gentoo? what are we supposed to do?) AND no x86_64 downloads...not completely satisfied with this yet...

---

### Post by mrgnash on 2008-10-04
US only and no 64bit? Worthless.

---

### Post by hellion0 on 2008-10-04
It's a good start, I'll say that.

---

### Post by DoxaLogos on 2008-10-16
I got this working on Kubuntu 8.04 64-bit based on previous suggestion using getlibs

sudo dpkg -i --force-install amazonmp3.deb

cd /usr/bin

sudo getlibs amazonmp3

And, you're done.  It will fire right up.

---

### Post by Nico0020 on 2008-10-16
I started using this program about a month ago.  I LOVE it.  This program is actually what has me buying individual MP3s now.  Amazon has created a new MP3 customer.  

On another note, if you drink pepsi, you can use the codes on the caps to pay for Mp3s.  I have used so many "pepsi points" to get free mp3s from this.  

Take that iTunes!  Cheaper and DRM free!

---

### Post by david_lynch on 2008-10-16
> **firenurse4 said:**
> Too bad it doesn't support 64 bit. :(Won't it run on a 64-bit box?

---

### Post by Grexe on 2009-12-09
For those who don't want to manipulate DEBs for foreign architectures or use proprietary software just to download legally purchased MP3s, here's a promising (and working) open-source alternative:

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

Tried it and it worked flawlessly!

---

### Post by oldos2er on 2009-12-09
> **Grexe said:**
> For those who don't want to manipulate DEBs for foreign architectures or use proprietary software just to download legally purchased MP3s, here's a promising (and working) open-source alternative:

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

Tried it and it worked flawlessly!

 +1 for clamz, and apologies to those who dislike +1.

---

### Post by Grexe on 2009-12-10
I just got a reply from Amazon, they really recommend hacking 32bit-debs into a 64bit-system... well I guess you have to be thankful they provide a version for Linux at all...

The only minor complaint is that clamz does not yet download album covers, which would be important for me as I like to keep my songs on CDs too, for backup etc, and it should look and feel original, with cover and all:)

---

### Post by timhalo on 2010-01-02
> **Grexe said:**
> For those who don't want to manipulate DEBs for foreign architectures or use proprietary software just to download legally purchased MP3s, here's a promising (and working) open-source alternative:

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

Tried it and it worked flawlessly!

Thanks friend. Amazon selling an album for $5, vs. getting each song individually .99/ea. for $14 total. Saved some scratch!

---

