---
title: "How can I create rsync cronjob on my server to desktop?"
date: 2007-08-17
forum: Server Platforms
---

### Post by justin_c18 on 2007-08-17
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

I just got rsync working on my server to do a backup to my desktop, but instead of running it manually, how can I make a cronjob that will handle rsync? 

The backup will consist of backing up my /var/www directory on my server, and the backup will go to ~/backup/ServerWWW on my desktop. Although, it's not compressed, or a new directory isn't created in ~/backup/ServerWWW when I do it a 2nd time. How can I create an archive of backups instead of overwriting the existing directory? It's like 20mb of data, but I could delete the older backups if I want when I get it working. 

Is there a way to do a cronjob without using a .sh executable? I'm not sure where I can find the RSA key that was created when I did the backup.

I currently use: "sudo rsync -az -e ssh /var/www/ user@internalIP:~/backup/ServerWWW" on the server, which will put the backup in ~/backup/ServerWWW.

If there's a way to improve that command, please, let me know, along with cronjob information.

Thank you
Justin

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFGxk+P49trG/OjrkIRAqv7AJ9Wg59wcQzg0ec1ecoT+ezK83m6TwCdFiPv
8rP/TDKbV3Xqlnkl+Prd9NE=
=SeRj
-----END PGP SIGNATURE-----

---

### Post by HermanAB on 2007-08-18
Make a softlink from /etc/cron.daily:
$ sudo ln -s /usr/local/bin/whatever /etc/cron.daily/whatever

However, for that to work, you have to ensure that every call to a program in the script has the complete path specification, since the cron environment is very limited, for security reasons.

Cheers,

Herman

---

### Post by justin_c18 on 2007-08-18
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1


Hey, I'm doing it a completely different way now with RSA automation. I followed, [http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)

I'm assuming the process worked with the automation because it only asked for my desktop passphrase. But now, would I include the passphrase in my backup.txt so it will automate corrently? hmm

I will try it out, hopefully it works. ](*,)
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFGxnnU49trG/OjrkIRAntYAJ9H0EmGgMlje5vRgy2f+ag0b52UTACfX7N6
BmfAI8jqQ8JGTTOHmLz73c8=
=F/bq
-----END PGP SIGNATURE-----

---

