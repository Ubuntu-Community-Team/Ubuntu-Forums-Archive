---
title: "Wish studio had same type installation as Ubuntu or Mint"
date: 2010-03-28
forum: Ubuntu Studio
---

### Post by wizarddrummer on 2010-03-28
Hi all,

I've spent some frustrating hours trying to partition a zeroed out hard drive in the very cryptic text based ununtu studio disk partitioning area.

Sudio is not going to win many converts with that "geeky" install program I can assure you.

Only BSD's install from a few years ago was worse.

In the regular, graphical, Ubuntu and Mint installation; when you created a partition ( manually) for /swap it was an option that could be selected from a list after you told it how much space you would allocate.

Once selected there were no other things (format, etc) that you could do to that partition. In the partitions list it appeared that /swap is a slightly different animal than / or /home because it did not have any descriptive attributes next to it.

The very cryptic and misleading text based partition manager in Studio does not have /swap in the list. If you select to enter a name manually, you are presented with the exact same options as / and /home which is not the case in the other two distros this was confusing.

Is there anyone working on a slightly more friendly installation program? You're all part of the same family, surely the skeleton source code for Mint's and Ubuntu's install could be tweaked to install studio.

---

### Post by cchhrriiss121212 on 2010-03-28
Studio was the first text install I'd ever used but I was able to set up my partitions OK, and I definitely made a successful swap partition with it. The option for swap is in the filesystem selection and not the one with /home in it. 
Having said that I did have to install it 3 times due to that mscorefonts thing.

But you should be happy to know you can easily install studio from a regular Ubuntu install. Search in synaptic for the studio metapackage that will install the rt kernel, the desktop, and all the programs for you. You will need to do a bit of configuration with setting the default kernel and jack though.

---

### Post by wizarddrummer on 2010-03-28
> **cchhrriiss121212 said:**
> Studio was the first text install I'd ever used but I was able to set up my partitions OK, and I definitely made a successful swap partition with it. The option for swap is in the filesystem selection and not the one with /home in it. 
Having said that I did have to install it 3 times due to that mscorefonts thing.

But you should be happy to know you can easily install studio from a regular Ubuntu install. Search in synaptic for the studio metapackage that will install the rt kernel, the desktop, and all the programs for you. You will need to do a bit of configuration with setting the default kernel and jack though.

really? That's good news. So I can install Ubuntu; find the metapackage and it's all auto magic?

Nice.
Thanks for that.

---

### Post by AutoStatic on 2010-03-29
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

