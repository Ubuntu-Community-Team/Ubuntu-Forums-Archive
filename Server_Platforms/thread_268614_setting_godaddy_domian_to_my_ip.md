---
title: "setting godaddy domian to my ip"
date: 2006-09-30
forum: Server Platforms
---

### Post by hal729 on 2006-09-30
I bought a domain name recently, and want to use my computer to serve it.  I've downloaded LAMP and bind9.  I followed the instructions from this thread ( [http://ubuntuforums.org/showthread.php?t=267025&highlight=nameserver](http://ubuntuforums.org/showthread.php?t=267025&highlight=nameserver) ) on how to set up the bind9 program.  But when I go to goDaddy's site and try to put in my IP as the nameserver, it doesn't work - all it says is errors were detected.

Oh, and I have a static IP address through my university.

I'm relatively new to Ubuntu, and I haven't got a clue what to do now.

ETA: I haven't done anything to any of the files in my version of apache2, because all the things I tried last time resulted in me having to uninstall it, so I'm not sure what needs to be done.

---

### Post by bluefrog on 2006-10-02
If I understand well your university has a static public ip, but as your computer is on the local network you have to forward the dns request to your computer.

I do not think you will be able to achieve what you want from where you are (except if you are part of the IT team or something similar).

James

---

### Post by halitech on 2006-10-02
you won't be able to use your system as the name server but ifyou create an account with zone edit (completely free if under 5 domains) you can use their DNS service to point your domain at your computer. with you being on a local LAN, it may or not work if you do not have the ability to forward ports and most universities normally block that type of thing, it may not work. You could *try* something like DYNU.com to set your external IP but don't think it will work.

---

