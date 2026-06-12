---
title: "So I'm finally Windows free. (Story Inside.)"
date: 2009-05-15
forum: Testimonials &amp; Experiences
---

### Post by Crafty Kisses on 2009-05-15
So for the longest time I had a dual boot for Windows and Ubuntu, but the only reason I had Ubuntu is because occasionaly my brother likes to come over and play some games that I had. Well I got fed up with Windows today and replaced it with Sabayon. Now I'm not sure if this is an Ubuntu rant so much as it is Sabayon, but I'd still like to share my experience, so I apologize if this is in the wrong section.

Now I'll tell you why I did this, it's for the simple fact that Windows would not let me shrink the Vista partition. I tried and it said "Access Denied" and I had full privledges. As ridiculous as that sounds, I tried numerous things and nothing worked. I opened up CMD and ran the following:
```
chkdsk /r
```
So I rebooted and tried it one more time and of course I get the same output, "Access Denied" and this issue is well documented on the Vista forums. So I decided to uninstall Windows and replace that empty partition with Sabayon.

Now I've been using Sabayon on my old laptop for awhile and it works great, I say it's one of my favorite distributions besides Ubuntu. It's based off of Gentoo and I love Gentoo. So all in all I'm now running Ubuntu/Sabayon dual boot, so my whole computer is Linux! :)

---

### Post by skygazer on 2009-05-15
hahah.. it can get pretty frustrating using windows.. I never had the realization that vista was so disgusting untill i switched over.. I used to waste hours and hours just maintaining the computer and keeping it uptodate. Then there were the ocassional hangs and Windows explorer crashes and in general a slow computer with the hdd spinning like crazy. Also the installation was bloated with almost 30 + GB vista partition.
Anyways congrats for your decision to get rid of windows. You can still use windows btw, using virtualbox. It will be a while before virtualbox supports 3d accelaration, after which gaming on a virtual guest OS will become the norm.

---

### Post by Greenwidth on 2009-05-15
You probably couldn't shrink the partition because of the Master File Table (MFT) which is at the end of the partition (to try and avoid fragmentation) and can't be moved.

---

### Post by scouser73 on 2009-05-15
I went back to using Windows for a course (which I never did take), I know shame on me, I came back to using Jaunty today and everything works seamlessly. Yet another great effort by the guys at Ubuntu.

---

### Post by Crafty Kisses on 2009-05-15
> **Greenwidth said:**
> You probably couldn't shrink the partition because of the Master File Table (MFT) which is at the end of the partition (to try and avoid fragmentation) and can't be moved.

It could be but I really don't think that's the case. At one point I checked my user privileges and I wasn't even an Administrator and I know for a fact that I was because I own the computer and I made the account, I then gave myself full admin privileges and still nothing, that problem is also stated in the thread over at the Vista forums. Here is the thread over at the Vista forums, I guess no one knows why it's happening: [http://thevistaforums.com/index.php?showtopic=9046](http://thevistaforums.com/index.php?showtopic=9046).

Now after running the following in CMD:

```
chkdsk /r
```

Nothing came back out of the ordinary and I did a clean reboot and I also defragged just to make sure and I still couldn't do it, which as I've already stated was kind of weird and I'm not sure why it was happening. My guess it was a privileges issue, but I don't see why that would be happening. Anyway, thanks for reading. ;)

---

### Post by Greenwidth on 2009-05-15
The MFT was the problem for me, I tried the visual defrag utility and could see the immovable files were right at the end of the drive. See:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by WatchingThePain on 2009-05-15
When I was a distro hopper I tried Sabayon and it asked too many questions that I could not answer during install.
There was like a massive list of programs and services and it said tick the ones you want.
I thought that was pretty harsh.
Is there something I should know?.

---

### Post by Crafty Kisses on 2009-05-15
> **WatchingThePain said:**
> When I was a distro hopper I tried Sabayon and it asked too many questions that I could not answer during install.
There was like a massive list of programs and services and it said tick the ones you want.
I thought that was pretty harsh.
Is there something I should know?.
Not really. I don't really get the question. You thought the install was hard on Sabayon or something?

---

