---
title: "Video DVDs not finalized by k3b ?"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by bedege on 2008-05-20
Hello

I've burned a DVD+R using k3b, from an iso image I created using k9copy. This DVD mounts and reads OK with Ubuntu:
- when inserted, it is mounted and has the usual video_ts directory
- the video plays fine with Totem

However, when I insert this DVD in a windows box, the systems complains that the disk is empty, while it also says it is 4.4 GB full. Of course Windows can not read nothing on it, but with vlc that reads the film ok.

What did I do wrong while burning with k3b ? Does it have to do with finalization ? If so, where is the right option to use ?

Thanks !

---

### Post by kelt65 on 2008-05-20
> **bedege said:**
> Hello

I've burned a DVD+R using k3b, from an iso image I created using k9copy. This DVD mounts and reads OK with Ubuntu:
- when inserted, it is mounted and has the usual video_ts directory
- the video plays fine with Totem


Is this a video DVD or a data DVD? (You say it has a video but it could just be a file)

Does a standard DVD player read the DVD?

I haven't had a problem with my DVD video copies made in K3B, excepting bad disks. 

If you burned it from an iso, well, there isn't a lot K3b has to do with that. It only calls cdrecord to burn it. Can you open that iso in windows?

---

### Post by bedege on 2008-05-21
That's a video DVD, created by k9copy.

I don't have a standard DVD player, just my computer ;-} Ubuntu reads the DVD ok but not windows.

Yes, I can read the iso file in Windows and read it directly using vlc for instance.

Any hint ?

---

### Post by bedege on 2008-05-22
Any idea ? Thanks

---

### Post by bedege on 2008-05-26
Hello

Sounds like nobody else has encountered this issue ?

---

### Post by lnogueir on 2008-05-28
Same issue! 

Help Please!

---

### Post by bedege on 2008-05-29
Hello

No solution yet. Sounds like it is an Ubuntu bug.

