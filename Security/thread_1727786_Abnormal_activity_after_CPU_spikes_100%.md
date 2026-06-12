---
title: "Abnormal activity after CPU spikes 100%"
date: 2011-04-12
forum: Security
---

### Post by espressobeanie on 2011-04-12
Hey all,

I'm not sure if I have been hit by something, or whether or not I found a bug somewhere. I just installed a php database called [Humogen]("http://humogen.com/") and I just finished setting it up when I took a 1.67Mb .GEODEB file and tried to import it for a test run.. My CPU spiked at 100% for about 5 minutes. I rebooted. I did a scan using chkrootkit, and it came back as nothing. I did a scan using rkhunter, and it gave me warnings:

Checking for 'hdparm' [Warning]
Checking for passwd file changes [Warning]
Checking for group file changes [Warning]
Checking for hidden files [Warning] <--probably false positive. I have many hidden files.

I did add a new account to give mysql it's own username, so root doesn't own it.

My CPU was below 10% before this incident, but now it hovers around 20%. I'm scanning with Tiger. Does anyone have any ideas what I should do next? I need to see what's taking up my CPU. I only account for 10% of the CPU fluctuating between Sys Monitor and firefox.

---

### Post by uRock on 2011-04-12
Does top or htop show what is causing the spike?

By spiking, do you mean that it is jumping up and staying there for a duration or going up then immediately returning to normal?

---

### Post by espressobeanie on 2011-04-12
Spiking, as going up and staying there. Hmm. I did a reboot to stop the 100% CPU power. It was loading a lot of data or something. 'Top' shows everything normal now.

Do you know of any programs that show any more in-depth analysis of what's going on aside from Top?

---

### Post by uRock on 2011-04-12
> **espressobeanie said:**
> Spiking, as going up and staying there.
Have you run the top command to see what is using the CPU?

If you use install and run htop it will allow you to kill the process with ease, once it is found. Once it is found someone here may be able to help you debug the process.

---

### Post by BkkBonanza on 2011-04-13
Most likely this is just the file import you did. The Humogen site warns that some large data imports can cause problems. I'd guess off hand that this is because the import routines may not be very efficient. Certainly a large import into a database with indexes and involving lots of data manipulation can cause severe loads for long periods.

The key really is to use top/htop to identify the process taking the resources. It is most likely either php or mysql depending on where the import work falls. The Humogen site and app looks pretty legit and well known so I wouldn't immediately jump to the conclusion that something malicious is happening - unless maybe you got files from some other location. A malicious data file could possibly be a threat if you just grabbed it off some forum or from an untrusted (torrent?) source.

htop is much better than top so you'd be wise to install that, sudo apt-get install htop. You can hit F6 to set sort to CPU % and it will pop the heavy users right to the top. Then leave it open in a terminal window while doing the file import and probably you'll see php/mysql right up there for a long time. If not then report back what process is taking the cpu.

---

### Post by espressobeanie on 2011-04-13
Sorry, for the delay. There aren't any unusual programs that I see. Mainly X.org, kcryptd, gnome-panel, metacity, and a couple of others that I recognize, like Mobloquer and initd every now and then. A lot of the noise sounds like my hard-drive spinning up and down. I thought it could be a malicious program running off with my entire disk, but htop says otherwise.

The highest are Mobloquer, X.org, and Tops. Wow, htop is so much better! Definitely what I was looking for! Gawd! I wish Windows Task Mgr had this much transparency.

I know it's not impossible, but do many rootkits and malicious files on Linux have odd filenames when executed, like Windows, or do they generally wrap around an existing process like Xorg or gdm?

---

### Post by BkkBonanza on 2011-04-13
A rootkit's primary goal is to be not detected. It usually replaces various system binaries with versions that do not show/log their use. The idea is that someone who has gained access can run things and do stuff without it showing up in process lists or logs and therefor goes undetected. If you see weird program names running it's almost by definition not a rootkit.

The problem with most of the automated rootkit detection tools is they throw up lots of false warnings and probably don't detect any real/modern rootkits. At least, according to my reading of forums, I've never seen a case where someone detected a real rootkit with one but I've seen endless streams of worried users reporting lists of warnings. 

Logically, what makes you think that any good rootkit wouldn't check for the 2 or 3 well known rootkit scanners and replace them with dummies? It's doing other system binaries so it may as well do them too.

The key to linux security is making sure root isn't compromised in the first place because once it is you may as well image the drive for forensics and re-install. In my opinion anyway.

---

