---
title: "Can I upgrade 10.04 to 12.04-Beta1 via update manager?"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nrundy on 2012-02-18
Hi guys.

In two weeks when 12.04-Beta1 comes out, is there a way to update 10.04 to this Beta release? How exactly do I do it? As I'm set up now, I'm pretty sure that only Stable release will cause Update manager to prompt for an upgrade.

---

### Post by philinux on 2012-02-18
> **nrundy said:**
> Hi guys.

In two weeks when 12.04-Beta1 comes out, is there a way to update 10.04 to this Beta release? How exactly do I do it? As I'm set up now, I'm pretty sure that only Stable release will cause Update manager to prompt for an upgrade.

If this is your main machine then my advice is to wait as the upgrade path from 10.04.4 has not been tested yet. It will need to be tested thoroughly too.

Wait till after release. I'm pretty sure canonical with provide detailed instructions for this on their website following release.

---

### Post by nrundy on 2012-02-18
> **philinux said:**
> If this is your main machine then my advice is to wait as the upgrade path from 10.04.4 has not been tested yet. It will need to be tested thoroughly too.

Wait till after release. I'm pretty sure canonical with provide detailed instructions for this on their website following release.

it's my main machine, but I was going to upgrade a second 10.04 install that is on a different partition than my daily-use 10.04 installation. Does this change anything?

---

### Post by marin123 on 2012-02-18
Go to Software Sources, Updates tab and choose in the Notify me of a new Ubuntu menu Long Term Support. If that doesn't do the trick, then hit Alt+F2 and run a command:
```
update-manager -d
```
and you will be notified about new version of Ubuntu (I don't know which version will you see).
Post the results here :)

---

### Post by nrundy on 2012-02-18
> **marin123 said:**
> Go to Software Sources, Updates tab and choose in the Notify me of a new Ubuntu menu Long Term Support. If that doesn't do the trick, then hit Alt+F2 and run a command:
```
update-manager -d
```and you will be notified about new version of Ubuntu (I don't know which version will you see).
Post the results here :)

Yeah, I have this configured. But I'm pretty sure it's only going to notify about when the Stable version is released. Which is understandable. I'm wondering if there's a setting I can add that will cause it to notify about when the Beta comes out.

---

### Post by philinux on 2012-02-18
> **nrundy said:**
> it's my main machine, but I was going to upgrade a second 10.04 install that is on a different partition than my daily-use 10.04 installation. Does this change anything?

Well as long as you have proper backups and you know what you're doing then yes it's doable from the command line. There are no guarantees it will work at this time though. See here.