I advise you to look at the folowwing thread: [http://ubuntuforums.org/showthread.php?t=787299](http://ubuntuforums.org/showthread.php?t=787299)
which is more active than this one I created last week.

Cheers

---

### Post by stinger30au on 2008-05-29
when you whet to burn the files, did you select the right most tab when you select the burn icon.

the right tab says "misc"

in there is says multisession mode and in there is a few choices

auto, no, start, continue, finish

when working with vcd or dvd video always set it to *NO* multisession

this will ensure it gives you best compatability

---

### Post by bedege on 2008-05-29
Well, here is what I do
1. launch k3b
2. choose "burn a DVD from an iso file" in the Tools menu (not sure it is the exact same wording on your computer, as I use a French k3b...)
3. a pop-up windows appears where I can select the name/location of the iso file + only _one_ tab called "paramters" in which  "Burn mode" only proposes "Auto". This pop up window has a Start button to launch the burn process

I see no other tab that proposes choices about finalization or equivalent option.

Did I miss something ??

---

### Post by bedege on 2008-06-02
I made a second attempt using Gnome's Brasero.

The result is identical: Video DVD is ok with Ubuntu, but unrecognized by Windows.

Does it mean that the issue is not with the GUI I use (k3b or Brasero) but more with the burning software itself (growisofs ?).

Any hint ?

---

### Post by roberto.eiberle on 2008-06-02
I often burn Isoimages using brasero, never a problem, just don't burn at max speed. are you absolutely sure the problem is not windows? had problems with dvd running on ubuntu and any box around the house incl. PS2 except windows, some virus?

---

### Post by bedege on 2008-06-03
> **roberto.eiberle said:**
> I often burn Isoimages using brasero, never a problem, just don't burn at max speed. are you absolutely sure the problem is not windows? had problems with dvd running on ubuntu and any box around the house incl. PS2 except windows, some virus?

Hello Roberto

Of course, I can't rule out it's a Windows issue or not. The point is
- when I burn an iso file to a DVD+R using k3b or Brasero with Hardy, I cannot read the disc with Windows
- when I burn a similar iso file (also created by k9copy) using nero 7 under Windows, then everything is fine.
This make me lean towards a k3b/brasero/growisofs issue, don't you think ?
[B]
Have you lately burned iso image to a DVD with Hardy ? From what I read elsewhere, sound like it is an Hardy bug/feature (see [http://ubuntuforums.org/showthread.php?t=787299](http://ubuntuforums.org/showthread.php?t=787299) for instance).[/B]

Cheers

---

### Post by bedege on 2008-06-04
Hello

Some recent news about that thread: from other bugs that exist on Launchpad (see [233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942") and [219577]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/219577") for instance), it appears that it's more likely genisomimage 1.1.6 that is broken when creating Joliet-type iso files.

Looks like the iso image I made when I was using Gutsy are ok under Windows; now with Hardy and an updated genisoimage 1.1.6, Joliet compatibility is broken.

Solution might be to upgrade to genisoimage 1.1.7 or higher, and possibly recreate the iso images... Has anybody tried that with Hardy ?

Cheers

---

### Post by bedege on 2008-06-10
> **bedege said:**
> Hello

Some recent news about that thread: from other bugs that exist on Launchpad (see [233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942") and [219577]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/219577") for instance), it appears that it's more likely genisomimage 1.1.6 that is broken when creating Joliet-type iso files.

Looks like the iso image I made when I was using Gutsy are ok under Windows; now with Hardy and an updated genisoimage 1.1.6, Joliet compatibility is broken.

Solution might be to upgrade to genisoimage 1.1.7 or higher, and possibly recreate the iso images... Has anybody tried that with Hardy ?

Cheers

Well, I installed genisoimage 1.1.7.1 from a Debian package (not from cdrkit sources) and it does not solve the issue... I read that I should install the whole cdrkit package from sources. Does anybody know the difference between cdrkit and genisoimage; what other cdrkit tools k9copy/k3b use that might be broken in the 1.1.6 release installed by Hardy ?

Cheers

---

### Post by scorchedbysun on 2008-06-11
> **bedege said:**
> Well, I installed genisoimage 1.1.7.1 from a Debian package (not from cdrkit sources) and it does not solve the issue... I read that I should install the whole cdrkit package from sources. Does anybody know the difference between cdrkit and genisoimage; what other cdrkit tools k9copy/k3b use that might be broken in the 1.1.6 release installed by Hardy ?

Cheers

I ran across the same problem a few days back on my Kubuntu 8.04 computer, but I was on a deadline and had to burn to disc on a Mac (which isn't trouble-free in this respect either, but that's another story).

IAC, this morning I sat down to do something about it and immediately stumbled upon the bug and solution (install newer cdrkit) at [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942) . (BTW, I saw you posting there, bedege). A short compile later my DVD Video discs are burning correctly.

I already posted my comments about this to another thread on this forum: [http://ubuntuforums.org/showthread.php?t=787299&page=3](http://ubuntuforums.org/showthread.php?t=787299&page=3) .

genisoimage is part of the cdrkit, which also includes wodim and some other apps. After compiling and installing the newest version of cdrkit I opened K3b and there, under Settings -> Configure: K3b -> Programs (or something like that, my KDE is not running in English) it lists /usr/bin/wodim 1.1.6 and /usr/local/bin/wodim 1.1.8, /usr/bin/genisoimage 1.1.6 and /usr/local/bin/genisoimage 1.1.8 and /usr/bin/readom 1.1.6 and /usr/local/bin/readom 1.1.8. K3b had already automatically marked the newer versions for use.

So:
1. K3b seems to use three apps from the cdrkit package: wodim, genisoimage and readom. cdrkit might or might not include other programs, I don't know.
2. As said in the cdrkit's readme, it installs to /usr/local/bin, so it in no way erases or replaces the existsing packages, which are in /usr/bin.
3. K3b detects both versions and pre-selects the newer one (in my case, at least). I haven't tried it, but it gives you the option of selecting the older version, in case you don't like the newer one for some reason.

Oh, one more thing. I wasn't actually creating ISOs, I just dropped the contents of a VIDEO_TS folder (prepared by DeVeDe) into a K3b Video DVD project and it worked without any problems.

---

### Post by bedege on 2008-06-11
On another thread, people suggested to upgrade to genisoimage 1.1.8, or downgrade to 1.1.2... [see here for details]("http://ubuntuforums.org/showthread.php?p=5166175#post5166175")

Well, I just tried both solutions
- 1st, upgraded to genisoimage 1.1.8 (from the Debian package; too lasy to actually compile from sources... or more frankly not enough time!). Similar result as earlier: burned DVD unreadable by Windows. This is independent on the burning software/platform I use. The 1.1.8 created iso file is buggy, when I use k3b to burn it, or when I use nero under windows.
- 2nd, downgraded to genisoimage 1.1.2 from the Ubuntu repositories. Here, that **WORKS !**. Iso file generated with 1.1.2 gives correct AUDIO_TS and VIDEO_TS directories under windows, whatever soft I use to burn the DVD (k3b/linux or nero/windows). Then I can read the video with vlc under windows.

---

### Post by bedege on 2008-06-17
I just made a quick test last night. I was still puzzled why iso I created with gutsy were ok, when those created under hardy yelled DVDs that are unreadable under Windows.

So, I installed genisoimage 1.1.6-1ubuntu3 from gutsy: it works fine and creates iso that burn to DVD fine and are readable under Windows.

Thus, the bug lies somewhere in the patches between 1.1.6-1ubuntu3 and 1.1.6-1ubuntu6, that very release being part of Hardy.

That narrows down the search.

---

### Post by DaveQB on 2008-08-23
I have join in on this an say its not only an issue with making Video DVD's but data DVD's too.  I think its Wodim thats the problem.

See my thread here: [http://www.linuxquestions.org/questions/linux-desktop-74/burning-a-data-dvd-with-k3b-unreadable-in-windows-657045/](http://www.linuxquestions.org/questions/linux-desktop-74/burning-a-data-dvd-with-k3b-unreadable-in-windows-657045/)

I have booted up in Mandrive 2008.1 and burnt a few Data DVD's and no issue at all opening in other systems and OS's

Mandriva 2008.1 is using 1.1.7 genisoimage and wodim, I guess 1.1.7 cdrkit.


[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942/](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942/)

---

### Post by wandalalakers on 2008-09-11
This is another problem that I have discovered.
When installing genisoimage_1.1.6-1ubuntu3_i386.deb it removes remastersys from my hard drive. When I put remastersys back on using Adept Manager it puts genisoimage_1.1.6-1ubuntu6_i386.deb back on. When I put genisoimage_1.1.6-1ubuntu3_i386.deb back on and I check to see if remastersys is installed, I try to run it and it never opens.

When I run remastersys from the teriminal instead of the program menu I see one of the following errors:
"The following packages have unmet dependencies:
remastersys: Depends: mkisofs"

So, remastersys is one program that's affected when downgrading genisoimage_1.1.6-1ubuntu6_i386.deb to genisoimage_1.1.6-1ubuntu3_i386.deb.

I was able to view a dvd using windows now with genisoimage_1.1.6-1ubuntu3_i386.deb but now remastersys doesn't work.

---

