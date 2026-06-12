---
title: "What are some uses for a server"
date: 2011-06-09
forum: The Cafe
---

### Post by ki4jgt on 2011-06-09
So, I was wanting to have my own server. What are some good uses for having one?

---

### Post by Joe of loath on 2011-06-09
Fileserver.
Webserver.
Music streaming server.
Torrent downloader.
IRC server.
Home automation.
CCTV server.
Backup server.

The list goes on :D

---

### Post by Macskeeball on 2011-06-09
USB printer sharing

VPN server, so that you can remotely access your home network while away from home, and in a secure manner. This would also give you an encrypted connection to use when you're on someone else's network, particularly open WiFi hotspots.

Non-server but still 24/7 type tasks, such as Folding@Home or another distributed computing project.

Hosting your own personal cloud computing: [http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/](http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/)

---

### Post by desktorp on 2011-06-09
Hosting Minecraft.
..okay hosting games in general.

---

### Post by PhillyPhil on 2011-06-09
I use mine for file backups, sharing files across my lan, media storage and viewing over the lan, bt downloading, and on rare occasions as a counter strike server.

In the future I'll look at making it a VPN server so I have access to my lan no matter where I am.

---

### Post by Irihapeti on 2011-06-09
I run several servers on my home desktop machine.

[LIST]
[*]apt-cacher-ng - so that I don't have to download updates multiple times

[*]webserver and blog (not accessible from the internet) for learning, and also for preparing new pages for a couple of sites I maintain

[*]ssh server - I have set up sshfs so that I can mount desktop folders on the laptop. That gives me extra encryption over wireless.

[*]small calendar server, not accessible from the internet
[/LIST]

---

### Post by Aquix on 2011-06-10
With you own server you could get of the cloud completely. No more dropbox, gmail, google docs and more. Have seen some nice tutorials for this.

---

### Post by ki4jgt on 2011-06-10
> **Aquix said:**
> With you own server you could get of the cloud completely. No more dropbox, gmail, google docs and more. Have seen some nice tutorials for this.

Dropbox replace sounds nice. They lost all my files last week. I emailed them about it and they said they'd fix it and my files are still missing :-(

---

### Post by Joe of loath on 2011-06-10
You can replace dropbox with sshfs, cron and rsync.

---

### Post by Copper Bezel on 2011-06-10
And that's where it gets *really* tempting for me - a personal cloud. A friend of mine refers to this as "stockpiling guns and food."

---

### Post by mips on 2011-06-10
Ftp server, nzb server, torrent box etc and don't forget about the porn :p

---

### Post by Thewhistlingwind on 2011-06-10
> **Copper Bezel said:**
> And that's where it gets *really* tempting for me - a personal cloud. A friend of mine refers to this as "stockpiling guns and food."

Normally when you "Stockpile guns and food" theres a reason (Or a system in place to make the stores serve as both a stockpile and a food supply at once.) so, is your friend one of those people predicting the cloud killing local storage? If so, LOL, that's not happening, especially when stuff like dropbox loses files all the time.

It's a backup at best.

---

### Post by Copper Bezel on 2011-06-10
>  so, is your friend one of those people predicting the cloud killing local storage?
Yeah, that was the shape of it.

Edit: To clarify, that's why it was funny in context - I was saying that I liked the idea of having my own cloud storage and such so as not to depend on services for the same, and she made the comparison to point out the silliness of the concern.

---

### Post by pricetech on 2011-06-10
There's always "Door Stop", "Wheel Chock", and "Boat Anchor", but I don't think that's what you're after.

Hey it's the cafe, don't get offended.

---

### Post by Macskeeball on 2011-06-10
> **ki4jgt said:**
> Dropbox replace sounds nice. They lost all my files last week. I emailed them about it and they said they'd fix it and my files are still missing :-(

Maybe it was your client that went wonky rather than something on their server. If so, you may be able to use the web interface to restore those previous contents.

---

### Post by hakermania on 2011-06-10
Well, they may be more personal reasons so as to use a server.
For example, I use one because im developing a open source project and im sending and receiving the source all the time between my folks, so I made a server and a script which updates the source being on the server so as to be always updated and ready for downloading!

---

### Post by Thewhistlingwind on 2011-06-10
> **pricetech said:**
> There's always "Door Stop", "Wheel Chock", and "Boat Anchor", but I don't think that's what you're after.

Hey it's the cafe, don't get offended.

The amount of things you can do with a server make you sound more uninformed then offensive.

Don't get so angry about it, it's just the cafe after all.:D

---

### Post by ki4jgt on 2011-06-10
> **Macskeeball said:**
> Maybe it was your client that went wonky rather than something on their server. If so, you may be able to use the web interface to restore those previous contents.

Already tried it. No good. I see the folder they were in, but it says and I've checked. It's empty :-( I had 5 coding projects, The next release of the main program that my site (mainly) offers, and a very personal document that I had written. I wanted to share it later with someone else, but it's gone now :-(
I know they still have the files, b/c the public links I copied from the site still work, but they're no longer in my account.

---

### Post by Dustin2128 on 2011-06-10
Free web hosting- get a co.cc address and you're set.

---

### Post by Macskeeball on 2011-06-10
I was under the impression that Dropbox used a version control system in addition to the up-to-date set of files, and that users could restore previous versions of files? You don't even have that? Wow.

This is what I'm talking about: [http://www.dropbox.com/help/11](http://www.dropbox.com/help/11) See the "show deleted files" section.

---

### Post by ki4jgt on 2011-06-10
wait a minute guys LOL. . . It's actually been a year (not a month) just wrote a month, but it's box.net, not drop box.

---

### Post by Macskeeball on 2011-06-10
Ah, that's an important piece of information to get right. Otherwise you end up spreading FUD about a service that had nothing to do with your problem. I feel bad for you having lost data, but please try to be accurate in your commentary. As a future tech journalist, I place a high value on that.

Anyway, with Box.net it looks like you're out of luck. That sucks. :(

[quote="Box.net support document: [ Using the Trash](http://support.box.net/app/answers/detail/a_id/126/kw/deleted)"]Box.net features a Trash, that allows you to recover files and folders that have been deleted. By default all deleted items will be moved the the Trash location of your account and will be **purged after 30 days**. This purge period can be customized by administrators on Business and Enterprise accounts.[/quote]

---

### Post by lisati on 2011-06-10
I set up my own server partly because the free web hosting service I was using was no longer free, and partly because I got fed up with the way a well known free email provider (whom my ISP uses) handles spam. :D

---

### Post by pookiebear on 2011-06-11
throw a big ATI card in it and farm bitcoins. while it is idle

---

### Post by Ctrl-Alt-F1 on 2011-06-11
> **Dustin2128 said:**
> Free web hosting- get a co.cc address and you're set.

I think that a professional looking .com or .net address is superior for the low low price of $0.84 a month ($10.00/year).  Some registrars are a lot cheaper than that even.

---

