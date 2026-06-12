---
title: "How to confrim syncing and should I stick with Ubuntu One?"
date: 2011-07-29
forum: Ubuntu One (CLOSED)
---

### Post by Jim_Rogers on 2011-07-29
Hello--

I've been using Ubuntu One for about 7 months now. It's been working OK-- my files, Tomboy notes and Evolution contacts all synchronize.

But I've had the (apparently common) problem with connecting the whole time I've been using it-- I have to start it several times to get it to hook up, the I have to hit connect several times before it connects. It often get stuck in "synchronize in progress" mode, at which point I have to reboot to get it to work. Finally, it has never synched my Firefox bookmarks.

All of these are more irritants than problems, and I've been patient waiting for them to eventually be fixed. However, I have been losing that patience a bit lately-- how long should it take for them to fix this?

What causes me to post now is the fact that about two weeks ago I created a new folder on one machine and added some data files to it. Sync was successful, and the new folder appears online in my Ubuntu One Dashboard.

Going to my other computer at home, sync was successful, the folder appeared, but it has no files. I figured maybe there was a glitch and it would eventually sync. It's been two weeks now, and still no files in that folder (on the home computer).

So it doesn't seem to be remedying itself, and I'm wondering now how many other folders might be doing the same thing. I'm almost afraid to check.

So my first question is, what is a good way to check that synchronization has worked properly? Second, how do I fix the fact that I know of at least one folder that is not synced even though Ubuntu One says it is?

I'm afraid that when I check I may find that I have several folders that are not synced and that I'm going to have a big mess trying to sort it all out.

Secondly, I'm wondering if I should even stick with Ubuntu One. I really like the idea of Ubuntu One and prefer to use it, but I'm only moderately technical in Linux, and frankly I don't really have time to mess with it. I really just need reliable file syncing.

Should I stay with it a bit longer or just switch to DropBox? Any advice would be appreciated.

Thanks,

--Jim

---

### Post by Mia1990 on 2011-07-30
Do you have all the updates?I have not had the first problem.I would install both if i was having that problem.There always updating u1 so you could just wake one morning and find it working or a update
for u1 that fixes it.

---

### Post by Jim_Rogers on 2011-07-30
> **Mia1990 said:**
> Do you have all the updates?I have not had the first problem.I would install both if i was having that problem.There always updating u1 so you could just wake one morning and find it working or a update
for u1 that fixes it.

Yes, my system checks for updates every day and whenever there is an update I immediately accept it. There used to be fairly regular updates of U1, but there hasn't been one in quite awhile.

However, I have not upgraded to 11.04 yet. I always wait 3 months or so after a new version is released to do the upgrade (so I will be doing it soon).

You think that will help? Any major improvements in U1 in Natty?

Even if there is (and my problem gets fixed) I still wonder if there is some clever/easy way (outside of U1) to check up on U1 and verify that it has synced properly.

---

### Post by duanedesign on 2011-08-04
Definitely the version of Ubuntu One in Natty contains lots of improvements. We have been trying to backport these to older clients but the SRU process meant to keep releases stable isn't friendly to packages with big changes.

To get more information about what Ubunt One is doing i made [a sticky on this topic]("http://ubuntuforums.org/showthread.php?t=1594301"). That should help.

As for the files that are not syncing I would like to help you figure out why. First i would check the syncdaemon-exceptions log to see if it contains anything. you can quicklt open that with the command:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log

```
Thank you,
duanedesign

---

### Post by Mia1990 on 2011-08-05
There are some.The biggest is the ubuntu one control panel (it's really nice) i personally think u1 works better on natty then u1 on 10.10.

---

### Post by ParadoxBlue on 2011-08-05
Did I get a free upgrade somehow? I'm on the free 2GB plan and I just synced 584.5MB and am showing 11.4% used. The percentage showing used was correct up until now. But hey at least I didn't get any "u1conlict"s this time.

---

### Post by duanedesign on 2011-08-11
> **ParadoxBlue said:**
> Did I get a free upgrade somehow? I'm on the free 2GB plan and I just synced 584.5MB and am showing 11.4% used. The percentage showing used was correct up until now. But hey at least I didn't get any "u1conlict"s this time.

Yes, All our plans got updated. Ubuntu One Basic customers are now on a plan called Ubuntu One Free which includes 5GB of storage for free.

---

