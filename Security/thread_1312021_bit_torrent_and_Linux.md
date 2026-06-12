---
title: "bit torrent and Linux"
date: 2009-11-02
forum: Security
---

### Post by ub9876 on 2009-11-02
can p2p be bad news for a linux machine also...?
which one would you use with Jaunty..?  elaborate please..

---

### Post by unamanic on 2009-11-02
What do you mean by bad news?
I use either transmission or ktorrent depending on my mood for desktop environments that day.  

If youre asking about frostwire, etc.  You won't get a virus from it, but any applications that abitrarily shares all files in a directory can be bad news from the "oops, I just showed my tax return to the world" kind of way.

---

### Post by Dark_Stang on 2009-11-02
> **unamanic said:**
> If youre asking about frostwire, etc.  You won't get a virus from it
Oh yes you can. It would be incredibly easy to write a virus for any OS provided the end user is dumb enough to run something they got from an untrusted source. If they give it their root password they're even dumber.

---

### Post by rookcifer on 2009-11-02
> **ub9876 said:**
> can p2p be bad news for a linux machine also...?
which one would you use with Jaunty..?  elaborate please..

It's only bad if you download malicious things that you allow to execute as root.  The nice thing about Linux, though, is that it makes doing this accidentally very difficult.

---

### Post by unamanic on 2009-11-02
You "can" but you won't, at least not until Google release chrome desktop and running Linux becomes as cool as the iPhone (even if people won't know it). Linux is still a small target compared even to Mac.

---

### Post by Dark_Stang on 2009-11-02
> **unamanic said:**
> You "can" but you won't, at least not until Google release chrome desktop and running Linux becomes as cool as the iPhone (even if people won't know it). Linux is still a small target compared even to Mac.

> **rookcifer said:**
> It's only bad if you download malicious things that you allow to execute as root.  The nice thing about Linux, though, is that it makes doing this accidentally very difficult.
Our community is getting too comfortable with things like this. What if the download searches for all available network shares and starts deleting everything it has permission to, then deletes everything in your home directory? It doesn't take administrative permission to do that.

---

### Post by unamanic on 2009-11-02
> **Dark_Stang said:**
> Our community is getting too comfortable with things like this. What if the download searches for all available network shares and starts deleting everything it has permission to, then deletes everything in your home directory? It doesn't take administrative permission to do that.

Honestly, the most likely "attack vector" to someone wanting to do harm to linux noobies is right here, answering a question with "sudo rm -rf [some system file]".  Yes, we must educate new users not to run things that they do not trust, that running executables from frostwire is stupid.  To understand commands before they enter them.  But to vilify an entire technology because some users use it to distribute malware is wrong.  But you are not going to get an mp3 from your favorite (CC liscensed) band from frostwire that will eat your children.

---

### Post by Dark_Stang on 2009-11-02
> **unamanic said:**
> Honestly, the most likely "attack vector" to someone wanting to do harm to linux noobies is right here, answering a question with "sudo rm -rf [some system file]".  Yes, we must educate new users not to run things that they do not trust, that running executables from frostwire is stupid.  To understand commands before they enter them.  But to vilify an entire technology because some users use it to distribute malware is wrong.  But you are not going to get an mp3 from your favorite (CC liscensed) band from frostwire that will eat your children.

Oh no, I will admit, I am a huge pirate. However I also feel as though I'm very knowledgeable, or at least very paranoid, when it comes to those things. Blanket statements like "You will not get a virus through p2p software for Linux" makes me want to make and spread viruses for Linux through p2p software to prove a point.

---

### Post by unamanic on 2009-11-02
> **Dark_Stang said:**
> Oh no, I will admit, I am a huge pirate. However I also feel as though I'm very knowledgeable, or at least very paranoid, when it comes to those things. Blanket statements like "You will not get a virus through p2p software for Linux" makes me want to make and spread viruses for Linux through p2p software to prove a point.

Agreed, thinking about it, a malicious cedega package would spread like wild fire.

/me starts writing "I will not make blanket statments" 100 times on the chalkboard

---

### Post by rookcifer on 2009-11-03
> **Dark_Stang said:**
> Our community is getting too comfortable with things like this. What if the download searches for all available network shares and starts deleting everything it has permission to, then deletes everything in your home directory? It doesn't take administrative permission to do that.

To what end?  Criminal enterprises who create sophisticated malware for Windows do it for profit -- they want your credit card numbers and banking info.  Simply deleting files in /home does not serve any purpose whatsoever.

---

### Post by cariboo on 2009-11-03
@Dark_Stang

If you can create a virus or worm that will work on a linux distribution without user intervention, you will be rich and famous and in jail in no time. :)

Remember, quite a bit of the internet runs on Linux as well as many embeded devices. Linux may be a bigger target than Windows, if you go by the number of installations.

---

### Post by Lars Noodén on 2009-11-03
@ ub9876 : transmission is popular, but there are many others to choose from.  

