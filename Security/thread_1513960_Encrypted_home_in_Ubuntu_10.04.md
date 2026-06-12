---
title: "Encrypted home in Ubuntu 10.04"
date: 2010-06-20
forum: Security
---

### Post by P3t3r on 2010-06-20
Hi,

I've been looking for more information on how the ubuntu 10.04 encrypted home directory works, but I can't really find the information I need. The help and wiki pages I find are outdated, or not answering my questions.

I wonder if some of you could tell me the following:
[LIST]
[*]When installing Ubuntu with encrypted home, the first startup gives me the opportunity to get a key, which is needed for data recovery. Asuming I don't want to recover data (i.e. I only want maximal security), do I need to do anything? Can I just ignore this window and assume that my data is well secured?
[*]How safe is this encryption? Can an adversary who steals my computer (powered off) do anything to see my data? He cannot see my documents, program settings, recent items (as these are in /home/myname/)? Can he see, for example, when I last logged in to my passworded profile or when I last edited information in it?
[*]Is it possible to make the root password much simpler than the encryption password? I don't want to type a random string of 20+ characters every time I need root access, and I don't want to secure my data with a short password. Is this possible, if so how, and will this break the security level?
[*]Are there any other reasons that this is less secure than a TrueCrypt volume with has to be decrypted at boot-time? Plausible denial seems ok, assuming one makes several accounts? Other things a cryptographer (like me) has to be aware of when using this security?
[/LIST]

Thanks in advance!

---

### Post by Bachstelze on 2010-06-20
> **P3t3r said:**
> 
When installing Ubuntu with encrypted home, the first startup gives me the opportunity to get a key, which is needed for data recovery. Asuming I don't want to recover data (i.e. I only want maximal security), do I need to do anything? Can I just ignore this window and assume that my data is well secured?

No, because this is what will be used to actually mount the volume.

> **P3t3r said:**
> How safe is this encryption? Can an adversary who steals my computer (powered off) do anything to see my data? He cannot see my documents, program settings, recent items (as these are in /home/myname/)?

No, that's the point.

> **P3t3r said:**
> Can he see, for example, when I last logged in to my passworded profile or when I last edited information in it?

Yes.

> **P3t3r said:**
> Is it possible to make the root password much simpler than the encryption password? I don't want to type a random string of 20+ characters every time I need root access, and I don't want to secure my data with a short password. Is this possible, if so how, and will this break the security level?

The root password? What does the root password have to do with anything?

> **P3t3r said:**
> Are there any other reasons that this is less secure than a TrueCrypt volume with has to be decrypted at boot-time? Plausible denial seems ok, assuming one makes several accounts?

You don't have any plausible deniability with ecryptfs. Anyone can see that you have an encrypted directory.

> **P3t3r said:**
> a cryptographer (like me)

orly?

---

### Post by P3t3r on 2010-06-22
> **Bachstelze said:**
> No, because this is what will be used to actually mount the volume.I'm afraid I still don't understand it: even if I ignore this, the volume auto-mounts when logging in. So it either regenerates this automatically (meaning it is not an independent key) or it is stored somewhere only accessible after decryption, right? In both cases I would think I *can* safely ignore it without breaching my security...?

> **Bachstelze said:**
> The root password? What does the root password have to do with anything? Hopefully nothing, but I fail to find the option to set separate root and user passwords during Ubuntu 10.04 install -- quite important for encrypted systems. More of an installer problem than anything else, apparently.

> **Bachstelze said:**
> Yes.And isn't there any way to hide this? Unless I completely misunderstand the way Ubuntu encrypts this, it should be possible: if the encrypted home directory is stored in some file (as with TrueCrypt), it seems the file's access/modify/view date can be resetted to a certain date on every (proper) logout, as well as any other places where this date is stored. If the home directory is not stored in a file then the date should not even be stored at all...

> **Bachstelze said:**
> You don't have any plausible deniability with ecryptfs. Anyone can see that you have an encrypted directory.Assuming dates can be erased as above, what am I still missing? If I store my sensitive information on an account "grandpa" and some nonsensitive ones on "myname", then I can claim that "grandpa" is the account from my grandfather who died last year, making it plausible that I don't have the password. Sure they can see it, but that is no problem: it has been made plausible that I cannot help them with decryption. Or is there any other problem with the way Ubuntu handles this encryption?

---

### Post by roeland on 2010-07-10
> **P3t3r said:**
> I'm afraid I still don't understand it: even if I ignore this, the volume auto-mounts when logging in. So it either regenerates this automatically (meaning it is not an independent key) or it is stored somewhere only accessible after decryption, right? In both cases I would think I *can* safely ignore it without breaching my security...?

There's an auto-generated private key, which is stored in a keyring, which in turn is encrypted with the user's login password. This means you can still recover your data with the evil-looking private key if you lose the user password. (Arguably the documentation doesn't emphasise strongly enough that your memorable user password had better be *good*).

> Hopefully nothing, but I fail to find the option to set separate root and user passwords during Ubuntu 10.04 install -- quite important for encrypted systems. More of an installer problem than anything else, apparently.

Modern Linux distro's seldom set a password for root, in order to eliminate brute-force attacks on a known username. Instead, a normal non-privileged user is equipped with sudo rights (lookup 'man sudo') which give you temporary superuser privileges. Again, the normal user with sudo rights should be aware that his/her system is only 1 password away from world dominance.

> And isn't there any way to hide this? Unless I completely misunderstand the way Ubuntu encrypts this, it should be possible: if the encrypted home directory is stored in some file (as with TrueCrypt), it seems the file's access/modify/view date can be resetted to a certain date on every (proper) logout, as well as any other places where this date is stored. If the home directory is not stored in a file then the date should not even be stored at all...

Unix systems tend to register your logins in one or more other places, mostly under /var/log. Also, ecryptfs crypts on a by-file basis, not on a per-volume basis. Your encrypted home dir looks like a tree of oddly-named files, with their timestamps and sizes unencrypted.

> Assuming dates can be erased as above, what am I still missing? If I store my sensitive information on an account "grandpa" and some nonsensitive ones on "myname", then I can claim that "grandpa" is the account from my grandfather who died last year, making it plausible that I don't have the password. Sure they can see it, but that is no problem: it has been made plausible that I cannot help them with decryption. Or is there any other problem with the way Ubuntu handles this encryption?

For a cryptographer, you seem to have odd ideas about 'plausible denial'. The idea is that you can deny altogether that there is something encrypted, at all. You surely don't think the [s]Gestapo[/s]NSA will fall for the grandpa excuse, do you?

If you want plausible denial, truecrypt may be of some help, although I've always failed to see how you could deny encryption if the friggin' program is installed on your system, and the bash command line history or who-knows what logfile or swapfile gives away you've been using it.

---

