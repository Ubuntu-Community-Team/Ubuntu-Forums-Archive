---
title: "Remove apparent malicious extension from Chrome"
date: 2016-12-31
forum: Security
---

### Post by motoperpetuo on 2016-12-31
Video Download Helper stopped working with Youtube videos for me a few months ago. The other night, I decided to try another Chrome extension, so I downloaded something, can't remember the exact name, but it calls itself Video Download Helper too. Since downloading it, I get lots of random popups trying to sell me stuff. Weirdly, I don't seem to be able to screen shot them.

I tried going to Settings | Extensions in Chrome to remove the extension, but when I try that, the Chrome tab just closes. Tried reinstalling Chrome with:

sudo apt-get purge google-chrome-stable

and then

sudo apt-get autoremove

then reinstalling, but the malicious extension is still there.

Is there much I can do aside from reinstalling my OS? This is the first time I've ever had to deal with malware in Linux.

---

### Post by wildmanne39 on 2016-12-31
*Thread moved to **Security**.* Please keep the topic confined to the malware issue and do not mention downloading youtube videos.
Thanks

---

### Post by Irihapeti on 2016-12-31
If Chrome is anything like other browsers, the problem is likely to be in your user profile. You'll need to delete that and start again.

---

### Post by The Cog on 2016-12-31
Reinstalling the OS won't help. It's in your personal chrome settings. Wiping all your personal data will fix it.

You can be more specific than that though. I don't have chrome installed here, I have chromium instead. All the settings for chromium are in /home/my-name/.config/chromium. You may well find a folder .config/chrome in your home folder (you need to turn on showing hidden folders - .config is a hidden name because it starts with a dot).

Removing the whole .config/chrome folder will delete all your chrome settings - bookmarks, saved passwords etc. You may be able to get more specific looking further down inside that directory. It's probably worth waiting for more knowledgeable replies.

---

### Post by llamabr on 2017-01-01
Also, we could help troubleshoot if we knew exactly what extension you installed. It's a huge pain to rm your entire config file, since you lose all your bookmarks and everything else, too.

---

### Post by motoperpetuo on 2017-01-01
Thanks. Deleting /home/my-name/.config/google-chrome seems to have done it. I appreciate the help. It did wipe out my bookmarks as someone else warned, but since I didn't have much it wasn't a big deal for me.

---

### Post by motoperpetuo on 2017-01-01
I appreciate it. It seems like the extension changed its name after I installed it to Video Download Helper. I wasn't able to get any other extension name because of the way it was restricting access to Extensions settings in Chrome. Nasty little piece of malware, but after deleting my profile it seems to be gone now. Good point about that wiping out bookmarks. Not a big deal in my case since I didn't have much, but I guess you could just export them first if you were worried about that, couldn't you?

---

### Post by The Cog on 2017-01-02
You certainly could be more specific. Inside google-chrome is a folder called Default, which contains all your default profile. Inside there are other folders.

I just found this link: [http://stackoverflow.com/questions/14543896/where-does-chrome-store-extensions](http://stackoverflow.com/questions/14543896/where-does-chrome-store-extensions)
I should have found that earlier, but I had a horrible cold and was not thinking clearly.

---

