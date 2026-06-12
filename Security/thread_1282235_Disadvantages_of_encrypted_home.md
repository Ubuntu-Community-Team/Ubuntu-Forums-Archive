---
title: "Disadvantages of encrypted home"
date: 2009-10-04
forum: Security
---

### Post by gnudoc on 2009-10-04
So we all know the advantage of an encrypted home folder

Are there any significant disadvantages to it? And should these be spelled out to users before giving them the option to do so during a standard install?

---

### Post by XCan on 2009-10-04
Performance hit? Really only noticable during large file transfers, if it's only the home, booting performance shouldn't be affected too much either.

---

### Post by undecim on 2009-10-04
Yeah, some performance hit when dealing with files in the home directory. That is why I opt for encrypted home directory instead of encrypted root partition.

Also, depending on how you encrypt your directory, it can be a pain to recover files. Make sure you have back-ups of any encryption keys you don't type in directly.

For example, I have ecryptfs on my home directory on my laptop. A PAM module automatically decrypts my encryption key from my login password (as well as updates it when my password changes), but I also have the unencrypted key stored on my server (where I don't worry with encryption, since there is less threat of physical theft.)

---

### Post by thewanderer on 2009-10-05
The primary disadvantage would have to be losing access to your files.

Do not lose the pass phrase.   ;)

---

### Post by noway2 on 2009-10-06
First, I have to wonder why you would want to.  The only benefit that I can perceive is that it would make things more difficult for someone who has obtained physical access to the machine, presumably by theft.  Encrypting the data would prevent them from using a sector-editor to get at your data, and possibly reconstructing the file chains that way, but that seems like it would be a lot of work.  I am sure there are utilities for this purpose, but still .... Otherwise, in order to access the data on the machine, they would need to login and guess or hack the password.

I would think that if you are that paranoid about what would be found on the computer the best, and by far safest, approach would be to not put it (the data) on there in the first place.

---

### Post by gnudoc on 2009-10-06
noway2, if you allow physical access then there are easier routes than sector-editors and brute-forcing - live CD anyone? Or better, just take the damn harddrive and run off!

But yes, broadly that is the scenario that comes to mind when I think of encrypting drectories or partitions. And while the safest place to keep your data is in your cranium, that's probably not the best solution.

In case it's not obvious, I'm somewhat (but only somewhat) sceptical of the current fashion for encrypting home folders. The reason the question came up was I recently did an install using the standard desktop disc - most of my installs are via alternate or server disc - and I saw how prominently the option was presented - prominently enough that someone who had heard of encryption (to the extent of "encryption = good") might decide to go for it without ny further knowledge.

So, yeah, apart from the resource consumption and forgetting your password issues, can anyone think of anything else?

Cheers,
gnudoc

---

### Post by scorp123 on 2009-10-06
> **gnudoc said:**
>  So, yeah, apart from the resource consumption and forgetting your password issues, can anyone think of anything else?  Running automatic stuff. Let me explain:

You may heard about Dropbox, right? For most people it's that little cute blueish cube icon that sits in their system tray area. That's how most people know it.

What most people don't know is that you could run it automagically in the background as system service.

BUT: for this to work (and I do have it working on a few systems like that!) the script that is responsible for booting up the "dropbox" service has to use the "su - yourusername" command at one place. Why? Well ... if you don't do that the "dropboxd" would be running as "root" (as all system services belong to "root"). And here the problem starts. Depending on what encryption mechanism you choose this will fail because whatever program "su - yourusername" tries to start on your behalf will not be able to read anything from your home directory until you are logged in somehow somewhere. BUT: if I have to be logged in so that this automatic service can work ... I could just as well leave it be and simply use the system tray icon like everybody else ... 

I have a similar problem with a "hamachi" VPN script that I wrote. I want "hamachi" to establish a VPN connection immediately after boot without my involvement. Nice idea. Except I have the same problem as above: For as long as I am not logged in the process won't be able to access its settings. And the only workaround is an ugly one: Leave it running as "root" ...

I have tried some other things too e.g. starting programs _AFTER_ I logged in and then leave them running after I logged out ... And guess what? This resulted in the harddisk remaining open and unencrypted because there was still one process running under my name. So ... why do I need encryption if the way I setup some background processes will defeat the purpose and leave the harddisk unlocked anyway?

So .... Long story short: If you are a weirdo like me and you want stuff (Dropbox, VPN clients, etc.) run automagically in the background for you (e.g. via boot scripts) then encryption will definitely be in your way. Either the background process can't run because the encryption is in its way or the encryption won't do a thing and not encrypt because that background process is preventing it from kicking in.

So right now I only really use full disk encryption on the laptops that I travel with. A few other machines have "ecryptfs" setup so that only a few critical sub-directories are encrypted while I am away (e.g. ~/.mozilla-thunderbird where Thunderbird stores my e-mails ...) but not the not-so-critical rest.

If however you're not such a shell script "let's automate everything" fetishist like me and more or less don't intend to use your system but from the comforts of a GUI .... then encryption probably won't be in your way at all. If your system is fast enough you won't even notice that it's there. :)

---

