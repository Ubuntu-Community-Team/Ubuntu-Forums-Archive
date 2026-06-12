---
title: "Need help regarding Skype security on Linux ?"
date: 2016-05-20
forum: Security
---

### Post by mark284 on 2016-05-20
Hi guys. So basically I don't trust microsoft as far as I can throw them and I do use Skype the Linux version 
to keep contacts. I know that they spy on all conversations and all that nonsense. Do you guys know of any tricks 
they may do as regards to backdoors or trying to break into my computer using rootkit technique's ?? Thanks.

---

### Post by TheFu on 2016-05-20
Skype is distributed as a binary.  That means they have complete control over the system with the same capabilities that the userid running it provides.  It could have a keylogger that captures all keystrokes, then use that to gain sudo access and completely own the system going forward.

This isn't just MSFT - any program you install (binary or script) could do the same thing. No rootkit needed.

Basically, if you don't trust the source for anything you allow to run on your computer, then pretty much anything can happen.  This isn't just binaries or scripts running, but flash, javascript, and other inputs to other tools that can break out.  This is why staying patched and using tools only from trusted sources is so very important.  It is all that we can do, though perhaps it is not enough for the truly paranoid - or anyone really concerned.

---

### Post by Habitual on 2016-05-23
> **mark284 said:**
> Do you guys know of any tricks they may do as regards to backdoors or trying to break into my computer using rootkit technique's ?? Thanks.
That's quite a leap.
How do you get from "they spy on all conversations" to backdoors?

Their software, their rules.

---

### Post by TheFu on 2016-05-24
For simple voice, chat, screen sharing and talking-head video, try [https://talky.io/](https://talky.io/) .  Browser-based using javascript and WebRTC, so Firefox, Chromium and Chrome work - perhaps Opera.  No real security, but if you create a fairly unique "room name", unlikely any strangers will join.  Think there is a 15 connection limit for each room.  I know it works with Chromium.  My firefox is locked down too much for talky to work. Don't know about the others.

Is this more secure than Skype?  Hard to say - in theory, yes because browsers should keep webrtc and javascript contained, but we all know that the complexity of browsers is so great that I wouldn't bet on that.

---

### Post by gordintoronto on 2016-05-26
The truth, Mark, is that you're just not that interesting. Nobody spies on your conversations, because it would be a waste of time. The exception would be if you have been identified as a threat to national security, and then it would be the government, not Microsoft.

---

### Post by TheFu on 2016-05-26
> **gordintoronto said:**
> The truth, Mark, is that you're just not that interesting. Nobody spies on your conversations, because it would be a waste of time. The exception would be if you have been identified as a threat to national security, and then it would be the government, not Microsoft.

[https://en.wikipedia.org/wiki/Skype_security#Eavesdropping_by_design](https://en.wikipedia.org/wiki/Skype_security#Eavesdropping_by_design) and the next section, *Flaws and potential flaws*,  provide a different view.  Any service provider can monitor their traffic and inspect the services.

I don't know how interesting Mark may or may not be. ;)  Most people are very interesting, IME.

---

### Post by atl45 on 2016-05-30
Skype is proprietary software. As Habitual said above, "Their software, their rules." Since no one (other than Microsoft) has access to the code, no one knows exactly how any backdoors might be implemented, and knows far less how to counter them. FYI, it is claimed that it was the Skype development team that installed backdoors PRIOR to being bought out by Microsoft.

@gordontoronto, that is one of the most absurd claims I can ever imagine being posted on a security forum: It either shows that you have a limited understanding of how algorithms work, at best, or that your purpose here is a malign one. 'If you have nothing to hide, you have nothing to fear": Is that it? Are you being deliberately ignorant of the fact that evidence wholly contrary to your statement is on the public record? Whether you agree with ES's motives or not, the documents he leaked dismantle your claim in its entirety, as do the laws on the statute books. Bulk surveillance is not some dystopian fantasy; it is a real and present reality. Apologies if I missed any irony in your post.

To the OP, unfortunately I can't recommend a desktop alternative to Skype. The Tox.im project appears to have disintegrated amidst accusation and acrimony. Jitsi is proffered as a VOIP client with e2e encryption. It is opensource. However, the development team (to the best of my knowledge) don't publish a public key, nor any signatures for their source. There has been a limited dialogue concerning this on Github but no resolution to date so far as I can tell. I've asked a number of times in their irc channel for keys/sigs and received no response. All I can say is that I'm dubious about a project dedicated to secure communications that pleads ignorance when it comes to the need for reliable verification tools (if the team is competent enough to write encryption software then it is competent enough to provide a means of verifying that software). If anyone here has broader knowledge of the Jitsi project then please interdict me.

You might consider voice chat software as an alternative for talking with friends on desktop. Mumble is open source and the Mumble team publishes its own public key and sigs - see [https://wiki.mumble.info/wiki/Main_Page](https://wiki.mumble.info/wiki/Main_Page) .

The best Android alternative, imo, is Signal, by OpenWhisper Systems. I can't recommend an alternative for iOS, and would not recommend an iOS device to anyone concerned about privacy in any case (but that is for another discussion). Android keeps me busy enough as it is but is easier to workaround.

---

### Post by TheFu on 2016-05-30
Another option is to only use skype inside a VM or a chroot or a container that is locked down.  There are tools that make GUI chroots possible under Ubuntu with a config file that chooses which kernel options are available.  The chroot/container options share the same kernel, but can prevent anything from being written to the normal file system - sorta like browser "private" modes that cannot be overwritten by a bug in the browser (which happens lots).  Cannot see why running skype inside one of these "private" chroots wouldn't work too.  

Can't recall the name of the tool I'm thinking of right now.   It is in the Ubuntu 16.04 repos (not 14.04) - starts with fire.....  Of course, this doesn't prevent anything bad in skype from still happening, but it does limit what damage can happen since you can control what is read-only and what isn't allowed to be accessed at all for the entire environment. Let me try to find that tool ....  **firejail** is the name.  It requires a fairly recent kernel since the file system stiff wasn't added until 3.18+.   I've only played with it for about 10 minutes, so it may not be useful - or it might be exactly what folks need.

---

### Post by Habitual on 2016-05-31
Check out [Wickr]("https://www.wickr.com/security#encryption")

---

### Post by zerubbabel on 2016-06-29
> **atl45 said:**
> The Tox.im project appears to have disintegrated amidst accusation and acrimony. 

Perhaps this is worth revisiting. I've been using Tox via the qTox client for several months now and have found it to be quite nice and stable, and presumably more secure than Skype, though I am no expert in cryptography. I'd like to know what others more knowledgeable think of it.

---

