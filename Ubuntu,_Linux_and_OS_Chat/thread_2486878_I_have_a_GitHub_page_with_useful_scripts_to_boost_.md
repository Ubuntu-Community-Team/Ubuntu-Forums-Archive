---
title: "I have a GitHub page with useful scripts to boost productivity"
date: 2023-05-15
forum: Ubuntu, Linux and OS Chat
---

### Post by slyfox1186 on 2023-05-15
I made a GitHub repo to be a convienient place where people could install the latest version of popular packages by sourcing the latest versions from their official websites (usually their official GitHub repo).

APT is a cool thing but most of the time it doesn't have the latest version of whatever package you are installing and I am trying to change that by this repo I created.

Most often you can install the latest versions using a single command line that can be run in any terminal that supports BASH.

I havn't found a lot of traffic and I was hoping that some of you would take a look.

FYI This is MOSTLY targeted for Ubuntu 22.04 but some of these scripts might work fine for other versions.

Some examples of packages that you can autoinstall the latest versions of are
[LIST=1]
[*]Curl
[*]CMake
[*]FFmpeg
[*]ImageMagick
[*]GParted with all the addons included (like btrfs wich is not available unless you install the dev package)
[*]7-zip
[*]Tilix (Advanced terminal and good replacment for the default gnome)
[*]WSL2 kernal
[*]Squid Proxy Server
[*]Media players (Multipe to choose from)
[*]Many other useful scripts that boost productivity.
[/LIST]
If you think this repo is useful please take a second to show me some love by starring the repository. It would help me stay motivated to continue making things easily accessible for others all located in one place.

Thank you for taking time to read this post. Cheers.

[https://github.com/slyfox1186/script-repo/]("https://github.com/slyfox1186/script-repo/tree/main")

---

### Post by TheFu on 2023-05-15
There are times when the latest version of a package is a good idea.  This is one of the reasons why PPAs exist.  PPAs integrate into APT, so people don't need to do anything special to get the latest versions of X, Y, Z other than the normal 'apt upgrade' process.

There are times when new is the enemy of stable too.

I skimmed some of the instructions.  The ssh key stuff is using sudo, which shouldn't be needed for regular users to run 2 commands. Do people really need a script to run these two commands?
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
Heck, just add them as aliases, if you like.  No matter, different people like to work in many different ways.  I just like to avoid extra layers that complicate things.

However, I'd love to have a version of ffmpeg that has the m8u3 patch to allow handling of the DISCONTINUITY error many of those streams create.  I think is known as the EXT-X-DISCONTINUITY issue in RFC-8216.  There are other parts.

---

### Post by slyfox1186 on 2023-05-15
Good comment. Thanks for your feedback. I know PPA's exist and they are a great tool. Maybe I need to rethink my goals regarding that. Perhaps make PPA's myself.

I will work on FFMPEG m38u's addon library support and post back if and when I get it up and working.

Cheers.

---

### Post by TheFu on 2023-05-16
> **slyfox1186 said:**
> I will work on FFMPEG m38u's addon library support and post back if and when I get it up and working.

It is a specific type of stream that ffmpeg doesn't handle related to RFC-8216.  I've seen patches for it.  The ffmpeg project has a need to make things that always work, so because the existing patches don't handle everything, they are unwilling to make those changes as part of the project.  It isn't just m8u3 streams ... it is about the stream content that ffmpeg dumps as EXT-X-DISCONTINUITY errors.   

I suspect if it were easy, someone would have done this already.  Heck, if it was just a recompile with a little patch and most other ffmpeg stuff still worked, I'd have done it for my itch.

---

