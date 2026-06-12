---
title: "Is it safe to use software not maintained by Canonical?"
date: 2010-03-13
forum: Security
---

### Post by jochem on 2010-03-13
I've been using ubuntu for some time now, but I still don't know exactly how safe it is to use software from the Ubuntu software center, but not maintained by canonical. 

Obviously, installing random .deb packages from the interwebs isn't really safe, it may contain malicious code.

But how is this with software, presented to my by the Ubuntu software center, maintained by users?

How and by who is the software checked? When are packages accepted to the software center?

How safe are PPA packages? I'm using the chromium PPA, is this actually safe?

Thanks in advance

---

### Post by MarkC502 on 2010-03-13
YES, if from a known source. Authors with websites or sourceforge pages etc would not last a month providing malware for linux in the name of a useful app. As long as the projects are open source it is a waste of a hackers time.  Why would someone code a linux app as malware when they could just go down to the local coffee shop and Mitm or sidejack everyone in 10 seconds and start collecting logins CC details etc. Or if botnet creation is the goal windows malware is much easier to both write and deliver to the target ( Mostly due to the "targets" being completely computer illiterate )  The plain cold fact is that Linux is quite secure factory stock, that said you can still be exploited rather easily when using WIFI or a wired network which you do not control the router. These dangers are due to flaws in the network protocols used and not the operating system in particular, hence Ubuntu uses the same networking protocols as Mac OS and Windows.  So just Google anything before you add it to your repositories or install it manually and always obtain it from the authors site not some torrent etc and you will be fine.   Mark

---

### Post by aysiu on 2010-03-13
It's a false dichotomy. Things are not either dangerous or safe. Many so-called "dangerous" third-party repositories are likely to pose no threat at all. There's also a possibility (however miniscule) that the Ubuntu main servers (or its mirrors) could be compromised, so that even if you were using "safe" repositories then your system could be compromised.

I'm not saying you should be paralyzingly paranoid or overly complacent and smug. Just use common sense. The official repositories are generally safe. Anything else you should vet.

I remember until recently anyone would say "Oh, want a theme? Just go to gnome-look.org." Do you know why? Because it's a community in which artists can share their work with others, and others can enjoy the sharing. All it takes is one malicious contributor to upload a .deb posing as a theme and all of a sudden gnome-look.org isn't trustworthy any more. Well, actually it is for the most part, but you just have to be careful.

That's really the bottom line. Just keep in mind how things get done. The Ubuntu repositories are officially maintained by only select individuals allowed to upload .debs to it. Third-party repositories have varying procedures for how .deb packages get on there. Some may also have better audits than others. Some may have no audits but just trust for the individuals allowed to upload. Some will allow pretty much anyone to upload.

---

### Post by jochem on 2010-03-14
Thanks Mark and aysiu. From now on I'm just going to trust stuff from the software center. I went from windows to ubuntu mainly because it's considered a safer OS. I guess I just need a little more faith in humanity, some things (most of them :)) are just not within my control.

Marked as solved!

---

