---
title: "TrueCrypt replacement?"
date: 2008-06-03
forum: Security
---

### Post by gfixler on 2008-06-03
I haven't used TrueCrypt since well before upgrading to Hardy about a month ago, but the new version is a nightmare to me. Everything pops up GUIs now. I know about -t, but even just asking for help in the shell now requires:

```
truecrypt -t -h
```

I feel this is patently ridiculous, being the only shell tool I use now that requires a special option *not* to go GUI. But that's just the beginning. I used to use -M to pass in shortname=mixed, to fix filename problems in my volumes, but that option is gone, seemingly replaced by --fs-option=OPTIONS, which errors on attempting to pass this in, quoted or not. This means I can no longer write in files without borking things like their filename cases.

I can no longer use TrueCrypt easily in my many automation scripts, as (aside from having to go change about 35 lines of calls in my .bashrc functions to try (and fail miserably) to fix the now wildly out-of-format options), it also asks me for keyfile, and hidden file protection options after entering the password. The latter of those two seems ludicrous to me. That's the one option intended to guard against rubber hose attacks - one of their highlight features - and now it blatantly announces to whomever may be looking over your shoulder that there might be a hidden volume! I have no clue what the developers are thinking anymore. Both of those options should be as they were - options specified by the user on the command line if they matter. It seems this was added to help interactively aid newbs, but they're not going to understand what either of those things means anyway, if they're not yet clever enough to use those features, and it means the 20+ times a day I'm logging into and out of my volumes, I'm having to do extra, pointless steps that will never apply to me. I suppose I could flag these issues away, but that means that when I'm not working with automated scripts, I'm typing out lines of options to fix what's now IMNSHO broken.

I feel like TrueCrypt is devoting itself to being great for Windows, and MacOS needs, and it's sort of kicking us 'power users' on Linux to the curb. And that's fine, I'll head elsewhere. But where exactly is elsewhere? Ideally I want almost no options at all. I liked the concept of making encrypted containers, but AES only is fine with me. I don't care about keyfiles, nor hidden volumes, nor any of that extra stuff. I just want to safeguard files on my home drives, in case the machine gets stolen, and on my USB keychain, in case I lose it. I also want something that exposes every option - creation, encryption, decryption - on the command line in a simple way, and honestly, I could care less about a UI. They aren't helpful to me, and the addition of one to TC on Linux seems to have broken just about everything I cared about. Here's the rough part: I need this to work on Windows, too. That's one huge reason I loved TC. It let me bring my pendrive between home (Ubuntu), and work (XP) with no hassle.

I know I can use the also-enormous --non-interactive flag so I don't have to enter the keyfile, and protection stuff, too, but then it errors out on no password, meaning it wants me to pass in my password as plaintext from the shell, meaning it goes into my history, meaning forget that.

I really hate when open source software does this to me. Thanks for any help, or pointers about getting TrueCrypt to go back to a time before it was this mess.

---

### Post by hyper_ch on 2008-06-03
why don't you use native linux full disk encryption with dm_crypt/luks?

Or on my server, where I have a ftp-only backup drive I use duplicity with ftplicity.... it uses gpg and created incremental snapshots (however you have to safeguard the gpg keys)

---

### Post by gfixler on 2008-06-03
Thanks, I'll take a look into it. Can I assume it doesn't have a Windows equivalent?

---

### Post by hyper_ch on 2008-06-03
luks/dm_crypt won't work on windows....

---

### Post by /etc/init.d/ on 2008-06-03
> **hyper_ch said:**
> luks/dm_crypt won't work on windows....
FreeOFTE supports LUKS just fine.

---

### Post by hyper_ch on 2008-06-03
interesting :)

---

### Post by kevdog on 2008-06-03
Careful with luks/dm_crypt.  For me and some others, when you upgrade kernels, the new kernel will not boot.  This isn't the case for all users, however I'm stuck with the current hardy kernel.

---

### Post by tubbygweilo on 2008-06-03
I seem to be suffering this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129") when using lvm & full disk encryption. 

The bug happens every now and then on my two different machines so I am hesitant about advocating this form of full disk encryption  for use amongst my friends and business acquaintances.

---

### Post by hyper_ch on 2008-06-03
> **kevdog said:**
> Careful with luks/dm_crypt.  For me and some others, when you upgrade kernels, the new kernel will not boot.

only if you use LVM

---

### Post by chewearn on 2008-06-03
I manually compile Truecrypt 4.3a for Hardy.

[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)
It a pain trying to figure out the patch and what not, but once successfully done, it runs better and faster than in Gusty :wink:

The only problem thus far is having to recompile  everytime the kernel is updated, but other than that, it works the same as before.

---

### Post by gfixler on 2008-06-04
> **kevdog said:**
> Careful with luks/dm_crypt.  For me and some others, when you upgrade kernels, the new kernel will not boot.  This isn't the case for all users, however I'm stuck with the current hardy kernel.

Does this mean it's a whole-disk encryption scheme? My methods so far revolve around only opening what I'm using at any given time by mounting encrypted TC volumes. Most of my stuff I don't care to encrypt - just certain things, like files of my creations, financial info, etc. I don't care if someone gets ahold of my Neverball scores :)

Also, a big need is to be able to encrypt a USB thumbdrive to bring back and forth between Linux and Windows. That's a pain, but I don't have a good alternative. Thanks for the info.

---

### Post by gfixler on 2008-06-04
> **AstalaVista said:**
> I manually compile Truecrypt 4.3a for Hardy.

[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)
It a pain trying to figure out the patch and what not, but once successfully done, it runs better and faster than in Gusty :wink:

The only problem thus far is having to recompile  everytime the kernel is updated, but other than that, it works the same as before.

I've looked through other options, but none does what I need yet. I may have to take you up on your compile trick. Thanks very much for the link.

---

### Post by /etc/init.d/ on 2008-06-04
> **tubbygweilo said:**
> I seem to be suffering this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129") when using lvm & full disk encryption.
VIA Padlock is a hardware encryption device, support for which was recently added into the kernel.  At bootup the kernel may load the padlock module in anticipation that you have the hardware.  If you don't, it returns "No such device" and carries on booting. 

The message is harmless, and doesn't affect anything else.  If your disk encryption is not working, it was not caused through this message.

If the message bothers you, you can blacklist the module.

---

### Post by tubbygweilo on 2008-06-04
> The message is harmless, and doesn't affect anything else. If your disk encryption is not working, it was not caused through this message.

That is reassuring to know.

> 
If the message bothers you, you can blacklist the module.
This I will think about.

Many thanks for your advice.

---

