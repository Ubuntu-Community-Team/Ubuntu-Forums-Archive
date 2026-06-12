---
title: "Need Help with Pkg Mgr Problem"
date: 2007-08-10
forum: Repositories &amp; Backports
---

### Post by MacDuff on 2007-08-10
I tried to install Mailwasher Pro on Ubuntu Feisty and it failed.  Now I cannot install any packages.  When I try I get the following message:

"E: The package mailwasher needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

To whom do I report this?  I contacted Firetrust and they told me that they have not had any similar problems reported.  They suggested doing a re-install of Ubuntu.

Is it REALLY necessary to do a complete re-install of Ubuntu?  It seems odd that if an application fails one would have to do a complete re-install of everything.  Is there not a way of deleting the erroneous file?

If I have to do a new Ubuntu Installation, can I do it over the existing install or does it re-partition the hard drive and leave the original installation?

I have asked this question of other threads and have not received any response.

Help Please.

---

### Post by kast on 2007-08-10
not sure you tried this

sudo apt-get autoclean

should clean any half install packages.

---

### Post by OzzyFrank on 2007-08-11
Hey Mac - it's the Ozzmeister again... but this time I can help! First I'll tackle Mailwasher Pro, then see if I can help re package manager.

One major piece of software for me to get into Ubuntu was a spam filter that could actually bounce back spam. I tried looking for something like my Mailwasher Pro, and there are scripts around, but guys like us want one with an easy GUI. I found the Linux version of Mailwasher Pro, then realised upon install that it is a 30 day trial (then you have to pay for it).

But guess what?? My Mailwasher Pro from Windows works ABSOLUTELY FINE in Ubuntu under Wine!!!!!!! I was getting Thunderbird and Evolution to leave mail on the server so I could bounce back the spam when in Windows, but now try not to even go online in the rare times I am in Windows.

Now, I'm assuming you have a Windows version, as you probably wouldn't have been ready to pay for a Linux one if you hadn't come to rely on it in Windows. Now, with Wine there is no rule: sometimes you need to install the Windows software, other times it is as easy as copying over the folder from Windows. I think i did do an install, then just copied over all the filters I had created; Mailwasher Pro then opened looking exactly like its Windows counterpart, with all my custom filters and email accounts ready to go! Only one abnormality, and that is only when closing the program: one of those "fatal exception" type error messages from Windowsland pops up twice, so I have to click OK 2 times before once more clicking the program's exit button (then it closes). A very minor annoyance, and the program doesn't sometimes crash like in Windows!

The other issue... had a similar thing with stupid Adobe acrobat reader trying to install (why I bothered when PDF support is already in Ubuntu I couldn't tell you, hehe...). Finally went into Synaptic, hunted for it, and uninstalled it. How did you install it? If it was actually via commandline, try the opposite, like **sudo apt-get remove mailwasher-pro** (replace with the proper package name).

As for reinstalltion of your operating system? God, if I had a dollar for every company that has told me to reinstall Windows to get their software working... hehe... this is known as a "cop-out", and all companies do this. And I can tell you from personal experience, that of friends, then later of clients, reinstalling your whole OS will still not get that one piece of trouble software or hardware (drivers) happening... and if you rang the company and told them it still isn't working, they'll just tell you to try reinstalling again, as obviously something is still wrong with your new Windows install if their program isn't working! So NEVER listen to rubbish like that, and even tell support staff to give you a real answer, not the age-old cop-out of "reinstall your OS" (when I am forced to contact software/hardware companies, I actually end my first email to them with something like "... and PLEASE don't ask me to reinstall my whole OS, as besides the fact that we all know this won't do anything but waste a lot of my time, it is actually embarrassing for both of us: for you to have to say this, and for me to have to listen to it.").

Hope some of this has been of help, Mac!

---

