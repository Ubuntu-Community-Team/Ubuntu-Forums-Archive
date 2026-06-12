---
title: "Comments on File Server Strategy"
date: 2006-06-13
forum: Server Platforms
---

### Post by jccj7 on 2006-06-13
Hi -

I want to use an older PC as a central place to store files, pictures, music, and other digital data for 3 computer home network.

I thought I wanted to load the Server version of Ubuntu, but was shocked that it was a cmd line interface. I really want the Ubuntu GUI that I've been accustomed too.

So would a normal installation of Ubuntu with the appropriate sharing installed and configured be a sufficent setup to satisfy my requirement? I want to balance performance and capability with ease of setup and maintenance.

All of my searches address server config - so interested in any comments or suggestions.

Thanks

jc
__________________

---

### Post by DanielArdelian on 2006-06-14
Best way to do it and still get good performance is to leave the server as command line only. Install Midnight Commander (a good file manager with a decent text editor) from the Universe repository:
  ```
apt-get install mc
```

There are other threads on how to enable the Universe repository, I won't go into details here. 

Install Samba:
  ```
apt-get install samba
```

and look for documentation on configuring Samba

The Server Guide (sticky thread at the top) gives some good getting-started info on Samba).

Alternatively, you can do a complete *desktop* installation and install / configure / run Samba from the GUI. It gives you the exact same capability as a server install for sharing files, the only downside is the GUI and related stuff  take up disk space, memory and CPU and this could affect the performance of your server. The impact might be negligible in your case, depending on the hardware configuration. If you have at least 256 MB of RAM and a 500 MHz processor, I'd say you're okay even running a GUI. Alternatively, you could try the xubuntu-desktop version, which is "lighter" on the hardware requirements.

The desktop part can also be installed on a server install using:
```
  apt-get install ubuntu-desktop 
```
or
```
  apt-get install xubuntu-desktop 
```

In that case, you might have to use the "startx" command to start the GUI after logging in at the console.

---

### Post by jccj7 on 2006-06-14
Nice suggestion, thanks.  I'll try MC out as I research other ideas.  Thanks.

---

