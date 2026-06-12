---
title: "New Server  (new server user as well.) Maybe Too ambitious..."
date: 2010-06-01
forum: Server Platforms
---

### Post by schnerf on 2010-06-01
I've come to the point where I'm thinking of building a simple, small server. The current idea involves an old case with a new power supply, ram, hard drives, and for low electricity use, a mini-itx atom board (with two SATA ports).

What I want to do:
  1 - Two hard drives in software Raid 1 on the SATA ports to securely back up 
       A - about ten years of digital photos that are currently scattered across three computers and four hard drives.
       B - important documents (ideally encrypted)
  2 - Share over the network an HP 1000 Laser Printer (USB)

Less importantly:
  3 - possibly over a usb drive (to improve reliability on the RAID drives) share music files, video files, the occasional data file, etc, that doesn't need the security and redundancy of the RAID drives
  4 - Have some sort of http based frontend to the printer. This is a gorgeous, effective printer, but it can be a serious pain to make it work: it has no drivers for Windows Vista (I have one of those) or for Windows 7 (No, but possible in the future), and I haven't managed to make my Mandriva Netbook connect with it. My PDA doesn't have USB or drivers, my dad's android phone doesn't either, etc, etc, etc. What I'm imagining here may well not exist, but the idea would be that I'd pull up a rather basic HTML page (password protected?), with a button that lets me browse for a file on any given web-enabled device, upload it, and it will print on the printer. To really work well, though, it would have to be able to take, format, and accurately print an ODT file, a PDF, probably DOC, RTF, and a variety of other file formats. I don't know if this exists.

For all of these things, it doesn't need any contact with the internet - so locking it down to be inaccessible from the other side of the router might be nice. I don't know how to do that - or even if it'd be advisable, as I might also want to set up notifications along the lines of "the disk is almost full", "the Internal temp is too high", or "I've just been reset" to be sent over email/sms to my cell phone. But security would be a major concern.


So what I'm looking for: 
 How foolhardy is this as a plan?
 Any suggestions?
 Are there any annotated tutorials I can follow for any of these things? I'm not exactly that good at any of this server stuff, but I can learn - and that's why annotations are good.
 I have suspicions that the web-based printer front end is either a complete pipe dream, foolish beyond all reason, OR, has been done for five years now, and why haven't I heard of it. Which is it?

---

### Post by JDorfler on 2010-06-01
It's easier than you think.  Not too sure about the http printer thing, but I have my server doing the following;

[LIST=1]
[*]Proxy/Adblock service (Squid)
[*]Jabber Server (Jabberd2)
[*]UPnP/DLNA Share (Mediatomb)
[*]DAAP Share (Firefly, AKA mt-daapd)
[*]Print Server (Just shared it out via printing under administration.)
[*]File Sharing/Storage (SAMBA)
[*]Transcoder (Handbrake)
[*]And just typical downloading/bittorrenting through Firefox/Transmission to share downloads of large files.
[/LIST]

I recommend going [here]("https://help.ubuntu.com/10.04/serverguide/C/index.html") and [here]("https://help.ubuntu.com/community/Servers") for a good start.  Right now looking to see what I can do to make a mail collection server as well on this thing.

---

### Post by HermanAB on 2010-06-02
Very easy to do actually.  On Mandriva or Suse you can do all of that at the click of a few mouse buttons in about 5 minutes.  

On Ubuntu, it may take a few days to set up, if you don't quite know what you are doing yet.

---

### Post by srivo on 2010-06-02
For the HP 1000, here is a little how-to. I was never successful in the past in installing that printer with the HP driver already in ubuntu same for SUSE.

Step:
0- Look if it works with the actual ubuntu driver, if it don't follow the next few step
1- Remove the actual HP driver in ubuntu with synaptic (HPLIP and other HP driver)
2- Reboot ubuntu
3- Go to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and follow the instruction

---

### Post by WinstonChurchill on 2010-06-02
You really don't need to put your music files on a separate USB drive... even if you've got a stupidly big music collection, you can get two 1.5TB HD's for $200 if you shop around, and 1.5 TB is a massive amount of space. Plus, RAID 1 will get you better read performance, so unless something you're doing needs to constantly read like 100+ MB/s off the hard drives, you don't need to worry about conserving resources.

---

### Post by schnerf on 2010-06-03
Well, I suspect that the read performance will be limited more by network speed than hard drive read speed - the RAID is intended to give the storage with non-replaceable photos as high of reliability as possible. 

As I might use the USB drive to hold video files in a upnp style thing, yes, consistent 100+ MB reads are possible and likely.
Since my movies/tv shows/music are on dvds/cds, they're rather easily replaceable. That's more a convenience thing.

---

