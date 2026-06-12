---
title: "black areas in wine apps"
date: 2010-10-21
forum: Wine
---

### Post by RikoW on 2010-10-21
Dear all,

after upgrading my Ubuntu box from 10.04 to 10.10, I see black areas in office and other applications both in the menus and the main window (see attached screenshot for illustration).

The black color usually disappears when moving with the mouse over it, clicking it or switching the desktop. However, they are back for example the next time the menu is opened. Looks almost like some sort of reverse mode.

In the attached screenshot for example, the black area in the spreadsheet appears when refreshing the Pivot chart. Also visible in the open menu.

This appears on CXoffice 9.1.9, 9.2.0 Pro and for example MS Office 2007 installed via PlayOnLinux using wine 1.2RC. I altready tried all the usual tricks like re-install wine, the application even upgraded and downgraded the mesa drivers.

This is on a Dell Lat e4200 with an Intel Mobil 4 Graphics Adapter. I'm running out of ideas what to try and where to look. Anybody here has any suggestions?

Thanks,
        Riko

---

### Post by RikoW on 2010-10-22
Just for reference: looks like it's a bug in the intel drivers installed on Maverick.

I downgraded to the xorg version of Lucid and things are back to normal.

Thanks to the codeweavers.com support on helping me:

[INDENT][http://www.codeweavers.com/support/tickets/browse/?ticket_id=821079;list=6;ticket_level=2]("http://www.codeweavers.com/support/tickets/browse/?ticket_id=821079;list=6;ticket_level=2")[/INDENT]

The bug report is here:

[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=30157]("https://bugs.freedesktop.org/show_bug.cgi?id=30157")[/INDENT]

Maybe that's helpful for others,

               Riko

---

### Post by fredrik.lysholm on 2010-11-26
Hi, I have the exact same problem! (took me a while to find this thread, it turnes out that "wine graphics problem" etc were not a very precise description of my problem :D )

Do you know whether there have been any progress with this issue? If not, would you care to elaborate a bit on how I would downgrade my xorg version ?

Best regards, 
Fredrik

---

### Post by RikoW on 2010-11-26
Hi Fredrik,

I'm not aware of any fix, but except of looking at the bug report every one and then, I don't follow it up really. So far, there is not solution posted in the report.

Let me try to recall what I did to downgrade. Remember, that this is written down from memory ....:

[LIST=1]
[*] open synaptic and search for all xserver-xorg packages installed, remember which packages are installed and removed them

[*] open /etc/apt/sources.list and replaced "maverick" with "lucid" everywhere

[*] run ```
sudo apt-get update
``` to re-sync the package list

[*] open again synaptic, search again "xserver-xorg" and re-install the necessary packages which you removed in 1). I left out most the graphic drivers for chip-sets I don't have (see attachment). At this point, your xserver might just restart. Don't be alarmed.

[*] revert sources.list back to "maverick" and apt-get update

[*] start synaptic and lock version on the xserver packages 

[*] reboot or restart X (if that didn't already happen at point 4) and you should be in lucid land as far as the xserver goes -> done!
[/LIST]

I think, it's obvious that you can easily toast your system with that exercise, so be extra careful, think about what you do and cross all fingers and toes available :)

Report back after success/failure and update recipe where necessary.

Good luck,
         Riko

PS: of course, use at your own risk! :)

---

### Post by psygen on 2010-12-12
I have this same problem... but I solve the problem to follow the tip posted the link above. Just open regedit and added a key and a text value as below:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

source: [https://bugs.freedesktop.org/show_bug.cgi?id=30157](https://bugs.freedesktop.org/show_bug.cgi?id=30157) by Tomas Jura

---

### Post by arukaddp on 2011-06-14
Hello,

Sorry to revive old topics but I am having the same problem in Wine in Natty. 

As it turns out it is a problem of the Intel driver, and I am thinking about downgrading. 

Can someone tell me if the above solution worked/it is correct/there is any other method of downgrading?

I am not that comfortable with compiling yet, but I am willing to give it a try is needed.

Thank you!
Alex

---

### Post by psygen on 2011-06-20
Hello Alex,

with Natty I using Wine 1.3 and work for me without any additional configuration.

---

### Post by RikoW on 2011-06-22
Hi,

I still had the problem after upgrading to Natty. However, I don't use vanilla wine but Codeweavers CXoffice. The effect of black areas and thick lines was not so bad anymore and but still annoying (especially in Excel).

Using software rendering as mentioned above helped with the black areas, but made the ribbons almost unreadable.

So I reverted back to the lucid xserver-xorg packages following the (updated) recipe I posted above. So it does work.

However, after the downgrade, **Unity doesn't start anymore**. I see notifications, but no unity bar. Since so far I'm not very happy with Unity and still prefer the Classic Gnome it's not a big deal for me ...

Cheers,
          Riko

---

### Post by RikoW on 2011-07-06
Hooray!

Finally there is a fix for this problem - at least for Natty and Oneiric.

This bug was reported several times with separate ids, the essential one which gives also the fix is this one:

[HTML]https://bugs.freedesktop.org/show_bug.cgi?id=28798[/HTML]

The patch can be installed via ppa:

[HTML]https://launchpad.net/~smorar/+archive/bugfixes[/HTML]

Just do

```

sudo apt-add-repository ppa:smorar/bugfixes
sudo apt-get update
sudo apt-get upgrade
```

Logout and login to restart the xserver and Voila!

I did that on Natty and now everything is the way it should be.

Cheers,
           Riko

---

### Post by Risingfate on 2011-08-16
I followed the steps for the fix and still ended up with big black boxes everywhere :( Are there any other options?

> **RikoW said:**
> Hooray!

Finally there is a fix for this problem - at least for Natty and Oneiric.

This bug was reported several times with separate ids, the essential one which gives also the fix is this one:

[HTML]https://bugs.freedesktop.org/show_bug.cgi?id=28798[/HTML]The patch can be installed via ppa:

[HTML]https://launchpad.net/~smorar/+archive/bugfixes[/HTML]Just do

```

sudo apt-add-repository ppa:smorar/bugfixes
sudo apt-get update
sudo apt-get upgrade
```Logout and login to restart the xserver and Voila!

I did that on Natty and now everything is the way it should be.

Cheers,
           Riko

---

### Post by RikoW on 2011-08-17
Sorry to hear that!

Are you sure, you have the proper Intel driver installed. The version I'm running is:

                   2:2.14.0-4ubuntu7.2

Other than that, I'm afraid I can't help.

Good luck,

               Riko

---

### Post by tonic75 on 2011-09-07
Worket great on 11.04 64 bits with driver 2:2.14.0-4ubuntu7.2

Thanks!

---