[http://askubuntu.com/questions/87487/will-the-upgrade-from-10-04-to-12-04-be-smooth](http://askubuntu.com/questions/87487/will-the-upgrade-from-10-04-to-12-04-be-smooth)

---

### Post by nrundy on 2012-02-18
> **philinux said:**
> Well as long as you have proper backups and you know what you're doing then yes it's doable from the command line. There are no guarantees it will work at this time though. See here.

[http://askubuntu.com/questions/87487/will-the-upgrade-from-10-04-to-12-04-be-smooth](http://askubuntu.com/questions/87487/will-the-upgrade-from-10-04-to-12-04-be-smooth)

thanks for this. Is there less cause for concern if I just use a DVD to install 12.04 Beta? the reason I was considering the update approach is cause my coputer does not have a dvd-r readable drive. since 12.04 can't use CD.

---

### Post by grahammechanical on 2012-02-18
You say this:

>  I was going to upgrade a second 10.04 install that is on a different partition than my daily-use 10.04 installation.

Good! That is the best way to become a beta tester. As has been previously noted, the upgrade path needs to be tested. A lot of people will be upgrading from 10.04 to 12.04 because they are moving from one LTS release to another LTS release. It is good that you want to share in testing this process.

Try it out and see what happens. I converted a spare 11.10 partition into a testing 12.04 partition by running a couple of commands in the terminal. I am trying to find those commands.

You might be willing to test the upgrade process more than once. Yes? On Ubuntu+1 we sometimes get invitations to test stuff before it is let out into the wild. You might just see an invitation to participate in testing the upgrade path.

There is a bit of debate over Upgrade verse Fresh Install. There is a very big difference between 10.04-10.10 and even 11.04 and 11.10-12.04, that I am of the opinion that upgrading a heavily modified desktop will cause problems. Upgrading to 11.10 cause a lot of people problems

But the upgrade path is part of Ubuntu. It too needs to be precise in its function.

Regards.

---

### Post by paul_in_london on 2012-02-18
Try it out on your other partition and if that works ok you could probably just do the same with your daily-use install.

Failing that, you might want to think about upgrading your daily-use install in stages:

Lucid -> Maverick -> Natty -> Oneiric -> Precise

(editing your sources list each time).

More of a pain to do it that way obviously. It depends whether you can live with hosing/losing your main setup.

---

### Post by nrundy on 2012-02-18
> **paul_in_london said:**
> Try it out on your other partition and if that works ok you could probably just do the same with your daily-use install.

Failing that, you might want to think about upgrading your daily-use install in stages:

Lucid -> Maverick -> Natty -> Oneiric -> Precise

(editing your sources list each time).

More of a pain to do it that way obviously. It depends whether you can live with hosing/losing your main setup.

what exactly do I do though to do this upgrade to the beta? this was my original question. Will this do it: sudo dist-upgrade -d

---

### Post by philinux on 2012-02-18
> **nrundy said:**
> what exactly do I do though to do this upgrade to the beta? this was my original question. Will this do it: sudo dist-upgrade -d

Follow post 4.

Like he says post back the results you get before hitting the Y key etc.

---

### Post by JRV on 2012-02-18
> **grahammechanical said:**
> 
There is a very big difference between 10.04-10.10 and even 11.04 and 11.10-12.04, that I am of the opinion that upgrading a heavily modified desktop will cause problems. 

Yes, the switch to Unity is huge.  As is the change from gtk2 to gtk3.  And gdm to lightdm.

I just migrated my e-mail, the changes in evolution made it considerably more difficult than just a simple backup/restore and with my choice of themes it was ugly.  So I switched to Thunderbird.  Moving the address book was a chore.  I would document it but I am not sure what I did.  The entire process took about three hours.

---

### Post by prusswan on 2012-02-18
I upgraded from two machines on 10.04.3 (one physical and one VM) to Precise Alpha 2, so I don't see why not even though it is not 100% guaranteed to work. You might have driver issues after the upgrade and mostly they are fixed the way you did for them in 10.04. It's a good idea to burn a copy of the latest 12.04 bootable cd (desktop or dvd), since you can't use the 10.04 disc to repair the 12.04 install (if you happen to break grub 2 config etc)

You could do a incremental upgrade across all the in between releases, but I'm not sure if that will be worth the time spent. Most of the problems you find in 12.04, are from those earlier releases (and guess what, they include problems unsolved since 10.04) anyway so it will not make a big difference. The biggest problem you might face would possibly be from the shock and disgust you get upon seeing the new interface :D

---

### Post by Ibidem on 2012-02-18
If you have problems, you might see [http://ubuntuforums.org/showthread.php?t=1897812](http://ubuntuforums.org/showthread.php?t=1897812)

You may not run into them, though.
I'd say apt-get update && apt-get dist-upgrade

---

### Post by jerrylamos on 2012-02-18
Ubuntu Alpha, Beta, and even RC (Release Candidate) are development level, buggy, might crash, save often, have back up copies of anything you want to keep.

The "development level unstable" builds are buggy, do fail, and can crash installs.

You'd better be familiar with installing - often - and if you don't want to, then wait for final release.

I test on another partition.  Do note the ubuntu forums are littered with notes from people who tried a upgrade and crashed, nothing would boot, start over.

The intent is for upgrade to work, maybe, and even if you wait for final code an upgrade may still fail - read the ubuntu forums.

Best way on trying out development level code is to carvel out another partition and try it out to see if it will or will not work with your hardware.

Good luck.  Expect to learn a lot of linux if you're trying development software.  If it was solid, didn't break, they could ship it.  Precise Pangolin is Not Ready Yet.

Jerry

---

### Post by ranch hand on 2012-02-18
You really need to wait for the release of 10.04.4.  You could, on some hardware, get lucky at anytime.

10.04.4 will have some "improvement" in the included tools to make the upgrade from LTS to LTS work better.

I am pretty sure that this will work when ready.  8.04 to 10.04 worked and that was a pretty huge change.  At least this time the boot loader will be compatible.

Check the 12.04 release schedule.  It also has the release date for 10.04.4.  Sorry but I don't have the link handy.  For all I know the thing may be already released.

Make sure that you have your 10.04 fully upgraded before attempting to upgrade to 12.04.  Remove any/all added external repos and ppas that may be in your sources.list before attempting to go to 12.04, you can put them back when you have finished, they are a major cause of failure.

---

### Post by fabricator4 on 2012-02-18
> **nrundy said:**
> thanks for this. Is there less cause for concern if I just use a DVD to install 12.04 Beta? the reason I was considering the update approach is cause my coputer does not have a dvd-r readable drive. since 12.04 can't use CD.

Use the ISO to burn a bootable USB pen drive. Since I had to do it to install Ubuntu on my EeePC (no optical reader at all) it's become my favourite method to install.

I also prefer to install rather than upgrade but they are getting much better.  I'd still say upgrade from the LiveCD/LiveUSB in preference to doing it on line.  If the on line upgrade fails it leaves you without a bootable copy of the release you're trying to upgrade to, and it can take a long time depending on the speed of your connection.

Chris

---

### Post by philinux on 2012-02-18
Howdy Ranch.

10.04.4 has been released into the wild yesterday I think.

---

### Post by dcstar on 2012-02-18
> **nrundy said:**
> Hi guys.

In two weeks when 12.04-Beta1 comes out, is there a way to update 10.04 to this Beta release? How exactly do I do it? As I'm set up now, I'm pretty sure that only Stable release will cause Update manager to prompt for an upgrade.

Doing any "Upgrade" is virtually guaranteed to cause more problems than a fresh install of a new version and then migrating the data across.

Find one of the many (hundreds?) of posts already in these forums on how to migrate to a new version via a fresh install and follow those steps.

---

### Post by ranch hand on 2012-02-18
> **philinux said:**
> Howdy Ranch.

10.04.4 has been released into the wild yesterday I think.
That is what I get for not ISO testing.  Thanks.

---

### Post by kansasnoob on 2012-02-18
I tested the upgrade path from Lucid to Precise in both Alpha 1 and Alpha 2, it's one of the tests I'm subscribed to. Anyway it was totally borked in Alpha 1, but upgrading for Alpha 2 worked fairly well.

Since then I've updated that install a few times and just recently I had to blow away some of the hidden "dot" folders to get back to a working theme, and oneconf keeps spawning errors, and gdm doesn't get purged like I'd think it should.

So, right now upgrading from Lucid to Precise is likely to be a little buggy, but I'll be testing it again during Beta 1 iso-testing. BTW to upgrade to the latest development release, eg; Precise Alpha 2 you'd run:

```
update-manager -d
```

But if you wanted to jump the gun and update to the latest current Precise you'd add -c like this:

```
update-manager -d -c
```

But expect some breakage ATM :D

---

### Post by nanog on 2012-02-19
I've already upgraded quite a few servers and dev boxes from lucid to precise. Obviously using a dev version can nuke everything so its goes without saying that you should back everything up. IMO, there is far more risk in a fresh install than in upgrading an existing install. I also believe that the majority of ubuntu users upgrade instead of reinstall.

---

### Post by nanog on 2012-02-19
> But expect some breakage ATM :grin:

The breakage these days is just not like it used to be. I still fondly remember the broken libc6 they pushed out in hardy.

---

### Post by ranch hand on 2012-02-20
> **nanog said:**
> The breakage these days is just not like it used to be. I still fondly remember the broken libc6 they pushed out in hardy.
While not quite up to that standard (I wasn't around but read the archives) I thought the advent of grub2 with no documentation was pretty FUN in 9.10-testing.

For about 2 weeks anyway.  After that we had it whipped.

---

### Post by nrundy on 2012-02-21
I tried a 11.10 ----> to 12.04 Alpha 2 today. Everything went fine.

---

