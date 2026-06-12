---
title: "can run a desktop with server?"
date: 2006-06-19
forum: Server Platforms
---

### Post by Aximilli on 2006-06-19
So I installed the server-edition, and was looking to put gnome on it so I can have a graphic interface. I tried install ubuntu-desktop, but of course that wiped out all the server apps. and apt-get install gnome says it cannot find the package. What can I do?

---

### Post by Iowan on 2006-06-19
Start with a quick search of the forums (this one in particular...), the topic has come up several times.  I'll try to look up a couple for you when I get home.  Good Luck (it CAN be done)!!!

---

### Post by az on 2006-06-19
[QUOTE=Aximilli]but of course that wiped out all the server apps. [/QUOTE]
Not true.  They do not conflict.

---

### Post by Iowan on 2006-06-19
Here's another thread about desktops and servers: [http://www.ubuntuforums.org/showthread.php?t=199988]("http://www.ubuntuforums.org/showthread.php?t=199988")
Oh, wait... that's yours...

---

### Post by houstonbofh on 2006-06-20
[QUOTE=Iowan]Start with a quick search of the forums (this one in particular...), the topic has come up several times.  I'll try to look up a couple for you when I get home.  Good Luck (it CAN be done)!!![/QUOTE]
That alone should tell us something...  I was quite surprised when I installed ubuntu-server for the first time.  No telnet, no ftp, no ssh, no desktop, no XDMCP, no webmin...  No way to touch the server, except for at the server.  Personally, I don't like to touch my servers.  I have a nice comfortable desktop to work at. :D  Since it is too late to make these install options, perhaps a big Stickie would help.

---

### Post by haircut on 2006-06-20
[QUOTE=houstonbofh]That alone should tell us something...  I was quite surprised when I installed ubuntu-server for the first time.  No telnet, no ftp, no ssh, no desktop, no XDMCP, no webmin...  No way to touch the server, except for at the server.  Personally, I don't like to touch my servers.  I have a nice comfortable desktop to work at. :D  Since it is too late to make these install options, perhaps a big Stickie would help.[/QUOTE]

That's why I love this server install. I don't want telnet, ftp, desktop, DMCP, webmin, samba, firewall ...

If you want LAMP then that's an option.

The only thing I needed and wanted above the standard install was SSH and a tutorial on iptables.

This server install isn't a "one application fits all" install. I tried the likes of Fedora and hated all the option I had to switch off to get it to install, it then still install a load of stuff I didnt want. I'd hate ubuntu if it moved away from the simplicity it already is. The best way it to try and provide options at install time.

Not flaming you here but I'm not to sure why you don't want to "touch" the server, maybe if you don't want to touch your server then Ubuntu isn't right for you?

Check the sticky at the top of this page regarding Server install, it tries to answer your questions, it certinly helped a nooob like me.

@Aximilli
I installed the desktop over the server, it worked fine for me but like I said I haven't installed much else but the default stuff.

---

### Post by Aximilli on 2006-06-20
Yea turns out that the 5.1 server edition just means it's running a kernel thats server-configged, or something like that. It's the drake server-edition that has lamp. thanx guys.

---

### Post by houstonbofh on 2006-06-20
[QUOTE=haircut]That's why I love this server install. I don't want telnet, ftp, desktop, DMCP, webmin, samba, firewall ...

If you want LAMP then that's an option.

The only thing I needed and wanted above the standard install was SSH and a tutorial on iptables.

This server install isn't a "one application fits all" install. I tried the likes of Fedora and hated all the option I had to switch off to get it to install, it then still install a load of stuff I didnt want. I'd hate ubuntu if it moved away from the simplicity it already is. The best way it to try and provide options at install time.[/QUOTE]
I agree.  A good example of this can be found at [http://paulenglish.com/windows/undell.html](http://paulenglish.com/windows/undell.html) which is a full day job!  My point is that one extra splash screen with common server programs you might want to install *with nothing checked by default.*  And for now, a big sticky with "Common packages for server install."

As to the "touching my server" bit.  Often the server is in another room, building, city or state.  Rarely are servers at the same desk as the user.

---

### Post by Isoss on 2006-06-20
I have installed LAMP and it worked fine ... I could SSH and FTP and everything, then I decided to install a desktop and all I did was apt-get install xubuntu-desktop and it's as if I have installed xubuntu from the first time. No conflict I assure that.

---

### Post by imagine on 2006-06-20
Maybe refering to the server install as a minimal install would clear up some misunderstandings.
If you want to have a X server and Gnome, then you don't want a server install, but the normal desktop install, because the server install option is essentially normal install minus ubuntu-desktop.

---

### Post by haircut on 2006-06-21
[QUOTE=houstonbofh]As to the "touching my server" bit.  Often the server is in another room, building, city or state.  Rarely are servers at the same desk as the user.[/QUOTE]

Same here, well sort of. At the moment my server is actully next to my desk but I don't have or want a mouse, keyboard and monitor attached to it. I SSH to it from a Win32 machine.

I got the impression you wanted a simple click and install with no further set-up required.

@ imagine
I think it was called minimal install before the called it server install ... maybe some Ubuntu guru could answer that for us. Calling it minimal could also be confusing as a minimal install could/should have a desktop anyway?

---

### Post by houstonbofh on 2006-06-21
[QUOTE=imagine]Maybe refering to the server install as a minimal install would clear up some misunderstandings.
If you want to have a X server and Gnome, then you don't want a server install, but the normal desktop install, because the server install option is essentially normal install minus ubuntu-desktop.[/QUOTE]
The problem is that we have ubuntu-desktop, kbuntu-desktop, and xbuntu-desktop tags, but no LAMP-server tag.  It is so much easier to install a LAMP server and apt-get install xbuntu-desktop than to install xbuntu and chase down all the LAMP components.  (But even that leaves out php-gd...  Nothing is perfect) :D  As a minimal install it makes sense, but as a functional LAMP server "for humans" I still think it could use a little more...  But there is a fine line between tools and bloat, so I am treading softly.

---

