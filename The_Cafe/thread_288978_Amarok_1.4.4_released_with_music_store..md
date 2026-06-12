---
title: "Amarok 1.4.4 released with music store."
date: 2006-10-30
forum: The Cafe
---

### Post by plb on 2006-10-30
[http://amarok.kde.org/](http://amarok.kde.org/)

---

### Post by Anonii on 2006-10-30
Its gonna rock, and its gonna rock hard.

Pity for us, GNOME users :(

[http://amarok.kde.org/content/view/84/66/](http://amarok.kde.org/content/view/84/66/)

---

### Post by Lord Illidan on 2006-10-30
You can still use it with GNOME



EDIT : as pointed out by Steveire, you should do this first

 ```
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg]("http://people.ubuntu.com/%7Ejriddell/kubuntu-packages-jriddell-key.gpg")
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

For edgy users, just add this to your sources.list.
```
 deb [http://www.kubuntu.org/packages/amarok-144](http://www.kubuntu.org/packages/amarok-144) edgy main
```

I am downloading right now...I love these guys!

Obligatory screenshot ... with MagnaTunes sidebar

---

### Post by peak_performance on 2006-10-30
Great, installing it as I write! Can't live without the keyboard shortcuts Amarok fixes per default :D

---

### Post by Anonii on 2006-10-30
> **Lord Illidan said:**
> You can still use it with GNOME

For edgy users, just add this to your sources.list

deb [http://www.kubuntu.org/packages/amarok-144](http://www.kubuntu.org/packages/amarok-144) edgy main

I am downloading right now...I love these guys!

Obligatory screenshot ... with MagnaTunes sidebar
I really dont want Qt libs running along with my GTK. Not for performance (3.2GHz and 1GB ram wont really feel it.), but I want to feel KDE free, since I selected GNOME, yes, I'm a weirdo.

---

### Post by Steveire on 2006-10-30
Actually, you should do this first:
```

 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

```
so that you don't get untrusted packages issues.

---

### Post by Lord Illidan on 2006-10-30
> **Anonii said:**
> I really dont want Qt libs running along with my GTK. Not for performance (3.2GHz and 1GB ram wont really feel it.), but I want to feel KDE free, since I selected GNOME, yes, I'm a weirdo.

Yes, you're a weirdo *shakes head sadly*

Performancewise, no you won't feel it. Firefox takes up more memory than Amarok, beagled, likewise. Here is a shot to show you.

Feel KDE free? Why? Is KDE bothering you? It's not even a case of closed source vs opensource..it's just weirdness on your part. Amarok is not KDE, it's just an app with the QT widgets.

---

### Post by Lord Illidan on 2006-10-30
> **Steveire said:**
> Actually, you should do this first:
```

 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

```so that you don't get untrusted packages issues.

Thanks, edited previous post.

---

### Post by Anonii on 2006-10-30
> **Lord Illidan said:**
> Yes, you're a weirdo *shakes head sadly*

Performancewise, no you won't feel it. Firefox takes up more memory than Amarok, beagled, likewise. Here is a shot to show you.

Feel KDE free? Why? Is KDE bothering you? It's not even a case of closed source vs opensource..it's just weirdness on your part. Amarok is not KDE, it's just an app with the QT widgets.
you just won a charisma roll against mine (specificaly, you rolled 17, I rolled 8 (Modifiers not applied.)). I'll be sure to try this Amarok's version, tomorrow. BTW, Qt programs dont run flawlessly, as far as the interace is concerned, in GNOME, right (Including *turay integuration* (Japaaaan is suppeeeriooor), window borders etc.)?

---

### Post by SunnyRabbiera on 2006-10-30
Amarok is awesome no doubt in my opinion.
Amarok is very itunes like and I like it much better then gnomes Rhythmbox, Rhythmbox is no where close in my book sorry to say.

---

### Post by ComplexNumber on 2006-10-30
> **Anonii said:**
> BTW, Qt programs dont run flawlessly, as far as the interace is concerned, in GNOME, right?
no, they tend to crash often. gnome programs run much more smoothly in kde than kde/qt programs run in gnome. part of the reason is to do with kde's philiosophy of "do everything the kde way" whereas gnome has always been more considerate and friendly towards other environments. this is further exemplified by gnome being much quicker to embrace common standards set forth by the portland-project/freedesktop.org.

---

### Post by DJ Wings on 2006-10-30
Ooooh God... I think I'm going to pass out. This is just too much. Now, amaroK COMPLETELY blows iTunes out of the music-management water.

---

### Post by chaosgeisterchen on 2006-10-30
They run flawlessly. Proved.

---

### Post by darkhatter on 2006-10-30
:confused: :confused: :confused: maybe I'm just weird but I run gtk and qt programs in kde and gnome and they run the same...

=P~ I'm getting my copy now

---

### Post by DJ Wings on 2006-10-30
The Kubuntu package is for 1.4.3 only. You have to compile it from source.

---

### Post by darkhatter on 2006-10-30
:(

---

### Post by Lord Illidan on 2006-10-30
> **DJ Wings said:**
> The Kubuntu package is for 1.4.3 only. You have to compile it from source.

Unless u have Edgy, read my previous post..

lol @> you just won a charisma roll against mine (specificaly, you rolled 17, I rolled 8 (Modifiers not applied.)). I'll be sure to try this Amarok's version, tomorrow. BTW, Qt programs dont run flawlessly, as far as the interace is concerned, in GNOME, right (Including *turay integuration* (Japaaaan is suppeeeriooor), window borders etc.)?Aye, I know they dont' run 100% correctly, but the Portland project might fix it, hopefully.. never let widget etc, get in the way, hehe.

What I don't like about this release is how they squeeezed another vertical tab into it, otherwise, it is really nice.

---

### Post by spockrock on 2006-10-30
shame that the daap doesnt work in gnome....... :(

---

### Post by mrgnash on 2006-10-30
Awesome news :) But I'm a weirdo too.. is there any way to theme it to match your GTK themes without installing all the rest of the KDE menagerie?

---

### Post by kircher on 2006-10-30
I installed Amarok when I was using dapper, and I'm sure the KDE libraries downloaded automatically. I can't remember whether I used apt-get or synaptic, but I was able to do it without downloading the KDE libraries manually. Perhaps it's different with edgy and with Amarok 1.4.4. I use 1.4.3. I will wait a while to download 1.4.4. I have approached my download limit with my ISP, and my room mates can't handle web pages loading 3 seconds slower when the connection gets shaped to 128/128. I assume the Music store uses ogg/vorbis format?

---

### Post by Sushi on 2006-10-31
> **ComplexNumber said:**
> no, they tend to crash often. gnome programs run much more smoothly in kde than kde/qt programs run in gnome. part of the reason is to do with kde's philiosophy of "do everything the kde way" whereas gnome has always been more considerate and friendly towards other environments. this is further exemplified by gnome being much quicker to embrace common standards set forth by the portland-project/freedesktop.org.

Is it just me, or are you always, ALWAYS taking pot-shots at KDE? Every single time you participate in a discussion that is somehow related to KDE, you just HAVE to make some underhanded comments about how KDE sucks and how GNOME rules.

Honestly: it's getting very old, very fast.

---

### Post by GeneralZod on 2006-10-31
> **Sushi said:**
> Is it just me, or are you always, ALWAYS taking pot-shots at KDE? Every single time you participate in a discussion that is somehow related to KDE, you just HAVE to make some underhanded comments about how KDE sucks and how GNOME rules.

Honestly: it's getting very old, very fast.

No, it's not just you ;)

---

### Post by NoTiG on 2006-10-31
How hard would it be to write amarok in either GTK2 or mono though so gnome users can have it blend in better? I really like amarok but im not switching to kde for it. I really think its great and their blending with magnatune i think is a really perfect fit. Imagine if it was more portable, how popular it would be. THere should be a windows version too. (watch there already be one)

---

### Post by FISHERMAN on 2006-10-31
What's so special about this?
I can easily buy at Magnatunes (and in lots of other shops) with my browser.
I see no reason to switch to amaroK just for such a minor feature.
I understand why lots of people like amaroK(I don´t)but a build-in music shop that everybody can visit with a browser is nothing special.](*,)

---

### Post by stokedfish on 2006-10-31
Argh, too late...I'll post it anyway! ;)

> Amarok continues to blast ahead with release 1.4.4.

We're thrilled to be able to take our long association with Magnatune to new heights with the addition of an integrated DRM-free music store with full-length mp3 previews. Magnatune's "we are not evil" attitude guarantees that you can purchase awesome tunes and the artist receives half of the purchase price!
[amarok.kde.org](http://amarok.kde.org/content/view/84/66/)

Magnatune integration...another wise move from the Amarok devs! ;)

Actually, I'm not much for adding musicstores to audioplayers...but this time, it's great stuff! Why? First, it's done very well and doesn't come into your way when using the player. If you don't like the store, just turn off the tab and you won't notice a thing.

Second, I really like the Magnatune concept!

All files are completely DRM-free, no restrictions at all. You can listen to all their music right in the player, full-length. If you purchase an album, YOU decide how much you pay...just pick a value between 5-18 dollars. 50% goes to the band, 40% to Magnatune and 10% to the Amarok devs - a very fair deal in my eyes, especially for the artists!  

The Magnatune collection is still rather small, but of very high quality...they accept less then 10% of the artists that apply to be in their label. Right now, the store features 236 artists, 505 albums and 6710 songs - and you can listen to all those tracks right in your player, full-length, and in good quality...hah, I just love it! :D

Soo...update your Amarok guys! Kubuntu Edgy packages? [*click*](http://kubuntu.org/announcements/amarok-1.4.4.php) ;)

[img]http://www.dachboden-wg.de/ftp/pics/fish/magnatune5.png[/img]

[img]http://www.dachboden-wg.de/ftp/pics/fish/magnatune6.png[/img]

[img]http://www.dachboden-wg.de/ftp/pics/fish/magnatune7.png[/img]

[img]http://www.dachboden-wg.de/ftp/pics/fish/magnatune8.png[/img]

---

### Post by slimdog360 on 2006-10-31
evil or not evil, that music store looks pretty crappy. I understand most big name bands have 45000 licences on their music but still, that shouldnt stop people from being able to buy it.
One thing I hated was when I bought a coldplay single it would only let me rip it into wma format. I was shocked. I had to rip it using a couple of other tools.

---

### Post by Lord Illidan on 2006-10-31
Magnatunes might not look too good now, but only because we are comparing it to Itunes. On its own, it is a good idea, and one which will only improve in the future.

To all those who want Amarok in GTK, there are a couple projects, like Listen and Exaile, but in my experience, they are slower and somewhat lacking.

---

### Post by Magnes on 2006-10-31
I use Exaile (as an addition to Amarok) and in MY experience it's faster. And of course it's lacking some options - it's VERY new project.

---

### Post by kuja on 2006-10-31
> **NoTiG said:**
> How hard would it be to write amarok in either GTK2 or mono though so gnome users can have it blend in better? I really like amarok but im not switching to kde for it. I really think its great and their blending with magnatune i think is a really perfect fit. Imagine if it was more portable, how popular it would be. THere should be a windows version too. (watch there already be one)
Very. It's tied rather tightly to KDE, as KDE apps tend to be. [http://amarok.**kde.org**](http://amarok.kde.org). I know at the very least the Amarok devs happen to be working on Phonon for KDE4 as well.

---

### Post by skymt on 2006-10-31
> **Lord Illidan said:**
> What I don't like about this release is how they squeeezed another vertical tab into it, otherwise, it is really nice.

You know you can turn individual tabs off, right? Just right-click a tab and uncheck any you don't want.

---

### Post by Milos_SD on 2006-10-31
I compiled Amarok 1.4.4 last night. I had to download 30 - 40 packages via dial-up :( . It's very nice, but I don't have all features in amarok. When it will be in repositories for Dapper?

P.S. Again, sorry for my English. :)

---

### Post by kuja on 2006-10-31
> **Milos_SD said:**
> I compiled Amarok 1.4.4 last night. I had to download 30 - 40 packages via dial-up :( . It's very nice, but I don't have all features in amarok. When it will be in repositories for Dapper?

P.S. Again, sorry for my English. :)

If you were missing features, then its because you were missing (even more) packages than you realized. ./configure will tell you what things it can be built with, and which things you have installed. If you're interested in those other features then install the development libraries for those features and recompile amarok. I'm not sure if they'll continue creating dapper packages for software updates or not really. For the most part it shouldn't be neccessary for KDE though, seeing as much of it is already freezing development and refocusing efforts to KDE4.

---

### Post by natedawg on 2006-10-31
This is sweet, I love Amarok! I used Amarok to DJ an all night party with my friends last weekend and it worked like a charm. Its way better than itunes. 
The cross fading feature makes transitions to new tunes easy. The only problem I have ever had with amarok is the global hotkeys wouldn't detect my laptops media keys but for some reason it started working after a reinstall of edgy.

---

### Post by Skia_42 on 2006-10-31
<wets his oants> I never thought we would be seeing a music store for Linux so soon. looks sweet!

---

### Post by banjobacon on 2006-10-31
I was curious to see what if this had been mentioned in the Rhythmbox mailing list and was surprised to find that a Rhythmbox plugin has been in development for a few months now.

It seems to be slightly usable at this point. Links to more information:

[Bug in Gnome Bugzilla](http://bugzilla.gnome.org/show_bug.cgi?id=345783)
[Mailing list post](http://mail.gnome.org/archives/rhythmbox-devel/2006-October/msg00015.html)

---

### Post by sbassett on 2006-10-31
For those amarok nuts (me being one of those) who use the ipod with amarok, please vote on this bug to get this fixed asap. KDE has some issues reading the correct length of any VBR mp3 files. This is fine within amarok until you transfer them to your ipod, at which point they get cut short. This happens a lot with a particular podcast.

[BUG 130945]("http://bugs.kde.org/show_bug.cgi?id=130945")

---

### Post by slimdog360 on 2006-10-31
Ive just installed the new version of amarok from the repos and it seems to be going quite well,. The last time I  used it, it was too buggy.
But I cant seem to get the streaming music from magnatune. Has anyone been able to do this? It seems to buffer alright and says that its playing but I cant hear anything. 
Other music already on my computer works like a charm.

---

### Post by henriquemaia on 2006-10-31
This is great! Amarok is my #1 choice in music playing. Is there a way of getting this version on Dapper (without having to compile from source)?

---

### Post by slimdog360 on 2006-10-31
> **henriquemaia said:**
> This is great! Amarok is my #1 choice in music playing. Is there a way of getting this version on Dapper (without having to compile from source)?
[http://amarok.kde.org/wiki/Download:Kubuntu]("http://amarok.kde.org/wiki/Download:Kubuntu")

---

### Post by henriquemaia on 2006-11-01
> **slimdog360 said:**
> [http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

Thanks for the info, but the newest version is Edgy only. :) 

Let's see if someone else comes up with an upgrade for Dapper.

---

### Post by Lord Illidan on 2006-11-01
> **Magnes said:**
> I use Exaile (as an addition to Amarok) and in MY experience it's faster. And of course it's lacking some options - it's VERY new project.

Aye, I have no doubt that it will improve..but until now, i prefer Amarok.

---

### Post by chaosgeisterchen on 2006-11-01
> **kuja said:**
> Very. It's tied rather tightly to KDE, as KDE apps tend to be. [http://amarok.**kde.org**](http://amarok.kde.org). I know at the very least the Amarok devs happen to be working on Phonon for KDE4 as well.

So what? It's too clear to have it bound tightly to KDE as it is the main music player of the K-desktop. They will clearly strive to get perfect integration with Phonon, Plasma and the other modules of KDE4 as they want to release a breathtaking new application, amaroK 2.0, completely coded in Ruby which seems very interesting to me. Hopefully it's not lacking performance.

---

### Post by Lord Illidan on 2006-11-01
> **chaosgeisterchen said:**
> So what? It's too clear to have it bound tightly to KDE as it is the main music player of the K-desktop. They will clearly strive to get perfect integration with Phonon, Plasma and the other modules of KDE4 as they want to release a breathtaking new application, amaroK 2.0, completely coded in Ruby which seems very interesting to me. Hopefully it's not lacking performance.

Hope not, but it seems to be getting faster with each new release...

---

### Post by kuja on 2006-11-01
> **chaosgeisterchen said:**
> So what? It's too clear to have it bound tightly to KDE as it is the main music player of the K-desktop. They will clearly strive to get perfect integration with Phonon, Plasma and the other modules of KDE4 as they want to release a breathtaking new application, amaroK 2.0, completely coded in Ruby which seems very interesting to me. Hopefully it's not lacking performance.
I agree. That's more or less what I was trying to say, even though, Amarok is not the main player of KDE. Actually, Juk is, or was anyway. I'm looking forward to KDE4 and amarok2.0 as well. I didn't know they're moving towards ruby though. It should perform okay though, seeing as the API in use (kdelibs + qt4) is still all c++ code, and it does all the hard work.

---

### Post by puppy on 2006-11-01
Can I just add that in another thread there's a version 1.4.3 available that has MTP media player support added - 1.4.4 from the Amarok website doesn't have this support built-in - here's hoping for 1.4.5  ;)

---

### Post by maniacmusician on 2006-11-01
is there an allotted date for KDE4 to be released or are they just sort of going to release it whenever it's done? Can't wait...

---

### Post by GeneralZod on 2006-11-02
> **maniacmusician said:**
> is there an allotted date for KDE4 to be released or are they just sort of going to release it whenever it's done? Can't wait...

I think there was a tentative launch date of beginning of Q2 2007, but "when it's done" seems more likely to me.  Note that the initial release is simply bound to be slow, buggy and unstable due to the amount of changes that it's gone through, so it might be wise to steer clear of it for a few months, at least.  Note also that it likely won't be delivered all in one go; key parts of the platform (notably Tenor) will likely be absent or extremely incomplete initially, and filled in as time goes by.

---

### Post by elektrolott on 2006-12-15
how come that there is still no 1.4.4 for dapper available? :-k

---

### Post by Lord Illidan on 2006-12-15
You can try this : [http://pansapiens.blogspot.com/2006/11/amarok-144-on-ubuntu-dapper.html](http://pansapiens.blogspot.com/2006/11/amarok-144-on-ubuntu-dapper.html)

---

### Post by Gargamella on 2006-12-15
does it work on dapper?

---

