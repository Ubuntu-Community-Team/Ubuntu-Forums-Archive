---
title: "Unity: Recent Updates: Dropbox Corruption?"
date: 2015-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2015-06-07
**This is not a support request but a question.


DE Unity, (14.04.2 LTS), recent corruption of Dropbox and failure to re-install . . . 

Just wondering if this is a one-off event (for) me or if due to recent Ubuntu updates. Dropbox requires QT 5.3 and I've noticed recent QT updates, thinking this might be a factor.

So, anyone have recent dropbox problems in Unity after updating past two weeks???

---

### Post by mbott on 2015-06-07
No problems to report with Dropbox under either 14.04.2 LTS or 15.04.

Sorry,

-- 
Mike

---

### Post by Copper Bezel on 2015-06-07
No, I haven't encountered anything like this. My 15.04 machine isn't fully updated to the latest, though. Certainly no problems on my 14.04 laptop, nor with installing Dropbox this week after the 15.04 update on my desktop. What problem did you encounter on attempting to reinstall?

---

### Post by Kurt_Alan on 2015-06-08
> **Copper Bezel said:**
> No, I haven't encountered anything like this. My 15.04 machine isn't fully updated to the latest, though. Certainly no problems on my 14.04 laptop, nor with installing Dropbox this week after the 15.04 update on my desktop. What problem did you encounter on attempting to reinstall?

The problem was root authentication loop. I next did a thorough uninstall per previous tech support advice:

Depending on your OS and the package you used to perform the installation, you could have files in two different locations. I'm sending you instructions for both of the cases, so if some of the commands error out don't worry.
Run the following commands in your terminal:

```
 dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox 
```

I then reinstalled 64 bit version via CLI from dropbox.com
No problems now. So, a one-off problem.
Segue: Here's a confusing item that could be an issue. Maybe you can clarify this. You can install via Synaptic or CLI nautilus-dropbox daemon. If you do this, then you have the full GUI dropbox but you can also access via CLI, if you choose: ```
 dropbox status
```

BUT if you install via CLI from dropbox.com THEN nautilus-dropbox is not installed, you have no CLI access, strictly a GUI proposition.

So, really, these are two different install paths. Is one better than the other? I am speculating that the nautilus-dropbox daemon might be buggy and that it might be better
to install without it, as I just did.

What do you think?

Problem now solved except for latter question.

---

### Post by tiger2000 on 2015-06-16
Hi
I got an issue  in Dropbox. I opened a thread 
[http://ubuntuforums.org/showthread.php?t=2282752&highlight=dropbox](http://ubuntuforums.org/showthread.php?t=2282752&highlight=dropbox)

I did not and I do not intend to re-install dropbox. I will indeed do , if necessary. However.. it's weird.

thannks

---

### Post by tiger2000 on 2015-06-16
One more thing :
in your instructions, the line : 
rm /etc/apt/source.d/dropbox

Should not be : 

rm /etc/apt/source.list.d/dropbox 

?
I do not see source.d under /etc/apt / .
thanks

---

### Post by mbott on 2015-06-22
I'm going to have to revise my earlier "no problem" reply. I have noticed that if I try and close a window or running program while Dropbox is uploading files, the display freezes, except for the mouse pointer. Further investigation is necessary to determine what is happening.

-- 
Mike

---

