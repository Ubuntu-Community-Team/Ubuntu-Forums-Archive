---
title: "Reiser4"
date: 2004-12-31
forum: The Cafe
---

### Post by Ozitraveller on 2004-12-31
I'm interested to know whether anyone has Reiser4 installed?

---

### Post by zeroK on 2005-01-01
[QUOTE=Ozitraveller]I'm interested to know whether anyone has Reiser4 installed?[/QUOTE]
 I had it on my laptop (which I now moved to Ubuntu) and still have it on my desktop. While I had no problems with it until now on the desktop, it was quite a pain on the laptop. The HDD of the laptop isn't really the fastest and you feel it even more with Reiser4. Saving things for example in VIM can takes ages :-( No I have XFS and the system feels much faster (sure, no really data journaling but at least faster ;-) )

---

### Post by CowPie on 2005-01-01
[QUOTE=Ozitraveller]I'm interested to know whether anyone has Reiser4 installed?[/QUOTE]
 I know jdong does ;) I would do it but I don't want to reformat and lose all my perfect settings....

---

### Post by Lovechild on 2005-01-01
I have used Reiser4 for a very long time on test machines, since my love-sources kernel tree was a test tree for Reiser4 prior to -mm inclusion.

It still doesn't run on anything but x86, it has design flaws (races, deadlocks, dataloss), it's slower than ext3 for many operations. All in all it's not really as great as Hans Reiser makes it out to be, but it has a very interesting plugin system I imagine one could have fun with.

I hardly think it will make vanilla, at least not in the current form, it simply doesn't cut it.

---

### Post by jdong on 2005-01-01
I am running reiser4 on Ubuntu Warty, with cko kernels (currently 2.6.10-cko1, previously 2.6.9-cko3) and reiser4progs backports (version 1.0.3).

It runs flawlessly, and the performance never fails to amaze me.


The Kanotix LiveCD was very helpful in the whole process, as it has kernel support for reiser4.

---

### Post by nemin on 2005-01-01
[QUOTE=Lovechild]It still doesn't run on anything but x86, it has design flaws (races, deadlocks, dataloss), it's slower than ext3 for many operations. All in all it's not really as great as Hans Reiser makes it out to be, but it has a very interesting plugin system I imagine one could have fun with.[/QUOTE]
hmm, this surprises me a bit. Linux Magazine was quite positive about Reiser4 in the october issue. I've never used Reiser4, so I can't talk about own experiences. I consider using Reiser4 so can anyone tell me a bit such "design flaws" and lack of performance?

---

### Post by jdong on 2005-01-01
Reiser4 is a weird beast... On 99% of tasks, it knocks its competitors dead, however, I've seen a few tasks (like APT dependency tree building) where reiser4 seems slightly slower than ext3/reiserfs.

As far as stability, there were a few sporadic hangs I've gotten with 2.6.7 and 2.6.8.1-mm*. With the 2.6.9 and 2.6.10 trees, I've yet to experience any trouble.

---

### Post by Ozitraveller on 2005-01-01
Is there likelyhood that we will see it in Ubuntu post Hoary?

---

### Post by Lovechild on 2005-01-01
[QUOTE=Ozitraveller]Is there likelyhood that we will see it in Ubuntu post Hoary?[/QUOTE]

If some version of it goes into vanilla then yes, baring the licensing issues are worked out (last I heard debian-legal had taken to a clause in Hans's "interpitation" of the GPL).

Then I think you can count on Debian and Ubuntu supporting it, but as it stands I don't think it will have a shot, on amd64 e.g. there's at least one reproducable dataloss bug which won't get fixed any time soon, since namesys refuses to get an AMD64 test machine.. in fact on anything but x86 Reiser4 doesn't run, period. This is a problem due to arch support in distros like Ubuntu, and technical advances in private homes - more and more people are simply getting AMD64 machines and they expect them to work.

Not to mention the wild ideas in some parts of Reiser4, like the metadata handling, of which there is heavy debate is even a good idea, and the fact that it doesn't run 4k stacks. But really to understand the technical issues with Reiser4 you should search LKML, especially VFS guru Al Viro's postings are good. I can also recommend Linux Weekly News' coverage of the Reiser4 threads, those should also be search able (*plug* buy a subscription to lwn.net, it's cheap and provides good coverage of the Linux world - support your starving linux journalists *plug*)

---

### Post by butters on 2005-01-01
I have Gentoo running love-sources 2.6.9 with reiser4 on both root and /home.  I want to switch to Ubuntu because my parents are sick of waiting for things to compile.  At first, I thought this was going to be really easy since /home is on a separate partition and I can just reformat root for Ubuntu.  However, it doesn't appear as if the lastest iteration of hoary has support for reiser4 in the installer.

Is the installer going to be able to handle the fact that I have a preexisting /home on reiser4 that I need to keep?  Has anyone had any experience with integrating a reiser4 /home with ubuntu after installation (with a custom kernel of course)?  Is reiser4progs in the hoary package tree?

I have had the Ubuntu installer crap out with some slightly exotic mount setups in the past (like mounting a fat32 data partition on /home/someuser/data for example).  I don't hold out any hope for running ubuntu with reiser4 root, but how about this reiser4 /home?

---

### Post by HiddenWolf on 2005-01-01
I've just moved my /home from / to a seperate partition on another harddisk.

there was no pain at all really. It took some time, but it worked.

I made a /temp directory and copied /home into it.
I deleted /home
I changed etc/fstab to piont /dev/hdb4 (in my case) to /home
I rebooted, then went into failsafe-terminal

copied /temp/home to /home
chown -R user /home 
chmod -R 771 /home  and I could boot again.

A bit of a tricky procedure, but hey. It was fun. :-)

---

