---
title: "Ubuntu One not syncing"
date: 2009-12-30
forum: Ubuntu One (CLOSED)
---

### Post by stevanbt on 2009-12-30
Hi,
I can't get my home pc to sync with Ubuntu One.  I think it's because I made a bit of a mess of my Ubuntu One account.  Something like this...

[LIST]
[*]Signed on from home using my yahoo email account - this is wrong email address
[*]Signed on from work using my gmail email account - this is right email address
[*]I've since logged on from home using gmail account.  Tomboy notes synchronize ok, but my Ubuntu One folder in my home directory doesn't sync with files I uploaded today at work.
[/LIST]

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1297076&highlight=config+file") in an attempt to get rid of any reference to my yahoo account on my home pc - but this hasn't made any difference.

Any other suggestions?

Thanks, Steve.

---

### Post by stevanbt on 2010-01-03
Anyone?

---

### Post by AmpersUK on 2010-01-11
Check the version number of your Tomboy Notes. If it is 1.0 then it won't.

You need version 1.1 - or is it 1.01? Not sure.

When 9.10 first came out, it worked with Ubuntu One. However, after my hard drive trashed, I had to download a new ISO a week or so ago, and it loaded the old version of Tomboy notes. And now, of course, it doesn't sync.

---

### Post by thebear78 on 2010-01-12
You may also be affected by this bug: 
[https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/479417](https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/479417) 
A fix is in progress.

---

### Post by AmpersUK on 2010-01-12
Thanks for this info, as long as it is in hand, I am happy.

---

### Post by redmistpete on 2010-01-12
> **AmpersUK said:**
> Thanks for this info, as long as it is in hand, I am happy.

I had the same problems - it seems that the website differs from the ubuntu one interface. Here is my solution (not sure if it will work for you)

(assuming all computers are registered to Ubuntu One accounts) On your work computer, navigate to the ubuntu one folder (it should say "disconnect", implying that it is connected) and right-click, selecting "sharing options" and fill in your home email address. This will send a share/sync request (via email) to your home email. Now do the same on your home computer. Accept both invitations on both computers, then restart both machines. It was a pain to get sorted but both my machines now sync using both the website and the shared folders. 

One other thing worthy of note. If you search for ubuntu one on your computer, run the app and select "Always show" and "Connect Automatically", it will connect your system on each reboot; the "connect button" in the Ubuntu One folder never worked for me whenever I clicked connect but the "Automatic connection" sorted that and now I can quickly jump to the folder by right-clicking the "ubuntu one" cloud in the panel ;)

Hope this helps someone at least.

---

### Post by AmpersUK on 2010-01-12
[QUOTE=redmistpete;8652103On your work computer, navigate to the ubuntu one folder (it should say "disconnect", implying that it is connected) and right-click, selecting "sharing options" and fill in your home email address. This will send a share/sync request (via email) to your home email. Now do the same on your home computer. Accept both invitations on both computers, then restart both machines.

One other thing worthy of note. If you search for ubuntu one on your computer, run the app and select "Always show" and "Connect Automatically",.[/QUOTE]

Thanks for this, I am sure it will help. Sent off the requests.

---

