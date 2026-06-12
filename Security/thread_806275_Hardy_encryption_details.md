---
title: "Hardy encryption details"
date: 2008-05-24
forum: Security
---

### Post by update_manager on 2008-05-24
Can anyone point me to a site that has the details of the install time encryption used in Hardy?

I'd like to know:
[LIST]
Is the swap partition encrypted?
[/LIST]
[LIST]
How can the password be changed after the installation?
[/LIST]

---

### Post by bwhite82 on 2008-05-24
Not sure on your password question, however, yes, the swap partition is encrypted, the only thing that isn't is the /boot partition which must remain unencrypted to be bootable.

---

### Post by michaelzap on 2008-05-24
For those of you who are using Hardy with encryption, how's it working for you? Is there any noticeable speed difference? I have a perfectly good unencrypted Hardy system (upgraded from Gutsy), but I think I'm going to start fresh with encrypted Hardy on a new drive.

---

### Post by Steve413z on 2008-05-24
> **michaelzap said:**
> For those of you who are using Hardy with encryption, how's it working for you? Is there any noticeable speed difference? I have a perfectly good unencrypted Hardy system (upgraded from Gutsy), but I think I'm going to start fresh with encrypted Hardy on a new drive.

no, not much speed difforence, (on my core duo laptop), if it's an older machine, there might be a problem.

make sure you get the Text Installer "Alternative" CD or the DVD to install using full disk encryption

---

### Post by hyper_ch on 2008-05-25
> **update_manager said:**
> Is the swap partition encrypted?
yes
> **update_manager said:**
> How can the password be changed after the installation?
Yes, it can

---

### Post by sunbird on 2008-05-25
I wrote this [how-to]("http://ubuntuforums.org/showthread.php?p=4604645"), which is focused on intel Macbook Pros dual-booting ubuntu, but the instructions for the encryption should be the same.

I've noticed zero speed difference.

---

### Post by hyper_ch on 2008-05-25
> **update_manager said:**
> How can the password be changed after the installation?
```

sudo cryptsetup luksAddKey /dev/sdX

```

You can have up to 10 slots of passwords or keyfiles and with luksAddKey you add new ones.... and with luksDeleteKey you remove existing ones.

Have a look at the cryptsetup man pages how to use those commands at fully extend.

---

### Post by update_manager on 2008-05-25
> **hyper_ch said:**
> ```

sudo cryptsetup luksAddKey /dev/sdX

```

You can have up to 10 slots of passwords or keyfiles and with luksAddKey you add new ones.... and with luksDeleteKey you remove existing ones.

Have a look at the cryptsetup man pages how to use those commands at fully extend.

Thanks!

If I wanted to take an existing mapping, I could boot into my current setup, then use:
cryptsetup reload luksAddKey

Does this sound right?

---

### Post by hyper_ch on 2008-05-25
not sure what you mean

---

### Post by update_manager on 2008-05-26
> **hyper_ch said:**
> not sure what you mean

Its not clear to me from the man page if cryptsetup can be used on mounted drives. 

In other words - can I do a default install, boot into encrypted partition then make changes.

---

### Post by hyper_ch on 2008-05-27
yes

---

### Post by michaelzap on 2008-05-27
> **Steve413z said:**
> no, not much speed difforence, (on my core duo laptop), if it's an older machine, there might be a problem.

Decided to give it a try tonight, and indeed it seems just as fast as my previous unencrypted system. I still have to install and configure all of the apps and whatnot that I use, but it's nice to have a clean slate to scribble on. I'll be right back to work tomorrow morning with a brand new system under the hood.

---

### Post by hyper_ch on 2008-05-27
you'll notice a difference when you start big read/write operations... but on a "normal" use, you hardly notice anything...

---

### Post by michaelzap on 2008-05-27
> **hyper_ch said:**
> you'll notice a difference when you start big read/write operations... but on a "normal" use, you hardly notice anything...

I mostly use an unencrypted scratch disk and network shares for big files anyway, so I think that other than the occasional video work I may never notice.

---

### Post by michaelzap on 2008-05-28
Just reporting back for posterity:

The encrypted installation went swimmingly (it only took me a couple of hours to set up everything just the way I wanted after the installation finished). I've been using the new system for a few days now, and if anything it seems faster than my previous one (which was an upgrade from Gutsy to Hardy, with some additional random software that I no longer use like Tracker). Everything works perfectly and I've had zero complications.

Kudos to the Ubuntu dev team!

---

### Post by hyper_ch on 2008-05-29
just remember to have an (encrypted) backup of that data somewhere.

If the harddisk fails at a critical point you cannot recover the encrypted files anymore.

---

