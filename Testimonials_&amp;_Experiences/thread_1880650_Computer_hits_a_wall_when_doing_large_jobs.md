---
title: "Computer hits a wall when doing large jobs"
date: 2011-11-14
forum: Testimonials &amp; Experiences
---

### Post by L a r r y on 2011-11-14
This computer seems to hit a brick wall and come to a crawl when using memory-intensive programs.  I would have to be quick to shut down Firefox as it started to quickly bog down and take forever to respond to my mouse clicks, otherwise I am sitting here for an hour trying to get something to move.

My flatbed scanner would be running under XSANE and it would just hit a wall and start to creep along, eventually completing the last half of the scan.

When it finally was done I would save the file, and it would be moving to about 40% then hit the wall and take an hour to finish saving.

Then I discovered swappiness.  Default setting is 60.  Maximum aggressive memory swapping would take place at swappiness 100, and memory swapping as absolutely needed takes place at swappiness 0.

Swappiness 10 allows everything on my computer to run to completion in scanning and saving, and even my Windows sound editor will do its job instead of just vanishing in the middle of a large wave file edit.  (I use Syntrillium Software's Cool Edit 96, a shareware I've used for 15 years, and it works well under Wine.)

You can Google search swappiness and get the [SwapFaq - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SwapFaq") for more details about how to check for and set the swappiness values.

Here is that pertinent copy from the FAQ:
> To check the swappiness value

```
cat /proc/sys/vm/swappiness

```
To change the swappiness value A temporary change (lost on reboot) with a swappiness value of 10 can be made with

```
sudo sysctl vm.swappiness=10

```
To make a change permanent, edit the configuration file with your favorite editor:

```
gksudo gedit /etc/sysctl.conf

```
Search for **_[FONT="Fixedsys"]vm.swappiness[/FONT]_** and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

```
vm.swappiness=10

```
Save the file and reboot.



I am thinking I may have some hard drive cabling or hdd controller issues on this computer that I should run into such slow response when I encounter swap. If I can swing it, I'm thinking of replacing this sonofagun.

---

### Post by oldos2er on 2011-11-14
Moved to T&E.

---

### Post by 3rdalbum on 2011-11-15
512mb is getting a bit on the low side these days for RAM. It gets cheaper and cheaper; why not buy a little more?

---

