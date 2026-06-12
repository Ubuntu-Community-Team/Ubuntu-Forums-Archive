---
title: "Intermitant wireless after upgrade gnome 14.04 beta"
date: 2014-03-19
forum: Ubuntu Development Version
---

### Post by Murdoc_of_puts on 2014-03-19
Hello, 
So after an upgrade my wireless has been extremely slow.  So I figured I'd try this [http://ubuntuforums.org/showthread.php?t=2209737](http://ubuntuforums.org/showthread.php?t=2209737)  which seemed to work great, except that now my wifi connection will randomly drop.  The connection rate will slow down to the point that it gets timed out and then will eventually disconnect.  If I turn off the wireless (both hardware and software) and then turn it back on it will reconnect again and work fine up until the point that it doesn't any more.  It's not a major problem, as I can just turn it on and off.  Just a note though there isn't a problem with the router or the connection at that end though, as there's another laptop with ubuntu 13.10 running that doesn't have connection issues, Also the read out from the router is nominal.  I've included the read out from  varunendra's script too.

---

### Post by Murdoc_of_puts on 2014-03-19
So one other thing that I can rule out, as it looks as if it's being randomly deauthorized for some reason, I just checked the routers ip address log, and there's nothing there that shouldn't be.  So that's good.

---

### Post by bapoumba on 2014-03-19
Moved to Ubuntu +1.

---

### Post by varunendra on 2014-03-19
> **Murdoc_of_puts said:**
> Hello, 
So after an upgrade my wireless has been extremely slow.  So I figured I'd try this [http://ubuntuforums.org/showthread.php?t=2209737](http://ubuntuforums.org/showthread.php?t=2209737)  which seemed to work great, except that now my wifi connection will randomly drop.

That solution worked great for the OP there because they needed the suggested driver. However, yours is a rather common card, not as new as theirs, and thus it depends on a rather common driver. Your attempt to install that one and wifi working better must have been just coincidence, I don't think installing that driver would have helped your card in any way.

Also, since you are using kernel 3.13, your driver is newer than I usually suggest with this card (driver from kernel 3.12). So I doubt if changing driver is going to help.

However, there is something that you should try with the router -

The Access-Point you are currently connected to as per the report is using the dreaded **[COLOR="#FF0000"]TKIP[/COLOR]** encryption while the WPA2 standard requires **AES (CCMP)**. I hate these vendors who allow such weird combinations, it shouldn't be an option in the first place. Apparently, most of your neighbours (or surrounding Access-Points in the same building) seem to be fond of TKIP and WPA/WPA2 mixed mode, plus, many of them are using channel "6" simultaneously to add to the problem. Please try the following in the router -

[indent]**1)** Change the encryption algorithm to **AES (CCMP)**. The encryption type is good (WPA2), so leave it unchanged, just change the algorithm only. Even if it doesn't seem to help, keep this setting.

**2)** Try changing the channel to **1 or 11**. Channel 11 seems to be least used among all the surrounding Access-Points, so it should be best for you, but 1 is not too crowded either. Reboot the router after Saving any changes you make.

**3)** If you are using any of those routers/Access-Points that are using WPA/WPA2 mixed mode, change their encryption too to pure **WPA2-PSK with AES (CCMP)** as suggested above.

**4)** Along with the above changes in the router, try some driver parameters in Ubuntu as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912) . If any of them seem helpful, you can make them permanent as suggested in posts #16 and #18 in the same thread.[/indent]

For now, try these and let us know if the performance improves.

---

### Post by Murdoc_of_puts on 2014-03-20
Yeah I guess I really never thought of that, that channel 6 was pretty cluttered.  Thanks, that seemed to do the trick, and add a little zip into the online connection for me.

---

### Post by varunendra on 2014-03-21
If it made the connection good enough, please consider marking the thread as [SOLVED] using the "Thread Tools" link above the first post. :)

However, if the performance is still poor, I hope you know what it means when using a "Development" version - that is - find problems and report them (by filing bug report or adding your logs to existing ones) to 'HELP' improving things before the final release.

If needed, you may also try compiling a relatively 'Older' driver to see if it works better.

---

### Post by Murdoc_of_puts on 2014-03-21
varunendra , Thanks for your help I really appreciate it.  I didn't want to mark it as solved right away, I wanted to give it a little time to see if the connection would drop again.  It hasn't, and also yes I know that using the development version of the os isn't stable and it has it's bugs, but I figure if I can sort through some things now then I'll be able to help other people when it rolls arround.

---

### Post by varunendra on 2014-03-21
Actually the point of using a development version is to offer help to developers by finding and reporting bugs. Sometimes there can be a huge amount of radical changes when it is finally released, in case when a lot of 'experimental' or 'buggy' features are held back if they were not sorted out in time.

But yeah, I get your idea, and is certainly noble. And the amount of changes in final release is not always 'huge'. :)

---

