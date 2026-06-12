---
title: "Creative opens up its Linux X-Fi driver"
date: 2008-11-08
forum: The Cafe
---

### Post by Bungo Pony on 2008-11-08
It's about bloody time!

[http://www.theinquirer.net/gb/inquirer/news/2008/11/07/creative-opens-linux-driver](http://www.theinquirer.net/gb/inquirer/news/2008/11/07/creative-opens-linux-driver)

==================================================

IT CAME OUT yesterday that Creative Labs has thrown in the towel on its Soundblaster X-Fi driver for Linux and released the source code under the GNU General Public Licence (GPL) version 2.

The binary driver Creative initially released for its rearchitected X-Fi sound card technology was simply horrible. It was released extremely late, riddled with so many severe bugs that it was effectively unusable, for quite a while supported only 64-bit Linux, and was lacking any Advanced Linux Sound Architecture (ALSA) support.

The company struggled to provide a decent Linux driver for the Soundblaster X-Fi line for over two years without much success.

It promised Linux support in June 2006, projecting at the time that it would release the binary driver in the second quarter of 2007 and promising X-Fi would have full ALSA, OpenAL 1.1 and Environmental Audio Extensions (EAX) support.

Alas, it was not to be. Creative admitted in May 2007 that the development effort required to support Microsoft Vista had forced it to postpone development of the X-Fi Linux driver.

Creative finally came out with a Soundblaster X-Fi Linux driver of sorts in September 2007, but that was disappointing to say the least. Not only was it binary-only &#8211; which meant Free Software purists wouldn't use it &#8211; but it supported only 64-bit Linux.

One had to wonder, what was Creative thinking, that perhaps only Linux users running 64-bit software on massive web and database servers and HPC workstations loaded up with more than 4GB of RAM would have Soundblaster X-Fi cards?

The binary X-Fi driver also required an obsolete version of the GCC libraries and didn't run well or at all on many popular Linux distributions.

However, last February Creative provided some X-Fi source headers and documentation to 4Front Technologies, enabling it to produce an X-Fi driver for the Linux Open Sound System (OSS). That effort was at least partially successful, though 4Front's OSS driver had its share of bugs and other problems, and it still didn't support ALSA, which is the dominant Linux sound processing regime used in many of the most popular distributions.

Then Creative tried again in April, at last delivering a 32-bit X-Fi binary driver, albeit in a tentative beta release. But the status of Creative's X-Fi support of Linux was still abysmal, more than two years after the first cards were sold and over a year after Creative Labs had released its initial Soundblaster X-Fi driver for Linux.

A single Novell developer started work on porting 4Front's OSS X-Fi driver to ALSA, but that lone developer didn't even have any Soundblaster X-Fi hardware to work with and the project obviously lacked sufficient resources to handle such an ambitious software effort.

But now Creative Labs has released all the source code to its Soundblaster X-Fi driver for Linux under the GPLv2 free software licence.

Rather than being seen as Creative suddenly seeing the light about the advantages of open sauce software development, it's more likely that the company simply threw up its hands, saying in effect that if Linux users want an X-Fi driver that really works properly, they can just jolly well get together and write it themselves.

Which a few itchy Linux coders surely will do.

The company also might have anticipated that revisions to its software drivers needed to support Windows 7 (aka Windows ME II SP1.a) could distract its developers for a while.

Creative Labs' XFiDrv 1.00 driver, which consists of 13,000 lines of source code, supports the full Soundblaster X-Fi line, including XtremeMusic, XtremeGamer, Fatal1ty, Platinum, Elite Pro, and Titanium series sound cards. It's supposedly capable of handling ALSA PCM playback, ALSA recording and ALSA mixing, but doesn't yet support external I/O modules.

The announcement was made on the Creative Labs Forums and the full source-code is available for download from its support area as file XFiDrv_Linux_Public_US_1.00.tar.gz.

The released driver reportedly still has a few bugs, but many eyes should quickly fix those and, whatever its motivations might have been, Creative Labs deserves applause for finally doing the right thing. µ

---

