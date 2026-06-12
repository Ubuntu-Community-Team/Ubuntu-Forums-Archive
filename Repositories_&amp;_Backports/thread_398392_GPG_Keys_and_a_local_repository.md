---
title: "GPG Keys and a local repository"
date: 2007-03-31
forum: Repositories &amp; Backports
---

### Post by BobSongs on 2007-03-31
[FONT=Verdana]Would asking about gpg keys here be out of place? In particular: when one has a mirror of repositories on one's hard drive.

I asked under General but received no answer.
[/FONT]

---

### Post by BobSongs on 2007-04-11
[FONT=Verdana]Perhaps a word of explanation:

I've created a tutorial on how to download the Ubuntu repositories locally, make DVD ISOs and burn them. It's located [**here**]("http://ubuntuforums.org/showthread.php?t=352460").

An added feature is the ability to use this resource to install packages directly from one's own hard drive (**see Step 9**). It works but always returns an annoying warning saying the repositories might not be trustworthy.

What I'm looking for is that missing step to make **apt** feel completely assured these repositories are indeed trustworthy.

:D Hope that clarifies things.

Here's the output when I try to install something (problem text highlighted in red):

[/FONT]> [FONT=Courier New]sudo apt-get install apt-mirror
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
[/FONT][INDENT][FONT=Courier New]   apt-mirror[/FONT]
[/INDENT][FONT=Courier New] 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.6kB of archives.
After unpacking, 119kB of additional disk space will be used.
[COLOR=Red][B] WARNING: The following packages cannot be authenticated!
[/B][/COLOR] [/FONT][INDENT][COLOR=Red]**[FONT=Courier New]   apt-mirror[/FONT]**[/COLOR]
[/INDENT][FONT=Courier New] Install these packages without verification [y/N]? y[/FONT]


---

