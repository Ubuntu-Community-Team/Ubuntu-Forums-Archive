---
title: "SSH files go missing"
date: 2017-03-01
forum: Server Platforms
---

### Post by jrdbrndt on 2017-03-01
Over the course of the last two years, I have been teaching computer science at the high school level. We are learning to build web sites. I am renting a virtual server that is located out of my physical reach.

I have an OpenSSH server installed on the web server, and we have tried many methods of connecting to it, including:

- From Windows using WinSCP
- From Windows using FileZilla
- From Ubuntu using FileZilla
- From Ubuntu using gvfsd-sftp
- From Ubuntu using sshfs

However, it doesn't seem to matter which front-end we are using to manage our files, users have been experiencing a strange event. I have never experienced it myself, and it certainly doesn't happen often, but perhaps a 1 or 2 dozen times in the last two years.

It just happened again yesterday, and then right away again today, so here I am.

Seemingly randomly, a user will create an SFTP connection to the web server from their computer, and some or all of their files will be missing. Just gone. No trace. I SSH into the web server with my administrator account and list the contents of their home directory and find the same thing -- it's not them, the files are just gone.

I have tried running fsck, but nothing has turned up in lost+found. Yesterday at 1:00pm I installed the audit daemon, watching for writes and attribute changes (auditctl -w /home -p wa). Unfortunately, more files went missing at 11:00am today, but they may have actually gone missing YESTERDAY at 11:00am and we only noticed it today. So at this moment, the audit daemon hasn't yielded anything I can use.

I have Googled and Googled, but I'm not sure I can find anyone else with this problem. Surely, the students aren't deleting their own work. They have exclusive write privileges in their home directories, so nobody else is deleting their files either. I'm hoping next time it happens the audit daemon will show me what's up -- but I have to assume that sshd is the process deleting the files... I just don't know why!

Anyone have any thoughts on why this might be happening? Any logs I can show, or other information that would help?

I appreciate you taking your time to read through this!!

---

Server:

Ubuntu Server 16.04.2
4.4.0-64-generic
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g

Client:

Xubuntu 16.04.2
4.4.0-64-generic
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g

---

### Post by QIII on 2017-03-01
Hello!

I'm not much of a believer in magic or computer gremlins.  It is more likely that the files *are being removed*.

It is possible that a sufficiently clever student(s) is accessing the home directory of other students with mischievous or malicious intent.

Have you confirmed the permissions and ownership of each student's home folder?  What are you doing to protect against "all access is root access"?

---

### Post by jrdbrndt on 2017-03-01
I understand your skepticism... I am not a fan of the "magic" theory either. To address your concerns, let's consider that the user whose files went missing today is named "pringles."

I can verify that:

/home/pringles belongs to root:root with 755 mode. (So I can chroot the user to their home folder in SFTP.)
/home/pringles/html belongs to pringles:pringles with 750 mode.
I am the only other member of the pringles group, so I can read pringles' files (to grade them).
All other users' folders were created in this same way.

As for sufficiently clever students... while I do have a couple geniuses in the class, I'm not convinced that this is the case, considering this problem has now spanned four different classes of students. I have had exactly the same issue during each semester, though the kids every semester have been different.

My admin password is "extremely" (my word, not necessarily anyone else's) secure, and I change it often enough that I'm convinced no other user has access to my account. The root account is also locked so no one can use it. I can verify that I am the only user with sudo privileges as well.

Jared

---

### Post by QIII on 2017-03-01
Is your VPS exposed to the web?

---

### Post by Habitual on 2017-03-01
When I hear, or think Gremlins, I check cron

Just sayin'

---

### Post by HermanAB on 2017-03-01
Well, you are listing five different access methods.  Which kind goes missing?

My guess is that things go missing due to interruptions in the network connection during transfers.  The student starts an 'synch' process, then closes the lid of his laptop or similar.  Simple file transfer protocols are not good at handling those kind of events.  The rsync program is designed to handle errors properly, so you'll have more luck with that.

I hope you make daily backups.

---

### Post by jrdbrndt on 2017-03-01
The VPS is exposed.

I see there are a lot of things in cron right now, but I've never touched any of them myself. I can check there to see if there's anything strange, but it will take a while before I could get back.

The problem seems to happen regardless of which client we are using to connect. Just for kicks, one of my students just suggested we try uploading a large file and interrupting it half way to see what would happen. I logged out half way through the transfer. The file was still there when we came back, but only partially uploaded -- not missing entirely. I agree with you that network interruptions are probably the most likely, but why would that cause an entire folder's contents to go missing, rather than just any open files?

Jared

---

### Post by kingneutron on 2017-03-01
--I would recommend scheduling a compressed tar backup of /home right after every class, to start with. Then you can go back from there.

---

### Post by jrdbrndt on 2017-03-01
On it. Backup is scheduled, so I can recover if need be in the future.

From the discussion, I assume that an interrupted synch process is the most likely culprit? I will just reinforce the idea of saving everything and doing a graceful unmount at the end of the day and hopefully this will happen less frequently.

Thank you all for your input. I will mark this as solved.

---

