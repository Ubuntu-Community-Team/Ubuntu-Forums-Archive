---
title: "Why doesn't Ubuntu use HTTPS for the main ISO download and system updates?"
date: 2018-04-04
forum: Ubuntu, Linux and OS Chat
---

### Post by junktext-0 on 2018-04-04
I love Ubuntu, but I was surprised to learn that the main ISO download link for the current, flagship release of 16.04 LTS is still not being downloaded over a secure HTTPS connection and neither are any system updates via Ubuntu's Software Updater (at least within my Ubuntu 16.04 LTS system).

What's even more confusing is that the main homepage for Ubuntu uses HTTPS: [URL="https://www.ubuntu.com/"]
https://www.ubuntu.com[/URL]

And so does the URL which points you to the download link for 16.04:
[https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.4&architecture=amd64](https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.4&architecture=amd64)

But, then if you cancel the auto-download dialog and click on the "download now" link it is not using HTTPS:
[http://releases.ubuntu.com/16.04.4/ubuntu-16.04.4-desktop-amd64.iso](http://releases.ubuntu.com/16.04.4/ubuntu-16.04.4-desktop-amd64.iso)

The system updates in Ubuntu's Software Updater are also not using HTTPS. You can confirm this by either hovering your mouse over an active download and it'll say it's getting the update from an "http://" connection, or you can also do this to see what I mean:


[LIST=1]
[*]Open up your "System Settings". 
[*]Click on "Software & Updates". 
[*]Under the "Ubuntu Software" tab, there's an area called "Download from", click on the "Other..." option. 
[*]Choose any mirror listed and the only protocol that is available is "http" (not HTTPS). 
[/LIST]

What gives? I know the main ISO has a [SHA checksum]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0") that advanced users can verify (novice users won't likely do this) and that updated system packages have been digitally-signed and such, but I would feel more reassured if all system packages were delivered to my computer using a secure HTTPS connection. Especially, since [Let's Encrypt]("https://letsencrypt.org/") is a free way to add HTTPS capability for anyone.

Thanks,

  --William

William Paul Liggett
[https://junktext.com](https://junktext.com)

---

### Post by Holger_Gehrke on 2018-04-04
https protects data confidentiality **not** data integrity. The contents of the ISO are not confidential, the fact you're downloading the ISO most probably isn't either. So why waste processing cycles (and energy) on encrypting the ISO again and again - since https uses unique session keys - for each and every download ?

---

### Post by coffeecat on 2018-04-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by The Cog on 2018-04-04
I think the answer is that the packages are all signed. So there is no chance of a corrupt (accidental or deliberate) package being installed, and I don't think anyone is really concerned about the possibility of an eavesdropper knowing which packages you are downloading. I don't know how much overhead using HTTPS would impose, but there must be some work involved.

---

### Post by Skaperen on 2018-04-08
i'm curious why you think HTTPS is necessary.  as one of those people that verifies data integrity with a checksum. i can say it rarely fails.  it did for me, once, so i downloaded again and got exactly the same error.  i downloaded at my server and got a good copy.  i downloaded that from the server and it was still good at home.  i compared the two bad copies and they were identical.  i spent a while doing various compares of a bad one to the good one and narrowed it down to a block that had a bitstring of 9 0s squeezed to 8 0s.  it turns out i had a bad ethernet card (probably a marginal ... on the edge of bad ... unserializer clock) that produced lots of transfer lockups.  i replaced that card and all was well.  sure HTTPS would have fixed that.  i got the good transfer of that ISO via SSH.  another way to fix these issues is compression.  and i do see more compression these days.  but even though HTTPS would have prevented this i do NOT see this as justifying its use for EVERY transfer.  an *rsync* download with compression enabled could help. i suspect that bad packet just happened to have the same CRC (Crooked Rabbit Conspiracy) as the good one, but i ended my research after a couple hours on it.

---

### Post by junktext-0 on 2018-04-09
Hey all, great comments! I am glad others have chimed in to give their take on this topic. I agree that enabling HTTPS for a 1.5 GB ISO file would likely slam the servers pretty harshly by needing to essentially re-encrypt the same file over-and-over again to accommodate the unique session key for each user downloading the file.

However, I still do have a complaint. Looking further into how the Ubuntu website is laid out, the person downloading the ISO is not explicitly told that they should verify the file with GPG until *after* the download has begun and this notice is poorly placed at the bottom of the [page]("https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.4&architecture=amd64"). The reason I worry about this is that without HTTPS, a man-in-the-middle (MITM) attack could be conceivable whereby an attacker has the victim to download a tampered version of the ISO. In this case, the victim goes ahead and essentially installs a forever-rootkit unless the victim specifically goes through the [painful process]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu") to: 

1. Hunt down the SHA checksums for the ISO.

2. Grabs the latest Ubuntu GPG signing key. 
 [I]   (The Ubuntu guide [recommends doing this via command-line]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#2"). But, not every person already 
     has GPG installed or knows how to use/understand the command-line. For example, the majority 
     of Windows and Mac users are in this category. So, I assume this is where most newbies give up.)[/I]

3. Verifies the signature of the checksums.

4. Finally uses the SHA checksums to verify the ISO.

Basically, if we want people to ensure they haven't downloaded a malicious ISO, then the suggestion to "[Verify your download]("https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.4&architecture=amd64")" should be in a [COLOR=#ff0000][FONT=arial\ black]bright red font[/FONT][/COLOR] that is placed prominently on the [initial download page]("https://www.ubuntu.com/download/desktop") for Ubuntu.

For what it's worth, I am suggesting this as I am a happy Ubuntu user that wants to keep the system safe for others. Also, I apologize if I seem a bit whiny, as I do appreciate that a process exists which utilizes GPG and doesn't just rely on the SHA hash checksums alone. I just highly doubt that most people downloading Ubuntu gets why it is important to verify the ISO with GPG+SHA, especially if they are a first-time Linux user.

Thanks,

  --William

William Paul Liggett
[https://junktext.com](https://junktext.com)

---

### Post by mastablasta on 2018-04-10
That suggestion should be sent to Cannonical not to other users. 

Also i don't think MITM works like that. you can't just insert stuff into file download. the "insecure" part is just that others can see it.

also there was a case not long ago with Linux mint where malicious iso files were loaded on server.:
[https://blog.linuxmint.com/?p=2994](https://blog.linuxmint.com/?p=2994)

---

### Post by junktext-0 on 2018-04-26
Thanks for the feedback, mastablasta. Well, I don't use these forums that much but I assumed Canonical representatives read and respond to threads since the forum is listed as a main link on their home page and this forum can be logged into via the [Ubuntu single-sign on (SSO)]("https://login.ubuntu.com") process. Anyways, if not, I apologize as my concern is more directed at Canonical (and not community helpers), but Canonical should make this more obvious, especially since I assumed the forums were like their presence on Freenode's IRC server, which is an official support channel.

Nonetheless, with a MITM attack, they don't need to stuff anything into a file download. The download link can simply be redirected to the attacker's malicious ISO file, which can be pretty easy to do if the victim has been attacked through a "man-in-the-browser" (MITB) [e.g., a hostile browser add-on]. Or even a low-grade, old school attack where the "hosts" file has been tampered with can easily redirect the "releases.ubuntu.com" link. Don't believe me? Here's some proof (feel free to try it on your system):

**1.** I modified my **/etc/hosts** file to now contain:[COLOR=#ff0000]
194.150.169.131[/COLOR]   [COLOR=#008000]releases.ubuntu.com[/COLOR]

**2.** Now, when I point my web browser to Ubuntu's ISO download link ([http://releases.ubuntu.com/16.04.4/ubuntu-16.04.4-desktop-amd64.iso](http://releases.ubuntu.com/16.04.4/ubuntu-16.04.4-desktop-amd64.iso)), I am sent to Phrack.org ([COLOR=#ff0000]194.150.169.131[/COLOR]). All they (Phrack) would need to do on their side is to add a malicious ISO called "ubuntu-16.04.4-desktop-amd64.iso" under a "16.04.4" folder on their server. [Note: Phrack is just used as an example, as they are a legitimate hacking/phreaking magazine and not some evil resource. ]

**3.** Boom. You are now running a forever-rootkit! 
 
So unless the ISO has been verified with GPG+SHA, we're all just hoping that nobody becomes a victim.

--William

William Paul Liggett
[https://junktext.com](https://junktext.com)

---

### Post by flocculant on 2018-04-26
Here you go:

[https://rt.ubuntu.com/Ticket/Create.html?Queue=1](https://rt.ubuntu.com/Ticket/Create.html?Queue=1)

That's where to report this.

I'd be surprised if they'd never thought of it ...

---

