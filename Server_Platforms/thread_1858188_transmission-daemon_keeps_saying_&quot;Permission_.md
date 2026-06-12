---
title: "transmission-daemon keeps saying &quot;Permission denied&quot; in the webui"
date: 2011-10-11
forum: Server Platforms
---

### Post by sirspazzolot on 2011-10-11
I added a torrent and it downloads a few hundred KB and then says Permission denied (long foldername)

the long foldername had an extra, nonexistent folder at the end of it, so I created that folder, but the problem persists. I've set the permissions on all to 777. Eh?

---

### Post by papibe on 2011-10-12
Hi sirspazzolot. Are you running transmission-daemon in the same machine you are using the WebUI?

Have you customize your settings.json ?
Could you post your /etc/transmission-daemon/settings.json ?

Regards.

---

### Post by kerry_s on 2011-10-12
What I do is set up transmission with the settings I want, then copy the settings to /etc/transmission-daemon/
It's a lot easier than editing the file directly.

---

### Post by DavidBeijer on 2011-10-12
Did you reload the deamon after you have changed the file? Or turned off the deamon, than saved the file changes and then started the deamon again? Otherwise your changes will not be applied, as Transmission writes to the settings.json file on exiting...

---

### Post by kerry_s on 2011-10-13
Good point, you need to do:
sudo service transmission-daemon stop

Make your changes, then:
sudo service transmission-daemon start

---

