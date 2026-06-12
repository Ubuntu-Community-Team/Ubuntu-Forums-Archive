---
title: "Is there a computer &quot;cleaner&quot; (like CCleaner) for Ubuntu?"
date: 2015-02-15
forum: Security
---

### Post by gmolivier on 2015-02-15
Is there a computer "cleaner" (like CCleaner) for Ubuntu?
Why would i NOT need one?

gmolivier

---

### Post by sudodus on 2015-02-15
There is not the same need for such cleaning in Ubuntu, but you might like Ubuntu Tweak. I use the ***janitor*** of Ubuntu Tweak to remove 'cruft' from Ubuntu systems.

See this link [http://askubuntu.com/questions/75454/how-do-i-install-ubuntu-tweak](http://askubuntu.com/questions/75454/how-do-i-install-ubuntu-tweak)

---

### Post by kurt18947 on 2015-02-15
IMO Bleachbit is fairly close.  There is something called Computer Janitor that did cause problems at one time, deleting things that shouldn't have been deleted. Bleachbit hasn't caused a problem that I'm aware of. It doesn't seem to me (I could be wrong) that Ubuntu or other distros have the same problem with orphaned bits causing problems causing problems. One source of problems with Windows is registry corruption. Ubuntu and other distros don't have a registry equivalent that I know of.

---

### Post by pfeiffep on 2015-02-15
> **gmolivier said:**
> Is there a computer "cleaner" (like CCleaner) for Ubuntu?
Why would i NOT need one?

gmolivierEver since I had a problem with /temp not being fully recognized on an old laaptop which caused extremely slow booting I installed and ran bleachbit regularly (which fixed the problem).

I recently ran an experiment on my desktop computer and discovered after about a week the 'junk' had accumulated to over 1GB. I know that I could have manually cleand every bit of the 'junk' and probably more, but I choose to use an automated tool. I also know that I could write a script to be executed by cron so that the operations are automated; but I choose differently!

Please be careful when setting up Bleachbit - take your time and don't be too aggressive.

---

### Post by vasa1 on 2015-02-15
> **pfeiffep said:**
> ...

I recently ran an experiment on my desktop computer and discovered after about a week the 'junk' had accumulated to over 1GB. ...
If you do run that experiment again, could you list the folders holding the junk?

---

### Post by pfeiffep on 2015-02-15
> **vasa1 said:**
> If you do run that experiment again, could you list the folders holding the junk?
I will start today and track ... I'll post daily, or if you prefer vasa I'll pm you

---

### Post by monkeybrain20122 on 2015-02-15
+1 to bleachbit. But there is also something very simple that one can do. Open Nautilus, go to Edit > Preferences > Behaviour and under Trash check the box to add a delete option that bypass trash. That way when you delete something it is really deleted rather than taking up space quietly in the trash folder. I think Trash is the most stupid design, when I delete something, I want it gone, not to be moved to another folder (there is an 'are you sure' popup before deleting so it is not likely you would delete something accidentally)

(bleachbit has an option to clean up Trash too)

---

### Post by gmolivier on 2015-02-15
...thanks all

gmo

---

### Post by vasa1 on 2015-02-15
> **pfeiffep said:**
> I will start today and track ... I'll post daily, or if you prefer vasa I'll pm you
Whatever is convenient to you, thanks!

---

### Post by cogset on 2015-02-16
If it isn't too much trouble, could you post here? I'm curious too about this junk files, as  I don't see many of them in my system.Or I just don't know where to look ...

---

### Post by pfeiffep on 2015-02-16
I plan testing this until the file space to be recovered is significant, and for me 1GB is significant. 
So others who might be interested in the locations I'm posting today the space that would have been recovered in about 1 hour of computing. 
I really don't know how much of this data would have been deleted upon a reboot (I shut down nightly) without running bleachbit, but I will keep a daily log of what bleachbit would have deleted just by running it in the preview mode.
I've also included the contents on my bleachbit.ini file.

```

 Disk space to be recovered: 50.4MB 
 Files to be deleted: 1605 
 Special operations: 34
  
 /home/pfeiffep/.mozilla/firefox/
 /home/pfeiffep/.adobe/Flash_Player
 /home/pfeiffep/.macromedia/ /home/pfeiffep/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol 
 /home/pfeiffep/.thunderbird/c8irxux4.default/
 /home/pfeiffep/.cache
 /home/pfeiffep/.cache/mozilla/firefox/
 /home/pfeiffep/.cache/upstart 
 /home/pfeiffep/.cache/thunderbird 
 /home/pfeiffep/.cache/thumbnails 
 /home/pfeiffep/.cache/wallpaper 
 /home/pfeiffep/.cache/logrotate 
 /home/pfeiffep/.cache/ibus 
 /home/pfeiffep/.cache/gstreamer-1.0 
 /home/pfeiffep/.cache/evolution 
 /home/pfeiffep/.cache/mozilla 
 /home/pfeiffep/.cache/event-sound-cache.tdb.c43d0e1c2cc51a90bea3b6d3544476b8.x86_64-pc-linux-gnu 
 /home/pfeiffep/.cache/indicator-applet-complete.log 
 /home/pfeiffep/.local/share/recently-used.xbel 
 /var/log/dmesg.0 
 /var/log/lightdm/x-0-greeter.log.old 
 /var/log/lightdm/x-0.log.old 
 /var/log/lightdm/lightdm.log.old 
 /var/log/Xorg.0.log.old 
 /tmp/sni-qt_python2.7_3680-Ihaf02/icons/hicolor/32x32/apps/python2.7_3680_2f282c85ef0c788eb09624bc3decd0b5.png 
 /home/pfeiffep/.xsession-errors 
 /home/pfeiffep/.config/libreoffice/4/user/registrymodifications.xcu 
 /home/pfeiffep/.config/chromium/Default/Preferences 
 /home/pfeiffep/.config/chromium/Default/Preferences 
 /home/pfeiffep/.config/chromium/Local State 
 /home/pfeiffep/.config/chromium/Local State 
 /home/pfeiffep/.config/chromium/Default/databases/Databases.db 
 /home/pfeiffep/.config/chromium/Default/Web Data 
 /home/pfeiffep/.config/chromium/Default/History 
 /home/pfeiffep/.config/chromium/Default/Favicons 
 /home/pfeiffep/.config/chromium/Default/Web Data 
 /home/pfeiffep/.config/chromium/Default/Cookies-journal 
 /home/pfeiffep/.config/chromium/Default/History 
 /home/pfeiffep/.config/chromium/Default/Web Data 

```

[SIZE=4]**bleachbit config**[/SIZE]
   ```


 pfeiffep@Dell-Studio:~/.config/bleachbit$ more *.ini 

 [bleachbit] 

 auto_start = False 

 check_beta = False 

 check_online_updates = True 

 shred = False 

 first_start = False 

 version = 1.0 

 hashsalt = daf5850c5894fd1d65341cefb475118f0128fced4506bda5ac04d3d003bbd2ddd4316 

 ceb79a9ece0dc8bc20a7013d89168d414c8807d0780e78958a862fad1a1 

  
 [hashpath] 

  
 
[list/shred_drives] 
 0 = /home/pfeiffep 
  
 [preserve_languages] 
 en = True 
  
 [tree] 

 apt = True 
 apt.autoclean = True 

 apt.autoremove = True 
 apt.clean = True 
 chromium = True 
 chromium.cache = True 
 chromium.cookies = True 
 chromium.current_session = True 
 chromium.dom = True 
 chromium.history = True 
 chromium.search_engines = True 
 chromium.vacuum = True 
 libreoffice = True 
 libreoffice.cache = True 
 libreoffice.history = True 
 system = True 
 system.desktop_entry = True 

 system.cache = True 
 system.clipboard = True 
 system.custom = True 
 system.recent_documents = True 
 system.rotated_logs = True 
 system.tmp = True 
 system.trash = True 
 thunderbird = True 
 thunderbird.vacuum = True 
 x11 = True 
 x11.debug_logs = True 
 flash = True 
 flash.cache = True 
 flash.cookies = True 
 firefox = True 
 firefox.cache = True 
 firefox.crash_reports = True 

 firefox.dom = True 
 firefox.download_history = True 
 firefox.session_restore = True 
 firefox.url_history = True 
 firefox.vacuum = True 
 chromium.form_history = True 
 chromium.passwords = True 


```

---

### Post by bashiergui on 2015-02-16
This link shows a few simple commands to remove cruft
<snipped crappy link>
basically ```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by pfeiffep on 2015-02-16
> **bashiergui said:**
> This link shows a few simple commands to remove cruft
[http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html)
basically ```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```Thanks, I was using that method for quite some time - the commands so an excellent job, but IMO don't go nearly far enough.

---

### Post by cogset on 2015-02-27
So far I haven't seen a lot in the files cleaned out, Firefox and Thunderbird cache files can be cleaned using native tools (either on the fly whilst using the program and/or automatically on exit) ,whilst Flash files can be dealt with in the same way (with the Clear Recent History option ,Firefox will clear LSOs and local storage as well if cookies, site preferences and offline website data are checked and the time range specified is "everything") or using an extension.
BTW, the new Firefox cache can get quite huge, in my case I've seen it  growing up to almost 300M.
Then there are the old logs, I assume that logrotate would take care of that, but maybe Bleachbit gets there first.
The other stuff in the .cache directory, it would be interesting to know how Ubuntu manages this ,I would guess that there may be a configuration file somewhere that states how and when dispose of those files?

---

### Post by kurt18947 on 2015-02-28
> **cogset said:**
> So far I haven't seen a lot in the files cleaned out, Firefox and Thunderbird cache files can be cleaned using native tools (either on the fly whilst using the program and/or automatically on exit) ,whilst Flash files can be dealt with in the same way (with the Clear Recent History option ,Firefox will clear LSOs and local storage as well if cookies, site preferences and offline website data are checked and the time range specified is "everything") or using an extension.
[SIZE=4]**BTW, the new Firefox cache can get quite huge, in my case I've seen it  growing up to almost 300M.**[/SIZE]
Then there are the old logs, I assume that logrotate would take care of that, but maybe Bleachbit gets there first.
The other stuff in the .cache directory, it would be interesting to know how Ubuntu manages this ,I would guess that there may be a configuration file somewhere that states how and when dispose of those files?

True about the firefox cache. I guess there's an advantage to a large cache if one has a slow internet connection or expensive per MB. web access. I have neither so one of the first things I do on a new install is open Firefox then Edit -> Preferences -> Advanced -> cached web content and manually set it to 30-40 MB instead of the default 350 MB. It seems to make Firefox quicker IMO.

---

### Post by ian-weisser on 2015-02-28
> **bashiergui said:**
> ```
sudo apt-get autoclean
sudo apt-get clean
```

Running both autoclean and clean seems rather a waste of time.
'autoclean' causes apt to do a lot of work, which 'clean' promptly erases.
I usually tell people to pick the one they want.

---

### Post by bashiergui on 2015-02-28
> **ian-weisser said:**
> Running both autoclean and clean seems rather a waste of time.
'autoclean' causes apt to do a lot of work, which 'clean' promptly erases.
I usually tell people to pick the one they want.Indeed it does. I removed that link as it was misleading on that point.

From the apt-get man page: > clean  clean clears out the local repository of retrieved package files. It removes everything but the lock file from[/var/cache/apt/archives/]("file:///var/cache/apt/archives/") and [/var/cache/apt/archives/partial/.]("file:///var/cache/apt/archives/partial/")


autoclean 
 Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

---

