---
title: "Any possible side effects of using the same firefox profile on Windows/Ubuntu?"
date: 2007-04-06
forum: The Cafe
---

### Post by PrimoTurbo on 2007-04-06
Being the genius that I am I mounted my Windows XP NTFS drive, created a new profile under in firefox and pointed it to my Windows profile. It imported all my stuff with out problems so far (but I have made a backup), extensions, passwords, settings, bookmarks, logged in sessions, cookies seem to be working so far. Can this completely mess something up? Has anyone else done this successfully.

---

### Post by Obor on 2007-04-06
I'm sharing my firefox and thunderbird profiles with windows for some time without any problems. I store my profiles on a fat32 partition though.

---

### Post by gurgle on 2007-04-06
I just use Google browser sync and foxmarks. I love both of them.

---

### Post by CarpKing on 2007-04-06
If your Windows partition is not mounted as writeable from Linux, it would probably be best to point you Windows profile to your Linux one instead (this is how I have mine).  I've never tried your setup, but I would imagine that you couldn't add bookmarks and whatnot if Firefox couldn't write to that partition from Linux.

---

### Post by PrimoTurbo on 2007-04-08
I had no negative side effects, NTFS was writeable and everything. I had some issues doing the same with with wine and utorrent, my torrents were all red on windows I had to readd the .torrent files.

---

### Post by fsando on 2007-04-09
I have firefox and thunderbird (and also sunbird) sharing profiles from win and linux. I have put them on a fat32 partition. The real beauty was that I copied my profiles from windows default location to a another drive, then from linux created new profiles pointing the folders at the copies - and presto! Everything was there - including all my plugins - and even in thunderbird the last read mail in windows was the mail in focus when opened in linux. So absolutely everything worked without a glitch.

I have later seen a couple minor issues:
1. The versions on the two platforms may come out of sync if they are updated automatically (you'll see firefox performing its compatibility check). This can turn out to be quite nasty if the two versions are really incompatible: I had this with sunbird (the calendar) one version wouldn't open at all because the profile had been opened in a newer version on the other platform. I solved it by updating to the newer version on both platforms.
2. some plugins (like flash) is apparently installed in the default location regardless of where the current profile is located - which means - you are constantly prompted to install it - and it is still not recognized. I've solved this by temporarily switching to default profile while installing the plugin - then switched back to my main profile and now flash was recognized.
3. I have now installed the calendar plugin in thunderbird in linux and it does not show up right in windows - but does not appear to break anything.

---

### Post by bailout on 2007-04-09
I do the same but with Opera. I installed Opera on a fat32 partition under Windows and my linux Opera uses the same bookmarks, cookies, wand, email and notes. Worked well but I was having problems with edgy crashing. As I usually have opera open I found that sometimes the email files could get corrupted by the crash and had to stop linking to those which meant I could only use email under windows. I now handle my emails on my laptop and have gone back to sharing them between win and linux.

---

