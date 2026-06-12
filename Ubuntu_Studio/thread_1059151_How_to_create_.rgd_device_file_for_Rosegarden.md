---
title: "How to create *.rgd device file for Rosegarden"
date: 2009-02-03
forum: Ubuntu Studio
---

### Post by grandoldie on 2009-02-03
I have Ubuntu 8.04 including Python v. 2.5 and Rosegarden 1.7.2 and a keyboard Yamaha YPT-200 for which I  try to make a * .rgd device definition file.
I followed the mini-HOWTO-instructions. I transformed the Voice List to YPT200.txt (ASCII) and and as alternative YPT200.csv . (The mini-HOWTO says CVS, but that is probably a typing error).
From the link in the instruction I downloaded txt2rgd.py and pasted that and YPT200.txt on the desktop. I opened the terminal window and wrote:

my@own-desktop:~$ txt2rgd.py YPT200.txt YPT200.rgd

but then followed:

bash: txt2rgd.py: command not found

What went wrong ?. Can anybody instruct the right syntax and way to do.

---

### Post by geoff123 on 2009-08-30
I'm probably a little late to reply, but here's what I do.  
Start with an example and manually type the .rgd using a text editor (kate or gedit). Here's the basic idea:

take example such this from this folder.  
/usr/share/apps/rosegarden/library/Roland-JV-1010.rgd

copy the file to your local directory to work on it.
such as ~/studio/rgds/newsynth.rgd

change the name to end with .gz (since it is a gz file with a rgd extension)
mv newsynth.rgd newsynth.rgd.gz

unzip the file (now its a plain text file with rgd extension)
gunzip newsynth.rgd.gz

open new text file in editor
kate newsynth.rgd

use the example to edit it for your synth.
then when done you need to gzip it, then change the name to .rgd.

also see.. 
[http://www.rosegardenmusic.com/resources/documents/rgd-HOWTO.shtml](http://www.rosegardenmusic.com/resources/documents/rgd-HOWTO.shtml)

Hope this helps.  Note these are not exact examples, you'll need to be comfortable with the command line to do this. Good Luck.

---

