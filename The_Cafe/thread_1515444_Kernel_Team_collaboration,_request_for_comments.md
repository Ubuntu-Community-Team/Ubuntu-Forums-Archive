---
title: "Kernel Team collaboration, request for comments"
date: 2010-06-22
forum: The Cafe
---

### Post by matthew on 2010-06-22
Hi, everyone. I'm following up on a conversation from UDS with members of the Ubuntu Kernel Team. One of the team members (and a Canonical employee), Jeremy Foshee, is leading their effort to make the wiki information about the kernel up to date as well as clearer and more complete than ever. They would also like to make it welcoming for forums members to use as a way to prevent the spread of incorrect information while making quality information easily accessible to our community.

Jeremy's new documentation will be here: [https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)

He is just starting the major overhaul of the information and invited us to participate by giving Jeremy feedback on how to make it as useful as possible.

Here are some questions to get the discussion going, but please don't feel like you need to limit comment(s) to these. Anything you think would be helpful in making the best kernel information available to forum members would be welcome. I will say, however, that it is not possible for the kernel devs to spend time on the forums answering questions and so on. They are all amazing and want to help, but they have a lot of demands on their time already. However, Jeremy has already volunteered to be available whenever he is on IRC for anyone to ask him any kernel related question, so we have a direct line to him when questions come up that are not answered in the upcoming new wiki documentation. This alone is a wonderful thing for which we should be quite thankful and I can get his contact information to everyone soon. So, on to some discussion starter questions. Feel free to bring up your own or contribute thoughts on any of these.

-What sort of information do we find forum members seeking with regards to kernel issues?

-What do we think people would like to know but don't know how to ask?

We can be as precise (e.g. "What do we expect to happen with btrfs and the kernel in the Maverick development cycle?") or as general (e.g. "Is there ever a reason for an Ubuntu user to compile her own kernel? When/why? or if not, why not?") as we like.

I've met Jeremy and the rest of the team, and I think this is a collaborative effort that will benefit both them and us and I hope you guys/gals think so too.

---

### Post by xebian on 2010-06-22
The podcast is 404 -not found

---

### Post by matthew on 2010-06-22
> **xebian said:**
> The podcast is 404 -not found

Oh, so it is. I guess that episode has been taken down for some reason. I'll edit the first post.

---

### Post by juancarlospaco on 2010-06-24
*Real Time Kernels and the Kernel PPA maybe...*

---

### Post by matthew on 2010-06-24
> **juancarlospaco said:**
> *Real Time Kernels and the Kernel PPA maybe...*

Thanks. I'm guessing you would like information about installing and using them along with a description of what RT kernels are and how they differ from the standard kernel as well as some commentary and description for the Kernel PPA and why/when/if/how it should be used. Is that correct?

---

### Post by juancarlospaco on 2010-06-25
Not me, 
but the people/clients i deal with on day to day basis, you are correct.


Also consider a link explaining the tipical:
*"Why i have so many Kernels on Boot Menu"*

A link to info about Grub, nothing to do with Kernel, 
but... anyways the users, think/ask on that way.

---

### Post by matthew on 2010-06-25
Excellent. Thank you.

---

### Post by vredley on 2010-06-26
A section explaining how to remove old kernels (and the advisability of doing so) would be great for people with limited disk space.

---

### Post by castrojo on 2010-06-27
I think a section on linux-backports-modules would be an important addition for people running an LTS but newer hardware, I ran into this problem today with a newer laptop and was pulling my hair out until I remembered that we have that.

---

### Post by NightwishFan on 2010-06-27
I agree. I helped a lady with her sound card that would not work and that was then solution. Personally I was saved from pulling my own hair out on 9.10 since the atk9k wireless driver was utterly broken in .31 but fixed by .32. Whoever thought of backports was an excellent edition to the team. :)

---

### Post by goseph on 2010-06-27
> **matthew said:**
> (e.g. "What do we expect to happen with btrfs and the kernel in the Maverick development cycle?") or as general (e.g. "Is there ever a reason for an Ubuntu user to compile her own kernel? When/why? or if not, why not?") as we like.


Actually, I'd love to know the answer to both of these!

Number 2 especially relates to my unresolved dilemma here where I ask about the advisability of compiling my own 2.6.35 kernel with a patch (on release) to get the Radeon power management that might solve all my overheating problems.

([http://ubuntuforums.org/showthread.php?p=9519716#post9519716](http://ubuntuforums.org/showthread.php?p=9519716#post9519716))

---

### Post by matthew on 2010-06-30
I have submitted the suggestions mentioned so far to the Kernel Team. I will leave this thread open for a few more days to give anyone who hasn't yet commented and wants to a chance to express their ideas. If you have been waiting, now is the time to jump in. :)

---

### Post by MaxIBoy on 2010-06-30
I personally compile all my own kernels. The main reasons why I do this are:

[LIST]
[*]Better settings for desktop interactivity (1000 Hz tickrate, tickless, preemptable, etc.)
[*]Optimizations for my CPU family (above and beyond the standard i686 optimizations.)
[*]Con Kolivas patchset (BFS, etc.)
[*]Get rid of built in ALSA/OSS3 support so I can use OSS4 instead.
[*]More-recent kernel releases (including release candidates.)
[/LIST]
My question is, are there plans to maintain versions of the kernel with any of those modifications within the repos? I can understand the rationale for not keeping up with new kernel releases, but especially the first three bullet points deserve consideration as special kernel versions in the repos. Along with better support for OSS4 within Ubuntu, that would go a long way toward eliminating the need for me to compile my own kernels (a chore I'd love to get rid of.) Bleeding-edge kernels aren't a dealbreaker.

I know this sounds more like a feature request than strictly a request for better documentation (as I already know how to do all of this stuff myself,) but there are a lot of users who I think could benefit from these modifications, and a streamlined procedure for it plus documentation on the topic would help them.

---

### Post by NightwishFan on 2010-06-30
It is probably too many kernels to manage many with specific optimizations. Though for Lucid and beyond there is a (64-bit only) preempt kernel for low latency needs. Perhaps specific note could be made of the advantages/uses of these. Recent kernels are already available as mainline applied with Ubuntu patches. Perhaps more convienient how/why for mainline kernels as well.

---

### Post by kio_http on 2010-07-30
The general users experience issues mainly related to laptop ACPI functions and FN buttons that require kernel configuring and fiddling with the kernel and what is linked to it.

Other than that I see no reason for many people to be even bothered with an OS kernel. Most Windows users don't even know what a kernel is. Windows NT is unquestionably a good kernel as general users are able to use the OS without the need to bother about the kernel and configuring it.

---

### Post by gnomeuser on 2010-08-02
As many of us know certain very common cases in the desktop can lead to long stalls. However work is progressingin this issue and I would like to know if this is being intended for a Lucid backport.

[http://lkml.org/lkml/2010/8/1/40](http://lkml.org/lkml/2010/8/1/40)

Similarly, the root of such issues seems to be that we as users see "poor performance" and are unable to describe it fully. Is there a plan to work on documentation to increase the usefulness of such reports?

---

### Post by saphil on 2010-08-20
> **vredley said:**
> A section explaining how to remove old kernels (and the advisability of doing so) would be great for people with limited disk space.
 
```
sudo aptitude autoclean
```
 will remove all of them, safely

---

### Post by matthew on 2010-08-20
I'm going to unstick and close this thread and will post a new one when the Kernel Team has their wiki pages ready.

Thanks for the input everyone!

---

