---
title: "VirtualBox Share folder"
date: 2011-10-11
forum: Virtualisation
---

### Post by tomhjp on 2011-10-11
Firstly, hi, nice to be here and I hope I'll be around a while as I'm new to Ubuntu but love it so far.

Now, I've got a weird problem with a shared folder in VirtualBox (4.0.4) running XP from a Ubuntu 11.04 host.

I've set up the share folder as /home/tom/Music and previously I was able to successfully add the whole of this folder to my iTunes library within the XP guest (this is so I can sync my iPhone). The only folder in this directory (/home/tom/Music) is iTunes which is basically just a copy/paste dump from my old Windows install before I switched to Ubuntu. The idea was that I would have this iTunes folder from which I would play all my music on Ubuntu, and then I could just link to this folder from the VirtualBox OS so that both my libraries for iPhone and PC would be in sync and I wouldn't have to replicate any music when I added stuff.

Unfortunately, after initially working, I can now no longer access the folder /home/tom/Music/iTunes from the XP guest. I get the error "X:\ is not accessible. The parameter is incorrect"
And although this prevents me from navigating to the folder and adding new music to my XP library, weirdly I am still able to play all my music from the X:\ drive (I have checked "get info..." and the path definitely goes through this folder I can't open X:\iTunes). I am also able to mount other directories (like my home directory) and explore everything there, though as soon as I try to open the iTunes folder in Music then it throws the same error.

Any ideas what is going on here? I'm wondering if it is a permission problem, but I am a total Linux newbie and am beyond being able to Google the answer.

Sorry this is a bit of a long post, wanted to try to include everything that was relevant.
Thanks

---

### Post by haqking on 2011-10-11
> **tomhjp said:**
> Firstly, hi, nice to be here and I hope I'll be around a while as I'm new to Ubuntu but love it so far.

Now, I've got a weird problem with a shared folder in VirtualBox (4.0.4) running XP from a Ubuntu 11.04 host.

I've set up the share folder as /home/tom/Music and previously I was able to successfully add the whole of this folder to my iTunes library within the XP guest (this is so I can sync my iPhone). The only folder in this directory (/home/tom/Music) is iTunes which is basically just a copy/paste dump from my old Windows install before I switched to Ubuntu. The idea was that I would have this iTunes folder from which I would play all my music on Ubuntu, and then I could just link to this folder from the VirtualBox OS so that both my libraries for iPhone and PC would be in sync and I wouldn't have to replicate any music when I added stuff.

Unfortunately, after initially working, I can now no longer access the folder /home/tom/Music/iTunes from the XP guest. I get the error "X:\ is not accessible. The parameter is incorrect"
And although this prevents me from navigating to the folder and adding new music to my XP library, weirdly I am still able to play all my music from the X:\ drive (I have checked "get info..." and the path definitely goes through this folder I can't open X:\iTunes). I am also able to mount other directories (like my home directory) and explore everything there, though as soon as I try to open the iTunes folder in Music then it throws the same error.

Any ideas what is going on here? I'm wondering if it is a permission problem, but I am a total Linux newbie and am beyond being able to Google the answer.

Sorry this is a bit of a long post, wanted to try to include everything that was relevant.
Thanks

you are running an old version of virtual box, i recommened upgrading to latest.

and also adding the extensions pack from same source

---

### Post by tomhjp on 2011-10-11
Thanks for the quick reply. I've now installed 4.1.4 and the extension pack, both from the VirtualBox website. Same problem as before unfortunately..

---

### Post by haqking on 2011-10-11
> **tomhjp said:**
> Thanks for the quick reply. I've now installed 4.1.4 and the extension pack, both from the VirtualBox website. Same problem as before unfortunately..

delete the x: drive and remove the connection

recreate the shared folder and remap it in your XP

see if that helps

---

### Post by tomhjp on 2011-10-11
I have tried disconnecting and then remapping the network drive but no joy. Interestingly while I was playing around in command prompt, I found that even though I wasn't able to look at what was in the iTunes folder in X:, I was still able to cd into the "iTunes Media" folder within and then generally do whatever inside (for example I was able to copy a file from X: into "X:\iTunes\iTunes Media"), I just still can't add files inside the iTunes folder as it seems to be some sort of block.

Is this behaviour symptomatic of anything obvious?

C:\Documents and Settings\tom>X:

X:\>dir
 Volume in drive X is VBOX_share
 Volume Serial Number is 0000-0805

 Directory of X:\

12/09/2011  23:38    <DIR>          iTunes
               0 File(s)          4,096 bytes
               1 Dir(s)  127,635,922,944 bytes free

X:\>cd iTunes

X:\iTunes>dir
 Volume in drive X is VBOX_share
 Volume Serial Number is 0000-0805

 Directory of X:\iTunes

File Not Found

X:\iTunes>cd "iTunes Media"

X:\iTunes\iTunes Media>dir
 Volume in drive X is VBOX_share
 Volume Serial Number is 0000-0805

 Directory of X:\iTunes\iTunes Media

11/09/2011  16:43    <DIR>          Podcasts
11/10/2011  23:19    <DIR>          Movies
11/10/2011  21:40    <DIR>          Music
11/09/2011  19:52    <DIR>          Ringtones
11/10/2011  23:19    <DIR>          TV Shows
21/12/2010  16:52    <DIR>          Automatically Add to iTunes
11/09/2011  19:53    <DIR>          Downloads
21/05/2011  16:01    <DIR>          Books
11/09/2011  12:02    <DIR>          Mobile Applications
               0 File(s)         45,056 bytes
               9 Dir(s)  127,636,000,768 bytes free

X:\iTunes\iTunes Media>

(Also I tried adding files to Automatically Add to iTunes but can't figure out how to get iTunes to register I put something there, however even if I did get that working it would still be a frustratingly clunky workaround, so I don't think I'll pursue that any further)

---

