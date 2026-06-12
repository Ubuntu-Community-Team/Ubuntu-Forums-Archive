---
title: "Newbie with a question"
date: 2009-09-29
forum: Server Platforms
---

### Post by greatwhitewing on 2009-09-29
I am considering buying a couple year old used computer as a home server and run Ubunto home server for a small home network. Mostly for backups and central file sharing. I don't want a monitor or keyboard for this server. I want to operate remote if possible since it will be in the basement.

I would like dual 1 TB drives mirrored in case one fails.

Any help on min computer requirements or  in any other way would be appreciated.

I hope I am on the right sub forum.

My computers consist of one HP Vista 64 bit laptop, 2 HP Vista 32 bit laptops, One Dell XP home laptop and finally a Dell XP home desktop.

I have a reasonable wired and wireless network. Two routers, one switchbox, a Vonage device and several wired circuits through-out the house.

Thanks
John:guitar:

---

### Post by KiLaHuRtZ on 2009-09-29
> **greatwhitewing said:**
> I am considering buying a couple year old used computer as a home server and run Ubunto home server for a small home network. Mostly for backups and central file sharing. I don't want a monitor or keyboard for this server. I want to operate remote if possible since it will be in the basement.

You sure can run it headless.  I'd recommend Ubuntu 8.04 LTS (Hardy).  Being an LTS (Long Term Support) edition, which is released every two years, it has server support up to April of 2013 before you are required to upgrade.  Your main package you'll want to setup is SSH (secure shell) so you can remotely administer it.  I'd also look towards a decent amount of RAM vs. CPU power for file sharing / backing up.  If you have a lot of large files, like movies, a decent amount of RAM will prevent a lot of disk reads.  Also, a good network card (or cards -- google ifenslave) would be a wise choice as well.

---

### Post by damo12 on 2009-09-30
As I am pretty much a newbie to Linux myself I would strongly recommend installing Webmin for remote access.  There is an excellent guide at [http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

---

### Post by cyrusthevirus on 2009-09-30
I've found the following documentation to be invaluable when it comes to configuring servers.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by greatwhitewing on 2009-09-30
Thanks for the reply. How do you load and set up a remote control? Can I do that from my Windoze laptop or do I need a keyboard and monitor to set it up?

What's the ifenslave? Why would I want it?

Sorry for the questions being so basic, I said I was a newbie... I am intermediate skill level with windows but servers and Linux are foreign to me.

John

> **KiLaHuRtZ said:**
> You sure can run it headless.  I'd recommend Ubuntu 8.04 LTS (Hardy).  Being an LTS (Long Term Support) edition, which is released every two years, it has server support up to April of 2013 before you are required to upgrade.  Your main package you'll want to setup is SSH (secure shell) so you can remotely administer it.  I'd also look towards a decent amount of RAM vs. CPU power for file sharing / backing up.  If you have a lot of large files, like movies, a decent amount of RAM will prevent a lot of disk reads.  Also, a good network card (or cards -- google ifenslave) would be a wise choice as well.

---

### Post by Iowan on 2009-09-30
You will need keyboard and monitor to set up system initially. I use SSH to administer most of my servers... but you gotta appreciate CLI. Server's *can* be set up with GUI, or use Webmin. ([eBox]("https://help.ubuntu.com/community/eBox") is another package that comes to mind)
[Here]("http://linux.about.com/cs/linux101/g/ifenslave.htm") is a definition of ifenslave and a [man]("http://linux.die.net/man/8/ifenslave") page for it.

---

### Post by greatwhitewing on 2009-09-30
Thanks but the definition made no sense to me at all to me. The whole server language is completely foreign to me. Should I avoid Linux because I really don't want to make a research project out of it?  I don't mind doing a little homework but I just don't have the time or desire to learn a lot about it.

I am not stupid but pretty darn ignorant... :lolflag:
Really appreciate your time and help.

John


> **Iowan said:**
> You will need keyboard and monitor to set up system initially. I use SSH to administer most of my servers... but you gotta appreciate CLI. Server's *can* be set up with GUI, or use Webmin. ([eBox]("https://help.ubuntu.com/community/eBox") is another package that comes to mind)
[Here]("http://linux.about.com/cs/linux101/g/ifenslave.htm") is a definition of ifenslave and a [man]("http://linux.die.net/man/8/ifenslave") page for it.

---

### Post by americanLoki on 2009-10-01
> **greatwhitewing said:**
> Thanks but the definition made no sense to me at all to me. The whole server language is completely foreign to me. Should I avoid Linux because I really don't want to make a research project out of it?  I don't mind doing a little homework but I just don't have the time or desire to learn a lot about it.

I am not stupid but pretty darn ignorant... :lolflag:
Really appreciate your time and help.

John

If I understand correctly ifenslave basically teams network devices together. So if you have network card A and B, ifenslave creates virtual card C for the system. Card C becomes your primary network interface and when packets are sent out via C they are sent out over both A and B. This allows you to have load balancing and in some cases greater throughput.

---

### Post by greatwhitewing on 2009-10-01
> **americanLoki said:**
> If I understand correctly ifenslave basically teams network devices together. So if you have network card A and B, ifenslave creates virtual card C for the system. Card C becomes your primary network interface and when packets are sent out via C they are sent out over both A and B. This allows you to have load balancing and in some cases greater throughput.

Thanks for the translation, makes sense. Maybe I should have said trying to keep things simple too.

---

### Post by Iowan on 2009-10-01
I have a few home servers set up - mostly for the experience. I don't use **ifenslave**. It isn't essential - if you want to try something new, go for it.  If it looks like too much trouble, leave it (at least for now). Setting up an LDAP server is still on my list, but it's gonna take more research.

If something else is on your more immediate list, help is only a question away.

---

### Post by stlsaint on 2009-10-01
setting up a server is very easy... Use the [UbuntuServerGuide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")...
i use ssh to control my server and my vps...make sure you setup public key cryptography so as to prevent an attack on your server. Yes you will need a keyboard and mouse for initial setup but after that you will never need it again...also i never use gui for my servers and this is my first one in ubuntu. Learn CLI...its the most valuable and gives you ultimate control. See here for [PublicKeyCrypt]("http://www.debuntu.org/ssh-key-based-authentication")!! It may take a little work (little) but once its all setup you will have a greater knowledge and respect for servers...and like i said its fun fun fun...and once you get good with that you can go on to virtual servers...even better!! =)
Also use IRC...real time help!!

---

