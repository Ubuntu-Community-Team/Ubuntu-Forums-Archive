---
title: "upgrade to server kernel - lost settings"
date: 2009-02-08
forum: Server Platforms
---

### Post by Jeztastic on 2009-02-08
Hi!

i recently set up a media home server, using Xubuntu desktop edition and then apt-get removing desktop. I now want to upgrade to the server kernel - mostly because it's a more elegant solution. So I did;

 ```
sudo apt-get install linux-server
```

Now when I boot into the server kernel nothing works. I have reverted to the generic kernel. I backed up /etc before I started - will restoring this replace all the settings? I don't really understand why updating the kernel causes all the settings to disappear.

---

### Post by steveneddy on 2009-02-08
It seems to me that the more "elegant" solution would be to either install the server edition and then add the media packages that you need or just install the media edition and turn the GUI on and off via a command line.

This way if you need the GUI you can start it up via command line.

```
sudo /etc/init.d/gdm start

sudo /etc/init.d/gdm stop
```

If memory serves, these are the correct commands to start/stop the GUI.

---

### Post by Jeztastic on 2009-02-08
> **steveneddy said:**
> It seems to me that the more "elegant" solution would be to either install the server edition and then add the media packages that you need or just install the media edition and turn the GUI on and off via a command line.

This way if you need the GUI you can start it up via command line.

```
sudo /etc/init.d/gdm start

sudo /etc/init.d/gdm stop
```

If memory serves, these are the correct commands to start/stop the GUI.

Sorry, you've completely misunderstood me... Probably my fault. I got rid of the GUI immediately, the only reason that I used it was because of the graphical install via the live CD is so good. 

When I say nothing works I mean that settings for networking and so on are not present. What has changed now that I've changed the kernel and why?

---

