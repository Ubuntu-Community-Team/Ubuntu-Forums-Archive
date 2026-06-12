---
title: "Running BleachBit as Root?"
date: 2011-06-25
forum: Security
---

### Post by cybrsaylr on 2011-06-25
Have used BleachBit on earlier Ubuntu versions. BleachBit does a great job of cleaning out the just files that build up over time. When BleachBit was installed there are usually two entries to use: 
regular BleachBit 
BleachBit as root.

When I installed BleachBit in Natty only regular BleachBit shows up. Ran it and there was a pile of junk to delete but the root files were highlighted in red and could not be deleted unless BleachBit is run as root.

So how do you get the capability to run BleachBit as root again? 
Synaptic only shows one entry of BleachBit to install.

---

### Post by oldos2er on 2011-06-25
```
gksu bleachbit
```

---

### Post by cybrsaylr on 2011-06-25
oldos2er,

Put your code in terminal and got this output and error:
> rr@rr-Studio-XPS-8000:~$ gksu bleachbit
info: starting BleachBit version 0.8.7
debug: makedirs(/root/.config/bleachbit)
debug: chown(/root/.config/bleachbit, uid=1000)
  File "/usr/share/bleachbit/bleachbit/Cleaner.py", line 44, in <module>
    import Special
  File "/usr/share/bleachbit/bleachbit/Special.py", line 27, in <module>
    from Options import options
  File "/usr/share/bleachbit/bleachbit/Options.py", line 246, in <module>
    options = Options()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 44, in __init__
    self.restore()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 149, in restore
    self.set_list('shred_drives', Unix.guess_overwrite_paths())
  File "/usr/share/bleachbit/bleachbit/Options.py", line 195, in set_list
    self.__flush()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 50, in __flush
    General.makedirs(Common.options_dir)
  File "/usr/share/bleachbit/bleachbit/General.py", line 120, in makedirs
    chownself(path)
  File "/usr/share/bleachbit/bleachbit/General.py", line 76, in chownself
    assert(path.find('/root') != 0)
AssertionError


What happened, or did I do something wrong?

---

### Post by doas777 on 2011-06-25
I've heard numberous places that Bleachbit should never be run as root (though I have done so many times without apparent issues.)

perhaps someone can clue us both in to why it is not recommended, and perhaps whether that capability was disabled at some point.

---

### Post by cybrsaylr on 2011-06-25
> **doas777 said:**
> I've heard numberous places that Bleachbit should never be run as root (though I have done so many times without apparent issues.)
Agree and have done the same many times with Karmic.

With Karmic, there were two options after it was installed:

Bleachbit
Bleachbit as root

Now with Natty the 'Bleachbit as root' option is missing.

---

### Post by doas777 on 2011-06-25
I'm still on lucid so...

---

### Post by jerrrys on 2011-06-25
thats strange, i have BB as root in 11.10

---

### Post by cybrsaylr on 2011-06-25
I stayed on Karmic till early this month when I went to Natty, because Karmic was running so great, at least for me. 

Ran Lucid and Maverick on other PCs but still preferred Karmic. Then they sent out notices saying Karmic was no longer being supported so I went to Natty.

IMHO Karmic ran better than Natty, that I have been using almost a full month now and have 'adjusted' to Unity.

---

### Post by cybrsaylr on 2011-06-25
> **jerrrys said:**
> thats strange, i have BB as root in 11.10

When I installed BB on Karmic with Synaptic both options were present.
With Natty only one option of BB installs with Synaptic and BB as root is missing.

---

### Post by jerrrys on 2011-06-25
to be sure, go to /user/share/applications.  may not of made it to your menu

---

### Post by cybrsaylr on 2011-06-25
> **jerrrys said:**
> to be sure, go to /user/share/applications.  may not of made it to your menu

Bingo!

That is where it is listed.

However when I try to open BleachBit (as root) I get this popup:

> There was an error launching the application.

Regular BleachBit opens fine from /user/share/applications.

---

### Post by jerrrys on 2011-06-25
reinstall, see if you get lucky

---

### Post by cybrsaylr on 2011-06-26
> **jerrrys said:**
> reinstall, see if you get lucky

Just tried doing that twice with no luck.

Both Synaptic and Ubuntu Software Center installed BleachBit 0.8.7

However I notice Ubuntu Software Center shows version 0.8.7-1 (bleachbit), which has a different screenshot look than the BleachBit 0.8.7 version I just installed and had before.

Not sure if this matters...

---

### Post by jerrrys on 2011-06-26
and not that it matters, but i am running 8.8.1

also noticed that at BB site the download for 11o4 is 0.8.8.1

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

---

### Post by cybrsaylr on 2011-06-26
jerrrys,

Bingo! That did the trick!

Got BleachBit 0.8.8 using your link that installed it with Ubuntu Software Center, even thought Ubuntu Software Center shows version 0.8.8-1 (bleachbit)

Got two entries for BB just like in earlier Ubuntu versions and they both open with Unity launcher bar.


Thanks for the help jerrrys.....;)

---

### Post by jerrrys on 2011-06-26
glad to help

---

### Post by Andrew.Z on 2011-06-27
The Ubuntu 11.04 repo has BleachBit 0.8.7, and if I remember right, there are two issues with the 0.8.7 in the Natty repo.  One problem is something related to sudo changed from 10.10 to 11.04 which causes a crash on startup, and another is downstream the menu shortcut disappeared.

Try [BleachBit version 0.8.8 which adds support for Ubuntu 11.04 (Natty Narwhal)](http://bleachbit.sourceforge.net/news/bleachbit-088).  I tested it on Natty.  The site has a .deb for Natty.

If it still doesn't work, report a bug downstream (if you use the Ubuntu repo) or upstream (if you use the .deb from this site)

---

### Post by bodhi.zazen on 2011-06-28
All of the cruft on your system can be easily managed by :

1. your package manager (apt).

2. Keeping any valuable data in a separate data partition, including a back up of any configuration file you wish to keep (.bashrc, .zshrc, .mozilla).

3. Proper browser configuration.

4. rm -rf $HOME/*

Just be sure to understand #2, especially the back up of mission critical config files.

---

