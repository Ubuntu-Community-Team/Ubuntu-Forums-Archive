---
title: "Firefox doesn't work since CE script upgrade"
date: 2006-09-18
forum: Ubuntu Christian Edition
---

### Post by mikesena on 2006-09-18
Hi,

I installed Christian Ubuntu off the Dapper script; all went well during the installation.  I restarted as suggested.

However, when i turned it back on again, firefox (and opera, which i also tried) no longer works.  I have internet, because gaim signs in, i can sudo apt-get update / install etc..  (I am writing this on a different computer)

How do I fix this?  I really want to use the filter program and have my internet filtered, but i think that's what's blocking it at the moment.  i have removed it and tinyproxy, which may / may not have been part of it, but it still doesn't work.

Any ideas?

Is there a way I can go back to regular ubuntu, if there isn't a solution?

---

### Post by mhancoc7 on 2006-09-18
> **mikesena said:**
> Hi,

I installed Christian Ubuntu off the Dapper script; all went well during the installation.  I restarted as suggested.

However, when i turned it back on again, firefox (and opera, which i also tried) no longer works.  I have internet, because gaim signs in, i can sudo apt-get update / install etc..  (I am writing this on a different computer)

How do I fix this?  I really want to use the filter program and have my internet filtered, but i think that's what's blocking it at the moment.  i have removed it and tinyproxy, which may / may not have been part of it, but it still doesn't work.

Any ideas?

Is there a way I can go back to regular ubuntu, if there isn't a solution?

Sorry for your trouble.

Did you use the Convert_Me script? 

I would suggest going into Synaptic and completely removing dansguardian, clamav, tinyproxy, and firehol. Be sure to select "Completely Remove". Then I would reboot and try the Convert_Me script again. Be sure to reboot when finished. This has worked for a few users who had dansguardian installed before running the script. Let me know how it goes. 

God Bless, Jereme

---

### Post by mikesena on 2006-09-18
Hi Jereme,

I was using the Convert_Me script.  I tried what you said, removing those programs and restarting did make firefox work again.

I then ran the script once more, and it didn't come up with christian ubuntu (in the panel that is displayed, showing what programs are being loaded after logging in), but instead it said 'Gnome 2.14' or something like that.  Before it changed it to 'Ubuntu Christian Edition'.  I have an automatic logon.

What should I do now?

Also, i presume is now running, but there is nothing in any of the config files.  before there were a couple of lines of comments, now there is nothing.  maybe the directories should have been removed manually?  i don't know.

Finally, how do I use urlblacklist.com in dansguardian, which is what the dansguardian site suggested.

Thanks,
Michael

---

### Post by mhancoc7 on 2006-09-18
> **mikesena said:**
> Hi Jereme,

I was using the Convert_Me script.  I tried what you said, removing those programs and restarting did make firefox work again.

I then ran the script once more, and it didn't come up with christian ubuntu (in the panel that is displayed, showing what programs are being loaded after logging in), but instead it said 'Gnome 2.14' or something like that.  Before it changed it to 'Ubuntu Christian Edition'.  I have an automatic logon.

What should I do now?

Also, i presume is now running, but there is nothing in any of the config files.  before there were a couple of lines of comments, now there is nothing.  maybe the directories should have been removed manually?  i don't know.

Finally, how do I use urlblacklist.com in dansguardian, which is what the dansguardian site suggested.

Thanks,
Michael

When you re-ran the script did you use a freshly extracted version. The script is somewhat disposable. So if you used the same one over again, you would get errors and it would not work.

I am not sure exactly what problem you are having now with the automatic login. Could you explain it a bit more?

To be honest I have only really worked with the basics of dansguardian. So I really can't help with the urlblacklist.com questions. Sorry!

Thanks, Jereme

---

### Post by mikesena on 2006-09-19
does it initially come with some blocked lists?  or some form of filtering?

---

### Post by mhancoc7 on 2006-09-19
> **mikesena said:**
> does it initially come with some blocked lists?  or some form of filtering?

Yes, dansguardian comes preconfigured with filter settings. You can use the GUi (Applications > System > Administration > Configure Parental Controls) to edit them.

Jereme

---

