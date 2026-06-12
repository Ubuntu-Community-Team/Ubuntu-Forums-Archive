---
title: "Encryption questions"
date: 2011-11-18
forum: Security
---

### Post by ftornell on 2011-11-18
Hi,
I have two questions regarding encryption of the homefolders.

Lets say I encrypt using the default installation encryption  for my /home/fredrik folder.

If I choose to mount a cifs/smb volume into /home/fredrik/pictures
That won't encrypt the sub-folders then right?

Another question:
for testing - I now run a small website to play with php/mysql and I can reach it from Internet. I also have a backup on that server for documents and pictures from my laptop as well as my wife's laptop.

If someone hacks into the server using apache/mysql exploits they will most likely have root-privileges and my personal files are compromised. And the encryption I talked about earlier wont prevent this since ubuntu decrypts the volume when I enter my password at logon?

How can I securely store this information. I know I should not have these "backup" on a web server facing Internet, but I have...

---

### Post by WasMeHere on 2011-11-18
> **ftornell said:**
> ...
How can I securely store this information. I know I should not have these "backup" on a web server facing Internet, but I have...

Hej Fredrik!

I don't know if a cifs/smb volume into /home/fredrik/pictures would be available but you can always test it. But instead you can mount it in another directory for example /home/shared.

Yes, if an attacker finds your password you have tough luck :-(

I'd say, do ***not*** store personal information on a server that is open to the internet. Store it on some other computer or simply ***on an external hard drive***, that is not connected to your server while connected to the internet!

Kolla vår nya wikisida om säkerhet för nybörjare
[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
men tänk på att det krävs mycket mer för att säkra en server!

Ha kul på din upptäcktsfärd i linuxrymden :-)
Olle

---

