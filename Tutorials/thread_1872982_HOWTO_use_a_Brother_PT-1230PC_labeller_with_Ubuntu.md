---
title: "HOWTO: use a Brother PT-1230PC labeller with Ubuntu"
date: 2011-10-31
forum: Tutorials
---

### Post by Fraoch on 2011-10-31
Google is your friend here - I googled "Brother PT-1230PC Linux" and the second link to come up was this:

[http://apz.fi/blabel/](http://apz.fi/blabel/)

Executive summary: Brother does not provide a Linux driver but this program works well for me in 11.10.  Brother's Linux drivers for labellers are [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html") - they usually provide excellent Linux support but the PT-1230PC is absent from this list.  Doesn't matter, B-Label works just fine!

Install the dependencies using:

```
sudo apt-get install libgtk2-perl libgtk2-gladexml-perl libgd-gd2-perl
```

apt-get will tell you if you already have these and install the missing ones.

Insert the tape and batteries into the printer, plug in the USB cable and turn it on.  Ubuntu will recognize the printer but can't find drivers for it.  Don't panic, just open CUPS by typing:

```
localhost:631
```

into your web browser, click "Adding Printers and Classes", "Add Printer" - you may then have to supply your user name and password.  The PT-1230PC should appear under "Local printers", select it and continue.  The next page with the printer name and model should be filled in for you, modify it if you like and continue.  On the next page, instead of "Brother", choose "Other Manufacturer", "Generic text-only printer" as the B-Label page instructs.  CUPS should then tell you the printer has been successfully added.

Then extract the blabel.zip file into a folder (I used "Home" - "Programs") and double-click the "blabel" file.

One note of caution - do not use 72 point Sans.  It only printed the last two characters and stopped.  72 point is too large anyway, the characters are cut off top and bottom.  I verified this twice.  40 point Sans worked fine though.  I'm not sure how large you can get it, the labeller only comes with a sample tape and replacement tapes are quite expensive so I didn't experiment around.  I e-mailed the developer about this.

Happy labelling!

---

### Post by Fraoch on 2011-11-01
> **Fraoch said:**
> One note of caution - do not use 72 point Sans.  It only printed the last two characters and stopped.  72 point is too large anyway, the characters are cut off top and bottom.  I verified this twice.  40 point Sans worked fine though.  I'm not sure how large you can get it, the labeller only comes with a sample tape and replacement tapes are quite expensive so I didn't experiment around.  I e-mailed the developer about this.

And the developer responded quite quickly:

[quote=Ari Sovijärvi]You're not the only one to hit that problem. It's not actually about the font size, but a specific pattern on a single line. After some experimentation, I've come to the conclusion that it's a firmware bug in the printer itself, the data I'm sending is valid. Changing the font size just by one point (you can type in "71" in the font dialog) will usually get past it.[/quote]

So there you go!

---

### Post by sean4u on 2013-06-13
blabel is a nice little application. I added a --fromfile command line argument to it to get around the between-label feed issue for a job that needed hundreds of labels. It allows you to (for example) create one big image composed of lots of little labels and print that as a single job. I'd never edited Perl before today, but it seems to work!

[http://firtl.com/2013/06/14/brother-pt-1230pc-on-ubuntu-linux/](http://firtl.com/2013/06/14/brother-pt-1230pc-on-ubuntu-linux/)

---

### Post by Fraoch on 2013-06-14
> **sean4u said:**
> blabel is a nice little application. I added a --fromfile command line argument to it to get around the between-label feed issue for a job that needed hundreds of labels. It allows you to (for example) create one big image composed of lots of little labels and print that as a single job. I'd never edited Perl before today, but it seems to work!

[http://firtl.com/2013/06/14/brother-pt-1230pc-on-ubuntu-linux/](http://firtl.com/2013/06/14/brother-pt-1230pc-on-ubuntu-linux/)

Neat idea.  Have you e-mailed the original developer about this?

BTW I had a little program hiccup when I upgraded to 13.04...I tried this program out and nothing happened when I pressed the print button, so I (stupidly) pressed the print button a few more times.  I think I then turned it off, unplugged it, plugged it in again and turned the printer on - then it promptly printed 4 labels off the rapidly-dwindling sample tape that was still in the machine.:roll:  So yeah, it does work, don't keep pressing the print button because Ubuntu caches the print requests.

---

### Post by sean4u on 2013-07-12
> **Fraoch said:**
> Neat idea.  Have you e-mailed the original developer about this?

BTW I had a little program hiccup when I upgraded to 13.04...I tried this program out and nothing happened when I pressed the print button, so I (stupidly) pressed the print button a few more times.  I think I then turned it off, unplugged it, plugged it in again and turned the printer on - then it promptly printed 4 labels off the rapidly-dwindling sample tape that was still in the machine.:roll:  So yeah, it does work, don't keep pressing the print button because Ubuntu caches the print requests.

I sent a patch and Ari replied, so maybe it'll appear in a later version. I also had the bad print queue experience while I was testing my code: it wouldn't have been so bad if I hadn't checked on the price of printer tape first!

---

