---
title: "rsync backup for Android issue"
date: 2015-09-01
forum: Server Platforms
---

### Post by cbrinegar on 2015-09-01
I've been using the "rsync backup for Android" app for a few years now with perfect success.  I use it to copy pictures from my and my wife's phones to my home server.  It previously ran 12.04 LTS, but it has been running 14.04 LTS for about a year with no issues.  I have not had a problem with it until a couple of weeks ago.

Now I cannot run rsync successfully to my server from my phone.  However, I can run the same command from my laptop to rsync files to my server, and I can rsync my phone to my laptop just fine.  Also, I can ssh from my phone to my server just fine.  The error is rather cryptic and appears as follows on both mine and my wife's phones (each running different Android versions - hers being 4.x and mine being 5.0).

Error (paraphrased):
Host 'blah' key accepted unconditionally. (this app uses a dss key not a password)
rsync: connection unexpectedly closed (0 bytes received so far) [sender] [sender] _exit_cleanup(code=12, file=io.c, line226): entered
rsync error: error in rsync protocol data stream (code 12) at io.c(226)
[sender=3.1.1]
[sender] _exit_cleanup(code=12, file=io.c, line=226): about to call exit(12)

I'm not exactly a newb, and I've tried many things including trying to run an rsync-debug script placed on my server.  I was only able to get this script to run one time by using the --rsync-path=/the/path/rsync-debug option.  It created the log file one time, and hasn't worked since.

I am very confused how the rsync can work from my phone to laptop (same Ubuntu 14.04 on the laptop and server) and not to the server.  I'm out of ideas on how to get debug data out of these tests.  I've tried -vvvvv on rsync, and I'm getting nowhere fast.

I have suspicions that a recent Ubuntu update may have broken something.  My phone also got a major update recently, but my wife's hasn't changed.  All things are pointing to the server having a config or software version issue.  But then there's the fact that I can rsync over ssh from my laptop to the server, and I think that both have the same software (including updates).

If anyone has any ideas on what to try next, that would be great.  Nothing I've found online has been helpful.

---

### Post by papibe on 2015-09-01
Hi cbrinegar.

Make sure that the pubic key you generated in your phone is on your servers' ~/.ssh/authorized_keys file. I believe the line should end in "android@bender"

Let us know if that helped.
Regards.

---

### Post by cbrinegar on 2015-09-02
It is not an issue with the authorized_keys file.  As I noted in my paraphrased error, the first line says that the key was accepted unconditionally.  For reference, the key ends in rsync@android.

Just for kicks, I put the key in again and got the same result.

---

### Post by TheFu on 2015-09-03
I don't use rsync from android, but do have an ssh trouble-shooting guide that might help.
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

Nothing jumped out at me, but I didn't make a table of what worked from where and what didn't for all the different configs you have either. On android, is the ssh client built into the rsync app? Back when I was looking for a solution, I recall how different all the android versions of ssh, scp, sftp, and rsync were. They each seemed to bring their own stuff.  Some weren't very secure - didn't v1 ssh become disabled by default recently?  Or was that just a warning?

---

### Post by cbrinegar on 2015-09-03
That particular rsync app downloads its own ssh and rsync that the developer compiled.

Wondering if you were onto something with the changes to ssh, I rolled back both ssh and rsync to the oldest versions available in synaptic.  However, the error persists with no changes.  I even tried the newest rsync 3.1.1 from a newer Ubuntu release (downloaded, compiled, and installed from the .tgz), but that didn't work either.

I could be wrong, but it looks like ssh works fine.  And as I mentioned, I can do the same operation from my phone to a different computer running Ubuntu 14.04, and I can rsync from a different computer to my server just fine.

---

### Post by SeijiSensei on 2015-09-04
Do you have the same connection problems if you use Acrosync from the Google Play store?

---

### Post by cbrinegar on 2015-09-16
I just tried Acrosync, and it works fine.  Maybe I'll just switch over to that or something else.

Thanks for the tip.

---

### Post by cbrinegar on 2015-09-19
Okay, color me an idiot.  As a last ditch effort I cleared out and recreated my ~/.ssh/authorized_keys file, and now it works.  Something must have gotten corrupted.  It's all fixed now.

---

