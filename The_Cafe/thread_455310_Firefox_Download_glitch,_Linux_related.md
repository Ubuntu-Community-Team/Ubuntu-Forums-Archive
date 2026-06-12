---
title: "Firefox Download glitch, Linux related?"
date: 2007-05-26
forum: The Cafe
---

### Post by mlanza on 2007-05-26
Originally, I was a Windows user who occasionally booted to his Ubuntu partition.  However, as Ubuntu has progressed--and progressed it has!--I am now an Ubuntu user who occasionally boots to Windows.  On both platforms I run Firefox as my browser of choice.

One thing has been bugging me on Linux.  When I click a link to download something, it save a zero byte file of that name in my Downloads folder.  That is, it doesn't attempt to fully download the item I clicked on.  If I right click and choose "Save Link As" this works just fine.  What gives?  This is not an issue on Windows.

This is especially frustrating as some sites obfuscate the actual direct link to the target item.

Any ideas?  Is this a known Firefox bug or simply an improper configuration on my part?

Thanks.
Mario

---

### Post by FuturePilot on 2007-05-26
Does this happen all the time or is it just on certain sites? Can you give a link for us to test? Maybe try it out on the live CD and see if it does it on that too.

---

### Post by starcraft.man on 2007-05-26
> **mlanza said:**
> Originally, I was a Windows user who occasionally booted to his Ubuntu partition.  However, as Ubuntu has progressed--and progressed it has!--I am now an Ubuntu user who occasionally boots to Windows.  On both platforms I run Firefox as my browser of choice.

One thing has been bugging me on Linux.  When I click a link to download something, it save a zero byte file of that name in my Downloads folder.  That is, it doesn't attempt to fully download the item I clicked on.  If I right click and choose "Save Link As" this works just fine.  What gives?  This is not an issue on Windows.

This is especially frustrating as some sites obfuscate the actual direct link to the target item.

Any ideas?  Is this a known Firefox bug or simply an improper configuration on my part?

Thanks.
Mario

I've never had this, can you give us a link like suggested and I/we will test our browser. Never heard of this happening to anyone else >.>.

---

### Post by Polygon on 2007-05-26
try clearing your internet cache... this is more of a network/internet related issue, like your connection keeps dropping out or is losing packets or something.

---

### Post by mlanza on 2007-05-26
Actually, this does seem file type specific.  (FYI. I did clear my internet cache.)

When I click on an archive file (default radio button is "Open with 'Archive Manager'") so I switch to the "Save to Disk" option.  It creates the file on the disk but it is zero bytes.

Test site: [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)
Try downloading either of the GKrellM archives.

Also, I tried to download a gem from [http://www.hobocentral.net/blog/getting-started](http://www.hobocentral.net/blog/getting-started)

I wasn't even prompted, it just filled the screen with a bunch of gobbledygook.  If I saved that page it turns out I did have the file and could extract the gem.

It seems the issue is Firefox isn't properly determining what to do with different file types.  As I said, if I right click and immediately choose "Save Link As..." everything works fine.   More of a nuisance than anything else.

Thanks for looking into this.

By the way, I have Firefox 2.0.0.3.

---

### Post by june3474 on 2007-12-29
Did you download files into a vfat(or fat32) parition by any chance?
If that's the case, refer to the following link.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164)

---

### Post by the_darkside_986 on 2007-12-29
I get download glitches all the time on the Windows version of Firefox. But it usually occurs only when the network is weak. However, I never seem to have this trouble in Firefox in Ubuntu. But I use Epiphany most of the time now.

---

### Post by Lostincyberspace on 2007-12-29
I don't have the problem but I use downthemall most of the time though.

---

