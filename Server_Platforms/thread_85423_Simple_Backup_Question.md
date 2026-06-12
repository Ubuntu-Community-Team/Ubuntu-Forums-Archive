---
title: "Simple Backup Question"
date: 2005-11-02
forum: Server Platforms
---

### Post by Mr. Electric Wizard on 2005-11-02
If I want to backup my Server (just a snapshot of current configurations), can I just use WinSCP or similar to just copy the contents of the server to a directory on another machine, and just load it up later if my hard drive ever crashes?
I know with windows you have to deal with the registry and drivers and such, and cannot just make a copy of the hard drive, to use later on to reload the system.
Would this work?


I have two servers at my house that I need to back up.  They don't need to be on a chron job or anything I just want to do a manual backup of everything in case I lose a hard drive.

---

### Post by wylfing on 2005-11-02
In the land of *nix everything is a file. So in essence copying all the files to a different medium and then copying them back will restore the system. You can get a slight amount of flakiness because directories like /tmp and /var/run and /proc will have stuff that's only applicable to what's currently running right now, but it's nothing to worry about.

Be warned, however, that if you change your hardware between backing up and restoring, you can get some rather poor results. If that's what you're up to, there's a more careful backup you should make -- and I might even recommend doing a fresh install and then restoring only select directories from backup to bring the system back to a semblance of how it was before.

---

### Post by LordHunter317 on 2005-11-02
[QUOTE=Mr. Electric Wizard]If I want to backup my Server (just a snapshot of current configurations), can I just use WinSCP or similar to just copy the contents of the server to a directory on another machine, and just load it up later if my hard drive ever crashes?[/quote]You'd need to be doing this to another UNIX machine and I'd recommend rdiff-backup or rsync highly, at hte very least.

[quote=wylfing]gIn the land of *nix everything is a file.[/quote]Sadly, that's not true.  It looks like it's true, but it really isn't.  All special inodes (pipes, devices, fifos) and symlinks aren't really files.

---

### Post by Mr. Electric Wizard on 2005-11-02
Ok, here's the scenario in a little more depth.
I have an IPCop box, and a ClarkConnect Server box. 
The only hardware that will be replaced when a restore is done is the hard drive where all the files reside.
I want to do a "snap shot" backup of both servers, so in the event one of the HD's crater, I want to be able to copy back all of my config files, photo galleries, user profiles, firewall settings and so forth.

Even though everything might not be a file, I think that (I hope that), this should suffice?

What do you guys think?  Bacula is integrated into ClarkConnect, but I really don't want to bother with Cron jobs and such...

(BTW - sorry Mods, this is not really a Ubuntu question, but rather a general linux question - obviously)

---

