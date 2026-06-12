---
title: "Agh.  Accidentally upgraded to pre-release!"
date: 2015-12-28
forum: Server Platforms
---

### Post by Phiwum on 2015-12-28
I evidently follow directions quite poorly.  While trying to upgrade my server, I seem to have upgraded to Xenial, an alpha release.  

I don't know if the fact I'm using a pre-release is the reason for my problems, but it's certainly not what I intended to do.  I'd just as soon downgrade to a more stable release.  Is there any easy way to do so?

This is a machine which I've used for some time, and I have rather a lot of little tweaks and fixes here and there.  A reinstallation would be messy and take days.

Thanks.

---

### Post by deadflowr on 2015-12-28
> I'd just as soon downgrade to a more stable release. Is there any easy way to do so?
Reinstall, no way out of that at this point.

It's unclear on what directions would have push you into the development release, could you post a link or something, for others to have a better understanding on that.

> I don't know if the fact I'm using a pre-release is the reason for my problems
The pre-release repositories are contained in the version of Ubuntu you are using, they have nothing to do with release-upgrades, only to do with packages-in-waiting for the version at hand.
Packages in pre-release for 14.04 will only affect users of 14.04 and have no ability to move that user beyond 14.04.
If that makes sense.

---

### Post by MAFoElffen on 2015-12-28
> **Phiwum said:**
> I evidently follow directions quite poorly.  While trying to upgrade my **[COLOR=#ff0000]server[/COLOR]**, I seem to have upgraded to Xenial, an alpha release.  

I don't know if the fact I'm using a pre-release is the reason for my problems, but it's certainly not what I intended to do.  I'd just as soon downgrade to a more stable release.  Is there any easy way to do so?

This is a machine which I've used for some time, and I have rather a lot of little tweaks and fixes here and there.  A reinstallation would be messy and take days.

Thanks.
@ Deadflowr (or Any other [COLOR=#ff0000]Forums Moderator[/COLOR]) --> Please move this to the [Server Support Section]("http://ubuntuforums.org/forumdisplay.php?f=339") so he can get the exposure he needs...

@OP:
- Is this a production server? 
 -- This will determine if you need to backup what you have at this point and how to go about back-tracking to the last LTS... 
- How did you go about updating where you ended up on 16.04?
 -- This might determine if there needs to be different methods needed.
- What server services are you providing and to whom are you providing them to?
 -- This has to do with the scope of what might need to be done...
- How much disk space do you have used and free?
 -- if needed you may have to backup what you have then migrate config files and data over to a fresh install to get back to where you were...

If not a production server, then you are fairly safe. Being involved with the Server Team as occasional support in the Server Support Section and doing Dev Testing, past experience tells me that most Dev Testing has to do with the Desktop Version. Very little in the Dev Cycle has to do with  the main Ubuntu core package. That is fairly stable. Anything to do with that is usually early on in the cycle (but does still happen). If you look at the current [Server dev cycle milestones for Server 16.04]("http://status.ubuntu.com/ubuntu-t/ubuntu-server.html"), most work is done already, and there is only 3 months to it's release... What is left has to do with certain packages and services. Most of the server dev this cycle has to do with OpenStack, Juju and MAAS.

So what you have setup, what you are doing, and what your scope is currently, may determine if you really need to "restore" back to what you were. That "restore" implies that (with a server) you should have had a backup/recovery plan implemented before upgrading to a new release, whether it was from old LTS to newer LTS, or what you did by mistake. That process, would make things easy, by just doing a restore to an earlier point in time...

Next is to correct your skills how you do a release upgrade, so that it does not happen again.

What I would really like info on (posted), is what was the original version of server installed and the "prompt=..." setting in file /etc/update-manager/release-upgrades <-- Please post that file.

---

### Post by grahammechanical on 2015-12-28
Some problems are like buses. You wait for one for a long time. and then 3 come along at once.

This is the 3rd or 4th post in recent weeks where someone has run do-release-upgrade with the -d switch and got upgraded to the only development release in town - xenial xerus (16.04).

People using Ubuntu desktop should use a setting in Software & Updates>Updates to be notified of either the next LTS release or the any new version.

People using Ubuntu server need to run

```
sudo aptitude install update-manager-core
sudo do-release-upgrade
```

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

These 2 commands will upgrade to the development version. As with any upgrade to the next release, there is no easy way back.

```

sudo apt-get install update-manager-core
sudo do-release-upgrade -d
```

Note, the -d switch = development version.

If the upgrade was successful & the server OS is not broken then my advice at this point in time would be to stick with Xenial Xerus and do frequent updates until it becomes 16.04 server in 4 months time.

Regards.

---

### Post by monkeybrain20122 on 2015-12-28
> **grahammechanical said:**
> 

People using Ubuntu desktop should use a setting in Software & Updates>Updates to be notified of either the next LTS release or the any new version.




No, they should just disable it (never notify) It is always a bad idea to upgrade on impulse just because a popup tells you a new OS is available. You have to do some planing and save your data first. Moreover "upgrade" tends to be problematic.

---