If you are worried about locking it down, you can try building an SE Linux policy around it so it only accesses what it is supposed to.  It wouldn't hurt to run it as a separate user virtually without privileges. Systrace would be another option if it were in Karmic repositories.   

The only real, IMHO, drawback to torrents, is that there is not a standard way yet to throttle incoming streams.  So it ends up competing for bandwidth  against your other activities and slowing down other loads.  Say you have a torrent leeching and are surfing the web.  It'd be nice for the incoming web page to knock the torrent down and take away all or most of its bandwidth for the duration of the page download.  That would make the torrent's load invisible to the user.

---

### Post by Dark_Stang on 2009-11-03
> **cariboo907 said:**
> @Dark_Stang

If you can create a virus or worm that will work on a linux distribution without user intervention, you will be rich and famous and in jail in no time. :)

Remember, quite a bit of the internet runs on Linux as well as many embeded devices. Linux may be a bigger target than Windows, if you go by the number of installations.
It wouldn't be a worm, that would be pretty hard. However making a virus that spreads via P2P is extremely easy. Many windows viruses do this. I see very few viruses that spread without User interaction on windows these days. The majority of what I see on a daily basis are infections from P2P and infections from exploits in web browsers.

Also, I don't see how I'd go to jail. If somebody downloaded it via P2P and ran it then it's their own stupid fault. What are they going to say? "I thought I was downloading Photoshop for freez and instead I got a virus!"

---

### Post by cariboo on 2009-11-03
What I was saying is if you could create a Linux virus that could spread without user interaction, you would be famous in no time.

BTW the way we frown on piracy in the forums, so please don't talk about illegal activities here. If you want to talk about your prowess as a software pirate, don't do it here.

---

### Post by __p1n__ on 2009-11-03
There's a service that "peeks" at packets on the network stack while they're still in PRE state i.e. before most netfilter points and definitely before it's routed.

This target occupies 100% of my linux network fuzzing focus.

---

### Post by Joe of loath on 2009-11-03
A self replicating virus is entirely possible. It runs, scans the firefox cache for credit car numbers etc uploads them to its botmaster, edits the .torrent for a torrent you're running (OR does the MSN virus thing and mails itself to everyone on your buddy list) and adds itself to the upload queue. All that can be done without root permissions, although it would have to be run in the first place.

Wouldn't work on servers though ;)

---

### Post by rookcifer on 2009-11-04
> **Lars Noodén said:**
> @ ub9876 : transmission is popular, but there are many others to choose from.  

If you are worried about locking it down, you can try building an SE Linux policy around it so it only accesses what it is supposed to.  It wouldn't hurt to run it as a separate user virtually without privileges. Systrace would be another option if it were in Karmic repositories.   

Good luck with trying to sandbox user level apps with SELinux.  No one has yet to even find a half-way reliable way to confine Firefox.  There is, however, something in SELinux called "sandbox -x" which basically allows for the creation of a sandboxed temporary user on the machine, but it's far from perfect due to a number of reasons I don't feel like going into.

A better choice would be to profile it with AppArmor.

> The only real, IMHO, drawback to torrents, is that there is not a standard way yet to throttle incoming streams.  So it ends up competing for bandwidth  against your other activities and slowing down other loads.  Say you have a torrent leeching and are surfing the web.  It'd be nice for the incoming web page to knock the torrent down and take away all or most of its bandwidth for the duration of the page download.  That would make the torrent's load invisible to the user.

QOS?

> **Dark_Stang said:**
> It wouldn't be a worm, that would be pretty hard. However making a virus that spreads via P2P is extremely easy. Many windows viruses do this. I see very few viruses that spread without User interaction on windows these days. The majority of what I see on a daily basis are infections from P2P and infections from exploits in web browsers.

Exploits in web browsers do not require user interaction.  These are commonly referred to as "drive-by downloads" meaning the user only has to visit a site to become infected.  And don't give me the "stay away from porn sites and you'll be OK" argument because many highly popular and typically benign sites have become infected with malicious scripts, etc. *[I] No site*[/I] is safe anymore.  

Drive-by downloads are not effective on Linux because most Linux machines are ran with limited privileges.  On the other hand, most Windows machines ware still being ran with full admin privs meaning one can easily be pwned even without doing anything other than browsing what are thought to be reputable sites.  And it is doubtful this paradigm will change much even with Windoze 7 because most people will either turn UAC off or just run from an admin account anyway.

---

### Post by Jekshadow on 2009-11-04
This does require root privileges (ironically), but if you chrooted Frostwire to someplace like /home/bob/frostwire, it could only delete anything in /home/bob/frostwire, if you did not run it as root within the chroot. It may be a semi-complex setup (making sure it can find the libs and config files), but it would be very secure.

This should protect your files as well.

Another option would be to create an image file, mount it without execute permissions on something like /home/bob/TorrentDownloads. The no execute would prevent anything malicious from running on your system from Frostwire, unless you moved it to your normal home directory.

---

### Post by lovinglinux on 2009-11-04
See the Security section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

