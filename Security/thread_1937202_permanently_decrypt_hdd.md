---
title: "permanently decrypt hdd"
date: 2012-03-07
forum: Security
---

### Post by DouglasAWh on 2012-03-07
There seem to be several people asking how to get rid of the passphrase and do a Windows-similar TPM chip thing. That is *not* what I am asking.

I want to permanently decrypt the drive. How do I do this? 

My searches are turning up empty because either "no one" else wants to do this, my search terms are terrible, my results are being swamped by the headless server crowd or of course some combination of the three.

Yes, I know this will leave my data easily readable by third parties that break into my house and steal my desktop drive. Yes, I know that in most instances encryption does not cause severe performance overhead. I am trying to discover the bottleneck on this particular machine so that I know which part(s) to replace, if any. They all could use upgrades, but money is tight and I am going to try to replace as few as possible.

---

### Post by Jonathan L on 2012-03-07
> I want to permanently decrypt the drive. How do I do this? 
Hi Douglas

Ubuntu doesn't encrypt things unless you tell it to: which you can do per hard drive or for home directories.  To "permanently decrypt", simply don't encrypt!

You could either reinstall, or if you tell us what's encrypted we might be able to help.

Though I see you're using 11.10.  Perhaps I'm out of date with my statement that it doesn't do it by default.  In which case: use 10.04 LTS, and it doesn't encrypt.

Does that help at all?

Kind regards,
Jonathan

---

### Post by DouglasAWh on 2012-03-07
> **Jonathan L said:**
> 
You could either reinstall, or if you tell us what's encrypted we might be able to help.

Oops, after all my searches including it, I left it out of the post. It's full disk encryption. That is, it's an LVM. 

This disk *was* in a higher performance machine and was in another location that made encryption more relevant. Performance was fine when in the higher performance machine.

I think the command may be ecryptfsd. I was trying to just use "ecrypt" before and there was no man page for that and it didn't exist. I am not in the same location at the moment, so I can't look back at the logs, but I can do that later and give specific things I tried if it helps. I've got something to look for now that I remembered the "fs" part.

---

### Post by Jonathan L on 2012-03-11
> **DouglasAWh said:**
> Oops, after all my searches including it, I left it out of the post. It's full disk encryption. That is, it's an LVM. 

This disk *was* in a higher performance machine and was in another location that made encryption more relevant. Performance was fine when in the higher performance machine.

I think the command may be ecryptfsd. I was trying to just use "ecrypt" before and there was no man page for that and it didn't exist. I am not in the same location at the moment, so I can't look back at the logs, but I can do that later and give specific things I tried if it helps. I've got something to look for now that I remembered the "fs" part.

Hi Douglas

With ecryptfsd, you get another mounted filesystem, which is a decrypted version of the mounted encrypted filesystem.  Use any method of copying it to another non-encrypted place such as a network mount, exactly like a backup/restore.  Depending what it is, you might like to use cp, tar, dd.  Reformat the encrypted disk as a non-encrypted one, and restore.

Deteails of this depend on whether it's the only disk in your system or not.

Any help?

Kind regards,
Jonathan.

---

