---
title: "Remove 12.04 GUI on Desktop install to create server"
date: 2012-12-27
forum: Server Platforms
---

### Post by rgl2020 on 2012-12-27
Hi, hopefully someone can help me out.  I have a computer I was using as a HTPC with Ubuntu Desktop on it.  I have been sticking to the LTS versions and have gone through several updates.  I no longer use it as a htpc and instead am using it as a file and media server as well as a few other things.  I want to get rid of the gui and all the extra bloat included in the desktop version.  I thought about doing a clean install, but thought that it would be more trouble than it's worth.  So now that you know my situation, I have several questions.

1. Is there an easy way to remove the gui and bloat that comes with it?
2.  Will it even make a performance difference removing the gui?
3.  I read somewhere on this forum that there isn't any real difference anymore between the server and desktop versions except the gui.  Is that actually true?
4.  Should I just disable the gui instead?

---

### Post by chadk5utc on 2012-12-27
I believe the command that your looking for in
> sudo apt-get &#8212;purge remove gnome*
I personally would back up as needed and do a clean install.

---

### Post by ibjsb4 on 2012-12-27
If you not so sure about a server install, why not set up a 10 gig partition, install it and play with it for a while.

---

### Post by newbie-user on 2012-12-29
```
apt-cache show ubuntu-desktop
```

That shows all the dependencies and recommends for the ubuntu-desktop. Just copy all those package names and apt-get remove them.

+1 to chadk5utc's comment about a clean install.

---

### Post by Wim Sturkenboom on 2012-12-29
If the space that is occupied by the bloatware is not an issue, you can easily change your system to boot to console instead of GUI.

Edit /etc/default/grub, find the line that contains 'quiet splash' and add (or replace 'quiet splash' by) 'text'. From another post that I made, it should be this line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
Next run
```

sudo update-grub

```

---

### Post by rgl2020 on 2012-12-31
Thanks for the input.  I decided to just do a clean install.

---

### Post by ibjsb4 on 2013-01-01
Happy New Year  :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mark+thread+solved&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mark+thread+solved&as_qdr=all&sa=Google+Search&lang=en)

---

