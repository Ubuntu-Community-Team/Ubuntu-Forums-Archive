---
title: "Change permissions of folder's content."
date: 2011-02-22
forum: Security
---

### Post by Koffeehaus on 2011-02-22
Recently I've tried installing Calibre from the Software Centre, but it seemed to be glitching as when I press Update Source, the 'In Progress' icon shows up, but when it finishes nothing changes - the Update Source button is still there. Should I report this?

Anyways, I've installed Calibre from their website to .calibre in Home Folder. However, the folder is 'locked' as it requires root priveleges and I can't drop files there without being the admin. I'd like to reduce 'open as root' files to minimum, so I was wondering if there is a way to change the permissions of all the content in one operation, preferably  using GUI, and not the terminal?

In addition I've noticed that other folders in my Home Folder like Pictures/Wallpapers require root privileges. This is really annoying as when I 'experiment' with Ubuntu I use Live CD to make sure I don't screw up the main system. When I do I can't open some files from hard disk because of those root inconsistencies.

Any idea why did this happen?

---

### Post by The Cog on 2011-02-22
You shouldn't be installing stuff in the /home folder. Peoples home folders live **in** the home folder - /home itself is a kind of no-man's-land. So assuming that your username is koffeehaus, your home folder is /home/koffeehaus and you should really stay within there (where you will find you have full rights). So you should probably put calibre in /home/koffeehaus/.calibre.

And if you choose to install "system" software - stuff that's available to all users, then /home is still the wrong place - /opt or /usr/local are the usual places.

You do have a home folder (/home/koffeehaus) don't you? I guess it is most likely that you don't realise that /home/koffeehaus is your home folder, rather than just /home. But maybe it's possible that your installation is totally screwed up and that folder hasn't been created, which would leave you somewhat in limbo.

Is that making sense?

---

### Post by Koffeehaus on 2011-02-22
> **The Cog said:**
> You shouldn't be installing stuff in the /home folder. Peoples home folders live **in** the home folder - /home itself is a kind of no-man's-land. So assuming that your username is koffeehaus, your home folder is /home/koffeehaus and you should really stay within there (where you will find you have full rights). So you should probably put calibre in /home/koffeehaus/.calibre.

And if you choose to install "system" software - stuff that's available to all users, then /home is still the wrong place - /opt or /usr/local are the usual places.

You do have a home folder (/home/koffeehaus) don't you? I guess it is most likely that you don't realise that /home/koffeehaus is your home folder, rather than just /home. But maybe it's possible that your installation is totally screwed up and that folder hasn't been created, which would leave you somewhat in limbo.

Is that making sense?


Uh, yes, I have all my stuff in home/koffeehaus. It is called the Home Folder, right?

That's right, calibre is in home/koffeehaus/.calibre, so it's not that. But if you look at the screen dump the folder is still locked.

I can run calibre from my applications menu, but it takes AGES! So I was thinking if I change the permissions from root to koffeehaus, it'll run faster

---

### Post by cariboo on 2011-02-22
.calibre is where the configurations for calibre live, not were the executable files should be. I would assume if you installed calibre to ~/calibre you wouldn't run into the problems you are now, but as The Cog said it really should be installed in /opt or /usr/local.

---

### Post by The Cog on 2011-02-23
cariboo907 is right - .calibre in your home folder would probably be where calibre places your personal settings. And it should definitely be owned by you. What's not clear so far is where the actual calibre application got installed to.

But anyway, this command will give ownership of the .koffeehaus folder back to you which is as things should be:
> sudo chown -R koffeehaus:koffeehaus /home/koffeehaus/.calibreMy guess is that somehow calibre first ran as root rather than yourself, so the directories it created at that time also belonged ot root. Perhaps they were created as part of the install procedure which was run with sudo?

---

### Post by Koffeehaus on 2011-02-24
Thanks Cog, it has changed the permissions to koffeehaus', but it still takes literally 2 minutes to launch. So I suppose it wasn't the permissions' fault after all, but location's.

I installed it from binary with the command that was provided on calibre's website:

```
sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

```Then it asked me for location. I typed .calibre. So it installed everything there. My personal settings are stored in Documents/Calibre Library. Moreover I have no idea how to uninstall it now, from digging the net I've seen it mentioned somewhere that the uninstall script is broken with binary's calibre. Great!

So If I manually drag and drop all the calibre files to usr/local or opt then do you reckon it would solve the problem of terribly slow start-up?

---

