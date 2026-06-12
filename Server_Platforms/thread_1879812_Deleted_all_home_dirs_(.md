---
title: "Deleted all home dirs :("
date: 2011-11-12
forum: Server Platforms
---

### Post by HighCommander540 on 2011-11-12
I accidentally deleted all of the home directory contents.

Its not a big deal everything was backed up. What I want to know is how I get the encrypted directory back (I had it just for my account).

Also, if I need to do anything to fix what I did. For instance are there any essential files that I need to repopulate seeing as I am the only administrator account?

---

### Post by Paddy Landau on 2011-11-14
If you had deleted just your home directory contents, all you need to is log in and restore them from your backup. That's it.

If you had deleted your entire /home directory, however, it's somewhat more complicated. Did you back up your *encrypted* folder, or did you back up the files unencrypted?

---

### Post by HighCommander540 on 2011-11-14
I deleted the entire /home dir. I really just want to know what the files are that are generated when I create the user and if they are important?

The files where already backup somewhere else it was a fairly new install. And how I get the encrypted dir back.

*Thanks, for replying since no one else would.

---

### Post by SeijiSensei on 2011-11-14
I can't help with the encrypted directory, but why can't you just copy the entire backed-up copy of /home for the other users with unencrypted directories?  The backup should contain all the users' files, no?  As long as you have the same /etc/passwd and /etc/group files as before, all the users and groups will be mapped correctly to their numerical UIDs and GIDs.

---

### Post by HighCommander540 on 2011-11-14
> **SeijiSensei said:**
> I can't help with the encrypted directory, but why can't you just copy the entire backed-up copy of /home for the other users with unencrypted directories?  The backup should contain all the users' files, no?  As long as you have the same /etc/passwd and /etc/group files as before, all the users and groups will be mapped correctly to their numerical UIDs and GIDs.

Forgive me for not going into great detail why I am doing it this way before. My old files are from an old system. I wanted the newest versions of the files. I just like having clean fresh config files to edit you know? And they all got deleted, I have the system all setup now I don't want to re-install the system just for that.

I was just wondering if there was a way to repopulate them with the newest options.

Thanks for your help though. :)

---

### Post by SeijiSensei on 2011-11-14
Re-create the users with the adduser command.  When copying the backup, make sure to exclude files matching \.?* to preserve the newer versions.

---

### Post by HighCommander540 on 2011-11-15
> **SeijiSensei said:**
> Re-create the users with the adduser command.  When copying the backup, make sure to exclude files matching \.?* to preserve the newer versions.

OK, thanks that is what I thought I was going to have to do. Sadface, only have one user (my admin account). So I am pretty sure I will just have to reinstall the system.

[SOLVED]

---

