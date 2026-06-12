---
title: "should i remove ubuntu?"
date: 2009-05-06
forum: The Cafe
---

### Post by mamamia88 on 2009-05-06
should i remove it before i send my laptop for repair?

---

### Post by monsterstack on 2009-05-06
I had to send my laptop back to the shop to fix some problem with the power adapter last year. The guy on the support line immediately thought my problems stemmed from running Linux, but when it turned out to not be the case, they just went and replaced the faulty component with no questions asked.

---

### Post by llemm on 2009-05-06
> **mamamia88 said:**
> should i remove it before i send my laptop for repair?

I dont think so.

---

### Post by doas777 on 2009-05-06
I have sent a completely non-booting laptop back for repair twice and didn't have problems, but that may have been because it wouldn't post beforehand, and by the time they noticed, the repair was done. also i paid extra for an extended service plan via the retailer, so it wasn't me sending it to HP, but them.

if you have the option, yes i would do it. if nothing else, it;s never a good idea to send your Pc off while it has personal content on it, and undelete is an easy operation if deleted data has not been overwritten.

good luck

---

### Post by Kingsley on 2009-05-06
I would set GRUB to timeout at 1 second and boot into Windows.

---

### Post by pastalavista on 2009-05-06
Is it dual boot or all Ubuntu? I would certainly back up everything before I sent it off, if that's possible. But no, I wouldn't remove it. After all, you paid for it and unless you're seeking warranty work, you should specify that they leave it as is.

---

### Post by mamamia88 on 2009-05-06
ok i think ill just format the drive and reinstall windows they are probably going to do it anyway and i just reinstalled jaunty last night and haven't changed anything yet so it won't be a big hassle

---

### Post by OutOfReach on 2009-05-06
Are you sure? I don't think they would mind you running another OS...unless of course it's the manufacturer's repair shop...

---

### Post by mamamia88 on 2009-05-06
is it possible to just delete the ubuntu partition and grub?  it will seriously take me half hour at most to reinstall don't want them sending it back

---

### Post by Skripka on 2009-05-06
> **mamamia88 said:**
> ok i think ill just format the drive and reinstall windows they are probably going to do it anyway and i just reinstalled jaunty last night and haven't changed anything yet so it won't be a big hassle

That is what I was about to say.  Odds are quite good they'll nuke your HDD anyway...might as well give them one less thing to suspect as causation or fault.

---

### Post by doas777 on 2009-05-06
> **mamamia88 said:**
> is it possible to just delete the ubuntu partition and grub?  it will seriously take me half hour at most to reinstall don't want them sending it back

if you wanna boot from a windows disk and use recovery console to format the drive. then run fixmbr to overwrite grub. you can also do this from a ubuntu live-cd ([http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)) but ms-sys is no longer in the repos, so you will have to google for it and install manually.

---

### Post by Icehuck on 2009-05-06
> **mamamia88 said:**
> should i remove it before i send my laptop for repair?

I would remove the drive and send just the shell. I don't like people looking at my files. When machines are repaired, techs have a habit of wiping the drive to eliminate chances from OS errors. Usually, they have you sign an agreement saying you acknowledge this.

---

### Post by mamamia88 on 2009-05-06
wait you think they'll care if i remove the harddrive?

---

### Post by doas777 on 2009-05-06
> **mamamia88 said:**
> wait you think they'll care if i remove the harddrive?
probably, and it may void your warenty.

---

### Post by mamamia88 on 2009-05-06
well im still in chat with the guy ill ask him before i send it in

---

### Post by pastalavista on 2009-05-06
> **mamamia88 said:**
> wait you think they'll care if i remove the harddrive?
It depends on what the problem with it is. They surely have a spare hard drive or two lying around to use for testing...

---

### Post by mamamia88 on 2009-05-06
the problem is either a dead wireless card or a dying motherboard thats causing wireless not to work anyway theres a recall on it

---

### Post by pastalavista on 2009-05-06
> **mamamia88 said:**
> the problem is either a dead wireless card or a dying motherboard thats causing wireless not to work anyway theres a recall on itIn that case, I wouldn't remove it. Just your personal data. There's always the chance the problem is with driver compatibility. If they think Ubuntu might be the culprit, they'll reinstall Windows for you.

---

### Post by mamamia88 on 2009-05-06
> **pastalavista said:**
> In that case, I wouldn't remove it. Just your personal data. There's always the chance the problem is with driver compatibility. If they think Ubuntu might be the culprit, they'll reinstall Windows for you.
thats the thing i was running windows restarted and it no longer detected it

---

### Post by mamamia88 on 2009-05-06
ok they said it was ok to remove the drive before sending it in.  seeing how i still have an external enclosure is it possible to boot from my current setup on my desktop?

---

### Post by Skripka on 2009-05-06
> **mamamia88 said:**
> ok they said it was ok to remove the drive before sending it in.  seeing how i still have an external enclosure is it possible to boot from my current setup on my desktop?

Presuming your BIOS supports booting from USB, sure...depending on how different the hardware is (ATi vs. Nvidia etc)-you may need to tweek to run...but odds are it'll at least boot to commandline if the BIOS supports boot from USB---otherwise you could use a spare SATA or IDE port and it would surefire boot.  Odds are you'll get X, odds are.

---

### Post by mamamia88 on 2009-05-06
> **Skripka said:**
> Presuming your BIOS supports booting from USB, sure...depending on how different the hardware is (ATi vs. Nvidia etc)-you may need to tweek to run...but odds are it'll boot if the BIOS supports boot from USB---otherwise you could use a spare SATA or IDE port and it would surefire boot.

cool thanks

---

